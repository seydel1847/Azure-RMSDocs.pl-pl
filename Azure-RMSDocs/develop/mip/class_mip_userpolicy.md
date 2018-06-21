# <a name="class-mipuserpolicy"></a>Klasa mip::UserPolicy 
Reprezentuje zasady skojarzone z zawartości chronionej.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny bool AccessCheck (const std::string & prawej) const  |  Sprawdza, czy zasady udziela użytkownikowi dostępu do określonych w prawo.
 publiczny UserPolicyType GetType()  |  Pobiera typ zasad.
 publiczny std::string GetName()  |  Pobiera nazwę zasady.
 publiczny std::string GetDescription()  |  Pobiera opis zasad.
publiczny std::shared_ptr<TemplateDescriptor> GetTemplateDescriptor()  |  Pobiera [TemplateDescriptor](class_mip_templatedescriptor.md) dla oparty na szablonie [UserPolicy](class_mip_userpolicy.md).
publiczny std::shared_ptr<PolicyDescriptor> GetPolicyDescriptor()  |  Pobiera [PolicyDescriptor](class_mip_policydescriptor.md) dla ad hoc [UserPolicy](class_mip_userpolicy.md).
 publiczny std::string GetOwner()  |  Pobiera wiadomość e-mail adres właściciela zawartości.
 publiczny std::string GetIssuedTo()  |  Pobiera użytkownika skojarzonych z zasadami ochrony.
 publiczny bool IsIssuedToOwner()  |  Pobiera czy bieżący użytkownik jest właścicielem zawartości.
 publiczny std::string GetContentId()  |  Pobiera unikatowy identyfikator dla dokumentu/zawartości.
 publiczny mip::AppDataHashMap const GetEncryptedAppData()  |  Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
 publiczny mip::AppDataHashMap const GetSignedAppData()  |  Pobiera dane specyficzne dla aplikacji, który został podpisany.
publiczny std::chrono::time_point < std::chrono::system_clock > GetContentValidUntil()  |  Pobiera godzinę wygaśnięcia zasad.
 publiczny bool DoesUseDeprecatedAlgorithms()  |  Pobiera czy zasada używa przestarzałego algorytmów kryptograficznych (ECB) dla zgodności z poprzednimi wersjami.
 publiczny bool IsAuditedExtractAllowed()  |  Pobiera czy zasada nie udziela uprawnienie "inspekcji wyodrębniania".
publiczny const std::vector<unsigned char> GetSerializedPolicy()  |  Serializować [UserPolicy](class_mip_userpolicy.md) w licencji publikowania (PL)
publiczny std::shared_ptr < rmscore::core::ProtectionPolicy > GetImpl()  |  Implementacja klasy pochodnej pobiera wewnętrzne [UserPolicy](class_mip_userpolicy.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="accesscheck"></a>AccessCheck
Sprawdza, czy zasady udziela użytkownikowi dostępu do określonych w prawo.

Parametry:  
* **prawy**: prawa do sprawdzenia



  
**Zwraca**: czy zasad udziela użytkownikowi dostępu do określonych w prawo
  
### <a name="userpolicytype"></a>UserPolicyType
Pobiera typ zasad.

  
**Zwraca**: typ zasad
  
### <a name="getname"></a>GetName
Pobiera nazwę zasady.

  
**Zwraca**: Nazwa zasad
  
### <a name="getdescription"></a>GetDescription
Pobiera opis zasad.

  
**Zwraca**: Opis zasad
  
### <a name="templatedescriptor"></a>TemplateDescriptor
Pobiera [TemplateDescriptor](class_mip_templatedescriptor.md) dla oparty na szablonie [UserPolicy](class_mip_userpolicy.md).

  
**Zwraca**: [TemplateDescriptor](class_mip_templatedescriptor.md) Jeśli [UserPolicy](class_mip_userpolicy.md) jest oparty na szablonie else nullptr
  
### <a name="policydescriptor"></a>PolicyDescriptor
Pobiera [PolicyDescriptor](class_mip_policydescriptor.md) dla ad hoc [UserPolicy](class_mip_userpolicy.md).

  
**Zwraca**: [PolicyDescriptor](class_mip_policydescriptor.md) Jeśli [UserPolicy](class_mip_userpolicy.md) jest w trybie ad hoc else nullptr
  
### <a name="getowner"></a>GetOwner
Pobiera wiadomość e-mail adres właściciela zawartości.

  
**Zwraca**: właściciel zawartości adres E-mail
  
### <a name="getissuedto"></a>GetIssuedTo
Pobiera użytkownika skojarzonych z zasadami ochrony.

  
**Zwraca**: użytkownik skojarzony z zasadami ochrony
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Pobiera czy bieżący użytkownik jest właścicielem zawartości.

  
**Zwraca**: Określa, czy bieżący użytkownik jest właścicielem zawartości
  
### <a name="getcontentid"></a>GetContentId
Pobiera unikatowy identyfikator dla dokumentu/zawartości.

  
**Zwraca**: Unikatowy identyfikator zawartości
  
### <a name="mipappdatahashmap"></a>MIP::AppDataHashMap
Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
A [UserPolicy](class_mip_userpolicy.md) może zawierać słownika dane specyficzne dla aplikacji, która została zaszyfrowana za pomocą usługi RMS. Te zaszyfrowane dane nie zależy od podpisanych danych dostępny za pośrednictwem [UserPolicy::GetSignedAppData](class_mip_userpolicy.md#getsignedappdata)
  
### <a name="mipappdatahashmap"></a>MIP::AppDataHashMap
Pobiera dane specyficzne dla aplikacji, który został podpisany.
A [UserPolicy](class_mip_userpolicy.md) może zawierać słownika dane specyficzne dla aplikacji, który został podpisany przez usługę RMS. Ta podpisanych danych jest niezależna od zaszyfrowanych danych dostępny za pośrednictwem [UserPolicy::GetEncryptedAppData](class_mip_userpolicy.md#getencryptedappdata)
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Pobiera godzinę wygaśnięcia zasad.

  
**Zwraca**: czas wygaśnięcia zasad
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Pobiera czy zasada używa przestarzałego algorytmów kryptograficznych (ECB) dla zgodności z poprzednimi wersjami.

  
**Zwraca**: Określa, czy zasada używa przestarzałego algorytmów kryptograficznych
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Pobiera czy zasada nie udziela uprawnienie "inspekcji wyodrębniania".

  
**Zwraca**: Określa, czy zasada nie udziela uprawnienie "inspekcji extract"
  
### <a name="getserializedpolicy"></a>GetSerializedPolicy
Serializować [UserPolicy](class_mip_userpolicy.md) w licencji publikowania (PL)

  
**Zwraca**: serializacji [UserPolicy](class_mip_userpolicy.md)
  
### <a name="getimpl"></a>GetImpl
Implementacja klasy pochodnej pobiera wewnętrzne [UserPolicy](class_mip_userpolicy.md).

  
**Zwraca**: Implementacja klasy pochodnej [UserPolicy](class_mip_userpolicy.md) tylko wewnętrznie