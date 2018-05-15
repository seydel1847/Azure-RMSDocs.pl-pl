# <a name="class-miprmsstreamexception"></a>Klasa mip::RMSStreamException 
Wyjątek strumienia usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny RMSStreamException (const std::string & wiadomości)  |  [RMSStreamException](class_mip_rmsstream_exception.md) konstruktora.
 publiczny RMSStreamException (const char * const & wiadomości)  |  [RMSStreamException](class_mip_rmsstream_exception.md) konstruktora.
 publiczny wirtualny const char * what() const  |  Pobiera komunikat o wyjątku.
 publiczny wirtualny type() ExceptionTypes const  |  Pobiera typ wyjątku.
 publiczny wirtualny int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](class_mip_rmsstream_exception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku


  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](class_mip_rmsstream_exception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku


  
### <a name="what"></a>Co
Pobiera komunikat o wyjątku.

  
**Zwraca**: komunikat o wyjątku
  
### <a name="exceptiontypes"></a>ExceptionTypes
Pobiera typ wyjątku.

  
**Zwraca**: typ wyjątku
  
### <a name="error"></a>Błąd
Pobiera kod błędu.

  
**Zwraca**: [błąd](class_mip_error.md) kodu