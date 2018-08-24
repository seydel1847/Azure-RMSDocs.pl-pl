---
title: Jak ustawić tryb zabezpieczeń interfejsu API | Azure RMS
description: Wybierz tryb zabezpieczeń, w którym aplikacja interfejsu API plików jest uruchamiana.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.service: information-protection
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: c6e7d29ac65e9f8494e6aaba8d5e3e2564bd3305
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42808416"
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
