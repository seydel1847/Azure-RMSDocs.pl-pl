---
title: Pojęcia — obiekt aparat interfejsu API plików
description: Ten artykuł ułatwi zrozumienie pojęcia dotyczące obiektu aparatu pliku, który jest tworzony podczas inicjowania aplikacji.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5a2e8702b1ace1df2e45224b9b0d76f4c7cb8c77
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214606"
---
# <a name="file-api-engine"></a>Aparat specyfikacji File API

`mip::FileEngine` w interfejsie API plików zestawu SDK MIP udostępnia interfejs dla wszystkich operacji, które są wykonywane w imieniu określonej tożsamości. Jeden aparat zostanie dodana dla każdego użytkownika, który wykonuje loguje się do aplikacji, a wszystkie operacje, które aparatu będą wykonywane w kontekście tej tożsamości.

`FileEngine` Ma dwa główne zadania: wyświetlanie etykiet dla uwierzytelnionego użytkownika i tworzenie plików programów obsługi do wykonywania operacji na plikach w imieniu użytkownika. 

- [`mip::FileEngine`](reference/class_mip_fileengine.md)
  - `ListSensitivityLabels()`: Pobiera listę etykiet dla aparatu załadowane.
  - `CreateFileHandler()`: Tworzy `mip::FileHandler` dla określonego pliku lub strumienia.

## <a name="add-a-file-engine"></a>Dodaj aparatu plików

Zgodnie z opisem w [pojęcia — aparat]() strony, aparat może mieć dwa stany - `CREATED` lub `LOADED`. Jeśli nie jest jedną z tych dwóch stanów, nie istnieje. Aby utworzyć i załadować stanu, tylko jest konieczne tylko jedno wywołanie `FileProfile::LoadAsync`. Jeśli aparat już istnieje w pamięci podręcznej stanu, będzie on `LOADED`. Jeśli nie istnieje, będzie on `CREATED` i `LOADED`. `CREATED` oznacza, że aplikacja ma wszystkie informacje potrzebne do załadowania aparatu usługi. `LOADED` Wskazuje, czy wszystkie struktury danych, trzeba korzystać z aparatem zostały utworzone w pamięci.

### <a name="create-file-engine-settings"></a>Tworzenie pliku ustawień aparatu

Podobnie jak w profilu, aparat wymaga również obiekt ustawień `mip::FileEngine::Settings`. Ten obiekt przechowuje identyfikator unikatowy aparatu dane możliwe do dostosowania klienta, który może służyć do debugowania lub dane telemetryczne i, opcjonalnie, ustawienia regionalne.

W tym miejscu utworzymy `FileEngine::Settings` obiektu o nazwie *engineSettings*. 

```cpp
FileEngine::Settings engineSettings("UniqueID", "");
```

Najlepszym rozwiązaniem jest pierwszy parametr `id`, powinny być coś, co umożliwia aparatowi łatwo połączyć skojarzonego użytkownika. Coś, jak adres e-mail, nazwy UPN lub identyfikator GUID obiektu usługi AAD będzie upewnij się, że identyfikator jest unikatowy i może zostać załadowany ze stanu lokalnego bez wywoływania usługi.

### <a name="add-the-file-engine"></a>Dodaj z aparatem plików

Aby dodać aparat, będzie wrócimy do wzorzec promise/przyszłość służący do [załadować profilu](). Zamiast tworzenia obietnicą dla `mip::FileProfile`, jest tworzony, za pomocą `mip::FileEngine`.

```cpp
  //auto profile will be std::shared_ptr<mip::FileProfile>
  auto profile = profileFuture.get();

  //Create the FileEngine::Settings object
  FileEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::FileEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::FileEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::FileEngine>
  auto engine = engineFuture.get();
```

Wynik końcowy w powyższym kodzie jest o tym, że aparat dla tego uwierzytelnionego użytkownika zostaną dodane do profilu.

## <a name="list-sensitivity-labels"></a>Utwórz listę etykiet czułości

Przy użyciu aparatu dodano, jest teraz jest to możliwe, aby wyświetlić listę wszystkich czułość etykiety dostępne dla tego uwierzytelnionego użytkownika, wywołując `engine->ListSensitivityLabels()`.

`ListSensitivityLabels()` powoduje pobranie listy etykiet i atrybuty etykiety dla określonego użytkownika z usługi. Wynik jest przechowywany w wektorze wskaźnika `std::shared_ptr<mip::Label>`.

Dowiedz się więcej [tutaj]() na `mip::Label`.

### <a name="listsensitivitylabels"></a>ListSensitivityLabels()

```cpp
std::vector<shared_ptr<mip::Label>> labels = engine->ListSensitivityLabels();
```

Lub uproszczonej:

```cpp
auto labels = engine->ListSensitivityLabels();
```

### <a name="print-the-labels-and-ids"></a>Drukuj etykiety i identyfikatory

Drukowanie nazwy jest łatwym sposobem wskazują, że firma Microsoft pomyślnie ściągnąć zasad z usługi i udało się pobrać etykiet. Aby zastosować etykietę, wymagany jest identyfikator etykiety. Poniższy kod wykonuje iterację przez wszystkie etykiety, wyświetlanie `name` i `id` dla każdej etykiety nadrzędnymi i podrzędnymi.

```cpp
//Iterate through all labels in the vector
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

## <a name="next-steps"></a>Następne kroki

Teraz, gdy profil jest załadowany, aparat, który został dodany, i mamy etykiety, możemy dodać program obsługi, aby zacząć odczytu, zapisu lub usuń etykiety z plików.

- [Tworzenie obsługi plików]()

