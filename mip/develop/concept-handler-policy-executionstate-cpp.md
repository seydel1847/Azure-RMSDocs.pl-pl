---
title: Pojęcia — Implementowanie ExecutionState na zestaw SDK Microsoft Information Protection
description: Ten artykuł pomoże Ci zrozumieć, jak używać ExecutionState w zestawu SDK usługi Microsoft Information Protection do wykonywania akcji, a następnie podaj szczegóły dotyczące rejestrowania inspekcji.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: 71cc6f08e130fe4a97604924643d13fd341a5625
ms.sourcegitcommit: ef70dab87478084fca853f389dab2408b95d1df1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304167"
---
# <a name="implement-executionstate"></a>Implementowanie ExecutionState

Przekazywanie informacji do zestawu SDK MCI do obliczenia akcję, które powinny zostać podjęte w oparciu o bieżący stan i żądanego stanu, jest implementowany za pośrednictwem `mip::ExecutionState` klasy. Inne klasy w zestawie SDK, takich jak `ExecutionState` jest klasą abstrakcyjną i musi być implementowany przez dewelopera.

> Aby uzyskać pełny przykład `ExecutionState` wdrożenia, przejrzyj następujące przykładowe źródło:
>
> * [execution_state_impl.h](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.h)
> * [execution_state_impl.cpp](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.cpp)

## <a name="mipexecutionstate-members"></a>MIP::ExecutionState elementów członkowskich

`ExecutionState` udostępnia następujące wirtualne elementy członkowskie. Każdy z nich zapewnia części kontekstu do aparatu zasad, aby zostały zwrócone informacje, na którym akcji powinna podejmowanych przez aplikację. Ponadto te informacje mogą służyć do zapewnienia informacji o inspekcji funkcji ochrony informacji Azure Reporting.


| Element członkowski                                                                           | Zwraca                                                                                                              |
|----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| `std::string GetNewLabelId()`                                                      | Zwraca identyfikator etykiety, która ma zostać zastosowany do obiektu.                                                                    |
| `mip::ContentState GetContentState()`                                              | Zwraca mip::ContentState obiektu.                                                                         |
| `std::pair<bool, std::string> IsDowngradeJustified()`                              | Zwraca std::pair wyrażające tego, czy jest to uzasadnione starszą wersję i uzasadnienie.                                 |
| `std::string GetContentIdentifier()`                                               | Zwraca identyfikator zawartości. Powinien być identyfikatorem czytelny dla człowieka, wskazując lokalizację obiektu.   |
| `mip::ActionSource GetNewLabelActionSource()`                                      | Zwraca mip::ActionSource etykiety.                                                                          |
| `mip::AssignmentMethod GetNewLabelAssignmentMethod()`                              | Zwraca mip::AssignmentMethod etykiety                                                                        |
| `std::vector<std::pair<std::string, std::string>> GetNewLabelExtendedProperties()` | Zwraca std::vector std::pairs ciągów, które zawierają niestandardowych metadanych, które zostaną zastosowane do dokumentu. |
| `std::vector<std::pair<std::string, std::string>> GetContentMetadata()`            | Zwraca std::vector std::pairs ciąg zawierający bieżące metadane zawartości.                               |
| `std::shared_ptr<mip::ProtectionDescriptor> GetProtectionDescriptor()`           | Zwraca wskaźnik do mip::ProtectionDescriptor                                                                     |
| `mip::ContentFormat GetContentFormat()`                                            | Zwraca mip::ContentFormat                                                                                           |
| `mip::ActionType GetSupportedActions()`                                           | Zwraca mip::ActionTypes dla etykiety.                                                                              |

Każdy z nich musi zostać zastąpiona w implementacji klasy pochodzącej od `mip::ExecutionState`. W przykładowej aplikacji linki umieszczono powyżej, ten proces odbywa się przez zaimplementowanie struktury o nazwie `ExecutionStateOptions`i że przekazanie do konstruktora klasy pochodnej.

W [przykład](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.h), struktury o nazwie `ExecutionStateOptions` jest zdefiniowany jako:

```cpp
struct ExecutionStateOptions {
    std::unordered_map<std::string, std::string> metadata;
    std::string newLabelId;
    std::string contentIdentifier;
    mip::ActionSource actionSource = mip::ActionSource::MANUAL;
    mip::ContentState contentState = mip::ContentState::REST;
    mip::AssignmentMethod assignmentMethod = mip::AssignmentMethod::STANDARD;
    bool isDowngradeJustified = false;
    std::string downgradeJustification;
    std::string templateId;
    mip::ContentFormat contentFormat = mip::ContentFormat::DEFAULT;
};
```

Każda właściwość jest ustawiona przez aplikację, następnie `ExecutionStateOptions` jest przekazywana do konstruktora klasy pochodzącej od `mip::ExecutionState`. Te informacje jest używane do ustalenia działania należy podjąć. Dane dostarczone w `mip::ExecutionState` ujawni się również w usłudze Azure Information Protection Analytics.

### <a name="next-steps"></a>Następne kroki

- Dowiedz się, jak określić [obliczenia akcje w przypadku nowej lub istniejącej etykiety](concept-handler-policy-computeactions-cpp.md)zgodnie z bieżącym i żądanego stanu.
- Pobierz [zasad przykłady interfejsu API z serwisu GitHub i wypróbuj zasad interfejsu API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
