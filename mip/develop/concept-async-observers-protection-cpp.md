---
title: Pojęcia — obserwatorów ochrona interfejsu API w zestawie SDK MIP.
description: Zestaw SDK MIP została zaprojektowana jako prawie całkowicie asynchronicznego. Ten artykuł pomoże zrozumieć, jak zaimplementować i umożliwiający asynchronicity obserwatorów interfejsie API ochrony.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 8403f1bd7b123c196c4063b7f38e2b0f73b9f5aa
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446536"
---
# <a name="microsoft-information-protection-sdk---protection-api-observers"></a>Usługi Microsoft Information Protection SDK — ochrona interfejsu API obserwatorów

Interfejs API ochrony zawiera trzy klasy obserwatora. Elementy członkowskie obserwatora wirtualne i może zostać zastąpiona w celu obsługi wywołań zwrotnych dla operacji asynchronicznych.

- [Profil ochrony: `mip::ProtectionProfile::Observer`](reference/class_mip_ProtectionProfile_observer.md)
- [Aparat ochrony: `mip::ProtectionEngine::Observer`](reference/class_mip_ProtectionEngine_observer.md)
- [Program obsługi ochrony: `mip::ProtectionHandler::Observer`](reference/class_mip_Protectionhandler_observer.md)

Po zakończeniu operacji asynchronicznej, `OnXxx()` jest wywoływana funkcja elementu członkowskiego odpowiadający wynik. Należą do nich `OnLoadSuccess()`, `OnLoadFailure()`, i `OnAddEngineSuccess()` dla `mip::ProtectionProfile::Observer`.

Poniższe przykłady pokazują wzorzec promise/przyszłość, jest również używany przez przykładowych zestawach SDK, która może zostać rozszerzony do zaimplementować to zachowanie żądaną wywołania zwrotnego. 

## <a name="protection-protection-observer-implementation"></a>Implementacja obserwatora ochrony ochrony

W poniższym przykładzie utworzyliśmy klasy `ProtectionProfileObserverImpl` , jest tworzony na podstawie `mip::ProtectionProfile::Observer`. Aby użyć wzorca promise/przyszłość używane w całym przykłady zostały zastąpione funkcje elementów członkowskich.

### <a name="protectionprofileobserverimpl-class-declaration"></a>Deklaracja klasy ProtectionProfileObserverImpl

W nagłówku definiujemy `ProtectionProfileObserverImpl`, wynikających ze `mip::ProtectionProfile::Observer`, następnie zastąpić każdą z funkcji elementów członkowskich.

```cpp
//ProtectionProfileObserverImpl.h
class ProtectionProfileObserverImpl final : public mip::ProtectionProfile::Observer {
public:
  ProtectionProfileObserverImpl() { }
  void OnLoadSuccess(const shared_ptr<mip::ProtectionProfile>& profile, const shared_ptr<void>& context) override;
  void OnLoadFailure(const exception_ptr& error, const shared_ptr<void>& context) override;
  void OnAddEngineSuccess(const shared_ptr<mip::ProtectionEngine>& engine, const shared_ptr<void>& context) override;
  void OnAddEngineError(const exception_ptr& error, const shared_ptr<void>& context) override;
};
```

### <a name="protectionprofileobserverimpl-implementation"></a>Implementacja ProtectionProfileObserverImpl

W celu wykonania samej definiujemy są po prostu akcję do wykonania dla każdej funkcji elementu członkowskiego obserwatora.

Każdy element członkowski akceptuje dwa parametry. Pierwsza to wspólny wskaźnik do klasy, którą firma Microsoft jest obsługa w funkcji. `ProtectionObserver::OnLoadSuccess` jakiego oczekuje się otrzymać `mip::ProtectionProtection`, `ProtectionObserver::OnAddEngineSuccess` oczekiwać `mip::ProtectionEngine`.

Druga jest wspólny wskaźnik do *kontekstu*. W naszej implementacji kontekstu jest odwołaniem do `std::promise`, przekazana jako `shared_ptr<void>`. Pierwszy wiersz w funkcji rzutuje na `std::promise`, następnie przechowywanych w obiekcie o nazwie `promise`.

Na koniec przyszłość wykonano gotowe, ustawiając `promise->set_value()` i przekazując `mip::ProtectionProtection` obiektu.

