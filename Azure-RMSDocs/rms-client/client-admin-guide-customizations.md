---
title: Niestandardowe konfiguracje klienta usługi Azure Information Protection
description: Informacje na temat dostosowywania klienta usługi Azure Information Protection dla systemu Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/12/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 6b5a2856f54ec6d38ae69007e80d9eb22d416799
ms.sourcegitcommit: 56a49619c0c52fa5296810b27161f23b3380eab9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39029937"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-client"></a>Podręcznik administratora: Konfiguracje niestandardowe dla klienta usługi Azure Information Protection

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, systemu Windows Server 2008 R2*

Poniższe informacje służą do tworzenia zaawansowanych konfiguracji, które mogą być wymagane w przypadku określonych scenariuszy lub podzbiorów użytkowników podczas zarządzania klientem usługi Azure Information Protection.

Niektóre z tych ustawień wymagają edycji rejestru. Inne korzystają z ustawień zaawansowanych, które należy skonfigurować w witrynie Azure Portal, a następnie opublikować do pobrania przez klientów.  

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>Jak skonfigurować zaawansowane ustawienia konfiguracji klienta w portalu

1. Jeśli użytkownik jeszcze tego nie zrobiono, w nowym oknie przeglądarki [Zaloguj się do witryny Azure portal](../deploy-use/configure-policy.md#signing-in-to-the-azure-portal), a następnie przejdź do **usługi Azure Information Protection** bloku.

2. Z **klasyfikacje** > **etykiety** opcji menu: Wybierz **zasady**.

3. Na **usługi Azure Information Protection — zasady** bloku, wybierz menu kontekstowe (**...** ) obok zasady zawierającej ustawienia zaawansowane. Następnie wybierz opcję **Ustawienia zaawansowane**.
    
    Możesz skonfigurować ustawienia zaawansowane dla zasad globalnych i zasad z określonym zakresem.

4. W bloku **Ustawienia zaawansowane** wpisz nazwę i wartość ustawienia zaawansowanego, a następnie wybierz opcję **Zapisz i zamknij**.

5. Upewnij się, że użytkownicy tych zasad, uruchom ponownie wszystkie otwarte wcześniej aplikacje pakietu Office.

6. Jeśli nie potrzebujesz już danego ustawienia i chcesz przywrócić zachowanie domyślne: w bloku **Ustawienia zaawansowane** wybierz menu kontekstowe (**...**) obok ustawienia, które przestało być potrzebne, a następnie wybierz opcję **Usuń**. Następnie kliknij przycisk **Zapisz i Zamknij**.

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>Zapobieganie monitom o logowanie dla komputerów korzystających tylko z usługi AD RMS

Domyślnie klient usługi Azure Information Protection automatycznie próbuje połączyć się z usługą Azure Information Protection. W przypadku komputerów, które komunikują się tylko z usługą AD RMS, ta konfiguracja może powodować wyświetlanie użytkownikom zbędnego monitu o logowanie. Temu monitowi o logowanie można zapobiec, edytując rejestr:

Znajdź następującą nazwę wartości, a następnie ustaw dane wartości na **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Niezależnie od tego ustawienia klient usługi Azure Information Protection postępuje zgodnie ze standardowym [procesem odnajdowania usługi RMS](../rms-client/client-deployment-notes.md#rms-service-discovery), aby odnaleźć swój klaster usługi AD RMS.

## <a name="sign-in-as-a-different-user"></a>Zaloguj się jako inny użytkownik

W środowisku produkcyjnym użytkownik nie ma zazwyczaj potrzeby logowania się jako inny użytkownik w przypadku korzystania z klienta usługi Azure Information Protection. Jednak jako administrator możesz potrzebować możliwości zalogowania się jako inny użytkownik podczas fazy testowania. 

Aby sprawdzić, za pomocą którego konta nastąpiło logowanie, otwórz okno dialogowe **Microsoft Azure Information Protection**, uruchom aplikację pakietu Office i na karcie **Narzędzia główne** w grupie **Ochrona** kliknij opcję **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. Nazwa konta jest widoczna w sekcji **Stan klienta**.

Pamiętaj także o sprawdzeniu wyświetlonej nazwy domeny konta użytego do zalogowania. Fakt, że logowanie następuje przy użyciu prawidłowej nazwy konta, ale niewłaściwej domeny, można łatwo przeoczyć. W przypadku użycia niewłaściwego konta może wystąpić problem z pobraniem zasad usługi Azure Information Protection albo nie będą widoczne oczekiwane etykiety lub zachowania.

Aby zalogować się jako inny użytkownik:

1. Przejdź do **%localappdata%\Microsoft\MSIP** i Usuń **TokenCache** pliku.

2. Uruchom ponownie wszystkie otwarte aplikacje pakietu Office i zaloguj się przy użyciu innego konta użytkownika. Jeśli w aplikacji pakietu Office nie został wyświetlony monit o zalogowanie się do usługi Azure Information Protection, wróć do okna dialogowego **Microsoft Azure Information Protection** i kliknij przycisk **Zaloguj** w zaktualizowanej sekcji **Stan klienta**.

Dodatkowo:

- To rozwiązanie jest obsługiwane w przypadku logowania się jako inny użytkownik z tej samej dzierżawy. Nie jest ono obsługiwane w przypadku logowania się jako inny użytkownik z innej dzierżawy. Do testowania usługi Azure Information Protection z wieloma dzierżawami użyj różnych komputerów.

- Jeśli korzystasz z logowania jednokrotnego, musisz wylogować się z systemu Windows i po wprowadzeniu zmian w rejestrze zalogować się przy użyciu innego konta użytkownika. Klient usługi Azure Information Protection przeprowadzi automatyczne uwierzytelnienie przy użyciu aktualnie zalogowanego konta użytkownika.

- Możesz użyć **zresetować ustawienia** opcję **Pomoc i opinie** wylogowania się i usunąć aktualnie pobrane zasady usługi Azure Information Protection.


## <a name="enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses"></a>Wymusić tryb z samą ochroną, gdy Twoja organizacja ma różne licencji

Jeśli Twoja organizacja nie ma żadnych licencji usługi Azure Information Protection, ale mają licencje usługi Office 365, która obejmuje usługi Azure Rights Management do ochrony danych, klient usługi Azure Information Protection dla Windows automatycznie uruchamia w [tryb z samą ochroną](../rms-client/client-protection-only-mode.md).

Jednak jeśli Twoja organizacja ma subskrypcję usługi Azure Information Protection, domyślnie wszystkie komputery Windows można pobrać zasad usługi Azure Information Protection. Nie usługi Azure Information Protection, w których klient ma licencję, sprawdzenie i wymuszania. 

W przypadku niektórych użytkowników, którzy nie mają licencji usługi Azure Information Protection, ale mieć licencję usługi Office 365, która obejmuje usługę Azure Rights Management, należy edytować rejestr na komputerach tych użytkowników, aby uniemożliwić użytkownikom uruchamianie licencjami Klasyfikacja i etykietowanie funkcji z usługi Azure Information Protection.

Znajdź następującą nazwę wartości i ustaw dane wartości **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Ponadto należy sprawdzić, czy te komputery nie mają plik o nazwie **Policy.msip** w **%LocalAppData%\Microsoft\MSIP** folderu. Jeśli ten plik już istnieje, należy go usunąć. Ten plik zawiera zasady usługi Azure Information Protection i mogło zostać pobrane przed edytowania rejestru, czy klient usługi Azure Information Protection został zainstalowany z opcją pokaz.

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ukryj opcję menu Klasyfikuj i chroń w Eksploratorze plików systemu Windows

Utwórz następującą nazwę wartości DWORD (z dowolnymi danymi wartości):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Obsługa odłączonych komputerów

Domyślnie klient usługi Azure Information Protection automatycznie próbuje połączyć się z usługą Azure Information Protection, aby pobrać najnowsze zasady usługi Azure Information Protection. W przypadku komputera pozbawionego w danym momencie możliwości nawiązania połączenia z Internetem można zapobiec próbie nawiązania połączenia z usługą, edytując rejestr. 

Znajdź następującą nazwę wartości i ustaw dane wartości **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Upewnij się, że klient ma prawidłowy plik zasad o nazwie **Policy.msip**w **%LocalAppData%\Microsoft\MSIP** folderu. W razie potrzeby można wyeksportować zasady z portalu Azure Portal i skopiować wyeksportowany plik do komputera klienckiego. Ta metoda umożliwia również zastąpienie nieaktualnego pliku zasad najnowszymi opublikowanymi zasadami.

Podczas eksportowania zasady, ta akcja spowoduje pobranie plik z rozszerzeniem zip z wieloma wersjami zasady, które odnosi się do różnych wersji klienta usługi Azure Information Protection:

1. Rozpakuj plik i skorzystaj z poniższej tabeli, aby zidentyfikować plik zasad, który należy. 
    
    |Nazwa pliku|Odpowiednia wersja klienta|
    |--------------------------|---------------------------------------------|
    |Policy1.1.msip |w wersji 1.2|
    |Policy1.2.msip |w wersji 1.3 1.7|
    |Policy1.3.msip |w wersji 1.8 i nowszych|
    
2. Zmień nazwę wskazany plik do **Policy.msip**, a następnie skopiować go do **%LocalAppData%\Microsoft\MSIP** folderu na komputerach, na których jest zainstalowany klient usługi Azure information protection. 


## <a name="hide-or-show-the-do-not-forward-button-in-outlook"></a>Ukryj lub Pokaż przycisk nie przesyłaj dalej w programie Outlook

Aby skonfigurować tę opcję zaleca przy użyciu [ustawienie zasad](../deploy-use/configure-policy-settings.md) **Dodawanie przycisku nie przesyłaj dalej do Wstążki programu Outlook**. Jednak również mogą skonfigurować tę opcję, za pomocą [Zaawansowane ustawienia klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal) skonfigurowanego w witrynie Azure portal.

Po skonfigurowaniu tego ustawienia, ukrywa lub pokazuje **nie przesyłaj dalej** przycisk na Wstążce w programie Outlook. To ustawienie nie ma wpływu na opcję nie przekazuj menu pakietu Office.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **DisableDNF**

- Wartość: **True** Aby ukryć przycisk, lub **False** wyświetlać przycisk

## <a name="make-the-custom-permissions-options-available-or-unavailable-to-users"></a>Być dostępne lub niedostępne opcje uprawnień niestandardowych dla użytkowników

Aby skonfigurować tę opcję zaleca przy użyciu [ustawienie zasad](../deploy-use/configure-policy-settings.md) **Udostępnij opcję niestandardowych uprawnień użytkownikom**. Jednak również mogą skonfigurować tę opcję, za pomocą [Zaawansowane ustawienia klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal) skonfigurowanego w witrynie Azure portal. 

Po skonfigurowaniu tego ustawienia i opublikowaniu zasad dla użytkowników, opcje uprawnień niestandardowych stają się widoczne dla użytkowników wybrać własne ustawienia ochrony lub są ukryte, aby użytkownicy nie mogą wybrać własne ustawienia ochrony, chyba że zostanie wyświetlony monit.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **EnableCustomPermissions**

- Wartość: **True** aby uwidocznić opcji uprawnień niestandardowych, lub **False** Aby ukryć tę opcję


## <a name="permanently-hide-the-azure-information-protection-bar"></a>Trwałe ukrycie paska usługi Azure Information Protection

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. Jej używać tylko wtedy, gdy [ustawienie zasad](../deploy-use/configure-policy-settings.md) **wyświetlany pasek Information Protection w aplikacjach pakietu Office** ustawiono **na**.

Gdy po skonfigurowaniu tego ustawienia i opublikowaniu zasad dla użytkowników użytkownik zdecyduje, aby nie wyświetlać paska usługi Azure Information Protection w aplikacjach pakietu Office, pasek pozostanie ukryty. Takie zachowanie ma miejsce, gdy użytkownik usunie zaznaczenie opcji **Pokaż pasek** na karcie **Strona główna**, w grupie **Ochrona**, w obszarze przycisku **Chroń**. To ustawienie nie daje efektu, jeśli użytkownik zamknie pasek za pomocą ikony **Zamknij ten pasek**.

Nawet gdy pasek usługi Azure Information Protection pozostaje ukryty, użytkownicy mogą wybrać etykietę z tymczasowo wyświetlanego paska, jeśli skonfigurowano zalecaną klasyfikację lub w przypadku, gdy dokument lub wiadomość e-mail musi mieć etykietę. 

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **EnableBarHiding**

- Wartość: **Prawda**


## <a name="enable-recommended-classification-in-outlook"></a>Włącz zalecana klasyfikacja w programie Outlook

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. To ustawienie jest w wersji zapoznawczej i mogą ulec zmianie.

Po skonfigurowaniu etykiety dla zalecana klasyfikacja, użytkownicy są monitowani o zaakceptowanie lub odrzucić zalecaną etykietę w programach Word, Excel i PowerPoint. To ustawienie rozszerza to zalecenie etykiety, można również wyświetlić w programie Outlook.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **OutlookRecommendationEnabled**

- Wartość: **Prawda**


## <a name="set-a-different-default-label-for-outlook"></a>Ustaw różne etykiety domyślne dla programu Outlook

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Po skonfigurowaniu tego ustawienia, program Outlook nie ma zastosowania etykiety domyślnej, skonfigurowanym w zasadach usługi Azure Information Protection, ustawienia **wybierz etykietę domyślną**. Zamiast tego programu Outlook, można zastosować różne etykiety domyślne lub brak etykiety.

Aby zastosować inną etykietę, należy określić identyfikator etykiety. Wartość Identyfikatora etykieta jest wyświetlana na **etykiety** bloku, wyświetlanie lub konfigurowanie zasad usługi Azure Information Protection w witrynie Azure portal. Dla plików, które mają stosowane etykiety, można również uruchomić [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) polecenia cmdlet programu PowerShell do identyfikowania etykiety (MainLabelId lub SubLabelId). Jeśli etykieta ma etykiet podrzędnych, zawsze określać identyfikator po prostu etykiety podrzędnej, a nie etykieta nadrzędnej.

Dlatego program Outlook nie ma zastosowania etykiety domyślnej, określić **Brak**.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **OutlookDefaultLabel**

- Wartość: \< **identyfikator etykiety**> lub **None**

## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>Usuń "Nie now" dla dokumentów, jeśli używasz obowiązkowego etykietowania

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Kiedy używasz [ustawienie zasad](../deploy-use/configure-policy-settings.md) z **wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**, użytkownicy są monitowani o wybranie etykiety są najpierw zapisywania dokumentu pakietu Office i po nich Wyślij wiadomość e-mail. W przypadku dokumentów, użytkownicy mogą wybrać **nie teraz** tymczasowo odrzucać monit o wybranie etykiety i wróć do dokumentu. Jednak nie można ich zamknąć zapisany dokument bez etykiet go. 

Po skonfigurowaniu tego ustawienia, usuwa **nie teraz** opcji użytkownicy muszą wybrać etykietę, przy pierwszym zapisaniu dokumentu.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **PostponeMandatoryBeforeSave**

- Wartość: **Fałsz**

## <a name="turn-on-classification-to-run-continuously-in-the-background"></a>Włącz klasyfikacji, aby uruchomić w sposób ciągły w tle

Ta opcja konfiguracji jest obecnie dostępna w wersji zapoznawczej i może ulec zmianie.

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Po skonfigurowaniu tego ustawienia, zmienia [domyślne zachowanie](../deploy-use/configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied) z jak klient usługi Azure Information Protection stosuje automatycznej i zalecanej etykiety w następujący sposób:

- Automatyczna klasyfikacja ma zastosowanie do programu Word, Excel, PowerPoint i Outlook. W przypadku dokumentów Automatyczna klasyfikacja działa w sposób ciągły w tle. Dla programu Outlook Automatyczna klasyfikacja jest uruchamiany, gdy są wysyłane wiadomości e-mail. 
    
    Nie można używać automatycznej klasyfikacji dokumentów, które zostały wcześniej oznaczone ręcznie lub wcześniej automatycznie z etykietą wyższej klasyfikacji. Wyjątkiem od to zachowanie jest użycie skanera usługi Azure Information Protection z parametrem OverrideLabel, ustaw wartość włączone.

- Zalecana klasyfikacja ma zastosowanie do programu Word, Excel i PowerPoint. Te dokumenty zaleca się Klasyfikacja działa w stale w tle. Nie można użyć zalecana klasyfikacja dla programu Outlook.
    
    Można użyć zalecana klasyfikacja dokumentów, które zostały wcześniej oznaczone, z lub bez wyższej klasyfikacji. 

Gdy klient usługi Azure Information Protection okresowo sprawdza, czy dokumenty dla reguł warunku, które można określić, to zachowanie umożliwia automatycznej i zalecanej klasyfikacji i ochrony dokumentów, które są przechowywane w usłudze SharePoint Online. Duże pliki również zapisać więcej szybkie ponieważ reguły warunek został już uruchomiony. 

Warunek reguły nie należy uruchamiać jako typy użytkownika w czasie rzeczywistym. Zamiast tego zadania uruchamiane okresowo jako zadanie w tle w przypadku modyfikowania dokumentu.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **RunPolicyInBackground**

- Wartość: **Prawda**

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Migrowanie etykiety z Secure Islands i innych rozwiązań etykietowania

Ta opcja konfiguracji jest obecnie dostępna w wersji zapoznawczej i może ulec zmianie.

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Dokumenty pakietu Office i dokumentów PDF, które są oznaczone przez Secure Islands można relabel te dokumenty za pomocą etykiety usługi Azure Information Protection przy użyciu mapowania, który zdefiniujesz. Ta metoda jest również użyć do ponownego użycia etykiet z innych rozwiązań, w przypadku ich etykiet w dokumentach pakietu Office. 

Tej opcji konfiguracji nowej etykiety usługi Azure Information Protection jest stosowany przez klienta usługi Azure Information Protection w następujący sposób:

- W przypadku dokumentów pakietu Office: po otwarciu dokumentu w aplikacji klasycznej, Nowa etykieta usługi Azure Information Protection jest wyświetlana jako zestawu i jest stosowana, gdy dokument zostanie zapisany.

- W Eksploratorze plików: W oknie dialogowym usługi Azure Information Protection nowej etykiety usługi Azure Information Protection jest wyświetlana jako zestawu i jest stosowana, gdy użytkownik wybierze **Zastosuj**. Jeśli użytkownik wybierze **anulować**, Nowa etykieta nie została zastosowana.

- Dla programu PowerShell: [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) zastosowanie nowej etykiety usługi Azure Information Protection. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) nie wyświetla nowej etykiety usługi Azure Information Protection, dopóki zostanie ustawiony przy użyciu innej metody.

- Skanera usługi Azure Information Protection: Odnajdywanie raportów, gdy będzie miał ustawienie nowej etykiety usługi Azure Information Protection i w trybie wymuszania można zastosować tej etykiety.

Ta konfiguracja wymaga określenia Klient zaawansowany, ustawienie o nazwie **LabelbyCustomProperty** dla każdej etykiety usługi Azure Information Protection, który ma być mapowany do starego etykiety. Następnie dla każdego wpisu, ustaw wartość używając następującej składni:

`[Azure Information Protection label ID],[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

Wartość Identyfikatora etykieta jest wyświetlana na **etykiety** bloku, wyświetlanie lub konfigurowanie zasad usługi Azure Information Protection w witrynie Azure portal. Aby określić etykiety podrzędnej, Etykieta nadrzędna musi być w tym samym zakresie lub w ramach globalnych zasad.

Podaj wybraną nazwę reguły migracji. Użyj opisową nazwę, która ułatwia ustalenie sposobu jedną lub więcej etykiet z poprzedniego rozwiązania etykietowania powinno zostać zamapowane etykiety usługi Azure Information Protection. Nazwa jest wyświetlana w raportach skanera, a w Podglądzie zdarzeń. 

### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Przykład 1: Mapowanie jeden do jednego z taką samą nazwę etykiety

Dokumenty, które ma etykietę "Poufne" Secure Islands powinien relabeled jako "Poufne" w usłudze Azure Information Protection.

W tym przykładzie:

- Etykiety usługi Azure Information Protection **poufne** identyfikatorze 1ace2cc3-14bc-4142-9125-bf946a70542c w etykiecie. 

- Etykieta Secure Islands jest przechowywany we właściwości niestandardowej o nazwie **klasyfikacji**.

Zaawansowane ustawienia klienta:

    
|Nazwa|Wartość|
|---------------------|---------|
|LabelbyCustomProperty|1ace2cc3-14bc-4142-9125-bf946a70542c, "Secure Islands etykiety są poufne", klasyfikacji, poufne|

### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Przykład 2: Mapowanie jeden do jednego dla nazwy innej etykiety

Dokumenty oznaczone jako "Poufne" przez Secure Islands powinien relabeled jako "Wysoce poufne" w usłudze Azure Information Protection.

W tym przykładzie:

- Etykiety usługi Azure Information Protection **wysoce poufne** identyfikatorze 3e9df74d-3168-48af-8b11-037e3021813f w etykiecie.

- Etykieta Secure Islands jest przechowywany we właściwości niestandardowej o nazwie **klasyfikacji**.

Zaawansowane ustawienia klienta:

    
|Nazwa|Wartość|
|---------------------|---------|
|LabelbyCustomProperty|3e9df74d-3168-48af-8b11-037e3021813f, "Secure Islands etykiety jest wrażliwa na", klasyfikacji, liter|


### <a name="example-3-many-to-one-mapping-of-label-names"></a>Przykład 3: Wiele do jednego mapowania nazw etykiet

Dwie etykiety Secure Islands, które zawierają słowo "Wewnętrzna", i chcesz, aby dokumenty, które mają jedną z tych etykiet Secure Islands relabeled jako "Ogólne" w usłudze Azure Information Protection.

W tym przykładzie:

- Etykiety usługi Azure Information Protection **ogólne** identyfikatorze 2beb8fe7-8293-444 c-9768-7fdc6f75014d w etykiecie.

- Etykieta Secure Islands jest przechowywany we właściwości niestandardowej o nazwie **klasyfikacji**.

Zaawansowane ustawienia klienta:

    
|Nazwa|Wartość|
|---------------------|---------|
|LabelbyCustomProperty|2beb8fe7-8293-444c-9768-7fdc6f75014d, "Secure Islands etykieta zawiera wewnętrzne" klasyfikacji. \*Wewnętrznego.\*|


## <a name="label-an-office-document-by-using-an-existing-custom-property"></a>Etykieta dokumentu pakietu Office przy użyciu istniejącej właściwości niestandardowej

> [!NOTE]
> Jeśli używasz tej konfiguracji i z poprzedniej sekcji, aby przeprowadzić migrację z innego rozwiązania etykietowania, etykietowania ustawienie migracji ma pierwszeństwo. 

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

Jednakże, gdy konto usługi, na którym uruchomiono skaner ma wyłącznie prawa, które zostały opisane w [wymagania wstępne skanera](../deploy-use/deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner), poziom o niskiej integralności nie jest konieczne i nie jest zalecane, ponieważ negatywnie wpływa na wydajność. 

Aby uzyskać więcej informacji na temat poziomów spójności Windows, zobacz [co to jest mechanizm integralności Windows?](https://msdn.microsoft.com/library/bb625957.aspx)

Aby skonfigurować zaawansowane ustawienia tak, aby skaner uruchamiana z poziomem integralności, który jest automatycznie przypisywany przez Windows (konta użytkownika standardowego jest uruchamiany o średnim poziomie integralności), wprowadź następujące parametry:

- Klucz: **ProcessUsingLowIntegrity**

- Wartość: **Fałsz**


## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>Integracja z klasyfikacją wiadomości programu Exchange dla rozwiązań etykietowania urządzeń przenośnych

Mimo że program Outlook w sieci web nie obsługuje jeszcze natywnie klasyfikacji usługi Azure Information Protection i ochrony, aby rozszerzyć etykiet usługi Azure Information Protection dla użytkowników mobilnych, gdy korzystają z programu Outlook w, można użyć klasyfikacji wiadomości programu Exchange w sieci Web. Outlook Mobile nie obsługuje klasyfikacji wiadomości programu Exchange.

W tym celu: 

1. Użyj polecenia cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) środowiska PowerShell programu Exchange w celu utworzenia klasyfikacji wiadomości z właściwością Name, która mapuje do nazw etykiet użytkownika w zasadach usługi Azure Information Protection. 

2. Tworzenie reguły przepływu poczty programu Exchange dla każdej etykiety: Zastosuj regułę, jeśli właściwości wiadomości obejmują skonfigurowaną przez Ciebie klasyfikację, a następnie zmodyfikuj właściwości wiadomości, aby ustawić nagłówek wiadomości. 

     Informacje, jakie należy określić dla nagłówka wiadomości, można zidentyfikować, sprawdzając nagłówki internetowe wiadomości e-mail wysłanej i sklasyfikowanej za pomocą etykiety usługi Azure Information Protection. Wyszukaj nagłówek **msip_labels** i ciąg, który następuje zaraz po nim, łącznie ze średnikiem. Przykład:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Następnie dla nagłówka wiadomości w regule określ element **msip_labels** dla nagłówka oraz pozostałe elementy ciągu dla wartości nagłówka. Przykład:
    
    ![Przykład reguły przepływu poczty usługi Exchange Online, która ustawia nagłówek wiadomości dla określonej etykiety usługi Azure Information Protection](../media/exchange-rule-for-message-header.png)
    
    Uwaga: Jeśli etykieta jest etykiety podrzędnej, należy także określić etykiecie nadrzędnej przed etykietę podrzędną w wartości nagłówka przy użyciu tego samego formatu. Na przykład jeśli Twoja etykietę podrzędną ma identyfikator GUID 27efdf94-80a0 - 4d-02-b88c-b615c12d69a9, wartość może wyglądać następująco: `MSIP_Label_ab70158b-bdcc-42a3-8493-2a80736e9cbd_Enabled=True;MSIP_Label_27efdf94-80a0-4d02-b88c-b615c12d69a9_Enabled=True;`

Przed testowaniem tej konfiguracji należy pamiętać, że często występuje opóźnienie podczas tworzenia lub edytowania reguły przepływu poczty (na przykład godzinne). Gdy reguła jest aktywna, następujące zdarzenia teraz się zdarzyć, gdy użytkownicy używają aplikacji Outlook Web Access lub klienta urządzenia przenośnego, który obsługuje protokół Exchange ActiveSync IRM: 

- Użytkownicy wybierają klasyfikację wiadomości programu Exchange i wysyłają wiadomość e-mail.

- Reguła programu Exchange wykrywa klasyfikację programu Exchange i odpowiednio modyfikuje nagłówek wiadomości w celu dodania klasyfikacji usługi Azure Information Protection.

- Jeśli mają zainstalowanego klienta usługi Azure Information Protection adresatów wewnętrznych wyświetlają wiadomość e-mail w programie Outlook, widzą przypisane etykiety usługi Azure Information Protection. 

Jeśli etykiety usługi Azure Information Protection zastosowania ochrony, Dodaj tę ochronę do konfiguracji reguły: wybierając opcję modyfikacji zabezpieczeń wiadomości, Zastosuj ochronę praw, a następnie wybierz szablon usług RMS lub opcję nie przesyłaj dalej.

Można również skonfigurować reguły przepływu poczty na potrzeby mapowania odwrotnego. Po wykryciu etykiety usługi Azure Information Protection ustaw odpowiednią klasyfikację wiadomości programu Exchange:

- Dla każdej etykiety usługi Azure Information Protection: Utwórz reguły przepływu poczty, która będzie stosowana, jeśli **msip_labels** nagłówek zawiera nazwę Twojej etykiety (na przykład **ogólne**) i stosować wiadomości Klasyfikacja, który jest mapowany do tej etykiety.


## <a name="next-steps"></a>Następne kroki
Po dostosowaniu klienta usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi, które mogą być przydatne podczas obsługi tego klienta:

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
