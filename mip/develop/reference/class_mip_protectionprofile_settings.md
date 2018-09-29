---
title: Klasa ustawień ProtectionProfile mipmapy
description: Dokumentacja dotycząca klasy ustawienia ProtectionProfile mipmapy
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: fe2413b2265cf4994dce0e57a7c472d59336902a
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446672"
---
# <a name="class-mipprotectionprofilesettings"></a>Klasa mip::ProtectionProfile::Settings 
[Ustawienia](class_mip_protectionprofile_settings.md) posługują się [ProtectionProfile](class_mip_protectionprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
Ustawienia publicznego (const std::string ś & cieżka, bool useInMemoryStorage std::shared_ptr const<AuthDelegate>& authDelegate, const std::shared_ptr<ConsentDelegate>& consentDelegate, const std::shared_ptr < ProtectionProfile::Observer > & obserwatora, const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) Konstruktor, który określa obserwatora ma być używany dla operacji asynchronicznej.
Ustawienia publicznego (const std::string ś & cieżka, bool useInMemoryStorage std::shared_ptr const<AuthDelegate>& authDelegate, const std::shared_ptr<ConsentDelegate>& consentDelegate, const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) używanego w przypadku operacji synchronicznych konstruktora.
 publiczne std::string const & GetPath() const  |  Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inne dodatkowe materiały ochrony są przechowywane.
 publiczne bool GetUseInMemoryStorage() const  |  Pobierz czy lub pamięci podręczne są przechowywane w pamięci tylko (a nie na dysku)
publiczne std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Pobiera metodę delegowaną uwierzytelniania, używane do uzyskiwania tokenów uwierzytelniania.
publiczne std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Pobiera metodę delegowaną zgody, używane do łączenia się z usługami.
publiczne std::shared_ptr < ProtectionProfile::Observer > GetObserver() const  |  Pobiera obserwatora, która odbiera powiadomienia zdarzeń związanych z [ProtectionProfile](class_mip_protectionprofile.md).
 publiczne ApplicationInfo const & GetApplicationInfo() const  |  Pobiera informacje o aplikacji, która zużywa ochrony zestawu SDK.
 publiczne OptOutTelemetry() void  |  Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
 publiczne bool IsTelemetryOptedOut() const  |  Pobiera Jeśli powinny być wyłączone zbieranie danych telemetrycznych, czy nie.
publiczne std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Uzyskaj delegata rejestratora (jeśli istnieje) udostępniany przez aplikację.
publiczne SetLoggerDelegate void (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Zastąp domyślną rejestratora.
publiczne std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  Uzyskaj delegata HTTP (jeśli istnieje) udostępniany przez aplikację.
publiczne SetHttpDelegate void (const std::shared_ptr<HttpDelegate>& httpDelegate)  |  Zastępują domyślne stos HTTP za pomocą własnego klienta.
 publiczne bool GetSkipTelemetryInit() const  |  Pobiera, jeśli ma być pomijana inicjowanie telemetrii, czy nie.
 publiczne SetSkipTelemetryInit() void  |  Wyłącza inicjowanie telemetrii.
 publiczne SetNewFeaturesDisabled() void  |  Wyłącza nowe funkcje.
 publiczne bool AreNewFeaturesDisabled() const  |  Pobiera, jeśli nowe funkcje są wyłączone lub nie.
 publiczne SetSessionId void (const std::string & sessionId)  |  Określa identyfikator sesji.
 publiczne std::string const & GetSessionId() const  |  Pobiera identyfikator sesji.
 publiczne SetMinimumLogLevel void (LogLevel logLevel)  |  Ustaw poziom minimalna dziennika, która wyzwoli rejestrowania zdarzeń.
 publiczne LogLevel GetMinimumLogLevel() const  |  Pobierz obiekt minimalny poziom dziennika.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) Konstruktor, który określa obserwatora ma być używany dla operacji asynchronicznej.

Parametry:  
* **ścieżka**: ścieżka pliku, w której rejestrowanie, dane telemetryczne i inne zabezpieczenia ochrony są przechowywane 


* **useInMemoryStorage**: Store dowolny stan pamięci podręcznej w pamięci, a nie na dysku 


* **authDelegate**: obiektu wywołania zwrotnego, które ma być używany do uwierzytelniania, implementowane przez aplikację kliencką 


* **Obserwator**: [obserwatora](class_mip_protectionprofile_observer.md) wystąpienia, który będzie otrzymywał powiadomienia o zdarzeniach związane z [ProtectionProfile](class_mip_protectionprofile.md)


* **applicationInfo**: informacje na temat aplikacji, która zużywa ochrony zestawu SDK


  
### <a name="settings"></a>Ustawienia
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) używanego w przypadku operacji synchronicznych konstruktora.

