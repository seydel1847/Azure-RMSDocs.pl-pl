---
title: Konfigurowanie etykiety usługi Azure Information Protection w celu zastosowania ochrony
description: Najbardziej poufne dokumenty i wiadomości e-mail możesz chronić po skonfigurowaniu etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/26/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: 0cac50caf3a7ecf9189d7731f1248e543871be9a
ms.sourcegitcommit: 3f524c5af39bee39169f86d9c4e72c661c960d83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37068945"
---
# <a name="how-to-configure-a-label-for-rights-management-protection"></a>Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Można chronić swoje najbardziej poufne dokumenty i wiadomości e-mail przy użyciu usługi Rights Management. Ta usługa używa zasad szyfrowania, tożsamości i autoryzacji, aby pomóc w uniknięciu utraty danych. Ochrona jest stosowana z etykietą, który jest skonfigurowany do korzystania z ochrony usługi Rights Management dla dokumentów i wiadomości e-mail i użytkownicy mogą również wybrać **nie przesyłaj dalej** przycisku w programie Outlook.

Gdy etykiety usługi jest skonfigurowany z ustawieniem ochrony **Azure (klucz w chmurze)**, dzieje się w tle, ta akcja tworzy i konfiguruje szablonu ochrony, które następnie są dostępne dla usługi i aplikacje, które integrują się z Szablonów usługi Rights Management. Na przykład Exchange Online i reguły przepływu poczty i programu Outlook w sieci web. 

## <a name="how-the-protection-works"></a>Jak działa ochrona

Gdy dokument lub wiadomość e-mail są chronione przez usługę Rights Management, są szyfrowane, podczas przechowywania i podczas przesyłania. Go następnie odszyfrować je mogą tylko autoryzowani użytkownicy. Szyfrowanie zostaje utrzymane w dokumencie lub wiadomości e-mail, nawet w przypadku zmiany nazwy dokumentu lub wiadomości. Ponadto możesz skonfigurować prawa i ograniczenia użytkowania, np.:

- Tylko użytkownicy w organizacji mogą otworzyć poufny firmowy dokument lub wiadomość e-mail.

- Tylko użytkownicy w dziale marketingu można edytować i drukować podwyższania poziomu ogłoszenie dokumentu lub wiadomości e-mail, gdy wszyscy inni użytkownicy w organizacji mogą być odczytane tylko ten dokument lub wiadomość e-mail.

- Użytkownicy nie mogą przesyłać dalej wiadomości e-mail, która zawiera informacje o wewnętrznej reorganizacji, ani kopiować jej zawartości.

- Bieżącego cennika przesyłanego do partnerów biznesowych nie można otworzyć po określonej dacie.

