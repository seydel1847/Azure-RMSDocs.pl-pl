# <a name="class-mipfilehandler"></a>Klasa mip::FileHandler 
Interfejs dla wszystkich plików, funkcje obsługi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne GetLabelAsync void (const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się podczas pobierania etykiety ważności z pliku.
publiczne GetProtectionAsync void (const std::shared_ptr<void>& kontekstu)  |  Zostanie uruchomiony, pobieranie zasad ochrony z pliku.
 publiczne SetLabel void (const std::string & etykiety, const LabelingOptions & labelingOptions)  |  Ustawia etykieta poufności do pliku.
 publiczne DeleteLabel void (metoda AssignmentMethod, const std::string & justificationMessage)  |  Usunięcie etykiety ważności z pliku.
publiczne SetProtection void (const std::shared_ptr<ProtectionDescriptor>& protectionDescriptor)  |  Ustawia niestandardowy lub szablon na podstawie uprawnień (zgodnie z protectionDescriptor -> GetProtectionType) do pliku.
 publiczne RemoveProtection() void  |  Usuwa ochronę z pliku. Jeśli ten plik został oznaczony, etykieta zostaną utracone.
publiczne CommitAsync void (const std::string & outputFilePath, const std::shared_ptr<void>& kontekstu) | Zapisuje zmiany w pliku określonym przez \|outputFilePath\ |  parametr.
publiczne CommitAsync void (const std::shared_ptr<Stream>& outputStream, const std::shared_ptr<void>& kontekstu) | Zapisuje zmiany w strumieniu określonego przez \|outputStream\ |  parametr.
 publiczne std::string GetOutputFileName()  |  Oblicza rozszerzenia na podstawie oryginalna nazwa pliku i zmiany narastająco i nazwa pliku wyjściowego.
 publiczne wirtualne ~FileHandler()  | _Jeszcze nie udokumentowano._
 FileHandler() chronionych  | _Jeszcze nie udokumentowano._
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getlabelasync"></a>GetLabelAsync
Rozpoczyna się podczas pobierania etykiety ważności z pliku.
[FileHandler::Observer](class_mip_filehandler_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.

Parametry:  
* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatora.


  
### <a name="getprotectionasync"></a>GetProtectionAsync
Zostanie uruchomiony, pobieranie zasad ochrony z pliku.
[FileHandler::Observer](class_mip_filehandler_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.

Parametry:  
* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatora.


  
### <a name="setlabel"></a>SetLabel
Ustawia etykieta poufności do pliku.
Zmiany nie zostaną zapisane do pliku, dopóki nie zostanie wywołana CommitAsync.
Zgłasza [JustificationRequiredError](class_mip_justificationrequirederror.md) kiedy ustawienie etykiety wymaga uzasadnienia i podano żadnej wiadomości uzasadnienie za pomocą parametru labelingOptions.
  
### <a name="deletelabel"></a>DeleteLabel
Usunięcie etykiety ważności z pliku.
Zmiany nie zostaną zapisane do pliku, dopóki nie zostanie wywołana CommitAsync. Uprzywilejowany i metoda automatycznie umożliwia interfejsu API zastąpić wszelkie istniejące zgłasza etykiety [JustificationRequiredError](class_mip_justificationrequirederror.md) kiedy ustawienie etykiety wymaga uzasadnienia i podano żadnej wiadomości uzasadnienie za pośrednictwem justificationMessage parametr.
  
### <a name="setprotection"></a>SetProtection
Ustawia niestandardowy lub szablon na podstawie uprawnień (zgodnie z protectionDescriptor -> GetProtectionType) do pliku.
Zmiany nie zostaną zapisane do pliku, dopóki nie zostanie wywołana CommitAsync.
  
### <a name="removeprotection"></a>RemoveProtection
Usuwa ochronę z pliku. Jeśli ten plik został oznaczony, etykieta zostaną utracone.
Zmiany nie zostaną zapisane do pliku, dopóki nie zostanie wywołana CommitAsync.
  
### <a name="commitasync"></a>CommitAsync
Zapisuje zmiany w pliku określonym przez | outputFilePath | parametr.
[FileHandler::Observer](class_mip_filehandler_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="commitasync"></a>CommitAsync
Zapisuje zmiany w strumieniu określonego przez | outputStream | parametr.
[FileHandler::Observer](class_mip_filehandler_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="getoutputfilename"></a>GetOutputFileName
Oblicza rozszerzenia na podstawie oryginalna nazwa pliku i zmiany narastająco i nazwa pliku wyjściowego.
  
### <a name="filehandler"></a>~ FileHandler
_Jeszcze nie udokumentowano._

  
### <a name="filehandler"></a>FileHandler
_Jeszcze nie udokumentowano._
