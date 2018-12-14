---
title: Usuwanie etykiet usługi Azure Information Protection
description: Instrukcje pozwalające usunąć etykiety klasyfikacji i ochrony z plików, które zostały oznaczone przez usługę Azure Information Protection lub objęte ochroną przez usługę Rights Management.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ''
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: ab98e211bf0f346359c6f6627a68db3071f7482e
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305084"
---
# <a name="user-guide-remove-labels-and-protection-from-files-and-emails-that-have-been-labeled-by-azure-information-protection-or-protected-by-rights-management"></a>Podręcznik użytkownika: Usuwanie etykiet klasyfikacji i ochrony z plików i wiadomości e-mail, które zostały oznaczone przez usługę Azure Information Protection lub objęte ochroną przez usługę Rights Management

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), system Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

Po [zainstalowaniu klienta usługi Azure Information Protection na komputerze](install-client-app.md) można usunąć etykiety klasyfikacji i ochrony z plików i wiadomości e-mail.

Jeśli etykieta, która ma zostać usunięta, jest skonfigurowana pod kątem zastosowania ochrony, wykonanie tej czynności spowoduje także wyłączenie ochrony pliku. Może zostać wyświetlony monit o podanie powodu usunięcia etykiety.

> [!IMPORTANT]
> Musisz być właścicielem pliku, aby usunąć ochronę, lub mieć przyznane uprawnienia do usuwania ochrony (Rights Management na to zgody **wyeksportować** lub **Pełna kontrola**).

Aby wybrać inną etykietę lub inny zbiór ustawień ochrony, nie musisz usuwać etykiety ani ochrony. Zamiast tego wybierz nową etykietę i w razie potrzeby można zdefiniować uprawnienia niestandardowe, jeśli administrator zezwala na tę konfigurację. 

Możesz usunąć etykiety i ochronę dokumentów pakietu Office i wiadomości e-mail podczas tworzenia lub edycji je w aplikacjach klasycznych pakietu Office: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Można także usuwać etykiety i ochronę, korzystając z **Eksploratora plików**, który obsługuje dodatkowe typy plików i zapewnia wygodny sposób usuwania etykiet i ochrony z wielu plików jednocześnie.

## <a name="using-office-apps-to-remove-labels-and-protection-from-documents-and-emails"></a>Usuwanie etykiet i ochrony dokumentów i wiadomości e-mail za pomocą aplikacji pakietu Office

Na pasku usługi Information Protection kliknij ikonę **Usuń etykietę**:

![Pasek usługi Azure Information Protection bar — Usuń etykietę](../media/delete-label.png)

Jeśli ikona **Usuń etykietę** nie jest od razu dostępna, kliknij najpierw ikonę **Edytuj etykietę**:

![Pasek usługi Azure Information Protection — Edytuj etykietę](../media/edit-label.png)

Jeśli nadal nie widzisz **Usuń etykietę** ikony, administrator nie zezwala na przy użyciu tej opcji.

> [!NOTE]
> Jeśli nie widzisz paska usługi Information Protection w aplikacjach pakietu Office:
>
> - Jeśli widzisz **Chroń** przycisk na Wstążce: Wybierz **Chroń**, a następnie wybierz pozycję **Pokaż pasek**.
> 
> - Być może nie został [zainstalowany](install-client-app.md) klient usługi Azure Information Protection lub klient jest uruchomiony w [trybie z samą ochroną](client-protection-only-mode.md).

## <a name="using-file-explorer-to-remove-labels-and-protection-from-files"></a>Usuwanie etykiet i ochrony plików przy użyciu Eksploratora plików

Korzystając z Eksploratora plików, można szybko usunąć etykiety i ochronę pojedynczego pliku, wielu plików lub folderu. Po wybraniu folderu automatycznie następuje wybór wszystkich plików znajdujących się w nim i jego podfolderach. 

1. W Eksploratorze plików wybierz plik, wiele plików lub folder. Kliknij prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**.

2. Aby usunąć etykietę: W **Klasyfikuj i Chroń — Azure Information Protection** okno dialogowe, kliknij przycisk **Usuń etykietę**. Jeśli etykieta została skonfigurowana pod kątem zastosowania ochrony, ochrona ta zostanie automatycznie usunięta.

3. Aby usunąć ochronę niestandardową z pojedynczego pliku: W **Klasyfikuj i Chroń — Azure Information Protection** okno dialogowe wyczyść **Chroń za pomocą uprawnień niestandardowych** opcji. 
    
    Jeśli nie widzisz **Chroń za pomocą uprawnień niestandardowych** opcji administrator nie zezwala na przy użyciu tej opcji.
    
4. Aby usunąć ochronę niestandardową z wielu plików: W **Klasyfikuj i Chroń — Azure Information Protection** okno dialogowe, kliknij przycisk **Usuń uprawnienia niestandardowe**.
    
    Jeśli nie widzisz **Usuń uprawnienia niestandardowe** opcji administrator nie zezwala na przy użyciu tej opcji.

5. Kliknij przycisk **Zastosuj** i poczekaj na pojawienie się komunikatu **Ukończona praca**, aby zobaczyć wyniki. Następnie kliknij przycisk **Zamknij**.


## <a name="other-instructions"></a>Inne instrukcje
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

- [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Dodatkowe informacje dla administratorów    
Aby uzyskać instrukcje dotyczące konfiguracji włączyć ustawienie zasad **Udostępnij opcję niestandardowych uprawnień użytkownikom**, zobacz [konfigurowania ustawień zasad usługi Azure Information Protection](../configure-policy-settings.md).

Inne instrukcje dotyczące konfiguracji: [Konfigurowanie zasad usługi Azure Information Protection](../configure-policy.md).

