# <a name="class-mipconsent"></a>Klasa mip::Consent 
Reprezentuje użytkownika akceptacji/odmowy akcji zezwalania z akcją.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny mip::ConsentResult const & wyników | Pobiera wynik żądania zgody.
Wartość & publicznego ResultConsentResult void) | Ustawia wynik żądania zgody.
mip::ConsentType publicznego typu | Pobiera typ zgody.
publiczny std::vector const < std::string > adresy URL | Pobiera adresy URL są zaangażowane w żądanie zgody.
publiczny std::string const użytkownika | Pobiera użytkownika (adres e-mail), od którego zażądano zgody.
publiczny std::string const domeny | Pobiera w domenie skojarzonej z użytkownikiem, z którego zażądano zgody.
## <a name="members"></a>Elementy członkowskie
### <a name="mipconsentresult"></a>MIP::ConsentResult
Pobiera wynik żądania zgody.
#### <a name="returns"></a>Zwraca
Wynik żądania zgody
### <a name="result"></a>Result
Ustawia wynik żądania zgody.
#### <a name="parameters"></a>Parametry
* wartość wynik żądania zgody
### <a name="mipconsenttype"></a>MIP::ConsentType
Pobiera typ zgody.
#### <a name="returns"></a>Zwraca
Typ zgody
### <a name="urls"></a>Adresy URL
Pobiera adresy URL są zaangażowane w żądanie zgody.
#### <a name="returns"></a>Zwraca
Adresy URL zaangażowane w żądanie zgody
### <a name="user"></a>Użytkownik
Pobiera użytkownika (adres e-mail), od którego zażądano zgody.
#### <a name="returns"></a>Zwraca
Z którego zażądano zgody użytkownika
### <a name="domain"></a>Domena
Pobiera w domenie skojarzonej z użytkownikiem, z którego zażądano zgody.
#### <a name="returns"></a>Zwraca
Domeny skojarzonych z użytkownikiem, z którego zażądano zgody