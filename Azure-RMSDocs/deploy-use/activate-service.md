---
title: "Aktywacja usługi Azure Rights Management — AIP"
description: "Konieczna jest aktywacja usługi Azure Rights Management, zanim Twoja organizacja będzie mogła rozpocząć chronienie dokumentów i wiadomości e-mail za pomocą aplikacji i usług, które obsługują to rozwiązanie do ochrony informacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 771c94825a8d63feb20985ccdf304e370ec1dc65
ms.sourcegitcommit: 31c79d948ec3089a4dc65639f1842c07c7aecba6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2018
---
# <a name="activating-azure-rights-management"></a>Aktywacja usługi Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

> [!NOTE]
> Te informacje o konfiguracji są przeznaczone dla administratorów odpowiedzialnych za usługę mającą zastosowanie do wszystkich użytkowników w organizacji. Jeśli szukasz pomocy dla użytkowników i informacji na temat sposobu używania funkcji usługi Rights Management dla określonej aplikacji lub sposobu otwierania pliku lub wiadomości e-mail z ochroną praw, skorzystaj z pomocy i wskazówek dołączonych do aplikacji.
>
> Na przykład w przypadku aplikacji pakietu Office kliknij ikonę Pomoc i wprowadź terminy wyszukiwania, takie jak **Rights Management** lub **IRM**. Aby uzyskać instrukcje dotyczące klienta usługi Azure Information Protection dla komputerów z systemem Windows, zobacz [podręcznik użytkownika klienta usługi Azure Information Protection ](../rms-client/client-user-guide.md).
>
> Aby uzyskać pomoc techniczną oraz inne pytania dotyczące usługi, zobacz [opcje pomocy technicznej i zasoby społecznościowe](../get-started/information-support.md#support-options-and-community-resources) informacji.

Po aktywowaniu usługi Azure Rights Management dla usługi Azure Information Protection dla Twojego dzierżawcy Twoja organizacja może rozpocząć chronienie istotnych danych za pomocą aplikacji i usług, które obsługują to rozwiązanie do ochrony informacji. Administratorzy mogą również zarządzać chronionymi plikami i wiadomościami e-mail organizacji oraz monitorować je. Należy włączyć tę usługę przed rozpoczęciem korzystania z funkcji zarządzania prawami do informacji (IRM, information rights management) w pakiecie Office, programie SharePoint i programie Exchange oraz przystąpieniem do ochrony wszelkich poufnych plików.

Jeśli chcesz dowiedzieć się więcej na temat usługi Azure Rights Management przed jej aktywowaniem — na przykład, jakie problemy biznesowe rozwiązuje go, niektóre typowe zastosowania i jak działa — zobacz [co to jest usługa Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Usługa Azure Rights Management nie zostanie aktywowany, jeśli masz Active Directory Rights Management Services (AD RMS) wdrożone w Twojej organizacji. [Więcej informacji](prepare-environment-adrms.md)

Przed aktywacją usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] upewnij się, że Twoja organizacja ma plan subskrypcji obejmujący ochronę danych w usłudze Azure Rights Management. Jeśli nie ma, nie będzie można aktywować usługi Azure Rights Management. Musi mieć jedną z następujących czynności:

- [Plan usługi Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) 

- [Planu usługi Office 365, obejmującego usługę Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Po uaktywnieniu usługi Azure RMS wszyscy użytkownicy w organizacji mogą stosować funkcje ochrony informacji wobec swoich plików oraz otwierać pliki (korzystać z nich) chronione przez usługę Azure Rights Management. Jeśli jednak wolisz ograniczyć możliwość stosowania funkcji ochrony informacji, możesz określić, kto będzie z niej korzystać, stosując kontrolki dołączania we wdrożeniu etapowym. Aby uzyskać więcej informacji, zobacz sekcję [Konfigurowanie kontrolek dołączania we wdrożeniu etapowym](#configuring-onboarding-controls-for-a-phased-deployment) w tym artykule.

## <a name="choosing-your-activation-method"></a>Wybieranie metodę aktywacji

Aby uzyskać instrukcje jak aktywować praw usługi zarządzania w portalu zarządzania wybierz, czy za pomocą Centrum administracyjnego usługi Office 365 lub portalu Azure:

- [Centrum administracyjne usługi Office 365](activate-office365.md) -wymaga konta administratora globalnego

- [Azure portal](activate-azure.md) — nie wymaga konta administratora globalnego

Możesz również użyć programu PowerShell do aktywacji usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]:

1. Zainstaluj moduł AADRM do konfigurowania i zarządzania usługi ochrony. Aby uzyskać instrukcje, zobacz [Instalowanie modułu programu PowerShell AADRM](../deploy-use/install-powershell.md).

2. W sesji programu PowerShell, uruchom [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice)i po wyświetleniu monitu podaj szczegóły konta administratora globalnego dla dzierżawy usługi Azure Information Protection.

3. Uruchom polecenie [Enable-Aadrm](/powershell/module/aadrm/enable-aadrm), które aktywuje usługę Azure Rights Management.

## <a name="configuring-onboarding-controls-for-a-phased-deployment"></a>Konfigurowanie kontrolek dołączania we wdrożeniu etapowym
Jeśli nie chcesz, aby wszyscy użytkownicy mogli od razu chronić pliki za pomocą usługi Azure Rights Management, możesz skonfigurować kontrolki dołączania użytkowników, korzystając z polecenia [Set-AadrmOnboardingControlPolicy](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) programu PowerShell. To polecenie można uruchomić przed aktywacją usługi Azure Rights Management lub po niej.

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

Jeśli skorzystasz z tych kontrolek dołączania, wszyscy użytkownicy w organizacji zawsze będą mogli skorzystać z chronionej zawartości, która została zabezpieczona przez wybrany podzbiór użytkowników, ale nie będą mogli stosować własnoręcznie funkcji ochrony informacji za pośrednictwem aplikacji klienckich. Przykładowo nie będą widzieć w swoich klientach pakietu Office domyślnych szablonów automatycznie publikowanych po aktywacji usługi Azure Rights Management lub skonfigurowanych szablonów niestandardowych.  Aplikacje serwerowe, np. program Exchange, mogą wdrażać własne kontrolki dołączania dla integracji z usługą Rights Management, aby osiągnąć ten sam rezultat.


## <a name="next-steps"></a>Następne kroki
Po aktywowaniu usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] dla Twojej organizacji możesz użyć [planu wdrożenia usługi Azure Information Protection](../plan-design/deployment-roadmap.md), aby sprawdzić, czy istnieją czynności konfiguracyjne, które należy wykonać przed wdrożeniem usługi Azure Information Protection dla użytkowników i administratorów. 

Na przykład możesz chcieć użyć [szablony](configure-policy-templates.md) aby ułatwić użytkownikom stosowanie ochrony informacji wobec plików, połączyć serwerów lokalnych do użycia [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] instalując [łącznik usługi Rights Management](deploy-rms-connector.md)i wdrażanie [klienta Azure Information Protection](../rms-client/aip-client.md) obsługującej ochronę wszystkich typów plików na wszystkich urządzeniach. 

Usługi pakietu Office, np. Exchange Online i SharePoint Online, wymagają przeprowadzenia dodatkowej konfiguracji przed użyciem narzędzia Zarządzanie prawami do informacji (IRM). Aby uzyskać informacje o współdziałaniu aplikacji z usługą Rights Management, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
