# <a name="class-mipgetuserpolicyresult"></a>Klasa mip::GetUserPolicyResult 
W tym artykule opisano wyniki nabycia żądania zasad użytkownika.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny GetUserPolicyResultStatus GetResultStatus()  |  Pobiera stan żądania nabycia zasad.
publiczny std::shared_ptr < std::string > GetReferrer()  |  Pobiera adres refererrer zasad.
publiczny std::shared_ptr<UserPolicy> GetPolicy()  |  Pobiera [UserPolicy](class_mip_userpolicy.md) wystąpienia.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuserpolicyresultstatus"></a>GetUserPolicyResultStatus
Pobiera stan żądania nabycia zasad.

  
**Zwraca**: stan żądania nabycia zasad
  
### <a name="getreferrer"></a>GetReferrer
Pobiera adres refererrer zasad.

  
**Zwraca**: adres Referrerer zasad odwołania jest identyfikatorem URI, który mogą być wyświetlane po nabycia zasad nie powiodło się, który zawiera informacje na temat jak użytkownik może uzyskać uprawnienia do uzyskania dostępu do zawartości.
  
### <a name="userpolicy"></a>UserPolicy
Pobiera [UserPolicy](class_mip_userpolicy.md) wystąpienia.

  
**Zwraca**: [UserPolicy](class_mip_userpolicy.md) wystąpienie, jeśli nabycia zakończyło się pomyślnie, else nullptr