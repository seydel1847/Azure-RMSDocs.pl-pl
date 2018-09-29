---
title: Klasa mip ProtectByTemplateAction
description: Odwołanie do klasy mip ProtectByTemplateAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: cb5f42b25e6f499bc09f3f460ec4a253627b45a5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445465"
---
# <a name="class-mipprotectbytemplateaction"></a>Klasa mip::ProtectByTemplateAction 
Klasa akcji, która określa dodawania ochrony za pomocą szablonu do dokumentu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetTemplateId() const  |  Uzyskaj identyfikator szablonu ochrony, które są skojarzone z akcją.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="gettemplateid"></a>GetTemplateId
Uzyskaj identyfikator szablonu ochrony, które są skojarzone z akcją.

  
**Zwraca**: identyfikator szablonu ochrony
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.