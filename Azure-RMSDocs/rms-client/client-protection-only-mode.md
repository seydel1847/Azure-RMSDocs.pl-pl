---
title: "Usługa Azure Information Protection działająca w trybie z samą ochroną"
description: "Informacje dla użytkowników, którzy uruchamiają klienta usługi Azure Information Protection w trybie z samą ochroną."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 55254496b23e49fe7e2dbd19721a824739004b21
ms.lasthandoff: 02/24/2017


---

# <a name="protection-only-mode-for-the-azure-information-protection-client"></a>Klient usługi Azure Information Protection działający w trybie z samą ochroną

Po uruchomieniu klienta usługi Azure Information Protection bez zasad usługi Azure Information Protection klient działa w trybie **tylko do ochrony**. Na przykład — kliknięcie prawym przyciskiem myszy opcji **Klasyfikuj i chroń** w Eksploratorze plików systemu Windows:

![Tryb z samą ochroną](../media/protection-only-mode.png)

 Ten tryb działa w następujących scenariuszach:

- Twoja organizacja nie ma subskrypcji usługi Azure Information Protection do klasyfikacji i ochrony danych, ale ma subskrypcję usługi Azure Rights Management do ochrony danych z usługi Office 365. 
    - Jest to obsługiwany scenariusz, w którym można użyć klienta usługi Azure Information Protection do ochrony plików oraz do wyświetlania chronionych plików.

- Organizacja ma subskrypcję usługi Azure Information Protection, ale nie jest możliwe pobranie zasad usługi Azure Information Protection. 
    - Powodem takiej sytuacji może być niewłaściwa konfiguracja lub nieudane logowanie. Skontaktuj się z działem pomocy technicznej lub z administratorem. Jednocześnie możesz być w stanie korzystać z klienta usługi Azure Information Protection do ochrony plików oraz wyświetlania chronionych plików.

## <a name="limitations-for-protection-only-mode"></a>Ograniczenia dotyczące trybu z samą ochroną

- W aplikacjach pakietu Office nie jest wyświetlany pasek usługi Azure Information Protection. Po kliknięciu pozycji **Chroń** > **Pokaż pasek** ta opcja jest niedostępna.

- Podczas korzystania z okna dialogowego **Klasyfikuj i chroń — Azure Information Protection** w Eksploratorze plików nie są widoczne etykiety klasyfikacji. Zamiast tego, podobnie jak na poprzedniej ilustracji, jest widoczna opcja wyboru szablonów usługi Rights Management (RMS). 

## <a name="supported-tasks-for-protection-only-mode"></a>Zadania obsługiwane w trybie z samą ochroną

- Włączenie lub wyłączenie ochrony dokumentów i wiadomości e-mail w aplikacjach pakietu Office za pomocą funkcji Zarządzanie prawami informacji (IRM) pakietu Office. Przykład: kliknij kolejno opcje **Plik** > **Informacje** > **Zabezpiecz dokument** > **Ogranicz dostęp**. Więcej informacji można znaleźć w [Korzystanie z ochrony informacji w usłudze Office 365 oraz w pakiecie Office 2016 lub Office 2013](../deploy-use/help-users.md).

- Włącz (lub wyłącz) ochronę plików za pomocą Eksploratora plików systemu Windows: kliknij prawym przyciskiem myszy plik, pliki lub folder i wybierz polecenie **Klasyfikuj i chroń**. Aby zastosować zabezpieczenia skonfigurowane przez administratora, w oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** kliknij pozycję **Wybierz szablon**, a następnie wskaż jeden z dostępnych szablonów.

- Wyświetlanie chronionych plików w Przeglądarce usługi Azure Information Protection.

- Dostęp do witryny śledzenia dokumentów z poziomu aplikacji pakietu Office. Uwaga: do śledzenia i odwoływania dokumentów z tej witryny jest wymagana ważna subskrypcja.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]  
