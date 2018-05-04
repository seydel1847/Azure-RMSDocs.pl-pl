# <a name="class-mippolicydescriptor"></a>Klasa mip::PolicyDescriptor 
Reprezentuje zasad ad hoc skojarzone z zawartości chronionej.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny const std::string & GetName()  |  Pobiera nazwę zasady.
publiczny SetName void (const std::string & wartość)  |  Ustawia nazwę zasady.
publiczny const std::string & GetDescription()  |  Pobiera opis zasad.
publiczny Opis_zestawu void (const std::string & wartość)  |  Ustawia opis zasad.
publiczny std::vector const<UserRights>& GetUserRightsList() const  |  Pobiera kolekcję mapowań prawa użytkownika.
publiczny std::vector const < mip::UserRoles > & GetUserRolesList()  |  Pobiera kolekcję mapowań użytkowników do ról.
publiczny std::chrono::time_point const < std::chrono::system_clock > & GetContentValidUntil()  |  Pobiera godzinę wygaśnięcia zasad.
publiczny SetContentValidUntil void (const std::chrono::time_point < std::chrono::system_clock > & wartość)  |  Ustawia czas wygaśnięcia zasad.
publiczny bool DoesAllowOfflineAccess()  |  Pobiera czy zasada zezwala na dostęp do zawartości w trybie offline.
publiczny SetAllowOfflineAccess void (wartość logiczna)  |  Ustawia, czy w trybie offline umożliwia zasad dostęp do zawartości.
publiczny std::string const & GetReferrer() const  |  Pobiera adres odwołania zasad.
publiczny SetReferrer void (const std::string & identyfikatora uri)  |  Ustawia adres odwołania zasad.
publiczny const AppDataHashMap & GetEncryptedAppData()  |  Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
publiczny SetEncryptedAppData void (const AppDataHashMap & wartość)  |  Ustawia dane specyficzne dla aplikacji, które powinny być szyfrowane.
publiczny const AppDataHashMap & GetSignedAppData()  |  Pobiera dane specyficzne dla aplikacji, który został podpisany.
publiczny SetSignedAppData void (const AppDataHashMap & wartość)  |  Ustawia dane specyficzne dla aplikacji, które powinny być podpisane.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getname"></a>GetName
Pobiera nazwę zasady.
  
#### <a name="returns"></a>Zwraca
Nazwa zasad
  
### <a name="setname"></a>SetName
Ustawia nazwę zasady.
  
#### <a name="parameters"></a>Parametry
* wartość Nazwa zasad
  
### <a name="getdescription"></a>GetDescription
Pobiera opis zasad.
  
#### <a name="returns"></a>Zwraca
Opis zasad
  
### <a name="setdescription"></a>Opis_zestawu
Ustawia opis zasad.
  
#### <a name="parameters"></a>Parametry
* Wartość Opis zasad
  
### <a name="userrights"></a>UserRights
Pobiera kolekcję mapowań prawa użytkownika.
  
#### <a name="returns"></a>Zwraca
Kolekcja mapowań prawa użytkownika wartości właściwości UserRightsList będzie pusta, jeśli bieżący użytkownik nie ma dostępu do informacji o prawach użytkownika (tj. nie jest właścicielem i nie mają prawa VIEWRIGHTSDATA).
  
### <a name="mipuserroles"></a>MIP::UserRoles
Pobiera kolekcję mapowań użytkowników do ról.
  
#### <a name="returns"></a>Zwraca
K olekcja mapowań użytkowników do ról
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Pobiera godzinę wygaśnięcia zasad.
  
#### <a name="returns"></a>Zwraca
Czas wygaśnięcia zasad
  
### <a name="setcontentvaliduntil"></a>SetContentValidUntil
Ustawia czas wygaśnięcia zasad.
  
#### <a name="parameters"></a>Parametry
* wartość czasu wygaśnięcia zasad
  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Pobiera czy zasada zezwala na dostęp do zawartości w trybie offline.
  
#### <a name="returns"></a>Zwraca
Określa, czy zasada zezwala na dostęp do zawartości w trybie offline (domyślna = true)
  
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
Ustawia, czy w trybie offline umożliwia zasad dostęp do zawartości.
  
#### <a name="parameters"></a>Parametry
* wartość określa, czy zasada zezwala na dostęp do zawartości w trybie offline
  
### <a name="getreferrer"></a>GetReferrer
Pobiera adres odwołania zasad.
  
#### <a name="returns"></a>Zwraca
Zasady — baza adresów odwołania jest identyfikatorem URI, który mogą być wyświetlane po nabycia zasad nie powiodło się, który zawiera informacje na temat jak użytkownik może uzyskać uprawnienia do uzyskania dostępu do zawartości.
  
### <a name="setreferrer"></a>SetReferrer
Ustawia adres odwołania zasad.
  
#### <a name="parameters"></a>Parametry
* Identyfikator URI zasad — baza adresów odwołania jest identyfikatorem URI, który mogą być wyświetlane po nabycia zasad nie powiodło się, który zawiera informacje na temat jak użytkownik może uzyskać uprawnienia do uzyskania dostępu do zawartości.
  
### <a name="appdatahashmap"></a>AppDataHashMap
Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
  
#### <a name="returns"></a>Zwraca
Dane specyficzne dla aplikacji, A [UserPolicy](#classmip_1_1_user_policy) może zawierać słownika dane specyficzne dla aplikacji, która została zaszyfrowana za pomocą usługi RMS. Te zaszyfrowane dane nie zależy od podpisanych danych dostępny za pośrednictwem [PolicyDescriptor::GetSignedAppData](#classmip_1_1_policy_descriptor_1ad523870efc92f9f81c82121a054d74d4)
  
### <a name="setencryptedappdata"></a>SetEncryptedAppData
Ustawia dane specyficzne dla aplikacji, które powinny być szyfrowane.
  
#### <a name="parameters"></a>Parametry
* dane wartości specyficzny dla aplikacji aplikacji można określić słownika danych specyficzny dla aplikacji, które będą szyfrowane przez usługę RMS. Te zaszyfrowane dane nie zależy od zestawu danych podpisane przez [PolicyDescriptor::SetSignedAppData](#classmip_1_1_policy_descriptor_1a00f35c0b91e48ccdcc6387466a61f362).
  
### <a name="appdatahashmap"></a>AppDataHashMap
Pobiera dane specyficzne dla aplikacji, który został podpisany.
  
#### <a name="returns"></a>Zwraca
Dane specyficzne dla aplikacji, A [UserPolicy](#classmip_1_1_user_policy) może zawierać słownika dane specyficzne dla aplikacji, który został podpisany przez usługę RMS. Ta podpisanych danych jest niezależna od zaszyfrowanych danych dostępny za pośrednictwem [PolicyDescriptor::GetEncryptedAppData](#classmip_1_1_policy_descriptor_1a9a5bcf9d1bf7357de549429179197ab6)
  
### <a name="setsignedappdata"></a>SetSignedAppData
Ustawia dane specyficzne dla aplikacji, które powinny być podpisane.
  
#### <a name="parameters"></a>Parametry
* dane wartości specyficzny dla aplikacji aplikacji można określić słownika danych specyficzny dla aplikacji, które zostaną podpisane przez usługę RMS. Te dane podpisem jest niezależna od zestawu danych zaszyfrowanych przez [PolicyDescriptor::SetEncryptedAppData](#classmip_1_1_policy_descriptor_1a5275224932dc17319092304497e59eb2).