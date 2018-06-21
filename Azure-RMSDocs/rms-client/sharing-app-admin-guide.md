---
title: Przewodnik administratora aplikacji RMS sharing — AIP
description: Instrukcje i informacje dla administratorów sieci przedsiębiorstwa odpowiedzialnych za wdrażanie aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management w systemie Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/27/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e1f3520a74b3ae57984e635ca68ba429dd6ad131
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
ms.locfileid: "30208553"
---
# <a name="rights-management-sharing-application-administrator-guide"></a>Przewodnik administratora aplikacji do udostępniania usługi Rights Management

>*Dotyczy: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

> [!IMPORTANT]
> **Powiadomienie o zakończeniu świadczenia pomocy technicznej**: aplikację RMS sharing dla systemu Windows zastąpi [klient usługi Azure Information Protection](aip-client.md). Pomoc techniczna dla starszych aplikacji spowoduje zatrzymanie 31 stycznia 2019. 

Poniższe informacje przydadzą się osobom odpowiedzialnym za aplikację do udostępniania usługi Microsoft Rights Management w sieci przedsiębiorstwa lub chcącym uzyskać więcej informacji technicznych niż jest dostępnych w artykułach [Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md) lub [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Microsoft Rights Management dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=303971).

Aplikacja RMS sharing najbardziej nadaje się do współpracy z usługą Azure Information Protection, ponieważ konfiguracja wdrożenia obsługuje wysyłanie chronionych załączników do użytkowników w innej organizacji, a także takie opcje jak powiadomienia e-mail i śledzenie dokumentów oraz odwoływanie dostępu do nich. Z pewnymi ograniczeniami współdziała również z lokalną wersją usług AD RMS. Obszerne porównanie funkcji obsługiwanych przez usługi Azure Information Protection i AD RMS można znaleźć w artykule [Porównanie usług Azure Information Protection i AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). Jeśli korzystasz z usług AD RMS i chcesz przeprowadzić migrację do usługi Azure Information Protection, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

Aby zapoznać się z przeglądem technicznym aplikacji usługi Rights Management, uzyskać informacje o natywnym i ogólnym poziomie ochrony, obsługiwanych typach plików i rozszerzeniach nazw plików oraz sposobach zmiany domyślnego poziomu ochrony, zobacz [Przegląd techniczny aplikacji do udostępniania usługi Microsoft Rights Management](sharing-app-admin-guide-technical.md). 

## <a name="automatic-deployment-for-the-microsoft-rights-management-sharing-application"></a>Automatyczne wdrażanie aplikacji do udostępniania usługi Microsoft Rights Management
Wersja aplikacji RMS sharing obsługuje instalację skryptową, dzięki czemu ta aplikacja nadaje się do wdrożeń w przedsiębiorstwie.

