---
title: "Informacje o wersji | Usługa Azure RMS"
description: 
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: CE379738-4E1D-42AD-83F4-F89B70456EBB
audience: developer
ms.reviewer: kartikk
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8af3161946b2dfc6ea58d0565491d8e59736d565
ms.openlocfilehash: 2f4c11f7661a814849ccea41c60edfc2ad2287e8
ms.lasthandoff: 02/28/2017


---

# <a name="release-notes"></a>Informacje o wersji

Ten temat zawiera ważne informacje o bieżącej i poprzednich wersjach zestawu RMS SDK 2.1.

## <a name="new-for-the-february-2017---sdk-documentation-update"></a>Nowość w lutym 2017 r. — aktualizacja dokumentacji zestawu SDK
>[!Note]  
> Aktualizacje dokumentacji w tej sekcji dotyczą zestawu SDK udostępnionego do pobrania w wersji 1.03102.0221.
 
- **Zbieranie danych** — funkcja zbierania informacji o błędach i wydajności aplikacji jest teraz dostępna. Ta funkcja jest kontrolowana przez nową właściwość, *IPC_EI_DATA_COLLECTION_ENABLED*, jedną z [właściwości środowiska](https://msdn.microsoft.com/en-us/library/hh535247.aspx), i można ją zastąpić administracyjnie. 

## <a name="february-2016---sdk-documentation-update"></a>Luty 2016 r. — aktualizacja dokumentacji zestawu SDK

>[!Note]
> Aktualizacje dokumentacji funkcji w tej sekcji dotyczą zestawu SDK udostępnionego do pobrania w dniu 12.11.2015 r.

- **Ulepszony przepływ uwierzytelniania** — przy użyciu metody uwierzytelniania opartej na tokenie protokołu OAuth2 za pośrednictwem [biblioteki Azure Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/). Aby uzyskać więcej informacji na temat tego procesu i przeznaczonych dla niego rozszerzeń interfejsu API, zobacz [Uwierzytelnianie ADAL dla aplikacji z obsługą usługi RMS](how-to-use-adal-authentication.md).

- **Aktualizacja do biblioteki ADAL** — aktualizacja aplikacji umożliwiająca użycie uwierzytelniania ADAL zamiast asystenta logowania usługi online firmy Microsoft zapewnia następujące możliwości:

 - Korzystanie z uwierzytelniania wieloskładnikowego
 - Instalowanie klienta usługi RMS 2.1 bez wymogu posiadania uprawnień administracyjnych na komputerze
 - Certyfikowanie aplikacji dla systemu Windows 10

- **Zakończenie świadczenia wsparcia dotyczącego asystenta logowania usługi online firmy Microsoft (SIA) z zestawem RMS SDK.** Będziemy świadczyć pomoc techniczną dotyczącą korzystania z usługi SIA przez 6 miesięcy, a po upływie których wsparcie zostanie zakończone.


## <a name="december-2015-update"></a>Aktualizacja z grudnia 2015 r.

- Zaimplementowane ulepszenia wydajności obejmują kilka obszarów, w tym:
    - Publikowanie z podstawowego serwera licencjonowania w przypadku korzystania z serwerów licencji.
    - Zestaw RMS SDK 2.1 szybciej zwraca błąd w przypadku braku połączenia sieciowego.

- Wiele aktualizacji poprawiających komunikowanie błędów i rozwiązywanie problemów.
- Zaktualizowano również listę [obsługiwanych platform](supported-platforms.md).
- W zestawie RMS SDK 2.1 wyeliminowano konieczność używania środowiska przedprodukcyjnego i manifestów aplikacji. Usunięto sekcje tego zestawu dokumentacji dla deweloperów oraz uproszczono i ponownie zorganizowano ogólną dokumentację.

## <a name="may-2015-update"></a>Aktualizacja z maja 2015 r.

-   **Aplikacje usługi i usługi RMS oparte na chmurze: struktura ** - [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx) wymaga podania trzech informacji: klucza symetrycznego, identyfikatora **AppPrincipalId** oraz identyfikatora **TenantBposId**. W temacie zawierającym omówienie tego zagadnienia dodano wytyczne dotyczące przetwarzania tych informacji. Tę aktualizację można znaleźć w poprawionej wersji artykułu [Umożliwianie współpracy aplikacji usługi z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="april-2015-update"></a>Aktualizacja z kwietnia 2015 r.

-   **Śledzenie dokumentów** jest teraz możliwe za pośrednictwem zestawu nowych interfejsów API. Aby uzyskać więcej informacji, zobacz [Śledzenie zawartości](tracking-content.md).
-   **Typ szyfrowania** — obsługujemy teraz sterowanie na poziomie interfejsu API w celu wybrania pakietu szyfrowania. Aby uzyskać więcej informacji, zobacz [Praca z szyfrowaniem](working-with-encryption.md).

    **Uwaga** Flaga **IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS** nie będzie już widoczna w interfejsach API. Oznacza to, że kompilacje aplikacji odwołujących się do tej flagi nie będą możliwe w przyszłości, ale istniejące aplikacje będą nadal działać, ponieważ będziemy flaga będzie prywatnie uznawana w kodzie interfejsu API. Nadal będzie można uzyskiwać korzyści zapewniane przez przestarzałą flagę algorytmów szyfrowania, zmieniając po prostu flagę. Aby uzyskać więcej informacji, zobacz [Praca z szyfrowaniem](working-with-encryption.md).

-   **Aplikacje w trybie serwera**, w których jest używana [wartość trybu API](https://msdn.microsoft.com/library/hh535236.aspx) **IPC\_API\_MODE\_SERVER**, nie wymagają już manifestu aplikacji. Można przetestować aplikację na serwerze produkcyjnym usługi RMS, przy czym nie jest wymagane uzyskanie licencji produkcyjnej podczas przełączania do środowiska produkcyjnego. Aby uzyskać więcej informacji na temat aplikacji w trybie serwera, zobacz [Typy aplikacji](application-types.md).
-   **Rejestrowanie** jest teraz implementowane zarówno za pośrednictwem plików, jak i śledzenia zdarzeń systemu Windows.
-   Jeśli korzystasz z komputera z systemem **Windows 7 z dodatkiem SP1 lub Windows Server 2008 R2**, zapoznaj się z uwagą umieszczoną pod sekcją „Ważne uwagi dla deweloperów”.

## <a name="january-2015-update"></a>Aktualizacja ze stycznia 2015 r.

-   **Zwiększenie rozmiaru obsługiwanego pliku chronionego (pfile)** — obsługiwane są pliki pfile o rozmiarze przekraczającym jeden gigabajt (1 GB). Aby uzyskać więcej informacji o plikach pfile, zobacz [Obsługiwane formaty plików](supported-file-formats.md).
-   **Ulepszone rejestrowania zapewniające lepszą diagnostykę** — na poziomach rejestrowania będą wyświetlane oznaczenia **BŁĄD** lub **OSTRZEŻENIE** w przypadku komunikatów, które wymagają przejrzenia. Wszystkie inne komunikaty, w tym nadal wyświetlane wyjątki, będą rejestrowane jako **INFORMACJE**.

    Wybraliśmy to rozwiązanie, aby nie dopuścić do przeoczenia żadnych szczegółów. Tylko ważne komunikaty są wyświetlane na poziomie OSTRZEŻENIA.

-   **Uzyskiwanie szablonów firmowych** — znaczące poprawki kodu uzyskiwania szablonów w oparciu o raporty i opinie klientów.
-   Ulepszona spójność lokalizacji

## <a name="october-2014-update"></a>Aktualizacja z października 2014 r.

-   Zaktualizowano domyślne zachowania składnika specyfikacji File API w zestawie SDK. Aby uzyskać więcej informacji, zobacz temat [Konfiguracja interfejsu API plików](file-api-configuration.md).
-   Nowa funkcja powiadomienia e-mail jest opisana w temacie zawierającym uwagi dla deweloperów [Włączanie powiadomień e-mail](how-to-enable-email-notification.md).

## <a name="july-2014-update"></a>Aktualizacja z lipca 2014 r.

Składniki specyfikacji File API w zestawie SDK zostały rozszerzone i oferują następujące funkcje:

-   Określenie funkcji ochrony, których należy użyć.
-   Zapewnienie ochrony za pomocą usługi RMS na poziomie szczegółowości pliku.

    Funkcje dodane w tej wersji:

    **Uwaga** Do rozszerzeń specyfikacji File API dodano dalsze pomocnicze typy i struktury danych, niewymienione w tym temacie. Wszystkie tematy, które zostały zaktualizowane w tej wersji, są oznaczone jako **wersje wstępne i mogą ulec zmianie**.

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

    W tej wersji zestawu Rights Management Services SDK 2.1 można dodać natywną obsługę dowolnego typu pliku (rozszerzenie). Na przykład dla dowolnego rozszerzenia &lt;roz&gt; (innego niż rozszerzenia pakietu office i PDF), będzie używany ciąg \*.p&lt;roz&gt;, jeśli konfiguracja administratora dla tego rozszerzenia ma wartość „NATIVE”.

    Aby uzyskać więcej informacji o obsługiwanych typach plików, zobacz temat [Konfiguracja interfejsu API plików](file-api-configuration.md).

-   **Na komputerach z systemem Windows 7 z dodatkiem SP1 i Windows Server 2008 R2 z dodatkiem SP1** bez aktualizacji [KB2533623](https://support.microsoft.com/en-us/kb/2533623) może wystąpić następujący błąd ochrony dowolnego pliku pakietu Office „Parametr jest nieprawidłowy. Kod błędu 0x80070057”. Jeśli widzisz taki komunikat, zainstaluj aktualizację i spróbuj ponownie. Jeśli problemy występują nadal, skontaktuj się z zespołem ds. opinii o wersji beta zestawu RMS SDK pod adresem <rmcstbeta@microsoft.com>.

    **Uwaga**  Począwszy od wersji z kwietnia 2015 r. dodano test procesu instalacji tej bazy wiedzy.

     

-   **Integracja specyfikacji File API**

    Usługi Active Directory Rights Management z dodatkiem specyfikacji File API zapewniają następujące korzyści i funkcje.

      - Można chronić poufne dane w zautomatyzowany sposób bez szczegółowej znajomości implementacji usługi Zarządzanie prawami do informacji (IRM) używanej przez różne formaty plików.

      - Ochrona natywna może obejmować pliki pakietu Microsoft Office, pliki w formacie Portable Document Format (PDF) oraz inne wybrane typy plików. Pełną listę typów plików, które mogą być chronione przy użyciu ochrony natywnej, można znaleźć w temacie [Konfiguracja interfejsu API plików](file-api-configuration.md).

      - Wszystkie pliki, z wyjątkiem plików systemowych i plików pakietu Office, mogą być chronione przy użyciu formatu pliku chronionego usługi RMS (PFile).

    Interfejs API plików jest implementowany za pośrednictwem następujących czterech nowych funkcji: [IpcfDecryptFile](https://msdn.microsoft.com/library/dn133058.aspx), [IpcfEncryptFile](https://msdn.microsoft.com/library/dn133059.aspx), [IpcfGetSerializedLicenseFromFile](https://msdn.microsoft.com/library/dn133060.aspx) i [IpcfIsFileEncrypted](https://msdn.microsoft.com/library/dn133061.aspx).

    Interfejs API plików wymaga zainstalowania klienta Rights Management Service Client 2.1 na komputerze klienckim i połączenia komputera z serwerem usługi RMS. Aby uzyskać więcej informacji na temat serwera usługi RMS, klienta usługi RMS i ich funkcji, zobacz zawartość TechNet w [dokumentacji usługi RMS dla informatyków](https://technet.microsoft.com/en-us/library/cc771234(v=ws.10).aspx).

-   **Problem**: Podczas tworzenia licencji od podstaw konieczne jest jawne przyznanie praw właściciela.

    **Rozwiązanie**: W przypadku tworzenia licencji od podstaw przy użyciu funkcji [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx) w aplikacji należy jawnie dodać prawa **właściciela** do właściciela licencji. Aby uzyskać więcej informacji, zobacz temat [Dodawanie jawnych praw właściciela](add-explicit-owner-rights.md).

-   **Problem**: Jeśli aplikacja dwukrotnie wywoła funkcję [IpcProtectWindow](https://msdn.microsoft.com/library/hh535268.aspx) lub [IpcUnprotectWindow](https://msdn.microsoft.com/library/hh535272.aspx) w tym samym oknie za pomocą jego uchwytu, zestaw RMS SDK 2.1 zwróci błąd w wyniku **HRESULT**.

    **Rozwiązanie**: Dokładne wskazówki dotyczące rozwiązania tego problemu znajdują się w sekcji uwag w tematach [IpcProtectWindow](https://msdn.microsoft.com/library/hh535268.aspx) i [IpcUnprotectWindow](https://msdn.microsoft.com/library/hh535272.aspx).

-   **Problem**: W przypadku tworzenia wielu architektur należy skorzystać z poniższych wskazówek.

    **Rozwiązanie**: Aby użyć pliku Ipcsecproc\*isv.dll dla innej architektury (na przykład w sytuacji, gdy 64-bitowy zestaw SDK został zainstalowany w systemie 64-bitowym, ale teraz ma zostać wdrożony w systemie 32-bitowym, który wymaga pliku Ipcsecproc\*isv.dll), należy zainstalować 32-bitowy zestaw SDK na innym komputerze i skopiować tam pliki Ipcsecproc\*isv.dll z folderu „%PROGRAMFILES%\\Microsoft Information Protection And Control” (do lokalizacji domyślnej lub wybranej lokalizacji instalacji zestawu SDK).

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**P**: Jak domyślne zachowanie języka współdziała z funkcjami, które przyjmują parametr LCID?

**O**: Użyj wartości 0 dla domyślnych ustawień regionalnych. W takim przypadku klient usług AD RMS w wersji 2.1 wyszukuje nazwy i opisy w następującej kolejności i pobiera pierwszą dostępną wartość:

    1 - User preferred LCID.
    2 - System locale LCID.
    3 - The first available language specified in the Rights Management Server (RMS) template.

Jeśli nie będzie można pobrać nazwy ani opisu, zostanie zwrócony błąd. Może istnieć tylko jedna nazwa i opis dla określonego identyfikatora LCID.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
