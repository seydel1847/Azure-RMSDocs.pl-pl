---
title: Pojęcia — obserwatorów zasad interfejsu API w zestawie SDK MIP.
description: Zestaw SDK MIP została zaprojektowana jako prawie całkowicie asynchronicznego. Ten artykuł pomoże zrozumieć, jak zaimplementować i umożliwiający asynchronicity obserwatorów zasad interfejsu API.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: fbdb1e7d1bf6a99228e810dca4d9532c79849d48
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214264"
---
# <a name="policy-api-observers"></a>Obserwatorzy zasad interfejsu API

Zestaw SDK interfejsu API zasad zawiera jedną klasę obserwatora. Członkowie obserwatora wirtualne i powinna zostać zastąpiona w celu obsługi wywołań zwrotnych dla operacji asynchronicznych.

- [`mip::Profile::Observer`](reference/class_mip_Profile_observer.md)

Po zakończeniu operacji asynchronicznej, `OnXxx()` jest wywoływana funkcja elementu członkowskiego odpowiadający wynik. Należą do nich `OnLoadSuccess()`, `OnLoadFailure()`, i `OnAddEngineSuccess()` dla `mip::Profile::Observer`.

Poniższe przykłady pokazują wzorzec promise/przyszłość, jest również używany przez przykładowych zestawach SDK, która może zostać rozszerzony do zaimplementować to zachowanie żądaną wywołania zwrotnego. 

## <a name="profile-observer-implementation"></a>Implementacja obserwatora profilu

W poniższym przykładzie utworzyliśmy klasy `ProfileObserver` , jest tworzony na podstawie `mip::Profile::Observer`. Aby użyć wzorca przyszłość/promise używane w całym przykłady zostały zastąpione funkcje elementów członkowskich.

**Uwaga**: tylko częściowo są implementowane poniżej przykładów i nie obejmują zastąpienia `mip::ProfileEngine` powiązane obserwatorów.

### <a name="profileobserverh"></a>profile_observer.h

W nagłówku definiujemy `ProfileObserver`, wynikających ze `mip::Profile::Observer`, następnie zastąpić każdą z funkcji elementów członkowskich.

```cpp
class ProfileObserver final : public mip::Profile::Observer {
public:
ProfileObserver() { }
  void OnLoadSuccess(const std::shared_ptr<mip::Profile>& profile, const std::shared_ptr<void>& context) override;
  void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
  //TODO: Implement remaining members
};
```

### <a name="profileobservercpp"></a>profile_observer.cpp

W celu wykonania samej definiujemy akcję do wykonania dla każdej funkcji elementu członkowskiego obserwatora.

Każdy element członkowski akceptuje dwa parametry. Pierwsza to wspólny wskaźnik do klasy obsługiwane przez funkcję. `ProfileObserver::OnLoadSuccess` jakiego oczekuje się otrzymać `mip::Profile`. `ProfileObserver::OnAddEngineSuccess` oczekiwać `mip::ProfileEngine`.

Druga jest wspólny wskaźnik do *kontekstu*. W naszej implementacji kontekstu jest odwołaniem do `std::promise`, przekazana jako `shared_ptr<void>`. Pierwszy wiersz w funkcji rzutuje na `std::promise`, następnie przechowywanych w obiekcie o nazwie `promise`.

Na koniec przyszłość wykonano gotowe, ustawiając `promise->set_value()` i przekazując `mip::Profile` obiektu.

```cpp
#include "profile_observer.h"
#include <future>

//Called when Profile is successfully loaded
void ProfileObserver::OnLoadSuccess(const std::shared_ptr<mip::Profile>& profile, const std::shared_ptr<void>& context) {
  //cast context to promise
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::Profile>>>(context);
  //set promise value to profile
  promise->set_value(profile);
}

//Called when Profile fails to load
void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::Profile>>>(context);
  promise->set_exception(error);
}

//TODO: Implement remaining observer members
```

Podczas przeprowadzania żadnych operacji asynchronicznej, implementacja obserwatora jest przekazywany do konstruktora ustawienia lub samej funkcji asynchronicznej. 

## <a name="next-steps"></a>Następne kroki

[TBD - Link, aby utworzyć `mip::Profile`, załaduj `mip::ProfileEngine`i wykonywać operacje na plikach z `mip::FileHandler`]()