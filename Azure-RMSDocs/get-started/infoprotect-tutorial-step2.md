---
title: Samouczek Szybki start krok 1 | Azure Information Protection
description: "Krok 2 samouczka wprowadzającego, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection w swojej organizacji. Wystarczy około 30 minut."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: bce1682624b040545d30ca1cc426e4e2f8c38018
ms.openlocfilehash: 7ba1566a81ca9a3ac45f340f69d3c9e933f015ff


---

# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>Krok 2. Konfigurowanie i publikowanie zasad usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Usługa Azure Information Protection zawiera domyślną zasadę, której można użyć bez konfiguracji, ale chcemy się jej przyjrzeć i wprowadzić kilka zmian.

1. W nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator globalny swojej dzierżawy.

2. W menu centralnym kliknij przycisk **Nowy**, a następnie z listy **MARKETPLACE** wybierz opcję **Zabezpieczenia i tożsamość**. W bloku **Zabezpieczenia i tożsamość ** wybierz z listy **POLECANE APLIKACJE** opcję **Azure Information Protection**. W bloku **Azure Information Protection** kliknij przycisk **Utwórz**.

    Spowoduje to utworzenie bloku **Azure Information Protection**, dzięki czemu przy następnym logowaniu w witrynie portalu będzie można wybrać usługę z listy centralnej **Więcej usług**. 

    > [!TIP] 
    > Wybierz opcję **Przypnij do pulpitu nawigacyjnego**, aby utworzyć kafelek usługi **Azure Information Protection** na pulpicie nawigacyjnym, dzięki czemu można będzie pominąć krok przeglądania w poszukiwaniu usługi przy następnym zalogowaniu w witrynie portalu.

3.  Eksploruj główny blok **Azure Information Protection** przedstawiający domyślne zasady usługi Information Protection, które są tworzone automatycznie:
    
    - Etykiety klasyfikacji: **Osobiste**, **Publiczne**, **Wewnętrzne**, **Poufne** i **Tajne**. Przeczytaj etykietkę narzędzia każdej z nich, aby zrozumieć sposób korzystania z etykiet. Należy pamiętać, że etykieta **Tajne** zawiera dwie etykiety podrzędne: **Wszyscy pracownicy** i **Moja grupa**, które stanowią przykład klasyfikacji z podkategoriami.

    - Z ustawieniami domyślnymi etykiety **Wewnętrzne**, **Poufne** i **Tajne** mają skonfigurowane oznaczenia wizualne (takie jak stopka, nagłówek i znak wodny), lecz żadna z tych etykiet nie ma ustawionej ochrony. Ponadto te cztery ustawienia globalne nie są ustawione, tak więc nie jest wymagane, aby dokumenty i wiadomości e-mail miały etykietę, brak jest etykiety domyślnej, użytkownicy nie muszą uzasadniać zmiany etykiet, a klient nie jest skonfigurowany dla linku pomocy niestandardowej.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zasada domyślna](../media/info-protect-policy.png)

## <a name="changing-the-global-settings-for-a-default-template-and-prompt-for-justification"></a>Zmiana ustawień globalnych szablonu domyślnego i monit o uzasadnienie

W naszym samouczku zmienimy kilka ustawień globalnych, aby zobaczyć, jak działają:

1. Dla opcji **Wybierz etykietę domyślną** wybierz wartość na **Wewnętrzne**.

2. Dla opcji **Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę** wybierz wartość **Włączone**.

## <a name="configuring-a-label-for-protection-a-watermark-and-a-condition-to-prompt-for-classification"></a>Konfigurowanie etykiety ochrony, znaku wodnego oraz warunku monitowania o klasyfikację

Zmienimy teraz ustawienia jednej z etykiet, **Poufne**:

1. Kliknij etykietę **Poufne**. 
    
    W nowym bloku **Etykieta: Poufne** ukażą się ustawienia dostępne dla każdej etykiety. 

