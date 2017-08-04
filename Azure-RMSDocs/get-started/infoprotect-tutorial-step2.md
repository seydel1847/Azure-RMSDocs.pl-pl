---
title: "Samouczek Szybki start — krok 2 — AIP"
description: "Krok 2 samouczka wprowadzającego, dzięki któremu można szybko wypróbować usługę Azure Information Protection — konfigurowanie zasad."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
ms.openlocfilehash: 86857d9fe744ee8b8949bdf247a360492ceb8165
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2017
---
# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>Krok 2. Konfigurowanie i publikowanie zasad usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Usługa Azure Information Protection zawiera domyślną zasadę, której można użyć bez konfiguracji, ale chcemy się jej przyjrzeć i wprowadzić kilka zmian.

1. W nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator globalny lub administrator zabezpieczeń swojej dzierżawy.

2. W menu centralnym kliknij przycisk **Nowy**, a następnie z listy **MARKETPLACE** wybierz opcję **Zabezpieczenia i tożsamość**. W bloku **Zabezpieczenia i tożsamość**  wybierz z listy **POLECANE APLIKACJE** opcję **Azure Information Protection**. W bloku **Azure Information Protection** kliknij przycisk **Utwórz**.

    Spowoduje to uaktywnienie usługi dla dzierżawy i utworzenie bloku **Azure Information Protection**, dzięki czemu przy następnym logowaniu w portalu będzie można wybrać usługę z listy centralnej **Więcej usług**. 

    > [!TIP] 
    > Wybierz opcję **Przypnij do pulpitu nawigacyjnego**, aby utworzyć kafelek usługi **Azure Information Protection** na pulpicie nawigacyjnym, dzięki czemu można będzie pominąć krok przeglądania w poszukiwaniu usługi przy następnym zalogowaniu w witrynie portalu.

3. Należy zwrócić uwagę na informację znajdującą się na stronie **Szybki start**, która zostanie automatycznie otwarta przy pierwszym połączeniu z usługą. Możesz do niej wrócić później. W tym samouczku kliknij przycisk **Zasady globalne**, aby otworzyć blok **Zasady: globalne**. Ten blok zostaje automatycznie otwarty przy kolejnych połączeniach z usługą i zawiera domyślne zasady usługi Information Protection, które są tworzone automatycznie dla dzierżawcy:
    
    - Etykiety klasyfikacji: **Osobiste**, **Publiczne**, **Ogólne**, **Poufne** i **Wysoce poufne**. Ostatnich dwóch etykiet rozwijania w celu pokazania etykiety podrzędne, które obejmują **wszyscy pracownicy** i **każdy (nie jest chroniony)**, zapewniając przykłady klasyfikacji podkategoriami.
    
       > [!NOTE]
       > Twoje zasady domyślne mogą się nieco różnić od podanych w tym samouczku. Na przykład możesz mieć etykietę o nazwie **Wewnętrzne** zamiast **Ogólne** i **Tajne** zamiast **Wysoce poufne**. Lub dodatkowych etykietę podrzędną o nazwie **odbiorców tylko**. Jest tak, ponieważ istnieją różne wersje domyślne zasady, w zależności od tego, kiedy został utworzony dla Twojej dzierżawy. Lub dokonałeś ich samodzielnej edycji przed uruchomieniem samouczka.
       > 
       > Jeśli Twoje domyślne zasady wyglądają inaczej, nadal możesz używać tego samouczka, ale należy pamiętać o tych zmianach, korzystając z poniższych instrukcji i obrazów. Jeśli chcesz zmodyfikować zasady domyślne tak, aby pasowały do bieżących zasad domyślnych, zobacz [Domyślne zasady usługi Azure Information Protection](../deploy-use/configure-policy-default.md).

    - Z konfiguracji domyślnej niektóre etykiet nie ma oznaczenia wizualne skonfigurowane (takie jak stopka, nagłówek, znak wodny). W zależności od Twojego domyślne zasady niektóre etykiety może być ochrony ustawiona, czy nie. Na przykład:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zasada domyślna](../media/info-protect-policy-default-labelsv2.png)
    
    Ponadto istnieją ustawienia zasad, które nie są ustawione. Wszystkie dokumenty i wiadomości e-mail nie muszą mieć etykietę, brak jest etykiety domyślnej, a użytkownicy nie muszą uzasadniać ich zmieniać etykiety:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zasada domyślna](../media/info-protect-policy-default-settings.png)

