---
title: "Konfigurowanie ustawień globalnych zasad usługi Azure Information Protection | Azure Information Protection"
description: "Istnieją 3 ustawienia w zasadach usługi Azure Information Protection, które mają zastosowanie do wszystkich użytkowników i urządzeń."
manager: mbaldwin
ms.date: 09/14/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: 801ca11da602d4acb9c398c9a89aeb33e45cb0f4
ms.openlocfilehash: d4e96321069b27ed832af3bfb6d995e0d3c5d450


---

# Konfigurowanie ustawień globalnych zasad usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Istnieją 3 ustawienia w zasadach usługi Azure Information Protection, które mają zastosowanie do wszystkich użytkowników i urządzeń:

![Ustawienia globalne zasad usługi Azure Information Protection](../media/info-protect-policy-settings.png)


Aby skonfigurować te ustawienia:

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com), a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. W bloku **Azure Information Protection** skonfiguruj następujące ustawienia globalne:

    - **Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**: w przypadku ustawienia dla tej opcji wartości **Wł.** wszystkie zapisane dokumenty i wysłane wiadomości e-mail będą musiały mieć zastosowaną etykietę. Etykiety mogą być przypisywane ręcznie przez użytkownika, automatycznie na podstawie [warunku](configure-policy-classification.md) lub domyślnie (przy użyciu opcji **Wybierz etykietę domyślną**). 

    Jeśli etykieta nie jest przypisana w momencie zapisywania dokumentu lub wysyłania wiadomości e-mail przez użytkownika, użytkownik otrzyma monit o wybranie etykiety:

    ![Monit usługi Azure Information Protection w przypadku wybrania niższej klasyfikacji](../media/info-protect-enforce-label.png)

    - **Wybierz etykietę domyślną**: po ustawieniu tej opcji wybierz etykietę, która ma być przypisywana do dokumentów i wiadomości e-mail bez etykiety. Nie możesz ustawić etykiety jako etykiety domyślnej, jeśli zawiera ona etykiety podrzędne. 

    - **Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę**: po ustawieniu tej opcji na wartość **Włączone** i wykonaniu dowolnej z tych akcji przez użytkownika (na przykład zmianie etykiety **Poufne** na **Osobiste**) użytkownik jest monitowany o podanie wyjaśnienia dla tej akcji. Przykładowo użytkownik może wyjaśnić, że dokument nie zawiera już poufnych informacji. Wykonywana czynność oraz stosowne uzasadnienie zostaną zapisane w ich lokalnym dzienniku zdarzeń systemu Windows: **Aplikacja**  >  **Microsoft Azure Information Protection**.  

    ![Monit usługi Azure Information Protection w przypadku wybrania niższej klasyfikacji](../media/info-protect-lower-justification.png)

    Ta opcja nie ma zastosowania wobec etykiet podrzędnych.

3. Kliknij przycisk **Zapisz**, aby zapisać zmiany.

4. Aby udostępnić zmiany użytkownikom, kliknij przycisk **Opublikuj**.

## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy).  












<!--HONumber=Sep16_HO3-->


