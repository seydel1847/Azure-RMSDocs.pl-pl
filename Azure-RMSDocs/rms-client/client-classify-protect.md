---
title: "Klasyfikować i chronić pliki i wiadomości e-mail przy użyciu usługi Azure Information Protection"
description: "Instrukcje dotyczące sposobu klasyfikowania i ochrony dokumentów i wiadomości e-mail użytkownika."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: bbd2d81149dd860d7707b6eee83dacce9c13dd54
ms.sourcegitcommit: 92bbef77091c66300e0d2acce60c064ffe314752
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2017
---
# <a name="user-guide-classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Podręcznik użytkownika: Sklasyfikowanych i chronionych plików lub wiadomości e-mail przy użyciu usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

> [!NOTE]
> Użyj tych instrukcji, aby ułatwić klasyfikować i chronić dokumenty i wiadomości e-mail. Jeśli potrzebne tylko klasyfikowania i nie chronić dokumenty i wiadomości e-mail, zobacz [instrukcje tylko do klasyfikowania](client-classify-protect.md). Jeśli nie masz pewności, zestaw instrukcji do użycia, skontaktuj się z administratorem lub pomocą techniczną.

Najprostszy sposób klasyfikowania i ochrony dokumentów i wiadomości e-mail jest dostępny podczas ich tworzenia lub edytowania za pośrednictwem aplikacji komputerowych pakietu Office: **Word**, **Excel**, **PowerPoint** i **Outlook**. 

Można jednak również klasyfikować i chronić pliki za pomocą **Eksploratora plików**. Ta metoda obsługuje inne typy plików i jest wygodny sposób klasyfikować i chronić wielu plików jednocześnie. Ta metoda zapewnia ochronę dokumentów pakietu Office, plików PDF, plików tekstowych i obrazów, a także wielu innych plików. 

Etykiety dotyczy ochrony dokumentu, dokument chroniony nie jest odpowiedni do zapisania w programie SharePoint lub usługi OneDrive. Te lokalizacje nie obsługują następujące chronionych plików: współtworzenia, Office Online wyszukiwania, dokumentu podglądu, miniatur i zbieranie elektronicznych materiałów dowodowych. 

### <a name="safely-share-a-file-with-people-outside-your-organization"></a>Bezpieczne udostępnianie pliku osobom spoza organizacji

Pliki, które są chronione, są bezpiecznie udostępniane innym użytkownikom. Na przykład Dołącz plik do wiadomości e-mail.

