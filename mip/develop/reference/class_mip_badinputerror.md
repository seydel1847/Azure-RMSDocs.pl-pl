---
title: Klasa mip BadInputError
description: Odwołanie do klasy mip BadInputError
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 1ee772499e55f413d8c7f4aa0d926cf2b579106d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446193"
---
# <a name="class-mipbadinputerror"></a>Klasa mip::BadInputError 
Zły błędów wejścia zgłaszany, gdy dane wejściowe do interfejsu API zestawu SDK są nieprawidłowe.
  
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

