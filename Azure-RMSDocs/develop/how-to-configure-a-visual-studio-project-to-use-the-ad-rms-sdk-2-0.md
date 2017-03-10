---
title: Konfigurowanie programu Visual Studio | Azure RMS
description: "Instrukcje dotyczące konfigurowania projektu programu Visual Studio do korzystania z zestawu RMS SDK 2.1."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 396A2C19-3A00-4E9A-9088-198A48B15289
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 0b0d761376854101dff66d8f78de01f97c3725de
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="configure-visual-studio"></a>Konfigurowanie programu Visual Studio

Ten temat zawiera instrukcje dotyczące konfigurowania projektu programu Visual Studio do korzystania z zestawu Rights Management Services SDK 2.1.

## <a name="prerequisites"></a>Wymagania wstępne

-   [Instalacja zestawu SDK](install-the-rms-sdk.md)

**Instrukcje**

### <a name="step-1-configure-a-visual-studio-project-to-use-rms-sdk-21"></a>Krok 1. Skonfigurowanie projektu programu Visual Studio do korzystania z zestawu RMS SDK 2.1

Te instrukcje dotyczą programu Microsoft Visual Studio 2010. Jeśli używasz innej wersji programu Microsoft Visual Studio, okna dialogowe ustawień mogą wyglądać nieco inaczej.

Te instrukcje dotyczą tworzenia natywnych aplikacji 32-bitowych.

1.  Dodaj katalog dołączania zestawu RMS SDK 2.1 do projektu programu Visual Studio 2010.

    W obszarze **Właściwości konfiguracji** wybierz pozycję **Katalogi VC++** i dodaj katalog dołączania zestawu RMS SDK 2.1, **$(MSIPCSDKDIR)\\inc**, do pola **Dołącz katalogi**.

    ![Pole katalogów dołączania właściwości konfiguracji](../media/include_directories.png)

2.  Dodaj katalog biblioteki zestawu RMS SDK 2.1 do projektu programu Visual Studio 2010.

    W obszarze **Właściwości konfiguracji** wybierz opcję **Katalogi VC++** i dodaj katalog biblioteki zestawu RMS SDK 2.1 do pola **Katalogi bibliotek** dla danej platformy.

    -   W przypadku systemu Win32 użyj wartości **$(MSIPCSDKDIR)\\lib**
    -   W przypadku systemu x64 użyj wartości **$(MSIPCSDKDIR)\\lib\\x64**

    ![Pole katalogów bibliotek właściwości konfiguracji](../media/library_directories.png)

3.  Dodaj pliki bibliotek zestawu RMS SDK 2.1 jako zależności programu Visual Studio 2010.

    W obszarze **Konsolidator** wybierz opcję **Dane wejściowe** i dodaj pliki bibliotek zestawu RMS SDK 2.1, **Msipc.lib** i **Msipc\_s.lib**, do pola **Dodatkowe zależności**.

    ![Pole zależności bibliotek konsolidatora](../media/additional_dependencies.png)

4.  Dodaj bibliotekę dołączaną dynamicznie (DLL, Dynamic Link Library) zestawu RMS SDK 2.1 jako bibliotekę DLL ładowaną z opóźnieniem.

    W obszarze **Konsolidator** wybierz opcję **Dane wejściowe** i dodaj plik DLL zestawu RMS SDK 2.1, **Msipc.dll**, do pola **Biblioteki DLL ładowane z opóźnieniem**.

    ![Pole bibliotek ładowanych z opóźnieniem konsolidatora](../media/delay_loaded.png)

5.  Utwórz informacje o wersji dla wynikowego pliku binarnego.

    W obszarze **Eksplorator rozwiązań** wybierz opcję **Pliki zasobów** i dodaj nazwę pliku binarnego do pola **Oryginalna nazwa pliku**.

    ![Pole plików zasobów eksploratora rozwiązań](../media/original_file_name.png)

## <a name="related-topics"></a>Tematy pokrewne

* [Instalacja zestawu SDK](install-the-rms-sdk.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]