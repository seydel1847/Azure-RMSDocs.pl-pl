---
title: Pojęcia — podstawowe pojęcia dotyczące zestawu SDK MIP — profil i aparatu
description: Ten artykuł pomoże zrozumieć podstawowe pojęcia dotyczące zestawu SDK, o nazwie profilu i silnika, które są tworzone podczas inicjowania aplikacji.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 05a66dc7a00b976dfb9883f44b3c93a25b4b6975
ms.sourcegitcommit: 0d3b43c9cedbaeae65299ac372fbfb9ad66ce27f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2019
ms.locfileid: "54183630"
---
# <a name="microsoft-information-protection-sdk---profile-and-engine-object-concepts"></a>Zestaw SDK — profil i aparat Microsoft Information Protection obiektu pojęcia

## <a name="profiles"></a>Profile

Profil, który jest klasą głównego dla wszystkich operacji w zestawie SDK MIP. Przed rozpoczęciem korzystania z żadnego z trzech interfejsów API, aplikacja kliencka musi utworzyć profil. W profilu lub przez inne obiekty, wykonywane są operacje przyszłych *dodano* do profilu.

Istnieją trzy typy profilu w zestawie SDK Mipmapy:

- [`PolicyProfile`](reference/class_mip_policyprofile.md): Klasa profilu dla interfejsu API zasad MIP.
- [`ProtectionProfile`](reference/class_mip_protectionprofile.md): Klasa profilu dla interfejsu API ochrony MIP.
- [`FileProfile`](reference/class_mip_fileprofile.md): Klasa profilu dla interfejsu API plików MIP.

Interfejs API używany w aplikacja odbierająca komunikaty Określa, która klasa profilu należy używać.

Sam oferuje następujące funkcje:

- Określa lokalizację magazynu dla stanu zestawu SDK. Dane stanu obejmują szczegóły użytkownika, zasady użytkownika pobrany, dzienniki i dane telemetryczne.
- Określa, czy stanu powinien być ładowane w pamięci lub utrwalony na dysku.
- Obsługuje uwierzytelnianie, akceptując `mip::AuthDelegate`.
- Ustawia identyfikator aplikacji oraz przyjazną nazwę aplikacji korzystających z zestawu SDK.

### <a name="profile-settings"></a>Ustawienia profilu