## <a name="changing-the-settings-for-a-default-label-and-prompt-for-justification"></a>Zmiana ustawień domyślnej etykiety i monit o uzasadnienie

W naszym samouczku zmienimy kilka z tych ustawień zasad, aby zobaczyć, jak działają:

1. Ustaw wartość opcji **Wybierz etykietę domyślną** na **Ogólne**. 

    Jeśli nie masz tej etykiety, ponieważ masz starszą wersję zasad, wybierz **Wewnętrzne** jako równoważną etykietę.

2. Dla opcji **Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę** wybierz wartość **Włączone**.

## <a name="configuring-a-label-for-protection-a-watermark-and-a-condition-to-prompt-for-classification"></a>Konfigurowanie etykiety ochrony, znaku wodnego oraz warunku monitowania o klasyfikację

Zmienimy teraz ustawienia jednej z podrzędnych etykiet **Wszyscy pracownicy** głównej etykiety **Poufne**. 

Jeśli etykieta **Poufne** nie ma podrzędnych etykiet, ponieważ masz starszą wersję zasad, możesz zamiast niej użyć etykiety **Poufne**. Czynności konfiguracyjne są takie same, ale nazwa bloku etykiety **poufne** zamiast **wszyscy pracownicy**.

1. Upewnij się, że **poufne** etykiety jest rozwinięty, ukazując etykiety podrzędne, a następnie w **wszyscy pracownicy** etykietę, zanotuj, czy **usługi Azure RMS** nie będą wyświetlane **ochrony** kolumny. Jeśli tak jest, masz najnowszą domyślne zasady i ochrony dla tej etykiety jest automatycznie konfigurowany dla Ciebie. Jeśli ta kolumna jest pusta, należy skonfigurować ochronę w kolejnym kroku.

    Wybierz tę opcję, **wszyscy pracownicy** etykietę podrzędną i w nowym **etykiety: Wszyscy pracownicy** bloku, pojawi się ustawienia, które są dostępne dla każdej etykiety. 

2. Odczytaj tekst **Opisu** dla tej etykiety. Opisuje on sposób zamierzonego użycia wybranej etykiety i jest widoczny dla użytkowników jako etykietka narzędzia pomagająca im zdecydować, którą etykietę wybrać.

3. Jeśli ochrony został już skonfigurowany dla etykiety, przejdź do kroku 5.
    
    Jeśli ochrona nie jest skonfigurowany dla etykiety, Znajdź sekcję **ustawić uprawnień dla dokumentów i wiadomości e-mail zawierających tę etykietę**. Wybierz **Chroń**, a następnie wybierz **ochrony** paska:
    
    ![Ochrony skonfigurowane dla etykiety usługi Azure Information Protection](../media/info-protect-protection-bar-configured.png) 
    
4. W **ochrony** bloku, upewnij się, że **usługi Azure RMS** jest zaznaczone, a następnie wybierz pozycję **wybierz szablon wstępnie zdefiniowany**. Kliknij pole listy rozwijanej, a następnie wybierz domyślny szablon, który pozwala wszystkim użytkownikom w organizacji widoku i edytowania zawartości chronionej. 
    
    Jeśli niedawno uzyskano subskrypcję, ten szablon ma nazwę **Poufne\Wszyscy pracownicy**. 
    
    Jeśli subskrypcję uzyskano wcześniej, szablon domyślny może mieć nazwę **\<nazwa organizacji > — poufne**. Na przykład jeśli nazwą firmy jest VanArsdel, Ltd, zobaczysz opcję **VanArsdel, Ltd — poufne**, którą wybierzesz: 
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — ustawianie ochrony usługi Azure RMS](../media/step2-select-rms-template.png)
    
    Jeśli ten szablon domyślny usługi Azure Rights Management został wyłączony, wybierz szablon alternatywny. Jednak w przypadku wybrania szablonu działu upewnij się, czy Twoje konto znajduje się w jego zakresie.
    
4. Kliknij przycisk **OK**, aby zapisać zmiany, co spowoduje zamknięcie bloku **Ochrona**. Zostanie wyświetlony pasek ochrony zaktualizowane w **etykiety: Wszyscy pracownicy** bloku. Na przykład:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — skonfigurowana ochrona usługi Azure RMS](../media/protection-bar-configured.png)
    
