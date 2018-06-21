# <a name="class-miprmspfileexception"></a>Klasa mip::RMSPFileException 
Wyjątek PFile usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny RMSPFileException (const std::string & wiadomości, przyczyna przyczyna)  |  [RMSPFileException](class_mip_rmspfileexception.md) konstruktora.
 publiczny RMSPFileException (const char * const & komunikatu, przyczyna przyczyna)  |  [RMSPFileException](class_mip_rmspfileexception.md) konstruktora.
 publiczny wirtualny reason() Przyczyna const  |  Pobiera klasyfikację błąd PFile.
 publiczny wirtualny const char * what() const  |  Pobiera komunikat o wyjątku.
 publiczny wirtualny type() ExceptionTypes const  |  Pobiera typ wyjątku.
 publiczny wirtualny int error() const  |  Pobiera kod błędu.
  
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
Pobiera klasyfikację błąd PFile.

  
**Zwraca**: Klasyfikacja błąd PFile
  
### <a name="what"></a>Co
Pobiera komunikat o wyjątku.

  
**Zwraca**: komunikat o wyjątku
  
### <a name="exceptiontypes"></a>ExceptionTypes
Pobiera typ wyjątku.

  
**Zwraca**: typ wyjątku
  
### <a name="error"></a>Błąd
Pobiera kod błędu.

  
**Zwraca**: [błąd](class_mip_error.md) kodu