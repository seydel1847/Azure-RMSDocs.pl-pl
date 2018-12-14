---
title: Śledzenie i odwoływanie dokumentów — Azure Information Protection
description: Po włączeniu ochrony dokumentów można śledzić ich użycie. W razie potrzeby można również odwołać dostęp do tych dokumentów, jeśli pewne osoby stracą prawo do ich czytania.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 251de2d7e959dc46bcf95c003fd8924cc4c34d13
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305232"
---
# <a name="user-guide-track-and-revoke-your-documents-when-you-use-azure-information-protection"></a>Podręcznik użytkownika: Śledzenie i odwoływanie dokumentów podczas korzystania z usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), system Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

Po włączeniu ochrony dokumentów za pomocą usługi Azure Information Protection można śledzić użycie tych dokumentów. W razie potrzeby można również odwołać dostęp do nich, jeśli pewne osoby stracą prawo do ich czytania. Służy do tego **witryna śledzenia dokumentów**. Jest ona dostępna z komputerów z systemem Windows, komputerów Mac, a nawet tabletów i telefonów.

Po uzyskaniu dostępu do tej witryny zaloguj się, aby śledzić swoje dokumenty. Jeśli Twoja organizacja ma [subskrypcję obsługującą śledzenie i odwoływanie dokumentów](https://www.microsoft.com/cloud-platform/azure-information-protection-features) oraz masz licencję na tę subskrypcję, możesz sprawdzić, kto próbował otworzyć zabezpieczone pliki i czy próba ta zakończyła się powodzeniem (nastąpiło pomyślne uwierzytelnienie). Widoczna jest także data i godzina próby otwarcia dokumentu oraz lokalizacja tego zdarzenia. Jednak w rzadkich przypadkach lokalizacji zgłoszone mogą być niedokładne. Na przykład gdy użytkownik, otwarcie chronionego dokumentu korzysta z połączenia sieci VPN lub komputera ma adres IPv6.

Akcje, które można wykonać w witrynie śledzenia dokumentów:

- Jeśli chcesz zaprzestać udostępniania dokumentu: 
    
    - Kliknij pozycję **Odwołaj dostęp**. Podaj okres, przez jaki dokument będzie jeszcze dostępny. Możesz powiadomić o odwołaniu dostępu osoby, którym dokument został wcześniej udostępniony. Jeśli się na to zdecydujesz, przygotuj dla nich własną wiadomość. Odwołanie udostępnionego dokumentu nie powoduje jego usunięcia, ale blokuje możliwość otwierania go przez autoryzowanych użytkowników:
        
        ![Ikona funkcji Odwołaj dostęp w witrynie śledzenia dokumentów](../media/tracking-site-revoke-access-icon.png)
        
- Jeśli chcesz wyeksportować plik do programu Excel: 
    
    - Kliknij pozycję **Eksportuj do pliku CSV**, aby móc modyfikować dane i tworzyć własne widoki oraz wykresy:
         
        ![Ikona funkcji Eksportuj do pliku CSV w witrynie śledzenia dokumentów](../media/tracking-site-export-icon.png)
         
- Jeśli chcesz skonfigurować powiadomienia e-mail: 
     
    - Kliknij pozycję **Ustawienia** i zdecyduj, czy chcesz otrzymywać pocztą e-mail powiadomienia o dostępie do dokumentu:
        
        ![Ikona funkcji Eksportuj do pliku CSV w witrynie śledzenia dokumentów](../media/tracking-site-settings-email.png)

- Jeśli chcesz śledzić i odwoływać dokumenty udostępnione innym użytkownikom:
    
    - Klikając ikonę administratora, administratorzy usługi Azure Information Protection mogą śledzić chronione dokumenty i odwoływać dostęp do nich dla użytkowników, którzy zarejestrowali swoje dokumenty w witrynie śledzenia dokumentów. Ta ikona jest widoczna tylko dla administratorów:
        
        ![Ikona administratora w witrynie śledzenia dokumentów](../media/tracking-site-admin-icon.png)
        
        Jeśli nie widzisz tę ikonę, mimo iż Administrator globalny, to, że nie udostępniasz jeszcze żadnych dokumentów. W takim przypadku należy użyć następującego adresu URL do uzyskania dostępu do witryny śledzenia dokumentów: https://portal.azurerms.com/#/admin

Jeśli nie masz uprawnień administracyjnych, możesz śledzić i odwoływać dokumenty, których ochrona została wprowadzona przez Ciebie. Nie można śledzić chronionych wiadomości e-mail za pomocą witryny śledzenia dokumentów.

> [!NOTE] 
> Jeśli administrator skonfigurował kontrolę prywatności dla witryny śledzenia dokumentów, może nie być wyświetlana informacja o użytkownikach z Twojej organizacji, którzy uzyskują dostęp do dokumentów śledzonych przez Ciebie. Administrator może wyłączyć ze śledzenia wszystkich lub tylko niektórych użytkowników. Jednak zawsze możesz odwołać dostęp do śledzonych przez siebie dokumentów.

Aby śledzić dokument, który jest chroniony przez Ciebie, użyj komputera z systemem Windows w celu zarejestrowania go w witrynie śledzenia dokumentów. W tym celu użyj Eksploratora plików lub aplikacji pakietu Office.

## <a name="using-office-to-track-or-revoke-the-document"></a>Śledzenie lub odwoływanie dokumentu przy użyciu pakietu Office

Dla pakietu Office aplikacji, Word, Excel i PowerPoint: 

1. Otwórz chroniony dokument, który chcesz śledzić lub odwołać.

2. Na karcie **Narzędzia główne**, w grupie **Ochrona**, kliknij kolejno pozycje **Chroń** > **Śledź i odwołuj**:

    ![Opcja śledzenia użycia](../media/track-usage-callout.png)
    
    Jeśli te opcje nie są widoczne w aplikacjach pakietu Office, prawdopodobnie wystąpił jeden z następujących powodów:
    
    - Na komputerze nie jest zainstalowany klient usługi Azure Information Protection.
    
    - Należy uruchomić ponownie aplikacje pakietu Office.
    
    - Aby ukończyć instalację, należy uruchomić ponownie komputer.
    
Aby uzyskać więcej informacji o sposobie instalowania klienta usługi Azure Information Protection, zobacz temat [Pobieranie i instalowanie klienta usługi Azure Information Protection](install-client-app.md).

## <a name="using-file-explorer-to-track-or-revoke-the-document"></a>Śledzenie lub odwoływanie dokumentu przy użyciu Eksploratora plików

1. Kliknij chroniony plik prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**.

2. W oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** kliknij opcję **Śledź i odwołuj**.

    ![Ikona śledzenia i odwoływania z okna dialogowego Klasyfikuj i chroń — Azure Information Protection](../media/track-and-revoke.png)


### <a name="using-a-web-browser-to-track-and-revoke-documents-that-you-have-registered"></a>Śledzenie i odwoływanie zarejestrowanych dokumentów w przeglądarce sieci Web

Po zarejestrowaniu chronionych dokumentów za pomocą Eksploratora plików lub aplikacji pakietu Office, dokumenty te można śledzić i odwoływać przy użyciu obsługiwanej przeglądarki sieci Web:

- Korzystając z komputera z systemem Windows, komputera Mac lub urządzenia przenośnego, przejdź do [witryny śledzenia dokumentów](https://go.microsoft.com/fwlink/?LinkId=529562).

    **Obsługiwane przeglądarki**: Firma Microsoft zaleca używanie programu Internet Explorer, który jest co najmniej w wersji 10, ale można użyć dowolnej z poniższych przeglądarek służące do witryny śledzenia dokumentów:

    - Program Internet Explorer: Co najmniej w wersji 10

    - Internet Explorer 9 z co najmniej MS12-037: Zbiorcza aktualizacja zabezpieczeń programu Internet Explorer: 12 czerwca 2012

    - Mozilla Firefox: Co najmniej wersja 12

    - Apple Safari 5: Co najmniej w wersji 5

    - Google Chrome: Co najmniej wersja 18 lub


## <a name="other-instructions"></a>Inne instrukcje
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

- [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Dodatkowe informacje dla administratorów    
Zobacz [Konfigurowanie i używanie śledzenia dokumentów usługi Azure Information Protection](client-admin-guide-document-tracking.md) z [podręczniku administratora](client-admin-guide.md).
