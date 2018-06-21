---
title: Wdrażanie łącznika usługi Rights Management — AIP
description: Instrukcje dotyczące wdrażania łącznika usług RMS, który udostępnia usługę ochrony danych dla istniejących wdrożeń lokalnych korzystających z programu Exchange Server, programu SharePoint Server lub systemu Windows Server oraz funkcji infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 90e7e33f-9ecc-497b-89c5-09205ffc5066
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: c49306a731bf629f3678dc9aa95b23b8ee46190e
ms.sourcegitcommit: 373e05ff0c411d29cc5b61c36edaf5a203becc14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217026"
---
# <a name="deploying-the-azure-rights-management-connector"></a>Wdrażanie łącznika usługi Azure Rights Management

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, w systemie Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Poniżej przedstawiono informacje dotyczące łącznika usługi Azure Rights Management i sposobu jego pomyślnego wdrażania w organizacji. Ten łącznik służy do zapewniania ochrony danych w istniejących wdrożeniach lokalnych korzystających z programu **Microsoft Exchange Server**, **SharePoint Server** lub serwerów plików, na których uruchomiony jest system Windows Server i które używają funkcji **infrastruktury klasyfikacji plików** (FCI, File Classification Infrastructure).


## <a name="overview-of-the-microsoft-rights-management-connector"></a>Łącznik usługi Microsoft Rights Management — omówienie
Łącznik usługi Microsoft Rights Management (RMS) pozwala szybko włączyć na istniejących serwerach lokalnych funkcjonalność zarządzania prawami do informacji (IRM, Information Rights Management) za pomocą opartej na chmurze usługi Microsoft Rights Management (usługa Azure RMS). Dzięki tej funkcji dział IT i użytkownicy mogą łatwo chronić dokumenty i obrazy zarówno wewnątrz organizacji, jak i poza nią, bez konieczności instalowania dodatkowej infrastruktury lub ustanawiania relacji zaufania z innymi organizacjami. 

Łącznik usług RMS jest zajmującą niewiele pamięci usługą instalowaną lokalnie na serwerach z systemem Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 lub Windows Server 2008 R2. Poza uruchamianiem łącznika na komputerach fizycznych można go również uruchomić na maszynach wirtualnych, w tym na maszynach wirtualnych Azure IaaS Po wdrożeniu łącznik działa jako interfejs komunikacji (przekaźnik) między serwerami lokalnymi i usługą w chmurze, jak przedstawiono na poniższej ilustracji. Strzałki wskazują kierunek inicjowania połączeń sieciowych.

![Architektura łącznika usługi RMS — omówienie](../media/RMS_connector.png)


### <a name="on-premises-servers-supported"></a>Obsługa serwerów lokalnych

Łącznik usługi RMS obsługuje następujące serwery lokalne: Exchange Server, SharePoint Server i serwery plików działające pod kontrolą systemu operacyjnego Windows Server i używające funkcji infrastruktury klasyfikacji plików do klasyfikowania oraz stosowania zasad do dokumentów pakietu Office w folderze. 

> [!NOTE]
> Aby chronić przy użyciu infrastruktury klasyfikacji plików wiele typów plików, a nie tylko dokumenty pakietu Office, zamiast łącznika usług RMS należy używać [poleceń cmdlet usługi Azure Information Protection](/powershell/azureinformationprotection/vlatest/aip).

Wersje tych serwerów lokalnych obsługiwane przez łącznik usług RMS można znaleźć w sekcji [Serwery lokalne, które obsługują usługi Azure RMS](..\get-started\requirements-servers.md).


### <a name="support-for-hybrid-scenarios"></a>Obsługa scenariuszy hybrydowych

