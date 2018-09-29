---
title: Klasa mip ProtectionEngine
description: Odwołanie do klasy mip ProtectionEngine
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: ddc8cfd58acb2a80d024978084b625f3d3728c87
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446740"
---
# <a name="class-mipprotectionengine"></a>Klasa mip::ProtectionEngine 
Zarządza związanych z ochroną akcje związane z określonej tożsamości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Pobiera ustawienia aparatu.
publiczne GetTemplatesAsync void (const std::shared_ptr < ProtectionEngine::Observer > & obserwatora, const std::shared_ptr<void>& kontekstu)  |  Pobierz zbiór szablonów dostępnych dla użytkownika.
publiczne std::vector < std::string > GetTemplates (const std::shared_ptr<void>& kontekstu)  |  Pobierz zbiór szablonów dostępnych dla użytkownika.
publiczne GetRightsForLabelIdAsync void (const std::string & element documentId, const std::string & etykiety, const std::string & ownerEmail, const std::shared_ptr < ProtectionEngine::Observer > & obserwatora, const std::shared_ptr<void>& kontekstu)  |  Nawiązać połączenia z kolekcji są dostępne prawa użytkownika dla identyfikatora etykiety.
publiczne std::vector < std::string > GetRightsForLabelId (const std::string & element documentId const std::string & etykiety, const std::string & ownerEmail, const std::shared_ptr<void>& kontekstu)  |  Pobieranie kolekcji są dostępne prawa użytkownika dla etykiety.
publiczne GetGrantingLabelIdsAsync void (const std::shared_ptr < ProtectionEngine::Observer > & obserwatora, const std::shared_ptr<void>& kontekstu)  |  Pobierz kolekcję dostępnych identyfikatorów etykiet do użytkownika.
publiczne std::vector < std::string > GetGrantingLabelIds (const std::shared_ptr<void>& kontekstu)  |  Pobierz kolekcję dostępnych identyfikatorów etykiet do użytkownika.
publiczne CreateProtectionHandlerFromDescriptorAsync void (const std::shared_ptr<ProtectionDescriptor>& deskryptora const ProtectionHandlerCreationOptions opcje, const std::shared_ptr < ProtectionHandler::Observer > & obserwatora, Const std::shared_ptr<void>& kontekstu)  |  Tworzy program obsługi ochrony gdzie prawa/role są przypisywane do konkretnych użytkowników.
publiczne std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromDescriptor (const std::shared_ptr<ProtectionDescriptor>& deskryptora const ProtectionHandlerCreationOptions & Opcje, const std::shared_ptr<void>& kontekstu)  |  Tworzy program obsługi ochrony gdzie prawa/role są przypisywane do konkretnych użytkowników.
publiczne CreateProtectionHandlerFromPublishingLicenseAsync void (const std::vector < uint8_t > & serializedPublishingLicense, const ProtectionHandlerCreationOptions & Opcje, const std::shared_ptr < ProtectionHandler::Observer > & obserwatora, const std::shared_ptr<void>& kontekstu)  |  Tworzy program obsługi ochrony z serializowanej licencji publikowania.
publiczne std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromPublishingLicense (const std::vector < uint8_t > & serializedPublishingLicense, opcje, const std::shared_ptr&constProtectionHandlerCreationOptions<void>& kontekstu)  |  Tworzy program obsługi ochrony z serializowanej licencji publikowania.
publiczne CreateProtectionHandlerFromPublishingLicenseContextAsync void (const std::shared_ptr const PublishingLicenseContext & publishingLicenseContext, const ProtectionHandlerCreationOptions & opcji < ProtectionHandler::O bSerwer > & obserwatora, const std::shared_ptr<void>& kontekstu)  |  Tworzy program obsługi ochrony z kontekstu licencji publikowania.
publiczne std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromPublishingLicenseContext (const PublishingLicenseContext & publishingLicenseContext, const ProtectionHandlerCreationOptions & opcji const std::shared_ptr<void>& kontekstu)  |  Tworzy program obsługi ochrony z kontekstu licencji publikowania.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Pobiera ustawienia aparatu.

  
**Zwraca**: ustawienia aparatu
  
### <a name="gettemplatesasync"></a>GetTemplatesAsync
Pobierz zbiór szablonów dostępnych dla użytkownika.

Parametry:  
* **Obserwator**: Implementacja klasy [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) interfejsu 


