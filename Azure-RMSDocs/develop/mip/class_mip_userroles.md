# <a name="class-mipuserroles"></a>Klasa mip::UserRoles 
Reprezentuje grupę użytkowników i ról związanych z nimi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny UserRoles(const UserList& users, const RoleList& roles) MIP_EXPORT  |  [Roli użytkownika](#classmip_1_1_user_roles) konstruktora.
wbudowany publicznego const UserList & Users() const  |  Pobiera skojarzonej z zestawem role użytkowników.
wbudowany publicznego const RoleList & Roles() const  |  Pobiera role skojarzone z grupą użytkowników.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="userroles"></a>Roli użytkownika
[Roli użytkownika](#classmip_1_1_user_roles) konstruktora.
  
#### <a name="parameters"></a>Parametry
* Grupy użytkowników, którzy udostępniają ról użytkowników 
* role [ról](#classmip_1_1_roles) współużytkowane przez grupę użytkowników
  
### <a name="userlist"></a>UserList
Pobiera skojarzonej z zestawem role użytkowników.
  
#### <a name="returns"></a>Zwraca
Użytkownicy skojarzeni z zestawu ról
  
### <a name="rolelist"></a>RoleList
Pobiera role skojarzone z grupą użytkowników.
  
#### <a name="returns"></a>Zwraca
[Role](#classmip_1_1_roles) skojarzony z grupą użytkowników