# <a name="class-mipprofile"></a>Klasa mip::Profile 
[Profil](#classmip_1_1_profile) klasa jest klasą głównego dla przy użyciu operacji Microsoft Information Protection. Typowa aplikacja będzie tylko jeden [profilu](#classmip_1_1_profile) , ale można utworzyć wiele profilów, jeśli to konieczne.
  
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
  
#### <a name="returns"></a>Zwraca
ustawienia w profilu.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Uruchamia listy aparatów operacji.
  
#### <a name="parameters"></a>Parametry
* kontekst parametr, który zostanie przekazany do funkcji obserwatora. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Uruchamia zwalnianie aparat zasad o danym identyfikatorze.
  
#### <a name="parameters"></a>Parametry
* Identyfikator aparat Unikatowy identyfikator. 
* kontekst parametr, który zostanie przekazany do funkcji obserwatora. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="addengineasync"></a>AddEngineAsync
Dodawanie nowych aparat zasad w profilu uruchamiania.
  
#### <a name="parameters"></a>Parametry
* ustawienia [mip::PolicyEngine::Settings](#classmip_1_1_policy_engine_1_1_settings) obiekt określający aparaty parametry. 
* kontekst parametr, który zostanie przekazany do funkcji obserwatora. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Rozpoczyna się usuwanie aparat zasad o danym identyfikatorze. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.
  
#### <a name="parameters"></a>Parametry
* Identyfikator aparat Unikatowy identyfikator. 
* kontekst parametr, który zostanie przekazany do funkcji obserwatora. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.