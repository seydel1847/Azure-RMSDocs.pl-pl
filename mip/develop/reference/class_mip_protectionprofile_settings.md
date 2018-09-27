# <a name="class-mipprotectionprofilesettings"></a>Klasa mip::ProtectionProfile::Settings 
[Ustawienia](class_mip_protectionprofile_settings.md) posługują się [ProtectionProfile](class_mip_protectionprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
Ustawienia publicznego (const std::string ś & cieżka, bool useInMemoryStorage std::shared_ptr const<AuthDelegate>& authDelegate, const std::shared_ptr<ConsentDelegate>& consentDelegate, const std::shared_ptr < ProtectionProfile::Observer > & obserwatora, const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) konstruktora zawierającego obserwatora, używany do wykonywania operacji asynchronicznej.
Ustawienia publicznego (const std::string ś & cieżka, bool useInMemoryStorage std::shared_ptr const<AuthDelegate>& authDelegate, const std::shared_ptr<ConsentDelegate>& consentDelegate, const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) używanego w przypadku operacji synchronicznych konstruktora.
 publiczne std::string const & GetPath() const  |  Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inne dodatkowe materiały ochrony są przechowywane.
 publiczne bool GetUseInMemoryStorage() const  |  Pobierz czy lub pamięci podręczne są przechowywane w pamięci tylko (a nie na dysku)
publiczne std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Pobiera metodę delegowaną uwierzytelniania, używane do uzyskiwania tokenów uwierzytelniania.
publiczne std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Pobiera metodę delegowaną zgody, używane do łączenia się z usługami.
publiczne std::shared_ptr < ProtectionProfile::Observer > GetObserver() const  |  Pobiera obserwatora, który odbiera powiadomienia zdarzeń związanych z [ProtectionProfile](class_mip_protectionprofile.md).
 publiczne ApplicationInfo const & GetApplicationInfo() const  |  Pobiera informacje dotyczące aplikacji, która zużywa ochrony zestawu SDK.
 publiczne OptOutTelemetry() void  |  Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
 publiczne bool IsTelemetryOptedOut() const  |  Pobiera informację określającą, czy należy wyłączyć zbieranie danych telemetrycznych.
publiczne std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Uzyskaj delegata rejestratora (jeśli istnieje) udostępniany przez aplikację.
publiczne SetLoggerDelegate void (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Zastąp domyślną rejestratora.
publiczne std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  Uzyskaj delegata http (jeśli istnieje) udostępniany przez aplikację.
publiczne SetHttpDelegate void (const std::shared_ptr<HttpDelegate>& httpDelegate)  |  Zastępują domyślne stos http za pomocą własnego klienta.
 publiczne bool GetSkipTelemetryInit() const  |  Pobiera informację określającą, czy ma być pomijana inicjowanie telemetrii.
 publiczne SetSkipTelemetryInit() void  |  Wyłącza inicjowanie telemetrii.
 publiczne SetNewFeaturesDisabled() void  |  Wyłącza nowe funkcje.
 publiczne bool AreNewFeaturesDisabled() const  |  Pobiera informację określającą, czy nowe funkcje zostały wyłączone.
 publiczne SetSessionId void (const std::string & sessionId)  |  Określa identyfikator sesji.
 publiczne std::string const & GetSessionId() const  |  Pobiera identyfikator sesji.
 publiczne SetMinimumLogLevel void (LogLevel logLevel)  |  Ustaw poziom minimalna dziennika, która wyzwoli rejestrowania zdarzeń.
 publiczne LogLevel GetMinimumLogLevel() const  |  Pobierz obiekt minimalny poziom dziennika.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) konstruktora zawierającego obserwatora, używany do wykonywania operacji asynchronicznej.

Parametry:  
* **ścieżka**: ścieżka pliku, w której rejestrowanie, dane telemetryczne i inne zabezpieczenia ochrony są przechowywane 


* **useInMemoryStorage**: Store dowolny stan pamięci podręcznej w pamięci, a nie na dysku 


* **authDelegate**: obiektu wywołania zwrotnego, które ma być używany do uwierzytelniania, implementowane przez aplikację kliencką 


* **Obserwator**: [obserwatora](class_mip_protectionprofile_observer.md) wystąpienia, które będą otrzymywać powiadomienia o zdarzeniach związane z [ProtectionProfile](class_mip_protectionprofile.md)


* **applicationInfo**: informacje dotyczące aplikacji, która zużywa ochrony zestawu SDK


  
### <a name="settings"></a>Ustawienia
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) używanego w przypadku operacji synchronicznych konstruktora.

