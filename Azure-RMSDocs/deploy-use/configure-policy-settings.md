---
title: Konfigurowanie ustawień zasad usługi Azure Information Protection
description: Skonfiguruj ustawienia w zasadach usługi Azure Information Protection mające zastosowanie do wszystkich użytkowników i urządzeń.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: cfdb1537ad5444ef478c18380b535f38b5f7c667
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32326552"
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Konfigurowanie ustawień zasad usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Oprócz ochrony informacji pasek tytuł i etykietka narzędzia istnieją niektóre ustawienia zasad usługi Azure Information Protection, które można skonfigurować niezależnie od etykiety:

![Ustawienia globalne zasad usługi Azure Information Protection](../media/info-protect-policy-default-settingsv3.png)

Należy pamiętać, że ustawień zasad może być różne domyślne wartości, w zależności od tego, kiedy zakupiono subskrypcję usługi Azure Information Protection. Niektóre ustawienia mogą również ustawić, [niestandardowe ustawienie klienta](../rms-client/client-admin-guide-customizations.md).

Aby skonfigurować te ustawienia:

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **zasady** opcji menu: na **usługi Azure Information Protection — zasady** bloku, wybierz opcję **Global** Jeśli ustawienia, które chcesz skonfigurować zostaną zastosowane dla wszystkich użytkowników.
    
    Jeśli ustawienia, które chcesz skonfigurować znajdują się w [zakres zasad](configure-policy-scope.md) tak, aby dotyczą tylko wybrani użytkownicy, wybierz zasady zakresami zamiast tego.

