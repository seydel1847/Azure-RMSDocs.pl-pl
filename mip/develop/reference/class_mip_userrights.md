---
title: Klasa mip UserRights
description: Odwołanie do klasy mip UserRights
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: c1ef7aaba00bf595d80f07f318aa5808f3a56409
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445125"
---
# <a name="class-mipuserrights"></a>Klasa mip::UserRights 
Grupy użytkowników i praw skojarzonych z nimi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne UserRights (const std::vector < std::string > & użytkowników, const std::vector < std::string > i prawa)  |  [UserRights](class_mip_userrights.md) konstruktora.
publiczne std::vector const < std::string > & Users() const  |  Pobiera użytkowników związanych z zestawem uprawnień.
publiczne std::vector const < std::string > & Rights() const  |  Pobiera prawa powiązane z grupą użytkowników.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="userrights"></a>UserRights
[UserRights](class_mip_userrights.md) konstruktora.

Parametry:  
* **Użytkownicy**: grupy użytkowników, którzy udostępniają te same prawa 


* **prawa**: prawa wspólne grupy użytkowników


  
### <a name="users"></a>Users
Pobiera użytkowników związanych z zestawem uprawnień.

  
**Zwraca**: użytkownicy skojarzeni z zestawem uprawnień
  
### <a name="rights"></a>Prawa
Pobiera prawa powiązane z grupą użytkowników.

  
**Zwraca**: praw skojarzonych z grupą użytkowników