---
title: "Nowa etykieta usługi Azure Information Protection"
description: "Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: ac12ab9023499d5aac632159ef689a8f10a91418
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Tworzenie nowej etykiety dla usługi Azure Information Protection
<a id="how-to-create-a-new-label-for-azure-information-protection" class="xliff"></a>

>*Dotyczy: Azure Information Protection*

Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection.

Jeśli potrzebujesz dodatkowego poziomu klasyfikacji, możesz dodać nową etykietę lub etykietę podrzędną do istniejącej etykiety. Na przykład ostatnia etykieta znajdująca się w [zasadach domyślnych](configure-policy-default.md) zawiera etykiety podrzędne.

Użyj poniższych instrukcji, aby dodać nową etykietę do zasad usługi Azure Information Protection.

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator zabezpieczeń lub administrator globalny, a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. Jeśli nowa etykieta, którą chcesz dodać, będzie miała zastosowanie do wszystkich użytkowników, wykonaj jedną z następujących czynności z bloku **Zasady: Globalne**. 

    - Aby utworzyć nową etykietę: kliknij przycisk **Dodaj nową etykietę**.

    - Aby utworzyć nową etykietę podrzędną: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...**) etykiety, dla której chcesz utworzyć etykietę podrzędną, a następnie kliknij polecenie **Dodaj etykietę podrzędną**.
    
     Jeśli nowa etykieta, którą chcesz dodać, będzie należeć do [zasad o określonym zakresie](configure-policy-scope.md) i z tego powodu będzie miała zastosowanie tylko do wybranych użytkowników, najpierw wybierz te zasady o określonym zakresie z początkowego bloku **Azure Information Protection**.

3. W bloku **Etykieta** lub **Etykieta podrzędna** wybierz opcje dla nowej etykiety, a następnie kliknij przycisk **Zapisz**.
    
    Pamiętaj, że nowym etykietom jest automatycznie przypisywany kolor czarny. Wybierz z listy kolorów wyróżniający się kolor lub wprowadź szesnastkowy tryplet dla składników czerwonego, zielonego i niebieskiego (RGB) koloru. Przykład: **#DAA520**. Jeśli potrzebujesz informacji o tych kodach, plik [Colors by Name](https://msdn.microsoft.com/library/aa358802\(v=vs.85).aspx) z dokumentacji MSDN to dobry punkt wyjścia. Takie kody znajdziesz w wielu programach do edycji obrazów, takich jak Microsoft Paint, gdzie kolor niestandardowy wybiera się z palety, a program automatycznie wyświetla wartości RGB.

4. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

5. Jeśli chcesz, aby ta nazwa i opis nowej etykiety były wyświetlane w różnych językach dla użytkowników, wykonaj procedury opisane w sekcji [Konfigurowanie etykiet w różnych językach](configure-policy-languages.md). 

## Następne kroki
<a id="next-steps" class="xliff"></a>

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

