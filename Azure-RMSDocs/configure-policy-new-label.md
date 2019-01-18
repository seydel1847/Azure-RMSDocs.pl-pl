---
title: Nowa etykieta usługi Azure Information Protection — AIP
description: Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: 3bc01282e579368105687fe53157ce2a05dbe4ff
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393523"
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Tworzenie nowej etykiety dla usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Mimo że usługę Azure Information Protection zawiera domyślne etykiety, które można dostosować, można również utworzyć własne etykiety.

Dodaj nową etykietę lub dodać nowe etykietę podrzędną do istniejącej etykiety, jeśli potrzebujesz dodatkowego poziomu klasyfikacji. Na przykład ostatnia etykieta w [domyślne zasady](configure-policy-default.md), zawiera etykiet podrzędnych.

Podczas tworzenia pierwszego etykietę podrzędną do etykiety, użytkownicy mogą wybrać już, oryginalny, etykietę nadrzędną. Jeśli to konieczne, należy utworzyć nowe etykiety podrzędnej, aby odtworzyć utracone ustawienia etykiety nadrzędnego, dzięki czemu użytkownicy mogą stosować te same ustawienia.

Skorzystaj z poniższych instrukcji, aby dodać nową etykietę, który można dodać do zasad usługi Azure Information Protection.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **etykiety** opcji menu: Na **usługi Azure Information Protection — etykiety** blok, wykonaj jedną z następujących czynności:
    
    - Aby utworzyć nową etykietę: Kliknij przycisk **Dodaj nową etykietę**.
    
    - Aby utworzyć nowe etykiety podrzędnej: Kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...** ) dla etykiety, który chcesz utworzyć etykietę podrzędną do, a następnie kliknij przycisk **Dodaj etykietę podrzędną**.

3. W bloku **Etykieta** lub **Etykieta podrzędna** wybierz opcje dla nowej etykiety, a następnie kliknij przycisk **Zapisz**.
    
    Po określeniu nazwy wyświetlanej, będą mogli określanie niektórych znaków (na przykład ukośnika odwrotnego i handlowe "i"), ponieważ nie wszystkie usługi i aplikacje, które używają usługi Azure Information Protection może obsługiwać te znaki. Oprócz znaki, które są zablokowane, nie określaj **#** znaków.    
    
    Pamiętaj, że nowym etykietom jest automatycznie przypisywany kolor czarny. Wybierz z listy kolorów wyróżniający się kolor lub wprowadź szesnastkowy tryplet dla składników czerwonego, zielonego i niebieskiego (RGB) koloru. Przykład: **#DAA520**. Jeśli potrzebujesz odwołanie o tych kodach [Colors by Name](https://msdn.microsoft.com/library/aa358802(v=vs.85).aspx) z MSDN dokumentacja jest dobry punkt wyjścia, a w wielu programów, takich jak Microsoft Paint, gdzie wybierz kolor niestandardowy z do edycji obrazów znajdziesz te kody Paleta i automatycznie wyświetla wartości RGB.

4. Aby udostępnić nowe etykiety dla użytkowników: Z **klasyfikacje** > **zasady** menu, wybierz zasady, które zawierają nową etykietę. Wybierz **apletu Dodaj lub usuń etykiety**. Wybierz etykietę z **zasad: Dodaj lub usuń etykiety** bloku wybierz **OK**, a następnie wybierz pozycję **Zapisz**.
    
    >[!TIP]
    >Dla nowych etykiet należy rozważyć dodanie ich do zasady o określonym zakresie, którego używasz do testowania. Gdy jesteś zadowolony z wyników, usunąć etykietę z tego zakresu testowania, a następnie dodaj etykietę do zasad, które są używane w środowisku produkcyjnym.     
    
    Aby uzyskać więcej informacji na temat dodawania etykiet, zobacz [jak dodać lub usunąć etykietę](configure-policy-add-remove-label.md).
    
    Zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma już opcji publikowania oddzielne.

5. Jeśli chcesz to nazwę nowej etykiety i opis, aby wyświetlić w różnych językach dla użytkowników: Postępuj zgodnie z procedurami w [Konfigurowanie etykiet w różnych językach](configure-policy-languages.md). 

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  


