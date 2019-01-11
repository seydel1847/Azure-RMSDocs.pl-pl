---
title: Przegląd — zestaw RMS SDK 4.2 | Azure RMS
description: AD RMS i Azure RMS to technologia ochrony informacji, która pomaga w zabezpieczaniu informacji cyfrowych przed nieautoryzowanym użyciem.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8A13494E-C1D7-407D-BCD1-A406915EA578
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: a1d251daac312e8a6b39da445cdffc0bca3343ea
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071384"
---
# <a name="overview"></a>Przegląd

Microsoft Rights Management SDK 4.2 to technologia ochrony informacji i jest dostępny dla różnych platform.  Jest to zestaw dewelopera oprogramowania (SDK) lub architektura, której celem jest pomoc komputerom i urządzeniom klienckim w ochronie dostępu do informacji przepływających przez aplikacje obsługujące prawa i w korzystaniu z tych informacji. Zestawy SDK dla tych platform zapewniają prosty interfejs API dla deweloperów aplikacji, który umożliwia ochronę i korzystanie z zawartości cyfrowej, pobieranie szablonów i uzyskiwanie zasad z serwera oraz powiązanych zadań zarządzania prawami.

Dodatkowe informacje na temat obsługiwanych obecnie aplikacji są dostępne w portalu dokumentacji dla deweloperów dla [zestawu SDK usługi Microsoft Rights Management](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md).

Poniżej zamieszczono kilka możliwych scenariuszy:

-   Kancelaria prawna chce zapobiec drukowaniu i przekazywaniu dalej poufnych wiadomości e-mail na urządzeniach przenośnych.
-   Deweloperzy oprogramowania CAD i oprogramowania produkcyjnego chcą ograniczyć dostęp do rysunków do niewielkiej grupy użytkowników z działu badawczego bez konieczności korzystania z haseł.
-   Właściciele graficznej aplikacji mobilnej chcą korzystać z pojedynczej licencji, która umożliwia swobodne wyświetlanie kopii obrazów w niskiej rozdzielczości, ale wymaga opłaty w celu uzyskania dostępu do wersji o wysokiej rozdzielczości.
-   Właściciele biblioteki dokumentów online chcą włączyć prawa do wyświetlania, drukowania i edycji dokumentów na podstawie tożsamości użytkownika przy pobieraniu dokumentów na urządzenie przenośne.
-   Firma chce publikować poufne informacje o pracownikach w wewnętrznej witrynie sieci Web, która ogranicza uprawnienia do wyświetlania i edycji do określonych użytkowników.

Zestaw SDK 4.2 usługi MS RMS można pobrać po potwierdzeniu i zaakceptowaniu umowy licencyjnej, dystrybuowany za oprogramowanie innych firm, aby umożliwić klientom dostęp do zawartości, która została, prawa chronione przez użycie i wdrożenie serwerów usług AD RMS w sieci środowisko lub usług Azure RMS. Aby uzyskać więcej informacji, zobacz temat [Rozpoczynanie pracy](get-started.md).

## <a name="sdk-highlights"></a>Najważniejsze funkcje zestawu SDK


Zestaw SDK 4.2 usługi MS RMS oferuje nowe, atrakcyjne funkcje, które są następujące:

-   **Ponownie zaprojektowane API** — interfejs API zestawu MS RMS SDK 4.2 został przeprojektowany pod kątem maksymalnej prostoty, dzięki czemu deweloperzy mogą korzystać prosty i przejrzysty szyfrowania i odszyfrowywania interfejsu API, który zapewnia spójne działanie usługi RMS przy minimalnym wysiłku.
-   **Hybrydowa obsługa usług AD RMS i Azure RMS** — jedna aplikacja z włączoną obsługą usługi RMS może wykorzystywać i chronić zawartość z serwera usługi AD RMS (przy użyciu rozszerzenia usługi AD RMS dla urządzeń przenośnych) i usługi Azure RMS. Zestaw SDK 4.2 usługi MS RMS w przejrzysty sposób odnajduje odpowiednie punkt końcowy, który Administratorzy IT mogą skonfigurować.
-   **Przełącz z własnej biblioteki uwierzytelniania** — Deweloper aplikacji możesz wybrać bibliotekę uwierzytelniania używaną z MS RMS SDK 4.2. Czy jest to [Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx) lub organizacji niestandardową biblioteką, zestaw SDK 4.2 usługi MS RMS rozdziela stos autoryzacji, co umożliwia wybór biblioteki najlepiej odpowiadającej potrzebom użytkownika.
-   **Przesuń interfejs użytkownika** — zestaw SDK 4.2 usługi MS RMS umożliwia teraz wdrożyć swoje dostosowania interfejsu użytkownika. Od ochrony zawartości i wyboru szablonów wyświetlanie i zmianę uprawnień podczas korzystania z zawartości chronionej, zestaw SDK 4.2 usługi MS RMS nie wymusza żadnego wbudowanego interfejsu użytkownika w aplikacjach. Możesz też skorzystać z bibliotek interfejsów użytkownika usługi Microsoft RMS dla wszystkich platform. Biblioteki te są dostępne przez nasze [konto GitHub](https://github.com/AzureAD/).
-   **Dostęp do zawartości chronionej w trybie offline** — zestaw SDK 4.2 usługi MS RMS umożliwia użytkownikom aplikacji dostęp do zawartości chronionej nawet wtedy, gdy brak połączenia internetowego. Zestaw SDK 4.2 usługi MS RMS bezpiecznie zapisuje w pamięci podręcznej zasady użytkowania zawartości chronionej, dzięki czemu Twoje użytkownicy mają dostęp do danych chronionych przez usługę RMS w trybie offline.

Skorzystaj z przewodnika [Rozpoczynanie pracy](get-started.md), aby rozpocząć pracę nad projektem aplikacji dla urządzenia z informacjami chronionymi.

## <a name="related-topics"></a>Tematy pokrewne

* [Zestaw Microsoft Rights Management SDK](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md)
* [Wprowadzenie](get-started.md)
* [Biblioteka Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx)
* [Konto GitHub](https://github.com/AzureAD/)
