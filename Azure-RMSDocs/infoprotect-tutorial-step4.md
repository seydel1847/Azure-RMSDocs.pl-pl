---
title: Samouczek Szybki start — krok 4 — AIP
description: Krok 4 samouczka wprowadzającego, dzięki któremu można szybko wypróbować usługę Azure Information Protection — prezentacja działania funkcji etykietowania i ochrony.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/29/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
ms.openlocfilehash: 93c5658bd59bb1b7f86580c41c0d22068b73d9d1
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44146645"
---
# <a name="step-4-see-classification-labeling-and-protection-in-action"></a>Krok 4. Prezentacja działania funkcji klasyfikacji, etykietowania i ochrony 

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Po otwarciu dokumentu programu Word z zainstalowanym klientem usługi Azure Information Protection możesz sprawdzić, jak łatwo rozpocząć etykietowanie i chronienie dokumentu za pomocą skonfigurowanej zasady.

Klasyfikacja i ochrona zachodzą podczas zapisywania dokumentu. Jednak zanim tego przejdziemy, użyjemy naszego niezapisanego dokumentu, aby zobaczyć, jak łatwo stosować i zmieniać etykiety.

## <a name="to-manually-change-our-default-label"></a>Aby ręcznie zmienić naszą domyślną etykietę

Na pasku usługi Information Protection wybierz ostatnią etykietę i zobacz, jak wyświetlać etykiet podrzędnych:

![Samouczek usługi Azure Information Protection — szybki start krok 4 — Wybieranie etykiety podrzędnej](./media/info-protect-sub-labelsv2.png)

Wybierz jedną z tych etykiet podrzędnych, i zobacz, jak inne etykiety nie są już wyświetlane na pasku po tym samym etykietę dla tego dokumentu. **Czułości** zmiany wartości, aby wyświetlić etykiety i etykiety podrzędnej, nazwij analogiczna zmiana koloru etykiety. Przykład:

![Samouczek usługi Azure Information Protection — szybki start krok 4 — wybrano etykietę podrzędną](./media/info-protect-sub-label-selectedv2.png)

Na pasku usługi Information Protection kliknij ikonę **Edytuj etykietę** obok aktualnie wybranej wartości etykiety:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — ikona Edytuj etykietę](./media/info-protect-edit-label-selectedv2.png)

Spowoduje to ponowne wyświetlenie dostępnych etykiet.

Teraz wybierz pierwszą etykietę **Osobiste**. Ponieważ wybrano etykiety mającej niższą klasyfikację niż etykieta wcześniej wybrana dla tego dokumentu zostanie wyświetlony monit o uzasadnienie, dlaczego one obniżenia poziomu klasyfikacji:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — monit o uzasadnienie potwierdzenia obniżenia](./media/info-protect-lower-justification.png)

Wybierz opcję **Poprzednia etykieta już nie obowiązuje** i kliknij przycisk **Potwierdź**. Wartość opcji **Ważność** zostanie zmieniona na **Osobiste** i pozostałe etykiety zostaną ponownie ukryte.

## <a name="to-remove-the-classification-completely"></a>Aby całkowicie usunąć klasyfikację

Na pasku o nazwie Information Protection kliknij ponownie ikonę **Edytuj etykietę**. Zamiast wybierać jedną z etykiet kliknij ikonę **Usuń etykietę**:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — ikona usuwania](./media/delete-icon-from-personalv2.png)

Tym razem, gdy zostanie wyświetlony monit, wpisz "ten dokument nie wymaga klasyfikacji" i kliknij przycisk **Potwierdź**.  

Zostanie wyświetlony **czułości** wartością wyświetlaną **Nieustawione**, który jest widoczny dla użytkowników początkowo nie ustawisz etykiety domyślnej.

## <a name="to-see-a-recommendation-prompt-for-labeling-and-automatic-protection"></a>Aby wyświetlić monit zalecający etykietowanie i automatyczne włączanie ochrony

1. W dokumencie programu Word wpisz poprawny numer karty kredytowej, na przykład: **4242-4242-4242-4242**. 

2. Zapisz dokument lokalnie, za pomocą dowolnej nazwy pliku. 

3. Teraz zostanie wyświetlony monit o zastosowanie etykiety, która została skonfigurowana do ochrony w przypadku wykrycia numerów kart kredytowych. Jeśli nie zgadzamy się z zaleceniem, nasze ustawienie zasad umożliwia nam jego odrzucenie po wybraniu pozycji **Odrzuć**. Przekazanie zalecenia, jednocześnie umożliwiając użytkownikowi zastąpienie go, pomaga zmniejszyć liczbę fałszywych alarmów podczas korzystania z automatycznej klasyfikacji. W przypadku tego samouczka kliknij pozycję **Zmień teraz**.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — monit z zaleceniem klasyfikacji](./media/change-nowv2.png)

    Oprócz dokumencie informacji o zastosowaniu skonfigurowanej etykiety (na przykład **poufne \ Finanse**), natychmiast zobaczysz znak wodny z nazwą organizacji na stronie oraz stopka  **Sklasyfikowane jako poufne** jest również zastosowane. 

    Dokument jest również chroniony przy użyciu uprawnień, które określone dla tej etykiety. Możesz sprawdzić, czy dokument jest chroniony przez kliknięcie przycisku **pliku** kartę i wyświetlając informację **Chroń dokument**. Zobacz, czy dokument jest chroniony przez **poufne \ Finanse** i opis etykiety. 
    
    Ze względu na konfigurację ochrony etykiety tylko pracownicy mogą otwierać dokument, a niektóre akcje są ograniczone do nich. Na przykład ponieważ nie ma Drukuj i kopii i wyodrębnić zawartości uprawnień, ich nie można drukować dokument lub kopiowania z niego. Takie ograniczenia pomóc uniknąć utraty danych. Jako właściciel dokumentu możesz wydrukować i skopiuj z niego. Jednak jeśli możesz wysłać wiadomość e-mail dokument innemu użytkownikowi w organizacji, nie można wykonać te akcje.

4. Możesz zamknąć ten dokument.

Po sprawdzeniu klasyfikacji, etykietowania i ochrony w działaniu zobaczmy, jak możesz chronić swoje dokumenty nawet po udostępnieniu ich innym osobom w innej organizacji. Możesz nawet śledzić ich wykorzystanie i cofać dostęp do nich.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Pełne instrukcje dotyczące ochrony plików i dodawania do nich etykiet |[Klasyfikowanie i ochrona pliku lub wiadomości e-mail](./rms-client/client-classify-protect.md)|
|W przypadku, gdy rejestrowane są działania związane z etykietowaniem |[Rejestrowanie użycia klienta usługi Azure Information Protection](./rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client)|


>[!div class="step-by-step"]
[&#171; Krok 3](infoprotect-tutorial-step3.md)
[Krok 5 &#187;](infoprotect-tutorial-step5.md)
