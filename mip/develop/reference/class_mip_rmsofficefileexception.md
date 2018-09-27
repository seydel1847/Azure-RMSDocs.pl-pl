# <a name="class-miprmsofficefileexception"></a>Klasa mip::RMSOfficeFileException 
Wyjątek pliku RMS Office.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne RMSOfficeFileException (const std::string & komunikat o błędzie, przyczyna przyczyna)  |  [RMSOfficeFileException](class_mip_rmsofficefileexception.md) konstruktora.
 publiczne RMSOfficeFileException (const char * const & komunikatu Przyczyna przyczyna)  |  [RMSOfficeFileException](class_mip_rmsofficefileexception.md) konstruktora.
 publiczne wirtualne reason() Przyczyna const  |  Pobiera klasyfikacji niepowodzenie plików pakietu Office.
 publiczne wirtualne const char * what() const  |  Pobiera komunikat o wyjątku.
 publiczne wirtualne type() ExceptionTypes const  |  Pobiera typ wyjątku.
 publiczne wirtualne int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](class_mip_rmsofficefileexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku 


* **Przyczyna**: Klasyfikacja błędów plików pakietu Office


  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](class_mip_rmsofficefileexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku 


* **Przyczyna**: Klasyfikacja błędów plików pakietu Office


  
### <a name="reason"></a>Przyczyna
Pobiera klasyfikacji niepowodzenie plików pakietu Office.

  
**Zwraca**: Klasyfikacja błędów plików pakietu Office
  
### <a name="what"></a>Co to
Pobiera komunikat o wyjątku.

  
**Zwraca**: komunikat o wyjątku
  
### <a name="exceptiontypes"></a>ExceptionTypes
Pobiera typ wyjątku.

  
**Zwraca**: typ wyjątku
  
### <a name="error"></a>Błąd
Pobiera kod błędu.

  
**Zwraca**: [błąd](class_mip_error.md) kodu