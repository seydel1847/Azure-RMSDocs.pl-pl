# <a name="class-mipfileioerror"></a>Klasa mip::FileIOError 
Błąd We/Wy pliku.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego char const * what() const  |  Komunikat błędu cstring —.
publiczny std::shared_ptr<Error> Clone() const  |  Klonowanie błędu.
wbudowany publiczny wirtualny ErrorType GetErrorType() const  |  Pobierz typ błędu.
wbudowany publiczny wirtualny const std::string & GetErrorName() const  |  Pobierz nazwę błędu.
wbudowany publiczny wirtualny const std::string & GetMessage() const  |  Komunikat o błędzie.
wbudowany publiczny wirtualny void SetMessage (const std::string & msg)  |  Ustaw komunikat o błędzie.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="what"></a>Co
Komunikat błędu cstring —.
  
#### <a name="returns"></a>Zwraca
cstring — błąd wiadomości
  
### <a name="error"></a>Error
Klonowanie błędu.
  
#### <a name="returns"></a>Zwraca
klon błędu.
  
### <a name="errortype"></a>ErrorType
Pobierz typ błędu.
  
#### <a name="returns"></a>Zwraca
Typ błędu.
  
### <a name="geterrorname"></a>GetErrorName
Pobierz nazwę błędu.
  
#### <a name="returns"></a>Zwraca
Nazwa błędu.
  
### <a name="getmessage"></a>GetMessage
Komunikat o błędzie.
  
#### <a name="returns"></a>Zwraca
komunikat o błędzie.
  
### <a name="setmessage"></a>SetMessage
Ustaw komunikat o błędzie.
  
#### <a name="parameters"></a>Parametry
* msg komunikat o błędzie.