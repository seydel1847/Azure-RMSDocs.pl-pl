---
title: Testowanie aplikacji | Azure RMS
description: Instrukcje dotyczące konfigurowania aplikacji na potrzeby testów.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: ce8c5866d721c64f5bf36bd0ee905b74deb01474
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393695"
---
# <a name="testing-your-application"></a>Testowanie aplikacji

Tutaj dowiesz się, jak przygotować się do testowania aplikacji.

## <a name="instructions"></a>Instrukcje

Możesz przetestować za pomocą usługi Azure RMS lub serwera usługi RMS w systemie Windows Server.  Rozpocznij testowanie za pomocą usługi Azure RMS i testowanie za pomocą serwera usługi RMS, (jeśli jest to wymagane dla danego wdrożenia).

- Aby uzyskać informacje na temat testowania za pomocą usługi Azure RMS, zobacz [Instrukcje: korzystanie z uwierzytelniania ADAL](how-to-use-adal-authentication.md).
- Aby uzyskać informacje na temat testowania za pomocą serwera usługi RMS, zobacz [How-to: install and configure an RMS server](how-to-install-and-configure-an-rms-server.md) (Instrukcje: instalowanie i konfigurowanie serwera usługi RMS).
- Aby zainstalować środowisko uruchomieniowe dewelopera:

   Klient Rights Management Service Client 2.1 musi być zainstalowany na komputerze, na którym będzie testowana aplikacja.
  - Aby przetestować aplikację na komputerze innym niż komputer deweloperski, należy zainstalować klienta RMS Client 2.1 na tym komputerze z [strony pobierania klienta AD RMS](https://www.microsoft.com/download/details.aspx?id=38396).
  - Komputer deweloperski powinien mieć Rights Management Services SDK 2.1, który został wcześniej zainstalowany.

    Aby uzyskać pomoc dotyczącą instalowania zestawu RMS SDK 2.1, zobacz [Zainstaluj zestaw SDK](install-the-rms-sdk.md).

## <a name="remarks"></a>Uwagi

Wskazówki te nie są kompletne. Aby dowiedzieć się, jak skonfigurować klienta RMS Client 2.1, zobacz [uwagach do wdrażania klienta RMS Client 2.1](https://technet.microsoft.com/library/jj159267(WS.10).aspx).

## <a name="related-topics"></a>Tematy pokrewne

* [Instrukcje: instalowanie i konfigurowanie serwera usługi RMS](how-to-install-and-configure-an-rms-server.md)
* [Instrukcje: korzystanie z uwierzytelniania ADAL](how-to-use-adal-authentication.md)
* [Instalacja zestawu SDK](install-the-rms-sdk.md)
* [Uwagi dotyczące wdrażania klienta RMS Client 2.1](https://technet.microsoft.com/library/jj159267(WS.10).aspx)

