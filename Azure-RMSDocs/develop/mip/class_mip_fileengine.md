# <a name="class-mipfileengine"></a>Klasa mip::FileEngine 
Interfejs dla wszystkich funkcji aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne wirtualne ~FileEngine()  | _Jeszcze nie udokumentowano._
 publiczne ustawienia const & GetSettings() const  |  Zwraca ustawień aparatu.
publiczne std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Zwraca listę etykiety ważności.
publiczne CreateFileHandlerAsync void (const std::string & inputFilePath const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się tworzenie obsługi plików dla podanej ścieżki pliku.
publiczne CreateFileHandlerAsync void (const std::shared_ptr<Stream>& inputStream, const std::string inputFileName, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się tworzenie obsługi plików dla danego pliku strumienia.
 protected FileEngine()  | _Jeszcze nie udokumentowano._
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="fileengine"></a>~FileEngine
_Jeszcze nie udokumentowano._

  
### <a name="settings"></a>Ustawienia
Zwraca ustawień aparatu.
  
### <a name="label"></a>Etykieta
Zwraca listę etykiety ważności.
  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Rozpoczyna się tworzenie obsługi plików dla podanej ścieżki pliku.

Parametry:  
* Plik, aby otworzyć **.** Ścieżka musi zawierać nazwę pliku i, jeśli taki istnieje, rozszerzenie nazwy pliku. 


* **A**: Implementacja klasy [FileHandler::Observer](class_mip_filehandler_observer.md) interfejsu. 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatora.


  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Rozpoczyna się tworzenie obsługi plików dla danego pliku strumienia.

Parametry:  
* **A**: strumień, który reprezentuje plik. 


* Ścieżka do pliku **.** Ścieżka musi zawierać nazwę pliku i, jeśli taki istnieje, rozszerzenie nazwy pliku. 


* **A**: Implementacja klasy [FileHandler::Observer](class_mip_filehandler_observer.md) interfejsu. 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatora.


  
### <a name="fileengine"></a>FileEngine
_Jeszcze nie udokumentowano._
