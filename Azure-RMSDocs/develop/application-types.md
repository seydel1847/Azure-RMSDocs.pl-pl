---
title: Typy aplikacji | Azure RMS
description: "W tym temacie omówiono typy aplikacji, które można wybrać do utworzenia jako aplikacje obsługujące prawa."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 97169FC3-1395-4433-A632-7B0F020FABFE
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: f7ebcb3a432a4521a71e3cc80c20b1af64e051c7
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="application-types"></a>Typy aplikacji


W tym temacie omówiono typy aplikacji, które można wybrać do utworzenia jako aplikacje obsługujące prawa.

Następujące typy aplikacji są obecnie obsługiwane przez zestaw Rights Management Services SDK 2.1.

## <a name="simple-applications"></a>Proste aplikacje

Prosta aplikacja może być narzędziem wiersza polecenia wbudowanym w celu zaszyfrowania podanego pliku. Przykład prostej, obsługującej prawa aplikacji zawiera implementacja *IPCHelloWorld* opisana w sekcji [Tworzenie aplikacji](developing-your-application.md).

### <a name="server-mode-applications"></a>Aplikacje w trybie serwera

*Tryb serwera* jest przeznaczony dla nieinterakcyjnych aplikacji, które wykorzystują, chronią lub przetwarzają zawartość chronioną przez usługę RMS. Przykładem może być aplikacja do *ochrony przed utratą danych*, która działa jako usługa na serwerze plików i automatycznie chroni poufne dokumenty. Zobacz przykład tego typu aplikacji w temacie [IpcDlp — przykład](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcDlpApp).

Jeśli aplikacja używa *trybu serwera*, powinna uwierzytelniać się na serwerze usługi RMS w trybie dyskretnym. W przeciwieństwie do *trybu klienta* zestaw RMS SDK 2.1 nie otworzy monitu poświadczeń w razie niepowodzenia uwierzytelniania w trybie dyskretnym. Ponadto podczas uruchamiania w *trybie serwera* nie jest wymagany manifest aplikacji.

Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń interfejsu API, zobacz [Ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md).

### <a name="rich-client-applications"></a>Rozbudowane aplikacje klienckie

Rozbudowane aplikacje klienckie pozwalają użytkownikom na wyświetlanie i manipulowanie danymi przy użyciu graficznego interfejsu użytkownika (GUI). Często dane prezentowane w tym graficznym interfejsie są cenne i wrażliwe na kradzież lub przypadkowe ujawnienie. Obsługa ochrony informacji zazwyczaj rozszerza istniejący scenariusz, ale nie jest główną motywacją do tworzenia aplikacji.

Użycie zestawu RMS SDK 2.1 w przypadku zaawansowanych aplikacji klienckich ułatwia:

-   Zagwarantowanie, że te dane są zawsze szyfrowane.

-   Uniemożliwienie użytkownikom wyodrębniania danych do formatu niechronionego (na przykład uniemożliwienie im korzystanie ze Schowka do kopiowania i wklejania).

Microsoft Notepad jest prostą rozbudowaną aplikacją kliencką. Microsoft Office jest bardziej złożoną rozbudowaną aplikacją kliencką.

Aby uzyskać więcej informacji o ochronie aplikacji, zobacz [Zrozumienie ograniczeń użycia](understanding-usage-restrictions.md).

## <a name="related-topics"></a>Tematy pokrewne

- [IpcDlp — przykład](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d)
- [Tworzenie aplikacji](developing-your-application.md)
- [Ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md)
- [Opis ograniczeń użycia](understanding-usage-restrictions.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]