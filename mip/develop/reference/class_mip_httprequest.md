---
title: mip klasy HttpRequest
description: Odwołanie do klasy mip HttpRequest
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e838eb247bc00d43da72db1de03304e89a1b1da5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445244"
---
# <a name="class-miphttprequest"></a>Klasa mip::HttpRequest 
Interfejs, który opisuje pojedynczego żądania HTTP.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne HttpRequestType GetRequestType() const  |  Pobierz typ żądania.
 publiczne std::string const & GetUrl() const  |  Adres url żądania GET.
 publiczne std::string const & GetBody() const  |  Uzyskaj treści żądania.
publiczne std::map const < std::string, std::string, CaseInsensitiveComparator > & GetHeaders() const  |  Pobierz nagłówki żądania.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="httprequesttype"></a>HttpRequestType
Pobierz typ żądania.

  
**Zwraca**: typ żądania
  
### <a name="geturl"></a>GetUrl
Adres url żądania GET.

  
**Zwraca**: adres url żądania
  
### <a name="getbody"></a>GetBody
Uzyskaj treści żądania.

  
**Zwraca**: treść żądania
  
### <a name="getheaders"></a>GetHeaders
Pobierz nagłówki żądania.

  
**Zwraca**: nagłówki żądania