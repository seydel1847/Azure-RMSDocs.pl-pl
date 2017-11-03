---
title: "Zainstaluj klienta usługi Azure Information Protection dla użytkowników"
description: "Instrukcje i informacje dla administratorów do wdrażania klienta usługi Azure Information Protection dla systemu Windows w sieciach firmowych."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ea3ec965-3720-4614-8564-3ecfe60bc175
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 675afc962da542a03b90bea2dcb5d004829e361a
ms.sourcegitcommit: 832d3ef5f9c41d6adb18a8cf5304f6048cc7252e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="admin-guide-install-the-azure-information-protection-client-for-users"></a>Podręcznik administratora: Zainstaluj klienta usługi Azure Information Protection dla użytkowników

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Przed zainstalowaniem klienta usługi Azure Information Protection w sieci przedsiębiorstwa, sprawdź, czy komputery mają wymagane wersje systemu operacyjnego i aplikacji usługi Azure Information Protection: [wymagania dotyczące informacji o Azure Ochrona](../get-started/requirements-azure-rms.md). 

Następnie należy sprawdzić dodatkowe wymagania wstępne, które mogą być wymagane dla klienta usługi Azure Information Protection, zgodnie z opisem w następnej sekcji. Nie wszystkie wymagania wstępne nie zaznaczono przez program instalacyjny.

## <a name="additional-prerequisites-for-the-azure-information-protection-client"></a>Dodatkowe wymagania wstępne dla klienta usługi Azure Information Protection

