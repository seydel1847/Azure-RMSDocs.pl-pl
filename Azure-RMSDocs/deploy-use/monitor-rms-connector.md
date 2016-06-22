---
# required metadata

title: Monitorowanie łącznika usługi Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 06/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8a1b3e54-f788-4f84-b9d7-5d5079e50b4e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Monitorowanie łącznika usługi Azure Rights Management

*Dotyczy: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*

Poniżej przedstawiono metody i informacje ułatwiające monitorowanie łącznika usługi RMS oraz korzystania z usługi Azure RMS w organizacji po zainstalowaniu i skonfigurowaniu łącznika.

## Wpisy dziennika zdarzeń aplikacji

Łącznik usługi RMS używa dziennika zdarzeń aplikacji do rejestrowania wpisów dotyczących **łącznika usługi Microsoft RMS**. 

Na przykład zdarzenia informacyjne o identyfikatorze 1000 zawierają potwierdzenie uruchomienia usługi łącznika, zdarzenia o identyfikatorze 1002 zawierają potwierdzenie pomyślnego połączenia serwera z łącznikiem usługi RMS, a zdarzenia o identyfikatorze 1004 informują o każdym pobraniu listy autoryzowanych kont (zawiera ona każde konto) w łączniku. 

Jeśli nie skonfigurowano łącznika do używania protokołu HTTPS, może zostać wyświetlone ostrzeżenie o identyfikatorze 2002 z informacją o tym, że klient korzysta z niezabezpieczonego połączenia (HTTP).

Jeśli łącznik nie może nawiązać połączenia z usługą Azure RMS, najprawdopodobniej wystąpi błąd 3001. Może to na przykład wynikać z problemu z usługą DNS lub braku dostępu do Internetu dla co najmniej jednego serwera z uruchomionym łącznikiem usługi RMS. 

> [!TIP] Częstą przyczyną braku możliwości nawiązania połączenia z usługą Azure RMS przez serwery łącznika usługi RMS jest konfiguracja serwera proxy sieci Web.

Tak jak w przypadku wszystkich wpisów dziennika zdarzeń można przejść do szczegółów komunikatu w celu uzyskania dodatkowych informacji.

Oprócz sprawdzenia dziennika zdarzeń przy pierwszym wdrożeniu łącznika można regularnie wyszukiwać ostrzeżenia i błędy. Na przykład łącznik może działać zgodnie z oczekiwaniami, ale inni administratorzy mogą zmienić zależne konfiguracje. Inny administrator może zmienić konfigurację serwera proxy sieci Web tak, aby serwery łącznika usługi RMS nie mogły już uzyskiwać dostępu do Internetu (błąd 3001), albo usunąć konto komputera z grupy autoryzowanej do korzystania z łącznika (ostrzeżenie 2001).

## Liczniki wydajności

W ramach instalacji łącznika usługi RMS są automatycznie tworzone liczniki wydajności **łącznika usługi Microsoft Rights Management**, które mogą być przydatne podczas monitorowania wydajności użycia usługi Azure RMS za pośrednictwem łącznika. 

Na przykład w przypadku regularnego występowania opóźnień przy włączonej ochronie dokumentów lub wiadomości e-mail albo otwierania chronionych dokumentów lub wiadomości e-mail liczniki wydajności mogą pomóc w ustaleniu, czy opóźnienie wynika z czasu przetwarzania w łączniku, czasu przetwarzania w usłudze Azure RMS czy opóźnienia sieci. Aby łatwiej wskazać przyczynę opóźnienia, zapoznaj się z licznikami zawierających średnią wartość **czasu przetwarzania łącznika**, **czasu odpowiedzi usługi** i **czasu odpowiedzi łącznika**. Przykład: **Średni czas odpowiedzi łącznika na żądania wsadowe dotyczące licencjonowania zakończone powodzeniem**.

Jeśli niedawno dodano nowe konta serwera na potrzeby korzystania z łącznika, warto zapoznać się z licznikiem **Czas od ostatniej aktualizacji zasad autoryzacji** w celu sprawdzenia, czy łącznik pobrał listę od czasu jej aktualizacji, czy należy zaczekać nieco dłużej (do 15 minut).

## Analizator usług RMS

Narzędzie Analizator usług Rights Management Services ułatwia monitorowanie kondycji łącznika i wykrywanie problemów dotyczących konfiguracji.

Jeśli jeszcze nie pobrano tego narzędzia, możesz to zrobić w [Centrum pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=46437) i zainstalować je na dowolnym komputerze z dostępem do Internetu, który może nawiązać połączenie z łącznikiem usługi RMS. Uruchom narzędzie, a następnie na stronie **powitalnej** wybierz opcję **Łącznik usługi Azure RMS**.

Aby uzyskać dodatkowe informacje i instrukcje, zobacz sekcje **Szczegóły** i **Instrukcje instalacji** na stronie pobierania.

## Rejestrowanie

Rejestrowanie użycia pomaga sprawdzić, kiedy wiadomości e-mail i dokumenty są chronione oraz używane. W przypadku korzystania z łącznika usługi RMS pole identyfikatora użytkownika w dziennikach zawiera główną nazwę usługi, która jest generowana automatycznie podczas instalacji łącznika usługi RMS.

Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management](log-analyze-usage.md).

Jeśli chcesz rejestrować bardziej szczegółowe dane w celach diagnostycznych, możesz użyć programu [Debugview](http://go.microsoft.com/fwlink/?LinkID=309277) dostępnego w witrynie Windows Sysinternals i włączyć śledzenie łącznika usługi RMS przez zmodyfikowanie pliku web.config domyślnej witryny w usługach IIS. Wykonaj następujące czynności:

1. Znajdź plik web.config w lokalizacji **%programfiles%\Microsoft Rights Management connector\Web Service**.

2. Znajdź następujący wiersz:

        <trace enabled="false" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

3. Zamień go na następujący wiersz:

        <trace enabled="true" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

4.  Zatrzymaj i uruchom usługi IIS, aby uaktywnić śledzenie. 

5.  Po przechwyceniu odpowiednich śladów przywróć wiersz z kroku 3, a następnie zatrzymaj i uruchom ponownie usługi IIS.



<!--HONumber=Jun16_HO2-->


