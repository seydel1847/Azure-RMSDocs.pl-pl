# <a name="class-mipaddcontentfooteraction"></a>Klasa mip::AddContentFooterAction 
Klasy akcji, która określa Dodawanie zawartości stopki do dokumentu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny const std::string & GetUIElementName()  |  Interfejs API służy do oznaczania element footer zawartości.
 publiczny std::string const & GetText() const  |  Pobierz tekst, który spowodował przejście do stopki zawartości.
 publiczny std::string const & GetFontName() const  |  Pobierz nazwę czcionki, używany do wyświetlania zawartości stopki.
 publiczny int GetFontSize() const  |  Pobierz rozmiar czcionki używany do wyświetlania zawartości stopki.
 publiczny std::string const & GetFontColor() const  |  Pobierz kolor czcionki używany do wyświetlania zawartości stopki.
 publiczny ContentMarkAlignment GetAlignment() const  |  Pobierz wyrównanie stopki.
 publiczny int GetMargin() const  |  Pobierz margines stopki od dołu.
 publicznych ActionType GetType() const  |  Wybrany typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuielementname"></a>GetUIElementName
Interfejs API służy do oznaczania element footer zawartości.

  
**Zwraca**: nazwa, która powinna być używana dla elementu interfejsu użytkownika, która przechowuje zawartości stopki. Tej samej nazwie, zostaną zwrócone w [RemoveContentFooterAction](class_mip_removecontentfooteraction.md) w przypadku, gdy konieczne jest usunięcie stopki zawartości.
  
### <a name="gettext"></a>GetText
Pobierz tekst, który spowodował przejście do stopki zawartości.

  
**Zwraca**: tekst stopki zawartości.
  
### <a name="getfontname"></a>GetFontName
Pobierz nazwę czcionki, używany do wyświetlania zawartości stopki.

  
**Zwraca**: Nazwa czcionki, wartość domyślna, jeśli nie określone przez zasady Calibri.
  
### <a name="getfontsize"></a>GetFontSize
Pobierz rozmiar czcionki używany do wyświetlania zawartości stopki.

  
**Zwraca**: rozmiar czcionki w postaci liczby całkowitej.
  
### <a name="getfontcolor"></a>GetFontColor
Pobierz kolor czcionki używany do wyświetlania zawartości stopki.

  
**Zwraca**: kolor czcionki jako ciąg (e.g."#000000").
  
### <a name="getalignment"></a>GetAlignment
Pobierz wyrównanie stopki.

  
**Zwraca**: ContentMarkAlignment modułu wyliczającego, lewo | PRAWA | CENTRUM. 
**Zobacz też**: ContentMarkAlignment
  
### <a name="getmargin"></a>GetMargin
Pobierz margines stopki od dołu.

  
**Zwraca**: liczba całkowita represeting marginesy w dolnej części dokumentu (np. 10 mm).
  
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy podstawowej.