# <a name="class-mipfileprofileobserver"></a>Klasa mip::FileProfile::Observer 
[Obserwator](#classmip_1_1_file_profile_1_1_observer) interfejsu, aby klienci mogli otrzymywać powiadomień dla profilu zdarzenia związane z.
Jeśli * wystąpi zdarzenie błędu, obiekt błąd zawiera wewnątrz [mip::Error](#classmip_1_1_error) klasy. Klient powinien nie wywołania aparat zwrotnego w wątku, który wywołuje obserwatora.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publiczny wirtualny ~Observer()  |  
wbudowany publiczny wirtualny void OnLoadSuccess (const std::shared_ptr < mip::FileProfile > & profilu, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy profil został pomyślnie załadowany.
wbudowany publiczny wirtualny void OnLoadFailure (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy ładowanie profilu spowodowało błąd.
wbudowany publiczny wirtualny void OnListEnginesSuccess (const std::vector < std::string > & engineIds, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy listy aparatów został pomyślnie wygenerowany.
wbudowany publiczny wirtualny void OnListEnginesError (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy lista aparaty spowodowało błąd.
wbudowany publiczny wirtualny void OnUnloadEngineSuccess (const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy aparat został zwolniony.
wbudowany publiczny wirtualny void OnUnloadEngineError (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy aparat zwalnianie spowodowało błąd.
wbudowany publiczny wirtualny void OnAddEngineSuccess (const std::shared_ptr < mip::FileEngine > & aparatu, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy nowy aparat został pomyślnie dodany.
wbudowany publiczny wirtualny void OnAddEngineError (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy dodawanie nowy aparat spowodowało błąd.
wbudowany publiczny wirtualny void OnDeleteEngineSuccess (const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy aparat został pomyślnie usunięty.
wbudowany publiczny wirtualny void OnDeleteEngineError (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy usunięcie aparatu spowodowało błąd.
wbudowany publiczny wirtualny void OnPolicyChanged (const std::string & engineId)  |  Wywołuje się, gdy zmieniono zasady dla aparatu o danym identyfikatorze.
wbudowany chronionych Observer()  |  
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="observer"></a>~ Obserwatora
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wywoływane, gdy profil został pomyślnie załadowany.
  
### <a name="onloadfailure"></a>OnLoadFailure
Wywoływane, gdy ładowanie profilu spowodowało błąd.
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wywoływane, gdy listy aparatów został pomyślnie wygenerowany.
  
### <a name="onlistengineserror"></a>OnListEnginesError
Wywoływane, gdy lista aparaty spowodowało błąd.
  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Wywoływane, gdy aparat został zwolniony.
  
### <a name="onunloadengineerror"></a>OnUnloadEngineError
Wywoływane, gdy aparat zwalnianie spowodowało błąd.
  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wywoływane, gdy nowy aparat został pomyślnie dodany.
  
### <a name="onaddengineerror"></a>OnAddEngineError
Wywoływane, gdy dodawanie nowy aparat spowodowało błąd.
  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wywoływane, gdy aparat został pomyślnie usunięty.
  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Wywoływane, gdy usunięcie aparatu spowodowało błąd.
  
### <a name="onpolicychanged"></a>OnPolicyChanged
Wywołuje się, gdy zmieniono zasady dla aparatu o danym identyfikatorze.
  
### <a name="observer"></a>Obserwatora