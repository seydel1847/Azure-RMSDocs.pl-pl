---
title: Pojęcia — interfejs API plików obiektu profilu
description: Ten artykuł ułatwi zrozumienie pojęcia dotyczące obiektu profilu pliku, który jest tworzony podczas inicjowania aplikacji.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 33ec266068d15e827267b7d518344aebd0f8f072
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445907"
---
# <a name="microsoft-information-protection-sdk---file-api-profile-concepts"></a>Usługi Microsoft Information Protection SDK — pojęcia profilu specyfikacji File API

Profil, który jest klasą głównego dla wszystkich operacji w zestawie SDK MIP. Przed rozpoczęciem korzystania z funkcjonalności interfejsu API plików `FileProfile` musi zostać utworzona, a wszystkie przyszłe operacje zostaną wykonane w profilu lub przez inne obiekty *dodano* do profilu.

Istnieje kilka wstępne kodu, które powinny zostać spełnione przed przystąpieniem do tworzenia wystąpienia profilu:

- `AuthDelegateImpl` zaimplementowany, aby rozszerzyć `mip::AuthDelegate`.
- `ConsentDelegateImpl` zaimplementowany, aby rozszerzyć `mip::ConsentDelegate`.
- Aplikacja została [zarejestrowane w usłudze Azure Active Directory](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad.md) i klienta z Identyfikatorem ustalone w plikach aplikacji lub konfiguracji. 
- Klasa dziedziczy `mip::FileProfile::Observer` został prawidłowo zaimplementowany.

## <a name="load-a-profile"></a>Załaduj profil

Za pomocą `ProfileObserver`, `ConsentDelegateImpl`, i `AuthDelegateImpl` zdefiniowane, `mip::FileProfile` mogą być utworzone. Tworzenie `mip::FileProfile` wymaga obiektu [ `mip::FileProfile::Settings` ](reference/class_mip_fileprofile_settings.md) do przechowywania wszystkich informacji o ustawieniach dotyczące `FileProfile`.

### <a name="fileprofilesettings-parameters"></a>Parametry FileProfile::Settings

`FileProfile::Settings` Konstruktor akceptuje parametry pięć, wymienionych poniżej:

- `std::string path`: Ścieżka pliku w ramach której rejestrowanie, dane telemetryczne i inne trwały stan jest przechowywany.
- `bool useInMemoryStorage`: Określa, czy wszystkie stany powinny być przechowywane w pamięci, w przeciwieństwie do na dysku.
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: Wspólny wskaźnik klasy `mip::AuthDelegate` 
- `std::shared_ptr<mip::ConsentDelegate>`: 
- `std::shared_ptr<mip::FileProfile::Observer> observer`: Wspólny wskaźnik do `FileProfile::Observer` implementacji.
- `mip::ApplicationInfo applicationInfo`: obiekt. Służy do definiowania informacje dotyczące aplikacji, która zużywa zestawu SDK.

W poniższych przykładach pokazano sposób tworzenia `profileSettings` obiektu przy użyciu lokalnego magazynu do przechowywania stanów, a także w pamięci tylko. Zarówno przyjęto założenie, że `authDelegateImpl` obiekt został już utworzony.

#### <a name="store-state-in-memory-only"></a>Stan Store tylko w pamięci

```cpp
FileProfile::Settings profileSettings(
    "",                                          //path to store settings
    true,                                        //useInMemoryStorage
    authDelegateImpl,                            //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),     //new consent delegate
    std::make_shared<FileProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Ustawienia profilu odczytu/zapisu ze ścieżki magazynu na dysku

Następujący fragment kodu będzie poinstruować `FileProfile` do przechowywania wszystkich danych stanu aplikacji w `./mip_app_data`.

```cpp
FileProfile::Settings profileSettings(
    "./mip_app_data",                            //path to store settings
    false,                                       //useInMemoryStorage
    authDelegateImpl,                            //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),     //new consent delegate
    std::make_shared<FileProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="load-the-profile"></a>Załaduj profil

Teraz za pomocą obu podejście podanymi powyżej szczegółami dotyczącymi, użyj wzorca promise/przyszłość załadować `FileProfile`.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<FileProfile>>>();
auto profileFuture = profilePromise->get_future();
FileProfile::LoadAsync(profileSettings, profilePromise);
```

Jeśli został wczytany, profil, że operacja zakończyła się pomyślnie, `ProfileObserver::OnLoadSuccess`, naszej implementacji `mip::FileProfile::Observer::OnLoadSuccess` jest wywoływana. Wynikowy obiekt lub wskaźnik wyjątek, a także kontekście, są przekazywane w jako parametry do funkcji. Kontekst jest wskaźnikiem do `std::promise` utworzyliśmy do obsługi operacji asynchronicznej. Funkcja po prostu ustawia wartość prawdziwą obiektowi FileProfile, która została przekazana jako pierwszy parametr. Gdy używa się funkcji main `Future.get()`, wyniki mogą być przechowywane w nowym obiekcie.

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

    FileProfile::Settings profileSettings("",
            false,
            authDelegateImpl,
            std::make_shared<ConsentDelegateImpl>(),
            std::make_shared<ProfileObserver>(),
            mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

    auto profilePromise = std::make_shared<promise<shared_ptr<FileProfile>>>();
    auto profileFuture = profilePromise->get_future();
    FileProfile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

Koniec powoduje, że firma Microsoft została pomyślnie załadował profil i przechowywanych w obiekcie o nazwie `profile`.

## <a name="next-steps"></a>Następne kroki

Teraz, że profil został dodany, następnym krokiem jest dodać aparat do profilu. 

- [Pojęcia dotyczące aparatu plików](concept-profile-engine-file-engine-cpp.md)