- Microsoft .NET Framework 4.6.2
    
    Do zainstalowania pełnej wersji klienta usługi Azure Information Protection jest domyślnie wymagany program Microsoft .NET Framework w wersji 4.6.2 lub wyższej. W przypadku jego braku Instalator spróbuje pobrać i zainstalować ten wymagany program. Jeśli ten wymagany program jest instalowany w ramach instalacji klienta, należy uruchomić ponownie komputer. Chociaż nie jest to zalecane, można pominąć to wymaganie wstępne, korzystając z [parametru instalacji niestandardowej](#more-information-about-the-downgradedotnetrequirement-installation-parameter).

- Microsoft .NET Framework 4.5.2
    
    Jeśli przeglądarka usługi Azure Information Protection jest instalowana oddzielnie, wymagany jest program Microsoft .NET Framework w wersji 4.5.2 lub wyższej. W przypadku jego braku Instalator nie pobierze i nie zainstaluje tego programu.

- Wersja 4.0 programu Windows PowerShell
    
    Moduł PowerShell dla klienta wymaga środowiska Windows PowerShell w wersji 4.0, co może powodować konieczność zainstalowania go w starszych systemach operacyjnych. Aby uzyskać więcej informacji, zobacz artykuł [How to Install Windows PowerShell 4.0](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx) (Jak zainstalować program Windows PowerShell 4.0). Instalator nie sprawdza ani nie instaluje tego wymagania wstępnego. Aby sprawdzić, która wersja programu Windows PowerShell jest używana, wpisz polecenie `$PSVersionTable` w sesji programu PowerShell.

- Asystent logowania w Usługach online firmy Microsoft 7.250.4303.0
    
    Komputery z pakietem Office 2010 wymagają Asystenta logowania w Usługach online firmy Microsoft w wersji 7.250.4303.0. Ta wersja jest dołączana do pakietu instalacji klienta. Jeśli masz Asystenta logowania w nowszej wersji, należy go odinstalować przed zainstalowaniem klienta usługi Azure Information Protection. Na przykład sprawdź wersję i odinstaluj Asystenta logowania, wybierając opcje **Panel sterowania** > **Programy i funkcje** > **Odinstaluj lub zmień program**.

- Aktualizacja KB 2533623
    
    Komputery z systemem Windows 7 z dodatkiem Service Pack 1 wymagają aktualizacji KB 2533623. Aby uzyskać więcej informacji o tej aktualizacji, zobacz temat [Microsoft Security Advisory: Załadowanie niezabezpieczonej biblioteki umożliwia zdalne wykonywanie kodu](https://support.microsoft.com/en-us/kb/2533623). Tę aktualizację można zainstalować bezpośrednio lub może ona zostać zastąpiona przez inną aktualizację, która zainstaluje ją automatycznie.
    
    Jeśli ta aktualizacja jest wymagana i nie została zainstalowana, instalator klienta wyświetla ostrzeżenie z informacją, że należy ją zainstalować. Tę aktualizację można zainstalować po zainstalowaniu klienta, ale niektóre czynności zostaną zablokowane i ponownie pojawi się komunikat.  

- Nie należy wyłączać dodatku **Microsoft Azure Information Protection** dla aplikacji pakietu Office
    
    Jeśli skonfigurowano ustawienie zasad grupy **Lista zarządzanych dodatków**, dodaj dodatek Microsoft Azure Information Protection dla aplikacji pakietu Office, określając następujące identyfikatory programowe (ProgID) dla usługi Azure Information Protection, a następnie ustaw opcję na wartość **1: Dodatek jest zawsze włączony**.
    
    - Dla programu Outlook: `MSIP.OutlookAddin`
    
    - Dla programu Word: `MSIP.WordAddin`
    
    - Dla programu Excel: `MSIP.ExcelAddin`
    
    - Dla programu PowerPoint: `MSIP.PowerPointAddin`
    
    Nawet jeśli nie skonfigurowano tego ustawienia zasad grupy **Lista zarządzanych dodatków**, konieczne może być skonfigurowanie go w przypadku otrzymywania raportów, że dodatek Microsoft Azure Information Protection zostanie wyłączony. Gdy ten dodatek jest wyłączony, użytkownicy nie widzą paska usługi Azure Information Protection w aplikacji pakietu Office.
    
    Aby uzyskać więcej informacji na temat tego ustawienia zasad grupy, zobacz [No Add-ins loaded due to group policy settings for Office 2013 and Office 2016 programs](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off) (Brak załadowanych dodatków z powodu ustawień zasad grupy dla pakietów Office 2013 i Office 2016).

> [!IMPORTANT]
> Instalacja klienta usługi Azure Information Protection wymaga lokalnych uprawnień administracyjnych.


## <a name="options-to-install-the-azure-information-protection-client-for-users"></a>Opcje instalacji klienta usługi Azure Information Protection dla użytkowników

Istnieją trzy opcje instalacji klienta dla użytkowników:

**Windows Update**: klient usługi Azure Information Protection znajduje się również w wykazie usługi Microsoft Update, dzięki czemu można zainstalować i zaktualizować klienta przy użyciu dowolnej usługi aktualizacji oprogramowania korzystającej z wykazu.

**Uruchomienie pliku wykonywalnego (exe) klienta**: zalecana metoda instalacji, którą można uruchomić interaktywnie lub w trybie cichym. Ta metoda jest najbardziej elastyczna i jest metodą zalecaną, ponieważ Instalator sprawdza wiele wymagań wstępnych i może automatycznie zainstalować brakujące elementy. [Instrukcje](#to-install-the-azure-information-protection-client-by-using-the-executable-installer)

**Wdrażanie instalatora klienta systemu Windows (msi)** : obsługiwane w przypadku instalacji cichej wykorzystującej mechanizm wdrożenia centralnego, taki jak zasady grupy, program Configuration Manager i Microsoft Intune. Ta metoda jest niezbędna w przypadku komputerów z systemem Windows 10, które są zarządzane przez usługę Intune i aplikację MDM (Mobile Device Management), ponieważ dla tych komputerów pliki wykonywalne nie są obsługiwane przez instalację. Jednak w przypadku użycia tej metody instalacji należy ręcznie sprawdzić i zainstalować lub odinstalować oprogramowanie zależne, co w wypadku pliku wykonywalnego byłoby przeprowadzone przez instalator. [Instrukcje](#to-install-the-azure-information-protection-client-by-using-the-msi-installer)

### <a name="to-install-the-azure-information-protection-client-by-using-the-executable-installer"></a>Aby zainstalować klienta usługi Azure Information Protection dla użytkowników przy użyciu instalatora wykonywalnego

Użyj poniższych instrukcji, aby zainstalować klienta bez korzystania z katalogu aktualizacji Microsoft Update ani wdrażania pliku msi przy użyciu metody wdrażania centralnego, jak w przypadku usługi Intune.

1. Pobierz wersję wykonywalną klienta usługi Azure Information Protection z [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 
    
    Jeśli dostępna jest wersja zapoznawcza, zachowaj ją tylko do celów testowych. Nie jest ona przeznaczona dla użytkowników końcowych w środowisku produkcyjnym. 

2. W przypadku instalacji domyślnej wystarczy uruchomić plik wykonywalny, np. **AzInfoProtection.exe**. Jednak aby wyświetlić opcje instalacji, należy najpierw uruchomić plik wykonywalny z parametrem **/help**: `AzInfoProtection.exe /help`

    Przykład instalacji klienta w trybie dyskretnym: `AzInfoProtection.exe /quiet`
    
    Przykład instalacji jedynie poleceń cmdlet środowiska PowerShell w trybie dyskretnym: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
    
    Dodatkowe parametry, które nie są wymienione na ekranie pomocy:
    
    - **ServiceLocation**: użyj tego parametru, jeśli instalujesz klienta na komputerach z pakietem Office 2010, a użytkownicy nie są administratorami lokalnymi na swoich komputerach lub jeśli nie chcesz, aby użytkownicy otrzymywali monity. [Więcej informacji](#more-information-about-the-servicelocation-installation-parameter) 
    
    - **DowngradeDotNetRequirement**: użyj tego parametru, aby pominąć wymaganie wstępne dotyczące programu Microsoft .NET Framework w wersji 4.6.2. [Więcej informacji](#more-information-about-the-downgradedotnetrequirement-installation-parameter)
    
    - **AllowTelemetry=0**: użyj tego parametru, aby wyłączyć opcję instalacji **Pomóż ulepszyć usługę Azure Information Protection, wysyłając statystyki użycia do firmy Microsoft**. 
    
3. W przypadku instalacji interaktywnej wybierz opcję zainstalowania **zasad demonstracyjnych**, jeśli nie możesz nawiązać połączenia z usługą Office 365 lub Azure Active Directory, ale chcesz zobaczyć i wypróbować klienta usługi Azure Information Protection przy użyciu zasad lokalnych w celach demonstracyjnych. Gdy klient nawiąże połączenie z usługą Azure Information Protection, te zasady demonstracyjne zostaną zastąpione zasadami usługi Azure Information Protection obowiązującymi w organizacji.
    
4. Aby ukończyć instalację: 

    - Ponownie uruchom komputer, jeśli jest na nim zainstalowany pakiet Office 2010. 
        
        Jeśli klienta zainstalowano bez parametru ServiceLocation, przy pierwszym uruchomieniu dowolnej aplikacji pakietu Office korzystającej z paska usługi Azure Information Protection (na przykład Word) należy potwierdzić wszystkie monity o zaktualizowanie rejestru w związku z pierwszym uruchomieniem. Klucze rejestru są wypełniane przy użyciu [odnajdywania usług](../rms-client/client-deployment-notes.md#rms-service-discovery). 
    
    - W przypadku innych wersji pakietu Office należy uruchomić ponownie wszystkie aplikacje pakietu Office i wszystkie wystąpienia Eksploratora plików. 
        
5. Aby potwierdzić, że instalacja zakończyła się pomyślnie, sprawdź plik dziennika instalacji, który domyślnie jest tworzony w folderze %temp%. Można zmienić tę lokalizację z użyciem parametru instalacji **/log**. 
 
    Ten plik ma następujący format nazwy: `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`
    
    Na przykład: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP. Setup.Main.msi.log**
    
    W tym pliku dziennika wyszukaj następujący ciąg: **Product: Microsoft Azure Information Protection -- Installation completed successfully.** (Produkt: Microsoft Azure Information Protection — Instalacja została pomyślnie ukończona). Jeśli instalacja nie powiodła się, ten plik dziennika zawiera szczegółowe informacje ułatwiające identyfikację i rozwiązywanie problemów.

#### <a name="more-information-about-the-servicelocation-installation-parameter"></a>Więcej informacji na temat parametru instalacji ServiceLocation

W przypadku instalowania klienta dla użytkowników pakietu Office 2010 nieposiadających lokalnych uprawnień administracyjnych należy określić parametr ServiceLocation i adres URL usługi Azure Rights Management. Te parametr i wartość tworzą oraz ustawiają następujące klucze rejestru:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

Zidentyfikuj wartość do określenia dla parametru ServiceLocation, wykonując następującą procedurę. 

##### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>Aby zidentyfikować wartość do określenia dla parametru ServiceLocation

1. Z poziomu sesji programu PowerShell najpierw uruchom polecenie [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice) i określ poświadczenia administratora, aby nawiązać połączenie z usługą Azure Rights Management. Następnie uruchom polecenie [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration). 
 
    Jeśli jeszcze nie zainstalowano modułu programu PowerShell dla usługi Azure Rights Management, zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

2. Opierając się na danych wyjściowych, zidentyfikuj wartość **LicensingIntranetDistributionPointUrl**.

    Na przykład: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. Usuń element **/_wmcs/licensing** z tego ciągu. Na przykład: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    Wynikowy ciąg jest wartością do określenia dla parametru ServiceLocation.

Przykład instalacji klienta w trybie dyskretnym dla pakietu Office 2010 i usługi Azure RMS: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


#### <a name="more-information-about-the-downgradedotnetrequirement-installation-parameter"></a>Więcej informacji na temat parametru instalacji DowngradeDotNetRequirement

Aby umożliwić obsługę automatycznych uaktualnień z użyciem usługi Windows Update oraz niezawodną integrację z aplikacjami pakietu Office, klient usługi Azure Information Protection korzysta z programu Microsoft .NET Framework w wersji 4.6.2. Podczas instalacji ma domyślnie miejsce sprawdzenie dostępności tej wersji, a w przypadku jej braku — próba jej instalacji. Następnie instalacja wymaga ponownego uruchomienia komputera.

Jeśli zainstalowanie nowszej wersji programu Microsoft .NET Framework nie jest możliwe, można zainstalować klienta z uwzględnieniem parametru i wartości **DowngradeDotNetRequirement=True**, co spowoduje pominięcie tego wymagania w przypadku, gdy na komputerze jest zainstalowany program Microsoft .NET Framework w wersji 4.5.1.

Na przykład: `AzInfoProtection.exe DowngradeDotNetRequirement=True`

Firma Microsoft zaleca zachowanie ostrożności przy stosowaniu tego parametru i używanie go ze świadomością, że są zgłaszane problemy z aplikacjami pakietu Office, które zawieszają się w przypadku użycia klienta usługi Azure Information Protection w połączeniu ze starszą wersją programu Microsoft .NET Framework. Jeśli aplikacje zaczną się zawieszać, uaktualnij program do zalecanej wersji przed zastosowaniem innych sposobów mających na celu rozwiązanie problemu. 

Pamiętaj również, że w przypadku użycia usługi Windows Update do uaktualniania klienta usługi Azure Information Protection konieczne będzie zastosowanie innego mechanizmu wdrażania oprogramowania w celu uaktualnienia klienta do nowszej wersji.

### <a name="to-install-the-azure-information-protection-client-by-using-the-msi-installer"></a>Jak zainstalować klienta usługi Azure Information Protection dla użytkowników przy użyciu instalatora msi

W przypadku wdrożenia centralnego skorzystaj z poniższych informacji, które są specyficzne dla instalacji wersji msi klienta usługi Azure Information Protection. 

Jeśli metoda wdrażania oprogramowania korzysta z oprogramowania Intune, użyj tych instrukcji razem z informacjami z sekcji [Dodawania aplikacji przy użyciu usługi Intune](/intune/deploy-use/add-apps).

1. Pobierz wersję msi klienta usługi Azure Information Protection z [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 
    
    Jeśli dostępna jest wersja zapoznawcza, zachowaj ją tylko do celów testowych. Nie jest ona przeznaczona dla użytkowników końcowych w środowisku produkcyjnym. 

2. Upewnij się, że następujące zależności oprogramowania zostały spełnione dla każdego komputera, na którym będzie uruchamiany plik msi. Na przykład umieść w pakiecie poniższe oprogramowanie razem z wersją msi klienta lub wdrażaj ją wyłącznie na komputerach, które spełniają te zależności:
    
    |Wersja pakietu Office|System operacyjny|Oprogramowanie|Akcja|
    |--------------------|--------------|----------------|---------------------|
    |Office 2016|Wszystkie obsługiwane wersje|64-bitowe: [KB317866](https://www.microsoft.com/en-us/download/details.aspx?id=55073)<br /><br />32-bitowe: [KB317866](https://www.microsoft.com/en-us/download/details.aspx?id=55058)<br /><br /> Wersja: 1.0|Instalowanie|
    |Office 2013|Wszystkie obsługiwane wersje|64-bitowe: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54992)<br /><br /> 32-bitowe: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54979) <br /><br />Wersja: 1.0|Instalowanie|
    |Pakiet Office 2010|Wszystkie obsługiwane wersje|[Asystent logowania w Usługach online firmy Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=28177)<br /><br /> Wersja: 2.1|Instalowanie|
    |Pakiet Office 2010|Windows 8.1 i Windows Server 2012 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Numer wersji uwzględniony w nazwie pliku: v3|Zainstaluj Jeśli KB2843630 lub KB2919355 nie jest zainstalowana.|
    |Pakiet Office 2010|Windows 8 i Windows Server 2012|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Numer wersji uwzględniony w nazwie pliku: v3|Instalowanie|
    |Pakiet Office 2010|Windows 7|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41709)<br /><br /> Numer wersji uwzględniony w nazwie pliku: v3|Zainstaluj Jeśli KB3125574 nie jest zainstalowana.|
    |Nie dotyczy|Windows 7|KB2627273 <br /><br /> Numer wersji uwzględniony w nazwie pliku: v4|Odinstalowanie|
    

3. W przypadku instalacji domyślnej uruchom plik msi z parametrem **/quiet**, na przykład `AzInfoProtection.msi /quiet`. Jednak może okazać się konieczne określenie dodatkowych parametrów instalacji, które są udokumentowane w [instrukcjach Instalatora wykonywalnego](#to-install-the-azure-information-protection-client-by-using-the-executable-installer).  


## <a name="how-to-install-the-azure-information-protection-scanner"></a>Jak zainstalować skaner usługi Azure Information Protection

Bieżąca wersja klienta usługi Azure Information Protection zawiera skanera usługi Azure Information Protection. Moduł programu PowerShell, który jest dołączana do klienta zawiera polecenia cmdlet, aby zainstalować i skonfigurować skanera.

Aby zainstalować klienta skanera, wykonaj instrukcje sam w poprzednich sekcjach. Należy pamiętać, że jeśli nie potrzebujesz wszystkich składników klienta, takich jak dodatku pakietu Office oraz przeglądarkę, można zainstalować tylko moduł programu PowerShell. Na przykład można uruchomić plik wykonywalny z `PowerShellOnly=true /quiet`.

Po zainstalowaniu klienta, możesz następnie zainstalować skanera. Aby uzyskać instrukcje, zobacz [wdrażanie usługi Azure Information Protection skanera można automatycznie klasyfikować i chronić pliki](../deploy-use/deploy-aip-scanner.md).


## <a name="next-steps"></a>Następne kroki
Po zainstalowaniu klienta usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:

- [Dostosowania](client-admin-guide-customizations.md)

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]