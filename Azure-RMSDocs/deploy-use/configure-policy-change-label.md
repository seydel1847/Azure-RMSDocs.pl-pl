---
title: "Zmiana etykiety usługi Azure Information Protection"
description: "Dowolne etykiety, które użytkownicy widzą na pasku usługi Information Protection, możesz zmienić lub dostosować, konfigurując je w zasadach usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: 48faf9703176ba8f67f57582ea584733fe3e9b01
ms.sourcegitcommit: d814d2876cf56e8fff0b107a5e3ec6df2aeda9ae
translationtype: HT
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Zmiana lub dostosowanie istniejącej etykiety dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Dowolne etykiety, które użytkownicy widzą na pasku usługi Information Protection, możesz zmienić lub dostosować, konfigurując je w zasadach usługi Azure Information Protection.

Na przykład możesz zmienić nazwę, etykietkę narzędzia, kolor i kolejność etykiet lub etykiet podrzędnych, ustawić stosowanie oznaczeń wizualnych, np. stopki lub znaku wodnego, stosowanie ochrony usługi Azure Rights Management oraz zalecanej i automatycznej klasyfikacji.

Aby zmienić etykietę, użyj następujących instrukcji.


1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator zabezpieczeń lub administrator globalny, a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. Aby zmienić etykietę z zasad globalnych, tak aby dotyczyła wszystkich użytkowników, wybierz etykietę do zmiany z bloku **Zasady: Globalne**, a następnie wprowadź zmiany w bloku **Etykieta** i wszystkich kolejnych wymaganych blokach. Aby zmienić etykietę z [zasad o określonym zakresie](configure-policy-scope.md), tak aby dotyczyła wybranych użytkowników, najpierw wybierz te zasady w początkowym bloku **Azure Information Protection**.

    Wyjątek stanowi sytuacja, w której chcesz zmienić kolejność etykiet. Operację przeprowadza się w bloku zasad pochodzącym z zasad globalnych lub wybranych przez Ciebie zasad o określonym zakresie: kliknij etykietę prawym przyciskiem myszy lub wybierz menu kontekstowe etykiety, a następnie wybierz opcję **Przenieś w górę** lub **Przenieś w dół**.

3. Jeśli wprowadzisz zmiany w bloku, kliknij przycisk **Zapisz** w tym bloku, aby zachować zmiany.

4. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

> [!TIP]
>Jeśli chcesz przywrócić jedną z etykiet domyślnych do wartości domyślnych, użyj informacji zawartych w temacie [Domyślne zasady usługi Information Protection](configure-policy-default.md).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu opcji etykiet oraz innych ustawień zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


