---
title: "Nowości i informacje o wersji | Azure RMS"
description: "Spis ważnych zmian i funkcji w tej nowej wersji zestawu RMS SDK."
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 9fd96c934d4f7a8e09035ff7eda4517f65a27e17
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="whats-new-and-release-notes"></a>Nowości i informacje o wersji

## <a name="whats-new"></a>Co nowego
Zestaw Microsoft Rights Management SDK 4.2 umożliwia łatwiejsze i bardziej elastyczne włączanie aplikacji RMS. W tym temacie wymieniono ważne zmiany i funkcjonalności w tej wersji zestawu RMS SDK.

### <a name="new-for-june-2016"></a>Nowości z czerwca 2016 r.

- **Obsługa nowoczesnego uwierzytelniania** — umożliwi logowanie oparte na bibliotece uwierzytelniania usługi Active Directory (ADAL) do aplikacji z obsługą usługi RMS. Zostaną udostępnione opcje logowania, takie jak usługa Multi-Factor Authentication (MFA), oparci na języku SAML dostawcy tożsamości firm zewnętrznych z aplikacjami klienckimi usługi RMS oraz uwierzytelnianie oparte na kartach inteligentnych i certyfikatach. Równocześnie zostanie wyeliminowana potrzeba korzystania z protokołu uwierzytelniania podstawowego w aplikacjach z obsługą usługi RMS.
- **Obsługa śledzenia dokumentów** — deweloperzy mogą teraz włączać śledzenie dokumentów w przypadku objęcia ich ochroną w swoich aplikacjach.
- Ulepszenia wydajności
- Poprawki


### <a name="december-2015-update"></a>Aktualizacja z grudnia 2015 r.

W tym wydaniu zestaw RMS SDK dla urządzeń ma wersję 4.2 i dodaje następujące funkcjonalności:

-   Śledzenie dokumentów, usługa RMS tylko w trybie online dla systemów operacyjnych iOS/OS X i Android.

    Aby uzyskać szczegółowe informacje i wskazówki dotyczące użycia w systemach iOS/OS X, zapoznaj się z klasą [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx), która dostarcza informacje dotyczące śledzenia, a także dodatkową metodą rejestrowania śledzenia dokumentów w zasadzie [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx). Istnieją podobne dodatki dla systemu Android do klasy [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx) i zasady [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx).

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

W tej wersji dodano następujące funkcjonalności:

-   Zestaw RMS SDK 4.1 dla platform Linux

    Aby uzyskać więcej informacji, zobacz temat [Rozpoczynanie pracy](get-started.md).

### <a name="may-2015-update---adds-logging-control"></a>Aktualizacja z maja 2015 r. — dodaje sterowanie rejestrowaniem

W tej wersji dodano obsługę następujących funkcjonalności:

