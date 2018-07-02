# <a name="class-mipfileprofile"></a>Klasa mip::FileProfile 
[FileProfile](class_mip_fileprofile.md) klasy jest klasą głównego dla przy użyciu operacji Microsoft Information Protection.
Typowa aplikacja będzie potrzebny tylko jeden [profilu](class_mip_profile.md) , ale można utworzyć wiele profilów, jeśli to konieczne.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne wirtualne ~FileProfile()  | _Jeszcze nie udokumentowano._
 publiczne ustawienia const & GetSettings() const  |  Zwraca ustawień profilu.
publiczne ListEnginesAsync void (const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się listy aparatów operacji.
publiczne UnloadEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się zwalnianie aparatu plików z danym identyfikatorem.
publiczne AddEngineAsync void (const FileEngine::Settings & Ustawienia, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się dodanie nowego aparatu pliku do tego profilu.
publiczne DeleteEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się usuwanie aparatu plików z danym identyfikatorem. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.
 FileProfile() chronionych  | _Jeszcze nie udokumentowano._
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="fileprofile"></a>~ FileProfile
_Jeszcze nie udokumentowano._

  
### <a name="settings"></a>Ustawienia
Zwraca ustawień profilu.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Rozpoczyna się listy aparatów operacji.
[FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Rozpoczyna się zwalnianie aparatu plików z danym identyfikatorem. [FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="addengineasync"></a>AddEngineAsync
Rozpoczyna się dodanie nowego aparatu pliku do tego profilu.
[FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Rozpoczyna się usuwanie aparatu plików z danym identyfikatorem. Wszystkie dane dla danego profilu zostaną całkowicie usunięte.
[FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="fileprofile"></a>FileProfile
_Jeszcze nie udokumentowano._
