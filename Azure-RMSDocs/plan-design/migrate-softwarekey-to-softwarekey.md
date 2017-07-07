---
title: "Migrowanie klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie — AIP"
description: "Instrukcje będące częścią ścieżki migracji z usługi AD RMS do usługi Azure Information Protection, stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez oprogramowanie, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez oprogramowanie."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: bc87379406d45f3fb39cae214839e127f71a366f
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="step-2-software-protected-key-to-software-protected-key-migration"></a>Krok 2. Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Te instrukcje są częścią [ścieżki migracji z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) i są stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez oprogramowanie, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez oprogramowanie. 

Jeśli nie jest to wybrany scenariusz konfiguracji, wróć do [Kroku 4. Eksportowanie danych konfiguracji z usługi AD RMS i importowanie ich do usługi Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) i wybierz inną konfigurację.

Wykonaj poniższe kroki, które umożliwiają zaimportowanie konfiguracji usługi AD RMS do usługi Azure Information Protection i zastosowanie w ten sposób klucza dzierżawy usługi Azure Information Protection zarządzanego przez firmę Microsoft.

## <a name="to-import-the-configuration-data-to-azure-information-protection"></a>Importowanie danych konfiguracji do usługi Azure Information Protection

1. Na stacji roboczej podłączonej do Internetu użyj polecenia cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice), aby połączyć się z usługą Azure Rights Management:

    ```
    Connect-AadrmService
    ```
    Po wyświetleniu monitu wprowadź poświadczenia administratora dzierżawy usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (zazwyczaj jest używane konto administratora globalnego usługi Azure Active Directory lub Office 365).

2. Użyj polecenia cmdlet [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd), aby przekazać każdy wyeksportowany plik XML zaufanej domeny publikacji. Na przykład po uaktualnieniu klastra usług AD RMS dla trybu kryptograficznego 2 powinien być dostępny przynajmniej jeden dodatkowy plik do zaimportowania. 
    
    Do uruchomienia tego polecenia cmdlet konieczne będzie hasło, które zostało określone wcześniej dla każdego pliku danych konfiguracji. 
    
    Na przykład — uruchom najpierw następujące polecenie, aby zapisać hasło:
    
        $TPD_Password = Read-Host -AsSecureString
    
    Wprowadź określone wcześniej hasło, aby wyeksportować pierwszy plik danych konfiguracji. Następnie korzystając z pliku E:\contosokey1.xml jako przykładu dla tego pliku konfiguracji, uruchom następujące polecenie i potwierdź wykonanie tej akcji:
    ```
    Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Verbose
    ```
    
3. Po przesłaniu każdego pliku uruchom polecenie [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties), aby zidentyfikować importowany klucz pasujący do aktualnie aktywnego klucza certyfikatu licencjodawcy serwera w usłudze AD RMS. Ten klucz będzie aktywnym kluczem dzierżawcy w usłudze Azure Rights Management.

4.  Użyj polecenia cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice), aby zakończyć połączenie z usługą Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```

Teraz możesz wykonać [Krok 5. Aktywuj usługę Azure Rights Management](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

