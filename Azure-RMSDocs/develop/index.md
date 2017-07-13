---
title: "Przewodnik dewelopera usług RMS | Azure RMS"
description: "Obecnie dostępne są trzy generacje zestawu Rights Management SDK."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0510ead4-2fe7-4269-885b-fe16bcc69888
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 899c05d233ec31db27cee058982c98d8dd809c3a
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Przewodnik dewelopera usług RMS
<a id="rms-developers-guide" class="xliff"></a>

## Przegląd
<a id="overview" class="xliff"></a> ##
Obecnie dostępne są trzy generacje zestawu Rights Management SDK: **zestaw Microsoft Rights Management SDK 4.2** dla systemu Android, iOS/OS X, urządzeń z systemem Windows i systemu Linux, **zestaw Microsoft Rights Management SDK 2.1** dla komputerów klienckich z systemem Windows oraz zastąpiony **zestaw AD RMS SDK**.

## Zestawy Software Development Kit
<a id="software-development-kits" class="xliff"></a> ##
| SDK | Opis |
|------|---------|
| [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Uproszczony zestaw narzędzi nowej generacji, zapewniający lekkie środowisko programistyczne dostarczające aplikacjom dla urządzeń z systemami Android, iOS, Mac OS X, Windows Phone/RT i Linux/C++ zabezpieczenia informacji za pośrednictwem usług Microsoft Rights Management |
| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) | Zaawansowany zestaw SDK dla twórców aplikacji komputerowych dla systemu Windows i rozwiązań serwerowych, umożliwiający wprowadzenie w produktach zarządzania prawami|
|[AD RMS SDK]()|** UWAGA ** — zestaw AD RMS SDK wykorzystujący funkcje udostępniane przez klienta w bibliotece Msdrm.dll jest dostępny do użytku w systemach Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows Server 2008 i Windows Vista. Może on zostać zmieniony lub przestać być dostępny w kolejnych wersjach. Zamiast tego należy używać zestawu Microsoft Rights Management Services SDK 2.1 korzystającego z funkcji udostępnianych przez klienta w bibliotece Msipc.dll.|
|[Interfejs API obsługi skryptów usług AD RMS]()| Służy do tworzenia skryptów administrujących instalacją usług AD RMS|

## Przykłady kodu i narzędzia
<a id="code-samples-and-tools" class="xliff"></a> ##
Ta kolekcja przykładów kodu usług RMS i narzędzi wspierających twórców dostarczonych przez firmę Microsoft obejmuje wszystkie obsługiwane systemy operacyjne: Android, iOS/OS X, Windows Phone i Windows Desktop. Jest okresowo aktualizowana w celu zapewnienia zgodności z obsługiwanym zestawem SDK.

| Element | System operacyjny | Wersja pomocniczego zestawu SDK | Opis |
|------|------------------|------------------------|-------------|
| [Odczyt dokumentu PDF zabezpieczonego plikiem PFILE](https://blogs.msdn.microsoft.com/rms/2015/11/09/reading-a-pfile-protected-pdf/) | System Windows Desktop| [Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x | **Odczyt dokumentu PDF zabezpieczonego plikiem PFILE** to prosty przykład kodu zamieszczony w naszym blogu RMS Developer's Corner, wykorzystujący interfejs API plików MSIPC do odszyfrowania i otwarcia dokumentu PDF zabezpieczonego plikiem PFILE.|
| [IpcManagedAPI](https://github.com/Azure-Samples/active-directory-dotnet-rms) | System Windows Desktop | [Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x | **IpcManagedAPI** to reprezentacja .NET (C#) zestawu SDK 2.1 usługi RMS, ułatwiająca włączenie obsługi usługi RMS w aplikacji zarządzanej.|
| [IPCNotepad](https://code.msdn.microsoft.com/ipcnotepad-sample-f67dae80) | System Windows Desktop | [Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x| **IPCNotepad** to przykładowa aplikacja obsługująca usługę RMS, prezentująca podstawowe kroki, które każda aplikacja obsługująca usługę RMS powinna wykonywać podczas chronienia i wykorzystywania zawartości ograniczonej.|
| [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms)|System Windows Desktop|[Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x|**IpcDlp** to przykładowa aplikacja Data Leak Protection (DLP) obsługująca usługę RMS, prezentująca podstawowe kroki, które każda aplikacja DLP obsługująca usługę RMS powinna wykonywać podczas wykorzystywania interfejsu API plików do ochrony i wykorzystywania zawartości ograniczonej.|
| [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) | System Windows Desktop|[Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x|**IpcAzureApp** to przykład przedstawiający zastosowanie zestawu SDK usługi RMS w aplikacji Azure do ochrony danych w usłudze Magazyn obiektów Blob Azure.|
| [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) | System Windows Desktop|[Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x|**RmsDocumentInspector** to narzędzie dostarczające informacji takich jak identyfikator zawartości i uprawnienia użytkownika na temat dowolnego pliku chronionego przez usługę RMS.|
| [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) | System Windows Desktop|[Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x|**RmsFileWatcher** to przykład, który demonstruje sposób tworzenia aplikacji systemu Windows, która prowadzi obserwację katalogów w systemie plików i stosuje zasady ochrony usługi RMS dla każdej zmiany, na przykład dodania lub modyfikacji pliku.|
| [Scenariusze użycia w systemie iOS/OS X](https://msdn.microsoft.com/library/dn758307(v=vs.85).aspx) |iOS / OS X|[Zestaw RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) i nowsze wersje zestawu SDK 4.x|Przykłady kodu w języku **Objective C** przedstawiające ważne scenariusze programowania, umożliwiające zapoznanie się z zestawem RMS SDK. Przykłady obejmują korzystanie z formatu Microsoft Protected File, niestandardowe formaty plików chronionych oraz niestandardowe kontrolki interfejsu użytkownika.|
| [Biblioteka interfejsów użytkownika i przykładowa aplikacja](https://github.com/AzureAD/rms-sdk-ui-for-ios) |iOS|[Zestaw RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) i nowsze wersje zestawu SDK 4.x|**Biblioteki interfejsów użytkownika i przykładowa aplikacja dla systemu iOS** w witrynie GitHub, umożliwiające szybkie rozpoczęcie pracy i wielokrotne korzystanie z naszego standardowego interfejsu użytkownika w aplikacjach.|
| [Biblioteka interfejsów użytkownika i przykładowa aplikacja](https://github.com/AzureAD/rms-sdk-ui-for-android) |Android|[Zestaw RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) i nowsze wersje zestawu SDK 4.x|**Biblioteki interfejsów użytkownika i przykładowa aplikacja dla systemu Android** w witrynie GitHub, umożliwiające szybkie rozpoczęcie pracy i wielokrotne korzystanie z naszego standardowego interfejsu użytkownika w aplikacjach.|
| [Scenariusze użycia w systemie Android](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx) |Android|[Zestaw RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) i nowsze wersje zestawu SDK 4.x|**Przykłady kodu w języku Java** przedstawiające ważne scenariusze programowania, umożliwiające zapoznanie się z zestawem RMS SDK. Przykłady obejmują korzystanie z formatu Microsoft Protected File, niestandardowe formaty plików chronionych oraz niestandardowe kontrolki interfejsu użytkownika.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]