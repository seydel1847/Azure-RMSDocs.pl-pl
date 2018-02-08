---
title: "Nowości i informacje o wersji"
description: "Spis ważnych zmian i funkcji w tym i poprzednich wersjach."
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 09/25/2017
ms.topic: article
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 130da5ecf3fb95297f9bc335b1ea5023d53c589f
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="whats-new-and-release-notes"></a>Nowości i informacje o wersji

## <a name="whats-new"></a>Co nowego

W tym temacie wymieniono ważne zmiany i funkcje w tej nowej wersji zestawu RMS SDK v4.x.

-   [Nowość w lipcu 2017](#new-for-july-2017)
-   [Aktualizacja z października 2016](#October-2016-update)
-   [Aktualizacja czerwca 2016 r.](#new-for-June-2016)
-   [Aktualizacja z grudnia 2015 r.](#december-2015-update)
-   [Aktualizacja z lipca 2015 r. — dodaje obsługę systemu Linux / programowania w języku C++](#july-2015-update-adds-support-for-linux-c-developm)
-   [Może aktualizacji 2015 r. — dodaje Sterowanie rejestrowaniem](#may-2015-update-adds-logging-control)
-   [Aktualizacja z lutego 2015 r. — obsługę aplikacji ze Sklepu Windows dodaje](#february-2015-update-adds-windows-store-application-support)
-   [Aktualizacja ze stycznia 2015 r. — dodaje obsługę platformy winphone](#january-2015-update-adds-winphone-platform-support)
-   [Października 2014 r. aktualizacja — uaktualnienie do zestawu Microsoft RMS SDK 4.1](#october-2014-update-upgrade-to-microsoft-rms-sdk-4-1)
-   [Informacje o wersji](#release-notes)
-   [Często zadawane pytania](#frequently-asked-questions)

### <a name="new-for-july-2017"></a>Nowość w lipcu 2017

Aktualizacja dla naszych wersji Lipcowej uwzględnione zwiększanie poprawki zestawu SDK, teraz 4.2.5.

- Zestaw SDK systemu android: Aplikacji można teraz **ustawić rejestrowania poziomu na bieżąco** z zestawu SDK systemu Android. Aby uzyskać więcej informacji, zobacz temat [Porady: Włączanie rejestrowania błędów i wydajności](https://docs.microsoft.com/information-protection/develop/enabling-logging)
- Zestaw SDK systemu iOS nie obsługuje poziomu rejestrowania. 
- Zestaw SDK teraz zwraca błąd dla tokenu dostępu do wartości NULL.

### <a name="october-2016-update"></a>Aktualizacja z października 2016

- Implementuje kilka poprawek błędów zaplecza.
- Włącz kodu bitowego dla Apple iOS/OS zestawu SDK.

### <a name="june-2016-update"></a>Aktualizacja czerwca 2016 r.

- **Obsługa nowoczesnego uwierzytelniania** — przełącza na podstawie Active Directory Authentication Library ADAL logowania do usług RMS w aplikacjach z obsługą. Umożliwia ona funkcje logowania takich jak uwierzytelnianie wieloskładnikowe (MFA), na języku SAML dostawcy tożsamości innych firm z aplikacjami klienckimi usługi RMS, karty inteligentnej i uwierzytelnianie oparte na certyfikatach i eliminuje to potrzebę RMS z obsługą aplikacji, które mają korzystać z podstawowego Protokół uwierzytelniania.
- **Obsługa śledzenia dokumentów** — deweloperzy mogą teraz włączać śledzenie dokumentów w przypadku objęcia ich ochroną w swoich aplikacjach.
- Ulepszenia wydajności
- Poprawki

### <a name="december-2015-update"></a>Aktualizacja z grudnia 2015 r.

W tym wydaniu zestaw RMS SDK dla urządzeń ma wersję 4.2 i dodaje następujące funkcjonalności:

-   Śledzenie dokumentów, usługa RMS tylko w trybie online dla systemów operacyjnych iOS/OS X i Android.

    Aby uzyskać szczegółowe informacje i wskazówki dotyczące użycia w systemie iOS/OS X, zobacz [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx) klasy, która dostarcza informacje o śledzeniu i dokumentu dodatkową metodą rejestrowania śledzenia na [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx). Istnieją podobne dodatki dla systemu Android do klasy [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx) i zasady [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx).

    Aby uzyskać szczegółowy opis funkcjonalności śledzenia dokumentów, zobacz temat [Instrukcje: korzystanie ze śledzenia dokumentów](how-to-use-document-tracking.md).

-   Zbiór metod synchronicznych, które w sposób równoległy realizują wersje asynchroniczne dla interfejsu API systemu Android:

    [Metoda synchroniczna CustomProtectedInputStream.create](https://msdn.microsoft.com/library/mt631362.aspx)

    [Metoda synchroniczna CustomProtectedOutputStream.create](https://msdn.microsoft.com/library/mt631363.aspx)

    [Metoda synchroniczna ProtectedFileInputStream.create](https://msdn.microsoft.com/library/mt631375.aspx)

    [Metoda synchroniczna ProtectedFileOutputStream.create](https://msdn.microsoft.com/library/mt631376.aspx)

    [Metoda synchroniczna TemplateDescriptor.getTemplates](https://msdn.microsoft.com/library/mt631380.aspx)

    [Metoda synchroniczna UserPolicy.acquire](https://msdn.microsoft.com/library/mt631384.aspx)

    [Metoda synchroniczna UserPolicy.create (PolicyDescriptor...)**](https://msdn.microsoft.com/library/mt631385.aspx)

    [Metoda synchroniczna UserPolicy.create (TemplateDescriptor...)](https://msdn.microsoft.com/library/mt631386.aspx)

-   Nowa klasa [ProtectedBuffer](https://msdn.microsoft.com/library/mt631369.aspx) została dodana do interfejsu API systemu Android.
-   Aktualizacje poprawiające komunikowanie błędów i rozwiązywanie problemów.
-   Znaczący wzrost wydajności operacji kryptograficznych.

### <a name="july-2015-update---adds-support-for-linux--c-development"></a>Aktualizacja z lipca 2015 r. — dodaje obsługę systemu Linux / programowania w języku C++

Tej wersji dodano następujące aktualizacje:

-   Zestaw RMS SDK 4.1 dla platform Linux

    Aby uzyskać więcej informacji, zobacz temat [Rozpoczynanie pracy](get-started.md).

### <a name="may-2015-update---adds-logging-control"></a>Aktualizacja z maja 2015 r. — dodaje sterowanie rejestrowaniem

Ta wersja dodaje obsługę następujące aktualizacje:

-   iOS

    Szyfrowanie i deszyfrowanie aplikacji może działać niezależnie i równolegle.

    Aby uzyskać więcej informacji, zobacz klasę [MSProtector](https://msdn.microsoft.com/library/mt210993.aspx).

    Włączono ustawienia kontroli poziomu dziennika.

    Aby uzyskać więcej informacji, zobacz temat [Porady: Włączanie rejestrowania błędów i wydajności](enabling-logging.md)

    Dodano obsługę czyszczenia pamięci podręcznej.

    Aby uzyskać więcej informacji, zobacz metodę [MSProtection:resetStateWithCompletionBlock](https://msdn.microsoft.com/library/mt210991.aspx).

### <a name="february-2015-update---adds-windows-store-application-support"></a>Aktualizacja z lutego 2015 r. — dodaje obsługę aplikacji ze Sklepu Windows

Ta wersja dodaje obsługę aplikacji ze Sklepu Windows i Windows Phone, Android i iOS/OS X wersji zestawu RMS SDK 4.1 zapewnia parzystość funkcji.

### <a name="january-2015-update---adds-winphone-platform-support"></a>Aktualizacja ze stycznia 2015 r. — dodaje obsługę platformy WinPhone

W tym wydaniu dodano obsługę systemu Windows Phone, zapewniając funkcjonalność odpowiadającą wydaniom dla systemów Android i iOS/OS zestawu RMS SDK 4.1.

### <a name="october-2014-update---upgrade-to-microsoft-rms-sdk-41"></a>Aktualizacja z października 2014 r. — uaktualnienie do zestawu Microsoft RMS SDK 4.1

W wydaniu wersji 4.1 zestawu RMS SDK dodano następujące nowe funkcjonalności do systemów Google Android i Apple iOS / OS X.

-   Rozszerzenia API zestawu SDK dla systemów Android i iOS/OS X dotyczące przetwarzania *zgody użytkownika*, umożliwiające potwierdzanie przez użytkownika działań zestawu SDK. Obecnie obsługiwanymi typami wyrażania zgody są śledzenie dokumentów i dostęp do nieznanych adresów URL usługi AD RMS.

    Aby uzyskać więcej informacji, zobacz jako przykład wersję [ConsentCallback interface](https://msdn.microsoft.com/library/dn833503.aspx) przeznaczoną dla interfejsu API systemu Android.

-   Systemy iOS 8 i OS X 10.10 (Yosemite) są teraz obsługiwane. Wprowadzono również kilka zmian nazw właściwości wymaganych przez Xcode 6.

    Na przykład nazwa właściwości MSUserPolicy.name została zmieniona na [MSUserPolicy.policyName](https://msdn.microsoft.com/library/dn790799.aspx).

## <a name="release-notes"></a>Informacje o wersji

W tej części przedstawiono istotne dla deweloperów informacje o bieżącym i poprzednich wydaniach interfejsów API zestawu Microsoft Rights Management SDK 4.x.

**Usługi AD RMS SDK 4.1 — wydanie z dostępnością globalną dla systemów iOS/OS X i Android**

-   **Obsługa usług AD RMS** —administratorzy IT mogą używać aplikacji z włączoną usługą RMS na urządzeniach przenośnych z rozszerzeniami dla urządzeń przenośnych nowego serwera usług AD RMS.
-   **Użycie trybu offline** — użytkownicy końcowi mają dostęp do danych chronionych przez usługę RMS w trybie offline.
-   **Rozdzielone uwierzytelnianie** — deweloperzy mogą używać własnych bibliotek uwierzytelniania dla usług Azure RMS i AD RMS (lub używać zalecanej [biblioteki uwierzytelniania usługi Azure AD (ADAL)](https://MSDN.Microsoft.Com/library/jj573266.aspx)).
-   **Rozdzielony interfejs użytkownika** —deweloperzy mogą tworzyć interfejsy użytkownika, aby używać dokumentów chronionych przez usługę RMS i ochraniać je.
-   **Przeprojektowany interfejsu API** — deweloperzy mogą korzystać prosty i przezroczystego szyfrowania i odszyfrowywania interfejsu API, który zapewnia spójne działanie usługi RMS i środowisko, przy minimalnym wysiłku.

**Wspólne dla wszystkich platform**

-   Interfejsy API zestawi RMS SDK 4.x nie są *bezpieczne wątkowo*.

**Android**

-   Korzystając z przykładowej aplikacji na urządzeniu z systemem Amazon® Kindle do wyświetlania załączników PTXT, należy najpierw pobrać plik zanim będzie się go wyświetlać.

    **Rozwiązanie** -znany problem zostanie rozwiązany później.

-   Aplikacja, która korzysta z zestawu SDK może ulec awarii w przypadku zezwolenia na działanie wielu wystąpień.

    **Rozwiązanie** — upewnij się, że aplikacja nie zezwala na wywołania interfejsu API systemu Android przez wiele wystąpień.

-   Kiedy używać [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write (byte\[ \] array, int offset, int length) metody z parametrem length różnym od *array.length* wartość, nie jestem stanie korzystać z zawartości później za pomocą zestawu SDK.

    **Rozwiązanie** — jest to znany problem. Aby go unikać, zawsze przekazuj parametr *byte \[\]* array o długości odpowiadającej parametrowi length lub używaj metody [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write(byte\[\] array).

**Systemy iOS i OS X**

-   Istnieją dwa dialekty języka portugalskiego obsługiwane przez nasze zestawy SDK dla systemów operacyjnych iOS i OS X. Niestety z powodu usterki, firma Microsoft nie obsługują aktualnie pierwszy lokalizacja całkowicie. Z powodu tej usterki język portugalski nie jest w pełni obsługiwany. Przetłumaczono większość tekstu, ale nie interfejs użytkownika.

    1. portugalski

    2. Portugalski (Portugalia)

**Tylko system iOS**

-   Zestaw RMS SDK4.x nie pokazuje wskaźnika działania sieci.

    Jest to znane zachowanie opcjonalne systemu iOS zgodnie z Apple Human Interface Guidelines.

**Tylko system OS X**

-   Zestaw RMS SDK4.x nie pokazuje wskaźnika działania sieci.

    Jest to znane zachowanie opcjonalne OS X zgodnie z dokumentem Apple Human Interface Guidelines.

-   **Rozwiązanie** — aby utworzyć aplikację z interfejsem wielu dokumentów (MDI) za pomocą naszego zestawu OS X SDK, użyj poniższych wskazówek.

    Następujących metod nie wolno uruchamiać jednocześnie. Aby monitorować przebieg działania, użyj wspomnianego podejścia bloku ukończenia.

    - [MSProtectedData.protectedDataWithProtectedFile](https://msdn.microsoft.com/library/dn758351.aspx)
    - [MSCustomProtectedData.customProtectedDataWithPolicy](https://msdn.microsoft.com/library/dn758315.aspx)



**Uwaga**  — aplikacje MDI nie są obsługiwane przez nasz interfejs API dla systemu iOS.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Wszystkie platformy**

**Pytanie**: nie widzę elementu wyboru **Uprawnienia niestandardowe** w interfejsie użytkownika w przepływie pracy ochrony. Dlaczego?

**Odpowiedź**: jest to znany problem i zostanie rozwiązany później.

**Pytanie**: jak uzyskać nowego organizacyjnego dzierżawcę, aby wypróbować zestaw SDK i przykładowe aplikacje?

**A**: Aby poprosić o poświadczenia dla organizacji testowych usługi Azure AD RMS, Wyślij wiadomość e-mail do <rmcstbeta@microsoft.com>.

**Pytanie**: w niniejszej dokumentacji nie widzę żadnych informacji o hierarchii testowej. Dlaczego?

**Odpowiedź**: w nowych zestawach AD RMS SDK nie obowiązuje koncepcja hierarchii testowej. Zawsze korzystasz z hierarchii produkcyjnej.

**Q**: W wersji 2.1 zestawu RMS SDK wygenerowany manifest było wymagane dla każdej aplikacji implementującej ochronę informacji. Dotyczy to nadal wersji 4.0 i nowsze wersje zestawu SDK?

**Odpowiedź**: nie, manifesty nie są już potrzebne w wersji 3.0 ani nowszych zestawu Rights Management SDK.

**Android**

**Pytanie**: w których środowiskach programistycznych został przetestowany zestaw SDK?

**Odpowiedź**: Eclipse Juno z interfejsem Google API 15 lub nowszym.

**Pytanie**: czy można wywołać metodę anulowani cancel() z wątku interfejsu użytkownika?
**Odpowiedź**: metodę cancel() należy wywoływać z wątku innego niż wątek interfejsu użytkownika, ponieważ może to przerwać połączenie sieciowe.

**iOS**

**Pytanie**: na których platformach sprawdzono programowanie z zestawem SDK?

**Odpowiedź**: Xcode 5.0 z systemem iOS 7 i nowszym.

**Pytanie**: po wywołaniu metody cancel() na operacji nadal otrzymuję powiadomienie, że operacja została ukończona. Dlaczego?

**Odpowiedź**: nie wszystkie operacje mogą zostać anulowane, więc operacja anulowania jest wykonywana w najlepszy możliwy sposób.

**OS x**

**Q**: przykładowa platforma aplikacji została dostosowana do wersji Xcode 5, można pracować z wersją Xcode 4.6?

**Odpowiedź**: OS X SDK współpracuje tylko z Xcode 4.6 i nowszymi wersjami, a także z systemem OS X 10.8 i nowszymi.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
