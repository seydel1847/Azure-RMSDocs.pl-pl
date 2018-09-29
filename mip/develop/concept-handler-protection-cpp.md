---
title: Pojęcia — obsługi ochrony w zestawie SDK MIP.
description: Ten artykuł pomoże zrozumieć sposób obsługi interfejsu API ochrony są tworzone i używane do wywoływania operacji.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a087f1bdef5a010718c67fbdca938ecbb62e5faa
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453511"
---
# <a name="microsoft-information-protection-sdk---protection-handler-concepts"></a>Usługi Microsoft Information Protection SDK — koncepcje programu obsługi ochrony

W interfejsie API ochrony MIP SDK `mip::ProtectionHandler` udostępnia funkcje służące do szyfrowania i odszyfrowywania chronionych strumieni i bufory, przeprowadzanie kontroli dostępu, uzyskiwanie licencji publikowania i pobierania atrybutów z chronionych informacji. 

## <a name="requirements"></a>Wymagania

Tworzenie `ProtectionHandler` wymaga, aby pracować z określonego pliku:

- A `ProtectionProfile`
- A `ProtectionEngine` dodane do `ProtectionProfile`
- Klasa, która dziedziczy `mip::ProtectionHandler::Observer`, podobny do wzorca opisane [tutaj]().
- A `mip::ProtectionDescriptor` lub licencji publikowania

## <a name="create-a-protection-handler"></a>Utwórz procedurę obsługi ochrony

`mip::ProtectionHandler` obiekty są konstruowane, podając jedną `ProtectionDescriptor` lub serializowanej licencji publikowania do jednej z dwóch `ProtectionEngine` funkcji. Deskryptor ochrony musi zostać wygenerowany na potrzeby ochrony informacji zwykłego tekstu, które nie mają jeszcze licencji publikowania. **Licencję publikowania** będą używane podczas odszyfrowywania zawartości chronionej przez już lub ochrony zawartości gdzie licencji już został skonstruowany. Nie można odszyfrować zawartość chronioną bez skojarzonych licencji publikowania.

`mip::ProtectionEngine` udostępnia dwie funkcje do tworzenia `ProtectionHandler`. Parametry są takie same, z wyjątkiem programu obsługi lub licencję publikowania jako pierwszy parametr.

- `mip::ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync`
  - Wymaga `ProtectionDescriptor` jako pierwszy parametr.
- `mip::ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync`
  - Wymaga serializowaną licencją publikowania, przechowywane w `std::vector<unint8_t>` jako pierwszy parametr.

### <a name="create-from-descriptor"></a>Tworzenie na podstawie deskryptora

W przypadku ochrony zawartości, która nie zostało jeszcze chroniona lub podczas stosowania nowej ochrony do zawartości, co oznacza, że to zostało odszyfrowane, `mip::ProtectionDescriptor` muszą być zbudowane. Gdy skonstruowany, jest przekazywany do `mip::ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync()` , a wynik jest zwracany za pośrednictwem `mip::ProtectionHandler::Observer`.

```cpp
auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<ProtectionHandler>>>();
auto handlerFuture = handlerPromise->get_future();
auto observer = std::make_shared<ProtectionHandlerObserverImpl>();

//Refer to ProtectionDescriptor docs for details on creating the descriptor
auto descriptor = CreateProtectionDescriptor(); //Stub function

mEngine->CreateProtectionHandlerFromDescriptorAsync(
    descriptor,
    mip::ProtectionHandlerCreationOptions::None,
    observer,
    handlerPromise);

auto handler = handlerFuture.get();
```

Po pomyślnym utworzeniu `ProtectionHandler` obiektu, można wykonać operacji na plikach (get/set/delete/zatwierdzania).

### <a name="create-from-publishing-license"></a>Tworzenie na podstawie licencji publikowania

Założono, że licencja publikowania już odczytane z określonego źródła i przechowywane w `std::vector<uint8_t> serializedPublishingLicense`.

```cpp

//TODO: Implement GetPublishingLicense()
//Snip implies that function reads PL from source file, database, stream, etc.
std::vector<uint8_t> serializedPublishingLicense = GetPublishingLicense(filePath);

auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<ProtectionHandler>>>();
auto handlerFuture = handlerPromise->get_future();

shared_ptr<ProtectionHandlerObserverImpl> handleObserver =
    std::make_shared<ProtectionHandlerObserverImpl>();

mEngine->CreateProtectionHandlerFromPublishingLicenseAsync(
    serializedPublishingLicense,
    mip::ProtectionHandlerCreationOptions::None,
    handleObserver,
    handlerPromise);

auto handler = handlerFuture.get();
```

