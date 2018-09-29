---
title: Klasa mip PolicyHandler
description: Odwołanie do klasy mip PolicyHandler
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 23de5616558a298189cb885727d69a20373a3609
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445941"
---
# <a name="class-mippolicyhandler"></a>Klasa mip::PolicyHandler 
Ta klasa udostępnia interfejs dla wszystkich funkcji programu obsługi zasad w pliku.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::shared_ptr<ContentLabel> GetSensitivityLabel (const ExecutionState & stanu)  |  Pobierz etykiety ważności z istniejącej zawartości.
publiczne std::vector < std::shared_ptr<Action>> ComputeActions (const ExecutionState & stanu)  |  Wykonuje reguły na podstawie podanego stanu programu obsługi i zwraca listę akcji do wykonania.
 publiczne NotifyCommittedActions void (const ExecutionState & stanu)  |  Wywołuje się, gdy obliczona akcje zostały zastosowane i danych nacisk na dysku.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="contentlabel"></a>ContentLabel
Pobierz etykiety ważności z istniejącej zawartości.

Parametry:  
* **Stan**: bieżący stan zawartości 



  
**Zwraca**: Etykieta aktualnie stosowane do zawartości. Jeśli nie ma etykiety, zwracany jest pusty.
  
### <a name="action"></a>Akcja
Wykonuje reguły na podstawie podanego stanu programu obsługi i zwraca listę akcji do wykonania.

Parametry:  
* **Stan**: bieżący stan wykonania w zawartości reguły są uruchomione na. 



  
**Zwraca**: Lista akcji, które powinny być stosowane wobec zawartości.
  
### <a name="notifycommittedactions"></a>NotifyCommittedActions
Wywołuje się, gdy obliczona akcje zostały zastosowane i danych nacisk na dysku.

Parametry:  
* **Stan**: bieżący stan wykonania zawartości po akcje zostały zatwierdzone 


: To wywołanie wysyła zdarzenia inspekcji