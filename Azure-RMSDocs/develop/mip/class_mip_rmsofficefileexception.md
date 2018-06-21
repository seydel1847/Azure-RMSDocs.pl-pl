# <a name="class-miprmsofficefileexception"></a>Klasa mip::RMSOfficeFileException 
Wyjątek pliku RMS Office.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny RMSOfficeFileException (const std::string & wiadomości, przyczyna przyczyna)  |  [RMSOfficeFileException](class_mip_rmsofficefileexception.md) konstruktora.
 publiczny RMSOfficeFileException (const char * const & komunikatu, przyczyna przyczyna)  |  [RMSOfficeFileException](class_mip_rmsofficefileexception.md) konstruktora.
 publiczny wirtualny reason() Przyczyna const  |  Pobiera klasyfikacji awarii plików pakietu Office.
 publiczny wirtualny const char * what() const  |  Pobiera komunikat o wyjątku.
 publiczny wirtualny type() ExceptionTypes const  |  Pobiera typ wyjątku.
 publiczny wirtualny int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](class_mip_rmsofficefileexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku 


* **Przyczyna**: Klasyfikacja awarii plików pakietu Office


  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](class_mip_rmsofficefileexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku 


* **Przyczyna**: Klasyfikacja awarii plików pakietu Office


  
### <a name="reason"></a>Przyczyna
Pobiera klasyfikacji awarii plików pakietu Office.

  
**Zwraca**: Klasyfikacja awarii plików pakietu Office
  
### <a name="what"></a>Co
Pobiera komunikat o wyjątku.

  
**Zwraca**: komunikat o wyjątku
  
### <a name="exceptiontypes"></a>ExceptionTypes
Pobiera typ wyjątku.

  
**Zwraca**: typ wyjątku
  
### <a name="error"></a>Błąd
Pobiera kod błędu.

  
**Zwraca**: [błąd](class_mip_error.md) kodu