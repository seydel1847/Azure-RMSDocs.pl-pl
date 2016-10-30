---
title: "Jak ustawić tryb zabezpieczeń interfejsu API | Azure RMS"
description: "Wybierz tryb zabezpieczeń, w którym aplikacja interfejsu API plików jest uruchamiana."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 77e2dfe7f2afb1e70de658850f83f86e9224aea6
ms.openlocfilehash: 9235fa1c194162689b854493ea31e76c08c40ce7


---

# Instrukcje: ustawianie trybu zabezpieczeń interfejsu API

Za pomocą funkcji [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) można wybrać tryb zabezpieczeń, w którym jest uruchamiana aplikacja interfejsu API plików.

Aby zainicjować aplikację do uruchamiania w *trybie serwera*, wywołaj funkcję [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) i ustaw tryb zabezpieczeń [IPC\_API\_MODE\_SERVER](https://msdn.microsoft.com/library/hh535236.aspx). Domyślnie aplikacja jest uruchamiana w *trybie klienta* (**IPC\_API\_MODE\_CLIENT**).

Aby uzyskać więcej informacji na temat *trybu serwera*, zobacz [Typy aplikacji](application-types.md).

**Ważne** Tryb zabezpieczeń należy ustawić przed wywołaniem innych funkcji zestawu Rights Management Services SDK 2.1. Ustawionego trybu zabezpieczeń nie można zmienić dla bieżącego procesu.

## Tematy pokrewne

* [Typy aplikacji](application-types.md)
* [Wartości trybów interfejsu API](https://msdn.microsoft.com/library/hh535236.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)
 

 



<!--HONumber=Oct16_HO3-->


