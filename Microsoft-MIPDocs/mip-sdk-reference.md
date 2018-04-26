# <a name="mip-sdk-for-c-preview-reference"></a>Zestaw SDK MCI odwołania C++ (wersja zapoznawcza)

Microsoft informacji ochrony (MCI) zestawu SDK dla języka C++ (wersja zapoznawcza) umożliwia deweloperom zarządzania i zastosowania zasad ochrony danych do danych i innych zasobów cyfrowych.  

Aby dowiedzieć się więcej, zobacz [blog deweloperów Mipmapy](https://aka.ms/MIPDevelopers) i [przykłady MCI](https://aka.ms/mipsdksamples).

MCI zestawu SDK dla języka C++ zawiera następujące klasy:

| Nazwa klasy | Opis |
| :----------|:------------|
[MIP::Action](class_mip_action.md) | Klasa podstawowa dla wszystkich akcji. |
[MIP::AddContentFooterAction](class_mip_addcontentfooteraction.md) | Klasy akcji, która określa Dodawanie zawartości stopki do dokumentu.
[MIP::addContentHeaderAction](class_mip_addcontentheaderaction.md) | Klasa akcji, która określa Dodawanie nagłówka zawartości.
[MIP::AddWatermarkAction](class_mip_addwatermarkaction.md) | Klasa akcji, która określa dodanie znaku wodnego.
[MIP::BadInputError](class_mip_badinputerror.md) | Zły błąd wejścia, danych wejściowych do interfejsu API jest nieprawidłowa.
[MIP::CommonRights](class_mip_commonrights.md) | Powszechnie obsługiwanych prawa.
[MIP::consent](class_mip_consent.md) | Reprezentuje użytkownika akceptacji/odmowy akcji zezwalania z akcją.
[MIP::ConsentCallback](class_mip_consentcallback.md) | Interfejs na potrzeby powiadomień żądania zgody.
[MIP::ConsentResult](class_mip_consentresult.md) | Przedstawia wynik żądania zgody po interakcji z użytkownikiem.
[MIP::ContentLabel](class_mip_contentlabel.md) | Abstrakcja etykiety Microsoft Information Protection, która jest stosowana do elementu zawartości, zwykle dokumentu.
[MIP::CustomAction](class_mip_customaction.md) | Klasy ogólne akcji, która przechwytuje wszystkie podrzędne właściwości działania jako zbiór właściwości.
[MIP::CustomProtectedStream](class_mip_customprotectedstream.md) | Opakowuje strumienia, aby zapewnić przezroczystego szyfrowania i odszyfrowywania na odczyt i zapis.
[MIP::EditableDocumentRights](class_mip_editabledocumentrights.md) | Prawa dotyczące dokumentów edytowalnych.
[MIP::EmailRights](class_mip_emailrights.md) | Prawa dotyczące wiadomości e-mail.
[MIP::Error](class_mip_error.md) | Klasa podstawowa dla wszystkich błędów, które będą zgłaszane (wyjątek lub zwróciło) z pakietu SDK Mipmapy.
[MIP::ExecutionState](class_mip_executionstate.md) | Interfejs dla wszystkich stanów konieczne jest wykonanie przez aparat.
[MIP::EileEngine](class_mip_fileengine.md) | Interfejs dla wszystkich funkcji aparatu.
[MIP::FileEngine::Settings](class_mip_fileengine_settings.md) | 
[MIP::FileHandler](class_mip_filehandler.md) | Interfejs do pliku wszystkie funkcje obsługi.
[MIP::FileHandler::Observer](class_mip_filehandler_observer.md) | Zdarzenia związane z interfejsu obserwatora, aby klienci mogli otrzymywać powiadomień do obsługi plików.
[MIP::FileIOError](class_mip_fileioerror.md) | Błąd We/Wy pliku.
[MIP::FileProfile](class_mip_fileprofile.md) | Klasy głównym operacjach Microsoft Information Protection.
[MIP::FileProfile::Observer](class_mip_fileprofile_observer.md) | Obserwator interfejs używany do odbierania powiadomień o zdarzeniach dotyczących profilu.
[MIP::FileProfile::Settings](class_mip_fileprofile_settings.md) | Interfejs do zarządzania ustawienia profilu z pliku.
[MIP::GetUserPolicyResult](class_mip_getuserpolicyresult.md) | W tym artykule opisano wyniki nabycia żądania zasad użytkownika.
[MIP::InternalError](class_mip_internalerror.md) | Błąd wewnętrzny zestawu SDK. Nieoczekiwany coś się stało.
[MIP::IStream](class_mip_istream.md) | Podstawowy interfejs dla strumieni chronionych.
[MIP::JustificationRequiredError](class_mip_justificationrequirederror.md) | Żądana zmiana wymaga wyjaśnienie zmiany.
[MIP::JustifyAction](class_mip_justifyaction.md) | Żądanie wymaga uzasadnienie obniżenia poziomu etykiety i ustawienie odpowiedzi w trakcie wykonywania.
[MIP::Label](class_mip_label.md) | Abstrakcja dla jednej etykiety Microsoft Information Protection.
[MIP::LabelingOptions](class_mip_labelingoptions.md) | Interfejs do konfigurowania opcji etykietowania dla metody SetLabel.
[MIP::MetadataAction](class_mip_metadataaction.md) | Akcja, określania informacji o metadanych do dodania do zawartości.
[MIP::NetworkError](class_mip_networkerror.md) | Wystąpił błąd sieci.
[MIP::NotSupportedError](class_mip_notsupportederror.md) | Błąd operacja nie jest obsługiwana.
[MIP::PolicyDescriptor](class_mip_policydescriptor.md) | Reprezentuje zasad ad hoc skojarzone z zawartości chronionej.
[MIP::PolicyEngine](class_mip_policyengine.md) | Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
[MIP::PolicyEngine::Settings](class_mip_policyengine_settings.md) | Podaj wystąpienia tej klasy z approprieted, musi należeć do parametrów można zainicjować aparatu.
[MIP::PrivilegedRequiredError](class_mip_privilegedrequirederror.md) | Bieżącej etykiety została ustawiona przez privilidge nie można zastąpić metody przypisania.
[MIP::profile](class_mip_profile.md) | Klasy głównym operacjach Microsoft Information Protection.
[MIP::profile::Observer](class_mip_profile_observer.md) | Interfejs używany do odbierania powiadomień dla profilu powiązane powiadomienia o zdarzeniach.
[MIP::profile::Settings](class_mip_profile_settings.md) | Konfiguruje ustawienia profilu.
[MIP::ProtectAdhocAction](class_mip_protectadhocaction.md) | Klasy akcji, która określa dodawania ochrony ad hoc do dokumentu.  
[MIP::ProtectbyTemplateAction](class_mip_protectbytemplateaction.md) | Klasy akcji, która określa dodawania ochrony za pomocą szablonu w dokumencie.
[MIP::ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md) | Klasy akcji, która określa Dodawanie nie przesyłaj dalej ochrony dokumentu.
[MIP::ProtectionProfile](class_mip_protectionprofile.md) | Klasa podstawowa używana do wykonywania operacji ochrony.
[MIP::ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) | Użyj, aby otrzymywać powiadomienia profilu ochrony.
[MIP::ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) | Ustawienia profilu ochrony używane przez cały czas życia wystąpienia.
[MIP::RemoveContentFooterAction](class_mip_removecontentfooteraction.md) | Klasy akcji, która określa usunięcie stopki zawartości z dokumentu.
[MIP::RemoveContentHeaderAction](class_mip_removecontentheaderaction.md) | Klasy akcji, która określa usunięcie nagłówka zawartości z dokumentu.
[MIP::RemoveProtectionAction](class_mip_removeprotectionaction.md) | Klasy akcji, która określa usuwanie ochrony z dokumentu.
[MIP::RemoveWatermarkAction](class_mip_removewatermarkaction.md) | Klasy akcji, która określa usuwanie znaki wodne z dokumentu.
[MIP::RMSCryptographyException](class_mip_rmscryptographyexception.md) | Wyjątek kryptografii usług RMS.
[MIP::RMSException](class_mip_rmsexception.md) | Wyjątek podstawowej usługi RMS.
[MIP::RMSInvalidArgumentException](class_mip_rmsinvalidargumentexception.md) | Wyjątek nieprawidłowego argumentu usługi RMS.
[MIP::RMSLogicException](class_mip_rmslogicexception.md) | Wyjątek logiki usługi RMS.
[MIP::RMSNetworkException](class_mip_rmsnetworkexception.md) | Wyjątek sieci usługi RMS.
[MIP::RMSNotFoundException](class_mip_rmsnotfoundexception.md) | Nie można odnaleźć wyjątek usługi RMS.
[MIP::RMSNullPointerException](class_mip_rmsnullpointerexception.md) | Wyjątek pustego wskaźnika usługi RMS.
[MIP::RMSOfficeFileException](class_mip_rmsofficefileexception.md) | Wyjątek pliku RMS Office.
[MIP::RMSPFileException](class_mip_rmspfileexception.md) | Wyjątek PFile usługi RMS.
[MIP::RMSRightsException](class_mip_rmsrightsexception.md) | Wyjątek praw usług RMS.
[MIP::RMSStreamException](class_mip_rmsstreamexception.md) | Wyjątek strumienia usługi RMS.
[MIP::Roles](class_mip_roles.md) | Definiuje ról do ochrony danych.
[MIP::Stream](class_mip_stream.md) | Klasa, która definiuje interfejs między MCI sdk i strumieni na podstawie zawartości.
[MIP::TemplateDescriptor](class_mip_templatedescriptor.md) | W tym artykule opisano szablon usług RMS.
[MIP::UserPolicy](class_mip_userpolicy.md) | Reprezentuje zasady skojarzone z zawartości chronionej.
[MIP::UserRights](class_mip_userrights.md) | Reprezentuje grupę użytkowników i praw skojarzonych z nimi.
[MIP::UserRoles](class_mip_userroles.md) | Reprezentuje grupę użytkowników i ról związanych z nimi.
 
