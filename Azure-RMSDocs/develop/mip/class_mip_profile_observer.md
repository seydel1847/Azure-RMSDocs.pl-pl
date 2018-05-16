# <a name="class-mipprofileobserver"></a>Klasa mip::Profile::Observer 
[Obserwator](class_mip_profile_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomień dla profilu zdarzenia związane z.
Jeśli * wystąpi zdarzenie błędu, obiekt błąd zawiera wewnątrz [mip::Error](class_mip_error.md) klasy. Klient powinien nie wywołania aparat zwrotnego w wątku, który wywołuje obserwatora.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny wirtualny OnLoadSuccess void (const std::shared_ptr<Profile>& profilu, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy profil został pomyślnie załadowany.
publiczny wirtualny OnLoadFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy ładowanie profilu spowodowało błąd.
publiczny wirtualny OnListEnginesSuccess void (const std::vector < std::string > & engineIds, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy listy aparatów został pomyślnie wygenerowany.
publiczny wirtualny OnListEnginesError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy lista aparaty spowodowało błąd.
publiczny wirtualny OnUnloadEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy aparat został zwolniony.
publiczny wirtualny OnUnloadEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy aparat zwalnianie spowodowało błąd.
publiczny wirtualny OnAddEngineSuccess void (const std::shared_ptr<PolicyEngine>& aparat, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy nowy aparat został pomyślnie dodany.
publiczny wirtualny OnAddEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy dodawanie nowy aparat spowodowało błąd.
publiczny wirtualny OnDeleteEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy aparat został pomyślnie usunięty.
publiczny wirtualny OnDeleteEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy usunięcie aparatu spowodowało błąd.
 publiczny wirtualny OnPolicyChanged void (const std::string & engineId)  |  Wywołuje się, gdy zmieniono zasady dla aparatu o danym identyfikatorze.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wywoływane, gdy profil został pomyślnie załadowany.

Parametry:  
* **profil**: bieżący profil używany do uruchomienia operacji. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onloadfailure"></a>OnLoadFailure
Wywoływane, gdy ładowanie profilu spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji ładowania. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wywoływane, gdy listy aparatów został pomyślnie wygenerowany.

Parametry:  
* **engineIds**: Lista identyfikatorów aparatu są dostępne. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onlistengineserror"></a>OnListEnginesError
Wywoływane, gdy lista aparaty spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji aparatu listy. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Wywoływane, gdy aparat został zwolniony.

Parametry:  
* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onunloadengineerror"></a>OnUnloadEngineError
Wywoływane, gdy aparat zwalnianie spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji aparatu unload. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wywoływane, gdy nowy aparat został pomyślnie dodany.
  
### <a name="onaddengineerror"></a>OnAddEngineError
Wywoływane, gdy dodawanie nowy aparat spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji aparatu Dodaj. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wywoływane, gdy aparat został pomyślnie usunięty.

Parametry:  
* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Wywoływane, gdy usunięcie aparatu spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji usuwania aparatu. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onpolicychanged"></a>OnPolicyChanged
Wywołuje się, gdy zmieniono zasady dla aparatu o danym identyfikatorze.

Parametry:  
* **engineId**: aparat 


Ładowanie nowych zasad należy wywołać AddEngineAsync ponownie z aparatem podane Id.