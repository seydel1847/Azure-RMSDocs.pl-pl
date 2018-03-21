---
title: "Niestandardowe konfiguracje klienta usługi Azure Information Protection"
description: "Informacje na temat dostosowywania klienta usługi Azure Information Protection dla systemu Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: e5c71068f979c13b2d8c9ee7c9c5c43e2ad3a7ad
ms.sourcegitcommit: 32b233bc1f8cef0885d9f4782874f1781170b83d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2018
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-client"></a>Podręcznik administratora: Konfiguracje niestandardowe dla klienta usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Poniższe informacje służą do tworzenia zaawansowanych konfiguracji, które mogą być wymagane w przypadku określonych scenariuszy lub podzbiorów użytkowników podczas zarządzania klientem usługi Azure Information Protection.

Niektóre z tych ustawień wymagają edycji rejestru. Inne korzystają z ustawień zaawansowanych, które należy skonfigurować w witrynie Azure Portal, a następnie opublikować do pobrania przez klientów.  

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>Jak skonfigurować zaawansowane ustawienia konfiguracji klienta w portalu

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki, [Zaloguj się do portalu Azure](../deploy-use/configure-policy.md#signing-in-to-the-azure-portal), a następnie przejdź do **usługi Azure Information Protection** bloku.

2. W pierwszym bloku usługi Azure Information Protection wybierz pozycję **Zasady z określonym zakresem**.

3. W bloku **Azure Information Protection — zasady z określonym zakresem** wybierz menu kontekstowe (**...** ) obok zasady zawierającej ustawienia zaawansowane. Następnie wybierz opcję **Ustawienia zaawansowane**.
    
    Możesz skonfigurować ustawienia zaawansowane dla zasad globalnych i zasad z określonym zakresem.

4. W bloku **Ustawienia zaawansowane** wpisz nazwę i wartość ustawienia zaawansowanego, a następnie wybierz opcję **Zapisz i zamknij**.

5. Kliknij przycisk **Opublikuj** i upewnij się, że użytkownicy tych zasad uruchomili ponownie wszystkie otwarte wcześniej aplikacje pakietu Office.

6. Jeśli nie potrzebujesz już danego ustawienia i chcesz przywrócić zachowanie domyślne: w bloku **Ustawienia zaawansowane** wybierz menu kontekstowe (**...**) obok ustawienia, które przestało być potrzebne, a następnie wybierz opcję **Usuń**. Następnie kliknij przycisk **Zapisz i zamknij** i ponownie opublikuj zmodyfikowane zasady.

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>Zapobieganie monitom o logowanie dla komputerów korzystających tylko z usługi AD RMS

Domyślnie klient usługi Azure Information Protection automatycznie próbuje połączyć się z usługą Azure Information Protection. W przypadku komputerów, które komunikują się tylko z usługą AD RMS, ta konfiguracja może powodować wyświetlanie użytkownikom zbędnego monitu o logowanie. Temu monitowi o logowanie można zapobiec, edytując rejestr:

Znajdź następującą nazwę wartości, a następnie ustaw dane wartości na **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Niezależnie od tego ustawienia klient usługi Azure Information Protection postępuje zgodnie ze standardowym [procesem odnajdowania usługi RMS](../rms-client/client-deployment-notes.md#rms-service-discovery), aby odnaleźć swój klaster usługi AD RMS.

## <a name="suppress-the-initial-congratulations-welcome-page"></a>Pomiń początkową "Gratulacje!" strony powitalnej

Po zainstalowaniu na komputerze klienta usługi Azure Information Protection i użytkownik otwiera Word, Excel, PowerPoint lub programie Outlook **Gratulacje!** zostanie wyświetlona strona krótkie instrukcje jak nowy pasek Information Protection umożliwia wybranie etykiety. Edytując rejestr, można pominąć tej strony.

Znajdź nazwę wartości następujących i Ustaw dane wartości **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnableWelcomeExperience** 


## <a name="sign-in-as-a-different-user"></a>Zaloguj się jako inny użytkownik

W środowisku produkcyjnym użytkownik nie ma zazwyczaj potrzeby logowania się jako inny użytkownik w przypadku korzystania z klienta usługi Azure Information Protection. Jednak jako administrator możesz potrzebować możliwości zalogowania się jako inny użytkownik podczas fazy testowania. 

Aby sprawdzić, za pomocą którego konta nastąpiło logowanie, otwórz okno dialogowe **Microsoft Azure Information Protection**, uruchom aplikację pakietu Office i na karcie **Narzędzia główne** w grupie **Ochrona** kliknij opcję **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. Nazwa konta jest widoczna w sekcji **Stan klienta**.

Pamiętaj także o sprawdzeniu wyświetlonej nazwy domeny konta użytego do zalogowania. Fakt, że logowanie następuje przy użyciu prawidłowej nazwy konta, ale niewłaściwej domeny, można łatwo przeoczyć. W przypadku użycia niewłaściwego konta może wystąpić problem z pobraniem zasad usługi Azure Information Protection albo nie będą widoczne oczekiwane etykiety lub zachowania.

Aby zalogować się jako inny użytkownik:

1. Przejdź do **%localappdata%\Microsoft\MSIP** i usunąć **TokenCache** pliku.

2. Uruchom ponownie wszystkie otwarte aplikacje pakietu Office i zaloguj się przy użyciu innego konta użytkownika. Jeśli w aplikacji pakietu Office nie został wyświetlony monit o zalogowanie się do usługi Azure Information Protection, wróć do okna dialogowego **Microsoft Azure Information Protection** i kliknij przycisk **Zaloguj** w zaktualizowanej sekcji **Stan klienta**.

Dodatkowo:

- To rozwiązanie jest obsługiwane w przypadku logowania się jako inny użytkownik z tej samej dzierżawy. Nie jest ono obsługiwane w przypadku logowania się jako inny użytkownik z innej dzierżawy. Do testowania usługi Azure Information Protection z wieloma dzierżawami użyj różnych komputerów.

- Jeśli korzystasz z logowania jednokrotnego, musisz wylogować się z systemu Windows i po wprowadzeniu zmian w rejestrze zalogować się przy użyciu innego konta użytkownika. Klient usługi Azure Information Protection przeprowadzi automatyczne uwierzytelnienie przy użyciu aktualnie zalogowanego konta użytkownika.

- Można użyć **Zresetuj ustawienia** opcję **Pomoc i opinie** Wyloguj się i usuń aktualnie pobrany zasady usługi Azure Information Protection.


## <a name="enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses"></a>Wymusić trybu tylko do ochrony, gdy Twoja organizacja ma kombinacji licencji

Jeśli Twoja organizacja nie ma żadnych licencji usługi Azure Information Protection, ale masz licencji dla usługi Office 365 obejmują usługę Azure Rights Management do ochrony danych, klient usługi Azure Information Protection dla systemu Windows jest uruchamiana automatycznie w [trybu tylko do ochrony](../rms-client/client-protection-only-mode.md).

Jednak jeśli organizacja ma subskrypcję usługi Azure Information Protection, domyślnie wszystkie komputery z systemem Windows można pobrać zasad usługi Azure Information Protection. Azure Information Protection, klient nie nie licencji sprawdzanie i wymuszania. 

Jeśli niektórzy użytkownicy, którzy nie mają licencji usługi Azure Information Protection, ale masz licencję dla usługi Office 365 obejmującą usługę Azure Rights Management, edytować rejestr na komputerach tych użytkowników, aby zapobiec uruchamianiu licencji klasyfikacji i etykietowania funkcji z usługi Azure Information Protection.

Znajdź następującą nazwę wartości i ustaw dane wartości **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Ponadto sprawdź, czy te komputery nie mają plik o nazwie **Policy.msip** w **%LocalAppData%\Microsoft\MSIP** folderu. Jeśli ten plik istnieje, usuń go. Ten plik zawiera zasady usługi Azure Information Protection i może zostały pobrane przed edytować rejestr lub jeśli klient usługi Azure Information Protection został zainstalowany z opcją pokaz.

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ukryj opcję menu Klasyfikuj i chroń w Eksploratorze plików systemu Windows

Utwórz następującą nazwę wartości DWORD (z dowolnymi danymi wartości):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Obsługa odłączonych komputerów

Domyślnie klient usługi Azure Information Protection automatycznie próbuje połączyć się z usługą Azure Information Protection, aby pobrać najnowsze zasady usługi Azure Information Protection. W przypadku komputera pozbawionego w danym momencie możliwości nawiązania połączenia z Internetem można zapobiec próbie nawiązania połączenia z usługą, edytując rejestr. 

Znajdź następującą nazwę wartości i ustaw dane wartości **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Upewnij się, że klient ma prawidłową zasadę plik o nazwie **Policy.msip**w **%LocalAppData%\Microsoft\MSIP** folderu. W razie potrzeby można wyeksportować zasady z portalu Azure Portal i skopiować wyeksportowany plik do komputera klienckiego. Ta metoda umożliwia również zastąpienie nieaktualnego pliku zasad najnowszymi opublikowanymi zasadami.

Podczas eksportowania zasady, ta akcja pobiera plik z rozszerzeniem zip z wieloma wersjami zasad, która odpowiada dla różnych wersji klienta Azure Information Protection:

1. Rozpakuj plik i skorzystaj z poniższej tabeli, aby określić plik zasad, które należy. 
    
    |Nazwa pliku|Odpowiednia wersja klienta|
    |--------------------------|---------------------------------------------|
    |Policy1.1.msip |w wersji 1.2|
    |Policy1.2.msip |w wersji 1.3 1.7|
    |Policy1.3.msip |Wersja 1,8 i nowsze|
    
2. Nazwy pliku zidentyfikowanych **Policy.msip**, a następnie skopiować go do **%LocalAppData%\Microsoft\MSIP** folderu na komputerach, które mają zainstalowanego klienta Azure information protection. 


## <a name="hide-or-show-the-do-not-forward-button-in-outlook"></a>Ukrycie lub pokazanie przycisku nie przesyłaj dalej w programie Outlook

Aby skonfigurować tę opcję zaleca przy użyciu [ustawienie zasad](../deploy-use/configure-policy-settings.md) **dodać do Wstążki programu Outlook przycisk nie przesyłaj dalej**. Jednak również można skonfigurować tę opcję, za pomocą [Zaawansowane ustawienia klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal) skonfigurowane w portalu Azure.

Po skonfigurowaniu tego ustawienia powoduje ukrycie lub pokazuje **nie przesyłaj dalej** na Wstążce w programie Outlook. To ustawienie nie ma wpływu na opcję nie przesyłaj dalej z menu pakietu Office.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **DisableDNF**

- Wartość: **True** do ukrywanie przycisku, lub **False** wyświetlać przycisk

## <a name="make-the-custom-permissions-options-available-or-unavailable-to-users"></a>Uprawnienia niestandardowe opcje stały dostępne lub niedostępne dla użytkowników

Aby skonfigurować tę opcję zaleca przy użyciu [ustawienie zasad](../deploy-use/configure-policy-settings.md) **udostępnić użytkownikom opcję uprawnień niestandardowych**. Jednak również można skonfigurować tę opcję, za pomocą [Zaawansowane ustawienia klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal) skonfigurowane w portalu Azure. 

Podczas konfigurowania tego ustawienia i opublikować zasady dla użytkowników, uprawnienia niestandardowe opcje staną się dostępne dla użytkowników wybrać własne ustawienia ochrony lub jest niedostępny, dzięki czemu użytkownicy nie można wybrać własne ustawienia ochrony, chyba że zostanie wyświetlony monit.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **EnableCustomPermissions**

- Wartość: **True** udostępnienie opcji uprawnień niestandardowych, lub **False** Aby ta opcja niedostępna

> [!IMPORTANT]
> Jeśli bieżąca wersja klienta jest używana, nie należy ustawiać tej opcji **False** Jeśli masz etykiety, które są skonfigurowane na uprawnienia zdefiniowane przez użytkownika dla programu Word, Excel, PowerPoint i Eksploratora plików. Jeśli to zrobisz, po zastosowaniu etykiety, użytkownicy nie monit, aby skonfigurować uprawnienia niestandardowe. Wynik jest etykietą dokumentu, ale nie jest chroniony, zgodnie z zamierzonym.

## <a name="permanently-hide-the-azure-information-protection-bar"></a>Trwałe ukrycie paska usługi Azure Information Protection

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. Go używać tylko wtedy, gdy [ustawienie zasad](../deploy-use/configure-policy-settings.md) **wyświetlane na pasku Information Protection w aplikacji pakietu Office** ustawiono **na**.

Gdy po skonfigurowaniu tego ustawienia i opublikowaniu zasad dla użytkowników użytkownik zdecyduje, aby nie wyświetlać paska usługi Azure Information Protection w aplikacjach pakietu Office, pasek pozostanie ukryty. Takie zachowanie ma miejsce, gdy użytkownik usunie zaznaczenie opcji **Pokaż pasek** na karcie **Strona główna**, w grupie **Ochrona**, w obszarze przycisku **Chroń**. To ustawienie nie daje efektu, jeśli użytkownik zamknie pasek za pomocą ikony **Zamknij ten pasek**.

Nawet gdy pasek usługi Azure Information Protection pozostaje ukryty, użytkownicy mogą wybrać etykietę z tymczasowo wyświetlanego paska, jeśli skonfigurowano zalecaną klasyfikację lub w przypadku, gdy dokument lub wiadomość e-mail musi mieć etykietę. 

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **EnableBarHiding**

- Wartość: **Prawda**


## <a name="enable-recommended-classification-in-outlook"></a>Włącz zalecana klasyfikacja w programie Outlook

Ta opcja konfiguracji jest obecnie w wersji zapoznawczej i mogą ulec zmianie.

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal.

Po skonfigurowaniu etykiety dla zalecana klasyfikacja użytkowników monit, aby zaakceptować lub odrzucić zalecaną etykietę, Word, Excel i PowerPoint. To ustawienie zwiększa to zalecenie etykiety można również wyświetlić w programie Outlook.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **OutlookRecommendationEnabled**

- Wartość: **Prawda**


## <a name="set-a-different-default-label-for-outlook"></a>Ustaw etykietę różne domyślne dla programu Outlook

Ta opcja konfiguracji jest obecnie w wersji zapoznawczej i mogą ulec zmianie. Ponadto ta opcja konfiguracji wymaga wersji zapoznawczej klienta.

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Po skonfigurowaniu tego ustawienia program Outlook nie ma zastosowania etykiety domyślnej, skonfigurowanym w ramach zasad usługi Azure Information Protection, ustawienia **wybierz etykietę domyślną**. Zamiast tego programu Outlook można stosować różne domyślne etykiety lub bez etykiety.

Aby zastosować inną etykietę, należy określić identyfikator etykiety. Wartość Identyfikatora etykiety jest wyświetlany na **etykiety** bloku, gdy wyświetlanie lub konfigurowanie zasad usługi Azure Information Protection w portalu Azure. Dla plików, które mają zastosowane etykiety, można również uruchomić [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) polecenia cmdlet programu PowerShell do identyfikowania etykiety (MainLabelId lub SubLabelId). Jeśli etykieta sublabels, zawsze Określ identyfikator właśnie sublabel i nie etykiety nadrzędnej.

Dlatego program Outlook nie ma zastosowania etykiety domyślnej, określ **Brak**.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **OutlookDefaultLabel**

- Wartość: \< **identyfikator etykiety**> lub **None**

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Migrowanie etykiety z Secure Islands i innych rozwiązań etykietowania

Ta opcja konfiguracji jest obecnie w wersji zapoznawczej i mogą ulec zmianie. Ponadto ta opcja konfiguracji wymaga wersji zapoznawczej klienta.

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Dokumenty pakietu Office i PDF dokumenty, które są oznaczone przez Secure Islands można relabel te dokumenty z etykietą usługi Azure Information Protection przy użyciu mapowania, które należy zdefiniować. Możesz również ta metoda umożliwia ponowne użycie etykiety z innych rozwiązań podczas ich etykiety znajdują się w dokumentach pakietu Office. 

W wyniku tej opcji konfiguracji nowej etykiety usługi Azure Information Protection jest stosowana przez klienta usługi Azure Information Protection w następujący sposób:

- W przypadku dokumentów pakietu Office: gdy dokument zostanie otwarty w aplikacji komputerowej, nowej etykiety usługi Azure Information Protection jest wyświetlana jako zestaw i jest stosowana, gdy dokument zostanie zapisany.

- W Eksploratorze plików: W oknie dialogowym usługi Azure Information Protection nowej etykiety usługi Azure Information Protection jest wyświetlana jako zestaw i jest stosowana, gdy użytkownik wybierze **Zastosuj**. Jeśli użytkownik wybierze **anulować**, nowej etykiety nie została zastosowana.

- Dla środowiska PowerShell: [AIPFileLabel zestaw](/powershell/module/azureinformationprotection/set-aipfilelabel) dotyczy nowej etykiety usługi Azure Information Protection. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) nie wyświetla nowej etykiety usługi Azure Information Protection, dopóki nie jest ustawiona przy użyciu innej metody.

- Skanera usługi Azure Information Protection: odnajdywania raportów, gdy ustawiał nowej etykiety usługi Azure Information Protection i tej etykiety mogą być stosowane z trybem Wymuś.

Ta konfiguracja wymaga określenia Klient zaawansowany, ustawienie o nazwie **LabelbyCustomProperty** dla każdej etykiety usługi Azure Information Protection, który ma być mapowany do starego etykiety. Następnie dla każdego wpisu, ustaw wartość przy użyciu następującej składni:

`[Azure Information Protection label ID],[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

Wartość Identyfikatora etykiety jest wyświetlany na **etykiety** bloku, gdy wyświetlanie lub konfigurowanie zasad usługi Azure Information Protection w portalu Azure. Aby określić sublabel, etykieta nadrzędny musi być w tym samym zakresie lub globalnych zasad.

Podaj wybraną nazwę reguły migracji. Użyj nazwy opisowej ułatwiające identyfikowanie etykiety jak co najmniej jednego z poprzednich rozwiązania etykietowania powinny być mapowane do etykiety usługi Azure Information Protection. Nazwa wyświetlana w raportach skanera, a w Podglądzie zdarzeń. 

### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Przykład 1: Mapowanie jeden do jednego z taką samą nazwę etykiety

Dokumentów, których etykiety Secure Islands "Poufne" powinien relabeled "Poufne" przez usługę Azure Information Protection.

W tym przykładzie:

- Etykieta usługi Azure Information Protection **poufne** identyfikatorze 1ace2cc3-14bc-4142-9125-bf946a70542c w etykiecie. 

- Etykieta Secure Islands są przechowywane w właściwość niestandardowa o nazwie **klasyfikacji**.

Zaawansowane ustawienia klienta:

    
|Nazwa|Wartość|
|---------------------|---------|
|LabelbyCustomProperty|1ace2cc3-14bc-4142-9125-bf946a70542c, "Secure Islands etykiety jest poufne," klasyfikacji, poufne|

### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Przykład 2: Mapowanie jeden do jednego dla nazwy innej etykiety

Dokumenty oznaczone jako "Poufne" przez Secure Islands powinien relabeled jako "Poufny" przez usługę Azure Information Protection.

W tym przykładzie:

- Etykieta usługi Azure Information Protection **poufny** identyfikatorze 3e9df74d-3168-48af-8b11-037e3021813f w etykiecie.

- Etykieta Secure Islands są przechowywane w właściwość niestandardowa o nazwie **klasyfikacji**.

Zaawansowane ustawienia klienta:

    
|Nazwa|Wartość|
|---------------------|---------|
|LabelbyCustomProperty|3e9df74d-3168-48af-8b11-037e3021813f, "Secure Islands etykiety jest liter" klasyfikacji, liter|


### <a name="example-3-many-to-one-mapping-of-label-names"></a>Przykład 3: Wiele do jednego mapowania nazw etykiety

Masz dwie etykiety Secure Islands zawierające słowo "Internal" i ma dokumentów, których jednej z tych etykiet Secure Islands relabeled jako "Ogólne" w przez usługę Azure Information Protection.

W tym przykładzie:

- Etykieta usługi Azure Information Protection **ogólne** identyfikatorze 2beb8fe7-8293-444 c-9768-7fdc6f75014d w etykiecie.

- Etykieta Secure Islands są przechowywane w właściwość niestandardowa o nazwie **klasyfikacji**.

Zaawansowane ustawienia klienta:

    
|Nazwa|Wartość|
|---------------------|---------|
|LabelbyCustomProperty|2beb8fe7-8293-444c-9768-7fdc6f75014d, "Secure Islands etykiety zawiera wewnętrzne" klasyfikacji. \*Wewnętrznego.\*|


## <a name="label-an-office-document-by-using-an-existing-custom-property"></a>Etykieta dokumentu pakietu Office przy użyciu istniejącej właściwości niestandardowej

Ta opcja konfiguracji jest obecnie w wersji zapoznawczej i mogą ulec zmianie.

> [!NOTE]
> Jeśli używasz tej konfiguracji i z poprzedniej sekcji, aby przeprowadzić migrację z innego rozwiązania etykietowania, pierwszeństwo ma etykietowania ustawienie migracji. 

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Po skonfigurowaniu tego ustawienia można klasyfikować (i opcjonalnie chronić) dokumentu pakietu Office, gdy ma istniejącej niestandardowe właściwości z wartością, która pasuje do jednej nazwy etykiety. Tej właściwości niestandardowej można ustawić z innego rozwiązania klasyfikacji lub można ustawić jako właściwość programu SharePoint.

W wyniku tej konfiguracji po dokumentu bez etykiety usługi Azure Information Protection jest otwarty i zapisany przez użytkownika w aplikacji pakietu Office, dokument jest następnie etykietami pasuje do odpowiadającej jej wartości właściwości. 

Ta konfiguracja wymaga określenia dwa ustawienia zaawansowane, które współpracują ze sobą. Pierwszy nosi nazwę **SyncPropertyName**, czyli nazwę właściwości niestandardowej, która została ustawiona z innych rozwiązań klasyfikacji lub właściwości, która jest ustawiony przez program SharePoint. Nosi nazwę drugiego **SyncPropertyState** i musi mieć ustawioną OneWay.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz 1: **SyncPropertyName**

- Wartość klucz 1: \< **nazwa właściwości**> 

- Klucz 2: **SyncPropertyState**

- Wartość klucza 2: **OneWay**

Tylko jeden właściwości niestandardowej, należy użyć tych kluczy i wartości.

Jako przykład masz kolumny programu SharePoint o nazwie **klasyfikacji** mający możliwe wartości **publicznego**, **ogólne**, i **poufne**. Dokumenty są przechowywane w programie SharePoint i mieć jeden z tych wartości właściwości klasyfikacji.

Aby dodać etykietę dokumentu pakietu Office, z jedną z następujących wartości klasyfikacji, ustaw **SyncPropertyName** do **klasyfikacji**, i **SyncPropertyState** do  **OneWay**. 

Teraz, gdy użytkownik otwiera i zapisuje jeden z tych dokumentów pakietu Office, jego etykietą **publicznego**, **ogólne**, lub **poufne** Jeśli etykiet z tych nazw platformy Azure Zasady ochrony informacji. Jeśli nie ma etykiety o tych nazwach, dokument pozostanie bez etykiety.

## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>Integracja z klasyfikacją wiadomości programu Exchange dla rozwiązań etykietowania urządzeń przenośnych

Pomimo tego, że program Outlook w sieci Web nie obsługuje natywnie klasyfikacji ani ochrony usługi Azure Information Protection, można użyć klasyfikacji wiadomości programu Exchange w celu poszerzenia zasięgu używania etykiet usługi Azure Information Protection o użytkowników urządzeń przenośnych.

W tym celu: 

1. Użyj polecenia cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) środowiska PowerShell programu Exchange w celu utworzenia klasyfikacji wiadomości z właściwością Name, która mapuje do nazw etykiet użytkownika w zasadach usługi Azure Information Protection. 

2. Utwórz dla każdej etykiety regułę transportu programu Exchange: zastosuj regułę, jeśli właściwości wiadomości obejmują skonfigurowaną przez Ciebie klasyfikację, a następnie zmodyfikuj właściwości wiadomości, aby ustawić nagłówek wiadomości. 

    Informacje, jakie należy określić dla nagłówka wiadomości, można zidentyfikować, sprawdzając nagłówki internetowe wiadomości e-mail wysłanej i sklasyfikowanej za pomocą etykiety usługi Azure Information Protection. Wyszukaj nagłówek **msip_labels** i ciąg, który następuje zaraz po nim, łącznie ze średnikiem. Korzystając z poprzedniego przykładu:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Następnie dla nagłówka wiadomości w regule określ element **msip_labels** dla nagłówka oraz pozostałe elementy ciągu dla wartości nagłówka. Przykład:
    
    ![Przykładowa reguła transportu usługi Exchange Online, która ustawia nagłówek wiadomości dla określonej etykiety usługi Azure Information Protection](../media/exchange-rule-for-message-header.png)

Testując tę konfigurację, trzeba pamiętać, że przy tworzeniu lub edytowaniu reguł transportu często występuje opóźnienie (na przykład godzinne). Gdy reguła jest aktywna, w przypadku użytkowników, którzy używają aplikacji Outlook w sieci Web lub klienta urządzenia przenośnego obsługującego ochronę za pomocą usługi Rights Management, ma miejsce następujący scenariusz: 

- Użytkownicy wybierają klasyfikację wiadomości programu Exchange i wysyłają wiadomość e-mail.

- Reguła programu Exchange wykrywa klasyfikację programu Exchange i odpowiednio modyfikuje nagłówek wiadomości w celu dodania klasyfikacji usługi Azure Information Protection.

- Gdy adresaci korzystający z klienta usługi Azure Information Protection wyświetlają wiadomość e-mail w programie Outlook, widzą przypisane etykiety usługi Azure Information Protection i wszelkie powiązane nagłówki, stopki lub znaki wodne wiadomości e-mail. 

Jeśli etykiety usługi Azure Information Protection zakładają zastosowanie ochrony zarządzania prawami, dodaj tę ochronę do konfiguracji reguły. Zaznacz opcję modyfikacji zabezpieczeń wiadomości, zastosuj ochronę praw, a następnie wybierz szablon usługi RMS lub opcję Nie przesyłaj dalej.

Możesz również skonfigurować reguły transportu na potrzeby mapowania odwrotnego. Po wykryciu etykiety usługi Azure Information Protection ustaw odpowiednią klasyfikację wiadomości programu Exchange:

- Dla każdej etykiety usługi Azure Information Protection utwórz regułę transportu, która będzie stosowana, jeśli nagłówek **msip_labels** będzie zawierać nazwę Twojej etykiety (na przykład **Ogólne**), oraz zastosuj klasyfikację wiadomości mapowaną do tej etykiety.


## <a name="next-steps"></a>Następne kroki
Po dostosowaniu klienta usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi, które mogą być przydatne podczas obsługi tego klienta:

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
