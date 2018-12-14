---
title: Nowości i informacje o wersji
description: Wymieniono ważne zmiany i funkcje, w tym i poprzednich wersji.
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 12/11/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 6433352f05401fcaafc84704a0441941ff87bdf3
ms.sourcegitcommit: 1cd4edd4ba1eb5e10cb61628029213eda316783a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53266702"
---
# <a name="whats-new-and-release-notes"></a>Nowości i informacje o wersji

## <a name="whats-new"></a>Co nowego

W tym temacie wymieniono ważne zmiany i funkcjonalności w tej nowej wersji v4.x zestawu RMS SDK.

-   [Nowość w lipca 2017 r.](#new-for-july-2017)
-   [Aktualizacja z października 2016](#October-2016-update)
-   [Aktualizacja z czerwca 2016](#june-2016-update)
-   [Aktualizacja z grudnia 2015](#december-2015-update)
-   [Aktualizacja z lipca 2015 — dodaje obsługę systemu Linux / programowania w języku C++](#july-2015-update---adds-support-for-linux--c-development)
-   [Może być 2015 update — dodaje Sterowanie rejestrowaniem](#may-2015-update---adds-logging-control)
-   [Aktualizacja z lutego 2015 — Obsługa aplikacji dodaje Windows Store](#february-2015-update---adds-windows-store-application-support)
-   [Styczeń 2015 aktualizacja — dodaje obsługę platformy WinPhone](#january-2015-update---adds-winphone-platform-support)
-   [Październik 2014 update - uaktualnienia do programu Microsoft RMS SDK 4.1](#october-2014-update---upgrade-to-microsoft-rms-sdk-4-1)
-   [Informacje o wersji](#release-notes)
-   [Często zadawane pytania](#frequently-asked-questions)

### <a name="new-for-july-2017"></a>Nowość w lipca 2017 r.

Aktualizacja dla naszych wersji Lipcowej uwzględnione, wersja zestawu SDK, teraz 4.2.5 przyrostu o wartości.

- Zestaw SDK systemu android: Aplikację można teraz **Ustaw rejestrowania poziomu na bieżąco** przy użyciu zestawu SDK systemu Android. Aby uzyskać więcej informacji, zobacz [jak: Włączanie rejestrowania błędów i wydajności](https://docs.microsoft.com/information-protection/develop/enabling-logging)
- Zestaw SDK systemu iOS nie obsługuje poziomu rejestrowania. 
- Zestaw SDK jest teraz zwraca błąd dla tokenu dostępu o wartości NULL.

### <a name="october-2016-update"></a>Aktualizacja z października 2016

- Implementuje kilka poprawek błędów zaplecza.
- Włącz kod bitcode dla firmy Apple dla systemu iOS/OSX zestawu SDK.

### <a name="june-2016-update"></a>Aktualizacja z czerwca 2016

- **Obsługa nowoczesnego uwierzytelniania** — oferuje oparte na Active Directory uwierzytelniania biblioteki ADAL logowania do usług RMS w aplikacjach z obsługą. Umożliwia ona funkcje logowania takich jak uwierzytelnianie wieloskładnikowe (MFA), opartej na SAML dostawcy tożsamości innych firm z aplikacjami klienckimi usługi RMS, karty inteligentnej i uwierzytelniania opartego na certyfikatach oraz jego eliminuje konieczność stosowania usług RMS z obsługą aplikacji, aby użyć podstawowa Protokół uwierzytelniania.
- **Obsługa śledzenia dokumentów** — deweloperzy mogą teraz włączać śledzenie dokumentów w przypadku objęcia ich ochroną w swoich aplikacjach.
- Ulepszenia wydajności
- Poprawki błędów

### <a name="december-2015-update"></a>Aktualizacja z grudnia 2015 r.

W tym wydaniu zestaw RMS SDK dla urządzeń ma wersję 4.2 i dodaje następujące funkcjonalności:

-   Śledzenie dokumentów, usługa RMS tylko w trybie online dla systemów operacyjnych iOS/OS X i Android.

    Aby uzyskać szczegółowe informacje i wskazówki dotyczące użycia w systemach iOS/OS X, zobacz [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx) klasy, która dostarcza informacje dotyczące śledzenia i dokumentu dodatkową metodą rejestrowania śledzenia na [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx). Istnieją podobne dodatki dla systemu Android do klasy [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx) i zasady [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx).

    Aby uzyskać szczegółowy opis funkcjonalności śledzenia dokumentów, zobacz [jak: Korzystanie ze śledzenia dokumentów](how-to-use-document-tracking.md).

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

W tej wersji dodano następujące aktualizacje:

-   Zestaw RMS SDK 4.1 dla platform Linux

    Aby uzyskać więcej informacji, zobacz temat [Rozpoczynanie pracy](get-started.md).

### <a name="may-2015-update---adds-logging-control"></a>Aktualizacja z maja 2015 r. — dodaje sterowanie rejestrowaniem

W tej wersji dodano obsługę następujących aktualizacji:

-   iOS

    Szyfrowanie i deszyfrowanie aplikacji może działać niezależnie i równolegle.

    Aby uzyskać więcej informacji, zobacz klasę [MSProtector](https://msdn.microsoft.com/library/mt210993.aspx).

    Włączono ustawienia kontroli poziomu dziennika.

    Aby uzyskać więcej informacji, zobacz [jak: Włączanie rejestrowania błędów i wydajności](enabling-logging.md)

    Dodano obsługę czyszczenia pamięci podręcznej.

    Aby uzyskać więcej informacji, zobacz metodę [MSProtection:resetStateWithCompletionBlock](https://msdn.microsoft.com/library/mt210991.aspx).

### <a name="february-2015-update---adds-windows-store-application-support"></a>Aktualizacja z lutego 2015 r. — dodaje obsługę aplikacji ze Sklepu Windows

Ta wersja dodaje obsługę aplikacji Windows Store i zapewnia parzystość Windows Phone, Android i iOS/OS X wersji zestawu RMS SDK 4.1.

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
-   **Użycie trybu offline** — użytkownicy końcowi mogą uzyskiwać dostęp danych chronionych przez usługę RMS w trybie offline.
-   **Rozdzielone uwierzytelnianie** — deweloperzy mogą używać własnych bibliotek uwierzytelniania dla usług Azure RMS i AD RMS (lub używać zalecanej [biblioteki uwierzytelniania usługi Azure AD (ADAL)](https://MSDN.Microsoft.Com/library/jj573266.aspx)).
-   **Rozdzielony interfejs użytkownika** —deweloperzy mogą tworzyć interfejsy użytkownika, aby używać dokumentów chronionych przez usługę RMS i ochraniać je.
-   **Przeprojektowany interfejs API** — deweloperzy mogą cieszyć się bardzo prosty i przejrzysty szyfrowania i odszyfrowywania interfejsu API, który zapewnia spójne działanie usługi RMS oraz komfort użytkownika, przy minimalnym wysiłku.

**Wspólne dla wszystkich platform**

-   Interfejsy API zestawi RMS SDK 4.x nie są *bezpieczne wątkowo*.

**Android**

-   Korzystając z przykładowej aplikacji na urządzeniu z systemem Amazon® Kindle do wyświetlania załączników PTXT, należy najpierw pobrać plik zanim będzie się go wyświetlać.

    **Rozwiązanie** -znany problem, który zostanie rozwiązany później.

-   Aplikacja, która korzysta z zestawu SDK może ulec awarii w przypadku zezwolenia na działanie wielu wystąpień.

    **Rozwiązanie** — upewnij się, że aplikacja nie zezwala na wywołania interfejsu API systemu Android przez wiele wystąpień.

-   Kiedy używać [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write (byte\[ \] array, int offset, int length) metody z length różnym od *array.length* wartość, nie mogę się Używanie zawartości później za pomocą zestawu SDK.

    **Rozwiązanie** — jest to znany problem. Aby go unikać, zawsze przekazuj parametr *byte \[\]* array o długości odpowiadającej parametrowi length lub używaj metody [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write(byte\[\] array).

**Systemy iOS i OS X**

-   Istnieją dwa dialekty języka portugalskiego obsługiwane przez nasze zestawy SDK dla systemów operacyjnych iOS i OS X. Niestety ze względu na usterkę, firma Microsoft nie obsługujemy pierwszej lokalizacji całkowicie. Z powodu tej usterki język portugalski nie jest w pełni obsługiwany. Przetłumaczono większość tekstu, ale nie interfejs użytkownika.

    1. portugalski

    2. Portugalski (Portugalia)

**Tylko system iOS**

-   Zestaw RMS SDK4.x nie pokazuje wskaźnika działania sieci.

    Jest to znane zachowanie opcjonalne systemu iOS zgodnie z Apple Human Interface Guidelines.

**Tylko system OS X**

-   Zestaw RMS SDK4.x nie pokazuje wskaźnika działania sieci.

    Jest to znane zachowanie opcjonalne OS X zgodnie z dokumentem Apple Human Interface Guidelines.

-   **Rozwiązanie** — aby utworzyć aplikację z interfejsem wielu dokumentów (MDI) za pomocą naszego zestawu OS X SDK, użyj poniższych wskazówek.

    Następujących metod nie wolno uruchamiać jednocześnie. Aby monitorować przebieg działania, użyj wspomnianego podejścia bloku ukończenia zgodnie z informacjami.

    - [MSProtectedData.protectedDataWithProtectedFile](https://msdn.microsoft.com/library/dn758351.aspx)
    - [MSCustomProtectedData.customProtectedDataWithPolicy](https://msdn.microsoft.com/library/dn758315.aspx)



**Uwaga**  aplikacje MDI nie są obsługiwane przez naszych interfejsów API systemu iOS.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

**Wszystkie platformy**

**Q**: Nie widzę **uprawnienia niestandardowe** wybór interfejsu użytkownika w przepływie pracy ochrony. Dlaczego?

**A**: Jest to znany problem i zostanie rozwiązany później.

**Q**: Jak uzyskać nowego organizacyjnego dzierżawcę, aby wypróbować zestaw SDK i przykładowe aplikacje?

**A**: Aby zgłosić żądanie poświadczeń dla organizacji testowych usługi Azure AD RMS, Wyślij e-mail na adres <rmcstbeta@microsoft.com>.

**Q**: Nie widać żadnych hierarchii testowej w dokumentacji. Dlaczego?

**A**: Nie obowiązuje koncepcja hierarchii testu za pomocą nowych zestawach AD RMS SDK. Zawsze korzystasz z hierarchii produkcyjnej.

**Q**: W wersji 2.1 zestawu RMS SDK dla każdej aplikacji implementującej ochronę informacji był potrzebny wygenerowany manifest. To jest nadal dotyczy 4.0 i nowsze wersje zestawu SDK?

**A**: Nie, manifesty nie są już potrzebne do wersji 3.0 ani nowszych zestawu Rights Management SDK.

**Android**

**Q**: Których środowiskach programistycznych zestaw SDK został przetestowany przy użyciu?

**A**: Eclipse Juno z interfejsem Google API 15 lub nowszym.

**Q**: Czy mogę wywołać cancel() metodę anulowani z wątku interfejsu użytkownika?
**A**: Metodę cancel() należy wywoływać z wątku innego niż interfejsu użytkownika, ponieważ może to przerwać połączenie sieciowe.

**iOS**

**Q**: Których platformach sprawdzono programowanie z zestawem SDK?

**A**: Środowisko Xcode 5.0 z systemem iOS 7 i nowszym.

**Q**: Po wywołaniu metody cancel() na operacji, jednak nadal otrzymuję powiadomienie, że operacja zakończona. Dlaczego?

**A**: Nie wszystkie operacje mogą zostać anulowane, więc operacja anulowania jest wykonywana jako najlepszy możliwy.

**OS x**

**Q**: Przykładowa platforma aplikacji została dostosowana do wersji Xcode 5, można pracować z wersją Xcode 4.6?

**Odpowiedź**: OS X SDK współpracuje tylko z Xcode 4.6 i nowszymi wersjami, a także z systemem OS X 10.8 i nowszymi.

