---
title: Nowa etykieta usługi Azure Information Protection
description: Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: 221b4228bc06868fb491a1a591939afb5baba8b8
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Tworzenie nowej etykiety dla usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Usługa Azure Information Protection zawiera domyślne etykiety, które można dostosować, można również utworzyć własne etykiety.

Możesz dodać nową etykietę, lub Dodaj nowe sublabel do istniejącej etykiety, jeśli potrzebujesz dodatkowego poziomu klasyfikacji. Na przykład ostatnia etykieta w [domyślne zasady](configure-policy-default.md), zawiera sublabels.

Po utworzeniu pierwszego sublabel dla etykiety, użytkownicy mogą wybrać już, oryginalne, nadrzędny etykiety. W razie potrzeby utwórz nowe sublabel do ponownego utworzenia ustawień obszaru nadrzędny etykiety, dzięki czemu użytkownicy mogą stosować te same ustawienia.

Użyj poniższych instrukcji, aby dodać nową etykietę, które następnie można dodać do zasad usługi Azure Information Protection.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **etykiety** opcji menu: na **usługi Azure Information Protection — etykiety** blok, wykonaj jedną z następujących czynności:
    
    - Aby utworzyć nową etykietę: kliknij przycisk **Dodaj nową etykietę**.
    
    - Aby utworzyć nowy sublabel: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...** ) dla etykiety, którą chcesz utworzyć sublabel dla, a następnie kliknij przycisk **Dodaj etykietę podrzędną**.

4. W bloku **Etykieta** lub **Etykieta podrzędna** wybierz opcje dla nowej etykiety, a następnie kliknij przycisk **Zapisz**.
    
    Po określeniu nazwy wyświetlanej, będą mogli Określanie niektóre znaki (na przykład ukośnikiem odwrotnym i handlowego "i"), ponieważ nie wszystkie usługi i aplikacje, które używają usługi Azure Information Protection może obsługiwać te znaki. Oprócz znaki, które są zablokowane, nie należy określać **#** znaków.    
    
    Pamiętaj, że nowym etykietom jest automatycznie przypisywany kolor czarny. Wybierz z listy kolorów wyróżniający się kolor lub wprowadź szesnastkowy tryplet dla składników czerwonego, zielonego i niebieskiego (RGB) koloru. Przykład: **#DAA520**. Jeśli potrzebujesz informacji o tych kodach, plik [Colors by Name](https://msdn.microsoft.com/library/aa358802\(v=vs.85).aspx) z dokumentacji MSDN to dobry punkt wyjścia. Takie kody znajdziesz w wielu programach do edycji obrazów, takich jak Microsoft Paint, gdzie kolor niestandardowy wybiera się z palety, a program automatycznie wyświetla wartości RGB.

5. Aby udostępnić użytkownikom nowej etykiety: Z **klasyfikacje** > **zasady** opcji menu, wybierz zasady zawierają nowe etykiety, wybierz **etykiety Dodaj lub usuń** , wybierz etykietę, z **zasad: Dodawanie lub usuwanie bloku etykiety**, wybierz pozycję **OK**, a następnie wybierz **zapisać**.
    
    >[!TIP]
    >Dla nowej etykiety należy rozważyć dodanie ich do zasad zakresami, używanej do testowania. Po zakończeniu wyniki usunąć etykiety z tego zakresu testowania, a następnie dodaj etykietę do zasad, które można używać w środowisku produkcyjnym.     
    
    Aby uzyskać więcej informacji na temat dodawania etykiety, zobacz [jak dodać lub usunąć etykietę](configure-policy-add-remove-label.md).
    
    Zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma oddzielne Publikuj.

6. Jeśli chcesz to nowa nazwa etykiety i opis, aby wyświetlić w różnych językach dla użytkowników: postępuj zgodnie z procedurami w [Konfigurowanie etykiety w różnych językach](configure-policy-languages.md). 

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

