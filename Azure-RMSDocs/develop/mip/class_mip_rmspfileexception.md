# <a name="class-miprmspfileexception"></a>Klasa mip::RMSPFileException 
Wyjątek PFile usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego RMSPFileException (const std::string & wiadomości, przyczyna przyczyna)  |  [RMSPFileException](#classmip_1_1_r_m_s_p_file_exception) konstruktora.
wbudowany publicznego RMSPFileException (const char * const & komunikatu, przyczyna przyczyna)  |  [RMSPFileException](#classmip_1_1_r_m_s_p_file_exception) konstruktora.
wbudowany publiczny wirtualny Przyczyna reason() const  |  Pobiera klasyfikację błąd PFile.
wbudowany publiczny wirtualny const char * what() const  |  Pobiera komunikat o wyjątku.
wbudowany publiczny wirtualny ExceptionTypes type() const  |  Pobiera typ wyjątku.
wbudowany publiczny wirtualny int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](#classmip_1_1_r_m_s_p_file_exception) konstruktora.
  
#### <a name="parameters"></a>Parametry
* komunikat o wyjątku wiadomości 
* Przyczyna klasyfikacji błąd PFile
  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](#classmip_1_1_r_m_s_p_file_exception) konstruktora.
  
#### <a name="parameters"></a>Parametry
* komunikat o wyjątku wiadomości 
* Przyczyna klasyfikacji błąd PFile
  
### <a name="reason"></a>Przyczyna
Pobiera klasyfikację błąd PFile.
  
#### <a name="returns"></a>Zwraca
Klasyfikacja błąd PFile
  
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