---
title: Pojęcia — obserwatorów specyfikacji File API w zestawie SDK MIP.
description: Zestaw SDK MIP została zaprojektowana jako prawie całkowicie asynchronicznego. Ten artykuł pomoże zrozumieć, jak zaimplementować i umożliwiający asynchronicity obserwatorów interfejsu API plików.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: d150e59c98300bfe20ced0b1a453a899558d1f27
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446264"
---
# <a name="microsoft-information-protection-sdk---file-api-observers"></a>Usługi Microsoft Information Protection SDK — obserwatorów specyfikacji File API

Interfejs API plików zawiera dwie klasy obserwatora. Elementy członkowskie obserwatora wirtualne i może zostać zastąpiona w celu obsługi zdarzeń wywołania zwrotne.

- [`mip::FileProfile::Observer`](reference/class_mip_fileprofile_observer.md)
- [`mip::FileHandler::Observer`](reference/class_mip_filehandler_observer.md)

Po zakończeniu operacji asynchronicznej, `OnXxx()` jest wywoływana funkcja elementu członkowskiego odpowiadający wynik. Należą do nich `OnLoadSuccess()`, `OnLoadFailure()`, i `OnAddEngineSuccess()` dla `mip::FileProfile::Observer`.

Poniższe przykłady pokazują wzorzec promise/przyszłość, jest również używany przez przykładowych zestawach SDK, która może zostać rozszerzony do zaimplementować to zachowanie żądaną wywołania zwrotnego. 

## <a name="file-profile-observer-implementation"></a>Plik implementacji obserwatora profilu

W poniższym przykładzie utworzyliśmy klasy `ProfileObserver` , jest tworzony na podstawie `mip::FileProfile::Observer`. Aby użyć wzorca przyszłość/promise używane w całym przykłady zostały zastąpione funkcje elementów członkowskich.

**Uwaga**: tylko częściowo są implementowane poniżej przykładów i nie obejmują zastąpienia `mip::FileEngine` powiązane obserwatorów.

### <a name="profileobserverh"></a>profile_observer.h

W nagłówku definiujemy `ProfileObserver`, wynikających ze `mip::FileProfile::Observer`, następnie zastąpić każdą z funkcji elementów członkowskich.

```cpp
class ProfileObserver final : public mip::FileProfile::Observer {
public:
ProfileObserver() { }
  void OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context) override;
  void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
  //TODO: Implement mip::FileEngine related observers.
};
```

### <a name="profileobservercpp"></a>profile_observer.cpp

W celu wykonania samej definiujemy akcję do wykonania dla każdej funkcji elementu członkowskiego obserwatora.

Każdy element członkowski akceptuje dwa parametry. Pierwsza to wspólny wskaźnik do klasy, którą firma Microsoft jest obsługa w funkcji. `ProfileObserver::OnLoadSuccess` jakiego oczekuje się otrzymać `mip::FileProfile`. `ProfileObserver::OnAddEngineSuccess` oczekiwać `mip::FileEngine`.

Druga jest wspólny wskaźnik do *kontekstu*. W naszej implementacji kontekstu jest odwołaniem do `std::promise`, przekazywany przez odwołanie jako `std::shared_ptr<void>`. Pierwszy wiersz w funkcji rzutuje na `std::promise`, następnie przechowywanych w obiekcie o nazwie `promise`.

Na koniec przyszłość wykonano gotowe, ustawiając `promise->set_value()` i przekazując `mip::FileProfile` obiektu.

```cpp
#include "profile_observer.h"
#include <future>

//Called when FileProfile is successfully loaded
void ProfileObserver::OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context) {
  //cast context to promise
  auto promise = 
  std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileProfile>>>(context);
  //set promise value to profile
  promise->set_value(profile);
}

//Called when FileProfile fails to load
void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileProfile>>>(context);
  promise->set_exception(error);
}

//TODO: Implement mip::FileEngine related observers.
```

Gdy firma Microsoft wystąpienia każdej klasy zestawu SDK lub użycia funkcji, która wykonuje operacje asynchroniczne, implementacja obserwatora będzie przekazywany do konstruktora ustawienia lub async sama funkcja. Podczas tworzenia wystąpienia `mip::FileProfile::Settings` obiektu, Konstruktor przyjmuje `mip::FileProfile::Observer` jako jeden z parametrów. W poniższym przykładzie pokazano nasze niestandardowe `ProfileObserver`, który jest używany w `mip::FileProfile::Settings` konstruktora.

## <a name="filehandler-observer-implementation"></a>Implementacja FileHandler obserwatora

Podobnie jak obserwatora profilu `mip::FileHandler` implementuje `mip::FileHandler::Observers` klasy do obsługi zdarzeń asynchronicznych powiadomień podczas operacji na plikach. Implementacja jest podobny do szczegóły przedstawiono powyżej. `FileHandlerObserver` częściowo jest zdefiniowana poniżej. 

### <a name="filehandlerobserverh"></a>file_handler_observer.h

```cpp
#include "mip/file/file_handler.h"

class FileHandlerObserver final : public mip::FileHandler::Observer {
public:
  void OnCreateFileHandlerSuccess(
      const std::shared_ptr<mip::FileHandler>& fileHandler,
      const std::shared_ptr<void>& context) override;

  void OnCreateFileHandlerFailure(
      const std::exception_ptr& error,
      const std::shared_ptr<void>& context) override;

  //TODO: override remaining member functions inherited from mip::FileHandler::Observer
};
```

### <a name="filehandlerobservercpp"></a>file_handler_observer.cpp

W tym przykładzie jest tylko pierwsze dwie funkcje, ale pozostałe funkcje podobny wzorzec tych i do `ProfileObserver`.

```cpp
#include "file_handler_observer.h"

void FileHandlerObserver::OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) {
    auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
    promise->set_value(fileHandler);
}

void FileHandlerObserver::OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
    auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
    promise->set_exception(error);
}

//TODO: override remaining member functions inherited from mip::FileHandler::Observer
```

