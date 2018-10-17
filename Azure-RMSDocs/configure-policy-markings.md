---
title: Konfigurowanie oznaczeń wizualnych dla etykiety usługi Azure Information Protection
description: Gdy przypisujesz etykietę do dokumentu lub wiadomości e-mail, możesz wybrać kilka opcji, dzięki którym wybrana klasyfikacja będzie łatwo widoczna. Oznaczenia wizualne to nagłówek, stopka i znak wodny.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/16/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.openlocfilehash: dbc63a0ddca9e7583693219103268048b524121c
ms.sourcegitcommit: 6a732226a3c97fc06fcf815fbbb24a2e2faae209
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49358979"
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Konfigurowanie etykiety pod kątem oznaczeń wizualnych w usłudze Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Gdy przypisujesz etykietę do dokumentu lub wiadomości e-mail, możesz wybrać kilka opcji, dzięki którym wybrana klasyfikacja będzie łatwo widoczna. Oznaczenia wizualne to nagłówek, stopka i znak wodny.

Dodatkowe informacje na temat tych oznaczeń wizualnych:

- Nagłówki i stopki dotyczą programów Word, Excel, PowerPoint i Outlook.

- Znaki wodne dotyczą programów Word, Excel i PowerPoint:

    - Excel: znaki wodne są widoczne tylko w trybach Podgląd wydruku i Układ strony oraz po wydrukowaniu.
    
    - PowerPoint: znaki wodne są stosowane do wzorca slajdów jako obraz tła. Na **widoku** karcie **wzorca slajdów**, upewnij się, że **Ukryj grafiki w tle** nie zaznaczono pole wyboru.
    
    - Wiele wierszy tekstu są obsługiwane.

- Ciąg maksymalnej długości:
    
    - Maksymalna długość ciągu wprowadzona w nagłówkach i stopkach to 1024 znaki. Jednak program Excel ma całkowity limit 255 znaków w nagłówkach i stopkach stron. Po wprowadzeniu długi ciąg w nagłówkach i stopkach stron w programie Excel, ten tekst może być obcięty do 255 znaków lub mniej.
    
    - Maksymalna długość ciągu dla znaki wodne, które można wprowadzić to 255 znaków.

