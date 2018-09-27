# <a name="mip-sdk-for-c-preview-reference"></a>SDK MIP dla odwołania do C++ (wersja zapoznawcza)

Microsoft informacji ochrony (MIP) zestawu SDK dla języka C++ (wersja zapoznawcza) pozwala deweloperom na zarządzanie i zastosować zasady ochrony danych do danych i innych zasobów cyfrowych.  

Aby dowiedzieć się więcej, zobacz [blog deweloperów MIP](https://aka.ms/MIPDevelopers)<!-- and [MIP samples](https://aka.ms/mipsdksamples)-->.

Zestaw SDK MIP dla języka C++ zawiera:

- [Wyliczenia i struktury](mip-enums-and-structs.md)
- [Funkcje](mip-functions.md)
- Następujące klasy:

| Nazwa klasy | Opis |
| :----------|:------------|
[ConsentDelegate](class_consentdelegate.md)  |  Delegat o zgodę operacji związanych z.
[MIP::AccessDeniedError](class_mip_accessdeniederror.md)  |  Użytkownik nie można uzyskać dostępu do zawartości. np. Brak uprawnień zawartości odwołany itp.
[MIP::Action](class_mip_action.md)  |  Interfejs dla akcji. Każda akcja przekłada się na kroku, które należy podjąć przez aplikację, aby zastosować etykietę (zgodnie z definicją w zasadach)
[MIP::AddContentFooterAction](class_mip_addcontentfooteraction.md)  |  Klasy akcji, która określa Dodawanie zawartości stopki do dokumentu.
[MIP::AddContentHeaderAction](class_mip_addcontentheaderaction.md)  |  Klasa akcji, która określa Dodawanie nagłówka zawartości.
[MIP::AddWatermarkAction](class_mip_addwatermarkaction.md)  |  Klasa akcji, która określa Dodawanie znaku wodnego.
[MIP::ApplyLabelAction](class_mip_applylabelaction.md)  |  Stosowanie etykiety akcji wymaga aplikacji wywołującej, aby zastosować etykietę.
[MIP::BadInputError](class_mip_badinputerror.md)  |  Zły błędów wejścia zgłaszany, gdy dane wejściowe do zestaw sdk interfejsu api jest nieprawidłowa.
[MIP::ClassificationResult](class_mip_classificationresult.md)  |  Klasa, która zawiera wynik wywołania klasyfikacji dla stanu wykonywania.
[MIP::consent](class_mip_consent.md)|Reprezentuje użytkownika akceptacji/odmowy, aby zezwolić na akcję.
[MIP::ConsentCallback](class_mip_consentcallback.md)|Interfejs do wyrażania zgody żądania powiadomienia.
[MIP::ConsentDeniedError](class_mip_consentdeniederror.md) |  Operacja, która wymaga zgody użytkownika nie uzyskał zgody.
[MIP::ConsentResult](class_mip_consentresult.md)|W tym artykule opisano wynik żądania zgody po interakcji z użytkownikiem.
[MIP::ContentLabel](class_mip_contentlabel.md)  |  Abstrakcję etykietę Microsoft Information Protection, która jest stosowana do fragmentu zawartości, zazwyczaj dokumentu.
[MIP::CustomAction](class_mip_customaction.md)  |  [Akcja niestandardowa](class_mip_customaction.md) jest klasą Akcja ogólna, która przechwytuje wszystkie właściwości podrzędnych działania jako zbiór właściwości. Obiekt wywołujący odpowiada może zrozumieć znaczenie akcji.
[MIP::CustomProtectedStream](class_mip_customprotectedstream.md)|Opakowuje strumienia do udostępniania przezroczyste szyfrowanie i odszyfrowywanie na odczyt i zapis.
[MIP::Error](class_mip_error.md)  |  Klasa podstawowa dla wszystkich błędów, które będą zgłaszane (generowany lub zwrócone) z zestawu SDK MIP.
[MIP::ExecutionState](class_mip_executionstate.md)  |  Interfejs dla wszystkich stanów, które są wymagane do wykonania z aparatem.
[MIP::FileEngine::Settings](class_mip_fileengine::settings.md)  | _Jeszcze nie udokumentowano._
[MIP::FileEngine](class_mip_fileengine.md)  |  Interfejs dla wszystkich funkcji aparatu.
[MIP::FileHandler::Observer](class_mip_filehandler::observer.md)  |  [Obserwator](class_mip_filehandler_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomienia dla pliku zdarzenia związane z programu obsługi.
[MIP::FileHandler](class_mip_filehandler.md)  |  Interfejs dla wszystkich plików, funkcje obsługi.
[MIP::FileIOError](class_mip_fileioerror.md)  |  Błąd We/Wy pliku.
[MIP::FileProfile::Observer](class_mip_fileprofile_observer.md)  |  [Obserwator](class_mip_fileprofile_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomienia dla profilu zdarzenia związane z.
[MIP::FileProfile::Settings](class_mip_fileprofile_settings.md)  |  Ustawienia używane przez [FileProfile](class_mip_fileprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[MIP::FileProfile](class_mip_fileprofile.md)  |  [FileProfile](class_mip_fileprofile.md) klasy jest klasą głównego dla przy użyciu operacji Microsoft Information Protection.
[MIP::GetUserPolicyResult](class_mip_getuserpolicyresult.md)|W tym artykule opisano wyniki nabycia żądania zasad użytkownika.
[MIP::HttpDelegate](class_mip_httpdelegate.md)  |  Interfejs dla zastępowanie obsługi protokołu http.
[MIP::HttpRequest](class_mip_httprequest.md)  |  Interfejs, który opisuje żądania http jednym.
[MIP::HttpResponse](class_mip_httpresponse.md)  |  Interfejs, który opisuje odpowiedzi http pojedynczego, implementowane przez aplikację klienta, gdy zastępowanie [HttpDelegate](class_mip_httpdelegate.md).
[MIP::InternalError](class_mip_internalerror.md)  |  Błąd wewnętrzny. Ten błąd jest zgłaszany, gdy zdarzy się coś nieoczekiwanego podczas wykonywania.
[MIP::IStream](class_mip_istream.md)|Podstawowy interfejs dla strumieni chronionych.
[MIP::JustificationRequiredError](class_mip_justificationrequirederror.md)  | _Jeszcze nie udokumentowano._
[MIP::JustifyAction](class_mip_justifyaction.md)  |  Wyjustuj do [akcji](class_mip_action.md) wymaga dostarczanie uzasadnienie obniżenia poziomu etykiety i ustawienia odpowiedzi w trakcie wykonywania.
[MIP::Label](class_mip_label.md)  |  Abstrakcyjną dla pojedynczej etykiecie Microsoft Information Protection.
[MIP::LabelingOptions](class_mip_labelingoptions.md)  |  Interfejs do konfigurowania opcji etykietowania dla metody SetLabel.
[MIP::LoggerDelegate](class_mip_loggerdelegate.md)  |  Klasa, która definiuje interfejs do rejestratora MIP SDK.
[MIP::MetadataAction](class_mip_metadataaction.md)  |  [Akcji](class_mip_action.md) dodająca informacji o metadanych do zawartości.
[MIP::NetworkError](class_mip_networkerror.md)  |  Błąd sieci. Przyczyną nieoczekiwane zachowanie podczas nawiązywania połączeń sieciowych do punktów końcowych usługi.
[MIP::NotSupportedError](class_mip_notsupportederror.md)  |  Operacja żądany przez aplikację nie jest obsługiwane przez zestaw sdk.
[MIP::PolicyDescriptor](class_mip_policydescriptor.md)|Reprezentuje zasad ad hoc, skojarzone z zawartości chronionej.
[MIP::PolicyEngine::Settings](class_mip_policyengine_settings.md)  |  Wystąpienie tej klasy z odpowiednimi parametrami powinien zapewniać można zainicjować aparatu.
[MIP::PolicyEngine](class_mip_policyengine.md)  |  Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
[MIP::PrivilegedRequiredError](class_mip_privilegedrequirederror.md)  |  Bieżąca etykieta zostało przypisane jako uprzywilejowaną operacją (odpowiednik operacji administratora), w związku z tym nie może zostać zastąpiony.
[MIP::profile::Observer](class_mip_profile_observer.md)  |  [Obserwator](class_mip_profile_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomienia dla profilu zdarzenia związane z.
[MIP::profile::Settings](class_mip_profile_settings.md)  |  [Ustawienia](class_mip_profile_settings.md) posługują się [profilu](class_mip_profile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[MIP::profile](class_mip_profile.md)  |  [Profil](class_mip_profile.md) klasy jest klasą głównego dla przy użyciu operacji Microsoft Information Protection. Typowa aplikacja będzie potrzebny tylko jeden [profilu](class_mip_profile.md) , ale można utworzyć wiele profilów, jeśli to konieczne.
[MIP::ProtectAdhocAction](class_mip_protectadhocaction.md)  |  Klasy akcji, która określa dodawania ochrony ad hoc do dokumentu.
[MIP::ProtectByTemplateAction](class_mip_protectbytemplateaction.md)  |  Klasy akcji, która określa dodawania ochrony za pomocą szablonu do dokumentu.
[MIP::ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md)  |  Klasy akcji, który określa Dodawanie nie przesyłaj dalej ochrony dokumentu.
[MIP::ProtectionDescriptor](class_mip_protectiondescriptor.md)  |  Reprezentuje zasad ad hoc, skojarzone z zawartości chronionej.
[MIP::ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)  |  Reprezentuje zasad ad hoc, skojarzone z zawartości chronionej.
[MIP::ProtectionEngine::Observer](class_mip_protectionengine_observer.md)  |  Interfejs, który odbiera powiadomienia związane z [ProtectionEngine](class_mip_protectionengine.md).
[MIP::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)  |  [Ustawienia](class_mip_protectionengine_settings.md) posługują się [ProtectionEngine](class_mip_protectionengine.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[MIP::ProtectionEngine](class_mip_protectionengine.md)  |  Wykonuje działania związanych z ochroną, odnoszące się do określonej tożsamości.
[MIP::ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)  |  Interfejs, który odbiera powiadomienia związane z [ProtectionHandler](class_mip_protectionhandler.md).
[MIP::ProtectionHandler](class_mip_protectionhandler.md)  |  Wykonuje akcje dotyczące ochrony dla konfiguracji ochrony określonych (czyli użytkowników, prawa, role itp.)
[MIP::ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)  |  Interfejs, który odbiera powiadomienia związane z [ProtectionProfile](class_mip_protectionprofile.md).
[MIP::ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)  |  [Ustawienia](class_mip_protectionprofile_settings.md) posługują się [ProtectionProfile](class_mip_protectionprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[MIP::ProtectionProfile](class_mip_protectionprofile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md) jest klasą głównego do wykonywania operacji ochrony.
[MIP::RecommendLabelAction](class_mip_recommendlabelaction.md)  |  Zaleca się etykieta działania jest przeznaczona do zasugerować etykiet do użytkowników. Pominięcie tego wywołania po użytkownik ignoruje zalecana etykieta powinna być podejmowana za pośrednictwem obsługiwanych akcji dla stanu wykonywania.
[MIP::RemoveContentFooterAction](class_mip_removecontentfooteraction.md)  |  Klasa akcji, który określa usunięcie stopki zawartości z dokumentu.
[MIP::RemoveContentHeaderAction](class_mip_removecontentheaderaction.md)  |  Klasy akcji, która określa usunięcie nagłówka zawartości z dokumentu.
[MIP::RemoveProtectionAction](class_mip_removeprotectionaction.md)  |  Klasa akcji, który określa usunięcie ochrony z dokumentu.
[MIP::RemoveWatermarkAction](class_mip_removewatermarkaction.md)  |  Klasa akcji, który określa, usuwając znaki wodne z dokumentu.
[MIP::RMSCryptographyException](class_mip_rmscryptographyexception.md)|Wyjątek kryptografii usługi RMS.
[MIP::RMSException](class_mip_rmsexception.md)|Wyjątek podstawowy usługi RMS.
[MIP::RMSInvalidArgumentException](class_mip_rmsinvalidargumentexception.md)|Wyjątek usługi RMS dla nieprawidłowe argumenty.
[MIP::RMSLogicException](class_mip_rmslogicexception.md)|Wyjątek logiki usługi RMS.
[MIP::RMSNetworkException](class_mip_rmsnetworkexception.md)|Wyjątek sieci usługi RMS.
[MIP::RMSNotFoundException](class_mip_rmsnotfoundexception.md)|Nie można odnaleźć wyjątek usługi RMS.
[MIP::RMSNullPointerException](class_mip_rmsnullpointerexception.md)|Wyjątek pustego wskaźnika usługi RMS.
[MIP::RMSOfficeFileException](class_mip_rmsofficefileexception.md)|Wyjątek pliku RMS Office.
[MIP::RMSPFileException](class_mip_rmspfileexception.md)|Wyjątek PFile usługi RMS.
[MIP::RMSRightsException](class_mip_rmsrightsexception.md)|Wyjątek praw usług RMS.
[MIP::RMSStreamException](class_mip_rmsstreamexception.md)|Wyjątek strumienia usługi RMS.
[MIP::Stream](class_mip_stream.md)|Klasa, która definiuje interfejs między MIP zestaw SDK, na podstawie strumienia zawartości.
[MIP::TemplateDescriptor](class_mip_templatedescriptor.md)|W tym artykule opisano szablonu usługi RMS.
[MIP::TransientNetworkError](class_mip_transientnetworkerror.md)  |  Przejściowy błąd sieci. Przyczyną nieoczekiwane zachowanie podczas nawiązywania połączeń sieciowych do punktów końcowych usługi. Mogą być ponawiane operacji, ponieważ jest to błąd przejściowy.
[MIP::UserPolicy](class_mip_userpolicy.md)|Reprezentuje zasady skojarzone z zawartości chronionej.
[MIP::UserRights](class_mip_userrights.md)  |  Reprezentuje grupę użytkowników i praw skojarzonych z nimi.
[MIP::UserRoles](class_mip_userroles.md)  |  Reprezentuje grupę użytkowników i ról związanych z nimi.

