---
title: "Opis ograniczeń użycia | Azure RMS"
description: "Wszystkie aplikacje z obsługą usługi RMS muszą wymuszać ograniczenia użycia."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: E388B16C-ECDA-4696-A040-D457D3C96766
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: cc383728d487cac45e59ef34ca43ba47c4db237b


---

# <a name="understanding-usage-restrictions"></a>Opis ograniczeń użycia

Wszystkie aplikacje z obsługą usługi RMS muszą wymuszać ograniczenia użycia. Ograniczenie użycia ma miejsce, gdy użytkownik próbuje wykonać akcję (np. wydrukować dokument), ale zasady usług RMS dla tego dokumentu nie przyznają uprawnienia lub prawa do wykonania tej akcji (np. prawa PRINT).

Uprawnienia użytkownika do danego dokumentu można sprawdzać za pomocą funkcji [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx).

## <a name="understanding-usage-restrictions"></a>Opis ograniczeń użycia

-   Zapoznaj się ze standardowymi prawami usług RMS

    Pełny zestaw praw usług RMS, które mogą być wymuszane przez aplikację, można znaleźć w temacie [Informacje o ograniczeniach użycia](usage-restriction-reference.md).

    Należy zauważyć, że można tworzyć prawa zdefiniowane przez aplikację, specyficzne dla określonej sytuacji, które wykraczają poza standardowe prawa usług RMS.

-   Zidentyfikuj punkty wymuszania ograniczeń użycia

    *Punkt wymuszania ograniczenia użycia* to miejsce w przepływie sterowania aplikacji, w którym konieczne jest wymuszenie ograniczenia użycia. Kilka przykładów typowych punktów wymuszania można znaleźć w temacie [Informacje o ograniczeniach użycia](usage-restriction-reference.md).

    Oceń swoją aplikację, aby określić, które punkty wymuszania ograniczeń użycia powinny być stosowane.

    Być może aplikacja nie potrzebuje wszystkich punktów wymuszania opisanych w temacie [Informacje o ograniczeniach użycia](usage-restriction-reference.md). Jeśli na przykład aplikacja nie zezwala użytkownikom na drukowanie zawartości, nie musi sprawdzać prawa **IPC\_GENERIC\_PRINT**.

-   Zaktualizuj kod w celu sprawdzania dostępu w każdym punkcie wymuszania ograniczeń

    Wskazówki dotyczące sposobu wymuszania określonych praw można znaleźć w temacie [Informacje o ograniczeniach użycia](usage-restriction-reference.md).

## <a name="related-topics"></a>Tematy pokrewne

* [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)
* [Informacje o ograniczeniach użycia](usage-restriction-reference.md)
 

 



<!--HONumber=Nov16_HO2-->


