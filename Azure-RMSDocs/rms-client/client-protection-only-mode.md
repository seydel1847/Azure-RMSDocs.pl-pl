---
title: "Usługa Azure Information Protection działająca w trybie z samą ochroną"
description: "Informacje dla użytkowników, którzy uruchamiają klienta usługi Azure Information Protection w trybie z samą ochroną."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/02/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: ea865f91751ed171779c587d1af4cb0f4226a59e
ms.sourcegitcommit: bc47834ae7180491ed1d9bc9f69eab398bcdc0a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2018
---
# <a name="user-guide-protection-only-mode-for-the-azure-information-protection-client"></a>Podręcznik użytkownika: Tryb tylko do ochrony dla klienta usługi Azure Information Protection

Gdy klient usługi Azure Information Protection nie ma etykiety do klasyfikowania dokumentów i wiadomości e-mail, jest uruchamiany w **tylko do ochrony** tryb. Na przykład, w tym trybie można napotkać następujące w Eksploratorze plików systemu Windows, kliknij prawym przyciskiem myszy, **Klasyfikuj i chronić**:

![Tryb z samą ochroną](../media/protection-only-mode.png)

Tryb tylko do ochrony jest uruchamiana w następujących scenariuszach:

- Twoja organizacja nie ma subskrypcji usługi Azure Information Protection, który zawiera klasyfikacji i etykietowania funkcje, ale ma subskrypcję usługi Office 365, która zawiera ochronę danych przy użyciu usługi Azure Rights Management. 
    
    - Klienta usługi Azure Information Protection umożliwia ochronę plików i wyświetlać chronione pliki. Nie można sklasyfikować lub etykieta dokumentów i wiadomości e-mail.

- Twoja organizacja ma subskrypcję usługi Azure Information Protection dla tylko podzestaw użytkowników:
    
    - W przypadku tej mieszanki subskrypcji jest Administratorze spoczywa odpowiedzialność za zapewnienie, że tylko podzestaw użytkowników można używać klasyfikacji i etykietowania funkcji. W pozostałej części użytkownicy powinna być uruchomiona w trybie tylko do ochrony klienta Azure Information Protection. 

- Organizacja ma subskrypcję usługi Azure Information Protection, ale nie jest możliwe pobranie zasad usługi Azure Information Protection. 
    
    - Może się to zdarzyć z powodu błędnej konfiguracji lub ponieważ logowanie nie powiodło się. Skontaktuj się z działem pomocy technicznej lub z administratorem. Jednocześnie możesz być w stanie korzystać z klienta usługi Azure Information Protection do ochrony plików oraz wyświetlania chronionych plików.

- Twoja organizacja korzysta z Active Directory Rights Management Services (AD RMS) tylko. 


## <a name="limitations-for-protection-only-mode"></a>Ograniczenia dotyczące trybu z samą ochroną

- W aplikacjach pakietu Office nie jest wyświetlany pasek usługi Azure Information Protection. Po kliknięciu pozycji **Chroń** > **Pokaż pasek** ta opcja jest niedostępna.

- Podczas korzystania z okna dialogowego **Klasyfikuj i chroń — Azure Information Protection** w Eksploratorze plików nie są widoczne etykiety klasyfikacji. Zamiast tego, podobnie jak na poprzedniej ilustracji, jest widoczna opcja wyboru szablonów usługi Rights Management (RMS). 

## <a name="supported-tasks-for-protection-only-mode"></a>Zadania obsługiwane w trybie z samą ochroną

- Włączenie lub wyłączenie ochrony dokumentów i wiadomości e-mail w aplikacjach pakietu Office za pomocą funkcji Zarządzanie prawami informacji (IRM) pakietu Office. Przykład: kliknij kolejno opcje **Plik** > **Informacje** > **Zabezpiecz dokument** > **Ogranicz dostęp**. Więcej informacji można znaleźć w [Korzystanie z ochrony informacji w usłudze Office 365 oraz w pakiecie Office 2016 lub Office 2013](../deploy-use/help-users.md).

- Włącz (lub wyłącz) ochronę plików za pomocą Eksploratora plików systemu Windows: kliknij prawym przyciskiem myszy plik, pliki lub folder i wybierz polecenie **Klasyfikuj i chroń**. Aby zastosować zabezpieczenia skonfigurowane przez administratora, w oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** kliknij pozycję **Wybierz szablon**, a następnie wskaż jeden z dostępnych szablonów.

- Wyświetlanie chronionych plików w Przeglądarce usługi Azure Information Protection.

- Dostęp do witryny śledzenia dokumentów z poziomu aplikacji pakietu Office. Uwaga: do śledzenia i odwoływania dokumentów z tej witryny jest wymagana ważna subskrypcja.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]  
