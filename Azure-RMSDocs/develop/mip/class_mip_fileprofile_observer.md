# <a name="class-mipfileprofileobserver"></a>Klasa mip::FileProfile::Observer 
[Obserwator](class_mip_fileprofile_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomień dla profilu zdarzenia związane z.
Jeśli * wystąpi zdarzenie błędu, obiekt błąd zawiera wewnątrz [mip::Error](class_mip_error.md) klasy. Klient powinien nie wywołania aparat zwrotnego w wątku, który wywołuje obserwatora.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny wirtualny ~Observer()  | _Nie została jeszcze udokumentowane._
publiczny wirtualny OnLoadSuccess void (const std::shared_ptr < mip::FileProfile > & profilu, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy profil został pomyślnie załadowany.
publiczny wirtualny OnLoadFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy ładowanie profilu spowodowało błąd.
publiczny wirtualny OnListEnginesSuccess void (const std::vector < std::string > & engineIds, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy listy aparatów został pomyślnie wygenerowany.
publiczny wirtualny OnListEnginesError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy lista aparaty spowodowało błąd.
publiczny wirtualny OnUnloadEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy aparat został zwolniony.
publiczny wirtualny OnUnloadEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy aparat zwalnianie spowodowało błąd.
publiczny wirtualny OnAddEngineSuccess void (const std::shared_ptr < mip::FileEngine > & aparatu, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy nowy aparat został pomyślnie dodany.
publiczny wirtualny OnAddEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy dodawanie nowy aparat spowodowało błąd.
publiczny wirtualny OnDeleteEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy aparat został pomyślnie usunięty.
publiczny wirtualny OnDeleteEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy usunięcie aparatu spowodowało błąd.
 publiczny wirtualny OnPolicyChanged void (const std::string & engineId)  |  Wywołuje się, gdy zmieniono zasady dla aparatu o danym identyfikatorze.
 Observer() chronionych  | _Nie została jeszcze udokumentowane._
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="observer"></a>~ Obserwatora
_Jeszcze nie udokumentowane._

  
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
_Jeszcze nie udokumentowane._
