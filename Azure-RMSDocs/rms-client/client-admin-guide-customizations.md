---
title: Niestandardowe konfiguracje klienta usługi Azure Information Protection
description: Informacje na temat dostosowywania klienta usługi Azure Information Protection dla systemu Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 9386889c41706e0603c5e758be09b0d2baafc7e8
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54394370"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-client"></a>Podręcznik administratora: Niestandardowe konfiguracje klienta usługi Azure Information Protection

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, systemu Windows Server 2012, Windows Server 2008 R2*

Poniższe informacje służą do tworzenia zaawansowanych konfiguracji, które mogą być wymagane w przypadku określonych scenariuszy lub podzbiorów użytkowników podczas zarządzania klientem usługi Azure Information Protection.

Niektóre z tych ustawień wymagają edycji rejestru. Inne korzystają z ustawień zaawansowanych, które należy skonfigurować w witrynie Azure Portal, a następnie opublikować do pobrania przez klientów.  

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>Jak skonfigurować zaawansowane ustawienia konfiguracji klienta w portalu

1. Jeśli użytkownik jeszcze tego nie zrobiono, w nowym oknie przeglądarki [Zaloguj się do witryny Azure portal](../configure-policy.md#signing-in-to-the-azure-portal), a następnie przejdź do **usługi Azure Information Protection** bloku.

2. Z **klasyfikacje** > **etykiety** opcji menu: Wybierz **zasady**.

3. Na **usługi Azure Information Protection — zasady** bloku, wybierz menu kontekstowe (**...** ) obok zasady zawierającej ustawienia zaawansowane. Następnie wybierz opcję **Ustawienia zaawansowane**.
    
    Możesz skonfigurować ustawienia zaawansowane dla zasad globalnych i zasad z określonym zakresem.

4. W bloku **Ustawienia zaawansowane** wpisz nazwę i wartość ustawienia zaawansowanego, a następnie wybierz opcję **Zapisz i zamknij**.

5. Upewnij się, że użytkownicy tych zasad, uruchom ponownie wszystkie otwarte wcześniej aplikacje pakietu Office.

6. Jeśli już nie wymagają tego ustawienia i chcesz przywrócić zachowanie domyślne: Na **Zaawansowane ustawienia** bloku, wybierz menu kontekstowe (**...** ) obok ustawienia możesz nie są już potrzebne, a następnie wybierz **Usuń**. Następnie kliknij przycisk **Zapisz i Zamknij**.

#### <a name="available-advanced-client-settings"></a>Dostępne zaawansowane ustawienia klienta

|Ustawienie|Scenariusz i instrukcje|
|----------------|---------------|
|DisableDNF|[Ukryj lub Pokaż przycisk nie przesyłaj dalej w programie Outlook](#hide-or-show-the-do-not-forward-button-in-outlook)|
|EnableBarHiding|[Trwałe ukrycie paska usługi Azure Information Protection](#permanently-hide-the-azure-information-protection-bar)|
|EnableCustomPermissions|[Być dostępne lub niedostępne opcje uprawnień niestandardowych dla użytkowników](#make-the-custom-permissions-options-available-or-unavailable-to-users)|
|EnablePDFv2Protection|[Nie Chroń pliki PDF przy użyciu standardu ISO do szyfrowania plików PDF](#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption)|
|LabelbyCustomProperty|[Migrowanie etykiety z Secure Islands i innych rozwiązań etykietowania](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|LabelToSMIME|[Konfigurowanie etykiety w celu zastosowania ochrony szyfrowania S/MIME w programie Outlook](#configure-a-label-to-apply-smime-protection-in-outlook)|
|OutlookDefaultLabel|[Ustaw różne etykiety domyślne dla programu Outlook](#set-a-different-default-label-for-outlook)|
|OutlookRecommendationEnabled|[Włącz zalecana klasyfikacja w programie Outlook](#enable-recommended-classification-in-outlook)|
|PostponeMandatoryBeforeSave|[Usuń "Nie now" dla dokumentów, jeśli używasz obowiązkowego etykietowania](#remove-not-now-for-documents-when-you-use-mandatory-labeling)|
|ProcessUsingLowIntegrity|[Wyłącz poziom o niskiej integralności skanera](#disable-the-low-integrity-level-for-the-scanner)|
|PullPolicy|[Obsługa odłączonych komputerów](#support-for-disconnected-computers)
|RemoveExternalContentMarkingInApp|[Usuwanie nagłówków i stopek z innych rozwiązań etykietowania](#remove-headers-and-footers-from-other-labeling-solutions)|
|ReportAnIssueLink|[Dodaj "Zgłoś problem" dla użytkowników](#add-report-an-issue-for-users)|
|RunPolicyInBackground|[Włącz klasyfikacji, aby uruchomić w sposób ciągły w tle](#turn-on-classification-to-run-continuously-in-the-background)|
|SyncPropertyName|[Etykieta dokumentu pakietu Office przy użyciu istniejącej właściwości niestandardowej](#label-an-office-document-by-using-an-existing-custom-property)|
|SyncPropertyState|[Etykieta dokumentu pakietu Office przy użyciu istniejącej właściwości niestandardowej](#label-an-office-document-by-using-an-existing-custom-property)|

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>Zapobieganie monitom o logowanie dla komputerów korzystających tylko z usługi AD RMS

Domyślnie klient usługi Azure Information Protection automatycznie próbuje połączyć się z usługą Azure Information Protection. W przypadku komputerów, które komunikują się tylko z usługą AD RMS, ta konfiguracja może powodować wyświetlanie użytkownikom zbędnego monitu o logowanie. Ten monit logowania można zapobiec, edytując rejestr.

 - Znajdź następującą nazwę wartości, a następnie ustaw dane wartości na **0**:
    
    **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Niezależnie od tego ustawienia klienta usługi Azure Information Protection nadal postępuje zgodnie ze standardowym [procesem odnajdowania usługi RMS](client-deployment-notes.md#rms-service-discovery) można znaleźć jej klastra usług AD RMS.

## <a name="sign-in-as-a-different-user"></a>Zaloguj się jako inny użytkownik

W środowisku produkcyjnym użytkownik nie ma zazwyczaj potrzeby logowania się jako inny użytkownik w przypadku korzystania z klienta usługi Azure Information Protection. Jednak jako administrator możesz potrzebować możliwości zalogowania się jako inny użytkownik podczas fazy testowania. 

Możesz zweryfikować konto, które jest obecnie zalogowany za pomocą **Microsoft Azure Information Protection** okno dialogowe: Otwórz aplikację pakietu Office i na karcie **Narzędzia główne** w grupie **Ochrona** kliknij kolejno przyciski **Chroń** oraz **Pomoc i opinie**. Nazwa konta jest widoczna w sekcji **Stan klienta**.

Pamiętaj także o sprawdzeniu wyświetlonej nazwy domeny konta użytego do zalogowania. Fakt, że logowanie następuje przy użyciu prawidłowej nazwy konta, ale niewłaściwej domeny, można łatwo przeoczyć. W przypadku użycia niewłaściwego konta może wystąpić problem z pobraniem zasad usługi Azure Information Protection albo nie będą widoczne oczekiwane etykiety lub zachowania.

Aby zalogować się jako inny użytkownik:

1. Przejdź do **%localappdata%\Microsoft\MSIP** i Usuń **TokenCache** pliku.

2. Uruchom ponownie wszystkie otwarte aplikacje pakietu Office i zaloguj się przy użyciu innego konta użytkownika. Jeśli w aplikacji pakietu Office nie został wyświetlony monit o zalogowanie się do usługi Azure Information Protection, wróć do okna dialogowego **Microsoft Azure Information Protection** i kliknij przycisk **Zaloguj** w zaktualizowanej sekcji **Stan klienta**.

Dodatkowo:

- Jeśli klient usługi Azure Information Protection jest nadal zalogowany za pomocą starego konta po wykonaniu tych kroków, Usuń wszystkie pliki cookie z programu Internet Explorer, a następnie powtórz kroki 1 i 2.

- Jeśli używasz rejestracji jednokrotnej, należy wylogować się z Windows i zaloguj się przy użyciu innego konta użytkownika po usunięciu plik tokenu. Klient usługi Azure Information Protection przeprowadzi automatyczne uwierzytelnienie przy użyciu aktualnie zalogowanego konta użytkownika.

- To rozwiązanie jest obsługiwane w przypadku logowania się jako inny użytkownik z tej samej dzierżawy. Nie jest ono obsługiwane w przypadku logowania się jako inny użytkownik z innej dzierżawy. Do testowania usługi Azure Information Protection z wieloma dzierżawami użyj różnych komputerów.

- Możesz użyć **zresetować ustawienia** opcję **Pomoc i opinie** wylogowania się i usunąć aktualnie pobrane zasady usługi Azure Information Protection.


## <a name="enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses"></a>Wymusić tryb z samą ochroną, gdy Twoja organizacja ma różne licencji

Jeśli Twoja organizacja nie ma żadnych licencji usługi Azure Information Protection, ale mają licencje usługi Office 365, która obejmuje usługi Azure Rights Management w celu zapewnienia ochrony danych, klient usługi Azure Information Protection dla Windows automatycznie uruchamia w [tryb z samą ochroną](client-protection-only-mode.md).

Jednak jeśli Twoja organizacja ma subskrypcję usługi Azure Information Protection, domyślnie wszystkie komputery Windows można pobrać zasad usługi Azure Information Protection. Nie usługi Azure Information Protection, w których klient ma licencję, sprawdzenie i wymuszania. 

W przypadku niektórych użytkowników, którzy nie mają licencji usługi Azure Information Protection, ale mieć licencję usługi Office 365, która obejmuje usługę Azure Rights Management, należy edytować rejestr na komputerach tych użytkowników, aby uniemożliwić użytkownikom uruchamianie licencjami Klasyfikacja i etykietowanie funkcji z usługi Azure Information Protection.

Znajdź następującą nazwę wartości i ustaw dane wartości **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Ponadto należy sprawdzić, czy te komputery nie mają plik o nazwie **Policy.msip** w **%LocalAppData%\Microsoft\MSIP** folderu. Jeśli ten plik już istnieje, należy go usunąć. Ten plik zawiera zasady usługi Azure Information Protection i mogło zostać pobrane przed edytowania rejestru, czy klient usługi Azure Information Protection został zainstalowany z opcją pokaz.

## <a name="add-report-an-issue-for-users"></a>Dodaj "Zgłoś problem" dla użytkowników

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Po określeniu następującego ustawienia klienta zaawansowanego, użytkownicy widzą **zgłosić problem** opcji, które można wybierać **Pomoc i opinie** klienta, okno dialogowe. Określ ciąg HTTP dla tego połączenia. Na przykład dostosowanej strony sieci web, przeznaczonego dla użytkowników, aby zgłosić problemy lub adres e-mail, który prowadzi do pomocy technicznej. 

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **ReportAnIssueLink**

- Wartość: **\<HTTP string>**

Przykładowa wartość dla witryny sieci Web: `https://support.contoso.com`

Przykładowa wartość dla adresu e-mail: `mailto:helpdesk@contoso.com`

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ukryj opcję menu Klasyfikuj i chroń w Eksploratorze plików systemu Windows

Utwórz następującą nazwę wartości DWORD (z dowolnymi danymi wartości):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Obsługa odłączonych komputerów

Domyślnie klient usługi Azure Information Protection automatycznie próbuje połączyć się z usługą Azure Information Protection, aby pobrać najnowsze zasady usługi Azure Information Protection. W przypadku komputerów, które znasz, nie będzie można połączyć się z Internetem przez czas można zapobiec próby połączenia z usługą, edytując rejestr klienta. 

Należy pamiętać, że bez połączenia internetowego klient nie może zastosować ochronę (lub wyłączania ochrony) przy użyciu klucza oparta na chmurze w Twojej organizacji. Zamiast tego klient może mieć maksymalnie przy użyciu etykiet, które są stosowane tylko klasyfikacja lub ochrony, który używa [HYOK](../configure-adrms-restrictions.md).

Można zapobiec monit logowania do usługi Azure Information Protection przy użyciu [Zaawansowane ustawienia klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal) , należy skonfigurować w witrynie Azure portal, a następnie pobrania zasad dla komputerów. Ewentualnie można zapobiec ten monit logowania, edytując rejestr.

- Aby skonfigurować zaawansowane ustawienia klienta:
    
    1. Wprowadź następujące parametry:
    
        - Klucz: **PullPolicy**
        
        - Wartość: **False**
    
    2. Pobierz zasady korzystając z tego ustawienia i zainstalować na komputerach, korzystając z instrukcji.

- Alternatywnie aby edytować rejestr:
    
    - Znajdź następującą nazwę wartości, a następnie ustaw dane wartości na **0**:
    
        **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 


Klient musi mieć prawidłowy plik zasad o nazwie **Policy.msip**w **%LocalAppData%\Microsoft\MSIP** folderu.

Można wyeksportować zasad globalnych lub zasad o określonym zakresie w witrynie Azure portal, a następnie skopiuj wyeksportowany plik na komputerze klienckim. Ta metoda umożliwia również zastąpienie pliku zasad wiadomość limit z date najnowsze zasady. Eksportowanie zasad nie obsługuje jednak scenariusz, w którym użytkownik należy do więcej niż jedna zasada o określonym zakresie. Należy także zauważyć, jeśli użytkownicy wybiorą **Resetowanie ustawień** opcję [Pomoc i opinie](client-admin-guide.md#help-and-feedback-section), ta akcja usuwa plik zasad i renderuje klienta przestanie działać, dopóki ręcznie zastąpić plik zasad lub Klient łączy się z usługą, aby pobrać zasady.

Podczas eksportowania zasady w witrynie Azure portal, plik z rozszerzeniem zip jest pobierana, który zawiera wiele wersji zasad. Te wersje zasad odpowiadają różne wersje klienta usługi Azure Information Protection:

1. Rozpakuj plik i skorzystaj z poniższej tabeli, aby zidentyfikować plik zasad, który należy. 
    
    |Nazwa pliku|Odpowiednia wersja klienta|
    |--------------------------|---------------------------------------------|
    |Policy1.1.msip |w wersji 1.2|
    |Policy1.2.msip |w wersji 1.3 1.7|
    |Policy1.3.msip |w wersji 1.8 1,29|
    |Policy1.4.msip |Wersja 1,32 i nowsze|
    
2. Zmień nazwę wskazany plik do **Policy.msip**, a następnie skopiować go do **%LocalAppData%\Microsoft\MSIP** folderu na komputerach, które mają zainstalowanego klienta usługi Azure Information Protection. 

Jeśli komputer odłączonego działa skaner usługi Azure Information Protection w wersji zapoznawczej, istnieją dodatkowych czynności konfiguracyjnych należy wykonać. Aby uzyskać więcej informacji, zobacz [ograniczeń: Skaner serwera nie może mieć połączenie z Internetem](../deploy-aip-scanner-preview.md#restriction-the-scanner-server-cannot-have-internet-connectivity) z instrukcjami wdrażania skanera.

## <a name="hide-or-show-the-do-not-forward-button-in-outlook"></a>Ukryj lub Pokaż przycisk nie przesyłaj dalej w programie Outlook

Aby skonfigurować tę opcję zaleca przy użyciu [ustawienie zasad](../configure-policy-settings.md) **Dodawanie przycisku nie przesyłaj dalej do Wstążki programu Outlook**. Jednak również mogą skonfigurować tę opcję, za pomocą [Zaawansowane ustawienia klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal) skonfigurowanego w witrynie Azure portal.

Po skonfigurowaniu tego ustawienia, ukrywa lub pokazuje **nie przesyłaj dalej** przycisk na Wstążce w programie Outlook. To ustawienie nie ma wpływu na opcję nie przekazuj menu pakietu Office.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **DisableDNF**

- Wartość: **Wartość true,** Aby ukryć przycisk, lub **False** wyświetlać przycisk

## <a name="make-the-custom-permissions-options-available-or-unavailable-to-users"></a>Być dostępne lub niedostępne opcje uprawnień niestandardowych dla użytkowników

Aby skonfigurować tę opcję zaleca przy użyciu [ustawienie zasad](../configure-policy-settings.md) **Udostępnij opcję niestandardowych uprawnień użytkownikom**. Jednak również mogą skonfigurować tę opcję, za pomocą [Zaawansowane ustawienia klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal) skonfigurowanego w witrynie Azure portal. 

Po skonfigurowaniu tego ustawienia i opublikowaniu zasad dla użytkowników, opcje uprawnień niestandardowych stają się widoczne dla użytkowników wybrać własne ustawienia ochrony lub są ukryte, aby użytkownicy nie mogą wybrać własne ustawienia ochrony, chyba że zostanie wyświetlony monit.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **EnableCustomPermissions**

- Wartość: **Wartość true,** aby uwidocznić opcji uprawnień niestandardowych, lub **False** Aby ukryć tę opcję


## <a name="permanently-hide-the-azure-information-protection-bar"></a>Trwałe ukrycie paska usługi Azure Information Protection

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. Jej używać tylko wtedy, gdy [ustawienie zasad](../configure-policy-settings.md) **wyświetlany pasek Information Protection w aplikacjach pakietu Office** ustawiono **na**.

Gdy po skonfigurowaniu tego ustawienia i opublikowaniu zasad dla użytkowników użytkownik zdecyduje, aby nie wyświetlać paska usługi Azure Information Protection w aplikacjach pakietu Office, pasek pozostanie ukryty. Takie zachowanie ma miejsce, gdy użytkownik usunie zaznaczenie opcji **Pokaż pasek** na karcie **Strona główna**, w grupie **Ochrona**, w obszarze przycisku **Chroń**. To ustawienie nie daje efektu, jeśli użytkownik zamknie pasek za pomocą ikony **Zamknij ten pasek**.

Nawet gdy pasek usługi Azure Information Protection pozostaje ukryty, użytkownicy mogą wybrać etykietę z tymczasowo wyświetlanego paska, jeśli skonfigurowano zalecaną klasyfikację lub w przypadku, gdy dokument lub wiadomość e-mail musi mieć etykietę. 

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **EnableBarHiding**

- Wartość: **True**


## <a name="enable-recommended-classification-in-outlook"></a>Włącz zalecana klasyfikacja w programie Outlook

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. To ustawienie jest w wersji zapoznawczej i mogą ulec zmianie.

Po skonfigurowaniu etykiety dla zalecana klasyfikacja, użytkownicy są monitowani o zaakceptowanie lub odrzucić zalecaną etykietę w programach Word, Excel i PowerPoint. To ustawienie rozszerza to zalecenie etykiety, można również wyświetlić w programie Outlook.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **OutlookRecommendationEnabled**

- Wartość: **True**


## <a name="set-a-different-default-label-for-outlook"></a>Ustaw różne etykiety domyślne dla programu Outlook

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Po skonfigurowaniu tego ustawienia, program Outlook nie ma zastosowania etykiety domyślnej, skonfigurowanym w zasadach usługi Azure Information Protection, ustawienia **wybierz etykietę domyślną**. Zamiast tego programu Outlook, można zastosować różne etykiety domyślne lub brak etykiety.

Aby zastosować inną etykietę, należy określić identyfikator etykiety. Wartość Identyfikatora etykieta jest wyświetlana na **etykiety** bloku, wyświetlanie lub konfigurowanie zasad usługi Azure Information Protection w witrynie Azure portal. Dla plików, które mają stosowane etykiety, można również uruchomić [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) polecenia cmdlet programu PowerShell do identyfikowania etykiety (MainLabelId lub SubLabelId). Jeśli etykieta ma etykiet podrzędnych, zawsze określać identyfikator po prostu etykiety podrzędnej, a nie etykieta nadrzędnej.

Dlatego program Outlook nie ma zastosowania etykiety domyślnej, określić **Brak**.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **OutlookDefaultLabel**

- Wartość: \< **identyfikator etykiety**> lub **None**

## <a name="configure-a-label-to-apply-smime-protection-in-outlook"></a>Konfigurowanie etykiety w celu zastosowania ochrony szyfrowania S/MIME w programie Outlook

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. To ustawienie jest w wersji zapoznawczej i mogą ulec zmianie.

Użyj tego ustawienia, tylko jeśli masz już działający [wdrożenia szyfrowania S/MIME](https://docs.microsoft.com/office365/SecurityCompliance/s-mime-for-message-signing-and-encryption) i etykiety w celu automatycznego zastosowania tej metody ochrony wiadomości e-mail, a nie ochrony usługi Rights Management z usługi Azure Information Protection. Wynikowy ochrony jest taka sama jak gdy użytkownik ręcznie wybierze opcji szyfrowania S/MIME z programu Outlook.

Ta konfiguracja wymaga określenia Klient zaawansowany, ustawienie o nazwie **LabelToSMIME** dla każdej etykiety usługi Azure Information Protection, który chcesz zastosować ochronę protokołu S/MIME. Następnie dla każdego wpisu, ustaw wartość używając następującej składni:

`[Azure Information Protection label ID];[S/MIME action]`

Wartość Identyfikatora etykieta jest wyświetlana na **etykiety** bloku, wyświetlanie lub konfigurowanie zasad usługi Azure Information Protection w witrynie Azure portal. Za pomocą protokołu S/MIME etykiety podrzędnej, należy zawsze określać identyfikator po prostu etykietę podrzędną i nie etykiecie nadrzędnej. Po określeniu etykiety podrzędnej, Etykieta nadrzędna musi być w tym samym zakresie lub w ramach globalnych zasad.

Akcja protokołu S/MIME może być:

- `Sign;Encrypt`: Aby zastosować podpisów cyfrowych i szyfrowania S/MIME

- `Encrypt`: Aby zastosować tylko szyfrowania S/MIME

- `Sign`: Aby zastosować tylko podpis cyfrowy

Przykładowe wartości, aby uzyskać identyfikator etykiety **dcf781ba-727f-4860-b3c1-73479e31912b**:

- Aby zastosować podpisów cyfrowych i szyfrowania S/MIME:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Sign;Encrypt**

- Aby zastosować tylko szyfrowania S/MIME:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Encrypt**
    
- Aby zastosować tylko podpis cyfrowy:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Sign**

W wyniku tej konfiguracji po zastosowaniu etykiety do wiadomości e-mail, S/MIME ochrona jest stosowana do wiadomości e-mail, oprócz etykiety klasyfikacji.

Jeśli etykieta, którą określasz, jest skonfigurowany do ochrony usługi Rights Management w witrynie Azure portal, ochrony szyfrowania S/MIME zastępuje ochrony usługi Rights Management tylko w programie Outlook. Dla wszystkich pozostałych scenariuszach, które obsługuje etykietowania zostaną zastosowane ochrony usługi Rights Management.

Etykiety, które mają być wyświetlane w programie Outlook w tylko, skonfigurować etykietę do stosowania jednej akcji zdefiniowane przez użytkownika z **nie przesyłaj dalej**, zgodnie z opisem w [Szybki Start: Konfigurowanie etykiety w celu użytkownikom łatwy sposób chronić wiadomości e-mail zawierające informacje poufne](../quickstart-label-dnf-protectedemail.md).

## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>Usuń "Nie now" dla dokumentów, jeśli używasz obowiązkowego etykietowania

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Kiedy używasz [ustawienie zasad](../configure-policy-settings.md) z **wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**, użytkownicy są monitowani o wybranie etykiety są najpierw zapisywania dokumentu pakietu Office i po nich Wyślij wiadomość e-mail. W przypadku dokumentów, użytkownicy mogą wybrać **nie teraz** tymczasowo odrzucać monit o wybranie etykiety i wróć do dokumentu. Jednak nie można ich zamknąć zapisany dokument bez etykiet go. 

Po skonfigurowaniu tego ustawienia, usuwa **nie teraz** opcji użytkownicy muszą wybrać etykietę, przy pierwszym zapisaniu dokumentu.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **PostponeMandatoryBeforeSave**

- Wartość: **False**

## <a name="turn-on-classification-to-run-continuously-in-the-background"></a>Włącz klasyfikacji, aby uruchomić w sposób ciągły w tle

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. To ustawienie jest w wersji zapoznawczej i mogą ulec zmianie.

Po skonfigurowaniu tego ustawienia, zmienia [domyślne zachowanie](../configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied) z jak klient usługi Azure Information Protection stosuje automatycznej i zalecanej etykiety do dokumentów: 

- Dla programu Word, Excel i PowerPoint Automatyczna klasyfikacja działa w sposób ciągły w tle.  

To zachowanie nie zmienia się dla programu Outlook.

Gdy klient usługi Azure Information Protection okresowo sprawdza, czy dokumenty dla reguł warunku, które można określić, to zachowanie umożliwia automatycznej i zalecanej klasyfikacji i ochrony dokumentów, które są przechowywane w usłudze SharePoint Online. Duże pliki również zapisać więcej szybkie ponieważ reguły warunek został już uruchomiony. 

Warunek reguły nie należy uruchamiać jako typy użytkownika w czasie rzeczywistym. Zamiast tego zadania uruchamiane okresowo jako zadanie w tle w przypadku modyfikowania dokumentu.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **RunPolicyInBackground**

- Wartość: **True**

## <a name="dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption"></a>Nie Chroń pliki PDF przy użyciu standardu ISO do szyfrowania plików PDF

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Gdy najnowszej wersji klienta usługi Azure Information Protection chroni plik PDF, wynikowy rozszerzenie nazwy pliku pozostaje jako PDF i jest zgodna z normą ISO standard do szyfrowania plików PDF. Aby uzyskać więcej informacji na temat tego standardu, zobacz sekcję **7.6 szyfrowania** z [dokument, który jest tworzony na podstawie obrazu ISO 32000 1](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf) i opublikowanych przez Incorporated systemów Adobe.

Jeśli potrzebujesz klienta, aby powrócić do zachowania w starszych wersjach klienta, który chronionych plików PDF, korzystając z rozszerzeniem nazwy pliku ppdf, należy użyć następującego ustawienia zaawansowane, wprowadzając następujące parametry:

- Klucz: **EnablePDFv2Protection**

- Wartość: **False**

Skanera usługi Azure Information Protection za pomocą nowego ustawienia należy ponownie uruchomić usługę skanera. Ponadto skaner będzie już chronić dokumenty PDF domyślnie. Jeśli chcesz, aby dokumenty PDF, które mają być chronione przez skaner, gdy EnablePDFv2Protection jest ustawiona na wartość False, należy najpierw [edytować rejestr](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner).

Aby uzyskać więcej informacji na temat nowych szyfrowania plików PDF, zobacz wpis w blogu [nową obsługę szyfrowania plików PDF z Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757).

### <a name="to-convert-existing-ppdf-files-to-protected-pdf-files"></a>Aby przekonwertować istniejące pliki ppdf chronionych plików PDF

Po klient usługi Azure Information Protection pobraniu zasad klienta za pomocą nowego ustawienia, można użyć poleceń programu PowerShell do konwersji istniejących plików ppdf plików PDF chronionych, które używają ISO standard w przypadku szyfrowania plików PDF. 

Aby korzystać z poniższych instrukcji dla plików, nie ochronę samodzielnie, konieczne jest posiadanie [prawa użytkowania usługi Rights Management](../configure-usage-rights.md) do usuwania ochrony plików lub być administratorem. Aby włączyć funkcję superużytkowników i skonfiguruj swoje konto jako administrator, zobacz [Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../configure-super-users.md).

Ponadto, korzystając z tych instrukcji dla plików, czy nie zostały zablokowane samodzielnie, staje się [wystawcą RMS](../configure-usage-rights.md#rights-management-issuer-and-rights-management-owner). W tym scenariuszu użytkownik, który był pierwotnie chroniony dokument mogą nie będzie śledzić i odwoływać go. Jeśli użytkownicy potrzebują do śledzenia i odwoływania chronionych dokumentów PDF, poproś go o ręczne usunięcie i ponowne zastosowanie etykiety za pomocą Eksploratora plików, kliknij prawym przyciskiem myszy.

Aby użyć poleceń programu PowerShell do konwersji istniejących plików ppdf plików PDF chronionych, które używają ISO standard w przypadku szyfrowania plików PDF:

1. Użyj [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) przy użyciu pliku ppdf. Przykład:
    
        Get-AIPFileStatus -Path \\Finance\Projectx\sales.ppdf

2. Z danych wyjściowych zanotuj następujące wartości parametrów:
    
   - Wartość (identyfikatora GUID) dla **SubLabelId**, jeśli taka istnieje. Jeśli ta wartość jest pusta, etykiety podrzędnej nie była używana, więc Zwróć uwagę na wartość dla **MainLabelId** zamiast tego.
    
     Uwaga: Jeśli nie ma wartości dla **MainLabelId** albo, plik nie jest etykietą. W takim przypadku można użyć [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) polecenia i [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) polecenia zamiast polecenia w kroku 3 i 4.
    
   - Wartość **RMSTemplateId**. Jeśli ta wartość jest **ograniczony dostęp**, użytkownik ma chroniony plik przy użyciu uprawnień niestandardowych, a nie z ustawień, które są skonfigurowane dla etykiety. Jeśli będziesz kontynuować, te uprawnienia niestandardowe zostaną zastąpione przez ustawienia ochrony etykiety. Zdecyduj, czy chcesz kontynuować, lub poprosić użytkownika (wartość wyświetlaną dla **RMSIssuer**) aby usunąć etykietę i zastosuj je ponownie, wraz z ich oryginalnego uprawnienia niestandardowe.

3. Usunąć etykietę, za pomocą [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) z *RemoveLabel* parametru. Jeśli używasz [ustawienie zasad](../configure-policy-settings.md) z **użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę**, należy także określić  *Uzasadnienie* parametru z powodu. Przykład: 
    
        Set-AIPFileLabel \\Finance\Projectx\sales.ppdf -RemoveLabel -JustificationMessage 'Removing .ppdf protection to replace with .pdf ISO standard'

4. Ponownie oryginalnej etykiety, określając wartość dla etykiety, który został zidentyfikowany w kroku 1. Przykład:
    
        Set-AIPFileLabel \\Finance\Projectx\sales.pdf -LabelId d9f23ae3-1234-1234-1234-f515f824c57b

Plik zachowuje rozszerzenie nazwy pliku PDF, ale jest klasyfikowany tak jak poprzednio, i jest chroniony przy użyciu standardu ISO do szyfrowania plików PDF.

## <a name="support-for-files-protected-by-secure-islands"></a>Obsługa plików chronionych przez Secure Islands

Ta opcja konfiguracji jest obecnie dostępna w wersji zapoznawczej i może ulec zmianie.

Jeśli używasz Secure Islands do ochrony dokumentów, może być ochroną tekstu i pliki obrazów oraz pliki objęte ochroną ogólną, w wyniku tej ochrony. Na przykład pliki, które mają rozszerzenie nazwy pliku, ptxt, pjpeg lub pfile. Gdy w następujący sposób edytowania rejestru usługi Azure Information Protection może odszyfrować te pliki:


Dodaj następującą wartość DWORD o **EnableIQPFormats** w następującej ścieżce rejestru i Ustaw dane wartości **1**:

- Dla 64-bitowej wersji systemu Windows: HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\MSIP

- Dla 32-bitowej wersji systemu Windows: HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\MSIP

W wyniku tego w rejestrze obsługiwane są następujące scenariusze:

- Przeglądarka usługi Azure Information Protection można otworzyć te pliki chronione.

- Skaner usługi Azure Information Protection można sprawdzić te pliki do poufnych informacji.

- Eksplorator plików, programu PowerShell i skanera usługi Azure Information Protection można oznaczyć te pliki. W rezultacie można stosować etykiety usługi Azure Information Protection dotyczący nowych ochronę z poziomu usługi Azure Information Protection lub który usuwa istniejące ochronę Secure Islands.

- Możesz użyć [etykietowania migracji klienta dostosowywania](#migrate-labels-from-secure-islands-and-other-labeling-solutions) Aby dokonać automatycznej konwersji etykiety Secure Islands na ten temat chronione pliki do etykiety usługi Azure Information Protection.

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Migrowanie etykiety z Secure Islands i innych rozwiązań etykietowania

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. To ustawienie jest w wersji zapoznawczej i mogą ulec zmianie.

Ta konfiguracja nie jest obecnie zgodna z nowe zachowanie domyślne, które chroni pliki PDF przy użyciu standardu ISO do szyfrowania plików PDF. W tym scenariuszu nie można otworzyć plików ppdf, przy użyciu Eksploratora plików, programu PowerShell lub skaner. Aby rozwiązać ten problem, należy użyć Zaawansowane ustawienia klienta dotyczącego [nie jest używany do szyfrowania plików PDF ISO standard](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption).

Dokumenty pakietu Office i dokumentów PDF, które są oznaczone przez Secure Islands można relabel te dokumenty za pomocą etykiety usługi Azure Information Protection przy użyciu mapowania, który zdefiniujesz. Ta metoda jest również użyć do ponownego użycia etykiet z innych rozwiązań, w przypadku ich etykiet w dokumentach pakietu Office. 

> [!NOTE]
> W przypadku plików innych niż dokumentów PDF i pakietu Office, które są chronione przez Secure Islands te można relabeled w po przeprowadzeniu edycji rejestru zgodnie z opisem w [poprzedniej sekcji](#support-for-files-protected-by-secure-islands). 

Tej opcji konfiguracji nowej etykiety usługi Azure Information Protection jest stosowany przez klienta usługi Azure Information Protection w następujący sposób:

- W przypadku dokumentów pakietu Office: Po otwarciu dokumentu w aplikacji klasycznej, Nowa etykieta usługi Azure Information Protection jest wyświetlana jako zestawu i jest stosowana, gdy dokument zostanie zapisany.

- W Eksploratorze plików: W oknie dialogowym usługi Azure Information Protection nowej etykiety usługi Azure Information Protection jest wyświetlana jako zestawu i jest stosowana, gdy użytkownik wybierze **Zastosuj**. Jeśli użytkownik wybierze **anulować**, Nowa etykieta nie została zastosowana.

- Dla programu PowerShell: [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) zastosowanie nowej etykiety usługi Azure Information Protection. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) nie wyświetla nowej etykiety usługi Azure Information Protection, dopóki zostanie ustawiony przy użyciu innej metody.

- Skanera usługi Azure Information Protection: Odnajdywanie raportów, gdy będzie miał ustawienie nowej etykiety usługi Azure Information Protection i w trybie wymuszania można zastosować tej etykiety.

Ta konfiguracja wymaga określenia Klient zaawansowany, ustawienie o nazwie **LabelbyCustomProperty** dla każdej etykiety usługi Azure Information Protection, który ma być mapowany do starego etykiety. Następnie dla każdego wpisu, ustaw wartość używając następującej składni:

`[Azure Information Protection label ID],[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

Wartość Identyfikatora etykieta jest wyświetlana na **etykiety** bloku, wyświetlanie lub konfigurowanie zasad usługi Azure Information Protection w witrynie Azure portal. Aby określić etykiety podrzędnej, Etykieta nadrzędna musi być w tym samym zakresie lub w ramach globalnych zasad.

Podaj wybraną nazwę reguły migracji. Użyj opisową nazwę, która ułatwia ustalenie sposobu jedną lub więcej etykiet z poprzedniego rozwiązania etykietowania powinno zostać zamapowane etykiety usługi Azure Information Protection. Nazwa jest wyświetlana w raportach skanera, a w Podglądzie zdarzeń. 

Należy pamiętać, że to ustawienie nie powoduje usunięcia oznaczenia wizualne, które starą może być zastosowane. Aby usunąć nagłówków i stopek, zobacz następną sekcję, [usuwanie nagłówków i stopek z innych rozwiązań etykietowania](#remove-headers-and-footers-from-other-labeling-solutions).

### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Przykład 1: Mapowanie jeden do jednego z taką samą nazwę etykiety

Dokumenty, które ma etykietę "Poufne" Secure Islands powinien relabeled jako "Poufne" w usłudze Azure Information Protection.

W tym przykładzie:

- Etykiety usługi Azure Information Protection **poufne** identyfikatorze 1ace2cc3-14bc-4142-9125-bf946a70542c w etykiecie. 

- Etykieta Secure Islands jest przechowywany we właściwości niestandardowej o nazwie **klasyfikacji**.

Zaawansowane ustawienia klienta:

    
|Name (Nazwa)|Wartość|
|---------------------|---------|
|LabelbyCustomProperty|1ace2cc3-14bc-4142-9125-bf946a70542c, "Secure Islands etykiety są poufne", klasyfikacji, poufne|

### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Przykład 2: Mapowanie jeden do jednego dla nazwy innej etykiety

Dokumenty oznaczone jako "Poufne" przez Secure Islands powinien relabeled jako "Wysoce poufne" w usłudze Azure Information Protection.

W tym przykładzie:

- Etykiety usługi Azure Information Protection **wysoce poufne** identyfikatorze 3e9df74d-3168-48af-8b11-037e3021813f w etykiecie.

- Etykieta Secure Islands jest przechowywany we właściwości niestandardowej o nazwie **klasyfikacji**.

Zaawansowane ustawienia klienta:

    
|Name (Nazwa)|Wartość|
|---------------------|---------|
|LabelbyCustomProperty|3e9df74d-3168-48af-8b11-037e3021813f, "Secure Islands etykiety jest wrażliwa na", klasyfikacji, liter|


### <a name="example-3-many-to-one-mapping-of-label-names"></a>Przykład 3: Mapowanie wiele do jednego nazwy etykiet

Dwie etykiety Secure Islands, które zawierają słowo "Wewnętrzna", i chcesz, aby dokumenty, które mają jedną z tych etykiet Secure Islands relabeled jako "Ogólne" w usłudze Azure Information Protection.

W tym przykładzie:

- Etykiety usługi Azure Information Protection **ogólne** identyfikatorze 2beb8fe7-8293-444 c-9768-7fdc6f75014d w etykiecie.

- Etykieta Secure Islands jest przechowywany we właściwości niestandardowej o nazwie **klasyfikacji**.

Zaawansowane ustawienia klienta:

    
|Name (Nazwa)|Wartość|
|---------------------|---------|
|LabelbyCustomProperty|2beb8fe7-8293-444c-9768-7fdc6f75014d, "Secure Islands etykieta zawiera wewnętrzne" klasyfikacji. \*Wewnętrznego.\*|


## <a name="remove-headers-and-footers-from-other-labeling-solutions"></a>Usuwanie nagłówków i stopek z innych rozwiązań etykietowania

Ta konfiguracja korzysta z wielu [Zaawansowane ustawienia klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal) , należy skonfigurować w witrynie Azure portal. Te ustawienia są w wersji zapoznawczej i mogą ulec zmianie.

Ustawienia pozwalają. Usuń lub Zamień oparte na tekście nagłówków i stopek z dokumentów, po zastosowaniu tych oznaczeń wizualnych, przez inne rozwiązanie etykietowania. Na przykład stopki stare zawiera nazwę starego etykiety, który teraz poddano migracji do usługi Azure Information Protection z nową nazwę etykiety i swój własny stopki.

Gdy klient pobiera tę konfigurację w zasadach, stare nagłówki i stopki są usunięty lub zastąpiony po otwarciu dokumentu w aplikacji pakietu Office i wszelkie etykiety usługi Azure Information Protection jest stosowany do dokumentu.

Ta konfiguracja nie jest obsługiwana dla programu Outlook i należy pamiętać, że podczas korzystania z programu Word, Excel i PowerPoint, jego może negatywnie wpłynąć na wydajność tych aplikacji dla użytkowników. Konfiguracja pozwala zdefiniować dla każdej aplikacji, na przykład wyszukiwanie tekstu w nagłówkach i stopkach dokumentów programu Word, ale nie arkusze kalkulacyjne programu Excel lub prezentacji programu PowerPoint.

Ponieważ dopasowanie wzorca wpływa na wydajność dla użytkowników, zaleca się ograniczenie typów aplikacji pakietu Office (**W**orządkuj, **E**xcel, **P**owerPoint) wyłącznie do tych które mają być wyszukiwane:

- Klucz: **RemoveExternalContentMarkingInApp**

- Wartość: \<**Typy aplikacji pakietu Office WXP**> 

Przykłady:

- Aby wyszukać tylko dokumenty programu Word, należy określić **W**.

- Aby przeprowadzić wyszukiwanie dokumentów programu Word i prezentacje programu PowerPoint, określ **WP**.

Następnie należy co najmniej jednego klienta bardziej zaawansowane ustawienia **ExternalContentMarkingToRemove**, aby określić zawartość nagłówka lub stopki i jak usunąć lub zastąpić je.

### <a name="how-to-configure-externalcontentmarkingtoremove"></a>Jak skonfigurować ExternalContentMarkingToRemove

Po określeniu wartość ciągu dla **ExternalContentMarkingToRemove** klucza, masz trzy opcje, które używają wyrażeń regularnych:

- Częściowe dopasowanie, aby usunąć wszystkie elementy w nagłówku lub stopce.
    
    Przykład: Nagłówków i stopek zawierają ciąg **Usuń tekst**. Chcesz całkowicie usunąć tych nagłówkach i stopkach strony. Określ wartość: `*TEXT*`.

- Pełne dopasowanie, aby usunąć tylko określone słowa w nagłówku lub stopce.
    
    Przykład: Nagłówków i stopek zawierają ciąg **Usuń tekst**. Chcesz usunąć wyraz **tekstu** , dlatego nagłówka lub stopki ciągu jako **Aby usunąć**. Określ wartość: `TEXT `.

- Pełne dopasowanie, aby usunąć wszystkie elementy w nagłówku lub stopce.
    
    Przykład: Nagłówków i stopek zawiera ciągu **Usuń tekst**. Chcesz usunąć w nagłówkach i stopkach stron, które mają dokładnie tego ciągu. Określ wartość: `^TEXT TO REMOVE$`.
    

Dopasowywania do wzorca dla ciągu znaków nie uwzględnia wielkości liter. Maksymalna długość ciągu to 255 znaków.

Ponieważ niektóre dokumenty mogą obejmować niewidoczne znaki lub różne rodzaje tabulacji lub spacji, ciąg, który określisz dla frazę lub zdanie mogą nie zostać wykryte. Jeśli to możliwe, określ pojedynczego wyrazu wyróżniający dla wartości, a należy przetestować wyniki, przed wdrożeniem w środowisku produkcyjnym.

- Klucz: **ExternalContentMarkingToRemove**

- Wartość: \< **ciąg do dopasowania, zdefiniowany jako wyrażenie regularne**> 

#### <a name="multiline-headers-or-footers"></a>Wielowierszowy nagłówków i stopek

Jeśli tekst nagłówka lub stopki jest więcej niż jeden wiersz, należy utworzyć klucz i wartość dla każdego wiersza. Na przykład masz następujące stopki z dwoma wierszami:

**Plik jest klasyfikowany jako poufne**

**Etykieta stosowane ręcznie**

Aby usunąć ten wspólny stopki, utworzysz następujące dwa wpisy:

- Klucz 1: **ExternalContentMarkingToRemove**

- Wartość klucza 1: **\*Poufne***

- Klucz 2: **ExternalContentMarkingToRemove**

- Wartość klucza 2: **\*Etykietę*** 

#### <a name="optimization-for-powerpoint"></a>Optymalizacja dla programu PowerPoint

Stopki w programie PowerPoint są implementowane jako kształtów. Aby uniknąć, usuwanie kształtów, które zawierają tekst został określony, ale nie są w nagłówkach i stopkach strony, należy użyć dodatkowych zaawansowanych ustawień klienta o nazwie **PowerPointShapeNameToRemove**. Firma Microsoft zaleca, aby uniknąć sprawdzanie tekstu w wszystkie kształty, które jest procesem obciążającym przy użyciu tego ustawienia.

Jeśli nie określisz tego dodatkowe zaawansowane ustawienia klienta i PowerPoint znajduje się w **RemoveExternalContentMarkingInApp** klucz wartość, będzie można sprawdzić wszystkie kształty tekst, który określisz w  **ExternalContentMarkingToRemove** wartość. 

Aby znaleźć nazwę kształtu, którego używasz jako nagłówka lub stopki:

1. W programie PowerPoint, Wyświetl **wybór** okienka: **Format** kartę > **Rozmieść** grupy > **okienko wyboru**.

2. Wybierz kształt na slajdzie, która zawiera nagłówek lub stopkę. Nazwa wybranego kształtu jest wyróżniony w **wybór** okienka.

Użyj nazwę kształtu, aby określić wartość ciągu dla **PowerPointShapeNameToRemove** klucza. 

Przykład: Jest nazwa kształtu **fc**. Aby usunąć kształt o tej nazwie, należy określić wartość: `fc`.

- Klucz: **PowerPointShapeNameToRemove**

- Wartość: \<**Nazwę kształtu programu PowerPoint**> 

Jeśli masz więcej niż jeden kształtu programu PowerPoint, aby usunąć, utwórz tyle **PowerPointShapeNameToRemove** klucze mają kształty do usunięcia. Dla każdego wpisu określić nazwę kształtu do usunięcia.

Domyślnie tylko wzorca slajdów są sprawdzane w nagłówkach i stopkach stron. Aby rozszerzyć to wyszukiwanie do wszystkich slajdów, która jest procesem bardziej dużej ilości zasobów, należy użyć dodatkowe zaawansowane ustawienia klienta o nazwie **RemoveExternalContentMarkingInAllSlides**:

- Klucz: **RemoveExternalContentMarkingInAllSlides**

- Wartość: **True**

## <a name="label-an-office-document-by-using-an-existing-custom-property"></a>Etykieta dokumentu pakietu Office przy użyciu istniejącej właściwości niestandardowej

> [!NOTE]
> Jeśli używasz tej konfiguracji i konfigurację, aby [migracji etykiety z Secure Islands i innych rozwiązań etykietowania](#migrate-labels-from-secure-islands-and-other-labeling-solutions), ustawienia pierwszeństwo migracji etykietowania. 

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Po skonfigurowaniu tego ustawienia, można klasyfikować (i ewentualnie chronić) dokumentu pakietu Office, gdy ma ona istniejącej właściwości niestandardowe z wartością, która pasuje do jednej z nazw etykiet. Tej właściwości niestandardowej można ustawić na inne rozwiązanie klasyfikacji lub może być ustawiona jako właściwość przez program SharePoint.

W wyniku tej konfiguracji po dokumentu bez etykiety usługi Azure Information Protection jest otwarty i zapisany przez użytkownika w aplikacji pakietu Office, dokument jest następnie oznaczony do dopasowania odpowiadającą wartość właściwości. 

Ta konfiguracja wymaga podania dwóch ustawień zaawansowanych, które współpracują ze sobą. Nosi nazwę pierwszego **SyncPropertyName**, czyli nazwy właściwości niestandardowej, która została ustawiona z innego rozwiązania klasyfikacji lub właściwości, który jest ustawiony przez program SharePoint. Nosi nazwę drugiego **SyncPropertyState** i musi być ustawione na jedną stronę.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz 1: **SyncPropertyName**

- Wartość klucz 1: \< **nazwa właściwości**> 

- Klucz 2: **SyncPropertyState**

- Wartość klucza 2: **OneWay**

Tylko jeden właściwości niestandardowej, należy użyć tych kluczy i odpowiadające im wartości.

Na przykład masz kolumnę programu SharePoint o nazwie **klasyfikacji** zawierającej możliwe wartości **publicznych**, **ogólne**, i **wysoce poufne wszystkie Pracownicy**. Dokumenty są przechowywane w programie SharePoint i mieć **publicznych**, **ogólne**, lub **wysoce poufne wszyscy pracownicy** jako wartości ustaw dla właściwości klasyfikacji.

Aby dodać etykietę dokumentu pakietu Office przy użyciu jednego z następujących wartości klasyfikacji, należy ustawić **SyncPropertyName** do **klasyfikacji**, i **SyncPropertyState** do  **OneWay**. 

Teraz, gdy użytkownik otwiera i zapisuje jednej z tych dokumentów pakietu Office, jego jest oznaczona etykietą **publicznych**, **ogólne**, lub **wysoce poufne \ wszyscy pracownicy** w przypadku etykiet z nimi nazwy w zasadach usługi Azure Information Protection. Jeśli nie masz etykiety o tych nazwach, dokument pozostaje bez etykiety.

## <a name="disable-the-low-integrity-level-for-the-scanner"></a>Wyłącz poziom o niskiej integralności skanera

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Domyślnie skanera usługi Azure Information Protection jest uruchamiany z poziomu o niskiej integralności. To ustawienie zapewnia wyższy izolacji zabezpieczeń, ale kosztem wydajności. Poziom o niskiej integralności jest odpowiednia, jeśli uruchomisz skaner przy użyciu konta, które ma uprzywilejowane prawa (np. konta administratora lokalnego), ponieważ to ustawienie pomaga chronić komputer z uruchomionym skanera.

Jednakże, gdy konto usługi, na którym uruchomiono skaner ma wyłącznie prawa, które zostały opisane w [wymagania wstępne skanera](../deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner), poziom o niskiej integralności nie jest konieczne i nie jest zalecane, ponieważ negatywnie wpływa na wydajność. 

Aby uzyskać więcej informacji na temat poziomów spójności Windows, zobacz [co to jest mechanizm integralności Windows?](https://msdn.microsoft.com/library/bb625957.aspx)

Aby skonfigurować zaawansowane ustawienia tak, aby skaner uruchamiana z poziomem integralności, który jest automatycznie przypisywany przez Windows (konta użytkownika standardowego jest uruchamiany o średnim poziomie integralności), wprowadź następujące parametry:

- Klucz: **ProcessUsingLowIntegrity**

- Wartość: **False**


## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>Integracja z klasyfikacją wiadomości programu Exchange dla rozwiązań etykietowania urządzeń przenośnych

Mimo że program Outlook w sieci web nie obsługuje jeszcze natywnie klasyfikacji usługi Azure Information Protection i ochrony, aby rozszerzyć etykiet usługi Azure Information Protection dla użytkowników mobilnych, gdy korzystają z programu Outlook w, można użyć klasyfikacji wiadomości programu Exchange w sieci Web. Outlook Mobile nie obsługuje klasyfikacji wiadomości programu Exchange.

W tym celu: 

1. Użyj polecenia cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) środowiska PowerShell programu Exchange w celu utworzenia klasyfikacji wiadomości z właściwością Name, która mapuje do nazw etykiet użytkownika w zasadach usługi Azure Information Protection. 

2. Utwórz reguły przepływu poczty programu Exchange dla każdej etykiety: Zastosuj regułę, jeśli właściwości wiadomości obejmują skonfigurowaną przez Ciebie klasyfikację, a następnie zmodyfikuj właściwości wiadomości, aby ustawić nagłówek wiadomości. 

     Informacje, jakie należy określić dla nagłówka wiadomości, można zidentyfikować, sprawdzając nagłówki internetowe wiadomości e-mail wysłanej i sklasyfikowanej za pomocą etykiety usługi Azure Information Protection. Wyszukaj nagłówek **msip_labels** i ciąg, który następuje zaraz po nim, łącznie ze średnikiem. Przykład:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Następnie dla nagłówka wiadomości w regule określ element **msip_labels** dla nagłówka oraz pozostałe elementy ciągu dla wartości nagłówka. Przykład:
    
    ![Przykład reguły przepływu poczty usługi Exchange Online, która ustawia nagłówek wiadomości dla określonej etykiety usługi Azure Information Protection](../media/exchange-rule-for-message-header.png)
    
    Uwaga: Jeśli etykieta jest etykiety podrzędnej, należy także określić etykiecie nadrzędnej przed etykietę podrzędną w wartości nagłówka przy użyciu tego samego formatu. Na przykład jeśli Twoja etykietę podrzędną ma identyfikator GUID 27efdf94-80a0 - 4d-02-b88c-b615c12d69a9, wartość może wyglądać następująco: `MSIP_Label_ab70158b-bdcc-42a3-8493-2a80736e9cbd_Enabled=True;MSIP_Label_27efdf94-80a0-4d02-b88c-b615c12d69a9_Enabled=True;`

Przed testowaniem tej konfiguracji należy pamiętać, że często występuje opóźnienie podczas tworzenia lub edytowania reguły przepływu poczty (na przykład godzinne). Gdy reguła jest aktywna, następujące zdarzenia teraz się zdarzyć, gdy użytkownicy używają aplikacji Outlook Web Access lub klienta urządzenia przenośnego, który obsługuje protokół Exchange ActiveSync IRM: 

- Użytkownicy wybierają klasyfikację wiadomości programu Exchange i wysyłają wiadomość e-mail.

- Reguła programu Exchange wykrywa klasyfikację programu Exchange i odpowiednio modyfikuje nagłówek wiadomości w celu dodania klasyfikacji usługi Azure Information Protection.

- Jeśli mają zainstalowanego klienta usługi Azure Information Protection adresatów wewnętrznych wyświetlają wiadomość e-mail w programie Outlook, widzą przypisane etykiety usługi Azure Information Protection. 

Jeśli etykiety usługi Azure Information Protection zastosowania ochrony, Dodaj tę ochronę do konfiguracji reguły: Wybierając opcję modyfikacji zabezpieczeń wiadomości, Zastosuj ochronę praw, a następnie wybierz szablon usług RMS lub opcję nie przesyłaj dalej.

Można również skonfigurować reguły przepływu poczty na potrzeby mapowania odwrotnego. Po wykryciu etykiety usługi Azure Information Protection ustaw odpowiednią klasyfikację wiadomości programu Exchange:

- Dla każdej etykiety usługi Azure Information Protection: Utwórz reguły przepływu poczty, która będzie stosowana, jeśli **msip_labels** nagłówek zawiera nazwę Twojej etykiety (na przykład **ogólne**) i Zastosuj klasyfikację wiadomości mapowaną do tej etykiety.


## <a name="next-steps"></a>Następne kroki
Po dostosowaniu klienta usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi, które mogą być przydatne podczas obsługi tego klienta:

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)


