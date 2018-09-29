---
title: Klasa mip PolicyProfile obserwatora
description: Odwołanie do klasy mip PolicyProfile obserwatora
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5de2156f4906c14e4ebc1418df8acb092c089d7d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446973"
---
# <a name="class-mippolicyprofileobserver"></a>Klasa mip::PolicyProfile::Observer 
[Obserwator](class_mip_policyprofile_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomienia dla profilu zdarzenia związane z.
Wszystkie błędy dziedziczyć [mip::Error](class_mip_error.md). Klient nie powinien wywoływać aparat Wstecz w wątku, który wywołuje obserwatora.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnLoadSuccess void (const std::shared_ptr<PolicyProfile>& profil, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy profil został pomyślnie załadowany.
publiczne wirtualne OnLoadFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas ładowania profilu spowodowało błąd.
publiczne wirtualne OnListEnginesSuccess void (const std::vector < std::string > & engineIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.
publiczne wirtualne OnListEnginesFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy lista aparatów spowodowało błąd.
publiczne wirtualne OnUnloadEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy aparat został zwolniony.
publiczne wirtualne OnUnloadEngineFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy zwalnianie aparat spowodowało błąd.
publiczne wirtualne OnAddEngineSuccess void (const std::shared_ptr<PolicyEngine>& aparat, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy nowy aparat został pomyślnie dodany.
publiczne wirtualne OnAddEngineFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas dodawania nowego aparatu spowodowało błąd.
publiczne wirtualne OnDeleteEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy aparat został pomyślnie usunięty.
publiczne wirtualne OnDeleteEngineFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy usuwanie aparat spowodowało błąd.
 publiczne wirtualne OnPolicyChanged void (const std::string & engineId)  |  Wywołuje się, gdy zmieniono zasady dla aparatu o podanym identyfikatorze.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wywołuje się, gdy profil został pomyślnie załadowany.

Parametry:  
* **profil**: bieżący profil używany do uruchomienia operacji. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onloadfailure"></a>OnLoadFailure
Metoda wywoływana podczas ładowania profilu spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodował niepowodzenie operacji obciążenia. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.

Parametry:  
* **engineIds**: listę identyfikatorów aparat są dostępne. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onlistenginesfailure"></a>OnListEnginesFailure
Wywołuje się, gdy lista aparatów spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodował niepowodzenie operacji aparatu listy. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Wywołuje się, gdy aparat został zwolniony.

Parametry:  
* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onunloadenginefailure"></a>OnUnloadEngineFailure
Wywołuje się, gdy zwalnianie aparat spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodował niepowodzenie operacji aparatu zwolnienia. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wywołuje się, gdy nowy aparat został pomyślnie dodany.
  
### <a name="onaddenginefailure"></a>OnAddEngineFailure
Metoda wywoływana podczas dodawania nowego aparatu spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodował niepowodzenie operacji aparatu Dodaj. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wywołuje się, gdy aparat został pomyślnie usunięty.

Parametry:  
* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="ondeleteenginefailure"></a>OnDeleteEngineFailure
Wywołuje się, gdy usuwanie aparat spowodowało błąd.

Parametry:  
* **Błąd**: błąd, który spowodował niepowodzenie operacji aparatu delete. 


* **kontekst**: kontekst przekazywany, aby wykonać operację.


  
### <a name="onpolicychanged"></a>OnPolicyChanged
Wywołuje się, gdy zmieniono zasady dla aparatu o podanym identyfikatorze.

Parametry:  
* **engineId**: aparat 


Ładowanie nowych zasad należy wywołać AddEngineAsync ponownie, używając podane ID aparatu.