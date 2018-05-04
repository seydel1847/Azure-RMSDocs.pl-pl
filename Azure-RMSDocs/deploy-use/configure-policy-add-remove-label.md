---
title: Dodaj lub Usuń etykietę do lub z zasad usługi Azure Information Protection
description: Dodaj lub Usuń etykietę usługi Azure Information Protection do lub z globalne zasady dla wszystkich użytkowników lub do lub z zakresu zasad dla podzbioru użytkowników.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0546cc11-67a5-4194-8c54-f3ac8ce9ebe1
ms.openlocfilehash: ad74efff44738c5475e988d861fda8d93686e794
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="add-or-remove-a-label-to-or-from-an-azure-information-protection-policy"></a>Dodaj lub Usuń etykietę do lub z zasad usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Po utworzeniu etykiety usługi Azure Information Protection możesz można następnie dodać go do zasady, aby była dostępna dla użytkowników. W przypadku etykiety dla wszystkich użytkowników, należy dodać etykietę do globalnych zasad. Jeśli etykieta podzbiór użytkowników, Dodaj etykietę do zakresie zasad. Obecnie można dodać etykietę do tylko jednej zasady. Aby dodać sublabel, jego nadrzędny etykiety musi być w ramach jednych zasad lub w ramach globalnych zasad.

Dla etykiet, które znajdują się już w zasadach należy je usunąć z zasad. Ta akcja nie powoduje usunięcia etykiety. Pozostaje dostępne do użycia w inne zasady.

Jeśli jeszcze nie utworzono etykiety, zobacz [Tworzenie nowej etykiety dla usługi Azure Information Protection](configure-policy-new-label.md).

Jeśli chcesz utworzyć zasadę zakresami tak, czy etykieta ma zastosowanie do określonej podgrupy użytkowników, zobacz [sposobu konfigurowania zasad usługi Azure Information Protection dla konkretnych użytkowników przy użyciu zakres zasad](configure-policy-scope.md).

## <a name="to-add-or-remove-a-label-to-or-from-a-policy"></a>Aby dodać lub usunąć etykietę do lub z zasad

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **zasady** opcji menu: na **usługi Azure Information Protection** - **zasady** bloku, wybierz opcję **Global** etykiety, aby dodać lub usunąć dotyczy wszystkich użytkowników.

    Jeśli etykiety, aby dodać lub usunąć ma zastosowanie do określonej podgrupy użytkowników, należy wybrać zakresie zasad.

3. Na **zasad** bloku, wybierz opcję **Dodaj lub usuń etykiety**.

4. Na **zasad: Dodawanie lub usuwanie etykiety** bloku widzisz wszystkich etykiet z pole wyboru jest zaznaczone, jeśli są one już zasady i nazwą zasad w **zasad** kolumny.
     
    Sublabels są wyświetlane jako wcięcia. W zakresie zasad etykiety, które są dziedziczone z globalne zasady wyświetlanej jako niedostępny.
    
    Wykonaj jedną lub więcej z następujących czynności, a następnie kliknij przycisk **OK**:
    
    - Aby dodać etykietę, zaznacz go, który dodaje wybrane pole wyboru.
    
    - Aby usunąć etykietę, wyczyść jej pole wyboru.
  
5. Kliknij przycisk **Zapisz**, aby zapisać zmiany.
   
    Zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma oddzielne Publikuj.


## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