W przypadku regularnego udostępniania plików osobom spoza organizacji, administrator może skonfigurować etykietę ustawiającą ochronę w taki sposób, że te osoby mogą je odczytać. Możesz także użyć [aplikacji pakietu Office](#set-custom-permissions-for-a-document) lub [Eksploratora plików](#using-file-explorer-to-classify-and-protect-files), aby ustawić uprawnienia niestandardowe dla pliku przed jego udostępnieniem. Jeśli zostały ustawione uprawnienia niestandardowe, a plik jest już chroniony do użytku wewnętrznego, w celu zachowania pierwotnych uprawnień należy najpierw utworzyć jego kopię. Kopii tej należy użyć do ustawienia uprawnień niestandardowych.  

Gdy plik jest chroniony za pomocą uprawnień niestandardowych, należy użyć standardowego mechanizmu udostępniania dla tego pliku. Jeśli osoby, którym udostępniasz pliki, otrzymają chroniony plik po raz pierwszy, mogą potrzebować instrukcji ich wyświetlenia. Można dla nich skopiować i wkleić następujący komunikat: **Ten plik został przeze mnie objęty ochroną w ramach usługi Microsoft Azure Information Protection. W przypadku użycia po raz pierwszy zobacz te [instrukcje](https://aka.ms/rms-signup).**

## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Korzystanie z aplikacji pakietu Office do klasyfikowania i ochrony dokumentów i wiadomości e-mail

Za pomocą paska usługi Azure Information Protection wybierz jedną z etykiet, które zostały skonfigurowane dla Ciebie. 

Przykładowo na poniższej ilustracji przedstawiono, że dokument nie został jeszcze oznaczony etykietą, ponieważ parametr **Poufność** ma wartość **Nieustawiona**. Aby ustawić etykiety, takie jak "Ogólne", kliknij pozycję **ogólne**. Jeśli nie masz pewności, którą etykietę zastosować do bieżącego dokumentu lub wiadomości e-mail, użyj etykietki narzędzi, aby dowiedzieć się więcej o każdej etykiecie i właściwym jej zastosowaniu. 

![Przykład paska usługi Azure Information Protection](../media/info-protect-bar-not-set-callout.png)

Jeśli etykieta jest już zastosowana do dokumentu i chcesz ją zmienić, możesz wybrać inną etykietę. Jeśli na pasku nie są wyświetlane etykiety, kliknij najpierw ikonę **Edytuj etykietę** obok wartości bieżącej etykiety.

> [!TIP]
> Możesz też wybrać etykiety z **Chroń** przycisk na **pliku** kartę.

Oprócz ręcznego wybierania etykiet można je też ustawiać w następujący sposób:

- Administrator skonfigurował etykietę domyślną, którą można zachować lub zmienić.

- Administrator skonfigurował zalecane monity o wybór określonej etykiety po wykryciu poufnych danych. Możesz zaakceptować zalecenie (i etykieta zostanie dodana) lub je odrzucić (zalecana etykieta nie zostanie dodana).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Wyjątki dotyczące paska usługi Azure Information Protection 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Nie widzisz tego paska usługi Information Protection w aplikacjach pakietu Office?

- Być może nie został [zainstalowany](install-client-app.md) klient usługi Azure Information Protection lub klient jest uruchomiony w [trybie z samą ochroną](client-protection-only-mode.md).
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed-on-the-bar"></a>Czy etykieta, który powinna się pojawić na pasku, nie jest wyświetlana? 

- Jeśli administrator skonfigurował ostatnio nową etykietę, zamknij wszystkie wystąpienia aplikacji pakietu Office i otwórz ją ponownie. Ta akcja sprawdza zmiany etykiet.

- Jeśli brakująca etykieta ustawia ochronę, być może posiadana wersja pakietu Office nie obsługuje ochrony w ramach usługi Rights Management. Aby sprawdzić, kliknij przycisk **Chroń** > **Pomoc i opinie**. W oknie dialogowym, sprawdź, czy istnieje komunikat **stanu klienta** sekcji informacją **ten klient nie ma licencji na pakiet Office Professional Plus.** 

- Etykieta może być objęta zasadami o określonym zakresie, które nie obejmują Twojego konta. Skontaktuj się z administratorem lub pomocą techniczną.

### <a name="set-custom-permissions-for-a-document"></a>Ustawienie uprawnień niestandardowych dla dokumentu

Zamiast korzystać z ustawień, które administrator uwzględnił dla wybranej etykiety, możesz określić dla dokumentu własne ustawienia ochrony.

1. Na karcie **Narzędzia główne**, w grupie **Ochrona**, kliknij kolejno pozycje **Chroń** > **Uprawnienia niestandardowe**:

    ![Opcja Uprawnienia niestandardowe](../media/custom-permissions-callout.png)
    
    Należy pamiętać, że wszystkie niestandardowe uprawnienia określone przez użytkownika zastępują, a nie uzupełniają, ustawienia ochrony, które administrator mógł zdefiniować dla wybranej etykiety.  

2. W oknie dialogowym **Microsoft Azure Information Protection** określ następujące elementy:

    - **Chroń za pomocą uprawnień niestandardowych**: aby możliwe było określenie i zastosowanie uprawnień niestandardowych, ta opcja musi być zaznaczona. Usuń zaznaczenie tej opcji, aby usunąć wszelkie uprawnienia niestandardowe.
    
    - **Wybierz uprawnienia**: aby chronić plik, zapewniając możliwość dostępu do niego wyłącznie sobie, wybierz opcję **Tylko dla mnie**. W przeciwnym razie wybierz poziom dostępu dla poszczególnych osób.
    
    - **Wybierz użytkowników, grupy lub organizacje**: Określ osoby, które powinny mieć wybrane przez Ciebie uprawnienia do pliku lub plików. Wpisz dla każdej z osób pełny adres e-mail, adres e-mail grupy lub — dla wszystkich użytkowników należących do organizacji — nazwę domeny. Uwaga: osobiste adresy e-mail nie są obecnie obsługiwane.
        
        Jeśli bieżąca wersja klienta, umożliwia także ikonę książki adresowej wybierz z książki adresowej użytkowników lub grup.
    
    - **Ważność dostępu**: Wybierz tę opcję tylko w przypadku harmonogramów pliki, aby wybrane osoby nie będzie można otworzyć wybranego pliku lub plików po dacie, które można ustawić. Nadal będzie można otworzyć oryginalny plik, ale po północy (bieżącej strefy czasowej), na dzień, w którym można ustawić określonej osoby nie będzie mógł otworzyć plik.

5. Kliknij przycisk **Zastosuj** i poczekaj na komunikat **Zastosowano uprawnienia niestandardowe**. Następnie kliknij przycisk **Zamknij**.

### <a name="safely-sharing-by-email"></a>Bezpieczne udostępnianie pocztą e-mail

Po udostępnieniu dokumentów pakietu Office za pośrednictwem poczty e-mail, możesz dołączyć dokument do wiadomości e-mail możesz chronić i dokumentu jest automatycznie chronione przez te same ograniczenia, które są stosowane do wiadomości e-mail. 

Jednak zaleca się najpierw ochrony dokumentu, a następnie dołącz do wiadomości e-mail. Chronić wiadomości e-mail oraz wiadomości e-mail zawiera poufne informacje. Dwie zalety ochrony dokumentu, przed dołączeniem do wiadomości e-mail:

- Można śledzić i w razie potrzeby odwołać dokumentu po pocztą e-mail go.

- Można stosować różne uprawnienia do dokumentu niż do wiadomości e-mail.

## <a name="using-file-explorer-to-classify-and-protect-files"></a>Klasyfikowanie i ochrona plików za pomocą Eksploratora plików

Korzystając z Eksploratora plików, można szybko klasyfikować i chronić pojedynczy plik, wiele plików lub folder. 

Po wybraniu folderu do wszystkich plików znajdujących się w nim i jego podfolderach zostaną automatycznie przypisane ustawione opcje ochrony. Jednak nowe pliki tworzone w tym folderze lub jego podfolderach nie są konfigurowane automatycznie z użyciem tych opcji.

Jeśli podczas używania Eksploratora plików do klasyfikowania i ustawiania ochrony plików jedna etykieta lub większa ich liczba jest wyszarzona, wybrane pliki nie obsługują klasyfikacji. W przypadku tych plików można wybrać etykietę tylko wtedy, gdy administrator skonfigurował etykietę do stosowania ochrony. Można też określić własne ustawienia ochrony. 

Niektóre pliki są automatycznie wykluczane z klasyfikacji i ochrony, ponieważ ich zmiana mogłaby spowodować zawieszanie się komputera. Pomimo zaznaczenia tych plików, są one pomijane jako wykluczone foldery i pliki. Przykładowo są to pliki wykonywalne i foldery systemu Windows.

W podręczniku administratora podano pełną listę typów plików obsługiwanych oraz tych plików i folderów, które są automatycznie wykluczane: [Typy plików obsługiwane przez klienta usługi Azure Information Protection](client-admin-guide-file-types.md).


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>Aby sklasyfikować i chronić plik za pomocą Eksploratora plików

1. W Eksploratorze plików wybierz plik, wiele plików lub folder. Kliknij prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**. Na przykład:
    
    ![Kliknięcie prawym przyciskiem myszy w oknie Eksploratora plików — klasyfikowanie i ochrona za pomocą usługi Azure Information Protection](../media/right-click-classify-protect-folder.png)

2. W oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** użyj etykiet w sposób analogiczny jak w aplikacji pakietu Office, który ustawia klasyfikację i ochronę w sposób zdefiniowany przez administratora. 

    - Jeśli nie można wybrać żadnej etykiety (są wyszarzone): wybrany plik nie obsługuje klasyfikacji, ale można go chronić z użyciem uprawnień niestandardowych (krok 3). Na przykład:

    ![Brak dostępnych etykiet w oknie dialogowym Klasyfikacja i ochrona — Azure Information Protection**](../media/info-protect-dialog-labels-dimmed.png)
    
    - Jeśli w tym oknie dialogowym nie widać etykiet, a tylko opcję **Ochrona wstępnie zdefiniowana przez firmę**: klient jest uruchomiony w [trybie z samą ochroną](client-protection-only-mode.md). Należy wybrać szablon, aby zastosować ochronę skonfigurowaną przez administratora, lub wybrać opcję **Uprawnienia niestandardowe**, aby określić własne ustawienia ochrony, i przejść do kroku 4.
    
    ![Brak etykiet w oknie dialogowym Klasyfikacja i ochrona — Azure Information Protection**](../media/info-protect-dialog-labels-protection-only.png)
    
3. Jeśli chcesz określić własne ustawienia ochrony zamiast korzystać z ustawień, które administrator mógł dołączyć do wybranej etykiety, zaznacz opcję **Chroń za pomocą uprawnień niestandardowych**.
    
    Wszystkie niestandardowe uprawnienia określone przez użytkownika zastępują, a nie uzupełniają, ustawienia ochrony, które administrator mógł zdefiniować dla wybranej etykiety.  

4. Po wybraniu opcji ustawień niestandardowych należy określić następujące ustawienia:

    - **Wybierz uprawnienia**: Wybierz poziom dostępu, który ma być przypisany użytkownikom przy ochronie wybranego pliku lub plików.
    
    - **Wybierz użytkowników, grupy lub organizacje**: Określ osoby, które powinny mieć wybrane przez Ciebie uprawnienia do pliku lub plików. Wpisz dla każdej z osób pełny adres e-mail, adres e-mail grupy lub — dla wszystkich użytkowników należących do organizacji — nazwę domeny. Uwaga: osobiste adresy e-mail nie są obecnie obsługiwane.
    
    Alternatywnie można ikonę książki adresowej wybierz z książki adresowej użytkowników lub grupy.
        
    - **Ważność dostępu**: wybierz tę opcję tylko dla plików uwarunkowanych czasowo, tak aby wybrane osoby nie mogły otworzyć danego pliku lub plików po ustawionym dniu. Otwarcie oryginalnego pliku przez Ciebie będzie nadal możliwe, ale po północy (w Twojej strefie czasowej) określonego dnia podane osoby nie będą mogły otworzyć pliku.
    
    Pamiętaj, że jeśli to ustawienie zostało wcześniej skonfigurowane przy użyciu uprawnień niestandardowych z aplikacji pakietu Office 2010, w tym oknie dialogowym nie jest wyświetlana podana data wygaśnięcia, chociaż nadal jest ustawiona. Ten problem z wyświetlaniem występuje tylko w przypadku, gdy datę wygaśnięcia skonfigurowano w pakiecie Office 2010.

5. Kliknij przycisk **Zastosuj** i poczekaj na pojawienie się komunikatu **Ukończona praca**, aby zobaczyć wyniki. Następnie kliknij przycisk **Zamknij**.

Wybrany plik lub pliki są teraz sklasyfikowane i chronione zgodnie z wybranymi przez Ciebie opcjami. W niektórych przypadkach (kiedy dodanie ochrony powoduje zmianę rozszerzenia nazwy pliku) oryginalny plik znajdujący się w Eksploratorze plików zostaje zastąpiony nowym plikiem oznaczonym ikoną kłódki, sygnalizującą ochronę za pomocą usługi Azure Information Protection. Na przykład:

![Chroniony plik z ikoną kłódki usługi Azure Information Protection](../media/Pfile.png)

Jeśli zmienisz zdanie na temat klasyfikacji i ochrony lub zechcesz później zmodyfikować ustawienia, po prostu powtórz proces z nowymi ustawieniami.

Wcześniej określona dla pliku klasyfikacja i ochrona obowiązuje nadal, nawet jeśli plik zostanie wysłany za pomocą poczty e-mail lub zapisany w innej lokalizacji. Jeśli plik jest chroniony, można śledzić, w jaki sposób jest używany, i w razie potrzeby odwołać dostęp do niego. Aby uzyskać więcej informacji, zobacz temat [Śledzenie i odwoływanie dokumentów chronionych podczas korzystania z usługi Azure Information Protection](client-track-revoke.md). 


## <a name="other-instructions"></a>Inne instrukcje
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

-   [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Dodatkowe informacje dla administratorów    
Zobacz [Konfigurowanie zasad usługi Azure Information Protection](../deploy-use/configure-policy.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
