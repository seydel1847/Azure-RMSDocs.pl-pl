---
title: "Konfigurowanie etykiety usługi Azure Information Protection w celu zastosowania ochrony"
description: "Najbardziej poufne dokumenty i wiadomości e-mail możesz chronić po skonfigurowaniu etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: 2f6bc027353f38e272a6765c10e770643b739d26
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2017
---
# <a name="how-to-configure-a-label-for-rights-management-protection"></a>Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management

>*Dotyczy: Azure Information Protection*

Najbardziej poufne dokumenty i wiadomości e-mail można chronić przy użyciu usługi Rights Management. Ta usługa używa zasad szyfrowania, tożsamości i autoryzacji w celu zapobieżenia utracie danych. Ochrona jest stosowana, gdy skonfigurujesz etykietę do używania ochrony usługi Rights Management dla dokumentów i wiadomości e-mail, lub **nie przesyłaj dalej** dotycząca wiadomości e-mail programu Outlook. 

## <a name="how-the-protection-works"></a>Jak działa ochrona

Gdy dokument lub wiadomość e-mail są chronione przez usługę Rights Management, będą szyfrowane podczas przechowywania i podczas przesyłania, a odszyfrować je mogą tylko autoryzowani użytkownicy. Szyfrowanie zostaje utrzymane w dokumencie lub wiadomości e-mail, nawet w przypadku zmiany nazwy dokumentu lub wiadomości. Ponadto możesz skonfigurować prawa i ograniczenia użytkowania, np.:

- Tylko użytkownicy w organizacji mogą otworzyć poufny firmowy dokument lub wiadomość e-mail.

- Tylko użytkownicy w dziale marketingu mogą edytować i drukować dokument lub wiadomość e-mail z ogłoszeniem o promocji, podczas gdy wszyscy inni użytkownicy w organizacji mogą jedynie odczytywać ten dokument lub tę wiadomość e-mail.

- Użytkownicy nie mogą przesyłać dalej wiadomości e-mail, która zawiera informacje o wewnętrznej reorganizacji, ani kopiować jej zawartości.

- Bieżącego cennika przesyłanego do partnerów biznesowych nie można otworzyć po określonej dacie.

