---
title: Podsumowanie
description: Podsumowanie
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5af209d5a627263399c8c60f474495dcadab24a0
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446502"
---
# <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
**Wspólne** |
Wyliczenie zgody       |  Odpowiedź użytkownika zleconą zgody połączyć się z punktu końcowego usługi.
Struktura ApplicationInfo  |  Struktura, która zawiera informacje o określonych aplikacji.
**mipmapy** |
Wyliczenie ErrorType       | _Jeszcze nie udokumentowano._
Wyliczenie HttpRequestType       |  Typ żądania HTTP.
Wyliczenie LogLevel       |  Poziomy dziennika używane w całym zestawie SDK MIP.
Wyliczenie ProtectionHandlerCreationOptions       |  Flagi bitowe, które wymuszają zachowanie tworzenia dodatkowych zasad.
Wyliczenie ProtectionType       |  Opisuje, czy ochrona na podstawie szablonu lub ad-hoc (niestandardowy)
Wyliczenie ActionType       |  Typy różne akcje.
mip::PublishingLicenseContext — struktura | Zawiera szczegółowe informacje o licencji publikowania użyty do utworzenia programu obsługi ochrony.

  
## <a name="enumerations-common"></a>Wyliczenia (wspólna)
  
### <a name="consent"></a>Wyrażenie zgody
Reprezentuje użytkownika decyzji zgody, aby nawiązać połączenie z punktu końcowego usługi.

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
AcceptAlways            | Zgoda i pamiętać tej decyzji
Akceptuj            | Zgodę, tylko jeden raz
Odrzuć            | Nie zgadza się
  
## <a name="enumerations-mip"></a>Wyliczenia (mip)

### <a name="actiontype"></a>ActionType

Typy różne akcje.

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
ADD_CONTENT_FOOTER            | Dodaj stopkę zawartości do akcji typu dokumentu.
ADD_CONTENT_HEADER            | Dodaj nagłówek zawartości do akcji typu dokumentu.
ADD_WATERMARK            | Dodaj znacznik limitu górnego typem akcji całego dokumentu.
NIESTANDARDOWE            | Typ akcji niestandardowej zdefiniowane.
WYJUSTUJ DO            | Wyjustuj typ akcji.
METADANE            | Metadane zmienić typ akcji.
PROTECT_ADHOC            | Chroń według typu działania zasad ad hoc.
PROTECT_BY_TEMPLATE            | Chroń przez typ akcji szablonu.
PROTECT_DO_NOT_FORWARD            | Chroń przez nie przesyłaj dalej typ akcji.
REMOVE_CONTENT_FOOTER            | Usuń typ akcji stopki zawartości.
REMOVE_CONTENT_HEADER            | Usuń typ akcji nagłówka zawartości.
REMOVE_PROTECTION            | Usuń typ akcji ochrony.
REMOVE_WATERMARK            | Usuń znaki wodne typ akcji.
APPLY_LABEL            | Zastosuj etykietę typ akcji.
RECOMMEND_LABEL            | Zaleca się typ akcji etykietę.

NIESTANDARDOWA jest typ ogólny akcji. Każdy typ działania jest określoną akcję przy użyciu określone znaczenie.

Wartości obiektu ActionType można łączyć, używając następujących operatorów:

- I (&) operator [akcji](class_mip_action.md) (`operator &(ActionType a, ActionType b)`)
- (Xor) (^) lub logiczny operator [akcji](class_mip_action.md). (`operator ^(ActionType a, ActionType b)`)


### <a name="errortype"></a>ErrorType
 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
