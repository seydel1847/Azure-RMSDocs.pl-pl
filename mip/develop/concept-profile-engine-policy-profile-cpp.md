---
title: Pojęcia — obiektu profilu zasad interfejsu API
description: Ten artykuł ułatwi zrozumienie pojęcia dotyczące zasad obiektu profil, który jest tworzony podczas inicjowania aplikacji.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 030b2edc81a20f15254aa30bd362f99a65de039c
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214666"
---
# <a name="policy-api-profile"></a>Profil zasady interfejsu API

`mip::Profile` Muszą być załadowane, można było wykonać wszystkie operacje interfejsu API dla zasad.

Dwa poniższe przykłady pokazują, jak można utworzyć obiektu profileSettings przy użyciu lokalnego magazynu do przechowywania stanów, a także w pamięci tylko. Zarówno przyjęto założenie, że `authDelegateImpl` obiekt został już utworzony.

## <a name="load-a-profile"></a>Załaduj profil

Teraz, gdy [ `ProfileObserver` ]() i [ `AuthDelegateImpl` ]() są zdefiniowane, użyjemy ich do utworzenia wystąpienia `mip::Profile`. Tworzenie `mip::Profile` wymaga obiektu [ `mip::Profile::Settings` ](https://docs.microsoft.com/en-us/azure/information-protection/develop/mip/class_mip_Profile_settings).

### <a name="profilesettings-parameters"></a>Parametry profile::Settings

- `std::string path`: Ścieżka pliku w ramach której rejestrowanie, dane telemetryczne i inne trwały stan jest przechowywany.
- `bool useInMemoryStorage`: Określa, czy wszystkie stany powinny być przechowywane w pamięci, w przeciwieństwie do na dysku.
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: Wspólny wskaźnik klasy `mip::AuthDelegate` (zobacz [sekcji uwierzytelnianie]())
- `std::shared_ptr<mip::Profile::Observer> observer`: Wspólny wskaźnik do [ `Profile::Observer` ]() implementacji.
- `mip::ApplicationInfo applicationInfo`: obiekt. Służy do definiowania informacje dotyczące aplikacji, która zużywa zestawu SDK.

Dwa poniższe przykłady pokazują, jak można utworzyć obiektu profileSettings przy użyciu lokalnego magazynu do przechowywania stanów, a także w pamięci tylko. Zarówno przyjęto założenie, że `authDelegateImpl` obiekt został już utworzony.

#### <a name="store-state-in-memory-only"></a>Stan Store tylko w pamięci

```cpp
Profile::Settings profileSettings("",
    true,
    authDelegateImpl,
    std::make_shared<ProfileObserver>(),
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Ustawienia profilu odczytu/zapisu ze ścieżki magazynu na dysku

```cpp
Profile::Settings profileSettings("./mip_app_data",
    false,
    authDelegateImpl,
    std::make_shared<ProfileObserver>(),
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });
```

Następnie użyj wzorca promise/przyszłość, aby załadować `Profile`.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<Profile>>>();
auto profileFuture = profilePromise->get_future();
Profile::LoadAsync(profileSettings, profilePromise);
```

Jeśli profil zostanie pomyślnie załadowana, `ProfileObserver::OnLoadSuccess`, naszej implementacji `mip::Profile::Observer::OnLoadSuccess` zostaje powiadomiony. Wynikowy obiekt, w tym przypadku `mip::Profile`, a także kontekście, są przekazywane w jako parametry do funkcji obserwatora.

*Kontekstu* jest wskaźnikiem do `std::promise` utworzyliśmy do obsługi operacji asynchronicznej. Funkcja po prostu ustawia wartość prawdziwą obiektu profilu, która została przekazana jako pierwszy parametr. Gdy używa się funkcji main `Future.get()`, wyniki mogą być przechowywane w nowego obiektu w wątku wywołującego.

```cpp
//get the future value and store in profile. 
auto profile = profileFuture.get();
```

### <a name="putting-it-together"></a>Umieszczenie go razem

Po w pełni zaimplementowane obserwatorów i delegowanie uwierzytelniania, jest teraz można całkowicie załadować profil. Poniższy fragment kodu zakłada, że wszystkie niezbędne nagłówki są już uwzględniane.

```cpp
int main()
{
    const string userName = "MyTestUser@consoto.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";
    auto authDelegateImpl = make_shared<sample::auth::AuthDelegateImpl>(userName, password, clientId);

    Profile::Settings profileSettings("", false, authDelegateImpl, std::make_shared<ProfileObserver>(), mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

    auto profilePromise = std::make_shared<promise<shared_ptr<Profile>>>();
    auto profileFuture = profilePromise->get_future();
    Profile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

Koniec powoduje, że firma Microsoft została pomyślnie załadował profil i przechowywanych w obiekcie o nazwie `profile`.

## <a name="next-steps"></a>Następne kroki

Teraz, że profil został dodany, następnym krokiem jest dodać aparat do profilu.

[Pojęcia dotyczące aparatu zasad](concept-profile-engine-policy-engine-cpp.md)