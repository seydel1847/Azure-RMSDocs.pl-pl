---
title: Klasa mip ProtectionDescriptorBuilder
description: Odwołanie do klasy mip ProtectionDescriptorBuilder
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 42e44cfaf269a43d0210c0c040ea70ccc1fb192e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446638"
---
# <a name="class-mipprotectiondescriptorbuilder"></a>Klasa mip::ProtectionDescriptorBuilder 
Konstruuje [ProtectionDescriptor](class_mip_protectiondescriptor.md) opisujący ochrony skojarzony element zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::shared_ptr MIP_API<ProtectionDescriptor> Build()  |  Tworzy [ProtectionDescriptor](class_mip_protectiondescriptor.md) której uprawnienia dostępu są definiowane przez to [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md) wystąpienia.
 publiczne SetName void (const std::string & wartość)  |  Nazwa zasad ochrony zestawów.
 publiczne Opis_zestawu void (const std::string & wartość)  |  Ustawia opis zasad ochrony.
publiczne SetContentValidUntil void (const std::chrono::time_point < std::chrono::system_clock > & wartość)  |  Ustawia czas wygaśnięcia zasady ochrony.
 publiczne SetAllowOfflineAccess void (wartość logiczna)  |  Zestawy, jeśli zasady ochrony w trybie offline zezwala na dostęp do zawartości, czy nie.
 publiczne SetReferrer void (const std::string & identyfikatora uri)  |  Ustawia adres odwołania zasady ochrony.
publiczne SetEncryptedAppData void (const std::map < std::string, std::string > i wartość)  |  Ustawia dane specyficzne dla aplikacji, które mają być szyfrowane.
publiczne SetSignedAppData void (const std::map < std::string, std::string > i wartość)  |  Ustawia dane specyficzne dla aplikacji, który powinien być podpisany.
 publiczne wirtualne ~ProtectionDescriptorBuilder()  | _Jeszcze nie udokumentowano._
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Tworzy [ProtectionDescriptor](class_mip_protectiondescriptor.md) której uprawnienia dostępu są definiowane przez to [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md) wystąpienia.

  
**Zwraca**: nowe [ProtectionDescriptor](class_mip_protectiondescriptor.md) wystąpienia
  
### <a name="setname"></a>SetName
Nazwa zasad ochrony zestawów.

Parametry:  
* **wartość**: Nazwa zasady ochrony


  
### <a name="setdescription"></a>Opis_zestawu
Ustawia opis zasad ochrony.

Parametry:  
* **wartość**: Opis zasad


  
### <a name="setcontentvaliduntil"></a>SetContentValidUntil
Ustawia czas wygaśnięcia zasady ochrony.

Parametry:  
* **wartość**: czas wygaśnięcia zasad


  
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
Zestawy, jeśli zasady ochrony w trybie offline zezwala na dostęp do zawartości, czy nie.

Parametry:  
* **wartość**: Jeśli zasady umożliwiają dostęp do zawartości w trybie offline lub nie


  
### <a name="setreferrer"></a>SetReferrer
Ustawia adres odwołania zasady ochrony.

Parametry:  
* **Identyfikator URI**: adres odwołania zasad


Odwołującym jest identyfikator URI, które mogą być wyświetlane podczas pozyskiwania zasad ochrony nie powiodło się, który zawiera informacje na temat sposobu ten użytkownik może uzyskać uprawnienia dostępu do zawartości użytkownika.
  
### <a name="setencryptedappdata"></a>SetEncryptedAppData
Ustawia dane specyficzne dla aplikacji, które mają być szyfrowane.

Parametry:  
* **wartość**: dane specyficzne dla aplikacji


Aplikacja może określić słownika zawierającego dane specyficzne dla aplikacji, które będą szyfrowane przez usługę ochrony. Te zaszyfrowane dane nie zależy od zestawu danych podpisanych przez SetSignedAppData.
  
### <a name="setsignedappdata"></a>SetSignedAppData
Ustawia dane specyficzne dla aplikacji, który powinien być podpisany.

Parametry:  
* **wartość**: dane specyficzne dla aplikacji


Aplikacja może określić słownika zawierającego dane specyficzne dla aplikacji, które zostanie podpisany przez usługę ochrony. Ta podpisanych danych jest niezależne od zestawu danych zaszyfrowanych przy SetEncryptedAppData.
  
### <a name="protectiondescriptorbuilder"></a>~ ProtectionDescriptorBuilder
_Jeszcze nie udokumentowano._
