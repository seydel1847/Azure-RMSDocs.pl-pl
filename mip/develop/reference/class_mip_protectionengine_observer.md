# <a name="class-mipprotectionengineobserver"></a>Klasa mip::ProtectionEngine::Observer 
Interfejs, który odbiera powiadomienia związane z [ProtectionEngine](class_mip_protectionengine.md).
Ten interfejs musi przez implementowany przez aplikacje przy użyciu zestawu SDK ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnGetTemplatesSuccess void (const std::shared_ptr < std::vector < std::string >> & templateIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy szablony zostały pomyślnie pobrane.
publiczne wirtualne OnGetTemplatesFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy pobieranie szablonów wygenerowany błąd.
publiczne wirtualne OnGetRightsForLabelIdSuccess void (const std::shared_ptr < std::vector < std::string >> & praw, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy uprawnienia zostały pomyślnie pobrane.
publiczne wirtualne OnGetRightsForLabelIdFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy trwa pobieranie praw do etykiety dla użytkownika.
publiczne wirtualne OnGetGrantingLabelIdsSuccess void (const std::shared_ptr < std::vector < std::string >> & lableIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy labelIds zostały pomyślnie pobrane.
publiczne wirtualne OnGetGrantingLabelIdsFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy trwa pobieranie labelIds dla użytkownika.
  
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
  
### <a name="ongetrightsforlabelidsuccess"></a>OnGetRightsForLabelIdSuccess
Wywołuje się, gdy uprawnienia zostały pomyślnie pobrane.

Parametry:  
* **prawa**: pobrać odwołanie do listy uprawnień 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync)


Aplikację można przekazać dowolny typ kontekstu (np. std::promise, std::function itp.) do [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::Observer :: OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) lub [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)
  
### <a name="ongetrightsforlabelidfailure"></a>OnGetRightsForLabelIdFailure
Wywołuje się, gdy trwa pobieranie praw do etykiety dla użytkownika.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) który wystąpił podczas pobierania uprawnień 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync)


Aplikację można przekazać dowolny typ kontekstu (np. std::promise, std::function itp.) do [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::Observer :: OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) lub [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)
  
### <a name="ongetgrantinglabelidssuccess"></a>OnGetGrantingLabelIdsSuccess
Wywołuje się, gdy labelIds zostały pomyślnie pobrane.

Parametry:  
* **lableIds**: pobrać odwołanie do listy lableIds 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync)


Aplikację można przekazać dowolny typ kontekstu (np. std::promise, std::function itp.) do [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::Observer :: OnGetGrantingLabelIdsSuccess](class_mip_protectionengine_observer.md#ongetgrantinglabelidssuccess) lub [ProtectionEngine::Observer::OnGetGrantingLabelIdsFailure](class_mip_protectionengine_observer.md#ongetgrantinglabelidsfailure)
  
### <a name="ongetgrantinglabelidsfailure"></a>OnGetGrantingLabelIdsFailure
Wywołuje się, gdy trwa pobieranie labelIds dla użytkownika.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) który wystąpił podczas pobierania labelIds 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync)


Aplikację można przekazać dowolny typ kontekstu (np. std::promise, std::function itp.) do [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::Observer :: OnGetGrantingLabelIdsSuccess](class_mip_protectionengine_observer.md#ongetgrantinglabelidssuccess) lub [ProtectionEngine::Observer::OnGetGrantingLabelIdsFailure](class_mip_protectionengine_observer.md#ongetgrantinglabelidsfailure)