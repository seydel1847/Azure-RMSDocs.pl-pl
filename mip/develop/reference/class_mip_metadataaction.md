# <a name="class-mipmetadataaction"></a>Klasa mip::MetadataAction 
[Akcji](class_mip_action.md) dodająca informacji o metadanych do zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::vector const < std::string > & GetMetadataToRemove() const  |  Pobierz listę nazw metadanych, które należy odłączyć od zawartości.
publiczne std::vector const < std::pair < std::string, std::string >> & GetMetadataToAdd() const  |  Uzyskaj listę metadanych jako pary klucz-wartość. Metadane musi zostać dodane do metadanych zawartości.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
Pobierz listę nazw metadanych, które należy odłączyć od zawartości.

  
**Zwraca**: wektor ciągów w celu usunięcia. Usuwanie metadanych powinno odbywać się przed dodaniem metadanych.
  
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
Uzyskaj listę metadanych jako pary klucz-wartość. Metadane musi zostać dodane do metadanych zawartości.

  
**Zwraca**: Const std::vector < std::pair < std::string, std::string >> & Usuwanie metadanych ma być przeprowadzane przed dodaniem metadanych.
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.