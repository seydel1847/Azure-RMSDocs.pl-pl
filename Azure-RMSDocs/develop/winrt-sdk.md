---
title: Konfiguracja Sklepu Windows | Azure RMS
description: Aplikacje Windows Store służy Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w aplikacjach.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2720aa0e-0d37-469f-be99-678bf95a9c51
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 6d16237ff8d4fbfe1b26a73577c16b78b31849e1
ms.sourcegitcommit: 1cd4edd4ba1eb5e10cb61628029213eda316783a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53266362"
---
# <a name="windows-store-setup"></a>Konfiguracja Sklepu Windows

Aplikacje Windows Store służy Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w aplikacjach za pomocą usługi Azure Active Directory Rights Management (AAD RM).

Ten temat zawiera informacje pomocne przy konfigurowaniu środowiska do tworzenia własnych, nowych aplikacji.

-   [Wymagania wstępne](#prerequisites)
-   [Opcjonalne](#optional)
-   [Konfigurowanie środowiska deweloperskiego](#configuring-your-development-environment)
-   [Zobacz też](#see-also)

## <a name="prerequisites"></a>Wymagania wstępne


Musisz mieć następujące oprogramowanie w systemie deweloperskim:

-   System operacyjny [Windows 8.1](https://windows.microsoft.com/windows-8/meet)
-   [Zestaw Windows SDK dla systemu Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)
-   Program Microsoft [Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/) lub nowszy albo program Visual Studio Express 2012 uwzględniony w zestawie Windows SDK dla systemu Windows 8.0/8.1
-   Pakiet MS RMS SDK 4.2 dla Windows Store aplikacji. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy](get-started.md).
-   Biblioteka uwierzytelniania: Firma Microsoft zaleca użycie [Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx) i innych bibliotek uwierzytelniania mogą być używane.

Temat [Nowości](release-notes.md) zawiera informacje dotyczące aktualizacji interfejsu API, urządzeń i środowiska oraz informacje o wersji i często zadawane pytania.

## <a name="optional"></a>Optional

Biblioteka interfejsów użytkownika firmy Microsoft udostępnia interfejs wielokrotnego użytku do operacji konsumenckich i zabezpieczających dla deweloperów, którzy nie chcą tworzyć własnego niestandardowego interfejsu użytkownika — [Biblioteka interfejsów użytkownika dla aplikacji ze Sklepu Windows](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore). Firma Microsoft udostępnia również przykładową aplikację ze Sklepu Windows — [Przykładowa aplikacja dla Sklepu Windows korzystająca z usługi RMS](https://github.com/AzureADSamples/rms-samples-for-windowsstore).

## <a name="configuring-your-development-environment"></a>Konfigurowanie środowiska deweloperskiego


-   Otwórz program Visual Studio.
-   Kliknij menu **Plik**, kliknij pozycję **Nowy**, a następnie kliknij pozycję **Projekt**.
-   W oknie dialogowym **Nowy projekt** kliknij pozycję **Visual C\#**, wybierz pozycję **Pusta aplikacja (Windows)**, a następnie kliknij przycisk **OK**.

    ![Tworzenie nowego projektu](../media/winrtsetup-newproj.png)

-   W **Eksploratorze rozwiązań** kliknij projekt prawym przyciskiem myszy, a następnie wybierz pozycję **Dodaj odwołanie**, aby otworzyć okno dialogowe **Dodawanie odwołania**.

    ![Dodawanie odwołania](../media/winrtsetup-addref.png)

-   W oknie dialogowym **Dodawanie odwołania** kliknij przycisk **Przeglądaj** i wybierz plik *Microsoft.RightsManagement.dll* znajdujący się w folderze, do którego wyodrębniono zestaw SDK.
-   **Aplikacje zarządzane** — To odwołanie należy dodać w przypadku kompilowania aplikacji zarządzanej. Wybierz pozycje **Windows 8.1**-&gt;**Rozszerzenia** i zaznacz pole wyboru **Windows Visual C++ Runtime Package for Windows**.

    ![Dodawanie rozszerzeń](../media/winrtsetup-refmngr.png)

-   **Dodawanie możliwości** — Aby korzystać z zestawu SDK, aplikacja musi mieć możliwość „Internet (klient i serwer)”. Aby dodać tę możliwość do aplikacji, otwórz plik *Package.appxmanifest* w projekcie i przejdź do karty **Możliwości**.

Teraz możesz przystąpić do tworzenia własnych nowych aplikacji dla Sklepu Windows.

### <a name="see-also"></a>Zobacz też

[Wprowadzenie](get-started.md)

[Co nowego](release-notes.md)

[Terminy i pojęcia dla deweloperów](core-concepts.md)

[Windows 8](https://windows.microsoft.com/windows-8/meet)

[Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/)

[Dokumentacja interfejsu API systemu Windows](https://msdn.microsoft.com/library/dn891914.aspx)
