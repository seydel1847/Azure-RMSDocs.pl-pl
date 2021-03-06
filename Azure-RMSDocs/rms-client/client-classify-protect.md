---
title: Klasyfikowanie i ochrona plików i wiadomości e-mail przy użyciu usługi Azure Information Protection
description: Instrukcje dotyczące sposobu klasyfikowania i ochrony dokumentów i wiadomości e-mail użytkownika.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: b1d46cb3c98c520ab6900f910f691af920337334
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393467"
---
# <a name="user-guide-classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Podręcznik użytkownika: Klasyfikowanie i ochrona pliku lub wiadomości e-mail za pomocą usługi Azure Information Protection

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), system Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

> [!NOTE]
> Użyj tych instrukcji, aby ułatwić klasyfikować i chronić swoje dokumenty i wiadomości e-mail. Jeśli potrzebujesz tylko do klasyfikowania i nie chronić swoje dokumenty i wiadomości e-mail, zobacz [instrukcje tylko do klasyfikowania](client-classify.md). Jeśli nie masz pewności, który zestaw instrukcje dotyczące korzystania z, skontaktuj się z administratorem lub pomocy technicznej.

Najprostszym sposobem klasyfikować i chronić swoje dokumenty i wiadomości e-mail jest podczas tworzenia lub edycji je w aplikacjach klasycznych pakietu Office: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Można jednak również klasyfikować i chronić pliki za pomocą **Eksploratora plików**. Ta metoda obsługuje dodatkowe typy plików i jest wygodny sposób klasyfikowania i ochrony wielu plików jednocześnie. Ta metoda zapewnia ochronę dokumentów pakietu Office, plików PDF, plików tekstowych i obrazów, a także wielu innych plików. 

Jeśli etykiety usługi dotyczy ochrony dokumentu, chronionego dokumentu nie jest odpowiednia do zapisania w usłudze SharePoint lub OneDrive. Te lokalizacje nie obsługuje wykonywania poniższych chronionych plików: Współtworzenie, Office Online, wyszukiwania, podglądu dokumentu, miniatury i zbierania elektronicznych materiałów dowodowych. 

### <a name="safely-share-a-file-with-people-outside-your-organization"></a>Bezpieczne udostępnianie pliku osobom spoza organizacji

Pliki, które są chronione, są bezpiecznie udostępniane innym użytkownikom. Na przykład Dołącz chroniony dokument do wiadomości e-mail.

Przed udostępnieniem plików osobom spoza organizacji, skontaktuj się z działem pomocy technicznej lub administratorem sposób ochrony plików dla użytkowników zewnętrznych.

Na przykład jeśli Twoja organizacja regularnie komunikuje się z osób w innej organizacji, administrator może skonfigurować etykiety, które ustawiającą ochronę w taki sposób, że te osoby może odczytywać i wykorzystywać dokumenty chronione. Następnie należy wybrać tych etykiet do klasyfikowania i ochrony dokumentów do udostępniania.

