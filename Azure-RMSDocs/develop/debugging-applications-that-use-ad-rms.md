---
title: "Jak debugować aplikację obsługującą prawa | Azure RMS"
description: "Poniższy temat opisuje metody debugowania aplikacji i korzystania z dziennika zdarzeń systemu Windows."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6F6C7651-6A6E-45DD-A0C5-F036F803249B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 31b2fe22bbbb31b991bdf88e408c943e6d2ba685


---

# Porada: debugowanie aplikacji obsługującej prawa

Poniższy temat opisuje metody debugowania aplikacji i korzystania z dziennika zdarzeń systemu Windows.

## Debugowanie aplikacji

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

### Rejestrowanie aplikacji przy użyciu dziennika zdarzeń systemu Windows

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

 

## Tematy pokrewne

 

 



<!--HONumber=Aug16_HO4-->


