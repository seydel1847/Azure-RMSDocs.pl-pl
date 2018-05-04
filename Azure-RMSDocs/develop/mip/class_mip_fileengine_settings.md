# <a name="class-mipfileenginesettings"></a>Klasa mip::FileEngine::Settings 
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego ustawień (const std::string & identyfikator, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  Tworzy wystąpienie z podanych parametrów.
wbudowany publicznego ustawień (const tożsamości i tożsamości, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  Tworzy wystąpienie z podanych parametrów.
const std::string publicznego wbudowanego & GetId() const  |  Zwraca aparat identyfikatora.
wbudowany publicznego const tożsamości i GetIdentity() const  |  Zwraca aparat tożsamości.
wbudowany publicznego void SetIdentity (const tożsamości i tożsamości)  |  Ustawia tożsamość aparatu.
const std::string publicznego wbudowanego & GetClientData() const  |  Zwraca dane klienta aparatu.
const std::string publicznego wbudowanego & GetLocale() const  |  Zwróć ustawień regionalnych aparatu.
wbudowany publicznego void SetCustomSettings (const std::vector < std::pair < std::string, std::string >> & wartość)  |  Ustawia listę par nazw i wartości używane do testowania i eksperymenty.
wbudowany publicznego const std::vector < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Pobiera listę par nazw i wartości używane do testowania i eksperymenty.
wbudowany publicznego void SetSessionId (const std::string & sessionId)  |  Ustawia aparat identyfikator sesji.
const std::string publicznego wbudowanego & GetSessionId() const  |  Zwraca identyfikator sesji aparatu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Tworzy wystąpienie z podanych parametrów.
Umożliwia to tworzenie [ustawienia](#classmip_1_1_file_engine_1_1_settings) do wywołania LoadEngineAsync można załadować aparatu istniejących (wcześniej dodane za pośrednictwem AddEngineAsync).
  
#### <a name="parameters"></a>Parametry
* Identyfikator ustaw ją na identyfikator unikatowy aparat generowane przez AddEngineAsync.
  
### <a name="settings"></a>Ustawienia
Tworzy wystąpienie z podanych parametrów.
Umożliwia to tworzenie [ustawienia](#classmip_1_1_file_engine_1_1_settings) do wywołania AddEngineAsync, aby dodać nowy aparat.
  
#### <a name="parameters"></a>Parametry
* informacje o tożsamości tożsamości użytkownika, dla którego aparat musi zostać dodany.
  
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