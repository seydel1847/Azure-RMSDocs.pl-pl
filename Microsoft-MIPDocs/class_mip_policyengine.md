# <a name="class-mippolicyengine"></a>Klasa mip::PolicyEngine 
Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny const ustawienia & GetSettings publicznego const std::vector < std::shared_ptr < Etykieta >> & ListSensitivityLabels | Wyświetl listę etykiet czułości skojarzonego z aparatem zasad.
publiczny std::shared_ptr < ContentLabel > GetSensitivityLabelExecutionState & stanu) | Pobierz etykiety ważności z istniejącej zawartości.
publiczny std::shared_ptr GetDefaultSensitivityLabel < Etykieta > | Pobierz domyślne etykiety ważności.
publiczny std::vector < std::shared_ptr < akcji >> ComputeActionsExecutionState & stanu) | Wykonuje reguł przez aparat na podstawie podanego stanu i zwraca listę akcji do wykonania.
## <a name="members"></a>Elementy członkowskie
### <a name="settings"></a>Ustawienia
Pobierz aparat zasad [ustawienia](#classmip_1_1_policy_engine_1_1_settings).
#### <a name="returns"></a>Zwraca
Ustawienia aparatu zasad. 
**Zobacz też**: [mip::PolicyEngine::Settings](#classmip_1_1_policy_engine_1_1_settings)
### <a name="label"></a>Etykieta
Wyświetl listę etykiet czułości skojarzonego z aparatem zasad.
#### <a name="returns"></a>Zwraca
Lista czułości etykiety.
### <a name="contentlabel"></a>ContentLabel
Pobierz etykiety ważności z istniejącej zawartości.
Informacje wymagane do pobrania etykiety będzie można uzyskać za pomocą stan wykonywania podana. 
#### <a name="parameters"></a>Parametry
* Stan 
#### <a name="returns"></a>Zwraca
obiekt zawartości etykiety, który zawiera etykiety ważności, jak również dodatkowe informacje. Zwraca pusty, jeśli nie istnieje. 
**Zobacz też**: [mip::ContentLabel](#classmip_1_1_content_label).
### <a name="label"></a>Etykieta
Pobierz domyślne etykiety ważności.
#### <a name="returns"></a>Zwraca
domyślne etykiety sensitivy, jeśli istnieje, nullptr Jeśli nie ustawiono etykiety domyślnej.
### <a name="action"></a>Akcja
Wykonuje reguł przez aparat na podstawie podanego stanu i zwraca listę akcji do wykonania.
#### <a name="parameters"></a>Parametry
* Stan zawartości, której reguły są uruchomione na bieżący stan wykonania. 
#### <a name="returns"></a>Zwraca
Lista akcji, które powinny być stosowane do zawartości.