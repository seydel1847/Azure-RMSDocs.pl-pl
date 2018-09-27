# <a name="class-miphttprequest"></a>Klasa mip::HttpRequest 
Interfejs, który opisuje żądania http jednym.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne HttpRequestType GetRequestType() const  |  Pobierz typ żądania.
 publiczne std::string const & GetUrl() const  |  Adres url żądania GET.
 publiczne std::string const & GetBody() const  |  Uzyskaj treści żądania.
publiczne std::map const < std::string, std::string, CaseInsensitiveComparator > & GetHeaders() const  |  Pobierz nagłówki żądania.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="httprequesttype"></a>HttpRequestType
Pobierz typ żądania.

  
**Zwraca**: typ żądania
  
### <a name="geturl"></a>GetUrl
Adres url żądania GET.

  
**Zwraca**: adres url żądania
  
### <a name="getbody"></a>GetBody
Uzyskaj treści żądania.

  
**Zwraca**: treść żądania
  
### <a name="getheaders"></a>GetHeaders
Pobierz nagłówki żądania.

  
**Zwraca**: nagłówki żądania