# <a name="class-mipfilehandlerobserver"></a>Klasa mip::FileHandler::Observer 
[Obserwator](class_mip_filehandler_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomienia dla pliku zdarzenia związane z programu obsługi.
Jeśli * wystąpi zdarzenie błędu, zawiera obiekt błędu, wewnątrz [mip::Error](class_mip_error.md) klasy. Klient nie powinien wywoływać aparat Wstecz w wątku, który wywołuje obserwatora.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnCreateFileHandlerSuccess void (const std::shared_ptr<FileHandler>& fileHandler, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy program obsługi został utworzony pomyślnie.
publiczne wirtualne OnCreateFileHandlerFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy nie można utworzyć programu obsługi z powodu błędu.
publiczne wirtualne OnGetLabelSuccess void (const std::shared_ptr<ContentLabel>& etykiety, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy etykiety są pomyślnie pobrane.
publiczne wirtualne OnGetLabelFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas pobierania etykiety nie powiodło się z powodu błędu.
publiczne wirtualne OnGetProtectionSuccess void (const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy zasady ochrony jest pomyślnie pobrane.
publiczne wirtualne OnGetProtectionFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy trwa pobieranie zasad ochrony nie powiodło się z powodu błędu.
publiczne wirtualne OnCommitSuccess void (została zatwierdzona, bool const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy zatwierdzania zmian do pliku zakończyły się pomyślnie.
publiczne wirtualne OnCommitFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy zatwierdzania zmian do pliku nie powiodło się z powodu błędu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="oncreatefilehandlersuccess"></a>OnCreateFileHandlerSuccess
Wywołuje się, gdy program obsługi został utworzony pomyślnie.
  
### <a name="oncreatefilehandlerfailure"></a>OnCreateFileHandlerFailure
Wywołuje się, gdy nie można utworzyć programu obsługi z powodu błędu.
  
### <a name="ongetlabelsuccess"></a>OnGetLabelSuccess
Wywołuje się, gdy etykiety są pomyślnie pobrane.
  
### <a name="ongetlabelfailure"></a>OnGetLabelFailure
Metoda wywoływana podczas pobierania etykiety nie powiodło się z powodu błędu.
  
### <a name="ongetprotectionsuccess"></a>OnGetProtectionSuccess
Wywołuje się, gdy zasady ochrony jest pomyślnie pobrane.
  
### <a name="ongetprotectionfailure"></a>OnGetProtectionFailure
Wywołuje się, gdy trwa pobieranie zasad ochrony nie powiodło się z powodu błędu.
  
### <a name="oncommitsuccess"></a>OnCommitSuccess
Wywoływane, gdy zatwierdzania zmian do pliku zakończyły się pomyślnie.
  
### <a name="oncommitfailure"></a>OnCommitFailure
Wywołuje się, gdy zatwierdzania zmian do pliku nie powiodło się z powodu błędu.