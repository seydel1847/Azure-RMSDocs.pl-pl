---
title: Klient usługi Azure Information Protection — wersja Historia wersji i zasady pomocy technicznej
description: Zobacz, co jest nowe lub zostały zmienione w wersji klienta usługi Azure Information Protection dla Windows i zrozumieć zasady świadczenia pomocy technicznej.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 732eb98b1cbd1af575f15ddc992349d77b436131
ms.sourcegitcommit: 78d368a4480cc1febedc8535c6c3e184e69caf7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37088263"
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
> Aby uzyskać pomoc techniczną, zobacz [opcje pomocy technicznej i zasoby społecznościowe](../get-started/information-support.md#support-options-and-community-resources) informacji. Zachęcamy także do kontaktowania się z naszym zespołem ds. usługi Azure Information Protection w [witrynie Yammer](https://www.yammer.com/askipteam/).

## <a name="version-12950"></a>Wersja 1.29.5.0 

**Wydana**: 06/26/2018 r.

Ta wersja zawiera wersję MSIPC 1.0.3403.1224 klienta usługi RMS.

**Poprawki**:

- W wersjach programu Outlook 16.0.9324.1000 i nowsze (kliknij polecenie do uruchomienia), na pasku usługi Azure Information Protection obsługuje najnowsze opcje wyświetlania monitor, które mogłyby prowadzić wcześniej na pasku wyświetlane poza aplikację Outlook.

- Oznaczenia wizualne, które można skonfigurować [według typu aplikacji pakietu Office](../deploy-use/configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook) teraz zastąpić nagłówka lub stopki uprzednio zastosowaną przez etykiety usługi Azure Information Protection.

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
    
    - Domyślnie skaner uruchamiane z poziomu o niskiej integralności na wyższy poziom zabezpieczeń w przypadku, gdy uruchamiasz skaner przy użyciu konta, które ma uprzywilejowane prawa. Jeśli konto usługi, na którym uruchomiono skaner ma wyłącznie prawa, które zostały udokumentowane w artykule [wymagania wstępne skanera](../deploy-use/deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner), poziom o niskiej integralności nie jest konieczne i nie jest zalecane, ponieważ negatywnie wpływa na wydajność. Możesz użyć zaawansowanych ustawień można wyłączyć poziom o niskiej integralności klienta. [Więcej informacji](../rms-client/client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) 
    
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

- Skaner usługi Azure Information Protection: moduł programu PowerShell, który jest dołączony klient ma nowe polecenia cmdlet do zainstalowania i skonfigurowania skaner, tak aby odnajdywania, klasyfikowania i ochrony plików na swoich lokalnych magazynów danych. Aby uzyskać instrukcje, zobacz [wdrażanie skanera usługi Azure Information Protection do automatycznego klasyfikowania i ochrony plików](../deploy-use/deploy-aip-scanner.md). 

- Teraz możesz ustawić różne pod kątem oznaczeń wizualnych programu Word, Excel, PowerPoint i Outlook przy użyciu zmiennej instrukcji "If.App" w ciągu tekstowym oraz identyfikowanie typu aplikacji. [Więcej informacji](../deploy-use/configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)

- Obsługa [ustawienie zasad](../deploy-use/configure-policy-settings.md), **wyświetlany pasek Information Protection w aplikacjach pakietu Office**. Gdy to ustawienie jest wyłączone, użytkownicy wybierają etykiety z **Chroń** przycisk na Wstążce.

- Nowe zaawansowane ustawienia klienta (w wersji zapoznawczej) można włączyć klasyfikacji, aby uruchomić w sposób ciągły w tle. Jeśli to ustawienie jest włączone dla aplikacji pakietu Office klasyfikacji automatycznej i zalecanej działa w sposób ciągły w tle, zamiast uruchamiać podczas zapisywania dokumentów. Ta zmiana w zachowaniu można teraz zastosować klasyfikacji automatycznej i zalecanej do dokumentów, które są przechowywane w usłudze SharePoint Online. [Więcej informacji](client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background)

- Nowe zaawansowane ustawienia klienta, program Outlook nie ma zastosowania etykiety domyślnej, która jest skonfigurowana w zasadach usługi Azure Information Protection. Zamiast tego programu Outlook, można zastosować różne etykiety domyślne lub brak etykiety. [Więcej informacji](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) 

- Dla aplikacji pakietu Office podczas określania uprawnień niestandardowych, można teraz Przeglądaj i wybierz użytkowników z ikony książki adresowej. Wybranie tej opcji powoduje parzystości wrażenia użytkownika podczas określania uprawnień niestandardowych za pomocą Eksploratora plików.

- Obsługa metodę całkowicie nieinterakcyjnych authentication dla kont usług, które korzystają z programu PowerShell i nie można udzielić **logować się lokalnie** prawo. Ta metoda uwierzytelniania, musisz korzystać z nowych *tokenu* parametrem [Set-AIPAuthentication](/powershell/module/azureinformationprotection/Set-AIPAuthentication), i uruchom skrypt programu PowerShell jako zadania. [Więcej informacji](../rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)

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

## <a name="version-110560"></a>Wersja 1.10.56.0

**Wydana**: 2017-09-18

Ta wersja zawiera wersję MSIPC 1.0.3219.0619 klienta usługi RMS.

**Nowe funkcje**:

- Obsługa nowych warunków DLP usługi Office 365, które można skonfigurować dla etykiety. Aby uzyskać więcej informacji, zobacz [Konfigurowanie warunków dla etykiety usługi Azure Information Protection](../deploy-use/configure-policy-classification.md).

- Pomoc techniczna dla etykiety, które są skonfigurowane dla akcji zdefiniowane przez użytkownika. Dla programu Outlook ta etykieta automatycznie zastosuje opcję programu Outlook nie przesyłaj dalej. Dla programu Word, Excel, PowerPoint i Eksploratora plików tej etykiety monituje użytkownika o podanie uprawnień niestandardowych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiety usługi Azure Information Protection do ochrony](../deploy-use/configure-policy-protection.md).

