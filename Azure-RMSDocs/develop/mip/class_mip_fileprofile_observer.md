# <a name="class-mipfileprofileobserver"></a>Klasa mip::FileProfile::Observer 
[Obserwator](class_mip_fileprofile_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomienia dla profilu zdarzenia związane z.
Jeśli * wystąpi zdarzenie błędu, zawiera obiekt błędu, wewnątrz [mip::Error](class_mip_error.md) klasy. Klient nie powinien wywoływać aparat Wstecz w wątku, który wywołuje obserwatora.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne wirtualne ~Observer()  | _Jeszcze nie udokumentowano._
publiczne wirtualne OnLoadSuccess void (const std::shared_ptr < mip::FileProfile > & profilu, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy profil został pomyślnie załadowany.
publiczne wirtualne OnLoadFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas ładowania profilu spowodowało błąd.
publiczne wirtualne OnListEnginesSuccess void (const std::vector < std::string > & engineIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.
publiczne wirtualne OnListEnginesError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy lista aparatów spowodowało błąd.
publiczne wirtualne OnUnloadEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy aparat został zwolniony.
publiczne wirtualne OnUnloadEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy zwalnianie aparat spowodowało błąd.
publiczne wirtualne OnAddEngineSuccess void (const std::shared_ptr < mip::FileEngine > & aparatu, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy nowy aparat został pomyślnie dodany.
publiczne wirtualne OnAddEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas dodawania nowego aparatu spowodowało błąd.
publiczne wirtualne OnDeleteEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy aparat został pomyślnie usunięty.
publiczne wirtualne OnDeleteEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy usuwanie aparat spowodowało błąd.
 publiczne wirtualne OnPolicyChanged void (const std::string & engineId)  |  Wywołuje się, gdy zmieniono zasady dla aparatu z danym identyfikatorem.
 Observer() chronionych  | _Jeszcze nie udokumentowano._
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="observer"></a>~ Obserwatora
_Jeszcze nie udokumentowano._

  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wywołuje się, gdy profil został pomyślnie załadowany.
  
### <a name="onloadfailure"></a>OnLoadFailure
Metoda wywoływana podczas ładowania profilu spowodowało błąd.
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.
  
### <a name="onlistengineserror"></a>OnListEnginesError
Wywołuje się, gdy lista aparatów spowodowało błąd.
  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Wywołuje się, gdy aparat został zwolniony.
  
### <a name="onunloadengineerror"></a>OnUnloadEngineError
Wywołuje się, gdy zwalnianie aparat spowodowało błąd.
  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wywołuje się, gdy nowy aparat został pomyślnie dodany.
  
### <a name="onaddengineerror"></a>OnAddEngineError
Metoda wywoływana podczas dodawania nowego aparatu spowodowało błąd.
  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wywołuje się, gdy aparat został pomyślnie usunięty.
  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Wywołuje się, gdy usuwanie aparat spowodowało błąd.
  
### <a name="onpolicychanged"></a>OnPolicyChanged
Wywołuje się, gdy zmieniono zasady dla aparatu z danym identyfikatorem.
  
### <a name="observer"></a>Obserwator
_Jeszcze nie udokumentowano._
