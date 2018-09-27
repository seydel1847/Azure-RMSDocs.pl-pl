# <a name="class-mipgetuserpolicyresult"></a>Klasa mip::GetUserPolicyResult 
W tym artykule opisano wyniki nabycia żądania zasad użytkownika.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne GetUserPolicyResultStatus GetResultStatus()  |  Pobiera stan żądania nabycia zasad.
publiczne std::shared_ptr < std::string > GetReferrer()  |  Pobiera adres refererrer zasad.
publiczne std::shared_ptr<UserPolicy> GetPolicy()  |  Pobiera [UserPolicy](class_mip_userpolicy.md) wystąpienia.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuserpolicyresultstatus"></a>GetUserPolicyResultStatus
Pobiera stan żądania nabycia zasad.

  
**Zwraca**: stan żądania nabycia zasad
  
### <a name="getreferrer"></a>GetReferrer
Pobiera adres refererrer zasad.

  
**Zwraca**: adres Referrerer zasad odwołującym jest identyfikator URI, które mogą być wyświetlane podczas pozyskiwania zasad nie powiodło się, który zawiera informacje na temat sposobu ten użytkownik może uzyskać uprawnienia dostępu do zawartości użytkownika.
  
### <a name="userpolicy"></a>UserPolicy
Pobiera [UserPolicy](class_mip_userpolicy.md) wystąpienia.

  
**Zwraca**: [UserPolicy](class_mip_userpolicy.md) wystąpienie, jeśli nabycia zakończyło się pomyślnie, else nullptr