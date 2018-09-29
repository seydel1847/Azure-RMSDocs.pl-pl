---
title: Klasa mip ApplyLabelAction
description: Odwołanie do klasy mip ApplyLabelAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 06a17ef1e60503cfb7d690bea9bb72316544f16d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445771"
---
# <a name="class-mipapplylabelaction"></a>Klasa mip::ApplyLabelAction 
Stosowanie etykiety akcji wymaga aplikacji wywołującej, aby zastosować etykietę.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetLabelId() const  |  Uzyskaj wymagany identyfikator etykiety.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getlabelid"></a>GetLabelId
Uzyskaj wymagany identyfikator etykiety.

  
**Zwraca**: identyfikator etykiety.
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.