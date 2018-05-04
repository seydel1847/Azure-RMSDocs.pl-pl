# <a name="class-mipexecutionstate"></a>Klasa mip::ExecutionState 
Interfejs dla wszystkich stanów konieczne jest wykonanie przez aparat.
Klienci powinny wywoływać tylko metody można uzyskać stanu, który jest wymagany. W związku z tym w celu zwiększenia wydajności, klienci mogą chcieć zawierać implementację tego interfejsu w taki sposób, że odpowiadający mu stan jest obliczana dynamicznie zamiast przetwarzania danych z wyprzedzeniem.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny std::string GetNewLabelId() const  |  Pobiera identyfikator etykiety czułości, który ma zostać zastosowany w dokumencie.
publiczny bool IsDowngradeJustified() const  |  Implementacja należy przekazać lub nie podano uzasadnienie na starszą wersję istniejącej etykiety.
publiczny AssignmentMethod GetNewLabelAssignmentMethod() const  |  GET, Metoda przydziału nowej etykiety.
publiczny std::vector < std::pair < std::string, std::string >> GetContentMetadata (const std::vector < std::string > & nazwy, const std::vector < std::string > & namePrefixes) const  |  Pobierz elementy metadanych z zawartości.
publiczny std::string GetTemplateId() const  |  Pobiera identyfikator rights management usługi ochrony szablonu.
publiczny ContentFormat GetContentFormat() const  |  Pobiera format zawartości.
publiczny const ActionType GetSupportedActions() const  |  Zwraca listę działań, obsługiwanych przez aplikację. Wszystkie typy akcji są wymienione w [mip/upe/action.h](#action_8h).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getnewlabelid"></a>GetNewLabelId
Pobiera identyfikator etykiety czułości, który ma zostać zastosowany w dokumencie.
  
#### <a name="returns"></a>Zwraca
Identyfikator etykiety czułości ma zostać zastosowany do zawartości, jeśli istnieje else puste, aby usunąć etykietę.
  
### <a name="isdowngradejustified"></a>IsDowngradeJustified
Implementacja należy przekazać lub nie podano uzasadnienie na starszą wersję istniejącej etykiety.
  
#### <a name="returns"></a>Zwraca
wartość true, jeśli obniżenia poziomu już jest uzasadnione, wartość false, jeśli jeszcze nie jest uzasadnione. 
**Zobacz też**: [mip::JustifyAction](#classmip_1_1_justify_action)
  
### <a name="getnewlabelassignmentmethod"></a>GetNewLabelAssignmentMethod
GET, Metoda przydziału nowej etykiety.
  
#### <a name="returns"></a>Zwraca
Metoda przydziału STANDARD, uprzywilejowane, AUTOMATYCZNIE. 
**Zobacz też**: mip::AssignmentMethod
  
### <a name="getcontentmetadata"></a>GetContentMetadata
Pobierz elementy metadanych z zawartości.
  
#### <a name="returns"></a>Zwraca
Wektor par wartości klucza reprezentujących metadane stosowane do zawartości. Każdy element meta-data to pary nazw i wartości.
  
### <a name="gettemplateid"></a>GetTemplateId
Pobiera identyfikator rights management usługi ochrony szablonu.
  
#### <a name="returns"></a>Zwraca
usługi rights management ochrony identyfikator szablonu usługi, jeśli istnieje else w formacie guid bez nawiasów klamrowych, zwracany ciąg pusty.
  
### <a name="getcontentformat"></a>GetContentFormat
Pobiera format zawartości.
  
#### <a name="returns"></a>Zwraca
Domyślnie E-mail **Zobacz też**: mip::ContentFormat
  
### <a name="actiontype"></a>ActionType
Zwraca listę działań, obsługiwanych przez aplikację. Wszystkie typy akcji są wymienione w [mip/upe/action.h](#action_8h).