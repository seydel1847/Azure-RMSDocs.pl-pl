# <a name="class-mipconsentresult"></a>Klasa mip::ConsentResult 
Przedstawia wynik żądania zgody po interakcji z użytkownikiem.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego ConsentResult publicznego wbudowanego bool zaakceptowane | Pobiera czy zgodę użytkownika na działania.
wbudowany publicznego bool ShowAgain | Pobiera czy zgody jawnej jest wymagana do przyszłych żądań.
const std::string publicznego wbudowanego & UserId | Pobiera użytkownika (adres e-mail), od którego zażądano zgody.
## <a name="members"></a>Elementy członkowskie
### <a name="consentresult"></a>ConsentResult
[ConsentResult](#classmip_1_1_consent_result) konstruktora.
#### <a name="parameters"></a>Parametry
* zaakceptowane czy zgodę użytkownika na akcję 
* showAgain czy zgody jawnej jest wymagany dla żądania przyszłych akcji 
* Nazwa użytkownika (adres e-mail), od którego zażądano zgody użytkownika
### <a name="accepted"></a>Zaakceptowane
Pobiera czy zgodę użytkownika na działania.
#### <a name="returns"></a>Zwraca
Czy contented do akcji użytkownika
### <a name="showagain"></a>ShowAgain
Pobiera czy zgody jawnej jest wymagana do przyszłych żądań.
#### <a name="returns"></a>Zwraca
Czy zgody jawnej jest wymagany do przyszłych żądań, jeśli to PRAWDA, zestaw SDK Pamiętaj wynik tej zgody, a nie Monituj aplikacji klienckiej w przyszłości o zgodę.
### <a name="userid"></a>UserId
Pobiera użytkownika (adres e-mail), od którego zażądano zgody.
#### <a name="returns"></a>Zwraca
Z którego zażądano zgody użytkownika