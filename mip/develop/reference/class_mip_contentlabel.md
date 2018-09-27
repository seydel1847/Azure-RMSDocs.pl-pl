# <a name="class-mipcontentlabel"></a>Klasa mip::ContentLabel 
Abstrakcję etykietę Microsoft Information Protection, która jest stosowana do fragmentu zawartości, zazwyczaj dokumentu.
Oprócz informacji etykiety przechowuje właściwości dla określonego przydzieloną etykietę.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetCreationTime() const  |  Pobrać czasu utworzenia etykiety.
 publiczne AssignmentMethod GetAssignmentMethod() const  |  Uzyskaj metodę przypisywania etykiety.
publiczne std::vector const < std::pair < std::string, std::string >> & GetExtendedProperties() const  |  Zwraca informację określającą, czy ochrona została zastosowana etykieta.
 publiczne bool IsProtectionAppliedFromLabel() const  |  Zwraca informację określającą, czy ochrona została zastosowana etykieta.
publiczne std::shared_ptr<Label> GetLabel() const  |  Pobierz obiekt rzeczywistych stosowane wobec zawartości.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getcreationtime"></a>GetCreationTime
Pobrać czasu utworzenia etykiety.

  
**Zwraca**: godzina utworzenia jako ciąg gmt.
  
### <a name="getassignmentmethod"></a>GetAssignmentMethod
Uzyskaj metodę przypisywania etykiety.

  
**Zwraca**: AssignmentMethod STANDARD | UPRZYWILEJOWANE | Automatycznie. 
  
**Zobacz też**: mip::AssignmentMethod
  
### <a name="getextendedproperties"></a>GetExtendedProperties
Zwraca informację określającą, czy ochrona została zastosowana etykieta.

  
**Zwraca**: wartość True, jeśli istnieje szablonu ochrony, a był za pomocą tej etykiety wartość false.
  
### <a name="isprotectionappliedfromlabel"></a>IsProtectionAppliedFromLabel
Zwraca informację określającą, czy ochrona została zastosowana etykieta.

  
**Zwraca**: wartość True, jeśli istnieje szablonu ochrony, a był za pomocą tej etykiety wartość false.
  
### <a name="label"></a>Etykieta
Pobierz obiekt rzeczywistych stosowane wobec zawartości.

  
**Zwraca**: obiekt etykiety zastosowane wobec zawartości. 
  
**Zobacz też**: [mip::Label](class_mip_label.md)