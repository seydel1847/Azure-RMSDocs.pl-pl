---
title: Pojęcia — obiekt aparatu zasad interfejsu API
description: Ten artykuł ułatwi zrozumienie pojęcia dotyczące obiektu aparatu zasad, który jest tworzony podczas inicjowania aplikacji.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 07e0fc59e0ed5ec1fc66fe3179fce07dfcb687d1
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445278"
---
# <a name="microsoft-information-protection-sdk---policy-api-engine-concepts"></a>Usługi Microsoft Information Protection SDK — pojęcia dotyczące aparatu zasad interfejsu API

`mip::PolicyEngine` implementuje wszystkie operacje, które mogą wykonywać zasad interfejsu API, z wyjątkiem ładowaniu profilu. 

## <a name="implementation-add-a-policy-engine"></a>Implementacja: Dodaj aparatu zasad

### <a name="implementation-create-policy-engine-settings"></a>Implementacja: Tworzenie ustawień aparatu zasad

Podobnie jak w profilu, aparat wymaga również obiekt ustawień `mip::PolicyEngine::Settings`. Ten obiekt przechowuje identyfikator unikatowy aparatu dane możliwe do dostosowania klienta, który może służyć do debugowania lub dane telemetryczne i, opcjonalnie, ustawienia regionalne.

W tym miejscu utworzymy `PolicyEngine::Settings` obiektu o nazwie *engineSettings*.

```cpp
PolicyEngine::Settings engineSettings("UniqueID", "");
```

Najlepszym rozwiązaniem jest pierwszy parametr **identyfikator**, powinny być coś, co umożliwia aparatowi łatwo połączyć skojarzony użytkownik, najlepiej główną nazwę użytkownika.

### <a name="implementation-add-the-policy-engine"></a>Implementacja: Dodaj aparatu zasad

Aby dodać aparat, będzie wrócimy do wzorca przyszłość/promise używana do ładowania profilu. Zamiast tworzyć obietnicą dla `mip::Profile`, użyjemy `mip::PolicyEngine`.

```cpp

  //auto profile will be std::shared_ptr<mip::Profile>
  auto profile = profileFuture.get();

  //Create the PolicyEngine::Settings object
  PolicyEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::PolicyEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::PolicyEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::PolicyEngine>
  auto engine = engineFuture.get();
```

Wynik końcowy powyższy kod jest, że pomyślnie dodaliśmy aparat dla tego uwierzytelnionego użytkownika w profilu.

## <a name="implementation-list-sensitivity-labels"></a>Implementacja: Lista czułości etykiety

Przy użyciu aparatu dodano, jest teraz jest to możliwe, aby wyświetlić listę wszystkich czułość etykiety dostępne dla tego uwierzytelnionego użytkownika, wywołując `engine->ListSensitivityLabels()`.

`ListSensitivityLabels()` powoduje pobranie listy etykiet i atrybuty etykiety dla określonego użytkownika z usługi. Wynik jest przechowywany w wektorze wskaźnika `std::shared_ptr<mip::Label>`.

### <a name="implementation-listsensitivitylabels"></a>Implementacja: ListSensitivityLabels()

```cpp
std::vector<shared_ptr<mip::Label>> labels = engine->ListSensitivityLabels();
```

### <a name="implementation-print-the-labels"></a>Implementacja: Wydrukować etykiety

```cpp
//Iterate through all labels in the vector
for (const auto& label : labels) {
  //print the label name
  cout << label->GetName() << endl;
  //Iterate through all child labels
  for (const auto& child : label->GetChildren()) {
    //Print the label with some formatting
    cout << "->  " << child->GetName() << endl;
  }
}
```

Drukowanie nazwy jest łatwym sposobem wskazują, że firma Microsoft pomyślnie ściągnąć zasad z usługi i udało się pobrać etykiet. Aby zastosować etykietę, wymagany jest identyfikator etykiety. Wyniki modyfikowania wycinek powyżej, aby zwrócić identyfikator etykiety:

```cpp
for (const auto& label : labels) {
  //Print label name and GUID
  cout << label->GetName() << " : " << label->GetId() << endl;

  //Print child label name and GUID
  for (const auto& child : label->GetChildren()) {    
    cout << "->  " << child->GetName() <<  " : " << child->GetId() << endl;
  }
}
```

Kolekcja `mip::Label` zwrócone przez `GetSensitivityLabels()` może służyć do wyświetlania wszystkich etykiet dostępnych dla użytkownika, a następnie, po wybraniu Użyj identyfikator w celu zastosowanie etykiety do pliku.

