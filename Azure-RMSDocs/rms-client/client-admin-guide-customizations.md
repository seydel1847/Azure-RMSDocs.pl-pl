---
title: "Niestandardowe konfiguracje klienta usługi Azure Information Protection"
description: "Informacje na temat dostosowywania klienta usługi Azure Information Protection dla systemu Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/25/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 32226274c8b50b02e453f1c1b6655fb01b4ec942
ms.sourcegitcommit: 7bec3dfe3ce61793a33d53691046c5b2bdba3fb9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="custom-configurations-for-the-azure-information-protection-client"></a>Niestandardowe konfiguracje klienta usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Poniższe informacje służą do tworzenia zaawansowanych konfiguracji, które mogą być wymagane w przypadku określonych scenariuszy lub podzbiorów użytkowników podczas zarządzania klientem usługi Azure Information Protection.

Niektóre z tych ustawień wymagają edycji rejestru. Inne korzystają z ustawień zaawansowanych, które należy skonfigurować w witrynie Azure Portal, a następnie opublikować do pobrania przez klientów. Ponadto pewne ustawienia mogą być dostępne tylko w wersji zapoznawczej klienta usługi Azure Information Protection. W przypadku tych ustawień minimalny numer wersji klienta został określony w dokumentacji. W przypadku ustawień i konfiguracji obsługiwanych w ogólnodostępnej wersji klienta minimalny numer wersji klienta nie jest określony w dokumentacji.

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>Jak skonfigurować zaawansowane ustawienia konfiguracji klienta w portalu

Ta konfiguracja jest obecnie dostępna w wersji zapoznawczej.

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator zabezpieczeń lub administrator globalny, a następnie przejdź do bloku **Azure Information Protection**.

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

## <a name="sign-in-as-a-different-user"></a>Zaloguj się jako inny użytkownik

W środowisku produkcyjnym użytkownik nie ma zazwyczaj potrzeby logowania się jako inny użytkownik w przypadku korzystania z klienta usługi Azure Information Protection. Jednak jako administrator możesz potrzebować możliwości zalogowania się jako inny użytkownik podczas fazy testowania. 

Aby sprawdzić, za pomocą którego konta nastąpiło logowanie, otwórz okno dialogowe **Microsoft Azure Information Protection**, uruchom aplikację pakietu Office i na karcie **Narzędzia główne** w grupie **Ochrona** kliknij opcję **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. Nazwa konta jest widoczna w sekcji **Stan klienta**.

Pamiętaj także o sprawdzeniu wyświetlonej nazwy domeny konta użytego do zalogowania. Fakt, że logowanie następuje przy użyciu prawidłowej nazwy konta, ale niewłaściwej domeny, można łatwo przeoczyć. W przypadku użycia niewłaściwego konta może wystąpić problem z pobraniem zasad usługi Azure Information Protection albo nie będą widoczne oczekiwane etykiety lub zachowania.

Aby zalogować się jako inny użytkownik:

1. W zależności od wersji klienta usługi Azure Information Protection: 
    
    - W ogólnie dostępnej wersji klienta usługi Azure Information Protection: w edytorze rejestru przejdź do pozycji **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP** i usuń wartość **TokenCache** (i jej skojarzone dane wartości).
    
    - W bieżącej wersji zapoznawczej klienta usługi Azure Information Protection: przejdź do pozycji **%localappdata%\Microsoft\MSIP** i usuń plik **TokenCache**.

2. Uruchom ponownie wszystkie otwarte aplikacje pakietu Office i zaloguj się przy użyciu innego konta użytkownika. Jeśli w aplikacji pakietu Office nie został wyświetlony monit o zalogowanie się do usługi Azure Information Protection, wróć do okna dialogowego **Microsoft Azure Information Protection** i kliknij przycisk **Zaloguj** w zaktualizowanej sekcji **Stan klienta**.

Dodatkowo:

