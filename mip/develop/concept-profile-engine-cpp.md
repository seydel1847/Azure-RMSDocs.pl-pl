---
title: Pojęcia — podstawowe pojęcia dotyczące zestawu SDK MIP — profil i aparatu
description: Ten artykuł pomoże zrozumieć podstawowe pojęcia dotyczące zestawu SDK, o nazwie profilu i silnika, które są tworzone podczas inicjowania aplikacji.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 9477e38a837736c39a9b7d772db3ef0f3d72f1d2
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214396"
---
# <a name="profile-and-engine-objects"></a>Profil i aparat obiektów

## <a name="profiles"></a>Profile

Profil, który jest klasą głównego dla wszystkich operacji w zestawie SDK MIP. Przed rozpoczęciem korzystania z żadnego z trzech interfejsów API, profil musi zostać utworzona przez aplikację klienta. Wszystkie przyszłe operacje będą wykonywane w profilu lub przez inne obiekty *dodano* do profilu.

Istnieją trzy typy profilu w zestawie SDK Mipmapy:

- [`Profile`](https://docs.microsoft.com/en-us/azure/information-protection/develop/mip/class_mip_profile)Klasa profilu dla interfejsu API zasad MIP.
- [`ProtectionProfile`](https://docs.microsoft.com/en-us/azure/information-protection/develop/mip/class_mip_protectionprofile)Klasa profilu dla interfejsu API ochrony MIP.
- [`FileProfile`](https://docs.microsoft.com/en-us/azure/information-protection/develop/mip/class_mip_fileprofile): Profil klasy dla interfejsu API plików MIP.

Interfejsu API użyta w aplikacja odbierająca komunikaty będzie określić, która klasa profil powinien być używany.

Sam oferuje następujące funkcje:

- Określa lokalizację magazynu dla stanu zestawu SDK. Dane stanu obejmują szczegóły użytkownika, zasady użytkownika pobrany, dzienniki i dane telemetryczne.
- Określa, czy stanu powinien być ładowane w pamięci lub utrwalony na dysku.
- Obsługuje uwierzytelnianie, akceptując `mip::AuthDelegate`.
- Ustawia identyfikator aplikacji oraz przyjazną nazwę aplikacji korzystających z zestawu SDK.

### <a name="profile-settings"></a>Ustawienia profilu

- `Path`: Ścieżka pliku w ramach której rejestrowanie, dane telemetryczne i inne trwały stan jest przechowywany.
- `useInMemoryStorage`Wartość logiczna, która definiuje, czy stan powinny być przechowywane w pamięci, lub na dysku.
- `authDelegate`: Wspólny wskaźnik klasy `mip::AuthDelegate`. ([TBD — pojęcia dotyczące uwierzytelniania]())
- `consentDelegate`: Wspólny wskaźnik klasy `mip::ConsentDelegate`. ([TBD — pojęcia dotyczące uwierzytelniania]())
- `observer`: Wspólny wskaźnik do [ `Profile::Observer` ]() implementacji.
- `applicationInfo`: Element `mip::ApplicationInfo` obiektu. Informacje o aplikacji, która jest korzystanie z zestawu SDK.

## <a name="engines"></a>Aparaty

W pliku, profilu i interfejsów API ochrony aparaty zapewniają interfejs do operacji wykonywanych w imieniu określonej tożsamości. Jeden aparat zostaną dodane do obiektu profilu dla każdego użytkownika, który loguje się do aplikacji. Wszystkie operacje wykonywane przez aparat będzie w kontekście tej tożsamości.

Istnieją trzy klasy aparatu w zestawie SDK, jeden dla każdego interfejsu API. Na poniższej liście przedstawiono klasy aparatu i kilka funkcji związanych z każdym:

- [`mip::ProtectionEngine`]
  - (TBD) — szczegółowe informacje w tym miejscu.
- [`mip::PolicyEngine`](https://docs.microsoft.com/en-us/azure/information-protection/develop/mip/class_mip_policyengine)
  - `ListSensitivityLabels()`: Pobiera listę etykiet dla aparatu załadowane.
  - `GetSensitivityLabel()`: Pobiera etykietę z istniejącej zawartości.
  - `ComputeActions()`: Podany identyfikator etykiety i opcjonalne metadane, zwraca listę wszystkich akcji, które powinny być wykonywane dla określonego elementu.
- [`mip::FileEngine`](https://docs.microsoft.com/en-us/azure/information-protection/develop/mip/class_mip_fileengine)
  - `ListSensitivityLabels()`: Pobiera listę etykiet dla aparatu załadowane.
  - `CreateFileHandler()`: Tworzy `mip::FileHandler` dla określonego pliku lub strumienia.

### <a name="engine-states"></a>Stany aparatu obsługi

Silnik może mieć jeden z trzech stanów:

- `CREATED`: Utworzone oznacza, że zestaw SDK ma wystarczającą ilość informacji o stanie lokalnego po wywołaniu usługi zaplecza.
- `LOADED`: Zestaw SDK opracowała struktur danych wymagane dla aparatu do użycia.

Aparat muszą być zarówno tworzone i ładowane do wykonywania jakichkolwiek operacji. `Profile` Klasa udostępnia kilka metod zarządzania aparat: `AddEngineAsync`, `RemoveEngineAsync`, i `UnloadEngineAsync`.

W poniższej tabeli opisano stany aparatu możliwości i metody mogą zmian tego stanu.

|         | BRAK              | UTWORZONE           | ZAŁADOWANO         |
|---------|-------------------|-------------------|----------------|
| BRAK    |                   |                   | AddEngineAsync |
| UTWORZONE | DeleteEngineAsync |                   | AddEngineAsync |
| ZAŁADOWANO  | DeleteEngineAsync | UnloadEngineAsync |                |

### <a name="engine-id"></a>Identyfikator aparatu

Każdy silnik ma unikatowy identyfikator, `id`, która jest używana we wszystkich operacjach zarządzania aparatu. Aplikacja może zapewniać `id` lub zestawu SDK zostanie wygenerowany nowy unikatowy identyfikator, jeśli nie jest dostarczony przez aplikację. Wszystkie pozostałe aparatu właściwości (na przykład, "adres e-mail podany w informacje o tożsamości") są nieprzezroczyste ładunków dla zestawu SDK. Zestaw SDK nie wykonać żadnej logiki przechowywać dowolne inne właściwości Unikatowy lub wymusić wszystkimi innymi ograniczeniami.

### <a name="engine-management-methods"></a>Metody zarządzania aparatu

Jak wspomniano powyżej, istnieją trzy metody zarządzania aparatu w zestawie SDK: `AddEngineAsync`, `DeleteEngineAsync`, i `UnloadEngineAsync`.

#### <a name="addengineasync"></a>AddEngineAsync

Ta metoda ładuje aparat istniejących lub tworzy nowy, jeśli nie istnieje już w stanie lokalnym.

Jeśli aplikacja nie udostępnia `id`, `AddEngineAsync` generuje nowy `id`. Następnie sprawdza, czy aparat, który `id` istnieje już w stanie lokalnym. Jeśli tak, ładuje silnika. Jeśli aparat *nie* znajdują się w stanie lokalnym, nowy aparat jest tworzony przez wywołanie niezbędne interfejsy API i usług zaplecza.

W obu przypadkach Jeśli metoda się powiedzie, aparat jest załadowany i gotowe do użycia.

#### <a name="deleteengineasync"></a>DeleteEngineAsync

Usuwa aparat z danym `id`. Wszystkie ślady aparat są usuwane ze stanu lokalnego.

#### <a name="unloadengineasync"></a>UnloadEngineAsync

Zwalnia struktury danych w pamięci dla aparatu z danym `id`. Stan lokalnego ten aparat jest nienaruszony i można ponownie załadować z `AddEngineAsync`.

Ta metoda umożliwia rozsądne dotyczące użycia pamięci przez zwalnianie silników, które nie powinny być używane tylko aplikacji.

## <a name="next-steps"></a>Następne kroki

Następnie przeczytaj [obserwatorów](concept-async-observers.md), i jak są używane do udostępniania powiadomień o zdarzeniach dla asynchronicznego zdarzeń.
