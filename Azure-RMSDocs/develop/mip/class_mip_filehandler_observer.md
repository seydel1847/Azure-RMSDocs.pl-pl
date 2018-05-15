# <a name="class-mipfilehandlerobserver"></a>Klasa mip::FileHandler::Observer 
[Obserwator](class_mip_filehandler_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomień dla pliku programu obsługi zdarzeń powiązanych.
Jeśli * wystąpi zdarzenie błędu, obiekt błąd zawiera wewnątrz [mip::Error](class_mip_error.md) klasy. Klient powinien nie wywołania aparat zwrotnego w wątku, który wywołuje obserwatora.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny wirtualny ~Observer()  | _Nie została jeszcze udokumentowane._
publiczny OnGetLabelSuccess void (const std::shared_ptr<ContentLabel>& etykiety, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy etykiety są pobierane pomyślnie (z pliku).
publiczny OnGetLabelFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy pobieranie etykiety (z pliku) nie powiodło się z powodu błędu.
publiczny OnGetProtectionSuccess void (const std::shared_ptr<UserPolicy>& userPolicy, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy zasady ochrony jest pomyślnie pobrane (z pliku).
publiczny OnGetProtectionFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy pobierania zasad ochrony (z pliku) nie powiodło się z powodu błędu.
publiczny OnCommitSuccess void (zatwierdzone bool, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy pomyślne zatwierdzenie zmian do pliku.
publiczny OnCommitFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy zatwierdzania zmian w pliku nie powiodło się z powodu błędu.
 Observer() chronionych  | _Nie została jeszcze udokumentowane._
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="observer"></a>~ Obserwatora
_Jeszcze nie udokumentowane._

  
### <a name="ongetlabelsuccess"></a>OnGetLabelSuccess
Wywoływane, gdy etykiety są pobierane pomyślnie (z pliku).
  
### <a name="ongetlabelfailure"></a>OnGetLabelFailure
Wywoływane, gdy pobieranie etykiety (z pliku) nie powiodło się z powodu błędu.
  
### <a name="ongetprotectionsuccess"></a>OnGetProtectionSuccess
Wywoływane, gdy zasady ochrony jest pomyślnie pobrane (z pliku).
  
### <a name="ongetprotectionfailure"></a>OnGetProtectionFailure
Wywoływane, gdy pobierania zasad ochrony (z pliku) nie powiodło się z powodu błędu.
  
### <a name="oncommitsuccess"></a>OnCommitSuccess
Wywoływane, gdy pomyślne zatwierdzenie zmian do pliku.
  
### <a name="oncommitfailure"></a>OnCommitFailure
Wywoływane, gdy zatwierdzania zmian w pliku nie powiodło się z powodu błędu.
  
### <a name="observer"></a>Obserwatora
_Jeszcze nie udokumentowane._