- To rozwiązanie jest obsługiwane w przypadku logowania się jako inny użytkownik z tej samej dzierżawy. Nie jest ono obsługiwane w przypadku logowania się jako inny użytkownik z innej dzierżawy. Do testowania usługi Azure Information Protection z wieloma dzierżawami użyj różnych komputerów.

- Jeśli korzystasz z logowania jednokrotnego, musisz wylogować się z systemu Windows i po wprowadzeniu zmian w rejestrze zalogować się przy użyciu innego konta użytkownika. Klient usługi Azure Information Protection przeprowadzi automatyczne uwierzytelnienie przy użyciu aktualnie zalogowanego konta użytkownika.

- Jeśli chcesz zresetować ustawienia użytkownika dla usługi Azure Rights Management, możesz to zrobić przy użyciu opcji **Pomoc i opinie**.

- Aby usunąć aktualnie pobrane zasady usługi Azure Information Protection, usuń plik **Policy.msip** z folderu **%localappdata%\Microsoft\MSIP**.

- Jeśli masz bieżącą wersję zapoznawczą klienta usługi Azure Information Protection, możesz użyć opcji **Resetuj ustawienia** w obszarze **Pomoc i opinie**, aby wylogować się i usunąć aktualnie pobrane zasady usługi Azure Information Protection.

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ukryj opcję menu Klasyfikuj i chroń w Eksploratorze plików systemu Windows

Ta opcja konfiguracji jest obecnie dostępna w wersji zapoznawczej.

Użytkownicy korzystający z klienta usługi Azure Information Protection w wersji 1.3.0.0 lub nowszej mogą skonfigurować tę konfigurację zaawansowaną, edytując rejestr. 

Utwórz następującą nazwę wartości DWORD (z dowolnymi danymi wartości):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Obsługa odłączonych komputerów

Domyślnie klient usługi Azure Information Protection automatycznie próbuje połączyć się z usługą Azure Information Protection, aby pobrać najnowsze zasady usługi Azure Information Protection. W przypadku komputera pozbawionego w danym momencie możliwości nawiązania połączenia z Internetem można zapobiec próbie nawiązania połączenia z usługą, edytując rejestr. 

Znajdź następującą nazwę wartości i ustaw dane wartości **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Upewnij się, że w folderze **%localappdata%\Microsoft\MSIP** znajduje się prawidłowy plik zasad klienta o nazwie **Policy.msip**. W razie potrzeby można wyeksportować zasady z portalu Azure Portal i skopiować wyeksportowany plik do komputera klienckiego. Ta metoda umożliwia również zastąpienie nieaktualnego pliku zasad najnowszymi opublikowanymi zasadami.

## <a name="hide-the-do-not-forward-button-in-outlook"></a>Ukrywanie przycisku Nie przesyłaj dalej w programie Outlook

Ta opcja konfiguracji jest obecnie dostępna w wersji zapoznawczej.

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. To ustawienie również wymaga wersji zapoznawczej klienta usługi Azure Information Protection o minimalnym numerze **1.8.41.0**.

Po skonfigurowaniu tego ustawienia przycisk **Nie przesyłaj dalej** na wstążce programu Outlook zostanie ukryty. Ta opcja nie zostanie jednak ukryta w menu pakietu Office.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **DisableDNF**

- Wartość: **Prawda**

## <a name="make-the-custom-permissions-options-unavailable-to-users"></a>Zablokowanie dostępu użytkowników do opcji uprawnień niestandardowych

Ta opcja konfiguracji jest obecnie dostępna w wersji zapoznawczej.

