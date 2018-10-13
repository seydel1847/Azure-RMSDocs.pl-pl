---
title: Dodaj lub usuń etykiety do lub z zasad usługi Azure Information Protection
description: Dodaj lub usuń etykiety usługi Azure Information Protection do lub z zasad globalnych dla wszystkich użytkowników, czy do lub z zasady o określonym zakresie dla podzbioru użytkowników.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 0546cc11-67a5-4194-8c54-f3ac8ce9ebe1
ms.openlocfilehash: a5e5e50f5271476c3690280cbe026be9ada7ceb2
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49170345"
---
# <a name="add-or-remove-a-label-to-or-from-an-azure-information-protection-policy"></a>Dodaj lub usuń etykiety do lub z zasad usługi Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Po utworzeniu etykiety usługi Azure Information Protection, można można następnie dodać do zasad wymagających używania czemu będzie ona dostępna dla użytkowników. Jeśli etykieta jest dla wszystkich użytkowników, Dodaj etykietę do zasad globalnych. Jeśli etykieta dla podzbioru użytkowników, Dodaj etykietę do zasad o określonym zakresie. Obecnie etykietę można dodać do tylko jedne zasady. Aby dodać etykiety podrzędnej, jego Etykieta nadrzędna musi być w tych samych zasadach lub w ramach globalnych zasad.

Dla etykiet, które znajdują się już w zasadach możesz je usunąć z zasad. Ta akcja nie powoduje usunięcia etykiety. Pozostanie dostępna do użycia w inne zasady.

Jeśli nie utworzono jeszcze etykiety, zobacz [Tworzenie nowej etykiety dla usługi Azure Information Protection](configure-policy-new-label.md).

Jeśli musisz utworzyć zasady o określonym zakresie, stosuje się etykietę do podzbioru użytkowników, zobacz [do konfigurowania zasad usługi Azure Information Protection dla konkretnych użytkowników przy użyciu zasad o określonym zakresie](configure-policy-scope.md).

## <a name="to-add-or-remove-a-label-to-or-from-a-policy"></a>Aby dodać lub usunąć etykietę z zasad lub

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **zasady** opcji menu: na **usługi Azure Information Protection** - **zasady** bloku wybierz **Global** etykiety, aby dodać lub usunąć dotyczy wszystkich użytkowników.

    Jeśli etykieta, aby dodać lub usunąć ma zastosowanie do określonej podgrupy użytkowników, należy wybrać zasady o określonym zakresie.

3. Na **zasad** bloku wybierz **apletu Dodaj lub usuń etykiety**.

4. Na **zasad: Dodaj lub usuń etykiety** wyświetlony blok wszystkich etykiet za pomocą pola wyboru jest zaznaczone, jeśli są już zasady, a także nazwę zasad w **zasad** kolumny.
     
    Etykiet podrzędnych są wyświetlane jako wcięte. W zasadach o określonym zakresie jako czas niedostępności wyświetlane etykiety, które są dziedziczone z zasad globalnych.
    
    Wykonaj jedną lub więcej z następujących czynności, a następnie kliknij przycisk **OK**:
    
    - Aby dodać etykietę, zaznacz go, który dodaje wybrane pola wyboru.
    
    - Aby usunąć etykietę, wyczyść odpowiednie pole wyboru.
  
5. Kliknij przycisk **Zapisz**, aby zapisać zmiany.
   
    Zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma już opcji publikowania oddzielne.


## <a name="next-steps"></a>Kolejne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

