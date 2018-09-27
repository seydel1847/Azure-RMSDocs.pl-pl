---
title: Pojęcia — programów obsługi plików w zestawie SDK MIP.
description: Ten artykuł pomoże zrozumieć, jak obsługi interfejsu API plików są używane do wywoływania operacji.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a8c284b0c875379f28a23ef1d9cd17e1cc343568
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214373"
---
# <a name="file-handlers-in-the-mip-sdk"></a>Procedury obsługi pliku w zestawie SDK MIP

W interfejsie API plików zestawu SDK MIP `mip::FileHandler` uwidacznia wszystkie różne operacje, które może służyć do odczytu i zapisu etykiety lub ochrony w zestawie typów plików, dla których obsługa jest wbudowana. 

## <a name="supported-file-types"></a>Obsługiwane typy plików

- Formaty plików pakietu Office oparte na OCP (pakiet Office 2010 lub nowszy)
- Formaty plików starszej wersji pakietu Office (Office 2007)
- PDF
- Ogólna obsługa PFILE
- Pliki, które obsługują Adobe XMP

## <a name="file-handler-functions"></a>Funkcje obsługi plików

`mip::FileHandler` udostępnia metody do odczytu, zapisu i usuwania etykiet i ochrony informacji. Aby uzyskać pełną listę, zapoznaj się [dokumentacja interfejsu API](reference/class_mip_filehandler.md).

W tym artykule zostały omówione następujących metod:

- `GetLabelAsync()`
- `SetLabel()`
- `DeleteLabel()`
- `CommitAsync()`

## <a name="requirements"></a>Wymagania

Tworzenie `FileHandler` wymaga, aby pracować z określonego pliku:

- A `FileProfile`
- A `FileEngine` dodane do `FileProfile`
- Klasa, która dziedziczy `mip::FileHandler::Observer`, podobny do wzorca opisane [tutaj]().

## <a name="create-a-file-handler"></a>Utwórz procedurę obsługi plików

Pierwszym krokiem wymaganego do zarządzania plików w interfejsu API plików jest utworzenie `FileHandler` obiektu. Ta klasa implementuje wszystkich funkcji, trzeba pobrać, ustaw, aktualizowanie i usuwanie i etykiety zatwierdzenia zmian do plików.

Tworzenie `FileHandler` jest równie proste jak wywołanie `FileEngine`firmy `CreateFileHandlerAsync` funkcję za pomocą wzorca promise/przyszłość.

`CreateFileHandlerAsync` trzy parametry: ścieżka do pliku, który należy odczytać lub zmodyfikować, `mip::FileHandler::Observer` dla powiadomień o zdarzeniach asynchronicznych i Obietnica dla `FileHandler`.

**Uwaga:** `mip::FileHandler::Observer` klasy należy zaimplementować w klasie pochodnej jako `CreateFileHandler` wymaga `Observer` obiektu. Przegląd [tutaj]() dla `Observer` szczegółowe informacje.

```cpp
auto createFileHandlerPromise = std::make_shared<std::promise<std::shared_ptr<mip::FileHandler>>>();
auto createFileHandlerFuture = createFileHandlerPromise->get_future();
fileEngine->CreateFileHandlerAsync(filePath, std::make_shared<FileHandlerObserver>(), createFileHandlerPromise);
auto handler = createFileHandlerFuture.get();
```

Po pomyślnym utworzeniu `FileHandler` obiektu, można wykonać operacji na plikach (get/set/delete/zatwierdzania).

## <a name="read-a-label"></a>Przeczytaj etykietę

### <a name="metadata-requirements"></a>Wymagania dotyczące metadanych

Istnieje kilka wymagań pomyślnie podczas odczytywania metadanych z pliku i tłumaczenia w coś, które mogą być używane w aplikacji.

- Etykieta odczytywanych nadal musi istnieć w usłudze O365. Jeśli go jest całkowicie usunięte, zestaw SDK zakończy się niepowodzeniem uzyskać informacje dotyczące tej etykiety i zwróci błąd.
- Metadane pliku musi być bez zmian. Metadane to między innymi:
  - Attribute1
  - Attribute2

### <a name="getlabelasync"></a>GetLabelAsync()

Jeśli utworzono program obsługi, aby wskazywał określonego pliku, zostanie zwrócona do wzorca promise/przyszłość do asynchronicznego odczytu etykiety. Obietnica dotyczy `mip::ContentLabel` obiekt, który zawiera wszystkie informacje na temat przydzieloną etykietę.

Po utworzeniu wystąpienia `promise` i `future` obiektów, firma Microsoft czyta etykietę, wywołując `handler->GetLabelAsync()` i zapewniając `promise` jako pojedynczy parametr. Na koniec etykiety mogą być przechowywane w `mip::ContentLabel` obiektu, że firma Microsoft otrzyma od `future`.

