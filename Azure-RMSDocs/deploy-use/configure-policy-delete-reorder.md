---
title: "Usuwanie lub zmiana kolejności etykiet usługi Azure Information Protection"
description: "Można usunąć lub zmienić kolejność etykiet, które użytkownicy widzą na pasku Information Protection, przeprowadzając konfigurację w zasadach usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
ms.openlocfilehash: 85d8e612d95358ce7f5d883450dc207e54549828
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Usuwanie lub zmiana kolejności etykiet dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Można usunąć lub zmienić kolejność etykiet, które użytkownicy widzą na pasku Information Protection, wybierając te akcje w ramach zasad usługi Azure Information Protection.

![Usuwanie lub zmiana kolejności etykiet w zasadach usługi Azure Information Protection](../media/info-protect-contextmenu.png)

Usuń etykietę, którą zastosowano do dokumentów i wiadomości e-mail, a następnie opublikuj zasadę usługi Azure Information Protection, że etykieta zostanie automatycznie usunięta z tych dokumentów lub wiadomości e-mail, gdy są one dalej otwarty przez klienta usługi Azure Information Protection.

Jednak jeśli etykieta zastosowano ochrony, czy ochrona nie zostanie usunięta. Ustawienia ochrony z etykiety pozostają i wyświetlane w **szablony ochrony**. Ten szablon teraz można przekonwertować na nową etykietę lub połączony z etykietą. Podczas pozostaje w tym szablonie, nie można utworzyć nową etykietę o takiej samej nazwie jako etykiety, który zostanie usunięty. Jeśli chcesz to zrobić, dostępne są następujące opcje:

- Przekonwertować szablon na etykietę. 
    
    Ta akcja jest zalecane, ponieważ w razie potrzeby można zmienić nazwę szablonu i zmodyfikować ustawienia ochrony.

- Zmień nazwę szablonu, lub usuń go za pomocą programu PowerShell.
    
    Przed wykonaniem działania te należy wziąć pod uwagę czy innych administratorów lub usługi używany jest szablon oraz umożliwiać jej identyfikację za pomocą bieżącej nazwy. Szablon można usunąć tylko wtedy, gdy nie trzeba otwierać dokumentów lub wiadomości e-mail, które były chronione przez szablon.

Aby uzyskać więcej informacji o zarządzaniu szablony ochrony, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md).

Przed usunięciem etykiety rozważ, czy nie byłoby lepiej ją tylko wyłączyć. Po wyłączeniu etykietę, którą zastosowano do dokumentów i wiadomości e-mail zastosowana etykieta nie jest usuwany z tych dokumentów i wiadomości e-mail, ale nie jest już wyświetlany jako etykietę, którą użytkownicy mogą wybrać na pasku Information Protection. Wyłączenie etykiety umożliwia również zachowanie oryginalnej konfiguracji, dzięki czemu w późniejszym czasie, po ponownym jej włączeniu, będzie można pozwolić użytkownikom na jej wybranie.

Kolejność etykiet określ w taki sposób, aby była ona logiczna na pasku usługi Information Protection. Przykładowo ułóż etykiety w kolejności z rosnącą ważnością, aby użytkownicy widzieli etykietę wskazującą najmniejszą ważność jako pierwszą, a etykietę wskazującą największą ważność jako ostatnią. [Zasady domyślne](configure-policy-default.md) wykorzystują tę konfigurację i odzwierciedlają rosnącą ważność nazw etykiet.

> [!IMPORTANT]
>W przypadku skonfigurowania [warunków](configure-policy-classification.md) dla etykiet, które mogą być stosowane do więcej niż jednej etykiety, musisz ułożyć etykiety w kolejności od etykiety wskazującej najmniejszą ważność do etykiety wskazującej największą ważność. Ta kolejność zapewnia zastosowanie etykiety wskazującej największą ważność w trakcie oceny warunków.


Użyj poniższych instrukcji, aby wprowadzić te zmiany.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Jeśli etykietę, którą chcesz skonfigurować będą stosowane do wszystkich użytkowników, pozostają **usługi Azure Information Protection — globalne zasady** bloku.
    
    Jeśli trwa etykietę, którą chcesz skonfigurować [zakres zasad](configure-policy-scope.md) tak, aby dotyczył tylko wybrani użytkownicy z **zasady** zaznaczenia menu, wybierz opcję **zakres zasad**. Następnie wybierz zakresie zasad z **zasady usługi Azure Information Protection - zakres** bloku.

3. Z **usługi Azure Information Protection — globalne zasady** bloku lub **zasad:\<name >** blok, wykonaj jedną z następujących czynności: 

    - Aby usunąć etykietę: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...**) dla etykiety, którą chcesz usunąć, kliknij polecenie **Usuń tę etykietę**, a następnie kliknij przycisk **Tak**, aby potwierdzić. Następnie kliknij przycisk **Zapisz**. 

    - Aby wyłączyć etykietę: wybierz etykietę, którą chcesz wyłączyć. W bloku **Etykieta** w pozycji **Wł.** kliknij polecenie **Wył.**, a następnie kliknij przycisk **Zapisz**.

    - Aby zmienić kolejność etykiet: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...** ) dla etykiety, którą chcesz zmienić, kliknij przycisk **Przenieś w górę** lub **Przenieś w dół** momentu etykiety w kolejności, która ma. Następnie kliknij przycisk **Zapisz**. 

4. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

