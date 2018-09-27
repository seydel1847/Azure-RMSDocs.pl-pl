# <a name="class-miprmsstreamexception"></a>Klasa mip::RMSStreamException 
Wyjątek strumienia usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne RMSStreamException (const std::string ko & munikat)  |  [RMSStreamException](class_mip_rmsstreamexception.md) konstruktora.
 publiczne RMSStreamException (const char * const & komunikatu)  |  [RMSStreamException](class_mip_rmsstreamexception.md) konstruktora.
 publiczne wirtualne const char * what() const  |  Pobiera komunikat o wyjątku.
 publiczne wirtualne type() ExceptionTypes const  |  Pobiera typ wyjątku.
 publiczne wirtualne int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](class_mip_rmsstreamexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku


  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](class_mip_rmsstreamexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku


  
### <a name="what"></a>Co to
Pobiera komunikat o wyjątku.

  
**Zwraca**: komunikat o wyjątku
  
### <a name="exceptiontypes"></a>ExceptionTypes
Pobiera typ wyjątku.

  
**Zwraca**: typ wyjątku
  
### <a name="error"></a>Błąd
Pobiera kod błędu.

  
**Zwraca**: [błąd](class_mip_error.md) kodu