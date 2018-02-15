---
title: "Nowa etykieta usługi Azure Information Protection"
description: "Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: cb7af6831040bb42a3c7e3a7e8ea355f72fc433c
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Tworzenie nowej etykiety dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection.

Możesz dodać nową etykietę, lub Dodaj nowe sublabel do istniejącej etykiety, jeśli potrzebujesz dodatkowego poziomu klasyfikacji. Na przykład ostatnia etykieta w [domyślne zasady](configure-policy-default.md), zawiera sublabels.

Użyj poniższych instrukcji, aby dodać nową etykietę do zasad usługi Azure Information Protection.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. W przypadku nowej etykiety, który chcesz dodać dla wszystkich użytkowników, pozostają **usługi Azure Information Protection — globalne zasady** bloku.
    
    W przypadku nowej etykiety, który chcesz dodać do wybranych użytkowników w [zakres zasad](configure-policy-scope.md), z **zasady** zaznaczenia menu, wybierz opcję **zakres zasad**. Następnie wybierz zakresie zasad z **zasady usługi Azure Information Protection - zakres** bloku.

3. Z **usługi Azure Information Protection — globalne zasady** bloku lub **zasad:\<name >** blok, wykonaj jedną z następujących czynności:
    
    - Aby utworzyć nową etykietę: kliknij przycisk **Dodaj nową etykietę**.
    
    - Aby utworzyć nowy sublabel: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...** ) dla etykiety, którą chcesz utworzyć sublabel dla, a następnie kliknij przycisk **Dodaj etykietę podrzędną**.

4. W bloku **Etykieta** lub **Etykieta podrzędna** wybierz opcje dla nowej etykiety, a następnie kliknij przycisk **Zapisz**.
    
    Pamiętaj, że nowym etykietom jest automatycznie przypisywany kolor czarny. Wybierz z listy kolorów wyróżniający się kolor lub wprowadź szesnastkowy tryplet dla składników czerwonego, zielonego i niebieskiego (RGB) koloru. Przykład: **#DAA520**. Jeśli potrzebujesz odwołania te kodów [kolory według nazwy](https://msdn.microsoft.com/library/aa358802\(v=vs.85\).aspx) w sieci MSDN dokumentacji stanowi punkt wyjścia przydatne i kody znajdziesz w edycji programów, takich jak Microsoft Paint, gdzie możesz wybrać niestandardowego koloru z wielu obrazów palety i automatycznie wyświetla wartości RGB.

5. Aby udostępnić użytkownikom zmiany, w początkowym bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

6. Jeśli chcesz, aby ta nazwa i opis nowej etykiety były wyświetlane w różnych językach dla użytkowników, wykonaj procedury opisane w sekcji [Konfigurowanie etykiet w różnych językach](configure-policy-languages.md). 

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

