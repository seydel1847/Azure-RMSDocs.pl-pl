---
title: Klasa ustawień FileProfile mipmapy
description: Dokumentacja dotycząca klasy ustawienia FileProfile mipmapy
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 4b79d8eb75a54a56f1b3e48645bdd5eec0afaa19
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446383"
---
# <a name="class-mipfileprofilesettings"></a>Klasa mip::FileProfile::Settings 
[Ustawienia](class_mip_fileprofile_settings.md) posługują się [FileProfile](class_mip_fileprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
Ustawienia publicznego (const std::shared_ptr std::string ś & cieżka, bool useInMemoryStorage<AuthDelegate> authDelegate, std::shared_ptr<ConsentDelegate> consentDelegate, std::shared_ptr<Observer> obserwatora, const ApplicationInfo & applicationInfo)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md) konstruktora.
 publiczne std::string const & GetPath() const  |  Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inny stan trwały są przechowywane.
 publiczne bool GetUseInMemoryStorage() const  |  Pobiera, jeśli wszystkie stany powinny być przechowywane w pamięci, (a nie na dysku)
publiczne std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Pobiera metodę delegowaną uwierzytelniania, używane do uzyskiwania tokenów uwierzytelniania.
publiczne std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Pobiera metodę delegowaną zgody, używany do zażądania zgody użytkownika łączenia się z usługami.
publiczne std::shared_ptr<Observer> GetObserver() const  |  Pobiera obserwatora, która odbiera powiadomienia zdarzeń związanych z [FileProfile](class_mip_fileprofile.md).
 publiczne const ApplicationInfo GetApplicationInfo() const  |  Pobiera informacje o aplikacji, która zużywa zestawu SDK.
 publiczne bool GetSkipTelemetryInit() const  |  Pobiera, jeśli ma być pomijana inicjowanie telemetrii, czy nie.
 publiczne SetSkipTelemetryInit() void  |  Wyłącza inicjowanie telemetrii.
 publiczne SetNewFeaturesDisabled() void  |  Wyłącza nowe funkcje.
 publiczne bool AreNewFeaturesDisabled() const  |  Pobiera, jeśli nowe funkcje są wyłączone lub nie.
