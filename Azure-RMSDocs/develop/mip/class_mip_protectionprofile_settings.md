# <a name="class-mipprotectionprofilesettings"></a>Klasa mip::ProtectionProfile::Settings 
[Ustawienia](#classmip_1_1_protection_profile_1_1_settings) używane przez [ProtectionProfile](#classmip_1_1_protection_profile) podczas jej tworzenia i przez cały cykl jej życia.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego SettingsProtectionProfile::Observer > & obserwatora, const ApplicationInfo & applicationInfo) std::string const publicznego wbudowanego & Funkcja GetPath | Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inne zabezpieczenia ochrony są przechowywane.
wbudowany publicznego const std::shared_ptr < ProtectionProfile::Observer > & GetObserver publicznego wbudowanego const ApplicationInfo & GetApplicationInfo | Pobiera informacje dotyczące aplikacji, która zajmuje ochrony zestawu SDK.
wbudowany publicznego bool GetSkipTelemetryInit | Pobiera czy inicjowanie telemetrii ma być pomijana.
wbudowany publicznego void SetSkipTelemetryInit | Wyłącza inicjowanie telemetrii.
wbudowany publicznego void SetSessionId | Ustawia identyfikator sesji. const std::string publicznego wbudowanego & GetSessionId | Pobiera identyfikator sesji.
## <a name="members"></a>Elementy członkowskie
### <a name="settings"></a>Ustawienia
[ProtectionProfile::Settings](#classmip_1_1_protection_profile_1_1_settings) konstruktora.
#### <a name="parameters"></a>Parametry
* Ścieżka pliku ścieżki pod które rejestrowania, telemetrii i inne zabezpieczenia ochrony jest przechowywany 
* Obserwator [obserwatora](#classmip_1_1_protection_profile_1_1_observer) wystąpienia, który będzie otrzymywał powiadomienia o zdarzeniach związanych z [ProtectionProfile](#classmip_1_1_protection_profile)
* applicationInfo informacje dotyczące aplikacji, która zajmuje ochrony zestawu SDK
### <a name="getpath"></a>Funkcja GetPath
Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inne zabezpieczenia ochrony są przechowywane.
#### <a name="returns"></a>Zwraca
Ścieżki, w których rejestrowania, telemetrii i inne zabezpieczenia ochrony jest przechowywany
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Pobiera obserwatora powiadomienia, które receieves zdarzeń związanych z [ProtectionProfile](#classmip_1_1_protection_profile).
#### <a name="returns"></a>Zwraca
[Obserwator](#classmip_1_1_protection_profile_1_1_observer) powiadomienia, które receieves zdarzeń związanych z [ProtectionProfile](#classmip_1_1_protection_profile)
### <a name="applicationinfo"></a>ApplicationInfo
Pobiera informacje dotyczące aplikacji, która zajmuje ochrony zestawu SDK.
#### <a name="returns"></a>Zwraca
Informacje dotyczące aplikacji, która zajmuje ochrony zestawu SDK
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Pobiera czy inicjowanie telemetrii ma być pomijana.
#### <a name="returns"></a>Zwraca
Określa, czy ma być pomijana inicjowanie telemetrii
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Wyłącza inicjowanie telemetrii.
To nie powinien zwykle być wywołany przez aplikacje klienckie, a nie jest on używany przez zestaw SDK pliku, (który inicjuje już telemetrii) aby uniknąć zduplikowanych inicjowania
### <a name="setsessionid"></a>SetSessionId
Ustawia identyfikator sesji.
#### <a name="parameters"></a>Parametry
* Identyfikator sesji identyfikator sesji, która będzie używana do skorelowania dzienników/telemetrii
### <a name="getsessionid"></a>GetSessionId
Pobiera identyfikator sesji.
#### <a name="returns"></a>Zwraca
Identyfikator sesji, która będzie używana do skorelowania dzienników/telemetrii