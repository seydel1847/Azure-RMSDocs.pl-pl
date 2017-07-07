---
title: "Pliki środowiska programistycznego | Azure RMS"
description: "W tym temacie przedstawiono pliki środowiska programistycznego i ich względne lokalizacje instalacji na komputerze."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: B57AC6F3-733C-42A8-AF83-0E15FBF27C99
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 2a3d658e420c7306526aaf85aec61f3e13ef67af
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="development-environment-files"></a>Pliki środowiska deweloperskiego

W tym temacie przedstawiono pliki środowiska programistycznego i ich względne lokalizacje instalacji na komputerze.

Zestaw Rights Management Services SDK 2.1 zawiera następujące pliki zainstalowane na komputerze w lokalizacji domyślnej lub określonej przez użytkownika: %MsipcSDKDir%.

|Plik|Ścieżka|Opis|
|----|----|-----------|
|ReadMe.htm| \ | Zawiera link do pomocy usługi RMS i [Informacje o wersji](release-notes-rtm.md).|
|Isvtier5appsigningprivkey.dat|\bin|Zawiera klucz prywatny służący do generowania manifestu używanego podczas tworzenia aplikacji obsługującej usługę RMS.|
|Isvtier5appsigningpubkey.dat|\bin|Zawiera klucz publiczny służący do generowania manifestu używanego podczas tworzenia aplikacji obsługującej usługę RMS.|
|Isvtier5appsignsdk_client.xml|\bin|Służy do generowania manifestu używanego podczas tworzenia aplikacji obsługującej usługę RMS.|
|NazwaAplikacji.isv.mcf|\bin|Wzorzec pliku konfiguracji manifestu umożliwiającego wygenerowanie manifestu podczas tworzenia aplikacji obsługującej usługę RMS.|
|Ipcsecproc_isv.dll|\bin\x86|Biblioteka DLL dla aplikacji x86 używana wewnętrznie przez program Active Directory Rights Management Services Client 2.1 podczas działania w hierarchii niezależnego dostawcy oprogramowania.|
|Ipcsecproc_ssp_isv.dll|\bin\x86|Biblioteka DLL dla aplikacji x86 używana wewnętrznie przez usługę AD RMS 2.1 podczas działania w hierarchii niezależnego dostawcy oprogramowania.|
|Ipcsecproc_isv.dll|\bin\x64|Biblioteka DLL dla aplikacji x64 używana wewnętrznie przez program AD RMS Client 2.1 podczas działania w hierarchii niezależnego dostawcy oprogramowania.|
|Ipcsecproc_ssp_isv.dll|\bin\x64|Biblioteka DLL dla aplikacji x64 używana wewnętrznie przez program AD RMS Client 2.1 podczas działania w hierarchii niezależnego dostawcy oprogramowania.|
|Msipc.h|\inc|Główny plik dołączany dla zestawu RMS SDK 2.1.|
|Ipcprot.h|\inc|Zawiera interfejs publiczny wyeksportowany przez zestaw RMS SDK 2.1.|
|Ipcbase.h|\inc|Zawiera typy podstawowe i funkcje pomocnicze wyeksportowane przez zestaw RMS SDK 2.1.|
|Ipcerror.h|\inc|Zawiera publiczne kody błędów wyeksportowane przez zestaw RMS SDK 2.1.|
|Ipcfile.h|\inc|Zawiera interfejsy API plików wyeksportowane przez zestaw RMS SDK 2.1.|
|Msipc.lib|\lib|Biblioteka do dołączenia podczas tworzenia aplikacji x86 przy użyciu zestawu RMS SDK 2.1.|
|Msipc_s.lib|\lib|Zapewnia punkt wejścia dla metody [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx) dla aplikacji x86.|
|Msipc.lib|\lib\x64|Biblioteka do dołączenia podczas tworzenia aplikacji x64 przy użyciu zestawu RMS SDK 2.1.|
|Msipc_s.lib|\lib\x64|Zapewnia punkt wejścia dla metody [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx) dla aplikacji x64.|
|Genmanifest.exe|\tools|Generuje manifest używany podczas tworzenia aplikacji obsługującej usługę RMS.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]