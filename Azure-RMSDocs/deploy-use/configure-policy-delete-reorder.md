---
title: Usuwanie lub zmiana kolejności etykiet usługi Azure Information Protection
description: Można usunąć lub zmienić kolejność etykiet usługi Azure Information Protection, które są widoczne dla użytkowników.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/22/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
ms.openlocfilehash: 6b790eddb4e111333cbd78fc0b8ec09963393494
ms.sourcegitcommit: 94d1c7c795e305444e9fde17ad73e46f242bcfa9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2018
---
# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Usuwanie lub zmiana kolejności etykiet dla usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

>[!NOTE]
> W tym artykule odzwierciedla najnowsze aktualizacje do portalu Azure, które pozwalają tworzyć etykiety niezależnie od globalnych zasad lub zakresie zasad. Opcję, aby opublikować zasady zostaną również usunięte. Jeśli dzierżawy nie jest jeszcze zaktualizowane dla tych zmian — na przykład nadal zobacz **publikowania** opcja dla usługi Azure Information Protection i nie ma **klasyfikacje** opcji menu — należy odczekać kilka dni i następnie wróć do niniejszych instrukcji.

Można usunąć lub zmienić kolejność etykiet usługi Azure Information Protection, które użytkownicy widzą w swoich aplikacjach pakietu Office, wybierając tych akcji dla etykiety.

![Usuwanie lub zmiana kolejności etykiet w zasadach usługi Azure Information Protection](../media/info-protect-contextmenu.png)

Po usunięciu etykietę, którą zastosowano do dokumentów i wiadomości e-mail użytkownicy widzą **Nieustawione** dla etykiety, stan, gdy te dokumenty i wiadomości e-mail dalej otwarty przez klienta usługi Azure Information Protection. Jednak pozostanie informacji etykiety w metadanych i nadal można odczytać przez usługi, które informacje etykiety do odnalezienia.

Ponadto usunięto etykiety zastosowanie ochrony, czy ochrona nie zostanie usunięta. Ustawienia ochrony z etykiety pozostają i wyświetlane w **szablony ochrony** sekcji. Ten szablon teraz można przekonwertować na nową etykietę lub połączony z etykietą. Podczas pozostaje w tym szablonie, nie można utworzyć nową etykietę o takiej samej nazwie jako etykiety, który zostanie usunięty. Jeśli chcesz to zrobić, dostępne są następujące opcje:

- Przekonwertować szablon na etykietę. 
    
    Ta akcja jest zalecane, ponieważ w razie potrzeby można zmienić nazwę szablonu i zmodyfikować ustawienia ochrony.

- Zmień nazwę szablonu, lub usuń go za pomocą programu PowerShell.
    
    Przed wykonaniem działania te należy wziąć pod uwagę czy innych administratorów lub usługi używany jest szablon oraz umożliwiać jej identyfikację za pomocą bieżącej nazwy. Szablon można usunąć tylko wtedy, gdy nie trzeba otwierać dokumentów lub wiadomości e-mail, które były chronione przez szablon.

Aby uzyskać więcej informacji o zarządzaniu szablony ochrony, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md).

Aby usunąć etykietę, zamiast tego należy wziąć pod uwagę jego wyłączenie lub usunięcie go z zasad:
    
- Po wyłączeniu etykietę, którą zastosowano do dokumentów i wiadomości e-mail zastosowana etykieta nie jest usuwany z tych dokumentów i wiadomości e-mail. Etykieta pozostanie w zasadach, ale nie jest już wyświetlany jako etykietę, którą użytkownicy mogą wybrać na pasku Information Protection. Wyłączanie etykietę można zachować oryginalną konfigurację po może być użytkownikom w ramach jednych zasad wybierz etykietę w późniejszym czasie, gdy użytkownik po prostu ponownie włączyć etykiety.

- Po usunięciu etykiety z zasad zastosowanych etykiety również nie jest usuwany z tych dokumentów i wiadomości e-mail. Jednak po usunięciu etykiety z zasad, będzie dostępny, można dodać tej etykiety na inne zasady. Aby uzyskać więcej informacji, zobacz [Dodaj lub Usuń etykietę do lub z zasad usługi Azure Information Protection](configure-policy-add-remove-label.md).

Kolejność etykiet określ w taki sposób, aby była ona logiczna na pasku usługi Information Protection. Przykładowo ułóż etykiety w kolejności z rosnącą ważnością, aby użytkownicy widzieli etykietę wskazującą najmniejszą ważność jako pierwszą, a etykietę wskazującą największą ważność jako ostatnią. [Zasady domyślne](configure-policy-default.md) wykorzystują tę konfigurację i odzwierciedlają rosnącą ważność nazw etykiet.

> [!IMPORTANT]
>W przypadku skonfigurowania [warunków](configure-policy-classification.md) dla etykiet, które mogą być stosowane do więcej niż jednej etykiety, musisz ułożyć etykiety w kolejności od etykiety wskazującej najmniejszą ważność do etykiety wskazującej największą ważność. Ta kolejność zapewnia zastosowanie etykiety wskazującej największą ważność w trakcie oceny warunków.


Użyj poniższych instrukcji, aby wprowadzić te zmiany.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **etykiety** opcji menu: na **usługi Azure Information Protection — etykiety** blok, wykonaj jedną z następujących czynności: 

    - Aby usunąć etykietę: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...** ) dla etykiety, którą chcesz usunąć, kliknij przycisk **Usuń tę etykietę**i kliknij przycisk **OK** o potwierdzenie. 

    - Aby wyłączyć etykietę: wybierz etykietę, którą chcesz wyłączyć. Na **etykiety** bloku dla **włączone**, wybierz pozycję **poza**, a następnie kliknij przycisk **zapisać**.

    - Aby zmienić kolejność etykiet: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...** ) dla etykiety, którą chcesz zmienić, kliknij przycisk **Przenieś w górę** lub **Przenieś w dół** momentu etykiety w kolejności, która ma.  

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

