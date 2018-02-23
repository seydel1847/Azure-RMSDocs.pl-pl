---
title: "Konfigurowanie oznaczeń wizualnych dla etykiety usługi Azure Information Protection"
description: "Gdy przypisujesz etykietę do dokumentu lub wiadomości e-mail, możesz wybrać kilka opcji, dzięki którym wybrana klasyfikacja będzie łatwo widoczna. Oznaczenia wizualne to nagłówek, stopka i znak wodny."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.openlocfilehash: 03e7e2a4e2fc6dc75bd6c56c117c627e0c854f98
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Konfigurowanie etykiety pod kątem oznaczeń wizualnych w usłudze Azure Information Protection

>*Dotyczy: Azure Information Protection*

Gdy przypisujesz etykietę do dokumentu lub wiadomości e-mail, możesz wybrać kilka opcji, dzięki którym wybrana klasyfikacja będzie łatwo widoczna. Oznaczenia wizualne to nagłówek, stopka i znak wodny.

Dodatkowe informacje dotyczące tych oznaczeń wizualnych:

- Nagłówki i stopki dotyczą programów Word, Excel, PowerPoint i Outlook.

- Znaki wodne dotyczą programów Word, Excel i PowerPoint:

    - Excel: znaki wodne są widoczne tylko w trybach Podgląd wydruku i Układ strony oraz po wydrukowaniu.
    
    - PowerPoint: znaki wodne są stosowane do wzorca slajdów jako obraz tła.
    
    - Wiele wierszy tekstu są obsługiwane.