- `Path`: Ścieżka pliku, w której rejestrowanie, dane telemetryczne i inne trwały stan jest przechowywany.
- `useInMemoryStorage`: Wartość logiczna, która definiuje, czy stan powinny być przechowywane w pamięci, lub na dysku.
- `authDelegate`: Wspólny wskaźnik klasy `mip::AuthDelegate`. 
- `consentDelegate`: Wspólny wskaźnik klasy [ `mip::ConsentDelegate` ](reference/class_consentdelegate.md). 
- `observer`: Wspólny wskaźnik do tego profilu `Observer` implementacji (w [ `PolicyProfile` ](reference/class_mip_policyprofile_observer.md), [ `ProtectionProfile` ](reference/class_mip_protectionprofile_observer.md), i [ `FileProfile` ](reference/class_mip_fileprofile_observer.md)).
- `applicationInfo`: A [ `mip::ApplicationInfo` ](reference/mip-enums-and-structs.md#structures) obiektu. Informacje o aplikacji, która zużywa zestaw SDK, który pasuje do Twojego Identyfikatora rejestracji aplikacji w usłudze Azure Active Directory i nazwę.

## <a name="engines"></a>Aparaty

Aparaty pliku, profilu i ochrona interfejsu API zapewniają interfejs do operacji wykonywanych w imieniu określonej tożsamości. Jeden aparat jest dodawany do obiektu profilu dla każdego użytkownika, który loguje się do aplikacji. Wszystkie operacje wykonywane przez aparat są w kontekście tej tożsamości.

Istnieją trzy klasy aparatu w zestawie SDK, jeden dla każdego interfejsu API. Na poniższej liście przedstawiono klasy aparatu i kilka funkcji związanych z każdym:

- [`mip::ProtectionEngine`](reference/class_mip_protectionengine.md)
- [`mip::PolicyEngine`](reference/class_mip_policyengine.md)
  - `ListSensitivityLabels()`: Pobiera listę etykiet dla aparatu załadowane.
  - `GetSensitivityLabel()`: Pobiera etykietę z istniejącej zawartości.
  - `ComputeActions()`: Podany identyfikator etykiety i opcjonalne metadane, zwraca listę wszystkich akcji, które powinny być wykonywane dla określonego elementu.
- [`mip::FileEngine`](reference/class_mip_fileengine.md)
  - `ListSensitivityLabels()`: Pobiera listę etykiet dla aparatu załadowane.
  - `CreateFileHandler()`: Tworzy `mip::FileHandler` dla określonego pliku lub strumienia.

### <a name="engine-states"></a>Stany aparatu obsługi

Silnik może mieć jeden z trzech stanów:

- `CREATED`: Utworzone oznacza, że zestaw SDK ma wystarczającą ilość informacji o stanie lokalnego po wywołaniu usługi zaplecza.
- `LOADED`: Zestaw SDK opracowała struktur danych wymagane dla aparatu do użycia.

Aparat muszą być zarówno tworzone i ładowane do wykonywania jakichkolwiek operacji. `Profile` Klasa udostępnia kilka metod zarządzania aparat: `AddEngineAsync`, `RemoveEngineAsync`, i `UnloadEngineAsync`.

W poniższej tabeli opisano stany aparatu możliwości i metody, które można zmienić ten stan:

|         | BRAK              | UTWORZONE           | ZAŁADOWANO         |
|---------|-------------------|-------------------|----------------|
| BRAK    |                   |                   | AddEngineAsync |
| UTWORZONE | DeleteEngineAsync |                   | AddEngineAsync |
| ZAŁADOWANO  | DeleteEngineAsync | UnloadEngineAsync |                |

### <a name="engine-id"></a>Identyfikator aparatu

Każdy silnik ma unikatowy identyfikator, `id`, która jest używana we wszystkich operacjach zarządzania aparatu. Aplikacja może zapewniać `id`, lub zestaw SDK może wygenerowany, jeśli nie zostanie podany przez aplikację. Wszystkie pozostałe aparatu właściwości (na przykład, "adres e-mail podany w informacje o tożsamości") są nieprzezroczyste ładunków dla zestawu SDK. Zestaw SDK nie wykonać żadnej logiki przechowywać dowolne inne właściwości Unikatowy lub wymusić wszystkimi innymi ograniczeniami.

### <a name="engine-management-methods"></a>Metody zarządzania aparatu

Jak wspomniano wcześniej, istnieją trzy metody zarządzania aparatu w zestawie SDK: `AddEngineAsync`, `DeleteEngineAsync`, i `UnloadEngineAsync`.

#### <a name="addengineasync"></a>AddEngineAsync

Ta metoda ładuje aparat istniejących lub tworzy jeden, jeśli nie istnieje już w stanie lokalnym.

Jeśli aplikacja nie udostępnia `id`, `AddEngineAsync` generuje nowy `id`. Następnie sprawdza, czy aparat, który `id` istnieje już w stanie lokalnym. Jeśli tak, ładuje silnika. Jeśli aparat *nie* znajdują się w stanie lokalnym, nowy aparat jest tworzony przez wywołanie niezbędne interfejsy API i usług zaplecza.

W obu przypadkach Jeśli metoda się powiedzie, aparat jest załadowany i gotowe do użycia.

#### <a name="deleteengineasync"></a>DeleteEngineAsync

Usuwa aparat z danym `id`. Wszystkie ślady aparat są usuwane ze stanu lokalnego.

#### <a name="unloadengineasync"></a>UnloadEngineAsync

Zwalnia struktury danych w pamięci dla aparatu z danym `id`. Stan lokalnego ten aparat jest nienaruszony i można ponownie załadować z `AddEngineAsync`.

Ta metoda umożliwia aplikacja stanie się w rozsądnej dotyczące użycia pamięci przez zwalnianie silników, które nie powinny służyć wkrótce.

## <a name="next-steps"></a>Następne kroki

- Następnie Dowiedz się więcej o [pojęć dotyczących uwierzytelniania](concept-authentication-cpp.md) i [obserwatorów](concept-async-observers.md). MIP zapewnia model uwierzytelniania rozszerzonego, mimo że obserwatora są używane do udostępniania powiadomień o zdarzeniach dla asynchronicznego zdarzeń. Obie mają zasadnicze znaczenie i zastosować do wszystkich zestawów MIP API.
- Następnie pracy z koncepcjami profilu i aparat plików, zasad i interfejsów API ochrony
  - [Pojęcia dotyczące profilu interfejsu API plików](concept-profile-engine-file-profile-cpp.md)
  - [Pojęcia dotyczące aparatu interfejsu API plików](concept-profile-engine-file-engine-cpp.md)
  - [Pojęcia dotyczące profilu zasad interfejsu API](concept-profile-engine-file-profile-cpp.md)
  - [Pojęcia dotyczące aparatu zasad interfejsu API](concept-profile-engine-file-engine-cpp.md)
  - [Pojęcia dotyczące profilu interfejsu API ochrony](concept-profile-engine-file-profile-cpp.md)
  - [Ochrona interfejsu API aparatu pojęcia](concept-profile-engine-file-engine-cpp.md)  
