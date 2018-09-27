# <a name="class-mipfileengine"></a>Klasa mip::FileEngine 
Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Zwraca ustawień aparatu.
publiczne std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Zwraca listę etykiety ważności.
 publiczne std::string const & GetMoreInfoUrl() const  |  Podaj adres url dla wyszukiwania więcej informacji na temat zasad/etykiety.
 publiczne bool IsLabelingRequired() const  |  Sprawdza, czy zasady mówią, dokument musi mieć etykietę.
publiczne CreateFileHandlerAsync void (const std::string & inputFilePath, const mip::ContentState contentState, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się tworzenie obsługi plików dla podanej ścieżki pliku.
publiczne CreateFileHandlerAsync void (const std::shared_ptr<Stream>& inputStream, const std::string & inputFileName, const mip::ContentState contentState, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się tworzenie obsługi plików dla danego pliku strumienia.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Zwraca ustawień aparatu.
  
### <a name="label"></a>Etykieta
Zwraca listę etykiety ważności.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
Podaj adres url dla wyszukiwania więcej informacji na temat zasad/etykiety.

  
**Zwraca**: adres url w formacie ciągu.
  
### <a name="islabelingrequired"></a>IsLabelingRequired
Sprawdza, czy zasady mówią, dokument musi mieć etykietę.

  
**Zwraca**: wartość True, jeśli etykietowanie jest obowiązkowy, wartość false.
  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Rozpoczyna się tworzenie obsługi plików dla podanej ścieżki pliku.

Parametry:  
* Plik, aby otworzyć **.** Ścieżka musi zawierać nazwę pliku i, jeśli taki istnieje, rozszerzenie nazwy pliku. 


* **contentState**: stan zawartości wykonywanej: ruchu | REST | UŻYJ 


* **A**: Implementacja klasy [FileHandler::Observer](class_mip_filehandler_observer.md) interfejsu. 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatora.


  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Rozpoczyna się tworzenie obsługi plików dla danego pliku strumienia.

Parametry:  
* **inputStream**: strumień, który reprezentuje plik. 


* **inputFileName**: ścieżka do pliku. Ścieżka musi zawierać nazwę pliku i, jeśli taki istnieje, rozszerzenie nazwy pliku. 


* **contentState**: stan zawartości wykonywanej: ruchu | REST | UŻYJ 


* **fileHandlerObserver**: Implementacja klasy [FileHandler::Observer](class_mip_filehandler_observer.md) interfejsu. 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatora.

