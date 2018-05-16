# <a name="class-mipfileprofile"></a>Klasa mip::FileProfile 
[FileProfile](class_mip_fileprofile.md) klasa jest klasą głównego dla przy użyciu operacji Microsoft Information Protection.
Typowa aplikacja będzie tylko jeden [profilu](class_mip_profile.md) , ale można utworzyć wiele profilów, jeśli to konieczne.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny wirtualny ~FileProfile()  | _Nie została jeszcze udokumentowane._
 Ustawienia publicznego const & GetSettings() const  |  Zwraca ustawień profilu.
publiczny ListEnginesAsync void (const std::shared_ptr<void>& kontekstu)  |  Uruchamia listy aparatów operacji.
publiczny UnloadEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Uruchamia zwalnianie aparat plików o danym identyfikatorze.
publiczny AddEngineAsync void (const FileEngine::Settings i ustawienia, const std::shared_ptr<void>& kontekstu)  |  Dodawanie nowy aparat plików do profilu uruchamiania.
publiczny DeleteEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się usuwanie aparat plików o danym identyfikatorze. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.
 FileProfile() chronionych  | _Nie została jeszcze udokumentowane._
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="fileprofile"></a>~ FileProfile
_Jeszcze nie udokumentowane._

  
### <a name="settings"></a>Ustawienia
Zwraca ustawień profilu.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Uruchamia listy aparatów operacji.
[FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Uruchamia zwalnianie aparat plików o danym identyfikatorze. [FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="addengineasync"></a>AddEngineAsync
Dodawanie nowy aparat plików do profilu uruchamiania.
[FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Rozpoczyna się usuwanie aparat plików o danym identyfikatorze. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.
[FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="fileprofile"></a>FileProfile
_Jeszcze nie udokumentowane._
