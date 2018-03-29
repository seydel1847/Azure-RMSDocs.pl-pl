---
title: Samouczek Szybki start — krok 2 — AIP
description: Krok 2 samouczka wprowadzającego, dzięki któremu można szybko wypróbować usługę Azure Information Protection — konfigurowanie zasad.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/29/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
ms.openlocfilehash: fecf9887937d3d17347e85759e2ed10b124ae8a1
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>Krok 2. Konfigurowanie i publikowanie zasad usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Usługa Azure Information Protection zawiera domyślną zasadę, której można użyć bez konfiguracji, ale chcemy się jej przyjrzeć i wprowadzić kilka zmian.

1. Kontynuowanie z [krok 1](infoprotect-tutorial-step1.md) i nadal w portalu Azure wybierz **globalne zasady** otworzyć **zasad: Global** bloku. Ten blok automatycznie otwiera dla kolejnych połączeń z usługą i wyświetla domyślne zasady ochrony informacji utworzony dla Twojej dzierżawy.

2. Spędzają na kilka minut zapoznawanie się z etykiet, które są wyświetlane:
    
    - Etykiety klasyfikacji: **Osobiste**, **Publiczne**, **Ogólne**, **Poufne** i **Wysoce poufne**. Rozwiń ostatnich dwóch etykiet można wyświetlić etykiety podrzędne, które zawierają przykłady klasyfikacji podkategoriami:
    
       > [!NOTE]
       > Twoje zasady domyślne mogą się nieco różnić od podanych w tym samouczku. Na przykład możesz mieć etykietę o nazwie **Wewnętrzne** zamiast **Ogólne** i **Tajne** zamiast **Wysoce poufne**. Być może nie masz etykiety podrzędne o nazwie **odbiorców tylko**, lub nie masz na wszystkich etykiety. Te zmiany są, ponieważ istnieją różne wersje domyślne zasady, w zależności od tego, kiedy został utworzony dla Twojej dzierżawy. Lub dokonałeś ich samodzielnej edycji przed uruchomieniem samouczka.
       > 
       > Jeśli Twoje domyślne zasady wyglądają inaczej, nadal możesz używać tego samouczka, ale należy pamiętać o tych zmianach, korzystając z poniższych instrukcji i obrazów. Jeśli chcesz zmodyfikować zasady domyślne tak, aby pasowały do bieżących zasad domyślnych, zobacz [Domyślne zasady usługi Azure Information Protection](../deploy-use/configure-policy-default.md).
    
    - Z konfiguracji domyślnej niektóre etykiety nie mają skonfigurowane oznaczenia wizualne. Znaczniki wizualne są stopka, nagłówek i znak wodny. W zależności od Twojego domyślne zasady niektóre etykiety może także mieć ustawionej ochrony. Przykład: 
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zasada domyślna](../media/info-protect-policy-default-labelsv2.png)
    
3. Możesz również sprawdzić, czy niektóre ustawienia zasad. Na przykład istnieje nie ustawiono etykiety domyślnej, dokumentów i wiadomości e-mail nie muszą mieć etykietę i użytkownicy nie muszą uzasadniać ich zmieniać etykiety:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zasada domyślna](../media/info-protect-policy-default-settings.png)

## <a name="changing-the-settings-for-a-default-label-and-prompt-for-justification"></a>Zmiana ustawień domyślnej etykiety i monit o uzasadnienie

W naszym samouczku zmienimy kilka z tych ustawień zasad, aby zobaczyć, jak działają:

1. Aby uzyskać **wybierz etykietę domyślną**, wybierz pozycję **ogólne**. 

    Jeśli nie masz tej etykiety, ponieważ masz starszą wersję zasad, wybierz **Wewnętrzne** jako równoważną etykietę.

2. Aby uzyskać **użytkownik musi podać uzasadnienie, aby ustawić niższy etykiety klasyfikacji, Usuń etykietę lub usuń ochronę**, ustaw tę opcję, **na**.

3. Ponadto Znajdź ustawienie **udostępnić użytkownikom opcję uprawnień niestandardowych**. Jeśli wartość jest ustawiona na **poza**, aby zmienić **na**.
    
    Nie może być konieczne ustawienie to można zmienić, ponieważ wartość domyślna zależy od daty uzyskać subskrypcję. Uprawnienia niestandardowe w dalszej części tego samouczka zostanie wykorzystany do udziału chronionego dokumentu z użytkownikiem, który określisz po kliknięciu prawym przyciskiem myszy plik w Eksploratorze plików.

