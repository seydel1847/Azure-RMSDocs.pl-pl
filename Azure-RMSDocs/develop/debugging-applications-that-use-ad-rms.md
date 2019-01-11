---
title: Jak debugować aplikację obsługującą prawa | Azure RMS
description: Poniższy temat opisuje metody debugowania aplikacji i korzystania z dziennika zdarzeń systemu Windows.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 6F6C7651-6A6E-45DD-A0C5-F036F803249B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: cb77177ecb0c92f3e991e0f6d06a55fa2c332873
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071558"
---
# <a name="how-to-debug-a-rights-enabled-application"></a>Porada: debugowanie aplikacji obsługującej prawa

Poniższy temat opisuje metody debugowania aplikacji i korzystania z dziennika zdarzeń systemu Windows.

## <a name="debugging-your-application"></a>Debugowanie aplikacji

W zestawie Rights Management Services SDK 2.1 w przypadku wersji środowiska uruchomieniowego przeznaczonej dla deweloperów testy chroniące przed debugowaniem są wyłączone.

Śledzenie debugowania możesz włączyć za pomocą następującego klucza rejestru. (Aby wyłączyć śledzenie debugowania, zmień wartość na 0). W tej wersji nie trzeba wykonywać żadnych dodatkowych czynności dotyczących debugowania.


```
HKEY_LOCAL_MACHINE
   SOFTWARE
      Microsoft
         MSIPC
            "Trace" = 00000001
            Data type
            dword
```

### <a name="application-logging-by-using-the-windows-event-log"></a>Rejestrowanie aplikacji przy użyciu dziennika zdarzeń systemu Windows

Nazwa dziennika zdarzeń to „Microsoft-RMS-MSIPC/Debug”. W Podglądzie zdarzeń systemu Windows dziennik jest wyświetlany w obszarze „Dzienniki aplikacji i usług\\Microsoft\\RMS\\MSIPC\\Debug”.

**Uwaga**  dziennik jest domyślnie włączona i ustawiony poziom szczegółowości 3.

 

Zmiany ustawień funkcji rejestrowania można wprowadzić za pomocą interfejsu użytkownika Podglądu zdarzeń systemu Windows lub programu Wevtutil — narzędzia wiersza polecenia wbudowanego w systemie Windows.

Interfejs narzędzia Wevtutil umożliwia określenie poziomu szczegółowości dziennika.

Obecnie są obsługiwane trzy poziomy rejestrowania:

-   Poziom 2 — błąd
-   Poziom 3 — ostrzeżenie
-   Poziom 4 — informacje

Na przykład użycie poniższego polecenia spowoduje włączenie dziennika zdarzeń MSIPC i ustawienie informacyjnego poziomu szczegółowości.

**wevtutil sl Microsoft-RMS-MSIPC/Debug /e:true /l:4**

**Uwaga**  w Windows Podglądzie zdarzeń na **widoku** menu, wybierz opcję **Pokaż analityczne i debugowania dzienniki** aby uwidocznić dziennik debugowania MSIPC.
