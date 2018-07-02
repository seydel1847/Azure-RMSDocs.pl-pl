# <a name="class-mippolicyengine"></a>Klasa mip::PolicyEngine 
Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Aparat zasad [ustawienia](class_mip_policyengine_settings.md).
publiczne std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Lista etykiet czułości skojarzone z aparatu zasad.
publiczne std::shared_ptr<ContentLabel> GetSensitivityLabel (const ExecutionState & stan) const  |  Pobierz etykiety ważności z istniejącej zawartości.
publiczne std::shared_ptr<Label> GetDefaultSensitivityLabel()  |  Pobierz domyślny etykieta poufności.
publiczne std::vector < std::shared_ptr<Action>> ComputeActions (const ExecutionState & stanu)  |  Wykonuje reguły w aparacie, na podstawie podanego stanu i zwraca listę akcji do wykonania.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Aparat zasad [ustawienia](class_mip_policyengine_settings.md).

  
**Zwraca**: ustawienia aparatu zasad. 
  
**Zobacz też**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="label"></a>Etykieta
Lista etykiet czułości skojarzone z aparatu zasad.

  
**Zwraca**: Lista etykiety ważności.
  
### <a name="contentlabel"></a>ContentLabel
Pobierz etykiety ważności z istniejącej zawartości.
Informacje wymagane do pobierania etykiety będzie można uzyskać za pomocą stan podanego wykonywania. 

Parametry:  
* **Stan**: 



  
**Zwraca**: obiekt zawartości etykiet, który zawiera czułość etykietę również jako dodatkowe informacje. Zwraca wartość pustą, jeśli nie istnieje. 
  
**Zobacz też**: [mip::ContentLabel](class_mip_contentlabel.md).
  
### <a name="label"></a>Etykieta
Pobierz domyślny etykieta poufności.

  
**Zwraca**: sensitivy etykiety domyślne, jeśli istnieje nullptr Jeśli nie ustawiono etykiety domyślnej.
  
### <a name="action"></a>Akcja
Wykonuje reguły w aparacie, na podstawie podanego stanu i zwraca listę akcji do wykonania.

Parametry:  
* **Stan**: bieżący stan wykonania w zawartości reguły są uruchomione na. 



  
**Zwraca**: Lista akcji, które powinny być stosowane wobec zawartości.