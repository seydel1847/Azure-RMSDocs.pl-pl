---
title: Wdrażanie usługi Azure Information Protection skanera
description: Instrukcje dotyczące instalowania, konfigurowania i uruchamiania skanera usługi Azure Information Protection, aby dowiedzieć się, klasyfikować i chronić pliki na następującą liczbę magazynów danych.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 20d29079-2fc2-4376-b5dc-380597f65e8a
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 207f3b91e656bb65820a42137ce3bd66109f36e1
ms.sourcegitcommit: c41490096af48e778947739e320e0dc8511f6c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2018
---
# <a name="deploying-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>Wdrażanie usługi Azure Information Protection skanera można automatycznie klasyfikować i chronić pliki

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2*

Dzięki tym informacjom można dowiedzieć się o skanera usługi Azure Information Protection i jak pomyślnie zainstalować, skonfigurować i uruchomić go. 

Ten skaner działa jako usługa systemu Windows Server i umożliwia odnajdywania, klasyfikowania i chronić pliki na następujące magazynów danych:

- Foldery lokalne na komputer z systemem Windows Server z uruchomioną skanera.

- Ścieżki UNC udziały sieciowe, które używają protokołu bloku komunikatów serwera (SMB).

- Lokacje i bibliotek programu SharePoint Server 2016 i SharePoint Server 2013.

## <a name="overview-of-the-azure-information-protection-scanner"></a>Omówienie usługi Azure Information Protection skanera

Po skonfigurowaniu sieci [zasad usługi Azure Information Protection](configure-policy.md) dla etykiet, które mają zastosowanie automatycznej klasyfikacji, następnie może być oznaczony jako pliki, które umożliwia odnalezienie tego skanera. Etykiety klasyfikować i opcjonalnie stosowanie ochrony lub usuń ochronę:

![Przegląd architektury skanera w usłudze Azure Information Protection](../media/infoprotect-scanner.png)

Skaner sprawdzić wszystkie pliki, które może indeksować systemu Windows, przy użyciu dodatki IFilter, które są zainstalowane na komputerze. Następnie aby ustalić, czy pliki muszą etykietowanie, skaner korzysta z usługi Office 365 wbudowane utraty zapobiegania (DLP) czułości informacji typy danych i wykrywania wzorzec lub wzorce regex usługi Office 365. Ponieważ skaner używa klienta usługi Azure Information Protection, można klasyfikować i chronić je [typów plików](../rms-client/client-admin-guide-file-types.md).

Można uruchomić skanera odnajdywania tylko w trybie, w którym korzystać z raportów do sprawdzenia, co się stanie, jeśli pliki zostały oznaczone jako. Alternatywnie można uruchomić skanera, aby automatycznie zastosować etykiety. Podgląd wyłącznie dla wersji można również uruchomić skanera, aby odnaleźć plików, które zawierają typy informacji poufnych, bez konfigurowania etykiety warunki, które mają zastosowanie automatycznej klasyfikacji.

Należy pamiętać, że skaner nie odnajdzie i etykiety w czasie rzeczywistym. Systematycznie przeszukiwania za pomocą plików na magazyny danych, które określisz i można skonfigurować tego cyklu do uruchamiania raz lub wielokrotnie.

Specyficzne dla wersji preview skanera:

- Domyślnie tylko dokumenty pakietu Office są chronione, a nie wszystkie typy plików. Pełną listę obsługiwanych typów plików pakietu Office to wymienione w [Przewodnik administratora](../rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection)w **typów obsługiwanych przez pakiet Office plików** tabeli. 
    
    Aby zmienić to zachowanie domyślne, na przykład objęty ochroną ogólną innych typów plików, należy ręcznie edytować rejestr i określić dodatkowe typy, które mają być chronione. Aby uzyskać instrukcje, zobacz [Konfiguracja interfejsu API plików](../develop/file-api-configuration.md) z wskazówki dla deweloperów. W tej dokumentacji dla deweloperów ochrona ogólna jest określana jako „PFile”.

- Można określić, jakie typy plików ze skanowaniem lub wykluczyć ze skanowania. Do ograniczenia, które pliki skanera przeprowadzający, zdefiniuj listę typów plików za pomocą [AIPScannerScannedFileType zestawu](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileType).