Ta konfiguracja korzysta z [zaawansowanych ustawień klienta](#how-to-configure-advanced-client-configuration-settings-in-the-portal), które należy skonfigurować w witrynie Azure Portal. 

Po skonfigurowaniu tego ustawienia i opublikowaniu zasad dla użytkowników opcje uprawnień niestandardowych w następujących lokalizacjach staną się niedostępne do wyboru przez użytkowników:

- W aplikacjach pakietu Office: karta **Strona główna** > grupa **Ochrona** > **Chroń** > **Uprawnienia niestandardowe**

- W Eksploratorze plików: kliknij prawym przyciskiem myszy opcję **Klasyfikuj i chroń** > **Uprawnienia niestandardowe**

To ustawienie nie ma wpływu na uprawnienia niestandardowe, które można skonfigurować przy użyciu opcji menu pakietu Office. 

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **EnableCustomPermissions**

- Wartość: **Fałsz**

## <a name="permanently-hide-the-azure-information-protection-bar"></a>Trwałe ukrycie paska usługi Azure Information Protection

Ta konfiguracja korzysta z ustawień zaawansowanych, które należy skonfigurować w witrynie Azure Portal. To ustawienie również wymaga wersji zapoznawczej klienta usługi Azure Information Protection o minimalnym numerze **1.9.58.0**.

Gdy po skonfigurowaniu tego ustawienia i opublikowaniu zasad dla użytkowników użytkownik zdecyduje, aby nie wyświetlać paska usługi Azure Information Protection w aplikacjach pakietu Office, pasek pozostanie ukryty. Takie zachowanie ma miejsce, gdy użytkownik usunie zaznaczenie opcji **Pokaż pasek** na karcie **Strona główna**, w grupie **Ochrona**, w obszarze przycisku **Chroń**. To ustawienie nie daje efektu, jeśli użytkownik zamknie pasek za pomocą ikony **Zamknij ten pasek**.

Nawet gdy pasek usługi Azure Information Protection pozostaje ukryty, użytkownicy mogą wybrać etykietę z tymczasowo wyświetlanego paska, jeśli skonfigurowano zalecaną klasyfikację lub w przypadku, gdy dokument lub wiadomość e-mail musi mieć etykietę. To ustawienie nie ma również wpływu na konfigurowane przez Ciebie lub innych użytkowników etykiety, takie jak klasyfikacja ręczna lub automatyczna, albo ustawienie etykiety domyślnej.

Aby skonfigurować to ustawienie zaawansowane, wprowadź następujące parametry:

- Klucz: **EnableBarHiding**

- Wartość: **Prawda**

## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>Integracja z klasyfikacją wiadomości programu Exchange dla rozwiązań etykietowania urządzeń przenośnych

Pomimo tego, że program Outlook w sieci Web nie obsługuje natywnie klasyfikacji ani ochrony usługi Azure Information Protection, można użyć klasyfikacji wiadomości programu Exchange w celu poszerzenia zasięgu używania etykiet usługi Azure Information Protection o użytkowników urządzeń przenośnych.

W tym celu: 

1. Użyj polecenia cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) środowiska PowerShell programu Exchange w celu utworzenia klasyfikacji wiadomości z właściwością Name, która mapuje do nazw etykiet użytkownika w zasadach usługi Azure Information Protection. 

2. Utwórz dla każdej etykiety regułę transportu programu Exchange: zastosuj regułę, jeśli właściwości wiadomości obejmują skonfigurowaną przez Ciebie klasyfikację, a następnie zmodyfikuj właściwości wiadomości, aby ustawić nagłówek wiadomości. 

    Informacje, jakie należy określić dla nagłówka wiadomości, można zidentyfikować, sprawdzając nagłówki internetowe wiadomości e-mail wysłanej i sklasyfikowanej za pomocą etykiety usługi Azure Information Protection. Wyszukaj nagłówek **msip_labels** i ciąg, który następuje zaraz po nim, łącznie ze średnikiem. Korzystając z poprzedniego przykładu:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Następnie dla nagłówka wiadomości w regule określ element **msip_labels** dla nagłówka oraz pozostałe elementy ciągu dla wartości nagłówka. Na przykład:
    
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