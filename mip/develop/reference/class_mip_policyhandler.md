# <a name="class-mippolicyhandler"></a>Klasa mip::PolicyHandler 
Ta klasa udostępnia interfejs dla wszystkich funkcji programu obsługi zasad w pliku.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::shared_ptr<ContentLabel> GetSensitivityLabel (const ExecutionState & stanu)  |  Pobierz etykiety ważności z istniejącej zawartości.
publiczne std::vector < std::shared_ptr<Action>> ComputeActions (const ExecutionState & stanu)  |  Wykonuje reguły na podstawie podanego stanu programu obsługi i zwraca listę akcji do wykonania.
 publiczne NotifyCommitedActions void (const ExecutionState & stanu)  |  Wywołuje się po zastosowaniu obliczanej akcje zatwierdzone danych na dysku.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="contentlabel"></a>ContentLabel
Pobierz etykiety ważności z istniejącej zawartości.
Informacje wymagane do pobierania etykiety będzie można uzyskać za pomocą stan podanego wykonywania. 

Parametry:  
* **Stan**: 



  
**Zwraca**: obiekt zawartości etykiet, który zawiera czułość etykietę również jako dodatkowe informacje. Zwraca wartość pustą, jeśli nie istnieje. 
  
**Zobacz też**: [mip::ContentLabel](class_mip_contentlabel.md).
  
### <a name="action"></a>Akcja
Wykonuje reguły na podstawie podanego stanu programu obsługi i zwraca listę akcji do wykonania.

Parametry:  
* **Stan**: bieżący stan wykonania w zawartości reguły są uruchomione na. 



  
**Zwraca**: Lista akcji, które powinny być stosowane wobec zawartości.
  
### <a name="notifycommitedactions"></a>NotifyCommitedActions
Wywołuje się po zastosowaniu obliczanej akcje zatwierdzone danych na dysku.

Parametry:  
* **Stan**: bieżący stan wykonania zawartości po akcje zostały zatwierdzone 


: To wywołanie wysyła zdarzenia inspekcji