```cpp
auto loadPromise = std::make_shared<std::promise<std::shared_ptr<mip::ContentLabel>>>();
auto loadFuture = loadPromise->get_future();
handler->GetLabelAsync(loadPromise);
auto label = loadFuture.get();
```

Może odczytywać dane etykiet `label` obiektu i przekazywane do innych składników lub funkcji w aplikacji.

***

## <a name="set-a-label"></a>Etykiety

Ustawienie etykiety jest procesem dwóch części. Najpierw Jeśli utworzono program obsługi, który wskazuje plik w danym, etykietę można ustawić przez wywołanie metody `FileHandler->SetLabel()` przy użyciu kilku parametrów.

```cpp
handler->SetLabel(label->GetId(), mip::LabelingOptions{ mip::AssignmentMethod::PRIVILEGED, "" });
```

Pierwszy parametr jest po prostu identyfikator etykiety z `ListLabelsAsync()`. Ta wartość mogą być przechowywane w zmiennej dedykowanych lub odczytując `mip::Label->GetId()`.

W powyższym przykładzie przyjęto założenie, firma Microsoft zapisanych żądaną `mip::Label` w obiekcie o nazwie `label`.

### <a name="labeling-options"></a>Opcje etykiet

Drugi parametr musi ustawić etykiety jest `mip::LabelingOptions` obiektu, możemy utworzyć wbudowany podczas wywoływania `SetLabel()` funkcji. Można także utworzyć wcześniej.

`LabelingOptions` Określa dodatkowe informacje na temat etykiety, takie jak `AssignmentMethod` i uzasadnienie dla akcji.

- `mip::AssignmentMethod` jest po prostu moduł wyliczający, który ma trzy wartości: `STANDARD`, `PRIVILEGED`, lub `AUTO`. Przegląd [mip::AssignmentMethod]() sekcji, aby uzyskać więcej informacji.
- Uzasadnienie jest wymagane tylko wtedy, gdy zasady usługi wymagają *i* obniżenia *istniejących* czułości pliku.

```cpp
auto labelingOptions = mip::LabelingOptions();
labelingOptions.SetMethod(mip::AssignmentMethod::STANDARD);
labelingOptions.SetJustificationMessage("Because I made an educated decision based upon the contents of this file.");
```

A teraz zamiast tworzenia etykietowania wbudowane opcje, może być przekazywany w celu `SetLabel()` funkcji.

```cpp
handler->SetLabel(label->GetId(), labelingOptions);
```

Teraz masz ustawić etykiety na plik wskazywany przez program obsługi, się nadal istnieje jeszcze jeden krok Zatwierdź zmianę i zapisywanie plików na dysku lub utworzyć strumień wyjściowy.

### <a name="commit-changes"></a>Zatwierdź zmiany

Ostatnim krokiem w zatwierdzanie każdą zmianę do pliku w zestawie SDK MIP jest **zatwierdzenia** zmiany. Jest to realizowane przy użyciu `FileHandler->CommitAsync()` funkcji. 

Aby zaimplementować funkcję zobowiązania, zostanie zwrócona do promise/przyszłych tworzenia obietnicą dla `bool`. `CommitAsync()` Funkcja zwróci wartość true, jeśli operacja zakończyła się pomyślnie lub wartość false, jeśli go nie powiodła się dla jakiegokolwiek powodu. TODO: Zaktualizuj szczegółowe informacje na temat obsługi wyjątków.

Po utworzeniu `promise` i `future`, `CommitAsync()` nosi nazwę i dwa parametry podane: ścieżka pliku wyjściowego (`std::string`) i prawdziwą. Ponadto wynik uzyskany przez wprowadzenie wartości `future` obiektu.

```cpp
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();
handler->CommitAsync(outputFile, commitPromise);
auto wasCommitted = commitFuture.get();
```

**Ważne:** `FileHandler` nie będzie aktualizacji lub zastąpienie istniejących plików. To Ty dla deweloperów, aby zaimplementować **zastępowanie** pliku który jest on oznaczony. 

Etykiety w celu pisania **FileA.docx**, kopia pliku **FileB.docx**, zostanie utworzony przy użyciu etykiety zastosowane. Kod musi być przystosowana do usuwania/zmiany nazwy **FileA.docx** i Zmień nazwę **FileB.docx**.

***

## <a name="delete-a-label"></a>Usuń etykietę

```cpp
auto handler = mEngine->CreateFileHandler(filePath, std::make_shared<FileHandlerObserverImpl>());
handler->DeleteLabel(mip::AssignmentMethod::PRIVILEGED, "Label unnecessary.");
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();
handler->CommitAsync(outputFile, commitPromise);
```
