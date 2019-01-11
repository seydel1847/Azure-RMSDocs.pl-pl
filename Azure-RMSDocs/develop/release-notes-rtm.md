---
title: Informacje o wersji
description: Zestaw SDK aktualizacje, poprawki i inne informacje dla deweloperów.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 10/18/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: CE379738-4E1D-42AD-83F4-F89B70456EBB
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 8132fd2afba45402f8f9c835f2d6db69dd8e81f2
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071204"
---
# <a name="release-notes"></a>Informacje o wersji

Ten artykuł zawiera ważne informacje o bieżącej i poprzednich wersjach zestawu RMS SDK 2.1.

## <a name="october-2017---update"></a>Aktualizacja z października 2017-

- Dodanie dwóch nowych interfejsów API dla środowiska inintialization i anulowania inicjowania. Aby uzyskać informacje, zobacz [IpcInitializeEnvironment](https://msdn.microsoft.com/library/hh535289.aspx) i [IpcUninitializeEnvironment](https://msdn.microsoft.com/library/hh535289.aspx).
- Typy plików programu Visio są teraz obsługiwane. Aby uzyskać więcej informacji, zobacz temat [Konfiguracja interfejsu API plików](file-api-configuration.md).

## <a name="february-2016---sdk-documentation-update"></a>Luty 2016 r. — aktualizacja dokumentacji zestawu SDK

>[!Note]
> Aktualizacje dokumentacji funkcji w tej sekcji dotyczą zestawu SDK udostępnionego do pobrania w dniu 12.11.2015 r.

- **Ulepszony przepływ uwierzytelniania** — przy użyciu uwierzytelniania opartego na tokenie protokołu OAuth2 za pośrednictwem [interfejsów Azure Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/). Aby uzyskać więcej informacji na temat tego procesu i przeznaczonych dla niego rozszerzeń interfejsu API, zobacz [Uwierzytelnianie ADAL dla aplikacji z obsługą usługi RMS](how-to-use-adal-authentication.md).

- **Aktualizacja do biblioteki ADAL** — aktualizacja aplikacji umożliwiająca użycie uwierzytelniania ADAL zamiast asystenta logowania usługi online firmy Microsoft zapewnia następujące możliwości:

 - Korzystanie z uwierzytelniania wieloskładnikowego
 - Instalowanie klienta usługi RMS 2.1 bez wymogu posiadania uprawnień administracyjnych na komputerze
 - Certyfikowanie aplikacji dla systemu Windows 10

- **Zakończenie świadczenia wsparcia dotyczącego asystenta logowania usługi online firmy Microsoft (SIA) z zestawem RMS SDK.** Firma Microsoft będzie obsługiwać korzystania z usługi SIA przez sześć miesięcy, po upływie których wsparcie zostanie zakończone.


## <a name="december-2015-update"></a>Aktualizacja z grudnia 2015 r.

- Zaimplementowane ulepszenia wydajności obejmują kilka obszarów, w tym:
    - Publikowanie z podstawowego serwera licencjonowania w przypadku korzystania z serwerów licencji.
    - Zestaw RMS SDK 2.1 szybciej zwraca błąd w przypadku braku połączenia sieciowego.

- Wiele aktualizacji poprawiających komunikowanie błędów i rozwiązywanie problemów.
- Zaktualizowano również listę [obsługiwanych platform](supported-platforms.md).
- Potrzebę środowisko produkcji wstępnej i umożliwia korzystanie z manifestu aplikacji został usunięty z zestawu RMS SDK 2.1. Usunięto sekcje tego zestawu dokumentacji dla deweloperów oraz uproszczono i ponownie zorganizowano ogólną dokumentację.

## <a name="may-2015-update"></a>Aktualizacja z maja 2015 r.

-   **Aplikacje usługi i oparte na chmurze RMS** - [IPC\_POŚWIADCZEŃ\_SYMMETRIC\_klucz](https://msdn.microsoft.com/library/dn133062.aspx) wymaga podania trzech informacji; klucz symetryczny  **Identyfikator AppPrincipalId**, i **TenantBposId**. Zaktualizowano artykuł, w tym wytyczne dotyczące przetwarzania tych informacji. Tę aktualizację można znaleźć w poprawionej wersji artykułu [Umożliwianie współpracy aplikacji usługi z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="april-2015-update"></a>Aktualizacja z kwietnia 2015 r.

-   **Śledzenie dokumentów** jest teraz możliwe za pośrednictwem zestawu nowych interfejsów API. Aby uzyskać więcej informacji, zobacz [Śledzenie zawartości](tracking-content.md).
-   **Typ szyfrowania** — obsługujemy teraz sterowanie na poziomie interfejsu API w celu wybrania pakietu szyfrowania. Aby uzyskać więcej informacji, zobacz [Praca z szyfrowaniem](working-with-encryption.md).

    **Uwaga**  będzie już widoczna **IPC\_LI\_uznane za PRZESTARZAŁE\_szyfrowania\_algorytmy** flagi w interfejsie API. Oznacza to, że kompilacje aplikacji odwołujących się do tej flagi nie będą możliwe w przyszłości, ale istniejące aplikacje będą nadal działać, ponieważ będziemy flaga będzie prywatnie uznawana w kodzie interfejsu API. Nadal będzie można uzyskiwać korzyści zapewniane przez przestarzałą flagę algorytmów szyfrowania, zmieniając po prostu flagę. Aby uzyskać więcej informacji, zobacz [Praca z szyfrowaniem](working-with-encryption.md).

-   **Aplikacje w trybie serwera**, w których jest używana [wartość trybu API](https://msdn.microsoft.com/library/hh535236.aspx) **IPC\_API\_MODE\_SERVER**, nie wymagają już manifestu aplikacji. Można przetestować aplikację na serwerze produkcyjnym usługi RMS, przy czym nie jest wymagane uzyskanie licencji produkcyjnej podczas przełączania do środowiska produkcyjnego. Aby uzyskać więcej informacji na temat aplikacji w trybie serwera, zobacz [Typy aplikacji](application-types.md).
-   **Rejestrowanie** jest teraz implementowane zarówno za pośrednictwem plików, jak i śledzenia zdarzeń systemu Windows.
-   Jeśli korzystasz z komputera z systemem **Windows 7 z dodatkiem SP1 lub Windows Server 2008 R2**, zapoznaj się z uwagą umieszczoną pod sekcją „Ważne uwagi dla deweloperów”.

## <a name="january-2015-update"></a>Aktualizacja ze stycznia 2015 r.

-   **Zwiększenie rozmiaru obsługiwanego pliku chronionego (pfile)** — obsługiwane są pliki pfile o rozmiarze przekraczającym jeden gigabajt (1 GB). Aby uzyskać więcej informacji o plikach pfile, zobacz [Obsługiwane formaty plików](supported-file-formats.md).
-   **Ulepszone rejestrowania zapewniające lepszą diagnostykę** — na poziomach rejestrowania będą wyświetlane oznaczenia **BŁĄD** lub **OSTRZEŻENIE** w przypadku komunikatów, które wymagają przejrzenia. Wszystkie inne komunikaty, w tym wyjątków, które są nadal wyświetlane, zostaną zarejestrowane jako **informacje**.

    Wybraliśmy to rozwiązanie, aby nie dopuścić do przeoczenia żadnych szczegółów. Tylko ważne komunikaty są wyświetlane na poziomie OSTRZEŻENIA.

-   **Uzyskiwanie szablonów firmowych** — znaczące poprawki kodu uzyskiwania szablonów w oparciu o raporty i opinie klientów.
-   Ulepszona spójność lokalizacji

## <a name="october-2014-update"></a>Aktualizacja z października 2014 r.

-   Zaktualizowano domyślne zachowania składnika specyfikacji File API w zestawie SDK. Aby uzyskać więcej informacji, zobacz temat [Konfiguracja interfejsu API plików](file-api-configuration.md).
-   Powiadomienia e-mail, nowa funkcja jest opisana w artykule uwagi dla deweloperów, [Włączanie powiadomień e-mail](how-to-enable-email-notification.md).

## <a name="july-2014-update"></a>Aktualizacja z lipca 2014 r.

Składnik interfejsu API plików zestawu SDK zostały rozszerzone i oferuje następujące funkcje:

-   Określenie funkcji ochrony, których należy użyć.
-   Zapewnienie ochrony za pomocą usługi RMS na poziomie szczegółowości pliku.

    Funkcje dodane w tej wersji:

    **Uwaga** — dalsze pomocnicze danych dla rozszerzeń specyfikacji File API dodano typy i struktury, niewymienione w tym miejscu. Wszystkie artykuły, które zostały zaktualizowane w tej wersji są oznaczone jako **wstępną i może ulec zmianie**.

    -   [IpcfOpenFileOnHandle](https://msdn.microsoft.com/library/dn771751.aspx)
    -   [IpcfOpenFileOnILockBytes](https://msdn.microsoft.com/library/dn771752.aspx)
    -   [IpcfGetFileProperty](https://msdn.microsoft.com/library/dn771749.aspx)
    -   [IpcfLogicalFileRangeToRawFileRange](https://msdn.microsoft.com/library/dn771750.aspx)
    -   [IpcfReadFile](https://msdn.microsoft.com/library/dn771753.aspx)
    -   [IpcfSetEndOfFile](https://msdn.microsoft.com/library/dn771754.aspx)
    -   [IpcfWriteFile](https://msdn.microsoft.com/library/dn771756.aspx)

## <a name="april-2014-update"></a>Aktualizacja z kwietnia 2014 r.

-   Ulepszono **użycie pamięci specyfikacji File API**, szczególnie w przypadku dużych plików PFile.
-   **Identyfikator zawartości** umożliwia teraz zapis za pośrednictwem właściwości **IPC\_LI\_CONTENT\_ID**. Aby uzyskać więcej informacji, zobacz [License property types](https://msdn.microsoft.com/library/hh535287.aspx) (Typy właściwości licencji).
-   **Wymaganie manifestu produkcji** — jeśli aplikacja/usługa z włączonymi usługami RMS jest uruchamiana w trybie serwera, firma Microsoft nie będzie już wymagać manifestu. Aby uzyskać więcej informacji, zobacz temat [Typy aplikacji](application-types.md).
-   **Aktualizacje dokumentacji**

    **Najlepsze rozwiązanie w zakresie testowania** — dodano wskazówki dotyczące korzystania z lokalnego serwera przed rozpoczęciem testów z użyciem usługi Azure RMS. Aby uzyskać więcej informacji, zobacz [Umożliwianie współpracy aplikacji usługi z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="important-developer-notes"></a>Ważne uwagi dla deweloperów

-   **Natywna obsługa wszystkich typów plików**

    Można dodać natywną obsługę dowolnego typu pliku (rozszerzenie) w tej wersji usługi Rights Management Services SDK 2.1. Na przykład dla dowolnego rozszerzenia &lt;roz&gt; (innego niż rozszerzenia pakietu office i PDF), będzie używany ciąg \*.p&lt;roz&gt;, jeśli konfiguracja administratora dla tego rozszerzenia ma wartość „NATIVE”.

    Aby uzyskać więcej informacji o obsługiwanych typach plików, zobacz temat [Konfiguracja interfejsu API plików](file-api-configuration.md).

-   **Windows 7 z dodatkiem SP1 i Windows Server 2008 R2 SP1 maszyny** bez aktualizacji, [KB2533623](https://support.microsoft.com/kb/2533623), może mieć następujący błąd ochrony dowolnego pliku pakietu office "parametr jest nieprawidłowy. Kod błędu 0x80070057”. Jeśli widzisz taki komunikat, zainstaluj aktualizację i spróbuj ponownie. Jeśli problemy występują nadal, skontaktuj się z opinii o wersji Beta zestawu RMS SDK <rmcstbeta@microsoft.com>.

    **Uwaga**  od kwietnia 2015 r. dodano test procesu instalacji tej bazy wiedzy.

     

-   **Integracja specyfikacji File API**

    Active Directory usług plików interfejs API Rights Management, z dodatkiem specyfikacji File API zapewnia następujące korzyści i funkcje.

      - Można chronić poufne dane w zautomatyzowany sposób bez szczegółowej znajomości implementacji usługi Zarządzanie prawami do informacji (IRM) używanej przez różne formaty plików.

      - Ochrona natywna może obejmować pliki pakietu Microsoft Office, pliki w formacie Portable Document Format (PDF) oraz inne wybrane typy plików. Pełną listę typów plików, które mogą być chronione przy użyciu ochrony natywnej, można znaleźć w temacie [Konfiguracja interfejsu API plików](file-api-configuration.md).

      - Wszystkie pliki, z wyjątkiem plików systemowych i plików pakietu Office, mogą być chronione przy użyciu formatu pliku chronionego usługi RMS (PFile).

    Interfejs API plików jest implementowany za pośrednictwem następujących czterech nowych funkcji: [IpcfDecryptFile](https://msdn.microsoft.com/library/dn133058.aspx), [IpcfEncryptFile](https://msdn.microsoft.com/library/dn133059.aspx), [IpcfGetSerializedLicenseFromFile](https://msdn.microsoft.com/library/dn133060.aspx), i [IpcfIsFileEncrypted](https://msdn.microsoft.com/library/dn133061.aspx).

    Interfejs API plików wymaga zainstalowania klienta Rights Management Service Client 2.1 na komputerze klienckim i połączenia komputera z serwerem usługi RMS. Aby uzyskać więcej informacji na temat serwera usługi RMS, klienta usługi RMS i ich funkcji, zobacz zawartość TechNet w [dokumentacji usługi RMS dla informatyków](https://technet.microsoft.com/library/cc771234(v=ws.10).aspx).

-   **Problem**: W przypadku tworzenia licencji od podstaw, jest jawne przyznanie praw własności.

    **Rozwiązanie**: W aplikacji należy jawnie dodać **właściciela** prawa do właściciela licencji w przypadku tworzenia licencji od podstaw przy użyciu [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx). Aby uzyskać więcej informacji, zobacz temat [Dodawanie jawnych praw właściciela](add-explicit-owner-rights.md).

-   **Problem**: Jeśli aplikacja wywołuje [IpcProtectWindow](https://msdn.microsoft.com/library/hh535268.aspx) lub [IpcUnprotectWindow](https://msdn.microsoft.com/library/hh535272.aspx) w tym samym oknie za pomocą jego uchwytu, zestaw RMS SDK 2.1 zwróci błąd w **HRESULT**.

    **Rozwiązanie**: Dokładne wskazówki dotyczące tego, zobacz sekcję Uwagi w [IpcProtectWindow](https://msdn.microsoft.com/library/hh535268.aspx) i [IpcUnprotectWindow](https://msdn.microsoft.com/library/hh535272.aspx).

-   **Problem**: Podczas tworzenia wielu architektur, należy skorzystać z poniższych wskazówek.

    **Rozwiązanie**: Jeśli chcesz używać Ipcsecproc\*isv.dll dla innej architektury (na przykład zainstalowano zestaw SDK 64-bitowym na komputerze 64-bitowym, ale teraz ma zostać wdrożony na komputerze 32-bitowy, który wymaga Ipcsecproc\*isv.dll), należy zainstalować 32-bitowy zestaw SDK na innym komputerze, a kopia Ipcsecproc\*isv.dll pliki do miejsca, z "% PROGRAMFILES %\\Microsoft Information Protection i kontrola" folder (domyślna lokalizacja lub wszędzie tam, gdzie chcesz zainstalować zestaw SDK).

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Q**: Jak działa domyślne zachowanie języka z funkcjami, które przyjmują parametr LCID?

**A**: Użycie wartości 0 dla domyślnych ustawień regionalnych. W takim przypadku klient usług AD RMS Client 2.1 wyszukuje nazwy i opisy w następującej kolejności i pobiera pierwszy z nich dostępne:

    1 - User preferred LCID.
    2 - System locale LCID.
    3 - The first available language specified in the Rights Management Server (RMS) template.

Jeśli nie będzie można pobrać nazwy ani opisu, zostanie zwrócony błąd. Może istnieć tylko jedna nazwa i opis dla określonego identyfikatora LCID.
