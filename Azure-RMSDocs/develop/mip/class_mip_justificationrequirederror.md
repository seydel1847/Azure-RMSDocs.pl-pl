# <a name="class-mipjustificationrequirederror"></a>Klasa mip::JustificationRequiredError 
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 JustificationRequiredError() publiczne  | _Nie została jeszcze udokumentowane._
publiczny wirtualny std::shared_ptr<Error> Clone() const  |  Klonowanie błędu.
 publiczny char const * what() const  |  Komunikat błędu cstring —.
 publiczny wirtualny ErrorType GetErrorType() const  |  Pobierz typ błędu.
 publiczny wirtualny std::string const & GetErrorName() const  |  Pobierz nazwę błędu.
 publiczny wirtualny std::string const & GetMessage() const  |  Komunikat o błędzie.
 publiczny wirtualny SetMessage void (const std::string & msg)  |  Ustaw komunikat o błędzie.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="justificationrequirederror"></a>JustificationRequiredError
_Jeszcze nie udokumentowane._

  
### <a name="error"></a>Error
Klonowanie błędu.

  
**Zwraca**: klon błędu.
  
### <a name="what"></a>Co
Komunikat błędu cstring —.

  
**Zwraca**: cstring — błąd wiadomości
  
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

