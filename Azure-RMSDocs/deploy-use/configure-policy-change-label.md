---
title: Zmiana etykiety usługi Azure Information Protection
description: Dowolne etykiety, które użytkownicy widzą na pasku usługi Information Protection, możesz zmienić lub dostosować, konfigurując je w zasadach usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: a8c745ac51c34139792367d55c5a83592c191571
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Zmiana lub dostosowanie istniejącej etykiety dla usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Możesz zmienić lub dostosować dowolne etykiety, które użytkownicy widzą na pasku lub z ochrony informacji **Chroń** na Wstążce pakietu Office, konfigurując etykiet w portalu Azure.

Na przykład można zmienić etykiety lub sublabel nazwy, etykietki narzędzia, kolor i kolejność. Można zmienić, czy etykieta oznaczeń wizualnych, np. stopki lub znaku wodnego. Można również zmienić, czy etykieta ma zastosowanie ochrony i zalecaną lub automatyczną klasyfikację.

Aby zmienić etykietę, użyj poniższych instrukcji:

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **etykiety** opcji menu: na **usługi Azure Information Protection — etykiety** bloku, wybierz etykietę, która ma zostać zmieniony.

    Wyjątkiem jest, jeśli chcesz zmienić kolejność etykiet: zamiast zaznaczania etykietę, kliknij etykietę prawym przyciskiem myszy lub wybierz menu kontekstowe dla etykiety. Następnie wybierz opcję **Przenieś w górę** lub **Przenieś w dół** opcje.

3. Jeśli wprowadzisz zmiany w nowym bloku, kliknij przycisk **zapisać** w tym bloku, jeśli chcesz zachować zmiany.
    
    Po kliknięciu **zapisać**, zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma oddzielne Publikuj.

4. Jeśli została zmieniona nazwa wyświetlana etykieta lub opis i skonfigurowano te dodatkowe języki: ponownie wyeksportuj zasady usługi Azure Information Protection, podaj nowe tłumaczenia i zaimportować zmiany. Więcej informacji można znaleźć w sekcji [Konfigurowanie etykiet w różnych językach](configure-policy-languages.md).

> [!TIP]
>Jeśli chcesz przywrócić jedną z etykiet domyślnych do wartości domyślnych, użyj informacji zawartych w temacie [Domyślne zasady usługi Information Protection](configure-policy-default.md).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu opcji etykiet oraz innych ustawień zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


