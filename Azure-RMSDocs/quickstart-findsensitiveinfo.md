---
title: Przewodnik Szybki Start — znajdowanie jakich informacji poufnych, masz w plików przechowywanych w środowisku lokalnym za pomocą skanera usługi Azure Information Protection
description: Użyj skanera usługi Azure Information Protection, aby znaleźć jakich informacji poufnych, masz w plików przechowywanych w środowisku lokalnym.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 68b070340767b0590711efeaae35edda884627c6
ms.sourcegitcommit: 80de8762953bdea2553c48b02259cd107d0c71dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51027214"
---
# <a name="quickstart-find-what-sensitive-information-you-have-in-files-stored-on-premises"></a>Szybki Start: Znajdź jakie poufne informacje, które masz w plików przechowywanych w środowisku lokalnym

W tym przewodniku Szybki Start będziesz zainstalowaniu i skonfigurowaniu skanera usługi Azure Information Protection można znaleźć w informacjach poufnych masz w plikach, które są przechowywane w magazynie danych w środowisku lokalnym. Na przykład folderu lokalnego, udziału sieciowego lub SharePoint Server. 

Aby zakończyć tę konfigurację w mniej niż 10 minut.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik Szybki Start, potrzebne są:

1. Subskrypcja, która obejmuje usługi Azure Information Protection Plan 1 lub Plan 2.
    
    Jeśli nie masz jedną z tych subskrypcji, możesz utworzyć [bezpłatne](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) konta dla Twojej organizacji.

2. Klient usługi Azure Information Protection jest zainstalowany na tym komputerze. 
    
    Aby zainstalować klienta, przejdź do [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) i Pobierz **AzInfoProtection.exe** ze strony usługi Azure Information Protection.
    
