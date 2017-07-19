---
title: "Usuwanie etykiet usługi Azure Information Protection"
description: "Instrukcje pozwalające usunąć etykiety klasyfikacji i ochrony z plików, które zostały oznaczone przez usługę Azure Information Protection lub objęte ochroną przez usługę Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: e6fe5edfeb165839260371942cbf59922853a342
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="remove-labels-and-protection-from-files-and-emails-that-have-been-labeled-by-azure-information-protection-or-protected-by-rights-management"></a>Usuwanie etykiet klasyfikacji i ochrony z plików i wiadomości e-mail, które zostały oznaczone przez usługę Azure Information Protection lub objęte ochroną przez usługę Rights Management

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

Po [zainstalowaniu klienta usługi Azure Information Protection na komputerze](install-client-app.md) można usunąć etykiety klasyfikacji i ochrony z plików i wiadomości e-mail.

Jeśli etykieta, która ma zostać usunięta, jest skonfigurowana pod kątem zastosowania ochrony, wykonanie tej czynności spowoduje także wyłączenie ochrony pliku. Może zostać wyświetlony monit o podanie powodu usunięcia etykiety.

> [!IMPORTANT]
> Aby móc usunąć ochronę, użytkownik musi być właścicielem pliku lub mieć przyznane uprawnienia do usuwania ochrony (wyodrębnione uprawnienia lub pełna kontrola w ramach usługi Rights Management).

Aby wybrać inną etykietę lub inny zbiór ustawień ochrony, nie musisz usuwać etykiety ani ochrony. Zamiast tego wybierz nową etykietę i w razie potrzeby zdefiniuj uprawnienia niestandardowe. 

Etykiety i ochronę dokumentów pakietu Office i wiadomości e-mail można usuwać podczas ich tworzenia lub edytowania, używając aplikacji klasycznych pakietu Office: **Word**, **Excel**, **PowerPoint** i **Outlook**. 

Można także usuwać etykiety i ochronę, korzystając z **Eksploratora plików**, który obsługuje dodatkowe typy plików i zapewnia wygodny sposób usuwania etykiet i ochrony z wielu plików jednocześnie.

## <a name="using-office-apps-to-remove-labels-and-protection-from-documents-and-emails"></a>Usuwanie etykiet i ochrony dokumentów i wiadomości e-mail za pomocą aplikacji pakietu Office

Na pasku usługi Information Protection kliknij ikonę **Usuń etykietę**:

![Pasek usługi Azure Information Protection bar — Usuń etykietę](../media/delete-label.png)

Jeśli ikona **Usuń etykietę** nie jest od razu dostępna, kliknij najpierw ikonę **Edytuj etykietę**:

![Pasek usługi Azure Information Protection — Edytuj etykietę](../media/edit-label.png)

> [!NOTE]
> Jeśli nie widzisz paska usługi Information Protection w aplikacjach pakietu Office:
> 
> - Być może nie został [zainstalowany](install-client-app.md) klient usługi Azure Information Protection lub klient jest uruchomiony w [trybie z samą ochroną](client-protection-only-mode.md).

## <a name="using-file-explorer-to-remove-labels-and-protection-from-files"></a>Usuwanie etykiet i ochrony plików przy użyciu Eksploratora plików

Korzystając z Eksploratora plików, można szybko usunąć etykiety i ochronę pojedynczego pliku, wielu plików lub folderu. Po wybraniu folderu automatycznie następuje wybór wszystkich plików znajdujących się w nim i jego podfolderach. 

1.  W Eksploratorze plików wybierz plik, wiele plików lub folder. Kliknij prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**.

2. Aby usunąć etykietę: w oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** kliknij opcję **Usuń etykietę**. Jeśli etykieta została skonfigurowana pod kątem zastosowania ochrony, ochrona ta zostanie automatycznie usunięta.

3. Aby usunąć ochronę niestandardową z pojedynczego pliku: w oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** usuń zaznaczenie pola **Ochrona przy użyciu uprawnień niestandardowych**.
    
4. Aby usunąć ochronę niestandardową z wielu plików: w oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** kliknij opcję **Usuń uprawnienia niestandardowe**.

5. Kliknij przycisk **Zastosuj** i poczekaj na pojawienie się komunikatu **Ukończona praca**, aby zobaczyć wyniki. Następnie kliknij przycisk **Zamknij**.


## <a name="other-instructions"></a>Inne instrukcje
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

- [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]