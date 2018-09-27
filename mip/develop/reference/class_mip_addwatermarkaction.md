# <a name="class-mipaddwatermarkaction"></a>Klasa mip::AddWatermarkAction 
Klasa akcji, która określa Dodawanie znaku wodnego.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetUIElementName()  |  Interfejs API jest używany do oznaczania elementu znaku wodnego.
 publiczne WatermarkLayout GetLayout() const  |  Interfejs API jest używane do uzyskania układ znacznik limitu górnego.
 publiczne std::string const & GetText() const  |  Pobierz tekst, który jest przeznaczony do przejść do znaku wodnego.
 publiczne std::string const & GetFontName() const  |  Pobierz nazwę czcionki używany do wyświetlania znaku wodnego.
 publiczne int GetFontSize() const  |  Pobierz rozmiar czcionki używany do wyświetlania znaku wodnego.
 publiczne std::string const & GetFontColor() const  |  Pobierz kolor czcionki używany do wyświetlania znaku wodnego.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuielementname"></a>GetUIElementName
Interfejs API jest używany do oznaczania elementu znaku wodnego.

  
**Zwraca**: nazwa, która powinna być używana dla elementu interfejsu użytkownika, który zawiera znaku wodnego. Tej samej nazwie w RemoveWatermarkingAction zostaną zwrócone, w przypadku, gdy znaku wodnego musi zostać usunięte.
  
### <a name="getlayout"></a>GetLayout
Interfejs API jest używane do uzyskania układ znacznik limitu górnego.

  
**Zwraca**: WatermarkLayout watermarking układu w postaci th wyliczenia w poziomie | PO PRZEKĄTNEJ. ,
  
### <a name="gettext"></a>GetText
Pobierz tekst, który jest przeznaczony do przejść do znaku wodnego.

  
**Zwraca**: zawartości tekst nagłówka.
  
### <a name="getfontname"></a>GetFontName
Pobierz nazwę czcionki używany do wyświetlania znaku wodnego.

  
**Zwraca**: Nazwa czcionki. Wartość domyślna to Calibri, jeśli nic nie jest ustawiony przez zasady.
  
### <a name="getfontsize"></a>GetFontSize
Pobierz rozmiar czcionki używany do wyświetlania znaku wodnego.

  
**Zwraca**: rozmiar czcionki jako liczba całkowita.
  
### <a name="getfontcolor"></a>GetFontColor
Pobierz kolor czcionki używany do wyświetlania znaku wodnego.

  
**Zwraca**: kolor czcionki jako ciąg (e.g."#000000").
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.