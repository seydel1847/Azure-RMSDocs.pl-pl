# <a name="class-mipprotectionprofile"></a>Klasa mip::ProtectionProfile 
[ProtectionProfile](class_mip_protectionprofile.md) jest klasą głównego do wykonywania operacji ochrony.
Aplikację należy utworzyć [ProtectionProfile](class_mip_protectionprofile.md) przed wykonaniem jakichkolwiek działań ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Pobiera ustawienia używane przez [ProtectionProfile](class_mip_protectionprofile.md) podczas jego inicjowania i w okresie swojego istnienia.
publiczne ListEnginesAsync void (const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się listy aparatów operacji.
publiczne AddEngineAsync void (const ProtectionEngine::Settings & Ustawienia, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się dodanie nowego aparatu ochrony do profilu.
publiczne DeleteEngineAsync void (const std::string & engineId, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się usuwanie aparat ochrony z danym identyfikatorem. Wszystkie dane dla danego aparatu zostaną całkowicie usunięte.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Pobiera ustawienia używane przez [ProtectionProfile](class_mip_protectionprofile.md) podczas jego inicjowania i w okresie swojego istnienia.

  
**Zwraca**: [ustawienia](class_mip_protectionprofile_settings.md) posługują się [ProtectionProfile](class_mip_protectionprofile.md) podczas jego inicjowania i w okresie swojego istnienia
  
### <a name="listenginesasync"></a>ListEnginesAsync
Rozpoczyna się listy aparatów operacji.

Parametry:  
* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="addengineasync"></a>AddEngineAsync
Rozpoczyna się dodanie nowego aparatu ochrony do profilu.

Parametry:  
* **ustawienia**: [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) obiekt, który określa parametry silnika. 


* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Rozpoczyna się usuwanie aparat ochrony z danym identyfikatorem. Wszystkie dane dla danego aparatu zostaną całkowicie usunięte.

Parametry:  
* **Identyfikator**: aparat Unikatowy identyfikator. 


* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.