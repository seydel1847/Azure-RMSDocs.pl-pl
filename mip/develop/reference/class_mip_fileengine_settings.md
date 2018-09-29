---
title: Klasa ustawień FileEngine mipmapy
description: Dokumentacja dotycząca klasy ustawienia FileEngine mipmapy
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 656ad1cf21a2d761dfb4c857b278b7421ee2b790
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446485"
---
# <a name="class-mipfileenginesettings"></a>Klasa mip::FileEngine::Settings 
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Ustawienia publicznego (const std::string & engineId, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  [FileEngine::Settings](class_mip_fileengine_settings.md) konstruktora do ładowania aparat istniejących.
 Ustawienia publicznego (const tożsamości i tożsamości, const std::string & dane klienckie, const std::string i ustawienia regionalne)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md) Konstruktor do tworzenia nowego aparatu.
 publiczne std::string const & GetEngineId() const  |  Zwraca identyfikator aparatu.
 Identyfikator publiczny const & GetIdentity() const  |  Zwraca aparatu tożsamości.
 publiczne SetIdentity void (const tożsamości i tożsamości)  |  Ustawia tożsamość aparatu.
 publiczne std::string const & GetClientData() const  |  Zwraca dane klienta aparatu.
 publiczne std::string const & GetLocale() const  |  Zwróć aparatu ustawień regionalnych.
publiczne SetCustomSettings void (const std::vector < std::pair < std::string, std::string >> & wartość)  |  Ustawia listę par nazw i wartości używane do testowania i eksperymentowania.
publiczne std::vector const < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Pobiera listę par nazw i wartości używane do testowania i eksperymentowania.
 publiczne SetSessionId void (const std::string & sessionId)  |  Ustawia aparat identyfikator sesji.
 publiczne std::string const & GetSessionId() const  |  Zwraca identyfikator aparatu sesji.
 publiczne SetProtectionCloudEndpointBaseUrl void (const std::string & protectionCloudEndpointBaseUrl)  |  Ustawia ochronę chmury punktu końcowego podstawowego adresu url, używany do określenia granic chmury.
 publiczne std::string const & GetProtectionCloudEndpointBaseUrl() const  |  Pobiera cloudEndpointBaseUrl.
 publiczne SetProtectionOnlyEngine void (const protectionOnly wartość logiczna)  |  Ustawia tylko wskaźnika aparat ochrony — Brak zasad/etykiety.
 publiczne bool const IsProtectionOnlyEngine() const  |  Zwróć tylko wskaźnika aparat ochrony — Brak zasad/etykiety.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
[FileEngine::Settings](class_mip_fileengine_settings.md) konstruktora do ładowania aparat istniejących.

Parametry:  
* **engineId**: Ustaw identyfikator unikatowy aparatu wygenerowany przez AddEngineAsync. 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem, gdy zwolniony, można pobrać z załadowanych aparatu. 


* **Ustawienia regionalne**: aparat możliwych do zlokalizowania w danych wyjściowych, które będą dostępne w tych ustawień regionalnych.


  
### <a name="settings"></a>Ustawienia
[FileProfile::Settings](class_mip_fileprofile_settings.md) Konstruktor do tworzenia nowego aparatu.

Parametry:  
* **tożsamość**: informacje o tożsamości użytkownika skojarzonego z nowego aparatu. 


* **Dane klienckie**: dane klienta można dostosować, które mogą być przechowywane z aparatem, gdy zwolniony, można pobrać z załadowanych aparatu. 


* **Ustawienia regionalne**: aparat możliwych do zlokalizowania w danych wyjściowych, które będą dostępne w tych ustawień regionalnych.


  
### <a name="getengineid"></a>GetEngineId
Zwraca identyfikator aparatu.
  
### <a name="getidentity"></a>Żądanie GetIdentity
Zwraca aparatu tożsamości.
  
### <a name="setidentity"></a>SetIdentity
Ustawia tożsamość aparatu.
  
### <a name="getclientdata"></a>GetClientData
Zwraca dane klienta aparatu.
  
### <a name="getlocale"></a>GetLocale
Zwróć aparatu ustawień regionalnych.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Ustawia listę par nazw i wartości używane do testowania i eksperymentowania.
  
### <a name="getcustomsettings"></a>GetCustomSettings
Pobiera listę par nazw i wartości używane do testowania i eksperymentowania.
  
### <a name="setsessionid"></a>SetSessionId
Ustawia aparat identyfikator sesji.
  
### <a name="getsessionid"></a>GetSessionId
Zwraca identyfikator aparatu sesji.
  
### <a name="setprotectioncloudendpointbaseurl"></a>SetProtectionCloudEndpointBaseUrl
Ustawia ochronę chmury punktu końcowego podstawowego adresu url, używany do określenia granic chmury.

Parametry:  
* **protectionCloudEndpointBaseUrl**: podstawowy adres url skojarzony z ochrony punktów końcowych


  
### <a name="getprotectioncloudendpointbaseurl"></a>GetProtectionCloudEndpointBaseUrl
Pobiera cloudEndpointBaseUrl.

  
**Zwraca**: podstawowy adres url skojarzony z ochrony punktów końcowych
  
### <a name="setprotectiononlyengine"></a>SetProtectionOnlyEngine
Ustawia tylko wskaźnika aparat ochrony — Brak zasad/etykiety.
  
### <a name="isprotectiononlyengine"></a>IsProtectionOnlyEngine
Zwróć tylko wskaźnika aparat ochrony — Brak zasad/etykiety.