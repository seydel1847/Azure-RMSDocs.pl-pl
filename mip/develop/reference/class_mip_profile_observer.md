# <a name="class-mipprofileobserver"></a>Klasa mip::Profile::Observer 
[Obserwator](class_mip_profile_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomienia dla profilu zdarzenia związane z.
Jeśli * wystąpi zdarzenie błędu, zawiera obiekt błędu, wewnątrz [mip::Error](class_mip_error.md) klasy. Klient nie powinien wywoływać aparat Wstecz w wątku, który wywołuje obserwatora.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnLoadSuccess void (const std::shared_ptr<Profile>& profil, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy profil został pomyślnie załadowany.
publiczne wirtualne OnLoadFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas ładowania profilu spowodowało błąd.
publiczne wirtualne OnListEnginesSuccess void (const std::vector < std::string > & engineIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.
publiczne wirtualne OnListEnginesError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy lista aparatów spowodowało błąd.
publiczne wirtualne OnUnloadEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy aparat został zwolniony.
publiczne wirtualne OnUnloadEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy zwalnianie aparat spowodowało błąd.
publiczne wirtualne OnAddEngineSuccess void (const std::shared_ptr<PolicyEngine>& aparat, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy nowy aparat został pomyślnie dodany.
publiczne wirtualne OnAddEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas dodawania nowego aparatu spowodowało błąd.
publiczne wirtualne OnDeleteEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy aparat został pomyślnie usunięty.
publiczne wirtualne OnDeleteEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy usuwanie aparat spowodowało błąd.
 publiczne wirtualne OnPolicyChanged void (const std::string & engineId)  |  Wywołuje się, gdy zmieniono zasady dla aparatu z danym identyfikatorem.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wywołuje się, gdy profil został pomyślnie załadowany.

Parametry:  
* **profil**: bieżący profil używany do uruchomienia operacji. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onloadfailure"></a>OnLoadFailure
Metoda wywoływana podczas ładowania profilu spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji obciążenia. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.

Parametry:  
* **engineIds**: Lista identyfikatorów aparat są dostępne. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onlistengineserror"></a>OnListEnginesError
Wywołuje się, gdy lista aparatów spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji aparatu listy. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Wywołuje się, gdy aparat został zwolniony.

Parametry:  
* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onunloadengineerror"></a>OnUnloadEngineError
Wywołuje się, gdy zwalnianie aparat spowodowało błąd.

Parametry:  
* **Błąd**: błąd powodującą, że operacja zwolnienia aparat nie powiedzie się. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wywołuje się, gdy nowy aparat został pomyślnie dodany.
  
### <a name="onaddengineerror"></a>OnAddEngineError
Metoda wywoływana podczas dodawania nowego aparatu spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji aparatu Dodaj. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wywołuje się, gdy aparat został pomyślnie usunięty.

Parametry:  
* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Wywołuje się, gdy usuwanie aparat spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji aparatu delete. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onpolicychanged"></a>OnPolicyChanged
Wywołuje się, gdy zmieniono zasady dla aparatu z danym identyfikatorem.

Parametry:  
* **engineId**: aparat 


Aby załadować nowe zasady należy ponownie wywołaj AddEngineAsync z aparatem podane Id.