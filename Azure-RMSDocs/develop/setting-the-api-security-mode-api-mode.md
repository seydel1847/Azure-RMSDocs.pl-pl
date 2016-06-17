---
# wymagane metadane

title: Instrukcje: ustawianie trybu zabezpieczeń interfejsu API | Opis usługi Azure RMS: wybieranie trybu zabezpieczeń, w którym jest uruchamiana aplikacja interfejsu API plików.
keywords: author: bruceperlerms manager: mbaldwin ms.date: 04/28/2016 ms.topic: article ms.prod: azure ms.service: rights-management ms.technology: techgroup-identity ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
# opcjonalne metadane

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

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
 

 


<!--HONumber=Jun16_HO2-->

