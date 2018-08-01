---
title: Aktywacja usługi Azure Rights Management — AIP
description: Konieczna jest aktywacja usługi Azure Rights Management, zanim Twoja organizacja będzie mogła rozpocząć chronienie dokumentów i wiadomości e-mail za pomocą aplikacji i usług, które obsługują to rozwiązanie do ochrony informacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/06/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 1471ba6a16abf2b227c709925a76a23e888f0b5b
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39372482"
---
# <a name="activating-azure-rights-management"></a>Aktywacja usługi Azure Rights Management

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!NOTE]
> Te informacje o konfiguracji są przeznaczone dla administratorów odpowiedzialnych za usługę mającą zastosowanie do wszystkich użytkowników w organizacji. Jeśli szukasz pomocy dla użytkowników i informacji na temat sposobu używania funkcji usługi Rights Management dla określonej aplikacji lub sposobu otwierania pliku lub wiadomości e-mail z ochroną praw, skorzystaj z pomocy i wskazówek dołączonych do aplikacji.
>
> Na przykład w przypadku aplikacji pakietu Office kliknij ikonę Pomoc i wprowadź terminy wyszukiwania, takie jak **Rights Management** lub **IRM**. Aby uzyskać instrukcje dotyczące klienta usługi Azure Information Protection dla komputerów z systemem Windows, zobacz [podręcznik użytkownika klienta usługi Azure Information Protection ](../rms-client/client-user-guide.md).
>
> Aby uzyskać pomoc techniczną oraz inne pytania dotyczące usługi, zobacz [opcje pomocy technicznej i zasoby społecznościowe](../get-started/information-support.md#support-options-and-community-resources) informacji.

Po aktywowaniu usługi Azure Rights Management dla usługi Azure Information Protection dla swojej organizacji Administratorzy i użytkownicy może rozpocząć chronienie ważnych danych za pomocą aplikacji i usług, które obsługują to rozwiązanie ochrony informacji. Administratorzy mogą również zarządzać i monitorować chronione dokumenty i wiadomości e-mail, które są własnością Twojej organizacji. 


## <a name="do-you-need-to-activate-azure-rights-management"></a>Czy należy aktywować usługę Azure Rights Management?

Jeśli masz plan usługi, która obejmuje usługę Azure Rights Management, możesz utracić aktywowania usługi:

- **Jeśli do końca lutego 2018 r. lub później uzyskano subskrypcję, która obejmuje usługę Azure Rights Management lub usługi Azure Information Protection:** usługi jest aktywowana automatycznie dla Ciebie. Nie masz aktywowanie usługi, chyba że użytkownik lub innego administratora globalnego Twojej organizacji dezaktywować usługę Azure Rights Management.

- **Jeśli uzyskano subskrypcję, która obejmuje usługę Azure Rights Management lub usługi Azure Information Protection, przed lub w trakcie lutego 2018 r.:** firmy Microsoft jest uruchamiana aktywować usługę Azure Rights Management dla tych subskrypcji, jeśli Twojej dzierżawy korzysta z usługi Exchange Online. Za te subskrypcje automatycznej aktywacji rozpoczyna wprowadzane do 1 sierpnia 2018 kiedy będzie można aktywować usługi dla Ciebie, chyba że zostanie wyświetlony **AutomaticServiceUpdateEnabled** ustawiono **false** po użytkownik Uruchom [Get-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/get-irmconfiguration?view=exchange-ps). 

Jeśli żadna z kolejnych scenariusze odnoszą się do Ciebie, możesz ręcznie aktywować usługę ochrony. 

Usługa została aktywowana, wszyscy użytkownicy w organizacji można zastosować ochronę informacji do swoich dokumentów i wiadomości e-mail, gdy każdy użytkownik może otworzyć (Używanie) dokumenty i wiadomości e-mail chronione za pomocą usługi Azure Rights Management. Jeśli jednak wolisz ograniczyć możliwość stosowania funkcji ochrony informacji, możesz określić, kto będzie z niej korzystać, stosując kontrolki dołączania we wdrożeniu etapowym. Aby uzyskać więcej informacji, zobacz sekcję [Konfigurowanie kontrolek dołączania we wdrożeniu etapowym](#configuring-onboarding-controls-for-a-phased-deployment) w tym artykule.

## <a name="how-to-activate-or-confirm-the-status-of-the-azure-rights-management-service"></a>Aktywacja i upewnij się, stan usługi Azure Rights Management 

> [!IMPORTANT]
> Jeśli masz Active Directory Rights Management Services (AD RMS) wdrożone w Twojej organizacji, nie aktywować usługi Azure Rights Management. [Więcej informacji](prepare-environment-adrms.md)

Aby użyć tego rozwiązania do ochrony danych, organizacja musi mieć plan usługi, która obejmuje usługę Azure Rights Management z usługi Azure Information Protection. Bez tego nie można aktywować usługę Azure Rights Management. Musi mieć jedną z następujących czynności:

- [Planu usługi Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) 

- [Planu usługi Office 365, obejmującego usługę Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Usługa Azure Rights Management została aktywowana, wszyscy użytkownicy w organizacji można zastosować ochronę informacji do swoich dokumentów i wiadomości e-mail, gdy każdy użytkownik może otworzyć (Używanie) dokumenty i wiadomości e-mail chronione za pomocą usługi Azure Rights Management Usługa. Jeśli jednak wolisz ograniczyć możliwość stosowania funkcji ochrony informacji, możesz określić, kto będzie z niej korzystać, stosując kontrolki dołączania we wdrożeniu etapowym. Aby uzyskać więcej informacji, zobacz sekcję [Konfigurowanie kontrolek dołączania we wdrożeniu etapowym](#configuring-onboarding-controls-for-a-phased-deployment) w tym artykule.

## <a name="choosing-your-activation-method"></a>Wybierając metodę aktywacji

Aby uzyskać instrukcje dotyczące aktywowania usługi Rights Management usługi z poziomu portalu zarządzania, wybierz, czy chcesz używać Centrum administracyjnego usługi Office 365 lub witryny Azure portal:

- [Centrum administracyjne usługi Office 365](activate-office365.md) -wymaga konta administratora globalnego

- [Witryna Azure portal](activate-azure.md) — nie wymaga konta administratora globalnego

Alternatywnie można użyć następujących poleceń programu PowerShell:

1. Zainstaluj w module AADRM, aby skonfigurować i zarządzać usługą ochrony. Aby uzyskać instrukcje, zobacz [Instalowanie modułu AADRM programu PowerShell](../deploy-use/install-powershell.md).

2. W sesji programu PowerShell, uruchom polecenie [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice)i po wyświetleniu monitu podaj szczegóły konta administratora globalnego dla dzierżawy usługi Azure Information Protection.

3. Uruchom [Get-Aadrm](/powershell/aadrm/vlatest/get-aadrm) aby upewnić się, czy usługa Azure Rights Management została aktywowana. Stan **włączone** potwierdza aktywacji; **Wyłączone** wskazuje dezaktywowaniu tej usługi.

4. Aby aktywować usługę, uruchom [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm).

## <a name="configuring-onboarding-controls-for-a-phased-deployment"></a>Konfigurowanie kontrolek dołączania we wdrożeniu etapowym
Jeśli nie chcesz, aby wszyscy użytkownicy mogli od razu chronić dokumenty i wiadomości e-mail przy użyciu usługi Azure Rights Management, można skonfigurować kontrolki dołączania użytkowników za pomocą [Set-AadrmOnboardingControlPolicy](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) polecenia programu PowerShell. To polecenie można uruchomić przed aktywacją usługi Azure Rights Management lub po niej.

> [!IMPORTANT]
> Aby użyć tego polecenia, musisz mieć co najmniej wersję **2.1.0.0** [modułu programu PowerShell usługi Azure Rights Management](https://go.microsoft.com/fwlink/?LinkId=257721).
>
> Aby sprawdzić zainstalowaną wersję, uruchom polecenie **(Get-Module aadrm –ListAvailable).Version**

Przykładowo jeśli chcesz, aby wstępnie tylko administratorzy w grupie „dział IT” (o identyfikatorze obiektu fbb99ded-32a0-45f1-b038-38b519009503) mogli chronić zawartość w celach testowych, użyj następującego polecenia:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fbb99ded-32a0-45f1-b038-38b519009503"
```

Zauważ, że w tej opcji konfiguracji musisz określić grupę; nie można określać poszczególnych użytkowników. Aby uzyskać identyfikator obiektu dla grupy, możesz użyć usługi Azure AD PowerShell — na przykład w przypadku wersji 1.0 modułu użyj polecenia [Get-MsolGroup](/powershell/msonline/v1/get-msolgroup). Możesz także skopiować wartość **identyfikatora obiektu** grupy z witryny Azure Portal.

Ewentualnie, jeśli chcesz się upewnić, że tylko użytkownicy prawidłowo licencjonowani do użycia usługi Azure Information Protection będą mogli chronić zawartość:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $True
```

Jeśli już nie musisz korzystać z kontrolek dołączania, bez względu na to, czy korzystano z grupy, czy z opcji licencjonowania, uruchom polecenie:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False
```

Aby uzyskać więcej informacji na temat tego polecenia cmdlet i dodatkowe przykłady, zobacz pomoc do polecenia [Set-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/set-aadrmonboardingcontrolpolicy).

Jeśli skorzystasz z tych kontrolek dołączania, wszyscy użytkownicy w organizacji zawsze będą mogli skorzystać z chronionej zawartości, która została zabezpieczona przez wybrany podzbiór użytkowników, ale nie będą mogli stosować własnoręcznie funkcji ochrony informacji za pośrednictwem aplikacji klienckich. Na przykład, nie będą widzieć w swoich aplikacjach pakietu Office domyślnych szablonów automatycznie publikowanych po aktywacji usługi Azure Rights Management lub szablonów niestandardowych, które można konfigurować. Aplikacje serwerowe, np. program Exchange, mogą wdrażać własne kontrolki dołączania dla integracji z usługą Rights Management, aby osiągnąć ten sam rezultat. Na przykład, aby uniemożliwić użytkownikom ochronę wiadomości e-mail w programie Outlook w sieci web, należy użyć [OwaMailboxPolicy zestaw](/powershell/module/exchange/client-access/set-owamailboxpolicy?view=exchange-ps) można ustawić *IRMEnabled* parametr *$false*.


## <a name="next-steps"></a>Kolejne kroki
Po aktywowaniu usługi Azure Rights Management dla swojej organizacji, użyj [planu wdrożenia usługi Azure Information Protection](../plan-design/deployment-roadmap.md) do sprawdzenia, czy istnieją inne czynności konfiguracyjne, które należy wykonać przed wdrożeniem Usługa Azure Information Protection dla użytkowników i administratorów. 

Na przykład możesz chcieć użyć [szablony](configure-policy-templates.md) aby ułatwić użytkownikom stosowanie ochrony informacji wobec plików, połączyć z serwerów lokalnych do użycia [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1.md)] , instalując [łącznika usługi Rights Management ](deploy-rms-connector.md)i wdrożyć [klienta Azure Information Protection](../rms-client/aip-client.md) , która obsługuje ochronę wszystkich typów plików na wszystkich urządzeniach. 

Usługi pakietu Office, np. Exchange Online i SharePoint Online, wymagają przeprowadzenia dodatkowej konfiguracji przed użyciem narzędzia Zarządzanie prawami do informacji (IRM). Aby uzyskać informacje o współdziałaniu aplikacji z usługą Rights Management, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md).


