# <a name="class-miplabel"></a>Klasa mip::Label 
Abstrakcyjną dla pojedynczej etykiecie Microsoft Information Protection.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetId() const  |  Pobierz etykietę identyfikatora.
 publiczne std::string const & GetName() const  |  Pobierz nazwę etykiety.
 publiczne std::string const & GetDescription() const  |  Pobierz opis etykiety.
 publiczne std::string const & GetColor() const  |  Pobierz kolor ma być wyświetlana etykieta.
 publiczne int GetSensitivity() const  |  Uzyskaj czułości etykiety.
 publiczne std::string const & GetTooltip() const  |  Pobierz opis etykietki narzędzia etykiety.
 publiczne bool IsActive() const  |  Pobiera wartość logiczną sygnalizowanie, jeśli etykieta jest aktywny.
publiczne std::weak_ptr<Label> GetParent() const  |  Pobierz etykietę nadrzędną.
publiczne std::vector const < std::shared_ptr<Label>> & GetChildren() const  |  Pobierz elementy podrzędne etykiety bieżącą etykietę.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getid"></a>Getid —
Pobierz etykietę identyfikatora.

  
**Zwraca**: identyfikator etykiety.
  
### <a name="getname"></a>Getname —
Pobierz nazwę etykiety.

  
**Zwraca**: Nazwa etykiety.
  
### <a name="getdescription"></a>GetDescription
Pobierz opis etykiety.

  
**Zwraca**: Opis etykiety.
  
### <a name="getcolor"></a>Getcolor —
Pobierz kolor ma być wyświetlana etykieta.

  
**Zwraca**: format ciągu wartości koloru. "#RRGGBB" gdzie każdy rekord Zasobu, GG, BB jest szesnastkowe 0-f.
  
### <a name="getsensitivity"></a>GetSensitivity
Uzyskaj czułości etykiety.

  
**Zwraca**: wartość liczbową. Wyższa wartość określa czułość wyższy.
  
### <a name="gettooltip"></a>GetTooltip
Pobierz opis etykietki narzędzia etykiety.

  
**Zwraca**: ciąg etykietki narzędzia.
  
### <a name="isactive"></a>IsActive
Pobiera wartość logiczną sygnalizowanie, jeśli etykieta jest aktywny.
Mogą być stosowane tylko aktywne etykiety. Nieaktywne etykiet nie można zastosować, a są używane tylko w celach wyświetlania. 

  
**Zwraca**: wartość True, jeśli etykieta jest aktywne, w przeciwnym razie wartość false.
  
### <a name="label"></a>Etykieta
Pobierz etykietę nadrzędną.

  
**Zwraca**: Etykieta słaby wskaźnik do elementu nadrzędnego, jeśli istnieje inne pustego wskaźnika.
  
### <a name="label"></a>Etykieta
Pobierz elementy podrzędne etykiety bieżącą etykietę.

  
**Zwraca**: wektor udostępnionego wskaźników do etykiety.