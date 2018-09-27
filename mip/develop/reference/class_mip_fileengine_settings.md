# <a name="class-mipfileenginesettings"></a>Klasa mip::FileEngine::Settings 
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Ustawienia publicznego (const std::string & engineId, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  Tworzy wystąpienie z podanych parametrów.
 Ustawienia publicznego (const tożsamości i tożsamości, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  Tworzy wystąpienie z podanych parametrów.
 publiczne std::string const & GetEngineId() const  |  Zwraca aparat, identyfikator.
 Identyfikator publiczny const & GetIdentity() const  |  Zwraca aparatu tożsamości.
 publiczne SetIdentity void (const tożsamości i tożsamości)  |  Ustawia tożsamość aparatu.
 publiczne std::string const & GetClientData() const  |  Zwraca dane klienta aparatu.
 publiczne std::string const & GetLocale() const  |  Zwróć aparatu ustawień regionalnych.
publiczne SetCustomSettings void (const std::vector < std::pair < std::string, std::string >> & wartość)  |  Ustawia listę par nazw i wartości używane do testowania i eksperymentowania.
publiczne std::vector const < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Pobiera listę par nazw i wartości używane do testowania i eksperymentowania.
 publiczne SetSessionId void (const std::string & sessionId)  |  Ustawia aparat identyfikator sesji.
 publiczne std::string const & GetSessionId() const  |  Zwraca identyfikator sesji aparatu.
 publiczne SetProtectionCloudEndpointBaseUrl void (const std::string & protectionCloudEndpointBaseUrl)  |  Ustawia ochronę chmury punktu końcowego podstawowego adresu url, używany do określenia granic chmury.
 publiczne std::string const & GetProtectionCloudEndpointBaseUrl() const  |  Pobiera cloudEndpointBaseUrl.
 publiczne SetProtectionOnlyEngine void (const protectionOnly wartość logiczna)  |  Ustawia tylko wskaźnika aparat ochrony — Brak zasad/etykiety.
 publiczne bool const IsProtectionOnlyEngine() const  |  Zwróć tylko wskaźnika aparat ochrony — Brak zasad/etykiety.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Tworzy wystąpienie z podanych parametrów.
Umożliwia to tworzenie [ustawienia](class_mip_fileengine_settings.md) wywołać LoadEngineAsync można załadować aparatu istniejących (wcześniej dodane za pośrednictwem AddEngineAsync).

Parametry:  
* **engineId**: Ustaw identyfikator unikatowy aparatu wygenerowany przez AddEngineAsync. 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem, gdy zwolniony, można pobrać z załadowanych aparatu. 


* **Ustawienia regionalne**: aparat możliwych do zlokalizowania w danych wyjściowych, które będą dostępne w tych ustawień regionalnych.


  
### <a name="settings"></a>Ustawienia
Tworzy wystąpienie z podanych parametrów.
Umożliwia to tworzenie [ustawienia](class_mip_fileengine_settings.md) wywołać AddEngineAsync, aby dodać nowy aparat.

Parametry:  
* **tożsamość**: informacje o tożsamości użytkownika, dla którego aparat musi zostać dodany. 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem, gdy zwolniony, można pobrać z załadowanych aparatu. 


* **Ustawienia regionalne**: aparat możliwych do zlokalizowania w danych wyjściowych, które będą dostępne w tych ustawień regionalnych.


  
### <a name="getengineid"></a>GetEngineId
Zwraca aparat, identyfikator.
  
### <a name="getidentity"></a>Żądanie GetIdentity
Zwraca aparatu tożsamości.
  
### <a name="setidentity"></a>SetIdentity
Ustawia tożsamość aparatu.
  
### <a name="getclientdata"></a>GetClientData
Zwraca dane klienta aparatu.
  
### <a name="getlocale"></a>GetLocale
Zwróć aparatu ustawień regionalnych.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Ustawia listę par nazw i wartości używane do testowania i eksperymentowania.
  
### <a name="getcustomsettings"></a>GetCustomSettings
Pobiera listę par nazw i wartości używane do testowania i eksperymentowania.
  
### <a name="setsessionid"></a>SetSessionId
Ustawia aparat identyfikator sesji.
  
### <a name="getsessionid"></a>GetSessionId
Zwraca identyfikator sesji aparatu.
  
### <a name="setprotectioncloudendpointbaseurl"></a>SetProtectionCloudEndpointBaseUrl
Ustawia ochronę chmury punktu końcowego podstawowego adresu url, używany do określenia granic chmury.

Parametry:  
* **protectionCloudEndpointBaseUrl**: podstawowy adres url skojarzony z ochrony punktów końcowych


  
### <a name="getprotectioncloudendpointbaseurl"></a>GetProtectionCloudEndpointBaseUrl
Pobiera cloudEndpointBaseUrl.

  
**Zwraca**: podstawowy adres url skojarzony z ochrony punktów końcowych
  
### <a name="setprotectiononlyengine"></a>SetProtectionOnlyEngine
Ustawia tylko wskaźnika aparat ochrony — Brak zasad/etykiety.
  
### <a name="isprotectiononlyengine"></a>IsProtectionOnlyEngine
Zwróć tylko wskaźnika aparat ochrony — Brak zasad/etykiety.