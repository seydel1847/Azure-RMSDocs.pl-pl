# <a name="class-mipcustomaction"></a>Klasa mip::CustomAction 
[Akcja niestandardowa](#classmip_1_1_custom_action) to klasa ogólnego akcji, która przechwytuje wszystkie podrzędne właściwości działania jako zbiór właściwości. Element wywołujący jest odpowiedzialny zrozumieć znaczenia akcji.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny std::vector const < std::pair < std::string, std::string >> & GetProperties | Pobierz listę pary wartości klucza właściwości.
publicznych ActionType GetType
## <a name="members"></a>Elementy członkowskie
### <a name="getproperties"></a>GetProperties
Pobierz listę pary wartości klucza właściwości.
#### <a name="returns"></a>Zwraca
Lista par wartości klucza.
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](#classmip_1_1_action).
#### <a name="returns"></a>Zwraca
Typ pochodny akcji ActionType ta klasa podstawowa mogą być rzutowane na.