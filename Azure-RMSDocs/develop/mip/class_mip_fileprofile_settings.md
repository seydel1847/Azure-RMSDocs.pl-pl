# <a name="class-mipfileprofilesettings"></a>Klasa mip::FileProfile::Settings 
[Ustawienia](class_mip_fileprofile_settings.md) posługują się [FileProfile](class_mip_fileprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
Ustawienia publicznego (const isLicenseCachingEnabled bool std::string ś & cieżka, bool useInMemoryStorage, std::shared_ptr<AuthDelegate> authDelegate, std::shared_ptr<ConsentDelegate> consentDelegate, std::shared_ptr<Observer> obserwatora, stała ApplicationInfo & applicationInfo)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md) konstruktora.
 publiczne std::string const & GetPath() const  |  Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inny stan trwały są przechowywane.
 publiczne bool GetUseInMemoryStorage() const  |  Pobiera informację określającą, czy wszystkie stany powinny być przechowywane w pamięci, (a nie na dysku)
 publiczne bool IsLicenseCachingEnabled() const  |  Pobierz czy lub włączone jest buforowanie licencji.
publiczne std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Pobiera metodę delegowaną uwierzytelniania, używane do uzyskiwania tokenów uwierzytelniania.
publiczne std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Pobiera metodę delegowaną zgody, używany do zażądania zgody użytkownika łączenia się z usługami.
publiczne std::shared_ptr<Observer> GetObserver() const  |  Pobiera obserwatora, który odbiera powiadomienia zdarzeń związanych z [FileProfile](class_mip_fileprofile.md).
 publiczne const ApplicationInfo GetApplicationInfo() const  |  Pobiera informacje dotyczące aplikacji, która zużywa zestawu SDK.
 publiczne bool GetSkipTelemetryInit() const  |  Pobiera informację określającą, czy ma być pomijana inicjowanie telemetrii.
 publiczne SetSkipTelemetryInit() void  |  Wyłącza inicjowanie telemetrii.
publiczne std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Uzyskaj delegata rejestratora (jeśli istnieje) udostępniany przez aplikację.
publiczne SetLoggerDelegate void (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Użyć implementacji zewnętrznych rejestratora.
 publiczne OptOutTelemetry() void  |  Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
 publiczne bool IsTelemetryOptedOut() const  |  Pobiera informację określającą, czy należy wyłączyć zbieranie danych telemetrycznych.
 publiczne SetSessionId void (const std::string & sessionId)  |  Określa identyfikator sesji.
 publiczne std::string const & GetSessionId() const  |  Pobiera identyfikator sesji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
[FileProfile::Settings](class_mip_fileprofile_settings.md) konstruktora.

Parametry:  
* **ścieżka**: ścieżka pliku, w której rejestrowanie, dane telemetryczne i inne są przechowywane trwały stan 


* **useInMemoryStorage**: Określa, czy wszystkie stany powinny być przechowywane w pamięci (a nie na dysku) 


* **isLicenseCachingEnabled**: Włączanie lub wyłączanie buforowania licencji ochrony 


* **authDelegate**: Delegowanie uwierzytelniania używany do uzyskiwania tokenów uwierzytelniania 


* **Obserwator**: [obserwatora](class_mip_fileprofile_observer.md) wystąpienia, które będą otrzymywać powiadomienia o zdarzeniach związane z [FileProfile](class_mip_fileprofile.md)


* **applicationInfo**: informacje dotyczące aplikacji, która zużywa zestawu SDK


  
### <a name="getpath"></a>Funkcja GetPath
Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inny stan trwały są przechowywane.

  
**Zwraca**: ścieżka w ramach której rejestrowanie, dane telemetryczne i inne są przechowywane przez stan trwały
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Pobiera informację określającą, czy wszystkie stany powinny być przechowywane w pamięci, (a nie na dysku)

  
**Zwraca**: Określa, czy wszystkie stany powinny być przechowywane w pamięci (a nie na dysku)
  
### <a name="islicensecachingenabled"></a>IsLicenseCachingEnabled
Pobierz czy lub włączone jest buforowanie licencji.

  
**Zwraca**: wartość True, jeśli pamięci podręczne są przechowywane wyłącznie w pamięci
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Pobiera metodę delegowaną uwierzytelniania, używane do uzyskiwania tokenów uwierzytelniania.

  
**Zwraca**: Delegowanie uwierzytelniania używany do uzyskiwania tokenów uwierzytelniania
  
### <a name="consentdelegate"></a>ConsentDelegate
Pobiera metodę delegowaną zgody, używany do zażądania zgody użytkownika łączenia się z usługami.

  
**Zwraca**: zgody delegata używany do żądania zgoda użytkownika
  
### <a name="observer"></a>Obserwator
Pobiera obserwatora, który odbiera powiadomienia zdarzeń związanych z [FileProfile](class_mip_fileprofile.md).

  
**Zwraca**: [obserwatora](class_mip_fileprofile_observer.md) która odbiera powiadomienia o zdarzenia związane z [FileProfile](class_mip_fileprofile.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
Pobiera informacje dotyczące aplikacji, która zużywa zestawu SDK.

  
**Zwraca**: informacje dotyczące aplikacji, która zużywa zestawu SDK
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Pobiera informację określającą, czy ma być pomijana inicjowanie telemetrii.

  
**Zwraca**: Określa, czy ma być pomijana inicjowanie telemetrii
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Wyłącza inicjowanie telemetrii.
To nie zwykle należy wywołać przez aplikacje klienckie, zamiast jest on używany przez zestaw SDK pliku, (które już inicjuje telemetrii) aby uniknąć zduplikowanych inicjowania
  
### <a name="loggerdelegate"></a>LoggerDelegate
Uzyskaj delegata rejestratora (jeśli istnieje) udostępniany przez aplikację.

  
**Zwraca**: Rejestrator delegata służący do rejestrowania
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
Użyć implementacji zewnętrznych rejestratora.
Ta powinna być wywoływana przez aplikacje klienckie, jeśli chcą używać własnych implementacji rejestratora
  
### <a name="optouttelemetry"></a>OptOutTelemetry
Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Pobiera informację określającą, czy należy wyłączyć zbieranie danych telemetrycznych.

  
**Zwraca**: Określa, czy należy wyłączyć zbieranie danych telemetrycznych
  
### <a name="setsessionid"></a>SetSessionId
Określa identyfikator sesji.

Parametry:  
* **Identyfikator sesji**: identyfikator sesji, który będzie używany w celu skorelowania dzienników/telemetrii


  
### <a name="getsessionid"></a>GetSessionId
Pobiera identyfikator sesji.

  
**Zwraca**: identyfikator sesji, który będzie używany w celu skorelowania dzienników/telemetrii