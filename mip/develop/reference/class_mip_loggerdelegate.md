---
title: Klasa mip LoggerDelegate
description: Odwołanie do klasy mip LoggerDelegate
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: b25cdb177735feccfa5c4d344613e4747d18b77f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445856"
---
# <a name="class-miploggerdelegate"></a>Klasa mip::LoggerDelegate 
Klasa, która definiuje interfejs do rejestratora MIP SDK.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne Init void (const std::string & storagePath, LogLevel logLevel)  |  Inicjowanie rejestratora.
 publiczne LogLevel GetLogLevel() const  |  Uzyskaj najniższy evel logl, które będą wyzwalać zdarzenia rejestrowania.
 publiczne Flush() void  |  Usuń z rejestratora.
 publiczne WriteToLog void (const poziom LogLevel const std::string & wiadomości, const std::string & — funkcja, const std::string & pliku, const wiersza int32_t)  |  Napisz instrukcję dziennik do pliku dziennika.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="init"></a>Init
Inicjowanie rejestratora.

Parametry:  
* **storagePath**: ścieżka do lokalizacji, w których trwały stan, w tym dzienniki, mogą być przechowywane. 


* **logLevel**: najniższy poziom dziennika, które powinny wyzwalać zdarzenia rejestrowania.


  
### <a name="loglevel"></a>LogLevel
Uzyskaj najniższy evel logl, które będą wyzwalać zdarzenia rejestrowania.

  
**Zwraca**: najniższy poziom rejestrowania, który spowoduje to wyzwolenie zdarzenia rejestrowania.
  
### <a name="flush"></a>Flush
Usuń z rejestratora.
  
### <a name="writetolog"></a>WriteToLog
Napisz instrukcję dziennik do pliku dziennika.

Parametry:  
* **poziom**: poziom rejestrowania dla instrukcji dziennika. 


* **komunikat**: komunikat dla instrukcji dziennika. 


* **Funkcja**: Nazwa funkcji dla instrukcji dziennika. 


* **plik**: Nazwa pliku, w której instrukcję log został wygenerowany. 


* **wiersz**: numer wiersza, w którym został wygenerowany instrukcję log.

