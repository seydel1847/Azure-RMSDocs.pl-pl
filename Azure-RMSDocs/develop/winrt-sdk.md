---
title: Konfiguracja Sklepu Windows | Azure RMS
description: "Aplikacje ze Sklepu Windows mogą używać zestawu Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w aplikacji."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2720aa0e-0d37-469f-be99-678bf95a9c51
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dc452dac3a86cd9cc39127d5a29106ae87ba94be
ms.openlocfilehash: c3dfa23a4bb03aec3ad9eae835382040a5347006


---

# <a name="windows-store-setup"></a>Konfiguracja Sklepu Windows

Aplikacje ze Sklepu Windows mogą używać zestawu Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w aplikacji przy użyciu usługi Azure Active Directory Rights Management (AAD RM).

Ten temat zawiera informacje pomocne przy konfigurowaniu środowiska do tworzenia własnych, nowych aplikacji.

-   [Wymagania wstępne](#prerequisites)
-   [Opcjonalne](#optional)
-   [Konfigurowanie środowiska deweloperskiego](#configuring-your-development-environment)
-   [Zobacz też](#see-also)

## <a name="prerequisites"></a>Wymagania wstępne


Musisz mieć następujące oprogramowanie w systemie deweloperskim:

-   System operacyjny [Windows 8.1](http://windows.microsoft.com/en-US/windows-8/meet)
-   [Zestaw Windows SDK dla systemu Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)
-   Program Microsoft [Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview) lub nowszy albo program Visual Studio Express 2012 uwzględniony w zestawie Windows SDK dla systemu Windows 8.0/8.1
-   Zestaw MS RMS SDK 4.2 dla aplikacji ze Sklepu Windows. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy](get-started.md).
-   Biblioteka uwierzytelniania: firma Microsoft zaleca stosowanie biblioteki [Azure AD Authentication Library](https://msdn.microsoft.com/en-us/library/jj573266.aspx), ale można korzystać z innych bibliotek uwierzytelniania.

Temat [Nowości](release-notes.md) zawiera informacje dotyczące aktualizacji interfejsu API, urządzeń i środowiska oraz informacje o wersji i często zadawane pytania.

## <a name="optional"></a>Opcjonalne

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

[Windows 8](http://windows.microsoft.com/en-US/windows-8/meet)

[Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview)

[Dokumentacja interfejsu API systemu Windows](https://msdn.microsoft.com/library/dn891914.aspx)



<!--HONumber=Nov16_HO1-->


