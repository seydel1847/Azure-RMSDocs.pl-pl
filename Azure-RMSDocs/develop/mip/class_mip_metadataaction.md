# <a name="class-mipmetadataaction"></a>Klasa mip::MetadataAction 
[Akcji](#classmip_1_1_action) przeznaczone, która określa, jakie informacje należy dodać do zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny std::vector const < std::string > & GetMetadataToRemove() const  |  Pobierz listę nazw metadanych, które muszą zostać usunięte z zawartości.
publiczny std::vector const < std::pair < std::string, std::string >> & GetMetadataToAdd() const  |  Pobierz listę metadanych jako pary wartości klucza. Meta-data musi mają zostać dodane do zawartości metadanych.
publicznych ActionType GetType() const  |  Wybrany typ [akcji](#classmip_1_1_action).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
Pobierz listę nazw metadanych, które muszą zostać usunięte z zawartości.
  
#### <a name="returns"></a>Zwraca
Wektor ciągów w celu usunięcia. Usuwanie meta-data powinno być wykonywane przed dodaniem metadanych.
  
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
Pobierz listę metadanych jako pary wartości klucza. Meta-data musi mają zostać dodane do zawartości metadanych.
  
#### <a name="returns"></a>Zwraca
Const std::vector < std::pair < std::string, std::string >> & Usuwanie meta danych powinno być wykonywane przed dodaniem metadanych.
  
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](#classmip_1_1_action).
  
#### <a name="returns"></a>Zwraca
Typ pochodny akcji ActionType ta klasa podstawowa mogą być rzutowane na.