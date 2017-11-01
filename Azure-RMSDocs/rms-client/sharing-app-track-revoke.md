---
title: "Śledzenie i odwoływanie dokumentów za pomocą aplikacji RMS sharing — AIP"
description: "Po włączeniu ochrony dokumentów za pomocą aplikacji RMS sharing można śledzić użycie chronionych dokumentów. W razie konieczności można także cofnąć dostęp do tych dokumentów, aby zatrzymać ich udostępnianie."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 61f349ce-bdd2-45c1-acc5-bc83937fb187
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 71f08e7500fbc9326bed3a5b37d694ecc5e37984
ms.sourcegitcommit: 02e48f0e5137ba777ec9a2bccde08130e6075c20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2017
---
# <a name="track-and-revoke-your-documents-when-you-use-the-rms-sharing-application"></a>Śledzenie i odwoływanie dokumentów podczas używania aplikacji RMS sharing

>*Dotyczy: Azure Information Protection, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Po zapewnieniu ochrony dokumentów przy użyciu aplikacji RMS sharing, jeśli organizacja korzysta z usługi Azure Information Protection zamiast usług Active Directory Rights Management, można sprawdzić, w jaki sposób użytkownicy korzystają z chronionych dokumentów. W razie konieczności można także cofnąć dostęp do tych dokumentów, aby zatrzymać ich udostępnianie. W tym celu należy użyć **witryny śledzenia dokumentów** dostępnej z komputerów z systemem Windows, komputerów Mac, a nawet tabletów i telefonów.

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation/player" frameborder="0" allowfullscreen></iframe>
</div>