3. Na **zasad** bloku, skonfigurować ustawienia:
    
    - **Wybierz etykietę domyślną**: po ustawieniu tej opcji wybierz etykietę, która ma być przypisywana do dokumentów i wiadomości e-mail bez etykiety. Nie możesz ustawić etykiety jako etykiety domyślnej, jeśli zawiera ona etykiety podrzędne. 
    
    - **Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**: w przypadku ustawienia dla tej opcji wartości **Wł.** wszystkie zapisane dokumenty i wysłane wiadomości e-mail będą musiały mieć zastosowaną etykietę. Etykiety mogą być przypisywane ręcznie przez użytkownika, automatycznie na podstawie [warunku](configure-policy-classification.md) lub domyślnie (przy użyciu opcji **Wybierz etykietę domyślną**).
        
        Jeśli etykieta nie przypisano użytkowników zapisywania dokumentu lub wysyłania wiadomości e-mail, są monitowani o wybranie etykiety. Przykład:
        
        ![Monit usługi Azure Information Protection, jeśli etykietowanie jest wymuszane](../media/info-protect-enforce-labelv2.png)
        
    - **Użytkownicy muszą uzasadnić obniżenie etykiety klasyfikacji, usunięcie etykiety lub usunięcie ochrony**: po ustawieniu tej opcji na wartość **Włączone** i wykonaniu dowolnej z tych akcji przez użytkownika (na przykład zmianie etykiety **Publiczne** na **Osobiste**) użytkownik jest monitowany o podanie wyjaśnienia dla tej akcji. Przykładowo użytkownik może wyjaśnić, że dokument nie zawiera już poufnych informacji. Akcji i przyczynę jej uzasadnienie, są rejestrowane w ich lokalnym dzienniku zdarzeń systemu Windows: **Dzienniki aplikacji i usług** > **usługi Azure Information Protection**.  
        
        ![Monit usługi Azure Information Protection w przypadku wybrania niższej klasyfikacji](../media/info-protect-lower-justification.png)
        
        Ta opcja nie ma zastosowania do sublabels.
        
    - **W przypadku wiadomości e-mail z załącznikami zastosuj etykietę, która odpowiada najwyższej klasyfikacji tych załączników**: po ustawieniu wartości tej opcji na **Zalecane** użytkownicy są monitowani o zastosowanie etykiety do wiadomości e-mail. Etykieta jest wybierana dynamicznie na podstawie klasyfikacji etykiet, która jest stosowana do załączników, po czym jest wybierana etykieta o najwyższej klasyfikacji. Załącznik musi być plikiem fizycznym i nie może być łączem do pliku (na przykład łączem do pliku w usłudze SharePoint lub OneDrive dla Firm). Użytkownicy mogą zaakceptować zalecenie lub odrzucić je. Po ustawieniu wartości tej opcji na **Włączone** etykieta jest stosowana automatycznie, ale użytkownicy mogą usunąć etykietę lub wybrać inną etykietę przed wysłaniem wiadomości e-mail.  
    
    - **Wyświetl pasek Information Protection w aplikacji pakietu Office**: Jeśli to ustawienie jest wyłączone, użytkownicy nie można wybrać etykiety z paska Word, Excel, PowerPoint i Outlook. Zamiast tego użytkownicy muszą wybrać etykiety z **Chroń** na Wstążce. Gdy to ustawienie jest włączone, użytkownicy mogą wybrać etykiety z pasku lub przycisku.
        
        Gdy to ustawienie jest włączone, można w połączeniu z klientem Zaawansowane ustawienia, dzięki czemu użytkownicy mogą [trwale ukryć pasek usługi Azure Information Protection](../rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar) decydując pokazywany na pasku. Można to zrobić, usuwając zaznaczenie **Pokaż pasek** opcję **Chroń** przycisku.
    
    - **Dodawanie przycisku nie przesyłaj dalej do wstążki Outlook**: Jeśli to ustawienie jest włączone, użytkownicy mogą wybrać ten przycisk z **ochrony** na wstążce programu Outlook także wybrać **nie przesyłaj dalej** opcji z menu programu Outlook. Aby zapewnić, że użytkownicy klasyfikowania ich wiadomości e-mail, a także je chronić, warto nie dodać ten przycisk, ale zamiast tego [Konfigurowanie etykiety pod kątem ochrony](configure-policy-protection.md) i uprawnień dla programu Outlook zdefiniowany przez użytkownika. To ustawienie ochrony funkcjonalnie jest taka sama jak wybranie **nie przesyłaj dalej** przycisku, ale gdy ta funkcja jest dostarczany z etykiet, wiadomości e-mail są klasyfikowane, a także chronione.
    
        To ustawienie zasad można również skonfigurować za pomocą klienta Zaawansowane ustawienia jako [dostosowywania klienta](../rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook).
    
    - **Udostępnić użytkownikom opcję uprawnień niestandardowych**: gdy to ustawienie jest włączone, użytkownicy mogą ustawić własne ustawienia ochrony i Zastąp wszystkie ustawienia ochrony, które zostały uwzględnione w konfiguracji etykiety. Gdy to ustawienie jest wyłączone, nie są dostępne dla użytkowników wybrać opcje uprawnienia niestandardowe.
        
        Należy pamiętać, że to ustawienie zasad nie ma wpływu na uprawnienia niestandardowe, które użytkownicy mogą konfigurować opcje menu pakietu Office. Jednak go można również skonfigurować za pomocą klienta Zaawansowane ustawienia jako [dostosowywania klienta](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users).
        
        Opcje uprawnień niestandardowych znajdują się w następujących miejscach:
        
        - W aplikacjach pakietu Office: na wstążce **Home** kartę > **ochrony** grupy > **Chroń** > **uprawnienia niestandardowe**
        
        - W Eksploratorze plików: kliknij prawym przyciskiem myszy opcję **Klasyfikuj i chroń** > **Uprawnienia niestandardowe**
    
    - **Podaj niestandardowy adres URL dla klienta usługi Azure Information Protection "Dowiedz się więcej" strona sieci web**: użytkownicy widzą to łącze w **Microsoft Azure Information Protection** okno dialogowe **Pomoc i opinie**sekcji, gdy użytkownik wybierze **Chroń** > **Pomoc i opinie** z **Home** kartę w swoich aplikacjach pakietu Office. Domyślnie ten link prowadzi do witryny sieci Web usługi [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection). Jeśli chcesz przejść do alternatywnej strony sieci Web, możesz wprowadzić adres URL protokołu HTTP lub HTTPS (zalecane). Nie jest przeprowadzana żadna weryfikacja, czy wprowadzony niestandardowy adres URL jest dostępny lub jest wyświetlany poprawnie na wszystkich urządzeniach.
        
        Na przykład dla pomocy technicznej, możesz wpisać stronę dokumentacji firmy Microsoft zawierający informacje o instalowaniu i używaniu klienta (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) lub zwolnij informacje o wersji (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Alternatywnie możesz opublikować własną stronę sieci Web zawierającą informacje dla użytkowników pozwalające skontaktować się z Twoją pomocą techniczną lub film, który krok po kroku objaśni użytkownikom, jak używać skonfigurowanych etykiet.

3. Kliknij, aby zapisać zmiany i udostępnić je użytkownikom **zapisać**.

Po kliknięciu **zapisać**, zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma oddzielne Publikuj.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
