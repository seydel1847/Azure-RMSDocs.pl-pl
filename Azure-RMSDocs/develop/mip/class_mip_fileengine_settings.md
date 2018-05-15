# <a name="class-mipfileenginesettings"></a>Klasa mip::FileEngine::Settings 
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Ustawienia publicznego (const std::string & identyfikator, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  Tworzy wystąpienie z podanych parametrów.
 Ustawienia publicznego (const tożsamości i tożsamości, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  Tworzy wystąpienie z podanych parametrów.
 publiczny std::string const & GetId() const  |  Zwraca aparat identyfikatora.
 publiczny tożsamości const & GetIdentity() const  |  Zwraca aparat tożsamości.
 publiczny SetIdentity void (const tożsamości i tożsamości)  |  Ustawia tożsamość aparatu.
 publiczny std::string const & GetClientData() const  |  Zwraca dane klienta aparatu.
 publiczny std::string const & GetLocale() const  |  Zwróć ustawień regionalnych aparatu.
publiczny SetCustomSettings void (const std::vector < std::pair < std::string, std::string >> & wartość)  |  Ustawia listę par nazw i wartości używane do testowania i eksperymenty.
publiczny std::vector const < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Pobiera listę par nazw i wartości używane do testowania i eksperymenty.
 publiczny SetSessionId void (const std::string & sessionId)  |  Ustawia aparat identyfikator sesji.
 publiczny std::string const & GetSessionId() const  |  Zwraca identyfikator sesji aparatu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Tworzy wystąpienie z podanych parametrów.
Umożliwia to tworzenie [ustawienia](class_mip_fileengine_settings.md) do wywołania LoadEngineAsync można załadować aparatu istniejących (wcześniej dodane za pośrednictwem AddEngineAsync).

Parametry:  
* **Identyfikator**: Ustaw identyfikator unikatowy aparat generowane przez AddEngineAsync.


  
### <a name="settings"></a>Ustawienia
Tworzy wystąpienie z podanych parametrów.
Umożliwia to tworzenie [ustawienia](class_mip_fileengine_settings.md) do wywołania AddEngineAsync, aby dodać nowy aparat.

Parametry:  
* **tożsamość**: informacje o tożsamości użytkownika, dla którego aparat musi zostać dodany.


  
### <a name="getid"></a>GetId
Zwraca aparat identyfikatora.
  
### <a name="getidentity"></a>Żądanie GetIdentity
Zwraca aparat tożsamości.
  
### <a name="setidentity"></a>SetIdentity
Ustawia tożsamość aparatu.
  
### <a name="getclientdata"></a>GetClientData
Zwraca dane klienta aparatu.
  
### <a name="getlocale"></a>GetLocale
Zwróć ustawień regionalnych aparatu.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Ustawia listę par nazw i wartości używane do testowania i eksperymenty.
  
### <a name="getcustomsettings"></a>GetCustomSettings
Pobiera listę par nazw i wartości używane do testowania i eksperymenty.
  
### <a name="setsessionid"></a>SetSessionId
Ustawia aparat identyfikator sesji.
  
### <a name="getsessionid"></a>GetSessionId
Zwraca identyfikator sesji aparatu.