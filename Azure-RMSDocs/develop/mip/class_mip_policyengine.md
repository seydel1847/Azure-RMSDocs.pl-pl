# <a name="class-mippolicyengine"></a>Klasa mip::PolicyEngine 
Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Ustawienia publicznego const & GetSettings() const  |  Pobierz aparat zasad [ustawienia](class_mip_policyengine_settings.md).
publiczny std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Wyświetl listę etykiet czułości skojarzonego z aparatem zasad.
publiczny std::shared_ptr<ContentLabel> GetSensitivityLabel (const ExecutionState & stanu)  |  Pobierz etykiety ważności z istniejącej zawartości.
publiczny std::shared_ptr<Label> GetDefaultSensitivityLabel()  |  Pobierz domyślne etykiety ważności.
publiczny std::vector < std::shared_ptr<Action>> ComputeActions (const ExecutionState & stanu)  |  Wykonuje reguł przez aparat na podstawie podanego stanu i zwraca listę akcji do wykonania.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Pobierz aparat zasad [ustawienia](class_mip_policyengine_settings.md).

  
**Zwraca**: ustawienia aparatu zasad. 
**Zobacz też**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="label"></a>Etykieta
Wyświetl listę etykiet czułości skojarzonego z aparatem zasad.

  
**Zwraca**: Lista czułości etykiety.
  
### <a name="contentlabel"></a>ContentLabel
Pobierz etykiety ważności z istniejącej zawartości.
Informacje wymagane do pobrania etykiety będzie można uzyskać za pomocą stan wykonywania podana. 

Parametry:  
* **Stan**: 



  
**Zwraca**: obiekt zawartości etykiety, który zawiera czułość etykietę również dodatkowych informacji. Zwraca pusty, jeśli nie istnieje. 
**Zobacz też**: [mip::ContentLabel](class_mip_contentlabel.md).
  
### <a name="label"></a>Etykieta
Pobierz domyślne etykiety ważności.

  
**Zwraca**: domyślne etykiety sensitivy, jeśli istnieje, nullptr Jeśli nie ustawiono etykiety domyślnej.
  
### <a name="action"></a>Akcja
Wykonuje reguł przez aparat na podstawie podanego stanu i zwraca listę akcji do wykonania.

Parametry:  
* **Stan**: bieżący stan wykonania w zawartości reguły są uruchomione na. 



  
**Zwraca**: Lista akcji, które powinny być stosowane do zawartości.