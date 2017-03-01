---
title: "Samouczek Szybki start — krok 2 — AIP"
description: "Krok 2 samouczka wprowadzającego, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection w swojej organizacji. Wystarczy około 20 minut."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 39dfa8a1c4dabf32f8b62f08a674152f41a5b96a
ms.lasthandoff: 02/24/2017


---

# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>Krok 2. Konfigurowanie i publikowanie zasad usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Usługa Azure Information Protection zawiera domyślną zasadę, której można użyć bez konfiguracji, ale chcemy się jej przyjrzeć i wprowadzić kilka zmian.

1. W nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator globalny swojej dzierżawy.

2. W menu centralnym kliknij przycisk **Nowy**, a następnie z listy **MARKETPLACE** wybierz opcję **Zabezpieczenia i tożsamość**. W bloku **Zabezpieczenia i tożsamość ** wybierz z listy **POLECANE APLIKACJE** opcję **Azure Information Protection**. W bloku **Azure Information Protection** kliknij przycisk **Utwórz**.

    Spowoduje to utworzenie bloku **Azure Information Protection**, dzięki czemu przy następnym logowaniu w witrynie portalu będzie można wybrać usługę z listy centralnej **Więcej usług**. 

    > [!TIP] 
    > Wybierz opcję **Przypnij do pulpitu nawigacyjnego**, aby utworzyć kafelek usługi **Azure Information Protection** na pulpicie nawigacyjnym, dzięki czemu można będzie pominąć krok przeglądania w poszukiwaniu usługi przy następnym zalogowaniu w witrynie portalu.

3.  W bloku Azure Information Protection kliknij pozycję **Globalne** i przejrzyj blok **Zasady: Globalne** zawierający domyślne zasady usługi Information Protection, które są tworzone automatycznie:
    
    - Etykiety klasyfikacji: **Osobiste**, **Publiczne**, **Wewnętrzne**, **Poufne** i **Tajne**. Przeczytaj etykietkę narzędzia każdej z nich, aby zrozumieć sposób korzystania z etykiet. Należy pamiętać, że etykieta **Tajne** zawiera dwie etykiety podrzędne: **Wszyscy pracownicy** i **Moja grupa**, które stanowią przykład klasyfikacji z podkategoriami.

    - Ustawienia domyślne zakładają, że etykiety **Wewnętrzne**, **Poufne** i **Tajne** mają skonfigurowane oznaczenia wizualne (takie jak stopka, nagłówek i znak wodny), lecz żadna z tych etykiet nie ma ustawionej ochrony: 
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zasada domyślna](../media/info-protect-policy-default-labels.png)
    
    Ponadto istnieją ustawienia globalne zasad, które nie są ustawione, tak więc nie jest wymagane, aby wszystkie dokumenty i wiadomości e-mail miały etykietę, brak jest etykiety domyślnej, użytkownicy nie muszą uzasadniać zmiany etykiet, a klient nie jest skonfigurowany pod kątem linku pomocy niestandardowej:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zasada domyślna](../media/info-protect-policy-default-settings.png)

## <a name="changing-the-global-settings-for-a-default-template-and-prompt-for-justification"></a>Zmiana ustawień globalnych szablonu domyślnego i monit o uzasadnienie

W naszym samouczku zmienimy kilka ustawień globalnych zasad, aby zobaczyć, jak działają:

1. Dla opcji **Wybierz etykietę domyślną** wybierz wartość na **Wewnętrzne**.

2. Dla opcji **Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę** wybierz wartość **Włączone**.

## <a name="configuring-a-label-for-protection-a-watermark-and-a-condition-to-prompt-for-classification"></a>Konfigurowanie etykiety ochrony, znaku wodnego oraz warunku monitowania o klasyfikację

Zmienimy teraz ustawienia jednej z etykiet, **Poufne**:

1. Kliknij etykietę **Poufne**. 
    
    W nowym bloku **Etykieta: Poufne** ukażą się ustawienia dostępne dla każdej etykiety. 

2. W bloku **Etykieta: Poufne** odszukaj sekcję **Ustawianie uprawnień do dokumentów i wiadomości e-mail oznaczonych tą etykietą**.

    Wybierz opcję **Ochrona**:
    
    ![Konfigurowanie ochrony dla etykiety usługi Azure Information Protection](../media/info-protect-protection-bar.png) 
    
    Spowoduje to otworzenie bloku **Uprawnienia**.
    
