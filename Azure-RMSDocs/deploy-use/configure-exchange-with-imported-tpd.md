---
title: "Konfigurowanie usługi IRM programu Exchange Online dla usługi Azure Rights Management z usługi Azure Information Protection"
description: "Informacje i instrukcje dla administratorów skonfigurować usługę Exchange Online dla usługi Azure Rights Management dla dzierżawcy usługi Office 365 nie obsługuje nowe funkcje w szyfrowanie wiadomości usługi Office 365."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/22/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a0c6fe7f7b6a34eea21b646ce5573ca03b13be3c
ms.sourcegitcommit: cd3320fa34acb90f05d5d3e0e83604cdd46bd9a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2017
---
# <a name="exchange-online-irm-configuration-when-you-have-imported-a-trusted-publishing-domain"></a>Konfiguracja usługi IRM programu Exchange Online w przypadku zaimportowano zaufaną domenę publikacji

>*Dotyczy: Azure Information Protection, Office 365*

Użyj tych instrukcji, tylko jeśli wcześniej skonfigurowano usługi Exchange Online dla usługi IRM importując zaufaną domenę publikacji (TPD) i muszą mieć możliwość odszyfrowywania wiadomości e-mail, które wcześniej były szyfrowane.

Jeśli żadna z tych warunków nie odnoszą się do Ciebie, nie używasz tych instrukcji i zamiast tego należy użyć instrukcji z [skonfigurować nowe możliwości szyfrowanie wiadomości usługi Office 365, rozszerzający usługi Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e).

## <a name="exchange-online-irm-configuration-if-you-have-an-imported-tpd"></a>Konfiguracji usługi IRM programu Exchange Online, jeśli masz importowanych zaufanej domeny publikacji

Aby skonfigurować usługę Exchange Online do obsługi usługi Azure Rights Management, należy skonfigurować usługę zarządzania prawami do informacji (IRM) dla usługi Exchange Online. W tym celu należy użyć programu Windows PowerShell (nie trzeba instalować oddzielnego modułu) i uruchomić [polecenia programu PowerShell dla usługi Exchange Online](https://technet.microsoft.com/library/jj200677.aspx).

> [!NOTE]
> Dopóki Microsoft migruje dzierżawy usługi Office 365, nie można skonfigurować usługi Exchange Online do obsługi usługi Azure Rights Management, jeśli używasz klucza dzierżawy zarządzanego przez klienta (BYOK) dla usługi Azure Information Protection, a nie w konfiguracji domyślnej Klucz dzierżawy zarządzany przez firmę Microsoft.
>
> Jeśli próbujesz skonfigurować usługę Exchange Online, a usługa Azure Rights Management korzysta z rozwiązania BYOK, działanie polecenia importowania klucza (krok 5 poniższej procedury) zakończy się niepowodzeniem z powodu błędu **[FailureCategory=Cmdlet-FailedToGetTrustedPublishingDomainFromRmsOnlineException]**.

W poniższych krokach przedstawiono typowy zestaw poleceń, które należy uruchomić, aby umożliwić usłudze Exchange Online do korzystania z usługi Azure Rights Management dla tego scenariusza:

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
Uruchom te same kroki, zgodnie z opisem w poprzedniej sekcji, ale jeśli nie chcesz wyświetlać, przed wykonaniem kroku 6, uruchom następujące polecenie, aby uniemożliwić szablonów funkcji IRM dostępne w programie Outlook Web App i kliencie programu Outlook szablonów:`Set-IRMConfiguration -ClientAccessServerEnabled $false`

Teraz możesz skonfigurować [reguły transportu](https://technet.microsoft.com/library/dd302432.aspx), aby zabezpieczenia wiadomości były automatycznie modyfikowane, jeśli odbiorcy znajdują się poza organizacją. Następnie wybierz opcję **Zastosuj szyfrowanie wiadomości usługi Office 365**.

Aby uzyskać więcej informacji na temat szyfrowania wiadomości, zobacz [Szyfrowanie w usłudze Office 365](https://technet.microsoft.com/library/dn569286.aspx) w bibliotece programu Exchange.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
