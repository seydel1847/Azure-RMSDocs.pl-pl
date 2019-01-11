---
title: Konfigurowanie programu Visual Studio | Azure RMS
description: Instrukcje dotyczące konfigurowania projektu programu Visual Studio do korzystania z zestawu RMS SDK 2.1.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 396A2C19-3A00-4E9A-9088-198A48B15289
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: f26400ba1230ef1b274fa04120c22995d2f6620c
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071492"
---
# <a name="configure-visual-studio"></a>Konfigurowanie programu Visual Studio

Ten temat zawiera instrukcje dotyczące konfigurowania projektu programu Visual Studio do korzystania z usługi Rights Management Services SDK 2.1.

## <a name="prerequisites"></a>Wymagania wstępne

-   [Instalacja zestawu SDK](install-the-rms-sdk.md)

**Instrukcje**

### <a name="step-1-configure-a-visual-studio-project-to-use-rmssdk21"></a>Krok 1: Konfigurowanie projektu programu Visual Studio, aby użyć zestawu RMS SDK 2.1

Te instrukcje są specyficzne dla Microsoft Visual Studio 2010. Jeśli używasz innej wersji programu Microsoft Visual Studio, okna dialogowe ustawień mogą wyglądać nieco inaczej.

Te instrukcje dotyczą tworzenia natywnych aplikacji 32-bitowych.

1.  Dodaj katalog, do projektu programu Visual Studio 2010 dołączania zestawu RMS SDK 2.1.

    W obszarze **właściwości konfiguracji** wybierz **katalogi VC ++** i Dodaj katalog, dołączania zestawu RMS SDK 2.1 **$(MSIPCSDKDIR)\\inc**, aby **Dołącz katalogi** pola.

    ![Pole katalogów dołączania właściwości konfiguracji](../media/include_directories.png)

2.  Dodaj katalog biblioteki zestawu RMS SDK 2.1 do projektu programu Visual Studio 2010.

    W obszarze **właściwości konfiguracji** wybierz **katalogi VC ++** i Dodaj katalog biblioteki zestawu RMS SDK 2.1 do **katalogi bibliotek** dla danej platformy.

    -   W przypadku systemu Win32 użyj wartości **$(MSIPCSDKDIR)\\lib**
    -   W przypadku systemu x64 użyj wartości **$(MSIPCSDKDIR)\\lib\\x64**

    ![Pole katalogów bibliotek właściwości konfiguracji](../media/library_directories.png)

3.  Dodaj pliki bibliotek zestawu RMS SDK 2.1 jako zależności programu Visual Studio 2010.

    W obszarze **konsolidatora**, wybierz opcję **dane wejściowe** i Dodaj pliki bibliotek zestawu RMS SDK 2.1; **Msipc.lib** i **Msipc\_s.lib**, **dodatkowe zależności** pola.

    ![Pole zależności bibliotek konsolidatora](../media/additional_dependencies.png)

4.  Dodaj RMS SDK 2.1 dynamiczne łącze biblioteki (DLL) jako bibliotek DLL ładowanych z opóźnieniem.

    W obszarze **konsolidatora**, wybierz opcję **dane wejściowe**i Dodaj plik RMS SDK 2.1 DLL **Msipc.dll**, **bibliotek DLL załadowanych z opóźnieniem** pola.

    ![Pole bibliotek ładowanych z opóźnieniem konsolidatora](../media/delay_loaded.png)

5.  Utwórz informacje o wersji dla wynikowego pliku binarnego.

    W obszarze **Eksplorator rozwiązań** wybierz opcję **Pliki zasobów** i dodaj nazwę pliku binarnego do pola **Oryginalna nazwa pliku**.

    ![Pole plików zasobów eksploratora rozwiązań](../media/original_file_name.png)

## <a name="related-topics"></a>Tematy pokrewne

* [Instalacja zestawu SDK](install-the-rms-sdk.md)
