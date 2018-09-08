---
title: Sklasyfikować pliki i wiadomości e-mail przy użyciu usługi Azure Information Protection
description: Instrukcje dotyczące sposobu klasyfikowania dokumentów i wiadomości e-mail.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/31/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: d65c7690-fab7-4823-845c-8c73903e9c79
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: e49cd5da0c34c8dd6fa537bca3d90ba56c32e690
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44150232"
---
# <a name="user-guide-classify-a-file-or-email-by-using-azure-information-protection"></a>Podręcznik użytkownika: Klasyfikowanie pliku lub wiadomości e-mail przy użyciu usługi Azure Information Protection

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), system Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

> [!NOTE]
> Użyj tych instrukcji, aby ułatwić klasyfikowania (ale nie chroni) swoje dokumenty i wiadomości e-mail. Jeśli musisz również chronić swoje dokumenty i wiadomości e-mail, zobacz [klasyfikować i chronić instrukcje](client-classify-protect.md). Jeśli nie masz pewności, który zestaw instrukcje dotyczące korzystania z, skontaktuj się z administratorem lub pomocy technicznej.

To najprostszy sposób klasyfikowania dokumentów i wiadomości e-mail, podczas tworzenia lub edycji je w aplikacjach klasycznych pakietu Office: **Word**, **Excel**, **PowerPoint**,  **Program Outlook**. 

Jednakże można także sklasyfikować pliki przy użyciu **Eksploratora plików**. Ta metoda obsługuje dodatkowe typy plików i to wygodny sposób klasyfikowania wielu plików jednocześnie. 

## <a name="using-office-apps-to-classify-your-documents-and-emails"></a>Za pomocą aplikacji pakietu Office do klasyfikowania dokumentów i wiadomości e-mail

Za pomocą paska usługi Azure Information Protection wybierz jedną z etykiet, które zostały skonfigurowane dla Ciebie. 

Przykładowo na poniższej ilustracji przedstawiono, że dokument nie został jeszcze oznaczony etykietą, ponieważ parametr **Poufność** ma wartość **Nieustawiona**. Aby ustawić etykietę, np. "Ogólne", kliknij pozycję **ogólne**. Jeśli nie masz pewności, którą etykietę zastosować do bieżącego dokumentu lub wiadomości e-mail, użyj etykietki narzędzi, aby dowiedzieć się więcej o każdej etykiecie i właściwym jej zastosowaniu. 

![Przykład paska usługi Azure Information Protection](../media/info-protect-bar-not-set-callout.png)

Jeśli etykieta jest już zastosowana do dokumentu i chcesz ją zmienić, możesz wybrać inną etykietę. Jeśli na pasku nie są wyświetlane etykiety, kliknij najpierw ikonę **Edytuj etykietę** obok wartości bieżącej etykiety.

> [!TIP]
> Możesz również wybrać etykiety z **Chroń** przycisk na **pliku** kartę.

Oprócz ręcznego wybierania etykiet można je też ustawiać w następujący sposób:

- Administrator skonfigurował etykietę domyślną, którą można zachować lub zmienić.

- Administrator skonfigurował zalecane monity o wybór określonej etykiety po wykryciu poufnych danych. Możesz zaakceptować zalecenie (i etykieta zostanie dodana) lub je odrzucić (zalecana etykieta nie zostanie dodana).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Wyjątki dotyczące paska usługi Azure Information Protection 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Nie widzisz tego paska usługi Information Protection w aplikacjach pakietu Office?

- Nie masz klienta usługi Azure Information Protection [zainstalowane](install-client-app.md).

- Jest zainstalowany klient, ale administrator skonfigurował ustawienia, które nie jest wyświetlany pasek. Zamiast tego należy wybrać etykiety z **Chroń** przycisk na **pliku** karty na Wstążce pakietu Office. 

##### <a name="is-the-label-that-you-expect-to-see-not-displayed-on-the-bar"></a>Czy etykieta, który powinna się pojawić na pasku, nie jest wyświetlana? 

- Jeśli administrator skonfigurował ostatnio nową etykietę, zamknij wszystkie wystąpienia aplikacji pakietu Office i otwórz ją ponownie. Ta akcja sprawdza zmiany etykiet.

- Etykieta może być objęta zasadami o określonym zakresie, które nie obejmują Twojego konta. Skontaktuj się z administratorem lub pomocą techniczną.


## <a name="using-file-explorer-to-classify-files"></a>Za pomocą Eksploratora plików do klasyfikowania plików

Korzystając z Eksploratora plików, można szybko klasyfikować pojedynczy plik, wiele plików lub folderu. 

Po wybraniu folderu, wszystkie pliki w tym folderze i jego podfoldery zostaną zaznaczone automatycznie klasyfikacji, który został ustawiony. Jednak nowe pliki tworzone w tym folderze lub jego podfolderach nie są automatycznie klasyfikowane.

Podczas używania Eksploratora plików do klasyfikowania plików, jeśli jeden lub więcej etykiet są wyszarzone, wybrane pliki nie obsługują klasyfikacji bez również ich ochronie.

W podręczniku administratora podano pełną listę typów plików, które obsługują klasyfikacji bez ochrony: [typy plików obsługiwane wyłącznie do klasyfikowania](client-admin-guide-file-types.md#file-types-supported-for-classification-only).

### <a name="to-classify-a-file-by-using-file-explorer"></a>Do klasyfikowania plików za pomocą Eksploratora plików

1. W Eksploratorze plików wybierz plik, wiele plików lub folder. Kliknij prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**. Przykład:
    
    ![Kliknięcie prawym przyciskiem myszy w oknie Eksploratora plików — klasyfikowanie i ochrona za pomocą usługi Azure Information Protection](../media/right-click-classify-protect-folder.png)

2. W **Klasyfikuj i Chroń — Azure Information Protection** okno dialogowe, Użyj etykiet w sposób analogiczny jak w aplikacji pakietu Office, który ustawia klasyfikację, zgodnie z definicją przez administratora. 
    
    Jeśli nie można wybrać żadnego etykiety (są wyszarzone): wybrany plik nie obsługuje klasyfikacji. Przykład:
    
    ![Brak dostępnych etykiet w oknie dialogowym Klasyfikacja i ochrona — Azure Information Protection**](../media/info-protect-dialog-labels-dimmed.png)

3. Jeśli wybrano plik, który nie obsługuje klasyfikacji, kliknij przycisk **Zamknij**. Nie można sklasyfikować tego pliku, bez jednocześnie zagwarantować ochronę.
    
    Jeśli wybrano etykietę, kliknij przycisk **Zastosuj** i poczekaj na **ukończona praca** komunikat, aby zobaczyć wyniki. Następnie kliknij przycisk **Zamknij**.

Jeśli zmienisz zdanie na temat wybranej etykiety, po prostu Powtórz ten proces i wybrać inną etykietę.

Klasyfikacji, który określiłeś pozostanie z plikiem, nawet jeśli pliki w wiadomościach e-mail lub zapisany w innej lokalizacji. 
## <a name="other-instructions"></a>Inne instrukcje
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

- [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Dodatkowe informacje dla administratorów    
Zobacz [Konfigurowanie zasad usługi Azure Information Protection](../configure-policy.md).

