---
title: Klient usługi Azure Information Protection — wersja Historia wersji i zasady pomocy technicznej
description: Zobacz, co jest nowe lub zostały zmienione w wersji klienta usługi Azure Information Protection dla Windows i zrozumieć zasady świadczenia pomocy technicznej.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/30/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b05b41b802b54d874d13dcf13f541374d4150564
ms.sourcegitcommit: b70d49870960a7a3feaf9a97a6e04ad350c4d2c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2018
ms.locfileid: "50751257"
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Klient usługi Azure Information Protection: zasady wydania wersji historii i pomoc techniczna

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, systemu Windows Server 2008 R2*

Zespół pracujący nad usługą Azure Information Protection regularnie aktualizuje klienta usługi Azure Information Protection w celu wprowadzenia poprawek i dodania nowych funkcji. 

Można pobrać najnowszej ogólnodostępnej wersji i bieżącej wersji zapoznawczej (jeśli jest dostępny) z [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). W wersji ogólnodostępnej znajduje się również w wykazie usługi Microsoft Update (kategoria: **usługi Azure Information Protection**), dzięki czemu można uaktualnić klienta za pomocą programu WSUS lub programu Configuration Manager lub innych wdrożeń oprogramowania mechanizmy, korzystających z usługi Microsoft Update.

Aby uzyskać więcej informacji, zobacz [uaktualnianie i obsługa klienta usługi Azure Information Protection](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client).

### <a name="servicing-information-and-timelines"></a>Obsługa informacji i osie czasu

Ogólna dostępność (GA) każdej wersji klienta usługi Azure Information Protection jest obsługiwana przez maksymalnie sześć miesięcy po kolejnych wersji Ogólnodostępnej. Nieobsługiwane wersje klienta nie znajdują się na tej stronie. Poprawki i nowe funkcje są one zawsze stosowane do najnowszej wersji ogólnie dostępnej wersji i nie będą stosowane do starszych wersji ogólnie dostępnej wersji.

Wersje zapoznawcze nie powinny być wdrażane dla użytkowników końcowych w sieciach produkcyjnych. Użyj najnowszej wersji zapoznawczej oraz ich wypróbowanie nowymi funkcjami i poprawkami, które zostaną wprowadzone w kolejnej Ogólnodostępnej wersji. Wersji zapoznawczych, które nie są aktualne, nie są obsługiwane.

### <a name="release-history"></a>Historia wersji

Skorzystaj z poniższych informacji, zobacz, co jest nowe lub zostały zmienione w obsługiwanej wersji klienta usługi Azure Information Protection dla Windows. Najnowsza wersja jest wyświetlana na początku listy. 

