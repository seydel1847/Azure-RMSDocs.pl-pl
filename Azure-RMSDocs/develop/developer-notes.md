---
title: "Wskazówki i informacje dla deweloperów | Azure RMS"
description: "W tym temacie podano dokładne wskazówki dotyczące kilku ważnych scenariuszy programowania."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a3d58cc4c430fe2335ff8fbb7e23c77915e6b8ab
ms.openlocfilehash: c09eebc8a950894038a758d8f968c5e3e5ae2a53


---

# <a name="developer-guidance-and-information"></a>Wskazówki i informacje dla deweloperów

W tej sekcji podano dokładne wskazówki dotyczące kilku ważnych scenariuszy programowania, jak również ogólne informacje dotyczące programowania za pomocą tego zestawu SDK. Scenariusze zawarte w tej sekcji dotyczą tej wersji zestawu Rights Management Services SDK 2.1 i mogą zostać zmienione w kolejnych wersjach.
- [Porada: korzystanie z uwierzytelniania ADAL](how-to-use-adal-authentication.md) — uwierzytelnianie w usługach Azure RMS dla aplikacji z użyciem biblioteki Azure Active Directory Authentication Library (ADAL).
- [Porada: dodawanie jawnych praw właściciela](add-explicit-owner-rights.md) — w przypadku tworzenia licencji od podstaw (przy użyciu funkcji [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx)) w aplikacji należy jawnie dodać prawa właściciela.
- [Porada: debugowanie aplikacji obsługującej prawa](debugging-applications-that-use-ad-rms.md) — w tym temacie opisano metody debugowania aplikacji i korzystania z dziennika zdarzeń systemu Windows.
- [Porada: włączanie śledzenia dokumentów i odwołania](tracking-content.md) — w tym temacie podano podstawowe wskazówki dotyczące implementowania śledzenia dokumentu z zawartością i zawarto przykładowy kod służący do aktualizacji metadanych i tworzenia przycisku **Śledź użycie** na potrzeby aplikacji.
- [Porada: włączanie powiadomień e-mail](how-to-enable-email-notification.md) — powiadomienia e-mail umożliwiają informowanie właściciela chronionej zawartości o dostępie do jego zawartości.
- [Porada: umożliwianie współpracy aplikacji usługi z usługami RMS opartymi na chmurze](how-to-use-file-api-with-aadrm-cloud.md) — w tym temacie opisano kroki konfigurowania aplikacji usługi do korzystania z usługi Azure Rights Management.
- [Porada: instalowanie i konfigurowanie serwera usług RMS](how-to-install-and-configure-an-rms-server.md) — ten temat zawiera opis kroków związanych z nawiązywaniem połączenia z serwerem usług RMS lub usługami Azure RMS na potrzeby testowania aplikacji obsługującej prawa.
- [Porada: ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md) — za pomocą funkcji [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) można wybrać tryb zabezpieczeń, w którym uruchamiana jest aplikacja interfejsu API plików.
- [Porada: praca z ustawieniami szyfrowania](working-with-encryption.md) — ten temat umożliwia zapoznanie się z pakietami szyfrowania firmy Microsoft i zawiera przykładowe fragmenty kodu, w których zastosowano te pakiety.
- [Typy aplikacji](application-types.md) — w tym temacie omówiono typy aplikacji, które można wybrać do utworzenia jako aplikacje obsługujące prawa.
- [Konfiguracja interfejsu API plików](file-api-configuration.md) — działanie interfejsu API plików można skonfigurować za pomocą ustawień rejestru.
- [Wskazówki dotyczące zabezpieczeń](security-guidelines.md) — ten temat zawiera informacje wprowadzające i wytyczne dla deweloperów aplikacji dotyczące efektywnej pracy w ekosystemie AIP.
- [Obsługiwane typy plików](supported-file-formats.md) — interfejs API plików obsługuje formaty natywne i Pfile
- [Obsługiwane platformy](supported-platforms.md) — ten temat zawiera informacje o platformach klientów i serwerów obsługiwanych przez zestaw RMS SDK 2.1.
- [Opis ograniczeń użycia](understanding-usage-restrictions.md) — wszystkie aplikacje obsługujące usługi RMS muszą wymuszać ograniczanie użycia określone przez stałe wymienione w tym temacie.

 
## <a name="related-topics"></a>Tematy pokrewne
* [Przegląd](ad-rms-overview.md)
 

 



<!--HONumber=Nov16_HO4-->


