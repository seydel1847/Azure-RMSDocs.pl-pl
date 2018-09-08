---
title: Jak ustawić tryb zabezpieczeń interfejsu API | Azure RMS
description: Wybierz tryb zabezpieczeń, w którym aplikacja interfejsu API plików jest uruchamiana.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: d88656d966bc551fb5513a9e67d02b6a5c2d9fb2
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151320"
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
