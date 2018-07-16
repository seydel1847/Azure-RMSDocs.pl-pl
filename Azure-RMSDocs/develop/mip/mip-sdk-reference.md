# <a name="mip-sdk-for-c-preview-reference"></a>SDK MIP dla odwołania do C++ (wersja zapoznawcza)

Microsoft informacji ochrony (MIP) zestawu SDK dla języka C++ (wersja zapoznawcza) pozwala deweloperom na zarządzanie i zastosować zasady ochrony danych do danych i innych zasobów cyfrowych.  

Aby dowiedzieć się więcej, zobacz [blog deweloperów MIP](https://aka.ms/MIPDevelopers)<!-- and [MIP samples](https://aka.ms/mipsdksamples)-->.

Zestaw SDK MIP dla języka C++ zawiera:

- [Wyliczenia i struktury](mip-enums-and-structs.md)
- [Funkcje](mip-functions.md)
- Następujące klasy:

| Nazwa klasy | Opis |
| :----------|:------------|
[ConsentDelegate](class_consentdelegate.md)  |  Delegat dla operacji związanych z zgody.
[MIP::AccessDeniedError](class_mip_accessdeniederror.md)  |  Użytkownik nie można uzyskać dostępu do zawartości, takiej jak odmowa dostępu, zawartość odwołany i tak dalej.
[MIP::Action](class_mip_action.md)  |  Interfejs dla akcji. Każda akcja przekłada się na kroku, które należy podjąć przez aplikację, aby zastosować etykietę (zgodnie z definicją w zasadach)
[MIP::AddContentFooterAction](class_mip_addcontentfooteraction.md)  |  Klasa akcji, która określa zawartości stopkę ma zostać dodany do dokumentu.
[MIP::AddContentHeaderAction](class_mip_addcontentheaderaction.md)  |  Klasa akcji, która określa Dodawanie nagłówka zawartości.
[MIP::AddWatermarkAction](class_mip_addwatermarkaction.md)  |  Klasa akcji, która określa Dodawanie znaku wodnego.
[MIP::ApplyLabelAction](class_mip_applylabelaction.md)  |  Stosowanie etykiety akcji wymaga aplikacji wywołującej, aby zastosować etykietę.
[MIP::BadInputError](class_mip_badinputerror.md)  |  Zły błędów wejścia zgłaszany, gdy dane wejściowe do zestaw sdk interfejsu api jest nieprawidłowa.
[MIP::ClassificationResult](class_mip_classificationresult.md)  |  Klasa, która zawiera wynik wywołania klasyfikacji dla stanu wykonywania.
[MIP::ContentLabel](class_mip_contentlabel.md)  |  Abstrakcję etykietę Microsoft Information Protection, która jest stosowana do fragmentu zawartości, zazwyczaj dokumentu.
[MIP::CustomAction](class_mip_customaction.md)  |  [Akcja niestandardowa](class_mip_customaction.md) jest klasą Akcja ogólna, która przechwytuje wszystkie właściwości działania jako zbiór właściwości. Obiekt wywołujący odpowiada może zrozumieć znaczenie akcji.
[MIP::Error](class_mip_error.md)  |  Klasa podstawowa dla wszystkich błędów, które będą zgłaszane (generowany lub zwrócone) z zestawu SDK MIP.
[MIP::ExecutionState](class_mip_executionstate.md)  |  Interfejs dla wszystkich stanów, które są wymagane do wykonania z aparatem.
[MIP::FileEngine](class_mip_fileengine.md)  |  Interfejs dla wszystkich funkcji aparatu.
[MIP::FileEngine::Settings](class_mip_fileengine::settings.md)  | _Jeszcze nie udokumentowano._
[MIP::FileHandler](class_mip_filehandler.md)  |  Interfejs dla wszystkich plików, funkcje obsługi.
[MIP::FileHandler::Observer](class_mip_filehandler::observer.md)  |  [Obserwator](class_mip_filehandler_observer.md)-interfejsu, aby klienci mogli otrzymywać powiadomienia dla pliku zdarzenia związane z programu obsługi.
[MIP::FileIOError](class_mip_fileioerror.md)  |  Błąd We/Wy pliku.
[MIP::FileProfile](class_mip_fileprofile.md)  |  [FileProfile](class_mip_fileprofile.md) klasy jest klasą głównego dla przy użyciu operacji Microsoft Information Protection.
[MIP::FileProfile::Observer](class_mip_fileprofile_observer.md)  |  [Obserwator](class_mip_fileprofile_observer.md)— interfejs dla klientów na uzyskanie powiadomienia dotyczące zdarzenia związane z profilem.
[MIP::FileProfile::Settings](class_mip_fileprofile_settings.md)  |  [Ustawienia](class_mip_fileprofile_settings.md) posługują się [FileProfile](class_mip_fileprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[MIP::InternalError](class_mip_internalerror.md)  |  Błąd wewnętrzny. Ten błąd jest zgłaszany, gdy zdarzy się coś nieoczekiwanego podczas wykonywania.
[MIP::JustificationRequiredError](class_mip_justificationrequirederror.md)  | _Jeszcze nie udokumentowano._
[MIP::JustifyAction](class_mip_justifyaction.md)  |  Wyjustuj do [akcji](class_mip_action.md) wymaga dostarczanie uzasadnienie obniżenia poziomu etykiety i ustawienia odpowiedzi w trakcie wykonywania.
[MIP::Label](class_mip_label.md)  |  Abstrakcyjną dla pojedynczej etykiecie Microsoft Information Protection.
[MIP::LabelingOptions](class_mip_labelingoptions.md)  |  Interfejs do konfigurowania opcji etykietowania dla metody SetLabel.
[MIP::LoggerDelegate](class_mip_loggerdelegate.md)  |  Klasa, która definiuje interfejs do rejestratora MIP SDK.
[MIP::MetadataAction](class_mip_metadataaction.md)  |  [Akcji](class_mip_action.md) dodająca informacji o metadanych do zawartości.
[MIP::NetworkError](class_mip_networkerror.md)  |  Błąd sieci. Przyczyną nieoczekiwane zachowanie podczas nawiązywania połączeń sieciowych do punktów końcowych usługi.
[MIP::NotSupportedError](class_mip_notsupportederror.md)  |  Operacja żądany przez aplikację nie jest obsługiwane przez zestaw sdk.
[MIP::PolicyEngine](class_mip_policyengine.md)  |  Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
[MIP::PolicyEngine::Settings](class_mip_policyengine_settings.md)  |  Wystąpienie tej klasy z odpowiednimi parametrami, należy podać można zainicjować aparatu.
[MIP::PrivilegedRequiredError](class_mip_privilegedrequirederror.md)  |  Bieżąca etykieta zostało przypisane jako uprzywilejowaną operacją (odpowiednik operacji administratora), w związku z tym nie może zostać zastąpiony.
[MIP::profile](class_mip_profile.md)  |  [Profil](class_mip_profile.md) klasy jest klasą głównego dla przy użyciu operacji Microsoft Information Protection. Typowa aplikacja będzie potrzebny tylko jeden [profilu](class_mip_profile.md) , ale można utworzyć wiele profilów, jeśli to konieczne.
[MIP::profile::Observer](class_mip_profile_observer.md)  |  [Obserwator](class_mip_profile_observer.md)-interfejsu, aby klienci mogli otrzymywać powiadomienia dla profilu zdarzenia związane z.
[MIP::profile::Settings](class_mip_profile_settings.md)  |  [Ustawienia](class_mip_profile_settings.md) posługują się [profilu](class_mip_profile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[MIP::ProtectAdhocAction](class_mip_protectadhocaction.md)  |  Klasy akcji, która określa dodawania ochrony ad hoc do dokumentu.
[MIP::ProtectByTemplateAction](class_mip_protectbytemplateaction.md)  |  Klasy akcji, która określa dodawania ochrony za pomocą szablonu do dokumentu.
[MIP::ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md)  |  Klasy akcji, który określa Dodawanie nie przesyłaj dalej ochrony dokumentu.
[MIP::ProtectionDescriptor](class_mip_protectiondescriptor.md)  |  Reprezentuje zasad ad hoc, skojarzone z zawartości chronionej.
[MIP::ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)  |  Reprezentuje zasad ad hoc, skojarzone z zawartości chronionej.
[MIP::ProtectionEngine](class_mip_protectionengine.md)  |  Wykonuje działania związanych z ochroną, odnoszące się do określonej tożsamości.
[MIP::ProtectionEngine::Observer](class_mip_protectionengine_observer.md)  |  Interfejs, który odbiera powiadomienia związane z [ProtectionEngine](class_mip_protectionengine.md).
[MIP::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)  |  [Ustawienia](class_mip_protectionengine_settings.md) posługują się [ProtectionEngine](class_mip_protectionengine.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[MIP::ProtectionHandler](class_mip_protectionhandler.md)  |  Wykonuje akcje dotyczące ochrony dla konfiguracji ochrony określonych (czyli użytkowników, prawa, role itp.)
[MIP::ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)  |  Interfejs, który odbiera powiadomienia związane z [ProtectionHandler](class_mip_protectionhandler.md).
[MIP::ProtectionProfile](class_mip_protectionprofile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md) jest klasą głównego do wykonywania operacji ochrony.
[MIP::ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)  |  Interfejs, który odbiera powiadomienia związane z [ProtectionProfile](class_mip_protectionprofile.md).
[MIP::ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)  |  [Ustawienia](class_mip_protectionprofile_settings.md) posługują się [ProtectionProfile](class_mip_protectionprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[MIP::RecommendLabelAction](class_mip_recommendlabelaction.md)  |  Zaleca się etykieta działania jest przeznaczona do zasugerować etykiet do użytkowników. Pominięcie tego wywołania po użytkownik ignoruje zalecana etykieta powinna być podejmowana za pośrednictwem obsługiwanych akcji dla stanu wykonywania.
[MIP::RemoveContentFooterAction](class_mip_removecontentfooteraction.md)  |  Klasa akcji, który określa usunięcie stopki zawartości z dokumentu.
[MIP::RemoveContentHeaderAction](class_mip_removecontentheaderaction.md)  |  Klasy akcji, która określa usunięcie nagłówka zawartości z dokumentu.
[MIP::RemoveProtectionAction](class_mip_removeprotectionaction.md)  |  Klasa akcji, który określa usunięcie ochrony z dokumentu.
[MIP::RemoveWatermarkAction](class_mip_removewatermarkaction.md)  |  Klasa akcji, który określa, usuwając znaki wodne z dokumentu.
[MIP::Stream](class_mip_stream.md)  |  Klasa, która definiuje interfejs między MIP zestaw SDK, na podstawie strumienia zawartości.
[MIP::UserRights](class_mip_userrights.md)  |  Reprezentuje grupę użytkowników i praw skojarzonych z nimi.
[MIP::UserRoles](class_mip_userroles.md)  |  Reprezentuje grupę użytkowników i ról związanych z nimi.

 
