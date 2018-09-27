# <a name="class-mipconsent"></a>Klasa mip::Consent 
Reprezentuje użytkownika akceptacji/odmowy, aby zezwolić na akcję.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne mip::ConsentResult const & Result() const  |  Pobiera wynik żądania zgody.
 publiczny typ void wynik (const ConsentResult & wartość)  |  Ustawia wynik żądania zgody.
 publiczne mip::ConsentType Type() const  |  Pobiera typ zgody.
publiczne std::vector const < std::string > Urls() const  |  Pobiera adresy URL są zaangażowane w żądanie zgody.
 publiczne std::string const User() const  |  Pobiera użytkownika (adres e-mail), od którego zażądano zgody.
 publiczne std::string const Domain() const  |  Pobiera domeny skojarzone z użytkownikiem, od którego zażądano zgody.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="mipconsentresult"></a>MIP::ConsentResult
Pobiera wynik żądania zgody.

  
**Zwraca**: wynik żądania zgody
  
### <a name="result"></a>Result
Ustawia wynik żądania zgody.

Parametry:  
* **wartość**: wynik żądania zgody


  
### <a name="mipconsenttype"></a>MIP::ConsentType
Pobiera typ zgody.

  
**Zwraca**: typ zgody
  
### <a name="urls"></a>adresy URL
Pobiera adresy URL są zaangażowane w żądanie zgody.

  
**Zwraca**: adresy URL zaangażowane w żądanie zgody
  
### <a name="user"></a>Użytkownik
Pobiera użytkownika (adres e-mail), od którego zażądano zgody.

  
**Zwraca**: użytkownika, od którego zażądano zgody
  
### <a name="domain"></a>Domena
Pobiera domeny skojarzone z użytkownikiem, od którego zażądano zgody.

  
**Zwraca**: domeny skojarzone z użytkownikiem, od którego zażądano zgody