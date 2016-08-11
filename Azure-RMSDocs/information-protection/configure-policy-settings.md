---
title: "Konfigurowanie ustawień globalnych zasad usługi Azure Information Protection | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 3b22cf76f03a4d36281db7e705359402dcbbde0e


---

# Konfigurowanie ustawień globalnych zasad usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Istnieją 3 ustawienia w zasadach usługi Azure Information Protection, które mają zastosowanie do wszystkich użytkowników i urządzeń:

![Ustawienia globalne zasad usługi Azure Information Protection](../media/info-protect-policy-settings.png)


Aby skonfigurować te ustawienia:

1. Zaloguj się do [portalu Azure](https://portal.azure.com).
 
2. Następnie w menu centralnym kliknij **Przeglądaj** i w polu filtru zacznij pisać **Information**. Wybierz pozycję **Azure Information Protection**.

3. W bloku **Azure Information Protection** skonfiguruj następujące ustawienia globalne:

    - **Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**: w przypadku ustawienia dla tej opcji wartości **Wł.** wszystkie zapisane dokumenty i wysłane wiadomości e-mail będą musiały mieć zastosowaną etykietę. Etykiety mogą być przypisywane ręcznie przez użytkownika, automatycznie na podstawie [warunku](configure-policy-classification.md) lub domyślnie (przy użyciu opcji **Wybierz etykietę domyślną**). 

    Jeśli etykieta nie jest przypisana w momencie zapisywania dokumentu lub wysyłania wiadomości e-mail przez użytkownika, użytkownik otrzyma monit o wybranie etykiety:

    ![Monit usługi Azure Information Protection w przypadku wybrania niższej klasyfikacji](../media/info-protect-enforce-label.png)

    - **Wybierz etykietę domyślną**: po ustawieniu tej opcji wybierz etykietę, która ma być przypisywana do dokumentów i wiadomości e-mail bez etykiety. Nie możesz ustawić etykiety jako etykiety domyślnej, jeśli zawiera ona etykiety podrzędne. 

    - **Użytkownicy muszą uzasadniać obniżenie charakterystyki**: w przypadku ustawienia tej opcji na wartość **Wł.** i zmiany etykiety istniejącego dokumentu lub wiadomości e-mail przez użytkownika na etykietę o niższej charakterystyce (np. z **Tajne** na **Publiczne**) użytkownik otrzyma monit o wyjaśnienie swojego działania. Przykładowo użytkownik może wyjaśnić, że dokument nie zawiera już poufnych informacji. Wykonywana czynność oraz stosowne uzasadnienie zostaną zapisane w ich lokalnym dzienniku zdarzeń systemu Windows: **Aplikacja**  >  **Microsoft Azure Information Protection**.  

    ![Monit usługi Azure Information Protection w przypadku wybrania niższej klasyfikacji](../media/info-protect-lower-justification.png)

    Ta opcja nie ma zastosowania wobec etykiet podrzędnych.

4. Kliknij przycisk **Zapisz**, aby zapisać zmiany.

5. Aby udostępnić zmiany użytkownikom, kliknij przycisk **Opublikuj**.

## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy).  












<!--HONumber=Jul16_HO5-->


