---
title: Klasa mip PolicyEngine
description: Odwołanie do klasy mip PolicyEngine
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 57dd325e9c00a3cb2a4056f7ef0b522efef5d0c4
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446043"
---
# <a name="class-mippolicyengine"></a>Klasa mip::PolicyEngine 
Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Aparat zasad [ustawienia](class_mip_policyengine_settings.md).
publiczne std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Lista etykiet czułości skojarzone z aparatu zasad.
 publiczne std::string const & GetMoreInfoUrl() const  |  Podaj adres url dla wyszukiwania więcej informacji na temat zasad/etykiety.
 publiczne bool IsLabelingRequired() const  |  Sprawdza, jeśli zasady mówią, że dokument muszą być oznaczone.
publiczne std::shared_ptr<Label> GetDefaultSensitivityLabel()  |  Pobierz domyślny etykieta poufności.
publiczne std::shared_ptr<PolicyHandler> CreatePolicyHandler (const std::string & contentIdentifier)  |  Utwórz procedurę obsługi zasad do wykonania funkcji związanych z zasady na stan wykonywania pliku.
 publiczne SendApplicationAuditEvent void (const std::string & poziom, const std::string & Typ zdarzenia, const std::string & eventData)  |  Rejestruje zdarzenie określonych aplikacji potok inspekcji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Aparat zasad [ustawienia](class_mip_policyengine_settings.md).

  
**Zwraca**: ustawienia aparatu zasad. 
  
**Zobacz też**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="label"></a>Etykieta
Lista etykiet czułości skojarzone z aparatu zasad.

  
**Zwraca**: Lista etykiety ważności.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
Podaj adres url dla wyszukiwania więcej informacji na temat zasad/etykiety.

  
**Zwraca**: adres url w formacie ciągu.
  
### <a name="islabelingrequired"></a>IsLabelingRequired
Sprawdza, jeśli zasady mówią, że dokument muszą być oznaczone.

  
**Zwraca**: wartość True, jeśli etykietowanie jest obowiązkowa, wartość false.
  
### <a name="label"></a>Etykieta
Pobierz domyślny etykieta poufności.

  
**Zwraca**: domyślne etykiety ważności, jeśli istnieje nullptr Jeśli nie ustawiono etykiety domyślnej.
  
### <a name="policyhandler"></a>PolicyHandler
Utwórz procedurę obsługi zasad do wykonania funkcji związanych z zasady na stan wykonywania pliku.

Parametry:  
* **contentIdentifier**: czytelny dla człowieka dentifier zawartości. przykład dla pliku: "C:\mip-sdk-for-cpp\files\audit.docx" [path] na przykład wiadomości e-mail: "RE: inspekcji design:user1@contoso.com" [podmiotu: nadawcy]



  
**Zwraca**: program obsługi zasad.
  
### <a name="sendapplicationauditevent"></a>SendApplicationAuditEvent
Rejestruje zdarzenie określonych aplikacji potok inspekcji.

Parametry:  
* **Opis**: poziom dziennika: Info/błąd/ostrzeżenie 


* **Typ zdarzenia**: opis typu zdarzenia 


* **eventData**: dane skojarzone ze zdarzeniem

