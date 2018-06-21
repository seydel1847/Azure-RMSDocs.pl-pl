# <a name="class-miprmsexception"></a>Klasa mip::RMSException 
Wyjątek podstawowej usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny RMSException (stała typu ExceptionTypes, const int, const std::string & błędu wiadomości)  |  [RMSException](class_mip_rmsexception.md) konstruktora.
 publiczny RMSException (const ExceptionTypes, const int błąd typu, const char * const & wiadomości)  |  [RMSException](class_mip_rmsexception.md) konstruktora.
 publiczny wirtualny const char * what() const  |  Pobiera komunikat o wyjątku.
 publiczny wirtualny type() ExceptionTypes const  |  Pobiera typ wyjątku.
 publiczny wirtualny int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsexception"></a>RMSException
[RMSException](class_mip_rmsexception.md) konstruktora.

Parametry:  
* **Typ**: typ wyjątku 


* **Błąd**: [błąd](class_mip_error.md) kodu 


* **komunikat**: komunikat o wyjątku


  
### <a name="rmsexception"></a>RMSException
[RMSException](class_mip_rmsexception.md) konstruktora.

Parametry:  
* **Typ**: typ wyjątku 


* **Błąd**: [błąd](class_mip_error.md) kodu 


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