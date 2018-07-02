# <a name="class-mipprotectiondescriptor"></a>Klasa mip::ProtectionDescriptor 
Reprezentuje zasad ad hoc, skojarzone z zawartości chronionej.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ProtectionType GetProtectionType() const  |  Pobiera typ ochrony, czy pochodzi z szablonu zestawu sdk ochrony, czy nie.
 publiczne std::string const & GetName() const  |  Pobiera nazwę zasad.
 publiczne std::string const & GetDescription() const  |  Pobiera opis zasad.
 publiczne std::string const & GetTemplateId() const  |  Pobiera identyfikator szablonu ochrony.
publiczne std::vector const<UserRights>& GetUserRights() const  |  Pobiera kolekcję mapowań prawa użytkownika.
publiczne std::vector const<UserRoles>& GetUserRoles() const  |  Pobiera kolekcję mapowań użytkowników do ról.
publiczne std::chrono::time_point const < std::chrono::system_clock > & GetContentValidUntil() const  |  Pobiera godzinę wygaśnięcia zasad.
 publiczne bool DoesAllowOfflineAccess() const  |  Pobiera informację określającą, czy zasady umożliwiają dostęp do zawartości w trybie offline.
 publiczne std::string const & GetReferrer() const  |  Pobiera adres odwołania zasad.
publiczne std::map const < std::string, std::string > & GetEncryptedAppData() const  |  Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
publiczne std::map const < std::string, std::string > & GetSignedAppData() const  |  Pobiera dane specyficzne dla aplikacji, który został podpisany.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="protectiontype"></a>ProtectionType
Pobiera typ ochrony, czy pochodzi z szablonu zestawu sdk ochrony, czy nie.

  
**Zwraca**: typ ochrony
  
### <a name="getname"></a>Getname —
Pobiera nazwę zasad.

  
**Zwraca**: Nazwa zasad
  
### <a name="getdescription"></a>GetDescription
Pobiera opis zasad.

  
**Zwraca**: Opis zasad
  
### <a name="gettemplateid"></a>GetTemplateId
Pobiera identyfikator szablonu ochrony.

  
**Zwraca**: identyfikator szablonu
  
### <a name="userrights"></a>UserRights
Pobiera kolekcję mapowań prawa użytkownika.

  
**Zwraca**: k Olekcja mapowań prawa użytkownika wartość [UserRights](class_mip_userrights.md) właściwość będzie pusta, jeśli bieżący użytkownik nie ma dostępu do informacji o prawach użytkownika (np. nie jest właścicielem i nie ma VIEWRIGHTSDATA Strzałka w prawo).
  
### <a name="userroles"></a>UserRoles
Pobiera kolekcję mapowań użytkowników do ról.

  
**Zwraca**: k Olekcja mapowań użytkowników do ról
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Pobiera godzinę wygaśnięcia zasad.

  
**Zwraca**: czas wygaśnięcia zasad
  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Pobiera informację określającą, czy zasady umożliwiają dostęp do zawartości w trybie offline.

  
**Zwraca**: Określa, czy zasady umożliwiają dostęp do zawartości w trybie offline (domyślny = true)
  
### <a name="getreferrer"></a>GetReferrer
Pobiera adres odwołania zasad.

  
**Zwraca**: adres odwołania zasad odwołującym jest identyfikator URI, które mogą być wyświetlane podczas użytkownika nabycia zasad, który zawiera informacje na temat sposobu ten użytkownik może uzyskać uprawnienia dostępu do zawartości nie powiodło się.
  
### <a name="getencryptedappdata"></a>GetEncryptedAppData
Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.

  
**Zwraca**: dane specyficzne dla aplikacji A [ProtectionHandler](class_mip_protectionhandler.md) może zawierać słownika zawierającego dane specyficzne dla aplikacji, która została zaszyfrowana za usługę ochrony. Te zaszyfrowane dane nie zależy od podpisanych danych dostępne za pośrednictwem [ProtectionDescriptor::GetSignedAppData](class_mip_protectiondescriptor.md#getsignedappdata)
  
### <a name="getsignedappdata"></a>GetSignedAppData
Pobiera dane specyficzne dla aplikacji, który został podpisany.

  
**Zwraca**: dane specyficzne dla aplikacji A [ProtectionHandler](class_mip_protectionhandler.md) może zawierać słownika zawierającego dane specyficzne dla aplikacji, który został podpisany przez usługę ochrony. Ta podpisanych danych jest niezależna od zaszyfrowanych danych dostępne za pośrednictwem [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata)