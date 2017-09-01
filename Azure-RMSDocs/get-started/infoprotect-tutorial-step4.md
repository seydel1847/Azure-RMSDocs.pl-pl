---
title: "Samouczek Szybki start — krok 4 — AIP"
description: "Krok 4 samouczka wprowadzającego, dzięki któremu można szybko wypróbować usługę Azure Information Protection — prezentacja działania funkcji etykietowania i ochrony."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
ms.openlocfilehash: 3a5e3fc018bb19480a52729345ad2ac6d4c851be
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2017
---
# <a name="step-4-see-classification-labeling-and-protection-in-action"></a>Krok 4. Prezentacja działania funkcji klasyfikacji, etykietowania i ochrony 

>*Dotyczy: Azure Information Protection*

Po otwarciu dokumentu programu Word z zainstalowanym klientem usługi Azure Information Protection możesz sprawdzić, jak łatwo rozpocząć etykietowanie i chronienie dokumentu za pomocą skonfigurowanej zasady.

Klasyfikacja i ochrona zachodzą podczas zapisywania dokumentu, ale zanim do tego przejdziemy, użyjemy naszego niezapisanego dokumentu, aby zobaczyć, jak w łatwy sposób stosować i zmieniać etykiety.

## <a name="to-manually-change-our-default-label"></a>Aby ręcznie zmienić naszą domyślną etykietę

Na pasku usługi Information Protection wybierz ostatnią etykietę, a wówczas zostaną wyświetlone etykiety podrzędne:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — wybieranie etykiety podrzędnej](../media/info-protect-sub-labelsv2.png)

Wybierz jedną z tych etykiet podrzędnych, a tym samym etykietę dla tego dokumentu, a wówczas inne etykiety nie będą już na pasku wyświetlane. Wartość opcji **Ważność** zostanie zmieniona, tak aby pokazać nazwę etykiety i etykiety podrzędnej, oraz nastąpi analogiczna zmiana koloru etykiety. Na przykład:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — wybrano etykietę podrzędną](../media/info-protect-sub-label-selectedv2.png)

Na pasku usługi Information Protection kliknij ikonę **Edytuj etykietę** obok aktualnie wybranej wartości etykiety:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — ikona Edytuj etykietę](../media/info-protect-edit-label-selectedv2.png)

Spowoduje to ponowne wyświetlenie dostępnych etykiet.

Teraz wybierz pierwszą etykietę **Osobiste**. Z powodu wybrania etykiety o klasyfikacji niższej niż etykieta wybrana wcześniej dla tego dokumentu zostanie wyświetlony monit o uzasadnienie, dlaczego obniżany jest poziom klasyfikacji:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — monit o uzasadnienie potwierdzenia obniżenia](../media/info-protect-lower-justification.png)

Wybierz opcję **Poprzednia etykieta już nie obowiązuje** i kliknij przycisk **Potwierdź**. Wartość opcji **Ważność** zostanie zmieniona na **Osobiste** i pozostałe etykiety zostaną ponownie ukryte.

## <a name="to-remove-the-classification-completely"></a>Aby całkowicie usunąć klasyfikację

Na pasku o nazwie Information Protection kliknij ponownie ikonę **Edytuj etykietę**. Zamiast wybierać jedną z etykiet kliknij ikonę **Usuń etykietę**:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — ikona usuwania](../media/delete-icon-from-personalv2.png)

Tym razem po wyświetleniu monitu wpisz komentarz o treści „Ten dokument nie wymaga klasyfikacji” i kliknij przycisk **Potwierdź**.  

Zostanie wyświetlony **czułości** wartością wyświetlaną **Nieustawione**, która jest, co użytkownicy widzą początkowo przed ustawieniem etykiety domyślnej.

## <a name="to-see-a-recommendation-prompt-for-labeling-and-automatic-protection"></a>Aby wyświetlić monit zalecający etykietowanie i automatyczne włączanie ochrony

1. W dokumencie programu Word wpisz poprawny numer karty kredytowej, na przykład: **4242-4242-4242-4242**. 

2. Zapisz lokalnie, dokument z żadną nazwą pliku. 

3. Teraz zostanie wyświetlony monit o zastosowanie etykiety, która została skonfigurowana do ochrony w przypadku wykrycia numerów kart kredytowych. Jeśli nie zgadzamy się z zaleceniem, nasze ustawienie zasad umożliwia nam jego odrzucenie po wybraniu pozycji **Odrzuć**. Przekazanie zalecenia, jednocześnie umożliwiając użytkownikowi zastąpienie go, pomaga zmniejszyć liczbę fałszywych alarmów podczas korzystania z automatycznej klasyfikacji. W przypadku tego samouczka kliknij pozycję **Zmień teraz**.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — monit z zaleceniem klasyfikacji](../media/change-nowv2.png)

    Oprócz dokument teraz zastosowana naszą skonfigurowanych etykietę (na przykład **poufne \ Finance**), natychmiast zobaczyć znak wodny z nazwą organizacji na stronie i w stopce  **Sklasyfikowanych jako poufne** jest również zastosowane. 

    Dokument jest również chroniony za pomocą uprawnienia określone dla tej etykiety. Można potwierdzić, że dokument jest chroniony przez kliknięcie przycisku **pliku** karcie i wyświetlić informacje o **ochrona dokumentu**. Zobaczysz, że dokument jest chroniony przez **poufne \ Finance** i opis etykiety. 
    
    Ze względu na konfigurację ochrony etykiety tylko pracownicy mogą otworzyć dokument, a niektóre akcje są ograniczone do nich. Na przykład ponieważ nie ma Print i kopii i Wyodrębnij zawartość uprawnień, ich nie można drukować dokument lub kopiowania z niego. Takie ograniczenia pomoc, aby zapobiec utracie danych. Jako właściciel dokumentu można wydrukować go i skopiuj z niego, ale jeśli dokument jest e-mail do innego użytkownika w organizacji, ich nie może wykonać te akcje.

4. Możesz zamknąć ten dokument.

Po sprawdzeniu klasyfikacji, etykietowania i ochrony w działaniu zobaczmy, jak możesz chronić swoje dokumenty nawet po udostępnieniu ich innym osobom w innej organizacji. Możesz nawet śledzić ich wykorzystanie i cofać dostęp do nich.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Pełne instrukcje dotyczące ochrony plików i dodawania do nich etykiet |[Klasyfikowanie i ochrona pliku lub wiadomości e-mail](../rms-client/client-classify-protect.md)|
|W przypadku, gdy rejestrowane są działania związane z etykietowaniem |[Rejestrowanie użycia klienta usługi Azure Information Protection](../rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client)|


>[!div class="step-by-step"]
[&#171; Krok 3](infoprotect-tutorial-step3.md)
[Krok 5 &#187;](infoprotect-tutorial-step5.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]