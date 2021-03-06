---
title: Klasa mip FileProfile obserwatora
description: Odwołanie do klasy mip FileProfile obserwatora
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 105380ef63f6533839190e4c9e3f3ee5379781f1
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446400"
---
# <a name="class-mipfileprofileobserver"></a>Klasa mip::FileProfile::Observer 
[Obserwator](class_mip_fileprofile_observer.md) interfejsu, aby klienci mogli otrzymywać powiadomienia dla profilu zdarzenia związane z.
Wszystkie błędy dziedziczyć [mip::Error](class_mip_error.md). Klient nie powinien wywoływać aparat Wstecz w wątku, który wywołuje obserwatora.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne wirtualne ~Observer()  | _Jeszcze nie udokumentowano._
publiczne wirtualne OnLoadSuccess void (const std::shared_ptr < mip::FileProfile > & profilu, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy profil został pomyślnie załadowany.
publiczne wirtualne OnLoadFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas ładowania profilu spowodowało błąd.
publiczne wirtualne OnListEnginesSuccess void (const std::vector < std::string > & engineIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.
publiczne wirtualne OnListEnginesFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy lista aparatów spowodowało błąd.
publiczne wirtualne OnUnloadEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy aparat został zwolniony.
publiczne wirtualne OnUnloadEngineFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy zwalnianie aparat spowodowało błąd.
publiczne wirtualne OnAddEngineSuccess void (const std::shared_ptr < mip::FileEngine > & aparatu, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy nowy aparat został pomyślnie dodany.
publiczne wirtualne OnAddEngineFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas dodawania nowego aparatu spowodowało błąd.
publiczne wirtualne OnDeleteEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy aparat został pomyślnie usunięty.
publiczne wirtualne OnDeleteEngineFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy usuwanie aparat spowodowało błąd.
 publiczne wirtualne OnPolicyChanged void (const std::string & engineId)  |  Wywołuje się, gdy zmieniono zasady dla aparatu o podanym identyfikatorze.
 Observer() chronionych  | _Jeszcze nie udokumentowano._
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="observer"></a>~ Obserwatora
_Jeszcze nie udokumentowano._

  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wywołuje się, gdy profil został pomyślnie załadowany.
  
### <a name="onloadfailure"></a>OnLoadFailure
Metoda wywoływana podczas ładowania profilu spowodowało błąd.
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.
  
### <a name="onlistenginesfailure"></a>OnListEnginesFailure
Wywołuje się, gdy lista aparatów spowodowało błąd.
  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Wywołuje się, gdy aparat został zwolniony.
  
### <a name="onunloadenginefailure"></a>OnUnloadEngineFailure
Wywołuje się, gdy zwalnianie aparat spowodowało błąd.
  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wywołuje się, gdy nowy aparat został pomyślnie dodany.
  
### <a name="onaddenginefailure"></a>OnAddEngineFailure
Metoda wywoływana podczas dodawania nowego aparatu spowodowało błąd.
  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wywołuje się, gdy aparat został pomyślnie usunięty.
  
### <a name="ondeleteenginefailure"></a>OnDeleteEngineFailure
Wywołuje się, gdy usuwanie aparat spowodowało błąd.
  
### <a name="onpolicychanged"></a>OnPolicyChanged
Wywołuje się, gdy zmieniono zasady dla aparatu o podanym identyfikatorze.
  
### <a name="observer"></a>Obserwator
_Jeszcze nie udokumentowano._
