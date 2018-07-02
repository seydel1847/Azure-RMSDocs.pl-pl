# <a name="class-mipprotectionengineobserver"></a>Klasa mip::ProtectionEngine::Observer 
Interfejs, który odbiera powiadomienia związane z [ProtectionEngine](class_mip_protectionengine.md).
Ten interfejs musi przez implementowany przez aplikacje przy użyciu zestawu SDK ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnGetTemplatesSuccess void (const std::shared_ptr < std::vector < std::string >> & templateIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy szablony zostały pomyślnie pobrane.
publiczne wirtualne OnGetTemplatesFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy pobieranie szablonów wygenerowany błąd.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="ongettemplatessuccess"></a>OnGetTemplatesSuccess
Wywołuje się, gdy szablony zostały pomyślnie pobrane.

Parametry:  
* **templateIds**: pobrać odwołanie do listy szablonów 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)


Aplikację można przekazać dowolny typ kontekstu (np. std::promise, std::function itp.) do [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::Observer::O nGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) lub [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)
  
### <a name="ongettemplatesfailure"></a>OnGetTemplatesFailure
Wywołuje się, gdy pobieranie szablonów wygenerowany błąd.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) który wystąpił podczas pobierania szablonów 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)


Aplikację można przekazać dowolny typ kontekstu (np. std::promise, std::function itp.) do [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::Observer::O nGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) lub [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)