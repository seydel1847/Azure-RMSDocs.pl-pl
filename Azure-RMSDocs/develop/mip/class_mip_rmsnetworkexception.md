# <a name="class-miprmsnetworkexception"></a>Klasa mip::RMSNetworkException 
Wyjątek sieci usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego RMSNetworkException (const std::string & wiadomości, przyczyna przyczyna)  |  [RMSNetworkException](#classmip_1_1_r_m_s_network_exception) konstruktora.
wbudowany publicznego RMSNetworkException (const char * const & komunikatu, przyczyna przyczyna)  |  [RMSNetworkException](#classmip_1_1_r_m_s_network_exception) konstruktora.
wbudowany publiczny wirtualny Przyczyna reason() const  |  Pobiera sieci klasyfikacji awarii.
wbudowany publiczny wirtualny const char * what() const  |  Pobiera komunikat o wyjątku.
wbudowany publiczny wirtualny ExceptionTypes type() const  |  Pobiera typ wyjątku.
wbudowany publiczny wirtualny int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](#classmip_1_1_r_m_s_network_exception) konstruktora.
  
#### <a name="parameters"></a>Parametry
* komunikat o wyjątku wiadomości 
* Przyczyna klasyfikacji błąd sieci
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](#classmip_1_1_r_m_s_network_exception) konstruktora.
  
#### <a name="parameters"></a>Parametry
* komunikat o wyjątku wiadomości 
* Przyczyna klasyfikacji błąd sieci
  
### <a name="reason"></a>Przyczyna
Pobiera sieci klasyfikacji awarii.
  
#### <a name="returns"></a>Zwraca
Klasyfikacja błąd sieci
  
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