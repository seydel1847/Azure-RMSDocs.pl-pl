# <a name="class-mipgetuserpolicyresult"></a>Klasa mip::GetUserPolicyResult 
W tym artykule opisano wyniki nabycia żądania zasad użytkownika.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny GetUserPolicyResultStatus GetResultStatus()  |  Pobiera stan żądania nabycia zasad.
publiczny std::shared_ptr < std::string > GetReferrer()  |  Pobiera adres odwołania zasad.
publiczny std::shared_ptr<UserPolicy> GetPolicy()  |  Pobiera [UserPolicy](#classmip_1_1_user_policy) wystąpienia.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuserpolicyresultstatus"></a>GetUserPolicyResultStatus
Pobiera stan żądania nabycia zasad.
  
#### <a name="returns"></a>Zwraca
Stan żądania nabycia zasad
  
### <a name="getreferrer"></a>GetReferrer
Pobiera adres odwołania zasad.
  
#### <a name="returns"></a>Zwraca
Adres odwołania zasad odwołania jest identyfikatorem URI, który mogą być wyświetlane po nabycia zasad nie powiodło się, który zawiera informacje na temat jak użytkownik może uzyskać uprawnienia do uzyskania dostępu do zawartości.
  
### <a name="userpolicy"></a>UserPolicy
Pobiera [UserPolicy](#classmip_1_1_user_policy) wystąpienia.
  
#### <a name="returns"></a>Zwraca
[UserPolicy](#classmip_1_1_user_policy) wystąpienia, jeśli nabycia zakończyło się powodzeniem, w przeciwnym razie `nullptr`.