Parametry:  
* **ścieżka**: ścieżka pliku, w której rejestrowanie, dane telemetryczne i inne zabezpieczenia ochrony są przechowywane 


* **useInMemoryStorage**: Store dowolny stan pamięci podręcznej w pamięci, a nie na dysku 


* **authDelegate**: obiektu wywołania zwrotnego, które ma być używany do uwierzytelniania, implementowane przez aplikację kliencką 


* **applicationInfo**: informacje dotyczące aplikacji, która zużywa ochrony zestawu SDK


  
### <a name="getpath"></a>Funkcja GetPath
Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inne dodatkowe materiały ochrony są przechowywane.

  
**Zwraca**: ścieżka w ramach której rejestrowanie, dane telemetryczne i inne dodatkowe materiały ochrony są przechowywane
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Pobierz czy lub pamięci podręczne są przechowywane w pamięci tylko (a nie na dysku)

  
**Zwraca**: wartość True, jeśli pamięci podręczne są przechowywane wyłącznie w pamięci
  
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
Zastąp domyślną rejestratora.

Parametry:  
* **loggerDelegate**: rejestrowanie interfejs wywołania zwrotnego implementowane przez aplikacje klienckie


Ta powinna być wywoływana przez aplikacje klienckie, które używają zapewniali własną implementację rejestratora
  
### <a name="httpdelegate"></a>HttpDelegate
Uzyskaj delegata http (jeśli istnieje) udostępniany przez aplikację.

  
**Zwraca**: delegata Http do użycia dla operacji http
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
Zastępują domyślne stos http za pomocą własnego klienta.

Parametry:  
* **httpDelegate**: Http interfejs wywołania zwrotnego implementowane przez aplikację kliencką


  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Pobiera informację określającą, czy ma być pomijana inicjowanie telemetrii.

  
**Zwraca**: Określa, czy ma być pomijana inicjowanie telemetrii
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Wyłącza inicjowanie telemetrii.
To nie zwykle należy wywołać przez aplikacje klienckie, zamiast jest on używany przez zestaw SDK pliku, (które już inicjuje telemetrii) aby uniknąć zduplikowanych inicjowania
  
### <a name="setnewfeaturesdisabled"></a>SetNewFeaturesDisabled
Wyłącza nowe funkcje.
W przypadku aplikacji, których nie chcesz wypróbowywać nowe funkcje
  
### <a name="arenewfeaturesdisabled"></a>AreNewFeaturesDisabled
Pobiera informację określającą, czy nowe funkcje zostały wyłączone.

  
**Zwraca**: Określa, czy nowe funkcje zostały wyłączone
  
### <a name="setsessionid"></a>SetSessionId
Określa identyfikator sesji.

Parametry:  
* **Identyfikator sesji**: identyfikator sesji, który będzie używany w celu skorelowania dzienników/telemetrii


  
### <a name="getsessionid"></a>GetSessionId
Pobiera identyfikator sesji.

  
**Zwraca**: identyfikator sesji, który będzie używany w celu skorelowania dzienników/telemetrii
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
Ustaw poziom minimalna dziennika, która wyzwoli rejestrowania zdarzeń.

Parametry:  
* **logLevel**: minimalny poziom rejestrowania wyzwalające zdarzenia rejestrowania. 



  
**Zwraca**: True
  
### <a name="loglevel"></a>LogLevel
Pobierz obiekt minimalny poziom dziennika.

  
**Zwraca**: co najmniej poziom rejestrowania, który spowoduje wyzwolenie zdarzenia rejestrowania.