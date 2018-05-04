# <a name="class-miprmsstreamexception"></a>Klasa mip::RMSStreamException 
Wyjątek strumienia usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego RMSStreamException (const std::string & wiadomości)  |  [RMSStreamException](#classmip_1_1_r_m_s_stream_exception) konstruktora.
wbudowany publicznego RMSStreamException (const char * const & wiadomości)  |  [RMSStreamException](#classmip_1_1_r_m_s_stream_exception) konstruktora.
wbudowany publiczny wirtualny const char * what() const  |  Pobiera komunikat o wyjątku.
wbudowany publiczny wirtualny ExceptionTypes type() const  |  Pobiera typ wyjątku.
wbudowany publiczny wirtualny int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](#classmip_1_1_r_m_s_stream_exception) konstruktora.
  
#### <a name="parameters"></a>Parametry
* komunikat o wyjątku wiadomości
  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](#classmip_1_1_r_m_s_stream_exception) konstruktora.
  
#### <a name="parameters"></a>Parametry
* komunikat o wyjątku wiadomości
  
### <a name="what"></a>Co
Pobiera komunikat o wyjątku.
  
#### <a name="returns"></a>Zwraca
Komunikat o wyjątku
  
### <a name="exceptiontypes"></a>ExceptionTypes
Pobiera typ wyjątku.
  
#### <a name="returns"></a>Zwraca
Typ wyjątku
  
### <a name="error"></a>Błąd
Pobiera kod błędu.
  
#### <a name="returns"></a>Zwraca
[Błąd](#classmip_1_1_error) kodu