- Można skonfigurować skanera przeprowadzać inspekcję plików dla wszystkich typów informacji poufnych lub Zastosuj etykiety domyślnej, bez żadnych inspekcji plików. [Więcej informacji](#using-the-scanner-with-alternative-configurations)

## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Wymagania wstępne dotyczące usługi Azure Information Protection skanera
Przed zainstalowaniem skanera usługi Azure Information Protection, upewnij się, że zostały spełnione następujące wymagania.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Komputer serwera systemu Windows do uruchamiania usługi skanera:<br /><br />-4 procesory<br /><br />-4 GB pamięci RAM|Windows Server 2016 lub Windows Server 2012 R2. <br /><br />Uwaga: Do celów testowania lub ewaluacji w środowiskach nieprodukcyjnych, możesz użyć systemu operacyjnego klienta systemu Windows, który jest [obsługiwane przez klienta usługi Azure Information Protection](../get-started/requirements.md#client-devices).<br /><br />Ten komputer może być komputer fizyczny lub wirtualny, która ma szybkie i niezawodne połączenie sieciowe do magazynów danych do przeskanowania. <br /><br />Upewnij się, że ten komputer ma [łączności z Internetem](../get-started/requirements.md#firewalls-and-network-infrastructure) wymaganych dla usługi Azure Information Protection. Lub, musisz skonfigurować go jako [odłączonymi komputerami](../rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers).|
|Program SQL Server do przechowywania konfiguracji skanera:<br /><br />-Lokalnego lub zdalnego wystąpienia<br /><br />— Roli Sysadmin Aby zainstalować skanera|SQL Server 2012 jest minimalną wersję dla następujących wersji:<br /><br />-SQL Server Enterprise<br /><br />-SQL Server Standard<br /><br />— Program SQL Server Express<br /><br />Konto, które instaluje skanera wymaga uprawnień do zapisu do wzorca bazy danych (musi być członkiem roli db_datawriter). Proces instalacji przyznaje roli właściciel bazy danych konta usługi z systemem skanera. Alternatywnie można ręcznie utworzyć bazę danych AzInfoProtectionScanner przed zainstalowaniem skanera i przypisać rolę właściciela bazy danych dla konta usługi skanera.|
|Konto usługi, aby uruchomić usługę skanera|Oprócz uruchomiona usługa skanera, to konto jest uwierzytelniany w usłudze Azure AD i pliki do pobrania zasad usługi Azure Information Protection. To konto musi być w związku z tym konta usługi Active Directory, który jest synchronizowany z usługą Azure AD, z następujących wymagań dodatkowych:<br /><br />- **Logowanie lokalne** prawo. To prawo jest wymagane do instalacji i konfiguracji skanera, ale nie dla operacji. To prawo, do konta usługi, należy przypisać, ale można usunąć tego prawa, po potwierdzeniu, że skaner można odnajdywania, klasyfikowania i ochrony plików. <br /><br />Uwaga: Jeśli wewnętrznych zasad nie umożliwiają konta usług mają konta to prawo, ale usługa może zostać przydzielony **logowanie w trybie wsadowym** do prawej strony, można spełniają to wymaganie z dodatkowe czynności konfiguracyjne. Aby uzyskać instrukcje, zobacz [określanie i użyj parametru tokenu dla zestawu AIPAuthentication](../rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) z podręcznika administratora.<br /><br />- **Zaloguj się jako usługa** prawo. To prawo jest automatycznie przyznawane kontu usługi podczas instalacji skanera, a to prawo jest wymagane do instalacji, konfiguracji i operacji skanera. <br /><br />-Uprawnienia do przechowywania danych: należy przyznać **odczytu** i **zapisu** uprawnienia skanowanie plików, a następnie zastosowanie i ochronę plików, które spełniają warunki określone w Zasady usługi Azure Information Protection. Aby uruchomić skanera odnajdywania tylko w trybie, **odczytu** uprawnienia są wystarczające.<br /><br />— Dla etykiet, które Włącz ponownie ochronę lub usuń ochronę: Aby zapewnić, że skaner zawsze ma dostęp do chronionych plików, należy to konto [superużytkowników](configure-super-users.md) usługi Azure Rights Management usługi i upewnij się, że funkcja superużytkowników jest włączona . Aby uzyskać więcej informacji o wymaganiach dotyczących konta stosowania ochrony, zobacz [przygotowywanie użytkowników i grup usługi Azure Information Protection](../plan-design/prepare.md).|
|Klient usługi Azure Information Protection jest zainstalowany na komputerze serwera systemu Windows|Należy zainstalować pełną klienta skanera. Nie należy instalować klienta z właśnie modułu programu PowerShell.<br /><br />Aby uzyskać instrukcje dotyczące instalacji klienta, zobacz [Przewodnik administratora](../rms-client/client-admin-guide.md).<br /><br />Uwaga: Jest już istnieje wcześniejszej wersji zapoznawczej skanera można zainstalować do celów testowych. Do zainstalowania tej wersji zapoznawczej, Pobierz i zainstaluj wersję zapoznawczą klienta z Microsoft Download Center.|
|Skonfigurowany etykiet, które stosowane automatycznej klasyfikacji oraz opcjonalnie ochrony|Aby uzyskać więcej informacji na temat konfigurowania warunków w ramach zasad usługi Azure Information Protection, zobacz [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection](configure-policy-classification.md).<br /><br />Aby uzyskać więcej informacji na temat konfigurowania etykiety w celu zastosowania ochrony plików, zobacz [jak konfigurowanie etykiety pod kątem ochrony usługi Rights Management](configure-policy-protection.md).<br /><br />Etykiety mogą być w globalnych zasad lub co najmniej jednej [zakres zasad](configure-policy-scope.md).<br /><br />Uwaga: Dla wersji preview, teraz możesz uruchomić skanera nawet wtedy, gdy nie skonfigurowano etykiety, które mają zastosowanie automatycznej klasyfikacji, ale w tym scenariuszu nie pasuje do instrukcji. [Więcej informacji](#using-the-scanner-without-automatic-classification)|
|Jeśli wszystkie pliki w co najmniej jeden repozytoriów danych muszą mieć etykietę:<br /><br />-Etykiety domyślnej skonfigurowany jako ustawienie zasad|Aby uzyskać więcej informacji o sposobie konfigurowania ustawieniem etykiety domyślnej, zobacz [sposób konfigurowania ustawień zasad usługi Azure Information Protection](configure-policy-settings.md).<br /><br />To ustawienie domyślne etykiety musi być w zakresie zasad skanera lub globalnych zasad. Jednak to ustawienie domyślne etykiety może być zastąpiona przez etykietę różne domyślne, którą można skonfigurować na poziomie repozytorium danych.<br /><br />Uwaga: Dla wersji preview nie jest już konieczne skonfigurowanie etykiety domyślnej w ramach zasad.| 


## <a name="install-the-azure-information-protection-scanner"></a>Zainstaluj skaner usługi Azure Information Protection

1. Zaloguj się do komputera systemu Windows Server, które zostanie uruchomione skanera. Użyj konta mającego uprawnienia administratora lokalnego i ma uprawnienia do zapisu w bazie danych master programu SQL Server.

2. Otwórz sesję środowiska Windows PowerShell z **Uruchom jako administrator** opcji.

3. Uruchom [AIPScanner instalacji](/powershell/module/azureinformationprotection/Install-AIPScanner) polecenia cmdlet, określając wystąpienia programu SQL Server, na którym chcesz utworzyć bazę danych dla skanera usługi Azure Information Protection: 
    
    ```
    Install-AIPScanner -SqlServerInstance <database name>
    ```
    
    Przykłady:
    
    Aby użyć domyślnego wystąpienia: `Install-AIPScanner -SqlServerInstance SQLSERVER1`
    
    Dla wystąpienia nazwanego: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER`
    
    Dla programu SQL Server Express: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS`
    
    Używaj pomocy online dotyczącej tego polecenia cmdlet, jeśli potrzebujesz więcej [szczegółowe przykłady](/powershell/module/azureinformationprotection/install-aipscanner#examples).
    
    Po wyświetleniu monitu podaj poświadczenia dla konta usługi skanera (\<azwa_użytkownika >) i hasło.

4. Sprawdź, czy usługa jest teraz zainstalowany za pomocą **narzędzia administracyjne** > **usług**. 
    
    Nosi nazwę zainstalowanej usługi **skanera ochrony informacji Azure** i jest skonfigurowana do uruchamiania za pomocą utworzonego konta usługi skanera.

Teraz, gdy zainstalowano skanera, należy uzyskać token dla konta usługi skanera do uwierzytelniania, co umożliwia uruchamianie nienadzorowanej usługi Azure AD. 

## <a name="get-an-azure-ad-token-for-the-scanner-service-account-to-authenticate-to-the-azure-information-protection-service"></a>Pobierz token dla konta usługi skanera do uwierzytelniania w usłudze Azure Information Protection do usługi Azure AD

1. Z tym samym komputerze z systemem Windows Server lub pulpit Zaloguj się do portalu Azure do utworzenia dwóch aplikacji usługi Azure AD, które są wymagane do określenia tokenu dostępu do uwierzytelniania. Po początkowej interakcyjnego logowania token ten umożliwia skanera nieinteraktywnie Uruchom.
    
    Aby utworzyć te aplikacje, postępuj zgodnie z instrukcjami [jak pliki etykiet nieinteraktywnie dla usługi Azure Information Protection](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) z podręcznika administratora.

2. Z komputera systemu Windows Server, jeśli konto usługi skanera zostało udzielone **logować się lokalnie** bezpośrednio do instalacji: Zaloguj się przy użyciu tego konta i Uruchom sesję programu PowerShell. Uruchom [AIPAuthentication zestaw](/powershell/module/azureinformationprotection/set-aipauthentication), określając wartości, które zostały skopiowane z poprzedniego kroku:
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application>  -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application >
    ```
    
    Po wyświetleniu monitu podaj hasło dla poświadczeń konta usługi dla usługi Azure AD, a następnie kliknij przycisk **Akceptuj**.
    
    Jeśli nie można udzielić konta usługi skanera **logować się lokalnie** bezpośrednio do instalacji: postępuj zgodnie z instrukcjami w [określanie i użyj parametru tokenu dla zestawu AIPAuthentication](../rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) sekcji w podręczniku administratora. 

Skaner ma teraz token do uwierzytelniania usługi Azure AD, które jest ważny przez jeden rok, dwa lata, lub nigdy nie wygasa, zgodnie z konfiguracją programu **sieci Web aplikacji /API** w usłudze Azure AD. Jeśli token jest ważny, należy powtórzyć kroki 1 i 2.

Teraz możesz określić magazyny danych do skanowania. 

## <a name="specify-data-stores-for-the-azure-information-protection-scanner"></a>Określ następującą liczbę magazynów danych skanera usługi Azure Information Protection

Użyj [AIPScannerRepository Dodaj](/powershell/module/azureinformationprotection/Add-AIPScannerRepository) polecenia cmdlet, aby określić dane są przechowywane do skanowania przez skaner usługi Azure Information Protection. Można określić ścieżki UNC, adresy URL programu SharePoint i foldery lokalne witryny programu SharePoint i bibliotek. 

Obsługiwane wersje programu SharePoint: SharePoint Server 2016 i SharePoint Server 2013.

1. Z tego samego komputera systemu Windows Server w sesji programu PowerShell Dodaj pierwsze dane sklepu, uruchamiając następujące polecenie:
    
        Add-AIPScannerRepository -Path <path>
    
    Na przykład: `Add-AIPScannerRepository -Path \\NAS\Documents`
    
    Inne przykłady można znaleźć [pomocy online](/powershell/module/azureinformationprotection/Add-AIPScannerRepository#examples) tego polecenia cmdlet.

2. Powtórz to polecenie dla wszystkich przechowuje dane chcesz skanować. Jeśli musisz usunąć magazyn danych, który został dodany, użyj [AIPScannerRepository Usuń](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository) polecenia cmdlet.

3. Upewnij się, że został określony w magazynie danych poprawnie, uruchamiając [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository) polecenia cmdlet:
    
        Get-AIPScannerRepository

Z konfiguracji domyślnej skanera możesz teraz gotowy do uruchomienia skanowania pierwszy w trybie odnajdowania.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-azure-information-protection-scanner"></a>Uruchomić cykl odnajdowania i wyświetlania raportów usługi Azure Information Protection skanera

1. Przy użyciu **narzędzia administracyjne** > **usług**, uruchom **skanera ochrony informacji Azure** usługi.

2. Poczekaj, aż skanera ukończyć jego cyklu. Podczas za pomocą wszystkich plików w magazynie danych, które określiłeś ma skanera zatrzymuje usługę. Można użyć lokalnego Windows **aplikacji i usług** dziennika zdarzeń **usługi Azure Information Protection**, aby upewnić się, gdy usługa jest zatrzymana. Należy wyszukać identyfikator zdarzenia informacyjną **911**.

3. Przejrzyj raporty, które są przechowywane w lokalizacji %*localappdata*%\Microsoft\MSIP\Scanner\Reports i które mają format pliku CSV. Z konfiguracji domyślnej skanera tylko te pliki, które spełniają warunki automatycznej klasyfikacji znajdują się w tych raportach.
    
    Wyniki są niezgodne z oczekiwaniami, może być konieczne dostosowania warunków określonych w zasadach usługi Azure Information Protection. Jeśli tak jest, powtórz kroki od 1 do 3, aż wszystko będzie gotowe zmienić konfigurację, aby zastosować klasyfikacji i opcjonalnie ochrony. Zawsze, powtórz te kroki, uruchom następujące polecenie programu PowerShell na komputerze systemu Windows Server:
    
        Set-AIPScannerConfiguration -Schedule OneTime

Gdy wszystko jest gotowe automatycznie etykietę pliki, które umożliwia odnalezienie skanera, przejdź do następnej procedury. 

## <a name="configure-the-azure-information-protection-scanner-to-apply-classification-and-protection-to-discovered-files"></a>Skonfiguruj skanera usługi Azure Information Protection do zastosowania i ochronę plików odnalezionych

W jego domyślne ustawienie skanera ma jeden czasu i w trybie tylko do raportowania. Aby zmienić te ustawienia, należy uruchomić [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) polecenia cmdlet.

1. Na komputerze z systemem Windows Server w sesji programu PowerShell, uruchom następujące polecenie:
    
    W wersji availabilty ogólne:
    
        Set-AIPScannerConfiguration -ScanMode Enforce -Schedule Continuous
    
    W wersji preview:
    
        Set-AIPScannerConfiguration -Enforce On -Schedule Continuous
    
    Brak innych ustawień konfiguracyjnych, które można zmienić. Na przykład czy atrybuty plików zostały zmienione, a co jest rejestrowane w raportach. Ponadto jeśli zasady usługi Azure Information Protection zawiera ustawienia, które wymaga wiadomość uzasadnienie, aby obniżyć poziom klasyfikacji lub usuń ochronę, należy określić wiadomości za pomocą tego polecenia cmdlet. Użyj [pomocy online](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration#parameters) Aby uzyskać więcej informacji o każdym ustawieniu konfiguracji. 

2. Przy użyciu **narzędzia administracyjne** > **usług**, uruchom ponownie **skanera ochrony informacji Azure** usługi.

3. Jak wcześniej monitorowanie dziennika zdarzeń i raporty, aby wyświetlić pliki, które zostały oznaczone, jakie klasyfikacji została zastosowana i czy została zastosowana ochrona.

Ponieważ został skonfigurowany harmonogram wykonywania, gdy skaner działał jego sposób za pomocą wszystkich plików, uruchomi nowy cykl tak, aby nowe i zmienione pliki są wykrywane.


## <a name="how-files-are-scanned-by-the-azure-information-protection-scanner"></a>Jak pliki są skanowane przez skaner usługi Azure Information Protection

Skaner automatycznie pomija pliki, które są [wykluczone z klasyfikacji i ochrony](../rms-client/client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection-by-the-azure-information-protection-client), takich jak pliki wykonywalne i system plików.

Dla wersji preview można zmienić to zachowanie, definiując listę typów plików ze skanowaniem lub wykluczyć ze skanowania. Należy określić tej listy, a nie należy określać repozytorium danych, listy zastosowanie do wszystkich repozytoria danych, które nie mają własne listy określony. Aby określić tej listy, użyj [AIPScannerScannedFileType zestawu](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileType). Po określeniu listy typów plików, należy dodać nowy typ pliku do listy przy użyciu [AIPScannerScannedFileType Dodaj](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileType)i usuwanie typów plików z listy przy użyciu [Remove-AIPScannerScannedFileType](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileType).

Następnie skanera używa iFilter systemu Windows w celu skanowania następujących typów plików. W przypadku tych typów plików dokumentu będzie oznaczone za pomocą warunków określonych dla etykiet.

|Typ aplikacji|Typ pliku|
|--------------------------------|-------------------------------------|
|Word|.docx; .docm; .dotm; .dotx|
|Excel|.xls; .xlt; .xlsx; .xltx; .xltm; .xlsm; .xlsb|
|PowerPoint|.ppt; .pps; .pot; .pptx; .ppsx; .pptm; .ppsm; .potx; .potm|
|Projekt|.mpp; .mpt|
|PDF|.pdf|
|Tekst|.txt; .xml; .csv|


Na koniec dla pozostałych typów plików, skanera dotyczy etykiety domyślnej w ramach zasad usługi Azure Information Protection lub skonfigurować skanera etykieta domyślna.

|Typ aplikacji|Typ pliku|
|--------------------------------|-------------------------------------|
|Projekt|.mpp; .mpt|
|Wydawca|.pub|
|Visio|.vsd; .vdw; .vst; .vss; .vsdx; .vsdm; .vssx; .vssm; .vstx; .vstm|
|XPS|.xps; .oxps; .dwfx|
|SolidWorks|.sldprt; .slddrw; .sldasm|
|JPEG |.jpg; .jpeg; .jpe; .jif; .jfif; .jfi|
|PNG |.png|
|plik GIF|.gif|
|Mapy bitowej|.bmp; .giff|
|TIFF|.tif; .tiff|
|Photoshop|.psdv|
|DigitalNegative|.dng|
|Pfile|pfile|

Należy pamiętać, że po etykietę stosuje ochronę ogólną do dokumentów, rozszerzenie nazwy pliku zmienia się na pfile. Ponadto plik staje się tylko do odczytu, dopóki nie jest otwarty przez autoryzowanego użytkownika i zapisany w jego formatu macierzystego. Pliki tekstowe i obrazy można zmieniać ich rozszerzenia nazwy pliku i stają się tylko do odczytu. Jeśli nie chcesz, aby ten problem, można zapobiec pliki, których określonego pliku, typu z chroniony. Na przykład zapobiec plik PDF chroniony plik PDF (ppdf) i zapobiec pliku txt chroniony (ptxt) plik tekstowy.

Aby uzyskać więcej informacji na temat różnych poziomów ochrony dla różnych typów plików i sposobu kontrolowania zachowania ochrony edytując rejestr, zobacz [typy obsługiwane w przypadku ochrony plików](../rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection) w przewodniku administratora.

W wersji ogólnodostępnej skanera:

- Domyślnie wszystkie typy plików są chronione.


W wersji preview skanera:

- Domyślnie tylko typy plików pakietu Office będą chronione.


## <a name="when-files-are-rescanned-by-the-azure-information-protection-scanner"></a>Jeśli pliki są ponownie skanowana przez skaner usługi Azure Information Protection

Dla pierwszego cyklu skanowania skaner sprawdza wszystkie pliki w magazynie danych skonfigurowanego i następnie dla kolejnych skanowania tylko nowe lub zmodyfikowane pliki są kontrolowane. 

Możesz wymusić skanera, aby ponownie sprawdzić wszystkie pliki, uruchamiając [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) z `-Type` ustawiona **pełne**. Ta konfiguracja jest użyteczna, jeśli raporty mają obejmować wszystkie pliki i jest zwykle używany podczas pracy w trybie odnajdowania skanera. Po zakończeniu pełnego skanowania typu skanowania automatycznie zmienia się przyrostowe tak, aby w przypadku kolejnych skanowania są skanowane tylko nowe lub zmodyfikowane pliki.

Ponadto wszystkie pliki są kontrolowane podczas skanera pobierania zasad usługi Azure Information Protection, zawierający nowe lub zostały zmienione warunki. Skaner odświeża zasady co godzinę, a usługa zostanie uruchomiona i zasady jest starsza niż jedna godzina.  

> [!TIP]
> Jeśli należy odświeżyć zasady wcześniej niż ten interwał jednej godziny, na przykład w okresie testowym: ręcznie usuń plik zasad **Policy.msip** z obu **%LocalAppData%\Microsoft\MSIP\Policy.msip** i **%LocalAppData%\Microsoft\MSIP\Scanner**. Następnie uruchom ponownie usługę Azure skanera informacji.
> 
> Zmiana ustawienia ochrony w zasadach również poczekaj 15 minut od po zapisaniu ustawień ochrony przed ponownym uruchomieniu usługi.

Jeśli skaner pobrać zasady, które miało żadnych warunków automatyczne skonfigurowane, kopię pliku zasad w folderze skaner nie jest aktualizowany. W tym scenariuszu należy usunąć plik zasad **Policy.msip** z obu **%LocalAppData%\Microsoft\MSIP\Policy.msip** i **%LocalAppData%\Microsoft\MSIP\Scanner**przed skanera można użyć pliku zasad nowo pobranej z etykiety poprawnie znalezienia automatyczne warunki.

## <a name="using-the-scanner-with-alternative-configurations"></a>Używanie skanera z alternatywnej konfiguracji

Korzystając z wersji zapoznawczej skanera, dostępne są dwa scenariusze alternatywnych, obsługiwanych przez skaner gdzie etykiety nie trzeba skonfigurować wszelkie warunki: 

- Zastosuj etykiety domyślnej, do wszystkich plików w repozytorium danych.
    
    W przypadku tej konfiguracji należy używać [AIPScannerRepository zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerRepository) polecenia cmdlet i ustaw *MatchPolicy* parametr **poza**. 
    
    Zawartość plików nie są kontrolowane i wszystkie pliki w repozytorium danych są oznaczone jako zgodnie z etykiety domyślnej, określony dla repozytorium danych (z *SetDefaultLabel* parametru) lub jeśli nie jest określony, etykiety domyślnej, które jest określone jako ustawienie zasad dla konto skanera.
    

- Zidentyfikuj wszystkie niestandardowe warunki i typy znane poufne informacje.
    
    W przypadku tej konfiguracji należy używać [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) polecenia cmdlet i ustaw *DiscoverInformationTypes* parametr **wszystkie**.
    
    Skaner używa żadnych niestandardowych warunków, które zostały określone dla etykiet w ramach zasad usługi Azure Information Protection oraz listę typów informacji, które można określić dla etykiet w zasadach usługi Azure Information Protection. 

## <a name="optimizing-the-performance-of-the-azure-information-protection-scanner"></a>Optymalizacja wydajności skanera usługi Azure Information Protection

Aby zmaksymalizować wydajność skanera:

- **Ma szybkie i niezawodne połączenie sieciowe między komputerem skanera i magazynu danych zeskanowane**
    
    Na przykład umieścić komputer skanera w tej samej sieci LAN lub (preferowane), w tym samym segmencie sieci do przechowywania danych zeskanowane.
    
    Jakość połączenia sieciowego wpływa na wydajność skanera, ponieważ do zbadania pliki, skaner przesyła zawartość plików do komputera z uruchomioną usługą skanera. Gdy ograniczenie (lub wyeliminowanie) liczbę przeskoków sieciowych, wymaga te dane są przesyłane również zmniejszyć obciążenie sieci. 

- **Upewnij się, że zasoby procesora dostępne na komputerze skanera**
    
    Sprawdzaniem zgodność z skonfigurowanych warunków, zawartość pliku i szyfrowania i odszyfrowywania plików są akcje obciążenie procesora. Monitorowanie typowych cykle skanowania dla Twojego magazynów określone dane ustalić, czy brak zasobów procesora negatywnego wpływu na wydajność skanera.
    
- **Skanuj folderów lokalnych na komputerze z uruchomioną usługą skanera**
    
    Jeśli masz foldery, aby przeprowadzić skanowanie w systemie Windows server, zainstalować skaner na innym komputerze i skonfigurować te foldery sieciowych udziałów do skanowania. Oddzielanie dwie funkcje obsługi plików i skanowanie plików oznacza, że zasoby obliczeniowe dla tych usług nie rywalizuje ze sobą.

Inne czynniki wpływające na wydajność skanera:

- Bieżące obciążenie i czasy odpowiedzi magazynów danych zawierających pliki do skanowania

- Określa, czy skaner działa w trybie odnajdowania lub tryb wymuszania
    
    Tryb odnajdowania zwykle ma wyższy skanowanie szybkości niż wymuszać trybu, ponieważ odnajdywanie wymaga jednego pliku do odczytu akcji, należy wymusić wymaga trybie odczytu i zapisu akcje.

- Zmień warunki usługi Azure Information Protection
    
    Pierwszy cykl skanowania podczas skaner musi sprawdzać każdy plik oczywiście będzie trwać dłużej niż kolejne skanowania cyklów domyślnie inspekcji tylko nowych i zmienionych plików. Jednak w przypadku zmiany warunków w ramach zasad usługi Azure Information Protection, wszystkie pliki są skanowane ponownie, zgodnie z opisem w [powyższej sekcji](#when-files-are-rescanned-by-the-azure-information-protection-scanner).

- Wybranego poziom rejestrowania
    
    Można wybrać **debugowania**, **informacji**, **błąd** i **poza** raportów skanera. **Wyłącz** powoduje najlepszą wydajność; **Debugowania** znacznie spowalnia skanera i powinna być używana tylko w celu rozwiązania problemu. Aby uzyskać więcej informacji, zobacz *ReportLevel* parametr [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) polecenia cmdlet.

- Same pliki:
    
    - Pliki pakietu Office są zeskanowane szybciej niż pliki PDF.
    
    - Niechronione pliki są szybsze do skanowania niż chronionych plików.
    
    - Duże pliki oczywiście skanowanie trwało dłużej niż małe pliki.

- W wersji preview skanera:
    
    - Potwierdź, że uruchomioną skanera konto usługi ma uprawnienia w [wymagania wstępne skanera](#prerequisites-for-the-azure-information-protection-scanner) sekcji, a następnie skonfiguruj [zaawansowane właściwości klienta](../rms-client/client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) wyłączyć niski poziom skaner integralności.
    
    - Skaner przebiega szybciej, korzystając z [alternatywnej konfiguracji](#using-the-scanner-with-alternative-configurations) do zastosowania etykiety domyślnej do wszystkich plików, ponieważ skaner nie sprawdzać zawartości pliku.
    
    - Skaner uruchamia więcej spowalniając, korzystając z [alternatywnej konfiguracji](#using-the-scanner-with-alternative-configurations) do identyfikowania wszystkie niestandardowe warunki i typy znane poufne informacje.
    

## <a name="list-of-cmdlets-for-the-azure-information-protection-scanner"></a>Listę poleceń cmdlet dla usługi Azure Information Protection skanera 

Inne polecenia cmdlet skanera pozwalają zmienić konta usługi i bazy danych dla skanera, Pobierz bieżące ustawienia skanera i odinstaluj usługę skanera. Skaner używa następujących poleceń cmdlet:

- [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository)

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/Set-AIPScannerRepository)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)

Dodatkowe polecenia cmdlet w wersji preview skanera:

- [Dodaj AIPScannerScannedFileType](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileType)

- [Usuń AIPScannerScannedFileType](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileType)

- [Zestaw AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes)


## <a name="event-log-ids-and-descriptions"></a>Identyfikatory i opisy dziennika zdarzeń

Skorzystaj z następujących sekcji do identyfikowania możliwych identyfikatorów zdarzeń i opisy skanera. Te zdarzenia są rejestrowane na serwerze z uruchomioną usługę skaner, w oknach **aplikacji i usług** dziennika zdarzeń **usługi Azure Information Protection**.

-----

Informacje o **910**

**Uruchomić skanera cyklu.**

To zdarzenie jest rejestrowane, gdy usługa skanera została uruchomiona i rozpocznie skanowanie w poszukiwaniu plików w repozytoria danych, które można określić.

----

Informacje o **911**

**Zakończono skanera cyklu.**

To zdarzenie jest rejestrowane po zakończeniu jego jednorazowe skanowanie skanera, od czasu uruchomienia serwera lub skaner zakończył cykl ciągłego harmonogramu.

----

Informacje o **913**

**Skaner jest zatrzymana, ponieważ skaner ustawiono wartość Never.**

To zdarzenie jest rejestrowane, gdy skaner jest skonfigurowany do uruchamiania jednego czasu zamiast stale, i usługę Azure Information Protection skanera ręcznego ponownego uruchomienia od czasu uruchomienia komputera.  

Skanowanie plików ponownie, musisz ustawić harmonogram **OneTime** lub **ciągłe**, a następnie ręcznie ponownie uruchom usługę. Aby zmienić harmonogram, użyj [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) polecenia cmdlet i **harmonogram** parametru.

----

Błąd **912**

**Wystąpił nieznany błąd.**

Więcej informacji jest zalogowany szczegółowego raportu, który jest przechowywany w % localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_YYYY_MM_DD_HH_MM.csv.

Skontaktuj się z [Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support) Jeśli to zdarzenie będzie nadal występować, mają być rejestrowane. 

----

Błąd **914**

**Usługa automatycznie została zatrzymana z powodu nieprawidłowych konfiguracji: plik zasad lub jest uszkodzony.**

To zdarzenie jest rejestrowane, gdy klient usługi Azure Information Protection nie ma pliku zasad skanera do uruchomienia.

Zasady usługi Azure Information Protection jest przechowywany w %localappdata%\Microsoft\MSIP i musi być skonfigurowany z etykietami, których warunki do zastosowania automatycznej klasyfikacji. Lub zasady muszą być skonfigurowane dla etykiety domyślnej.

Upewnij się, że zapory nie blokują wymaga połączenia z Internetem. Aby uzyskać więcej informacji, zobacz [zapory i infrastruktury sieci](../get-started/requirements.md#firewalls-and-network-infrastructure) wymagania dotyczące usługi Azure Information Protection. Jeśli połączenie z Internetem nie jest możliwe, wykonaj instrukcje dotyczące obsługi [odłączone komputery](../rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers).


## <a name="next-steps"></a>Następne kroki

Może być zastanawiasz się: [jaka jest różnica między infrastruktury klasyfikacji plików systemu Windows Server i skanera usługi Azure Information Protection?](../get-started/faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

Za pomocą programu PowerShell można także interaktywnie klasyfikować i chronić pliki z komputera stacjonarnego. Aby uzyskać więcej informacji dotyczących tego i innych scenariuszy korzystających z programu PowerShell, zobacz [przy użyciu programu PowerShell przy użyciu klienta usługi Azure Information Protection](../rms-client/client-admin-guide-powershell.md).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
