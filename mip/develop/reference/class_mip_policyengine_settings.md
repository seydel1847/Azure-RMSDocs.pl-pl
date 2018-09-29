---
title: Klasa ustawień PolicyEngine mipmapy
description: Dokumentacja dotycząca klasy ustawienia PolicyEngine mipmapy
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6ac94d1e34615a0248dac85f28c55154b127574f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446349"
---
# <a name="class-mippolicyenginesettings"></a>Klasa mip::PolicyEngine::Settings 
Definiuje ustawienia skojarzone z [PolicyEngine](class_mip_policyengine.md).
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Ustawienia publicznego (const std::string & engineId, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  [PolicyEngine::Settings](class_mip_policyengine_settings.md) konstruktora do ładowania aparat istniejących.
 Ustawienia publicznego (const tożsamości i tożsamości, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  [PolicyEngine::Settings](class_mip_policyengine_settings.md) Konstruktor do tworzenia nowego aparatu.
 publiczne std::string const & GetEngineId() const  |  Pobierz identyfikator aparatu
 publiczne SetEngineId void (const std::string & identyfikator)  |  Ustaw identyfikator aparatu.
 Identyfikator publiczny const & GetIdentity() const  |  Pobierz obiekt tożsamości.
 publiczne SetIdentity void (const tożsamości i tożsamości)  |  Obiekt tożsamości zestawu.
 publiczne std::string const & GetClientData() const  |  Pobierz dane klienta w oknie Ustawienia.
 publiczne SetClientData void (const std::string & dane klienckie)  |  Ustaw parametry danych klienta.
 publiczne std::string const & GetLocale() const  |  Pobierz ustawienia regionalne w oknie Ustawienia.
publiczne SetCustomSettings void (const std::vector < std::pair < std::string, std::string >> & customSettings)  |  Ustaw ustawienia niestandardowe, używany dla funkcji uzyskania bramowego i testowania.
publiczne std::vector const < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Pobierz ustawienia niestandardowe, używany dla funkcji uzyskania bramowego i testowania.
 publiczne SetSessionId void (const std::string & sessionId)  |  Ustaw identyfikator sesji używany dla telemetrii klient jest zdefiniowany.
 publiczne std::string const & GetSessionId() const  |  Pobierz identyfikator sesji, unikatowy identyfikator.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
[PolicyEngine::Settings](class_mip_policyengine_settings.md) konstruktora do ładowania aparat istniejących.

Parametry:  
* **engineId**: ustaw ją na identyfikator unikatowy aparatu wygenerowany przez AddEngineAsync lub jeden własnym wygenerowany. Podczas ładowania aparat istniejących, należy ponownie użyć innego Identyfikatora zostanie utworzony nowy aparat. 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem, gdy zwolniony, można pobrać z załadowanych aparatu. 


* **Ustawienia regionalne**: aparat możliwych do zlokalizowania w danych wyjściowych, które będą dostępne w tych ustawień regionalnych.


  
### <a name="settings"></a>Ustawienia
[PolicyEngine::Settings](class_mip_policyengine_settings.md) Konstruktor do tworzenia nowego aparatu.

Parametry:  
* **tożsamość**: informacje o tożsamości użytkownika skojarzonego z nowego aparatu. 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem, gdy zwolniony, można pobrać z załadowanych aparatu. 


* **Ustawienia regionalne**: aparat możliwych do zlokalizowania w danych wyjściowych, które będą dostępne w tych ustawień regionalnych.


  
### <a name="getengineid"></a>GetEngineId
Pobierz identyfikator aparatu

  
**Zwraca**: unikatowy ciąg identyfikujący silnika.
  
### <a name="setengineid"></a>SetEngineId
Ustaw identyfikator aparatu.

Parametry:  
* **Identyfikator**: aparat identyfikatora.


  
### <a name="getidentity"></a>Żądanie GetIdentity
Pobierz obiekt tożsamości.

  
**Zwraca**: odwołanie do tożsamości w obiekcie ustawień. 
  
**Zobacz też**: mip::Identity
  
### <a name="setidentity"></a>SetIdentity
Obiekt tożsamości zestawu.

Parametry:  
* **tożsamość**: unikatową tożsamość użytkownika. 


  
**Zobacz też**: mip::Identity
  
### <a name="getclientdata"></a>GetClientData
Pobierz dane klienta w oknie Ustawienia.

  
**Zwraca**: ciągu danych określony przez klienta.
  
### <a name="setclientdata"></a>SetClientData
Ustaw parametry danych klienta.

Parametry:  
* **Dane klienckie**: określone dane przez użytkownika.


  
### <a name="getlocale"></a>GetLocale
Pobierz ustawienia regionalne w oknie Ustawienia.

  
**Zwraca**: ustawienia regionalne.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Ustaw ustawienia niestandardowe, używany dla funkcji uzyskania bramowego i testowania.

Parametry:  
* **customSettings**: Lista par nazwa/wartość.


  
### <a name="getcustomsettings"></a>GetCustomSettings
Pobierz ustawienia niestandardowe, używany dla funkcji uzyskania bramowego i testowania.

  
**Zwraca**: Lista par nazwa/wartość.
  
### <a name="setsessionid"></a>SetSessionId
Ustaw identyfikator sesji używany dla telemetrii klient jest zdefiniowany.

Parametry:  
* **Identyfikator sesji**: unikatowy ciąg, który nawiązuje połączenie zdarzenia telemetrii.


  
### <a name="getsessionid"></a>GetSessionId
Pobierz identyfikator sesji, unikatowy identyfikator.

  
**Zwraca**: identyfikator sesji.