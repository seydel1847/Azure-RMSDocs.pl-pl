# <a name="class-mipprofile"></a>Klasa mip::Profile 
[Profil](class_mip_profile.md) klasy jest klasą głównego dla przy użyciu operacji Microsoft Information Protection. Typowa aplikacja będzie potrzebny tylko jeden [profilu](class_mip_profile.md) , ale można utworzyć wiele profilów, jeśli to konieczne.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Pobierz ustawienia w profilu.
publiczne ListEnginesAsync void (const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się listy aparatów operacji.
publiczne UnloadEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się zwalnianie aparatu zasad z danym identyfikatorem.
publiczne AddEngineAsync void (const PolicyEngine::Settings & Ustawienia, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się dodanie nowego aparatu zasad w profilu.
publiczne DeleteEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się usuwanie aparatu zasad z danym identyfikatorem. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Pobierz ustawienia w profilu.

  
**Zwraca**: ustawienia w profilu.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Rozpoczyna się listy aparatów operacji.

Parametry:  
* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[Profile::Observer](class_mip_profile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Rozpoczyna się zwalnianie aparatu zasad z danym identyfikatorem.

Parametry:  
* **Identyfikator**: aparat Unikatowy identyfikator. 


* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[Profile::Observer](class_mip_profile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="addengineasync"></a>AddEngineAsync
Rozpoczyna się dodanie nowego aparatu zasad w profilu.

Parametry:  
* **ustawienia**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md) obiekt, który określa parametry silników. 


* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[Profile::Observer](class_mip_profile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Rozpoczyna się usuwanie aparatu zasad z danym identyfikatorem. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.

Parametry:  
* **Identyfikator**: aparat Unikatowy identyfikator. 


* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[Profile::Observer](class_mip_profile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.