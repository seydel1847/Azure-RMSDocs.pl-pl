---
title: SDK MIP dla odwołania do C++ (wersja zapoznawcza)
description: SDK MIP dla odwołania do C++ (wersja zapoznawcza)
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 06d8bb26a8e3026562006d68d4ae8d1630eba81c
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446332"
---
# <a name="mip-sdk-for-c-preview-reference"></a>SDK MIP dla odwołania do C++ (wersja zapoznawcza)

Microsoft informacji ochrony (MIP) zestawu SDK dla języka C++ (wersja zapoznawcza) pozwala deweloperom na zarządzanie i zastosować zasady ochrony danych do danych i innych zasobów cyfrowych.  

Aby dowiedzieć się więcej, zobacz [blog deweloperów MIP](https://aka.ms/MIPDevelopers)<!-- and [MIP samples](https://aka.ms/mipsdksamples)-->.

Zestaw SDK MIP dla języka C++ zawiera:

- [Wyliczenia i struktury](mip-enums-and-structs.md)
- [Funkcje](mip-functions.md)
- Następujące klasy:

| Nazwa klasy | Opis |
| :----------|:------------|
[AccessDeniedError](class_mip_accessdeniederror.md)  |  Użytkownik nie można uzyskać dostępu do zawartości. Na przykład brak uprawnień zawartości odwołany.
[Akcja](class_mip_action.md)  |  Interfejs dla akcji. Każda akcja przekłada się na kroku, które należy podjąć przez aplikację, aby zastosować etykietę (zgodnie z definicją w zasadach)
[AddContentFooterAction](class_mip_addcontentfooteraction.md)  |  Klasa akcji, która określa Dodawanie zawartości stopki do dokumentu.
[AddContentHeaderAction](class_mip_addcontentheaderaction.md)  |  Klasa akcji, która określa Dodawanie nagłówka zawartości.
[AddWatermarkAction](class_mip_addwatermarkaction.md)  |  Klasa akcji, która określa Dodawanie znaku wodnego.
[ApplyLabelAction](class_mip_applylabelaction.md)  |  Stosowanie etykiety akcji wymaga aplikacji wywołującej, aby zastosować etykietę.
[BadInputError](class_mip_badinputerror.md)  |  Zły błędów wejścia zgłaszany, gdy dane wejściowe do interfejsu API zestawu SDK są nieprawidłowe.
[ClassificationResult](class_mip_classificationresult.md)  |  Klasa, która zawiera wynik wywołania klasyfikacji dla stanu wykonywania.
[ConsentDelegate](class_consentdelegate.md)  |  Delegat o zgodę operacji związanych z.
[ConsentDeniedError](class_mip_consentdeniederror.md)  |  Operacja, która wymaga zgody użytkownika nie uzyskał zgody.
[ContentLabel](class_mip_contentlabel.md)  |  Abstrakcję etykietę Microsoft Information Protection, która jest stosowana do fragmentu zawartości, zazwyczaj dokumentu.
[CustomAction](class_mip_customaction.md)  |  [Akcja niestandardowa](class_mip_customaction.md) jest klasą Akcja ogólna, która przechwytuje wszystkie właściwości podrzędnych działania jako zbiór właściwości. Obiekt wywołujący odpowiada może zrozumieć znaczenie akcji.
[Error](class_mip_error.md)  |  Klasa podstawowa dla wszystkich błędów, które będą zgłaszane (generowany lub zwrócone) z zestawu SDK MIP.
[ExecutionState](class_mip_executionstate.md)  |  Interfejs dla wszystkich stanów, które są wymagane do wykonania z aparatem.
[FileEngine::Settings](class_mip_fileengine_settings.md)  | _Jeszcze nie udokumentowano._
[FileEngine](class_mip_fileengine.md)  |  Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
[FileHandler::Observer](class_mip_filehandler_observer.md)  |  [Obserwator](class_mip_filehandler_observer.md) interfejsu, aby klienci mogli odbierać powiadomienia zdarzenia związane z obsługi plików.
[FileHandler](class_mip_filehandler.md)  |  Interfejs dla wszystkich plików, funkcje obsługi.
[FileIOError](class_mip_fileioerror.md)  |  Błąd We/Wy pliku.
[FileProfile::Observer](class_mip_fileprofile_observer.md)  |  [Obserwator](class_mip_fileprofile_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomienia dla profilu zdarzenia związane z.
[FileProfile::Settings](class_mip_fileprofile_settings.md)  |  [Ustawienia](class_mip_fileprofile_settings.md) posługują się [FileProfile](class_mip_fileprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[FileProfile](class_mip_fileprofile.md)  |  [FileProfile](class_mip_fileprofile.md) klasy jest klasą głównego dla przy użyciu operacji Microsoft Information Protection.
[HttpDelegate](class_mip_httpdelegate.md)  |  Interfejs dla zastępowanie obsługi protokołu HTTP.
[httpRequest](class_mip_httprequest.md)  |  Interfejs, który opisuje pojedynczego żądania HTTP.
[HttpResponse](class_mip_httpresponse.md)  |  Interfejs, który opisuje jedną odpowiedź HTTP implementowane przez aplikację klienta, gdy zastępowanie [HttpDelegate](class_mip_httpdelegate.md).
[InternalError](class_mip_internalerror.md)  |  Błąd wewnętrzny. Ten błąd jest zgłaszany, gdy zdarzy się coś nieoczekiwanego podczas wykonywania.
[JustificationRequiredError](class_mip_justificationrequirederror.md)  | _Jeszcze nie udokumentowano._
[JustifyAction](class_mip_justifyaction.md)  |  Wyjustuj do [akcji](class_mip_action.md) wymaga dostarczanie uzasadnienie obniżenia poziomu etykiety i ustawienia odpowiedzi w trakcie wykonywania.
[Label](class_mip_label.md)  |  Abstrakcyjną dla pojedynczej etykiecie Microsoft Information Protection.
[LabelingOptions](class_mip_labelingoptions.md)  |  Interfejs do konfigurowania opcji etykietowania dla metod SetLabel/DeleteLabel.
[LoggerDelegate](class_mip_loggerdelegate.md)  |  Klasa, która definiuje interfejs do rejestratora MIP SDK.
[MetadataAction](class_mip_metadataaction.md)  |  [Akcji](class_mip_action.md) dodająca informacji o metadanych do zawartości.
[NetworkError](class_mip_networkerror.md)  |  Błąd sieci. Przyczyną nieoczekiwane zachowanie podczas nawiązywania połączeń sieciowych do punktów końcowych usługi.
[NotSupportedError](class_mip_notsupportederror.md)  |  Operacja żądany przez aplikację nie jest obsługiwane przez zestaw SDK.
[PolicyEngine::Settings](class_mip_policyengine_settings.md)  |  Definiuje ustawienia skojarzone z [PolicyEngine](class_mip_policyengine.md).
[PolicyEngine](class_mip_policyengine.md)  |  Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
[PolicyHandler](class_mip_policyhandler.md)  |  Ta klasa udostępnia interfejs dla wszystkich funkcji programu obsługi zasad w pliku.
[PolicyProfile::Observer](class_mip_policyprofile_observer.md)  |  [Obserwator](class_mip_policyprofile_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomienia dla profilu zdarzenia związane z.
[PolicyProfile::Settings](class_mip_policyprofile_settings.md)  |  [Ustawienia](class_mip_policyprofile_settings.md) posługują się [PolicyProfile](class_mip_policyprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[PolicyProfile](class_mip_policyprofile.md)  |  [PolicyProfile](class_mip_policyprofile.md) klasy jest klasą głównego dla przy użyciu operacji Microsoft Information Protection. Typowa aplikacja będzie potrzebny tylko jeden [PolicyProfile](class_mip_policyprofile.md) , ale można utworzyć wiele profilów, jeśli to konieczne.
[PolicySyncError](class_mip_policysyncerror.md)  |  Podjęto próbę synchronizacji danych zasad nie powiodło się.
[PrivilegedRequiredError](class_mip_privilegedrequirederror.md)  |  Bieżąca etykieta zostało przypisane jako uprzywilejowaną operacją (odpowiednik operacji administratora), w związku z tym nie może zostać zastąpiony.
[ProtectAdhocAction](class_mip_protectadhocaction.md)  |  Klasa akcji, która określa dodawania ochrony ad hoc do dokumentu.
[ProtectByTemplateAction](class_mip_protectbytemplateaction.md)  |  Klasa akcji, która określa dodawania ochrony za pomocą szablonu do dokumentu.
[ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md)  |  Klasa akcji, która określa, dodając nie przesyłaj dalej ochrony dokumentu.
[ProtectionDescriptor](class_mip_protectiondescriptor.md)  |  Opis ochrony skojarzony element zawartości.
[ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)  |  Konstruuje [ProtectionDescriptor](class_mip_protectiondescriptor.md) opisujący ochrony skojarzony element zawartości.
[ProtectionEngine::Observer](class_mip_protectionengine_observer.md)  |  Interfejs, który odbiera powiadomienia związane z [ProtectionEngine](class_mip_protectionengine.md).
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)  |  [Ustawienia](class_mip_protectionengine_settings.md) posługują się [ProtectionEngine](class_mip_protectionengine.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[ProtectionEngine](class_mip_protectionengine.md)  |  Zarządza związanych z ochroną akcje związane z określonej tożsamości.
[ProtectionHandler::Observer](class_mip_protectionhandler.md)  |  Interfejs, który odbiera powiadomienia związane z [ProtectionHandler](class_mip_protectionhandler.md).
[ProtectionHandler](class_mip_protectionhandler.md)  |  Zarządza związanych z ochroną akcje konfiguracji określonego ochrony.
[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)  |  Interfejs, który odbiera powiadomienia związane z [ProtectionProfile](class_mip_protectionprofile.md).
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)  |  [Ustawienia](class_mip_protectionprofile_settings.md) posługują się [ProtectionProfile](class_mip_protectionprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
[ProtectionProfile](class_mip_protectionprofile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md) jest klasą głównego do wykonywania operacji ochrony.
[RecommendLabelAction](class_mip_recommendlabelaction.md)  |  Zaleca się etykieta działania jest przeznaczona do zasugerować etykiet do użytkowników. Pominięcie tego wywołania po użytkownik ignoruje zalecana etykieta powinna być podejmowana za pośrednictwem obsługiwanych akcji dla stanu wykonywania.
[RemoveContentFooterAction](class_mip_removecontentfooteraction.md)  |  Klasa akcji, która określa usunięcie stopki zawartości z dokumentu.
[RemoveContentHeaderAction](class_mip_removecontentheaderaction.md)  |  Klasa akcji, która określa usunięcie nagłówka zawartości z dokumentu.
[RemoveProtectionAction](class_mip_removeprotectionaction.md)  |  Klasa akcji, która określa usunięcie ochrony z dokumentu.
[RemoveWatermarkAction](class_mip_removewatermarkaction.md)  |  Klasa akcji, która określa, usuwając znaki wodne z dokumentu.
[Stream](class_mip_stream.md)  |  Klasa, która definiuje interfejs między MIP zestaw SDK, na podstawie strumienia zawartości.
[TransientNetworkError](class_mip_transientnetworkerror.md)  |  Przejściowy błąd sieci. Przyczyną nieoczekiwane zachowanie podczas nawiązywania połączeń sieciowych do punktów końcowych usługi. Mogą być ponawiane operacji, ponieważ ten błąd jest przejściowy błąd.
[UserRights](class_mip_userrights.md)  |  Grupy użytkowników i praw skojarzonych z nimi.
[UserRoles](class_mip_userroles.md)  |  Grupa użytkowników i ról związanych z nimi.
