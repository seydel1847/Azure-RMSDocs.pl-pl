# <a name="class-miprmsofficefileexception"></a>Klasa mip::RMSOfficeFileException 
Wyjątek pliku RMS Office.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego RMSOfficeFileException (const std::string & wiadomości, przyczyna przyczyna)  |  [RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception) konstruktora.
wbudowany publicznego RMSOfficeFileException (const char * const & komunikatu, przyczyna przyczyna)  |  [RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception) konstruktora.
wbudowany publiczny wirtualny Przyczyna reason() const  |  Pobiera klasyfikacji awarii plików pakietu Office.
wbudowany publiczny wirtualny const char * what() const  |  Pobiera komunikat o wyjątku.
wbudowany publiczny wirtualny ExceptionTypes type() const  |  Pobiera typ wyjątku.
wbudowany publiczny wirtualny int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception) konstruktora.
  
#### <a name="parameters"></a>Parametry
* komunikat o wyjątku wiadomości 
* Przyczyna klasyfikacji awarii plików pakietu Office
  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception) konstruktora.
  
#### <a name="parameters"></a>Parametry
* komunikat o wyjątku wiadomości 
* Przyczyna klasyfikacji awarii plików pakietu Office
  
### <a name="reason"></a>Przyczyna
Pobiera klasyfikacji awarii plików pakietu Office.
  
#### <a name="returns"></a>Zwraca
Klasyfikacja awarii plików pakietu Office
  
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