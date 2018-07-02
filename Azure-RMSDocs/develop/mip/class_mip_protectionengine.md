# <a name="class-mipprotectionengine"></a>Klasa mip::ProtectionEngine 
Wykonuje działania związanych z ochroną, odnoszące się do określonej tożsamości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Pobiera ustawienia aparatu.
publiczne GetTemplatesAsync void (const std::shared_ptr < ProtectionEngine::Observer > & obserwatora, const std::shared_ptr<void>& kontekstu)  |  Pobierz zbiór szablonów dostępnych dla użytkownika.
publiczne CreateProtectionHandlerFromDescriptorAsync void (const std::shared_ptr<ProtectionDescriptor>& deskryptora const ProtectionHandlerCreationOptions opcje, const std::shared_ptr < ProtectionHandler::Observer > & obserwatora, Const std::shared_ptr<void>& kontekstu)  |  Tworzy program obsługi ochrony gdzie prawa/role są przypisywane do konkretnych użytkowników.
publiczne CreateProtectionHandlerFromPublishingLicenseAsync void (const std::vector < uint8_t > & serializedPublishingLicense, const ProtectionHandlerCreationOptions & Opcje, const std::shared_ptr < ProtectionHandler::Observer > & obserwatora, const std::shared_ptr<void>& kontekstu)  |  Tworzy program obsługi ochrony na podstawie jego serializowanej formie.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Pobiera ustawienia aparatu.

  
**Zwraca**: ustawienia aparatu
  
### <a name="gettemplatesasync"></a>GetTemplatesAsync
Pobierz zbiór szablonów dostępnych dla użytkownika.

Parametry:  
* **Obserwator**: Implementacja klasy [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) interfejsu 


* **kontekst**: ten sam kontekst zostaną przekazane do [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) lub [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)


  
### <a name="createprotectionhandlerfromdescriptorasync"></a>CreateProtectionHandlerFromDescriptorAsync
Tworzy program obsługi ochrony gdzie prawa/role są przypisywane do konkretnych użytkowników.

Parametry:  
* **Deskryptor**: A [ProtectionDescriptor](class_mip_protectiondescriptor.md) opisujący konfigurację ochrony 


* **opcje**: opcje tworzenia 


* **Obserwator**: Implementacja klasy [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interfejsu 


* **kontekst**: ten sam kontekst zostaną przekazane do [ProtectionHandler::Observer::OnCreateProtectionHandlerSuccess](class_mip_protectionhandler_observer.md#oncreateprotectionhandlersuccess) lub ProtectionHandler::Observer::OnCreateProtectionHandlerFailure


  
### <a name="createprotectionhandlerfrompublishinglicenseasync"></a>CreateProtectionHandlerFromPublishingLicenseAsync
Tworzy program obsługi ochrony na podstawie jego serializowanej formie.

Parametry:  
* **serializedPublishingLicense**: A serializowana licencja publikowania 


* **opcje**: opcje tworzenia 


* **Obserwator**: Implementacja klasy [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interfejsu 


* **kontekst**: ten sam kontekst zostaną przekazane do [ProtectionHandler::Observer::OnCreateProtectionHandlerSuccess](class_mip_protectionhandler_observer.md#oncreateprotectionhandlersuccess) lub ProtectionHandler::Observer::OnCreateProtectionHandlerFailure

