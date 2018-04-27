# <a name="class-mipaddwatermarkaction"></a>Klasa mip::AddWatermarkAction 
Klasa akcji, która określa dodanie znaku wodnego.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny const std::string & GetUIElementName | Interfejs API służy do oznaczania elementu znaku wodnego.
publiczny WatermarkLayout GetLayout | Interfejs API używany do pobierania układu znacznik limitu górnego.
publiczny const std::string & GetText | Pobierz tekst, który spowodował, aby przejść do zawartości nagłówka.
publiczny const std::string & GetFontName | Pobierz nazwę czcionki, używany do wyświetlania zawartości nagłówka.
publiczny int GetFontSize | Pobierz rozmiar czcionki używany do wyświetlania zawartości nagłówka.
publiczny const std::string & GetFontColor | Pobierz kolor czcionki używany do wyświetlania zawartości nagłówka.
publicznych ActionType GetType
## <a name="members"></a>Elementy członkowskie
### <a name="getuielementname"></a>GetUIElementName
Interfejs API służy do oznaczania elementu znaku wodnego.
#### <a name="returns"></a>Zwraca
Nazwa, która powinna być używana dla elementu interfejsu użytkownika, który zawiera znak wodny. Tej samej nazwie w RemoveWatermarkingAction zostaną zwrócone, w przypadku, gdy konieczne jest usunięcie znaku wodnego.
### <a name="getlayout"></a>GetLayout
Interfejs API używany do pobierania układu znacznik limitu górnego.
#### <a name="returns"></a>Zwraca
WatermarkLayout watermarking układu w postaci th wyliczenia POZIOMYM | PRZEKĄTNEJ. ,
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
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](#classmip_1_1_action).
#### <a name="returns"></a>Zwraca
Typ pochodny akcji ActionType ta klasa podstawowa mogą być rzutowane na.