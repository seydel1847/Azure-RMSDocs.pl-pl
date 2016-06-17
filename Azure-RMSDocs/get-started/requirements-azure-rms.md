---
# required metadata

title: Wymagania dotyczące usługi Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Wymagania dotyczące usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*


Przed wdrożeniem usługi Microsoft Azure Rights Management (Azure RMS) w organizacji upewnij się, że poniższe wymagania wstępne zostały spełnione. Następnie możesz skorzystać z [planu wdrożenia usługi Azure Rights Management](../plan-design/deployment-roadmap.md) w Twojej organizacji.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Subskrypcja chmury w usłudze RMS|Organizacja musi mieć subskrypcję chmury, która obsługuje usługę RMS.<br /><br />Aby uzyskać informacje dotyczące licencji, zobacz temat [Subskrypcje usług w chmurze, które obsługują usługi Azure RMS](requirements-subscriptions.md)|
|Katalog usługi Azure AD|Aby obsługiwać uwierzytelnianie użytkowników na potrzeby usługi RMS, organizacja musi mieć katalog usługi Azure AD. Ponadto jeśli chcesz użyć kont użytkowników z katalogu lokalnego (AD DS), musisz również skonfigurować integrację katalogów.<br /><br />Usługa Multi-Factor Authentication (MFA) jest obsługiwana za pomocą usługi Azure RMS, jeśli masz wymagane oprogramowanie klienckie i prawidłowo skonfigurowaną infrastrukturę obsługującą usługę MFA.<br /><br />Aby uzyskać więcej informacji, zobacz [Katalog usługi Azure AD](requirements-azure-ad.md).|
|Urządzenia klienckie|Użytkownicy muszą mieć urządzenia klienckie (komputer lub urządzenie przenośne) z systemem operacyjnym, który obsługuje usługę RMS.<br /><br />Aby uzyskać więcej informacji, zobacz temat [Urządzenia klienckie, które obsługują usługę Azure RMS](requirements-client-devices.md)|
|Aplikacje|Użytkownicy muszą uruchamiać aplikacje, które obsługują usługę RMS.<br /><br />Aby uzyskać więcej informacji, zobacz temat [Aplikacje, które obsługują usługę Azure RMS](requirements-applications.md).|
|Infrastruktura obsługująca łączność z Internetem i zależnymi usługami w chmurze|Jeśli korzystasz z zapory lub podobnych pośredniczących urządzeń sieciowych, które należy skonfigurować, aby zezwolić na określone połączenia, zobacz temat [Zakresy adresów IP i URL usługi Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Lista adresów URL i IP w temacie Lista adresów URL i IP w sekcji **Portal i udziały usługi Office 365** oraz **Uwierzytelnianie i tożsamość usługi Office 365** ma zastosowanie do portalu usługi Office 365, zasobów usługi Azure Active Directory i usługi Azure Rights Management. Aby zawsze mieć dostęp do aktualnych zmian tych informacji, subskrybuj źródło danych RSS, postępując zgodnie z instrukcjami podanymi w tym artykule.<br /><br />Oprócz informacji w artykule dotyczącym pakietu Office skorzystaj z poniższych uwag dotyczących usługi Azure RMS:<br /><br />— Nie kończ połączenia TLS między klientem i usługą (np. w celu przeprowadzenia inspekcji na poziomie pakietu). Spowoduje to przerwanie przypinania certyfikatu, którego klienci usługi RMS używają razem z urzędami certyfikacji zarządzanymi przez firmę Microsoft do zabezpieczania komunikacji z usługą Azure RMS.<br /><br />— Jeśli używasz serwera proxy sieci Web, który wymaga uwierzytelniania, musisz skonfigurować go do korzystania ze zintegrowanego uwierzytelniania systemu Windows przy użyciu poświadczeń logowania usługi Active Directory użytkownika.|

Jeśli chcesz korzystać z usługi Azure RMS na serwerach lokalnych, obsługiwane są następujące produkty:

-   Exchange Server

-   SharePoint Server

-   Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików

Aby uzyskać informacje o dodatkowych wymaganiach usługi Azure RMS dla tego scenariusza, zobacz [Serwery lokalne, które obsługują usługę Azure RMS](requirements-servers.md).

> [!IMPORTANT] Następujący scenariusz wdrażania nie jest obsługiwany:
> 
> -   Uruchamianie usług AD RMS i usługi Azure RMS równocześnie w tej samej organizacji, z wyjątkiem procesu migracji, zgodnie z opisem w temacie [Migracja z usług AD RMS do usługi Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md).
> 
> Istnieje obsługiwana ścieżka migracji [z usług AD RMS do usługi Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx) i z [usługi Azure RMS do usług AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Jeśli po wdrożeniu usługi Azure RMS zdecydujesz, że nie chcesz już używać tej usługi w chmurze, zobacz temat [Likwidowanie i dezaktywowanie usługi Azure Rights Management](../deploy-use/decommission-deactivate.md).





<!--HONumber=May16_HO3-->


