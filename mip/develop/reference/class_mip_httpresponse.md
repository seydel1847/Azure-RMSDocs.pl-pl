# <a name="class-miphttpresponse"></a>Klasa mip::HttpResponse 
Interfejs, który opisuje odpowiedzi http pojedynczego, implementowane przez aplikację klienta, gdy zastępowanie [HttpDelegate](class_mip_httpdelegate.md).
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne int32_t GetStatusCode() const  |  Pobierz kod stanu odpowiedzi.
 publiczne std::string const & GetBody() const  |  Uzyskaj treści żądania.
publiczne std::map const < std::string, std::string, CaseInsensitiveComparator > & GetHeaders() const  |  Pobierz nagłówki żądania.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getstatuscode"></a>GetStatusCode
Pobierz kod stanu odpowiedzi.

  
**Zwraca**: kod stanu:
  
### <a name="getbody"></a>GetBody
Uzyskaj treści żądania.

  
**Zwraca**: treść żądania
  
### <a name="getheaders"></a>GetHeaders
Pobierz nagłówki żądania.

  
**Zwraca**: nagłówki żądania