2. W bloku **Etykieta: poufne** odszukaj sekcję **Ustawianie szablonu usług RMS w celu ochrony dokumentów i wiadomości e-mail oznaczonych tą etykietą**:
    
    Dla opcji **Wybierz szablon usług RMS z** zachowaj ustawienia domyślne **Azure RMS**. Następnie dla opcji **Wybierz szablon usług RMS** kliknij menu rozwijane i wybierz szablon domyślny **\<nazwa organizacji > Poufne**. 
    
    Na przykład jeśli nazwą firmy jest VanArsdel, Ltd, zobaczysz opcję **VanArsdel, Ltd — Poufne**, którą wybierzesz: 
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — ustawianie ochrony usługi Azure RMS](../media/step2-select-rms-template.png)
    
    Jeśli ten szablon domyślny usługi Azure Rights Management został wyłączony, wybierz szablon alternatywny. Jednak w przypadku wybrania szablonu działu upewnij się, czy Twoje konto znajduje się w jego zakresie.
    
3. Zlokalizuj sekcję **Ustaw oznaczanie wizualne**:
    
    Dla ustawienia **Dokumenty z tą etykietą mają znak wodny** kliknij opcję **Włącz**, a następnie wpisz nazwę swojej organizacji w polu **Tekst**. W naszym przykładzie: **VanArsdel, Ltd**: 
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — ustawianie ochrony usługi Azure RMS](../media/step2-configure-watermark.png)
    
    Można zmienić rozmiar, kolor i układ znaków wodnych, ale chwilowo pozostawimy wartości domyślne tych ustawień.
    
4. Zlokalizuj sekcję **Konfigurowanie warunków automatycznego stosowania tej etykiety**:
    
    Kliknij przycisk **Dodaj nowy warunek** i następnie w bloku **Warunek** wykonaj następujące czynności:
    
    a. **Wybierz typ warunku**: zachowaj wartość domyślną **Wbudowany**.
    
    b. **Wybierz wbudowany**: z listy rozwijanej wybierz opcję **Numer karty kredytowej**.
    
    c. **Minimalna liczba wystąpień**: zachowaj ustawienie domyślne **1**.
    
    d. **Zliczaj tylko wystąpienia o unikatowych wartościach**: zachowaj wartość domyślną **Wł**.
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — konfigurowanie warunku karty kredytowej](../media/step2-configure-condition.png)
    
    Kliknij przycisk **Zapisz**, aby powrócić do bloku **Etykieta: Poufne**.

5. W bloku **Etykieta: Poufne** zobaczysz, że jako **NAZWA WARUNKU** jest wyświetlany **Numer karty kredytowej** z opcją **WYSTĄPIENIA** równą **1**:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — konfigurowanie warunku karty kredytowej](../media/step2-see-condition.png)

6. Dla opcji **Wybierz sposób stosowania tej etykiety**: zachowaj wartość domyślną **Zalecany** i nie zmieniaj domyślnej wskazówki zasad:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zalecana klasyfikacja](../media/step2-keep-recommended.png)

7. W polu **Wprowadź informacje dla celów wewnętrznych** wpisz **Tylko do testów**:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — wpisz uwagi](../media/step2-type-notes.png)

8. Kliknij przycisk **Zapisz** w tym bloku **Etykieta: Poufne**. Następnie w głównym bloku **Azure Information Protection** kliknij przycisk **Zapisz**.

9. Po wprowadzeniu i zapisaniu zmian chcemy udostępnić je użytkownikom, więc klikamy **Opublikuj**, a następnie klikamy przycisk **Tak**, aby potwierdzić.

![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — skonfigurowana zasada domyślna](../media/info-protect-policy-configured.png)

Po zakończeniu tego samouczka możesz zamknąć portal Azure lub zostawić otwarty w celu wypróbowania innych opcji konfiguracji.

Skoro przyjrzeliśmy się już domyślnej zasadzie i wprowadziliśmy w niej kilka zmian, następnym krokiem jest zainstalowanie klienta usługi Azure Information Protection oraz aplikacji RMS sharing.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje o opcjach konfiguracji zasad|[Konfigurowanie zasad usługi Azure Information Protection](../deploy-use/configure-policy.md)|


>[!div class="step-by-step"]
[&#171; Krok 1](infoprotect-tutorial-step1.md)
[Krok 3 &#187;](infoprotect-tutorial-step3.md)


<!--HONumber=Nov16_HO3-->


