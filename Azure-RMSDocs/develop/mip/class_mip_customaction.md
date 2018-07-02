# <a name="class-mipcustomaction"></a>Klasa mip::CustomAction 
[Akcja niestandardowa](class_mip_customaction.md) jest klasą Akcja ogólna, która przechwytuje wszystkie właściwości podrzędnych działania jako zbiór właściwości. Obiekt wywołujący odpowiada może zrozumieć znaczenie akcji.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::vector const < std::pair < std::string, std::string >> & GetProperties() const  |  Pobieranie listy pary wartości klucza właściwości.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getproperties"></a>Getproperties —
Pobieranie listy pary wartości klucza właściwości.

  
**Zwraca**: Lista pary wartości klucza.
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.