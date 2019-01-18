---
title: Konfigurowanie ustawień zasad usługi Azure Information Protection — AIP
description: Skonfiguruj ustawienia w zasadach usługi Azure Information Protection mające zastosowanie do wszystkich użytkowników i urządzeń.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/16/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: c3d95b0dc8328665c921ab4ff6b37e53ec726f03
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393479"
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Konfigurowanie ustawień zasad usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Oprócz tytuł paska i etykietkę narzędzia istnieją niektóre ustawienia w zasadach usługi Azure Information Protection, które można skonfigurować niezależnie od etykiety:

![Ustawienia globalne zasad usługi Azure Information Protection](./media/info-protect-policy-default-settingsv3.png)

Należy pamiętać, że ustawienia zasad mogą mieć różne domyślne wartości, w zależności od tego, jeśli zakupiono subskrypcję usługi Azure Information Protection. Niektóre ustawienia mogą również ustawić, [niestandardowe ustawienie klienta](./rms-client/client-admin-guide-customizations.md).

Aby skonfigurować te ustawienia:

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **zasady** opcji menu: Na **usługi Azure Information Protection — zasady** bloku wybierz **Global** Jeśli ustawienia, które chcesz skonfigurować, będzie miała zastosowanie do wszystkich użytkowników.
    
    Jeśli ustawienia, które chcesz skonfigurować znajdują się w [zasad o określonym zakresie](configure-policy-scope.md) tak, aby dotyczyły one tylko do wybranych użytkowników, wybierz swoje te zasady o określonym zakresie.

