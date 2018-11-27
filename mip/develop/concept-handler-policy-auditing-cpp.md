---
title: Pojęcia — inspekcji w Microsoft zestawu SDK zasad usługi Information Protection interfejsu API
description: Ten artykuł pomoże Ci zrozumieć, jak przesłać API zasad inspekcji zdarzeń do usługi Azure Information Protection Analytics przy użyciu zestawu SDK usługi Microsoft Information Protection.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/07/2018
ms.author: tommos
ms.openlocfilehash: bc85a6e737c883afdc39e8730483fc2c0da720a9
ms.sourcegitcommit: ef70dab87478084fca853f389dab2408b95d1df1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304201"
---
# <a name="auditing-in-the-mip-sdk"></a>Inspekcja w zestawie SDK MIP

W portalu administratora usługi Azure Information Protection zapewnia dostęp do raportów administratora. Te raporty zapewniają wgląd w etykiety, użytkownicy mają zastosowanie, ręcznie lub automatycznie przez wszystkie aplikacje, które mają zintegrowany zestaw SDK MIP. Partnerzy programowania, korzystając z zestawu SDK można łatwo włączyć tę funkcję zezwolenie informacji z poziomu ich aplikacji, aby przedstawić w raportach klienta.

## <a name="event-types"></a>Typy zdarzeń

Istnieją trzy typy zdarzeń, które mogą zostać przesłany za pośrednictwem zestawu SDK do usługi Azure Information Protection Analytics. **Zdarzenia pulsu**, **zdarzenia odnajdywania**, i **zdarzenia zmian**

### <a name="heartbeat-events"></a>Zdarzenia pulsu

Zdarzenia pulsu są generowane automatycznie dla każdej aplikacji, która została zintegrowana z zasad interfejsu API. Zdarzenia pulsu obejmują:

* TenantId
* Godzina wygenerowania
* Nazwa główna użytkownika
* Nazwa maszyny, na którym został wygenerowany inspekcji
* Nazwa procesu
* Platforma
* Identyfikator aplikacji — odnosi się do usługi Azure AD identyfikator aplikacji.

Zdarzenia te są przydatne podczas wykrywania aplikacji w całym przedsiębiorstwie, które korzystają z zestawu SDK usługi Microsoft Information Protection.

### <a name="discovery-events"></a>Zdarzenia odnajdywania

Zdarzenia odnajdywania zawierają informacje o informacje etykietami odczytu lub używane przez interfejs API zasad. Zdarzenia te są przydatne, zgodnie z ich powierzchni urządzeń, lokalizacji i użytkowników, którzy uzyskują dostęp do informacji w organizacji.

Zdarzenia odnajdywania są generowane w interfejsie API zasad przez ustawienie flagi, tworząc `mip::PolicyHandler` obiektu. W przykładzie poniżej wartość **isAuditDiscoveryEnabled** ustawiono `true`. Gdy `mip::ExecutionState` jest przekazywany do `ComputeActions()` lub `GetSensitivityLabel()` (z istniejących metadanych informacje i zawartość identifier), informacje o odnajdywaniu zostanie przesłany do usługi Azure Information Protection Analytics.

Inspekcja odnajdywania jest generowany, gdy aplikacja wywołuje `ComputeActions()` lub `GetSensitivityLabel()` i zapewnia `mip::ExecutionState`. To zdarzenie jest generowane tylko raz na program obsługi.

Przegląd `mip::ExecutionState` pojęcia dotyczące dokumentacji szczegółowe informacje na temat stanu wykonywania.

```cpp
// Create PolicyHandler, passing in true for isAuditDiscoveryEnabled
auto handler = mEngine->CreatePolicyHandler(true);

// Returns vector of mip::Action and generates discovery event.
auto actions = handler->ComputeActions(*state);

//Or, get the label for a given state
auto label = handler->GetSensitivityLabel(*state);
```

W praktyce **isAuditDiscoveryEnabled** powinien być `true` podczas `mip::PolicyHandler` konstrukcji, aby umożliwić pliku uzyskiwanie dostępu do informacji, które będą przepływać do usługi Azure Information Protection Analytics.

## <a name="change-event"></a>Zdarzenie zmiany

Zdarzenia zmiany zawierają informacje o pliku, etykietę, która została zastosowana lub zmienione i wszelkie uzasadnienia dostarczone przez użytkownika. Zdarzenia zmiany są generowane przez wywołanie metody `NotifyCommittedActions()` na `mip::PolicyHandler`. Dochodzi do wywołania po zmiana została pomyślnie zatwierdzona do pliku, przekazując `mip::ExecutionState` użytą do obliczenia akcje.

> Jeśli aplikacja nie powiedzie się wywołać tę funkcję, system przeniesie żadnych zdarzeń w usłudze Azure Information Protection Analytics.

```cpp
handler->NotifyCommittedActions(*state);
```

## <a name="audit-dashboard"></a>Pulpit nawigacyjny inspekcji

Zdarzenia przesyłane do potoku inspekcji usługi Azure Information Protection ujawni w raportach na https://portal.azure.com. Usługa Azure Analytics ochrona informacji jest w publicznej wersji zapoznawczej i narzędzi i funkcje mogą ulec zmianie.

## <a name="next-steps"></a>Następne kroki

- Aby uzyskać szczegółowe informacje dotyczące doświadczenie inspekcji usługi Azure Information Protection, zobacz [ogłoszenie w blogu w społeczności technicznej w wersji zapoznawczej](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854).
- Pobierz [zasad przykłady interfejsu API z serwisu GitHub i wypróbuj zasad interfejsu API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)

