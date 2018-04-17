---
title: Konfigurowanie usługi IRM programu Exchange Online dla usługi Azure Rights Management z usługi Azure Information Protection
description: Informacje i instrukcje dla administratorów skonfigurować usługę Exchange Online dla usługi Azure Rights Management dla dzierżawcy usługi Office 365 nie obsługuje nowe funkcje w szyfrowanie wiadomości usługi Office 365.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ''
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e452f5ac4e3297106a54a2034d64f57d8f6d5302
ms.sourcegitcommit: affda7572064edaf9e3b63d88f4a18d0d6932b13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="exchange-online-irm-configuration-to-import-a-trusted-publishing-domain"></a>Konfiguracja usługi IRM programu Exchange Online można zaimportować zaufaną domenę publikacji

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Użyj tych instrukcji, tylko wtedy, gdy dzierżawy nie będzie mógł korzystać z nowych funkcji szyfrowanie wiadomości usługi Office 365. Aby upewnić się, uruchom Exchange Online [Get-IRMConfiguration] (https://technet.microsoft.com/library/dd776120(v=exchg.160\)aspx) polecenia i zobacz, sprawdź, czy masz **AzureRMSLicensingEnabled** parametru. Jeśli widzisz ten parametr dzierżawy można użyć nowych funkcji szyfrowanie wiadomości usługi Office 365:

- Jeśli **AzureRMSLicensingEnabled** ustawiono **True**, dzierżawy już korzysta z nowych funkcji szyfrowanie wiadomości usługi Office 365 i nie należy używać zgodnie z instrukcjami w następnej sekcji.

- Jeśli **AzureRMSLicensingEnabled** ustawiono **False**, dzierżawy obsługuje nowe funkcje szyfrowanie wiadomości usługi Office 365, ale nie został jeszcze skonfigurowany w tym celu. Aby skonfigurować dzierżawy dla nowych funkcji, zobacz [skonfigurować nowe możliwości szyfrowanie wiadomości usługi Office 365, rozszerzający usługi Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). 

Tylko wtedy, gdy dzierżawy nie obsługuje nowe funkcje szyfrowanie wiadomości usługi Office 365, użyj postępuj zgodnie z instrukcjami.

## <a name="exchange-online-irm-configuration"></a>Konfiguracja usługi IRM programu Exchange Online

Aby skonfigurować usługi IRM programu Exchange Online, należy użyć programu Windows PowerShell (nie trzeba instalować oddzielnego modułu) i uruchom [poleceń programu PowerShell dla usługi Exchange Online](https://technet.microsoft.com/library/jj200677.aspx).

> [!NOTE]
> Dopóki Microsoft migruje dzierżawy usługi Office 365 w celu obsługi nowych funkcji, nie można skonfigurować usługi Exchange Online do obsługi usługi Azure Rights Management, jeśli używasz klucza dzierżawy zarządzanego przez klienta (BYOK) dla usługi Azure Information Protection, a nie niż domyślna konfiguracja klucz dzierżawy zarządzany przez firmę Microsoft.
>
> Jeśli próbujesz skonfigurować usługę Exchange Online, a usługa Azure Rights Management korzysta z rozwiązania BYOK, działanie polecenia importowania klucza (krok 5 poniższej procedury) zakończy się niepowodzeniem z powodu błędu **[FailureCategory=Cmdlet-FailedToGetTrustedPublishingDomainFromRmsOnlineException]**.

W poniższych krokach przedstawiono typowy zestaw poleceń, które należy uruchomić, aby włączyć usługi IRM programu Exchange Online:

1.  Jeśli używasz programu Windows PowerShell dla usługi Exchange Online na komputerze po raz pierwszy, musisz skonfigurować program Windows PowerShell do uruchamiania podpisanych skryptów. Uruchom sesję programu Windows PowerShell przy użyciu opcji **Uruchom jako administrator**, a następnie wpisz:

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

2.  W sesji programu Windows PowerShell zaloguj się do usługi Exchange Online przy użyciu konta z włączoną opcją zdalnego dostępu do programu PowerShell. Domyślnie wszystkie konta tworzone w usłudze Exchange Online mają włączoną opcję zdalnego dostępu do programu PowerShell, ale można ją wyłączyć (i włączyć) przy użyciu polecenia [Set-User &lt;TożsamośćUżytkownika&gt; -RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx).

    Aby się zalogować, wpisz:

    ```
    $UserCredential = Get-Credential
    ```
    W oknie dialogowym **Żądanie poświadczeń programu Windows PowerShell** podaj nazwę użytkownika i hasło do usługi Office 365.

3.  Połącz się z usługą Exchange Online, uruchamiając następujące dwa polecenia:

    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    ```
    Import-PSSession $Session
    ```

4.  Określ lokalizację klucza dzierżawy usługi Azure Information Protection na podstawie położenia organizacji, w której utworzono dzierżawę:

    Dla Ameryki Północnej:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Dla Europy:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Azja:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Ameryka Południowa:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Usługa Office 365 Government (chmura społecznościowa dla instytucji rządowych):

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc"
    ```

5.  Zaimportuj dane konfiguracji z usługi Azure Rights Management do usługi Exchange Online w formie zaufanej domeny publikacji (TPD, Trusted Publishing Domain). Dane te obejmują klucz dzierżawy usługi Azure Information Protection i szablony usługi Azure Rights Management:

    ```
    Import-RMSTrustedPublishingDomain -RMSOnline -name "RMS Online"
    ```
    W tym poleceniu użyliśmy nazwy **RMS Online** jako podstawowej nazwy zaufanej domeny publikacji usługi Azure Rights Management w usłudze Exchange Online. Zaimportowana zaufana domena publikacji będzie w usłudze Exchange Online nosić nazwę **RMS Online — 1**.

6.  Włącz funkcjonalność usługi Azure Rights Management, aby funkcje IRM były dostępne w usłudze Exchange Online:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $true
    ```
    Po uruchomieniu tego polecenia usługa Rights Management będzie automatycznie włączona dla klienta programu Outlook, aplikacji Outlook Web App i programu Exchange ActiveSync.

7.  Opcjonalnie można sprawdzić, czy ta konfiguracja działa prawidłowo, używając następującego polecenia:

    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    Na przykład: **Test-IRMConfiguration -Sender  adams@contoso.com**

    To polecenie umożliwia uruchomienie serii testów obejmujących sprawdzanie połączenia z usługą, pobieranie konfiguracji oraz pobieranie identyfikatorów URI, licencji i dowolnych szablonów. W sesji programu Windows PowerShell będą widoczne wyniki wszystkich testów, a na koniec — jeśli testy zakończą się pomyślnie — zostanie wyświetlona informacja **WYNIK OGÓLNY: POZYTYWNY**.

8.  Rozłącz zdalną sesję programu PowerShell:

    ```
    Remove-PSSession $Session
    ```

Użytkownicy mogą teraz chronić swoje wiadomości e-mail za pomocą usługi Azure Rights Management. Na przykład w aplikacji Outlook Web App wybierz **ustawić uprawnienia** z menu rozszerzonego (**...** ), a następnie wybierz pozycję **nie przesyłaj dalej** lub jeden z dostępnych szablonów, aby zastosować ochronę informacji do wiadomości e-mail i załączniki. Jednak ze względu na to, że buforowanie interfejsu użytkownika w aplikacji Outlook Web App trwa cały dzień, przed podjęciem próby zastosowania ochrony wiadomości e-mail i po uruchomieniu poleceń konfiguracji zaczekaj, aż ten czas minie. Dopóki aktualizacje interfejsu użytkownika nie odzwierciedlą nowej konfiguracji, żadne opcje menu **Ustaw uprawnienia** nie będą widoczne.

> [!IMPORTANT]
> W przypadku tworzenia nowych [szablonów niestandardowych](configure-custom-templates.md) dla usługi Azure Rights Management lub aktualizacji szablonów za każdym razem musisz uruchomić następujące polecenie programu Exchange Online PowerShell (w razie potrzeby wykonaj najpierw kroki 2 i 3), aby zsynchronizować te zmiany w usłudze Exchange Online: `Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates –RMSOnline`

Jako administrator programu Exchange możesz teraz skonfigurować funkcje, które umożliwiają automatyczne stosowanie ochrony informacji, takie jak [reguły transportu](https://technet.microsoft.com/library/dd302432.aspx), [zasady zapobiegania utracie danych (DLP)](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) i [chroniona poczta głosowa](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (Unified Messaging).


### <a name="office-365-message-encryption"></a>Szyfrowanie wiadomości usługi Office 365
Uruchom te same kroki, zgodnie z opisem w poprzedniej sekcji, ale jeśli nie chcesz wyświetlać, przed wykonaniem kroku 6, uruchom następujące polecenie, aby uniemożliwić szablonów funkcji IRM dostępne w programie Outlook Web App i kliencie programu Outlook szablonów: `Set-IRMConfiguration -ClientAccessServerEnabled $false`

Teraz możesz skonfigurować [reguły transportu](https://technet.microsoft.com/library/dd302432.aspx), aby zabezpieczenia wiadomości były automatycznie modyfikowane, jeśli odbiorcy znajdują się poza organizacją. Następnie wybierz opcję **Zastosuj szyfrowanie wiadomości usługi Office 365**.

Aby uzyskać więcej informacji na temat szyfrowania wiadomości, zobacz [Szyfrowanie w usłudze Office 365](https://technet.microsoft.com/library/dn569286.aspx) w bibliotece programu Exchange.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
