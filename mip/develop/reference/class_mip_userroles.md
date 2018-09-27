# <a name="class-mipuserroles"></a>Klasa mip::UserRoles 
Reprezentuje grupę użytkowników i ról związanych z nimi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne UserRoles (const std::vector < std::string > & użytkownicy, const std::vector < std::string > & role)  |  [UserRoles](class_mip_userroles.md) konstruktora.
publiczne std::vector const < std::string > & Users() const  |  Pobiera skojarzony zestaw ról użytkowników.
publiczne std::vector const < std::string > & Roles() const  |  Pobiera role skojarzone z grupą użytkowników.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="userroles"></a>UserRoles
[UserRoles](class_mip_userroles.md) konstruktora.

Parametry:  
* **Użytkownicy**: grupy użytkowników, którzy udostępniają te same role 


* **role**: role współużytkowane przez grupę użytkowników


  
### <a name="users"></a>Users
Pobiera skojarzony zestaw ról użytkowników.

  
**Zwraca**: użytkownicy skojarzeni z zestawu ról
  
### <a name="roles"></a>Role
Pobiera role skojarzone z grupą użytkowników.

  
**Zwraca**: role skojarzone z grupą użytkowników