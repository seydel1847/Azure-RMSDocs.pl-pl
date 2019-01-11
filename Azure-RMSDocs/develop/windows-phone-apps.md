---
title: Konfiguracja systemu Windows Phone | Azure RMS
description: Aplikacje Windows Phone można użyć programu Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w aplikacjach.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: e25a446e-b977-4736-9c65-7711171fb0e1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 711b19631cc191f7a182602d3e05556f97072ee4
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071718"
---
# <a name="windows-phone-setup"></a>Konfiguracja systemu Windows Phone


Aplikacje Windows Phone można użyć programu Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w aplikacjach za pomocą usługi Azure Active Directory Rights Management (AAD RM).

Ten temat zawiera informacje pomocne przy konfigurowaniu środowiska do tworzenia nowych własnych aplikacji.

-   [Wymagania wstępne](#prerequisites)
-   [Konfigurowanie środowiska deweloperskiego](#configuring-your-development-environment)
-   [Zobacz też](#see-also)

## <a name="prerequisites"></a>Wymagania wstępne


Musisz mieć następujące oprogramowanie w systemie deweloperskim:

-   System operacyjny [Windows 8.1](https://windows.microsoft.com/windows-8/meet).
-   [Narzędzia programistyczne (SDK) dla systemu Windows Phone 8.1](https://developer.microsoft.com/windows/downloads/sdk-archive)
-   Program Microsoft [Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/) lub nowszy albo program Visual Studio Express 2012 uwzględniony w zestawie SDK dla systemu Windows Phone 8.0/8.1
-   Pakiet MS RMS SDK 4.2 dla Windows Phone. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy](get-started.md).
-   Biblioteka uwierzytelniania: Firma Microsoft zaleca użycie [Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx) i innych bibliotek uwierzytelniania mogą być używane.

Temat [Nowości](release-notes.md) zawiera informacje dotyczące aktualizacji interfejsu API, urządzeń i środowiska oraz informacje o wersji i często zadawane pytania.

Przejrzyj informacje w przewodniku [Opracowywanie aplikacji dla systemu Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/ff402535.aspx) w Centrum deweloperów systemu Windows Phone.

## <a name="configuring-your-development-environment"></a>Konfigurowanie środowiska deweloperskiego


-   Otwórz program *Visual Studio*.
-   Kliknij menu **Plik**. W menu **Plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **Projekt**.
-   W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C\#**, wybierz pozycję **Pusta aplikacja (Windows Phone)**, a następnie kliknij przycisk **OK**.

    ![Tworzenie nowego projektu](../media/wpsetup-newproj.png)

-   W Eksploratorze rozwiązań kliknij projekt prawym przyciskiem myszy, a następnie wybierz pozycję **Dodaj odwołanie**, aby otworzyć okno dialogowe **Dodawanie odwołania**.

    ![Dodawanie odwołania](../media/wpsetup-addref.png)

-   Kliknij przycisk **Przeglądaj** w lewym dolnym rogu okna dialogowego **Dodawanie odwołania** i wybierz plik *Microsoft.RightsManagment.dll* znajdujący się w folderze, do którego wyodrębniono pakiet.
-   **Aplikacje zarządzane** — To odwołanie należy dodać w przypadku kompilowania aplikacji zarządzanej. Wybierz pozycje **Windows 8.1**-&gt;**Rozszerzenia** i zaznacz pole wyboru **Windows Visual C++ Runtime Package for Windows**.

    ![Dodawanie rozszerzeń](../media/wpsetup-refmngr.png)

-   **Dodawanie funkcji** — Aby korzystać z zestawu SDK, aplikacja musi mieć możliwość „Internet (klient i serwer)”. Aby dodać tę możliwość do aplikacji, otwórz plik *Package.appxmanifest* w projekcie i przejdź do karty **Możliwości**.

Teraz możesz przystąpić do tworzenia własnych nowych aplikacji dla systemu Windows Phone.

### <a name="see-also"></a>Zobacz też

[Wprowadzenie](get-started.md)

[Co nowego](release-notes.md)

[Podstawowe koncepcje](core-concepts.md)

[Opracowywanie aplikacji dla systemu Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/ff402535.aspx)

[Dokumentacja interfejsu API systemu Windows](https://msdn.microsoft.com/library/dn891914.aspx)

[Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/)

[Zestaw SDK dla systemu Windows Phone](https://developer.microsoft.com/windows/downloads/sdk-archive)
