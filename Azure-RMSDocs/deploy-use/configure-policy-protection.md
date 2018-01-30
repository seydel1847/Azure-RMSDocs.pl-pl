---
title: "Konfigurowanie etykiety usługi Azure Information Protection w celu zastosowania ochrony"
description: "Najbardziej poufne dokumenty i wiadomości e-mail możesz chronić po skonfigurowaniu etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: d42a561e61991a6299e83c5054ceb2ed8151ebf6
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-configure-a-label-for-rights-management-protection"></a>Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management

>*Dotyczy: Azure Information Protection*

Najbardziej poufne dokumenty i wiadomości e-mail można chronić przy użyciu usługi Rights Management. Ta usługa używa zasad szyfrowania, tożsamości i autoryzacji w celu zapobieżenia utracie danych. Ochrona jest stosowana etykietą, która jest skonfigurowana do używania ochrony usługi Rights Management dla dokumentów i wiadomości e-mail i użytkowników można również wybrać **nie przesyłaj dalej** przycisku w programie Outlook. 

## <a name="how-the-protection-works"></a>Jak działa ochrona

Gdy dokument lub wiadomość e-mail są chronione przez usługę Rights Management, jest on zaszyfrowany podczas przechowywania i podczas przesyłania. Następnie można go odszyfrować tylko przez autoryzowanych użytkowników. Szyfrowanie zostaje utrzymane w dokumencie lub wiadomości e-mail, nawet w przypadku zmiany nazwy dokumentu lub wiadomości. Ponadto możesz skonfigurować prawa i ograniczenia użytkowania, np.:

- Tylko użytkownicy w organizacji mogą otworzyć poufny firmowy dokument lub wiadomość e-mail.

- Tylko użytkownicy w dziale marketingu można edytować i drukować podwyższania poziomu anonsu dokumentu lub wiadomości e-mail, gdy wszyscy inni użytkownicy w organizacji mogą być odczytywane tylko ten dokument lub wiadomość e-mail.

- Użytkownicy nie mogą przesyłać dalej wiadomości e-mail, która zawiera informacje o wewnętrznej reorganizacji, ani kopiować jej zawartości.

- Bieżącego cennika przesyłanego do partnerów biznesowych nie można otworzyć po określonej dacie.

