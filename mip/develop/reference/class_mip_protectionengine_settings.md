---
title: Klasa ustawień ProtectionEngine mipmapy
description: Dokumentacja dotycząca klasy ustawienia ProtectionEngine mipmapy
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f61e86a87ecfea21bc9d02f4e55f3fbe663e9b80
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446706"
---
# <a name="class-mipprotectionenginesettings"></a>Klasa mip::ProtectionEngine::Settings 
[Ustawienia](class_mip_protectionengine_settings.md) posługują się [ProtectionEngine](class_mip_protectionengine.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Ustawienia publicznego (const tożsamości i tożsamości, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) Konstruktor do tworzenia nowego aparatu.
 Ustawienia publicznego (const std::string & engineId, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) konstruktora do ładowania aparat istniejących.
 publiczne std::string const & GetEngineId() const  |  Pobiera identyfikator aparatu.
 publiczne SetEngineId void (const std::string & engineId)  |  Ustawia identyfikator aparatu.
 Identyfikator publiczny const & GetIdentity() const  |  Pobiera użytkownika, którego tożsamość skojarzone z aparatem.
 publiczne SetIdentity void (const tożsamości i tożsamości)  |  Ustawia użytkownika, którego tożsamość skojarzone z aparatem.
 publiczne std::string const & GetClientData() const  |  Pobiera dane niestandardowe określony przez klienta.
 publiczne SetClientData void (const std::string & dane klienckie)  |  Ustawia dane niestandardowe określony przez klienta.
 publiczne std::string const & GetLocale() const  |  Pobiera ustawienia regionalne w aparacie, które będą zapisywane dane.
publiczne SetCustomSettings void (const std::vector < std::pair < std::string, std::string >> & wartość)  |  Zestawy par nazwa/wartość służy do testowania i eksperymentowania.
publiczne std::vector const < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Pobiera par nazwa/wartość służy do testowania i eksperymentowania.
 publiczne SetSessionId void (const std::string & sessionId)  |  Ustawia aparat identyfikator sesji, używane na potrzeby korelacji rejestrowania/danych telemetrycznych.
 publiczne std::string const & GetSessionId() const  |  Pobiera identyfikator aparatu sesji.
 publiczne SetCloudEndpointBaseUrl void (const std::string & cloudEndpointBaseUrl)  |  Opcjonalnie ustawia adres URL podstawowego punktu końcowego chmury.
 publiczne std::string const & GetCloudEndpointBaseUrl() const  |  Pobiera chmury podstawowy adres URL używany przez wszystkie żądania obsługi, jeśli określony.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md) Konstruktor do tworzenia nowego aparatu.

Parametry:  
* **tożsamość**: tożsamość, która zostanie skojarzona z [ProtectionEngine](class_mip_protectionengine.md)


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem, gdy zwolniony i mogą być pobierane z załadowanych aparatu. 


* **Ustawienia regionalne**: aparat danych wyjściowych, które będą dostępne w tych ustawień regionalnych.


  
### <a name="settings"></a>Ustawienia
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md) konstruktora do ładowania aparat istniejących.

Parametry:  
* **engineId**: Unikatowy identyfikator aparat, który zostanie załadowany 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem, gdy zwolniony i mogą być pobierane z załadowanych aparatu. 


* **Ustawienia regionalne**: aparat danych wyjściowych, które będą dostępne w tych ustawień regionalnych.


  
### <a name="getengineid"></a>GetEngineId
Pobiera identyfikator aparatu.

  
**Zwraca**: aparat identyfikator
  
### <a name="setengineid"></a>SetEngineId
Ustawia identyfikator aparatu.

Parametry:  
* **engineId**: aparat identyfikatora.


  
### <a name="getidentity"></a>Żądanie GetIdentity
Pobiera użytkownika, którego tożsamość skojarzone z aparatem.

  
**Zwraca**: tożsamość użytkownika skojarzonego z aparatem
  
### <a name="setidentity"></a>SetIdentity
Ustawia użytkownika, którego tożsamość skojarzone z aparatem.

Parametry:  
* **tożsamość**: tożsamość użytkownika skojarzonego z aparatem


  
### <a name="getclientdata"></a>GetClientData
Pobiera dane niestandardowe określony przez klienta.

  
**Zwraca**: dane niestandardowe określone przez klienta
  
### <a name="setclientdata"></a>SetClientData
Ustawia dane niestandardowe określony przez klienta.

Parametry:  
* **Niestandardowe**: dane określone przez klienta


  
### <a name="getlocale"></a>GetLocale
Pobiera ustawienia regionalne w aparacie, które będą zapisywane dane.

  
**Zwraca**: ustawienia regionalne w aparacie, które będą zapisywane dane
  
### <a name="setcustomsettings"></a>SetCustomSettings
Zestawy par nazwa/wartość służy do testowania i eksperymentowania.

Parametry:  
* **customSettings**: par nazw i wartości używane do testowania i eksperymentowania


  
### <a name="getcustomsettings"></a>GetCustomSettings
Pobiera par nazwa/wartość służy do testowania i eksperymentowania.

  
**Zwraca**: par nazw i wartości używane do testowania i eksperymentowania
  
### <a name="setsessionid"></a>SetSessionId
Ustawia aparat identyfikator sesji, używane na potrzeby korelacji rejestrowania/danych telemetrycznych.

Parametry:  
* **Identyfikator sesji**: aparat identyfikator sesji, używane na potrzeby korelacji rejestrowania/danych telemetrycznych


  
### <a name="getsessionid"></a>GetSessionId
Pobiera identyfikator aparatu sesji.

  
**Zwraca**: aparat identyfikator sesji
  
### <a name="setcloudendpointbaseurl"></a>SetCloudEndpointBaseUrl
Opcjonalnie ustawia adres URL podstawowego punktu końcowego chmury.

Parametry:  
* **cloudEndpointBaseUrl**: podstawowy adres URL używany przez wszystkie żądania usługi (na przykład "https://api.aadrm.com")


Jeśli podstawowy adres URL nie jest określony, będzie określana przez wyszukiwanie DNS domeny tożsamość aparatu.
  
### <a name="getcloudendpointbaseurl"></a>GetCloudEndpointBaseUrl
Pobiera chmury podstawowy adres URL używany przez wszystkie żądania obsługi, jeśli określony.

  
**Zwraca**: bazowy adres URL