Parametry:  
* **ścieżka**: ścieżka pliku, w której rejestrowanie, dane telemetryczne i inne zabezpieczenia ochrony są przechowywane 


* **useInMemoryStorage**: Store dowolny stan pamięci podręcznej w pamięci, a nie na dysku 


* **authDelegate**: obiektu wywołania zwrotnego, które ma być używany do uwierzytelniania, implementowane przez aplikację kliencką 


* **applicationInfo**: informacje na temat aplikacji, która zużywa ochrony zestawu SDK


  
### <a name="getpath"></a>Funkcja GetPath
Pobiera ścieżkę, pod którym rejestrowania, telemetrii, oraz inne dodatkowe materiały ochrony są przechowywane.

  
**Zwraca**: ścieżka w ramach której rejestrowanie, dane telemetryczne i inne dodatkowe materiały ochrony są przechowywane
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Pobierz czy lub pamięci podręczne są przechowywane w pamięci tylko (a nie na dysku)

  
**Zwraca**: wartość True, jeśli pamięci podręczne są przechowywane wyłącznie w pamięci
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Pobiera metodę delegowaną uwierzytelniania, używane do uzyskiwania tokenów uwierzytelniania.

  
**Zwraca**: Delegowanie uwierzytelniania używany do uzyskiwania tokenów uwierzytelniania
  
### <a name="consentdelegate"></a>ConsentDelegate
Pobiera metodę delegowaną zgody, używane do łączenia się z usługami.

  
**Zwraca**: zgody delegata używany do łączenia się z usługami
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Pobiera obserwatora, która odbiera powiadomienia zdarzeń związanych z [ProtectionProfile](class_mip_protectionprofile.md).

  
**Zwraca**: [obserwatora](class_mip_protectionprofile_observer.md) , która otrzymuje powiadomienia o zdarzenia związane z [ProtectionProfile](class_mip_protectionprofile.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
Pobiera informacje o aplikacji, która zużywa ochrony zestawu SDK.

  
**Zwraca**: informacje na temat aplikacji, która zużywa ochrony zestawu SDK
  
### <a name="optouttelemetry"></a>OptOutTelemetry
Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Pobiera Jeśli powinny być wyłączone zbieranie danych telemetrycznych, czy nie.

  
**Zwraca**: Jeśli zbieranie danych telemetrycznych powinny być wyłączone lub nie
  
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
  
### <a name="setsessionid"></a>SetSessionId
Określa identyfikator sesji.

Parametry:  
* **Identyfikator sesji**: identyfikator sesji, która będzie służyć do skorelowania dzienników/telemetrii


  
### <a name="getsessionid"></a>GetSessionId
Pobiera identyfikator sesji.

  
**Zwraca**: identyfikator sesji, która będzie służyć do skorelowania dzienników/telemetrii
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
Ustaw poziom minimalna dziennika, która wyzwoli rejestrowania zdarzeń.

Parametry:  
* **logLevel**: minimalny poziom rejestrowania wyzwalające zdarzenia rejestrowania. 



  
**Zwraca**: True
  
### <a name="loglevel"></a>LogLevel
Pobierz obiekt minimalny poziom dziennika.

  
**Zwraca**: co najmniej poziom rejestrowania, który spowoduje wyzwolenie zdarzenia rejestrowania.