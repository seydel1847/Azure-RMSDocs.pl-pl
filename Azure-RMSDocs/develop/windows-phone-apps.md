---
title: Konfiguracja systemu Windows Phone | Azure RMS
description: Aplikacje systemu Windows Phone mogą używać zestawu Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w aplikacji.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e25a446e-b977-4736-9c65-7711171fb0e1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: e606703aa764f8e4fea009131f41c9394ebb29fb
ms.sourcegitcommit: 8e622a93ff8d07a180e3be6e8b14748354e640bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2018
ms.locfileid: "30258806"
---
# <a name="windows-phone-setup"></a>Konfiguracja systemu Windows Phone


Aplikacje systemu Windows Phone mogą używać zestawu Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w aplikacji przy użyciu usługi Azure Active Directory Rights Management (AAD RM).

Ten temat zawiera informacje pomocne przy konfigurowaniu środowiska do tworzenia nowych własnych aplikacji.

-   [Wymagania wstępne](#prerequisites)
-   [Konfigurowanie środowiska deweloperskiego](#configuring-your-development-environment)
-   [Zobacz też](#see-also)

## <a name="prerequisites"></a>Wymagania wstępne


Musisz mieć następujące oprogramowanie w systemie deweloperskim:

-   System operacyjny [Windows 8.1](http://windows.microsoft.com/en-US/windows-8/meet).
-   [Narzędzia programistyczne (SDK) dla systemu Windows Phone 8.1](http://dev.windowsphone.com/en-us/downloadsdk)
-   Program Microsoft [Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview) lub nowszy albo program Visual Studio Express 2012 uwzględniony w zestawie SDK dla systemu Windows Phone 8.0/8.1
-   Zestaw MS RMS SDK 4.2 dla systemu Windows Phone. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy](get-started.md).
-   Biblioteka uwierzytelniania: firma Microsoft zaleca stosowanie biblioteki [Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx), ale można korzystać z innych bibliotek uwierzytelniania.

Temat [Nowości](release-notes.md) zawiera informacje dotyczące aktualizacji interfejsu API, urządzeń i środowiska oraz informacje o wersji i często zadawane pytania.

Przejrzyj informacje w przewodniku [Opracowywanie aplikacji dla systemu Windows Phone](https://msdn.microsoft.com/en-us/library/windowsphone/develop/ff402535.aspx) w Centrum deweloperów systemu Windows Phone.

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

[Opracowywanie aplikacji dla systemu Windows Phone](https://msdn.microsoft.com/en-us/library/windowsphone/develop/ff402535.aspx)

[Dokumentacja interfejsu API systemu Windows](https://msdn.microsoft.com/library/dn891914.aspx)

[Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview)

[Zestaw SDK dla systemu Windows Phone](http://dev.windowsphone.com/en-us/downloadsdk)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]