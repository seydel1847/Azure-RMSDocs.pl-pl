# <a name="class-mipuserroles"></a>Klasa mip::UserRoles 
Reprezentuje grupę użytkowników i ról związanych z nimi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny UserRoles(const UserList& users, const RoleList& roles) MIP_EXPORT  |  [Roli użytkownika](class_mip_userroles.md) konstruktora.
 publiczny UserList const & Users() const  |  Pobiera skojarzonej z zestawem role użytkowników.
 publiczny RoleList const & Roles() const  |  Pobiera role skojarzone z grupą użytkowników.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="userroles"></a>Roli użytkownika
[Roli użytkownika](class_mip_userroles.md) konstruktora.

Parametry:  
* **Użytkownicy**: grupy użytkowników, którzy udostępniają ról 


* **role**: [ról](class_mip_roles.md) współużytkowane przez grupę użytkowników


  
### <a name="userlist"></a>UserList
Pobiera skojarzonej z zestawem role użytkowników.

  
**Zwraca**: użytkownicy skojarzeni z zestawu ról
  
### <a name="rolelist"></a>RoleList
Pobiera role skojarzone z grupą użytkowników.

  
**Zwraca**: [ról](class_mip_roles.md) skojarzony z grupą użytkowników