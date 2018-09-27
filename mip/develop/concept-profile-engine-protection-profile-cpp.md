---
title: Pojęcia — ochrona interfejsu API obiektu profilu
description: Ten artykuł ułatwi zrozumienie pojęcia dotyczące ochrony obiektu profilu, który jest tworzony podczas inicjowania aplikacji.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: c5a728ca3345be7a25bf2137965fc2586e387153
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214354"
---
# <a name="protection-api-profile"></a>Profil interfejsu API ochrony

Dwa poniższe przykłady pokazują, jak można utworzyć obiektu profileSettings przy użyciu lokalnego magazynu do przechowywania stanów, a także w pamięci tylko. Zarówno przyjęto założenie, że `authDelegateImpl` obiekt został już utworzony.

## <a name="load-a-profile"></a>Załaduj profil

Teraz, gdy [ `ProtectionProfileObserverImpl` ]() i [ `AuthDelegateImpl` ]() są zdefiniowane, użyjemy ich do utworzenia wystąpienia `mip::ProtectionProfile`. Tworzenie `mip::ProtectionProfile` wymaga obiektu [ `mip::ProtectionProfile::Settings` ](https://docs.microsoft.com/en-us/azure/information-protection/develop/mip/class_mip_ProtectionProfile_settings).

### <a name="protectionprofilesettings-parameters"></a>Parametry ProtectionProfile::Settings

- `std::string path`: Ścieżka pliku w ramach której rejestrowanie, dane telemetryczne i inne trwały stan jest przechowywany.
- `bool useInMemoryStorage`: Określa, czy wszystkie stany powinny być przechowywane w pamięci, w przeciwieństwie do na dysku.
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: Wspólny wskaźnik klasy `mip::AuthDelegate` (zobacz [sekcji uwierzytelnianie]())
- `std::shared_ptr<mip::ProtectionProfile::Observer> observer`: Wspólny wskaźnik do [ `ProtectionProfile::Observer` ]() implementacji.
- `mip::ApplicationInfo applicationInfo`: obiekt. Służy do definiowania informacje dotyczące aplikacji, która zużywa zestawu SDK.

Dwa poniższe przykłady pokazują, jak można utworzyć obiektu profileSettings przy użyciu lokalnego magazynu do przechowywania stanów, a także w pamięci tylko. Zarówno przyjęto założenie, że `authDelegateImpl` obiekt został już utworzony.

#### <a name="store-state-in-memory-only"></a>Stan Store tylko w pamięci

```cpp
ProtectionProfile::Settings profileSettings(
    "",                                     //path to store settings
    true,                                   //useInMemoryStorage
    authDelegateImpl,                       //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),//new consent delegate
    std::make_shared<ProtectionProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Ustawienia profilu odczytu/zapisu ze ścieżki magazynu na dysku

```cpp
ProtectionProfile::Settings profileSettings(
    "./mip_app_data",                       //path to store settings
    false,                                  //useInMemoryStorage
    authDelegateImpl,                       //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),//new consent delegate
    std::make_shared<ProtectionProfileObserverImpl>(), //new protection profile
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

Następnie użyj wzorca promise/przyszłość, aby załadować `ProtectionProfile`.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<ProtectionProfile>>>();
auto profileFuture = profilePromise->get_future();
ProtectionProfile::LoadAsync(profileSettings, profilePromise);
```

Jeśli został wczytany, profil, że operacja zakończyła się pomyślnie, `ProtectionProfileObserverImpl::OnLoadSuccess`, naszej implementacji `mip::ProtectionProfile::Observer::OnLoadSuccess` jest wywoływana. Wynikowy obiekt lub wskaźnik wyjątek, a także kontekście, są przekazywane w jako parametry do funkcji. Kontekst jest wskaźnikiem do `std::promise` utworzyliśmy do obsługi operacji asynchronicznej. Funkcja po prostu ustawia wartość prawdziwą obiektowi ProtectionProfile (kontekstu). Gdy używa się funkcji main `Future.get()`, wyniki mogą być przechowywane w nowym obiekcie.

```cpp
//get the future value and store in profile.
auto profile = profileFuture.get();
```

### <a name="putting-it-together"></a>Umieszczenie go razem

Po w pełni zaimplementowane obserwatorów i delegowanie uwierzytelniania, jest teraz można całkowicie załadować profil. Poniższy fragment kodu zakłada, że wszystkie niezbędne nagłówki są już uwzględniane.

```cpp
int main()
{
    const string userName = "MyTestUser@contoso.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";
    auto authDelegateImpl = make_shared<sample::auth::AuthDelegateImpl>(userName, password, clientId);

    ProtectionProfile::Settings profileSettings("",
        false,
        authDelegateImpl,
        std::make_shared<ConsentDelegateImpl>(),
        std::make_shared<ProfileObserver>(),
        mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

    auto profilePromise = std::make_shared<promise<shared_ptr<ProtectionProfile>>>();
    auto profileFuture = profilePromise->get_future();
    ProtectionProfile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

Koniec powoduje, że firma Microsoft została pomyślnie załadował profil i przechowywanych w obiekcie o nazwie `profile`.

## <a name="next-steps"></a>Następne kroki

Teraz, że profil został dodany, następnym krokiem jest dodać aparat do profilu.

[Koncepcje aparat ochrony](concept-profile-engine-protection-engine-cpp.md)