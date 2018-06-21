# <a name="class-mippolicyenginesettings"></a>Klasa mip::PolicyEngine::Settings 
Podaj wystąpienia tej klasy z approprieted, musi należeć do parametrów można zainicjować aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Ustawienia publicznego (const std::string & identyfikator, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  Skonstruować wystąpienia o określonych parametrach. Umożliwia to tworzenie [ustawienia](class_mip_policyengine_settings.md) do wywołania LoadEngineAsync załadować istniejących aparatu.
 Ustawienia publicznego (const tożsamości i tożsamości, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  Umożliwia to tworzenie [ustawienia](class_mip_policyengine_settings.md) do wywołania AddEngineAsync, aby dodać nowy aparat.
 publiczny std::string const & GetId() const  |  Pobierz identyfikator aparatu.
 publiczny typ void identyfikator zestawu (const std::string & id)  |  Ustaw identyfikator aparatu.
 publiczny tożsamości const & GetIdentity() const  |  Pobierz obiekt tożsamości.
 publiczny SetIdentity void (const tożsamości i tożsamości)  |  Obiekt tożsamości zestawu.
 publiczny std::string const & GetClientData() const  |  Pobierz dane klienta w ustawieniach.
 publiczny SetClientData void (const std::string & dane klienckie)  |  Ustaw ciąg danych klienta.
 publiczny std::string const & GetLocale() const  |  Pobierz ustawienia ustawienia regionalne.
publiczny SetCustomSettings void (const std::vector < std::pair < std::string, std::string >> & customSettings)  |  Określ ustawienia niestandardowe, używane dla funkcji bramkowanie i testowania.
publiczny std::vector const < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Określ ustawienia niestandardowe, używane dla funkcji bramkowanie i testowania.
 publiczny SetSessionId void (const std::string & sessionId)  |  Ustaw identyfikator sesji używany do telementry klient jest zdefiniowany.
 publiczny std::string const & GetSessionId() const  |  Pobierz identyfikator sesji, unikatowy identyfikator.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Skonstruować wystąpienia o określonych parametrach. Umożliwia to tworzenie [ustawienia](class_mip_policyengine_settings.md) do wywołania LoadEngineAsync załadować istniejących aparatu.

Parametry:  
* **Identyfikator**: ustaw ją na identyfikator unikatowy aparat generowane przez AddEngineAsync lub jeden własnym wygenerowany. Podczas ponownego ładowania istniejących aparat użycia identyfikator else nowy aparat zostanie utworzony. 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem podczas zwolnione, można pobrać z załadować aparatu. 


* **Ustawienia regionalne**: aparat Lokalizowalny dane wyjściowe zostaną dodane do tych ustawień regionalnych, domyślny "en US".


  
### <a name="settings"></a>Ustawienia
Umożliwia to tworzenie [ustawienia](class_mip_policyengine_settings.md) do wywołania AddEngineAsync, aby dodać nowy aparat.

Parametry:  
* **tożsamość**: Unikatowy identyfikator użytkownika, dla którego aparat musi zostać dodany. 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem podczas zwolnione, można pobrać z załadować aparatu. 


* **Ustawienia regionalne**: aparat Lokalizowalny dane wyjściowe zostaną dodane do tych ustawień regionalnych, domyślny "en US".


  
### <a name="getid"></a>GetId
Pobierz identyfikator aparatu.

  
**Zwraca**: unikatowy ciąg identyfikujący aparat.
  
### <a name="setid"></a>Identyfikator zestawu
Ustaw identyfikator aparatu.

Parametry:  
* **Identyfikator**: identyfikator aparatu.


  
### <a name="getidentity"></a>Żądanie GetIdentity
Pobierz obiekt tożsamości.

  
**Zwraca**: refrence tożsamości w obiekcie ustawień. 
**Zobacz też**: mip::Identity
  
### <a name="setidentity"></a>SetIdentity
Obiekt tożsamości zestawu.

Parametry:  
* **tożsamość**: unikatową tożsamość użytkownika. 


**Zobacz też**: mip::Identity
  
### <a name="getclientdata"></a>GetClientData
Pobierz dane klienta w ustawieniach.

  
**Zwraca**: ciąg danych określony przez klienta.
  
### <a name="setclientdata"></a>SetClientData
Ustaw ciąg danych klienta.

Parametry:  
* **Dane klienckie**: data określona przez użytkownika.


  
### <a name="getlocale"></a>GetLocale
Pobierz ustawienia ustawienia regionalne.

  
**Zwraca**: ustawienia regionalne.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Określ ustawienia niestandardowe, używane dla funkcji bramkowanie i testowania.

Parametry:  
* **customSettings**: Lista par nazwa/wartość.


  
### <a name="getcustomsettings"></a>GetCustomSettings
Określ ustawienia niestandardowe, używane dla funkcji bramkowanie i testowania.

Parametry:  
* **Lista**: par nazwa/wartość.


  
### <a name="setsessionid"></a>SetSessionId
Ustaw identyfikator sesji używany do telementry klient jest zdefiniowany.

Parametry:  
* **Identyfikator sesji**: unikatowy ciąg, który łączy zdarzenia telemetrii.


  
### <a name="getsessionid"></a>GetSessionId
Pobierz identyfikator sesji, unikatowy identyfikator.

  
**Zwraca**: identyfikator sesji.