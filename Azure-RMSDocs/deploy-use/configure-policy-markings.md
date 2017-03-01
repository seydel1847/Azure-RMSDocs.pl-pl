---
title: "Konfigurowanie oznaczeń wizualnych dla etykiety usługi Azure Information Protection"
description: "Gdy przypisujesz etykietę do dokumentu lub wiadomości e-mail, możesz wybrać kilka opcji, dzięki którym wybrana klasyfikacja będzie łatwo widoczna. Oznaczenia wizualne to nagłówek, stopka i znak wodny."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 4ddacf2be34cb7921dfbe282a0476a8cd47de2cf
ms.lasthandoff: 02/24/2017


---

# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Konfigurowanie etykiety pod kątem oznaczeń wizualnych w usłudze Azure Information Protection

>*Dotyczy: Azure Information Protection*

Gdy przypisujesz etykietę do dokumentu lub wiadomości e-mail, możesz wybrać kilka opcji, dzięki którym wybrana klasyfikacja będzie łatwo widoczna. Oznaczenia wizualne to nagłówek, stopka i znak wodny:

Oznaczenia wizualne są stosowane w dokumentach Word, Excel i PowerPoint po zastosowaniu etykiety i zapisaniu dokumentu. W przypadku wiadomości e-mail oznaczenia wizualne są stosowane, gdy wiadomość e-mail jest wysyłana.

Dodatkowe informacje dotyczące tych oznaczeń wizualnych:

- Nagłówki i stopki dotyczą programów Word, Excel, PowerPoint i Outlook.

- Znaki wodne dotyczą programów Word, Excel i PowerPoint:

    - Excel: znaki wodne są widoczne tylko w trybach Podgląd wydruku i Układ strony oraz po wydrukowaniu.

    - PowerPoint: znaki wodne są stosowane do wzorca slajdów jako obraz tła.

- Można określić tylko ciąg tekstowy lub użyć [zmiennych](#using-variables-in-the-text-string) w celu dynamicznego tworzenia ciągu tekstowego podczas stosowania nagłówka, stopki lub znaku wodnego. 

Użyj poniższych instrukcji, aby skonfigurować oznaczenia wizualne dla etykiety.

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator globalny, a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. Jeśli etykieta, którą chcesz skonfigurować pod kątem oznaczeń wizualnych, będzie miała zastosowanie do wszystkich użytkowników, wybierz etykietę do zmiany z bloku **Zasady: Globalne**. 

     Jeśli etykieta, którą chcesz skonfigurować, należy do [zasad o określonym zakresie](configure-policy-scope.md) i z tego powodu ma zastosowanie tylko do wybranych użytkowników, najpierw wybierz te zasady o określonym zakresie z początkowego bloku **Azure Information Protection**.

3. W bloku **Etykieta** w sekcji **Ustaw oznaczenie wizualne (np. nagłówek lub stopkę)** skonfiguruj ustawienia dla żądanych oznaczeń wizualnych, a następnie kliknij przycisk **Zapisz**:

    - Aby skonfigurować nagłówek: dla opcji **Dokumenty oznaczone tą etykietą mają nagłówek** wybierz wartość **Wł.**, jeśli chcesz użyć nagłówka, lub **Wył.**, jeśli nie chcesz. Jeśli wybierzesz opcję **Wł.**, następnie należy określić tekst, rozmiar, kolor i wyrównanie nagłówka.
    
    - Aby skonfigurować stopkę: dla opcji **Dokumenty oznaczone tą etykietą mają stopkę** wybierz wartość **Wł.**, jeśli chcesz użyć stopki, lub **Wył.**, jeśli nie chcesz. Jeśli wybierzesz opcję **Wł.**, następnie należy określić tekst, rozmiar, kolor i wyrównanie stopki.
    
    - Aby skonfigurować znak wodny: dla opcji **Dokumenty oznaczone tą etykietą mają znak wodny** wybierz wartość **Wł.**, jeśli chcesz użyć znaku wodnego, lub **Wył.**, jeśli nie chcesz. Jeśli wybierzesz opcję **Wł.**, następnie należy określić tekst, rozmiar i kolor znaku wodnego oraz układ nagłówka. 

4. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## <a name="using-variables-in-the-text-string"></a>Używanie zmiennych w ciągu tekstowym

W ciągu tekstowym dla nagłówka, stopki lub znaku wodnego można używać następujących zmiennych:

- `${Item.Label}` — wybrana etykieta. Na przykład: Wewnętrzne

- `${Item.Name}` — nazwa pliku lub tematu wiadomości e-mail. Na przykład: JulySales.docx

- `${Item.Location}` — ścieżka i nazwa pliku w przypadku dokumentów oraz temat wiadomości e-mail w przypadku wiadomości e-mail. Na przykład: \\\Sales\2016\Q3\JulyReport.docx

- `${User.Name}` — właściciel dokumentu lub wiadomości e-mail (nazwa zalogowanego użytkownika systemu Windows). Na przykład: rsimone

- `${User.PrincipalName}` — właściciel dokumentu lub wiadomości e-mail (adres e-mail zalogowanego klienta usługi Azure Information Protection — UPN). Na przykład: rsimone@vanarsdelltd.com

- `${Event.DateTime}` — data i godzina ustawienia wybranej etykiety. Na przykład: 16.08.2016 13:30
    
Przykład: w przypadku określenia ciągu `Document: ${item.name}  Classification: ${item.label}` dla stopki etykiety Tajne, tekst stopki stosowany dla udokumentowanego nazwanego pliku project.docx będzie następujący: **Document: project.docx  Classification: Tajne**.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


