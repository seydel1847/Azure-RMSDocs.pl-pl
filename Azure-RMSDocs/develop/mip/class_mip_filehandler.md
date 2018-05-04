# <a name="class-mipfilehandler"></a>Klasa mip::FileHandler 
Interfejs do pliku wszystkie funkcje obsługi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny GetLabelAsync void (const std::shared_ptr<void>& kontekstu)  |  Uruchamia pobieranie etykiety ważności z pliku.
publiczny GetProtectionAsync void (const std::shared_ptr<void>& kontekstu)  |  Uruchamia pobierania zasad ochrony z pliku.
publiczny SetLabel void (const std::string & etykiety, const LabelingOptions & labelingOptions)  |  Ustawia etykiety ważności do pliku.
publiczny DeleteLabel void (metoda AssignmentMethod, const std::string i justificationMessage)  |  Usuwa etykietę czułości z pliku.
publiczny SetCustomPermissions void (const std::shared_ptr<PolicyDescriptor>& policyDescriptor)  |  Ustawia niestandardowe uprawnienia do pliku.
publiczny RemoveProtection() void  |  Usuwa ochronę z pliku. Jeśli plik jest oznaczona, etykiety zostaną utracone.
publiczny CommitAsync void (const std::string & outputFilePath, const std::shared_ptr<void>& kontekstu) | Zapisuje zmiany w pliku określonego przez \|outputFilePath\ |  parametr.
publiczny CommitAsync void (const std::shared_ptr<Stream>& outputStream, const std::shared_ptr<void>& kontekstu) | Zapisuje zmiany w strumieniu określony przez \|outputStream\ |  parametr.
publiczny std::string GetOutputFileName()  |  Oblicza nazwę pliku wyjściowego i rozszerzenia na podstawie oryginalna nazwa pliku i wszystkich zmian.
wbudowany publiczny wirtualny ~FileHandler()  |  
wbudowany chronionych FileHandler()  |  
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getlabelasync"></a>GetLabelAsync
Uruchamia pobieranie etykiety ważności z pliku.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
  
#### <a name="parameters"></a>Parametry
* kontekst klienta kontekstu będzie można w sposób nieprzezroczysty przekazywane z powrotem do obserwatora.
  
### <a name="getprotectionasync"></a>GetProtectionAsync
Uruchamia pobierania zasad ochrony z pliku.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
  
#### <a name="parameters"></a>Parametry
* kontekst klienta kontekstu będzie można w sposób nieprzezroczysty przekazywane z powrotem do obserwatora.
  
### <a name="setlabel"></a>SetLabel
Ustawia etykiety ważności do pliku.
Zmiany nie zostaną zapisane do pliku, dopóki nie zostanie wywołana CommitAsync.
Zgłasza wyjątek [JustificationRequiredError](#classmip_1_1_justification_required_error) gdy ustawienie etykiety wymaga uzasadnienie i za pomocą parametru labelingOptions nie dostarczono żadnych komunikatów uzasadnienie.
  
### <a name="deletelabel"></a>DeleteLabel
Usuwa etykietę czułości z pliku.
Zmiany nie zostaną zapisane do pliku, dopóki nie zostanie wywołana CommitAsync. Metoda Privilegd i automatycznie umożliwia interfejsu API w celu zastąpienia żadnych istniejących zgłasza etykiety [JustificationRequiredError](#classmip_1_1_justification_required_error) gdy ustawienie etykiety wymaga uzasadnienie i nie dostarczono żadnych komunikatów uzasadnienie za pośrednictwem justificationMessage parametr.
  
### <a name="setcustompermissions"></a>SetCustomPermissions
Ustawia niestandardowe uprawnienia do pliku.
Zmiany nie zostaną zapisane do pliku, dopóki nie zostanie wywołana CommitAsync.
  
### <a name="removeprotection"></a>RemoveProtection
Usuwa ochronę z pliku. Jeśli plik jest oznaczona, etykiety zostaną utracone.
Zmiany nie zostaną zapisane do pliku, dopóki nie zostanie wywołana CommitAsync.
  
### <a name="commitasync"></a>CommitAsync
Zapisuje zmiany w pliku określonego przez | outputFilePath | parametr.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="commitasync"></a>CommitAsync
Zapisuje zmiany w strumieniu określony przez | outputStream | parametr.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="getoutputfilename"></a>GetOutputFileName
Oblicza nazwę pliku wyjściowego i rozszerzenia na podstawie oryginalna nazwa pliku i wszystkich zmian.
  
### <a name="filehandler"></a>~ FileHandler
  
### <a name="filehandler"></a>FileHandler