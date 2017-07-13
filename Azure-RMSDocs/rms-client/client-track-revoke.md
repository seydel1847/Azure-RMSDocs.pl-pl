---
title: "Śledzenie i odwoływanie dokumentów — Azure Information Protection"
description: "Po włączeniu ochrony dokumentów można śledzić ich użycie. W razie potrzeby można również odwołać dostęp do tych dokumentów, jeśli pewne osoby stracą prawo do ich czytania."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 79c02795ca10ff875744f3b6c90cebd582cb8c3e
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Śledzenie i odwoływanie dokumentów podczas korzystania z usługi Azure Information Protection
<a id="track-and-revoke-your-documents-when-you-use-azure-information-protection" class="xliff"></a>

>*Dotyczy: Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

Po włączeniu ochrony dokumentów za pomocą usługi Azure Information Protection można śledzić użycie tych dokumentów. W razie potrzeby można również odwołać dostęp do nich, jeśli pewne osoby stracą prawo do ich czytania. W tym celu należy użyć **witryny śledzenia dokumentów** dostępnej z komputerów z systemem Windows, komputerów Mac, a nawet tabletów i telefonów.

Po uzyskaniu dostępu do tej witryny zaloguj się, aby śledzić swoje dokumenty. Jeśli Twoja organizacja ma [subskrypcję obsługującą śledzenie i odwoływanie dokumentów](https://www.microsoft.com/cloud-platform/azure-information-protection-features) oraz masz licencję na tę subskrypcję, możesz sprawdzić, kto próbował otworzyć zabezpieczone pliki i czy próba ta zakończyła się powodzeniem (nastąpiło pomyślne uwierzytelnienie). Widoczna jest także data i godzina próby otwarcia dokumentu oraz lokalizacja tego zdarzenia. Ponadto:

- Jeśli chcesz zaprzestać udostępniania dokumentu: 
    
    - Kliknij pozycję **Odwołaj dostęp**, podaj okres, przez jaki dokument będzie jeszcze dostępny, i zdecyduj, czy chcesz powiadomić o odwołaniu dostępu osoby, którym dokument był wcześniej udostępniony. Jeśli się na to zdecydujesz, przygotuj dla nich niestandardową wiadomość. Odwołanie udostępnionego dokumentu nie powoduje jego usunięcia, ale blokuje możliwość otwierania go przez autoryzowanych użytkowników:
        
        ![Ikona funkcji Odwołaj dostęp w witrynie śledzenia dokumentów](../media/tracking-site-revoke-access-icon.png)
        
- Jeśli chcesz wyeksportować plik do programu Excel: 
    
    - Kliknij pozycję **Eksportuj do pliku CSV**, aby móc modyfikować dane i tworzyć własne widoki oraz wykresy:
         
        ![Ikona funkcji Eksportuj do pliku CSV w witrynie śledzenia dokumentów](../media/tracking-site-export-icon.png)
         
- Jeśli chcesz skonfigurować powiadomienia e-mail: 
     
    - Kliknij pozycję **Ustawienia** i zdecyduj, czy chcesz otrzymywać pocztą e-mail powiadomienia o dostępie do dokumentu:
        
        ![Ikona funkcji Eksportuj do pliku CSV w witrynie śledzenia dokumentów](../media/tracking-site-settings-email.png)

- Jeśli chcesz śledzić i odwoływać dokumenty udostępnione innym użytkownikom:
    
    - Administratorzy usługi Azure Information Protection mogą śledzić i odwoływać dokumenty chronione dla innych użytkowników, klikając ikonę administratora. Ta ikona jest widoczna tylko dla administratorów:
        
        ![Ikona administratora w witrynie śledzenia dokumentów](../media/tracking-site-admin-icon.png)

Jeśli nie masz uprawnień administracyjnych, możesz śledzić i odwoływać dokumenty, których ochrona została wprowadzona przez Ciebie. Nie można śledzić chronionych wiadomości e-mail za pomocą witryny śledzenia dokumentów.

> [!NOTE] 
> Jeśli administrator skonfigurował kontrolę prywatności dla witryny śledzenia dokumentów, może nie być wyświetlana informacja o użytkownikach z Twojej organizacji, którzy uzyskują dostęp do dokumentów śledzonych przez Ciebie. Administrator może wyłączyć ze śledzenia wszystkich lub tylko niektórych użytkowników. Jednak zawsze możesz odwołać dostęp do śledzonych przez siebie dokumentów.

Aby śledzić dokument, który jest chroniony przez Ciebie, użyj komputera z systemem Windows w celu zarejestrowania go w witrynie śledzenia dokumentów. W tym celu użyj Eksploratora plików lub aplikacji pakietu Office.

## Śledzenie lub odwoływanie dokumentu przy użyciu pakietu Office
<a id="using-office-to-track-or-revoke-the-document" class="xliff"></a>

W przypadku aplikacji pakietu Office (Word, Excel, PowerPoint, Outlook): 

1. Otwórz chroniony dokument, który chcesz śledzić lub odwołać.

2. Na karcie **Narzędzia główne**, w grupie **Ochrona**, kliknij kolejno pozycje **Chroń** > **Śledź i odwołuj**:

    ![Opcja śledzenia użycia](../media/track-usage-callout.png)

Jeśli opcje ochrony nie są wyświetlone, możliwe, że klient usługi Azure Information Protection nie jest zainstalowany na danym komputerze, Twoje aplikacje pakietu Office muszą zostać uruchomione ponownie albo trzeba ponownie uruchomić komputer w celu ukończenia instalacji. Aby uzyskać więcej informacji o sposobie instalowania klienta usługi Azure Information Protection, zobacz temat [Pobieranie i instalowanie klienta usługi Azure Information Protection](install-client-app.md).

## Śledzenie lub odwoływanie dokumentu przy użyciu Eksploratora plików
<a id="using-file-explorer-to-track-or-revoke-the-document" class="xliff"></a>

1. Kliknij chroniony plik prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**.

2. W oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** kliknij opcję **Śledź i odwołuj**.

    ![Ikona śledzenia i odwoływania z okna dialogowego Klasyfikuj i chroń — Azure Information Protection](../media/track-and-revoke.png)


### Śledzenie i odwoływanie zarejestrowanych dokumentów w przeglądarce sieci Web
<a id="using-a-web-browser-to-track-and-revoke-documents-that-you-have-registered" class="xliff"></a>

Po zarejestrowaniu chronionych dokumentów za pomocą Eksploratora plików lub aplikacji pakietu Office, dokumenty te można śledzić i odwoływać przy użyciu obsługiwanej przeglądarki sieci Web:

- Korzystając z komputera z systemem Windows, komputera Mac lub urządzenia przenośnego, przejdź do [witryny śledzenia dokumentów](https://go.microsoft.com/fwlink/?LinkId=529562).

    **Obsługiwane przeglądarki**: zaleca się korzystanie z przeglądarki Internet Explorer 10 lub nowszej, jednak dostęp do witryny śledzenia dokumentów można uzyskać przy użyciu dowolnej z poniższych przeglądarek:

    -   Internet Explorer: wersja 10 lub nowsza

    -   Internet Explorer 9 z poprawką MS12-037: zbiorcza aktualizacja zabezpieczeń programu Internet Explorer z 12 czerwca 2012 r.

    -   Mozilla Firefox: wersja 12 lub nowsza

    -   Apple Safari 5: wersja 5 lub nowsza

    -   Google Chrome: wersja 18 lub nowsza


## Inne instrukcje
<a id="other-instructions" class="xliff"></a>
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

- [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]