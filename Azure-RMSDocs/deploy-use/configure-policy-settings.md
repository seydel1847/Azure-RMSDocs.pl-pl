---
title: "Konfigurowanie ustawień zasad usługi Azure Information Protection"
description: "Skonfiguruj ustawienia w zasadach usługi Azure Information Protection mające zastosowanie do wszystkich użytkowników i urządzeń."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: 2bc5493c906b0d21be2679f0d777cb4fd5fbe30c
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2017
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Konfigurowanie ustawień zasad usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Poza tytułem i etykietką narzędzia paska usługi Information Protection istnieje kilka ustawień w zasadach usługi Azure Information Protection, które mają zastosowanie do wszystkich użytkowników i urządzeń:

![Ustawienia globalne zasad usługi Azure Information Protection](../media/info-protect-policy-default-settingsv2.png)


Aby skonfigurować te ustawienia:

1. Jeśli jeszcze tego nie zrobiono, nowe okno przeglądarki, zaloguj się do [portalu Azure](https://portal.azure.com) jako zabezpieczeń administratora lub administratora globalnego. Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. Jeśli ustawienia, które chcesz skonfigurować zostaną zastosowane dla wszystkich użytkowników, pozostają **usługi Azure Information Protection — globalne zasady** bloku.
    
    Jeśli ustawienia, które chcesz skonfigurować znajdują się w [zakres zasad](configure-policy-scope.md) tak, aby dotyczą tylko wybrani użytkownicy z **zasady** zaznaczenia menu, wybierz opcję **zakres zasad**. Następnie wybierz zakresie zasad z **zasady usługi Azure Information Protection - zakres** bloku.

3. Z **usługi Azure Information Protection — globalne zasady** bloku lub **zasad:\<name >** bloku, skonfigurować ustawienia:
    
    - **Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**: w przypadku ustawienia dla tej opcji wartości **Wł.** wszystkie zapisane dokumenty i wysłane wiadomości e-mail będą musiały mieć zastosowaną etykietę. Etykiety mogą być przypisywane ręcznie przez użytkownika, automatycznie na podstawie [warunku](configure-policy-classification.md) lub domyślnie (przy użyciu opcji **Wybierz etykietę domyślną**). 
        
        Jeśli etykieta nie jest przypisana w momencie zapisywania dokumentu lub wysyłania wiadomości e-mail przez użytkownika, użytkownik otrzyma monit o wybranie etykiety. Na przykład:
        
        ![Monit usługi Azure Information Protection, jeśli etykietowanie jest wymuszane](../media/info-protect-enforce-labelv2.png)
        
    - **Wybierz etykietę domyślną**: po ustawieniu tej opcji wybierz etykietę, która ma być przypisywana do dokumentów i wiadomości e-mail bez etykiety. Nie możesz ustawić etykiety jako etykiety domyślnej, jeśli zawiera ona etykiety podrzędne. 
        
    - **Użytkownicy muszą uzasadnić obniżenie etykiety klasyfikacji, usunięcie etykiety lub usunięcie ochrony**: po ustawieniu tej opcji na wartość **Włączone** i wykonaniu dowolnej z tych akcji przez użytkownika (na przykład zmianie etykiety **Publiczne** na **Osobiste**) użytkownik jest monitowany o podanie wyjaśnienia dla tej akcji. Przykładowo użytkownik może wyjaśnić, że dokument nie zawiera już poufnych informacji. Wykonywana czynność oraz stosowne uzasadnienie zostaną zapisane w ich lokalnym dzienniku zdarzeń systemu Windows: **Aplikacja**  >  **Microsoft Azure Information Protection**.  
        
        ![Monit usługi Azure Information Protection w przypadku wybrania niższej klasyfikacji](../media/info-protect-lower-justification.png)
        
        Ta opcja nie ma zastosowania wobec etykiet podrzędnych.
        
    - **W przypadku wiadomości e-mail z załącznikami zastosuj etykietę, która odpowiada najwyższej klasyfikacji tych załączników**: po ustawieniu wartości tej opcji na **Zalecane** użytkownicy są monitowani o zastosowanie etykiety do wiadomości e-mail. Etykieta jest wybierana dynamicznie na podstawie klasyfikacji etykiet, która jest stosowana do załączników, po czym jest wybierana etykieta o najwyższej klasyfikacji. Załącznik musi być plikiem fizycznym i nie może być łączem do pliku (na przykład łączem do pliku w usłudze SharePoint lub OneDrive dla Firm). Użytkownicy mogą zaakceptować zalecenie lub odrzucić je. Po ustawieniu wartości tej opcji na **Włączone** etykieta jest stosowana automatycznie, ale użytkownicy mogą usunąć etykietę lub wybrać inną etykietę przed wysłaniem wiadomości e-mail.  

    - **Podaj niestandardowy adres URL dla klienta usługi Azure Information Protection dla strony sieci Web „Powiedz mi więcej**: użytkownicy widzą ten link w oknie dialogowym usługi **Microsoft Azure Information Protection**, w sekcji **Pomoc i opinie** po wybraniu pozycji **Ochrona** > **Pomoc i opinie** na karcie **Narzędzia główne** w swoich aplikacjach pakietu Office. Domyślnie ten link prowadzi do witryny sieci Web usługi [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection). Jeśli chcesz przejść do alternatywnej strony sieci Web, możesz wprowadzić adres URL protokołu HTTP lub HTTPS (zalecane). Nie jest przeprowadzana żadna weryfikacja, czy wprowadzony niestandardowy adres URL jest dostępny lub jest wyświetlany poprawnie na wszystkich urządzeniach.
        
        Na przykład dla pomocy technicznej możesz wprowadzić adres strony dokumentacji firmy Microsoft, która zawiera informacje na temat instalowania klienta i korzystania z niego (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) lub informacje o wersji (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Alternatywnie możesz opublikować własną stronę sieci Web zawierającą informacje dla użytkowników pozwalające skontaktować się z Twoją pomocą techniczną lub film, który krok po kroku objaśni użytkownikom, jak używać skonfigurowanych etykiet.

3. Kliknij przycisk **Zapisz**, aby zapisać zmiany.

4. Aby udostępnić użytkownikom zmiany, w początkowym bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