3. Upewnij się, że w bloku **Uprawnienia** jest zaznaczona opcja **Azure RMS** oraz że zaznaczono również opcję **Wybierz szablon**, a następnie kliknij pole listy rozwijanej i wybierz domyślny szablon ** \<nazwa organizacji> — Poufne**.     
    
    Na przykład jeśli nazwą firmy jest VanArsdel, Ltd, zobaczysz opcję **VanArsdel, Ltd — Poufne**, którą wybierzesz: 
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — ustawianie ochrony usługi Azure RMS](../media/step2-select-rms-template.png)
    
    Jeśli ten szablon domyślny usługi Azure Rights Management został wyłączony, wybierz szablon alternatywny. Jednak w przypadku wybrania szablonu działu upewnij się, czy Twoje konto znajduje się w jego zakresie.
    
4. Kliknij przycisk **Gotowe**, aby zapisać zmiany i zamknąć blok **Uprawnienia**.

5. Po powrocie do bloku **Etykieta: Poufne** zlokalizuj sekcję **Ustawianie oznaczenia wizualnego**:
    
    Dla ustawienia **Dokumenty z tą etykietą mają znak wodny** kliknij opcję **Włącz**, a następnie wpisz nazwę swojej organizacji w polu **Tekst**. W naszym przykładzie: **VanArsdel, Ltd**: 
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — ustawianie ochrony usługi Azure RMS](../media/step2-configure-watermark.png)
    
    Można zmienić rozmiar, kolor i układ znaków wodnych, ale chwilowo pozostawimy wartości domyślne tych ustawień.
    
6. Zlokalizuj sekcję **Konfigurowanie warunków automatycznego stosowania tej etykiety**:
    
    Kliknij przycisk **Dodaj nowy warunek** i następnie w bloku **Warunek** wykonaj następujące czynności:
    
    a. **Wybierz typ warunku**: zachowaj wartość domyślną **Wbudowany**.
    
    b. **Wybierz wbudowany**: z listy rozwijanej wybierz opcję **Numer karty kredytowej**.
    
    c. **Minimalna liczba wystąpień**: zachowaj ustawienie domyślne **1**.
    
    d. **Zliczaj tylko wystąpienia o unikatowych wartościach**: zachowaj wartość domyślną **Wł**.
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — konfigurowanie warunku karty kredytowej](../media/step2-configure-condition.png)
    
    Kliknij przycisk **Zapisz**, aby powrócić do bloku **Etykieta: Poufne**.

7. W bloku **Etykieta: Poufne** zobaczysz, że jako **NAZWA WARUNKU** jest wyświetlany **Numer karty kredytowej** z opcją **WYSTĄPIENIA** równą **1**:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — konfigurowanie warunku karty kredytowej](../media/step2-see-condition.png)

8. Dla opcji **Wybierz sposób stosowania tej etykiety**: zachowaj wartość domyślną **Zalecany** i nie zmieniaj domyślnej wskazówki zasad:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zalecana klasyfikacja](../media/step2-keep-recommended.png)

9. W polu **Wprowadź informacje dla celów wewnętrznych** wpisz **Tylko do testów**:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — wpisz uwagi](../media/step2-type-notes.png)

10. Kliknij przycisk **Zapisz** w tym bloku **Etykieta: Poufne**. Następnie ponownie kliknij przycisk **Zapisz** w bloku **Zasady: Globalne**.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — skonfigurowana zasada domyślna](../media/info-protect-policy-configured.png)

11. Aby po wprowadzeniu i zapisaniu zmian udostępnić je użytkownikom, w bloku początkowym **Azure Information Protection** należy kliknąć opcję **Opublikuj**, a następnie przycisk **Tak**, aby potwierdzić wybór.

Po zakończeniu tego samouczka możesz zamknąć portal Azure lub zostawić otwarty w celu wypróbowania innych opcji konfiguracji.

Skoro przyjrzeliśmy się już domyślnej zasadzie i wprowadziliśmy w niej kilka zmian, następnym krokiem jest zainstalowanie klienta usługi Azure Information Protection.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje o opcjach konfiguracji zasad|[Konfigurowanie zasad usługi Azure Information Protection](../deploy-use/configure-policy.md)|


>[!div class="step-by-step"]
[&#171; Krok 1](infoprotect-tutorial-step1.md)
[Krok 3 &#187;](infoprotect-tutorial-step3.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
