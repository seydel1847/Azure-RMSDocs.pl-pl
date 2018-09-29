---
title: Klasa mip ProtectionDescriptor
description: Odwołanie do klasy mip ProtectionDescriptor
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e723041af1eec7be7a839bf36f6d3db67b32447f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446553"
---
# <a name="class-mipprotectiondescriptor"></a>Klasa mip::ProtectionDescriptor 
Opis ochrony skojarzony element zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ProtectionType GetProtectionType() const  |  Pobiera typ ochrony, czy pochodzi z szablonu zestawu SDK ochrony, czy nie.
 publiczne std::string GetOwner() const  |  Pobiera właściciela dla ochrony.
 publiczne std::string GetName() const  |  Pobiera nazwę ochrony.
 publiczne std::string GetDescription() const  |  Pobiera opis ochrony.
 publiczne std::string GetTemplateId() const  |  Pobiera identyfikator szablonu ochrony, jeśli istnieje.
 publiczne std::string GetLabelId() const  |  Pobiera identyfikator etykiety, jeśli istnieje.
publiczne std::vector<UserRights> GetUserRights() const  |  Pobiera kolekcję mapowań prawa użytkownika.
publiczne std::vector<UserRoles> GetUserRoles() const  |  Pobiera kolekcję mapowań użytkowników do ról.
publiczne std::chrono::time_point < std::chrono::system_clock > GetContentValidUntil() const  |  Pobiera godzinę wygaśnięcia ochrony.
 publiczne bool DoesAllowOfflineAccess() const  |  Dostęp do zawartości pobiera, jeśli ochrona umożliwia w trybie offline, czy nie.
 publiczne std::string GetReferrer() const  |  Pobiera adres odwołania ochrony.
publiczne std::map < std::string, std::string > GetEncryptedAppData() const  |  Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
publiczne std::map < std::string, std::string > GetSignedAppData() const  |  Pobiera dane specyficzne dla aplikacji, który został podpisany.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="protectiontype"></a>ProtectionType
Pobiera typ ochrony, czy pochodzi z szablonu zestawu SDK ochrony, czy nie.

  
**Zwraca**: typ ochrony
  
### <a name="getowner"></a>GetOwner —
Pobiera właściciela dla ochrony.

  
**Zwraca**: właściciel ochrony
  
### <a name="getname"></a>Getname —
Pobiera nazwę ochrony.

  
**Zwraca**: Nazwa ochrony
  
### <a name="getdescription"></a>GetDescription
Pobiera opis ochrony.

  
**Zwraca**: Opis ochrony
  
### <a name="gettemplateid"></a>GetTemplateId
Pobiera identyfikator szablonu ochrony, jeśli istnieje.

  
**Zwraca**: identyfikator szablonu
  
### <a name="getlabelid"></a>GetLabelId
Pobiera identyfikator etykiety, jeśli istnieje.

  
**Zwraca**: [etykiety](class_mip_label.md) identyfikator tej właściwości zostanie tylko uzupełnione w ProtectionDescriptors dla istniejący wcześniej chronionej zawartości. Jest to pole wypełnione przez serwer w momencie chronionej zawartości jest używany.
  
### <a name="userrights"></a>UserRights
Pobiera kolekcję mapowań prawa użytkownika.

  
**Zwraca**: k Olekcja mapowań prawa użytkownika wartość [UserRights](class_mip_userrights.md) właściwość będzie pusta, jeśli bieżący użytkownik nie ma dostępu do tych informacji (to znaczy, jeśli użytkownik nie jest właścicielem i nie ma VIEWRIGHTSDATA Strzałka w prawo).
  
### <a name="userroles"></a>UserRoles
Pobiera kolekcję mapowań użytkowników do ról.

  
**Zwraca**: k Olekcja mapowań użytkowników do ról
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Pobiera godzinę wygaśnięcia ochrony.

  
**Zwraca**: czas wygaśnięcia ochrony
  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Dostęp do zawartości pobiera, jeśli ochrona umożliwia w trybie offline, czy nie.

  
**Zwraca**: Jeśli ochrona umożliwia dostęp do zawartości w trybie offline lub nie (domyślny = true)
  
### <a name="getreferrer"></a>GetReferrer
Pobiera adres odwołania ochrony.

  
**Zwraca**: adres odwołania ochrony odwołującym jest identyfikator URI, który jest zawiera użytkownika, jeśli nie można wyłączyć ochrony zawartości. Zawiera on informacji na temat sposobu ten użytkownik może uzyskać uprawnienia dostępu do zawartości.
  
### <a name="getencryptedappdata"></a>GetEncryptedAppData
Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.

  
**Zwraca**: dane specyficzne dla aplikacji A [ProtectionHandler](class_mip_protectionhandler.md) mogą je utrzymywać słownika zawierającego dane specyficzne dla aplikacji, która została zaszyfrowana za usługę ochrony. Te zaszyfrowane dane nie zależy od podpisanych danych dostępne za pośrednictwem [ProtectionDescriptor::GetSignedAppData](class_mip_protectiondescriptor.md#getsignedappdata)
  
### <a name="getsignedappdata"></a>GetSignedAppData
Pobiera dane specyficzne dla aplikacji, który został podpisany.

  
**Zwraca**: dane specyficzne dla aplikacji A [ProtectionHandler](class_mip_protectionhandler.md) mogą je utrzymywać słownika zawierającego dane specyficzne dla aplikacji, który został podpisany przez usługę ochrony. Ta podpisanych danych jest niezależna od zaszyfrowanych danych dostępne za pośrednictwem [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata)