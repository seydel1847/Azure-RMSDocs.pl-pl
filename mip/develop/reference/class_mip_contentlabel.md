---
title: Klasa mip ContentLabel
description: Odwołanie do klasy mip ContentLabel
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: c105f620ed2cd3d6f1427f2543784ea66ce2c4d7
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446026"
---
# <a name="class-mipcontentlabel"></a>Klasa mip::ContentLabel 
Abstrakcję etykietę Microsoft Information Protection, która jest stosowana do fragmentu zawartości, zazwyczaj dokumentu.
Przechowuje właściwości wystąpienia określonego przydzieloną etykietę.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetCreationTime() const  |  Pobrać czasu utworzenia etykiety.
 publiczne AssignmentMethod GetAssignmentMethod() const  |  Uzyskaj metodę przypisywania etykiety.
publiczne std::vector const < std::pair < std::string, std::string >> & GetExtendedProperties() const  |  Pobiera właściwości rozszerzone.
 publiczne bool IsProtectionAppliedFromLabel() const  |  Pobiera, jeśli ochrona została zastosowana etykieta, czy nie.
publiczne std::shared_ptr<Label> GetLabel() const  |  Pobierz obiekt rzeczywistych stosowane wobec zawartości.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getcreationtime"></a>GetCreationTime
Pobrać czasu utworzenia etykiety.

  
**Zwraca**: godzina utworzenia jako ciąg GMT.
  
### <a name="getassignmentmethod"></a>GetAssignmentMethod
Uzyskaj metodę przypisywania etykiety.

  
**Zwraca**: AssignmentMethod STANDARD | UPRZYWILEJOWANE | Automatycznie. 
  
**Zobacz też**: mip::AssignmentMethod
  
### <a name="getextendedproperties"></a>GetExtendedProperties
Pobiera właściwości rozszerzone.

  
**Zwraca**: właściwości rozszerzone.
  
### <a name="isprotectionappliedfromlabel"></a>IsProtectionAppliedFromLabel
Pobiera, jeśli ochrona została zastosowana etykieta, czy nie.

  
**Zwraca**: wartość True, jeśli istnieje szablonu ochrony, a był za pomocą tej etykiety wartość false.
  
### <a name="label"></a>Etykieta
Pobierz obiekt rzeczywistych stosowane wobec zawartości.

  
**Zwraca**: obiekt etykiety zastosowane wobec zawartości. 
  
**Zobacz też**: [mip::Label](class_mip_label.md)