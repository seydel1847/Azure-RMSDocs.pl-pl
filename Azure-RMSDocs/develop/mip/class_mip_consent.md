# <a name="class-mipconsent"></a>Klasa mip::Consent 
Reprezentuje użytkownika akceptacji/odmowy akcji zezwalania z akcją.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny mip::ConsentResult const & Result() const  |  Pobiera wynik żądania zgody.
 publiczny typ void powoduje (const ConsentResult & wartość)  |  Ustawia wynik żądania zgody.
 publiczny mip::ConsentType Type() const  |  Pobiera typ zgody.
publiczny std::vector const < std::string > Urls() const  |  Pobiera adresy URL są zaangażowane w żądanie zgody.
 publiczny std::string const User() const  |  Pobiera użytkownika (adres e-mail), od którego zażądano zgody.
 publiczny std::string const Domain() const  |  Pobiera w domenie skojarzonej z użytkownikiem, z którego zażądano zgody.
  
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
  
### <a name="urls"></a>Adresy URL
Pobiera adresy URL są zaangażowane w żądanie zgody.

  
**Zwraca**: zaangażowane w żądanie zgody adresy URL
  
### <a name="user"></a>Użytkownik
Pobiera użytkownika (adres e-mail), od którego zażądano zgody.

  
**Zwraca**: użytkownika, od którego zażądano zgody
  
### <a name="domain"></a>Domena
Pobiera w domenie skojarzonej z użytkownikiem, z którego zażądano zgody.

  
**Zwraca**: domeny skojarzony z użytkownikiem, z którego zażądano zgody