---
title: "Migrowanie klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie — AIP"
description: "Instrukcje będące częścią ścieżki migracji z usługi AD RMS do usługi Azure Information Protection, stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez oprogramowanie, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez oprogramowanie."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 60370cc34184b28f5cdecf6ad51f9ba58dd4816a
ms.sourcegitcommit: 77b0936bea2700eb12b580e5738e077d447d5686
translationtype: HT
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

2. Użyj polecenia cmdlet [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd), aby przekazać pierwszy wyeksportowany plik (XML) zaufanej domeny publikacji. Jeśli masz więcej niż jeden plik XML z powodu użycia wielu zaufanych domen publikacji, wybierz plik zawierający wyeksportowaną zaufaną domenę publikacji, którą chcesz zastosować w usłudze Azure Information Protection do ochrony zawartości po migracji. Użyj następującego polecenia:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword <secure string> -Active $True -Verbose
    ```
    Aby określić hasło jako bezpieczny ciąg, można użyć jednego z dwóch poleceń [ConvertTo-SecureString -AsPlaintext](https://technet.microsoft.com/library/hh849818.aspx) lub [Read-Host](https://technet.microsoft.com/library/hh849945.aspx). Jeśli zdecydujesz się użyć polecenia ConvertTo-SecureString i hasło zawiera znaki specjalne, wprowadź hasło między apostrofy lub użyj znaków ucieczki.
    
    Na przykład: najpierw uruchom polecenie **$TPD_Password = Read-Host -AsSecureString** i wprowadź hasło określone wcześniej. Następnie uruchom polecenie **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Active $true -Verbose**. Po wyświetleniu monitu potwierdź chęć wykonania tej akcji.
    
3.  Po zakończeniu wykonywania polecenia powtórz krok 3 dla każdego z pozostałych plików XML, które zostały utworzone przez wyeksportowanie zaufanej domeny publikacji. Na przykład po uaktualnieniu klastra usług AD RMS dla trybu kryptograficznego 2 powinien być dostępny przynajmniej jeden dodatkowy plik do zaimportowania. Dla tych plików ustaw opcję **-Active** na wartość **false** podczas uruchamiania polecenia Import. Na przykład: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword $TPD_Password -Active $false -Verbose**

4.  Użyj polecenia cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice), aby zakończyć połączenie z usługą Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```


Teraz możesz wykonać [Krok 5. Aktywowanie dzierżawy usługi Azure Information Protection](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

