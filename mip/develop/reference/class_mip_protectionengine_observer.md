---
title: Klasa mip ProtectionEngine obserwatora
description: Odwołanie do klasy mip ProtectionEngine obserwatora
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 9999b450d614b4465f151f0b2df80892a83bc143
ms.sourcegitcommit: 4cd90fcf94ac6e2543d8be10e6e29e8218d5fd9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49651349"
---
# <a name="class-mipprotectionengineobserver"></a>Klasa mip::ProtectionEngine::Observer 
Interfejs, który odbiera powiadomienia związane z [ProtectionEngine](class_mip_protectionengine.md).
Ten interfejs muszą być zaimplementowane przez aplikacje przy użyciu zestawu SDK ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnGetTemplatesSuccess void (const std::shared_ptr < std::vector < std::string >> & templateIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy szablony zostały pomyślnie pobrane.
publiczne wirtualne OnGetTemplatesFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy pobieranie szablonów wygenerowany błąd.
publiczne wirtualne OnGetRightsForLabelIdSuccess void (const std::shared_ptr < std::vector < std::string >> & praw, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy uprawnienia zostały pomyślnie pobrane.
publiczne wirtualne OnGetRightsForLabelIdFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas pobierania uprawnień dla Identyfikatora etykiety dla użytkownika.
publiczne wirtualne OnGetGrantingLabelIdsSuccess void (const std::shared_ptr < std::vector < std::string >> & labelIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy identyfikatorach etykiety zostały pomyślnie pobrane.
publiczne wirtualne OnGetGrantingLabelIdsFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy trwa pobieranie identyfikatory etykiet dla użytkownika.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="ongettemplatessuccess"></a>OnGetTemplatesSuccess
Wywołuje się, gdy szablony zostały pomyślnie pobrane.

Parametry:  
* **templateIds**: pobrać odwołanie do listy szablonów 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)


Aplikację można przekazać dowolny typ kontekstu (na przykład std::promise, std::function) do [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::Observer::O nGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) lub [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)
  
### <a name="ongettemplatesfailure"></a>OnGetTemplatesFailure
Wywołuje się, gdy pobieranie szablonów wygenerowany błąd.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) który wystąpił podczas pobierania szablonów 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)


Aplikację można przekazać dowolny typ kontekstu (na przykład std::promise, std::function) do [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::Observer::O nGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) lub [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)
  
### <a name="ongetrightsforlabelidsuccess"></a>OnGetRightsForLabelIdSuccess
Wywołuje się, gdy uprawnienia zostały pomyślnie pobrane.

Parametry:  
* **prawa**: pobrać odwołanie do listy uprawnień 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync)


Aplikację można przekazać dowolny typ kontekstu (na przykład std::promise, std::function) do [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::O bserver::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) lub [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)
  
### <a name="ongetrightsforlabelidfailure"></a>OnGetRightsForLabelIdFailure
Metoda wywoływana podczas pobierania uprawnień dla Identyfikatora etykiety dla użytkownika.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) który wystąpił podczas pobierania uprawnień 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync)


Aplikację można przekazać dowolny typ kontekstu (na przykład std::promise, std::function) do [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::O bserver::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) lub [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)
  
### <a name="ongetgrantinglabelidssuccess"></a>OnGetGrantingLabelIdsSuccess
Wywołuje się, gdy identyfikatorach etykiety zostały pomyślnie pobrane.

Parametry:  
* **labelIds**: pobrać odwołanie do listy identyfikatory etykiet 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync)


Aplikację można przekazać dowolny typ kontekstu (na przykład std::promise, std::function) do [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::O bserver::OnGetGrantingLabelIdsSuccess](class_mip_protectionengine_observer.md#ongetgrantinglabelidssuccess) lub [ProtectionEngine::Observer::OnGetGrantingLabelIdsFailure](class_mip_protectionengine_observer.md#ongetgrantinglabelidsfailure)
  
### <a name="ongetgrantinglabelidsfailure"></a>OnGetGrantingLabelIdsFailure
Wywołuje się, gdy trwa pobieranie identyfikatory etykiet dla użytkownika.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) który wystąpił podczas pobierania identyfikatory etykiet 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync)


Aplikację można przekazać dowolny typ kontekstu (na przykład std::promise, std::function) do [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionEngine::O bserver::OnGetGrantingLabelIdsSuccess](class_mip_protectionengine_observer.md#ongetgrantinglabelidssuccess) lub [ProtectionEngine::Observer::OnGetGrantingLabelIdsFailure](class_mip_protectionengine_observer.md#ongetgrantinglabelidsfailure)
