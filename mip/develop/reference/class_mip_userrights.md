# <a name="class-mipuserrights"></a>Klasa mip::UserRights 
Reprezentuje grupę użytkowników i praw skojarzonych z nimi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne UserRights (const std::vector < std::string > & użytkowników, const std::vector < std::string > i prawa)  |  [UserRights](class_mip_userrights.md) konstruktora.
publiczne std::vector const < std::string > & Users() const  |  Pobiera użytkowników związanych z zestawem uprawnień.
publiczne std::vector const < std::string > & Rights() const  |  Pobiera prawa powiązane z grupą użytkowników.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="userrights"></a>UserRights
[UserRights](class_mip_userrights.md) konstruktora.

Parametry:  
* **Użytkownicy**: grupy użytkowników, którzy udostępniają te same prawa 


* **prawa**: prawa wspólne grupy użytkowników


  
### <a name="users"></a>Users
Pobiera użytkowników związanych z zestawem uprawnień.

  
**Zwraca**: użytkownicy skojarzeni z zestawem uprawnień
  
### <a name="rights"></a>Prawa
Pobiera prawa powiązane z grupą użytkowników.

  
**Zwraca**: praw skojarzonych z grupą użytkowników