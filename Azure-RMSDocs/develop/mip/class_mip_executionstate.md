# <a name="class-mipexecutionstate"></a>Klasa mip::ExecutionState 
Interfejs dla wszystkich stanów, które są wymagane do wykonania z aparatem.
Klienci powinny wywoływać tylko metody, które można uzyskać stanu, który jest potrzebny. W związku z tym w w celu zwiększenia wydajności klientów można implementować ten interfejs w taki sposób, że odpowiadający mu stan jest dynamicznie obliczana zamiast z góry obliczeń.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string GetNewLabelId() const  |  Pobiera identyfikator etykiety ważności, który ma zostać zastosowany do dokumentu.
 publiczne bool IsDowngradeJustified() const  |  Implementacja powinna przekazać informację określającą, czy podano uzasadnienie, aby obniżyć istniejącą etykietę.
 publiczne AssignmentMethod GetNewLabelAssignmentMethod() const  |  Uzyskaj metodę przypisywania nową etykietę.
publiczne std::vector < std::pair < std::string, std::string >> GetNewLabelExtendedProperties() const  |  Zwraca właściwości rozszerzone nową etykietę.
publiczne std::vector < std::pair < std::string, std::string >> GetContentMetadata (const std::vector < std::string > & nazwy, const std::vector < std::string > & namePrefixes) const  |  Pobierz elementy meta-data, od zawartości.
 publiczne std::string GetTemplateId() const  |  Pobiera identyfikator szablonu ochrony usługi zarządzania prawami.
 publiczne ContentFormat GetContentFormat() const  |  Pobiera format zawartości.
 publiczne ActionType GetSupportedActions() const  |  Pobiera maskowanego wyliczenia, reprezentujący wszystkie typy obsługiwanych akcji.
publiczne wirtualne std::map < std::string, std::shared_ptr<ClassificationResult>> GetClassificationResults (const std::vector < std::string > &) const  |  Zwraca mapę wyniki klasyfikacji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getnewlabelid"></a>GetNewLabelId
Pobiera identyfikator etykiety ważności, który ma zostać zastosowany do dokumentu.

  
**Zwraca**: identyfikator etykiety ważności mają być stosowane do zawartości if else istnieje pozostawić puste, aby usunąć etykietę.
  
### <a name="isdowngradejustified"></a>IsDowngradeJustified
Implementacja powinna przekazać informację określającą, czy podano uzasadnienie, aby obniżyć istniejącą etykietę.

  
**Zwraca**: wartość True, jeśli obniżenia poziomu już jest uzasadnione, wartość false, jeśli jeszcze nie zostało to uzasadnione. 
  
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
  
### <a name="gettemplateid"></a>GetTemplateId
Pobiera identyfikator szablonu ochrony usługi zarządzania prawami.

  
**Zwraca**: usługi rights management service identyfikator szablonu ochrony, jeśli istnieje inne w formacie identyfikatora guid, bez nawiasów klamrowych, zwracany ciąg pusty.
  
### <a name="getcontentformat"></a>GetContentFormat
Pobiera format zawartości.

  
**Zwraca**: domyślne, adres E-mail 
  
**Zobacz też**: mip::ContentFormat
  
### <a name="actiontype"></a>ActionType
Pobiera maskowanego wyliczenia, reprezentujący wszystkie typy obsługiwanych akcji.

  
**Zwraca**: maskowanego wyliczenia, reprezentujący wszystkie typy obsługiwanych akcji.
  
### <a name="classificationresult"></a>ClassificationResult
Zwraca mapę wyniki klasyfikacji.

Parametry:  
* **classificationId**: Lista klasyfikacji identyfikator 



  
**Zwraca**: lista wyników klasyfikacji.