# <a name="class-miprmsnetworkexception"></a>Klasa mip::RMSNetworkException 
Wyjątek sieci usługi RMS.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny RMSNetworkException (const std::string & wiadomości, przyczyna przyczyna)  |  [RMSNetworkException](class_mip_rmsnetworkexception.md) konstruktora.
 publiczny RMSNetworkException (const char * const & komunikatu, przyczyna przyczyna)  |  [RMSNetworkException](class_mip_rmsnetworkexception.md) konstruktora.
 publiczny wirtualny reason() Przyczyna const  |  Pobiera sieci klasyfikacji awarii.
 publiczny wirtualny const char * what() const  |  Pobiera komunikat o wyjątku.
 publiczny wirtualny type() ExceptionTypes const  |  Pobiera typ wyjątku.
 publiczny wirtualny int error() const  |  Pobiera kod błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](class_mip_rmsnetworkexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku 


* **Przyczyna**: Klasyfikacja błąd sieci


  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](class_mip_rmsnetworkexception.md) konstruktora.

Parametry:  
* **komunikat**: komunikat o wyjątku 


* **Przyczyna**: Klasyfikacja błąd sieci


  
### <a name="reason"></a>Przyczyna
Pobiera sieci klasyfikacji awarii.

  
**Zwraca**: Klasyfikacja błąd sieci
  
### <a name="what"></a>Co
Pobiera komunikat o wyjątku.

  
**Zwraca**: komunikat o wyjątku
  
### <a name="exceptiontypes"></a>ExceptionTypes
Pobiera typ wyjątku.

  
**Zwraca**: typ wyjątku
  
### <a name="error"></a>Błąd
Pobiera kod błędu.

  
**Zwraca**: [błąd](class_mip_error.md) kodu