-   iOS

    Szyfrowanie i deszyfrowanie aplikacji może działać niezależnie i równolegle.

    Aby uzyskać więcej informacji, zobacz klasę [MSProtector](https://msdn.microsoft.com/library/mt210993.aspx).

    Włączono ustawienia kontroli poziomu dziennika.

    Aby uzyskać więcej informacji, zobacz temat [Porady: Włączanie rejestrowania błędów i wydajności](enabling-logging.md)

    Dodano obsługę czyszczenia pamięci podręcznej.

    Aby uzyskać więcej informacji, zobacz metodę [MSProtection:resetStateWithCompletionBlock](https://msdn.microsoft.com/library/mt210991.aspx).

### <a name="february-2015-update---adds-windows-store-application-support"></a>Aktualizacja z lutego 2015 r. — dodaje obsługę aplikacji ze Sklepu Windows

W tym wydaniu dodano obsługę aplikacji ze Sklepu Windows, zapewniając funkcjonalność odpowiadającą wydaniom dla systemów Windows Phone, Android i iOS/OS zestawu RMS SDK 4.1.

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
-   **Użycie trybu offline** — użytkownicy końcowi mogą uzyskać dostęp do chronionych przez usługę RMS danych w trybie offline.
-   **Rozdzielone uwierzytelnianie** — deweloperzy mogą używać własnych bibliotek uwierzytelniania dla usług Azure RMS i AD RMS (lub używać zalecanej [biblioteki uwierzytelniania usługi Azure AD (ADAL)](https://MSDN.Microsoft.Com/library/jj573266.aspx)).
-   **Rozdzielony interfejs użytkownika** —deweloperzy mogą tworzyć interfejsy użytkownika, aby używać dokumentów chronionych przez usługę RMS i ochraniać je.
-   **Zmieniony interfejs API** — deweloperzy mogą korzystać z prostego i przejrzystego interfejsu API szyfrowania i odszyfrowywania, który zapewnia spójne działanie usługi RMS i interfejsu użytkownika przy minimalnym wysiłku.

**Wspólne dla wszystkich platform**

-   Interfejsy API zestawi RMS SDK 4.x nie są *bezpieczne wątkowo*.

**Android**

-   Korzystając z przykładowej aplikacji na urządzeniu z systemem Amazon® Kindle do wyświetlania załączników PTXT, należy najpierw pobrać plik zanim będzie się go wyświetlać.

    **Rozwiązanie** — jest to znany problem i zostanie rozwiązany później.

-   Aplikacja, która korzysta z zestawu SDK może ulec awarii w przypadku zezwolenia na działanie wielu wystąpień.

    **Rozwiązanie** — upewnij się, że aplikacja nie zezwala na wywołania interfejsu API systemu Android przez wiele wystąpień.

-   W razie użycia metody [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write(byte\[\] array, int offset, int length) z parametrem length różnym od wartości *array.length* późniejsze użycie zawartości za pomocą zestawu SDK jest niemożliwe.

    **Rozwiązanie** — jest to znany problem. Aby go unikać, zawsze przekazuj parametr *byte \[\]* array o długości odpowiadającej parametrowi length lub używaj metody [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write(byte\[\] array).

**Systemy iOS i OS X**

-   Istnieją dwa dialekty języka portugalskiego obsługiwane przez nasze zestawy SDK dla systemów operacyjnych iOS i OS X. Niestety z powodu usterki, obecnie nie obsługujemy całkowicie 1. lokalizacji. Z powodu tej usterki język portugalski nie jest w pełni obsługiwany. Przetłumaczono większość tekstu, ale nie interfejs użytkownika.

    1. portugalski

    2. Portugalski (Portugalia)

**Tylko system iOS**

-   Zestaw RMS SDK4.x nie pokazuje wskaźnika działania sieci.

    Jest to znane zachowanie opcjonalne systemu iOS zgodnie z dokumentem Apple Human Interface Guidelines.

**Tylko system OS X**

-   Zestaw RMS SDK4.x nie pokazuje wskaźnika działania sieci.

    Jest to znane zachowanie opcjonalne systemu OS X zgodnie z dokumentem Apple Human Interface Guidelines.

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

**Odpowiedź**: wyślij wiadomość e-mail na adres <rmcstbeta@microsoft.com> z żądaniem poświadczeń dla organizacji testowych usługi Azure AD RMS.

**Pytanie**: w niniejszej dokumentacji nie widzę żadnych informacji o hierarchii testowej. Dlaczego?

**Odpowiedź**: w nowych zestawach AD RMS SDK nie obowiązuje koncepcja hierarchii testowej. Zawsze korzystasz z hierarchii produkcyjnej.

**Pytanie**: W wersji 2.1 zestawu RMS SDK dla każdej aplikacji implementującej ochronę informacji był potrzebny wygenerowany manifest. Czy obowiązuje to nadal wersji 4.0 i nowszych wersjach zestawu SDK?

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

**Pytanie**: przykładowa platforma aplikacji została dostosowana do wersji Xcode 5. Czy mogę pracować z wersją Xcode 4.6?

**Odpowiedź**: OS X SDK współpracuje tylko z Xcode 4.6 i nowszymi wersjami, a także z systemem OS X 10.8 i nowszymi.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]