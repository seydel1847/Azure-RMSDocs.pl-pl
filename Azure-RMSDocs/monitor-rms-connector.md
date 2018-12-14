---
title: Monitorowanie łącznika usługi Rights Management — AIP
description: Informacje dotyczące monitorowania łącznika i korzystania przez organizację z usługi Azure Rights Management w ramach usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8a1b3e54-f788-4f84-b9d7-5d5079e50b4e
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 46f8c817911408d62f12a1fce0a7ae0ce14069e2
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305492"
---
# <a name="monitor-the-azure-rights-management-connector"></a>Monitorowanie łącznika usługi Azure Rights Management

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Po zainstalowaniu i skonfigurowaniu łącznika usługi RMS można skorzystać z następujących metod i informacji, które ułatwiają monitorowanie łącznika oraz korzystanie przez organizację z usługi Azure Rights Management w ramach usługi Azure Information Protection.

## <a name="application-event-log-entries"></a>Wpisy dziennika zdarzeń aplikacji

Łącznik usługi RMS używa dziennika zdarzeń aplikacji do rejestrowania wpisów dotyczących **łącznika usługi Microsoft RMS**. 

Mogą to być zdarzenia informacyjne, takie jak:

- Identyfikator 1000 — potwierdzenie uruchomienia usługi łącznika

- Identyfikator 1002 — potwierdzenie pomyślnego połączenia serwera z łącznikiem usługi RMS

- Identyfikator 1004 — po każdym pobraniu listy autoryzowanych kont (zawierającej wszystkie konta) do łącznika 

Jeśli nie skonfigurowano łącznika do używania protokołu HTTPS, może zostać wyświetlone ostrzeżenie o identyfikatorze 2002 z informacją o tym, że klient korzysta z niezabezpieczonego połączenia (HTTP).

Jeśli łącznik nie może nawiązać połączenia z usługą Azure Rights Management, najprawdopodobniej odnotowany zostanie błąd 3001. Taki błąd połączenia może na przykład wynikać z problemu z usługą DNS lub braku dostępu do Internetu dla co najmniej jednego serwera z uruchomionym łącznikiem usługi RMS. 

> [!TIP]
> Częstą przyczyną braku możliwości nawiązania połączenia z usługą Azure Rights Management przez serwery łącznika usługi RMS jest konfiguracja serwera proxy sieci Web.

Podobnie jak w przypadku wszystkich wpisów dziennika zdarzeń, można przejść do szczegółów komunikatu w celu uzyskania dodatkowych informacji.

Oprócz sprawdzenia dziennika zdarzeń przy pierwszym wdrożeniu łącznika można regularnie wyszukiwać ostrzeżenia i błędy. Łącznik może początkowo działać zgodnie z oczekiwaniami, ale inni administratorzy mogą zmienić zależne konfiguracje. Inny administrator może zmienić konfigurację serwera proxy sieci Web tak, aby serwery łącznika usługi RMS nie mogły już uzyskiwać dostępu do Internetu (błąd 3001), albo usunąć konto komputera z grupy autoryzowanej do korzystania z łącznika (ostrzeżenie 2001).

### <a name="event-log-ids-and-descriptions"></a>Identyfikatory i opisy dziennika zdarzeń

Następujące sekcje zawierają informacje dotyczące identyfikowania możliwych identyfikatorów zdarzeń, opisów i innych dodatkowych informacji.

-----

Informacja **1000**

**Usługa sieci Web łącznika usługi Microsoft RMS została uruchomiona.**

To zdarzenie jest rejestrowane, gdy podejmowana jest pierwsza próba uruchomienia łącznika usług RMS.

----

Informacja **1001**

**Usługa sieci Web łącznika usługi Microsoft RMS została zatrzymana.**

To zdarzenie jest rejestrowane, gdy łącznik usługi RMS zostanie zatrzymany w wyniku normalnej operacji. Ma to miejsce na przykład w przypadku ponownego uruchomienia usług IIS lub wyłączenia komputera. 

----

Informacja **1002**

**Zezwolono na dostęp do łącznika usługi Microsoft RMS przez autoryzowany serwer.**

To zdarzenie jest rejestrowane, gdy po raz pierwszy jest nawiązywane połączenie z łącznikiem usługi RMS za pomocą konta z serwera lokalnego po autoryzacji konta przez administratora usługi Azure RMS przy użyciu narzędzia administratora łącznika usługi RMS. Identyfikator SID, nazwa konta i nazwa komputera nawiązującego połączenie jest zawarta w komunikacie zdarzenia.

----

Informacja **1003**

**Połączenie od klienta wymienionego poniżej zostało przełączone z połączenia niezabezpieczonego (HTTP) na połączenie bezpieczne (HTTPS).**

