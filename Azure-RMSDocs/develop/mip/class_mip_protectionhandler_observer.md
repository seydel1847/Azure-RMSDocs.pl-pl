# <a name="class-mipprotectionhandlerobserver"></a>Klasa mip::ProtectionHandler::Observer 
Interfejs, który odbiera powiadomienia związane z [ProtectionHandler](class_mip_protectionhandler.md).
Ten interfejs musi przez implementowany przez aplikacje przy użyciu zestawu SDK ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnCreateProtectionHandlerSuccess void (const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy [ProtectionHandler](class_mip_protectionhandler.md) został pomyślnie utworzony.
publiczne wirtualne OnCreateProtectionHandlerError void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy [ProtectionHandler](class_mip_protectionhandler.md) tworzenie nie powiodło się.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="oncreateprotectionhandlersuccess"></a>OnCreateProtectionHandlerSuccess
Wywoływane, gdy [ProtectionHandler](class_mip_protectionhandler.md) został pomyślnie utworzony.

Parametry:  
* **protectionHandler**: nowo utworzony [ProtectionHandler](class_mip_protectionhandler.md)


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) lub [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)


Aplikację można przekazać dowolny typ kontekstu (np. std::promise, std::function itp.) do [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) lub [ProtectionEngine:: CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync), a tym samym kontekście zostaną przekazane jako-ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess lub ProtectionEngine::Observer::O nCreateProtectionHandlerFailure
  
### <a name="oncreateprotectionhandlererror"></a>OnCreateProtectionHandlerError
Wywoływane, gdy [ProtectionHandler](class_mip_protectionhandler.md) tworzenie nie powiodło się.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) które wystąpiły podczas tworzenia 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) lub [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)


Aplikację można przekazać dowolny typ kontekstu (np. std::promise, std::function itp.) do [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) lub [ProtectionEngine:: CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync), a tym samym kontekście zostaną przekazane jako-ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess lub ProtectionEngine::Observer::O nCreateProtectionHandlerFailure