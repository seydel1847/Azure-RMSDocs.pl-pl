---
title: Usługa Azure Information Protection działająca w trybie z samą ochroną
description: Informacje dla użytkowników, którzy uruchamiają klienta usługi Azure Information Protection w trybie z samą ochroną.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/14/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: d55ef8caa7540cba2cd783613f5ea373ba1d545c
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39372397"
---
# <a name="user-guide-protection-only-mode-for-the-azure-information-protection-client"></a>Przewodnik po użytkownik: Tryb z samą ochroną dla klienta usługi Azure Information Protection

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), system Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*


Gdy klient usługi Azure Information Protection nie zawiera etykiet do klasyfikowania dokumentów i wiadomości e-mail, jest ono wykonywane **obejmujący tylko ochronę** trybu. Na przykład, w tym trybie można napotkać następujące podczas używania Eksploratora plików Windows, kliknij prawym przyciskiem myszy, **Klasyfikuj i Chroń**:

![Tryb z samą ochroną](../media/protection-only-mode.png)

Tryb z samą ochroną uruchamia się w następujących scenariuszach:

- Twoja organizacja ma subskrypcję usługi Azure Information Protection, który zawiera klasyfikacji i etykietowania funkcji, ale ma subskrypcję usługi Office 365, która obejmuje ochronę danych przy użyciu usługi Azure Rights Management. 
    
    - Klient usługi Azure Information Protection umożliwia ochronę plików oraz wyświetlania chronionych plików. Nie można sklasyfikować lub etykietowania dokumentów i wiadomości e-mail.

- Twoja organizacja ma subskrypcję usługi Azure Information Protection dla tylko podzbioru użytkowników:
    
    - Ta kombinacja subskrypcji jest Administratorze spoczywa odpowiedzialność za upewnij się, że tylko podzbioru użytkowników można użyć klasyfikacji i etykietowania funkcji. W pozostałej części użytkowników powinna być uruchomiona w trybie z samą ochroną klienta usługi Azure Information Protection. 

- Twoja organizacja ma subskrypcję usługi Azure Information Protection, ale nie masz żadnych etykiety skonfigurowane.
    
    - Może to nastąpić, gdy wszystkie etykiety globalne zasady są wyłączone, a Twoje konto nie jest dodawany do zasad o określonym zakresie. To może być spowodowane przez dział IT właśnie rozpoczęła się do wdrożenia usługi Azure Information Protection, ale jeszcze nie został udostępniony etykiet do klasyfikowania dokumentów i wiadomości e-mail. W międzyczasie można użyć klienta usługi Azure Information Protection do ochrony plików oraz wyświetlania chronionych plików.

- Organizacja ma subskrypcję usługi Azure Information Protection, ale nie jest możliwe pobranie zasad usługi Azure Information Protection. 
    
    - Taka sytuacja może wystąpić z powodu błędnej konfiguracji lub ponieważ logowanie zakończy się niepowodzeniem. Skontaktuj się z działem pomocy technicznej lub z administratorem. Jednocześnie możesz być w stanie korzystać z klienta usługi Azure Information Protection do ochrony plików oraz wyświetlania chronionych plików.

- Twoja organizacja korzysta z Active Directory Rights Management Services (AD RMS) tylko. 


## <a name="limitations-for-protection-only-mode"></a>Ograniczenia dotyczące trybu z samą ochroną

- W aplikacjach pakietu Office nie jest wyświetlany pasek usługi Azure Information Protection. Po kliknięciu pozycji **Chroń** > **Pokaż pasek** ta opcja jest niedostępna.

- Podczas korzystania z okna dialogowego **Klasyfikuj i chroń — Azure Information Protection** w Eksploratorze plików nie są widoczne etykiety klasyfikacji. Zamiast tego, podobnie jak na poprzedniej ilustracji, jest widoczna opcja wyboru szablonów usługi Rights Management (RMS). 

## <a name="supported-tasks-for-protection-only-mode"></a>Zadania obsługiwane w trybie z samą ochroną

- Włączenie lub wyłączenie ochrony dokumentów i wiadomości e-mail w aplikacjach pakietu Office za pomocą funkcji Zarządzanie prawami informacji (IRM) pakietu Office. Przykład: kliknij kolejno opcje **Plik** > **Informacje** > **Zabezpiecz dokument** > **Ogranicz dostęp**. Więcej informacji można znaleźć w [Korzystanie z ochrony informacji w usłudze Office 365 oraz w pakiecie Office 2016 lub Office 2013](../deploy-use/help-users.md).

- Włącz (lub wyłącz) ochronę plików za pomocą Eksploratora plików systemu Windows: kliknij prawym przyciskiem myszy plik, pliki lub folder i wybierz polecenie **Klasyfikuj i chroń**. Aby zastosować zabezpieczenia skonfigurowane przez administratora, w oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** kliknij pozycję **Wybierz szablon**, a następnie wskaż jeden z dostępnych szablonów.

- Wyświetlanie chronionych plików w Przeglądarce usługi Azure Information Protection.

- Dostęp do witryny śledzenia dokumentów z poziomu aplikacji pakietu Office. Uwaga: do śledzenia i odwoływania dokumentów z tej witryny jest wymagana ważna subskrypcja.
  
