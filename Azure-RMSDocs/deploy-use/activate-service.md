---
title: "Aktywacja usługi Azure Rights Management | Azure Information Protection"
description: "Konieczna jest aktywacja usługi Azure Rights Management, zanim Twoja organizacja będzie mogła rozpocząć chronienie dokumentów i wiadomości e-mail za pomocą aplikacji i usług, które obsługują to rozwiązanie do ochrony informacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/09/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 84072c64f83ec97ac41d6ec030be5eabff263b4b
ms.openlocfilehash: 51bc2c66cfce9f50b0d876fb1066d740f570d27d


---

# <a name="activating-azure-rights-management"></a>Aktywacja usługi Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

Po aktywowaniu usługi Azure Rights Management dla usługi Azure Information Protection Twoja organizacja może rozpocząć chronienie istotnych danych za pomocą aplikacji i usług, które obsługują to rozwiązanie do ochrony informacji. Administratorzy mogą również zarządzać chronionymi plikami i wiadomościami e-mail organizacji oraz monitorować je. Należy włączyć tę usługę przed rozpoczęciem korzystania z funkcji zarządzania prawami do informacji (IRM, information rights management) w pakiecie Office, programie SharePoint i programie Exchange oraz przystąpieniem do ochrony wszelkich poufnych plików.

Jeśli chcesz dowiedzieć się więcej na temat usługi Azure Rights Management przed jej aktywowaniem — na przykład o tym, jakie problemy biznesowe rozwiązuje, jak działa i jakie są jej przykładowe, typowe zastosowania — zobacz [Co to jest usługa Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Przed aktywacją usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] upewnij się, że Twoja organizacja ma plan subskrypcji obejmujący ochronę danych w usłudze Azure Rights Management. Jeśli nie ma, nie będzie można aktywować usługi Azure Rights Management.
>
> Potrzebujesz [planu usługi Azure Information Protection Premium](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) lub [planu usługi Office 365 obejmującego usługę Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Po uaktywnieniu usługi Azure RMS wszyscy użytkownicy w organizacji mogą stosować funkcje ochrony informacji wobec swoich plików oraz otwierać pliki (korzystać z nich) chronione przez usługę Azure Rights Management. Jeśli jednak wolisz ograniczyć możliwość stosowania funkcji ochrony informacji, możesz określić, kto będzie z niej korzystać, stosując kontrolki dołączania we wdrożeniu etapowym. Aby uzyskać więcej informacji, zobacz sekcję [Konfigurowanie kontrolek dołączania we wdrożeniu etapowym](#configuring-onboarding-controls-for-a-phased-deployment) w tym artykule.

Aby uzyskać instrukcje dotyczące aktywowania usługi Rights Management z poziomu portalu zarządzania, wybierz, czy będziesz używać centrum administracyjnego usługi Office 365 (wersja zapoznawcza lub klasyczna), czy klasycznego portalu zarządzania platformy Azure:


- [Centrum administracyjne usługi Office 365 — wersja zapoznawcza](activate-office365-preview.md)
- [Centrum administracyjne usługi Office 365 — wersja klasyczna](activate-office365-classic.md)
- [Klasyczny portal Azure](activate-azure-classic.md)

Możesz również użyć programu PowerShell do aktywacji usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]:

1. Zainstaluj narzędzie Azure Rights Management Administration Tool, które instaluje moduł administracyjny usługi Azure Rights Management. Instrukcje znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

2. W sesji programu PowerShell uruchom polecenie [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) i po wyświetleniu odpowiedniego monitu podaj szczegóły konta administratora globalnego dla dzierżawy usługi Azure Information Protection.

3. Uruchom polecenie [Enable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx), które aktywuje usługę Azure Rights Management.

## <a name="configuring-onboarding-controls-for-a-phased-deployment"></a>Konfigurowanie kontrolek dołączania we wdrożeniu etapowym
Jeśli nie chcesz, aby wszyscy użytkownicy mogli od razu chronić pliki za pomocą usługi Azure Rights Management, możesz skonfigurować kontrolki dołączania użytkowników, korzystając z polecenia [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) programu PowerShell. To polecenie można uruchomić przed aktywacją usługi Azure Rights Management lub po niej.

> [!IMPORTANT]
> Aby użyć tego polecenia, musisz mieć co najmniej wersję **2.1.0.0** [modułu programu PowerShell usługi Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721).
>
> Aby sprawdzić zainstalowaną wersję, uruchom polecenie **(Get-Module aadrm –ListAvailable).Version**

Przykładowo jeśli chcesz, aby wstępnie tylko administratorzy w grupie „dział IT” (o identyfikatorze obiektu fbb99ded-32a0-45f1-b038-38b519009503) mogli chronić zawartość w celach testowych, użyj następującego polecenia:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Zauważ, że w tej opcji konfiguracji musisz określić grupę; nie można określać poszczególnych użytkowników. Aby uzyskać identyfikator obiektu dla grupy, użyj usługi Azure AD PowerShell — na przykład w przypadku [wersji 1.0](https://msdn.microsoft.com/library/azure/jj151815\(v=azure.98\).aspx) modułu użyj polecenia [Get-MsolGroup](https://msdn.microsoft.com/library/azure/dn194130\(v=azure.98\).aspx).

Ewentualnie, jeśli chcesz się upewnić, że tylko użytkownicy prawidłowo licencjonowani do użycia usługi Azure Information Protection będą mogli chronić zawartość:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```

Aby uzyskać więcej informacji na temat tego polecenia cmdlet i dodatkowe przykłady, zobacz pomoc do polecenia [Set-AadrmOnboardingControlPolicy](https://msdn.microsoft.com/library/dn857521.aspx).

Jeśli skorzystasz z tych kontrolek dołączania, wszyscy użytkownicy w organizacji zawsze będą mogli skorzystać z chronionej zawartości, która została zabezpieczona przez wybrany podzbiór użytkowników, ale nie będą mogli stosować własnoręcznie funkcji ochrony informacji za pośrednictwem aplikacji klienckich. Przykładowo nie będą widzieć w swoich klientach pakietu Office domyślnych szablonów automatycznie publikowanych po aktywacji usługi Azure Rights Management lub skonfigurowanych szablonów niestandardowych.  Aplikacje serwerowe, np. program Exchange, mogą wdrażać własne kontrolki dołączania dla integracji z usługą Rights Management, aby osiągnąć ten sam rezultat.


## <a name="next-steps"></a>Następne kroki
Po aktywowaniu usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] dla Twojej organizacji możesz użyć [planu wdrożenia usługi Azure Information Protection](../plan-design/deployment-roadmap.md), aby sprawdzić, czy istnieją czynności konfiguracyjne, które należy wykonać przed wdrożeniem usługi Azure Information Protection dla użytkowników i administratorów. 

Przykładowo możesz użyć [szablonów niestandardowych](configure-custom-templates.md), aby ułatwić użytkownikom stosowanie ochrony informacji wobec plików, połączyć się z lokalnymi serwerami, aby użyć usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] poprzez zainstalowanie [łącznika usługi Rights Management](deploy-rms-connector.md) i wdrożyć [aplikację Rights Management sharing](../rms-client/sharing-app-windows.md), która obsługuje ochronę wszystkich typów plików na wszystkich urządzeniach. 

Usługi pakietu Office, np. Exchange Online i SharePoint Online, wymagają przeprowadzenia dodatkowej konfiguracji przed użyciem narzędzia Zarządzanie prawami do informacji (IRM). Aby uzyskać informacje o współdziałaniu aplikacji z usługą Rights Management, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md).




<!--HONumber=Nov16_HO2-->


