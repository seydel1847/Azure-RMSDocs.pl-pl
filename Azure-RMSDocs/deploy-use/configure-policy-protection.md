---
title: "Konfigurowanie etykiety usługi Azure Information Protection w celu zastosowania ochrony"
description: "Najbardziej poufne dokumenty i wiadomości e-mail możesz chronić po skonfigurowaniu etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: f5c4e2f7513832a884820ec0c57c7da2dec5f04e
ms.sourcegitcommit: 8b768e7e249e124f24acdf630d165eaf743f9c21
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2017
---
# Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management
<a id="how-to-configure-a-label-for-rights-management-protection" class="xliff"></a>

>*Dotyczy: Azure Information Protection*

Najbardziej poufne dokumenty i wiadomości e-mail możesz chronić przy użyciu usługi Rights Management, która korzysta z zasad szyfrowania, tożsamości oraz autoryzacji w celu zapobieżenia utracie danych. Ochrona jest stosowana po skonfigurowaniu etykiety do korzystania z szablonu Rights Management dla dokumentów i wiadomości e-mail lub po wybraniu opcji **Nie przekazuj** dla wiadomości e-mail programu Outlook. 

Szablon może być jednym z szablonów domyślnych, które są automatycznie tworzone podczas aktywacji usługi Azure Rights Management, lub szablonem niestandardowym. Szablony działów usługi Azure Rights Management są obsługiwane, ale stosują ochronę tylko wtedy, gdy autor dokumentu lub wiadomości e-mail znajduje się w skonfigurowanym zakresie szablonu. Jeśli użytkownik znajduje się poza zakresem, zobaczy komunikat informujący o tym, że usługa Azure Information Protection nie może zastosować etykiety.

## Jak działa ochrona
<a id="how-the-protection-works" class="xliff"></a>

Gdy dokument lub wiadomość e-mail są chronione przez usługę Rights Management, będą szyfrowane podczas przechowywania i podczas przesyłania, a odszyfrować je mogą tylko autoryzowani użytkownicy. Szyfrowanie zostaje utrzymane w dokumencie lub wiadomości e-mail, nawet w przypadku zmiany nazwy dokumentu lub wiadomości. Ponadto możesz skonfigurować prawa i ograniczenia użytkowania, np.:

- Tylko użytkownicy w organizacji mogą otworzyć poufny firmowy dokument lub wiadomość e-mail.

- Tylko użytkownicy w dziale marketingu mogą edytować i drukować dokument lub wiadomość e-mail z ogłoszeniem o promocji, podczas gdy wszyscy inni użytkownicy w organizacji mogą jedynie odczytywać ten dokument lub tę wiadomość e-mail.

- Użytkownicy nie mogą przesyłać dalej wiadomości e-mail, która zawiera informacje o wewnętrznej reorganizacji, ani kopiować jej zawartości.

- Bieżącego cennika przesyłanego do partnerów biznesowych nie można otworzyć po określonej dacie.

