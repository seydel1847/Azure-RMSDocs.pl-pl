# <a name="class-miprmsexception"></a>Klasa mip::RMSException 
Wyjątek podstawowej usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego RMSException (stała typu ExceptionTypes, const int, const std::string & błędu wiadomości)  |  [RMSException](#classmip_1_1_r_m_s_exception) konstruktora.
wbudowany publicznego RMSException (const ExceptionTypes, const int błąd typu, const char * const & wiadomości)  |  [RMSException](#classmip_1_1_r_m_s_exception) konstruktora.
wbudowany publiczny wirtualny const char * what() const  |  Pobiera komunikat o wyjątku.
wbudowany publiczny wirtualny ExceptionTypes type() const  |  Pobiera typ wyjątku.
wbudowany publiczny wirtualny int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsexception"></a>RMSException
[RMSException](#classmip_1_1_r_m_s_exception) konstruktora.
  
#### <a name="parameters"></a>Parametry
* Wpisz typ wyjątku 
* Błąd [błąd](#classmip_1_1_error) kodu 
* komunikat o wyjątku wiadomości
  
### <a name="rmsexception"></a>RMSException
[RMSException](#classmip_1_1_r_m_s_exception) konstruktora.
  
#### <a name="parameters"></a>Parametry
* Wpisz typ wyjątku 
* Błąd [błąd](#classmip_1_1_error) kodu 
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