---
title: Klasa mip MetadataAction
description: Odwołanie do klasy mip MetadataAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 8f7480775a0226c7161c9ad770184e54427a5084
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47444623"
---
# <a name="class-mipmetadataaction"></a>Klasa mip::MetadataAction 
[Akcji](class_mip_action.md) dodająca informacji o metadanych do zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::vector const < std::string > & GetMetadataToRemove() const  |  Pobierz listę nazw metadanych, które powinny zostać usunięte z zawartością.
publiczne std::vector const < std::pair < std::string, std::string >> & GetMetadataToAdd() const  |  Pobierz metadane pary nazwa/wartość, które powinny zostać dodane do zawartości.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
Pobierz listę nazw metadanych, które powinny zostać usunięte z zawartością.

  
**Zwraca**: wektor ciągów w celu usunięcia. Usuwanie metadanych powinno odbywać się przed dodaniem metadanych.
  
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
Pobierz metadane pary nazwa/wartość, które powinny zostać dodane do zawartości.

  
**Zwraca**: Const std::vector < std::pair < std::string, std::string >> & Usuwanie metadanych ma być przeprowadzane przed dodaniem metadanych.
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.