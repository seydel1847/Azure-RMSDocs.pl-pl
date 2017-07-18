---
title: "Opis ograniczeń użycia | Azure RMS"
description: "Wszystkie aplikacje z obsługą usługi RMS muszą wymuszać ograniczenia użycia."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: E388B16C-ECDA-4696-A040-D457D3C96766
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8862c1be4f084ee1495126b73f4e2adbdeb47acc
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="understanding-usage-restrictions"></a>Opis ograniczeń użycia

Wszystkie aplikacje z obsługą usługi RMS muszą wymuszać ograniczenia użycia. Ograniczenie użycia ma miejsce, gdy użytkownik próbuje wykonać akcję (np. wydrukować dokument), ale zasady usług RMS dla tego dokumentu nie przyznają uprawnienia lub prawa do wykonania tej akcji (np. prawa PRINT).

Uprawnienia użytkownika do danego dokumentu można sprawdzać za pomocą funkcji [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx).

## <a name="designing-with-usage-restrictions"></a>Projektowanie z uwzględnieniem ograniczeń użycia

-   Zapoznaj się ze standardowymi prawami usług RMS

    Pełny zestaw praw usług RMS, które mogą być wymuszane przez aplikację, można znaleźć w temacie [Informacje o ograniczeniach użycia](#usage-restriction-reference).

    Należy zauważyć, że można tworzyć prawa zdefiniowane przez aplikację, specyficzne dla określonej sytuacji, które wykraczają poza standardowe prawa usług RMS.

-   Zidentyfikuj punkty wymuszania ograniczeń użycia

    *Punkt wymuszania ograniczenia użycia* to miejsce w przepływie sterowania aplikacji, w którym konieczne jest wymuszenie ograniczenia użycia. Kilka przykładów typowych punktów wymuszania można znaleźć w temacie [Informacje o ograniczeniach użycia](#usage-restriction-reference).

    Oceń swoją aplikację, aby określić, które punkty wymuszania ograniczeń użycia powinny być stosowane.

    Być może aplikacja nie potrzebuje wszystkich punktów wymuszania opisanych w temacie [Informacje o ograniczeniach użycia](#usage-restriction-reference). Jeśli na przykład aplikacja nie zezwala użytkownikom na drukowanie zawartości, nie musi sprawdzać prawa **IPC\_GENERIC\_PRINT**.

-   Zaktualizuj kod w celu sprawdzania dostępu w każdym punkcie wymuszania ograniczeń

    Wskazówki dotyczące sposobu wymuszania określonych praw można znaleźć w temacie [Informacje o ograniczeniach użycia](#usage-restriction-reference).

## <a name="usage-restriction-reference"></a>Informacje o ograniczeniach użycia

Ograniczenia użycia są określane przy użyciu następujących stałych.

Każde prawo użytkownika, wymienione w prawej kolumnie usługi AD RMS, ma opis, punkt wymuszania i sugerowane metody wymuszania.

| Prawo usługi AD RMS/opis | Jak wymusić |
|--------------------------|----------------|
|**IPC_GENERIC_ALL** <br><br> Przyznaje wszystkie prawa użytkownikowi. <br><br> **Typowe punkty wymuszania**: brak |To prawo jest używane przez system. Zazwyczaj nie powinno być sprawdzane bezpośrednio. <br><br> Element [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx) używa tego prawa do określenia, czy użytkownikowi należy przydzielić inne uprawnienia, jak w poniższym przykładzie.<br><br> `/* fAccessGranted is set to TRUE if either the IPC_GENERIC_WRITE or the IPC_GENERIC_ALL right is granted */` <br><br> `IpcAccessCheck(hKey, IPC_GENERIC_WRITE, &fAccessGranted);`|
|**IPC_GENERIC_READ** <br><br> Prawo do odczytu zawartości dokumentu. <br><br> **Typowe punkty wymuszania**: ładowanie dokumentu|Nie ładuj ani nie prezentuj zawartości dokumentu.|
|**IPC_GENERIC_WRITE** <br><br> Prawo do edycji zawartości dokumentu. <br><br> **Typowe punkty wymuszania**: modyfikacja dokumentu|Ustaw wszystkie kontrolki interfejsu użytkownika używane do modyfikowania zawartości dokumentu jako nieedytowalne. <br><br> Wyłącz wszystkie elementy menu, które mogą powodować zmiany w dokumencie. Typowymi przykładami są opcje **Edycja** > **Wytnij**, **Edycja** > **Wklej** i **Wstaw**. <br><br>Wyłącz wszystkie elementy menu skrótów, które mogą powodować zmiany w dokumencie.|
|Brak prawa usługi AD RMS <br><br> Brak opisu <br><br> **Typowe punkty wymuszania**: Zapisz | Wyłącz menu **Plik** > **Zapisz**. <br><br> **Uwaga** To prawo nie kontroluje opcji **Plik** > **Zapisz jako**, ponieważ prawo nie reprezentuje zmiany w oryginalnym dokumencie.<br><br> Wyłącz wszelkie skróty klawiaturowe, które mogą posłużyć do wyzwalania opcji Zapisz (np. Ctrl + S).<br><br> **Porada** Najlepszym rozwiązaniem jest zaktualizowanie podstawowego kodu opcji **Plik** > **Zapisz** w taki sposób, aby brak takiego prawa u użytkownika powodował błąd. Jest to dodatkowe zabezpieczenie na wypadek pominięcia jakichkolwiek mechanizmów środowiska użytkownika, które mogą służyć do wyzwolenia opcji zapisywania. |
|**IPC_GENERIC_EXTRACT** <br><br> Prawo do wyodrębniania zawartości z formatu chronionego i umieszczanie jej w formacie niechronionym. <br><br> **Typowe punkty wymuszania**: Kopiuj do Schowka | Wyłącz menu **Edycja** > **Kopiuj**. Wyłącz menu **Edycja** > **Wytnij**. <br><br>Wyłącz funkcje **Kopiuj** i **Wytnij** we wszystkich menu skrótów.<br><br>Wyłącz wszelkie skróty klawiaturowe, które mogą posłużyć do wyzwalania opcji Kopiuj (np. Ctrl + C lub Ctrl + X).<br><br>Zaktualizuj programy obsługi komunikatów okien pod kątem uprawnienia [**WM_CUT**](https://msdn.microsoft.com/library/ms649023), aby odrzucały kopiowanie danych, jeśli użytkownik nie ma tego prawa. Jeśli okno używa domyślnych programów obsługi komunikatów systemu Windows, utwórz podklasę tego okna i wprowadź własne programy obsługi dla uprawnień **WM_COPY** i **WM_CUT**. |
|Brak prawa usługi AD RMS <br><br> Brak opisu <br><br> **Typowe punkty wymuszania**: Zapisz jako |W oknie dialogowym **Zapisywanie jako** wyłącz wszelkie formaty plików, które umożliwiałyby zapisanie dokumentu bez ochrony przez usługę RMS.|
|Brak prawa usługi AD RMS <br><br> Brak opisu <br><br> **Typowe punkty wymuszania**: Alt+PrtScn|Wywołaj element [IpcProtectWindow](https://msdn.microsoft.com/library/hh535268.aspx) we wszystkich oknach, które renderują zawartość dokumentu.|
|**IPC_GENERIC_EXPORT** <br><br> Prawo do wyodrębniania zawartości z formatu chronionego i umieszczanie jej w innym formacie chronionym przez usługi AD RMS. <br><br> **Typowe punkty wymuszania**: Zapisz jako|W oknie dialogowym **Zapisywanie jako** wyłącz możliwość zapisywania w jakimkolwiek innym formacie pliku.<br><br>**Porada** Najlepszym rozwiązaniem jest zaktualizowanie podstawowego kodu opcji **Plik** > **Zapisz jako** w taki sposób, aby próba zapisania tego pliku w innym formacie przez użytkownika, który nie ma tego prawa, powodowała błąd. Jest to dodatkowe zabezpieczenie na wypadek pominięcia jakichkolwiek mechanizmów środowiska użytkownika, które mogą służyć do wyzwolenia opcji Zapisz jako.|
|**IPC_GENERIC_PRINT** <br><br> Prawo do drukowania zawartości dokumentu. <br><br> **Typowe punkty wymuszania**: Drukuj|Wyłącz menu **Plik** > **Drukuj**.<br><br>Wyłącz wszelkie skróty klawiaturowe, które mogą posłużyć do wyzwalania opcji Drukuj (np. Ctrl + P).<br><br>Wyłącz elementy menu skrótów, które mogą wyzwalać opcję drukowania.<br><br>**Porada** Najlepszym rozwiązaniem jest zaktualizowanie podstawowego kodu opcji **Plik** > **Drukuj** w taki sposób, aby brak tego prawa u użytkownika powodował błąd. Jest to dodatkowe zabezpieczenie na wypadek pominięcia jakichkolwiek mechanizmów środowiska użytkownika, które mogą służyć do wyzwolenia opcji drukowania.|
|**IPC_GENERIC_COMMENT** <br><br> Niektóre aplikacje obsługują możliwość dodawania komentarzy i adnotacji do dokumentu bez aktualizowania podstawowej zawartości dokumentu.<br><br>To prawo zezwala użytkownikowi na dostęp do tej funkcji. <br><br> **Typowe punkty wymuszania**: <br><br> Recenzja > Wstaw komentarz <br><br> Recenzja > Usuń komentarz | Wyłącz wszystkie elementy menu, które mogą służyć do modyfikowania komentarzy lub adnotacji w dokumencie. Przykłady: **Recenzja** > **Wstaw komentarz** i **Recenzja** > **Usuń komentarz**. <br><br>Wyłącz wszelkie skróty klawiaturowe, które mogą wyzwalać opcję modyfikacji komentarzy w dokumencie.<br><br>**Uwaga** Domyślne wdrożenie wymaga, aby uprawnienia **IPC_GENERIC_COMMENT** i **IPC_GENERIC_WRITE** utrwalały nowe komentarze w pliku. Aplikacje mogą umożliwić obsługę w przypadku przyznania prawa **IPC_GENERIC_COMMENT** i nieprzyznania prawa **IPC_GENERIC_WRITE**. W takim przypadku można zezwolić na użycie opcji Zapisz, jeśli modyfikacje dokumentu są ograniczone wyłącznie do komentarzy.|
|**IPC_VIEW_RIGHTS** <br><br> Brak opisu <br><br> **Typowe punkty wymuszania**: brak|Wymuszane przez system. System nie pozwoli deweloperowi na wykonanie zapytania o [**listę praw użytkownika**](https://msdn.microsoft.com/library/hh535286.aspx) z licencji, jeśli to prawo nie zostało przyznane.
|**IPC_EDIT_RIGHTS** <br><br> Niektóre aplikacje umożliwiają użytkownikom modyfikowanie zbioru użytkowników i praw dotyczących zawartości chronionej przez usługę AD RMS.<br><br>To prawo zezwala użytkownikowi na dostęp do tej funkcji. <br><br> **Typowe punkty wymuszania**: prawa aplikacji do edycji kontrolek interfejsu użytkownika|Blokuje użytkownikowi dostęp do wszelkich elementów interfejsu użytkownika, których można użyć do edycji zasad usługi RMS dla dokumentu.|


## <a name="related-topics"></a>Tematy pokrewne

* [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]