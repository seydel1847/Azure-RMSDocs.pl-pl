---
title: Klasa mip Akcja niestandardowa
description: Odwołanie do klasy mip Akcja niestandardowa
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a94a41c0e7f7848201e2af44187cce2540579b27
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47444728"
---
# <a name="class-mipcustomaction"></a>Klasa mip::CustomAction 
[Akcja niestandardowa](class_mip_customaction.md) jest klasą Akcja ogólna, która przechwytuje wszystkie właściwości podrzędnych działania jako zbiór właściwości. Obiekt wywołujący odpowiada może zrozumieć znaczenie akcji.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetName() const  |  Pobierz nazwę akcji.
publiczne std::vector const < std::pair < std::string, std::string >> & GetProperties() const  |  Pobieranie listy pary wartości klucza właściwości.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getname"></a>Getname —
Pobierz nazwę akcji.

  
**Zwraca**: Nazwa akcji, jeśli taki istnieje inne pusty ciąg.
  
### <a name="getproperties"></a>Getproperties —
Pobieranie listy pary wartości klucza właściwości.

  
**Zwraca**: Lista pary wartości klucza.
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.