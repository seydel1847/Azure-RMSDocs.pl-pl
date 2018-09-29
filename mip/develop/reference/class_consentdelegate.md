---
title: Klasa ConsentDelegate
description: Dokumentacja dotycząca klasy ConsentDelegate
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 841049b1e6b369eb2f6a34d9701ed34eca028af6
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446366"
---
# <a name="class-consentdelegate"></a>Klasa ConsentDelegate 
Delegat o zgodę operacji związanych z.
Ten delegat jest implementowany przez aplikację kliencką, aby dowiedzieć się, kiedy powiadomienie żądanie zgody powinna być wyświetlana użytkownikowi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne GetUserConsent(const std::string& url) zgody  |  Wywołuje się, gdy zestaw SDK wymaga zgody użytkownika, aby nawiązać połączenie z punktu końcowego usługi.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="consent"></a>Wyrażenie zgody
Wywołuje się, gdy zestaw SDK wymaga zgody użytkownika, aby nawiązać połączenie z punktu końcowego usługi.

Parametry:  
* **adres URL**: adres URL, dla której zestaw SDK wymaga zgody użytkownika



  
**Zwraca**: wyliczenia zgody użytkownika decyzji.
Gdy zestaw SDK zażąda zgody użytkownika przy użyciu tej metody, aplikacja kliencka powinni przedstawić potwierdzenie odpowiedniego adresu URL dla użytkownika. Aplikacje klienckie należy podać kilka sposobów uzyskiwania zgody użytkownika i ponownie odpowiednie wyliczenia zgody, który odpowiada decyzja użytkownika.