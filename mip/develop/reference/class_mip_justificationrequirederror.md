# <a name="class-mipjustificationrequirederror"></a>Klasa mip::JustificationRequiredError 
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne std::shared_ptr<Error> Clone() const  |  Klonuj ten błąd.
 publiczne char const * what() const  |  Pojawia się komunikat cstring.
 publiczne wirtualne ErrorType GetErrorType() const  |  Pobierz typ błędu.
 publiczne wirtualne std::string const & GetErrorName() const  |  Pobierz nazwę błędu.
 publiczne wirtualne std::string const & GetMessage() const  |  Komunikat o błędzie.
 publiczne wirtualne SetMessage void (const std::string & msg)  |  Ustaw komunikat o błędzie.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="error"></a>Error
Klonuj ten błąd.

  
**Zwraca**: klonowania błędu.
  
### <a name="what"></a>Co to
Pojawia się komunikat cstring.

  
**Zwraca**: cstring err wiadomości
  
### <a name="errortype"></a>ErrorType
Pobierz typ błędu.

  
**Zwraca**: typ błędu.
  
### <a name="geterrorname"></a>GetErrorName
Pobierz nazwę błędu.

  
**Zwraca**: nazwa błędu.
  
### <a name="getmessage"></a>GetMessage
Komunikat o błędzie.

  
**Zwraca**: komunikat o błędzie.
  
### <a name="setmessage"></a>SetMessage
Ustaw komunikat o błędzie.

Parametry:  
* **msg**: komunikat o błędzie.

