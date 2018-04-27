# <a name="class-mipuserpolicy"></a>Klasa mip::UserPolicy 
Reprezentuje zasady skojarzone z zawartości chronionej.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny bool AccessCheck | Sprawdza, czy zasady udziela użytkownikowi dostępu do określonych w prawo.
UserPolicyType GetType publiczny | Pobiera typ zasad.
publiczny std::string GetName | Pobiera nazwę zasady.
publiczny std::string GetDescription | Pobiera opis zasad.
publiczny std::shared_ptr < TemplateDescriptor > GetTemplateDescriptor publicznego std::shared_ptr < PolicyDescriptor > GetPolicyDescriptor publicznego std::string GetOwner | Pobiera wiadomość e-mail adres właściciela zawartości.
publiczny std::string GetIssuedTo | Pobiera użytkownika skojarzonych z zasadami ochrony.
publiczny bool IsIssuedToOwner | Pobiera czy bieżący użytkownik jest właścicielem zawartości.
publiczny std::string GetContentId | Pobiera unikatowy identyfikator dla dokumentu/zawartości.
publiczny mip::AppDataHashMap const GetEncryptedAppData | Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
publiczny mip::AppDataHashMap const GetSignedAppData | Pobiera dane specyficzne dla aplikacji, który został podpisany.
publiczny std::chrono::time_point < std::chrono::system_clock > GetContentValidUntil | Pobiera godzinę wygaśnięcia zasad.
publiczny bool DoesUseDeprecatedAlgorithms | Pobiera czy zasada używa przestarzałego algorytmów kryptograficznych (ECB) dla zgodności z poprzednimi wersjami.
publiczny bool IsAuditedExtractAllowed | Pobiera czy zasada nie udziela uprawnienie "inspekcji wyodrębniania".
publiczny const std::vector < char bez znaku > GetSerializedPolicy publicznego std::shared_ptr < rmscore::core::ProtectionPolicy > GetImpl
## <a name="members"></a>Elementy członkowskie
### <a name="accesscheck"></a>AccessCheck
Sprawdza, czy zasady udziela użytkownikowi dostępu do określonych w prawo.
#### <a name="parameters"></a>Parametry
* Prawy prawo do sprawdzenia
#### <a name="returns"></a>Zwraca
Czy zasady udziela użytkownikowi dostępu do określonych prawej
### <a name="userpolicytype"></a>UserPolicyType
Pobiera typ zasad.
#### <a name="returns"></a>Zwraca
Typ zasad
### <a name="getname"></a>GetName
Pobiera nazwę zasady.
#### <a name="returns"></a>Zwraca
Nazwa zasad
### <a name="getdescription"></a>GetDescription
Pobiera opis zasad.
#### <a name="returns"></a>Zwraca
Opis zasad
### <a name="templatedescriptor"></a>TemplateDescriptor
Pobiera [TemplateDescriptor](#classmip_1_1_template_descriptor) dla oparty na szablonie [UserPolicy](#classmip_1_1_user_policy).
#### <a name="returns"></a>Zwraca
[TemplateDescriptor](#classmip_1_1_template_descriptor) Jeśli [UserPolicy](#classmip_1_1_user_policy) jest oparty na szablonie else nullptr
### <a name="policydescriptor"></a>PolicyDescriptor
Pobiera [PolicyDescriptor](#classmip_1_1_policy_descriptor) dla ad hoc [UserPolicy](#classmip_1_1_user_policy).
#### <a name="returns"></a>Zwraca
[PolicyDescriptor](#classmip_1_1_policy_descriptor) Jeśli [UserPolicy](#classmip_1_1_user_policy) jest w trybie ad hoc else nullptr
### <a name="getowner"></a>GetOwner
Pobiera wiadomość e-mail adres właściciela zawartości.
#### <a name="returns"></a>Zwraca
Adres e-mail właściciela zawartości
### <a name="getissuedto"></a>GetIssuedTo
Pobiera użytkownika skojarzonych z zasadami ochrony.
#### <a name="returns"></a>Zwraca
Użytkownik skojarzony z zasadami ochrony
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Pobiera czy bieżący użytkownik jest właścicielem zawartości.
#### <a name="returns"></a>Zwraca
Określa, czy bieżący użytkownik jest właścicielem zawartości
### <a name="getcontentid"></a>GetContentId
Pobiera unikatowy identyfikator dla dokumentu/zawartości.
#### <a name="returns"></a>Zwraca
Unikatowy identyfikator zawartości
### <a name="mipappdatahashmap"></a>MIP::AppDataHashMap
Pobiera dane specyficzne dla aplikacji, która została zaszyfrowana.
A [UserPolicy](#classmip_1_1_user_policy) może zawierać słownika dane specyficzne dla aplikacji, która została zaszyfrowana za pomocą usługi RMS. Te zaszyfrowane dane nie zależy od podpisanych danych dostępny za pośrednictwem [UserPolicy::GetSignedAppData](#classmip_1_1_user_policy_1a1c8a284d50adcac1a0a09316afa1d43e)
### <a name="mipappdatahashmap"></a>MIP::AppDataHashMap
Pobiera dane specyficzne dla aplikacji, który został podpisany.
A [UserPolicy](#classmip_1_1_user_policy) może zawierać słownika dane specyficzne dla aplikacji, który został podpisany przez usługę RMS. Ta podpisanych danych jest niezależna od zaszyfrowanych danych dostępny za pośrednictwem [UserPolicy::GetEncryptedAppData](#classmip_1_1_user_policy_1a610fbc799284ab0ce4354c0611ece0e8)
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Pobiera godzinę wygaśnięcia zasad.
#### <a name="returns"></a>Zwraca
Czas wygaśnięcia zasad
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Pobiera czy zasada używa przestarzałego algorytmów kryptograficznych (ECB) dla zgodności z poprzednimi wersjami.
#### <a name="returns"></a>Zwraca
Określa, czy używa zasad przestarzałe algorytmy kryptograficzne
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Pobiera czy zasada nie udziela uprawnienie "inspekcji wyodrębniania".
#### <a name="returns"></a>Zwraca
Określa, czy zasada nie udziela uprawnienie "inspekcji extract"
### <a name="getserializedpolicy"></a>GetSerializedPolicy
Serializować [UserPolicy](#classmip_1_1_user_policy) w licencji publikowania (PL)
#### <a name="returns"></a>Zwraca
Serializowany [UserPolicy](#classmip_1_1_user_policy)
### <a name="getimpl"></a>GetImpl
Implementacja klasy pochodnej pobiera wewnętrzne [UserPolicy](#classmip_1_1_user_policy).
#### <a name="returns"></a>Zwraca
Implementacja klasy pochodnej [UserPolicy](#classmip_1_1_user_policy) tylko wewnętrznie