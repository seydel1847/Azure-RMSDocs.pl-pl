---
title: "Jak debugować aplikację obsługującą prawa | Azure RMS"
description: "Poniższy temat opisuje metody debugowania aplikacji i korzystania z dziennika zdarzeń systemu Windows."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6F6C7651-6A6E-45DD-A0C5-F036F803249B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 0995a18f77f40bf345be3e69860032fdb63a9b38
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
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

**Uwaga** Dziennik jest domyślnie włączony i ma ustawiony poziom szczegółowości na wartość 3.

 

Zmiany ustawień funkcji rejestrowania można wprowadzić za pomocą interfejsu użytkownika Podglądu zdarzeń systemu Windows lub programu Wevtutil — narzędzia wiersza polecenia wbudowanego w systemie Windows.

Interfejs narzędzia Wevtutil umożliwia określenie poziomu szczegółowości dziennika.

Obecnie są obsługiwane trzy poziomy rejestrowania:

-   Poziom 2 — błąd
-   Poziom 3 — ostrzeżenie
-   Poziom 4 — informacje

Na przykład użycie poniższego polecenia spowoduje włączenie dziennika zdarzeń MSIPC i ustawienie informacyjnego poziomu szczegółowości.

**wevtutil sl Microsoft-RMS-MSIPC/Debug /e:true /l:4**

**Uwaga** Aby uwidocznić dziennik debugowania MSIPC, w Podglądzie zdarzeń systemu Windows w menu **Widok** wybierz opcję **Pokaż dzienniki analityczne i debugowania**.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]