Można użyć łącznika usług RMS nawet w przypadku, gdy niektórzy użytkownicy są podłączeni do usług online w scenariuszu hybrydowym. Na przykład skrzynki pocztowe niektórych użytkowników korzystają z usługi Exchange Online, podczas gdy skrzynki pocztowe innych użytkowników korzystają z programu Exchange Server. Po zainstalowaniu łącznika usługi RMS wszyscy użytkownicy mogą chronić informacje oraz korzystać z wiadomości e-mail i załączników za pomocą usługi Azure RMS, podczas gdy ochrona informacji współpracuje płynnie z dwiema konfiguracjami wdrożenia.

### <a name="support-for-customer-managed-keys-byok"></a>Obsługa kluczy zarządzanych przez klienta (BYOK)

Jeśli zarządzasz własnym kluczem dzierżawy dla usług Azure RMS (scenariusz z użyciem własnego klucza — BYOK), łącznik usług RMS i serwery lokalne, które go używają, nie uzyskują dostępu do modułu HSM zawierającego Twój klucz dzierżawy. Jest to spowodowane tym, że wszystkie operacje kryptograficzne, które używają klucza dzierżawy, są wykonywane w ramach usługi Azure RMS, a nie lokalnie.

Jeśli chcesz dowiedzieć się więcej na temat tego scenariusza, w którym można zarządzać z kluczem dzierżawy, zobacz [planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design\plan-implement-tenant-key.md).

## <a name="prerequisites-for-the-rms-connector"></a>Wymagania wstępne dotyczące łącznika usługi RMS
Przed zainstalowaniem łącznika usługi RMS upewnij się, że zostały spełnione następujące wymagania.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Usługa Rights Management (RMS) została aktywowana|[Aktywacja usługi Azure Rights Management](activate-service.md)|
|Synchronizacja katalogu lokalnych lasów usługi Active Directory i usługi Azure Active Directory|Po uaktywnieniu usługi RMS usługa Azure Active Directory musi być skonfigurowana do pracy z użytkownikami i grupami w bazie danych usługi Active Directory użytkownika.<br /><br />**Ważne**: Ten krok synchronizacji katalogu należy wykonać dla zapewnienia działania łącznika usługi RMS, nawet w przypadku sieci testowej. Chociaż z usługi Office 365 i usługi Azure Active Directory można korzystać przy użyciu kont, które zostały ręcznie utworzone w usłudze Azure Active Directory, ten łącznik wymaga synchronizacji kont w usłudze Azure Active Directory z Usługami domenowymi Active Directory. Ręczna synchronizacja haseł nie jest wystarczająca.<br /><br />Więcej informacji można znaleźć w następujących zasobach:<br /><br />[Integrowanie tożsamości użytkownika lokalnego z usługą Azure Active Directory](/active-directory/active-directory-aadconnect)<br /><br />[Porównanie narzędzi integracji katalogu tożsamości hybrydowej](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison)|
|Co najmniej dwa komputery członkowskie, na których zostanie zainstalowany łącznik usług RMS:<br /><br />– 64-bitowy komputer fizyczny lub wirtualny działający pod kontrolą jednego z następujących systemów operacyjnych: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 lub Windows Server 2008 R2.<br /><br />– Co najmniej 1 GB pamięci RAM.<br /><br />– Co najmniej 64 GB miejsca na dysku.<br /><br />– Co najmniej jeden interfejs sieciowy.<br /><br />– Dostęp do Internetu za pośrednictwem zapory (lub serwera proxy sieci Web), która nie wymaga uwierzytelniania.<br /><br />– Musi należeć do lasu lub domeny, które ufają innym lasom w organizacji, zawierającym instalacje serwerów programu Exchange lub SharePoint przeznaczone do użycia z łącznikiem usługi RMS.|W celu zachowania odporności na uszkodzenia i wysokiej dostępności łącznik usług RMS należy zainstalować na co najmniej dwóch komputerach.<br /><br />**Porada**: Jeśli używasz programu Outlook Web Access lub urządzeń przenośnych, które korzystają z programu Exchange ActiveSync IRM, a szczególnie ważne jest, by utrzymywać dostęp do wiadomości e-mail i załączników chronionych za pomocą usługi Azure RMS, zalecamy wdrożenie grupy serwerów łącznika z funkcją równoważenia obciążenia dla zapewnienia wysokiej dostępności.<br /><br />Do uruchomienia łącznika nie są potrzebne dedykowane serwery, ale musi on zostać zainstalowany na innym komputerze niż serwery używające łącznika.<br /><br />**Ważne**: Nie instaluj łącznika na komputerze z systemem Exchange Server, SharePoint Server ani na serwerze plików skonfigurowanym dla funkcji infrastruktury klasyfikacji plików, jeśli chcesz skorzystać z funkcjonalności tych usług za pomocą usługi Azure RMS. Ponadto nie należy instalować tego łącznika na kontrolerze domeny.<br /><br />Jeśli masz obciążeń serwera, które mają być używane dla łącznika usługi RMS, ale swoich serwerów znajdują się w domenach, które nie są zaufane domeny, z którego chcesz uruchomić łącznik można zainstalować dodatkowe serwery łącznika usługi RMS w tych niezaufanych domenach lub innych domen w lesie, ich. <br /><br />Nie ma żadnego limitu liczby serwerów łącznika, które można uruchomić w Twojej organizacji i wszystkie serwery łącznika zainstalowane udziału organizacji w tej samej konfiguracji. Jednak do konfigurowania łącznika do autoryzowania serwerów należy mogą przeglądać dla konta serwera lub usługi, które chcesz autoryzować, co oznacza, że należy uruchomić narzędzie administracyjne usług RMS w lesie, w którym można przeglądać w tych kont.|