```cpp
//protection_observers.cpp

void ProtectionProfileObserverImpl::OnLoadSuccess(
  const shared_ptr<mip::ProtectionProfile>& profile,
  const shared_ptr<void>& context) {
  auto loadPromise = static_cast<promise<shared_ptr<mip::ProtectionProfile>>*>(context.get());
  loadPromise->set_value(profile);
};

void ProtectionProfileObserverImpl::OnLoadFailure(const exception_ptr& error, const shared_ptr<void>& context) {
  auto loadPromise = static_cast<promise<shared_ptr<mip::ProtectionProfile>>*>(context.get());
  loadPromise->set_exception(error);
};

void ProtectionProfileObserverImpl::OnAddEngineSuccess(
  const shared_ptr<mip::ProtectionEngine>& engine,
  const shared_ptr<void>& context) {
  auto addEnginePromise = static_cast<promise<shared_ptr<mip::ProtectionEngine>>*>(context.get());
  addEnginePromise->set_value(engine);
};

void ProtectionProfileObserverImpl::OnAddEngineError(
  const exception_ptr& error,
  const shared_ptr<void>& context) {
  auto addEnginePromise = static_cast<promise<shared_ptr<mip::ProtectionEngine>>*>(context.get());
  addEnginePromise->set_exception(error);
};
```

Gdy firma Microsoft wystąpienia każdej klasy zestawu SDK lub użycia funkcji, która wykonuje operacje asynchroniczne, implementacja obserwatora będzie przekazywany do konstruktora ustawienia lub async sama funkcja. Podczas tworzenia wystąpienia `mip::ProtectionProfile::Settings` obiektu, Konstruktor przyjmuje `mip::ProtectionProfile::Observer` jako jeden z parametrów. W poniższym przykładzie pokazano nasze niestandardowe `ProtectionProfileObserverImpl`, który jest używany w `mip::ProtectionProfile::Settings` konstruktora.

## <a name="protectionhandler-observer-implementation"></a>Implementacja ProtectionHandler obserwatora

Podobnie jak obserwatora ochrony `mip::ProtectionHandler` implementuje `mip::ProtectionHandler::Observer` klasy do obsługi zdarzeń asynchronicznych powiadomień podczas operacji ochrony. Implementacja jest podobny do szczegóły przedstawiono powyżej. `ProtectionHandlerObserverImpl` częściowo jest zdefiniowana poniżej. Pełną implementację można znaleźć w naszej [przykładowego repozytorium GitHub](https://github.com/Azure-Samples?utf8=%E2%9C%93&q=MipSdk).

### <a name="protectionhandlerobserverimpl-class-declaration"></a>Deklaracja klasy ProtectionHandlerObserverImpl

```cpp
//protection_observers.h

class ProtectionHandlerObserverImpl final : public mip::ProtectionHandler::Observer {
public:
  ProtectionHandlerObserverImpl() { }
  void OnCreateProtectionHandlerSuccess(const shared_ptr<mip::ProtectionHandler>& protectionHandler, const shared_ptr<void>& context) override;
  void OnCreateProtectionHandlerError(const exception_ptr& error, const shared_ptr<void>& context) override;
};
```

### <a name="protectionhandlerobserverimpl-partial-implementation"></a>Implementacja ProtectionHandlerObserverImpl częściowego

W tym przykładzie jest tylko pierwsze dwie funkcje, ale pozostałe funkcje podobny wzorzec tych i do `ProtectionObserver`.

```cpp
//protection_observers.cpp

void ProtectionHandlerObserverImpl::OnCreateProtectionHandlerSuccess(
  const shared_ptr<mip::ProtectionHandler>& protectionHandler,
  const shared_ptr<void>& context) {
  auto createProtectionHandlerPromise = static_cast<promise<shared_ptr<mip::ProtectionHandler>>*>(context.get());
  createProtectionHandlerPromise->set_value(protectionHandler);
};

void ProtectionHandlerObserverImpl::OnCreateProtectionHandlerError(
  const exception_ptr& error,
  const shared_ptr<void>& context) {
  auto createProtectionHandlerPromise = static_cast<promise<shared_ptr<mip::ProtectionHandler>>*>(context.get());
  createProtectionHandlerPromise->set_exception(error);
};
```

