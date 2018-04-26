# <a name="class-mipfilehandlerobserver"></a>Klasa mip::FileHandler::Observer 
[Obserwator](#classmip_1_1_file_handler_1_1_observer) interfejsu, aby klienci mogli otrzymywać powiadomień dla pliku programu obsługi zdarzeń powiązanych.
Jeśli * wystąpi zdarzenie błędu, obiekt błąd zawiera wewnątrz [mip::Error](#classmip_1_1_error) klasy. Klient powinien nie wywołania aparat zwrotnego w wątku, który wywołuje obserwatora.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
wbudowany publiczny wirtualny ~ obserwatora | 
publiczny typ void OnGetLabelSuccessContentLabel > & etykietę const std::shared_ptr < void > & kontekstu) | Wywoływane, gdy etykiety są pobierane pomyślnie (z pliku).
publiczny OnGetLabelFailure void | Wywoływane, gdy pobieranie etykiety (z pliku) nie powiodło się z powodu błędu.
publiczny typ void OnGetProtectionSuccessUserPolicy > & userPolicy, const std::shared_ptr < void > & kontekstu) | Wywoływane, gdy zasady ochrony jest pomyślnie pobrane (z pliku).
publiczny OnGetProtectionFailure void | Wywoływane, gdy pobierania zasad ochrony (z pliku) nie powiodło się z powodu błędu.
publiczny OnCommitSuccess void | Wywoływane, gdy pomyślne zatwierdzenie zmian do pliku.
publiczny OnCommitFailure void | Wywoływane, gdy zatwierdzania zmian w pliku nie powiodło się z powodu błędu.
wbudowany chronionych obserwatora | 
## <a name="members"></a>Elementy członkowskie
### <a name="observer"></a>~ Obserwatora
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