Aby uzyskać więcej informacji na temat ochrony usługi Azure Rights Management i jak to działa, zobacz [co to jest Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Aby skonfigurować etykietę w celu zastosowania tej ochrony, usługa Azure Rights Management musi być aktywowana w organizacji. Aby uzyskać więcej informacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

Gdy stosuje się etykietę ochrony, chronionego dokumentu nie jest odpowiednia do zapisania w usłudze SharePoint lub OneDrive. Te lokalizacje są obsługiwane następujące funkcje dla plików chronionych: Współtworzenie, Office Online, wyszukiwania, podglądu dokumentu, miniatury, zbierania elektronicznych materiałów dowodowych i ochrony przed utratą danych (DLP). 

Program Exchange nie ma skonfigurowany dla usługi Azure Information Protection, zanim użytkownicy mogą stosować etykiety w programie Outlook, aby chronić swoje wiadomości e-mail. Jednak dopóki program Exchange jest skonfigurowany dla usługi Azure Information Protection, nie można pobrać pełnej funkcjonalności podczas korzystania z ochrony usługi Azure Rights Management z programem Exchange. Na przykład użytkownicy nie mogą wyświetlać chronionych wiadomości e-mail na telefonach komórkowych lub z programem Outlook w sieci web i chronionych wiadomości e-mail nie będą też indeksowane do wyszukiwania, a nie można skonfigurować programu Exchange Online DLP dla ochrony usługi Rights Management. Aby upewnić się, że program Exchange może obsługiwać tych dodatkowych scenariuszy, zobacz następujące zasoby:

- Exchange Online — zobacz temat [Usługa Exchange Online: konfiguracja usługi IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- W przypadku lokalnej instalacji programu Exchange należy wdrożyć [łącznik usługi RMS i skonfigurować serwery Exchange](../deploy-use/deploy-rms-connector.md). 

## <a name="to-configure-a-label-for-protection-settings"></a>Aby skonfigurować etykiety w celu ustawienia ochrony

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **etykiety** opcji menu: na **usługi Azure Information Protection — etykiety** bloku, wybierz etykietę, o których chcesz zmienić. 

3. Na **etykiety** bloku Znajdź **ustawić uprawnienia dla dokumentów i wiadomości e-mail zawierających tę etykietę**i wybierz jedną z następujących opcji:
    
    - **Nieskonfigurowane**: wybierz tę opcję, jeśli etykieta jest obecnie skonfigurowana do stosowania ochrony i już nie chcesz, aby wybrana etykieta korzystała z ochrony. Następnie przejdź do kroku 11.
        
        Ochronę wcześniej skonfigurowane ustawienia są przechowywane jako szablon ochrony zarchiwizowane i pojawi się ponownie po zmianie opcji z powrotem do **Chroń**. Nie widzisz tego szablonu w witrynie Azure portal, ale jeśli to konieczne, szablon nadal można zarządzać za pomocą [PowerShell](configure-templates-with-powershell.md). Oznacza to zachowanie, że zawartość pozostaje dostępna, jeśli ma on tej etykiety za pomocą ustawień ochrony zastosowane wcześniej.
    
    - **Ochrona**: Wybierz tę opcję, aby zastosować ochronę, a następnie przejdź do kroku 5, aby skonfigurować ustawienia ochrony.
    
    Uwaga: Można zapisać nową etykietę na tym etapie bez dalszej konfiguracji. Jeśli to zrobisz, etykieta jest skonfigurowany do stosowania ochrony w taki sposób, że tylko osoby, która stosuje etykietę można otworzyć dokumentu lub wiadomości e-mail bez żadnych ograniczeń użycia. W niektórych przypadkach może to być wymagany wynik, tak aby użytkownik może zapisać plik w dowolnej lokalizacji i mieć pewność, że tylko mogą go otworzyć. Jeśli ten wynik jest zgodna z wymaganiami, a inne nie są wymagane do współpracy nad chronioną zawartością, przejdź bezpośrednio do kroku 12, zamiast kroku 5.
    
    - **Usuń ochronę**: Wybierz tę opcję, aby usunąć ochronę, jeśli dokument lub wiadomość e-mail jest chroniona. Następnie przejdź do kroku 11.
        
        Ochronę wcześniej skonfigurowane ustawienia są przechowywane jako szablon ochrony zarchiwizowane i pojawi się ponownie po zmianie opcji z powrotem do **Chroń**. Nie widzisz tego szablonu w witrynie Azure portal, ale jeśli to konieczne, szablon nadal można zarządzać za pomocą [PowerShell](configure-templates-with-powershell.md). Oznacza to zachowanie, że zawartość pozostaje dostępna, jeśli ma on tej etykiety za pomocą ustawień ochrony zastosowane wcześniej.
        
        Należy pamiętać, że dla użytkowników zastosować etykietę, która ma tę opcję, ich musi mieć uprawnienia do usuwania ochrony usługi Rights Management. Wymaganie to oznacza, że użytkownicy muszą mieć **wyeksportować** lub **Pełna kontrola** [prawa użytkowania](../deploy-use/configure-usage-rights.md). Lub, musisz być właścicielem usługi Rights Management (co automatycznie udziela prawa użytkowania Pełna kontrola) lub być [superużytkowników usługi Azure Rights Management](../deploy-use/configure-super-users.md). Domyślne szablony usługi Azure Rights Management nie obejmują praw użytkowania, które pozwalają użytkownikom na usuwanie ochrony. 
        
        Jeśli użytkownicy nie mają uprawnień do usuwania ochrony usługi Rights Management i wybrania etykiety, który jest skonfigurowany z tym **Usuń ochronę** opcji, zobaczą następujący komunikat: **usługi Azure Information Protection Nie można zastosować tej etykiety. Jeśli problem będzie nadal występować, skontaktuj się z administratorem.**

4. Jeśli została wybrana opcja **Chroń**, wybierz pasek **Ochrona**, aby otworzyć blok **Ochrona**:
    
    ![Konfigurowanie ochrony dla etykiety usługi Azure Information Protection](../media/info-protect-protection-bar-configured.png)

5. Na **ochrony** bloku wybierz **Azure (klucz w chmurze)** lub **HYOK (AD RMS)**.
    
    W większości przypadków zaznacz **Azure (klucz w chmurze)** dla swoich ustawień uprawnień. Nie należy wybierać usługi **HYOK (AD RMS)**, chyba że użytkownik przeczytał i zrozumiał warunki wstępne i ograniczenia towarzyszące tej konfiguracji rozwiązania „*zachowaj własny klucz*” (HYOK, hold your own key). Aby uzyskać więcej informacji, zobacz [Wymagania i ograniczenia dotyczące rozwiązania „hold your own key” (HYOK) dla ochrony za pomocą usług AD RMS](configure-adrms-restrictions.md). Aby kontynuować konfigurację dla usługi HYOK (AD RMS), przejdź do kroku 9.
    
6. Wybierz jedną z następujących opcji:
    
    - **Ustaw uprawnienia**: Aby zdefiniować nowe ustawienia ochrony w tym portalu.
    
    - **Ustaw uprawnienia zdefiniowane przez użytkownika (wersja zapoznawcza)**: Aby umożliwić użytkownikom określanie, kto powinien mieć przyznane uprawnienia i uprawnienia te są. Można dostosować tę opcję i wybierz opcję tylko w programie Outlook lub Word, Excel, PowerPoint i Eksploratora plików. Ta opcja nie jest obsługiwane i nie działa, jeśli etykieta jest skonfigurowany do [automatycznej klasyfikacji](configure-policy-classification.md).
        
        Jeśli wybierzesz opcję programu Outlook: Etykieta jest wyświetlana w programie Outlook i wynikowe zachowania, gdy użytkownicy mają zastosowanie etykiety jest taki sam jak opcję nie przesyłaj dalej.
        
        Jeśli wybierzesz opcję dla programu Word, Excel, PowerPoint i Eksploratora plików: gdy ta opcja jest ustawiona, etykieta jest wyświetlana w tych aplikacjach. Wynikowe zachowania, gdy użytkownicy mają zastosowanie etykiety jest wyświetlane okno dialogowe użytkownikom na wybór uprawnienia niestandardowe. W tym oknie dialogowym Użytkownicy muszą określić uprawnienia, użytkowników lub grup i daty wygaśnięcia. Upewnij się, że użytkownicy mają wskazówki i instrukcje jak przekazać te wartości.
    
    - **Wybierz wstępnie zdefiniowany szablon**: aby użyć jednego z szablonów domyślnych lub samodzielnie skonfigurowanego szablonu niestandardowego. Należy zauważyć, że nie są wyświetlane tę opcję, jeśli edytujesz etykiety, który korzystał wcześniej z **Ustaw uprawnienia** opcji.
    
    Aby wybrać wstępnie zdefiniowany szablon, szablon musi zostać opublikowany (nie zarchiwizowanych) i nie muszą już połączona z inną etykietę. Po wybraniu tej opcji, możesz użyć **Edytuj szablon** przycisk, aby [konwersji szablonu na etykietę](configure-policy-templates.md#to-convert-templates-to-labels).
    
    Porada: Możesz są używane do tworzenia i edytowania szablonów niestandardowych, użytkownik może być bardzo przydatne do odwołania [zadania, które były wykonywane przy użyciu klasycznego portalu Azure](migrate-portal.md).

    - **Wybierz wstępnie zdefiniowany szablon**: aby użyć jednego z szablonów domyślnych lub samodzielnie skonfigurowanego szablonu niestandardowego. Należy zauważyć, że nie są wyświetlane tę opcję, jeśli edytujesz etykiety, który korzystał wcześniej z **Ustaw uprawnienia** opcji.
    
    Aby wybrać wstępnie zdefiniowany szablon, szablon musi zostać opublikowany (nie zarchiwizowanych) i nie muszą już połączona z inną etykietę. Po wybraniu tej opcji, możesz użyć **Edytuj szablon** przycisk, aby [konwersji szablonu na etykietę](configure-policy-templates.md#to-convert-templates-to-labels).
    
    Porada: Możesz są używane do tworzenia i edytowania szablonów niestandardowych, użytkownik może być bardzo przydatne do odwołania [zadania, które były wykonywane przy użyciu klasycznego portalu Azure](migrate-portal.md).

7. W przypadku wybrania **Ustaw uprawnienia** dla **Azure (klucz w chmurze)**, ta opcja umożliwia skonfigurowanie tych samych ustawień, które można skonfigurować w szablonie. 
    
    Wybierz **Dodaj uprawnienia**, a następnie na **Dodaj uprawnienia** bloku, wybierz pierwszy zestaw użytkowników i grupy, którzy będą mieć prawa do korzystania z zawartości, które będą chronione za pomocą wybranej etykiety:
    
    - Wybierz **wybierz z listy** której następnie można dodać wszystkich użytkowników z Twojej organizacji, wybierając **Dodaj \<nazwa organizacji > — wszystkie elementy członkowskie**. To ustawienie wyłącza konta gościa. Lub możesz wybrać **Dodaj wszystkich uwierzytelnionych użytkowników (wersja zapoznawcza)**, lub Przeglądaj katalog.
        
        Wybierz wszystkie elementy Członkowskie lub Przeglądaj katalog, użytkowników lub grupy, musi mieć adres e-mail. W środowisku produkcyjnym użytkowników i grup prawie zawsze mieć adres e-mail, ale w prostym środowisku testowym, może być konieczne dodanie adresów e-mail do kont użytkowników lub grup.
        
        ###### <a name="more-information-about-add-any-authenticated-users"></a>Więcej informacji na temat **Dodaj wszystkich uwierzytelnionych użytkowników** 
        To ustawienie nie ogranicza kto ma dostęp do zawartości, czy etykieta chroni szyfrowanie treści i opcji, można ograniczyć, jak zawartości mogą być używane (uprawnienia), zapewniając i dostępne (wygaśnięcia i dostęp w trybie offline). Jednak aplikacja otwierania chronionej zawartości musi umożliwiać do obsługi uwierzytelniania. Z tego powodu federacyjnego dostawców sieci społecznościowych, takich jak Google i jednorazowej kod dostępu uwierzytelniania należy używać tylko dla wiadomości e-mail i tylko wtedy, gdy używasz usługi Exchange Online i nowe funkcje z szyfrowanie wiadomości usługi Office 365. Konta Microsoft można przy użyciu podglądu usługi Azure Information Protection i pakietu Office 2016 kliknij do uruchomienia. 
        
        Niektóre typowe scenariusze dotyczące wszystkie uwierzytelnieni użytkownicy ustawienie: — Możesz nie mieć nic przeciwko, kto może wyświetlać zawartość, ale chcesz ograniczyć, sposobie ich użycia. Na przykład nie ma zawartość, aby edytować, skopiować lub drukowane.
            — Nie trzeba ograniczyć, kto uzyskuje dostęp do zawartości, ale chcesz mieć możliwość śledzenia, który zostanie otwarty i ewentualnie odwołać.
            — Masz wymaganie, że zawartość, muszą być szyfrowane podczas przechowywania i podczas przesyłania, ale nie wymaga kontroli dostępu.     
        
    - Wybierz **wprowadź szczegóły** ręcznie określić adres e-mail, adresy dla poszczególnych użytkowników lub grup (wewnętrznych lub zewnętrznych). Możesz też użyć tej opcji w celu objęcia wszystkich użytkowników w innej organizacji, wprowadzając dowolną nazwę domeny z tej organizacji. Dla dostawców sieci społecznościowych, można także użyć tej opcji, wprowadzając odpowiednią nazwę domeny, takich jak **gmail.com**, **hotmail.com**, lub **outlook.com**.
        
    >[!NOTE]
    >Jeśli adres e-mail ulegnie zmianie po wybraniu użytkownika lub grupy, zobacz [zagadnienia w przypadku zmiany adresów e-mail](../plan-design/prepare.md#considerations-for-azure-information-protection-if-email-addresses-change) sekcji dokumentacji planowania.
    
    Najlepszym rozwiązaniem jest użycie grupy zamiast użytkowników. Ta strategia zapewnia prostszy konfigurację i zmniejsza prawdopodobieństwo, że trzeba zaktualizować konfigurację etykiety w dalszej części i następnie ponownie włącz ochronę zawartości. Jednak w przypadku wprowadzania zmian w grupie należy pamiętać, że ze względu na wydajność w usłudze Azure Rights Management [członkostwo w grupie jest buforowane](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection). 
    
    Po określeniu pierwszy zestaw użytkowników i grup, wybierz uprawnienia, aby udzielić tych użytkowników i grup. Aby uzyskać więcej informacji o uprawnieniach, które możesz wybrać, zobacz [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](configure-usage-rights.md). Jednak aplikacje, które obsługują tę ochronę mogą się różnić się sposobami wdrażania tych uprawnień. Należy zapoznać się z ich dokumentacją i samodzielnie przeprowadzić testy z użyciem aplikacji wykorzystywanych przez użytkowników, aby sprawdzić zachowanie szablonów przed ich wdrożeniem dla użytkowników.
    
    W razie potrzeby możesz teraz dodać drugi zestaw użytkowników i grup z prawami użytkowania. Powtórz określono wszyscy użytkownicy i grupy wraz z ich odpowiednimi uprawnieniami.

    >[!TIP]
    >Rozważ dodanie **Zapisz jako, Eksportuj (EXPORT)** niestandardowe uprawnienie oraz uprawnienie to można przyznać administratorom odzyskiwania danych i pracowników w inne role mają obowiązki odzyskiwania informacji. Jeśli to konieczne, tacy użytkownicy mogą następnie wyłączyć ochronę plików i wiadomości e-mail chronionych przy użyciu tej etykiety lub szablonu. Możliwość usunięcia ochrony na poziomie uprawnień dla dokumentu lub wiadomości e-mail zapewnia bardziej szczegółową kontrolę niż [funkcji superużytkowników](configure-super-users.md).
    
    Dla wszystkich użytkowników i grup, które można określić na **ochrony** bloku teraz sprawdzić, czy chcesz wprowadzić zmiany w następujących ustawieniach. Pamiętaj, że te ustawienia, tak jak uprawnienia, nie mają zastosowania do [wystawcy ani właściciela w usłudze Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner), ani żadnego przypisanego przez Ciebie [administratora](configure-super-users.md).
    
    ###### <a name="information-about-the-protection-settings"></a>Informacje dotyczące ustawień ochrony
    
    |Ustawienie|Więcej informacji|Zalecane ustawienie
    |-----------|--------------------|--------------------|
    |**wygaśnięcie zawartości**|Zdefiniuj datę lub liczbę dni w przypadku, gdy dokumenty lub wiadomości e-mail, które są chronione przez te ustawienia nie należy otwierać dla wybranych użytkowników. Można określić datę lub wskazać liczbę dni, jakie muszą minąć, począwszy od momentu objęcia zawartości ochroną.<br /><br />W przypadku określenia daty ustawienie wchodzi w życie o północy czasu mającego zastosowanie w bieżącej strefie czasowej.|**Zawartość nigdy nie wygasa**, jeśli zawartość nie ma określonych wymagań związanych z czasem.|
    |**Zezwalaj na dostęp offline**|Użyj tego ustawienia, aby zrównoważyć wszelkie wymagania dotyczące zabezpieczeń (w tym dostęp po odwołaniu) za pomocą umożliwienia wybranym użytkownikom otwierania chronionej zawartości bez połączenia internetowego.<br /><br />Jeśli określisz, że zawartość nie jest dostępna bez połączenia z Internetem lub że zawartość jest dostępna tylko dla określonej liczby dni, po osiągnięciu progu Ci użytkownicy muszą być ponownie uwierzytelniany, a ich dostęp jest zalogowany. Kiedy tak się stanie, w przypadku, gdy poświadczenia nie są buforowane, przed otwarciem dokumentu lub wiadomości e-mail tym użytkownikom będzie wyświetlany monit o zalogowanie się.<br /><br />Oprócz ponowne uwierzytelnianie jest ponownie oceniane zasad i członkostwa w grupie użytkowników. Oznacza to, że użytkownicy mogą mieć inny poziom dostępu do tego samego dokumentu lub tej samej wiadomości e-mail po wprowadzeniu zmian w zasadach lub w członkostwie grupy mającym miejsce po ich ostatnim uzyskaniu dostępu do danej zawartości. Może to oznaczać brak dostępu, jeśli dokument został [odwołany](../rms-client/client-track-revoke.md).|W zależności od tego, na ile poufna jest zawartość:<br /><br />- **Liczba dni, w których zawartość jest dostępna bez połączenia z Internetem** = **7** dla poufnych danych biznesowych, których udostępnienie nieupoważnionym osobom mogłoby spowodować szkodę w firmie. To zalecenie oferuje zrównoważony kompromis między elastycznością i zabezpieczeniami. Do przykładów należą kontrakty, raporty dotyczące zabezpieczeń, podsumowania prognoz i dane konta sprzedaży.<br /><br />- **Nigdy** dla bardzo poufnych danych biznesowych, które spowodują szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. To zalecenie stawia zabezpieczenia ponad elastycznością i zapewnia, że w przypadku odwołania dokumentu wszyscy autoryzowani użytkownicy natychmiast utracą możliwość otwierania tego dokumentu. Do przykładów należą dane pracowników i klientów, hasła, kod źródłowy i wstępnie zapowiadane raporty finansowe.|
    
    Po zakończeniu konfigurowania uprawnień i ustawień, kliknij przycisk **OK**. 
    
    Ta grupa ustawień tworzy niestandardowy szablon dla usługi Azure Rights Management. Te szablony mogą być używane z aplikacjami i usługami, które integrują się z usługą Azure Rights Management. Aby uzyskać informacje dotyczące sposobu pobierania i odświeżania tych szablonów przez komputery i usługi, zobacz [Odświeżanie szablonów dla użytkowników i usług](refresh-templates.md).

8. W przypadku wybrania **wybierz wstępnie zdefiniowany szablon** dla **Azure (klucz w chmurze)**, kliknij pole listy rozwijanej i wybierz [szablonu](../deploy-use/configure-policy-templates.md) chcesz użyć do ochrony dokumentów i wiadomości e-mail przy użyciu tej etykiety. Nie widzisz zarchiwizowane szablony lub szablonów, które zostały już wybrane do innej etykiety.
    
    Jeśli wybierzesz **szablonu dla działu**, lub jeśli skonfigurowano [kontrolek dołączania](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment):
    
    - Użytkownicy, którzy są poza skonfigurowanym zasięgiem szablonu lub są wyłączeni ze stosowania ochrony usługi Azure Rights Management nadal widzieć etykietę, ale nie można zastosować. Jeśli wybiorą etykietę, zobaczą następujący komunikat: **Usługa Azure Information Protection nie może zastosować tej etykiety. Jeśli problem będzie nadal występować, skontaktuj się z administratorem.**
        
        Należy pamiętać, że wszystkie opublikowane szablony są zawsze wyświetlane, nawet wtedy, gdy konfigurujesz zasady o określonym zakresie. Na przykład konfigurujesz zasady o określonym zakresie dla grupy Marketing. Szablony, które można wybierać nie są ograniczone do szablonów, które są ograniczone do grupy Marketing i można wybrać szablon dla działu, nie można użyć wybranych użytkowników. W celu ułatwienia konfiguracji i zminimalizowania potrzeby rozwiązywania problemów należy wziąć pod uwagę nadanie szablonowi dla działu nazwy zgodnej z etykietą w Twoich zasadach o określonym zakresie. 

9. W przypadku wybrania **HYOK (AD RMS)**, wybierz opcję **szczegóły szablonów usług AD RMS zestaw** lub **uprawnienia (wersja zapoznawcza) zdefiniowane przez użytkownika zestaw**. Następnie określ adres URL licencjonowania klastra usług AD RMS.
    
    Aby uzyskać instrukcje określić szablon identyfikator GUID i adres URL licencjonowania, zobacz [lokalizowania informacji do określania ochrony usług AD RMS za pomocą etykiety usługi Azure Information Protection](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label).
    
    Opcja uprawnienia zdefiniowane przez użytkownika pozwala użytkownikowi na określenie, którzy powinny mieć przyznane uprawnienia i uprawnienia te są. Można dostosować tę opcję i wybierz opcję tylko w programie Outlook (ustawienie domyślne) lub programu Word, Excel, PowerPoint i Eksploratora plików. Ta opcja nie jest obsługiwane i nie działa, jeśli etykieta jest skonfigurowany do [automatycznej klasyfikacji](configure-policy-classification.md).
    
    Jeśli wybierzesz opcję programu Outlook: Etykieta jest wyświetlana w programie Outlook i wynikowe zachowania, gdy użytkownicy mają zastosowanie etykiety jest taki sam jak opcję nie przesyłaj dalej.
    
    Jeśli wybierzesz opcję dla programu Word, Excel, PowerPoint i Eksploratora plików: Etykieta jest wyświetlana w tych aplikacjach. Wynikowe zachowania, gdy użytkownicy mają zastosowanie etykiety jest wyświetlane okno dialogowe użytkownikom na wybór uprawnienia niestandardowe. W tym oknie dialogowym Użytkownicy muszą określić uprawnienia, użytkowników lub grup i daty wygaśnięcia. Upewnij się, że użytkownicy mają wskazówki i instrukcje jak przekazać te wartości.

10. Kliknij przycisk **OK** zamknąć **ochrony** bloku i zobacz swój wybór w opcji **zdefiniowane przez użytkownika** lub obraz wyświetlonego wybranego szablonu dla **ochrony** opcji **etykiety** bloku.

11. W bloku **Etykieta** kliknij przycisk **Zapisz**.

12. Na **usługi Azure Information Protection** bloku **ochrony** kolumny, aby upewnić się, że etykiety są obecnie wyświetlane ustawienia ochrony, który ma:
    
    - Znacznik wyboru, jeśli została skonfigurowana ochrona. 
    
    - Znak x do oznaczania anulowania, po skonfigurowaniu etykiety w celu usunięcia ochrony.
    
    - Puste pola, gdy ochrona nie jest ustawiona. 

Po kliknięciu **Zapisz**, zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma już opcji publikowania oddzielne.


## <a name="example-configurations"></a>Przykładowe konfiguracje

**Wszyscy pracownicy** i **tylko adresaci** sublabels z **poufne** i **wysokiej poufne** etykiety z [domyślne zasady](configure-policy-default.md) zawierają przykłady sposobu konfigurowania etykiet stosujących ochronę. Umożliwia także poniższe przykłady ułatwiają konfigurowanie ochrony dla różnych scenariuszy. 

Dla każdego przykładu, który następuje na Twoje \< *nazwę etykiety*> bloku wybierz **Chroń** , a następnie wybierz **ochrony** otworzyć  **Ochrona** bloku.

### <a name="example-1-label-that-applies-do-not-forward-to-send-a-protected-email-to-a-gmail-account"></a>Przykład 1: Etykieta ma zastosowanie nie przesyłaj dalej do wysyłania chronionych wiadomości e-mail na konto Gmail

Ta etykieta jest dostępna tylko w programie Outlook i jest odpowiednie w przypadku usługi Exchange Online skonfigurowano na potrzeby [nowe funkcje w szyfrowanie wiadomości usługi Office 365](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Poinstruować użytkowników, aby wybrać tę etykietę, kiedy ich potrzebują wysłać chronioną wiadomość e-mail do osób, przy użyciu konta Gmail (lub innego konta e-mail spoza Twojej organizacji). 

Użytkownicy, wpisz adres e-mail usługi Gmail w **do** pola.  Następnie wybiorą etykietę i opcję nie przekazuj jest automatycznie dodawany do wiadomości e-mail. Wynik jest, że adresatów nie może przesyłać dalej wiadomości e-mail, drukować, kopiować, lub Zapisz załączniki lub zapisać wiadomość e-mail z inną nazwą. 

1. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Wybierz **Ustaw uprawnienia zdefiniowane przez użytkownika (wersja zapoznawcza)**.

3. Upewnij się, że wybrano następujące opcje: **w programie Outlook Zastosuj nie przesyłaj dalej**.

4. Jeśli zaznaczone, wyczyść będzie następująca opcja: **w programie Word, Excel, PowerPoint i Eksploratora plików Monituj użytkownika o uprawnienia niestandardowe**.

5. Kliknij przycisk **OK** na **ochrony** bloku, a następnie kliknij **Zapisz** na **etykiety** bloku.


### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization-and-that-supports-immediate-revocation"></a>Przykład 2: Etykieta, która ogranicza uprawnienia tylko do odczytu dla wszystkich użytkowników w innej organizacji i bezpośredniego odwołania, która obsługuje

Ta etykieta jest udostępniona (tylko do odczytu) bardzo poufnych dokumentów, które zawsze wymagają dostępu do Internetu, aby go wyświetlić. Odwołane, użytkownicy nie będą mogli wyświetlić dokument następnym razem użytkownik podejmie próbę, aby go otworzyć.

Ta etykieta nie jest odpowiednia dla wiadomości e-mail.

1. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Upewnij się, że **Ustaw uprawnienia** opcja jest wybrany, a następnie wybierz **Dodaj uprawnienia**.

3. Na **Dodaj uprawnienia** bloku wybierz **wprowadź szczegóły**.

4. Wprowadź nazwę domeny z innej organizacji, na przykład **fabrikam.com**. Następnie wybierz pozycję **Dodaj**.

5. Z **wybierz uprawnienia z wstępnie ustawionych**, wybierz opcję **podglądu**, a następnie wybierz pozycję **OK**.

6. Po powrocie **ochrony** bloku dla **zezwala na dostęp w trybie offline, ustawianie**, wybierz opcję **nigdy**.

7. Kliknij przycisk **OK** na **ochrony** bloku, a następnie kliknij **Zapisz** na **etykiety** bloku.


### <a name="example-3-add-external-users-to-an-existing-label"></a>Przykład 3: Dodawanie użytkowników zewnętrznych do istniejącej etykiety

Nowych użytkowników, które dodajesz będzie w stanie otwarte dokumenty i wiadomości e-mail, które są już chronione przy użyciu tej etykiety. Uprawnienia przyznanie Ci użytkownicy mogą różnić się od uprawnienia, które mają istniejących użytkowników.

1. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Upewnij się, że **Ustaw uprawnienia** jest wybrany, a następnie wybierz **Dodaj uprawnienia**.

3. Na **Dodaj uprawnienia** bloku wybierz **wprowadź szczegóły**.

4. Wprowadź adres e-mail użytkownika pierwszy (lub grupy) aby dodać, a następnie wybierz pozycję **Dodaj**.

5. Wybierz uprawnienia dla tego użytkownika (lub grupy).

6. Powtórz kroki 4 i 5 dla każdego użytkownika (lub grupy), który chcesz dodać do tej etykiety. Następnie kliknij przycisk **OK**.

7. Kliknij przycisk **OK** na **ochrony** bloku, a następnie kliknij **Zapisz** na **etykiety** bloku.

### <a name="example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward"></a>Przykład 4: Etykieta chronioną wiadomość e-mail, obsługującego mniej restrykcyjne uprawnienia niż nie przesyłaj dalej

Ta etykieta nie może być ograniczony do programu Outlook, ale zapewnia formantów mniej restrykcyjny niż przy użyciu nie przesyłaj dalej. Na przykład chcesz adresatów, aby można było skopiować z wiadomości e-mail lub załącznika lub zapisać i Edytuj załącznik.

Jeśli określisz użytkowników zewnętrznych, którzy nie mają konta w usłudze Azure AD:

- Etykieta jest odpowiednia do obsługi poczty e-mail, korzystając z usługi Exchange Online jest [nowe funkcje w szyfrowanie wiadomości usługi Office 365](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). 
 
- Dla załączników pakietu Office, które są automatycznie chronione dokumenty te są dostępne do wyświetlania w przeglądarce. Aby edytować te dokumenty, Pobierz i edytować je za pomocą pakietu Office 2016 kliknij do uruchomienia i konta Microsoft, która używa tego samego adresu e-mail. [Więcej informacji](../get-started/secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)


> [!NOTE]
> Exchange Online wprowadza nową opcję [tylko do szyfrowania](configure-usage-rights.md#encrypt-only-option-for-emails). Ta opcja nie jest dostępne dla konfiguracji etykiety. Jednak, gdy wiesz, który będzie adresatów, aby skonfigurować etykietę przy użyciu tego samego zestawu praw użytkowania można użyć w tym przykładzie. 

Gdy użytkownicy określić adresy e-mail w **do** polu adresy muszą należeć do tych samych użytkowników, które określisz dla tej konfiguracji etykiety. Ponieważ użytkownicy mogą należeć do grupy i mieć więcej niż jeden adres e-mail, adres e-mail, które określają musi odpowiadać na adres e-mail, należy określić uprawnienia. Jednak określając taki sam adres e-mail jest najprostszym sposobem zapewnienia, że odbiorcy będą uzyskał autoryzację. Aby uzyskać więcej informacji na temat sposobu autoryzowanych użytkowników na potrzeby uprawnień, zobacz [przygotowywanie użytkowników i grup usługi Azure Information Protection](../plan-design/prepare.md). 

1. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Upewnij się, że **Ustaw uprawnienia** jest zaznaczone i wybierz **Dodaj uprawnienia**.

3. Na **Dodaj uprawnienia** bloku: Aby udzielić uprawnień dla użytkowników w Twojej organizacji, wybierz **Dodaj \<nazwa organizacji > — wszystkie elementy członkowskie** zaznacz wszystkich użytkowników w dzierżawie. To ustawienie wyłącza konta gościa. Lub wybierz **przeglądania katalogu** wybrać określone grupy. Aby udzielić uprawnień dla użytkowników zewnętrznych lub jeśli wolisz wpisz adres e-mail, wybierz **wprowadź szczegóły** i wpisz adres e-mail użytkownika lub grupy usługi Azure AD lub nazwy domeny.
    
    Powtórz ten krok, aby określić dodatkowych użytkowników, którzy powinni mieć takie same uprawnienia.

4. Dla **wybierz uprawnienia z wstępnie ustawionych**, wybierz opcję **współwłaściciel**, **Współautor**, **recenzenta**, lub **niestandardowe**wybrać, które chcesz udzielić uprawnień.
    
    Uwaga: Nie należy wybierać **podglądu** dla wiadomości e-mail i wybranie **niestandardowe**, upewnij się, że zawrzesz **Edytuj i zapisuj**.
    
    Aby wybrać te same uprawnienia, które pasują do nowych **tylko do szyfrowania** usługi Exchange Online, wybierz opcję **niestandardowe**. Następnie wybierz pozycję wszystkie uprawnienia z wyjątkiem **Zapisz jako, Eksportuj (EXPORT)** i **Pełna kontrola (OWNER)**.

5. Aby określić dodatkowych użytkowników, którzy powinni mieć różne uprawnienia, powtórz kroki 3 i 4.

6. Kliknij przycisk **OK** na **Dodaj uprawnienia** bloku.

7. Kliknij przycisk **OK** na **ochrony** bloku, a następnie kliknij **Zapisz** na **etykiety** bloku.


### <a name="example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it"></a>Przykład 5: Etykiety, która szyfruje zawartość, ale nie ogranicza kto ma dostęp

Ta konfiguracja ma tę zaletę, że nie trzeba określić użytkowników, grupy lub domeny, do ochrony wiadomości e-mail lub dokumentu. Zawartość nadal będą szyfrowane i nadal można określić praw użytkowania, datę wygaśnięcia oraz dostęp w trybie offline. Tej konfiguracji należy używać tylko wtedy, gdy trzeba ograniczyć, kto może otwierać chronionego dokumentu lub wiadomości e-mail. [Więcej informacji na temat tego ustawienia](#more-information-about-add-any-authenticated-users)

1. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Upewnij się, że **Ustaw uprawnienia** jest wybrany, a następnie wybierz **Dodaj uprawnienia**.

3. Na **Dodaj uprawnienia** bloku na **wybierz z listy** , a następnie wybierz **Dodaj wszystkich uwierzytelnionych użytkowników (wersja zapoznawcza)**.

4. Wybierz uprawnienia i kliknij przycisk **OK**.

5. Po powrocie **ochrony** bloku, skonfigurować ustawienia dla **wygaśnięcia zawartości** i **Zezwalaj na dostęp offline**, jeśli potrzebne, a następnie kliknij przycisk **OK**.

6. Na **etykiety** bloku wybierz **Zapisz**.


## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy). 

Reguły przepływu poczty programu Exchange można także zastosować ochronę, na podstawie Twojej etykiet. Aby uzyskać więcej informacji i przykładów, zobacz [konfigurowania usługi Exchange Online reguły przepływu poczty dla etykiety usługi Azure Information Protection](configure-exo-rules.md).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]