Aby uzyskać więcej informacji o szablonach usługi Azure Rights Management i sposobie ich konfigurowania w klasycznym portalu Azure, zobacz temat [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

Aby uzyskać więcej informacji na temat usługi Azure Rights Management i jej działania, zobacz [Co to jest usługa Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Aby skonfigurować etykietę do stosowania ochrony usługi Rights Management, usługa Azure Rights Management musi być aktywowana dla Twojej organizacji. Jeśli jeszcze nie zostało to zrobione, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

Zanim użytkownicy będą mogli stosować w programie Outlook etykiety do ochrony wiadomości e-mail, programu Exchange nie trzeba konfigurować do zarządzania prawami do informacji (IRM). Jednak dopóki program Exchange nie zostanie skonfigurowany dla usługi IRM, nie będzie można uzyskać pełnej funkcjonalności podczas korzystania z ochrony usługi Azure Rights Management w połączeniu z programem Exchange. Na przykład użytkownicy nie będą mogli wyświetlać chronionych wiadomości e-mail na telefonach komórkowych ani w aplikacji Outlook w sieci Web. Chronione wiadomości e-mail nie będą też indeksowane do wyszukiwania ani nie będzie można skonfigurować programu Exchange Online DLP pod kątem ochrony zarządzania prawami. Informacje o konfigurowaniu programu Exchange do obsługi tych dodatkowych scenariuszy można znaleźć w następujących zasobach:

- Exchange Online — zobacz temat [Usługa Exchange Online: konfiguracja usługi IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- W przypadku lokalnej instalacji programu Exchange należy wdrożyć [łącznik usługi RMS i skonfigurować serwery Exchange](../deploy-use/deploy-rms-connector.md). 


## Aby skonfigurować etykietę pod kątem ochrony usługi Rights Management
<a id="to-configure-a-label-for-rights-management-protection" class="xliff"></a>

1. Jeśli jeszcze tego nie zrobiono, otwórz nowe okno przeglądarki i zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator zabezpieczeń lub administrator globalny, a następnie przejdź do bloku **Azure Information Protection**. 

    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. Jeśli etykieta, którą chcesz skonfigurować, będzie miała zastosowanie do wszystkich użytkowników, z bloku **Azure Information Protection** wybierz opcję **Globalne**. Jeśli jednak etykieta, którą chcesz skonfigurować, należy do [zasad o określonym zakresie](configure-policy-scope.md) i z tego powodu ma zastosowanie tylko do wybranych użytkowników, wybierz te zasady o określonym zakresie.

3. W bloku **Zasady** zaznacz etykietę, którą chcesz skonfigurować, co spowoduje otwarcie bloku **Etykieta**. 

4. W bloku **Etykieta** znajdź pozycję **Ustaw uprawnienia dla dokumentów i wiadomości e-mail zawierających tę etykietę** i wybierz jedną z następujących opcji.
    
    - **Nieskonfigurowane**: wybierz tę opcję, jeśli etykieta jest obecnie skonfigurowana do stosowania ochrony i już nie chcesz, aby wybrana etykieta korzystała z ochrony. Następnie przejdź do kroku 11.
    
    - **Chroń**: wybierz tę opcję, aby zastosować ochronę, a następnie przejdź do kroku 5.
    
    - **Usuń ochronę**: wybierz tę opcję, aby usunąć ochronę, jeśli jest skonfigurowana dla dokumentu lub wiadomości e-mail. Następnie przejdź do kroku 11.
        
        Należy zauważyć, że użytkownicy muszą mieć uprawnienia do usuwania ochrony usługi Rights Management w celu zastosowania etykiety, która ma tę opcję. Ta opcja wymaga, aby użytkownicy posiadali [prawa użytkowania](../deploy-use/configure-usage-rights.md) **Eksportuj** lub **Pełna kontrola**, byli właścicielami usługi Rights Management (co automatycznie udziela prawa użytkowania Pełna kontrola) lub byli [administratorami usługi Azure Rights Management](../deploy-use/configure-super-users.md). Domyślne szablony usługi Azure Rights Management nie obejmują praw użytkowania, które pozwalają użytkownikom na usuwanie ochrony. 
        
        Jeśli użytkownicy nie mają uprawnień do usuwania ochrony usługi Rights Management i wybiorą etykietę z opcją **Usuń ochronę**, zobaczą następujący komunikat: **Usługa Azure Information Protection nie może zastosować etykiety. Jeśli problem będzie nadal występować, skontaktuj się z administratorem.**

5. Jeśli została wybrana opcja **Chroń**, wybierz pasek **Ochrona**, aby otworzyć blok **Ochrona**:
    
    ![Konfigurowanie ochrony dla etykiety usługi Azure Information Protection](../media/info-protect-protection-bar.png)

6. W bloku **Ochrona** wybierz opcję **Azure RMS** lub **HYOK (AD RMS)**. 
    
    W większości przypadków wybierzesz opcję **Azure RMS** dla swoich ustawień uprawnień. Nie należy wybierać usługi **HYOK (AD RMS)**, chyba że użytkownik przeczytał i zrozumiał warunki wstępne i ograniczenia towarzyszące tej konfiguracji rozwiązania „*zachowaj własny klucz*” (HYOK, hold your own key). Aby uzyskać więcej informacji, zobacz [Wymagania i ograniczenia dotyczące rozwiązania „hold your own key” (HYOK) dla ochrony za pomocą usług AD RMS](configure-adrms-restrictions.md). Aby kontynuować konfigurację dla funkcji HYOK (AD RMS), przejdź do kroku 10.
    
7. Wybierz jedną z następujących opcji:
    
    - **Nie przesyłaj dalej**: aby ustawić tę opcję programu Outlook dla wiadomości e-mail.
    
    - **Wybierz wstępnie zdefiniowany szablon**: aby użyć jednego z szablonów domyślnych lub samodzielnie skonfigurowanego szablonu niestandardowego.
    
    - **Ustaw uprawnienia (wersja zapoznawcza)**: aby zdefiniować nowe ustawienia ochrony w tym portalu.

8. W przypadku wybrania opcji **Wybierz wstępnie zdefiniowany szablon** dla usługi **Azure RMS** kliknij pole listy rozwijanej i wybierz [szablon](../deploy-use/configure-custom-templates.md), którego chcesz użyć do ochrony dokumentów i wiadomości e-mail przy użyciu tej etykiety.
    
    Należy pamiętać, że w przypadku wybrania **szablonu dla działu** lub skonfigurowania [kontrolek dołączania](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment):
    
    - Użytkownicy, którzy są poza skonfigurowanym zasięgiem szablonu lub są wyłączeni ze stosowania ochrony usługi Azure Rights Management, będą również widzieć etykietę, ale nie będą mogli jej zastosować. Jeśli wybiorą etykietę, zobaczą następujący komunikat: **Usługa Azure Information Protection nie może zastosować tej etykiety. Jeśli problem będzie nadal występować, skontaktuj się z administratorem.**
    
        Należy pamiętać, że zawsze wyświetlane są wszystkie szablony, nawet jeśli konfigurujesz zasady o określonym zakresie. Na przykład konfigurujesz zasady o określonym zakresie dla grupy Marketing. Możliwe do wyboru szablony usług Azure RMS nie będą ograniczone do szablonów należących do zakresu grupy Marketing. Można wybrać szablon dla działu, którego nie mogą użyć wybrani przez Ciebie użytkownicy. W celu ułatwienia konfiguracji i zminimalizowania potrzeby rozwiązywania problemów należy wziąć pod uwagę nadanie szablonowi dla działu nazwy zgodnej z etykietą w Twoich zasadach o określonym zakresie. 
            
9. Jeśli wybierzesz opcję **Ustaw uprawnienia (wersja zapoznawcza)** dla usługi **Azure RMS**, zawiera ona większość opcji konfiguracji dla [szablonów niestandardowych](configure-custom-templates.md), które można konfigurować w klasycznym portalu Azure. Ponadto możesz łatwo dodać wszystkich użytkowników w swojej organizacji i określić zewnętrzne adresy e-mail dla poszczególnych użytkowników lub grup, a po określeniu nazwy domeny — dla wszystkich użytkowników w innej organizacji. 
    
    Aby uzyskać więcej informacji o tej konfiguracji podglądu, zobacz wpis na blogu [Azure Information Protection unified administration now in Preview](https://blogs.technet.microsoft.com/enterprisemobility/2017/04/26/azure-information-protection-unified-administration-now-in-preview/) (Azure Information Protection: ujednolicone administrowanie teraz w w wersji zapoznawczej). 
    
    Aby uzyskać więcej informacji o uprawnieniach, które możesz wybrać, zobacz [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](configure-usage-rights.md).
    
    Sprawdź, czy nie jest konieczne wprowadzenie zmian w następujących ustawieniach uwzględnionych w opcji **Ustaw uprawnienia (wersja zapoznawcza)**. Pamiętaj, że te ustawienia, tak jak uprawnienia, nie mają zastosowania do [wystawcy ani właściciela w usłudze Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner), ani żadnego przypisanego przez Ciebie [administratora](configure-super-users.md).
    
    |Ustawienie|Więcej informacji|Zalecane ustawienie
    |-----------|--------------------|--------------------|
    |**wygaśnięcie zawartości**|Dla danego szablonu określ datę lub liczbę dni, po upływie których określeni użytkownicy nie będą mogli otwierać dokumentów ani wiadomości e-mail chronionych za pomocą tego szablonu. Można określić datę lub wskazać liczbę dni, jakie muszą minąć, począwszy od momentu objęcia zawartości ochroną.<br /><br />W przypadku określenia daty ustawienie wchodzi w życie o północy czasu mającego zastosowanie w bieżącej strefie czasowej.|**Zawartość nigdy nie wygasa**, jeśli zawartość nie ma określonych wymagań związanych z czasem.|
    |**Zezwalaj na dostęp offline**|Użyj tego ustawienia, aby zrównoważyć wszelkie wymagania dotyczące zabezpieczeń (w tym dostęp po odwołaniu) za pomocą umożliwienia wybranym użytkownikom otwierania chronionej zawartości bez połączenia internetowego.<br /><br />Jeśli wybierzesz ustawienie uniemożliwiające uzyskanie dostępu do zawartości w przypadku braku połączenia z Internetem lub ustawienie umożliwiające uzyskanie dostępu do zawartości jedynie w ciągu określonej liczby dni, po osiągnięciu progu ci użytkownicy muszą zostać ponownie uwierzytelnieni, a ich dostęp musi zostać zarejestrowany. Kiedy tak się stanie, w przypadku, gdy poświadczenia nie są buforowane, przed otwarciem dokumentu lub wiadomości e-mail tym użytkownikom będzie wyświetlany monit o zalogowanie się.<br /><br />Poza ponownym uwierzytelnieniem następuje także ponowna ocena zasad i członkostwa w grupie użytkowników. Oznacza to, że użytkownicy mogą mieć inny poziom dostępu do tego samego dokumentu lub tej samej wiadomości e-mail po wprowadzeniu zmian w zasadach lub w członkostwie grupy mającym miejsce po ich ostatnim uzyskaniu dostępu do danej zawartości. Może to oznaczać brak dostępu, jeśli dokument został [odwołany](../rms-client/client-track-revoke.md).|W zależności od tego, na ile poufna jest zawartość:<br /><br />- **Liczba dni, w których zawartość jest dostępna bez połączenia z Internetem** = **7** dla poufnych danych biznesowych, których udostępnienie nieupoważnionym osobom mogłoby spowodować szkodę w firmie. To zalecenie oferuje zrównoważony kompromis między elastycznością i zabezpieczeniami. Do przykładów należą kontrakty, raporty dotyczące zabezpieczeń, podsumowania prognoz i dane konta sprzedaży.<br /><br />- **Nigdy** dla bardzo poufnych danych biznesowych, które spowodują szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. To zalecenie stawia zabezpieczenia ponad elastycznością i zapewnia, że w przypadku odwołania dokumentu wszyscy autoryzowani użytkownicy natychmiast utracą możliwość otwierania tego dokumentu. Do przykładów należą dane pracowników i klientów, hasła, kod źródłowy i wstępnie zapowiadane raporty finansowe.|
    
    Ta grupa ustawień tworzy niestandardowy szablon dla usługi Azure Rights Management. Te szablony mogą być używane z aplikacjami i usługami, które integrują się z usługą Azure Rights Management. Aby uzyskać informacje dotyczące sposobu pobierania i odświeżania tych szablonów przez komputery i usługi, zobacz [Odświeżanie szablonów dla użytkowników i usług](refresh-templates.md).

10. W przypadku wybrania opcji **Wybierz szablon** dla usługi **HYOK (AD RMS)**: podaj identyfikator GUID szablonu i adres URL licencjonowania klastra usługi AD RMS. [Więcej informacji](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

11. Kliknij przycisk **OK**, aby zamknąć blok **Ochrona**, i zobacz swój wybór w opcji **Nie przekazuj** lub obraz wyświetlonego wybranego szablonu dla opcji **Ochrona** w bloku **Etykieta**.

12. W bloku **Etykieta** kliknij przycisk **Zapisz**.

13. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## Następne kroki
<a id="next-steps" class="xliff"></a>

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]