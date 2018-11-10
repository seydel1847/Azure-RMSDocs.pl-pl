---
title: Pojęcia — generowanie zdarzeń inspekcji przy użyciu zestawu SDK usługi Microsoft Information Protection
description: Ten artykuł pomoże Ci zrozumieć, jak używać zestawu SDK usługi Microsoft Information Protection do obliczenia.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: 2bb757746e6a730442ff487492af8676cf7bdcd1
ms.sourcegitcommit: 05fdaf43f74013eecb5886b95b09dd5e00670753
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297912"
---
# <a name="compute-an-action"></a>Obliczenia akcję

Zgodnie z wcześniej opisem podstawowych funkcji interfejsu API zasad są:
- Lista dostępnych etykiet
- Zwraca określony zbiór akcji, które należy podjąć w oparciu o bieżące i żądany stan

Ostatnim krokiem w procesie jest zapewnienie identyfikator etykiety i, opcjonalnie, metadane dotyczące istniejącą etykietę do `ComputeActions()` funkcji.

Przykładowy kod w tym artykule znajdują się w witrynie GitHub.

* [mipsdk — policyapi-cpp — przykładowe podstawowe](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic)

## <a name="compute-an-action-for-a-new-label"></a>Obliczenia akcję dla nowej etykiety

Przetwarzanie `mip::Actions` dla nowej etykiety, można osiągnąć za pomocą `ExecutionStateImpl` zdefiniowane w [ExecutionState](concept-auditing-policy-executionstate-cpp.md).

```cpp
// Replace with valid label ID.
string newLabelId = "d7b93a40-4df3-47e4-b2fd-7862fc6b095c"; 
sample::policy::ExecutionStateOptions options;

// Set desired newLabelId in ExecutionStateOptions.
options.newLabelId = newLabelId;

// Initialize ExecutionStateImpl with options, create handler, call ComputeActions.
std::unique_ptr<ExecutionStateImpl> state(new ExecutionStateImpl(options));
auto handler = mEngine->CreatePolicyHandler(false); // Don't generate audit event.
auto actions = handler->ComputeActions(*state);
```

Zapisywanie po prostu z `mip::MetadataActions` zwracane jako część `actions` Wyświetla:

```cpp
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled : true
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate : 2018-10-23T20:39:06-0800
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method : Standard
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name : Contoso FTEs (C)
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId : 94f6984e-8d31-4794-bdeb-3ac89ad2b660
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId : 2266fbe8-a0d9-44e8-bad8-00008f2a0915
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits : 3
```

`PolicyHandler` Akcje oblicza i zwraca `std::vector` z `mip::Action`. To Ty Deweloper aplikacji, aby zastosować te metadane do pliku lub danych.

> [!NOTE]
> W powyższym przykładzie wyświetla tylko `mip::MetadataAction` danych wyjściowych. Na przykład wyświetlanie typów dodatkowych akcji przejrzyj przykładowe pakiety za pomocą [pobierania zasad interfejsu API](https://aka.ms/mipsdkbins).

## <a name="compute-actions-with-an-existing-label"></a>Obliczenia akcji przy użyciu istniejącej etykiety

Korzystając z interfejsu API zasad, jest do aplikacji na odczytywanie metadanych z zawartości. Te metadane znajduje się w interfejsie API w ramach `mip::ExecutionState`. `ComputeActions()` może obsługiwać bardziej złożonych operacji niż stosowanie nową etykietę do dokumentu bez etykiety. W poniższym przykładzie pokazano obniżenie etykiety z etykiety w przypadku bardziej poufnych mniej wrażliwych etykietę, gdzie etykieta już istnieje. Ten proces jest symulowane przez odczytywanie w ciąg rozdzielony przecinkami, metadanych i określanie dla interfejsu API za pośrednictwem `mip::ExecutionState`.

> [!NOTE]
> W przykładzie użyto funkcji narzędzia o nazwie `SplitString()`. Przykład można znaleźć [tutaj](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/utils.cpp)

```cpp
// Replace with valid label ID.
string newLabelId = "d7b93a40-4df3-47e4-b2fd-7862fc6b095c";

// Comma and Pipe Delimited Metadata.
string metadata = "MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled|true,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate|2018-10-23T21:53:31-0800,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method|Standard,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name|Contoso FTEs (C),MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId|94f6984e-8d31-4794-bdeb-3ac89ad2b660,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId|b56491d9-155f-40ff-866f-0000acd85c31,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits|7";

// Create ExecutionStateOptions and set newLabelId.
sample::policy::ExecutionStateOptions options;
options.newLabelId = newLabelId;

// Split metadata string by commas, store in vector.
vector<string> metadataPairs = sample::utils::SplitString(metadata, ','); 

// Iterate through each string, splitting by the pipe.
// Add each key/value pair to ExecutionStateOptions metadata.
for (const string& metadataPair : metadataPairs) {
    vector<string> keyValue = sample::utils::SplitString(metadataPair, '|');
    options.metadata[keyValue[0]] = keyValue[1];
}

// Initialize ExecutionStateImpl with options, create handler, call ComputeActions
std::unique_ptr<ExecutionStateImpl> state(new ExecutionStateImpl(options));
auto handler = mEngine->CreatePolicyHandler(false); // Don't generate audit event.
auto actions = handler->ComputeActions(*state);
```

W powyższym przykładzie może spowodować kilka akcji. Te akcje zależą od etykiety, podana jako dane wejściowe i konfigurację etykiety. Jako minimum, wynik będzie pojedynczy `mip::MetadataAction` zawierający dane, aby usunąć, za pośrednictwem `GetMetadataToRemove()` i dane, które można dodać za pomocą `GetMetadataToAdd()`.

```
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Enabled : true
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_SetDate : 2018-10-23T23:59:41-0800
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Method : Standard
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Name : General
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_SiteId : 94f6984e-8d31-4794-bdeb-3ac89ad2b660
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_ActionId : 447a996b-28ea-482c-b0b5-000075bd4bb3
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_ContentBits : 7
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId
```

## <a name="next-steps"></a>Następne kroki

* Następnie należy pobrać [zasad przykłady interfejsu API z serwisu GitHub i wypróbuj zasad interfejsu API](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
* Uzyskać informacje dotyczące sposobu [przekazywania zdarzeń inspekcji do potoku inspekcji usługi Azure Information Protection](concept-auditing-policy-cpp.md)