---
title: "Usuwanie lub zmiana kolejności etykiet dla usługi Azure Information Protection | Azure Rights Management"
description: "Etykiety, które użytkownicy widzą na pasku usługi Information Protection, możesz usunąć lub zmienić ich kolejność, przeprowadzając konfigurację w zasadach usługi Azure Information Protection."
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: 43b43657627135886f6d0be42fef41ba939bdae1


---

# Usuwanie lub zmiana kolejności etykiet dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Etykiety, które użytkownicy widzą na pasku usługi Information Protection, możesz usunąć lub zmienić ich kolejność, przeprowadzając konfigurację w zasadach usługi Azure Information Protection.

![Usuwanie lub zmiana kolejności etykiet w zasadach usługi Azure Information Protection](../media/info-protect-contextmenu.png)

Zamiast usuwać etykietę możesz ją po prostu wyłączyć, jeśli chcesz zachować konfigurację etykiety, jednocześnie uniemożliwiając jej wyświetlanie na pasku usługi Information Protection.

Kolejność etykiet określ w taki sposób, aby była ona logiczna na pasku usługi Information Protection. Przykładowo ułóż etykiety w kolejności z rosnącą ważnością, aby użytkownicy widzieli etykietę wskazującą najmniejszą ważność jako pierwszą, a etykietę wskazującą największą ważność jako ostatnią. [Zasady domyślne](configure-policy-default.md) używają takiej konfiguracji.

> [!IMPORTANT]
>W przypadku skonfigurowania [warunków](configure-policy-classification.md) dla etykiet, które mogą być stosowane do więcej niż jednej etykiety, musisz ułożyć etykiety w kolejności od etykiety wskazującej najmniejszą ważność do etykiety wskazującej największą ważność. Ta kolejność zapewnia zastosowanie etykiety wskazującej największą ważność w trakcie oceny warunków.


Użyj poniższych instrukcji, aby wprowadzić te zmiany.

1. Jeśli jeszcze tego nie zrobiono, zaloguj się do [Portalu Azure](https://portal.azure.com), a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij przycisk **Przeglądaj** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. W bloku **Azure Information Protection** wykonaj jedną z następujących czynności, w zależności od tego, czy chcesz usunąć etykietę, wyłączyć ją, czy zmienić jej kolejność:

    - Aby usunąć etykietę: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...**) dla etykiety, którą chcesz usunąć, kliknij polecenie **Usuń tę etykietę**, a następnie kliknij przycisk **Tak**, aby potwierdzić. Następnie kliknij przycisk **Zapisz**. 

    - Aby wyłączyć etykietę: wybierz etykietę, którą chcesz wyłączyć. W bloku **Etykieta** w pozycji **Wł.** kliknij polecenie **Wył.**, a następnie kliknij przycisk **Zapisz**.

    - Aby zmienić kolejność etykiet: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...**) dla etykiety, której kolejność chcesz zmienić, a następnie klikaj polecenie **Przenieś w górę** lub **Przenieś w dół**, aż do uzyskania odpowiedniej kolejności etykiet. Następnie kliknij przycisk **Zapisz**. 

3. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Aug16_HO4-->

