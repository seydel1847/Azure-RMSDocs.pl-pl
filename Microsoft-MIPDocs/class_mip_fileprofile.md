# <a name="class-mipfileprofile"></a>Klasa mip::FileProfile 
[FileProfile](#classmip_1_1_file_profile) klasa jest klasą głównego dla przy użyciu operacji Microsoft Information Protection.
Typowa aplikacja będzie tylko jeden [profilu](#classmip_1_1_profile) , ale można utworzyć wiele profilów, jeśli to konieczne.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publiczny wirtualny ~ FileProfile | 
Ustawienia publicznego const & GetSettings | Zwraca ustawień profilu.
publiczny ListEnginesAsync void | Uruchamia listy aparatów operacji.
publiczny UnloadEngineAsync void | Uruchamia zwalnianie aparat plików o danym identyfikatorze.
publiczny void AddEngineAsyncFileEngine::Settings i ustawienia, const std::shared_ptr < void > i kontekstu) | Dodawanie nowy aparat plików do profilu uruchamiania.
publiczny DeleteEngineAsync void | Rozpoczyna się usuwanie aparat plików o danym identyfikatorze. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.
wbudowany chronionych FileProfile | 
## <a name="members"></a>Elementy członkowskie
### <a name="fileprofile"></a>~ FileProfile
### <a name="settings"></a>Ustawienia
Zwraca ustawień profilu.
### <a name="listenginesasync"></a>ListEnginesAsync
Uruchamia listy aparatów operacji.
[FileProfile::Observer](#classmip_1_1_file_profile_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
### <a name="unloadengineasync"></a>UnloadEngineAsync
Uruchamia zwalnianie aparat plików o danym identyfikatorze. [FileProfile::Observer](#classmip_1_1_file_profile_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
### <a name="addengineasync"></a>AddEngineAsync
Dodawanie nowy aparat plików do profilu uruchamiania.
[FileProfile::Observer](#classmip_1_1_file_profile_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
### <a name="deleteengineasync"></a>DeleteEngineAsync
Rozpoczyna się usuwanie aparat plików o danym identyfikatorze. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.
[FileProfile::Observer](#classmip_1_1_file_profile_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
### <a name="fileprofile"></a>FileProfile