---
title: Klasa mip PolicyProfile
description: Odwołanie do klasy mip PolicyProfile
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 387e28780cb0ef02d56050f534d4783fdebc286e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446960"
---
# <a name="class-mippolicyprofile"></a>Klasa mip::PolicyProfile 
[PolicyProfile](class_mip_policyprofile.md) klasy jest klasą głównego dla przy użyciu operacji Microsoft Information Protection. Typowa aplikacja będzie potrzebny tylko jeden [PolicyProfile](class_mip_policyprofile.md) , ale można utworzyć wiele profilów, jeśli to konieczne.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Pobierz ustawienia w profilu.
publiczne ListEnginesAsync void (const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się listy aparatów operacji.
publiczne UnloadEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się zwalnianie aparatu zasad o podanym identyfikatorze.
publiczne AddEngineAsync void (const PolicyEngine::Settings & Ustawienia, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się dodanie nowego aparatu zasad w profilu.
publiczne DeleteEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się usuwanie aparatu zasad o podanym identyfikatorze. Zostaną usunięte wszystkie dane dla danego profilu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Pobierz ustawienia w profilu.

  
**Zwraca**: ustawienia w profilu.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Rozpoczyna się listy aparatów operacji.

Parametry:  
* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Rozpoczyna się zwalnianie aparatu zasad o podanym identyfikatorze.

Parametry:  
* **Identyfikator**: aparat Unikatowy identyfikator. 


* **kontekst**: parametr, który będzie w sposób nieprzezroczysty przekazywany do funkcji obserwatora. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="addengineasync"></a>AddEngineAsync
Rozpoczyna się dodanie nowego aparatu zasad w profilu.

Parametry:  
* **ustawienia**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md) obiekt, który określa ustawienia aparatu. 


* **kontekst**: parametr, który ma być fowarded sposób nieprzezroczysty dla funkcji obserwatora. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Rozpoczyna się usuwanie aparatu zasad o podanym identyfikatorze. Zostaną usunięte wszystkie dane dla danego profilu.

Parametry:  
* **Identyfikator**: aparat Unikatowy identyfikator. 


* **kontekst**: parametr, który zostanie przekazany do funkcji obserwatora. 


[PolicyProfile::Observer](class_mip_policyprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.