To zdarzenie jest rejestrowane, gdy serwer lokalny zmieni swoje połączenie z łącznikiem usługi RMS z protokołu HTTP (mniej bezpieczny) na protokół HTTPS (bardziej bezpieczny). Identyfikator SID, nazwa konta i nazwa komputera nawiązującego połączenie jest zawarta w komunikacie zdarzenia.

----

Informacja **1004**

**Lista autoryzowanych kont została zaktualizowana.**

To zdarzenie jest rejestrowane po pobraniu przez łącznik usługi RMS najnowszej listy kont (istniejące konta i wszelkie zmiany), które są autoryzowane do korzystania z łącznika usługi RMS. Ta lista jest pobierana co 15 minut, o ile łącznik usługi RMS może komunikować się z usługą Azure Rights Management.

----

Ostrzeżenie **2000**

**W kontekście HTTP brak głównej nazwy użytkownika lub jest ona nieprawidłowa. Sprawdź, czy dla witryny sieci Web łącznika usługi Microsoft RMS jest wyłączone uwierzytelnianie anonimowe w usługach IIS i włączone jest tylko uwierzytelnianie systemu Windows.**

To zdarzenie jest rejestrowane, gdy łącznik usługi RMS nie może jednoznacznie zidentyfikować konta, które podejmuje próbę nawiązania połączenia z łącznikiem usługi RMS. Może to być wynikiem niepoprawnie skonfigurowanego uwierzytelniania anonimowego dla usług IIS lub tego, że konto pochodzi z niezaufanego lasu.

----

Ostrzeżenie **2001**

**Podjęto próbę nieautoryzowanego dostępu do łącznika usługi Microsoft RMS.**

To zdarzenie jest rejestrowane, gdy konto próbuje nawiązać połączenie z łącznikiem usługi RMS, ale próba ta nie powiedzie się. Najbardziej typową przyczyną tego ostrzeżenia jest sytuacja, gdy konto, które podejmuje próbę nawiązania połączenia, nie znajduje się na liście autoryzowanych kont pobranej przez łącznik usługi RMS z usługi Azure Rights Management. Na przykład najnowsza lista mogła nie zostać jeszcze pobrana (to zdarzenie występuje co 15 minut) lub lista nie zawiera konta. 

Inną przyczyną może być zainstalowanie łącznika usługi RMS na tym samym serwerze, który został skonfigurowany do używania łącznika. Na przykład na serwerze z systemem Exchange Server instalowany jest łącznik usługi RMS, a konto programu Exchange jest autoryzowane do używania łącznika. Ta konfiguracja nie jest obsługiwana, ponieważ łącznik usługi RMS nie może poprawnie zidentyfikować konta podczas próby nawiązania połączenia.

Komunikat zdarzenia zawiera informacje o koncie i komputerze, który podejmuje próbę nawiązania połączenia z łącznikiem usługi RMS:

