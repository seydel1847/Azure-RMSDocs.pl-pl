# <a name="class-mipaddcontentheaderaction"></a>Klasa mip::AddContentHeaderAction 
Klasa akcji, która określa Dodawanie nagłówka zawartości.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny const std::string & GetUIElementName | Interfejs API służy do oznaczania elementu zawartości nagłówka.
publiczny const std::string & GetText | Pobierz tekst, który spowodował, aby przejść do zawartości nagłówka.
publiczny const std::string & GetFontName | Pobierz nazwę czcionki, używany do wyświetlania zawartości nagłówka.
publiczny int GetFontSize | Pobierz rozmiar czcionki używany do wyświetlania zawartości nagłówka.
publiczny const std::string & GetFontColor | Pobierz kolor czcionki używany do wyświetlania zawartości nagłówka.
publiczny ContentMarkAlignment GetAlignment | Pobierz wyrównanie nagłówka.
publiczny int GetMargin | Pobierz margines nagłówka od dołu.
publicznych ActionType GetType
## <a name="members"></a>Elementy członkowskie
### <a name="getuielementname"></a>GetUIElementName
Interfejs API służy do oznaczania elementu zawartości nagłówka.
#### <a name="returns"></a>Zwraca
Nazwa, która powinna być używana dla elementu interfejsu użytkownika, która przechowuje zawartości nagłówka. Tej samej nazwie, zostaną zwrócone w [RemoveContentHeaderAction](#classmip_1_1_remove_content_header_action) w przypadku, gdy konieczne jest usunięcie zawartości nagłówka.
### <a name="gettext"></a>GetText
Pobierz tekst, który spowodował, aby przejść do zawartości nagłówka.
#### <a name="returns"></a>Zwraca
tekst nagłówka zawartości.
### <a name="getfontname"></a>GetFontName
Pobierz nazwę czcionki, używany do wyświetlania zawartości nagłówka.
#### <a name="returns"></a>Zwraca
Nazwa czcionki, wartość domyślna w przeciwnym razie określone przez zasady Calibri.
### <a name="getfontsize"></a>GetFontSize
Pobierz rozmiar czcionki używany do wyświetlania zawartości nagłówka.
#### <a name="returns"></a>Zwraca
rozmiar czcionki jako liczba całkowita.
### <a name="getfontcolor"></a>GetFontColor
Pobierz kolor czcionki używany do wyświetlania zawartości nagłówka.
#### <a name="returns"></a>Zwraca
Kolor czcionki jako ciąg (e.g."#000000").
### <a name="getalignment"></a>GetAlignment
Pobierz wyrównanie nagłówka.
#### <a name="returns"></a>Zwraca
Moduł wyliczający ContentMarkAlignment w lewo | PRAWA | CENTRUM. 
**Zobacz też**: ContentMarkAlignment
### <a name="getmargin"></a>GetMargin
Pobierz margines nagłówka od dołu.
#### <a name="returns"></a>Zwraca
Liczba całkowita represeting marginesy w dolnej części dokumentu (np. 10 mm).
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](#classmip_1_1_action).
#### <a name="returns"></a>Zwraca
Typ pochodny akcji ActionType ta klasa podstawowa mogą być rzutowane na.