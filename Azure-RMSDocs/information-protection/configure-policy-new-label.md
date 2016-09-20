---
title: "Jak utworzyć nową etykietę dla usługi Azure Information Protection | Azure Information Protection"
description: "Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection."
manager: mbaldwin
ms.date: 09/14/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
translationtype: Human Translation
ms.sourcegitcommit: 801ca11da602d4acb9c398c9a89aeb33e45cb0f4
ms.openlocfilehash: 4edbdde88444304c314251124618d563a3662477


---

# Tworzenie nowej etykiety dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection.

Jeśli potrzebujesz dodatkowego poziomu klasyfikacji, możesz dodać nową etykietę lub etykietę podrzędną do istniejącej etykiety. Na przykład etykieta **Tajne** znajdująca się w [zasadach domyślnych](configure-policy-default.md) zawiera etykiety podrzędne.

Użyj poniższych instrukcji, aby dodać nową etykietę do zasad usługi Azure Information Protection.

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com), a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. W bloku **Azure Information Protection** wykonaj jedną z następujących czynności:

    - Aby utworzyć nową etykietę: kliknij przycisk **Dodaj nową etykietę**.

    - Aby utworzyć nową etykietę podrzędną: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...**) etykiety, dla której chcesz utworzyć etykietę podrzędną, a następnie kliknij polecenie **Dodaj etykietę podrzędną**.

3. W bloku **Etykieta** lub **Etykieta podrzędna** wybierz opcje dla nowej etykiety, a następnie kliknij przycisk **Zapisz**.

    > [!NOTE]
    >Aby uzyskać informacje o konfigurowaniu ochrony, zobacz [Konfigurowanie etykiety w celu zastosowania ochrony](configure-policy-protection.md).

4. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Sep16_HO3-->