- Jeśli konto, które podejmuje próbę nawiązania połączenia z łącznikiem usługi RMS, jest prawidłowe, należy użyć narzędzia administratora łącznika usług RMS, aby dodać konto do listy kont autoryzowanych. Aby uzyskać więcej informacji o kontach, które muszą być autoryzowane, zobacz [Dodawanie serwera do listy dozwolonych serwerów](install-configure-rms-connector.md#add-a-server-to-the-list-of-allowed-servers). 

- Jeśli konto, które podejmuje próbę nawiązania połączenia z łącznikiem usługi RMS, znajduje się na tym samym komputerze co serwer łącznika usługi RMS, należy zainstalować łącznik na osobnym serwerze. Aby uzyskać więcej informacji o wymaganiach wstępnych dotyczących łącznika, zobacz [Wymagania wstępne dotyczące łącznika usługi RMS]( deploy-rms-connector.md#prerequisites-for-the-rms-connector).

----

Ostrzeżenie **2002**

**Połączenie z wymienionego poniżej klienta jest połączeniem niezabezpieczonym (HTTP).**

To zdarzenie jest rejestrowane, gdy serwer lokalny pomyślnie nawiąże połączenie z łącznikiem usługi RMS, ale połączenie korzysta z protokołu HTTP (mniej bezpieczny), a nie protokołu HTTPS (bardziej bezpieczny). Jedno zdarzenie jest rejestrowane dla jednego konta, a nie dla połączenia. To zdarzenie jest wyzwalane ponownie, jeśli konto zostało pomyślnie przełączone do używania protokołu HTTPS, ale powróciło do używania protokołu HTTP.

Komunikaty zdarzenia zawiera identyfikator SID konta, nazwę konta i nazwę komputera, który nawiązuje połączenie z łącznikiem usługi RMS.

Aby uzyskać informacje o sposobie konfigurowania łącznika usługi RMS na potrzeby połączeń HTTPS, zobacz [Konfigurowanie łącznika usługi RMS do używania protokołu HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https).

----

Ostrzeżenie **2003**

**Lista autoryzacji jest pusta. Z usługi nie będzie można korzystać, dopóki lista autoryzowanych użytkowników i grup dla łącznika nie zostanie wypełniona.**

To zdarzenie jest rejestrowane, gdy łącznik usługi RMS nie ma listy autoryzowanych kont, w związku z czym żaden serwer lokalny nie może nawiązać z nim połączenia. Łącznik usługi RMS pobiera listę co 15 minut z usługi Azure RMS. 

Do określania kont należy użyć narzędzia administratora łącznika usługi RMS. Aby uzyskać więcej informacji, zobacz [Autoryzowanie serwerów do korzystania z łącznika usługi RMS]( install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector). 

----

Błąd **3000**

**Wystąpił nieobsługiwany wyjątek w łączniku usługi Microsoft RMS.**

To zdarzenie jest rejestrowane za każdym razem, gdy łącznik usługi RMS napotka nieoczekiwany błąd. Szczegóły błędu znajdują się w komunikacie zdarzenia.

Jedną z możliwych przyczyn może wskazywać tekst **Żądanie nie powiodło się i została zwrócona pusta odpowiedź** w komunikacie o zdarzeniu. Jeśli widzisz ten tekst, może to oznaczać, że urządzenie sieciowe przeprowadza inspekcję pakietów połączenia SSL między serwerami lokalnymi i serwerem łącznika usługi RMS. Usługa Azure Rights Management nie obsługuje tej konfiguracji, czego wynikiem jest błąd komunikacji oraz wyświetlenie tego komunikatu dziennika zdarzeń.

----

Błąd **3001**

**Wystąpił wyjątek podczas pobierania informacji o autoryzacji.**

To zdarzenie jest rejestrowane, jeśli łącznik usługi RMS nie może pobrać najnowszej listy kont, które zostały autoryzowane do korzystania z łącznika usługi RMS. Szczegóły błędu znajdują się w komunikacie dotyczącym zdarzenia.



----

## <a name="performance-counters"></a>Liczniki wydajności

Podczas instalacji łącznika usługi RMS są automatycznie tworzone liczniki wydajności **łącznika usługi Microsoft Rights Management**, które mogą być przydatne do monitorowania i zwiększania wydajności użycia usługi Azure Rights Management. 

Przykładem może być sytuacja, gdy po objęciu ochroną dokumentów lub wiadomości e-mail regularnie występują opóźnienia. Opóźnienia mogą także występować po otwarciu chronionych dokumentów lub wiadomości e-mail. W takich przypadkach liczniki wydajności mogą pomóc w ustaleniu, czy opóźnienia są spowodowane czasem przetwarzania w łączniku lub czasem przetwarzania przez usługę Azure Rights Management, czy też są to opóźnienia sieci. 

Aby łatwiej wskazać przyczynę opóźnienia, zapoznaj się z licznikami zawierających średnią wartość **czasu przetwarzania łącznika**, **czasu odpowiedzi usługi** i **czasu odpowiedzi łącznika**. Przykład: **Licencjonowanie pomyślne wsadowej czasu odpowiedzi łącznika średni żądania**.

Jeśli niedawno dodano nowe konta serwera na potrzeby korzystania z łącznika, warto zapoznać się z licznikiem **Czas od ostatniej aktualizacji zasad autoryzacji** w celu sprawdzenia, czy łącznik pobrał listę od czasu jej aktualizacji, czy należy zaczekać nieco dłużej (do 15 minut).

## <a name="logging"></a>Rejestrowanie

Rejestrowanie użycia pomaga sprawdzić, kiedy wiadomości e-mail i dokumenty są chronione oraz używane. W przypadku używania łącznika usługi RMS do ochrony zawartości i korzystania z niej pole identyfikatora użytkownika w dziennikach zawiera główną nazwę usługi **Aadrm_S-1-7-0**. Ta nazwa jest tworzona automatycznie dla łącznika usługi RMS.

Aby uzyskać więcej informacji na temat rejestrowania użycia, zobacz [Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management](log-analyze-usage.md).

Jeśli potrzebujesz bardziej szczegółowego rejestrowania do celów diagnostycznych, możesz użyć aplikacji [Debugview](https://go.microsoft.com/fwlink/?LinkID=309277) z witryny Windows Sysinternals. Włącz śledzenie dla łącznika usługi RMS, modyfikując plik web.config dla witryny domyślnej w usługach IIS:

1. Znajdź plik web.config w lokalizacji **%programfiles%\Microsoft Rights Management connector\Web Service**.

2. Znajdź następujący wiersz:

        <trace enabled="false" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

3. Zastąp go następującym tekstem:

        <trace enabled="true" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

4.  Zatrzymaj i uruchom usługi IIS, aby uaktywnić śledzenie. 

5.  Po przechwyceniu odpowiednich śladów przywróć wiersz z kroku 3, a następnie zatrzymaj i uruchom ponownie usługi IIS.