Aby uzyskać więcej informacji na temat ochrony usługi Azure Rights Management i jej działania, zobacz [co to jest usługa Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Aby skonfigurować etykietę w celu zastosowania tej ochrony, usługi Azure Rights Management musi być aktywowany dla Twojej organizacji. Jeśli jeszcze nie zostało to zrobione, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

Gdy etykieta dotyczy ochrony, chronionego dokumentu nie nadaje się do zapisania w programie SharePoint lub usługi OneDrive. Te lokalizacje nie obsługują następujące chronionych plików: współtworzenia, Office Online wyszukiwania, dokumentu podglądu, miniatur i zbieranie elektronicznych materiałów dowodowych. 

Zanim użytkownicy będą mogli stosować w programie Outlook etykiety do ochrony wiadomości e-mail, programu Exchange nie trzeba konfigurować do zarządzania prawami do informacji (IRM). Jednak dopóki program Exchange nie zostanie skonfigurowany dla usługi IRM, nie będzie można uzyskać pełnej funkcjonalności podczas korzystania z ochrony usługi Azure Rights Management w połączeniu z programem Exchange. Na przykład użytkownicy nie będą mogli wyświetlać chronionych wiadomości e-mail na telefonach komórkowych ani w aplikacji Outlook w sieci Web. Chronione wiadomości e-mail nie będą też indeksowane do wyszukiwania ani nie będzie można skonfigurować programu Exchange Online DLP pod kątem ochrony zarządzania prawami. Informacje o konfigurowaniu programu Exchange do obsługi tych dodatkowych scenariuszy można znaleźć w następujących zasobach:

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

6. W bloku **Ochrona** wybierz opcję **Azure RMS** lub **HYOK (AD RMS)**.     
    W większości przypadków wybierz **usługi Azure RMS** dla ustawienia uprawnień. Nie należy wybierać usługi **HYOK (AD RMS)**, chyba że użytkownik przeczytał i zrozumiał warunki wstępne i ograniczenia towarzyszące tej konfiguracji rozwiązania „*zachowaj własny klucz*” (HYOK, hold your own key). Aby uzyskać więcej informacji, zobacz [Wymagania i ograniczenia dotyczące rozwiązania „hold your own key” (HYOK) dla ochrony za pomocą usług AD RMS](configure-adrms-restrictions.md). Aby kontynuować konfigurację dla funkcji HYOK (AD RMS), przejdź do kroku 10.
    
7. Wybierz jedną z następujących opcji:
    
    - **Wybierz wstępnie zdefiniowany szablon**: aby użyć jednego z szablonów domyślnych lub samodzielnie skonfigurowanego szablonu niestandardowego. Ten szablon musi zostać opublikowany (bez archiwizacji) i nie muszą już połączony z inną etykietę. Po wybraniu tej opcji można użyć **Edytuj szablon** przycisk, aby [przekonwertować szablon na etykietę](configure-policy-templates.md#to-convert-templates-to-labels).
    
    - **Ustaw uprawnienia**: Aby zdefiniować nowe ustawienia ochrony w tym portalu.
    
    - **Uprawnienia (wersja zapoznawcza) zdefiniowane przez użytkownika zestaw**: pozwala określić kto powinien mieć uprawnienia i są te uprawnienia. Można następnie dostosować tę opcję i wybierz tylko w programie Outlook (ustawienie domyślne) lub programu Word, Excel, PowerPoint i Eksploratora plików. 
        
        Jeśli wybierzesz opcję dla programu Outlook: Etykieta jest wyświetlana w programie Outlook i efekty, gdy użytkownicy mają zastosowanie etykiety jest taka sama jak opcja nie przekazuj.
        
        Jeśli wybierzesz opcję dla programu Word, Excel, PowerPoint i Eksploratora plików: Ta opcja wymaga wersja klienta usługi Azure Information Protection. Gdy ta opcja jest ustawiona, a użytkownicy mają klienta w wersji zapoznawczej, etykiety jest wyświetlany w tych aplikacjach. Efekty, gdy użytkownicy mają zastosowanie etykiety jest wyświetlane okno dialogowe, które użytkownicy mogą wybierać uprawnienia niestandardowe. W tym oknie dialogowym Użytkownicy muszą określić uprawnienia, użytkowników lub grup i daty wygaśnięcia. Upewnij się, że użytkownicy mają instrukcje i wytyczne jak podać te wartości.

8. W przypadku wybrania **wybierz szablon wstępnie zdefiniowany** dla **usługi Azure RMS**, kliknij pole listy rozwijanej i wybierz [szablonu](../deploy-use/configure-policy-templates.md) chcesz użyć do ochrony dokumentów i wiadomości e-mail przy użyciu tej etykiety. Nie widzieć zarchiwizowane szablony lub szablonów, które zostały już wybrane do innej etykiety.
    
    W przypadku wybrania **szablon dla działu**, lub jeśli skonfigurowano [kontrolki dołączania](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment):
    
    - Użytkownicy, którzy są poza skonfigurowanym zasięgiem szablonu lub są wyłączeni ze stosowania ochrony usługi Azure Rights Management, będą również widzieć etykietę, ale nie będą mogli jej zastosować. Jeśli wybiorą etykietę, zobaczą następujący komunikat: **Usługa Azure Information Protection nie może zastosować tej etykiety. Jeśli problem będzie nadal występować, skontaktuj się z administratorem.**
        
        Należy pamiętać, że wszystkie opublikowane szablony są zawsze wyświetlane, nawet jeśli konfigurujesz zakresie zasad. Na przykład konfigurujesz zasady o określonym zakresie dla grupy Marketing. Nie są ograniczone do szablonów, które należą do grupy Marketing zakresu szablonów usługi Azure RMS, które można wybrać i można wybrać szablon dla działu, którego nie można użyć wybranych użytkowników. W celu ułatwienia konfiguracji i zminimalizowania potrzeby rozwiązywania problemów należy wziąć pod uwagę nadanie szablonowi dla działu nazwy zgodnej z etykietą w Twoich zasadach o określonym zakresie. 
            
9. W przypadku wybrania **ustawić uprawnienia** dla **usługi Azure RMS**, ta opcja umożliwia skonfigurowanie tych samych ustawień, które można skonfigurować w szablonie. 
    
    Wybierz **dodać uprawnienia**i na **dodać uprawnienia** bloku, wybierz pierwszy zbioru użytkowników i grupy, które będą mieć prawa do korzystania z zawartości, które będą chronione za pomocą wybranej etykiety:
    
    - Wybierz **wybierz z listy** dodać wszystkich użytkowników w organizacji lub przeglądanie katalogu.
        
        Użytkownicy lub grupy musi mieć adres e-mail. W środowisku produkcyjnym, to jest prawie zawsze można, ale w prostym środowisku testowym, może być konieczne dodanie adresów e-mail do kont użytkowników lub grup.
        
    - Wybierz **wprowadź szczegóły** ręcznie określić adres e-mail adresy dla poszczególnych użytkowników lub grup (wewnętrznych lub zewnętrznych). Alternatywnie można określić wszystkich użytkowników w innej organizacji, wprowadzając nazwę domeny z tej organizacji. 
        
    >[!NOTE]
    >Jeśli adres e-mail zmieni się po wybraniu użytkownika lub grupy, zobacz [zagadnienia w przypadku zmiany adresów e-mail](../plan-design/prepare.md#considerations-for-azure-information-protection-if-email-addresses-change) sekcji planowania dokumentacji.
    
    Najlepszym rozwiązaniem wykorzystywanie grup zamiast użytkowników. Ta stratetegy przechowuje konfigurację prostszy i zmniejsza prawdopodobieństwo, że trzeba zaktualizować konfiguracji etykiety później, a następnie zacznij ponownie chronić zawartość. Jednak w przypadku wprowadzania zmian w grupie należy pamiętać, że ze względu na wydajność w usłudze Azure Rights Management [członkostwo w grupie jest buforowane](../plan-design/prepare.md#group-membership-caching-by-azure-rights-management ). 
    
    Po określeniu pierwszy zestaw użytkowników i grup, wybierz uprawnienia, aby udzielić tych użytkowników i grup. Aby uzyskać więcej informacji o uprawnieniach, które możesz wybrać, zobacz [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](configure-usage-rights.md). Jednak aplikacje, które obsługują tę ochronę mogą różnić się w zakresie sposobu wdrażania tych uprawnień. Należy zapoznać się z ich dokumentacją i samodzielnie przeprowadzić testy z użyciem aplikacji wykorzystywanych przez użytkowników, aby sprawdzić zachowanie szablonów przed ich wdrożeniem dla użytkowników.
    
    W razie potrzeby można teraz dodać drugi zestaw użytkowników i grup z prawami użytkowania. Powtórz określono wszyscy użytkownicy i grupy z odpowiednimi uprawnieniami.

    >[!TIP]
    >Rozważ dodanie **Kopiuj i Wyodrębnij zawartość** uprawnień niestandardowych i ich nadanie administratorom odzyskiwania danych lub personel w innych ról, których obowiązki odzyskiwania informacji. W razie potrzeby Ci użytkownicy mogą następnie usuń ochronę plików i wiadomości e-mail, które będą chronione przy użyciu tej etykiety lub szablonu. Możliwość usunięcia ochrony na poziomie uprawnień do dokumentu lub wiadomości e-mail, zapewnia bardziej szczegółową kontrolę niż [funkcja superużytkowników](configure-super-users.md).
    
    Dla wszystkich użytkowników i grup, które można określić na **ochrony** bloku teraz Sprawdź, czy chcesz wprowadzić zmiany w następujących ustawieniach. Pamiętaj, że te ustawienia, tak jak uprawnienia, nie mają zastosowania do [wystawcy ani właściciela w usłudze Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner), ani żadnego przypisanego przez Ciebie [administratora](configure-super-users.md).
    
    |Ustawienie|Więcej informacji|Zalecane ustawienie
    |-----------|--------------------|--------------------|
    |**wygaśnięcie zawartości**|Dla danego szablonu określ datę lub liczbę dni, po upływie których określeni użytkownicy nie będą mogli otwierać dokumentów ani wiadomości e-mail chronionych za pomocą tego szablonu. Można określić datę lub wskazać liczbę dni, jakie muszą minąć, począwszy od momentu objęcia zawartości ochroną.<br /><br />W przypadku określenia daty ustawienie wchodzi w życie o północy czasu mającego zastosowanie w bieżącej strefie czasowej.|**Zawartość nigdy nie wygasa**, jeśli zawartość nie ma określonych wymagań związanych z czasem.|
    |**Zezwalaj na dostęp offline**|Użyj tego ustawienia, aby zrównoważyć wszelkie wymagania dotyczące zabezpieczeń (w tym dostęp po odwołaniu) za pomocą umożliwienia wybranym użytkownikom otwierania chronionej zawartości bez połączenia internetowego.<br /><br />Jeśli można określić, że zawartość nie jest dostępna bez połączenia z Internetem lub zawartość jest dostępna tylko dla określonej liczby dni, po osiągnięciu progu, można ponownie uwierzytelnić tych użytkowników i ich dostęp jest rejestrowany. Kiedy tak się stanie, w przypadku, gdy poświadczenia nie są buforowane, przed otwarciem dokumentu lub wiadomości e-mail tym użytkownikom będzie wyświetlany monit o zalogowanie się.<br /><br />Oprócz ponowne uwierzytelnianie jest ponowna ocena zasad i członkostwa w grupie użytkowników. Oznacza to, że użytkownicy mogą mieć inny poziom dostępu do tego samego dokumentu lub tej samej wiadomości e-mail po wprowadzeniu zmian w zasadach lub w członkostwie grupy mającym miejsce po ich ostatnim uzyskaniu dostępu do danej zawartości. Może to oznaczać brak dostępu, jeśli dokument został [odwołany](../rms-client/client-track-revoke.md).|W zależności od tego, na ile poufna jest zawartość:<br /><br />- **Liczba dni, w których zawartość jest dostępna bez połączenia z Internetem** = **7** dla poufnych danych biznesowych, których udostępnienie nieupoważnionym osobom mogłoby spowodować szkodę w firmie. To zalecenie oferuje zrównoważony kompromis między elastycznością i zabezpieczeniami. Do przykładów należą kontrakty, raporty dotyczące zabezpieczeń, podsumowania prognoz i dane konta sprzedaży.<br /><br />- **Nigdy** dla bardzo poufnych danych biznesowych, które spowodują szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. To zalecenie stawia zabezpieczenia ponad elastycznością i zapewnia, że w przypadku odwołania dokumentu wszyscy autoryzowani użytkownicy natychmiast utracą możliwość otwierania tego dokumentu. Do przykładów należą dane pracowników i klientów, hasła, kod źródłowy i wstępnie zapowiadane raporty finansowe.|
    
    Po zakończeniu konfigurowania uprawnień, kliknij przycisk **OK**. 
    
    Ta grupa ustawień tworzy niestandardowy szablon dla usługi Azure Rights Management. Te szablony mogą być używane z aplikacjami i usługami, które integrują się z usługą Azure Rights Management. Aby uzyskać informacje dotyczące sposobu pobierania i odświeżania tych szablonów przez komputery i usługi, zobacz [Odświeżanie szablonów dla użytkowników i usług](refresh-templates.md).

10. W przypadku wybrania **HYOK (AD RMS)**, wybierz opcję **zestawu AD RMS szablonów szczegóły** lub **uprawnienia (wersja zapoznawcza) zdefiniowane przez użytkownika zestaw**, a następnie określ adres URL licencjonowania usług AD RMS klaster.
    
    Aby uzyskać instrukcje określić szablon identyfikator GUID i adres URL licencjonowania, zobacz [lokalizowanie informacji używanych do określania ochrony usług AD RMS z etykietą usługi Azure Information Protection](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label).
    
    Aby użyć opcji uprawnienia zdefiniowane przez użytkownika, musi mieć wersja klienta usługi Azure Information Protection. Ta opcja pozwala określić kto powinien mieć uprawnienia i te uprawnienia są. Można następnie dostosować tę opcję i wybierz tylko w programie Outlook (ustawienie domyślne) lub programu Word, Excel, PowerPoint i Eksploratora plików. 
    
    Jeśli wybierzesz opcję dla programu Outlook: Etykieta jest wyświetlana w programie Outlook i efekty, gdy użytkownicy mają zastosowanie etykiety jest taka sama jak opcja nie przekazuj.
    
    Jeśli wybierzesz opcję dla programu Word, Excel, PowerPoint i Eksploratora plików: Etykieta jest wyświetlany w tych aplikacjach. Efekty, gdy użytkownicy mają zastosowanie etykiety jest wyświetlane okno dialogowe, które użytkownicy mogą wybierać uprawnienia niestandardowe. W tym oknie dialogowym Użytkownicy muszą określić uprawnienia, użytkowników lub grup i daty wygaśnięcia. Upewnij się, że użytkownicy mają instrukcje i wytyczne jak podać te wartości. Obecnie ta opcja w Eksploratorze plików zawsze używa ochrony usług Azure RMS zamiast ochrony HYOK (AD RMS).

11. Kliknij przycisk **OK**, aby zamknąć blok **Ochrona**, i zobacz swój wybór w opcji **Nie przekazuj** lub obraz wyświetlonego wybranego szablonu dla opcji **Ochrona** w bloku **Etykieta**.

12. W bloku **Etykieta** kliknij przycisk **Zapisz**.

13. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]