# <a name="class-mippolicyenginesettings"></a>Klasa mip::PolicyEngine::Settings 
Wystąpienie tej klasy z odpowiednimi parametrami powinien zapewniać można zainicjować aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Ustawienia publicznego (const std::string & engineId, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  Skonstruować wystąpienia z podanych parametrów. Umożliwia to tworzenie [ustawienia](class_mip_policyengine_settings.md) wywołać LoadEngineAsync można załadować aparatu istniejących.
 Ustawienia publicznego (const tożsamości i tożsamości, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  Umożliwia to tworzenie [ustawienia](class_mip_policyengine_settings.md) wywołać AddEngineAsync, aby dodać nowy aparat.
 publiczne std::string const & GetEngineId() const  |  Pobierz identyfikator aparatu.
 publiczne SetEngineId void (const std::string & identyfikator)  |  Ustaw identyfikator aparatu.
 Identyfikator publiczny const & GetIdentity() const  |  Pobierz obiekt tożsamości.
 publiczne SetIdentity void (const tożsamości i tożsamości)  |  Obiekt tożsamości zestawu.
 publiczne std::string const & GetClientData() const  |  Pobierz dane klienta w oknie Ustawienia.
 publiczne SetClientData void (const std::string & dane klienckie)  |  Ustaw parametry danych klienta.
 publiczne std::string const & GetLocale() const  |  Pobierz ustawienia regionalne w oknie Ustawienia.
publiczne SetCustomSettings void (const std::vector < std::pair < std::string, std::string >> & customSettings)  |  Ustaw ustawienia niestandardowe, używany dla funkcji uzyskania bramowego i testowania.
publiczne std::vector const < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Pobierz ustawienia niestandardowe, używany dla funkcji uzyskania bramowego i testowania.
 publiczne SetSessionId void (const std::string & sessionId)  |  Ustaw identyfikator sesji używany dla telemetrii klient jest zdefiniowany.
 publiczne std::string const & GetSessionId() const  |  Pobierz identyfikator sesji, unikatowy identyfikator.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Skonstruować wystąpienia z podanych parametrów. Umożliwia to tworzenie [ustawienia](class_mip_policyengine_settings.md) wywołać LoadEngineAsync można załadować aparatu istniejących.

Parametry:  
* **engineId**: ustaw ją na identyfikator unikatowy aparatu wygenerowany przez AddEngineAsync lub jeden własnym wygenerowany. Podczas ponownego ładowania aparat istniejących Użyj identyfikatora, przeciwnym razie nowy aparat zostanie utworzony. 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem, gdy zwolniony, można pobrać z załadowanych aparatu. 


* **Ustawienia regionalne**: aparat możliwych do zlokalizowania w danych wyjściowych, które będą dostępne w tych ustawień regionalnych.


  
### <a name="settings"></a>Ustawienia
Umożliwia to tworzenie [ustawienia](class_mip_policyengine_settings.md) wywołać AddEngineAsync, aby dodać nowy aparat.

Parametry:  
* **tożsamość**: Unikatowy identyfikator użytkownika, dla którego aparat musi zostać dodany. 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem, gdy zwolniony, można pobrać z załadowanych aparatu. 


* **Ustawienia regionalne**: aparat możliwych do zlokalizowania w danych wyjściowych, które będą dostępne w tych ustawień regionalnych.


  
### <a name="getengineid"></a>GetEngineId
Pobierz identyfikator aparatu.

  
**Zwraca**: unikatowy ciąg identyfikujący silnika.
  
### <a name="setengineid"></a>SetEngineId
Ustaw identyfikator aparatu.

Parametry:  
* **Identyfikator**: identyfikator aparatu.


  
### <a name="getidentity"></a>Żądanie GetIdentity
Pobierz obiekt tożsamości.

  
**Zwraca**: odwołanie do tożsamości w obiekcie ustawień. 
  
**Zobacz też**: mip::Identity
  
### <a name="setidentity"></a>SetIdentity
Obiekt tożsamości zestawu.

Parametry:  
* **tożsamość**: unikatową tożsamość użytkownika. 


  
**Zobacz też**: mip::Identity
  
### <a name="getclientdata"></a>GetClientData
Pobierz dane klienta w oknie Ustawienia.

  
**Zwraca**: ciągu danych określony przez klienta.
  
### <a name="setclientdata"></a>SetClientData
Ustaw parametry danych klienta.

Parametry:  
* **Dane klienckie**: określone dane przez użytkownika.


  
### <a name="getlocale"></a>GetLocale
Pobierz ustawienia regionalne w oknie Ustawienia.

  
**Zwraca**: ustawienia regionalne.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Ustaw ustawienia niestandardowe, używany dla funkcji uzyskania bramowego i testowania.

Parametry:  
* **customSettings**: Lista par nazwa/wartość.


  
### <a name="getcustomsettings"></a>GetCustomSettings
Pobierz ustawienia niestandardowe, używany dla funkcji uzyskania bramowego i testowania.

  
**Zwraca**: Lista par nazwa/wartość.
  
### <a name="setsessionid"></a>SetSessionId
Ustaw identyfikator sesji używany dla telemetrii klient jest zdefiniowany.

Parametry:  
* **Identyfikator sesji**: unikatowy ciąg, który nawiązuje połączenie zdarzenia telemetrii.


  
### <a name="getsessionid"></a>GetSessionId
Pobierz identyfikator sesji, unikatowy identyfikator.

  
**Zwraca**: identyfikator sesji.