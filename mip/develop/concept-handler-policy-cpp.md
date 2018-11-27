---
title: Pojęcia — zasady obsługi w zestawie SDK MIP.
description: Ten artykuł pomoże zrozumieć, jak tworzone i używane do wywoływania operacji obsługi zasad interfejsu API.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: tommos
ms.openlocfilehash: 02198f7762e2952f946757d14c13a41b22d73c7a
ms.sourcegitcommit: ef70dab87478084fca853f389dab2408b95d1df1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52303995"
---
# <a name="microsoft-information-protection-sdk---policy-handler-concepts"></a>Zestaw SDK — pojęcia dotyczące obsługi zasad usługi Microsoft Information Protection

W interfejsie API zasad `mip::PolicyHandler` udostępnia operacje używane do obliczeń akcje dotyczące zasad i przesyłanie zdarzeń inspekcji.

## <a name="policy-handler-functions"></a>Funkcje obsługi zasad

`mip::PolicyHandler` udostępnia metody do odczytu, zapisu i usuwania etykiet i ochrony informacji. Aby uzyskać pełną listę, zapoznaj się [dokumentacja interfejsu API](reference/class_mip_PolicyHandler.md).

W tym artykule zostały omówione następujących metod:

- `ComputeActions`
- `NotifyCommittedActions`

## <a name="requirements"></a>Wymagania

Tworzenie `PolicyHandler` wymaga:

- A `PolicyProfile`
- A `PolicyEngine` dodane do `PolicyProfile`
- Klasa, która dziedziczy `mip::PolicyHandler::Observer`

## <a name="create-a-policy-handler"></a>Utwórz procedurę obsługi zasad

Pierwszym krokiem wymagane w uzyskaniu akcje zasad jest utworzenie `PolicyHandler` obiektu. Ta klasa implementuje funkcje wymagane, aby uzyskać listę akcji, które należy wykonać określonej etykiety. Implementuje także funkcję, aby wyzwolić zdarzenie inspekcji.

Tworzenie `PolicyHandler` jest równie proste jak wywołanie `PolicyEngine`firmy `CreatePolicyHandlerAsync` funkcję za pomocą wzorca promise/przyszłość.

`CreatePolicyHandlerAsync` przyjmuje jeden parametr: **isAuditDiscoveryEnabled**. Ustaw tę wartość na **true** Jeśli aplikacja powinna powierzchni zdarzenia pulsu w rejestrowanie inspekcji.

> [!NOTE]
> `mip::PolicyHandler::Observer` Klasy należy zaimplementować w klasie pochodnej jako `CreatePolicyHandler` wymaga `Observer` obiektu. 

```cpp
auto createPolicyHandlerPromise = std::make_shared<std::promise<std::shared_ptr<mip::PolicyHandler>>>();
auto createPolicyHandlerFuture = createPolicyHandlerPromise->get_future();
PolicyEngine->CreatePolicyHandlerAsync(true);
auto handler = createPolicyHandlerFuture.get();
```

Po pomyślnym utworzeniu `PolicyHandler` obiektu, działania mogą być obliczone i inspekcja przesyłane zdarzeń.

## <a name="next-steps"></a>Następne kroki

Teraz, kiedy znasz już o tworzeniu zasad obsługi:

- Dowiedz się, jak [utworzyć klasę stanu wykonywania](concept-handler-policy-executionstate-cpp.md), używanej do określania operacje obliczeniowe.
- Pobierz [zasad przykłady interfejsu API z serwisu GitHub i wypróbuj zasad interfejsu API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
