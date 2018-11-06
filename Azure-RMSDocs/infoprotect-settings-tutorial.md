---
title: Samouczek — Konfigurowanie ustawień zasad usługi Azure Information Protection ułatwia klasyfikowanie, dokumentów i wiadomości e-mail
description: Samouczek wprowadzający, który przeprowadzi Cię przez konfigurację ustawień zasad usługi Azure Information Protection ułatwia klasyfikowanie dokumentów i wiadomości e-mail w organizacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: tutorial
ms.service: information-protection
ms.openlocfilehash: ead65d9fef1b6c4f0087757e044caccee14805df
ms.sourcegitcommit: 80de8762953bdea2553c48b02259cd107d0c71dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51027220"
---
# <a name="tutorial-configure-azure-information-protection-policy-settings-that-work-together"></a>Samouczek: Konfigurowanie ustawień zasad usługi Azure Information Protection, które współpracują ze sobą

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

W tym samouczku dowiesz się, jak:
> [!div class="checklist"]
> * Konfigurowanie ustawień zasad, które współpracują ze sobą
> * Zobacz ustawienia w działaniu

Zamiast polegać na użytkowników, aby ręcznie oznaczać swoje dokumenty i wiadomości e-mail, można użyć ustawień zasad w celu:

- Upewnij się, podstawowy poziom klasyfikacji dla nowych i edytowane zawartości

- Poinformuj użytkowników o etykiety i ułatwiają stosowanie odnoszących się prawidłowa etykieta

W tym samouczku można zakończyć w ciągu około 15 minut.

## <a name="prerequisites"></a>Wymagania wstępne 

Do ukończenia tego samouczka, potrzebne są:

1. Subskrypcja, która obejmuje usługi Azure Information Protection Plan 2.
    
    Jeśli nie masz subskrypcję obejmującą tego planu, możesz utworzyć [bezpłatne](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) konta dla Twojej organizacji.

2. Został dodany do bloku usługi Azure Information Protection do witryny Azure portal i potwierdza, że aktywacji usługi ochrony.

    Jeśli potrzebujesz pomocy przy użyciu tych akcji, zobacz [Szybki Start: Dodawanie usługi Azure Information Protection do witryny Azure portal i Wyświetl zasady](quickstart-viewpolicy.md)

3. Klient usługi Azure Information Protection jest zainstalowany na tym komputerze. 
    
    Aby zainstalować klienta, przejdź do [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) i Pobierz **AzInfoProtection.exe** ze strony usługi Azure Information Protection.

4. Komputer z systemem Windows (co najmniej Windows 7 z dodatkiem Service Pack 1), a na tym komputerze, użytkownik jest zalogowany do aplikacji pakietu Office z jednej z następujących kategorii:
    
    - Usługa Office 365 z aplikacji pakietu Office 2016 (minimalna wersja 1805, kompilacja 9330.2078). Aby użyć tej opcji, Twoje konto musi mieć przypisaną licencję usługi Azure Rights Management. Ta licencja jest dołączone do subskrypcji usługi Azure Information Protection.
    
    - Usługi Office 365 Proplus z wersji aplikacji 2016 lub 2013 (Instalacja kliknij polecenie do uruchomienia lub opartych na Instalatorze Windows).
    
    - Office Professional Plus 2016.
    
    - Office Professional Plus 2013 z dodatkiem Service Pack 1.
    
    - Office Professional Plus 2010 z dodatkiem Service Pack 2.

Aby uzyskać pełną listę wymagań wstępnych do używania usługi Azure Information Protection, zobacz [wymagania dotyczące usługi Azure Information Protection](requirements.md).

Zaczynamy!

## <a name="edit-the-azure-information-protection-policy"></a>Edytowanie zasad usługi Azure Information Protection

Zamiast polegać na użytkowników, aby ręcznie oznaczać swoje dokumenty i wiadomości e-mail, można użyć niektórych ustawień zasad, aby zapewnić podstawowy poziom klasyfikacji. 

Przy użyciu portalu Azure, firma Microsoft będzie edytowanie zasad globalnych, aby zmienić ustawienia zasad dla wszystkich użytkowników.

1. Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](https://portal.azure.com). Następnie przejdź do **usługi Azure Information Protection**. 
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Wybierz **klasyfikacje** > **zasady** > **Global** otworzyć **zasady: globalne** bloku. 

3. Znajdź ustawienia zasad po etykietach, w **Konfiguruj ustawienia wyświetlania i Zastosuj Information Protection, użytkownicy końcowi** sekcji. Ustawienia może mieć różne wartości w tych pokazano:
    
    ![Samouczek usługi Azure Information Protection — ustawienia domyślne](./media/defaultsettings-aip.png)

4. Zmienić ustawienia, aby dopasować wartość w poniższej tabeli. Zanotuj ustawienia, które zmieniają się w przypadku, gdy chcesz zmienić je ponownie ponownie po ukończeniu tego samouczka. 

    |Ustawienie|Wartość|Informacje|
    |-------|-----|-----|
    |**Wybierz etykietę domyślną**|**Ogólne**|Jeśli użytkownik nie ma etykietę o nazwie **ogólne**, wybierz inną etykietę z listy rozwijanej. Bez etykiety dokumentów i wiadomości e-mail mają tę etykietę stosowane automatycznie, jako podstawowy klasyfikacji. Jednak użytkownicy mogą zmienić wybranej etykiety do innego.|
    |**Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**|**On**|To ustawienie jest często nazywany obowiązkowego etykietowania, ponieważ jego uniemożliwia użytkownikom zapisywanie dokumentów i wysyłania wiadomości e-mail, które są bez etykiety. Wraz z etykiety domyślnej dokumentów i wiadomości e-mail będzie mieć etykietę domyślną, który został ustawiony lub etykiety, która wybiera.
    |**W przypadku wiadomości e-mail z załącznikami Zastosuj etykietę, która odpowiada najwyższej klasyfikacji tych załączników**|**Zalecane**|To ustawienie monituje użytkowników, aby wybrać etykietę wyższego poziomu klasyfikacji wiadomości e-mail, gdy ich Dołącz dokumenty zawierające klauzulę wyższą niż etykiety z domyślną.
    |**Wyświetl pasek usługi Information Protection w aplikacjach pakietu Office**|**On**|Wyświetlanie paska usługi Information Protection ułatwia użytkownikom wyświetlić i zmienić domyślną etykietę.
    
    Ustawienia powinna teraz wyglądać następująco:
    
    ![Samouczek usługi Azure Information Protection — zmienione ustawienia domyślne](./media/defaultsettings-aip-changed.png)

5. Wybierz **Zapisz** na tym **zasady: globalne** bloku i jeśli zostanie wyświetlony monit o potwierdzenie tej akcji, wybierz opcję **OK**. 

## <a name="see-your-policy-settings-in-action"></a>Zobacz ustawienia zasad w działaniu 

W tym samouczku użyjemy Word i Outlook Aby zobaczyć zmiany zasad w działaniu. Jeśli te aplikacje zostały już załadowane przed zmianą ustawień zasad, należy ponownie uruchomić ich pobranie zmian.

### <a name="default-label-and-the-information-protection-bar"></a>Etykiety domyślnej i pasek usługi Information Protection

Otwórz nowy dokument programu Word. Zobaczysz, że dokument jest automatycznie oznaczony etykietą **ogólne** zamiast polegać na użytkowników o wybranie etykiety. 

Za pomocą paska usługi Information Protection wyświetlane i pokazujący dostępne etykiety jest łatwe dla użytkowników wyświetlić aktualnie wybranej etykiety, a następnie ją zmienić, gdy jest etykiety domyślnej:

![Samouczek usługi Azure Information Protection — nowy dokument z ustawieniem etykiety domyślnej](./media/defaultlabel-word.png)

Zamiast zmieniać etykietę, Zamknij na pasku Information Protection do porównania w środowisku, jeśli nie jest wyświetlany pasek:

![Samouczek usługi Azure Information Protection — nowy dokument z ustawieniem etykiety domyślnej](./media/infoprotect-bar-close.png)

**Ogólne** etykieta jest nadal zaznaczona, ale jest znacznie mniej oczywista. Również jest mniej oczywistych, jak wybrać inną etykietę. Aby to zrobić, użytkownicy muszą wybrać **Chroń** przycisku:

![Samouczek usługi Azure Information Protection — ochrona zaznaczonego przycisku](./media/infoprotect-protectbutton-pulldown.png)

Teraz, z menu rozwijanego zobaczysz, że **ogólne** etykieta jest zaznaczona, ponieważ ma ona znacznik wyboru obok niego. Aby zmienić ustawienia aktualnie wybranej etykiety, użytkownicy mogą wybrać inną etykietę z listy. W przypadku nowych do etykietowania użytkownicy są prawdopodobnie nie należy pamiętać o zaznaczeniu **Chroń** każdym razem przycisk. One również może nie należy pamiętać, że użytkownik może wybrać inną etykietę.

Aby wyświetlić paska usługi Information Protection ponownie, wybierz **Pokaż pasek** z menu rozwijanego.

> [!TIP]
> Można wybrać różne etykiety domyślne dla programu Outlook, konfigurując [Zaawansowane ustawienia klienta](./rms-client/client-admin-guide-customizations.md#set-a-different-default-label-for-outlook).

### <a name="mandatory-labeling"></a>Obowiązkowego etykietowania

Możesz zmienić obecnie wybranym parametrem **ogólne** etykiety na inną etykietę, ale nie można go usunąć. Ponieważ zmieniliśmy **wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę** ustawienie **na**, **Usuń etykietę** ikona nie jest dostępna na pasku usługi Information Protection. 

Jeśli to ustawienie nie zostało zmienione, pasek usługi Information Protection pokazuje tę ikonę:

![Samouczek usługi Azure Information Protection — ochrona zaznaczonego przycisku](./media/infoprotect-deletelabel-icon.png)

Razem z ustawieniem etykiety domyślnej obowiązkowego etykietowania gwarantuje, że nowe i edytowane dokumenty (i wiadomości e-mail) podstawowej klasyfikacji wybrane. 

Jeśli nie zostało ustawimy za pomocą obowiązkowego etykietowania ustawienia etykiety domyślnej, użytkownicy zawsze są monitowani o wybranie etykiety, podczas zapisywania dokumentu bez etykiety lub Wyślij wiadomość e-mail bez etykiety. Dla wielu użytkowników monity ciągłe mogą być irytujące i również spowodować etykietowania mniej dokładne. Musiały zostać wyświetlony monit o wybranie etykiety, po ich zakończeniu pracy nad dokumentem lub wiadomości e-mail przerywa działanie swoich przepływów pracy i jest następnie możliwość przesłania dla nich losowo wybrać wszelkie etykiety, dzięki czemu mogą przenosić na kolejną rzeczą muszą zrobić.

### <a name="recommendations-for-emails-with-attachments"></a>Zalecenia dotyczące wiadomości e-mail z załącznikami

Otwórz dokument programu Word, wybierz etykietę, która zawiera klauzulę wyższą niż **ogólne**. Na przykład, jedną z etykiet podrzędnych, w obszarze **poufne**, takich jak **poufne — każdy (niechronione)**. Zapisz dokument lokalnie i nadać mu dowolną nazwę. 

Uruchom program Outlook i Utwórz nową wiadomość e-mail. Tak samo, jak widzieliśmy wyrazami nowych wiadomości e-mail jest automatycznie oznaczony etykietą **ogólne** i jest wyświetlany pasek usługi Information Protection.

Dodaj dokument programu Word, który po prostu oznaczone jako załącznik do wiadomości e-mail. Zostanie wyświetlony monit, Zmiana etykiety wiadomości e-mail do **poufne** etykietę, która odpowiada załącznik programu Word. Można zaakceptować zalecenie lub odrzucić je:

![Samouczek usługi Azure Information Protection — Monituj o relabel wiadomości e-mail odpowiednio oznaczone załącznika](./media/infoprotect-matchemail-label.png)

Jeśli klikniesz **Odrzuć**, nie ma zastosowania nowej etykiety, ale Zobacz, jak adres e-mail jest nadal oznaczony etykiety domyślnej, który został skonfigurowany, **ogólne**. Dostępne etykiety są nadal widoczny, aby wybrać jako alternatywa.

Jeśli wybierzesz **teraz zmienić**, adres e-mail jest relabeled do **poufne** etykietę podrzędną. Jednak użytkownicy nadal mogą zmieniać etykietę przed wysłaniem wiadomości e-mail, wybierając pozycję Edytuj etykietę:

![Samouczek usługi Azure Information Protection — Monituj o relabel wiadomości e-mail odpowiednio oznaczone załącznika](./media/infoprotect-editlabel-icon.png)

Pasek usługi Information Protection, a następnie ponownie wyświetla użytkownikowi wybrać alternatywny etykietę.

Ponieważ etykieta jest zaznaczony przed wysłaniem wiadomości e-mail, nie ma potrzeby celu rzeczywistego wysłania wiadomości e-mail, aby zobaczyć, jak działa to ustawienie zasad. Możesz zamknąć wiadomości e-mail bez wysyłania i zapisanie go.

Jednak należy powtórzyć tego ćwiczenia, ale również dołączyć dokumentu zawierającego wyższej klasyfikacji (etykiety podrzędnej z **wysoce poufne** etykiety). Następnie zobaczysz, jak zmieni się na zastosować wyższy etykiety klasyfikacji.

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Jeśli nie chcesz zachować zmiany wprowadzone w ramach tego samouczka, wykonaj następujące czynności:

1. Wybierz **klasyfikacje** > **zasady** > **Global** otworzyć **zasady: globalne** bloku.

2. Powrócić do ich oryginalnych wartości, które miały Zanotuj ustawień zasad, a następnie wybierz **Zapisz**.

Ponowne uruchomienie aplikacji Word i Outlook, aby pobrać te zmiany.

## <a name="next-steps"></a>Kolejne kroki

Aby uzyskać więcej informacji dotyczących edytowania ustawień zasad usługi Azure Information Protection ma zobacz [sposób konfigurowania ustawień zasad usługi Azure Information Protection](configure-policy-settings.md).

Ustawienia zasad, które zmieniliśmy brały udział w upewnij się, podstawowy poziom klasyfikacji, a także zachęcić użytkowników do wybierz odpowiednią etykietę. Następnym krokiem jest rozszerzyć tej strategii, inspekcja zawartości dokumentów i wiadomości e-mail, a następnie zalecania lub automatycznego stosowania odpowiednich etykiety. W tym celu konfigurowania etykiety dla warunków. Aby dowiedzieć się więcej, zobacz [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection](configure-policy-classification.md).
