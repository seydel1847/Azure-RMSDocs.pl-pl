# <a name="class-miplabel"></a>Klasa mip::Label 
Abstrakcja dla jednej etykiety Microsoft Information Protection.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny const std::string & GetId | Pobierz etykiety identyfikatora.
publiczny const std::string & GetName | Pobierz nazwę etykiety.
publiczny const std::string & GetDescription | Pobiera opis etykiety.
publiczny const std::string & GetColor | Pobierz kolor, który ma być wyświetlana etykieta.
publiczny const std::string & GetOrder | Pobiera kolejność etykiety.
publiczny const std::string & GetTooltip | Pobiera opis etykietka narzędzia etykiety.
publiczny bool IsActive | Pobiera wartość logiczną sygnalizowania, jeśli etykieta jest aktywny.
publiczny std::weak_ptr < Etykieta > GetParent | Pobierz etykiecie nadrzędnej.
publiczny std::vector const < std::shared_ptr < Etykieta >> & GetChildren | Pobierz elementy podrzędne etykiety bieżącej etykiety.
## <a name="members"></a>Elementy członkowskie
### <a name="getid"></a>GetId
Pobierz etykiety identyfikatora.
#### <a name="returns"></a>Zwraca
Identyfikator etykiety.
### <a name="getname"></a>GetName
Pobierz nazwę etykiety.
#### <a name="returns"></a>Zwraca
Nazwa etykiety.
### <a name="getdescription"></a>GetDescription
Pobiera opis etykiety.
#### <a name="returns"></a>Zwraca
Opis etykiety.
### <a name="getcolor"></a>GetColor
Pobierz kolor, który ma być wyświetlana etykieta.
#### <a name="returns"></a>Zwraca
wartość koloru format ciągu. "#RRGGBB" których każdy rekord Zasobu, GG, bb jest szesnastkowa 0-f.
### <a name="getorder"></a>GetOrder
Pobiera kolejność etykiety.
#### <a name="returns"></a>Zwraca
wartość liczbowa przypisany jako ciąg.
### <a name="gettooltip"></a>GetTooltip
Pobiera opis etykietka narzędzia etykiety.
#### <a name="returns"></a>Zwraca
ciąg etykietki narzędzia.
### <a name="isactive"></a>IsActive
Pobiera wartość logiczną sygnalizowania, jeśli etykieta jest aktywny.
Można zastosować tylko aktywne etykiety. Nieaktywne etykiet nie można zastosować i służą tylko do wyświetlania. 
#### <a name="returns"></a>Zwraca
wartość true, jeśli etykieta jest aktywne, w przeciwnym razie wartość false.
### <a name="label"></a>Etykieta
Pobierz etykiecie nadrzędnej.
#### <a name="returns"></a>Zwraca
etykiety słabe wskaźnika do elementu nadrzędnego, jeśli istnieje else pustego wskaźnika.
### <a name="label"></a>Etykieta
Pobierz elementy podrzędne etykiety bieżącej etykiety.
#### <a name="returns"></a>Zwraca
Wektor udostępnionego wskaźników do etykiet.