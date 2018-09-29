---
title: Klasa mip błąd wewnętrzny
description: Odwołanie do klasy mip błąd wewnętrzny
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: fc0babd7cff6dae6d322ba4f49fe5330a73255e5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445601"
---
# <a name="class-mipinternalerror"></a>Klasa mip::InternalError 
Błąd wewnętrzny. Ten błąd jest zgłaszany, gdy zdarzy się coś nieoczekiwanego podczas wykonywania.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne char const * what() const  |  Komunikat o błędzie.
publiczne std::shared_ptr<Error> Clone() const  |  Klonuj ten błąd.
 publiczne wirtualne ErrorType GetErrorType() const  |  Pobierz typ błędu.
 publiczne wirtualne std::string const & GetErrorName() const  |  Pobierz nazwę błędu.
 publiczne wirtualne std::string const & GetMessage() const  |  Komunikat o błędzie.
 publiczne wirtualne SetMessage void (const std::string & msg)  |  Ustaw komunikat o błędzie.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="what"></a>Co to
Komunikat o błędzie.

  
**Zwraca**: komunikat o błędzie
  
### <a name="error"></a>Error
Klonuj ten błąd.

  
**Zwraca**: klonowania błędu.
  
### <a name="errortype"></a>ErrorType
Pobierz typ błędu.

  
**Zwraca**: typ błędu.
  
### <a name="geterrorname"></a>GetErrorName
Pobierz nazwę błędu.

  
**Zwraca**: nazwa błędu.
  
### <a name="getmessage"></a>GetMessage
Komunikat o błędzie.

  
**Zwraca**: komunikat o błędzie.
  
### <a name="setmessage"></a>SetMessage
Ustaw komunikat o błędzie.

Parametry:  
* **msg**: komunikat o błędzie.