## <a name="creating-a-new-label-for-protection-visual-markers-and-a-condition-to-prompt-for-classification"></a>Tworzenie nowej etykiety dla ochrony, znaczniki wizualne i warunku z monitem o klasyfikacji

Teraz utworzymy nową etykietę podrzędną dla **poufne**.

1. Kliknij prawym przyciskiem myszy **poufne** etykiety, a następnie wybierz **Dodaj etykietę podrzędną**.
    
    Jeśli nie masz etykietę o nazwie **poufne**, można wybrać inną etykietę, lub można zamiast tego utworzyć nowe etykiety i nadal czynności opisane w samouczku z niewielkie różnice.

2. Na **etykietę podrzędną** bloku, określ nazwę etykiety **Finance** i Dodaj następujący opis: **poufnych danych, który zawiera informacje finansowe, który jest ograniczony do pracowników tylko**.
    
    Ten tekst opisuje sposób wybranej etykiety jest przeznaczona do użycia, i jest widoczne dla użytkowników jako etykietka narzędzia, aby pomóc zdecydować, które etykietę do wybrania.

3. W sekcji **Ustaw uprawnienia do dokumentów i wiadomości e-mail zawierających tę etykietę** wybierz pozycję **Chroń**, a następnie **Ochrona**:
    
    ![Ochrony skonfigurowane dla etykiety usługi Azure Information Protection](../media/info-protect-protection-bar-configured.png) 
    
4. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone. Ta opcja używa usługi Azure Rights Management do ochrony dokumentów i wiadomości e-mail. Upewnij się, że **Ustaw uprawnienia** jest zaznaczony. Następnie wybierz **dodać uprawnienia**.

5. Na **dodać uprawnienia** bloku, wybierz opcję **Dodaj \<nazwa organizacji > — wszystkie elementy członkowskie**. Na przykład jeśli nazwą firmy jest VanArsdel, Ltd, zobacz następującą opcję, aby wybrać:
    
    ![Udzielanie wszystkie elementy członkowskie ochrony uprawnień dla etykiety usługi Azure Information Protection](../media/info-protect-protection-all-members.png) 
    
    Ta opcja automatycznie wybiera wszystkich użytkowników w organizacji, którzy mogą mieć uprawnienia. Jednak widać z innych opcji, które można przeglądać i wyszukiwanie grup lub użytkowników w dzierżawie. Lub, w przypadku zaznaczenia pola wyboru **wprowadź szczegóły** opcji można określić adresy e-mail poszczególnych lub nawet dla wszystkich użytkowników z innej organizacji.

6. Uprawnienia, wybierz **Weryfikacja** wstępnie zdefiniowane opcje. Zobacz, jak ten poziom uprawnień automatycznie udziela niektóre uprawnienia na liście, ale nie wszystkie uprawnienia:
    
    ![Udzielanie uprawnień ochrony Współautor etykiety usługi Azure Information Protection](../media/info-protect-protection-reviewer.png)
    
    Można wybrać różne poziomy uprawnień lub Określ prawa użytkowania poszczególnych przy użyciu **niestandardowy** opcji. Zachowując w tym samouczku **Weryfikacja** opcji. Można później Poeksperymentuj z innymi uprawnieniami i jak ich ograniczać określeni użytkownicy czynności z chronionego dokumentu lub wiadomości e-mail do odczytu.

7. Kliknij przycisk **OK** zamknąć to **dodać uprawnienia** bloku i zostanie wyświetlony jak **ochrony** bloku jest aktualizowana w celu uwzględnienia konfiguracji. Przykład:
    
     ![Blok ochrony konfiguracji uprawnień dla etykiety usługi Azure Information Protection](../media/info-protect-protection-configured.png)
    
    W przypadku wybrania **dodać uprawnienia**, spowoduje to otwarcie **dodać uprawnienia** bloku ponownie, dzięki czemu można dodawać kolejnych użytkowników i przyznano im różne uprawnienia. Na przykład udostępnić tylko widok dla określonej grupy. Ale w tym samouczku, firma Microsoft będzie jeden zestaw uprawnień dla wszystkich użytkowników.

8. Przejrzyj i Zachowaj wartości domyślne dla wygaśnięcia zawartości i dostęp w trybie offline, a następnie kliknij **OK** Aby zapisać i zamknąć to **ochrony** bloku.

