---
# required metadata

title: Konfigurowanie programu Visual Studio | Azure RMS
description: Instrukcje dotyczące konfigurowania projektu programu Visual Studio do korzystania z zestawu RMS SDK 2.1.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 396A2C19-3A00-4E9A-9088-198A48B15289
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurowanie programu Visual Studio

Ten temat zawiera instrukcje dotyczące konfigurowania projektu programu Visual Studio do korzystania z zestawu Rights Management Services SDK 2.1.

## Wymagania wstępne

-   [Instalacja zestawu SDK](create-your-first-rights-aware-application.md)

**Instrukcje**

### Krok 1. Skonfigurowanie projektu programu Visual Studio do korzystania z zestawu RMS SDK 2.1

Te instrukcje dotyczą programu Microsoft Visual Studio 2010. Jeśli używasz innej wersji programu Microsoft Visual Studio, okna dialogowe ustawień mogą wyglądać nieco inaczej.

Te instrukcje dotyczą tworzenia natywnych aplikacji 32-bitowych.

1.  Dodaj katalog dołączania zestawu RMS SDK 2.1 do projektu programu Visual Studio 2010.

    W obszarze **Właściwości konfiguracji** wybierz opcję **Katalogi VC++** i dodaj katalog dołączania zestawu RMS SDK 2.1, **$(MSIPCSDKDIR)\\inc**, do pola **Katalogi dołączania**.

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

## Tematy pokrewne

* [Sposób użycia](how-to-use-msipc.md)
* [Instalacja zestawu SDK](create-your-first-rights-aware-application.md)
 

 





<!--HONumber=Apr16_HO4-->


