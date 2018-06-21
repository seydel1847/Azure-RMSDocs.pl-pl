# <a name="class-mipconsentresult"></a>Klasa mip::ConsentResult 
Przedstawia wynik żądania zgody po interakcji z użytkownikiem.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny ConsentResult (bool zaakceptowane, bool showAgain, const std::string i nazwa użytkownika)  |  [ConsentResult](class_mip_consentresult.md) konstruktora.
 publiczny bool Funkcja Accepted() const  |  Pobiera czy zgodę użytkownika na działania.
 publiczny bool ShowAgain() const  |  Pobiera czy zgody jawnej jest wymagana do przyszłych żądań.
 publiczny std::string const & UserId() const  |  Pobiera użytkownika (adres e-mail), od którego zażądano zgody.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="consentresult"></a>ConsentResult
[ConsentResult](class_mip_consentresult.md) konstruktora.

Parametry:  
* **zaakceptowane**: Określa, czy użytkownik zgodę na akcji 


* **showAgain**: Określa, czy jest wymagany dla żądania przyszłych akcji wyraźnej zgody 


* **Identyfikator userId**: użytkownik (adres e-mail), od którego zażądano zgody


  
### <a name="accepted"></a>Zaakceptowane
Pobiera czy zgodę użytkownika na działania.

  
**Zwraca**: czy contented do akcji użytkownika
  
### <a name="showagain"></a>ShowAgain
Pobiera czy zgody jawnej jest wymagana do przyszłych żądań.

  
**Zwraca**: Określa, czy zgody jawnej jest wymagany na potrzeby przyszłych żądań Jeśli to PRAWDA, zestaw SDK będzie Pamiętaj wynik tej zgody i nie Monituj aplikacji klienckiej w przyszłości o zgodę.
  
### <a name="userid"></a>UserId
Pobiera użytkownika (adres e-mail), od którego zażądano zgody.

  
**Zwraca**: użytkownika, od którego zażądano zgody