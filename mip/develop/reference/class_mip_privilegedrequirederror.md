---
title: Klasa mip PrivilegedRequiredError
description: Odwołanie do klasy mip PrivilegedRequiredError
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e55228cb48ff779e271695d4f6461be115d05b2f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445754"
---
# <a name="class-mipprivilegedrequirederror"></a>Klasa mip::PrivilegedRequiredError 
Bieżąca etykieta zostało przypisane jako uprzywilejowaną operacją (odpowiednik operacji administratora), w związku z tym nie może zostać zastąpiony.
  
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

