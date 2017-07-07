---
title: "Jak ustawić tryb zabezpieczeń interfejsu API | Azure RMS"
description: "Wybierz tryb zabezpieczeń, w którym aplikacja interfejsu API plików jest uruchamiana."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 5ad73cdb72957425ce71f77ba3d11ec457a4f72f
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="how-to-set-the-api-security-mode"></a>Instrukcje: ustawianie trybu zabezpieczeń interfejsu API

Za pomocą funkcji [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) można wybrać tryb zabezpieczeń, w którym jest uruchamiana aplikacja interfejsu API plików.

Aby zainicjować aplikację do uruchamiania w *trybie serwera*, wywołaj funkcję [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) i ustaw tryb zabezpieczeń [IPC\_API\_MODE\_SERVER](https://msdn.microsoft.com/library/hh535236.aspx). Domyślnie aplikacja jest uruchamiana w *trybie klienta* (**IPC\_API\_MODE\_CLIENT**).

Aby uzyskać więcej informacji na temat *trybu serwera*, zobacz [Typy aplikacji](application-types.md).

**Ważne** Tryb zabezpieczeń należy ustawić przed wywołaniem innych funkcji zestawu Rights Management Services SDK 2.1. Ustawionego trybu zabezpieczeń nie można zmienić dla bieżącego procesu.

## <a name="related-topics"></a>Tematy pokrewne

* [Typy aplikacji](application-types.md)
* [Wartości trybów interfejsu API](https://msdn.microsoft.com/library/hh535236.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]