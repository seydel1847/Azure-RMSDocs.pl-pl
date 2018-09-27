# <a name="class-mipprotectionprofileobserver"></a>Klasa mip::ProtectionProfile::Observer 
Interfejs, który odbiera powiadomienia związane z [ProtectionProfile](class_mip_protectionprofile.md).
Ten interfejs musi przez implementowany przez aplikacje przy użyciu zestawu SDK ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnLoadSuccess void (const std::shared_ptr<ProtectionProfile>& profil, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy profil został pomyślnie załadowany.
publiczne wirtualne OnLoadFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas ładowania profilu spowodowało błąd.
publiczne wirtualne OnListEnginesSuccess void (const std::vector < std::string > & engineIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.
publiczne wirtualne OnListEnginesError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy lista aparatów zakończyło się błędem.
publiczne wirtualne OnAddEngineSuccess void (const std::shared_ptr<ProtectionEngine>& aparat, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy nowy aparat został pomyślnie dodany.
publiczne wirtualne OnAddEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas dodawania nowego aparatu zakończyło się błędem.
publiczne wirtualne OnDeleteEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy aparat został pomyślnie usunięty.
publiczne wirtualne OnDeleteEngineError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy usuwanie aparat zakończyło się błędem.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wywołuje się, gdy profil został pomyślnie załadowany.

Parametry:  
* **profil**: odwołanie do nowo utworzony [ProtectionProfile](class_mip_protectionprofile.md)


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


Aplikację można przekazać dowolny typ kontekstu (np. std::promise, std::function itp.) do [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) lub [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)
  
### <a name="onloadfailure"></a>OnLoadFailure
Metoda wywoływana podczas ładowania profilu spowodowało błąd.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) który wystąpił podczas ładowania 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


Aplikację można przekazać dowolny typ kontekstu (np. std::promise, std::function itp.) do [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) lub [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.

Parametry:  
* **engineIds**: Lista identyfikatorów aparat są dostępne. 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync)


  
### <a name="onlistengineserror"></a>OnListEnginesError
Wywołuje się, gdy lista aparatów zakończyło się błędem.

Parametry:  
* **Błąd**: błąd, który spowodować aparatów listy operacja nie powiodła się. 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync)


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wywołuje się, gdy nowy aparat został pomyślnie dodany.

Parametry:  
* **aparat**: nowy aparat 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


  
### <a name="onaddengineerror"></a>OnAddEngineError
Metoda wywoływana podczas dodawania nowego aparatu zakończyło się błędem.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji aparatu Dodaj. 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wywołuje się, gdy aparat został pomyślnie usunięty.

Parametry:  
* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync)


  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Wywołuje się, gdy usuwanie aparat zakończyło się błędem.

Parametry:  
* **Błąd**: błąd, który spowodować niepowodzenie operacji aparatu delete. 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync)

