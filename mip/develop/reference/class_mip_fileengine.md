---
title: Klasa mip FileEngine
description: Odwołanie do klasy mip FileEngine
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a7342edf27b19f43881b2e8d378fa243d26f7056
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446077"
---
# <a name="class-mipfileengine"></a>Klasa mip::FileEngine 
Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Zwraca ustawień aparatu.
publiczne std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Zwraca listę etykiety ważności.
 publiczne std::string const & GetMoreInfoUrl() const  |  Podaj adres url dla wyszukiwania więcej informacji na temat zasad/etykiety.
 publiczne bool IsLabelingRequired() const  |  Sprawdza, czy jeśli decyduje o zasady, muszą być oznaczone dokumentu.
publiczne CreateFileHandlerAsync void (const std::string & inputFilePath, const ContentState contentState, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się tworzenie obsługi plików dla podanej ścieżki pliku.
publiczne CreateFileHandlerAsync void (const std::shared_ptr<Stream>& inputStream, const std::string & inputFilePath, const mip::ContentState contentState, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się tworzenie obsługi plików dla danego pliku strumienia.
 publiczne SendApplicationAuditEvent void (const std::string & poziom, const std::string & Typ zdarzenia, const std::string & eventData)  |  Rejestruje zdarzenie określonych aplikacji potok inspekcji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Zwraca ustawień aparatu.
  
### <a name="label"></a>Etykieta
Zwraca listę etykiety ważności.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
Podaj adres url dla wyszukiwania więcej informacji na temat zasad/etykiety.

  
**Zwraca**: adres url w formacie ciągu.
  
### <a name="islabelingrequired"></a>IsLabelingRequired
Sprawdza, czy jeśli decyduje o zasady, muszą być oznaczone dokumentu.

  
**Zwraca**: wartość True, jeśli etykietowanie jest obowiązkowa, wartość false.
  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Rozpoczyna się tworzenie obsługi plików dla podanej ścieżki pliku.

Parametry:  
* Plik, aby otworzyć **.** Ścieżka musi zawierać nazwę pliku i, jeśli taki istnieje, rozszerzenie nazwy pliku. 


* **contentState**: stan zawartości, gdy aplikacja prowadzi interakcję z nią. 


* **A**: Implementacja klasy [FileHandler::Observer](class_mip_filehandler_observer.md) interfejsu. 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatora.


  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Rozpoczyna się tworzenie obsługi plików dla danego pliku strumienia.

Parametry:  
* **inputStream**: strumień zawierające dane plików. 


* **inputFilePath**: ścieżka do pliku. Ścieżka musi zawierać nazwę pliku i, jeśli taki istnieje, rozszerzenie nazwy pliku. 


* **contentState**: stan zawartości, gdy aplikacja prowadzi interakcję z nią. 


* **fileHandlerObserver**: Implementacja klasy [FileHandler::Observer](class_mip_filehandler_observer.md) interfejsu. 


* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatora.


  
### <a name="sendapplicationauditevent"></a>SendApplicationAuditEvent
Rejestruje zdarzenie określonych aplikacji potok inspekcji.

Parametry:  
* **poziom**: opis poziomu dziennika: Info/błąd/ostrzeżenie 


* **Typ zdarzenia**: opis typu zdarzenia 


* **eventData**: dane skojarzone ze zdarzeniem

