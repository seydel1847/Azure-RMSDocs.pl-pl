# <a name="class-mipfileprofilesettings"></a>Klasa mip::FileProfile::Settings 
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego ustawień (const std::shared_ptr std::string & ścieżki, bool useInMemoryStorage<AuthDelegate> authDelegate, std::shared_ptr<Observer> obserwatora, const ApplicationInfo & applicationInfo)  |  Interfejs służący do konfigurowania profilu.
~Settings() publicznych wbudowany  |  
const std::string publicznego wbudowanego & GetPath() const  |  
wbudowany publicznego bool GetUseInMemoryStorage() const  |  
std::shared_ptr publicznych wbudowanego<AuthDelegate> GetAuthDelegate() const  |  
std::shared_ptr publicznych wbudowanego<Observer> GetObserver() const  |  
wbudowany publicznego const ApplicationInfo GetApplicationInfo() const  |  
wbudowany publicznego bool GetSkipTelemetryInit() const  |  
wbudowany publicznego void SetSkipTelemetryInit()  |  
wbudowany publicznego void SetSessionId (const std::string & sessionId)  |  Ustawia identyfikatora sesji profilu.
const std::string publicznego wbudowanego & GetSessionId() const  |  Zwraca identyfikator sesji profilu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Interfejs służący do konfigurowania profilu.
  
#### <a name="parameters"></a>Parametry
* Implementacja klasy obserwatora [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) interfejsu. Może być nullptr.
  
### <a name="settings"></a>~ Ustawienia
  
### <a name="getpath"></a>Funkcja GetPath
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
  
### <a name="getauthdelegate"></a>GetAuthDelegate
  
### <a name="observer"></a>Obserwatora
  
### <a name="applicationinfo"></a>ApplicationInfo
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
  
### <a name="setsessionid"></a>SetSessionId
Ustawia identyfikatora sesji profilu.
  
### <a name="getsessionid"></a>GetSessionId
Zwraca identyfikator sesji profilu.