3. SQL Server Express jest również instalowany na komputerze.
    
    Jeśli ta wersja programu SQL Server nie jest już zainstalowany, możesz pobrać go z [Microsoft Download Center](https://www.microsoft.com/en-us/sql-server/sql-server-editions-express) i wybierz opcję instalacji podstawowej.

4. Twoje konto domeny są synchronizowane z usługą Azure AD.

Aby uzyskać pełną listę wymagań wstępnych do używania usługi Azure Information Protection, zobacz [wymagania dotyczące usługi Azure Information Protection](requirements.md).

## <a name="prepare-a-test-folder-and-file"></a>Przygotowanie plików i folderów testu

Dla testu wstępnego upewnić się, że działa skaner:

1. Utwórz folder lokalny na komputerze. Na przykład **TestScanner** na lokalnym dysku C.

2. Utwórz i Zapisz dokument programu Word w tym folderze, który zawiera tekst **4242-4242-4242-4242** (numer karty kredytowej znanych do testowania).

## <a name="install-the-scanner"></a>Zainstaluj skaner

1. Otwórz sesję programu PowerShell przy użyciu **Uruchom jako administrator** opcji.

2. Aby zainstalować skanera, określając nazwę komputera, użyj następującego polecenia:
    
        Install-AIPScanner -SqlServerInstance <your computer name>\SQLEXPRESS
    
    Po wyświetleniu monitu podaj swoje własne poświadczenia skanera przy użyciu \<domena\nazwa_użytkownika > format i hasło. 

## <a name="specify-your-test-data-store"></a>Określ magazyn danych testowych

W sesji programu PowerShell wpisz następujące polecenie:

    Add-AIPScannerRepository -Path C:\TestScanner

## <a name="configure-the-scanner-to-discover-all-information-types"></a>Konfigurowanie skanera, aby odnaleźć wszystkie typy informacji

W sesji programu PowerShell wpisz następujące polecenie:

    Set-AIPScannerConfiguration -Enforce Off -Schedule Manual -DiscoverInformationTypes All

To polecenie służy do konfigurowania skanera celu jednorazowego odnajdywanie wszystkich plików w repozytorium określone dane. To skanowanie szuka wszystkich typów informacji poufnych znane i nie wymaga najpierw skonfiguruj etykiety usługi Azure Information Protection lub ustawień zasad.

## <a name="start-the-scan-and-confirm-it-finished"></a>Uruchom skanowanie i upewnij się, że jej zakończenie

1. W sesji programu PowerShell wpisz następujące polecenie, aby uruchomić skanera:
    
        Start-AIPScan
    
    Istnieje tylko jeden mały plik, aby sprawdzić, więc to skanowanie testu wstępnego będą bardzo szybkie. 

2. Przejdź do usługi Windows **Podgląd zdarzeń** > **aplikacji i usług** > **usługi Azure Information Protection** dziennika zdarzeń. 
    
    Upewnij się, że usługi Azure Information Protection zawiera identyfikator zdarzenia informacyjne **911** dla **MSIP. Skaner** procesu. Wpis dziennika zdarzeń ma również podsumowanie wyników skanowania.

## <a name="see-detailed-results"></a>Zobacz szczegółowe wyniki

Za pomocą Eksploratora plików Znajdź raporty skanera w lokalizacji %*localappdata*% \Microsoft\MSIP\Scanner\Reports. Otwórz plik szczegółowy raport, który ma format pliku CSV.

W programie Excel pierwszych dwóch kolumnach są wyświetlane dane repozytorium i plik nazwę Sklepu. W trakcie przeglądania przez kolumny będzie widoczny jeden o nazwie **nazwy typu informacji**, czyli kolumny interesuje Cię najbardziej. Dla naszych testu wstępnego, wyświetla **numer karty kredytowej**, jeden z wielu typów informacji poufnych, które można znaleźć skaner.

## <a name="scan-your-own-data"></a>Skanowanie danych użytkownika

1. Uruchom ponownie Dodaj AIPScannerRepository, tym razem, określając własne lokalnych magazyn danych, który chcesz przeprowadzić skanowanie poufne informacje. 
    
    Można określić folder lokalny, udziału sieciowego (ścieżka UNC) lub adres URL serwera programu SharePoint dla witryny programu SharePoint lub biblioteki. 
    
    - Przykład folderu lokalnego:
        
            Add-AIPScannerRepository -Path D:\Data\Finance
    
    - Przykład udziału sieciowego
        
            Add-AIPScannerRepository -Path \\NAS\HR
    
    - Przykład dla folderu programu SharePoint:
        
            Add-AIPScannerRepository -Path "http://sp2016/Shared Documents"

2. Uruchom ponownie skaner:
    
        Start-AIPScan

3. Wyświetlić nowe wyniki, gdy skanowanie zostanie zakończone. 
    
    Jak długo trwa to skanowanie zależy od tego, ile plików znajdują się w swoim magazynem danych, jak duże są te pliki i typu pliku. 

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W środowisku produkcyjnym należy uruchomić skanera w systemie Windows Server, przy użyciu konta usługi, które dyskretnie uwierzytelnia się w usłudze Azure Information Protection. Będzie także używać wersji korporacyjnej programu SQL Server, a także prawdopodobnie Określ kilku repozytoriów danych. 

Aby wyczyścić zasoby, gotowe do tego wdrożenia produkcyjnego, w sesji programu PowerShell, uruchom następujące polecenie, aby odinstalować skaner:

    Uninstall-AIPScanner

Następnie uruchom ponownie komputer.

To polecenie nie powoduje usunięcia następujące elementy i należy ręcznie je usunąć, jeśli nie chcesz ich po tym przewodniku Szybki Start:

- Baza danych programu SQL Server, który został utworzony, uruchamiając polecenie cmdlet Install-AIPScanner skanera usługi Azure Information Protection został zainstalowany. 

- Raporty skanera znajduje się w lokalizacji %*localappdata*% \Microsoft\MSIP\Scanner\Reports.

- **Zaloguj się jako usługa** przypisania prawa użytkownika, przyznanej konta domeny dla komputera lokalnego.


## <a name="next-steps"></a>Kolejne kroki

Ten przewodnik Szybki Start zawiera minimalnej konfiguracji, dzięki czemu można szybko sprawdzić, jak znaleźć poufnych informacji w udziale sieciowym skanera. Jeśli jesteś gotowy do zainstalowania skanera w środowisku produkcyjnym, zobacz [wdrażanie skanera usługi Azure Information Protection do automatycznego klasyfikowania i ochrony plików](deploy-aip-scanner.md).

Jeśli chcesz klasyfikować i chronić pliki, które zawierają poufne informacje, należy skonfigurować etykiety usługi Azure Information Protection dla automatycznej klasyfikacji i ochrony:

- [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection](configure-policy-classification.md)

- [Konfigurowanie etykiety w celu ochrony usługi Rights Management](configure-policy-protection.md)