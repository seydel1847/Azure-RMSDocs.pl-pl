---
title: Testowanie aplikacji | Azure RMS
description: Instrukcje dotyczące konfigurowania aplikacji na potrzeby testów.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8f99338daf79b2a59ddacb914d424da81d2b630b
ms.sourcegitcommit: 8e622a93ff8d07a180e3be6e8b14748354e640bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2018
ms.locfileid: "30258972"
---
# <a name="testing-your-application"></a>Testowanie aplikacji

W tym miejscu zostanie przedstawiony sposób przygotowania do testowania aplikacji.

## <a name="instructions"></a>Instrukcje

Należy przeprowadzić test za pomocą usług Azure RMS lub serwera usługi RMS w systemie Windows Server.  Rozpoczęcie testowania z usługą Azure RMS i testowania serwera usługi RMS (jeśli jest to wymagane do wdrożenia).

- Aby uzyskać informacje na temat testowania za pomocą usługi Azure RMS, zobacz [Instrukcje: korzystanie z uwierzytelniania ADAL](how-to-use-adal-authentication.md).
- Aby uzyskać informacje na temat testowania za pomocą serwera usługi RMS, zobacz [How-to: install and configure an RMS server](how-to-install-and-configure-an-rms-server.md) (Instrukcje: instalowanie i konfigurowanie serwera usługi RMS).
- Aby zainstalować środowisko uruchomieniowe dewelopera:

   Klient Rights Management Service Client 2.1 musi być zainstalowany na komputerze, na którym będzie testowana aplikacja.
   - Aby przetestować aplikację na komputerze innym niż komputer deweloperski, należy zainstalować klienta RMS Client 2.1 na komputerze z [strony pobierania klienta AD RMS](http://www.microsoft.com/en-us/download/details.aspx?id=38396).
   - Komputer deweloperski powinny mieć Rights Management Services SDK 2.1, który został wcześniej zainstalowany.

   Aby uzyskać pomoc, Instalowanie zestawu RMS SDK 2.1, zobacz [Zainstaluj zestaw SDK](install-the-rms-sdk.md).

## <a name="remarks"></a>Uwagi

W tych wskazówkach nie są kompletne. Aby dowiedzieć się, jak skonfigurować klienta RMS Client 2.1, zobacz [uwagi dotyczące wdrażania usług RMS Client 2.1](https://technet.microsoft.com/library/jj159267(WS.10).aspx).

## <a name="related-topics"></a>Tematy pokrewne

* [Instrukcje: instalowanie i konfigurowanie serwera usługi RMS](how-to-install-and-configure-an-rms-server.md)
* [Instrukcje: korzystanie z uwierzytelniania ADAL](how-to-use-adal-authentication.md)
* [Instalacja zestawu SDK](install-the-rms-sdk.md)
* [Uwagi dotyczące wdrażania klienta RMS Client 2.1](https://technet.microsoft.com/library/jj159267(WS.10).aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
