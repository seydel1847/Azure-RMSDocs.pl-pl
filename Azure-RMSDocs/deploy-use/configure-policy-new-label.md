---
title: "Nowa etykieta usługi Azure Information Protection"
description: "Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: eb9f68994d92695412c64a7795c6ae2b2b094218
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Tworzenie nowej etykiety dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection.

Jeśli potrzebujesz dodatkowego poziomu klasyfikacji, możesz dodać nową etykietę lub etykietę podrzędną do istniejącej etykiety. Na przykład etykieta **Tajne** znajdująca się w [zasadach domyślnych](configure-policy-default.md) zawiera etykiety podrzędne.

Użyj poniższych instrukcji, aby dodać nową etykietę do zasad usługi Azure Information Protection.

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator globalny, a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. Jeśli nowa etykieta, którą chcesz dodać, będzie miała zastosowanie do wszystkich użytkowników, wykonaj jedną z następujących czynności z bloku **Zasady: Globalne**. 

    - Aby utworzyć nową etykietę: kliknij przycisk **Dodaj nową etykietę**.

    - Aby utworzyć nową etykietę podrzędną: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...**) etykiety, dla której chcesz utworzyć etykietę podrzędną, a następnie kliknij polecenie **Dodaj etykietę podrzędną**.
    
     Jeśli nowa etykieta, którą chcesz dodać, będzie należeć do [zasad o określonym zakresie](configure-policy-scope.md) i z tego powodu będzie miała zastosowanie tylko do wybranych użytkowników, najpierw wybierz te zasady o określonym zakresie z początkowego bloku **Azure Information Protection**.

3. W bloku **Etykieta** lub **Etykieta podrzędna** wybierz opcje dla nowej etykiety, a następnie kliknij przycisk **Zapisz**.

    > [!NOTE]
    >Aby uzyskać informacje o konfigurowaniu ochrony, zobacz [Konfigurowanie etykiety w celu zastosowania ochrony](configure-policy-protection.md).

4. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

