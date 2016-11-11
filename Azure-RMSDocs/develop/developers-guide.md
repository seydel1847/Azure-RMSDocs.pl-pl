---
title: Przewodnik dewelopera | Azure RMS
description: "Omówienie narzędzi dla deweloperów, zestawów SDK, dodatkowych bibliotek i przykładów kodu."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a22e6bd0-8ce8-45b4-9a32-273126ab831e
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 84072c64f83ec97ac41d6ec030be5eabff263b4b
ms.openlocfilehash: 366652cbf38c1215f73e6996edd54829170ba4c5


---

# <a name="developers-guide"></a>Przewodnik dewelopera

## <a name="overview"></a>Przegląd ##
Ten przewodnik zawiera opis zestawu pakietów SDK usługi Rights Management oraz rosnącej gamy narzędzi i przykładów kodu dla wszystkich obsługiwanych platform.

## <a name="software-development-kits"></a>Zestawy Software Development Kit ##
Obecnie dostępne są trzy generacje zestawów SDK usługi RMS, opisane w poniższej tabeli.

| Zestaw SDK | Opis |
|------|---------|
| [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Uproszczony zestaw narzędzi nowej generacji, zapewniający lekkie środowisko programistyczne dostarczające aplikacjom dla urządzeń z systemami Android, iOS, Mac OS X, Windows Phone/RT i Linux/C++ zabezpieczenia informacji za pośrednictwem usług Microsoft Rights Management |
| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) | Zaawansowany zestaw SDK dla twórców aplikacji komputerowych dla systemu Windows i rozwiązań serwerowych, umożliwiający wprowadzenie w produktach zarządzania prawami|
|[AD RMS SDK](https://msdn.microsoft.com/library/cc530379.aspx)|** UWAGA ** — zestaw AD RMS SDK wykorzystujący funkcje udostępniane przez klienta w bibliotece Msdrm.dll jest dostępny do użytku w systemach Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows Server 2008 i Windows Vista. Może on zostać zmieniony lub przestać być dostępny w kolejnych wersjach. Zamiast tego należy używać zestawu Microsoft Rights Management Services SDK 2.1 korzystającego z funkcji udostępnianych przez klienta w bibliotece Msipc.dll.|
|[Interfejs API obsługi skryptów usług AD RMS](https://msdn.microsoft.com/en-us/library/bb968797.aspx)| Służy do tworzenia skryptów administrujących instalacją usług AD RMS|

## <a name="powershell-guidance"></a>Wskazówki dotyczące programu PowerShell

[Polecenia cmdlet usługi Azure Rights Management](https://msdn.microsoft.com/library/azure/dn629398.aspx) umożliwiają administrowanie usługą Azure RMS z poziomu wiersza polecenia. Mimo że pozwala to na automatyzację, umożliwia również obsługę niezawodnych i powtarzanych procesów w celu zmniejszenia kosztów administracyjnych. Ponadto niektóre zaawansowane konfiguracje i operacje usługi Azure RMS wymagają programu Azure PowerShell.

[Polecenia cmdlet ochrony usługi RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx) mogą być używane z ochroną danych usługi Azure Rights Management (Azure RMS) z poziomu usługi Azure Information Protection lub z usługą Active Directory Rights Management Services (AD RMS) w celu uzupełnienia innych modułów programu PowerShell na potrzeby wdrożeń usługi Rights Management. Użyj tych poleceń cmdlet ochrony usługi RMS, aby grupowo obejmować ochroną pliki dowolnego typu i anulować tę ochronę.

## <a name="code-samples-and-tools"></a>Przykłady kodu i narzędzia
Ta kolekcja przykładów kodu usługi RMS i narzędzi wspierających twórców dostarczonych przez firmę Microsoft obejmuje wszystkie obsługiwane systemy operacyjne: Android, iOS/OS X, Windows Phone i Windows Desktop. Jest okresowo aktualizowana w celu zapewnienia zgodności z obsługiwanym zestawem SDK.

### <a name="android"></a>Android

Poniższe elementy działają w systemie Android obsługiwanym przez zestaw [SDK 4.2 usługi RMS](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) i nowsze wersje zestawu SDK 4.x.

- [Biblioteka interfejsów użytkowników i przykładowa aplikacja](https://github.com/AzureAD/rms-sdk-ui-for-android) w witrynie GitHub, umożliwiające szybkie rozpoczęcie pracy i wielokrotne korzystanie z naszego standardowego interfejsu użytkownika w aplikacjach.
- [Scenariusze użytkowania systemu Android](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx) w języku Java przedstawiają ważne scenariusze deweloperskie, umożliwiające zapoznanie się z zestawem SDK usługi RMS. Przykłady obejmują korzystanie z formatu Microsoft Protected File, niestandardowe formaty plików chronionych oraz niestandardowe kontrolki interfejsu użytkownika.

### <a name="ios-os-x"></a>iOS / OS X

Poniższe elementy działają w systemach iOS / OS X obsługiwanych przez zestaw [SDK 4.2 usługi RMS](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) i nowsze wersje zestawu SDK 4.x.

- [Scenariusze użytkowania systemów iOS/OS X](https://msdn.microsoft.com/en-us/library/dn758307(v=vs.85).aspx) w języku Objective C przedstawiają ważne scenariusze deweloperskie, umożliwiające zapoznanie się z zestawem SDK usługi RMS. Przykłady obejmują korzystanie z formatu Microsoft Protected File, niestandardowe formaty plików chronionych oraz niestandardowe kontrolki interfejsu użytkownika.
- [Biblioteka interfejsów użytkowników i przykładowa aplikacja](https://github.com/AzureAD/rms-sdk-ui-for-ios) w witrynie GitHub, umożliwiające szybkie rozpoczęcie pracy i wielokrotne korzystanie z naszego standardowego interfejsu użytkownika w aplikacjach. Obsługiwana **tylko w systemie iOS**.

### <a name="windows-desktop"></a>System Windows Desktop

Poniższe elementy działają w systemie Windows Desktop obsługiwanym przez zestaw [SDK 2.1 usługi RMS](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x.

- [Odczyt dokumentu PDF zabezpieczonego plikiem PFILE](https://blogs.msdn.microsoft.com/rms/2015/11/09/reading-a-pfile-protected-pdf/) to prosty przykład kodu zamieszczony w naszym blogu RMS Developer's Corner, wykorzystujący interfejs API plików MSIPC do odszyfrowania i otwarcia dokumentu PDF zabezpieczonego plikiem PFILE.
- [IpcManagedAPI](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcManagedAPI) to reprezentacja .NET (C#) zestawu SDK 2.1 usługi RMS, ułatwiająca włączenie obsługi usługi RMS w aplikacji zarządzanej.
- [IPCNotepad](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcNotepad) to przykładowa aplikacja obsługująca usługę RMS, prezentująca podstawowe kroki, które każda aplikacja obsługująca usługę RMS powinna wykonywać podczas chronienia i wykorzystywania zawartości ograniczonej.
- [IpcDlp](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcDlpApp) to przykładowa aplikacja Data Leak Protection (DLP) obsługująca usługę RMS, prezentująca podstawowe kroki, które każda aplikacja DLP obsługująca usługę RMS powinna wykonywać podczas wykorzystywania interfejsu API plików do ochrony i wykorzystywania zawartości ograniczonej.
- [IpcAzureApp](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcAzureApp) to przykład przedstawiający zastosowanie zestawu SDK usługi RMS w aplikacji Azure do ochrony danych w usłudze Magazyn obiektów Blob Azure.
- [RmsDocumentInspector](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/RmsDocumentInspector) to narzędzie dostarczające informacji takich jak identyfikator zawartości i uprawnienia użytkownika na temat dowolnego pliku chronionego przez usługę RMS.
- [RmsFileWatcher](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/RmsFileWatcher) to przykład, który demonstruje sposób tworzenia aplikacji systemu Windows, która prowadzi obserwację katalogów w systemie plików i stosuje zasady ochrony usługi RMS dla każdej zmiany, na przykład dodania lub modyfikacji pliku.

### <a name="windows-store-and-phone"></a>Sklep Windows i system Windows Phone

- [Biblioteka interfejsów użytkownika dla Sklepu Windows](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore) — biblioteka interfejsów użytkownika dla zestawu SDK 4.1 usługi Microsoft RMS dla aplikacji ze Sklepu Windows. Biblioteka ta jest opcjonalna, a programista może zdecydować się na stworzenie własnego interfejsu użytkownika podczas korzystania z zestawu SDK 4.1 usługi Microsoft RMS.

- [Biblioteka interfejsów użytkownika dla systemu Windows Phone](https://github.com/AzureAD/rms-sdk-ui-for-winphone) — biblioteka interfejsów użytkownika dla zestawu SDK 4.1 usługi Microsoft RMS dla aplikacji systemu Windows Phone. Biblioteka ta jest opcjonalna, a programista może zdecydować się na stworzenie własnego interfejsu użytkownika podczas korzystania z zestawu SDK 4.1 usługi Microsoft RMS.

- [Przykładowa aplikacja](https://github.com/Azure-Samples/active-directory-dotnet-rms-windowsstore) — przykład dla zestawu SDK 4.1 usługi Microsoft RMS dla aplikacji ze Sklepu Windows zawiera przykład podstawowego wykorzystania dokumentów dla platformy.



<!--HONumber=Nov16_HO2-->


