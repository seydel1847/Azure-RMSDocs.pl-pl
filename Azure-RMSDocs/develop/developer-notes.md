---
# required metadata

title: Uwagi dla deweloperów | Azure RMS
description: W tym temacie podano dokładne wskazówki dotyczące kilku ważnych scenariuszy programowania. 
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Uwagi dla deweloperów

W tej sekcji podano dokładne wskazówki dotyczące kilku ważnych scenariuszy programowania. Scenariusze zawarte w tej sekcji dotyczą tej wersji zestawu Rights Management Services SDK 2.1 i mogą zostać zmienione w kolejnych wersjach.

- [Jawne dodawanie praw właściciela](add-explicit-owner-rights.md) — w przypadku tworzenia licencji od podstaw (przy użyciu funkcji [IpcCreateLicenseFromScratch](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)) w aplikacji należy jawnie dodać prawa właściciela.
- [Typowe warunki wystąpienia błędów i rozwiązania](common-error-conditions-and-solutions.md) — najczęstsze komunikaty o błędach, które mogą być wyświetlane podczas korzystania z narzędzi programistycznych zestawu RMS SDK 2.1.
- [Włączanie powiadomień e-mail](how-to-enable-email-notification.md) — powiadomienia e-mail umożliwiają informowanie właściciela chronionej zawartości o dostępie do jego zawartości.
- [Konfiguracja interfejsu API plików](file-api-configuration.md) — działanie interfejsu API plików można skonfigurować za pomocą ustawień rejestru.
- [IPCHelloWorld — przykładowa aplikacja](how-to-build-your-first-application.md) — ten temat zawiera instrukcje dotyczące tworzenia przykładowej aplikacji obsługującej prawa.
- [Ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md) — za pomocą funkcji [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) można wybrać tryb zabezpieczeń, w którym uruchamiana jest aplikacja interfejsu API plików.
- [Obsługiwane typy plików](supported-file-formats.md) — interfejs API plików obsługuje formaty natywne i Pfile.
- [Śledzenie zawartości](tracking-content.md) — w tym temacie podano podstawowe wskazówki dotyczące implementowania śledzenia dokumentu z zawartością chronioną przy użyciu zestawu RMS SDK 2.1.
- [Praca z szyfrowaniem](working-with-encryption.md) — ten temat umożliwia zapoznanie się z pakietami szyfrowania firmy Microsoft i zawiera przykładowe fragmenty kodu, w których zastosowano te pakiety.

 

## Tematy pokrewne ##
* [Przegląd](ad-rms-overview.md)
* [Sposób użycia](how-to-use-msipc.md)
 

 


<!--HONumber=Apr16_HO4-->