Jedynym wymaganiem w przypadku tej instalacji jest zainstalowanie na komputerach systemu Windows 7 z dodatkiem Service Pack 1 (lub nowszego) oraz oprogramowania Microsoft Framework w wersji 4.0 lub nowszej. Jeśli musisz zainstalować program Microsoft .NET Framework 4.0, możesz [go pobrać z Centrum pobierania Microsoft w celu instalacji](http://www.microsoft.com/download/details.aspx?id=17718).

### <a name="to-download-the-rms-sharing-application-for-automatic-deployment"></a>Aby pobrać aplikację RMS sharing do automatycznego wdrożenia

1.  Przejdź do strony [aplikacji do udostępniania usługi Microsoft Rights Management dla systemu Windows](http://www.microsoft.com/download/details.aspx?id=40857) w Centrum pobierania Microsoft, a następnie kliknij przycisk **Pobierz**.

2.  Wybierz i pobierz potrzebne pliki. Istnieją dwa pakiety instalacyjne klienta: jeden dla 64-bitowej wersji systemu Windows (Microsoft Rights Management sharing application x64.zip) i drugi dla 32-bitowej wersji systemu Windows (Microsoft Rights Management sharing application x86.zip).

3.  Wypakuj pliki ze skompresowanych pakietów instalacyjnych, na przykład klikając je dwukrotnie. Następnie skopiuj wypakowane pliki do lokalizacji sieciowej, która jest dostępna dla komputerów klienckich.

Pakiety instalacyjne aplikacji RMS sharing obsługują różne scenariusze wdrażania i obejmuje następujące elementy:

|Opis|Scenariusz wdrożenia|
|---------------|-----------------------|
|Asystent logowania usługi online firmy Microsoft|Pakiet Office 2010 i usługa Azure Information Protection<br /><br />Pakiet Office 2013 i usługa Azure Information Protection, jeśli nie zainstalowano [aktualizacji pakietu Office 2013 z 9 czerwca 2015 r.](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Poprawka dla pakietu Office (KB 2596501)|Pakiet Office 2010 i usługa Azure Information Protection<br /><br />Pakiet Office 2010 i usługi Active Directory RMS|
|Poprawka umożliwiająca współdziałanie klienta 1.0 usługi AD RMS z usługą Azure Information Protection (KB 2843630)|Pakiet Office 2010 i usługa Azure Information Protection<br /><br />Pakiet Office 2010 i usługi Active Directory RMS|
|Klient usług AD RMS i aplikacja RMS sharing|Pakiet Office 2016 lub Office 2013 i usługa Azure Information Protection lub Active Directory RMS<br /><br />Pakiet Office 2010 i usługa Azure Information Protection<br /><br />Pakiet Office 2010 i usługi Active Directory RMS<br /><br />Tylko aplikacja RMS sharing i dodatek dla pakietu Office|
|Dodatek dla Wstążki pakietu Office|Pakiet Office 2016 lub Office 2013 i usługa Azure Information Protection lub Active Directory RMS<br /><br />Pakiet Office 2010 i usługa Azure Information Protection<br /><br />Pakiet Office 2010 i usługi Active Directory RMS<br /><br />Tylko aplikacja RMS sharing i dodatek dla pakietu Office|
|Narzędzie do przygotowywania usługi Active Directory Rights Management|Pakiet Office 2010 i usługa Azure Information Protection|
Poniższe procedury umożliwiają zidentyfikowanie poleceń wymaganych do wdrożenia aplikacji RMS sharing dotyczących następujących scenariuszy wdrażania:

-   **Pakiet Office 2016 lub Office 2013 i usługa Azure Information Protection lub Active Directory RMS**

    Użytkownicy korzystają z pakietu Office 2016 lub Office 2013, organizacja używa usługi Azure Information Protection lub Active Directory RMS, a użytkownicy współpracują z innymi organizacjami korzystającymi z usługi Azure Information Protection lub Active Directory RMS.

-   **Pakiet Office 2010 i usługa Azure Information Protection**

    Użytkownicy korzystają z pakietu Office 2010, organizacja używa usługi Azure Information Protection, a użytkownicy współpracują z innymi organizacjami korzystającymi z usługi Azure Information Protection lub Active Directory RMS.

-   **Pakiet Office 2010 i usługi Active Directory RMS**

    Użytkownicy korzystają z pakietu Office 2010, organizacja używa usługi AD RMS, a użytkownicy współpracują z innymi organizacjami korzystającymi z usługi Azure Information Protection.

-   **Tylko aplikacja do udostępniania usługi RMS i dodatek dla pakietu Office**

    Użytkownicy korzystają z pakietu Office 2016, Office 2013 lub Office 2010, organizacja używa usługi AD RMS, a użytkownicy nie muszą współpracować z innymi organizacjami korzystającymi z usługi Azure Information Protection. W ramach tej instalacji wystarczy zainstalować tylko aplikację do udostępniania i dodatek dla pakietu Office.

> [!NOTE]
> W tych scenariuszach w organizacji korzystającej z usługi AD RMS użytkownicy mogą odbierać zawartość chronioną od innych organizacji korzystających z usługi Azure Information Protection, ale nie mogą wysyłać zawartości chronionej do użytkowników w organizacji używającej usługi Azure Information Protection. Jeśli jednak organizacja korzysta z usługi Azure Information Protection, użytkownicy mogą wysyłać zawartość chronioną do innych organizacji i ją od nich odbierać.

Do ukończenia każdej procedury instalacji jest wymagane ponowne uruchomienie komputera. Możesz zainicjować automatyczne ponowne uruchomienie przy użyciu polecenia **shutdown /i**.

### <a name="to-deploy-the-rms-sharing-application-for-office-2016-or-office-2013-and-azure-information-protection-or-active-directory-rms"></a>Aby wdrożyć aplikację RMS sharing dla pakietu Office 2016 lub Office 2013 i usługi Azure Information Protection lub Active Directory RMS

-   Na każdym komputerze, na którym chcesz zainstalować aplikację RMS sharing i składniki pokrewne, uruchom następujące polecenie z podniesionymi uprawnieniami:

    ```
    setup.exe /s
    ```

Aby sprawdzić, czy instalacja przebiegła pomyślnie, zobacz sekcję [Sprawdzanie, czy instalacja przebiegła pomyślnie](#verifying-installation-success) w tym artykule.

### <a name="to-deploy-the-rms-sharing-application-for-office-2010-and-azure-information-protection"></a>Aby wdrożyć aplikację RMS sharing dla pakietu Office 2010 i usługi Azure Information Protection

1.  Musisz być administratorem globalnym usługi Office 365 lub dzierżawcy usługi Azure Active Directory, aby uzyskać adres URL usługi certyfikacji swojej organizacji, uruchamiając narzędzie do przygotowywania usługi Active Directory Rights Management. To narzędzie należy uruchomić tylko raz, na jednym komputerze. Adres URL usługi certyfikacji musi zostać użyty podczas instalacji aplikacji RMS sharing na każdym komputerze:

    1.  Zaloguj się na komputerze przy użyciu konta administratora lokalnego.

    2.  Na tym komputerze [pobierz i zainstaluj Asystenta logowania w witrynie Microsoft Online Services](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Uruchom poniższe polecenie, aby wyświetlić adres URL usługi certyfikacji, który możesz skopiować i zachować do użycia w kolejnym kroku:

        -   W 64-bitowym systemie Windows 8.1 i Windows 8:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   W 32-bitowym systemie Windows 8.1 i Windows 8:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   W 64-bitowym systemie Windows 7:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > To polecenie może spowodować wyświetlenie monitu o podanie poświadczeń dla systemu Azure. Monit zostanie wyświetlony, jeśli komputer nie jest przyłączony do domeny. Jeśli komputer będzie przyłączony do domeny, narzędzie może użyć buforowanych poświadczeń.

2.  Na każdym komputerze, na którym chcesz zainstalować aplikację udostępniania usługi RMS, uruchom jednorazowo następujące polecenie z podniesionymi uprawnieniami:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  Na każdym komputerze, na którym chcesz zainstalować aplikację udostępniania usługi RMS, każdy użytkownik tego komputera musi uruchomić następujące polecenie (nie są wymagane podniesione uprawnienia). Można to osiągnąć różnymi metodami, w tym prosząc użytkowników o uruchomienie polecenia (na przykład przez kliknięcie linku w wiadomości e-mail lub w portalu pomocy technicznej) lub dodając polecenie do skryptu logowania każdego użytkownika:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Aby sprawdzić, czy instalacja przebiegła pomyślnie, zobacz sekcję [Sprawdzanie, czy instalacja przebiegła pomyślnie](#verifying-installation-success) w tym artykule.

### <a name="to-deploy-the-rms-sharing-application-for-office-2010-and-active-directory-rms"></a>Aby wdrożyć aplikację do udostępniania usług RMS dla pakietu Office 2010 i usług Active Directory RMS

1.  Na każdym komputerze, na którym chcesz zainstalować aplikację RMS sharing, uruchom następujące polecenie z podniesionymi uprawnieniami:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  Na każdym komputerze, na którym chcesz zainstalować aplikację RMS sharing, użytkownicy muszą uruchomić następujące polecenia (podniesione uprawnienia nie są konieczne). Można to osiągnąć różnymi metodami, w tym prosząc użytkowników o uruchomienie polecenia (na przykład przez kliknięcie linku w wiadomości e-mail lub w portalu pomocy technicznej) albo dodając polecenie do skryptu logowania każdego użytkownika:

    -   W 64-bitowym systemie Windows 10, Windows 8.1 i Windows 8:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   W 32-bitowym systemie Windows 10, Windows 8.1 i Windows 8:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   W 64-bitowym systemie Windows 7:

            pushd x64\win7
            aadrmpep.exe /configureO2010
            popd

    -   W 32-bitowym systemie Windows 7:

            pushd x86\win7
            aadrmpep.exe /configureO2010
            popd


Aby sprawdzić, czy instalacja przebiegła pomyślnie, zobacz sekcję [Sprawdzanie, czy instalacja przebiegła pomyślnie](#verifying-installation-success) w tym artykule.

### <a name="to-install-the-rms-sharing-application-and-office-add-in-only"></a>Aby zainstalować tylko aplikację RMS sharing i dodatek dla pakietu Office

1.  Zainstaluj klienta usług AD RMS oraz aplikację RMS sharing przy użyciu następującego polecenia, określając istniejący folder w celu utworzenia pliku dziennika:

    -   W 64-bitowym systemie Windows:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   W 32-bitowym systemie Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Na przykład: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`
    
    Jeśli to polecenie nie powiedzie się pomyślnie uruchomić, nie zobaczysz jakiekolwiek komunikaty o błędach z powodu **/quiet** parametru. W celu ułatwienia rozwiązywania problemów w razie niepowodzenia instalacji należy ponownie uruchomić to polecenie bez parametru /quiet, aby komunikaty o błędach były widoczne.

2.  Zainstaluj dodatek pakietu Office przy użyciu następujących poleceń, określając istniejący folder w celu utworzenia pliku dziennika:

    -   W 64-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   W 32-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Na przykład: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`
    
    Jeśli to polecenie nie powiedzie się pomyślnie uruchomić, nie zobaczysz jakiekolwiek komunikaty o błędach z powodu **/quiet** parametru. W celu ułatwienia rozwiązywania problemów w razie niepowodzenia instalacji należy ponownie uruchomić to polecenie bez parametru /quiet, aby komunikaty o błędach były widoczne.

Aby sprawdzić, czy instalacja przebiegła pomyślnie, zobacz sekcję [Sprawdzanie, czy instalacja przebiegła pomyślnie](#verifying-installation-success) w tym artykule.

## <a name="verifying-installation-success"></a>Sprawdzanie, czy instalacja przebiegła pomyślnie
Korzystając z plików dzienników instalacji, możesz sprawdzić, czy instalacja przebiegła pomyślnie.

### <a name="to-verify-installation-success-for-the-rms-sharing-application-for-office-2016-or-office-2013-and-azure-information-protection-or-active-directory-rms"></a>Aby sprawdzić, czy instalacja aplikacji RMS sharing dla pakietu Office 2016 lub Office 2013 i usługi Azure Information Protection lub Active Directory RMS przebiegła pomyślnie

-   Aby sprawdzić, czy polecenie Setup.exe zostało pomyślnie uruchomione na każdym komputerze, poszukaj pliku dziennika instalacji **RMInstaller.log** w folderze *%temp%\RMS_installer_&lt;guid&gt;*, a następnie zidentyfikuj kod wyjścia.

    Kod wyjścia udanej instalacji ma wartość 0. Każda inna liczba oznacza, że instalacja nie powiodła się.

    Przykładowa nazwa pliku dziennika: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

### <a name="to-verify-installation-success-for-the-rms-sharing-application-for-office-2010-and-azure-information-protection"></a>Aby sprawdzić, czy instalacja aplikacji RMS sharing dla pakietu Office 2010 i usługi Azure Information Protection przebiegła pomyślnie

1.  Aby sprawdzić, czy polecenie Setup.exe zostało pomyślnie uruchomione na każdym komputerze, poszukaj pliku dziennika instalacji **RMInstaller.log** w folderze *%temp%\RMS_installer_&lt;guid&gt;*, a następnie zidentyfikuj kod wyjścia.

    Kod wyjścia udanej instalacji ma wartość 0. Każda inna liczba oznacza, że instalacja nie powiodła się.

    Przykładowa nazwa pliku dziennika: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Po udanym uruchomieniu polecenia RMSSetup.exe w folderze *%localappdata%\microsoft\drm* powinny zostać utworzone następujące pliki:

    -   CERT-Machine-2048.drm

    -   CERT-Machine.drm

    -   CLC-&#42;.drm

    -   GIC-&#42;.drm

    Przykładowy plik CLC-&#42;.drm:

    **CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf;k5b11;k4a10;kac15;k29b2b6980f4c}.drm**

### <a name="to-verify-installation-success-for-the-rms-sharing-application-for-office-2010-and-active-directory-rms"></a>Aby sprawdzić, czy udało się zainstalować aplikację RMS sharing dla pakietu Office 2010 i usług Active Directory RMS

1.  Aby sprawdzić, czy polecenie Setup.exe zostało pomyślnie uruchomione na każdym komputerze, poszukaj pliku dziennika instalacji w folderze *%temp%\RMS_installer_&lt;guid&gt;*, a następnie zidentyfikuj kod wyjścia.

    Kod wyjścia udanej instalacji ma wartość 0. Każda inna liczba oznacza, że instalacja nie powiodła się.

    Przykładowa nazwa pliku dziennika: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Aby sprawdzić, czy polecenie aadrmprep.exe zostało pomyślnie uruchomione na każdym komputerze, poszukaj w pliku dziennika instalacji następującego tekstu: **aadrmprep.exe exited with status SUCCESS** (program aadrmprep.exe zakończył działanie ze stanem POWODZENIE).

    > [!NOTE]
    > Czasami ta instalacja może zostać uruchomiona dwukrotnie — pierwsze wystąpienie nie powiedzie się, natomiast drugie zakończy się pomyślnie.

    Zmiany w rejestrze wprowadzone przez to narzędzie, które można sprawdzić ręcznie, są następujące:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @="&lt;adres_url_certyfikacji&gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser="&lt;użytkownik_domyślny&gt;"

### <a name="to-verify-installation-success-for-the-rms-sharing-application-and-office-add-in-only"></a>Aby sprawdzić, czy udało się zainstalować tylko aplikację RMS sharing i dodatek dla pakietu Office

1.  Aby sprawdzić, czy polecenie Setup_ipviewer.exe zostało pomyślnie uruchomione, poszukaj w pliku dziennika instalacji następującego tekstu: **Stan powodzenia lub błędu instalacji: 0**.

    Przykładowe wiersze z pomyślnej instalacji:

    **MSI (s) (F0:B8) [14:19:57:854]: Produkt: Active Directory Rights Management Services Client 2.1 -- Instalacja została ukończona pomyślnie.**

    **MSI (s) (F0:B8) [14:19:57:854]: Instalator Windows zainstalował produkt. Nazwa produktu: Active Directory Rights Management Services Client 2.1. Wersja produktu: 1.0.1179.1. Język produktu: 1033. Producent: Microsoft Corporation. Stan powodzenia lub błędu instalacji: 0.**

2.  Aby sprawdzić, czy dodatek dla pakietu Office został pomyślnie zainstalowany na każdym komputerze, poszukaj w pliku dziennika instalacji następującego tekstu: **Stan powodzenia lub błędu instalacji: 0**

    Przykładowe wiersze z pomyślnej instalacji:

    **MSI (s) (9C:88) [18:49:04:007]: Produkt: Microsoft RMS Office Addins -- Instalacja została ukończona pomyślnie.**

    **MSI (s) (9C:88) [18:49:04:007]: Instalator Windows zainstalował produkt. Nazwa produktu: Microsoft RMS Office Addins. Wersja produktu: 1.0.7. Język produktu: 1033. Producent: Microsoft. Stan powodzenia lub błędu instalacji: 0.**

## <a name="uninstall-commands"></a>Polecenia dezinstalacji
Nie wszystkie polecenia instalacji wymagane przez te wdrożenia obsługują polecenie dezinstalacji. Można odinstalować klienta usług AD RMS, aplikację do udostępniania i dodatek dla pakietu Office. W tym celu należy użyć następujących poleceń.

### <a name="to-uninstall-the-ad-rms-client-and-the-rms-sharing-application"></a>Aby odinstalować klienta usług AD RMS i aplikację do udostępniania usług RMS

-   Użyj następujących poleceń:

    -   W 64-bitowym systemie Windows:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   W 32-bitowym systemie Windows:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

### <a name="to-uninstall-the-office-add-in"></a>Aby odinstalować dodatek dla pakietu Office

-   Użyj następujących poleceń:

    -   W 64-bitowym systemie Windows:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   W 32-bitowym systemie Windows:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

## <a name="suppressing-automatic-updates"></a>Pomijanie aktualizacji automatycznych
Domyślnie użytkownicy są powiadamiani, jeśli jest dostępna nowsza wersja aplikacji RMS sharing. Jest wówczas wyświetlany monit o jej pobranie. To powiadomienie można pominąć, wykonując następującą zmianę w rejestrze:

1.  Przejdź do klucza **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** i utwórz nowy klucz o nazwie **RmsSharingApp**, jeśli jeszcze nie istnieje.

2.  Wybierz klucz **RmsSharingApp**, utwórz nową wartość DWORD ciągu **AllowUpdatePrompt** i ustaw wartość na **0**.

Ponieważ aplikacja RMS sharing nie jest obsługiwana przez program WSUS, warto przetestować każda nową wersję aplikacji RMS sharing przed wdrożeniem jej u wszystkich użytkowników. Można to zrobić w następujący sposób:

1.  Na wszystkich komputerach użytkowników uruchom skrypt powodujący pomijanie aktualizacji automatycznych. Nie uruchamiaj tego skryptu na komputerach używanych przez administratorów do testowania nowych wersji.

2.  Kiedy zostaje udostępniona nowa wersja, administratorzy pobierają ją i testują.

3.  Po ukończeniu testowania i rozwiązaniu ewentualnych problemów najnowszą wersję można wdrożyć u wszystkich użytkowników, korzystając z instrukcji wdrażania automatycznego dostępnych w tym podręczniku.

## <a name="azure-information-protection-only-configuring-document-tracking"></a>Tylko usługa Azure Information Protection: konfigurowanie śledzenia dokumentów
Jeśli Twoja [subskrypcja obejmuje obsługę śledzenia dokumentów](https://www.microsoft.com/cloud-platform/azure-information-protection-features), witryna śledzenia dokumentów jest domyślnie włączona dla wszystkich użytkowników w organizacji. Podczas śledzenia dokumentów pokazywane są informacje, takie jak adresy e-mail osób, które próbowały uzyskać dostęp do chronionych dokumentów udostępnionych przez użytkowników, czas podjęcia takich prób oraz lokalizacja tych osób. Jeśli wyświetlanie tych informacji jest w organizacji zabronione ze względu na wymagania ochrony prywatności, możesz wyłączyć dostęp do witryny śledzenia dokumentów za pomocą polecenia cmdlet [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature). W dowolnym momencie możesz ponownie włączyć dostęp do witryny za pomocą polecenia [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature) i sprawdzić, czy dostęp jest aktualnie włączony, czy wyłączony, za pomocą polecenia [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature).

Aby uruchomić te polecenia cmdlet, musisz mieć co najmniej wersję **2.3.0.0** modułu Azure Rights Management dla programu Windows PowerShell. Aby uzyskać instrukcje instalacji, zobacz [Instalowanie modułu programu PowerShell AADRM](../deploy-use/install-powershell.md).

> [!TIP]
> Jeśli moduł został wcześniej pobrany i zainstalowany, sprawdź numer wersji, uruchamiając polecenie: `(Get-Module aadrm –ListAvailable).Version`

Następujące adresy URL są używane do śledzenia dokumentów i muszą być dozwolone (można je na przykład dodać do zaufanych witryn w przypadku korzystania z programu Internet Explorer ze zwiększonymi zabezpieczeniami):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > Ten adres URL jest przeznaczony dla usługi Mapy Bing.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="tracking-and-revoking-documents-for-users"></a>Śledzenie i odwoływanie dokumentów dla użytkowników

Użytkownicy po zalogowaniu się do witryny śledzenia dokumentów mogą śledzić i odwoływać dokumenty, które udostępnili za pomocą aplikacji RMS sharing. Po zalogowaniu się jako administrator usługi Azure Information Protection (administrator globalny) możesz kliknąć ikonę administratora w prawym górnym rogu strony, aby przełączyć się do trybu administratora i wyświetlić dokumenty udostępnione przez użytkowników w organizacji.

Akcje wykonywane w trybie administratora są poddawane inspekcji i rejestrowane w plikach dziennika użycia. Musisz potwierdzić, aby kontynuować. Aby uzyskać więcej informacji na temat tego rejestrowania, zobacz następną sekcję.

W trybie administratora możesz wyszukiwać według użytkownika lub dokumentu. Wyszukiwanie według użytkownika umożliwia wyświetlenie wszystkich dokumentów udostępnionych przez określonego użytkownika. W przypadku wyszukiwania według dokumentu zostaną wyświetleni wszyscy użytkownicy w organizacji, którzy udostępnili dany dokument. Następnie możesz przejść do szczegółów wyników wyszukiwania, aby śledzić dokumenty udostępnione przez użytkowników i w razie potrzeby odwołać te dokumenty. 

Aby wyjść z trybu administratora, kliknij przycisk **X** obok pozycji **Wyjdź z trybu administratora**.

Aby uzyskać instrukcje dotyczące sposobu korzystania z witryny śledzenia dokumentów, zobacz sekcję [Śledzenie i odwoływanie dokumentów](sharing-app-track-revoke.md) w podręczniku użytkownika.



### <a name="usage-logging-for-the-document-tracking-site"></a>Rejestrowanie użycia dla witryny śledzenia dokumentów

Dwa pola w plikach dziennika użycia mają zastosowanie do śledzenia dokumentów: **AdminAction** i **ActingAsUser**.

**AdminAction** — to pole ma wartość true, gdy administrator używa witryny śledzenia dokumentów w trybie administratora, na przykład w celu odwołania dokumentu w imieniu użytkownika lub sprawdzenia, kiedy dokument został udostępniony. To pole jest puste w przypadku, gdy użytkownik loguje się do witryny śledzenia dokumentów.

**ActingAsUser** — jeśli pole AdminAction ma wartość true, to pole zawiera nazwę użytkownika, w imieniu którego administrator działa (wyszukiwanego użytkownika lub właściciela dokumentu). To pole jest puste w przypadku, gdy użytkownik loguje się do witryny śledzenia dokumentów. 

Istnieją również typy żądań, które rejestrują sposób, w jaki użytkownicy i administratorzy korzystają z witryny śledzenia dokumentu. Na przykład typ żądania **RevokeAccess** dotyczy sytuacji, gdy użytkownik lub administrator w imieniu użytkownika odwołał dokument w witrynie śledzenia dokumentów. Użyj tego typu żądania w połączeniu z polem AdminAction, aby określić, czy użytkownik odwołał własny dokument (pole AdminAction jest puste), czy też administrator odwołał dokument w imieniu użytkownika (pole AdminAction ma wartość true).


Aby uzyskać więcej informacji na temat rejestrowania użycia, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md)

## <a name="ad-rms-only-support-for-multiple-email-domains-within-your-organization"></a>Tylko usługi AD RMS: obsługa wielu domen poczty e-mail w danej organizacji
Jeśli korzystasz z usług AD RMS, a użytkownicy w Twojej organizacji mają adresy e-mail w kilku domenach (np. na skutek fuzji lub przejęcia), musisz wprowadzić następującą zmianę w rejestrze:

1.  Przejdź do klucza **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** i utwórz nowy klucz o nazwie **RmsSharingApp**, jeśli jeszcze nie istnieje.

2.  Wybierz klucz **RmsSharingApp**, utwórz nową wartość ciągu wielokrotnego o nazwie **FederatedDomains**, a następnie dodaj wszystkie domeny i domeny podrzędne używane w organizacji. Symbole wieloznaczne nie są obsługiwane.

    Na przykład: firma Coho Vineyard &amp; Winery ma standardową domenę poczty e-mail **cohovineyardandwinery.com**, ale na skutek fuzji korzysta również z domen poczty e-mail **cohowinery.com**, **eastcoast.cohowinery.com** i **cohovineyard**. Dla danych wartości **FederatedDomains** administrator wprowadza: **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

Jeśli nie wprowadzisz tej zmiany w rejestrze, użytkownicy mogą nie mieć możliwości korzystania z zawartości chronionej przez innych użytkowników w tej organizacji. W przypadku korzystania z usługi Azure Information Protection ta zmiana w rejestrze nie jest konieczna.


## <a name="next-steps"></a>Następne kroki
Aby uzyskać dodatkowe informacje techniczne, w których wyjaśniono różnice między poziomami ochrony (natywny i ogólny), obsługiwane typy plików i rozszerzenia nazw plików oraz sposób zmiany domyślnego poziomu ochrony, zobacz [Przegląd techniczny aplikacji do udostępniania usługi Rights Management](sharing-app-admin-guide-technical.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
