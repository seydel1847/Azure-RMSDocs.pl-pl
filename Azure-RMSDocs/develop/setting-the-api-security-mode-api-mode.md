---
title: Jak ustawić tryb zabezpieczeń interfejsu API | Azure RMS
description: Wybierz tryb zabezpieczeń, w którym aplikacja interfejsu API plików jest uruchamiana.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: c1f6b30fa15ac050b77314e1baf8d355f6887f24
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071407"
---
# <a name="how-to-set-the-api-security-mode"></a>Instrukcje: ustawianie trybu zabezpieczeń interfejsu API

Za pomocą funkcji [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) można wybrać tryb zabezpieczeń, w którym jest uruchamiana aplikacja interfejsu API plików.

Aby zainicjować aplikację do uruchamiania w *trybie serwera*, wywołaj funkcję [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) i ustaw tryb zabezpieczeń [IPC\_API\_MODE\_SERVER](https://msdn.microsoft.com/library/hh535236.aspx). Domyślnie aplikacja jest uruchamiana w *trybie klienta* (**IPC\_API\_MODE\_CLIENT**).

Aby uzyskać więcej informacji na temat *trybu serwera*, zobacz [Typy aplikacji](application-types.md).

**Ważne**  tryb zabezpieczeń należy ustawić przed wywołaniem dowolnej funkcji zestawu Rights Management Services SDK 2.1. Ustawionego trybu zabezpieczeń nie można zmienić dla bieżącego procesu.

## <a name="related-topics"></a>Tematy pokrewne

* [Typy aplikacji](application-types.md)
* [Wartości trybów interfejsu API](https://msdn.microsoft.com/library/hh535236.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)
