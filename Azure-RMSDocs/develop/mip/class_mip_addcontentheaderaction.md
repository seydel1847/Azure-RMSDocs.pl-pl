# <a name="class-mipaddcontentheaderaction"></a>Klasa mip::AddContentHeaderAction 
Klasa akcji, która określa Dodawanie nagłówka zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny const std::string & GetUIElementName()  |  Interfejs API służy do oznaczania elementu zawartości nagłówka.
 publiczny std::string const & GetText() const  |  Pobierz tekst, który spowodował, aby przejść do zawartości nagłówka.
 publiczny std::string const & GetFontName() const  |  Pobierz nazwę czcionki, używany do wyświetlania zawartości nagłówka.
 publiczny int GetFontSize() const  |  Pobierz rozmiar czcionki używany do wyświetlania zawartości nagłówka.
 publiczny std::string const & GetFontColor() const  |  Pobierz kolor czcionki używany do wyświetlania zawartości nagłówka.
 publiczny ContentMarkAlignment GetAlignment() const  |  Pobierz wyrównanie nagłówka.
 publiczny int GetMargin() const  |  Pobierz margines nagłówka od dołu.
 publicznych ActionType GetType() const  |  Wybrany typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuielementname"></a>GetUIElementName
Interfejs API służy do oznaczania elementu zawartości nagłówka.

  
**Zwraca**: nazwa, która powinna być używana dla elementu interfejsu użytkownika, która przechowuje zawartości nagłówka. Tej samej nazwie, zostaną zwrócone w [RemoveContentHeaderAction](class_mip_removecontentheaderaction.md) w przypadku, gdy konieczne jest usunięcie zawartości nagłówka.
  
### <a name="gettext"></a>GetText
Pobierz tekst, który spowodował, aby przejść do zawartości nagłówka.

  
**Zwraca**: tekst nagłówka zawartości.
  
### <a name="getfontname"></a>GetFontName
Pobierz nazwę czcionki, używany do wyświetlania zawartości nagłówka.

  
**Zwraca**: Nazwa czcionki, wartość domyślna, jeśli nie określone przez zasady Calibri.
  
### <a name="getfontsize"></a>GetFontSize
Pobierz rozmiar czcionki używany do wyświetlania zawartości nagłówka.

  
**Zwraca**: rozmiar czcionki w postaci liczby całkowitej.
  
### <a name="getfontcolor"></a>GetFontColor
Pobierz kolor czcionki używany do wyświetlania zawartości nagłówka.

  
**Zwraca**: kolor czcionki jako ciąg (e.g."#000000").
  
### <a name="getalignment"></a>GetAlignment
Pobierz wyrównanie nagłówka.

  
**Zwraca**: ContentMarkAlignment modułu wyliczającego, lewo | PRAWA | CENTRUM. 
**Zobacz też**: ContentMarkAlignment
  
### <a name="getmargin"></a>GetMargin
Pobierz margines nagłówka od dołu.

  
**Zwraca**: liczba całkowita represeting marginesy w dolnej części dokumentu (np. 10 mm).
  
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy podstawowej.