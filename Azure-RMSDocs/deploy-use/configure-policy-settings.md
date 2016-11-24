---
title: "Konfigurowanie ustawień globalnych zasad | Azure Information Protection"
description: "Istnieją 3 ustawienia w zasadach usługi Azure Information Protection, które mają zastosowanie do wszystkich użytkowników i urządzeń."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: 8fa2ed9ff9ebe5c850ab5681e4dcc1f3d3c676b3
ms.openlocfilehash: de5f5fbddb84e4444751e9fefbfe6ec3fe3e45e4


---

# <a name="how-to-configure-the-global-policy-settings-for-azure-information-protection"></a>Konfigurowanie ustawień globalnych zasad usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Istnieją cztery ustawienia w zasadach usługi Azure Information Protection, które mają zastosowanie do wszystkich użytkowników i urządzeń:

![Ustawienia globalne zasad usługi Azure Information Protection](../media/info-protect-policy-settings.png)


Aby skonfigurować te ustawienia:

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator globalny, a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. W bloku **Azure Information Protection** skonfiguruj następujące ustawienia globalne:

    - **Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**: w przypadku ustawienia dla tej opcji wartości **Wł.** wszystkie zapisane dokumenty i wysłane wiadomości e-mail będą musiały mieć zastosowaną etykietę. Etykiety mogą być przypisywane ręcznie przez użytkownika, automatycznie na podstawie [warunku](configure-policy-classification.md) lub domyślnie (przy użyciu opcji **Wybierz etykietę domyślną**). 

    Jeśli etykieta nie jest przypisana w momencie zapisywania dokumentu lub wysyłania wiadomości e-mail przez użytkownika, użytkownik otrzyma monit o wybranie etykiety:

    ![Monit usługi Azure Information Protection w przypadku wybrania niższej klasyfikacji](../media/info-protect-enforce-label.png)

    - **Wybierz etykietę domyślną**: po ustawieniu tej opcji wybierz etykietę, która ma być przypisywana do dokumentów i wiadomości e-mail bez etykiety. Nie możesz ustawić etykiety jako etykiety domyślnej, jeśli zawiera ona etykiety podrzędne. 

    - **Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę**: po ustawieniu tej opcji na wartość **Włączone** i wykonaniu dowolnej z tych akcji przez użytkownika (na przykład zmianie etykiety **Poufne** na **Osobiste**) użytkownik jest monitowany o podanie wyjaśnienia dla tej akcji. Przykładowo użytkownik może wyjaśnić, że dokument nie zawiera już poufnych informacji. Wykonywana czynność oraz stosowne uzasadnienie zostaną zapisane w ich lokalnym dzienniku zdarzeń systemu Windows: **Aplikacja**  >  **Microsoft Azure Information Protection**.  

    ![Monit usługi Azure Information Protection w przypadku wybrania niższej klasyfikacji](../media/info-protect-lower-justification.png)

    Ta opcja nie ma zastosowania wobec etykiet podrzędnych.

    - **Podaj niestandardowy adres URL dla klienta usługi Azure Information Protection dla strony sieci Web „Powiedz mi więcej**: użytkownicy widzą ten link w oknie dialogowym usługi **Microsoft Azure Information Protection**, w sekcji **Pomoc i opinie** po wybraniu pozycji **Ochrona** > **Pomoc i opinie** na karcie **Narzędzia główne** w swoich aplikacjach pakietu Office. Domyślnie ten link prowadzi do witryny sieci Web usługi [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection). Jeśli chcesz przejść do alternatywnej strony sieci Web, możesz wprowadzić adres URL protokołu HTTP lub HTTPS (zalecane). Nie jest przeprowadzana żadna weryfikacja, czy wprowadzony niestandardowy adres URL jest dostępny lub jest wyświetlany poprawnie na wszystkich urządzeniach.
    
    Na przykład dla pomocy technicznej możesz wprowadzić adres strony dokumentacji firmy Microsoft, która zawiera informacje na temat instalowania klienta i korzystania z niego (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) lub informacje o wersji (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Alternatywnie możesz opublikować własną stronę sieci Web zawierającą informacje dla użytkowników pozwalające skontaktować się z Twoją pomocą techniczną lub film, który krok po kroku objaśni użytkownikom, jak używać skonfigurowanych etykiet.

3. Kliknij przycisk **Zapisz**, aby zapisać zmiany.

4. Aby udostępnić zmiany użytkownikom, kliknij przycisk **Opublikuj**.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  












<!--HONumber=Nov16_HO3-->


