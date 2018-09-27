# <a name="class-miprmspfileexception"></a>Klasa mip::RMSPFileException 
Wyjątek PFile usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne RMSPFileException (const std::string & komunikat o błędzie, przyczyna przyczyna)  |  [RMSPFileException](class_mip_rmspfileexception.md) konstruktora.
 publiczne RMSPFileException (const char * const & komunikatu Przyczyna przyczyna)  |  [RMSPFileException](class_mip_rmspfileexception.md) konstruktora.
 publiczne wirtualne reason() Przyczyna const  |  Pobiera klasyfikacji błąd PFile.
 publiczne wirtualne const char * what() const  |  Pobiera komunikat o wyjątku.
 publiczne wirtualne type() ExceptionTypes const  |  Pobiera typ wyjątku.
 publiczne wirtualne int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](class_mip_rmspfileexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku 


* **Przyczyna**: Klasyfikacja błąd PFile


  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](class_mip_rmspfileexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku 


* **Przyczyna**: Klasyfikacja błąd PFile


  
### <a name="reason"></a>Przyczyna
Pobiera klasyfikacji błąd PFile.

  
**Zwraca**: Klasyfikacja błąd PFile
  
### <a name="what"></a>Co to
Pobiera komunikat o wyjątku.

  
**Zwraca**: komunikat o wyjątku
  
### <a name="exceptiontypes"></a>ExceptionTypes
Pobiera typ wyjątku.

  
**Zwraca**: typ wyjątku
  
### <a name="error"></a>Błąd
Pobiera kod błędu.

  
**Zwraca**: [błąd](class_mip_error.md) kodu