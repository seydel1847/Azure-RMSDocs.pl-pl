---
title: Testowanie aplikacji | Azure RMS
description: "Instrukcje dotyczące konfigurowania aplikacji na potrzeby testów."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: a4306d69fd08f4839c0b02fd3e0a2acbbbc28721
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="testing-your-application"></a>Testowanie aplikacji

Ten temat zawiera instrukcje dotyczące konfigurowania aplikacji na potrzeby testów.

## <a name="instructions"></a>Instrukcje

### <a name="step-1-setup-for-testing"></a>Krok 1. Konfigurowanie na potrzeby testów

Możesz przeprowadzić test za pomocą usługi Azure RMS lub serwera usługi RMS w systemie Windows Server. Zalecamy rozpoczęcie testowania od usługi Azure RMS, a następnie przeprowadzenie testu przy użyciu serwera usługi RMS, jeśli wymaga tego wdrożenie.

1. Aby uzyskać informacje na temat testowania za pomocą usługi Azure RMS, zobacz [Instrukcje: korzystanie z uwierzytelniania ADAL](how-to-use-adal-authentication.md).
2. Aby uzyskać informacje na temat testowania za pomocą serwera usługi RMS, zobacz [How-to: install and configure an RMS server](how-to-install-and-configure-an-rms-server.md) (Instrukcje: instalowanie i konfigurowanie serwera usługi RMS).
3. Poniżej opisano sposób instalowania środowiska uruchomieniowego dla deweloperów.

   Klient Rights Management Service Client 2.1 musi być zainstalowany na komputerze, na którym będzie testowana aplikacja.
   - W przypadku testowania aplikacji na komputerze innym niż komputer deweloperski można zainstalować na nim klienta RMS Client 2.1 przy użyciu [strony pobierania klienta AD RMS Client](http://www.microsoft.com/en-us/download/details.aspx?id=38396).
   - W przypadku testowania aplikacji na komputerze deweloperskim zestaw SDK 2.1 Usług Rights Management powinien być już na nim zainstalowany. Klient RMS Client 2.1 powinien zostać wtedy zainstalowany w trybie cichym.

    Informacje na temat metody instalowania zestawu SDK 2.1 usługi RMS znajdują się w temacie [Instalacja zestawu SDK](install-the-rms-sdk.md).

## <a name="remarks"></a>Uwagi

Wskazówki zawarte w tym temacie nie są kompletne. Aby uzyskać szczegółowe informacje na temat konfigurowania klienta RMS Client 2.1, zobacz [Uwagi dotyczące wdrażania klienta RMS Client 2.1](https://technet.microsoft.com/en-us/library/jj159267(WS.10).aspx).

### <a name="related-topics"></a>Tematy pokrewne

* [Instrukcje: instalowanie i konfigurowanie serwera usługi RMS](how-to-install-and-configure-an-rms-server.md)
* [Instrukcje: korzystanie z uwierzytelniania ADAL](how-to-use-adal-authentication.md)
* [Instalacja zestawu SDK](install-the-rms-sdk.md)
* [Uwagi dotyczące wdrażania klienta RMS Client 2.1](https://technet.microsoft.com/en-us/library/jj159267(WS.10).aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]