# <a name="class-mipprotectionprofilesettings"></a>Klasa mip::ProtectionProfile::Settings 
[Ustawienia](class_mip_protectionprofile_settings.md) posługują się [ProtectionProfile](class_mip_protectionprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
Ustawienia publicznego (const isLicenseCachingEnabled bool std::string ś & cieżka, bool useInMemoryStorage, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<ConsentDelegate>& consentDelegate, const std::shared_ptr < ProtectionProfile::Observer > & obserwatora, const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) konstruktora.
 publiczne std::string const & GetPath() const  |  Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inne dodatkowe materiały ochrony są przechowywane.
 publiczne bool GetUseInMemoryStorage() const  |  Pobierz czy lub pamięci podręczne są przechowywane w pamięci tylko (a nie na dysku)
 publiczne bool IsLicenseCachingEnabled() const  |  Pobierz czy lub włączone jest buforowanie licencji.
publiczne std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Pobiera metodę delegowaną uwierzytelniania, używane do uzyskiwania tokenów uwierzytelniania.
publiczne std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Pobiera metodę delegowaną zgody, używane do łączenia się z usługami.
publiczne std::shared_ptr const < ProtectionProfile::Observer > & GetObserver() const  |  Pobiera obserwatora, który odbiera powiadomienia zdarzeń związanych z [ProtectionProfile](class_mip_protectionprofile.md).
 publiczne ApplicationInfo const & GetApplicationInfo() const  |  Pobiera informacje dotyczące aplikacji, która zużywa ochrony zestawu SDK.
 publiczne OptOutTelemetry() void  |  Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
 publiczne bool IsTelemetryOptedOut() const  |  Pobiera informację określającą, czy należy wyłączyć zbieranie danych telemetrycznych.
publiczne std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Uzyskaj delegata rejestratora (jeśli istnieje) udostępniany przez aplikację.
publiczne SetLoggerDelegate void (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Użyć implementacji zewnętrznych rejestratora.
 publiczne bool GetSkipTelemetryInit() const  |  Pobiera informację określającą, czy ma być pomijana inicjowanie telemetrii.
 publiczne SetSkipTelemetryInit() void  |  Wyłącza inicjowanie telemetrii.
 publiczne SetSessionId void (const std::string & sessionId)  |  Określa identyfikator sesji.
 publiczne std::string const & GetSessionId() const  |  Pobiera identyfikator sesji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) konstruktora.

Parametry:  
* **ścieżka**: ścieżka pliku, w której rejestrowanie, dane telemetryczne i inne zabezpieczenia ochrony są przechowywane 


* **useInMemoryStorage**: Store dowolny stan pamięci podręcznej w pamięci, a nie na dysku 


* **isLicenseCachingEnabled**: Włączanie lub wyłączanie buforowania licencji zestawu sdk ochrony 


* **authDelegate**: obiektu wywołania zwrotnego, które ma być używany do uwierzytelniania, implementowane przez aplikację kliencką 


* **Obserwator**: [obserwatora](class_mip_protectionprofile_observer.md) wystąpienia, które będą otrzymywać powiadomienia o zdarzeniach związane z [ProtectionProfile](class_mip_protectionprofile.md)


* **applicationInfo**: informacje dotyczące aplikacji, która zużywa ochrony zestawu SDK


  
### <a name="getpath"></a>Funkcja GetPath
Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inne dodatkowe materiały ochrony są przechowywane.

  
**Zwraca**: ścieżka w ramach której rejestrowanie, dane telemetryczne i inne dodatkowe materiały ochrony są przechowywane
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Pobierz czy lub pamięci podręczne są przechowywane w pamięci tylko (a nie na dysku)

  
**Zwraca**: wartość True, jeśli pamięci podręczne są przechowywane wyłącznie w pamięci
  
### <a name="islicensecachingenabled"></a>IsLicenseCachingEnabled
Pobierz czy lub włączone jest buforowanie licencji.

  
**Zwraca**: wartość True, jeśli włączone jest buforowanie licencji usługi ochrony zestawu SDK
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Pobiera metodę delegowaną uwierzytelniania, używane do uzyskiwania tokenów uwierzytelniania.

  
**Zwraca**: Delegowanie uwierzytelniania używany do uzyskiwania tokenów uwierzytelniania
  
### <a name="consentdelegate"></a>ConsentDelegate
Pobiera metodę delegowaną zgody, używane do łączenia się z usługami.

  
**Zwraca**: zgody delegata używany do łączenia się z usługami
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Pobiera obserwatora, który odbiera powiadomienia zdarzeń związanych z [ProtectionProfile](class_mip_protectionprofile.md).

  
**Zwraca**: [obserwatora](class_mip_protectionprofile_observer.md) która odbiera powiadomienia o zdarzenia związane z [ProtectionProfile](class_mip_protectionprofile.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
Pobiera informacje dotyczące aplikacji, która zużywa ochrony zestawu SDK.

  
**Zwraca**: informacje dotyczące aplikacji, która zużywa ochrony zestawu SDK
  
### <a name="optouttelemetry"></a>OptOutTelemetry
Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Pobiera informację określającą, czy należy wyłączyć zbieranie danych telemetrycznych.

  
**Zwraca**: Określa, czy należy wyłączyć zbieranie danych telemetrycznych
  
### <a name="loggerdelegate"></a>LoggerDelegate
Uzyskaj delegata rejestratora (jeśli istnieje) udostępniany przez aplikację.

  
**Zwraca**: Rejestrator delegata służący do rejestrowania
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
Użyć implementacji zewnętrznych rejestratora.
Ta powinna być wywoływana przez aplikacje klienckie, jeśli chcą używać własnych implementacji rejestratora
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Pobiera informację określającą, czy ma być pomijana inicjowanie telemetrii.

  
**Zwraca**: Określa, czy ma być pomijana inicjowanie telemetrii
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Wyłącza inicjowanie telemetrii.
To nie zwykle należy wywołać przez aplikacje klienckie, zamiast jest on używany przez zestaw SDK pliku, (które już inicjuje telemetrii) aby uniknąć zduplikowanych inicjowania
  
### <a name="setsessionid"></a>SetSessionId
Określa identyfikator sesji.

Parametry:  
* **Identyfikator sesji**: identyfikator sesji, który będzie używany w celu skorelowania dzienników/telemetrii


  
### <a name="getsessionid"></a>GetSessionId
Pobiera identyfikator sesji.

  
**Zwraca**: identyfikator sesji, który będzie używany w celu skorelowania dzienników/telemetrii