- Można określić tylko ciąg tekstowy lub użyć [zmiennych](#using-variables-in-the-text-string) w celu dynamicznego tworzenia ciągu tekstowego podczas stosowania nagłówka, stopki lub znaku wodnego.

- Word, PowerPoint i Outlook obsługuje oznaczeń wizualnych w różnych kolorach. Oznaczenia wizualne, które są skonfigurowane do obsługi kolory zawsze wyświetlane jako czarny w programie Excel.

- Oznaczenia wizualne obsługuje tylko jeden język.

## <a name="when-visual-markings-are-applied"></a>Po zastosowaniu oznaczenia wizualne

W przypadku wiadomości e-mail oznaczenia wizualne są stosowane, gdy wiadomość e-mail jest wysyłana z programu Outlook.

W przypadku dokumentów oznaczenia wizualne są stosowane w następujący sposób:

- W aplikacji pakietu Office oznaczenia wizualne z etykiety są stosowane po zastosowaniu etykiety. Oznaczenia wizualne są również stosowane, gdy etykietą dokument jest otwarty i pierwszym zapisaniu dokumentu.  

- Jeśli dokument jest oznaczona etykietą za pomocą Eksploratora plików, programu PowerShell lub skanera usługi Azure Information Protection: oznaczenia wizualne nie są natychmiast stosowane, ale są stosowane przez klienta usługi Azure Information Protection, po otwarciu dokumentu w aplikacji pakietu Office i pierwszym zapisaniu dokumentu.
    
    Wyjątek jest w przypadku używania [zapisywania](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) w pakiecie Office 2016 dla plików, które są zapisywane w usłudze SharePoint Online, OneDrive lub OneDrive dla firm: podczas zapisywania jest włączona, oznaczenia wizualne nie są stosowane, jeśli nie skonfigurujesz [ Zaawansowane ustawienia klienta](./rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background) włączyć klasyfikacji, aby uruchomić w sposób ciągły w tle. 

## <a name="to-configure-visual-markings-for-a-label"></a>Aby skonfigurować oznaczenia wizualne dla etykiety

Użyj poniższych instrukcji, aby skonfigurować oznaczenia wizualne dla etykiety.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **etykiety** opcji menu: na **usługi Azure Information Protection — etykiety** bloku, wybierz etykietę, który zawiera element wizualny oznaczenia, które chcesz dodać lub zmienić.

3. Na **etykiety** bloku, w **Ustaw oznaczenie wizualne (np. nagłówka lub stopki)** konfigurowania ustawień pod kątem oznaczeń wizualnych, które, a następnie kliknij pozycję **Zapisz**:
    
    - Aby skonfigurować nagłówek: dla opcji **Dokumenty oznaczone tą etykietą mają nagłówek** wybierz wartość **Wł.**, jeśli chcesz użyć nagłówka, lub **Wył.**, jeśli nie chcesz. Jeśli wybierzesz **na**, następnie określ nagłówek tekst, rozmiar, [czcionki](#setting-the-font-name), [kolor](#setting-the-font-color)i wyrównanie nagłówka.
    
    - Aby skonfigurować stopkę: dla opcji **Dokumenty oznaczone tą etykietą mają stopkę** wybierz wartość **Wł.**, jeśli chcesz użyć stopki, lub **Wył.**, jeśli nie chcesz. Jeśli wybierzesz **na**, następnie określ stopki tekst, rozmiar, [czcionki](#setting-the-font-name), [kolor](#setting-the-font-color)i wyrównanie stopki.
    
    - Aby skonfigurować znak wodny: dla opcji **Dokumenty oznaczone tą etykietą mają znak wodny** wybierz wartość **Wł.**, jeśli chcesz użyć znaku wodnego, lub **Wył.**, jeśli nie chcesz. Jeśli wybierzesz **na**, następnie określ znak wodny tekst, rozmiar, [czcionki](#setting-the-font-name), [kolor](#setting-the-font-color)i wyrównanie znaku wodnego.
    
Po kliknięciu **Zapisz**, zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma już opcji publikowania oddzielne.


## <a name="using-variables-in-the-text-string"></a>Używanie zmiennych w ciągu tekstowym

W ciągu tekstowym dla nagłówka, stopki lub znaku wodnego można używać następujących zmiennych:

- `${Item.Label}` — wybrana etykieta. Na przykład: Wewnętrzne

- `${Item.Name}` — nazwa pliku lub tematu wiadomości e-mail. Na przykład: JulySales.docx

- `${Item.Location}` — ścieżka i nazwa pliku w przypadku dokumentów oraz temat wiadomości e-mail w przypadku wiadomości e-mail. Na przykład: \\\Sales\2016\Q3\JulyReport.docx

- `${User.Name}` — właściciel dokumentu lub wiadomości e-mail (nazwa zalogowanego użytkownika systemu Windows). Na przykład: rsimone

- `${User.PrincipalName}` — właściciel dokumentu lub wiadomości e-mail (adres e-mail zalogowanego klienta usługi Azure Information Protection — UPN). Na przykład: rsimone@vanarsdelltd.com

- `${Event.DateTime}` — data i godzina ustawienia wybranej etykiety. Na przykład: 16.08.2016 13:30

Przykład: w przypadku określenia ciągu `Document: ${item.name}  Classification: ${item.label}` dla stopki etykiety **Ogólne** tekst stopki stosowany dla udokumentowanego nazwanego pliku project.docx będzie następujący: **Document: project.docx Classification: Ogólne**.

## <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Ustawienie różnych pod kątem oznaczeń wizualnych programu Word, Excel, PowerPoint i Outlook

Domyślnie oznaczenia wizualne, które określisz są stosowane dla programu Word, Excel, PowerPoint i Outlook. Jednak podczas możesz określić oznaczeń wizualnych dla typu aplikacji pakietu Office można użyć zmiennej instrukcji "If.App" w ciągu tekstowym i zidentyfikować typ aplikacji przy użyciu wartości **Word**, **Excel**, **PowerPoint**, lub **Outlook**. Można również skrócić te wartości, a abbreiwhich jest konieczne, jeśli chcesz określić więcej niż jeden w tej samej instrukcji If.App.

Należy użyć następującej składni:

    ${If.App.<application type>}<your visual markings text> ${If.End}

Ta składnia w tej instrukcji jest uwzględniana wielkość liter.

Przykłady:

- **Ustaw tekst nagłówka dla tylko dokumenty programu Word:**
    
    `${If.App.Word}This Word document is sensitive ${If.End}`
    
    Word tylko nagłówki dokumentu stosuje się etykietę tekst nagłówka "ten dokument programu Word to poufne". Brak tekstu nagłówka jest stosowany do innych aplikacjach pakietu Office.

- **Ustaw tekst stopki dla programu Word, Excel i Outlook i tekst stopki różnych dla programu PowerPoint:**
    
    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`
    
    W programach Word, Excel i Outlook stosuje się etykietę tekst stopki "tej zawartości jest poufne." W programie PowerPoint stosuje się etykietę tekst stopki "w tej prezentacji są poufne."

- **Ustawianie tekstu znaku wodnego określonych dla programów Word i PowerPoint, a następnie limitu tekstu dla programu Word, Excel i PowerPoint:**
    
    `${If.App.WP}This content is ${If.End}Confidential`
    
    W programach Word i PointPoint stosuje się etykietę tekstu znaku wodnego "tej zawartości jest poufne". W programie Excel etykieta dotyczy tekstu znaku wodnego "Poufne". W programie Outlook etykieta nie dowolnego tekstu znaku wodnego, znaki wodne, jak oznaczenia wizualne nie są obsługiwane dla programu Outlook.

### <a name="setting-the-font-name"></a>Ustawianie nazwy czcionki

Calibri jest domyślna czcionka nagłówki, stopki i tekstu znaku wodnego. Jeśli określisz nazwę czcionki alternatywnego, upewnij się, że jest ona dostępna na urządzeniach klienckich, które będą stosowane oznaczeń wizualnych. 

Jeśli czcionki określony jest niedostępny, klient powraca do używana czcionka Calibri.

### <a name="setting-the-font-color"></a>Ustawianie koloru czcionki

Można wybrać z listy dostępnych kolorów lub określić kolor niestandardowy, wprowadzając szesnastkowy tryplet dla składników czerwonego, zielonego i niebieskiego (RGB) koloru. Przykład: **#DAA520**. 

Jeśli potrzebujesz odwołanie o tych kodach [Colors by Name](https://msdn.microsoft.com/library/aa358802\(v=vs.85\).aspx) z MSDN dokumentacja jest dobry punkt wyjścia. Możesz również znaleźć te kody w wielu aplikacjach, które pozwalają edytować obrazów. Na przykład Microsoft Paint pozwala wybrać niestandardowy kolor z palety i wartości RGB są automatycznie wyświetlane, które można skopiować.

## <a name="next-steps"></a>Kolejne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