* **kontekst**: kontekst klienta, który ma być sposób nieprzezroczysty przekazany do obserwatorów i opcjonalne [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="gettemplates"></a>GetTemplates
Pobierz zbiór szablonów dostępnych dla użytkownika.

Parametry:  
* **kontekst**: kontekst klienta, który zostanie sposób nieprzezroczysty przekazany do opcjonalne [HttpDelegate](class_mip_httpdelegate.md)



  
**Zwraca**: Lista identyfikatorów szablonów.
  
### <a name="getrightsforlabelidasync"></a>GetRightsForLabelIdAsync
Nawiązać połączenia z kolekcji są dostępne prawa użytkownika dla identyfikatora etykiety.

Parametry:  
* **Element documentId**: skojarzony identyfikator dokumentu metadanych dokumentu 


* **Identyfikator etykiety**: [etykiety](class_mip_label.md) identyfikator skojarzony z metadanymi dokumentu za pomocą którego utworzyć dokumentu 


* **ownerEmail**: właściciel dokumentu 


* **Obserwator**: Implementacja klasy [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) interfejsu 


* **kontekst**: ten sam kontekst zostaną przekazane do [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) lub [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)


  
### <a name="getrightsforlabelid"></a>GetRightsForLabelId
Pobieranie kolekcji są dostępne prawa użytkownika dla etykiety.

Parametry:  
* **Element documentId**: skojarzony identyfikator dokumentu metadanych dokumentu 


* **Identyfikator etykiety**: [etykiety](class_mip_label.md) identyfikator skojarzony z metadanymi dokumentu za pomocą którego utworzyć dokumentu 


* **ownerEmail**: właściciel dokumentu 


* **kontekst**: ten sam kontekst zostaną przekazane do opcjonalne [HttpDelegate](class_mip_httpdelegate.md)



  
**Zwraca**: listę praw
  
### <a name="getgrantinglabelidsasync"></a>GetGrantingLabelIdsAsync
Pobierz kolekcję dostępnych identyfikatorów etykiet do użytkownika.

Parametry:  
* **Obserwator**: Implementacja klasy [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) interfejsu 


* **kontekst**: ten sam kontekst zostaną przekazane do [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) lub ProtectionEngine::Observer::OnGrantingLabelIdsFailure


  
### <a name="getgrantinglabelids"></a>GetGrantingLabelIds
Pobierz kolekcję dostępnych identyfikatorów etykiet do użytkownika.

Parametry:  
* **kontekst**: ten sam kontekst zostaną przekazane do opcjonalne [HttpDelegate](class_mip_httpdelegate.md)



  
**Zwraca**: Lista identyfikatorów etykiet
  
### <a name="createprotectionhandlerfromdescriptorasync"></a>CreateProtectionHandlerFromDescriptorAsync
Tworzy program obsługi ochrony gdzie prawa/role są przypisywane do konkretnych użytkowników.

Parametry:  
* **Deskryptor**: A [ProtectionDescriptor](class_mip_protectiondescriptor.md) opisujący konfigurację ochrony 


* **opcje**: opcje tworzenia 


* **Obserwator**: Implementacja klasy [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interfejsu 


* **kontekst**: kontekst klienta, który ma być sposób nieprzezroczysty przekazany do obserwatorów i opcjonalne [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="protectionhandler"></a>ProtectionHandler
Tworzy program obsługi ochrony gdzie prawa/role są przypisywane do konkretnych użytkowników.

Parametry:  
* **Deskryptor**: A [ProtectionDescriptor](class_mip_protectiondescriptor.md) opisujący konfigurację ochrony 


* **opcje**: opcje tworzenia 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty na opcjonalny [HttpDelegate](class_mip_httpdelegate.md)



  
**Zwraca**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicenseasync"></a>CreateProtectionHandlerFromPublishingLicenseAsync
Tworzy program obsługi ochrony z serializowanej licencji publikowania.

Parametry:  
* **serializedPublishingLicense**: A serializowana licencja publikowania 


* **opcje**: opcje tworzenia 


* **Obserwator**: Implementacja klasy [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interfejsu 


* **kontekst**: kontekst klienta, który ma być sposób nieprzezroczysty przekazany do obserwatorów i opcjonalne [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="protectionhandler"></a>ProtectionHandler
Tworzy program obsługi ochrony z serializowanej licencji publikowania.

Parametry:  
* **serializedPublishingLicense**: A serializowana licencja publikowania 


* **opcje**: opcje tworzenia 


* **Obserwator**: Implementacja klasy [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interfejsu 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty na opcjonalny [HttpDelegate](class_mip_httpdelegate.md)



  
**Zwraca**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicensecontextasync"></a>CreateProtectionHandlerFromPublishingLicenseContextAsync
Tworzy program obsługi ochrony z kontekstu licencji publikowania.

Parametry:  
* **publishingLicenseContext**: wstępnie przetworzonego postaci serializowanej licencji publikowania 


* **opcje**: opcje tworzenia 


* **Obserwator**: Implementacja klasy [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interfejsu 


* **kontekst**: kontekst klienta, który ma być sposób nieprzezroczysty przekazany do obserwatorów i opcjonalne [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="protectionhandler"></a>ProtectionHandler
Tworzy program obsługi ochrony z kontekstu licencji publikowania.

Parametry:  
* **publishingLicenseContext**: wstępnie przetworzonego postaci serializowanej licencji publikowania 


* **opcje**: opcje tworzenia 


* **Obserwator**: Implementacja klasy [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interfejsu 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty na opcjonalny [HttpDelegate](class_mip_httpdelegate.md)



  
**Zwraca**: [ProtectionHandler](class_mip_protectionhandler.md)