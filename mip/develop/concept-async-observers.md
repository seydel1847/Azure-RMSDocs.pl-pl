---
title: Pojęcia — obserwatorów w zestawie SDK MIP.
description: Zestaw SDK MIP została zaprojektowana jako prawie całkowicie asynchronicznego. Ten artykuł pomoże zrozumieć, jak zaimplementować i umożliwiający asynchronicity obserwatorów.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e8014e24917bfcae4d7974881007ec0c4e95fc19
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214324"
---
# <a name="observers-in-the-mip-sdk"></a>Obserwatorzy w zestawie SDK MIP

Zestaw SDK MIP została zaprojektowana jako prawie całkowicie asynchronicznego. Na przykład każdej operacji skutkuje we/wy sieci lub plik jest wykonywana asynchronicznie. Aby obsługiwać powiadomienia o zdarzeniach dla tych zdarzeń asynchronicznych, zestaw SDK sprawia, że użycie [wzorzec obserwatora](https://wikipedia.org/wiki/Observer_pattern). 

## <a name="implementation-overview"></a>Przegląd wdrożenia

Podczas tworzenia obiektu, który będzie wykonywać operację asynchroniczną `Observer` klasy należy zaimplementować. Obserwatorzy odbierać zdarzenia powiadomień związanych z różnych operacji asynchronicznych w zestawie SDK MIP i uzyskać wynik do obiektu wywołującego.

Funkcje w każdym `Observer` klasy wirtualne i są zastępowane dla preferowanego wzorca asynchronicznego. Zestaw SDK implementuje wzorzec obserwatora zdarzeń powiadomienia, za pośrednictwem `std::promise` i `std::future`.

Każdego obserwatora swoiste dla klas zawiera zestaw funkcji sukcesów i niepowodzeń/błąd, wynik operacji asynchronicznej. *Powodzenie* funkcje zwracają obiekt skojarzony z operacją. *Błąd*/*błąd* funkcje zwracają wyjątku, który zawiera szczegółowe informacje na temat przyczyny operacja nie powiodła się.

Na przykład `FileProfile` obsługuje następujące dwie operacje: 

- Nowy aparat go dodać do profilu za pomocą `FileProfile::AddEngineAsync`. 
- Jej zwolnienie aparat z profilu za pomocą `FileProfile::UnloadEngineAsync`.

Od dwóch `Observer` funkcje są implementowane na operację asynchroniczną, można założyć, że istnieją **cztery** `Observer` metody związane z `FileProfile`: 

- `FileProfileObserver::OnAddEngineSuccess()`
- `FileProfileObserver::OnAddEngineError()`
- `FileProfileObserver::OnUnloadEngineSuccess`
- `FileProfileObserver::OnUnloadEngineError()`. 

## <a name="mip-sdk-observer-classes"></a>Zestaw SDK MIP obserwatora klas

Interfejs API plików zestawu SDK MIP zawiera dwa obserwatorów:

* `mip::FileProfile::Observer`
* `mip::FileHandler::Observer`

Interfejs API zasad dla zestawu SDK MIP ma tylko jednego obserwatora:

* `mip::Profile::Observer`

Interfejs API ochrony dla zestawu SDK MIP ma trzy obserwatorów:

* `mip::ProtectionProfile::Observer`
* `mip::ProtectionEngine::Observer`
* `mip::ProtectionHandler::Observer`

## <a name="next-steps-tbd"></a>Następne kroki (TBD)

Dowiedz się więcej na temat sposobu zaimplementowane i używane przez różne interfejsy API obserwatorów:

* [Obserwatorzy specyfikacji File API (C++)](concept-async-observers-file-cpp.md)
* [Obserwatorzy zasad interfejsu API (C++)](concept-async-observers-policy-cpp.md)
* [Ochrona interfejsu API obserwatorzy (C++)](concept-async-observers-protection-cpp.md)
