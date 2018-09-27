# <a name="class-mipconsentresult"></a>Klasa mip::ConsentResult 
W tym artykule opisano wynik żądania zgody po interakcji z użytkownikiem.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ConsentResult (bool zaakceptowane, bool showAgain, const std::string i nazwa użytkownika)  |  [ConsentResult](class_mip_consentresult.md) konstruktora.
 publiczne bool Funkcja Accepted() const  |  Pobiera informację określającą, czy użytkownik wyraża zgodę na akcji.
 publiczne bool ShowAgain() const  |  Pobiera informację określającą, czy wyraźnej zgody jest wymagany dla przyszłych żądań.
 publiczne std::string const & UserId() const  |  Pobiera użytkownika (adres e-mail), od którego zażądano zgody.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="consentresult"></a>ConsentResult
[ConsentResult](class_mip_consentresult.md) konstruktora.

Parametry:  
* **zaakceptowane**: Określa, czy użytkownik wyraża zgodę na akcję 


* **showAgain**: Określa, czy jest wymagane dla akcji przyszłych żądań wyraźnej zgody 


* **Identyfikator userId**: użytkownik (adres e-mail), od którego zażądano zgody


  
### <a name="accepted"></a>Zaakceptowane
Pobiera informację określającą, czy użytkownik wyraża zgodę na akcji.

  
**Zwraca**: niezależnie od tego czy contented akcji użytkownika
  
### <a name="showagain"></a>ShowAgain
Pobiera informację określającą, czy wyraźnej zgody jest wymagany dla przyszłych żądań.

  
**Zwraca**: Określa, czy wyraźnej zgody jest wymagany na potrzeby przyszłych żądań, jeśli jest to wartość true, zestaw SDK będzie zapamiętanie wyników tej zgody i nie Monituj przez aplikację kliencką zgody w przyszłości.
  
### <a name="userid"></a>UserId
Pobiera użytkownika (adres e-mail), od którego zażądano zgody.

  
**Zwraca**: użytkownika, od którego zażądano zgody