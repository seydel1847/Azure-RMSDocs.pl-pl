# <a name="class-mipprofilesettings"></a>Klasa mip::Profile::Settings 
[Ustawienia](class_mip_profile_settings.md) posługują się [profilu](class_mip_profile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
Ustawienia publicznego (const std::string ś & cieżka, bool useInMemoryStorage std::shared_ptr const<AuthDelegate>& authDelegate, const std::shared_ptr < Profile::Observer > & obserwatora, const ApplicationInfo & applicationInfo)  |  Interfejs do konfigurowania profilu.
 publiczne std::string const & GetPath() const  |  Pobierz ścieżkę do przechowywanego stanu.
 publiczne bool GetUseInMemoryStorage() const  |  Pobierz flagi użycia magazynu w pamięci.
publiczne std::shared_ptr const<AuthDelegate>& GetAuthDelegate() const  |  Uzyskaj delegowanie uwierzytelniania.
publiczne std::shared_ptr const < Profile::Observer > & GetObserver() const  |  Uzyskaj obserwatora zdarzeń.
 publiczne const ApplicationInfo GetApplicationInfo() const  |  Uzyskaj informacje o aplikacji.
publiczne std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Uzyskaj delegata rejestratora (jeśli istnieje) udostępniany przez aplikację.
publiczne SetLoggerDelegate void (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Użyć implementacji zewnętrznych rejestratora.
 publiczne OptOutTelemetry() void  |  Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
 publiczne bool IsTelemetryOptedOut() const  |  Pobiera informację określającą, czy należy wyłączyć zbieranie danych telemetrycznych.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Interfejs do konfigurowania profilu.

Parametry:  
* **ścieżka**: ścieżka do katalogu, w którym zestaw sdk będzie przechowywać stanu profilowania. 


* **useInMemoryStorage**: flagę wskazującą, czy stan powinny być przechowywane na dysku. 


* **authDelegate**: Delegowanie uwierzytelniania używany przez zestaw SDK do uzyskiwania tokenów uwierzytelniania. 


* **Obserwator**: Implementacja klasy [Profile::Observer](class_mip_profile_observer.md) interfejsu. Może być nullptr. 


* **applicationInfo**: identyfikatory aplikacji używane dla dostępu do usługi.


  
### <a name="getpath"></a>Funkcja GetPath
Pobierz ścieżkę do przechowywanego stanu.

  
**Zwraca**: ścieżka do zapisanego stanu.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Pobierz flagi użycia magazynu w pamięci.

  
**Zwraca**: wartość True, jeśli użycia w pamięci jest ustawiony przeciwnym razie wartość false.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Uzyskaj delegowanie uwierzytelniania.

  
**Zwraca**: Delegowanie uwierzytelniania.
  
### <a name="profileobserver"></a>Profile::Observer
Uzyskaj obserwatora zdarzeń.

  
**Zwraca**: obserwatora zdarzeń.
  
### <a name="applicationinfo"></a>ApplicationInfo
Uzyskaj informacje o aplikacji.

  
**Zwraca**: informacje o aplikacji.
  
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