# <a name="class-mipcontentlabel"></a>Klasa mip::ContentLabel 
Abstrakcja etykiety Microsoft Information Protection, która jest stosowana do elementu zawartości, zwykle dokumentu.
Oprócz informacji etykiety przechowuje właściwości dla określonej etykiety zastosowane.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny std::string const & GetCreationTime() const  |  Pobrać czasu utworzenia etykiety.
 publiczny AssignmentMethod GetAssignmentMethod() const  |  GET, Metoda przydziału etykiety.
publiczny std::shared_ptr<Label> GetLabel() const  |  Pobierz obiekt rzeczywistych stosowane do zawartości.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getcreationtime"></a>GetCreationTime
Pobrać czasu utworzenia etykiety.

  
**Zwraca**: czas utworzenia jako ciąg gmt.
  
### <a name="getassignmentmethod"></a>GetAssignmentMethod
GET, Metoda przydziału etykiety.

  
**Zwraca**: AssignmentMethod STANDARD | UPRZYWILEJOWANE | Automatycznie. 
**Zobacz też**: mip::AssignmentMethod
  
### <a name="label"></a>Etykieta
Pobierz obiekt rzeczywistych stosowane do zawartości.

  
**Zwraca**: obiektu etykiety stosowane do zawartości. 
**Zobacz też**: [mip::Label](class_mip_label.md)