Aby uzyskać więcej informacji na temat ochrony usługi Azure Rights Management i jej działania, zobacz [co to jest usługa Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Aby skonfigurować etykietę w celu zastosowania tej ochrony, usługi Azure Rights Management musi być aktywowany dla Twojej organizacji. Aby uzyskać więcej informacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

Gdy etykieta dotyczy ochrony, chronionego dokumentu nie nadaje się do zapisania w programie SharePoint lub usługi OneDrive. Te lokalizacje nie obsługują następujące funkcje dla plików chronionych: współtworzenia, Office Online wyszukiwania, dokumentu podglądu, miniatur, zbieranie elektronicznych materiałów dowodowych i ochrony przed utratą danych (DLP). 

Program Exchange nie ma umożliwiać zarządzania prawami do informacji (IRM), zanim użytkownicy mogą stosować etykiet w programie Outlook, aby chronić swoje wiadomości e-mail. Jednak aż do programu Exchange jest skonfigurowany dla usługi IRM, nie otrzymasz pełną funkcjonalnością stosowania ochrony usługi Azure Rights Management z programem Exchange. Na przykład użytkownicy nie mogą wyświetlać chronionych wiadomości e-mail w telefonach komórkowych lub w programie Outlook w sieci web chronionych wiadomości e-mail nie można indeksować wyszukiwania i nie można skonfigurować usługi Exchange Online DLP dla ochrony usługi Rights Management. Informacje o konfigurowaniu programu Exchange do obsługi tych dodatkowych scenariuszy można znaleźć w następujących zasobach:

- Exchange Online — zobacz temat [Usługa Exchange Online: konfiguracja usługi IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- W przypadku lokalnej instalacji programu Exchange należy wdrożyć [łącznik usługi RMS i skonfigurować serwery Exchange](../deploy-use/deploy-rms-connector.md). 

## <a name="to-configure-a-label-for-rights-management-protection"></a>Aby skonfigurować etykietę pod kątem ochrony usługi Rights Management

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i zaloguj się do [portalu Azure](https://portal.azure.com) jako zabezpieczeń administratora lub administratora globalnego. Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. Jeśli etykietę, którą chcesz skonfigurować będą stosowane do wszystkich użytkowników, pozostają **usługi Azure Information Protection — globalne zasady** bloku. Jednak jeśli etykietę, którą chcesz skonfigurować jest [zakres zasad](configure-policy-scope.md) tak, aby dotyczył tylko wybrani użytkownicy z **zasady** zaznaczenia menu, wybierz opcję **zakres zasad**. Następnie wybierz zakresie zasad z **zasady usługi Azure Information Protection - zakres** bloku.

3. Wybierz etykietę, którą chcesz skonfigurować, i otwiera **etykiety** bloku. 

4. Na **etykiety** bloku zlokalizować **ustawić uprawnień dla dokumentów i wiadomości e-mail zawierających tę etykietę** i wybierz jedną z następujących opcji:
    
    - **Nieskonfigurowane**: wybierz tę opcję, jeśli etykieta jest obecnie skonfigurowana do stosowania ochrony i już nie chcesz, aby wybrana etykieta korzystała z ochrony. Następnie przejdź do kroku 11.
    
    - **Chroń**: wybierz tę opcję, aby zastosować ochronę, a następnie przejdź do kroku 5.
    
    - **Usuń ochronę**: Wybierz tę opcję, aby usunąć ochronę, jeśli jest chroniony dokument lub wiadomość e-mail. Następnie przejdź do kroku 11.
        
        Należy pamiętać, że dla użytkowników do zastosowania etykiety, która ma tę opcję, ich musi mieć uprawnienia do usuwania ochrony usługi Rights Management. Wymaganie to oznacza, że użytkownicy muszą mieć **wyeksportować** lub **Pełna kontrola** [prawa użytkowania](../deploy-use/configure-usage-rights.md). Lub musi być właścicielem usługi Rights Management (który automatycznie przyzna prawo użytkowania Pełna kontrola) lub być [superużytkowników usługi Azure Rights Management](../deploy-use/configure-super-users.md). Domyślne szablony usługi Azure Rights Management nie zawierają praw użytkowania, które pozwalają użytkownikom usunięcia ochrony. 
        
        Jeśli użytkownicy nie mają uprawnienia do usuwania ochrony usługi Rights Management i wybrania etykiety, który jest skonfigurowany z tym **Usuń ochronę** opcji, zobaczy następujący komunikat: **usługi Azure Information Protection Nie można zastosować tej etykiety. Jeśli problem będzie nadal występować, skontaktuj się z administratorem.**

5. Jeśli została wybrana opcja **Chroń**, wybierz pasek **Ochrona**, aby otworzyć blok **Ochrona**:
    
    ![Konfigurowanie ochrony dla etykiety usługi Azure Information Protection](../media/info-protect-protection-bar-configured.png)

6. Na **ochrony** bloku, wybierz opcję **Azure (klucz w chmurze)** lub **HYOK (AD RMS)**.
    
    W większości przypadków wybierz **Azure (klucz w chmurze)** dla ustawienia uprawnień. Nie należy wybierać usługi **HYOK (AD RMS)**, chyba że użytkownik przeczytał i zrozumiał warunki wstępne i ograniczenia towarzyszące tej konfiguracji rozwiązania „*zachowaj własny klucz*” (HYOK, hold your own key). Aby uzyskać więcej informacji, zobacz [Wymagania i ograniczenia dotyczące rozwiązania „hold your own key” (HYOK) dla ochrony za pomocą usług AD RMS](configure-adrms-restrictions.md). Aby kontynuować konfigurację dla funkcji HYOK (AD RMS), przejdź do kroku 10.
    
7. Wybierz jedną z następujących opcji:
    
    - **Ustaw uprawnienia**: Aby zdefiniować nowe ustawienia ochrony w tym portalu.
    
    - **Uprawnienia (wersja zapoznawcza) zdefiniowane przez użytkownika zestaw**: pozwala określić kto powinien mieć uprawnienia i są te uprawnienia. Można następnie dostosować tę opcję i wybierz tylko w programie Outlook lub Word, Excel, PowerPoint i Eksploratora plików. Ta opcja nie jest obsługiwane i nie działa, jeśli etykiety jest skonfigurowany do [automatycznej klasyfikacji](configure-policy-classification.md).
        
        Jeśli wybierzesz opcję dla programu Outlook: Etykieta jest wyświetlana w programie Outlook i efekty, gdy użytkownicy mają zastosowanie etykiety jest taka sama jak opcja nie przekazuj.
        
        Jeśli wybierzesz opcję dla programu Word, Excel, PowerPoint i Eksploratora plików: gdy ta opcja jest ustawiona, jest wyświetlana etykieta w tych aplikacjach. Efekty, gdy użytkownicy mają zastosowanie etykiety jest wyświetlane okno dialogowe, które użytkownicy mogą wybierać uprawnienia niestandardowe. W tym oknie dialogowym Użytkownicy muszą określić uprawnienia, użytkowników lub grup i daty wygaśnięcia. Upewnij się, że użytkownicy mają instrukcje i wytyczne jak podać te wartości.
    
    - **Wybierz wstępnie zdefiniowany szablon**: aby użyć jednego z szablonów domyślnych lub samodzielnie skonfigurowanego szablonu niestandardowego. Należy pamiętać, że nie są wyświetlane tę opcję, jeśli edytujesz etykiety, który korzystał wcześniej z **ustawić uprawnienia** opcji.
    
    Aby wybrać szablon wstępnie zdefiniowany, szablon musi zostać opublikowany (bez archiwizacji) i nie muszą już połączony z inną etykietę. Po wybraniu tej opcji można użyć **Edytuj szablon** przycisk, aby [przekonwertować szablon na etykietę](configure-policy-templates.md#to-convert-templates-to-labels).
    
    Porada: Jeśli użytkownik są używane do tworzenia i edytowania szablonów niestandardowych, użytkownik może być bardzo przydatne do odwołania [zadań, które są używane z klasycznego portalu Azure](migrate-portal.md).

8. W przypadku wybrania **ustawić uprawnienia** dla **Azure (klucz w chmurze)**, ta opcja umożliwia skonfigurowanie tych samych ustawień, które można skonfigurować w szablonie. 
    
    Wybierz **dodać uprawnienia**i na **dodać uprawnienia** bloku, wybierz pierwszy zbioru użytkowników i grupy, które będą mieć prawa do korzystania z zawartości, które będą chronione za pomocą wybranej etykiety:
    
    - Wybierz **wybierz z listy** dodać wszystkich użytkowników w organizacji lub przeglądanie katalogu.
        
        Użytkownicy lub grupy musi mieć adres e-mail. W środowisku produkcyjnym użytkowników i grup prawie zawsze mieć adres e-mail, ale w prostym środowisku testowym, może być konieczne dodanie adresów e-mail do kont użytkowników lub grup.
        
    - Wybierz **wprowadź szczegóły** ręcznie określić adres e-mail adresy dla poszczególnych użytkowników lub grup (wewnętrznych lub zewnętrznych). Lub użyj tej opcji w celu objęcia wszystkich użytkowników w innej organizacji, wprowadzając nazwę domeny z tej organizacji. Musisz wprowadzić tylko nazwę domeny, nie należy wprowadzać nazwy domen z serwisów społecznościowych, które obsługują osobiste konta e-mail. Na przykład nie należy wprowadzać **gmail.com**, **hotmail.com**, lub **outlook.com**.
        
    >[!NOTE]
    >Jeśli adres e-mail zmieni się po wybraniu użytkownika lub grupy, zobacz [zagadnienia w przypadku zmiany adresów e-mail](../plan-design/prepare.md#considerations-for-azure-information-protection-if-email-addresses-change) sekcji planowania dokumentacji.
    
    Najlepszym rozwiązaniem wykorzystywanie grup zamiast użytkowników. Ta strategia przechowuje konfigurację prostszy i zmniejsza prawdopodobieństwo, że trzeba zaktualizować konfiguracji etykiety później, a następnie zacznij ponownie chronić zawartość. Jednak w przypadku wprowadzania zmian w grupie należy pamiętać, że ze względu na wydajność w usłudze Azure Rights Management [członkostwo w grupie jest buforowane](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection). 
    
    Po określeniu pierwszy zestaw użytkowników i grup, wybierz uprawnienia, aby udzielić tych użytkowników i grup. Aby uzyskać więcej informacji o uprawnieniach, które możesz wybrać, zobacz [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](configure-usage-rights.md). Jednak aplikacje, które obsługują tę ochronę mogą różnić się w zakresie sposobu wdrażania tych uprawnień. Należy zapoznać się z ich dokumentacją i samodzielnie przeprowadzić testy z użyciem aplikacji wykorzystywanych przez użytkowników, aby sprawdzić zachowanie szablonów przed ich wdrożeniem dla użytkowników.
    
    W razie potrzeby można teraz dodać drugi zestaw użytkowników i grup z prawami użytkowania. Powtórz określono wszyscy użytkownicy i grupy z odpowiednimi uprawnieniami.

    >[!TIP]
    >Rozważ dodanie **Kopiuj i Wyodrębnij zawartość** uprawnień niestandardowych oraz uprawnienie to można przyznać administratorom odzyskiwania danych i personelu w innych ról, których obowiązki odzyskiwania informacji. W razie potrzeby Ci użytkownicy mogą następnie usuń ochronę plików i wiadomości e-mail, które będą chronione przy użyciu tej etykiety lub szablonu. Możliwość usunięcia ochrony na poziomie uprawnień do dokumentu lub wiadomości e-mail, zapewnia bardziej szczegółową kontrolę niż [funkcja superużytkowników](configure-super-users.md).
    
    Dla wszystkich użytkowników i grup, które można określić na **ochrony** bloku teraz Sprawdź, czy chcesz wprowadzić zmiany w następujących ustawieniach. Pamiętaj, że te ustawienia, tak jak uprawnienia, nie mają zastosowania do [wystawcy ani właściciela w usłudze Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner), ani żadnego przypisanego przez Ciebie [administratora](configure-super-users.md).
    
    |Ustawienie|Więcej informacji|Zalecane ustawienie
    |-----------|--------------------|--------------------|
    |**wygaśnięcie zawartości**|Zdefiniuj datę lub liczbę dni, gdy dokumentów lub wiadomości e-mail, które są chronione przez te ustawienia nie należy otwierać dla wybranych użytkowników. Można określić datę lub wskazać liczbę dni, jakie muszą minąć, począwszy od momentu objęcia zawartości ochroną.<br /><br />W przypadku określenia daty ustawienie wchodzi w życie o północy czasu mającego zastosowanie w bieżącej strefie czasowej.|**Zawartość nigdy nie wygasa**, jeśli zawartość nie ma określonych wymagań związanych z czasem.|
    |**Zezwalaj na dostęp offline**|Użyj tego ustawienia, aby zrównoważyć wszelkie wymagania dotyczące zabezpieczeń (w tym dostęp po odwołaniu) za pomocą umożliwienia wybranym użytkownikom otwierania chronionej zawartości bez połączenia internetowego.<br /><br />Jeśli można określić, że zawartość nie jest dostępna bez połączenia z Internetem lub zawartość jest dostępna tylko dla określonej liczby dni, po osiągnięciu progu, można ponownie uwierzytelnić tych użytkowników i ich dostęp jest rejestrowany. Kiedy tak się stanie, w przypadku, gdy poświadczenia nie są buforowane, przed otwarciem dokumentu lub wiadomości e-mail tym użytkownikom będzie wyświetlany monit o zalogowanie się.<br /><br />Oprócz ponowne uwierzytelnianie jest ponownie oceniane zasad i członkostwa w grupie użytkowników. Oznacza to, że użytkownicy mogą mieć inny poziom dostępu do tego samego dokumentu lub tej samej wiadomości e-mail po wprowadzeniu zmian w zasadach lub w członkostwie grupy mającym miejsce po ich ostatnim uzyskaniu dostępu do danej zawartości. Może to oznaczać brak dostępu, jeśli dokument został [odwołany](../rms-client/client-track-revoke.md).|W zależności od tego, na ile poufna jest zawartość:<br /><br />- **Liczba dni, w których zawartość jest dostępna bez połączenia z Internetem** = **7** dla poufnych danych biznesowych, których udostępnienie nieupoważnionym osobom mogłoby spowodować szkodę w firmie. To zalecenie oferuje zrównoważony kompromis między elastycznością i zabezpieczeniami. Do przykładów należą kontrakty, raporty dotyczące zabezpieczeń, podsumowania prognoz i dane konta sprzedaży.<br /><br />- **Nigdy** dla bardzo poufnych danych biznesowych, które spowodują szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. To zalecenie stawia zabezpieczenia ponad elastycznością i zapewnia, że w przypadku odwołania dokumentu wszyscy autoryzowani użytkownicy natychmiast utracą możliwość otwierania tego dokumentu. Do przykładów należą dane pracowników i klientów, hasła, kod źródłowy i wstępnie zapowiadane raporty finansowe.|
    
    Po zakończeniu konfigurowania uprawnień, kliknij przycisk **OK**. 
    
    Ta grupa ustawień tworzy niestandardowy szablon dla usługi Azure Rights Management. Te szablony mogą być używane z aplikacjami i usługami, które integrują się z usługą Azure Rights Management. Aby uzyskać informacje dotyczące sposobu pobierania i odświeżania tych szablonów przez komputery i usługi, zobacz [Odświeżanie szablonów dla użytkowników i usług](refresh-templates.md).

9. W przypadku wybrania **wybierz szablon wstępnie zdefiniowany** dla **Azure (klucz w chmurze)**, kliknij pole listy rozwijanej i wybierz [szablonu](../deploy-use/configure-policy-templates.md) chcesz użyć do ochrony dokumentów i wiadomości e-mail przy użyciu tej etykiety. Nie widzieć zarchiwizowane szablony lub szablonów, które zostały już wybrane do innej etykiety.
    
    W przypadku wybrania **szablon dla działu**, lub jeśli skonfigurowano [kontrolki dołączania](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment):
    
    - Użytkownicy, którzy są poza skonfigurowanym zakresie szablonu lub które są wykluczone z zastosowania ochrony usługi Azure Rights Management nadal wyświetlany etykiety, ale nie można go zastosować. Jeśli wybiorą etykietę, zobaczą następujący komunikat: **Usługa Azure Information Protection nie może zastosować tej etykiety. Jeśli problem będzie nadal występować, skontaktuj się z administratorem.**
        
        Należy pamiętać, że wszystkie opublikowane szablony są zawsze wyświetlane, nawet jeśli konfigurujesz zakresie zasad. Na przykład konfigurujesz zasady o określonym zakresie dla grupy Marketing. Szablony, które można wybrać nie są ograniczone do szablonów, które należą do grupy Marketing zakresu i można wybrać szablon dla działu, którego nie można użyć wybranych użytkowników. W celu ułatwienia konfiguracji i zminimalizowania potrzeby rozwiązywania problemów należy wziąć pod uwagę nadanie szablonowi dla działu nazwy zgodnej z etykietą w Twoich zasadach o określonym zakresie. 

10. W przypadku wybrania **HYOK (AD RMS)**, wybierz opcję **zestawu AD RMS szablonów szczegóły** lub **uprawnienia (wersja zapoznawcza) zdefiniowane przez użytkownika zestaw**. Następnie należy określić adres URL licencjonowania klastra usług AD RMS.
    
    Aby uzyskać instrukcje określić szablon identyfikator GUID i adres URL licencjonowania, zobacz [lokalizowanie informacji używanych do określania ochrony usług AD RMS z etykietą usługi Azure Information Protection](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label).
    
    Opcja uprawnienia zdefiniowane przez użytkownika umożliwia użytkownikom określić kto powinien mieć uprawnienia i są te uprawnienia. Można następnie dostosować tę opcję i wybierz tylko w programie Outlook (ustawienie domyślne) lub programu Word, Excel, PowerPoint i Eksploratora plików. Ta opcja nie jest obsługiwane i nie działa, jeśli etykiety jest skonfigurowany do [automatycznej klasyfikacji](configure-policy-classification.md).
    
    Jeśli wybierzesz opcję dla programu Outlook: Etykieta jest wyświetlana w programie Outlook i efekty, gdy użytkownicy mają zastosowanie etykiety jest taka sama jak opcja nie przekazuj.
    
    Jeśli wybierzesz opcję dla programu Word, Excel, PowerPoint i Eksploratora plików: Etykieta jest wyświetlany w tych aplikacjach. Efekty, gdy użytkownicy mają zastosowanie etykiety jest wyświetlane okno dialogowe, które użytkownicy mogą wybierać uprawnienia niestandardowe. W tym oknie dialogowym Użytkownicy muszą określić uprawnienia, użytkowników lub grup i daty wygaśnięcia. Upewnij się, że użytkownicy mają instrukcje i wytyczne jak podać te wartości. Należy pamiętać, że w przypadku braku wersja klienta tej opcji w przypadku Eksploratora plików zawsze używa ochrony usług Azure RMS zamiast ochrony HYOK (AD RMS).

11. Kliknij przycisk **OK** zamknąć **ochrony** bloku i sprawdzić wybór **zdefiniowanych przez użytkownika** lub ekranu wybrany szablon do **ochrony** w przystawce **etykiety** bloku.

12. W bloku **Etykieta** kliknij przycisk **Zapisz**.

13. Na **usługi Azure Information Protection** bloku, użyj **ochrony** kolumny, aby upewnić się, że etykiety są obecnie wyświetlane ustawienia ochrony, który ma:
    
    - Znacznik wyboru, jeśli skonfigurowano ochrony. 
    
    - Znak x do oznaczania anulowania, jeśli skonfigurowano etykiety w celu usunięcia ochrony.
    
    - Pole puste, gdy nie ustawiono ochrony. 

13. Aby udostępnić zmiany użytkownikom, kliknij przycisk **Opublikuj**.

## <a name="example-configurations"></a>Przykładowe konfiguracje

**Wszyscy pracownicy** i **odbiorców tylko** sublabels z **poufne** i **wysokiej poufne** etykiety z [domyślne zasady](configure-policy-default.md) zawierają przykłady sposobu konfigurowania etykiety, które mają zastosowanie ochrony. Umożliwia także następujące przykłady ułatwiające konfigurowanie ochrony dla różnych scenariuszy. 

Dla każdego przykładzie, na Twojej \< *nazwę etykiety*> bloku, wybierz opcję **Chroń** , a następnie wybierz **ochrony** otworzyć  **Ochrona** bloku.

### <a name="example-1-label-that-applies-do-not-forward-to-send-a-protected-email-to-a-gmail-account"></a>Przykład 1: Etykiety, której dotyczy nie przesyłaj dalej do wysyłania chronionych wiadomości e-mail do konta usługi Gmail

Etykieta jest dostępna tylko w programie Outlook i jest odpowiednia w przypadku usługi Exchange Online jest skonfigurowany dla [nowych funkcji szyfrowanie wiadomości usługi Office 365](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Poinstruować użytkowników, aby wybrać tę etykietę, w przypadku konieczności wysłania chronioną wiadomość e-mail do osoby za pomocą konta usługi Gmail (lub inne konta e-mail spoza organizacji). 

Użytkownicy, wpisz adres e-mail usługi Gmail w **do** pola.  Następnie w ich wybierz etykietę, a opcja nie przekazuj jest automatycznie dodawany do wiadomości e-mail. Wynik jest, że adresatów nie może przesłać wiadomości e-mail, wydrukować go, skopiować z niej, lub zapisywanie załączników lub zapisać wiadomość e-mail z inną nazwą. 

1. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Wybierz **uprawnienia (wersja zapoznawcza) zdefiniowane przez użytkownika zestaw**.

3. Upewnij się, że jest zaznaczona Poniższa opcja: **w programie Outlook nie przesyłaj dalej zastosować**.

4. Jeśli zaznaczone, wyczyść następująca opcja: **w, Word, Excel, PowerPoint i Eksploratora plików Monituj użytkownika o uprawnienia niestandardowe**.

5. Kliknij przycisk **OK** na **ochrony** bloku, a następnie opublikuj zmiany.


### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization-and-that-supports-immediate-revocation"></a>Przykład 2: Etykiety, który ogranicza uprawnienia tylko do odczytu do wszystkich użytkowników w innej organizacji i obsługującej natychmiastowe odwoływanie

Ta etykieta jest udostępniona (tylko do odczytu) bardzo poufnych dokumentów, które zawsze wymagają połączenia internetowego, aby go wyświetlić. Jeśli odwołany, użytkownicy nie będą mogli wyświetlić dokument przy następnym próbują otworzyć go.

Etykieta nie jest odpowiedni dla wiadomości e-mail.

1. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Upewnij się, że **ustawić uprawnienia** opcja jest wybrany, a następnie wybierz **dodać uprawnienia**.

3. Na **dodać uprawnienia** bloku, wybierz opcję **wprowadź szczegóły**.

4. Wprowadź nazwę domeny z innej organizacji, na przykład **fabrikam.com**. Następnie wybierz **Dodaj**.

5. Z **wybierz uprawnienia z ustawienie wstępne**, wybierz pozycję **podglądu**, a następnie wybierz **OK**.

6. Ponownie **ochrony** bloku dla **zezwala na dostęp offline Ustawianie**, wybierz pozycję **nigdy**.

7. Kliknij przycisk **OK** na **ochrony** bloku, a następnie opublikuj zmiany.


### <a name="example-3-add-external-users-to-an-existing-label"></a>Przykład 3: Dodawanie użytkowników zewnętrznych do istniejącej etykiety

Nowi użytkownicy, które można dodać będzie w stanie otwarte dokumenty i wiadomości e-mail, które są już chronione przy użyciu tej etykiety. Uprawnienia przyznanie Ci użytkownicy mogą się różnić od uprawnień, które mają istniejących użytkowników.

1. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Upewnij się, że **ustawić uprawnienia** jest wybrany, a następnie wybierz **dodać uprawnienia**.

3. Na **dodać uprawnienia** bloku, wybierz opcję **wprowadź szczegóły**.

4. Wprowadź adres e-mail pierwszy użytkownik (lub grupy) można dodać, a następnie wybierz **Dodaj**.

5. Wybierz uprawnienia dla tego użytkownika (lub grupy).

6. Powtórz kroki 4 i 5 dla każdego użytkownika (lub grupy), który chcesz dodać do tej etykiety. Następnie kliknij przycisk **OK**.

7. Kliknij przycisk **OK** na **ochrony** bloku, a następnie opublikuj zmiany.

### <a name="example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward"></a>Przykład 4: Etykieta chronioną wiadomość e-mail, obsługujący mniej restrykcyjnych uprawnień niż nie przesyłaj dalej

Etykieta nie może być ograniczony do programu Outlook, ale zawiera formanty mniej restrykcyjny niż przy użyciu nie przesyłaj dalej. Możesz na przykład adresatów, aby można było skopiować z wiadomości e-mail lub załącznika lub wydrukować i Zapisz załącznik. Jeśli określisz użytkowników zewnętrznych, którzy nie mają konta w usłudze Azure AD, pamiętaj Poinstruuj użytkowników, nie należy używać tej etykiety dla dokumentów, tylko wiadomości e-mail. Ponadto, aby zapewnić obsługę tych użytkowników zewnętrznych, Exchange Online musi być skonfigurowana dla [nowych funkcji szyfrowanie wiadomości usługi Office 365](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e).  

Gdy użytkownicy określić adresy e-mail w **do** okno, adresy muszą być tego samego użytkowników określonych dla tej konfiguracji etykiety. Ponieważ użytkownicy mogą należeć do grupy i mieć więcej niż jeden adres e-mail, adresu e-mail, dlatego nie ma zgodny z adresem e-mail określ uprawnienia. Jednak określenie taki sam adres e-mail jest najprostszym sposobem, aby upewnić się, że odbiorcy będą pomyślnie uprawnienia. Aby uzyskać więcej informacji na temat jak użytkownicy są uprawnieni do uprawnień, zobacz [przygotowywanie użytkowników i grup usługi Azure Information Protection](../plan-design/prepare.md). 

1. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Upewnij się, że **ustawić uprawnienia** jest zaznaczone i wybierz **dodać uprawnienia**.

3. Na **dodać uprawnienia** bloku: Aby udzielić uprawnień dla użytkowników w organizacji, wybierz **Dodaj \<nazwa organizacji > — wszystkie elementy członkowskie** wybierz wszystkich użytkowników w dzierżawie, lub wybierz  **Przeglądanie katalogu** wybrać określoną grupę. Aby udzielić uprawnień dla użytkowników zewnętrznych lub jeśli wolisz wpisz adres e-mail, wybierz **wprowadź szczegóły** i wpisz adres e-mail użytkownika lub grupy usługi Azure AD.
    
    Powtórz ten krok w celu określenia dodatkowych użytkowników, którzy powinni mieć te same uprawnienia.

4. Dla **wybierz uprawnienia z ustawienie wstępne**, wybierz pozycję **współwłaściciel**, **Współautor**, **Weryfikacja**, lub **niestandardowy**wybierz uprawnienia, które chcesz udzielić. 
    
    Uwaga: Nie należy wybierać **podglądu** dla wiadomości e-mail i wybranie **niestandardowy**, upewnij się, że obejmuje **Edytuj i zapisuj**. 

5. Aby określić dodatkowych użytkowników, którzy powinni mieć inne uprawnienia, powtórz kroki 3 i 4.

6. Kliknij przycisk **OK** na **dodać uprawnienia** bloku. 

7. Kliknij przycisk **OK** na **ochrony** bloku, a następnie opublikuj zmiany.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]