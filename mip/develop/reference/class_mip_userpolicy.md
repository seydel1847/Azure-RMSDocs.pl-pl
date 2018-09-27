# <a name="class-mipuserpolicy"></a>Klasa mip::UserPolicy 
Reprezentuje zasady skojarzone z zawartości chronionej.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne bool AccessCheck (const std::string & po prawej stronie) const  |  Sprawdza, jeśli zasady udziela użytkownikowi dostępu do określone w prawo.
 publiczne UserPolicyType wartości GetType()  |  Pobiera typ zasad.
 publiczne std::string GetName()  |  Pobiera nazwę zasad.
 publiczne std::string GetDescription()  |  Pobiera opis zasad.
publiczne std::shared_ptr<TemplateDescriptor> GetTemplateDescriptor()  |  Pobiera [TemplateDescriptor](class_mip_templatedescriptor.md) dla oparty na szablonie [UserPolicy](class_mip_userpolicy.md).
publiczne std::shared_ptr<PolicyDescriptor> GetPolicyDescriptor()  |  Pobiera [PolicyDescriptor](class_mip_policydescriptor.md) for ad-hoc [UserPolicy](class_mip_userpolicy.md).
 publiczne std::string GetOwner()  |  Pobiera wiadomość e-mail adres właściciela zawartości.
 publiczne std::string GetIssuedTo()  |  Pobiera użytkownika skojarzonego z zasadami ochrony.
 publiczne bool IsIssuedToOwner()  |  Pobiera informację określającą, czy bieżący użytkownik jest właścicielem zawartości.
 publiczne std::string GetContentId()  |  Pobiera unikatowy identyfikator dla dokumentu/zawartości.
 publiczne mip::AppDataHashMap const GetEncryptedAppData()  |  Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
 publiczne mip::AppDataHashMap const GetSignedAppData()  |  Pobiera dane specyficzne dla aplikacji, który został podpisany.
publiczne std::chrono::time_point < std::chrono::system_clock > GetContentValidUntil()  |  Pobiera godzinę wygaśnięcia zasad.
 publiczne bool DoesUseDeprecatedAlgorithms()  |  Pobiera informację określającą, czy zasada używa przestarzałego algorytmów kryptograficznych (ECB) zgodności z poprzednimi wersjami.
 publiczne bool IsAuditedExtractAllowed()  |  Pobiera informację określającą, czy zasady udziela prawa "inspekcji wyodrębniania" użytkownika.
publiczne std::vector const<unsigned char> GetSerializedPolicy()  |  Serializowanie [UserPolicy](class_mip_userpolicy.md) w licencji publikowania (PL)
publiczne std::shared_ptr < rmscore::core::ProtectionPolicy > GetImpl()  |  Pobiera wewnętrzne pochodne klasy implementację [UserPolicy](class_mip_userpolicy.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="accesscheck"></a>AccessCheck
Sprawdza, jeśli zasady udziela użytkownikowi dostępu do określone w prawo.

Parametry:  
* **prawy**: po prawej stronie, aby sprawdzić



  
**Zwraca**: niezależnie od tego czy zasad udziela użytkownikowi dostępu do określone bezpośrednio
  
### <a name="userpolicytype"></a>UserPolicyType
Pobiera typ zasad.

  
**Zwraca**: typ zasad
  
### <a name="getname"></a>Getname —
Pobiera nazwę zasad.

  
**Zwraca**: Nazwa zasad
  
### <a name="getdescription"></a>GetDescription
Pobiera opis zasad.

  
**Zwraca**: Opis zasad
  
### <a name="templatedescriptor"></a>TemplateDescriptor
Pobiera [TemplateDescriptor](class_mip_templatedescriptor.md) dla oparty na szablonie [UserPolicy](class_mip_userpolicy.md).

  
**Zwraca**: [TemplateDescriptor](class_mip_templatedescriptor.md) Jeśli [UserPolicy](class_mip_userpolicy.md) jest oparte na szablonach else nullptr
  
### <a name="policydescriptor"></a>PolicyDescriptor
Pobiera [PolicyDescriptor](class_mip_policydescriptor.md) for ad-hoc [UserPolicy](class_mip_userpolicy.md).

  
**Zwraca**: [PolicyDescriptor](class_mip_policydescriptor.md) Jeśli [UserPolicy](class_mip_userpolicy.md) jest zapytań ad hoc else nullptr
  
### <a name="getowner"></a>GetOwner —
Pobiera wiadomość e-mail adres właściciela zawartości.

  
**Zwraca**: wiadomości E-mail adres właściciela zawartości
  
### <a name="getissuedto"></a>GetIssuedTo
Pobiera użytkownika skojarzonego z zasadami ochrony.

  
**Zwraca**: użytkownik skojarzony z zasadami ochrony
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Pobiera informację określającą, czy bieżący użytkownik jest właścicielem zawartości.

  
**Zwraca**: Określa, czy bieżący użytkownik jest właścicielem zawartości
  
### <a name="getcontentid"></a>GetContentId
Pobiera unikatowy identyfikator dla dokumentu/zawartości.

  
**Zwraca**: Unikatowy identyfikator zawartości
  
### <a name="mipappdatahashmap"></a>MIP::AppDataHashMap
Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
A [UserPolicy](class_mip_userpolicy.md) może zawierać Słownik danych specyficzny dla aplikacji, która została zaszyfrowana za usługi RMS. Te zaszyfrowane dane nie zależy od podpisanych danych dostępne za pośrednictwem [UserPolicy::GetSignedAppData](class_mip_userpolicy.md#getsignedappdata)
  
### <a name="mipappdatahashmap"></a>MIP::AppDataHashMap
Pobiera dane specyficzne dla aplikacji, który został podpisany.
A [UserPolicy](class_mip_userpolicy.md) może zawierać słownika zawierającego dane specyficzne dla aplikacji, który został podpisany przez usługę RMS. Ta podpisanych danych jest niezależna od zaszyfrowanych danych dostępne za pośrednictwem [UserPolicy::GetEncryptedAppData](class_mip_userpolicy.md#getencryptedappdata)
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Pobiera godzinę wygaśnięcia zasad.

  
**Zwraca**: czas wygaśnięcia zasad
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Pobiera informację określającą, czy zasada używa przestarzałego algorytmów kryptograficznych (ECB) zgodności z poprzednimi wersjami.

  
**Zwraca**: Określa, czy zasada jest używany przestarzały algorytmów kryptograficznych
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Pobiera informację określającą, czy zasady udziela prawa "inspekcji wyodrębniania" użytkownika.

  
**Zwraca**: Określa, czy zasady udzielają uprawnienie "inspekcji extract"
  
### <a name="getserializedpolicy"></a>GetSerializedPolicy
Serializowanie [UserPolicy](class_mip_userpolicy.md) w licencji publikowania (PL)

  
**Zwraca**: serializacji [UserPolicy](class_mip_userpolicy.md)
  
### <a name="getimpl"></a>GetImpl
Pobiera wewnętrzne pochodne klasy implementację [UserPolicy](class_mip_userpolicy.md).

  
**Zwraca**: Implementacja klasy pochodnej [UserPolicy](class_mip_userpolicy.md) tylko do użytku wewnętrznego