# <a name="class-mipprofile"></a>Klasa mip::Profile 
[Profil](class_mip_profile.md) klasa jest klasą głównego dla przy użyciu operacji Microsoft Information Protection. Typowa aplikacja będzie tylko jeden [profilu](class_mip_profile.md) , ale można utworzyć wiele profilów, jeśli to konieczne.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Ustawienia publicznego const & GetSettings() const  |  Pobierz ustawienia w profilu.
publiczny ListEnginesAsync void (const std::shared_ptr<void>& kontekstu)  |  Uruchamia listy aparatów operacji.
publiczny UnloadEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Uruchamia zwalnianie aparat zasad o danym identyfikatorze.
publiczny AddEngineAsync void (const PolicyEngine::Settings i ustawienia, const std::shared_ptr<void>& kontekstu)  |  Dodawanie nowych aparat zasad w profilu uruchamiania.
publiczny DeleteEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się usuwanie aparat zasad o danym identyfikatorze. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Pobierz ustawienia w profilu.

  
**Zwraca**: ustawienia skonfigurowane w profilu.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Uruchamia listy aparatów operacji.

Parametry:  
* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[Profile::Observer](class_mip_profile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Uruchamia zwalnianie aparat zasad o danym identyfikatorze.

Parametry:  
* **Identyfikator**: aparat Unikatowy identyfikator. 


* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[Profile::Observer](class_mip_profile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="addengineasync"></a>AddEngineAsync
Dodawanie nowych aparat zasad w profilu uruchamiania.

Parametry:  
* **ustawienia**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md) obiekt określający aparaty parametry. 


* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[Profile::Observer](class_mip_profile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Rozpoczyna się usuwanie aparat zasad o danym identyfikatorze. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.

Parametry:  
* **Identyfikator**: aparat Unikatowy identyfikator. 


* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[Profile::Observer](class_mip_profile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.