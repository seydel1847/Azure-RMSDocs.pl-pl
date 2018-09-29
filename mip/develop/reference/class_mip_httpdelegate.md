---
title: Klasa mip HttpDelegate
description: Odwołanie do klasy mip HttpDelegate
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3e55f9aff5a9ebd97731ec21e408a33f22905648
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445375"
---
# <a name="class-miphttpdelegate"></a>Klasa mip::HttpDelegate 
Interfejs dla zastępowanie obsługi protokołu HTTP.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::shared_ptr<HttpResponse> wysyłania (const std::shared_ptr<HttpRequest>& żądania, const std::shared_ptr<void>& kontekstu)  |  Wyślij żądanie HTTP.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="httpresponse"></a>HttpResponse
Wyślij żądanie HTTP.

Parametry:  
* **żądanie**: żądania HTTP 


* **kontekst**: ten sam kontekst nieprzezroczyste klienta, który został przekazany do interfejsu API, które spowodowały to żądanie HTTP



  
**Zwraca**: odpowiedź HTTP