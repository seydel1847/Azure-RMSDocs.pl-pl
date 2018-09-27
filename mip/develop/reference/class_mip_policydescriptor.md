# <a name="class-mippolicydescriptor"></a>Klasa mip::PolicyDescriptor 
Reprezentuje zasad ad hoc, skojarzone z zawartości chronionej.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetName()  |  Pobiera nazwę zasad.
 publiczne SetName void (const std::string & wartość)  |  Nazwa zasad zestawów.
 publiczne std::string const & GetDescription()  |  Pobiera opis zasad.
 publiczne Opis_zestawu void (const std::string & wartość)  |  Ustawia opis zasad.
publiczne std::vector const<UserRights>& GetUserRightsList() const  |  Pobiera kolekcję mapowań prawa użytkownika.
publiczne std::vector const < mip::UserRoles > & GetUserRolesList()  |  Pobiera kolekcję mapowań użytkowników do ról.
publiczne std::chrono::time_point const < std::chrono::system_clock > & GetContentValidUntil()  |  Pobiera godzinę wygaśnięcia zasad.
publiczne SetContentValidUntil void (const std::chrono::time_point < std::chrono::system_clock > & wartość)  |  Ustawia czas wygaśnięcia zasad.
 publiczne bool DoesAllowOfflineAccess()  |  Pobiera informację określającą, czy zasady umożliwiają dostęp do zawartości w trybie offline.
 publiczne SetAllowOfflineAccess void (wartość logiczna)  |  Ustawia informację, czy w trybie offline umożliwia zasady dostęp do zawartości.
 publiczne std::string const & GetReferrer() const  |  Pobiera adres odwołania zasad.
 publiczne SetReferrer void (const std::string & identyfikatora uri)  |  Ustawia adres odwołania zasad.
 publiczne AppDataHashMap const & GetEncryptedAppData()  |  Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
 publiczne SetEncryptedAppData void (const AppDataHashMap & wartość)  |  Ustawia dane specyficzne dla aplikacji, które mają być szyfrowane.
 publiczne AppDataHashMap const & GetSignedAppData()  |  Pobiera dane specyficzne dla aplikacji, który został podpisany.
 publiczne SetSignedAppData void (const AppDataHashMap & wartość)  |  Ustawia dane specyficzne dla aplikacji, który powinien być podpisany.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getname"></a>Getname —
Pobiera nazwę zasad.

  
**Zwraca**: Nazwa zasad
  
### <a name="setname"></a>SetName
Nazwa zasad zestawów.

Parametry:  
* **wartość**: Nazwa zasad


  
### <a name="getdescription"></a>GetDescription
Pobiera opis zasad.

  
**Zwraca**: Opis zasad
  
### <a name="setdescription"></a>Opis_zestawu
Ustawia opis zasad.

Parametry:  
* **wartość**: Opis zasad


  
### <a name="userrights"></a>UserRights
Pobiera kolekcję mapowań prawa użytkownika.

  
**Zwraca**: Kolekcja mapowań prawa użytkownika wartości właściwości UserRightsList będzie pusta, jeśli bieżący użytkownik nie ma dostępu do informacji o prawach użytkownika (np. nie jest właścicielem i nie ma prawo VIEWRIGHTSDATA).
  
### <a name="mipuserroles"></a>MIP::UserRoles
Pobiera kolekcję mapowań użytkowników do ról.

  
**Zwraca**: k Olekcja mapowań użytkowników do ról
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Pobiera godzinę wygaśnięcia zasad.

  
**Zwraca**: czas wygaśnięcia zasad
  
### <a name="setcontentvaliduntil"></a>SetContentValidUntil
Ustawia czas wygaśnięcia zasad.

Parametry:  
* **wartość**: czas wygaśnięcia zasad


  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Pobiera informację określającą, czy zasady umożliwiają dostęp do zawartości w trybie offline.

  
**Zwraca**: Określa, czy zasady umożliwiają dostęp do zawartości w trybie offline (domyślny = true)
  
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
Ustawia informację, czy w trybie offline umożliwia zasady dostęp do zawartości.

Parametry:  
* **wartość**: Określa, czy zasady umożliwiają dostęp do zawartości w trybie offline


  
### <a name="getreferrer"></a>GetReferrer
Pobiera adres odwołania zasad.

  
**Zwraca**: adres odwołania zasad odwołującym jest identyfikator URI, które mogą być wyświetlane podczas użytkownika nabycia zasad, który zawiera informacje na temat sposobu ten użytkownik może uzyskać uprawnienia dostępu do zawartości nie powiodło się.
  
### <a name="setreferrer"></a>SetReferrer
Ustawia adres odwołania zasad.

Parametry:  
* **Identyfikator URI**: adres odwołania zasad


Odwołującym jest identyfikator URI, które mogą być wyświetlane podczas pozyskiwania zasad nie powiodło się, który zawiera informacje na temat sposobu ten użytkownik może uzyskać uprawnienia dostępu do zawartości użytkownika.
  
### <a name="appdatahashmap"></a>AppDataHashMap
Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.

  
**Zwraca**: dane specyficzne dla aplikacji A [UserPolicy](class_mip_userpolicy.md) może zawierać Słownik danych specyficzny dla aplikacji, która została zaszyfrowana za usługi RMS. Te zaszyfrowane dane nie zależy od podpisanych danych dostępne za pośrednictwem [PolicyDescriptor::GetSignedAppData](class_mip_policydescriptor.md#getsignedappdata)
  
### <a name="setencryptedappdata"></a>SetEncryptedAppData
Ustawia dane specyficzne dla aplikacji, które mają być szyfrowane.

Parametry:  
* **wartość**: dane specyficzne dla aplikacji


Aplikacja może określić słownika zawierającego dane specyficzne dla aplikacji, które będą szyfrowane przez usługę RMS. Te zaszyfrowane dane nie zależy od zestawu danych podpisanych przez [PolicyDescriptor::SetSignedAppData](class_mip_policydescriptor.md#setsignedappdata).
  
### <a name="appdatahashmap"></a>AppDataHashMap
Pobiera dane specyficzne dla aplikacji, który został podpisany.

  
**Zwraca**: dane specyficzne dla aplikacji A [UserPolicy](class_mip_userpolicy.md) może zawierać słownika zawierającego dane specyficzne dla aplikacji, który został podpisany przez usługę RMS. Ta podpisanych danych jest niezależna od zaszyfrowanych danych dostępne za pośrednictwem [PolicyDescriptor::GetEncryptedAppData](class_mip_policydescriptor.md#getencryptedappdata)
  
### <a name="setsignedappdata"></a>SetSignedAppData
Ustawia dane specyficzne dla aplikacji, który powinien być podpisany.

Parametry:  
* **wartość**: dane specyficzne dla aplikacji


Aplikacja może określić słownika zawierającego dane specyficzne dla aplikacji, które będą podpisywane przez usługę RMS. Ta podpisanych danych zależy od zestawu danych zaszyfrowanych przy [PolicyDescriptor::SetEncryptedAppData](class_mip_policydescriptor.md#setencryptedappdata).