---
title: "Klasyfikowanie i ochrona za pomocą usługi Azure Information Protection"
description: "Instrukcje dotyczące sposobu klasyfikowania i ochrony dokumentów i wiadomości e-mail użytkownika."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 6d727cdbfba193a80742441ae1a372d2e8fbd699
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Klasyfikowanie i ochrona pliku lub wiadomości e-mail za pomocą usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

Najprostszy sposób klasyfikowania i ochrony dokumentów i wiadomości e-mail jest dostępny podczas ich tworzenia lub edytowania za pośrednictwem aplikacji komputerowych pakietu Office: **Word**, **Excel**, **PowerPoint** i **Outlook**. 

Pliki można jednak klasyfikować i chronić także za pomocą **Eksploratora plików**, który obsługuje dodatkowe typy plików i stanowi wygodny sposób klasyfikowania oraz ochrony wielu plików jednocześnie. Ta metoda zapewnia ochronę dokumentów pakietu Office, plików PDF, plików tekstowych i obrazów, a także wielu innych plików. 

### <a name="safely-share-a-file-with-people-outside-your-organization"></a>Bezpieczne udostępnianie pliku osobom spoza organizacji

Pliki, które są chronione, są bezpiecznie udostępniane innym użytkownikom. Na przykład można dołączyć plik do wiadomości e-mail lub wysłać zaproszenie z witryny usługi SharePoint.

W przypadku regularnego udostępniania plików osobom spoza organizacji, administrator może skonfigurować etykietę ustawiającą ochronę w taki sposób, że te osoby mogą je odczytać. Alternatywnie można użyć [Eksploratora plików, aby ustawić uprawnienia niestandardowe](#using-file-explorer-to-classify-and-protect-files) dla pliku przed jego udostępnieniem. 

Jeśli zostały ustawione uprawnienia niestandardowe, a plik jest już chroniony do użytku wewnętrznego, należy najpierw utworzyć jego kopię. Kopii tej należy użyć do ustawienia uprawnień niestandardowych.  

Gdy plik jest chroniony za pomocą uprawnień niestandardowych, należy użyć standardowego mechanizmu udostępniania dla tego pliku. Jeśli osoby, którym udostępniasz pliki, otrzymają chroniony plik po raz pierwszy, mogą potrzebować instrukcji ich wyświetlenia. Można dla nich skopiować i wkleić następujący komunikat: **Ten plik został przeze mnie objęty ochroną w ramach usługi Microsoft Azure Information Protection. W przypadku użycia po raz pierwszy zobacz te [instrukcje](https://aka.ms/rms-signup).**


## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Korzystanie z aplikacji pakietu Office do klasyfikowania i ochrony dokumentów i wiadomości e-mail

Za pomocą paska usługi Azure Information Protection wybierz jedną z etykiet, które zostały skonfigurowane dla Ciebie. 

Przykładowo na poniższej ilustracji przedstawiono, że dokument nie został jeszcze oznaczony etykietą, ponieważ parametr **Poufność** ma wartość **Nieustawiona**. Aby ustawić etykietę, np. „Wewnętrzna”, kliknij przycisk **Wewnętrzna**. Jeśli nie masz pewności, którą etykietę zastosować do bieżącego dokumentu lub wiadomości e-mail, użyj etykietki narzędzi, aby dowiedzieć się więcej o każdej etykiecie i właściwym jej zastosowaniu.

![Przykład paska usługi Azure Information Protection](../media/info-protect-bar-not-set-callout.png)

Jeśli etykieta jest już zastosowana do dokumentu i chcesz ją zmienić, możesz wybrać inną etykietę. Jeśli na pasku nie są wyświetlane etykiety, kliknij najpierw ikonę **Edytuj etykietę** obok wartości bieżącej etykiety.

Oprócz ręcznego wybierania etykiet można je też ustawiać w następujący sposób:

- Administrator skonfigurował etykietę domyślną, którą można zachować lub zmienić.

- Administrator skonfigurował zalecane monity o wybór określonej etykiety po wykryciu poufnych danych. Możesz zaakceptować zalecenie (i etykieta zostanie dodana) lub je odrzucić (zalecana etykieta nie zostanie dodana).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Wyjątki dotyczące paska usługi Azure Information Protection 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Nie widzisz tego paska usługi Information Protection w aplikacjach pakietu Office?

- Być może nie został [zainstalowany](install-client-app.md) klient usługi Azure Information Protection lub klient jest uruchomiony w [trybie z samą ochroną](client-protection-only-mode.md).
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed-on-the-bar"></a>Czy etykieta, który powinna się pojawić na pasku, nie jest wyświetlana? 

- Jeśli administrator skonfigurował ostatnio nową etykietę, zamknij wszystkie wystąpienia aplikacji pakietu Office i otwórz ją ponownie. Ta akcja sprawdza zmiany etykiet.

- Jeśli brakująca etykieta ustawia ochronę, być może posiadana wersja pakietu Office nie obsługuje ochrony w ramach usługi Rights Management. Aby to sprawdzić, kliknij pozycję **Chroń** > **Pomoc i opinie** i sprawdź, czy w sekcji **Stan klienta** jest widoczny komunikat: **Ten klient nie ma licencji dla pakietu Office Professional Plus.** 

- Etykieta może być objęta zasadami o określonym zakresie, które nie obejmują Twojego konta. Skontaktuj się z administratorem lub pomocą techniczną.

### <a name="keyboard-shortcuts-for-the-azure-information-protection-bar"></a>Skróty klawiaturowe dla paska usługi Azure Information Protection

Aby uzyskać dostęp do paska usługi Azure Information Protection za pomocą skrótów klawiaturowych, użyj następujących kombinacji klawiszy:

- Naciśnij klawisze **Ctrl** + **Shift** + **~** 

Następnie użyj klawisza Tab, aby wybrać etykiety i inne kontrolki na pasku (ikona **Ukryj etykiety** i ikona **Usuń etykietę**), a następnie naciśnij klawisz Enter, aby je wybrać.

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
    
    - **Wybierz użytkowników**: Określ osoby, które powinny mieć wybrane przez Ciebie uprawnienia do pliku lub plików. Do wyszukiwania i wybierania osób i grup w organizacji można użyć książki adresowej. W przypadku osób z innej organizacji należy określić ich pełny adres e-mail. Upewnij się, że używasz służbowego adresu e-mail, ponieważ osobiste adresy e-mail nie są obecnie obsługiwane.
        
    - **Unieważnij dostęp**: Wybierz tę opcję tylko w przypadku plików zależnych od czasu, dzięki czemu określone przez Ciebie osoby nie będą mogły otworzyć wybranego pliku lub plików po określonej przez Ciebie dacie. Nadal będziesz mieć możliwość otwarcia oryginalnego pliku, ale po północy (Twojej bieżącej strefy czasowej) wybranego przez Ciebie dnia określone przez Ciebie osoby nie będą mogły go otworzyć.

5. Kliknij przycisk **Zastosuj** i poczekaj na pojawienie się komunikatu **Ukończona praca**, aby zobaczyć wyniki. Następnie kliknij przycisk **Zamknij**.

Wybrany plik lub pliki są teraz sklasyfikowane i chronione zgodnie z wybranymi przez Ciebie opcjami. W niektórych przypadkach (kiedy dodanie ochrony powoduje zmianę rozszerzenia nazwy pliku) oryginalny plik znajdujący się w Eksploratorze plików zostaje zastąpiony nowym plikiem oznaczonym ikoną kłódki, sygnalizującą ochronę za pomocą usługi Azure Information Protection. Na przykład:

![Chroniony plik z ikoną kłódki usługi Azure Information Protection](../media/Pfile.png)

Jeśli zmienisz zdanie na temat klasyfikacji i ochrony lub zechcesz później zmodyfikować ustawienia, po prostu powtórz proces z nowymi ustawieniami.

Wcześniej określona dla pliku klasyfikacja i ochrona obowiązuje nadal, nawet jeśli plik zostanie wysłany za pomocą poczty e-mail lub zapisany w innej lokalizacji. Jeśli plik jest chroniony, można śledzić, w jaki sposób jest używany, i w razie potrzeby odwołać dostęp do niego. Aby uzyskać więcej informacji, zobacz temat [Śledzenie i odwoływanie dokumentów chronionych podczas korzystania z usługi Azure Information Protection](client-track-revoke.md). 


## <a name="other-instructions"></a>Inne instrukcje
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

-   [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
