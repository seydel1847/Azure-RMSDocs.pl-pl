---
title: "Zmiana etykiety usługi Azure Information Protection"
description: "Dowolne etykiety, które użytkownicy widzą na pasku usługi Information Protection, możesz zmienić lub dostosować, konfigurując je w zasadach usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: da89ea5986ac78cdf79e97336d74c54e9db2a825
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Zmiana lub dostosowanie istniejącej etykiety dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Dowolne etykiety, które użytkownicy widzą na pasku usługi Information Protection, możesz zmienić lub dostosować, konfigurując je w zasadach usługi Azure Information Protection.

Na przykład można zmienić etykiety lub sublabel nazwy, etykietki narzędzia, kolor i kolejność. Można zmienić, czy etykieta oznaczeń wizualnych, np. stopki lub znaku wodnego. Można również zmienić, czy etykieta ma zastosowanie ochrony i zalecaną lub automatyczną klasyfikację.

Aby zmienić etykietę, użyj poniższych instrukcji:

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Aby zmienić etykietę globalne zasady, że jest ona stosowana do wszystkich użytkowników, wybierz etykietę do zmiany z **usługi Azure Information Protection — globalne zasady** bloku oraz wszelkich kolejnych blokach wedle potrzeb. Aby zmienić etykietę z [zakres zasad](configure-policy-scope.md) tak, aby dotyczył tylko wybrani użytkownicy, najpierw wybierz **zakres zasad** z **zasady** zaznaczenia menu. Następnie wybierz zakresie zasad z **zasady usługi Azure Information Protection - zakres** bloku.

    Wyjątkiem są, jeśli chcesz zmienić kolejność etykiet. W bloku zasad z globalnych zasad lub z wybranymi zasadami zakresami: kliknij etykietę prawym przyciskiem myszy albo wybierz menu kontekstowe dla etykiety. Następnie wybierz opcję **Przenieś w górę** lub **Przenieś w dół** opcje.

3. Jeśli wprowadzisz zmiany w bloku, kliknij przycisk **Zapisz** w tym bloku, aby zachować zmiany.

4. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

5. Jeśli została zmieniona nazwa wyświetlana etykieta lub opis i skonfigurowano te dodatkowe języki: ponownie wyeksportuj zasady usługi Azure Information Protection, podaj nowe tłumaczenia i zaimportować zmiany. Więcej informacji można znaleźć w sekcji [Konfigurowanie etykiet w różnych językach](configure-policy-languages.md).

> [!TIP]
>Jeśli chcesz przywrócić jedną z etykiet domyślnych do wartości domyślnych, użyj informacji zawartych w temacie [Domyślne zasady usługi Information Protection](configure-policy-default.md).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu opcji etykiet oraz innych ustawień zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


