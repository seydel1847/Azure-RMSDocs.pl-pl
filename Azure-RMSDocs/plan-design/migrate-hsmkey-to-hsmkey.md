---
title: "Krok 2&colon; Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM | Azure Information Protection"
description: "Instrukcje będące częścią ścieżki migracji z usługi AD RMS do usługi Azure Information Protection, stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez moduł HSM, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez moduł HSM w usłudze Azure Key Vault."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/23/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5aac7b9fae12642c9846a70c5d271c7600af4096
ms.openlocfilehash: 5def3aa722afd29b99ef18c100d71a447c22554f


---

# <a name="step-2-hsm-protected-key-to-hsm-protected-key-migration"></a>Krok 2. Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection*


Te instrukcje są częścią [ścieżki migracji z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) i są stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez moduł HSM, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez moduł HSM w usłudze Azure Key Vault. 

Jeśli nie jest to wybrany scenariusz konfiguracji, wróć do [Kroku 2. Eksportowanie danych konfiguracji z usługi AD RMS i importowanie ich do usługi Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) i wybierz inną konfigurację.

> [!NOTE]
> W tych instrukcjach przyjęto założenie, że klucz usługi AD RMS jest chroniony przez moduł. Jest to najbardziej typowy przypadek. 

Jest to składająca się z dwóch części procedura, która umożliwia zaimportowanie klucza HSM i konfiguracji usługi AD RMS do usługi Azure Information Protection oraz zastosowanie w ten sposób zarządzanego przez Ciebie klucza dzierżawy usługi Azure Information Protection (BYOK).

Ponieważ klucz dzierżawy usługi Azure Information Protection będzie przechowywany i zarządzany przez usługę Azure Key Vault, ta część migracji wymaga administracji w usłudze Azure Key Vault poza administracją w usłudze Azure Information Protection. Jeśli usługa Azure Key Vault jest zarządzana przez innego administratora w Twojej organizacji, musisz skoordynować pracę z tym administratorem, aby zakończyć procedurę.

Przed rozpoczęciem upewnij się, że Twoja organizacja ma magazyn kluczy utworzony w usłudze Azure Key Vault oraz że obsługuje klucze chronione przez moduł HSM. Chociaż nie jest to wymagane, zaleca się posiadanie dedykowanego magazynu kluczy dla usługi Azure Information Protection. Ten magazyn kluczy zostanie skonfigurowany tak, aby usługa Azure Rights Management mogła uzyskać do niego dostęp, dlatego klucze przechowywane w tym magazynie kluczy powinny być ograniczone wyłącznie do kluczy usługi Azure Information Protection.


> [!TIP]
> Jeśli chcesz przeprowadzić konfigurację usługi Azure Key Vault, a nie masz doświadczenia z tą usługą platformy Azure, przydatne może okazać się przeczytanie artykułu [Wprowadzenie do usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/). 


## <a name="part-1-transfer-your-hsm-key-to-azure-key-vault"></a>Część 1. Przesłanie klucza HSM do usługi Azure Key Vault

Te procedury są wykonywane tylko przez administratora usługi Azure Key Vault.

1.  Wykonaj instrukcje zawarte w dokumentacji usługi Azure Key Vault, korzystając z sekcji [Implementowanie funkcji BYOK dla usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) z następującym wyjątkiem:

    - Nie wykonuj kroków procedury **Generowanie klucza dzierżawy**, ponieważ istnieje już jego odpowiednik pochodzący z wdrożenia usługi AD RMS. Zamiast tego zidentyfikuj klucz używany na serwerze usługi AD RMS z instalacji firmy Thales i użyj go podczas migracji. Zaszyfrowane pliki klucza firmy Thales mają przeważnie nazwę **key<*nazwa_aplikacji_klucza*><*identyfikator_klucza*>** i są przechowywane lokalnie na serwerze.

    Gdy klucz zostanie przekazany do usługi Azure Key Vault, zostaną wyświetlone właściwości klucza zawierające identyfikator klucza. Identyfikator będzie wyglądać podobnie do następującego: https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333. Zanotuj ten adres URL, ponieważ administrator usługi Azure Information Protection będzie go potrzebować, aby skonfigurować usługę Azure Rights Management do użycia tego klucza jako klucza dzierżawy.

