# <a name="class-mipmetadataaction"></a>Klasa mip::MetadataAction 
[Akcji](class_mip_action.md) przeznaczone, która określa, jakie informacje należy dodać do zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny std::vector const < std::string > & GetMetadataToRemove() const  |  Pobierz listę nazw metadanych, które muszą zostać usunięte z zawartości.
publiczny std::vector const < std::pair < std::string, std::string >> & GetMetadataToAdd() const  |  Pobierz listę metadanych jako pary wartości klucza. Meta-data musi mają zostać dodane do zawartości metadanych.
 publicznych ActionType GetType() const  |  Wybrany typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
Pobierz listę nazw metadanych, które muszą zostać usunięte z zawartości.

  
**Zwraca**: wektor ciągów w celu usunięcia. Usuwanie meta-data powinno być wykonywane przed dodaniem metadanych.
  
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
Pobierz listę metadanych jako pary wartości klucza. Meta-data musi mają zostać dodane do zawartości metadanych.

  
**Zwraca**: Const std::vector < std::pair < std::string, std::string >> & Usuwanie meta danych należy zrobić przed dodaniem metadanych.
  
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy podstawowej.