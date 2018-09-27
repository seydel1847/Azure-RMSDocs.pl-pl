# <a name="class-miphttpdelegate"></a>Klasa mip::HttpDelegate 
Interfejs dla zastępowanie obsługi protokołu http.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::shared_ptr<HttpResponse> wysyłania (const std::shared_ptr<HttpRequest>& żądania, const std::shared_ptr<void>& kontekstu)  |  Wyślij żądanie http.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="httpresponse"></a>HttpResponse
Wyślij żądanie http.

Parametry:  
* **żądanie**: żądania Http 


* **kontekst**: ten sam kontekst nieprzezroczyste klienta, który został przekazany do interfejsu API, które spowodowały to żądanie http



  
**Zwraca**: odpowiedź Http