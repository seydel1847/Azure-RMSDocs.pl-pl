---
title: Klasa ustawień PolicyProfile mipmapy
description: Dokumentacja dotycząca klasy ustawienia PolicyProfile mipmapy
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 07cbcbc022c02a43f751e1cf55b5b0efdfb816d1
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446979"
---
# <a name="class-mippolicyprofilesettings"></a>Klasa mip::PolicyProfile::Settings 
[Ustawienia](class_mip_policyprofile_settings.md) posługują się [PolicyProfile](class_mip_policyprofile.md) podczas jej tworzenia, jak i w okresie swojego istnienia.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
Ustawienia publicznego (const std::string ś & cieżka, bool useInMemoryStorage std::shared_ptr const<AuthDelegate>& authDelegate, const std::shared_ptr < PolicyProfile::Observer > & obserwatora, const ApplicationInfo & applicationInfo)  |  Interfejs do konfigurowania profilu.
 publiczne std::string const & GetPath() const  |  Pobierz ścieżkę do przechowywanego stanu.
 publiczne bool GetUseInMemoryStorage() const  |  Pobierz flagi użycia magazynu w pamięci.
publiczne std::shared_ptr const<AuthDelegate>& GetAuthDelegate() const  |  Uzyskaj delegowanie uwierzytelniania.
publiczne std::shared_ptr const < PolicyProfile::Observer > & GetObserver() const  |  Uzyskaj obserwatora zdarzeń.
 publiczne const ApplicationInfo GetApplicationInfo() const  |  Uzyskaj informacje o aplikacji.
publiczne std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Uzyskaj delegata rejestratora (jeśli istnieje) udostępniany przez aplikację.
publiczne SetLoggerDelegate void (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Zastąp domyślną rejestratora.
publiczne std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  Uzyskaj delegata HTTP (jeśli istnieje) udostępniany przez aplikację.
publiczne SetHttpDelegate void (const std::shared_ptr<HttpDelegate>& httpDelegate)  |  Zastępują domyślne stos HTTP za pomocą własnego klienta.
 publiczne OptOutTelemetry() void  |  Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
 publiczne bool IsTelemetryOptedOut() const  |  Pobiera Jeśli powinny być wyłączone zbieranie danych telemetrycznych, czy nie.
 publiczne SetMinimumLogLevel void (LogLevel logLevel)  |  Ustaw poziom minimalna dziennika, która wyzwoli rejestrowania zdarzeń.
 publiczne LogLevel GetMinimumLogLevel() const  |  Pobierz obiekt minimalny poziom dziennika.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Interfejs do konfigurowania profilu.

Parametry:  
* **ścieżka**: ścieżka do katalogu, w którym zestaw SDK będzie przechowywać stanu profilowania. 


* **useInMemoryStorage**: Store dowolny stan pamięci podręcznej w pamięci, a nie na dysku. 


* **authDelegate**: Delegowanie uwierzytelniania używany przez zestaw SDK do uzyskiwania tokenów uwierzytelniania. 


* **Obserwator**: Implementacja klasy [PolicyProfile::Observer](class_mip_policyprofile_observer.md) interfejsu. Może być nullptr. 


* **applicationInfo**: identyfikatory aplikacji używane dla dostępu do usługi.


  
### <a name="getpath"></a>Funkcja GetPath
Pobierz ścieżkę do przechowywanego stanu.

  
**Zwraca**: ścieżka do zapisanego stanu.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Pobierz flagi użycia magazynu w pamięci.

  
**Zwraca**: wartość True, jeśli użycia w pamięci jest ustawiony przeciwnym razie wartość false.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Uzyskaj delegowanie uwierzytelniania.

  
**Zwraca**: Delegowanie uwierzytelniania.
  
### <a name="policyprofileobserver"></a>PolicyProfile::Observer
Uzyskaj obserwatora zdarzeń.

  
**Zwraca**: obserwatora zdarzeń.
  
### <a name="applicationinfo"></a>ApplicationInfo
Uzyskaj informacje o aplikacji.

  
**Zwraca**: informacje o aplikacji.
  
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

  
**Zwraca**: delegata Http do użycia dla operacji HTTP
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
Zastępują domyślne stos HTTP za pomocą własnego klienta.

Parametry:  
* **httpDelegate**: Http interfejs wywołania zwrotnego implementowane przez aplikację kliencką


  
### <a name="optouttelemetry"></a>OptOutTelemetry
Oznacza brak zgody na wszystkie dane telemetryczne zbierania.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Pobiera Jeśli powinny być wyłączone zbieranie danych telemetrycznych, czy nie.

  
**Zwraca**: gromadzenie Iftelemetry powinny być wyłączone lub nie
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
Ustaw poziom minimalna dziennika, która wyzwoli rejestrowania zdarzeń.

Parametry:  
* **logLevel**: minimalny poziom rejestrowania wyzwalające zdarzenia rejestrowania. 



  
**Zwraca**: True
  
### <a name="loglevel"></a>LogLevel
Pobierz obiekt minimalny poziom dziennika.

  
**Zwraca**: co najmniej poziom rejestrowania, który spowoduje wyzwolenie zdarzenia rejestrowania.