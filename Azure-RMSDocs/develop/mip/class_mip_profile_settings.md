# <a name="class-mipprofilesettings"></a>Klasa mip::Profile::Settings 
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
Ustawienia publicznego (const std::string & ścieżki, bool useInMemoryStorage std::shared_ptr const<AuthDelegate>& authDelegate, const std::shared_ptr < Profile::Observer > & obserwatora, const ApplicationInfo & applicationInfo)  |  Interfejs służący do konfigurowania profilu.
 publiczny std::string const & GetPath() const  |  Uzyskać ścieżki do przechowywany stan.
 publiczny bool GetUseInMemoryStorage() const  |  Pobierz flagi użycia magazynu w pamięci.
publiczny std::shared_ptr const<AuthDelegate>& GetAuthDelegate() const  |  Pobierz delegata uwierzytelniania.
publiczny std::shared_ptr const < Profile::Observer > & GetObserver() const  |  Pobierz obserwatora zdarzeń.
 publiczny const ApplicationInfo GetApplicationInfo() const  |  Pobierz informacje o aplikacji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Interfejs służący do konfigurowania profilu.

Parametry:  
* **ścieżka**: ścieżka do katalogu, w którym zestawu sdk będą przechowywać stanu profilowania. 


* **useInMemoryStorage**: flagę wskazującą, czy stan powinny być przechowywane na dysku. 


* **authDelegate**: delegata uwierzytelniania używany przez zestaw SDK do uzyskiwania tokenów authenitication. 


* **Obserwator**: Implementacja klasy [Profile::Observer](class_mip_profile_observer.md) interfejsu. Może być nullptr. 


* **applicationInfo**: identyfikatory aplikacji używane do dostępu do usługi.


  
### <a name="getpath"></a>Funkcja GetPath
Uzyskać ścieżki do przechowywany stan.

  
**Zwraca**: ścieżka do zapisanego stanu.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Pobierz flagi użycia magazynu w pamięci.

  
**Zwraca**: True, jeśli użycia w pamięci jest ustawiony przeciwnym razie wartość false.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Pobierz delegata uwierzytelniania.

  
**Zwraca**: delegata uwierzytelniania.
  
### <a name="profileobserver"></a>Profile::Observer
Pobierz obserwatora zdarzeń.

  
**Zwraca**: obserwatora zdarzeń.
  
### <a name="applicationinfo"></a>ApplicationInfo
Pobierz informacje o aplikacji.

  
**Zwraca**: informacje o aplikacji.