publiczne std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Uzyskaj delegata rejestratora (jeśli istnieje) udostępniany przez aplikację.
publiczne SetLoggerDelegate void (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Zastąp domyślną rejestratora.
publiczne std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  Uzyskaj delegata HTTP (jeśli istnieje) udostępniany przez aplikację.
publiczne SetHttpDelegate void (const std::shared_ptr<HttpDelegate>& httpDelegate)  |  Zastępują domyślne stos HTTP za pomocą własnego klienta.
 publiczne OptOutTelemetry() void  |  Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
 publiczne bool IsTelemetryOptedOut() const  |  Pobiera Jeśli powinny być wyłączone zbieranie danych telemetrycznych, czy nie.
 publiczne SetSessionId void (const std::string & sessionId)  |  Określa identyfikator sesji.
 publiczne std::string const & GetSessionId() const  |  Pobiera identyfikator sesji.
 publiczne SetMinimumLogLevel void (LogLevel logLevel)  |  Ustaw najniższy poziom rejestrowania, który spowoduje wyzwolenie zdarzenia rejestrowania.
 publiczne LogLevel GetMinimumLogLevel() const  |  Uzyskaj najniższy poziom rejestrowania, który spowoduje wyzwolenie zdarzenia rejestrowania.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
[FileProfile::Settings](class_mip_fileprofile_settings.md) konstruktora.

Parametry:  
* **ścieżka**: ścieżka pliku, w której rejestrowanie, dane telemetryczne i inne są przechowywane trwały stan 


* **useInMemoryStorage**: wartość true, jeśli wszystkie stany powinny być przechowywane w pamięci, wartość false, jeśli stan mogą być buforowane na dysku 


* **authDelegate**: Delegowanie uwierzytelniania używany do uzyskiwania tokenów uwierzytelniania 


* **Obserwator**: [obserwatora](class_mip_fileprofile_observer.md) wystąpienia, który będzie otrzymywał powiadomienia o zdarzeniach związane z [FileProfile](class_mip_fileprofile.md)


* **applicationInfo**: informacje na temat aplikacji, która zużywa zestawu SDK


  
### <a name="getpath"></a>Funkcja GetPath
Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inny stan trwały są przechowywane.

  
**Zwraca**: ścieżka w ramach której rejestrowanie, dane telemetryczne i inne są przechowywane przez stan trwały
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Pobiera, jeśli wszystkie stany powinny być przechowywane w pamięci, (a nie na dysku)

  
**Zwraca**: Jeśli stan wszystkich powinny być przechowywane w pamięci, (a nie na dysku)
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Pobiera metodę delegowaną uwierzytelniania, używane do uzyskiwania tokenów uwierzytelniania.

  
**Zwraca**: Delegowanie uwierzytelniania używany do uzyskiwania tokenów uwierzytelniania
  
### <a name="consentdelegate"></a>ConsentDelegate
Pobiera metodę delegowaną zgody, używany do zażądania zgody użytkownika łączenia się z usługami.

  
**Zwraca**: zgody delegata używany do żądania zgoda użytkownika
  
### <a name="observer"></a>Obserwator
Pobiera obserwatora, która odbiera powiadomienia zdarzeń związanych z [FileProfile](class_mip_fileprofile.md).

  
**Zwraca**: [obserwatora](class_mip_fileprofile_observer.md) , która otrzymuje powiadomienia o zdarzenia związane z [FileProfile](class_mip_fileprofile.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
Pobiera informacje o aplikacji, która zużywa zestawu SDK.

  
**Zwraca**: informacje na temat aplikacji, która zużywa zestawu SDK
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Pobiera, jeśli ma być pomijana inicjowanie telemetrii, czy nie.

  
**Zwraca**: Jeśli inicjowanie telemetrii ma być pomijana, czy nie
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Wyłącza inicjowanie telemetrii.
Ta metoda nie jest zazwyczaj wywoływana przez aplikacje klienckie, zamiast jest on używany przez zestaw SDK pliku Aby uniknąć zduplikowanych inicjowania
  
### <a name="setnewfeaturesdisabled"></a>SetNewFeaturesDisabled
Wyłącza nowe funkcje.
W przypadku aplikacji, których nie chcesz wypróbowywać nowe funkcje
  
### <a name="arenewfeaturesdisabled"></a>AreNewFeaturesDisabled
Pobiera, jeśli nowe funkcje są wyłączone lub nie.

  
**Zwraca**: Jeśli nowe funkcje są wyłączone lub nie
  
### <a name="loggerdelegate"></a>LoggerDelegate
Uzyskaj delegata rejestratora (jeśli istnieje) udostępniany przez aplikację.

  
**Zwraca**: rejestratora
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
Zastąp domyślną rejestratora.

Parametry:  
* **loggerDelegate**: rejestrowanie interfejs wywołania zwrotnego implementowane przez aplikacje klienckie


Ta metoda powinna być wywoływana przez aplikacje klienckie, które używają zapewniali własną implementację rejestratora
  
### <a name="httpdelegate"></a>HttpDelegate
Uzyskaj delegata HTTP (jeśli istnieje) udostępniany przez aplikację.

  
**Zwraca**: HTTP delegować do użycia w przypadku operacji HTTP
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
Zastępują domyślne stos HTTP za pomocą własnego klienta.

Parametry:  
* **httpDelegate**: HTTP interfejs wywołania zwrotnego implementowane przez aplikację kliencką


  
### <a name="optouttelemetry"></a>OptOutTelemetry
Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Pobiera Jeśli powinny być wyłączone zbieranie danych telemetrycznych, czy nie.

  
**Zwraca**: Jeśli zbieranie danych telemetrycznych powinny być wyłączone lub nie
  
### <a name="setsessionid"></a>SetSessionId
Określa identyfikator sesji.

Parametry:  
* **Identyfikator sesji**: identyfikator sesji, która będzie służyć do skorelowania dzienników/telemetrii


  
### <a name="getsessionid"></a>GetSessionId
Pobiera identyfikator sesji.

  
**Zwraca**: identyfikator sesji, która będzie służyć do skorelowania dzienników/telemetrii
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
Ustaw najniższy poziom rejestrowania, który spowoduje wyzwolenie zdarzenia rejestrowania.

Parametry:  
* **logLevel**: najniższy poziom, która wyzwoli rejestrowania zdarzeń dziennika. 



  
**Zwraca**: True
  
### <a name="loglevel"></a>LogLevel
Uzyskaj najniższy poziom rejestrowania, który spowoduje wyzwolenie zdarzenia rejestrowania.

  
**Zwraca**: najniższy poziom rejestrowania, który spowoduje wyzwolenie zdarzenia rejestrowania.