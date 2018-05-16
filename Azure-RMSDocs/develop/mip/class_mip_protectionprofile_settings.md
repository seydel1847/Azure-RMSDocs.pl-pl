# <a name="class-mipprotectionprofilesettings"></a>Klasa mip::ProtectionProfile::Settings 
[Ustawienia](class_mip_protectionprofile_settings.md) używane przez [ProtectionProfile](class_mip_protectionprofile.md) podczas jej tworzenia i przez cały cykl jej życia.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
Ustawienia publicznego (const std::string & ścieżki, const std::shared_ptr < ProtectionProfile::Observer > & obserwatora, const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) konstruktora.
 publiczny std::string const & GetPath() const  |  Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inne zabezpieczenia ochrony są przechowywane.
publiczny std::shared_ptr const < ProtectionProfile::Observer > & GetObserver() const  |  Pobiera obserwatora powiadomienia, które receieves zdarzeń związanych z [ProtectionProfile](class_mip_protectionprofile.md).
 publiczny ApplicationInfo const & GetApplicationInfo() const  |  Pobiera informacje dotyczące aplikacji, która zajmuje ochrony zestawu SDK.
 publiczny bool GetSkipTelemetryInit() const  |  Pobiera czy inicjowanie telemetrii ma być pomijana.
 publiczny SetSkipTelemetryInit() void  |  Wyłącza inicjowanie telemetrii.
 publiczny SetSessionId void (const std::string & sessionId)  |  Ustawia identyfikator sesji.
 publiczny std::string const & GetSessionId() const  |  Pobiera identyfikator sesji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) konstruktora.

Parametry:  
* **ścieżka**: ścieżka pliku, pod którym rejestrowania, telemetrii i inne zabezpieczenia ochrony jest przechowywany 


* **Obserwator**: [obserwatora](class_mip_protectionprofile_observer.md) wystąpienia, który będzie otrzymywał powiadomienia o zdarzeniach związanych z [ProtectionProfile](class_mip_protectionprofile.md)


* **applicationInfo**: informacje dotyczące aplikacji, która zajmuje ochrony zestawu SDK


  
### <a name="getpath"></a>Funkcja GetPath
Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inne zabezpieczenia ochrony są przechowywane.

  
**Zwraca**: ścieżki, w których rejestrowania, telemetrii i inne zabezpieczenia ochrony jest przechowywany
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Pobiera obserwatora powiadomienia, które receieves zdarzeń związanych z [ProtectionProfile](class_mip_protectionprofile.md).

  
**Zwraca**: [obserwatora](class_mip_protectionprofile_observer.md) powiadomienia, które receieves zdarzeń związanych z [ProtectionProfile](class_mip_protectionprofile.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
Pobiera informacje dotyczące aplikacji, która zajmuje ochrony zestawu SDK.

  
**Zwraca**: informacje dotyczące aplikacji, która zajmuje ochrony zestawu SDK
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Pobiera czy inicjowanie telemetrii ma być pomijana.

  
**Zwraca**: Określa, czy ma być pomijana inicjowanie telemetrii
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Wyłącza inicjowanie telemetrii.
To nie powinien zwykle być wywołany przez aplikacje klienckie, a nie jest on używany przez zestaw SDK pliku, (który inicjuje już telemetrii) aby uniknąć zduplikowanych inicjowania
  
### <a name="setsessionid"></a>SetSessionId
Ustawia identyfikator sesji.

Parametry:  
* **Identyfikator sesji**: identyfikator sesji, która będzie używana do skorelowania dzienników/telemetrii


  
### <a name="getsessionid"></a>GetSessionId
Pobiera identyfikator sesji.

  
**Zwraca**: identyfikator sesji, która będzie używana do skorelowania dzienników/telemetrii