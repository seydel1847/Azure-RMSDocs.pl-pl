# <a name="class-miprmsnetworkexception"></a>Klasa mip::RMSNetworkException 
Wyjątek sieci usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne RMSNetworkException (const std::string & komunikat o błędzie, przyczyna przyczyna)  |  [RMSNetworkException](class_mip_rmsnetworkexception.md) konstruktora.
 publiczne RMSNetworkException (const char * const & komunikatu Przyczyna przyczyna)  |  [RMSNetworkException](class_mip_rmsnetworkexception.md) konstruktora.
 publiczne wirtualne reason() Przyczyna const  |  Pobiera sieci niepowodzenia klasyfikacji.
 publiczne wirtualne const char * what() const  |  Pobiera komunikat o wyjątku.
 publiczne wirtualne type() ExceptionTypes const  |  Pobiera typ wyjątku.
 publiczne wirtualne int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](class_mip_rmsnetworkexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku 


* **Przyczyna**: sieci niepowodzenia klasyfikacji


  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](class_mip_rmsnetworkexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku 


* **Przyczyna**: sieci niepowodzenia klasyfikacji


  
### <a name="reason"></a>Przyczyna
Pobiera sieci niepowodzenia klasyfikacji.

  
**Zwraca**: sieci niepowodzenia klasyfikacji
  
### <a name="what"></a>Co to
Pobiera komunikat o wyjątku.

  
**Zwraca**: komunikat o wyjątku
  
### <a name="exceptiontypes"></a>ExceptionTypes
Pobiera typ wyjątku.

  
**Zwraca**: typ wyjątku
  
### <a name="error"></a>Błąd
Pobiera kod błędu.

  
**Zwraca**: [błąd](class_mip_error.md) kodu