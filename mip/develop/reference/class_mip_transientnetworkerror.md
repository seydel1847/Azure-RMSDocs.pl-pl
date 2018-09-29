---
title: Klasa mip TransientNetworkError
description: Odwołanie do klasy mip TransientNetworkError
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 33b0bdd6c04e506bb7852d9925c943558da52b5e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445365"
---
# <a name="class-miptransientnetworkerror"></a>Klasa mip::TransientNetworkError 
Przejściowy błąd sieci. Przyczyną nieoczekiwane zachowanie podczas nawiązywania połączeń sieciowych do punktów końcowych usługi. Mogą być ponawiane operacji, ponieważ ten błąd jest przejściowy błąd.
  
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