Alternatywnie Jeśli masz użytkowników zewnętrznych [konta firmowe (B2B)](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) utworzone dla nich, możesz użyć usługi [aplikacji pakietu Office, aby ustawić uprawnienia niestandardowe](#set-custom-permissions-for-a-document) lub użyj [Eksploratora plików, aby ustawić uprawnienia niestandardowe](#using-file-explorer-to-classify-and-protect-files) dokumentu przed jego udostępnieniem. Jeśli zostały ustawione uprawnienia niestandardowe, a dokument jest już chroniony do użytku wewnętrznego, należy najpierw utworzyć jej kopię do zachowania pierwotnych uprawnień. Kopii tej należy użyć do ustawienia uprawnień niestandardowych.


## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Korzystanie z aplikacji pakietu Office do klasyfikowania i ochrony dokumentów i wiadomości e-mail

Za pomocą paska usługi Azure Information Protection lub **Chroń** przycisk na Wstążce, aby wybrać jedną z etykiet, skonfigurowane dla Ciebie. 

Na przykład na poniższej ilustracji przedstawiono, że dokument nie został jeszcze oznaczony etykietą ponieważ **czułości** pokazuje **Nieustawione** na pasku usługi Azure Information Protection. Aby ustawić etykietę, np. "Ogólne", kliknij pozycję **ogólne**. Jeśli nie masz pewności, którą etykietę zastosować do bieżącego dokumentu lub wiadomości e-mail, użyj etykietki narzędzi, aby dowiedzieć się więcej o każdej etykiecie i właściwym jej zastosowaniu. 

![Przykład paska usługi Azure Information Protection](../media/info-protect-bar-not-set-callout.png)

Jeśli etykieta jest już zastosowana do dokumentu i chcesz ją zmienić, możesz wybrać inną etykietę. Jeśli na pasku nie są wyświetlane etykiety, kliknij najpierw ikonę **Edytuj etykietę** obok wartości bieżącej etykiety.

Oprócz ręcznego wybierania etykiet można je też ustawiać w następujący sposób:

- Administrator skonfigurował etykietę domyślną, którą można zachować lub zmienić.

- Administrator skonfigurował zalecane monity o wybór określonej etykiety po wykryciu poufnych danych. Możesz zaakceptować zalecenie (i etykieta zostanie dodana) lub je odrzucić (zalecana etykieta nie zostanie dodana).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Wyjątki dotyczące paska usługi Azure Information Protection 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Nie widzisz tego paska usługi Information Protection w aplikacjach pakietu Office?

Możliwe przyczyny:

- W przypadku braku klienta usługi Azure Information Protection [zainstalowane](install-client-app.md).

- Jest zainstalowany klient, ale administrator skonfigurował ustawienia, które nie jest wyświetlany pasek. Zamiast tego należy wybrać etykiety z **Chroń** przycisk na **pliku** karty na Wstążce pakietu Office. 

- Klient jest uruchomiony w [tryb z samą ochroną](client-protection-only-mode.md).
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed"></a>Jest etykietę, która powinna się pojawić nie jest wyświetlane? 

Możliwe przyczyny:

- Jeśli administrator skonfigurował ostatnio nową etykietę, zamknij wszystkie wystąpienia aplikacji pakietu Office i otwórz ją ponownie. Ta akcja sprawdza zmiany etykiet.

- Jeśli brakująca etykieta ustawia ochronę, być może posiadana wersja pakietu Office nie obsługuje ochrony w ramach usługi Rights Management. Aby sprawdzić, kliknij przycisk **Chroń** > **Pomoc i opinie**. W oknie dialogowym Sprawdź, czy komunikat **stanu klienta** sekcja, która wynika z **ten klient nie ma licencji pakietu Office Professional Plus.** 
    
    Nie trzeba pakiet Office Professional Plus Jeśli masz aplikacje pakietu Office 2016 z minimalną wersją 1805, kompilacja 9330.2078, a Twoje konto ma przypisanej licencji usługi Azure Rights Management (nazywanego także usługi Azure Information Protection dla usługi Office 365).

- Etykieta może być objęta zasadami o określonym zakresie, które nie obejmują Twojego konta. Skontaktuj się z administratorem lub pomocą techniczną.

### <a name="set-custom-permissions-for-a-document"></a>Ustawienie uprawnień niestandardowych dla dokumentu

Jeśli jest to dozwolone przez administratora, można określić własne ustawienia ochrony dokumentów zamiast korzystać z ustawień, które administrator uwzględnił dla wybranej etykiety. Ta opcja jest właściwe dla dokumentów i nie jest dostępne w programie Outlook.

1. Na karcie **Narzędzia główne**, w grupie **Ochrona**, kliknij kolejno pozycje **Chroń** > **Uprawnienia niestandardowe**:

    ![Opcja Uprawnienia niestandardowe](../media/custom-permissions-callout.png)
    
    Jeśli nie widzisz **uprawnienia niestandardowe**, administrator nie umożliwiają używanie tej opcji.
    
    Należy pamiętać, że wszystkie niestandardowe uprawnienia określone przez użytkownika zastępują, a nie uzupełniają, ustawienia ochrony, które administrator mógł zdefiniować dla wybranej etykiety.  

2. W oknie dialogowym **Microsoft Azure Information Protection** określ następujące elementy:

    - **Ochrona przy użyciu uprawnień niestandardowych**: Upewnij się, że ta opcja jest zaznaczona, aby było określenie i zastosowanie uprawnień niestandardowych. Usuń zaznaczenie tej opcji, aby usunąć wszelkie uprawnienia niestandardowe.
    
    - **Wybierz uprawnienia**: Jeśli chcesz ochrony pliku, tak aby tylko można do niego dostęp, wybierz opcję **tylko dla mnie**. W przeciwnym razie wybierz poziom dostępu dla poszczególnych osób.
    
    - **Wybierz użytkowników, grupy lub organizacje**: Określanie osób, które mają uprawnienia, które zostały wybrane do pliku lub plików. Wpisz dla każdej z osób pełny adres e-mail, adres e-mail grupy lub — dla wszystkich użytkowników należących do organizacji — nazwę domeny. 
        
        Umożliwia także ikonę książki adresowej do wybierz z książki adresowej użytkowników lub grupy.
    
    - **Unieważnij dostęp**: Wybierz tę opcję, tylko w przypadku plików zależnych od czasu, tak aby osoby, który określiłeś, nie będą mogły otworzyć wybranego pliku lub plików po określonej dacie, który został ustawiony. Nadal będziesz mieć możliwość otwarcia oryginalnego pliku, ale po północy (Twojej bieżącej strefy czasowej), na dzień, w którym można ustawić określone przez Ciebie osoby nie będzie można otworzyć pliku.

5. Kliknij przycisk **Zastosuj** i poczekaj na komunikat **Zastosowano uprawnienia niestandardowe**. Następnie kliknij przycisk **Zamknij**.

### <a name="safely-sharing-by-email"></a>Bezpieczne udostępnianie za pośrednictwem poczty e-mail

Po udostępnieniu dokumentów pakietu Office za pośrednictwem poczty e-mail, można dołączyć dokument do wiadomości e-mail możesz chronić i dokument jest chroniony automatycznie z takim samym ograniczeniom, które są stosowane do wiadomości e-mail. 

Jednak zaleca się najpierw ochrony dokumentu, a następnie dołączyć go do wiadomości e-mail. Ochrona wiadomości e-mail również, jeśli wiadomość e-mail zawiera poufne informacje. Dwie zalety ochrony dokumentu, przed dołączeniem do wiadomości e-mail:

- Można śledzić i w razie potrzeby odwoływanie dokumentu po jego wysłanego pocztą.

- Można zastosować różne uprawnienia do dokumentu niż do wiadomości e-mail.

## <a name="using-file-explorer-to-classify-and-protect-files"></a>Klasyfikowanie i ochrona plików za pomocą Eksploratora plików

Korzystając z Eksploratora plików, można szybko klasyfikować i chronić pojedynczy plik, wiele plików lub folder. 

Po wybraniu folderu do wszystkich plików znajdujących się w nim i jego podfolderach zostaną automatycznie przypisane ustawione opcje ochrony. Jednak nowe pliki tworzone w tym folderze lub jego podfolderach nie są konfigurowane automatycznie z użyciem tych opcji.

Jeśli podczas używania Eksploratora plików do klasyfikowania i ustawiania ochrony plików jedna etykieta lub większa ich liczba jest wyszarzona, wybrane pliki nie obsługują klasyfikacji. W przypadku tych plików można wybrać etykietę tylko wtedy, gdy administrator skonfigurował etykietę do stosowania ochrony. Można też określić własne ustawienia ochrony. 

Niektóre pliki są automatycznie wykluczane z klasyfikacji i ochrony, ponieważ ich zmiana mogłaby spowodować zawieszanie się komputera. Pomimo zaznaczenia tych plików, są one pomijane jako wykluczone foldery i pliki. Przykładowo są to pliki wykonywalne i foldery systemu Windows.

W podręczniku administratora podano pełną listę typów plików obsługiwanych oraz pliki i foldery, które są automatycznie wykluczane: [Typy plików obsługiwane przez klienta usługi Azure Information Protection](client-admin-guide-file-types.md).


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>Aby sklasyfikować i chronić plik za pomocą Eksploratora plików

1. W Eksploratorze plików wybierz plik, wiele plików lub folder. Kliknij prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**. Przykład:
    
    ![Kliknięcie prawym przyciskiem myszy w oknie Eksploratora plików — klasyfikowanie i ochrona za pomocą usługi Azure Information Protection](../media/right-click-classify-protect-folder.png)

2. W oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** użyj etykiet w sposób analogiczny jak w aplikacji pakietu Office, który ustawia klasyfikację i ochronę w sposób zdefiniowany przez administratora. 

   - Jeśli nie można wybrać żadnego etykiety (są wyszarzone): Wybrany plik nie obsługuje klasyfikacji, ale można go chronić przy użyciu uprawnień niestandardowych (krok 3). Przykład:

     ![Brak dostępnych etykiet w oknie dialogowym Klasyfikacja i ochrona — Azure Information Protection**](../media/info-protect-dialog-labels-dimmed.png)
    
   - Jeśli nie ma etykiety, ale opcja **wstępnie zdefiniowana przez firmę ochrony** w tym oknie dialogowym: Klient jest uruchomiony w [tryb z samą ochroną](client-protection-only-mode.md). Należy wybrać szablon, aby zastosować ochronę skonfigurowaną przez administratora, lub wybrać opcję **Uprawnienia niestandardowe**, aby określić własne ustawienia ochrony, i przejść do kroku 4.
    
     ![Brak etykiet w oknie dialogowym Klasyfikacja i ochrona — Azure Information Protection**](../media/info-protect-dialog-labels-protection-only.png)
    
3. Jeśli jest to dozwolone przez administratora, można określić własne ustawienia ochrony zamiast korzystać z ustawień, które administrator uwzględnił dla wybranej etykiety. Aby to zrobić, wybierz **Chroń za pomocą uprawnień niestandardowych**.
    
    Jeśli nie widzisz **Chroń za pomocą uprawnień niestandardowych**, administrator nie umożliwiają używanie tej opcji.
    
    Wszystkie niestandardowe uprawnienia określone przez użytkownika zastępują, a nie uzupełniają, ustawienia ochrony, które administrator mógł zdefiniować dla wybranej etykiety.  

4. Po wybraniu opcji ustawień niestandardowych należy określić następujące ustawienia:

   - **Wybierz uprawnienia**: Wybierz poziom dostępu, który ma użytkownikom przy ochronie wybranego pliku lub plików.
    
   - **Wybierz użytkowników, grupy lub organizacje**: Określanie osób, które mają uprawnienia, które zostały wybrane do pliku lub plików. Wpisz dla każdej z osób pełny adres e-mail, adres e-mail grupy lub — dla wszystkich użytkowników należących do organizacji — nazwę domeny. 
    
     Alternatywnie można użyć ikonę książki adresowej do wybierz z książki adresowej użytkowników lub grupy.
        
   - **Unieważnij dostęp**: Wybierz tę opcję tylko dla plików uwarunkowanych czasowo, tak aby określone przez Ciebie osoby nie będą mogły otworzyć wybranego pliku lub plików po określonej dacie, który został ustawiony nadal będą mogli otworzyć oryginalny plik, ale po północy (Twojej bieżącej strefy czasowej) , na dzień, w którym można ustawić, określone przez Ciebie osoby nie będzie można otworzyć pliku.
    
     Pamiętaj, że jeśli to ustawienie zostało wcześniej skonfigurowane przy użyciu uprawnień niestandardowych z aplikacji pakietu Office 2010, w tym oknie dialogowym nie jest wyświetlana podana data wygaśnięcia, chociaż nadal jest ustawiona. Ten problem z wyświetlaniem występuje tylko w przypadku, gdy datę wygaśnięcia skonfigurowano w pakiecie Office 2010.

5. Kliknij przycisk **Zastosuj** i poczekaj na pojawienie się komunikatu **Ukończona praca**, aby zobaczyć wyniki. Następnie kliknij przycisk **Zamknij**.

Wybrany plik lub pliki są teraz sklasyfikowane i chronione zgodnie z wybranymi przez Ciebie opcjami. W niektórych przypadkach (kiedy dodanie ochrony powoduje zmianę rozszerzenia nazwy pliku) oryginalny plik znajdujący się w Eksploratorze plików zostaje zastąpiony nowym plikiem oznaczonym ikoną kłódki, sygnalizującą ochronę za pomocą usługi Azure Information Protection. Przykład:

![Chroniony plik z ikoną kłódki usługi Azure Information Protection](../media/Pfile.png)

Jeśli zmienisz zdanie na temat klasyfikacji i ochrony lub zechcesz później zmodyfikować ustawienia, po prostu powtórz proces z nowymi ustawieniami.

Wcześniej określona dla pliku klasyfikacja i ochrona obowiązuje nadal, nawet jeśli plik zostanie wysłany za pomocą poczty e-mail lub zapisany w innej lokalizacji. Jeśli plik jest chroniony, można śledzić, w jaki sposób jest używany, i w razie potrzeby odwołać dostęp do niego. Aby uzyskać więcej informacji, zobacz temat [Śledzenie i odwoływanie dokumentów chronionych podczas korzystania z usługi Azure Information Protection](client-track-revoke.md). 


## <a name="other-instructions"></a>Inne instrukcje
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

-   [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Dodatkowe informacje dla administratorów    
Aby uzyskać instrukcje dotyczące konfiguracji włączyć ustawienie zasad **Udostępnij opcję niestandardowych uprawnień użytkownikom**, zobacz [konfigurowania ustawień zasad usługi Azure Information Protection](../configure-policy-settings.md).

Inne instrukcje dotyczące konfiguracji: [Konfigurowanie zasad usługi Azure Information Protection](../configure-policy.md).

