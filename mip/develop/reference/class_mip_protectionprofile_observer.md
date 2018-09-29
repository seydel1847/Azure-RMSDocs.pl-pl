---
title: Klasa mip ProtectionProfile obserwatora
description: Odwołanie do klasy mip ProtectionProfile obserwatora
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3678e6c1e1659f28b2f1dcc36f61295a8d29393e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446434"
---
# <a name="class-mipprotectionprofileobserver"></a>Klasa mip::ProtectionProfile::Observer 
Interfejs, który odbiera powiadomienia związane z [ProtectionProfile](class_mip_protectionprofile.md).
Ten interfejs muszą być zaimplementowane przez aplikacje przy użyciu zestawu SDK ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnLoadSuccess void (const std::shared_ptr<ProtectionProfile>& profil, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy profil został pomyślnie załadowany.
publiczne wirtualne OnLoadFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas ładowania profilu spowodowało błąd.
publiczne wirtualne OnListEnginesSuccess void (const std::vector < std::string > & engineIds, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.
publiczne wirtualne OnListEnginesFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy lista aparatów zakończyło się błędem.
publiczne wirtualne OnAddEngineSuccess void (const std::shared_ptr<ProtectionEngine>& aparat, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy nowy aparat został pomyślnie dodany.
publiczne wirtualne OnAddEngineFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas dodawania nowego aparatu zakończyło się błędem.
publiczne wirtualne OnDeleteEngineSuccess void (const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy aparat został pomyślnie usunięty.
publiczne wirtualne OnDeleteEngineFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy usuwanie aparat zakończyło się błędem.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Wywołuje się, gdy profil został pomyślnie załadowany.

Parametry:  
* **profil**: odwołanie do nowo utworzonego [ProtectionProfile](class_mip_protectionprofile.md)


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync)


Aplikację można przekazać dowolny typ kontekstu (na przykład std::promise, std::function) do [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) lub [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)
  
### <a name="onloadfailure"></a>OnLoadFailure
Metoda wywoływana podczas ładowania profilu spowodowało błąd.

Parametry:  
* **Błąd**: [błąd](class_mip_error.md) który wystąpił podczas ładowania 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync)


Aplikację można przekazać dowolny typ kontekstu (na przykład std::promise, std::function) do [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync) i tym samym kontekście zostaną przekazane jako — jest [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) lub [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Wywołuje się, gdy listy aparatów został pomyślnie wygenerowany.

Parametry:  
* **engineIds**: listę identyfikatorów aparat są dostępne. 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync)


  
### <a name="onlistenginesfailure"></a>OnListEnginesFailure
Wywołuje się, gdy lista aparatów zakończyło się błędem.

Parametry:  
* **Błąd**: błąd, który spowodował niepowodzenie operacji aparatów listy. 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync)


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Wywołuje się, gdy nowy aparat został pomyślnie dodany.

Parametry:  
* **aparat**: nowo utworzony aparatu 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


  
### <a name="onaddenginefailure"></a>OnAddEngineFailure
Metoda wywoływana podczas dodawania nowego aparatu zakończyło się błędem.

Parametry:  
* **Błąd**: błąd, który spowodował niepowodzenie operacji aparatu Dodaj. 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Wywołuje się, gdy aparat został pomyślnie usunięty.

Parametry:  
* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync)


  
### <a name="ondeleteenginefailure"></a>OnDeleteEngineFailure
Wywołuje się, gdy usuwanie aparat zakończyło się błędem.

Parametry:  
* **Błąd**: błąd, który spowodował niepowodzenie operacji aparatu delete. 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync)

