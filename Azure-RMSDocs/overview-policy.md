---
title: Omówienie zasad usługi Azure Information Protection
description: Dowiedz się, etykiety i ustawienia w zasadach usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/27/2018
ms.topic: conceptual
ms.service: information-protection
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 6483600d8ba74a29a54965010441fe10dc309d8e
ms.sourcegitcommit: b10df82d9f00b3f826bce38beb7b666ce3f56e84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/28/2018
ms.locfileid: "53814190"
---
# <a name="overview-of-the-azure-information-protection-policy"></a>Omówienie zasad usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Zasady usługi Azure Information Protection zawierają następujące elementy, które można skonfigurować:
    
- Etykiety, które są uwzględniane, umożliwiają administratorom i użytkownikom sklasyfikować (i ewentualnie chronić) dokumenty i wiadomości e-mail.

- Tytuł i etykietka narzędzia paska usługi Information Protection, które użytkownicy zobaczą w swoich aplikacjach pakietu Office.

- Opcja ustawienia etykiety domyślnej jako punktu wyjścia dla klasyfikowania dokumentów i wiadomości e-mail.

- Opcja wymuszenia klasyfikacji w momencie zapisywania dokumentów i wysyłania wiadomości e-mail przez użytkowników.

- Opcja monitowania użytkowników o podanie przyczyny wybrania etykiety, która ma niższą charakterystykę niż oryginalna.

- Opcja automatycznego określania etykiety wiadomości e-mail na podstawie jej załączników.

- Możliwość kontrolowania, czy pasek usługi Information Protection jest wyświetlany w aplikacjach pakietu Office.

- Możliwość kontrolowania, czy przycisk nie przesyłaj dalej jest wyświetlany w programie Outlook.

- Opcja umożliwia użytkownikowi określenie własnych uprawnień dla dokumentów.

- Opcja udostępniania linku do niestandardowej pomocy dla użytkowników.

Usługa Azure Information Protection obejmuje [domyślne zasady](configure-policy-default.md), które zawierają pięć głównych etykiet. Dwa z tych etykiet zawierają etykiet podrzędnych, aby zapewnić podkategorii, w razie. 

Po skonfigurowaniu etykiety dla etykiet podrzędnych użytkownicy nie mogą wybrać etykietę głównego, ale należy wybrać jedną z etykiet podrzędnych. W tym scenariuszu głównej etykiety jest obsługiwany jako kontener wyświetlania tylko nazwę i kolor.

Etykiety usługi Azure Information Protection może służyć dla pełnego zakresu danych, które organizacja zazwyczaj tworzy i przechowuje, od najniższej klasyfikacji danych osobowych do najwyższej klasyfikacji wysoce poufne dane. 

Możesz użyć domyślnych etykiet bez wprowadzania zmian, dostosować etykiety lub usunąć je, a także utworzyć nowe etykiety. Aby uzyskać pełne instrukcje, zobacz [Konfigurowanie zasad usługi Azure Information Protection](configure-policy.md).


## <a name="next-steps"></a>Następne kroki

Aby uzyskać przykłady sposobów dostosowania zasad usługi Azure Information Protection i zobaczyć efekty dla użytkowników, wypróbuj następujące samouczki:

- [Edytowanie zasad usługi Azure Information Protection i utworzyć nową etykietę i tworzenie nowej etykiety](infoprotect-quick-start-tutorial.md)

- [Konfigurowanie ustawień zasad usługi Azure Information Protection, które współpracują ze sobą](infoprotect-settings-tutorial.md)
