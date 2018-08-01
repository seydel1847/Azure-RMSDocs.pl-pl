---
title: Uwagi dotyczące wdrażania klienta usługi RMS — Azure Information Protection
description: Informacje dotyczące ponownej instalacji, obsługiwanych systemów operacyjnych, ustawień rejestru i odnajdowania usług dla usługi Rights Management Service (klienta usługi RMS) w wersji 2, która jest również znana jako klient MSIPC.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/12/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 751f1a5bf2728a848bd450ce1081a15ea1e35456
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376590"
---
# <a name="rms-client-deployment-notes"></a>Uwagi dotyczące wdrażania klienta usługi RMS

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 7 z z dodatkiem SP1, systemu operacyjnego Windows 8, Windows 8.1, systemu Windows 10, Windows Server 2008 R2, systemu Windows Server 2012, Windows Server 2012 R2, Windows Server 2016*

Klient usługi Rights Management (klient usługi RMS) w wersji 2 jest także znany jako klient MSIPC. Jest to oprogramowanie przeznaczone dla komputerów z systemem Windows, które komunikuje się z usługą Microsoft Rights Management lokalnie lub w chmurze, aby ułatwić ochronę dostępu do informacji i ich użycia. Ochrona obejmuje przepływ informacji przez aplikacje i urządzenia w granicach organizacji lub poza zarządzanymi granicami. 

