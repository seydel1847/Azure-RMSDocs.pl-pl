---
title: "Klasyfikowania plików i wiadomości e-mail przy użyciu usługi Azure Information Protection"
description: "Instrukcje dotyczące sposobu klasyfikowania dokumentów i wiadomości e-mail."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/02/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d65c7690-fab7-4823-845c-8c73903e9c79
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: cb8e7bab70ab6b135b7741a8f7ae6ba82b3585a7
ms.sourcegitcommit: 92bbef77091c66300e0d2acce60c064ffe314752
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2017
---
# <a name="user-guide-classify-a-file-or-email-by-using-azure-information-protection"></a>Podręcznik użytkownika: Klasyfikowania plików lub wiadomości e-mail przy użyciu usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

> [!NOTE]
> Użyj tych instrukcji, aby ułatwić klasyfikowania (ale nie chroni) dokumentów i wiadomości e-mail. Jeśli konieczne jest również ochrony dokumentów i wiadomości e-mail, zobacz [klasyfikować i chronić instrukcje](client-classify-protect.md). Jeśli nie masz pewności, zestaw instrukcji do użycia, skontaktuj się z administratorem lub pomocą techniczną.

Najprostszym sposobem klasyfikowania dokumentów i wiadomości e-mail jest podczas tworzenia lub je z edycji w aplikacji komputerowych pakietu Office: **Word**, **Excel**, **PowerPoint**,  **Outlook**. 

Jednakże można także sklasyfikować pliki za pomocą **Eksploratora plików**. Ta metoda obsługuje inne typy plików i jest wygodny sposób klasyfikować wielu plików jednocześnie. 

## <a name="using-office-apps-to-classify-your-documents-and-emails"></a>Do klasyfikowania dokumentów i wiadomości e-mail przy użyciu aplikacji pakietu Office

Za pomocą paska usługi Azure Information Protection wybierz jedną z etykiet, które zostały skonfigurowane dla Ciebie. 

Przykładowo na poniższej ilustracji przedstawiono, że dokument nie został jeszcze oznaczony etykietą, ponieważ parametr **Poufność** ma wartość **Nieustawiona**. Aby ustawić etykiety, takie jak "Ogólne", kliknij pozycję **ogólne**. Jeśli nie masz pewności, którą etykietę zastosować do bieżącego dokumentu lub wiadomości e-mail, użyj etykietki narzędzi, aby dowiedzieć się więcej o każdej etykiecie i właściwym jej zastosowaniu. 

![Przykład paska usługi Azure Information Protection](../media/info-protect-bar-not-set-callout.png)

Jeśli etykieta jest już zastosowana do dokumentu i chcesz ją zmienić, możesz wybrać inną etykietę. Jeśli na pasku nie są wyświetlane etykiety, kliknij najpierw ikonę **Edytuj etykietę** obok wartości bieżącej etykiety.

> [!TIP]
> Możesz też wybrać etykiety z **Chroń** przycisk na **pliku** kartę.

Oprócz ręcznego wybierania etykiet można je też ustawiać w następujący sposób:

- Administrator skonfigurował etykietę domyślną, którą można zachować lub zmienić.

- Administrator skonfigurował zalecane monity o wybór określonej etykiety po wykryciu poufnych danych. Możesz zaakceptować zalecenie (i etykieta zostanie dodana) lub je odrzucić (zalecana etykieta nie zostanie dodana).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Wyjątki dotyczące paska usługi Azure Information Protection 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Nie widzisz tego paska usługi Information Protection w aplikacjach pakietu Office?

- Nie masz klienta Azure Information Protection [zainstalowane](install-client-app.md).
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed-on-the-bar"></a>Czy etykieta, który powinna się pojawić na pasku, nie jest wyświetlana? 

- Jeśli administrator skonfigurował ostatnio nową etykietę, zamknij wszystkie wystąpienia aplikacji pakietu Office i otwórz ją ponownie. Ta akcja sprawdza zmiany etykiet.

- Etykieta może być objęta zasadami o określonym zakresie, które nie obejmują Twojego konta. Skontaktuj się z administratorem lub pomocą techniczną.


## <a name="using-file-explorer-to-classify-files"></a>Do klasyfikowania plików za pomocą Eksploratora plików

Korzystając z Eksploratora plików, można szybko klasyfikować jednego pliku, wielu plików lub folder. 

Po wybraniu folderu wszystkie pliki w tym folderze i wszelkich podfolderów, które ma zostaną zaznaczone automatycznie ustawionej klasyfikacji. Jednak nowych plików utworzonych w tym folderze lub jego podfolderach nie są automatycznie klasyfikowane.

Użyj Eksploratora plików do klasyfikowania plików, jeśli jeden lub więcej etykiet wyszarzone, wybranych plików nie obsługują bez chroni także klasyfikacji.

Przewodnik administratora zawiera pełną listę typów plików, które obsługują klasyfikacji bez ochrony: [typów obsługiwane wyłącznie do klasyfikowania plików](client-admin-guide-file-types.md#file-types-supported-for-classification-only).

### <a name="to-classify-a-file-by-using-file-explorer"></a>Do klasyfikowania plików za pomocą Eksploratora plików

1. W Eksploratorze plików wybierz plik, wiele plików lub folder. Kliknij prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**. Na przykład:
    
    ![Kliknięcie prawym przyciskiem myszy w oknie Eksploratora plików — klasyfikowanie i ochrona za pomocą usługi Azure Information Protection](../media/right-click-classify-protect-folder.png)

2. W **Klasyfikacja i ochrona — usługi Azure Information Protection** okno dialogowe, użyj etykiety jako możesz zrobić w aplikacji pakietu Office, który określa klasyfikacji zdefiniowanych przez administratora. 
    
    Jeśli żadna z tych etykiet można wybrać (wygaszone): wybrany plik nie obsługuje klasyfikacji. Na przykład:
    
    ![Brak dostępnych etykiet w oknie dialogowym Klasyfikacja i ochrona — Azure Information Protection**](../media/info-protect-dialog-labels-dimmed.png)

3. Jeśli wybrano plik, który nie obsługuje klasyfikacji, kliknij przycisk **Zamknij**. Ten plik nie można sklasyfikować bez również ochronę.
    
    W przypadku wybrania etykiety, kliknij przycisk **Zastosuj** i poczekaj, aż **Zakończono pracy** komunikat, aby zobaczyć wyniki. Następnie kliknij przycisk **Zamknij**.

Jeśli zmienisz zdanie o etykietę, którą wybrano po prostu Powtórz ten proces i wybierz inną etykietę.

Należy określić klasyfikację pozostanie z plikiem, nawet wtedy, gdy plik w wiadomościach e-mail lub zapisać go do innej lokalizacji. 
## <a name="other-instructions"></a>Inne instrukcje
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

- [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Dodatkowe informacje dla administratorów    
Zobacz [Konfigurowanie zasad usługi Azure Information Protection](../deploy-use/configure-policy.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
