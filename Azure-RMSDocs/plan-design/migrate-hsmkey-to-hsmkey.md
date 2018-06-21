---
title: Migrowanie klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM — AIP
description: Instrukcje będące częścią ścieżki migracji z usługi AD RMS do usługi Azure Information Protection, stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez moduł HSM, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez moduł HSM w usłudze Azure Key Vault.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/19/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: c8ed0fd3e8daa2c03f179cf71c0c258b8ef79901
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
ms.locfileid: "30207917"
---
# <a name="step-2-hsm-protected-key-to-hsm-protected-key-migration"></a>Krok 2. Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM

>*Dotyczy: Active Directory Rights Management Services [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*


Te instrukcje są częścią [ścieżki migracji z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) i są stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez moduł HSM, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez moduł HSM w usłudze Azure Key Vault. 

Jeśli nie jest to wybrany scenariusz konfiguracji, wróć do [Kroku 4. Eksportowanie danych konfiguracji z usługi AD RMS i importowanie ich do usługi Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) i wybierz inną konfigurację.

> [!NOTE]
> W tych instrukcjach przyjęto założenie, że klucz usługi AD RMS jest chroniony przez moduł. Jest to najbardziej typowy przypadek. 

Jest to składająca się z dwóch części procedura, która umożliwia zaimportowanie klucza HSM i konfiguracji usługi AD RMS do usługi Azure Information Protection oraz zastosowanie w ten sposób zarządzanego przez Ciebie klucza dzierżawy usługi Azure Information Protection (BYOK).

Ponieważ klucz dzierżawy usługi Azure Information Protection będzie przechowywany i zarządzany przez usługę Azure Key Vault, ta część migracji wymaga administracji w usłudze Azure Key Vault poza administracją w usłudze Azure Information Protection. Jeśli usługa Azure Key Vault jest zarządzana przez innego administratora w Twojej organizacji, musisz podjąć współpracę z tym administratorem, aby zakończyć procedury.

Przed rozpoczęciem upewnij się, że Twoja organizacja ma magazyn kluczy utworzony w usłudze Azure Key Vault oraz że obsługuje klucze chronione przez moduł HSM. Chociaż nie jest to wymagane, zaleca się posiadanie dedykowanego magazynu kluczy dla usługi Azure Information Protection. Ten magazyn kluczy zostanie skonfigurowany tak, aby usługa Azure Rights Management mogła uzyskać do niego dostęp, dlatego klucze przechowywane w tym magazynie kluczy powinny być ograniczone wyłącznie do kluczy usługi Azure Information Protection.


> [!TIP]
> Jeśli przeprowadzasz konfigurację usługi Azure Key Vault, a nie masz doświadczenia z tą usługą platformy Azure, warto zapoznać się z artykułem [Rozpoczynanie pracy z usługą Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/). 


## <a name="part-1-transfer-your-hsm-key-to-azure-key-vault"></a>Część 1. Przesłanie klucza HSM do usługi Azure Key Vault

Te procedury są wykonywane tylko przez administratora usługi Azure Key Vault.

1. W przypadku każdego wyeksportowanego klucza SLC, który chcesz przechowywać w usłudze Azure Key Vault, postępuj zgodnie z instrukcją zawartą w dokumentacji usługi Azure Key Vault w sekcji [Implementowanie funkcji BYOK dla usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azurekey-vault), z następującym wyjątkiem:

    - Nie wykonuj kroków procedury **Generowanie klucza dzierżawy**, ponieważ istnieje już jego odpowiednik pochodzący z wdrożenia usługi AD RMS. Zamiast tego zidentyfikuj klucz używany na serwerze usługi AD RMS z instalacji firmy Thales i użyj go podczas migracji. Zazwyczaj są nazywane zaszyfrowane pliki klucza firmy Thales **klucza <*keyAppName*><*keyIdentifier* >**  lokalnie na serwerze.

    Gdy klucz zostanie przekazany do usługi Azure Key Vault, zostaną wyświetlone właściwości klucza zawierające identyfikator klucza. Będzie wyglądała podobnie do https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333. Zanotuj ten adres URL, ponieważ administrator usługi Azure Information Protection potrzebuje go, aby skonfigurować usługę Azure Rights Management do użycia tego klucza jako klucza dzierżawy.

2. Na stacji roboczej podłączonej do Internetu, w sesji programu PowerShell, użyj polecenia cmdlet [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy), aby autoryzować nazwę główną usługi Azure Rights Management do dostępu do magazynu kluczy, w którym przechowywany będzie klucz dzierżawy usługi Azure Information Protection. Wymagane uprawnienia to: decrypt, encrypt, unwrapkey, wrapkey, verify i sign.
    
    Przykładowo jeśli magazyn kluczy utworzony dla usługi Azure Information Protection ma nazwę contoso-byok-ky, a grupa zasobów ma nazwę contoso-byok-rg, uruchom następujące polecenie:
    
        Set-AzureRmKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get


Teraz klucz HSM w usłudze Azure Key Vault jest już gotowy do użycia w usłudze Azure Rights Management z usługi Azure Information Protection, a Ty możesz importować dane konfiguracji usługi AD RMS.

## <a name="part-2-import-the-configuration-data-to-azure-information-protection"></a>Część 2. Importowanie danych konfiguracji do usługi Azure Information Protection

Te procedury są wykonywane tylko przez administratora usługi Azure Information Protection.

1. Na stacji roboczej podłączonej do Internetu i w sesji programu PowerShell połącz się z usługą Azure Rights Management, używając polecenia cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice).
    
    Następnie przekaż każdy plik XML zaufanej domeny publikacji, korzystając z polecenia cmdlet [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd). Na przykład po uaktualnieniu klastra usług AD RMS dla trybu kryptograficznego 2 powinien być dostępny przynajmniej jeden dodatkowy plik do zaimportowania.
    
    Do uruchomienia tego polecenia cmdlet konieczne jest hasło, które zostało określone wcześniej dla każdego pliku danych konfiguracji, oraz adres URL klucza zidentyfikowany w poprzednim kroku.
    
    Przykładowo — używając pliku danych konfiguracji C:\contoso-tpd1.xml i naszej wartości adresu URL klucza z poprzedniego kroku, należy najpierw uruchomić następujące polecenie w celu zapisania hasła:
    
    ```
    $TPD_Password = Read-Host -AsSecureString
    ```
    
    Wprowadź określone wcześniej hasło, aby wyeksportować plik danych konfiguracji. Później uruchom następujące polecenie i potwierdź wykonanie tej akcji:
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword $TPD_Password –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Verbose
    ```
    
    W ramach tego importu klucz SLC zostanie zaimportowany i automatycznie ustawiony jako zarchiwizowany.

2.  Po przesłaniu każdego pliku uruchom polecenie [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) w celu określenia, który zaimportowany klucz pasuje do aktualnie aktywnego klucza certyfikatu licencjodawcy serwera w klastrze AD RMS. Ten klucz staje się aktywnym kluczem dzierżawy usługi Azure Rights Management.

3.  Użyj polecenia cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice), aby zakończyć połączenie z usługą Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```

Jeśli chcesz później potwierdzić, którego klucza używa Twój klucz dzierżawy usługi Azure Rights Management w usłudze Azure Key Vault, użyj polecenia cmdlet usługi Azure RMS [Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys).

Teraz możesz wykonać [Krok 5. Aktywuj usługę Azure Rights Management](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