2. Na stacji roboczej podłączonej do Internetu, w sesji programu PowerShell, użyj polecenia cmdlet [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/en-us/library/mt603625(v=azure.300\).aspx), aby autoryzować nazwę główną usługi Azure Rights Management do dostępu do magazynu kluczy, w którym przechowywany będzie klucz dzierżawy usługi Azure Information Protection. Wymagane uprawnienia to: decrypt, encrypt, unwrapkey, wrapkey, verify i sign.
    
    Przykładowo jeśli magazyn kluczy utworzony dla usługi Azure Information Protection ma nazwę contoso-byok-ky, a grupa zasobów ma nazwę contoso-byok-rg, uruchom następujące polecenie:
    
        Set-AzureRmKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get


Teraz klucz HSM w usłudze Azure Key Vault jest już gotowy do użycia w usłudze Azure Rights Management z usługi Azure Information Protection, a Ty możesz importować dane konfiguracji usługi AD RMS.

## <a name="part-2-import-the-configuration-data-to-azure-information-protection"></a>Część 2. Importowanie danych konfiguracji do usługi Azure Information Protection

Te procedury są wykonywane tylko przez administratora usługi Azure Information Protection.

1.  Na stacji roboczej podłączonej do Internetu i w sesji programu PowerShell połącz się z usługą Azure Rights Management, używając polecenia cmdlet [Connect-AadrmService](https://msdn.microsoft.com/library/dn629415.aspx).
    
    Następnie przekaż pierwszy wyeksportowany plik (XML) zaufanej domeny publikacji, korzystając z polecenia cmdlet [Import-AadrmTpd](https://msdn.microsoft.com/library/dn857523.aspx). Jeśli masz więcej niż jeden plik XML z powodu użycia wielu zaufanych domen publikacji, wybierz plik zawierający wyeksportowaną zaufaną domenę publikacji odpowiadającą kluczowi HSM, który chcesz zastosować w usłudze Azure RMS do ochrony zawartości po migracji. 
    
    Aby uruchomić to polecenie cmdlet, wymagany jest adres URL dla klucza zidentyfikowany w poprzednim kroku.
    
    Przykładowo, używając naszej wartości adresu URL klucza z poprzedniego kroku i pliku TPD C:\contoso-tpd1.xml, należy uruchomić następujące polecenie:
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```
    
    Po wyświetleniu monitu wprowadź określone wcześniej hasło i potwierdź, że chcesz wykonać tę akcję.

2.  Po zakończeniu wykonywania polecenia powtórz krok 1 dla każdego z pozostałych plików XML, który został utworzony przez wyeksportowanie zaufanej domeny publikacji. Na przykład po uaktualnieniu klastra usług AD RMS dla trybu kryptograficznego 2 powinien być dostępny przynajmniej jeden dodatkowy plik do zaimportowania. Dla tych plików ustaw opcję **-Active** na wartość **false** podczas uruchamiania polecenia Import.  

3.  Użyj polecenia cmdlet [Disconnect-AadrmService](https://msdn.microsoft.com/library/azure/dn629416.aspx), aby zakończyć połączenie z usługą Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Jeśli chcesz później potwierdzić, którego klucza używa Twój klucz dzierżawy usługi Azure Rights Management w usłudze Azure Key Vault, użyj polecenia cmdlet usługi Azure RMS [Get-AadrmKeys](https://msdn.microsoft.com/library/dn629420.aspx).

Teraz możesz wykonać [Krok 3. Aktywowanie dzierżawy usługi Azure Information Protection](migrate-from-ad-rms-phase1.md#step-3-activate-your-azure-information-protection-tenant).




<!--HONumber=Nov16_HO4-->


