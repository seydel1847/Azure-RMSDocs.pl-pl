---
title: Zmiana etykiety usługi Azure Information Protection — AIP
description: Dowolne etykiety, które użytkownicy widzą na pasku usługi Information Protection, możesz zmienić lub dostosować, konfigurując je w zasadach usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: d421f4a4ddd53409695e1a3def925b09bec372d7
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53304931"
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Zmiana lub dostosowanie istniejącej etykiety dla usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Możesz zmienić lub dostosować dowolne etykiety, które użytkownicy zobaczą na Information Protection, pasek lub z **Chroń** przycisk na Wstążce pakietu Office, konfigurując etykiet w witrynie Azure portal.

Na przykład możesz zmienić etykietę lub etykietę podrzędną nazwy, etykietki narzędzia, kolor i kolejność. Można zmienić, czy etykieta ma być stosowanie oznaczeń wizualnych, np. stopki lub znaku wodnego. Można również zmienić, czy etykieta ma być stosowanie ochrony i zalecaną lub automatyczną klasyfikację.

Aby zmienić etykietę, użyj poniższych instrukcji:

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **etykiety** opcji menu: Na **usługi Azure Information Protection — etykiety** bloku, wybierz etykietę, o których chcesz zmienić.

    Wyjątkiem jest, jeśli chcesz zmienić kolejność etykiet: Zamiast zaznaczania etykiety, kliknij etykietę prawym przyciskiem myszy lub wybierz menu kontekstowe dla etykiety. Następnie wybierz **Przenieś w górę** lub **Przenieś w dół** opcje.

3. Po każdym wprowadzeniu zmian w nowym bloku kliknij **Zapisz** w tym bloku, jeśli chcesz zachować zmiany.
    
    Po kliknięciu **Zapisz**, zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma już opcji publikowania oddzielne.

4. Jeśli zmienisz nazwę wyświetlaną etykiety lub opis i skonfigurowano te dodatkowe języki: Ponownie wyeksportować zasady usługi Azure Information Protection, podać nowe tłumaczenia i zaimportować zmiany. Więcej informacji można znaleźć w sekcji [Konfigurowanie etykiet w różnych językach](configure-policy-languages.md).

> [!TIP]
>Jeśli chcesz przywrócić jedną z etykiet domyślnych do wartości domyślnych, użyj informacji zawartych w temacie [Domyślne zasady usługi Information Protection](configure-policy-default.md).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu opcji etykiet oraz innych ustawień zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).



