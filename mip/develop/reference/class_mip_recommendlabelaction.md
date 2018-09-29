---
title: Klasa mip RecommendLabelAction
description: Odwołanie do klasy mip RecommendLabelAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: b8e56daed967523b7580087d7bb934c1b2164320
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446009"
---
# <a name="class-miprecommendlabelaction"></a>Klasa mip::RecommendLabelAction 
Zaleca się etykieta działania jest przeznaczona do zasugerować etykiet do użytkowników. Pominięcie tego wywołania po użytkownik ignoruje zalecana etykieta powinna być podejmowana za pośrednictwem obsługiwanych akcji dla stanu wykonywania.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetLabelId() const  |  Pobierz identyfikator etykiety sugerowane.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getlabelid"></a>GetLabelId
Pobierz identyfikator etykiety sugerowane.

  
**Zwraca**: identyfikator etykiety.
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.