---
title: Samouczek Szybki start krok 4 | Azure Rights Management
description: "Krok 3 samouczka wprowadzającego, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection w swojej organizacji. Wystarczy około 30 minut."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: bcf1e9ee7a2d6cf8fb264533f150b350ce0a9e56


---

# <a name="step-4-see-classification-labeling-and-protection-in-action"></a>Krok 4. Prezentacja działania funkcji klasyfikacji, etykietowania i ochrony 

>*Dotyczy: Azure Information Protection*

Po otwarciu dokumentu programu Word z zainstalowanym klientem usługi Azure Information Protection możesz sprawdzić, jak łatwo rozpocząć etykietowanie i chronienie dokumentu za pomocą skonfigurowanej zasady.

Klasyfikacja i ochrona zachodzą podczas zapisywania dokumentu, ale zanim do tego przejdziemy, użyjemy naszego niezapisanego dokumentu, aby zobaczyć, jak łatwo stosować i zmieniać etykiety.

## <a name="to-manually-change-our-default-label"></a>Aby ręcznie zmienić naszą domyślną etykietę

Na pasku Information Protection wybierz etykietę **Osobiste**. Zostanie wyświetlony monit o uzasadnienie obniżenia poziomu klasyfikacji:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — monit o uzasadnienie potwierdzenia obniżenia](../media/info-protect-lower-justification.png)

Wybierz opcję **Poprzednia etykieta już nie obowiązuje** i kliknij przycisk **Potwierdź**. Wartość opcji **Ważność** zmieni się na **Osobiste**.

## <a name="to-remove-the-classification-completely"></a>Aby całkowicie usunąć klasyfikację

Na pasku Information Protection kliknij ikonę **Edytuj etykietę** obok opcji **Osobiste**. Zostaną wyświetlone dostępne etykiety. Zamiast wybierać którąś z etykiet, kliknij ikonę **Usuń etykietę**. Kliknij przycisk **OK**, aby potwierdzić, a następnie podaj uzasadnienie dla tej akcji.  

Zobaczysz, że wartość opcji **Ważność** zmieni się na **Nieustawione**, która jest wartością wyświetlaną początkowo, przed ustawieniem etykiety domyślnej:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — usuwanie klasyfikacji](../media/sensitivity-not-set.png)


## <a name="to-see-a-recommendation-prompt-for-labeling-and-automatic-protection"></a>Aby wyświetlić monit zalecający etykietowanie i automatyczne włączanie ochrony

1. W dokumencie programu Word wpisz poprawny numer karty kredytowej, na przykład: **4242-4242-4242-4242**. 

2. Zapisz dokument (użyj dowolnej nazwy pliku i dowolnej lokalizacji). 

3. Pojawi się monit: **Zaleca się nadać temu plikowi etykietę Poufne**. Kliknij przycisk **Zmień teraz**.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — monit z zaleceniem klasyfikacji](../media/change-now.png)

    Poza ustawieniem etykiety dokumentu na Poufne natychmiast zobaczysz znak wodny z nazwą organizacji na całej stronie, jak również stopkę **Poufność: Poufne**. 

    Dokument jest również chroniony za pomocą podanego szablonu Azure Rights Management, co można potwierdzić, klikając kartę **Plik** i wyświetlając informację **Ochrona dokumentu**. Jeśli używany jest domyślny szablon Poufne, zostaną wyświetlone informacje, że zasięg dokumentu jest ograniczony do użytkowników wewnętrznych (użytkownicy spoza organizacji nie będą mogli otworzyć dokumentu) i jego zawartość nie może być kopiowana ani drukowana. Jako właściciel dokumentu możesz skopiować i wydrukować dokument, ale jeśli wyślesz go pocztą e-mail do innego użytkownika w organizacji, nie będzie on mógł wykonać tych czynności.

Po sprawdzeniu klasyfikacji, etykietowania i ochrony w działaniu zobaczmy, jak możesz chronić swoje dokumenty nawet po udostępnieniu ich innym osobom w innej organizacji. Możesz nawet śledzić ich wykorzystanie i cofać dostęp do nich.

>[!div class="step-by-step"]
[&#171; Krok 3](infoprotect-tutorial-step3.md)
[Krok 5 &#187;](infoprotect-tutorial-step5.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