Klient usługi RMS jest dostarczany razem z [klientem usługi Azure Information Protection dla systemu Windows](aip-client.md). Jest również dostępny jako [opcjonalny plik do pobrania](http://www.microsoft.com/download/details.aspx?id=38396), który można — po potwierdzeniu i zaakceptowaniu umowy licencyjnej — za darmo rozpowszechniać za pomocą oprogramowania innych firm. Dzięki temu klienci mogą chronić i wykorzystywać zawartość chronioną przy użyciu usług Rights Management.


## <a name="redistributing-the-rms-client"></a>Dystrybucja klienta usługi RMS
Klient usługi RMS może być za darmo dystrybuowany i umieszczany w pakietach z innymi aplikacjami i rozwiązaniami IT. Jeśli jesteś deweloperem aplikacji lub dostawcą rozwiązań i chcesz dystrybuować klienta usługi RMS, masz dwie opcje:

- Zalecana: osadź instalatora klienta usługi RMS w instalacji aplikacji i uruchom go w trybie dyskretnym (przełącznik **/quiet** szczegółowo opisany w następnej sekcji).

- Ustaw klienta usługi RMS jako wymaganie wstępne aplikacji. W przypadku tej opcji może być konieczne udostępnienie użytkownikom dodatkowych instrukcji dotyczących uzyskiwania i instalowania klienta oraz aktualizowania komputerów przy jego użyciu przed rozpoczęciem korzystania z aplikacji.

## <a name="installing-the-rms-client"></a>Instalowanie klienta usługi RMS
Klient usługi RMS jest zawarty w wykonywalnym pliku Instalatora o nazwie **setup_msipc_*\<arch\>*.exe**, gdzie  *\<arch >* jest **x86** (dla 32-bitowych komputerów klienckich) lub **x64** (dla 64-bitowych komputerów klienckich). Pakiet instalatora wersji 64-bitowej (x64) instaluje zarówno plik wykonywalny 32-bitowego środowiska uruchomieniowego na potrzeby zachowania zgodności z 32-bitowymi aplikacjami działającymi w 64-bitowym systemie operacyjnym, jak i plik wykonywalny 64-bitowego środowiska uruchomieniowego do obsługi natywnych aplikacji 64-bitowych. Instalator 32-bitowych (x 86) nie działa w 64-bitowej instalacji Windows.

> [!NOTE]
> Do zainstalowania klienta usługi RMS wymagane są podniesione uprawnienia, np. członka grupy Administratorzy na komputerze lokalnym.

Klienta usługi RMS można zainstalować przy użyciu jednej z następujących metod instalacji:

- **Tryb dyskretny.** Używając przełącznika **/quiet** w opcjach wiersza polecenia, można zainstalować klienta usługi RMS na komputerach w trybie dyskretnym. W poniższym przykładzie przedstawiono instalację klienta usługi RMS w trybie dyskretnym na 64-bitowym komputerze klienckim:

    ```
    setup_msipc_x64.exe /quiet
    ```

- **Tryb interaktywny.** Alternatywnie można zainstalować klienta usługi RMS za pomocą graficznego interfejsu użytkownika Instalatora dostarczonego przez Kreatora instalacji klienta usługi RMS. Aby zainstalować interaktywnie, kliknij dwukrotnie pakiet Instalatora klienta RMS (**setup_msipc_*\<arch\>*.exe**) w folderze, do którego został skopiowany lub pobrany na lokalnym komputer.

## <a name="questions-and-answers-about-the-rms-client"></a>Pytania i odpowiedzi dotyczące klienta usługi RMS
Poniższa sekcja zawiera często zadawane pytania na temat klienta usługi RMS oraz odpowiedzi na nie.

### <a name="which-operating-systems-support-the-rms-client"></a>Które systemy operacyjne są obsługiwane przez klienta usługi RMS?
Klient usługi RMS jest obsługiwany w następujących systemach operacyjnych:

|System operacyjny Windows Server|Kliencki system operacyjny Windows|
|-----------------------------------|-----------------------------------|
|Windows Server 2016|Windows 10|
|Windows Server 2012 R2|Windows 8.1|
|Windows Server 2012|Windows 8|
|Windows Server 2008 R2|Windows 7 co najmniej z dodatkiem SP1|


### <a name="which-processors-or-platforms-support-the--rms-client"></a>Które procesory lub platformy obsługują klienta usługi RMS?
Klient usługi RMS jest obsługiwany na platformach obliczeniowych x86 i x64.

### <a name="where-is-the--rms-client-installed"></a>Gdzie jest instalowany klient usługi RMS?
Domyślnie klient usługi RMS jest zainstalowany w katalogu %ProgramFiles%\Active Directory Rights Management Services Client 2. \<podrzędny numer wersji >.

### <a name="what-files--are-associated-with-the-rms-client-software"></a>Które pliki są skojarzone z oprogramowaniem klienta usługi RMS?
Następujące pliki są instalowane jako część oprogramowania klienckiego usługi RMS:

-   Msipc.dll

-   Ipcsecproc.dll

-   Ipcsecproc_ssp.dll

-   MSIPCEvents.man

Oprócz wymienionych plików klient usługi RMS instaluje również pliki obsługi wielojęzycznego interfejsu użytkownika (MUI) w 44 językach. Aby sprawdzić listę obsługiwanych języków, uruchom instalację klienta usługi RMS i po jej zakończeniu przejrzyj zawartość folderów obsługi wielu języków w domyślnej ścieżce.

### <a name="is-the-rms-client-included-by-default-when-i-install-a-supported-operating-system"></a>Czy klient usługi RMS jest domyślnie uwzględniany podczas instalacji obsługiwanego systemu operacyjnego?
Nie. Ta wersja klienta usługi RMS jest dostarczana jako opcjonalny plik do pobrania, który można osobno instalować na komputerach z obsługiwanymi wersjami systemu operacyjnego Microsoft Windows.

### <a name="is-the-rms-client-automatically-updated-by-microsoft-update"></a>Czy klient usługi RMS jest automatycznie aktualizowany przy użyciu usługi Microsoft Update?
Jeśli ten klient usługi RMS został zainstalowany w trybie dyskretnym, dziedziczy bieżące ustawienia usługi Microsoft Update. Jeśli klient usługi RMS został zainstalowany za pomocą instalatora opartego na graficznym interfejsie użytkownika, kreator instalacji klienta usługi RMS monituje użytkownika o włączenie usługi Microsoft Update.

## <a name="rms-client-settings"></a>Ustawienia klienta usługi RMS
Poniższa sekcja zawiera informacje na temat ustawień klienta usługi RMS. Informacje te mogą być przydatne, jeśli masz problemy z aplikacjami lub usługami korzystającymi z klienta usługi RMS.

> [!NOTE]
> Niektóre ustawienia są zależne od tego, czy aplikacja obsługująca usługę RMS działa jako aplikacja w trybie klienta (np. programy Microsoft Word i Outlook lub klient usługi Azure Information Protection z Eksploratorem plików systemu Windows), czy aplikacja w trybie serwera (np. programy SharePoint i Exchange). W poniższych tabelach te ustawienia są identyfikowane odpowiednio jako **Tryb klienta** i **Tryb serwera**.

### <a name="where-the-rms-client-stores-licenses-on-client-computers"></a>Gdzie klient usługi RMS przechowuje licencje na komputerach klienckich
Klient usługi RMS przechowuje licencje na dysku lokalnym oraz buforuje niektóre informacje w rejestrze systemu Windows.

|Opis|Ścieżki trybu klienta|Ścieżki trybu serwera|
|---------------|---------------------|---------------------|
|Lokalizacja magazynu licencji|%localappdata%\Microsoft\MSIPC|%allusersprofile%\Microsoft\MSIPC\Server\\*\<SID\>*|
|Lokalizacja magazynu szablonów|%localappdata%\Microsoft\MSIPC\Templates|%allusersprofile%\Microsoft\MSIPC\Server\\*\<SID\>*|
|Lokalizacja w rejestrze|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> \Local Settings<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> \\*\<IDENTYFIKATOR SID*\>|

> [!NOTE]
> *\<Identyfikator SID*> to bezpieczny identyfikator (SID) dla konta, na którym działa aplikacja serwera. Na przykład, jeśli aplikacja jest uruchomiona w ramach wbudowane konto usługi sieciowej, należy zastąpić *\<SID\>* z wartością znanego identyfikatora SID dla tego konta (S-1-5-20).

### <a name="windows-registry-settings-for-the-rms-client"></a>Ustawienia rejestru systemu Windows klienta usługi RMS
Za pomocą kluczy rejestru systemu Windows można ustawić lub zmodyfikować niektóre konfiguracje klienta usługi RMS. Na przykład administrator aplikacji z obsługą usługi RMS, które komunikują się z serwerami AD RMS, może zaktualizować lokalizację usługi przedsiębiorstwa (zastąpić serwer usług AD RMS wybrany do użycia podczas publikowania) w zależności od aktualnej lokalizacji komputera klienckiego w topologii usługi Active Directory. Można też włączyć śledzenie usługi RMS na komputerze klienckim, aby ułatwić rozwiązywanie problemów dotyczących aplikacji obsługującej usługę RMS. Skorzystaj z poniższej tabeli, aby zidentyfikować ustawienia rejestru, które możesz zmieniać w przypadku klienta usługi RMS.

|Zadanie|Ustawienia|
|--------|------------|
|Jeśli klient jest w wersji 1.03102.0221 lub nowszej:<br /><br />**Aby kontrolować zbieranie danych aplikacji**|**Ważne**: Aby szanować prywatność użytkowników, przed włączeniem funkcji zbierania danych administrator musi poprosić użytkownika o zgodę.<br /><br />Jeśli włączysz funkcję zbierania danych, zgadzasz się na wysyłanie danych przez Internet do firmy Microsoft. Firma Microsoft używa tych danych do zapewniania i poprawiania jakości, bezpieczeństwa i integralności swoich produktów i usług. Na przykład firma Microsoft analizuje wydajność i niezawodność, takich jak jakich funkcji używasz, jak szybko funkcje reagują, wydajność urządzenia, interakcje z interfejsem użytkownika i wszelkie problemy, które wystąpią wraz z produktem. Dane obejmują także informacje o konfiguracji oprogramowania, takie jak oprogramowanie, które są aktualnie uruchomione i adres IP.<br /><br />Dla wersji 1.0.3356 lub nowszej: <br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft\MSIPC<br />REG_DWORD: DiagnosticAvailability<br /><br />Wersje przed 1.0.3356: <br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft\MSIPC<br />REG_DWORD: DiagnosticState<br /><br />**Wartość:** 0 dla aplikacji zdefiniowanej (domyślnie) za pomocą właściwości środowiska [IPC_EI_DATA_COLLECTION_ENABLED](https://msdn.microsoft.com/library/hh535247(v=vs.85).aspx), 1 dla opcji Wyłączone, 2 dla opcji Włączone<br /><br />**Uwaga**: Jeśli Twoja 32-bitowej aplikacji MSIPC działa w 64-bitowej wersji systemu Windows, lokalizacja jest HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC.|
|Tylko usługi AD RMS:<br /><br />**Aby zaktualizować lokalizację usługi przedsiębiorstwa dla komputera klienckiego**|Zaktualizuj następujące klucze rejestru:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />REG_SZ: domyślna<br /><br />**Wartość:**\<http lub https>://*nazwa _klastra_usługi_RMS*/_wmcs/Certification<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />REG_SZ: domyślna<br /><br />**Wartość:** \<http lub https>://*nazwa _klastra_usługi_RMS*/_wmcs/Licensing|
|**Aby włączyć lub wyłączyć śledzenie**|Zaktualizuj następujący klucz rejestru:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />REG_DWORD: Trace<br /><br />**Wartość:** 1 — włączenie śledzenia, 0 — wyłączenie śledzenia (wartość domyślna)|
|**Aby zmienić częstotliwość odświeżania szablonów w dniach**|Określ następujące wartości rejestru, jak często szablony odświeżenie na komputerze użytkownika, jeśli nie ustawiono wartości TemplateUpdateFrequencyInSeconds.  Jeśli żadna z tych wartości nie zostanie ustawiona, domyślnym interwałem odświeżania aplikacji za pomocą klienta usługi RMS (wersja 1.0.1784.0) w celu pobrania szablonów będzie 1 dzień. Wcześniejsze wersje ma wartość domyślna to 7 dni.<br /><br />**Tryb klienta:**<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: TemplateUpdateFrequency<br /><br />**Wartość:** wartość całkowita określająca liczbę dni (minimum 1) między pobraniami.<br /><br />**Tryb serwera:**<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\\<SID\><br />REG_DWORD: TemplateUpdateFrequency<br /><br />**Wartość:** wartość całkowita określająca liczbę dni (minimum 1) między pobraniami.|
|**Aby zmienić częstotliwość odświeżania szablonów w sekundach**<br /><br />Uwaga: Jeśli to ustawienie zostanie określone, tej wartości częstotliwość odświeżania szablonów w dniach jest ignorowana. Określ jedną z tych wartości, nie obydwie.|Określ następujące wartości rejestru, jak często szablony odświeżenie na komputerze użytkownika. Jeśli nie ustawiono tej wartości ani wartości zmiany częstotliwości w dniach (TemplateUpdateFrequency), domyślnym interwałem odświeżania aplikacji za pomocą klienta usługi RMS (wersja 1.0.1784.0) w celu pobrania szablonów będzie 1 dzień. Wcześniejsze wersje ma wartość domyślna to 7 dni.<br /><br />**Tryb klienta:**<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: TemplateUpdateFrequencyInSeconds<br /><br />**Wartość:** wartość całkowita określająca liczbę sekund (minimum 1) między pobraniami.<br /><br />**Tryb serwera:**<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\\<*SID*><br />REG_DWORD: TemplateUpdateFrequencyInSeconds<br /><br />**Wartość:** wartość całkowita określająca liczbę sekund (minimum 1) między pobraniami.|
|Tylko usługi AD RMS:<br /><br />**Aby pobierać szablony natychmiast po następnym żądaniu publikowania**|Na potrzeby operacji testowania i oceniania możesz wybrać opcję pobierania szablonów przy użyciu klienta usługi RMS tak szybko, jak to możliwe. W przypadku tej konfiguracji, a następnie pliki do pobrania szablony natychmiast po następnym publikowania żądania, zamiast czekać przez czas określony w ustawieniu rejestru TemplateUpdateFrequency Usuń następujący klucz rejestru, a klient usługi RMS:<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\\<*Server Name*>\Template <br /><br />**Uwaga**: klucz \<*Server Name*> może wskazywać zewnętrzny (corprights.contoso.com) i wewnętrzny (corprights) adres URL, więc wpisy mogą być dwa.|
|Tylko usługi AD RMS:<br /><br />**Aby włączyć obsługę uwierzytelniania federacyjnego**|Jeśli komputer kliencki usługi RMS łączy się z klastrem usług AD RMS za pomocą zaufania federacyjnego, należy skonfigurować obszar macierzysty federacji.<br /><br />HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />REG_SZ: FederationHomeRealm<br /><br />**Wartość:** wartość tego wpisu rejestru to identyfikator uniform resource identifier (URI) dla usługi federacyjnej (na przykład "http://TreyADFS.trey.net/adfs/services/trust").<br /><br /> **Uwaga**: Ważne jest, aby dla tej wartości podać protokół http, a nie https. Ponadto jeśli Twoja 32-bitowej aplikacji MSIPC działa w 64-bitowej wersji systemu Windows, lokalizacja jest następująca: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Federation. Konfigurację przykładową przedstawiono w temacie [Wdrażanie Usług Active Directory Rights Management z Usługami federacyjnymi Active Directory](https://technet.microsoft.com/library/dn758110.aspx).|
|Tylko usługi AD RMS:<br /><br />**Aby obsługiwać serwery federacyjne partnera wymagające uwierzytelniania opartego na formularzu do wprowadzenia danych przez użytkowników**|Domyślnie klient usługi RMS działa w trybie dyskretnym i użytkownik nie musi wprowadzać żadnych danych. Serwery federacyjne partnerów mogą być jednak skonfigurowane tak, aby wymagać wprowadzenia danych przez użytkownika, na przykład w ramach uwierzytelniania opartego na formularzu. W takim przypadku należy skonfigurować klienta usługi RMS, aby ignorował tryb dyskretny w celu umożliwienia wyświetlenia formularza uwierzytelniania federacyjnego w oknie przeglądarki na potrzeby uwierzytelniania użytkowników.<br /><br />HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />REG_DWORD: EnableBrowser<br /><br />**Uwaga**: jeśli serwer federacyjny został skonfigurowany do użycia uwierzytelniania opartego na formularzu, ten klucz jest wymagany. Jeśli serwer federacyjny jest skonfigurowany do korzystania ze zintegrowanego uwierzytelniania Windows, ten klucz nie jest wymagane.|
|Tylko usługi AD RMS:<br /><br />**Aby zablokować użycie usługi ILS**|Domyślnie klient usługi RMS obsługuje korzystanie z zawartości chronionej przez usługę ILS, można go jednak skonfigurować tak, aby blokował tę usługę, używając poniższego klucza rejestru. Jeśli ten klucz rejestru jest ustawiona na blokowanie usługi ILS, wszelkie próby otwarcia zawartości chronionej rzez usługę ILS zwraca następujący błąd:<br />HRESULT_FROM_WIN32(ERROR_ACCESS_DISABLED_BY_POLICY)<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: **DisablePassportCertification**<br /><br />**Wartość:** 1 — blokowanie użycia usługi ILS, 0 — zezwolenie na użycie usługi ILS (wartość domyślna)|

### <a name="managing-template-distribution-for-the-rms-client"></a>Zarządzanie dystrybucją szablonów dla klienta usługi RMS
Szablony ułatwiają użytkownikom i administratorom szybkie stosowanie ochrony usługi Rights Management, a klient usługi RMS automatycznie pobiera szablony z serwerów usługi RMS lub usług. Jeśli szablony zostaną umieszczone w poniższej lokalizacji folderu, klient usługi RMS nie pobierać szablonów z lokalizacji domyślnej i nie zamian pobierze szablony znajdujące się w tym folderze. Klient usługi RMS może kontynuować pobieranie z innych dostępnych serwerów usługi RMS.

**Tryb klienta:** %localappdata%\Microsoft\MSIPC\UnmanagedTemplates

**Tryb serwera:** %allusersprofile%\Microsoft\MSIPC\Server\UnmanagedTemplates\\*\<SID\>*

Jeśli korzystasz z tego folderu, nie trzeba używać specjalnej konwencji nazewnictwa. Szablony muszą jednak zostać wydane przez usługę lub serwer RMS, a wymagane rozszerzenie nazwy pliku to XML. Prawidłowe nazwy to na przykład Contoso-Confidential.xml lub Contoso-ReadOnly.xml.

## <a name="ad-rms-only-limiting-the-rms-client-to-use-trusted-ad-rms-servers"></a>Tylko usługi AD RMS: ograniczanie klienta usługi RMS do użycia zaufanych serwerów usług AD RMS
Klienta usługi RMS można ograniczyć tak, aby używał tylko określonych zaufanych serwerów usług AD RMS, wprowadzając poniższe zmiany do rejestru systemu Windows na komputerach lokalnych.

**Aby włączyć ograniczanie klienta usługi RMS tak, aby używał tylko zaufanych serwerów AD RMS**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
   
    REG_DWORD:AllowTrustedServersOnly
    
    **Wartość:** Jeśli określono wartość niezerową, klient usługi RMS zaufania tylko określonych serwerów, które są skonfigurowane w liście TrustedServers i usługę Azure Rights Management.

**Aby dodać elementy członkowskie do listy zaufanych serwerów usług AD RMS**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    
    REG_SZ:*\<URL_or_HostName>*
    
    **Wartość:** wartości ciągu w tej lokalizacji klucza rejestru mogą być albo format nazwy domeny DNS (na przykład **adrms.contoso.com**) lub pełne adresy URL zaufanych serwerów usług AD RMS (na przykład **https://adrms.contoso.com**). Jeśli określony adres URL rozpoczyna się od **https://**, klient usługi RMS używa protokołu SSL lub TLS do kontaktowania się z określonym serwerem usług AD RMS.

## <a name="rms-service-discovery"></a>Odnajdowanie usługi RMS
Odnajdowanie usługi RMS umożliwia klientowi usługi RMS sprawdzanie usługi lub serwera RMS, z którym będzie nawiązywana komunikacja, przed rozpoczęciem ochrony zawartości. Odnajdowanie usługi również może nastąpić, gdy klient usługi RMS korzysta z zawartości chronionej, ale ten rodzaj odnajdywania jest mniej prawdopodobne, ponieważ zasady dołączone do zawartości zawierają preferowaną usługę lub serwer RMS. Tylko wtedy, gdy zakończy się pomyślnie tych źródeł klient uruchomi odnajdowanie usługi.

Podczas odnajdowania usługi klient usługi RMS sprawdza następujące elementy:

1. **Rejestr systemu Windows na komputerze lokalnym**: jeśli w rejestrze skonfigurowano ustawienia odnajdowania usług, zostaną one wypróbowane jako pierwsze. 

    Domyślnie te ustawienia nie są konfigurowane w rejestrze, ale administrator może skonfigurować je dla usługi AD RMS zgodnie z procedurą opisaną w [tej sekcji](#enabling-client-side-service-discovery-by-using-the-windows-registry). Zazwyczaj administrator konfiguruje te ustawienia usługi Azure Rights Management podczas [procesu migracji](../plan-design/migrate-from-ad-rms-phase2.md) z usług AD RMS do usługi Azure Information Protection.

2. **Active Directory Domain Services**: komputer dołączony do domeny wysyła do usługi Active Directory zapytanie o punkt połączenia usługi (SCP). 

    Jeśli punkt połączenia usługi został zarejestrowany zgodnie z opisem w [tej sekcji](#ad-rms-only-enabling-server-side-service-discovery-by-using-active-directory), do klienta usługi RMS zwracany jest adres URL serwera AD RMS do użycia.

3. **Usługa odnajdowania Azure Rights Management**: klient usługi RMS łączy się z **https://discover.aadrm.com**, który monituje użytkownika do uwierzytelniania.

    Po pomyślnym uwierzytelnieniu nazwa użytkownika (i domena) z procesu uwierzytelniania będzie służyć do identyfikowania dzierżawy usługi Azure Information Protection do użycia. Adres URL usługi Azure Information Protection do użycia dla konta użytkownika jest zwracany do klienta RMS. Adres URL znajduje się w następującym formacie: **https://**\<Adres_url_dzierżawy\>  **/_wmcs/licensing** 

    Na przykład: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing

    *\<Adres_URL_dzierżawy\>* ma następujący format: **{GUID}.rms.[Region].aadrm.com**.Tę wartość można znaleźć, identyfikując wartość **RightsManagementServiceId** po uruchomieniu polecenia cmdlet [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) dla usługi Azure RMS.

> [!NOTE]
> Istnieją cztery ważne wyjątki związane z tym przepływem odnajdowania usługi:
> 
> - Urządzenia przenośne są najlepiej przystosowane do używania usługi w chmurze, więc domyślnie używają odnajdowania usług dla usługi Azure Rights Management (https://discover.aadrm.com). Aby zastąpić to ustawienie domyślne, tak aby urządzenia przenośne używają usług AD RMS, a nie usługi Azure Rights Management, należy określić rekordy SRV w systemie DNS i zainstalować rozszerzenie dla urządzeń przenośnych, zgodnie z opisem w [Active Directory Rights Management Services Mobile urządzenia Rozszerzenie](https://technet.microsoft.com/library/dn673574\(v=ws.11\).aspx). 
>
> - Jeśli usługa Rights Management jest wywoływana za pośrednictwem etykiety usługi Azure Information Protection, odnajdowanie usługi nie jest przeprowadzane. W zamian adres URL jest określany bezpośrednio w ustawieniu etykiety konfigurowanym w obrębie zasad usługi Azure Information Protection. 
>  
> - Po zainicjowaniu logowania użytkownika z aplikacji pakietu Office nazwa użytkownika (i domena) z procesu uwierzytelniania będzie służyć do identyfikowania dzierżawy usługi Azure Information Protection do użycia. W takim przypadku ustawienia rejestru są niepotrzebne i punkt połączenia usługi nie jest wybierany.
> 
> - Po skonfigurowaniu [przekierowania DNS](../plan-design/migrate-from-ad-rms-phase3.md#client-reconfiguration-by-using-dns-redirection) dla aplikacji klasycznych Szybka instalacja pakietu Office 2016, klient usługi RMS znajduje usługi Azure Rights Management przez nastąpiła odmowa dostępu do klastra usług AD RMS, który wcześniej znaleźć. Odmów to wyzwalacze akcji klienta do wyszukiwania dla rekordu SRV, który przekierowuje klienta do usługi Azure Rights Management dla dzierżawy. Ten rekord SRV umożliwia również usługi Exchange Online odszyfrowywania wiadomości e-mail, które są chronione przez Twój klaster usług AD RMS. 

### <a name="ad-rms-only-enabling-server-side-service-discovery-by-using-active-directory"></a>Tylko usługi AD RMS: włączanie odnajdowania po stronie serwera za pomocą usługi Active Directory
Jeśli Twoje konto ma wystarczające uprawnienia (Administratorzy przedsiębiorstwa i administrator lokalny serwera usług AD RMS), można automatycznie zarejestrować punkt połączenia usługi (SCP) podczas instalowania serwera klastra głównego usług AD RMS. Jeśli punkt połączenia usługi już istnieje w lesie, należy najpierw usunąć istniejący punkt połączenia usługi przed zarejestrowaniem nowego.

Aby zarejestrować i usunąć punkt połączenia usługi po zainstalowaniu usług AD RMS, można wykonać kroki poniższej procedury. Przed rozpoczęciem upewnij się, że konto ma wymagane uprawnienia (administratorzy przedsiębiorstwa i administrator lokalny serwera usług AD RMS).

#### <a name="to-enable-ad-rms-service-discovery-by-registering-an-scp-in-active-directory"></a>Aby włączyć odnajdywanie usług AD RMS przez zarejestrowanie punktu połączenia w usłudze Active Directory

1.  Otwórz konsolę usług Active Directory Management na serwerze usług AD RMS:
    
    - W systemie Windows Server 2012 R2 lub Windows Server 2012, w Menedżerze serwera wybierz **narzędzia** > **usługi zarządzania prawami dostępu w usłudze Active Directory**.

    - Dla systemu Windows Server 2008 R2, wybierz **Start** > **narzędzia administracyjne** > **usługi zarządzania prawami dostępu w usłudze Active Directory**.

2.  W konsoli usług AD RMS kliknij prawym przyciskiem myszy klaster usług AD RMS, a następnie kliknij przycisk **właściwości**.

3.  Kliknij kartę **Punkt połączenia usługi**.

4.  Zaznacz pole wyboru **Zmień punkt połączenia usługi**.

5.  Wybierz opcję **Ustaw punkt połączenia usługi na bieżący klaster certyfikacji**, a następnie kliknij przycisk **OK**.

### <a name="enabling-client-side-service-discovery-by-using-the-windows-registry"></a>Włączanie odnajdowania usługi po stronie klienta za pomocą rejestru systemu Windows
Jeśli nie chcesz używać punktu połączenia usługi lub jeśli punkt połączenia usługi nie istnieje, możesz skonfigurować rejestr na komputerze klienckim, aby klient usługi RMS mógł znaleźć odpowiedni serwer usług AD RMS.

#### <a name="to-enable-client-side-ad-rms-service-discovery-by-using-the-windows-registry"></a>Aby włączyć odnajdowanie usługi AD RMS po stronie klienta za pomocą rejestru systemu Windows

1. Otwórz edytor rejestru systemu Windows — Regedit.exe:
    
    - Na komputerze klienckim w oknie uruchamiania wpisz ciąg **regedit**, a następnie naciśnij klawisz Enter, aby otworzyć Edytor rejestru.

2. W Edytorze rejestru przejdź do klucza **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!NOTE]
    > Jeśli używasz 32-bitowej aplikacji na komputerze 64-bitowym, przejdź do **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**

3. Aby utworzyć podklucz ServiceLocation, kliknij prawym przyciskiem myszy pozycję **MSIPC**, wskaż pozycję **Nowy**, kliknij pozycję **Klucz**, a następnie wpisz ciąg **ServiceLocation**.

4. Aby utworzyć podklucz EnterpriseCertification, kliknij prawym przyciskiem myszy pozycję **ServiceLocation**, wskaż pozycję **Nowy**, kliknij pozycję **Klucz**, a następnie wpisz ciąg **EnterpriseCertification**.

5. Aby ustawić adres URL certyfikacji przedsiębiorstwa, kliknij dwukrotnie **(opcja domyślna)** podklucza **EnterpriseCertification** podklucza. Gdy **Edytowanie ciągu** pojawi się okno dialogowe dla **dane wartości**, typ `<http or https>://<AD RMS_cluster_name>/_wmcs/Certification`, a następnie kliknij przycisk **OK**.

6. Aby utworzyć podklucz EnterprisePublishing, kliknij prawym przyciskiem myszy **ServiceLocation**, wskaż polecenie **nowy**, kliknij przycisk **klucz**, a następnie wpisz `EnterprisePublishing`.

7. Aby ustawić adres URL publikowania przedsiębiorstwa, kliknij dwukrotnie **(opcja domyślna)** w obszarze **EnterprisePublishing** podklucza. Gdy **Edytowanie ciągu** pojawi się okno dialogowe dla **dane wartości**, typ `<http or https>://<AD RMS_cluster_name>/_wmcs/Licensing`, a następnie kliknij przycisk **OK**.

8.  Zamknij Edytor rejestru.

Klient usługi RMS nie może znaleźć punkt połączenia usługi, badając usługi Active Directory, i nie jest określony w rejestrze, wywołania odnajdowania usługi dla usług AD RMS nie powiedzie się.

### <a name="redirecting-licensing-server-traffic"></a>Przekierowywanie ruchu serwera licencyjnego
W pewnych przypadkach może wystąpić potrzeba przekierowania ruchu w czasie odnajdowania usługi, na przykład gdy są łączone ze sobą dwie organizacje i stary serwer licencyjny w jednej z organizacji jest wycofywany, a klienci muszą zostać przekierowani do nowego serwera. Dotyczy to także migracji z usług AD RMS do usługi Azure RMS. Użyj następującej procedury, aby włączyć przekierowywanie licencjonowania.

#### <a name="to-enable-rms-licensing-redirection-by-using-the-windows-registry"></a>Aby włączyć przekierowywanie serwera licencyjnego usługi RMS za pomocą rejestru systemu Windows

1.  Otwórz Edytor rejestru Windows — Regedit.exe.

2.  W Edytorze rejestru przejdź do jednej z gałęzi:

    -   W przypadku 64-bitowej wersji pakietu Office na platformie x64: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   W przypadku 32-bitowej wersji pakietu Office na platformie x64: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Utwórz podklucz LicensingRedirection: kliknij prawym przyciskiem myszy pozycję **Servicelocation**, wskaż pozycję **Nowy**, kliknij pozycję **Klucz**, a następnie wpisz **LicensingRedirection**.

4.  Aby ustawić przekierowywanie licencjonowania, kliknij prawym przyciskiem myszy podklucz **LicensingRedirection**, wybierz pozycję **Nowy**, a następnie wybierz pozycję **Wartość ciągu**.  W polu **Nazwa** podaj adres URL starego serwera licencyjnego, a w polu **Wartość** podaj adres URL nowego serwera licencyjnego.

    Na przykład aby przekierować licencjonowanie z serwera Contoso.com do serwera Fabrikam.com, możesz wprowadzić następujące wartości:

    **Nazwa:** `https://contoso.com/_wmcs/licensing`

    **Wartość:** `https://fabrikam.com/_wmcs/licensing`
    
    > [!NOTE]
    > Jeśli stary serwer licencyjny ma intranetowy i ekstranetowy adres URL określony, nową nazwę i mapowanie wartość należy ustawić dla obu tych adresów URL w **LicensingRedirection** klucza.

5.  Powtórz poprzedni krok w przypadku wszystkich serwerów, które muszą zostać przekierowane.

6.  Zamknij Edytor rejestru.

