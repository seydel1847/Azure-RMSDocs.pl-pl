---
title: "Konfigurowanie oznaczeń wizualnych dla etykiety usługi Azure Information Protection"
description: "Gdy przypisujesz etykietę do dokumentu lub wiadomości e-mail, możesz wybrać kilka opcji, dzięki którym wybrana klasyfikacja będzie łatwo widoczna. Oznaczenia wizualne to nagłówek, stopka i znak wodny."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.openlocfilehash: a65299651abd97adb0fc7641be2f2f3c6f1d8d2f
ms.sourcegitcommit: adb38b008656ac706920a8488fd2beafedadbc97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2017
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Konfigurowanie etykiety pod kątem oznaczeń wizualnych w usłudze Azure Information Protection

>*Dotyczy: Azure Information Protection*

Gdy przypisujesz etykietę do dokumentu lub wiadomości e-mail, możesz wybrać kilka opcji, dzięki którym wybrana klasyfikacja będzie łatwo widoczna. Oznaczenia wizualne to nagłówek, stopka i znak wodny.

Dodatkowe informacje dotyczące tych oznaczeń wizualnych:

- Nagłówki i stopki dotyczą programów Word, Excel, PowerPoint i Outlook.

- Znaki wodne dotyczą programów Word, Excel i PowerPoint:

    - Excel: znaki wodne są widoczne tylko w trybach Podgląd wydruku i Układ strony oraz po wydrukowaniu.
    
    - PowerPoint: znaki wodne są stosowane do wzorca slajdów jako obraz tła.
    
    - Wiele wierszy tekstu jest obsługiwana w przypadku użycia bieżąca wersja klienta usługi Azure Information Protection.

- Można określić tylko ciąg tekstowy lub użyć [zmiennych](#using-variables-in-the-text-string) w celu dynamicznego tworzenia ciągu tekstowego podczas stosowania nagłówka, stopki lub znaku wodnego.

## <a name="when-visual-markings-are-applied"></a>Gdy oznaczenia wizualne są stosowane.

W przypadku wiadomości e-mail oznaczenia wizualne są stosowane, gdy wiadomość e-mail jest wysyłana z programu Outlook.

W przypadku dokumentów oznaczenia wizualne są stosowane w następujący sposób:

- **Dla wersji ogólnodostępnej** klienta Azure Information Protection: 
    
    - W aplikacji pakietu Office oznaczenia wizualne z etykiety są stosowane po zastosowaniu etykiety i zawsze, gdy dokument zostanie zapisany. 
    
    - Gdy dokument jest oznaczona za pomocą Eksploratora plików lub środowiska PowerShell, oznaczenia wizualne nie są natychmiast stosowane, ale są stosowane, gdy ten dokument jest otwarty w aplikacji pakietu Office i zawsze, gdy dokument zostanie zapisany.

- **Dla bieżącej wersji preview** klienta Azure Information Protection: 
    
    - W aplikacji pakietu Office oznaczenia wizualne z etykiety są stosowane po zastosowaniu etykiety. Oznaczenia wizualne, również są stosowane po otwarciu dokumentu etykietą i zapisywaniu dokumentu.  
    
    - Gdy dokument jest oznaczona za pomocą Eksploratora plików lub środowiska PowerShell, oznaczenia wizualne nie są natychmiast stosowane, ale są stosowane, gdy ten dokument jest otwarty w aplikacji pakietu Office i zapisywaniu dokumentu.

## <a name="to-configure-visual-markings-for-a-label"></a>Aby skonfigurować oznaczenia wizualne dla etykiety

Użyj poniższych instrukcji, aby skonfigurować oznaczenia wizualne dla etykiety.

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator zabezpieczeń lub administrator globalny, a następnie przejdź do bloku **Azure Information Protection**.

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

Przykład: w przypadku określenia ciągu `Document: ${item.name}  Classification: ${item.label}` dla stopki etykiety **Ogólne** tekst stopki stosowany dla udokumentowanego nazwanego pliku project.docx będzie następujący: **Document: project.docx Classification: Ogólne**.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
