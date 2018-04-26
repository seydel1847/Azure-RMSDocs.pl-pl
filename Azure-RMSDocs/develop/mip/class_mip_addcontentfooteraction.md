# <a name="class-mipaddcontentfooteraction"></a>Klasa mip::AddContentFooterAction 
Klasy akcji, która określa Dodawanie zawartości stopki do dokumentu.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny const std::string & GetUIElementName | Interfejs API służy do oznaczania element footer zawartości.
publiczny const std::string & GetText | Pobierz tekst, który spowodował przejście do stopki zawartości.
publiczny const std::string & GetFontName | Pobierz nazwę czcionki, używany do wyświetlania zawartości stopki.
publiczny int GetFontSize | Pobierz rozmiar czcionki używany do wyświetlania zawartości stopki.
publiczny const std::string & GetFontColor | Pobierz kolor czcionki używany do wyświetlania zawartości stopki.
publiczny ContentMarkAlignment GetAlignment | Pobierz wyrównanie stopki.
publiczny int GetMargin | Pobierz margines stopki od dołu.
publicznych ActionType GetType
## <a name="members"></a>Elementy członkowskie
### <a name="getuielementname"></a>GetUIElementName
Interfejs API służy do oznaczania element footer zawartości.
#### <a name="returns"></a>Zwraca
Nazwa, która powinna być używana dla elementu interfejsu użytkownika, która przechowuje zawartości stopki. Tej samej nazwie, zostaną zwrócone w [RemoveContentFooterAction](#classmip_1_1_remove_content_footer_action) w przypadku, gdy konieczne jest usunięcie stopki zawartości.
### <a name="gettext"></a>GetText
Pobierz tekst, który spowodował przejście do stopki zawartości.
#### <a name="returns"></a>Zwraca
Tekst stopki zawartości.
### <a name="getfontname"></a>GetFontName
Pobierz nazwę czcionki, używany do wyświetlania zawartości stopki.
#### <a name="returns"></a>Zwraca
Nazwa czcionki, wartość domyślna w przeciwnym razie określone przez zasady Calibri.
### <a name="getfontsize"></a>GetFontSize
Pobierz rozmiar czcionki używany do wyświetlania zawartości stopki.
#### <a name="returns"></a>Zwraca
rozmiar czcionki jako liczba całkowita.
### <a name="getfontcolor"></a>GetFontColor
Pobierz kolor czcionki używany do wyświetlania zawartości stopki.
#### <a name="returns"></a>Zwraca
Kolor czcionki jako ciąg (e.g."#000000").
### <a name="getalignment"></a>GetAlignment
Pobierz wyrównanie stopki.
#### <a name="returns"></a>Zwraca
Moduł wyliczający ContentMarkAlignment w lewo | PRAWA | CENTRUM. 
**Zobacz też**: ContentMarkAlignment
### <a name="getmargin"></a>GetMargin
Pobierz margines stopki od dołu.
#### <a name="returns"></a>Zwraca
Liczba całkowita represeting marginesy w dolnej części dokumentu (np. 10 mm).
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](#classmip_1_1_action).
#### <a name="returns"></a>Zwraca
Typ pochodny akcji ActionType ta klasa podstawowa mogą być rzutowane na.