---
title: Usuwanie lub zmiana kolejności etykiet usługi Azure Information Protection — AIP
description: Można usunąć lub zmiana kolejności etykiet usługi Azure Information Protection, które są widoczne dla użytkowników.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
ms.openlocfilehash: 1f957874649fe9e5697c3dd0164b0b0b255d1e6e
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53304880"
---
# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Usuwanie lub zmiana kolejności etykiet dla usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Można usunąć lub zmiana kolejności etykiet usługi Azure Information Protection, które użytkownicy zobaczą w swoich aplikacjach pakietu Office, wybierając te akcje dotyczące etykiet.

![Usuwanie lub zmiana kolejności etykiet w zasadach usługi Azure Information Protection](./media/info-protect-contextmenu.png)

Jeśli usuniesz etykietę, która została zastosowana do dokumentów i wiadomości e-mail, użytkownicy widzą **Nieustawione** etykiety stanu w przypadku tych dokumentów i wiadomości e-mail dalej otwarty przez klienta usługi Azure Information Protection. Jednak informacje o etykiecie jest nadal w metadanych i nadal można odczytywać przez usługi, które poszukują te informacje etykiety.

Ponadto jeśli usunięto etykietę zastosować ochronę, ochrona nie zostanie usunięty. Ustawienia ochrony z etykiety pozostają i wyświetlane w **szablonami ochrony** sekcji. Ten szablon teraz mogą być konwertowane na nową etykietę. Ten szablon pozostaje, nie można utworzyć nową etykietę o takiej samej nazwie jak etykiety, który został usunięty. Jeśli chcesz to zrobić, masz następujące opcje:

- Konwersji szablonu na etykietę. 
    
    Ta akcja jest zalecana, ponieważ w razie potrzeby można zmienić nazwę szablonu i zmodyfikować ustawienia ochrony.

- Zmień nazwę szablonu, lub usuń go za pomocą programu PowerShell.
    
    Przed wykonaniem tych czynności należy wziąć pod uwagę czy innych administratorów lub usług są przy użyciu szablonu i identyfikację za pomocą nazwy bieżącego. Szablon można usunąć tylko wtedy, gdy nie trzeba otwierać dokumentów lub wiadomości e-mail, które były chronione przez szablon.

Aby uzyskać więcej informacji na temat zarządzania szablonami ochrony, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md).

Zanim usuniesz etykietę, zamiast tego należy wziąć pod uwagę jej wyłączenie lub usunięcie go z zasad:
    
- Po wyłączeniu etykiety, która została zastosowana do dokumentów i wiadomości e-mail zastosowana etykieta nie zostanie usunięta z tych dokumentów i wiadomości e-mail. Etykieta pozostają w zasadach, ale przestanie być wyświetlana jako etykieta, który użytkownicy mogą wybrać na pasku usługi Information Protection. Wyłączenie etykiety umożliwia zachowanie oryginalnej konfiguracji, gdy być może chcesz użytkowników w ramach jednych zasad o wybranie etykiety w późniejszym czasie, gdy użytkownik po prostu ponownie włączyć etykiety.

- Gdy usuniesz etykietę z zasad zastosowana etykieta również nie zostanie usunięta z tych dokumentów i wiadomości e-mail. Ale etykieta zostanie usunięta z zasad, staje się dostępne, można dodać tej etykiety na inne zasady. Aby uzyskać więcej informacji, zobacz [apletu Dodaj lub Usuń etykietę z zasad usługi Azure Information Protection lub](configure-policy-add-remove-label.md).

Kolejność etykiet określ w taki sposób, aby była ona logiczna na pasku usługi Information Protection. Przykładowo ułóż etykiety w kolejności z rosnącą ważnością, aby użytkownicy widzieli etykietę wskazującą najmniejszą ważność jako pierwszą, a etykietę wskazującą największą ważność jako ostatnią. [Zasady domyślne](configure-policy-default.md) wykorzystują tę konfigurację i odzwierciedlają rosnącą ważność nazw etykiet.

> [!IMPORTANT]
>W przypadku skonfigurowania [warunków](configure-policy-classification.md) dla etykiet, które mogą być stosowane do więcej niż jednej etykiety, musisz ułożyć etykiety w kolejności od etykiety wskazującej najmniejszą ważność do etykiety wskazującej największą ważność. Ta kolejność zapewnia zastosowanie etykiety wskazującej największą ważność w trakcie oceny warunków.


Użyj poniższych instrukcji, aby wprowadzić te zmiany.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **etykiety** opcji menu: Na **usługi Azure Information Protection — etykiety** blok, wykonaj jedną lub więcej z następujących czynności: 

    - Aby usunąć etykietę: Kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...** ) dla etykiety, który chcesz usunąć, kliknij przycisk **usunąć tę etykietę**i kliknij przycisk **OK** o potwierdzenie. 

    - Aby wyłączyć etykietę: Wybierz etykietę, która ma zostać wyłączony. Na **etykiety** bloku dla **włączone**, wybierz opcję **poza**, a następnie kliknij przycisk **Zapisz**.

    - Aby zmienić kolejność etykiet: Kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...** ) dla etykiety, który chcesz zmienić, kliknij przycisk **Przenieś w górę** lub **Przenieś w dół** momentu etykiety w kolejności, w którym chcesz.  

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  


