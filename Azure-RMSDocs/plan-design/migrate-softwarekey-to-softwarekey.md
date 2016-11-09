---
title: Krok 2&colon; Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie | Azure Information Protection
description: "Instrukcje będące częścią ścieżki migracji z usługi AD RMS do usługi Azure Information Protection, stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez oprogramowanie, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez oprogramowanie."
author: cabailey
manager: mbaldwin
ms.date: 11/03/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1fcebaaa2fbe1479e83c232d51013341977796fc
ms.openlocfilehash: 4a5e45bfef8e39d147410330b0d6b658c8d52474


---


# <a name="step-2-softwareprotected-key-to-softwareprotected-key-migration"></a>Krok 2. Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Te instrukcje są częścią [ścieżki migracji z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) i są stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez oprogramowanie, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez oprogramowanie. 

Jeśli nie jest to wybrany scenariusz konfiguracji, wróć do [Kroku 2. Eksportowanie danych konfiguracji z usługi AD RMS i importowanie ich do usługi Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) i wybierz inną konfigurację.

Wykonaj poniższe kroki, które umożliwiają zaimportowanie konfiguracji usługi AD RMS do usługi Azure Information Protection i zastosowanie w ten sposób klucza dzierżawy usługi Azure Information Protection zarządzanego przez firmę Microsoft.

## <a name="to-import-the-configuration-data-to-azure-information-protection"></a>Importowanie danych konfiguracji do usługi Azure Information Protection

1.  Na połączonej z Internetem stacji roboczej pobierz i zainstaluj moduł Windows PowerShell dla usługi Azure Rights Management (wersja minimalna: 2.5.0.0), który zawiera polecenie cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx). Usługa Azure Rights Management (Azure RMS) udostępnia usługę ochrony dla usługi Azure Information Protection.

    > [!TIP]
    > Jeśli moduł został wcześniej pobrany i zainstalowany, sprawdź numer wersji, uruchamiając polecenie: `(Get-Module aadrm -ListAvailable).Version`

    Instrukcje instalacji znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

2.  Uruchom program Windows PowerShell przy użyciu opcji **Uruchom jako administrator**, a następnie uruchom polecenie cmdlet [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx), aby nawiązać połączenie z usługą Azure RMS:

    ```
    Connect-AadrmService
    ```
    Po wyświetleniu monitu wprowadź poświadczenia administratora dzierżawy usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (zazwyczaj jest używane konto administratora globalnego usługi Azure Active Directory lub Office 365).

3.  Użyj polecenia cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx), aby przekazać pierwszy wyeksportowany plik (XML) zaufanej domeny publikacji. Jeśli masz więcej niż jeden plik XML z powodu użycia wielu zaufanych domen publikacji, wybierz plik zawierający wyeksportowaną zaufaną domenę publikacji, którą chcesz zastosować w usłudze Azure Information Protection do ochrony zawartości po migracji. Użyj następującego polecenia:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword <secure string> -Active $True -Verbose
    ```
    Aby określić hasło jako bezpieczny ciąg, można użyć jednego z dwóch poleceń [ConvertTo-SecureString -AsPlaintext](https://technet.microsoft.com/library/hh849818.aspx) lub [Read-Host](https://technet.microsoft.com/library/hh849945.aspx). Jeśli zdecydujesz się użyć polecenia ConvertTo-SecureString i hasło zawiera znaki specjalne, wprowadź hasło między apostrofy lub użyj znaków ucieczki.
    
    Na przykład: najpierw uruchom polecenie **$TPD_Password = Read-Host -AsSecureString** i wprowadź hasło określone wcześniej. Następnie uruchom polecenie **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Active $true -Verbose**. Po wyświetleniu monitu potwierdź chęć wykonania tej akcji.
    
4.  Po zakończeniu wykonywania polecenia powtórz krok 3 dla każdego z pozostałych plików XML, które zostały utworzone przez wyeksportowanie zaufanej domeny publikacji. Dla tych plików ustaw opcję **-Active** na wartość **false** podczas uruchamiania polecenia Import. Na przykład: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword $TPD_Password -Active $false -Verbose**

5.  Użyj polecenia cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx), aby zakończyć połączenie z usługą Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```


Teraz możesz wykonać [Krok 3. Aktywowanie dzierżawy usługi Azure Information Protection](migrate-from-ad-rms-phase1.md#step-3-activate-your-azure-information-protection-tenant).





<!--HONumber=Nov16_HO1-->


