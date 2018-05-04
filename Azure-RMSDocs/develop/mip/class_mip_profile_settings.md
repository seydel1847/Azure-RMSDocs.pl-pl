# <a name="class-mipprofilesettings"></a>Klasa mip::Profile::Settings 
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publicznego ustawień (const std::string & ścieżki, bool useInMemoryStorage std::shared_ptr const<AuthDelegate>& authDelegate, const std::shared_ptr < Profile::Observer > & obserwatora, const ApplicationInfo & applicationInfo)  |  Interfejs służący do konfigurowania profilu.
const std::string publicznego wbudowanego & GetPath() const  |  Uzyskać ścieżki do przechowywany stan.
wbudowany publicznego bool GetUseInMemoryStorage() const  |  Pobierz flagi użycia magazynu w pamięci.
const std::shared_ptr publicznego wbudowanego<AuthDelegate>& GetAuthDelegate() const  |  Pobierz delegata uwierzytelniania.
wbudowany publicznego const std::shared_ptr < Profile::Observer > & GetObserver() const  |  Pobierz obserwatora zdarzeń.
wbudowany publicznego const ApplicationInfo GetApplicationInfo() const  |  Pobierz informacje o aplikacji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Interfejs służący do konfigurowania profilu.
  
#### <a name="parameters"></a>Parametry
* Ścieżka ścieżkę do katalogu, w którym zestawu sdk będą przechowywać stanu profilowania. 
* useInMemoryStorage A flaga oznaczająca, czy stan powinny być przechowywane na dysku. 
* authDelegate delegata uwierzytelniania używany przez zestaw SDK do uzyskiwania tokenów authenitication. 
* Implementacja klasy obserwatora [Profile::Observer](#classmip_1_1_profile_1_1_observer) interfejsu. Może być nullptr. 
* applicationInfo identyfikatory aplikacji używane dla dostępu do usługi.
  
### <a name="getpath"></a>Funkcja GetPath
Uzyskać ścieżki do przechowywany stan.
  
#### <a name="returns"></a>Zwraca
Ścieżka do zapisanego stanu.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Pobierz flagi użycia magazynu w pamięci.
  
#### <a name="returns"></a>Zwraca
wartość true, jeśli użycia w pamięci jest ustawiony przeciwnym razie wartość false.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Pobierz delegata uwierzytelniania.
  
#### <a name="returns"></a>Zwraca
Delegat uwierzytelniania.
  
### <a name="profileobserver"></a>Profile::Observer
Pobierz obserwatora zdarzeń.
  
#### <a name="returns"></a>Zwraca
Obserwator zdarzeń.
  
### <a name="applicationinfo"></a>ApplicationInfo
Pobierz informacje o aplikacji.
  
#### <a name="returns"></a>Zwraca
informacje o aplikacji.