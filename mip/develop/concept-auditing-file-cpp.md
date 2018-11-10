---
title: Pojęcia — inspekcji w pliku interfejsu API zestawu SDK ochrony informacji firmy Microsoft
description: Ten artykuł pomoże Ci zrozumieć, jak przesłać interfejsu API plików inspekcji zdarzeń do usługi Azure Information Protection Analytics przy użyciu zestawu SDK usługi Microsoft Information Protection.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: bd04d9aa2edd6be01ae9e912d7ddbf936d6dd4df
ms.sourcegitcommit: 05fdaf43f74013eecb5886b95b09dd5e00670753
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297904"
---
# <a name="auditing-in-the-mip-sdk-file-api"></a>Przeprowadzanie inspekcji w pliku MIP SDK interfejsu API

W portalu administratora usługi Azure Information Protection zapewnia dostęp do raportów administratora. Te raporty zapewniają wgląd w użytkowników, którzy etykiety są stosowane, ręcznie lub automatycznie przez wszystkie aplikacje, wszystkie usługi, które mają zintegrowany zestaw SDK MIP. Partnerzy programowania przy użyciu zestawu SDK można łatwo włączyć tę funkcję, tak, aby ujawni informacje z poziomu ich aplikacji w raportach klienta.

## <a name="event-types"></a>Typy zdarzeń

Istnieją trzy typy zdarzeń, które mogą zostać przesłany za pośrednictwem zestawu SDK do usługi Azure Information Protection Analytics. **Zdarzenia pulsu**, **zdarzenia odnajdywania**, i **zdarzenia zmian**

### <a name="heartbeat-events"></a>Zdarzenia pulsu

Zdarzenia pulsu są generowane automatycznie dla każdej aplikacji, która została zintegrowana z interfejsu API plików. Zdarzenia pulsu obejmują:

* TenantId
* Godzina wygenerowania
* Nazwa główna użytkownika
* Nazwa maszyny, na którym został wygenerowany inspekcji
* Nazwa procesu
* Platforma
* Identyfikator aplikacji — odnosi się do usługi Azure AD identyfikator aplikacji.

Zdarzenia te są przydatne podczas wykrywania aplikacji w całym przedsiębiorstwie, które korzystają z zestawu SDK usługi Microsoft Information Protection.

### <a name="discovery-events"></a>Zdarzenia odnajdywania

Zdarzenia odnajdywania zawierają informacje o informacje etykietami odczytu lub używane przez interfejs API plików. Zdarzenia te są przydatne, zgodnie z ich powierzchni urządzeń, lokalizacji i użytkowników, którzy uzyskują dostęp do informacji w organizacji.

Zdarzenia te są przesyłane do usługi Azure Information Protection Analytics, ustawiając `AuditDiscoveryEnabled` parametru na wartość true, podczas tworzenia nowego `mip::FileHandler`. Ponadto znajduje się identyfikator zawartości, który identyfikuje plik niektóre format czytelny dla człowieka. Zaleca się użycie ścieżki pliku dla tego identyfikatora.

Poniższy przykład tworzy nowy `mip::FileHandler` z włączoną funkcję inspekcji odnajdowania. `CreateFileHandler()` Wywoływana jest metoda `mip::FileEngine` i `AuditDiscoveryEnabled` ma wartość true. Raz `FileHanlder` odczytuje etykietę, inspekcji odnajdywania zostanie wygenerowany.

```cpp
// Create FileHandler with discovery enabled
auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
auto handlerFuture = handlerPromise->get_future();
fileEngine->CreateFileHandlerAsync(filePath, contentId, mip::ContentState::REST, true /*AuditDiscoveryEnabled*/, make_shared<FileHandlerObserver>(), createFileHandlerPromise);
auto handler = handlerFuture.get();

// Read label. This generates the discovery audit.
auto label = handler->GetLabel();
```

### <a name="change-events"></a>Zdarzenia zmian

Zdarzenia zmiany zawierają informacje o pliku, etykietę, która została zastosowana lub zmienione i wszelkie uzasadnienia dostarczone przez użytkownika. Zdarzenia zmiany są generowane przez wywołanie metody `NotifyCommitSuccessful()` na `mip::FileHandler`po zmianie została pomyślnie zatwierdzona do pliku.

```cpp
// Create labeling options, set label
string contentId = "C:\users\myuser\Documents\MyPlan.docx";
mip::LabelingOptions labelingOptions(mip::AssignmentMethod::PRIVILEGED, mip::ActionSource::MANUAL);
handler->SetLabel(labelId, labelingOptions);
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();

// CommitAsync() returns a bool. If the change was successful, call NotifyCommitSuccessful().
fileHandler->CommitAsync(outputFile, commitPromise);
if(commitFuture.get()) {

    // Submit audit event.
    handler->NotifyCommitSuccessful(contentId);
}
```

## <a name="audit-dashboard"></a>Pulpit nawigacyjny inspekcji

Zdarzenia przesyłane do potoku inspekcji usługi Azure Information Protection ujawni w raportach na https://portal.azure.com. Usługa Azure Analytics ochrona informacji jest w publicznej wersji zapoznawczej i narzędzi i funkcje mogą ulec zmianie.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać szczegółowe informacje na temat doświadczenie inspekcji usługi Azure Information Protection, Przyjrzyj się [ogłoszenie w blogu w społeczności technicznej w wersji zapoznawczej](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854).
