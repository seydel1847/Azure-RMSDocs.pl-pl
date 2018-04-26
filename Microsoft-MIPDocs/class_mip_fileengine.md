# <a name="class-mipfileengine"></a>Klasa mip::FileEngine 
Interfejs dla wszystkich funkcji aparatu.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publiczny wirtualny ~ FileEngine | 
Ustawienia publicznego const & GetSettings | Zwraca ustawień aparatu.
publiczny std::vector const < std::shared_ptr < Etykieta >> & ListSensitivityLabels | Zwraca listę czułości etykiety.
publiczny std::shared_ptr < FileHandler > CreateFileHandlerFileHandler::Observer > & fileHandlerObserver) | Zwraca program obsługi plików dla danej ścieżki pliku.
publiczny std::shared_ptr < FileHandler > CreateFileHandlerStream > & inputStream, const std::string & inputFileName, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver) | Zwraca program obsługi plików dla danego strumienia pliku.
wbudowany chronionych FileEngine | 
## <a name="members"></a>Elementy członkowskie
### <a name="fileengine"></a>~ FileEngine
### <a name="settings"></a>Ustawienia
Zwraca ustawień aparatu.
### <a name="label"></a>Etykieta
Zwraca listę czułości etykiety.
### <a name="filehandler"></a>FileHandler
Zwraca program obsługi plików dla danej ścieżki pliku.
#### <a name="parameters"></a>Parametry
* Aby otworzyć plik. Ścieżka musi zawierać nazwę pliku i, jeśli taki istnieje, rozszerzenie nazwy pliku. 
* Implementacja klasy [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) interfejsu.
### <a name="filehandler"></a>FileHandler
Zwraca program obsługi plików dla danego strumienia pliku.
#### <a name="parameters"></a>Parametry
* Strumień, który reprezentuje plik. 
* Ścieżka do pliku. Ścieżka musi zawierać nazwę pliku i, jeśli taki istnieje, rozszerzenie nazwy pliku. 
* Implementacja klasy [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) interfejsu.
### <a name="fileengine"></a>FileEngine