---
title: Pojęcia — obiektu profilu zasad interfejsu API
description: Ten artykuł ułatwi zrozumienie pojęcia dotyczące zasad obiektu profil, który jest tworzony podczas inicjowania aplikacji.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: b229148c3028f4478f83cbbc928e19666c2f44b5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445431"
---
# <a name="microsoft-information-protection-sdk---policy-api-profile-concepts"></a>Usługi Microsoft Information Protection SDK — pojęcia profilu zasad interfejsu API

`mip::Profile` Muszą być załadowane, można było wykonać wszystkie operacje interfejsu API dla zasad.

Dwa poniższe przykłady pokazują, jak można utworzyć obiektu profileSettings przy użyciu lokalnego magazynu do przechowywania stanów, a także w pamięci tylko. Zarówno przyjęto założenie, że `authDelegateImpl` obiekt został już utworzony.

## <a name="load-a-profile"></a>Załaduj profil

Teraz, gdy `ProfileObserver` i `AuthDelegateImpl` są zdefiniowane, użyjemy ich do utworzenia wystąpienia `mip::PolicyProfile`. Tworzenie `mip::PolicyProfile` wymaga obiektu [ `mip::PolicyProfile::Settings` ](reference/class_mip_PolicyProfile_settings.md).

### <a name="profilesettings-parameters"></a>Parametry profile::Settings

- `std::string path`: Ścieżka pliku w ramach której rejestrowanie, dane telemetryczne i inne trwały stan jest przechowywany.
- `bool useInMemoryStorage`: Określa, czy wszystkie stany powinny być przechowywane w pamięci, w przeciwieństwie do na dysku.
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: Wspólny wskaźnik klasy `mip::AuthDelegate` 
- `std::shared_ptr<mip::PolicyProfile::Observer> observer`: Wspólny wskaźnik do `PolicyProfile::Observer` implementacji.
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