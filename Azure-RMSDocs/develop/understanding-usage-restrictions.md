---
# required metadata

title: Opis ograniczeń użycia | Azure RMS
description: Wszystkie aplikacje z obsługą usługi RMS muszą wymuszać ograniczenia użycia.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: E388B16C-ECDA-4696-A040-D457D3C96766
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Opis ograniczeń użycia

Wszystkie aplikacje z obsługą usługi RMS muszą wymuszać ograniczenia użycia. Ograniczenie użycia ma miejsce, gdy użytkownik próbuje wykonać akcję (np. wydrukować dokument), ale zasady usługi RMS dla tego dokumentu nie przyznają uprawnienia lub prawa do wykonania tej akcji (np. prawa PRINT).

Uprawnienia użytkownika do danego dokumentu można sprawdzać za pomocą funkcji [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck).

## Opis ograniczeń użycia

-   Zapoznaj się ze standardowymi prawami usługi RMS

    Pełny zestaw praw usługi RMS, które mogą być wymuszane przez aplikację, można znaleźć w temacie [Informacje o ograniczeniach użycia](usage-restriction-reference.md).

    Możesz tworzyć zdefiniowane przez aplikację prawa specyficzne dla określonej sytuacji, które wykraczają poza standardowe prawa usługi RMS.

-   Zidentyfikuj punkty wymuszania ograniczeń użycia

    *Punkt wymuszania ograniczenia użycia* to miejsce w przepływie sterowania aplikacji, w którym konieczne jest wymuszenie ograniczenia użycia. Kilka przykładów typowych punktów wymuszania można znaleźć w temacie [Informacje o ograniczeniach użycia](usage-restriction-reference.md).

    Oceń swoją aplikację, aby określić, które punkty wymuszania ograniczeń użycia powinny być stosowane.

    Być może aplikacja nie potrzebuje wszystkich punktów wymuszania opisanych w temacie [Informacje o ograniczeniach użycia](usage-restriction-reference.md). Jeśli na przykład aplikacja nie zezwala użytkownikom na drukowanie zawartości, nie musi sprawdzać prawa **IPC\_GENERIC\_PRINT**.

-   Zaktualizuj kod w celu sprawdzania dostępu w każdym punkcie wymuszania

    Wskazówki dotyczące wymuszania określonych praw można znaleźć w temacie [Informacje o ograniczeniach użycia](usage-restriction-reference.md).

## Tematy pokrewne

* [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck)
* [Informacje o ograniczeniach użycia](usage-restriction-reference.md)
 

 


<!--HONumber=Jun16_HO2-->