> [!NOTE]
> Niewielkie poprawki nie są wyświetlane, dlatego jeśli wystąpi problem z klientem usługi Azure Information Protection, zalecamy sprawdzenie, czy problem został rozwiązany za pomocą najnowszej wersji ogólnie dostępnej. Jeśli problem będzie się powtarzać, sprawdź bieżącą wersję (wersja zapoznawcza).
>  
> Aby uzyskać pomoc techniczną, zobacz [opcje pomocy technicznej i zasoby społecznościowe](../information-support.md#support-options-and-community-resources) informacji. Zachęcamy także do kontaktowania się z naszym zespołem ds. usługi Azure Information Protection w [witrynie Yammer](https://www.yammer.com/askipteam/).

## <a name="versions-later-than-137190"></a>Wersjach starszych niż 1.37.19.0

W przypadku wersji 1 klienta, która jest nowsza niż 1.37.19.0 jest kompilacji w wersji zapoznawczej do celów testowania i oceny. 

> [!TIP]
> Zainteresowani oceny klienta etykietowania ujednolicone usługi Azure Information Protection, ponieważ etykiety są publikowane w Centrum zgodności i zabezpieczeń usługi Office 365? Zobacz [usługi Azure Information Protection unified etykietowania klienta: informacje o wersji wersji](unifiedlabelingclient-version-release-history.md).

**Wydana**: 20/09/2018

**Nowe funkcje:**

- Obsługa [centralnej funkcji raportowania](../reports-aip.md) dla funkcji analizy usługi Azure Information Protection ogłoszeniem na konferencji Microsoft Ignite.

**Dodatkowe:**

Tylko dla tej wersji zapoznawczej, specyficzne dla skaner:

- Zainstaluj skaner, wykonując następujące czynności:
    
    1. Zainstaluj bieżącą wersję GA (1.37.19.0) klienta.
    2. Zainstaluj i skonfiguruj skanera.
    3. Uruchomić skanera.
    4. Uaktualnienie klienta usługi Azure Information Protection do tej wersji zapoznawczej.
    5. Uruchomić skanera.

- Znany problem z skanowaniem dużych zestawów danych:
    
    Z tą wersją zapoznawczą stopniowo zwiększać liczbę plików do skanowania i monitorowania postępu. Jeśli stan skanera zgłasza, że jest uruchomiona, ale nowe pliki nie uzyskać skanowany, Zmniejsz liczbę plików do skanowania i ponownie uruchomić skanera. 

Aby uzyskać instrukcje dotyczące instalowania, konfigurowania i uruchomić skanera, zobacz [wdrażanie skanera usługi Azure Information Protection do automatycznego klasyfikowania i ochrony plików](../deploy-aip-scanner.md).

## <a name="version-137190"></a>Wersja 1.37.19.0

**Wydana**: 09/17/2018 r.

Ta wersja zawiera wersję MSIPC 1.0.3592.627 klienta usługi RMS.

**Nowe funkcje**: 

- Obsługa standardu ISO do szyfrowania plików PDF, konfigurując nową [Zaawansowana konfiguracja klienta](client-admin-guide-customizations.md#protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption). W przypadku skonfigurowania tej opcji, dokumentów PDF, które można chronić zachować ich rozszerzenia nazwy pliku PDF (zamiast Zmień ppdf) i mogą być otwierane przez czytniki PDF, obsługujące tego standardu ISO. Obecnie należy poinstruować użytkowników, aby otworzyć tych chronionych plików PDF ręcznie przy użyciu podglądu usługi Azure Information Protection. Aby ułatwić użytkownikom to, kiedy adresat otworzy tych chronionych plików PDF, zobaczą strony z ikon w celu wybrania systemu operacyjnego.

- Obsługa nowych typów informacji poufnych klasyfikować dokumenty, które zawierają dane osobowe. [Więcej informacji](../configure-policy-classification.md#sensitive-information-types-that-require-a-minimum-version-of-the-client) 

- Etykiety umożliwiające objęcie ochroną teraz wyświetlane w aplikacji pakietu Office 2016 (minimalna wersja 1805, kompilacja 9330.2078) po użytkownik ma przypisaną licencję usługi Azure Rights Management (nazywanego także usługi Azure Information Protection dla usługi Office 365).

- Obsługa etykietowania **Strict otwartego dokumentu XML** format w plikach programu Word, Excel i PowerPoint. Aby uzyskać więcej informacji na temat formatów Open XML, zobacz w blogu pakietu Office, [nowe opcje format pliku w nowy pakiet Office](https://www.microsoft.com/en-us/microsoft-365/blog/2012/08/13/new-file-format-options-in-the-new-office/). 

- Obsługa plików, które są chronione przez Secure Islands, gdy te pliki są inne niż dokumentów PDF i pakietu Office. Na przykład chronionych plików tekstowych i obrazów. Lub rozszerzenie nazwy pliku plików, które mają plik pfile. Ta obsługa umożliwia nowe scenariusze, takie jak skanera usługi Azure Information Protection będzie mogła sprawdzić te pliki do poufnych informacji i automatycznie relabeling je do usługi Azure Information Protection. [Więcej informacji](client-admin-guide-customizations.md#support-for-files-protected-by-secure-islands)

- Nowe zaawansowane ustawienia klienta do usunięcia, nagłówki i stopki, które zostały zastosowane do dokumentów przez innych rozwiązań etykietowania. [Więcej informacji](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions)

- Skanera usługi Azure Information Protection:

    - Nowe polecenie cmdlet, [AIPScanner aktualizacji](/powershell/module/azureinformationprotection/Update-AIPScanner): wymagane do uruchamiania raz po uaktualnianie z poprzedniej wersji Ogólnodostępnej (1.29.5.0) lub wcześniej.
    
    - Nowe polecenie cmdlet, [Get AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus): pobiera bieżący stan usługi skanera.  
    
    - Nowe polecenie cmdlet, [Start AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan): powoduje, że skanera można uruchomić na czas cykl skanowania w poszukiwaniu, kiedy harmonogram ustawiono na ręcznie.
    
    - Program SharePoint Server 2010 jest obsługiwana w przypadku klientów, którzy mają [rozszerzoną obsługę w tej wersji programu SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).
    
- Obsługa nowej **usługi Azure Information Protection — węzły (wersja zapoznawcza)** bloku w witrynie Azure portal, która umożliwia Zarządzanie skanerami z centralnej lokalizacji. Informacje z Twojej wdrożonej skanerów, które mają łączność do platformy Azure jest aktualizowana co pięć minut. Z tego bloku można uruchomić skanera jednorazowe skanowania, ponownego skanowania wszystkich plików, sprawdź stan skaner i wyświetlić szybkość skanowania.

**Poprawki**

- Skanera usługi Azure Information Protection:
    
    - W przypadku dokumentów, które są chronione w bibliotekach programu SharePoint, jeśli *DefaultOwner* parametr nie jest używany do repozytorium danych, wartość edytora programu SharePoint jest teraz używana jako wartość domyślną, zamiast autora.
    
    - Skaner raporty zawierają "Ostatnio modyfikowany przez", dokumentów pakietu Office.
    
    - Można teraz chronić wszystkie typy plików za pomocą `*` symboli wieloznacznych podczas edycji rejestru zgodnie z opisem w [edycji rejestru skanera](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner) sekcji.

- Podczas klasyfikowania i ochrony za pomocą programu PowerShell lub skaner metadane dokumentu pakietu Office jest ono usuwane lub szyfrowane.

- Podczas wyświetlania wiadomości e-mail przy użyciu ikony strzałek następnej i poprzedniej pozycji na pasku narzędzi Szybki dostęp pokazywane jest prawidłowa etykieta dla każdej wiadomości e-mail.

- Uprawnienia niestandardowe obsługuje adresy e-mail adresatów, zawierające apostrof.

- Środowisko komputera zostaną zainicjowane pomyślnie (bootstrap) Ta akcja jest inicjowane przez otwarcie chronionego dokumentu, który jest przechowywany w usłudze SharePoint Online.

- Po kliknięciu prawym przyciskiem myszy w Eksploratorze plików, programu PowerShell lub skaner korzystania z klienta, etykietowania jest zablokowany dla plików w lokalizacji WebDav, ponieważ jest to nieobsługiwany scenariusz.

- Nie wyświetla ikonę Usuń etykietę w aplikacjach klienckich (Word, Excel, PowerPoint i Outlook) po skonfigurowaniu [ustawienie zasad](../configure-policy-settings.md) z **wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**.

**Dodatkowe zmiany**:

- Aby uzyskać [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration):
    
    - Wartości *harmonogram* parametru nie są już **OneTime**, **ciągłe**, i **nigdy**, ale teraz **ręczne** i **zawsze**.
        
    - *Typu* parametr zostanie usunięty, więc również są usuwane z danych wyjściowych, po uruchomieniu [Get AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration). Domyślnie tylko nowe lub zmodyfikowane pliki są kontrolowane po pierwsze skanowanie cyklu. Jeśli ustawione wcześniej *typu* parametr **pełną** ponownego skanowania wszystkich plików, uruchom teraz [Start AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan) z *resetowania* parametru. Skaner muszą również zostać skonfigurowane ręcznie harmonogramu, który wymaga *harmonogram* parametr należy ustawić **ręczne** z [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration).
    
- Domyślną listę wykluczeń dla klienta i skaner obejmuje teraz pliki msg, RAR i zip. Skaner także wyklucza .rtf — pliki. [Więcej informacji](client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection)

- Wersja zasad jest zmieniany na 1.4. Identyfikowanie numer wersji jest wymagana dla [Konfigurowanie odłączonych komputerów](client-admin-guide-customizations.md#support-for-disconnected-computers).

- **Prześlij nam opinię** łącze w **Pomoc i opinie** okno dialogowe zostanie usunięty. Tymczasowo zastąpione **zgłosić problem**, ale link ten będzie wyświetlać teraz w wersji zapoznawczej tylko w wersji. Domyślnie opcja ta wysyła wiadomość e-mail do firmy Microsoft, ale możesz zmienić ten adres e-mail, na ciągu HTTP, który określisz. Na przykład dostosowanej strony sieci web, przeznaczonego dla użytkowników, aby zgłosić problemy lub adres e-mail, który prowadzi do pomocy technicznej. Aby zmodyfikować ten adres, użyj [Zaawansowane ustawienia klienta](client-admin-guide-customizations.md#modify-the-email-address-for-the-report-an-issue-link).

## <a name="version-12950"></a>Wersja 1.29.5.0 

**Wydana**: 06/26/2018 r.

Ta wersja zawiera wersję MSIPC 1.0.3403.1224 klienta usługi RMS.

**Poprawki**:

- W wersjach programu Outlook 16.0.9324.1000 i nowsze (kliknij polecenie do uruchomienia), na pasku usługi Azure Information Protection obsługuje najnowsze opcje wyświetlania monitor, które mogłyby prowadzić wcześniej na pasku wyświetlane poza aplikację Outlook.

- Oznaczenia wizualne, które można skonfigurować [według typu aplikacji pakietu Office](../configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook) teraz zastąpić nagłówka lub stopki uprzednio zastosowaną przez etykiety usługi Azure Information Protection.

- Gdy już nazywa plik programu Excel i stosuje się etykietę oznaczeń wizualnych, nowy arkusz ma teraz oznaczeń wizualnych etykiety zastosowane.

- Kiedy używasz Zaawansowane ustawienia klienta dotyczącego [etykiety dokumentu pakietu Office przy użyciu istniejącej właściwości niestandardowej](client-admin-guide-customizations.md#label-an-office-document-by-using-an-existing-custom-property), etykietowania automatycznego nie zastępuje ręcznego etykietowania.

## <a name="version-127480"></a>Wersja 1.27.48.0

**Wydana**: 05/30/2018 r.

Ta wersja zawiera wersję MSIPC 1.0.3403.1224 klienta usługi RMS.

**Nowe funkcje**: 

- Skanera usługi Azure Information Protection:
    
    - Można określić listy typów plików, aby uwzględnić lub wykluczyć ze skanowania. Aby określić tej listy, użyj [AIPScannerScannedFileTypes zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes). Po określeniu listy typów plików, nowy typ pliku można dodać do listy przy użyciu [AIPScannerScannedFileTypes Dodaj](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileTypes)i usuwanie typu pliku z listy przy użyciu [Remove-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileTypes).
    
    - Można oznaczyć pliki bez sprawdzania zawartości przez zastosowanie etykiety domyślnej. Użyj [AIPScannerRepository zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerRepository) polecenia cmdlet i ustaw *MatchPolicy* parametr **poza**. 
    
    - Pliki można odnajdywać za pomocą typów informacji poufnych, bez konieczności konfigurowania etykiet klasyfikacji automatycznej. Użyj [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) polecenia cmdlet i ustaw *DiscoverInformationTypes* parametr **wszystkie**
    
    - Domyślnie tylko typy dokumentów pakietu Office będą chronione. Inne typy plików mogą być chronione, podczas definiowania w rejestrze. Aby uzyskać instrukcje, zobacz [Konfiguracja interfejsu API plików](../develop/file-api-configuration.md) we wskazówkach dla deweloperów.
    
    - Domyślnie skaner uruchamiane z poziomu o niskiej integralności na wyższy poziom zabezpieczeń w przypadku, gdy uruchamiasz skaner przy użyciu konta, które ma uprzywilejowane prawa. Jeśli konto usługi, na którym uruchomiono skaner ma wyłącznie prawa, które zostały udokumentowane w artykule [wymagania wstępne skanera](../deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner), poziom o niskiej integralności nie jest konieczne i nie jest zalecane, ponieważ negatywnie wpływa na wydajność. Możesz użyć zaawansowanych ustawień można wyłączyć poziom o niskiej integralności klienta. [Więcej informacji](client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) 
    
- Aby uzyskać [Get-AIPFileStatus](/powershell/module/azureinformationprotection/Get-AIPFileStatus), dane wyjściowe obejmują teraz właściciela usługi Rights Management i Wystawca usługi Rights Management oraz datę, która była chroniona zawartość.
 
**Dodatkowe zmiany**:

- Skanera usługi Azure Information Protection: 
    
    - Jeśli zainstalowano poprzednią wersję skaner, uruchom ponownie polecenie instalacji skanera [AIPScanner instalacji](/powershell/module/azureinformationprotection/Install-AIPScanner) po uaktualnieniu klienta usługi Azure Information Protection. Ustawienia konfiguracji dla repozytoriów i skaner zostaną zachowane. Ponowna instalacja skaner przyznaje uprawnienia do usuwania konta usługi dla skanera bazy danych, który będzie potrzebny w przypadku raportów skanera.    
    
    - *ScanMode* parametr [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) została zmieniona na **Wymuś**, przy użyciu wartości OFF, a na.
    
    - Aby korzystać z ustawieniem etykiety domyślnej, nie potrzebujesz już skonfigurować etykiety domyślnej jako ustawienie zasad. Zamiast tego po prostu określić etykieta domyślna konfiguracja repozytorium. 

- Usunięte "Gratulujemy!" Witaj i "What's new in Azure Information Protection" strony wyświetlany w aplikacjach pakietu Office do użytku po raz pierwszy.

## <a name="version-12660"></a>Wersja 1.26.6.0

**Wydana**: 04/17/2018 r.

Ta wersja zawiera wersję MSIPC 1.0.3403.1224 klienta usługi RMS.

**Nowe funkcje**:

- Skaner usługi Azure Information Protection: moduł programu PowerShell, który jest dołączony klient ma nowe polecenia cmdlet do zainstalowania i skonfigurowania skaner, tak aby odnajdywania, klasyfikowania i ochrony plików na swoich lokalnych magazynów danych. Aby uzyskać instrukcje, zobacz [wdrażanie skanera usługi Azure Information Protection do automatycznego klasyfikowania i ochrony plików](../deploy-aip-scanner.md). 
- Teraz możesz ustawić różne pod kątem oznaczeń wizualnych programu Word, Excel, PowerPoint i Outlook przy użyciu zmiennej instrukcji "If.App" w ciągu tekstowym oraz identyfikowanie typu aplikacji. [Więcej information]configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)

- Obsługa [ustawienie zasad](../configure-policy-settings.md), **wyświetlany pasek Information Protection w aplikacjach pakietu Office**. Gdy to ustawienie jest wyłączone, użytkownicy wybierają etykiety z **Chroń** przycisk na Wstążce.

- Nowe zaawansowane ustawienia klienta (w wersji zapoznawczej) można włączyć klasyfikacji, aby uruchomić w sposób ciągły w tle. Jeśli to ustawienie jest włączone dla aplikacji pakietu Office klasyfikacji automatycznej i zalecanej działa w sposób ciągły w tle, zamiast uruchamiać podczas zapisywania dokumentów. Ta zmiana w zachowaniu można teraz zastosować klasyfikacji automatycznej i zalecanej do dokumentów, które są przechowywane w usłudze SharePoint Online. [Więcej informacji](client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background)

- Nowe zaawansowane ustawienia klienta, program Outlook nie ma zastosowania etykiety domyślnej, która jest skonfigurowana w zasadach usługi Azure Information Protection. Zamiast tego programu Outlook, można zastosować różne etykiety domyślne lub brak etykiety. [Więcej informacji](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) 

- Dla aplikacji pakietu Office podczas określania uprawnień niestandardowych, można teraz Przeglądaj i wybierz użytkowników z ikony książki adresowej. Wybranie tej opcji powoduje parzystości wrażenia użytkownika podczas określania uprawnień niestandardowych za pomocą Eksploratora plików.

- Obsługa metodę całkowicie nieinterakcyjnych authentication dla kont usług, które korzystają z programu PowerShell i nie można udzielić **logować się lokalnie** prawo. Ta metoda uwierzytelniania, musisz korzystać z nowych *tokenu* parametrem [Set-AIPAuthentication](/powershell/module/azureinformationprotection/Set-AIPAuthentication), i uruchom skrypt programu PowerShell jako zadania. [Więcej informacji](client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)

- Nowy parametr *IntegratedAuth* dla [Set-RMSServerAuthentication](/powershell/module/azureinformationprotection/set-rmsserverauthentication). Ten parametr obsługuje tryb serwera dla usług AD RMS, który jest wymagany dla usług AD RMS do obsługi infrastruktury klasyfikacji plików systemu Windows Server.


**Poprawki**:

Poprawki dotyczące stabilności i dla konkretnych scenariuszy, które obejmują:

- W przypadku wersji pakietu Office 16.0.8628.2010 i nowsze (kliknij polecenie do uruchomienia), na pasku usługi Azure Information Protection obsługuje najnowsze opcje wyświetlania monitor, które mogłyby prowadzić wcześniej na pasku wyświetlane poza aplikacje pakietu Office.

- Po dwóch organizacji, za pomocą usługi Azure Information Protection udostępnić etykietami dokumentów i wiadomości e-mail, własne etykiety są zachowywane i nie zastępuje etykiet w organizacji.

- Dla programu Excel:
        
    - Obsługa zmiany Motywy pakietu Office lub motywy Windows, które uprzednio spowodowały Excel nie zawiera żadnych danych po motyw został zmieniony.
        
    - Obsługa komórek zawierających odsyłaczy, które wcześniej spowodowany uszkodzeniem tekstu w komórce.
    
    - Obsługa, wpisując znaki japońskie, chiński lub koreański, których wcześniej zamknięte okno, więc nie można wybrać następujące znaki.
    
    - Obsługa komentarzy, które wcześniej zamknięty komentarz, gdy został on wpisany.

- Dla programu PowerPoint: Obsługa współtworzenia, który mógł wcześniej spowodować utratę danych.

- Pliki, które mają rozszerzenie nazwy pliku XML można teraz sprawdzone pod kątem zalecaną lub automatyczną klasyfikację.

- Podgląd teraz otworzyć chronionych plików tekstowych (ptxt i pxml) większe niż 20 MB. 
- Zapobiegaj wiszące programu Outlook, podczas korzystania z programu Outlook przypomnienia.

- Usługa ładowania początkowego pomyślnie Office 64-bitowy, tak, aby chronić dokumenty i wiadomości e-mail.

- Można teraz skonfigurować etykietę uprawnienia zdefiniowane przez użytkownika dla programu Word, Excel, PowerPoint i Eksplorator plików i także użyć zaawansowanego ustawienie klienta umożliwiające Ukryj opcje uprawnień niestandardowych. [Więcej informacji](client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users) 

- Wrócić do czcionki Calibri Jeśli oznaczeń wizualnych w zasadach usługi Azure Information Protection są skonfigurowane dla nazwę czcionki, który nie jest zainstalowany na komputerze klienckim.

- Zapobiegaj Office awarii po uaktualnieniu klienta usługi Azure Information Protection.

- Dla aplikacji pakietu Office należy zwiększyć użycie wydajności i pamięci.

- Po skonfigurowaniu etykiety dla uprawnienia zdefiniowane przez użytkownika i ochrony HYOK (AD RMS), ochrony nie są już nieprawidłowo korzysta z usługi Azure Rights Management.

- Dla bardziej spójne środowisko zarządzania etykiet podrzędnych nie będzie dziedziczyć oznaczenia wizualne i ustawienia ochrony ich etykietę nadrzędną.

**Dodatkowe zmiany**:

- Aby uzyskać [dzienniki użycia klienta](client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client ): 102 identyfikator zdarzenia i identyfikator 103 są zastępowane zdarzenia o numerze 101 identyfikator.

## <a name="next-steps"></a>Kolejne kroki

Aby uzyskać więcej informacji o instalowaniu i używaniu klienta: 

- Użytkownicy: [pobieranie i instalowanie klienta](install-client-app.md)

- Administratorzy: [Podręcznik administratora klienta usługi Azure Information Protection](client-admin-guide.md)


