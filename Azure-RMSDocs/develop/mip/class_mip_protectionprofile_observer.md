# <a name="class-mipprotectionprofileobserver"></a>Klasa mip::ProtectionProfile::Observer 
Interfejs, który odbiera powiadomienia związane z [ProtectionProfile](class_mip_protectionprofile.md).
Ten interfejs musi przez implementowana przez aplikacje przy użyciu ochrony zestawu SDK
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny wirtualny OnLoadSuccess void (const std::shared_ptr<ProtectionProfile>& profilu, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy profil został pomyślnie załadowany.
publiczny wirtualny OnLoadFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy ładowanie profilu spowodowało błąd.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wywoływane, gdy profil został pomyślnie załadowany.

Parametry:  
* **profil**: odwołanie do nowo utworzonego [ProtectionProfile](class_mip_protectionprofile.md)


* **kontekst**: tym samym kontekście, który został przekazany do [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync)


Aplikacja może przekazać dowolnego typu kontekstu (np. std::promise, std::function itp.) do [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync) i tym samym kontekście zostaną przekazane jako-ma [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) lub [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)
  
### <a name="onloadfailure"></a>OnLoadFailure
Wywoływane, gdy ładowanie profilu spowodowało błąd.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) który wystąpił podczas ładowania 


* **kontekst**: tym samym kontekście, który został przekazany do [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync)


Aplikacja może przekazać dowolnego typu kontekstu (np. std::promise, std::function itp.) do [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync) i tym samym kontekście zostaną przekazane jako-ma [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) lub [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)