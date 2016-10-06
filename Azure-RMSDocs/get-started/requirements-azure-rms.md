---
title: "Wymagania dotyczące usługi Azure Information Protection | Azure Information Protection"
description: "Określanie wymagań wstępnych dotyczących wdrażania usługi Azure Information Protection w organizacji."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a809edc63801912e836878e9205643d7d52188f1
ms.openlocfilehash: 1239b1abe0ab720ef52ecce6c2bc948eb60fba18


---

# Wymagania dotyczące usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*


Przed wdrożeniem usługi Azure Information Protection w organizacji upewnij się, że następujące wymagania wstępne zostały spełnione. 

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Subskrypcja usługi Azure Information Protection|Przejrzyj informacje o subskrypcji znajdujące się na [stronie z cenami](https://go.microsoft.com/fwlink/?LinkId=827589) usługi Azure Information Protection, aby upewnić się, że subskrypcja organizacji obejmuje funkcje usługi Azure Information Protection, których chcesz użyć.|
|Katalog usługi Azure AD|Aby obsługiwać uwierzytelnianie użytkowników na potrzeby usługi Azure Information Protection, organizacja musi mieć katalog usługi Azure AD. Ponadto jeśli chcesz użyć kont użytkowników z katalogu lokalnego (AD DS), musisz również skonfigurować integrację katalogów.<br /><br />Uwierzytelnianie wieloskładnikowe jest obsługiwane przez usługę Azure Information Protection, jeśli masz wymagane oprogramowanie klienckie i prawidłowo skonfigurowaną infrastrukturę obsługującą to uwierzytelnianie.<br /><br />Aby uzyskać więcej informacji, zobacz [Azure Active Directory requirements for Azure Information Protection](requirements-azure-ad.md) (Wymagania usługi Azure Active Directory dotyczące usługi Azure Information Protection).|
|Urządzenia klienckie|Użytkownicy muszą mieć urządzenia klienckie (komputer lub urządzenie przenośne) z systemem operacyjnym, który obsługuje usługę Azure Information Protection.<br /><br />Następujące urządzenia obsługują klienta usługi Azure Information Protection, co pozwala użytkownikom klasyfikować i oznaczać ich wiadomości e-mail i dokumenty pakietu Office:<br /><br />— Windows 10 (x86, x64)<br /><br />— Windows 8.1 (x86, x64)<br /><br />— Windows 8 (x86, x64)<br /><br />— Windows 7 z dodatkiem Service Pack 1 (x86, x64)<br /><br />Gdy klient chroni dane za pomocą usługi Azure Rights Management, mogą być one używane przez te same urządzenia (z systemem Windows, Mac, iOS lub Android), które obsługują usługę Azure Rights Management. <br /><br />Aby uzyskać szczegółowe informacje na temat urządzeń obsługujących usługę Azure Rights Management, zobacz [Client devices that support Azure Rights Management data protection](../get-started/requirements-client-devices.md) (Urządzenia klienckie obsługujące ochronę danych usługi Azure Rights Management).|
|Aplikacje|Klient usługi Azure Information Protection obsługuje etykietowanie i ochronę plików oraz wiadomości e-mail, które zostały utworzone przez aplikacje **Word**, **Excel**, **PowerPoint** i **Outlook** pochodzące z następujących pakietów Office:<br /><br />— Office Professional Plus 2016<br /><br />— Office Professional Plus 2013 z dodatkiem Service Pack 1<br /><br />— Office Professional Plus 2010<br /><br />Aby uzyskać więcej informacji na temat aplikacji obsługujących usługę Azure Rights Management, zobacz [Applications that support Azure Rights Management data protection](requirements-applications.md) (Aplikacje obsługujące ochronę danych usługi Azure Rights Management).|
|Infrastruktura obsługująca łączność z Internetem i zależnymi usługami w chmurze|Jeśli jest używana zapora lub podobne aktywne urządzenie sieciowe wymagające skonfigurowania określonych połączeń sieciowych, zapoznaj się z informacjami o usłudze **Azure Rights Management (RMS)** w sekcji [Portal usługi Office 365 i udostępnianie](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) w następującym artykule o pakiecie Office: [Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Aby zawsze mieć dostęp do aktualnych wersji tych informacji, subskrybuj źródło danych RSS, postępując zgodnie z instrukcjami podanymi w tym artykule pakietu Office.<br /><br />Oprócz informacji zawartych w artykule dotyczącym pakietu Office skorzystaj z poniższych uwag dotyczących usługi Azure Information Protection:<br /><br />— Zezwalaj na ruch HTTPS na porcie TCP 443 do witryny **api.informationprotection.azure.com**.<br /><br />— Nie kończ połączenia TLS między klientem i usługą (np. w celu przeprowadzenia inspekcji na poziomie pakietu). Spowoduje to przerwanie przypinania certyfikatu, którego klienci usługi RMS używają razem z urzędami certyfikacji zarządzanymi przez firmę Microsoft do zabezpieczania komunikacji z usługą Azure RMS.<br /><br />— Jeśli używasz serwera proxy sieci Web, który wymaga uwierzytelniania, musisz skonfigurować go do korzystania ze zintegrowanego uwierzytelniania systemu Windows przy użyciu poświadczeń logowania usługi Active Directory użytkownika.|

Następujące produkty serwera lokalnego są obsługiwane przez usługę Azure Rights Management działającą w ramach usługi Azure Information Protection:

-   Exchange Server

-   SharePoint Server

-   Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików

Aby uzyskać informacje o dodatkowych wymaganiach dla tego scenariusza, zobacz [On-premises servers that support Azure Rights Management data protection](requirements-servers.md) (Serwery lokalne obsługujące ochronę danych usługi Azure Rights Management).

> [!IMPORTANT]
> Poniższy scenariusz wdrożenia nie jest obsługiwany, chyba że jest używana ochrona usług AD RMS w ramach usługi Azure Information Protection — konfiguracja HYOK („Hold Your Own Key”):
> 
> -   Uruchamianie usług AD RMS i Azure RMS równocześnie w tej samej organizacji, z wyjątkiem procesu migracji, zgodnie z opisem zawartym w temacie [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).
> 
> Istnieje obsługiwana ścieżka migracji [z usług AD RMS do usługi Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) i z [usługi Azure Information Protection do usług AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Jeśli po wdrożeniu usługi Azure Information Protection zdecydujesz, że nie chcesz już używać tej usługi w chmurze, zobacz [Decommissioning and deactivating Azure Information Protection](../deploy-use/decommission-deactivate.md) (Likwidowanie i dezaktywowanie usługi Azure Information Protection).






<!--HONumber=Sep16_HO5-->


