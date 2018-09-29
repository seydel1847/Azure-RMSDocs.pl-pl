---
title: Klasa mip ProtectionProfile
description: Odwołanie do klasy mip ProtectionProfile
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a7dffb4a6b1490ef185eb9a5062f394f4509f00a
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446689"
---
# <a name="class-mipprotectionprofile"></a>Klasa mip::ProtectionProfile 
[ProtectionProfile](class_mip_protectionprofile.md) jest klasą głównego do wykonywania operacji ochrony.
Aplikacja musi utworzyć [ProtectionProfile](class_mip_protectionprofile.md) przed wykonaniem jakiejkolwiek operacji ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Pobiera ustawienia używane przez [ProtectionProfile](class_mip_protectionprofile.md) podczas jego inicjowania i w okresie swojego istnienia.
publiczne ListEnginesAsync void (const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się listy aparatów operacji.
publiczne std::vector < std::string > ListEngines()  |  Aparaty listy.
publiczne AddEngineAsync void (const ProtectionEngine::Settings & Ustawienia, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się dodanie nowego aparatu ochrony do profilu.
publiczne std::shared_ptr<ProtectionEngine> AddEngine (const ProtectionEngine::Settings & ustawień)  |  Dodaj nowy aparat ochrony, do profilu.
publiczne DeleteEngineAsync void (const std::string & engineId, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się usuwanie aparat ochrony o podanym identyfikatorze. Zostaną usunięte wszystkie dane dla danego aparatu.
 publiczne DeleteEngine void (const std::string & engineId)  |  Usuń aparat ochrony o podanym identyfikatorze. Zostaną usunięte wszystkie dane dla danego aparatu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Pobiera ustawienia używane przez [ProtectionProfile](class_mip_protectionprofile.md) podczas jego inicjowania i w okresie swojego istnienia.

  
**Zwraca**: [ustawienia](class_mip_protectionprofile_settings.md) posługują się [ProtectionProfile](class_mip_protectionprofile.md) podczas jego inicjowania i w okresie swojego istnienia
  
### <a name="listenginesasync"></a>ListEnginesAsync
Rozpoczyna się listy aparatów operacji.

Parametry:  
* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatorów


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="listengines"></a>ListEngines
Aparaty listy.

  
**Zwraca**: buforowanych identyfikatorów aparatu
  
### <a name="addengineasync"></a>AddEngineAsync
Rozpoczyna się dodanie nowego aparatu ochrony do profilu.

Parametry:  
* **ustawienia**: [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) obiekt, który określa ustawienia aparatu. 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatorów


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="protectionengine"></a>ProtectionEngine
Dodaj nowy aparat ochrony, do profilu.

Parametry:  
* **ustawienia**: [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) obiekt, który określa ustawienia aparatu.



  
**Zwraca**: nowo utworzony [ProtectionEngine](class_mip_protectionengine.md)
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Rozpoczyna się usuwanie aparat ochrony o podanym identyfikatorze. Zostaną usunięte wszystkie dane dla danego aparatu.

Parametry:  
* **Identyfikator**: aparat Unikatowy identyfikator. 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatorów


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="deleteengine"></a>DeleteEngine
Usuń aparat ochrony o podanym identyfikatorze. Zostaną usunięte wszystkie dane dla danego aparatu.

Parametry:  
* **Identyfikator**: aparat Unikatowy identyfikator.

