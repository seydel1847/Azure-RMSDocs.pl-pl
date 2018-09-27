# <a name="class-miprmslogicexception"></a>Klasa mip::RMSLogicException 
Wyjątek logiki usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne RMSLogicException (const błąd ErrorTypes, const std::string & komunikatu)  |  [RMSLogicException](class_mip_rmslogicexception.md) konstruktora.
 publiczne RMSLogicException (const błąd ErrorTypes, const char * const & komunikatu)  |  [RMSLogicException](class_mip_rmslogicexception.md) konstruktora.
 publiczne wirtualne const char * what() const  |  Pobiera komunikat o wyjątku.
 publiczne wirtualne type() ExceptionTypes const  |  Pobiera typ wyjątku.
 publiczne wirtualne int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmslogicexception"></a>RMSLogicException
[RMSLogicException](class_mip_rmslogicexception.md) konstruktora.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) kodu 


* **komunikat**: komunikat o wyjątku


  
### <a name="rmslogicexception"></a>RMSLogicException
[RMSLogicException](class_mip_rmslogicexception.md) konstruktora.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) kodu 


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