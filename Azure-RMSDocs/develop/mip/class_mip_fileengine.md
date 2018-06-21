# <a name="class-mipfileengine"></a>Klasa mip::FileEngine 
Interfejs dla wszystkich funkcji aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny wirtualny ~FileEngine()  | _Nie została jeszcze udokumentowane._
 Ustawienia publicznego const & GetSettings() const  |  Zwraca ustawień aparatu.
publiczny std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Zwraca listę czułości etykiety.
publiczny std::shared_ptr<FileHandler> CreateFileHandler (const std::string & inputFilePath, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver)  |  Zwraca program obsługi plików dla danej ścieżki pliku.
publiczny std::shared_ptr<FileHandler> CreateFileHandler (const std::shared_ptr<Stream>& inputStream, const std::string & inputFileName, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver)  |  Zwraca program obsługi plików dla danego strumienia pliku.
 FileEngine() chronionych  | _Nie została jeszcze udokumentowane._
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="fileengine"></a>~ FileEngine
_Jeszcze nie udokumentowane._

  
### <a name="settings"></a>Ustawienia
Zwraca ustawień aparatu.
  
### <a name="label"></a>Etykieta
Zwraca listę czułości etykiety.
  
### <a name="filehandler"></a>FileHandler
Zwraca program obsługi plików dla danej ścieżki pliku.

Parametry:  
* ****: Plik, aby otworzyć. Ścieżka musi zawierać nazwę pliku i, jeśli taki istnieje, rozszerzenie nazwy pliku. 


* **A**: Implementacja klasy [FileHandler::Observer](class_mip_filehandler_observer.md) interfejsu.


  
### <a name="filehandler"></a>FileHandler
Zwraca program obsługi plików dla danego strumienia pliku.

Parametry:  
* **A**: strumień, który reprezentuje plik. 


* ****: Ścieżka do pliku. Ścieżka musi zawierać nazwę pliku i, jeśli taki istnieje, rozszerzenie nazwy pliku. 


* **A**: Implementacja klasy [FileHandler::Observer](class_mip_filehandler_observer.md) interfejsu.


  
### <a name="fileengine"></a>FileEngine
_Jeszcze nie udokumentowane._
