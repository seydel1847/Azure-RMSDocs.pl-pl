---
title: "Jak ustawić tryb zabezpieczeń interfejsu API | Azure RMS"
description: "Wybierz tryb zabezpieczeń, w którym aplikacja interfejsu API plików jest uruchamiana."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 1cc034787f8bc47f874259edb143ba0b3f62e47a


---

# Instrukcje: ustawianie trybu zabezpieczeń interfejsu API

Za pomocą funkcji [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) można wybrać tryb zabezpieczeń, w którym jest uruchamiana aplikacja interfejsu API plików.

Aby zainicjować aplikację do uruchamiania w *trybie serwera*, wywołaj funkcję [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) i ustaw tryb zabezpieczeń [**IPC\_API\_MODE\_SERVER**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER). Domyślnie aplikacja jest uruchamiana w *trybie klienta* (**IPC\_API\_MODE\_CLIENT**).

Aby uzyskać więcej informacji na temat *trybu serwera*, zobacz [Typy aplikacji](application-types.md).

**Ważne** Tryb zabezpieczeń należy ustawić przed wywołaniem innych funkcji zestawu Rights Management Services SDK 2.1. Ustawionego trybu zabezpieczeń nie można zmienić dla bieżącego procesu.

## Tematy pokrewne

* [Typy aplikacji](application-types.md)
* [**Wartości trybów interfejsu API**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER)
* [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
 

 



<!--HONumber=Aug16_HO4-->