Po uzyskaniu dostępu do tej witryny zaloguj się, aby śledzić swoje dokumenty. Jeśli Twoja organizacja ma [subskrypcję obsługującą śledzenie i odwoływanie dokumentów](https://www.microsoft.com/cloud-platform/azure-information-protection-features) oraz masz licencję na tę subskrypcję, możesz sprawdzić, kto próbował otworzyć zabezpieczone pliki i czy próba ta zakończyła się powodzeniem (nastąpiło pomyślne uwierzytelnienie). Rejestrowana jest także data i godzina próby otwarcia dokumentu oraz lokalizacja tego zdarzenia. Ponadto:

-   Jeśli chcesz zatrzymać udostępnianie dokumentu: kliknij pozycję **Odwołaj dostęp**, podaj okres, przez jaki dokument będzie jeszcze dostępny, i zdecyduj, czy chcesz powiadomić o odwołaniu dostępu osoby, którym dokument był wcześniej udostępniony. Jeśli się na to zdecydujesz, przygotuj niestandardową wiadomość dla nich. Odwołanie udostępnionego dokumentu nie powoduje jego usunięcia, ale blokuje możliwość otwierania go przez autoryzowanych użytkowników.

-   Jeśli chcesz wyeksportować plik do programu Excel: kliknij pozycję **Eksportuj do pliku CSV**, aby móc modyfikować dane i tworzyć własne widoki oraz wykresy.

-   Jeśli chcesz skonfigurować powiadomienia e-mail: kliknij pozycję **Ustawienia** i zdecyduj, czy chcesz otrzymywać pocztą e-mail powiadomienia o dostępie do dokumentu.

- Jeśli chcesz śledzić i odwoływać dokumenty udostępnione innym: administratorzy usługi Azure Information Protection mogą śledzić i odwoływać dokumenty dla innych użytkowników, klikając ikonę administratora. Ta ikona jest widoczna tylko dla administratorów.
    
    Uwaga: Jeśli nie widzisz tę ikonę, mimo iż administratora globalnego, jest ponieważ nie udostępniasz jeszcze żadnych dokumentów. W takim przypadku należy użyć następującego adresu URL dostęp do witryny śledzenia dokumentów: https://portal.azurerms.com/#/admin

-   Jeśli masz pytania lub chcesz wyrazić swoją opinię na temat witryny śledzenia dokumentów: kliknij ikonę Pomoc, aby uzyskać dostęp do artykułu [Często zadawane pytania dotyczące śledzenia dokumentów](http://go.microsoft.com/fwlink/?LinkId=523977).

## <a name="using-office-to-access-the-document-tracking-site"></a>Dostęp do witryny śledzenia dokumentów za pomocą pakietu Office

-   W przypadku aplikacji pakietu Office (Word, Excel i PowerPoint): na karcie **Narzędzia główne** w grupie **RMS** kliknij pozycję **Udostępnij chronione**, a następnie kliknij pozycję **Śledź użycie**.

    ![Śledzenie użycia z poziomu aplikacji pakietu Office w przypadku korzystania z aplikacji RMS sharing ](../media/ADRMS_MSRMSApp_OfficeToolbarTrackUsage.png)

-   W programie Outlook: na karcie **Narzędzia główne** w grupie **RMS** kliknij pozycję **Śledź użycie**:

    ![Wybierz opcję Śledź użycie w programie Outlook w przypadku korzystania z aplikacji RMS sharing ](../media/ADRMS_MSRMSApp_OutlookTrackUsage.png)

Jeśli te opcje usług RMS nie są wyświetlone, możliwe, że aplikacja RMS sharing nie jest zainstalowana na danym komputerze, nie zainstalowano najnowszej wersji albo trzeba ponownie uruchomić komputer w celu ukończenia instalacji. Aby uzyskać więcej informacji na temat sposobu instalowania aplikacji do udostępniania, zobacz [Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](install-sharing-app.md).

> [!NOTE] 
> Jeśli zainstalowano [klienta usługi Azure Information Protection](../rms-client/info-protect-client.md), możesz także uzyskać dostęp do witryny śledzenia dokumentów przy użyciu przycisku **Chroń**: 
> 
> - W aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** kliknij kolejno pozycje **Chroń** > **Śledź użycie**. 

### <a name="other-ways-to-track-and-revoke-your-documents"></a>Inne metody śledzenia i odwoływania dokumentów
Oprócz śledzenia dokumentów na komputerach z systemem Windows przy użyciu aplikacji pakietu Office można użyć także następujących alternatyw:

-   **W przeglądarce sieci Web**: ta metoda działa w przypadku wszystkich obsługiwanych urządzeń.

-   **W Eksploratorze plików**: ta metoda działa na komputerach z systemem Windows.

-   **W wiadomości e-mail programu Outlook**: ta metoda działa na komputerach z systemem Windows.

#### <a name="using-a-web-browser-to-access-the-doc-tracking-site"></a>Otwieranie witryny śledzenia dokumentów za pomocą przeglądarki sieci Web

-   Przy użyciu obsługiwanej przeglądarki przejdź do [witryny śledzenia dokumentów](http://go.microsoft.com/fwlink/?LinkId=529562).

    Obsługiwane przeglądarki: zaleca się korzystanie z przeglądarki Internet Explorer w wersji 10 lub nowszej, jednak dostęp do witryny śledzenia dokumentów można uzyskać przy użyciu dowolnej z poniższych przeglądarek:

    -   Internet Explorer: wersja 10 lub nowsza

    -   Internet Explorer 9 z poprawką MS12-037: zbiorcza aktualizacja zabezpieczeń programu Internet Explorer z 12 czerwca 2012 r.

    -   Mozilla Firefox: wersja 12 lub nowsza

    -   Apple Safari 5: wersja 5 lub nowsza

    -   Google Chrome: wersja 18 lub nowsza

#### <a name="using-file-explorer-to-access-the-doc-tracking-site"></a>Otwieranie witryny śledzenia dokumentów za pomocą Eksploratora plików

-   Kliknij plik prawym przyciskiem myszy, wybierz pozycję **Chroń za pomocą usługi RMS**, a następnie wybierz pozycję **Śledź użycie**:

    ![Wybierz opcję Śledź użycie w Eksploratorze w przypadku korzystania z aplikacji RMS sharing](../media/ADRMS_MSRMSApp_ExplorerTrackUsage.png)

#### <a name="using-an-outlook-email-message-to-access-the-doc-tracking-site"></a>Dostęp do witryny śledzenia dokumentów za pomocą wiadomości e-mail programu Outlook

-   W wiadomości e-mail na karcie **Wiadomość** w grupie **RMS** kliknij pozycję **Udostępnij chronioną zawartość**, a następnie kliknij pozycję **Śledź użycie**:

    ![Wybierz opcję Śledź użycie w programie Outlook w przypadku korzystania z aplikacji RMS sharing](../media/ADRMS_MSRMSApp_OutlookMessageTrackUsage.png)

## <a name="examples-and-other-instructions"></a>Przykłady i inne instrukcje
Aby uzyskać instrukcje i przykłady dotyczące korzystania z aplikacji do udostępniania usługi Rights Management, zapoznaj się z następującymi sekcjami podręcznika użytkownika aplikacji do udostępniania usługi Rights Management:

-   [Przykłady korzystania z aplikacji do udostępniania usługi RMS](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Co chcesz zrobić?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]