## <a name="steps-to-deploy-the-rms-connector"></a>Procedura wdrażania łącznika usług RMS

Łącznik nie jest sprawdzana automatycznie wszystkie [wymagania wstępne](deploy-rms-connector.md#prerequisites-for-the-rms-connector) wymagane do pomyślnego wdrożenia, dlatego należy upewnić się, że są one w miejscu przed rozpoczęciem. Wdrożenie wymaga instalacji łącznika, skonfigurowania łącznika, a następnie skonfigurowania serwerów, które mają być używane z łącznikiem. 

-   **Krok 1.**  [Instalowanie łącznika usług RMS](install-configure-rms-connector.md#installing-the-rms-connector)

-   **Krok 2.**  [Wprowadzanie poświadczeń](install-configure-rms-connector.md#entering-credentials)

-   **Krok 3.**  [Autoryzowanie serwerów do korzystania z łącznika usługi RMS](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector)

-   **Krok 4.**  [Konfigurowanie funkcji równoważenia obciążenia i wysokiej dostępności](install-configure-rms-connector.md#configuring-load-balancing-and-high-availability)

-   Opcjonalnie: [Konfigurowanie łącznika usługi RMS do obsługi protokołu HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https)

-   Opcjonalnie: [Konfigurowanie łącznika usługi RMS dla serwera proxy sieci web](install-configure-rms-connector.md#configuring-the-rms-connector-for-a-web-proxy-server)

-   Opcjonalnie: [Instalowanie narzędzia administracyjnego łącznika usługi RMS na komputerach administracyjnych](install-configure-rms-connector.md#installing-the-rms-connector-administration-tool-on-administrative-computers)

-   **Krok 5.**  [Konfigurowanie serwerów do korzystania z łącznika usługi RMS](configure-servers-rms-connector.md)

    -   [Konfigurowanie serwera programu Exchange do używania łącznika](configure-servers-rms-connector.md#configuring-an-exchange-server-to-use-the-connector)

    -   [Konfigurowanie serwera programu SharePoint do używania łącznika](configure-servers-rms-connector.md#configuring-a-sharepoint-server-to-use-the-connector)

    -   [Konfigurowanie serwera plików dla funkcji infrastruktury klasyfikacji plików do używania łącznika](configure-servers-rms-connector.md#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)


## <a name="next-steps"></a>Następne kroki

Przejdź do kroku 1: [Instalowanie i konfigurowanie łącznika usługi Azure Rights Management](install-configure-rms-connector.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]