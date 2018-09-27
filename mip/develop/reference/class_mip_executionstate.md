# <a name="class-mipexecutionstate"></a>Klasa mip::ExecutionState 
Interfejs dla wszystkich stanów, które są wymagane do wykonania z aparatem.
Klienci powinny wywoływać tylko metody, które można uzyskać stanu, który jest potrzebny. W związku z tym w w celu zwiększenia wydajności klientów można implementować ten interfejs w taki sposób, że odpowiadający mu stan jest dynamicznie obliczana zamiast z góry obliczeń.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string GetNewLabelId() const  |  Pobiera identyfikator etykiety ważności, który ma zostać zastosowany do dokumentu.
 publiczne ActionSource GetNewLabelActionSource() const  |  Pobiera źródło dla nowej akcji etykietę.
 publiczne std::string GetContentIdentifier() const  |  Pobiera identyfikator zawartości, który ma zostać zastosowany do dokumentu, na podstawie bieżącego stanu. przykład dla pliku: "C:\mip-sdk-for-cpp\files\audit.docx" [ścieżka: nazwa_pliku] przykład wiadomości e-mail: "RE: inspekcji design:user1@contoso.com" [podmiotu: nadawcy].
 publiczne ContentState GetContentState() const  |  Pobiera ContentState danych według stawki ustalonej przez aplikację.
publiczne std::pair < wartość logiczna, std::string > IsDowngradeJustified() const  |  Implementacja powinna przekazać informację określającą, czy podano uzasadnienie, aby obniżyć istniejącą etykietę.
 publiczne AssignmentMethod GetNewLabelAssignmentMethod() const  |  Uzyskaj metodę przypisywania nową etykietę.
publiczne std::vector < std::pair < std::string, std::string >> GetNewLabelExtendedProperties() const  |  Zwraca właściwości rozszerzone nową etykietę.
publiczne std::vector < std::pair < std::string, std::string >> GetContentMetadata (const std::vector < std::string > & nazwy, const std::vector < std::string > & namePrefixes) const  |  Pobierz elementy meta-data, od zawartości.
publiczne std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor() const  |  Pobieranie deskryptora ochrony.
 publiczne ContentFormat GetContentFormat() const  |  Pobiera format zawartości.
 publiczne ActionType GetSupportedActions() const  |  Pobiera maskowanego wyliczenia, reprezentujący wszystkie typy obsługiwanych akcji.
publiczne wirtualne std::map < std::string, std::shared_ptr<ClassificationResult>> GetClassificationResults (const std::vector < std::string > &) const  |  Zwraca mapę wyniki klasyfikacji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getnewlabelid"></a>GetNewLabelId
Pobiera identyfikator etykiety ważności, który ma zostać zastosowany do dokumentu.

  
**Zwraca**: identyfikator etykiety ważności mają być stosowane do zawartości if else istnieje pozostawić puste, aby usunąć etykietę.
  
### <a name="getnewlabelactionsource"></a>GetNewLabelActionSource
Pobiera źródło dla nowej akcji etykietę.

  
**Zwraca**: źródło akcji.
  
### <a name="getcontentidentifier"></a>GetContentIdentifier
Pobiera identyfikator zawartości, który ma zostać zastosowany do dokumentu, na podstawie bieżącego stanu. przykład dla pliku: "C:\mip-sdk-for-cpp\files\audit.docx" [ścieżka: nazwa_pliku] przykład wiadomości e-mail: "RE: inspekcji design:user1@contoso.com" [podmiotu: nadawcy].

  
**Zwraca**: Identyfikator zawartości, które mają być stosowane do zawartości.
  
### <a name="getcontentstate"></a>GetContentState
Pobiera ContentState danych według stawki ustalonej przez aplikację.

  
**Zwraca**: stan danych wykonywanej
  
### <a name="isdowngradejustified"></a>IsDowngradeJustified
Implementacja powinna przekazać informację określającą, czy podano uzasadnienie, aby obniżyć istniejącą etykietę.

  
**Zwraca**: wartość True, jeśli obniżenia poziomu już jest uzasadnione, wartość false, jeśli jeszcze nie zostało to uzasadnione. 

  
**Zwraca**: komunikat uzasadnienie skojarzony z obniżania 
  
**Zobacz też**: [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod"></a>GetNewLabelAssignmentMethod
Uzyskaj metodę przypisywania nową etykietę.

  
**Zwraca**: metody przypisywania STANDARD, UPRZYWILEJOWANY, AUTO. 
  
**Zobacz też**: mip::AssignmentMethod
  
### <a name="getnewlabelextendedproperties"></a>GetNewLabelExtendedProperties
Zwraca właściwości rozszerzone nową etykietę.

  
**Zwraca**: wektor pary klucz-wartość reprezentujących rozszerzone właściwości, które są stosowane do zawartości.
  
### <a name="getcontentmetadata"></a>GetContentMetadata
Pobierz elementy meta-data, od zawartości.

  
**Zwraca**: wektor pary klucz-wartość reprezentujących metadane stosowane do zawartości. Każdy element metadanych jest pary nazw i wartości.
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Pobieranie deskryptora ochrony.

  
**Zwraca**: deskryptor ochrony
  
### <a name="getcontentformat"></a>GetContentFormat
Pobiera format zawartości.

  
**Zwraca**: domyślne, adres E-mail 
  
**Zobacz też**: mip::ContentFormat
  
### <a name="actiontype"></a>ActionType
Pobiera maskowanego wyliczenia, reprezentujący wszystkie typy obsługiwanych akcji.

  
**Zwraca**: maskowanego wyliczenia, reprezentujący wszystkie typy obsługiwanych akcji.
ActionType::Justify zawsze muszą być obsługiwane. Jeśli zmiany zasad i etykiet wymaga uzasadnienia, akcja uzasadnienie zawsze zostaną zwrócone.
  
### <a name="classificationresult"></a>ClassificationResult
Zwraca mapę wyniki klasyfikacji.

Parametry:  
* **classificationId**: Lista klasyfikacji identyfikator 



  
**Zwraca**: lista wyników klasyfikacji.