3. Na **zasad** bloku, skonfigurować ustawienia:
    
   - **Wybierz etykietę domyślną**: Po ustawieniu tej opcji Wybierz etykietę do przypisania do dokumentów i wiadomości e-mail, które nie mają etykiety. Nie można ustawić etykiety jako domyślny, jeśli ma on etykiet podrzędnych. 
    
   - **Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**: Po ustawieniu tej opcji na **na**, wszystkie zapisane dokumenty i wysłane wiadomości e-mail muszą mieć etykietę stosowaną. Etykiety mogą być przypisywane ręcznie przez użytkownika, automatycznie na podstawie [warunku](configure-policy-classification.md) lub domyślnie (przy użyciu opcji **Wybierz etykietę domyślną**).
        
       Jeśli etykieta nie jest przypisany, gdy użytkownicy zapisywania dokumentu lub Wyślij wiadomość e-mail, są monitowani o wybranie etykiety. Przykład:
        
       ![Monit usługi Azure Information Protection, jeśli etykietowanie jest wymuszane](./media/info-protect-enforce-labelv2.png)
        
       Ta opcja nie ma zastosowania, gdy usuniesz etykietę przy użyciu [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) polecenia cmdlet programu PowerShell przy użyciu *RemoveLabel* parametru.
        
   - **Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę**: Po ustawieniu tej opcji na **na** i wykonaniu dowolnej z tych akcji przez użytkownika (na przykład zmienić **publicznych** etykietę **osobistych**), użytkownik jest monitowany o podanie wyjaśnienia dla tej akcji. Przykładowo użytkownik może wyjaśnić, że dokument nie zawiera już poufnych informacji. Akcji i przyczynę jej uzasadnienie są rejestrowane w ich lokalnym dzienniku zdarzeń Windows: **Dzienniki aplikacji i usług** > **usługi Azure Information Protection**.  
        
       ![Monit usługi Azure Information Protection w przypadku wybrania niższej klasyfikacji](./media/info-protect-lower-justification.png)
        
       Ta opcja nie ma zastosowania, obniżając klasyfikacji etykiet podrzędnych, w ramach tej samej etykiety nadrzędnej lub skaner w wersji zapoznawczej.
        
   - **W przypadku wiadomości e-mail z załącznikami Zastosuj etykietę, która odpowiada najwyższej klasyfikacji tych załączników**: Po ustawieniu tej opcji na **zalecane**, użytkownicy są monitowani o zastosowanie etykiety do wiadomości e-mail. Etykieta jest wybierana dynamicznie na podstawie klasyfikacji etykiet, która jest stosowana do załączników, po czym jest wybierana etykieta o najwyższej klasyfikacji. Załącznik musi być plikiem fizycznym i nie może być łączem do pliku (na przykład łączem do pliku w usłudze SharePoint lub OneDrive dla Firm). Użytkownicy mogą zaakceptować zalecenie lub odrzucić je. Po ustawieniu tej opcji na **automatyczne**, etykieta jest stosowana automatycznie, ale użytkownicy mogą usunąć etykietę lub wybrać inną etykietę przed wysłaniem wiadomości e-mail.
    
     Po skonfigurowaniu załącznika z najwyższą etykiety klasyfikacji dla ochrony za pomocą ustawień w wersji zapoznawczej uprawnienia zdefiniowane przez użytkownika wiadomości e-mail jest oznaczony za pomocą tej samej klasyfikacji, ale ochrona nie jest stosowana.
    
   - **Wyświetl pasek usługi Information Protection w aplikacjach pakietu Office**: Gdy to ustawienie jest wyłączone, użytkownicy nie można wybrać etykiety na pasku Word, Excel, PowerPoint i Outlook. Zamiast tego użytkownicy muszą wybrać etykiety z **Chroń** przycisk na Wstążce. Gdy to ustawienie jest włączone, użytkownicy mogą wybrać etykiety z paska lub przycisku.
        
       Gdy to ustawienie jest włączone, może służyć w połączeniu z klientem Zaawansowane ustawienia, aby użytkownicy mogą [trwałe ukrycie paska usługi Azure Information Protection](./rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar) Jeśli zdecydują się pokazywany na pasku. Można to zrobić, czyszcząc **Pokaż pasek** opcję **Chroń** przycisku.
    
   - **Dodawanie przycisku nie przesyłaj dalej do Wstążki programu Outlook**: Gdy to ustawienie jest włączone, użytkownicy mogą wybrać ten przycisk **ochrony** grupę na wstążce programu Outlook, oprócz wybierając **nie przesyłaj dalej** opcję z menu programu Outlook. Aby mieć pewność, że użytkownicy klasyfikowanie wiadomości e-mail, a także je chronić, warto dodaje ten przycisk, ale zamiast tego [Konfigurowanie etykiety w celu ochrony](configure-policy-protection.md) i uprawnień dla programu Outlook zdefiniowany przez użytkownika. To ustawienie ochrony funkcjonalnie jest taka sama, jak wybór **nie przesyłaj dalej** przycisku, ale gdy ta funkcja jest uwzględniona w etykietę, wiadomości e-mail są klasyfikowane, jak również chronione.
    
       To ustawienie zasad można również skonfigurować za pomocą Zaawansowanego klienta jako [dostosowywania klienta](./rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook).
    
   - **Udostępnij opcję niestandardowych uprawnień użytkownikom**: Gdy to ustawienie jest włączone, użytkownicy widzą opcje, aby ustawić własne ustawienia ochrony, które można zastąpić żadnych ustawień ochrony, które zostały uwzględnione w konfiguracji etykiety. Użytkownicy widzą także możliwość usunięcia ochrony. Gdy to ustawienie jest wyłączone, użytkownicy nie widzą tych opcji.
        
       Należy pamiętać, że to ustawienie zasad nie ma wpływu na uprawnienia niestandardowe, które użytkownicy mogą konfigurować z opcji menu pakietu Office. Jednak go można również skonfigurować za pomocą Zaawansowanego klienta jako [dostosowywania klienta](./rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users).
        
       Opcje uprawnień niestandardowych znajdują się w następujących miejscach:
        
       - W aplikacjach pakietu Office: Na wstążce **Home** kartę > **ochrony** grupy > **Chroń** > **uprawnienia niestandardowe**
        
       - W Eksploratorze plików: Kliknij prawym przyciskiem myszy > **Klasyfikuj i Chroń** > **uprawnienia niestandardowe**
    
   - **Podaj niestandardowy adres URL dla klienta usługi Azure Information Protection strony sieci web "Powiedz mi więcej"**: Użytkownicy widzą ten link w **Microsoft Azure Information Protection** okno dialogowe **Pomoc i opinie** sekcji, po wybraniu **Chroń**  >  **Pomoc i opinie** z **Home** kartę w swoich aplikacjach pakietu Office. Domyślnie ten link prowadzi do witryny sieci Web usługi [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection). Jeśli chcesz przejść do alternatywnej strony sieci Web, możesz wprowadzić adres URL protokołu HTTP lub HTTPS (zalecane). Nie jest przeprowadzana żadna weryfikacja, czy wprowadzony niestandardowy adres URL jest dostępny lub jest wyświetlany poprawnie na wszystkich urządzeniach.
        
       Na przykład dla pomocy technicznej, możesz wprowadzić strony dokumentacji firmy Microsoft, w tym informacje o instalowaniu i używaniu klienta (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) lub informacje o wersji (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Alternatywnie możesz opublikować własną stronę sieci Web zawierającą informacje dla użytkowników pozwalające skontaktować się z Twoją pomocą techniczną lub film, który krok po kroku objaśni użytkownikom, jak używać skonfigurowanych etykiet.

4. Kliknij, aby zapisać zmiany i udostępnić je użytkownikom **Zapisz**.

Po kliknięciu **Zapisz**, zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma już opcji publikowania oddzielne.

## <a name="next-steps"></a>Następne kroki

Aby zobaczyć, jak niektóre z tych ustawień zasad mogą współdziałać ze sobą, spróbuj [ustawienia zasad konfigurowania usługi Azure Information Protection, które współpracują ze sobą](infoprotect-settings-tutorial.md) samouczka.

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).

