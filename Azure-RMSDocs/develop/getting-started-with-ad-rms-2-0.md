---
title: Wprowadzenie | Azure RMS
description: Platforma zestawu RMS SDK 2.1 umożliwia deweloperom tworzenie aplikacji korzystających z ochrony informacji usługi RMS.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 728113C9-FCF9-4280-BE1D-6AF5C15E449E
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: b1d53d6d79f9d3bd8174e4cf8cf2ae6caff4eb94
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071747"
---
# <a name="getting-started"></a>Wprowadzenie

Zestaw Rights Management Services SDK 2.1 umożliwia deweloperom tworzenie aplikacji korzystających z ochrony informacji usługi RMS za pomocą serwera usługi RMS lub usługi Azure RMS. Platforma obsługuje złożone rozwiązania w zakresie zabezpieczeń, takie jak zarządzanie kluczami oraz przetwarzanie szyfrowania i odszyfrowywania, a także oferuje uproszczony interfejs API ułatwiający tworzenie aplikacji.

## <a name="get-started-with-rmssdk21"></a>Wprowadzenie do zestawu RMS SDK 2.1

W tym temacie szczegółowo przedstawiono proces konfigurowania i uruchamiania aplikacji z obsługą praw w środowisku testowym. Poniższe tematy zawierają opis konfigurowania środowiska deweloperskiego. Wymieniono je w porządku sugerującym kolejność wykonywania czynności.

## <a name="in-this-sections"></a>Zawartość tej sekcji

| Temat | Opis |
|-------|-------------|
| [Informacje o wersji](release-notes-rtm.md) | Ten temat zawiera ważne informacje o bieżącej i poprzednich wersjach zestawu RMS SDK 2.1.|
| [Instalacja zestawu SDK](install-the-rms-sdk.md) | W tym temacie szczegółowo opisano proces instalacji narzędzi deweloperskich.|
| [Konfigurowanie programu Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md) | Ten temat zawiera instrukcje dotyczące konfigurowania projektu programu Visual Studio do korzystania z zestawu RMS SDK 2.1.|
| [Tworzenie aplikacji](developing-your-application.md) | Ten temat zawiera podstawowe wskazówki dotyczące kluczowych aspektów aplikacji z obsługą usługi RMS i może służyć jako podstawa tworzenia aplikacji.|
| [Testowanie aplikacji](how-to-set-up-your-test-environment.md) |Ten temat zawiera instrukcje dotyczące konfigurowania aplikacji na potrzeby testów.|
| [Wdrażanie w środowisku produkcyjnym](deploying-your-application.md) |W tym temacie szczegółowo przedstawiono opcje wdrażania aplikacji z obsługą praw.|


Spróbuj przy użyciu zestawu RMS SDK 2.1, postępując zgodnie ze wskazówkami w tych tematach:

- [Instalacja zestawu SDK](install-the-rms-sdk.md)
- [Konfigurowanie programu Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md)
- [Tworzenie aplikacji](developing-your-application.md)
- [Testowanie aplikacji](how-to-set-up-your-test-environment.md)
- [Wdrażanie w środowisku produkcyjnym](deploying-your-application.md)

### <a name="why-use-rmssdk21-for-protecting-your-content"></a>Dlaczego warto używać zestawu RMS SDK 2.1 do ochrony Twojej zawartości

Dla deweloperów, którzy chcą dodać obsługę usługi RMS do nowych i istniejących aplikacji zestaw RMS SDK 2.1 pomaga w ułatwienia:

-   Tworzenie zarządzanych, zgodnych i niezawodnych aplikacji obsługujących usługę RMS.
-   Trwałe szyfrowanie danych użytkowników. Dane pozostaną zaszyfrowane niezależnie od środowiska, urządzenia i systemu operacyjnego.
-   Wymuszanie dużego zestawu ograniczeń użycia, na przykład zapobieganie przechwytywaniu zawartości ekranu z danymi poufnymi.
-   Obsługa zasad ochrony zarządzanych przez przedsiębiorstwo.
-   Obsługa nowych mechanizmów uwierzytelniania i algorytmów szyfrowania w miarę ich wprowadzania.

Zestaw RMS SDK 2.1 obsługuje szeroką gamę ważnych platform klientów i serwerów. Aby uzyskać więcej informacji, zobacz [Obsługiwane platformy](supported-platforms.md).

## <a name="core-principles"></a>Podstawowe zasady

**Prostota** — opinie i wzorce użycia zestawu AD RMS SDK 1.0 zostały przeanalizowane, a uzyskane dane zostały użyte do uproszczenia lub zautomatyzowania najtrudniejszych zadań programistycznych. Aplikacje RMS tworzone za pomocą zestawu RMS SDK 2.1 zwykle wymagają 5–10 razy mniej wierszy kodu RMS niż aplikacje RMS napisane przy użyciu zestawu AD RMS SDK 1.0.
**Jednokrotne tworzenie** — aplikacje zestawu RMS SDK 2.1 nie wymagają zmiany kodu ani ponownej kompilacji do korzystania z najnowszych funkcji usługi RMS. Nowe funkcje usługi RMS będą udostępniane w istniejącej aplikacji w miarę dodawania ich do serwera usługi RMS.
**Spójność** — zestaw RMS SDK 2.1 ułatwia tworzenie aplikacji spójnie obsługujących różne konfiguracje usługi RMS. Ponadto znacząco zmniejsza on liczbę elementów interfejsu użytkownika usługi RMS, które musi utworzyć deweloper aplikacji, co ułatwia zachowanie spójnego wyglądu i sposobu działania oraz minimalizuje konieczność edukacji użytkowników.

## <a name="related-topics"></a>Tematy pokrewne

* [Przewodnik dla deweloperów usług RMS](developers-guide.md)