BAD_INPUT_ERROR            | Obiekt wywołujący przekazane nieprawidłowe dane wejściowe.
FILE_IO_ERROR            | Błąd We/Wy ogólne pliku.
NETWORK_ERROR            | Problemy z siecią ogólne; np. usługa jest nieosiągalny.
TRANSIENT_NETWORK_ERROR            | Przejściowe problemy z siecią; np. Zła brama.
INTERNAL_ERROR            | Nieoczekiwane błędy wewnętrzne. np. w protokole klient serwer (Odebrano nieoczekiwaną odpowiedź).
JUSTIFICATION_REQUIRED            | Do ukończenia działania pliku należy podać uzasadnienie.
NOT_SUPPORTED_OPERATION            | Żądana operacja nie jest jeszcze obsługiwana.
PRIVILEGED_REQUIRED            | Nie można zastąpić uprzywilejowanych etykiety, gdy nowa metoda etykiety jest standardowa.
ACCESS_DENIED            | Użytkownik nie można uzyskać dostępu do zawartości. np. Brak uprawnień zawartości odwołany itp.
CONSENT_DENIED            | Operacja, która wymaga zgody użytkownika nie uzyskał zgody.
  
### <a name="httprequesttype"></a>HttpRequestType
Typ żądania HTTP.

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
Pobranie            | POBIERZ
Wpis            | POST
  
### <a name="loglevel"></a>LogLevel

Poziomy dziennika używane w całym zestawie SDK MIP.

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
Śledzenia            | 
Informacje            | 
Ostrzeżenie            | 
Error            | 
Poziomy dziennika używane w całym zestawie sdk mip.
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions

Flagi bitowe, które wymuszają zachowanie tworzenia dodatkowych zasad.

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
Brak            | Brak
OfflineOnly            | Nie zezwalaj na operacje interfejsu użytkownika i sieci.
AllowAuditedExtraction            | Zawartość będzie można otworzyć w app protection SDK — nieobsługującą
PreferDeprecatedAlgorithms            | Użyj przestarzałe algorytmów kryptograficznych (ECB) dla zapewnienia zgodności


### <a name="protectiontype"></a>ProtectionType
Opisuje, czy ochrona na podstawie szablonu lub ad-hoc (niestandardowy)

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
TemplateBased            | Uchwyt został utworzony na podstawie szablonu
Niestandardowy            | Dojście zostało utworzone ad-hoc

  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions
Bitowy operator OR ProtectionHandlerCreationOptions.

Parametry:  
* **Left wartość** 

* **b**: kliknij prawym przyciskiem myszy wartość

### <a name="releaseallresources"></a>ReleaseAllResources
Zwolnij wszystkie zasoby (wątków itp.), przed zamknięciem.
W przypadku MIP dynamicznych bibliotek ładowanych z opóźnieniem przez aplikację, ta funkcja musi zostać wywołana przed uwzględnieniem jawne zwalnianie tych bibliotek MIP w celu uniknięcia zakleszczenia. Na przykład na win32, ta funkcja musi być wywoływana przed wszelkie wywołania jawnie zwalnianie bibliotek DLL MIP, za pośrednictwem FreeLibrary lub \__FUnloadDelayLoadedDLL2. Aplikacje, trzeba zwolnić odwołania do wszystkich obiektów MIP (np. profile, aparatów obsługi) przed wywołaniem tej funkcji.
  
**Zwraca**: bitowe lub parametrów
  
## <a name="structures"></a>Struktury

### <a name="applicationinfo"></a>ApplicationInfo 
Struktura, która zawiera informacje o określonych aplikacji.

 Pola                        | Opisy                                
--------------------------------|---------------------------------------------
 Identyfikator publiczny std::string aplikacji  |  Identyfikator aplikacji ustawione w portalu usługi Azure AD.
 applicationName std::string publiczne  |  Nazwa aplikacji
 applicationVersion std::string publiczne  |  Wersja używanej aplikacji
  
### <a name="mippublishinglicensecontext"></a>MIP::PublishingLicenseContext 
Zawiera szczegółowe informacje o licencji publikowania użyty do utworzenia programu obsługi ochrony.
  
 Pola                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne const licenseInfo std::vector < uint8_t >  | _Jeszcze nie udokumentowano._
publiczne const serializedPublishingLicense std::vector < uint8_t >  | _Jeszcze nie udokumentowano._
publiczne PublishingLicenseContext (const std::vector < uint8_t > & licenseInfo, const std::vector < uint8_t > & serializedPublishingLicense)  | _Jeszcze nie udokumentowano._
  
