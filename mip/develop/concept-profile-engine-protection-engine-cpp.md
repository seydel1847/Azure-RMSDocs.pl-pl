---
title: Pojęcia — obiekt aparat interfejsu API ochrony
description: Ten artykuł ułatwi zrozumienie pojęcia dotyczące obiektu aparat ochrony, który jest tworzony podczas inicjowania aplikacji.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: da0c50de6a818fcd8beda0483696ba433ce22149
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453320"
---
# <a name="microsoft-information-protection-sdk---protection-api-engine-concepts"></a>Usługi Microsoft Information Protection SDK — ochrona interfejsu API aparatu pojęcia

## <a name="implementation-add-a-protection-engine"></a>Implementacja: Dodaj aparat ochrony

W interfejsie API pliku `mip::ProtectionProfile` klasy jest klasą głównego dla wszystkich operacji SDK. Już masz utworzone profilu, możemy teraz dodać aparat do profilu.

W poniższym przykładzie pokazano, przy użyciu pojedynczego aparatu dla pojedynczego użytkownika uwierzytelnionego.

### <a name="implementation-create-protection-engine-settings"></a>Implementacja: Tworzenie ustawień aparatu ochrony

Podobnie jak w profilu, aparat wymaga również obiekt ustawień `mip::ProtectionEngine::Settings`. Ten obiekt przechowuje identyfikator unikatowy aparatu dane możliwe do dostosowania klienta, który może służyć do debugowania lub dane telemetryczne i, opcjonalnie, ustawienia regionalne.

W tym miejscu utworzymy `ProtectionEngine::Settings` obiektu o nazwie *engineSettings*. 

```cpp
ProtectionEngine::Settings engineSettings("UniqueID", "");
```

**Uwaga**: Jeśli za pomocą tej metody można utworzyć obiektu ustawień ochrony, należy również ręcznie ustawić CloudEndpointBaseUrl https://api.aadrm.com

Najlepszym rozwiązaniem jest pierwszy parametr **identyfikator**, powinny być coś, co umożliwia aparatowi łatwo połączyć skojarzony użytkownik **lub** `mip::Identity` obiektu. Można zainicjować ustawienia z `mip::Identity`:

```cpp
ProtectionEngine::Settings engineSettings(mip::Identity("Bob@Contoso.com", "");
```

Mimo że zazwyczaj należy wprowadzić w zmiennej tożsamości, a nie kod twardych.

### <a name="implementation-add-the-protection-engine"></a>Implementacja: Dodaj aparat ochrony

Aby dodać aparat, będzie wrócimy do wzorca przyszłość/promise używana do ładowania profilu. Zamiast tworzyć obietnicą dla `mip::ProtectionProfile`, użyjemy `mip::ProtectionEngine`.

```cpp

  //auto profile will be std::shared_ptr<mip::ProtectionProfile>
  auto profile = profileFuture.get();

  //Create the ProtectionEngine::Settings object
  ProtectionEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::ProtectionEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::ProtectionEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::ProtectionEngine>
  auto engine = engineFuture.get();
```

Wynik końcowy powyższy kod jest, że pomyślnie dodaliśmy aparat dla tego uwierzytelnionego użytkownika w profilu.

## <a name="implementation-list-templates"></a>Implementacja: Lista szablonów

Przy użyciu aparatu dodano, jest teraz możliwe wyświetlić listę wszystkich szablonów czułości dostępne dla tego uwierzytelnionego użytkownika, wywołując `engine->GetTemplatesAsync()`. 

`GetTemplatesAsync()` powoduje pobranie listy identyfikatorów szablonów. Wynik jest przechowywany w wektorze wskaźnika `std::shared_ptr<std::string>`.

### <a name="implementation-listsensitivitytemplates"></a>Implementacja: ListSensitivityTemplates()

```cpp
auto loadPromise = std::make_shared<std::promise<shared_ptr<vector<string>>>>();
std::future<std::shared_ptr<std::vector<std::string>>> loadFuture = loadPromise->get_future();
mEngine->GetTemplatesAsync(engineObserver, loadPromise);
auto templates = loadFuture.get();
```

### <a name="implementation-print-the-template-ids"></a>Implementacja: Drukuj identyfikatorów szablonu

```cpp
//Iterate through all template IDs in the vector
for (const auto& temp : *templates) {
  cout << "Template:" << "\n\tId: " << temp << endl;
}
```

Drukowanie nazwy to prosty sposób wskazują, że firma Microsoft pomyślnie ściągnąć zasad z usługi i udało się pobrania szablonów. Aby zastosować szablon, wymagany jest identyfikator szablonu.

Mapowanie szablonów na etykiety jest możliwe tylko za pośrednictwem zasad interfejsu API, sprawdzając wynik `ComputeActions()`.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy profil jest załadowany, aparat, który został dodany, i mamy szablonów, możemy dodać program obsługi, aby zacząć odczytu, zapisu lub usuwania Szablony plików. Zobacz [koncepcje programu obsługi ochrony](concept-handler-protection-cpp.md).