- Można określić tylko ciąg tekstowy lub użyć [zmiennych](#using-variables-in-the-text-string) w celu dynamicznego tworzenia ciągu tekstowego podczas stosowania nagłówka, stopki lub znaku wodnego.

- Znaczniki wizualne obsługuje tylko jeden język.

## <a name="when-visual-markings-are-applied"></a>Gdy oznaczenia wizualne są stosowane.

W przypadku wiadomości e-mail oznaczenia wizualne są stosowane, gdy wiadomość e-mail jest wysyłana z programu Outlook.

W przypadku dokumentów oznaczenia wizualne są stosowane w następujący sposób:

- W aplikacji pakietu Office oznaczenia wizualne z etykiety są stosowane po zastosowaniu etykiety. Oznaczenia wizualne, również są stosowane po otwarciu dokumentu etykietą i zapisywaniu dokumentu.  

- Gdy dokument jest oznaczona za pomocą Eksploratora plików lub środowiska PowerShell, oznaczenia wizualne nie są natychmiast stosowane, ale są stosowane, gdy ten dokument jest otwarty w aplikacji pakietu Office i zapisywaniu dokumentu.

## <a name="to-configure-visual-markings-for-a-label"></a>Aby skonfigurować oznaczenia wizualne dla etykiety

Użyj poniższych instrukcji, aby skonfigurować oznaczenia wizualne dla etykiety.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Jeśli etykietę, którą chcesz skonfigurować będą stosowane do wszystkich użytkowników, pozostają **usługi Azure Information Protection — globalne zasady** bloku.
    
    Jeśli trwa etykietę, którą chcesz skonfigurować [zakres zasad](configure-policy-scope.md) tak, aby dotyczył tylko wybrani użytkownicy z **zasady** zaznaczenia menu, wybierz opcję **zakres zasad**. Następnie wybierz zakresie zasad z **zasady usługi Azure Information Protection - zakres** bloku.

3. W bloku **Etykieta** w sekcji **Ustaw oznaczenie wizualne (np. nagłówek lub stopkę)** skonfiguruj ustawienia dla żądanych oznaczeń wizualnych, a następnie kliknij przycisk **Zapisz**:
    
    - Aby skonfigurować nagłówek: dla opcji **Dokumenty oznaczone tą etykietą mają nagłówek** wybierz wartość **Wł.**, jeśli chcesz użyć nagłówka, lub **Wył.**, jeśli nie chcesz. W przypadku wybrania **na**, następnie określ nagłówek tekst, rozmiar, [czcionki](#setting-the-font-name), [kolor](#setting-the-font-color)i wyrównanie nagłówka.
    
    - Aby skonfigurować stopkę: dla opcji **Dokumenty oznaczone tą etykietą mają stopkę** wybierz wartość **Wł.**, jeśli chcesz użyć stopki, lub **Wył.**, jeśli nie chcesz. W przypadku wybrania **na**, następnie określ stopki tekst, rozmiar, [czcionki](#setting-the-font-name), [kolor](#setting-the-font-color)i wyrównanie stopki.
    
    - Aby skonfigurować znak wodny: dla opcji **Dokumenty oznaczone tą etykietą mają znak wodny** wybierz wartość **Wł.**, jeśli chcesz użyć znaku wodnego, lub **Wył.**, jeśli nie chcesz. W przypadku wybrania **na**, następnie określ znak wodny tekst, rozmiar, [czcionki](#setting-the-font-name), [kolor](#setting-the-font-color)i wyrównanie znaku wodnego.

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

## <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Ustawienie różnych oznaczenia wizualne dla programu Word, Excel, PowerPoint i Outlook

To ustawienie jest obecnie w wersji zapoznawczej i wymaga wersja klienta usługi Azure Information Protection.

Domyślnie oznaczeń wizualnych, które określisz są stosowane przez program Word, Excel, PowerPoint i Outlook. Jednak można określić oznaczenia wizualne dla typu aplikacji pakietu Office przy użyciu zmiennej instrukcji "If.App" w ciągu tekstowym, a Określ typ aplikacji przy użyciu wartości **Word**, **Excel**, **PowerPoint**, lub **Outlook**. Można również skrócić te wartości i abbreiwhich jest niezbędne, jeśli chcesz określić więcej niż jedną w tej samej instrukcji If.App.

Należy użyć następującej składni:

    ${If.App.<application type>}<your visual markings text> ${If.End}

Ta składnia w tej instrukcji jest rozróżniana wielkość liter.

Przykłady:

- **Ustaw tekst nagłówka dla tylko dokumenty programu Word:**
    
    `${If.App.Word}This Word document is sensitive ${If.End}`
    
    W Word tylko nagłówki dokumentu etykiety stosuje tekst nagłówka "poufne jest ten dokument programu Word". Tekst nagłówka nie jest stosowany do innych aplikacjach pakietu Office.

- **Ustawić tekst stopki dla programów Word, Excel i Outlook, a tekst stopki różnych dla programu PowerPoint.**
    
    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`
    
    W programach Word, Excel i Outlook etykiety stosuje się tekst stopki "tej zawartości jest poufne". W programie PowerPoint etykiety stosuje się tekst stopki "poufne jest tej prezentacji."

- **Ustawianie tekstu znaku wodnego określonych dla programów Word i PowerPoint, a następnie znaku wodnego tekstu dla programu Word, Excel i PowerPoint:**
    
    `${If.App.WP}This content is ${If.End}Confidential`
    
    W programach Word i PointPoint etykiety stosuje tekstu znaku wodnego "tej zawartości jest poufne". W programie Excel etykiety stosuje tekstu znaku wodnego "Poufne". W programie Outlook etykiety nie tekstu znaku wodnego, znaki wodne jako oznaczenia wizualne nie są obsługiwane dla programu Outlook.

### <a name="setting-the-font-name"></a>Ustawienie nazwy czcionki

To ustawienie jest obecnie w przeglądzie.

Calibri jest domyślną czcionkę dla nagłówków, stopek i tekstu znaku wodnego. Jeśli określono nazwę alternatywną czcionki, upewnij się, że jest ona dostępna na urządzenia klienckie, które będą stosowane żądanych oznaczeń. W przeciwnym razie czcionki, który będzie używany jest deterministyczna. 

Jeśli masz wersja klienta usługi Azure Information Protection, a czcionka określony nie jest dostępna, klient powraca przy użyciu czcionki Calibri.

### <a name="setting-the-font-color"></a>Ustawianie koloru czcionki

Można wybrać z listy dostępnych kolorów lub określić niestandardowego koloru przez wprowadzenie kodu szesnastkowych Trzykolumnowa składników (RGB) czerwony, zielonemu i niebieskiemu koloru. Przykład: **#DAA520**. 

Jeśli potrzebujesz odwołania te kodów [kolory według nazwy](https://msdn.microsoft.com/library/aa358802\(v=vs.85\).aspx) w sieci MSDN dokumentacji stanowi punkt wyjścia przydatne. Możesz również znaleźć kody w wielu aplikacjach, które umożliwiają edytowanie obrazów. Na przykład Microsoft Paint pozwala wybrać paletę kolorów niestandardowych i wartości RGB są automatycznie wyświetlane, które można następnie skopiować.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
