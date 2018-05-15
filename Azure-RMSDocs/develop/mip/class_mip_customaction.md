# <a name="class-mipcustomaction"></a>Klasa mip::CustomAction 
[Akcja niestandardowa](class_mip_customaction.md) to klasa ogólnego akcji, która przechwytuje wszystkie podrzędne właściwości działania jako zbiór właściwości. Element wywołujący jest odpowiedzialny zrozumieć znaczenia akcji.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny std::vector const < std::pair < std::string, std::string >> & GetProperties() const  |  Pobierz listę pary wartości klucza właściwości.
 publicznych ActionType GetType() const  |  Wybrany typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getproperties"></a>GetProperties
Pobierz listę pary wartości klucza właściwości.

  
**Zwraca**: Lista pary wartości klucza.
  
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy podstawowej.