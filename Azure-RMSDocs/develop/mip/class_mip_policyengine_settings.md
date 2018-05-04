# <a name="class-mippolicyenginesettings"></a>Klasa mip::PolicyEngine::Settings 
Podaj wystąpienia tej klasy z approprieted, musi należeć do parametrów można zainicjować aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
`public inline Settings(const std::string& id, const std::string& clientData, const std::string& locale)`  |  Skonstruować wystąpienia o określonych parametrach. Umożliwia to tworzenie [ustawienia](#classmip_1_1_policy_engine_1_1_settings) do wywołania LoadEngineAsync załadować istniejących aparatu.
`public inline Settings(const Identity& identity, const std::string& clientData, const std::string& locale)`  |  Umożliwia to tworzenie [ustawienia](#classmip_1_1_policy_engine_1_1_settings) do wywołania AddEngineAsync, aby dodać nowy aparat.
`public inline const std::string& GetId() const`  |  Pobierz identyfikator aparatu
`public inline void SetId(const std::string& id)`  |  Ustaw identyfikator aparatu.
`public inline const Identity& GetIdentity() const`  |  Pobierz obiekt tożsamości.
`public inline void SetIdentity(const Identity& identity)`  |  Obiekt tożsamości zestawu.
`public inline const std::string& GetClientData() const`  |  Pobierz dane klienta w ustawieniach.
`public inline void SetClientData(const std::string& clientData)`  |  Ustaw ciąg danych klienta.
`public inline const std::string& GetLocale() const`  |  Pobierz ustawienia ustawienia regionalne.
`public inline void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& customSettings)`  |  Określ ustawienia niestandardowe, używane dla funkcji bramkowanie i testowania.
`public inline const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const`  |  Określ ustawienia niestandardowe, używane dla funkcji bramkowanie i testowania.
`public inline void SetSessionId(const std::string& sessionId)`  |  Ustaw identyfikator sesji używany do telemetrii klient jest zdefiniowany.
`public inline const std::string& GetSessionId() const`  |  Pobierz identyfikator sesji, unikatowy identyfikator.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Skonstruować wystąpienia o określonych parametrach. Umożliwia to tworzenie [ustawienia](#classmip_1_1_policy_engine_1_1_settings) do wywołania LoadEngineAsync załadować istniejących aparatu.
  
#### <a name="parameters"></a>Parametry
* Identyfikator ustaw ją na identyfikator unikatowy aparat generowane przez AddEngineAsync lub wygenerować własny. Podczas ponownego ładowania istniejących aparat użycia identyfikator else nowy aparat zostanie utworzony. 
* dane klienta można dostosowywać dane klienckie, które mogą być przechowywane z aparatem podczas zwolnione, można pobrać z załadować aparatu. 
* Ustawienia regionalne aparat Lokalizowalny w danych wyjściowych będzie dostępna w tych ustawień regionalnych, domyślny "en US".
  
### <a name="settings"></a>Ustawienia
Umożliwia to tworzenie [ustawienia](#classmip_1_1_policy_engine_1_1_settings) do wywołania AddEngineAsync, aby dodać nowy aparat.
  
#### <a name="parameters"></a>Parametry
* Unikatowy identyfikator tożsamości użytkownika, dla którego aparat musi zostać dodany. 
* dane klienta można dostosowywać dane klienckie, które mogą być przechowywane z aparatem podczas zwolnione, można pobrać z załadować aparatu. 
* Ustawienia regionalne aparat Lokalizowalny w danych wyjściowych będzie dostępna w tych ustawień regionalnych, domyślne `en-US`.
  
### <a name="getid"></a>GetId
Pobierz identyfikator aparatu
  
#### <a name="returns"></a>Zwraca
Unikatowy ciąg identyfikujący aparat.
  
### <a name="setid"></a>Identyfikator zestawu
Ustaw identyfikator aparatu.
  
#### <a name="parameters"></a>Parametry
* Identyfikator ID aparatu.
  
### <a name="getidentity"></a>Żądanie GetIdentity
Pobierz obiekt tożsamości.
  
#### <a name="returns"></a>Zwraca
Odwołanie do tożsamości w obiekcie ustawień. 
**Zobacz też**: mip::Identity
  
### <a name="setidentity"></a>SetIdentity
Obiekt tożsamości zestawu.
  
#### <a name="parameters"></a>Parametry
* tożsamość unikatową tożsamość użytkownika. 
**Zobacz też**: mip::Identity
  
### <a name="getclientdata"></a>GetClientData
Pobierz dane klienta w ustawieniach.
  
#### <a name="returns"></a>Zwraca
Ciąg danych określony przez klienta.
  
### <a name="setclientdata"></a>SetClientData
Ustaw ciąg danych klienta.
  
#### <a name="parameters"></a>Parametry
* Dane klienckie użytkownik określił danych.
  
### <a name="getlocale"></a>GetLocale
Pobierz ustawienia ustawienia regionalne.
  
#### <a name="returns"></a>Zwraca
Ustawienia regionalne.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Określ ustawienia niestandardowe, używane dla funkcji bramkowanie i testowania.
  
#### <a name="parameters"></a>Parametry
* customSettings Lista par nazwa/wartość.
  
### <a name="getcustomsettings"></a>GetCustomSettings
Określ ustawienia niestandardowe, używane dla funkcji bramkowanie i testowania.
  
#### <a name="parameters"></a>Parametry
* Lista par nazwa/wartość.
  
### <a name="setsessionid"></a>SetSessionId
Ustaw identyfikator sesji używany do telemetrii klient jest zdefiniowany.
  
#### <a name="parameters"></a>Parametry
* Identyfikator sesji unikatowy ciąg, który łączy zdarzenia telemetrii.
  
### <a name="getsessionid"></a>GetSessionId
Pobierz identyfikator sesji, unikatowy identyfikator.
  
#### <a name="returns"></a>Zwraca
Identyfikator sesji.