# <a name="class-mipfileprofilesettings"></a>Klasa mip::FileProfile::Settings 
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego SettingsObserver > obserwatora, const ApplicationInfo & applicationInfo) | Interfejs służący do konfigurowania profilu.
wbudowany publicznego ~ ustawienia | 
const std::string publicznego wbudowanego & Funkcja GetPath | 
wbudowany publicznego bool GetUseInMemoryStorage | 
wbudowany publicznego std::shared_ptr < AuthDelegate > GetAuthDelegate | 
wbudowany publicznego std::shared_ptr < obserwatora > GetObserver | 
wbudowany publicznego const ApplicationInfo GetApplicationInfo | 
wbudowany publicznego bool GetSkipTelemetryInit | 
wbudowany publicznego void SetSkipTelemetryInit | 
wbudowany publicznego void SetSessionId | Ustawia identyfikatora sesji profilu.
const std::string publicznego wbudowanego & GetSessionId | Zwraca identyfikator sesji profilu.
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