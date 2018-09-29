---
title: Klasa mip ProtectionHandler obserwatora
description: Odwołanie do klasy mip ProtectionHandler obserwatora
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 7fed286dec42f16d7dfa8e375ec739264bd365ba
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446187"
---
# <a name="class-mipprotectionhandlerobserver"></a>Klasa mip::ProtectionHandler::Observer 
Interfejs, który odbiera powiadomienia związane z [ProtectionHandler](class_mip_protectionhandler.md).
Ten interfejs muszą być zaimplementowane przez aplikacje przy użyciu zestawu SDK ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnCreateProtectionHandlerSuccess void (const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy [ProtectionHandler](class_mip_protectionhandler.md) został pomyślnie utworzony.
publiczne wirtualne OnCreateProtectionHandlerFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy [ProtectionHandler](class_mip_protectionhandler.md) tworzenie nie powiodło się.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="oncreateprotectionhandlersuccess"></a>OnCreateProtectionHandlerSuccess
Wywoływane, gdy [ProtectionHandler](class_mip_protectionhandler.md) został pomyślnie utworzony.

Parametry:  
* **protectionHandler**: nowo utworzony [ProtectionHandler](class_mip_protectionhandler.md)


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) lub [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)


Aplikację można przekazać dowolny typ kontekstu (na przykład std::promise, std::function) do [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) lub [ProtectionEngine:: CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync), a tym samym kontekście zostaną przekazane jako-ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess lub ProtectionEngine::Observer::O nCreateProtectionHandlerFailure
  
### <a name="oncreateprotectionhandlerfailure"></a>OnCreateProtectionHandlerFailure
Wywoływane, gdy [ProtectionHandler](class_mip_protectionhandler.md) tworzenie nie powiodło się.

Parametry:  
* **Błąd**: błąd, który wystąpił podczas tworzenia 


* **kontekst**: ten sam kontekst, który został przekazany do [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) lub [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)


Aplikację można przekazać dowolny typ kontekstu (na przykład std::promise, std::function) do [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) lub [ProtectionEngine:: CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync), a tym samym kontekście zostaną przekazane jako-ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess lub ProtectionEngine::Observer::O nCreateProtectionHandlerFailure