---
title: "Usuwanie lub zmiana kolejności etykiet | Azure Information Protection"
description: "Etykiety, które użytkownicy widzą na pasku usługi Information Protection, możesz usunąć lub zmienić ich kolejność, przeprowadzając konfigurację w zasadach usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/13/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
translationtype: Human Translation
ms.sourcegitcommit: 55895dd6fd0e106c33914a232e2d00d98e8a154a
ms.openlocfilehash: 195a4ff44d0edc9d35ee30786bdddbcc821fc106


---

# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Usuwanie lub zmiana kolejności etykiet dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Etykiety, które użytkownicy widzą na pasku usługi Information Protection, możesz usunąć lub zmienić ich kolejność, przeprowadzając konfigurację w zasadach usługi Azure Information Protection.

![Usuwanie lub zmiana kolejności etykiet w zasadach usługi Azure Information Protection](../media/info-protect-contextmenu.png)

Jeśli usuniesz etykietę, która została zastosowana do dokumentów lub wiadomości e-mail, a następnie opublikujesz zasady usługi Azure Information Protection, taka etykieta zostanie automatycznie usunięta z tych dokumentów lub wiadomości e-mail, kiedy zostaną one otwarte następnym razem w kliencie usługi Azure Information Protection.

Zamiast usuwać etykietę, możesz ją po prostu wyłączyć, jeśli chcesz ją zachować, jednocześnie uniemożliwiając jej wyświetlanie na pasku usługi Information Protection.

Kolejność etykiet określ w taki sposób, aby była ona logiczna na pasku usługi Information Protection. Przykładowo ułóż etykiety w kolejności z rosnącą ważnością, aby użytkownicy widzieli etykietę wskazującą najmniejszą ważność jako pierwszą, a etykietę wskazującą największą ważność jako ostatnią. [Zasady domyślne](configure-policy-default.md) używają takiej konfiguracji.

> [!IMPORTANT]
>W przypadku skonfigurowania [warunków](configure-policy-classification.md) dla etykiet, które mogą być stosowane do więcej niż jednej etykiety, musisz ułożyć etykiety w kolejności od etykiety wskazującej najmniejszą ważność do etykiety wskazującej największą ważność. Ta kolejność zapewnia zastosowanie etykiety wskazującej największą ważność w trakcie oceny warunków.


Użyj poniższych instrukcji, aby wprowadzić te zmiany.

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator globalny, a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. Jeśli etykieta, którą chcesz usunąć, wyłączyć lub której kolejność chcesz zmienić, ma zastosowanie do wszystkich użytkowników, wykonaj jedną z następujących czynności z bloku **Zasady: Globalne**. 

    - Aby usunąć etykietę: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...**) dla etykiety, którą chcesz usunąć, kliknij polecenie **Usuń tę etykietę**, a następnie kliknij przycisk **Tak**, aby potwierdzić. Następnie kliknij przycisk **Zapisz**. 

    - Aby wyłączyć etykietę: wybierz etykietę, którą chcesz wyłączyć. W bloku **Etykieta** w pozycji **Wł.** kliknij polecenie **Wył.**, a następnie kliknij przycisk **Zapisz**.

    - Aby zmienić kolejność etykiet: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...**) dla etykiety, której kolejność chcesz zmienić, a następnie klikaj polecenie **Przenieś w górę** lub **Przenieś w dół**, aż do uzyskania odpowiedniej kolejności etykiet. Następnie kliknij przycisk **Zapisz**. 

     Jeśli etykieta, którą chcesz usunąć, wyłączyć lub której kolejność chcesz zmienić, należy do [zasad o określonym zakresie](configure-policy-scope.md) i z tego powodu ma zastosowanie tylko do wybranych użytkowników, najpierw wybierz te zasady o określonym zakresie z początkowego bloku **Azure Information Protection**.

3. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  





<!--HONumber=Dec16_HO2-->