- Etykiety obsługują wiele języków. Począwszy od 30 sierpnia 2017 r. [domyślne zasady](../deploy-use/configure-policy-default.md) obejmuje obsługę wielu języków wyświetlanych przez tę wersję klienta dla użytkowników. Aby użytkownikom były wyświetlane etykiety w ich własnym języku preferowanym z domyślnych zasad przed tą datą i etykiety, które można skonfigurować, zobacz [Konfigurowanie etykiet w różnych językach w usłudze Azure Information Protection](../deploy-use/configure-policy-languages.md).

- Etykiety są wyświetlane z **Chroń** przycisk na Wstążce pakietu Office, oprócz wyświetlania na pasku usługi Information Protection. 

- Ochrona natywna dla następujących typów plików programu Visio: .vsdm vsdx, .vssm, .vssx, .vstm, .vstx

- Obsługiwane konfiguracje Zaawansowanego klienta, które można skonfigurować w witrynie Azure portal. Te konfiguracje obejmują następujące czynności:
    
    - [Ukryj lub Pokaż przycisk nie przesyłaj dalej w programie Outlook](../rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook)
    
    - [Być dostępne lub niedostępne opcje uprawnień niestandardowych dla użytkowników](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users)
    
    - [Trwałe ukrycie paska usługi Azure Information Protection](../rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar)
    
    - [Włącz zalecana klasyfikacja w programie Outlook](../rms-client/client-admin-guide-customizations.md#enable-recommended-classification-in-outlook)

- W przypadku programu PowerShell obsługują aby oznaczyć pliki nieinterakcyjny przy użyciu nowych poleceń cmdlet programu PowerShell [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) i [Clear-AIPAuthentication](/powershell/module/azureinformationprotection/clear-aipauthentication). Aby uzyskać więcej informacji jak używać tych poleceń cmdlet, zobacz [sekcji PowerShell](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) podręcznika administratora.

- Dla poleceń cmdlet programu PowerShell [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) i [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification), istnieją nowe parametry: **właściciela** i **PreserveFileDetails** . Parametry te pozwalają określić adres e-mail właściciela niestandardowej właściwości i pozostawienie niezmienionej dokumentów, które etykiety daty.

**Poprawki**:

Poprawki dotyczące stabilności i dla konkretnych scenariuszy, które obejmują:

- Obsługa ochrony ogólnej dużych plików, które wcześniej może spowodować uszkodzenie, jeśli jest większa niż 1 GB. Teraz rozmiar pliku jest ograniczony tylko ilością dostępnego miejsca na dysku i dostępnej pamięci. Aby uzyskać więcej informacji na temat ograniczenia rozmiaru plików, zobacz [rozmiary obsługiwane w przypadku ochrony plików](client-admin-guide-file-types.md#file-sizes-supported-for-protection) w podręczniku administratora.

- Przeglądarka klienta usługi Azure Information Protection otwiera chronionych plików PDF (ppdf) jako tylko do wyświetlania.

- Obsługa etykietowanie i ochronę plików przechowywanych na serwerze programu SharePoint.

- Znaki wodne są teraz obsługiwane w wielu wierszach. Ponadto oznaczenia wizualne są teraz stosowane do dokumentu na [najpierw Zapisz tylko](../deploy-use/configure-policy-markings.md#when-visual-markings-are-applied) zamiast każdym razem, gdy dokument zostanie zapisany.

- **Uruchom diagnostykę** opcji **Pomoc i opinie** okno dialogowe jest zastępowany **Resetowanie ustawień**. Zachowanie dla tej akcji została zmieniona na obejmują wylogowywania użytkownika i usunięcie zasad usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz [więcej informacji na temat opcji resetowania ustawień](..\rms-client\client-admin-guide.md#more-information-about-the-reset-settings-option) w podręczniku administratora.

- Obsługa uwierzytelniania serwera proxy.

Poprawki dla wygody użytkowników, które obejmują:

- Wiadomość e-mail sprawdzania poprawności, gdy użytkownicy określić uprawnienia niestandardowe. Ponadto wiele adresów e-mail, można teraz określić, naciskając klawisz Enter.

- Etykieta nadrzędna nie jest wyświetlany, gdy jej etykiet podrzędnych jest skonfigurowany do ochrony, a klient nie ma wersji pakietu Office, który obsługuje ochronę. 

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o instalowaniu i używaniu klienta: 

- Użytkownicy: [pobieranie i instalowanie klienta](install-client-app.md)

- Administratorzy: [Podręcznik administratora klienta usługi Azure Information Protection](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
