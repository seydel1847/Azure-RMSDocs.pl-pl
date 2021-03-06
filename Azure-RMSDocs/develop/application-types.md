---
title: Typy aplikacji | Azure RMS
description: W tym temacie omówiono typy aplikacji, które można wybrać do utworzenia jako aplikacje obsługujące prawa.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 97169FC3-1395-4433-A632-7B0F020FABFE
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 744a5648bc436bb903cf1b8feb47ca91b19bb7fc
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071662"
---
# <a name="application-types"></a>Typy aplikacji


W tym temacie omówiono typy aplikacji, które można wybrać do utworzenia jako aplikacje obsługujące prawa.

Następujące typy aplikacji są obecnie obsługiwane przez usługi Rights Management Services SDK 2.1

## <a name="simple-applications"></a>Proste aplikacje

Prosta aplikacja może być narzędziem wiersza polecenia wbudowanym w celu zaszyfrowania podanego pliku. Przykład prostej, obsługującej prawa aplikacji zawiera implementacja *IPCHelloWorld* opisana w sekcji [Tworzenie aplikacji](developing-your-application.md).

### <a name="server-mode-applications"></a>Aplikacje w trybie serwera

*Tryb serwera* jest przeznaczony dla nieinterakcyjnych aplikacji, które wykorzystują, chronią lub przetwarzają zawartość chronioną przez usługę RMS. Przykładem może być aplikacja do *ochrony przed utratą danych*, która działa jako usługa na serwerze plików i automatycznie chroni poufne dokumenty. Zobacz przykład tego typu aplikacji w temacie [IpcDlp — przykład](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcDlpApp).

Jeśli aplikacja używa *trybu serwera*, powinna uwierzytelniać się na serwerze usługi RMS w trybie dyskretnym. W odróżnieniu od *tryb klienta*, zestaw RMS SDK 2.1 nie otworzy monicie o poświadczenia podczas niepowodzenia uwierzytelniania w trybie dyskretnym. Ponadto podczas uruchamiania w *trybie serwera* nie jest wymagany manifest aplikacji.

Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń interfejsu API, zobacz [Ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md).

### <a name="rich-client-applications"></a>Rozbudowane aplikacje klienckie

Rozbudowane aplikacje klienckie pozwalają użytkownikom na wyświetlanie i manipulowanie danymi przy użyciu graficznego interfejsu użytkownika (GUI). Często dane prezentowane w tym graficznym interfejsie są cenne i wrażliwe na kradzież lub przypadkowe ujawnienie. Obsługa ochrony informacji zazwyczaj rozszerza istniejący scenariusz, ale nie jest główną motywacją do tworzenia aplikacji.

Przy użyciu zestawu RMS SDK 2.1 z zaawansowanych aplikacji klienckich ułatwia:

-   Zagwarantowanie, że te dane są zawsze szyfrowane.

-   Uniemożliwienie użytkownikom wyodrębniania danych do formatu niechronionego (na przykład uniemożliwienie im korzystanie ze Schowka do kopiowania i wklejania).

Microsoft Notepad jest prostą rozbudowaną aplikacją kliencką. Microsoft Office jest bardziej złożoną rozbudowaną aplikacją kliencką.

Aby uzyskać więcej informacji o ochronie aplikacji, zobacz [Zrozumienie ograniczeń użycia](understanding-usage-restrictions.md).

## <a name="related-topics"></a>Tematy pokrewne

- [IpcDlp — przykład](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d)
- [Tworzenie aplikacji](developing-your-application.md)
- [Ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md)
- [Opis ograniczeń użycia](understanding-usage-restrictions.md)
