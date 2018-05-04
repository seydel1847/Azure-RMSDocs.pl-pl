# <a name="class-mipprotectionprofileobserver"></a>Klasa mip::ProtectionProfile::Observer 
Interfejs, który odbiera powiadomienia związane z [ProtectionProfile](#classmip_1_1_protection_profile).
Ten interfejs musi przez implementowana przez aplikacje przy użyciu ochrony zestawu SDK
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publiczny wirtualny void OnLoadSuccess (const std::shared_ptr<ProtectionProfile>& profilu, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy profil został pomyślnie załadowany.
wbudowany publiczny wirtualny void OnLoadFailure (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy ładowanie profilu spowodowało błąd.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wywoływane, gdy profil został pomyślnie załadowany.
  
#### <a name="parameters"></a>Parametry
* Odwołanie do nowo utworzony profil [ProtectionProfile](#classmip_1_1_protection_profile)
* w kontekście tego samego kontekstu, który został przekazany do [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) aplikacji można przekazać dowolnego typu kontekstu (np. std::promise, std::function itp.) do [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) i tym samym kontekście zostaną przekazane jako-ma [ProtectionProfile::Observer::OnLoadSuccess](#classmip_1_1_protection_profile_1_1_observer_1a31e73965ffb0bd152b3954b013faa773) lub [ProtectionProfile::Observer::OnLoadFailure](#classmip_1_1_protection_profile_1_1_observer_1acdad73bb6a2dcc93295e0e16e422f291)
  
### <a name="onloadfailure"></a>OnLoadFailure
Wywoływane, gdy ładowanie profilu spowodowało błąd.
  
#### <a name="parameters"></a>Parametry
* Błąd [błąd](#classmip_1_1_error) który wystąpił podczas ładowania 
* w kontekście tego samego kontekstu, który został przekazany do [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) aplikacji można przekazać dowolnego typu kontekstu (np. std::promise, std::function itp.) do [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) i tym samym kontekście zostaną przekazane jako-ma [ProtectionProfile::Observer::OnLoadSuccess](#classmip_1_1_protection_profile_1_1_observer_1a31e73965ffb0bd152b3954b013faa773) lub [ProtectionProfile::Observer::OnLoadFailure](#classmip_1_1_protection_profile_1_1_observer_1acdad73bb6a2dcc93295e0e16e422f291)