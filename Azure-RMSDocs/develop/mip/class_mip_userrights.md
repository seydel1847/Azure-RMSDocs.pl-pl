# <a name="class-mipuserrights"></a>Klasa mip::UserRights 
Reprezentuje grupę użytkowników i praw skojarzonych z nimi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny UserRights (const UserList & użytkowników, const RightList & praw)  |  [UserRights](class_mip_userrights.md) konstruktora.
 publiczny UserList const & Users() const  |  Pobiera użytkownicy skojarzeni z zestaw praw.
 publiczny RightList const & Rights() const  |  Pobiera praw skojarzonych z grupy użytkowników.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="userrights"></a>UserRights
[UserRights](class_mip_userrights.md) konstruktora.

Parametry:  
* **Użytkownicy**: grupy użytkowników, które mają te same prawa 


* **prawa**: prawa wspólne grupy użytkowników


  
### <a name="userlist"></a>UserList
Pobiera użytkownicy skojarzeni z zestaw praw.

  
**Zwraca**: użytkownicy skojarzeni z tym zestawem uprawnień
  
### <a name="rightlist"></a>RightList
Pobiera praw skojarzonych z grupy użytkowników.

  
**Zwraca**: prawa skojarzony z grupą użytkowników