5. Teraz w bloku **Etykieta: Wszyscy pracownicy** odszukaj sekcję **Ustawianie oznaczenia wizualnego**:
    
    Dla ustawienia **Dokumenty z tą etykietą mają znak wodny** kliknij opcję **Włącz**, a następnie wpisz nazwę swojej organizacji w polu **Tekst**. W naszym przykładzie: **VanArsdel, Ltd**: 
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — ustawianie ochrony usługi Azure RMS](../media/step2-configure-watermark.png)
    
    Mimo że można zmienić rozmiar, kolor i układ znaki wodne, pozostanie te ustawienia wartości domyślne dla teraz.
    
6. Zlokalizuj sekcję **Konfigurowanie warunków automatycznego stosowania tej etykiety**:
    
    Kliknij przycisk **Dodaj nowy warunek** i następnie w bloku **Warunek** wykonaj następujące czynności:
    
    a. **Wybierz typ warunku**: zachowaj wartość domyślną **Wbudowany**.
    
    b. **Wybierz wbudowany**: z listy rozwijanej wybierz opcję **Numer karty kredytowej**.
    
    c. **Minimalna liczba wystąpień**: zachowaj ustawienie domyślne **1**.
    
    d. **Zliczaj tylko wystąpienia o unikatowych wartościach**: zachowaj wartość domyślną **Wł**.
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — konfigurowanie warunku karty kredytowej](../media/step2-configure-condition.png)
    
    Kliknij przycisk **Zapisz**, aby powrócić do bloku **Etykieta: Wszyscy pracownicy**.

7. W bloku **Etykieta: Wszyscy pracownicy** zobaczysz, że jako **NAZWA WARUNKU** jest wyświetlany **Numer karty kredytowej** z opcją **WYSTĄPIENIA** równą **1**:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — konfigurowanie warunku karty kredytowej](../media/step2-see-condition.png)

8. Dla opcji **Wybierz sposób stosowania tej etykiety**: zachowaj wartość domyślną **Zalecany** i nie zmieniaj domyślnej wskazówki zasad:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zalecana klasyfikacja](../media/step2-keep-recommendedv2.png)

9. W polu **Wprowadź informacje dla celów wewnętrznych** wpisz **Tylko do testów**:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — wpisz uwagi](../media/step2-type-notes.png)

10. Kliknij przycisk **zapisać** na tym **etykiety: Wszyscy pracownicy** bloku. Następnie ponownie kliknij przycisk **Zapisz** w bloku **Zasady: Globalne**.
    
    Po skonfigurowaniu etykiety dla ochrony etykiety jest teraz zaktualizowane w celu wyświetlenia ochrony usług Azure RMS:

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — skonfigurowana zasada domyślna](../media/info-protect-policy-configuredv2.png)
    
    Widoczny jest również, czy ustawienia zostały skonfigurowane z zmiany dla etykiety domyślnej oraz uzasadnienie:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — skonfigurowane ustawienia](../media/info-protect-settings-configuredv2.png)
    
11. Aby po wprowadzeniu i zapisaniu zmian udostępnić je użytkownikom, w bloku początkowym **Azure Information Protection** należy kliknąć opcję **Opublikuj**, a następnie przycisk **Tak**, aby potwierdzić wybór.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — publikowanie skonfigurowanych zasad](../media/info-protect-publish.png)

Po zakończeniu tego samouczka możesz zamknąć portal Azure lub zostawić otwarty w celu wypróbowania innych opcji konfiguracji.

Skoro przyjrzeliśmy się już domyślnej zasadzie i wprowadziliśmy w niej kilka zmian, następnym krokiem jest zainstalowanie klienta usługi Azure Information Protection.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje o opcjach konfiguracji zasad|[Konfigurowanie zasad usługi Azure Information Protection](../deploy-use/configure-policy.md)|
|Ustawienia konfiguracji w domyślnych zasad|[Domyślne zasady usługi Azure Information Protection](../deploy-use/configure-policy-default.md)|


>[!div class="step-by-step"]
[&#171; Krok 1](infoprotect-tutorial-step1.md)
[Krok 3 &#187;](infoprotect-tutorial-step3.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]