8. Ponownie **etykietę podrzędną** bloku zlokalizować **Ustaw oznaczenie wizualne** sekcji:
    
    Dla **dokumenty oznaczone tą etykietą mają stopkę** ustawienie, kliknij przycisk **na**, a następnie **tekst** wpisz **sklasyfikowanych jako poufne** . 
    
    Dla ustawienia **Dokumenty z tą etykietą mają znak wodny** kliknij opcję **Włącz**, a następnie wpisz nazwę swojej organizacji w polu **Tekst**. Na przykład **VanArsdel, Ltd** 
    
    Mimo że można zmienić wygląd dla tych oznaczeń wizualnych, pozostanie te ustawienia wartości domyślne dla teraz.
    
9. Zlokalizuj sekcję **Konfigurowanie warunków automatycznego stosowania tej etykiety**:
    
    Kliknij przycisk **Dodaj nowy warunek** , a następnie na **warunku** blok, wykonaj następujące czynności:
    
    a. **Wybierz typ warunku**: Zachowaj ustawienie domyślne **typów informacji**.
    
    b. W **wybierz typy informacji** pole wyszukiwania: typ **numer karty kredytowej**. w wynikach wyszukiwania wybierz **numer karty kredytowej**.
    
    c. **Minimalna liczba wystąpień**: zachowaj ustawienie domyślne **1**.
    
    d. **Zliczaj tylko wystąpienia o unikatowych wartościach**: zachowaj wartość domyślną **Wł**.
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — konfigurowanie warunku karty kredytowej](../media/step2-configure-condition.png)
    
    Kliknij przycisk **zapisać** aby powrócić do **etykietę podrzędną** bloku.

10. Na **etykietę podrzędną** bloku, który zobacz **numer karty kredytowej** jest wyświetlany jako **nazwa WARUNKU**, z **1**  **WYSTĄPIENIA**:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — konfigurowanie warunku karty kredytowej](../media/step2-see-condition.png)

11. Dla **wybierz sposób zastosowania tej etykiety**: Zachowaj ustawienie domyślne **zalecane**, a nie powoduje zmiany tip zasady domyślne. 

12. W polu **Wprowadź informacje dla celów wewnętrznych** wpisz **Tylko do testów**.

13. Kliknij przycisk **zapisać** na tym **etykietę podrzędną** bloku. Następnie ponownie kliknij przycisk **Zapisz** w bloku **Zasady: Globalne**.
    
    Teraz widoczne z nową etykietę podrzędną, która jest skonfigurowana pod kątem oznaczeń wizualnych i ochrony. Przykład:

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — skonfigurowana zasada domyślna](../media/info-protect-policy-configuredv2.png)
    
    Widoczny jest również, czy ustawienia zostały skonfigurowane z zmiany dla etykiety domyślnej oraz uzasadnienie:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — skonfigurowane ustawienia](../media/info-protect-settings-configuredv2.png)
    
14. Wprowadziliśmy naszych zmian i zapisaniu, chcemy udostępnić je użytkownikom, więc klikamy **publikowania**i kliknij przycisk **tak** o potwierdzenie.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — publikowanie skonfigurowanych zasad](../media/info-protect-publish.png)

Po zakończeniu tego samouczka możesz zamknąć portal Azure lub zostawić otwarty w celu wypróbowania innych opcji konfiguracji.

Skoro przyjrzeliśmy się już domyślnej zasadzie i wprowadziliśmy w niej kilka zmian, następnym krokiem jest zainstalowanie klienta usługi Azure Information Protection.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Domyślne zasady i różnych wersji — informacje|[Domyślne zasady usługi Azure Information Protection](../deploy-use/configure-policy-default.md)|
|Konfigurowania zasad|[Konfigurowanie zasad usługi Azure Information Protection](../deploy-use/configure-policy.md)|
|Szczegółowe instrukcje dotyczące konfigurowania etykiety dla ochrony|[Konfigurowanie etykiety dla ochrony usługi Rights Management](../deploy-use/configure-policy-protection.md)|
|Szczegółowe informacje na temat uprawnień|[Konfigurowanie praw użytkowania dla usługi Azure Rights Management](../deploy-use/configure-usage-rights.md)|



>[!div class="step-by-step"]
[&#171; Krok 1](infoprotect-tutorial-step1.md)
[Krok 3 &#187;](infoprotect-tutorial-step3.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]