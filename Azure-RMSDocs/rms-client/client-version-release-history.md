---
title: Klient usługi Azure Information Protection — wersja Historia wersji i zasady pomocy technicznej
description: Zobacz, co jest nowe lub zostały zmienione w wersji klienta usługi Azure Information Protection dla Windows i zrozumieć zasady świadczenia pomocy technicznej.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/27/2018
ms.topic: conceptual
ms.service: information-protection
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 94120417c5e2e61f1d28fc16d714ec1c91a4ed0f
ms.sourcegitcommit: 630f03a91f84d79219e04b4085bdfb5bc6478e88
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54011977"
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Klient usługi Azure Information Protection: Wydania wersji zasad historii i pomoc techniczna

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, systemu Windows Server 2012, Windows Server 2008 R2*

Zespół pracujący nad usługą Azure Information Protection regularnie aktualizuje klienta usługi Azure Information Protection w celu wprowadzenia poprawek i dodania nowych funkcji. 

Można pobrać najnowszej ogólnodostępnej wersji i bieżącej wersji zapoznawczej (jeśli jest dostępny) z [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Po krótkiej chwili zazwyczaj kilka tygodni, najnowszej wersji ogólnodostępnej znajduje się również w wykazie usługi Microsoft Update (kategoria: **Usługa Azure Information Protection**). To uwzględnienie w wykazie oznacza, że uaktualnienie klienta za pomocą programu WSUS lub programu Configuration Manager lub innych mechanizmów wdrażania oprogramowania, korzystających z usługi Microsoft Update.

Aby uzyskać więcej informacji, zobacz [uaktualnianie i obsługa klienta usługi Azure Information Protection](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client).

### <a name="servicing-information-and-timelines"></a>Obsługa informacji i osie czasu

Ogólna dostępność (GA) każdej wersji klienta usługi Azure Information Protection jest obsługiwana przez maksymalnie sześć miesięcy po kolejnych wersji Ogólnodostępnej. Dokumentacja nie zawiera informacji na temat nieobsługiwane wersje klienta. Poprawki i nowe funkcje są one zawsze stosowane do najnowszej wersji ogólnie dostępnej wersji i nie będą stosowane do starszych wersji ogólnie dostępnej wersji.

Wersje zapoznawcze nie powinny być wdrażane dla użytkowników końcowych w sieciach produkcyjnych. Użyj najnowszej wersji zapoznawczej oraz ich wypróbowanie nowymi funkcjami i poprawkami, które zostaną wprowadzone w kolejnej Ogólnodostępnej wersji. Wersji zapoznawczych, które nie są aktualne, nie są obsługiwane.

### <a name="release-history"></a>Historia wersji

Skorzystaj z poniższych informacji, zobacz, co jest nowe lub zostały zmienione w obsługiwanej wersji klienta usługi Azure Information Protection dla Windows. Najnowsza wersja jest wyświetlana na początku listy. 

> [!NOTE]
> Niewielkie poprawki nie są wyświetlane, dlatego jeśli wystąpi problem z klientem usługi Azure Information Protection, zalecamy sprawdzenie, czy problem został rozwiązany za pomocą najnowszej wersji ogólnie dostępnej. Jeśli problem będzie się powtarzać, sprawdź bieżącą wersję (wersja zapoznawcza).
>  
> Aby uzyskać pomoc techniczną, zobacz [opcje pomocy technicznej i zasoby społecznościowe](../information-support.md#support-options-and-community-resources) informacji. Zachęcamy także do kontaktowania się z naszym zespołem ds. usługi Azure Information Protection w [witrynie Yammer](https://www.yammer.com/askipteam/).

## <a name="version-141510"></a>Wersja 1.41.51.0

> [!TIP]
> Zainteresowani oceny klienta etykietowania ujednolicone usługi Azure Information Protection, ponieważ etykiety są publikowane w Centrum zgodności i zabezpieczeń usługi Office 365? Zobacz [usługi Azure Information Protection unified etykietowania klienta: Informacje o wersji wersji](unifiedlabelingclient-version-release-history.md).

**Wydana**: 11 27 2018

Ta wersja zawiera wersję MSIPC 1.0.3592.627 klienta usługi RMS.

**Nowe funkcje:**

- Klient usługi Azure Information Protection, domyślnie teraz chroni pliki PDF przy użyciu standardu ISO do szyfrowania plików PDF. Wcześniej należało włączyć obsługę tego za pomocą zaawansowanych ustawień klienta.
    
    Jeśli klient powraca do ochrony plików PDF, korzystając z rozszerzeniem nazwy pliku ppdf, należy używać tego samego [Zaawansowane ustawienia klienta](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption), ale określono **False**.

- Obsługa [centralnej funkcji raportowania](../reports-aip.md) dla funkcji analizy usługi Azure Information Protection ogłoszeniem na konferencji Microsoft Ignite.

- W programie Excel teraz również obsługuje [oznaczenia wizualnego](../configure-policy-markings.md)s w różnych kolorach.

- Dla istniejących wdrożeń S/MIME nowy Zaawansowane ustawienia (w wersji zapoznawczej) Aby skonfigurować etykietę klienta automatyczne stosowanie ochrony szyfrowania S/MIME w programie Outlook. [Więcej informacji](client-admin-guide-customizations.md#configure-a-label-to-apply-smime-protection-in-outlook)

- Nowe zaawansowane ustawienia klienta, jako alternatywę do edytowania rejestru, aby zapobiec monity o logowanie dla usługi Azure Information Protection [odłączone komputery](client-admin-guide-customizations.md#support-for-disconnected-computers).

**Poprawki**:

- Klient usługi Azure Information Protection nie jest już wyklucza msg, RAR i zip rozszerzeń nazw plików dla Eksploratora plików (kliknij prawym przyciskiem myszy) i poleceń programu PowerShell. Jednak te rozszerzenia nazw plików pozostaną wykluczone domyślnie skanera. 

- Klient usługi Azure Information Protection można wyłączyć ochronę wielu plików (Wybór wielokrotny i folderu zawierającego pliki chronione) podczas używania Eksploratora plików kliknij prawym przyciskiem myszy.

- Dla programu Excel:
    
    - Oznaczenia wizualne są teraz stosowane, jeśli zapiszesz arkusz kalkulacyjny podczas edytowania komórki.
    
    - Excel 2010: Gdy arkusz kalkulacyjny jest chroniony za pomocą współautorem [poziom uprawnień](../configure-usage-rights.md#rights-included-in-permissions-levels), **Usuń etykietę** przycisk jest teraz dostępna, kliknij prawym przyciskiem myszy plik, a wybranie **Klasyfikuj i Chroń**.

- Zaawansowane ustawienia klienta, które mogą [usuwanie nagłówków i stopek z innych rozwiązań etykietowania](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions) obsługuje teraz układy niestandardowe.

**Dodatkowe zmiany:**

- Jeśli harmonogram skanera została ustawiona na **zawsze**, jest teraz opóźnienie równej 30 sekund między skanowania.

- Skaner nie jest już zmienia właściciela usługi Rights Management dla plików, które go etykiet, gdy plik jest już chroniona.

## <a name="version-137190"></a>Wersja 1.37.19.0

**Wydana**: 09/17/2018 r.

Ta wersja zawiera wersję MSIPC 1.0.3592.627 klienta usługi RMS.

**Nowe funkcje**: 

- Obsługa standardu ISO do szyfrowania plików PDF, konfigurując nową [Zaawansowana konfiguracja klienta](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption). Jeśli ta opcja jest ustawiona **True**, dokumentów PDF, które można chronić zachować ich rozszerzenia nazwy pliku PDF (zamiast Zmień ppdf) i mogą być otwierane przez czytniki PDF, obsługujące tego standardu ISO. Obecnie należy poinstruować użytkowników, aby otworzyć tych chronionych plików PDF ręcznie przy użyciu podglądu usługi Azure Information Protection. Aby ułatwić użytkownikom to, kiedy adresat otworzy tych chronionych plików PDF, zobaczą strony z ikon w celu wybrania systemu operacyjnego.

- Obsługa nowych typów informacji poufnych klasyfikować dokumenty, które zawierają dane osobowe. [Więcej informacji](../configure-policy-classification.md#sensitive-information-types-that-require-a-minimum-version-of-the-client) 

- Etykiety umożliwiające objęcie ochroną teraz wyświetlane w aplikacji pakietu Office 2016 (minimalna wersja 1805, kompilacja 9330.2078) po użytkownik ma przypisaną licencję usługi Azure Rights Management (nazywanego także usługi Azure Information Protection dla usługi Office 365).

- Obsługa etykietowania **Strict otwartego dokumentu XML** format w plikach programu Word, Excel i PowerPoint. Aby uzyskać więcej informacji na temat formatów Open XML, zobacz w blogu pakietu Office, [nowe opcje format pliku w nowy pakiet Office](https://www.microsoft.com/en-us/microsoft-365/blog/2012/08/13/new-file-format-options-in-the-new-office/). 

- Obsługa plików, które są chronione przez Secure Islands, gdy te pliki są inne niż dokumentów PDF i pakietu Office. Na przykład chronionych plików tekstowych i obrazów. Lub rozszerzenie nazwy pliku plików, które mają plik pfile. Ta obsługa umożliwia nowe scenariusze, takie jak skanera usługi Azure Information Protection będzie mogła sprawdzić te pliki do poufnych informacji i automatycznie relabeling je do usługi Azure Information Protection. [Więcej informacji](client-admin-guide-customizations.md#support-for-files-protected-by-secure-islands)

- Nowe zaawansowane ustawienia klienta do usunięcia, nagłówki i stopki, które zostały zastosowane do dokumentów przez innych rozwiązań etykietowania. [Więcej informacji](client-admin-guide-customizations.md#remove-headers-and-footers-from-other-labeling-solutions)

- Skanera usługi Azure Information Protection:

    - Nowe polecenie cmdlet, [AIPScanner aktualizacji](/powershell/module/azureinformationprotection/Update-AIPScanner): Wymagane do uruchamiania raz po uaktualnianie z poprzedniej wersji Ogólnodostępnej (1.29.5.0) lub wcześniej.
    
    - Nowe polecenie cmdlet, [Get AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus): Pobiera bieżący stan usługi skanera.  
    
    - Nowe polecenie cmdlet, [Start AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan): Powoduje, że skanera można uruchomić na czas cykl skanowania w poszukiwaniu, kiedy harmonogram ustawiono na ręcznie.
    
    - Gdy ISO standard jest używany do szyfrowania plików PDF, dokumentów PDF są teraz chronione domyślnie.
    
    - Program SharePoint Server 2010 jest obsługiwana w przypadku klientów, którzy mają [rozszerzoną obsługę w tej wersji programu SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).
    
- Obsługa nowej **usługi Azure Information Protection — węzły (wersja zapoznawcza)** bloku w witrynie Azure portal, która umożliwia Zarządzanie skanerami z centralnej lokalizacji. Informacje z Twojej wdrożonej skanerów, które mają łączność do platformy Azure jest aktualizowana co pięć minut. Z tego bloku można uruchomić skanera jednorazowe skanowania, ponownego skanowania wszystkich plików, sprawdź stan skaner i wyświetlić szybkość skanowania.

**Poprawki**

- Skanera usługi Azure Information Protection:
    
    - W przypadku dokumentów, które są chronione w bibliotekach programu SharePoint, jeśli *DefaultOwner* parametr nie jest używany do repozytorium danych, wartość edytora programu SharePoint jest teraz używana jako wartość domyślną, zamiast autora.
    
    - Skaner raporty zawierają "Ostatnio modyfikowany przez", dokumentów pakietu Office.
    
    - Można teraz chronić wszystkie typy plików za pomocą `*` symboli wieloznacznych podczas edycji rejestru zgodnie z opisem w [edycji rejestru skanera](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner) sekcji.

- Podczas wyświetlania wiadomości e-mail przy użyciu ikony strzałek następnej i poprzedniej pozycji na pasku narzędzi Szybki dostęp pokazywane jest prawidłowa etykieta dla każdej wiadomości e-mail.

- Podczas klasyfikowania i ochrony za pomocą Eksploratora plików, programu PowerShell lub skaner metadane dokumentu pakietu Office jest ono usuwane lub szyfrowane.

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

- **Prześlij nam opinię** łącze w **Pomoc i opinie** okno dialogowe zostanie usunięty. Tymczasowo zastąpione **zgłosić problem** wiadomość e-mail, domyślnie wysyłane do firmy Microsoft. Od grudnia 2018, **zgłosić problem** opcja nie jest wyświetlany domyślnie, ale można dodać z [Zaawansowane ustawienia klienta](client-admin-guide-customizations.md#add-report-an-issue-for-users) gdzie Określ ciąg HTTP dla tego połączenia. Na przykład dostosowanej strony sieci web, przeznaczonego dla użytkowników, aby zgłosić problemy lub adres e-mail, który prowadzi do pomocy technicznej. 

## <a name="version-12950"></a>Wersja 1.29.5.0 

**Wydana**: 06/26/2018 r.

Ta wersja zawiera wersję MSIPC 1.0.3403.1224 klienta usługi RMS.

**Poprawki**:

- W wersjach programu Outlook 16.0.9324.1000 i nowsze (kliknij polecenie do uruchomienia), na pasku usługi Azure Information Protection obsługuje najnowsze opcje wyświetlania monitor, które mogłyby prowadzić wcześniej na pasku wyświetlane poza aplikację Outlook.

- Oznaczenia wizualne, które można skonfigurować [według typu aplikacji pakietu Office](../configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook) teraz zastąpić nagłówka lub stopki uprzednio zastosowaną przez etykiety usługi Azure Information Protection.

- Gdy już nazywa plik programu Excel i stosuje się etykietę oznaczeń wizualnych, nowy arkusz ma teraz oznaczeń wizualnych etykiety zastosowane.

- Kiedy używasz Zaawansowane ustawienia klienta dotyczącego [etykiety dokumentu pakietu Office przy użyciu istniejącej właściwości niestandardowej](client-admin-guide-customizations.md#label-an-office-document-by-using-an-existing-custom-property), etykietowania automatycznego nie zastępuje ręcznego etykietowania.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o instalowaniu i używaniu klienta: 

- Dla użytkowników: [Pobieranie i instalowanie klienta](install-client-app.md)

- Dla administratorów: [Podręcznik administratora klienta usługi Azure Information Protection](client-admin-guide.md)
