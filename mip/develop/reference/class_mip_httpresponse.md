---
title: Klasa mip HttpResponse
description: Odwołanie do klasy mip HttpResponse
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a19ea78b048cafe94501d452bb9c7409237f6ffd
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445362"
---
# <a name="class-miphttpresponse"></a>Klasa mip::HttpResponse 
Interfejs, który opisuje jedną odpowiedź HTTP implementowane przez aplikację klienta, gdy zastępowanie [HttpDelegate](class_mip_httpdelegate.md).
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne int32_t GetStatusCode() const  |  Pobierz kod stanu odpowiedzi.
 publiczne std::string const & GetBody() const  |  Uzyskaj treści żądania.
publiczne std::map const < std::string, std::string, CaseInsensitiveComparator > & GetHeaders() const  |  Pobierz nagłówki żądania.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getstatuscode"></a>GetStatusCode
Pobierz kod stanu odpowiedzi.

  
**Zwraca**: kod stanu:
  
### <a name="getbody"></a>GetBody
Uzyskaj treści żądania.

  
**Zwraca**: treść żądania
  
### <a name="getheaders"></a>GetHeaders
Pobierz nagłówki żądania.

  
**Zwraca**: nagłówki żądania