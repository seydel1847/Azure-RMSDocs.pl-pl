---
title: "Wymagania dotyczące usługi Azure Information Protection"
description: "Określanie wymagań wstępnych dotyczących wdrażania usługi Azure Information Protection w organizacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 66874f6e60c2cd5efb2dedaae470170811a84a67
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Wymagania dotyczące usługi Azure Information Protection
<a id="requirements-for-azure-information-protection" class="xliff"></a>

>*Dotyczy: Azure Information Protection, Office 365*

Przed wdrożeniem usługi Azure Information Protection w organizacji upewnij się, że następujące wymagania wstępne zostały spełnione. 

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Subskrypcja usługi Azure Information Protection|Na potrzeby klasyfikacji, etykietowania i ochrony musisz dysponować [planem usługi Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing). Na potrzeby samej ochrony musisz dysponować [planem usługi Office 365 obejmującym usługę Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).<br /><br /> Przejrzyj [informacje o subskrypcji](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) oraz [listę funkcji](https://www.microsoft.com/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection, aby upewnić się, że subskrypcja organizacji obejmuje funkcje usługi Azure Information Protection, których chcesz użyć.<br /><br />Uwaga: Jeśli masz pytania dotyczące subskrypcji lub licencji, nie umieszczaj ich na tej stronie, tylko skontaktuj się z konsultantem ds. klientów firmy Microsoft lub [Pomocą techniczną firmy Microsoft](information-support.md#to-contact-microsoft-support). |
|Azure Active Directory|Aby obsługiwać uwierzytelnianie i autoryzację użytkowników na potrzeby usługi Azure Information Protection, organizacja musi korzystać z usługi Azure Active Directory (Azure AD). Ponadto jeśli chcesz użyć kont użytkowników z katalogu lokalnego (AD DS), musisz również skonfigurować integrację katalogów.<br /><br />Uwierzytelnianie wieloskładnikowe jest obsługiwane przez usługę Azure Information Protection, jeśli masz wymagane oprogramowanie klienckie i prawidłowo skonfigurowaną infrastrukturę obsługującą to uwierzytelnianie.<br /><br />Aby uzyskać więcej informacji na temat wymagań dotyczących uwierzytelniania, zobacz artykuł [Wymagania usługi Azure Active Directory dotyczące usługi Azure Information Protection](requirements-azure-ad.md). <br /><br />Aby uzyskać więcej informacji na temat wymagań dotyczących kont użytkowników i grup do autoryzacji, zobacz artykuł [Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection](../plan-design/prepare.md).|
|Urządzenia klienckie|Użytkownicy muszą mieć urządzenia klienckie (komputer lub urządzenie przenośne) z systemem operacyjnym, który obsługuje usługę Azure Information Protection.<br /><br />Następujące urządzenia obsługują klienta usługi Azure Information Protection, co pozwala użytkownikom klasyfikować i oznaczać ich wiadomości e-mail i dokumenty pakietu Office:<br /><br />— Windows 10 (x86, x64)<br /><br />— Windows 8.1 (x86, x64)<br /><br />— Windows 8 (x86, x64)<br /><br />— Windows 7 z dodatkiem Service Pack 1 (x86, x64)<br /><br />— Windows Server 2016 <br /><br /> — Windows Server 2012 R2 i Windows Server 2012<br /><br />Gdy klient chroni dane za pomocą usługi Azure Rights Management, mogą być one używane przez te same urządzenia (z systemem Windows, Mac, iOS lub Android), które obsługują usługę Azure Rights Management. <br /><br />Aby uzyskać szczegółowe informacje na temat urządzeń obsługujących usługę Azure Rights Management, zobacz [Client devices that support Azure Rights Management data protection](../get-started/requirements-client-devices.md) (Urządzenia klienckie obsługujące ochronę danych usługi Azure Rights Management).|
|Aplikacje|Klient usługi Azure Information Protection umożliwia etykietowanie i ochronę plików oraz wiadomości e-mail za pośrednictwem aplikacji pakietu Office **Word**, **Excel**, **PowerPoint** i **Outlook** pochodzących z dowolnych z następujących pakietów Office:<br /><br /> — Office 365 ProPlus z aplikacjami w wersji 2016 lub 2013 (instalacja z użyciem szybkiej instalacji lub Instalatora Windows)<br /><br />— Office Professional Plus 2016<br /><br />— Office Professional Plus 2013 z dodatkiem Service Pack 1<br /><br />— Office Professional Plus 2010 <br /><br />Inne wersje pakietu Office nie mogą chronić dokumentów i wiadomości e-mail przy użyciu usługi Rights Management. W przypadku tych wersji usługa Azure Information Protection jest obsługiwana wyłącznie do klasyfikowania, a etykiety, które dołączają ochronę, nie są wyświetlane na pasku usługi Azure Information Protection. <br /><br />Aby uzyskać więcej informacji na temat wersji pakietów Office obsługujących usługę ochrony danych, zobacz [Aplikacje obsługujące ochronę danych usługi Azure Rights Management](requirements-applications.md).|
|Infrastruktura obsługująca łączność z Internetem i zależnymi usługami w chmurze|Jeśli jest używana zapora lub podobne aktywne urządzenie sieciowe wymagające skonfigurowania określonych połączeń sieciowych, zapoznaj się z informacjami o usłudze **Azure Rights Management (RMS)** w sekcji [Portal usługi Office 365 i udostępnianie](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US#bkmk_portal-identity) w następującym artykule o pakiecie Office: [Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Aby zawsze mieć dostęp do aktualnych wersji tych informacji, subskrybuj źródło danych RSS, postępując zgodnie z instrukcjami podanymi w tym artykule pakietu Office.<br /><br />Oprócz informacji zawartych w artykule dotyczącym pakietu Office skorzystaj z poniższych uwag dotyczących usługi Azure Information Protection:<br /><br />— Zezwalaj na ruch HTTPS na porcie TCP 443 do witryny **api.informationprotection.azure.com**.<br /><br />— Nie kończ połączenia TLS między klientem i usługą (np. w celu przeprowadzenia inspekcji na poziomie pakietu). Spowoduje to przerwanie przypinania certyfikatu, którego klienci usługi RMS używają razem z urzędami certyfikacji zarządzanymi przez firmę Microsoft do zabezpieczania komunikacji z usługą Azure RMS.<br /><br />— Jeśli używasz serwera proxy sieci Web, który wymaga uwierzytelniania, musisz skonfigurować go do korzystania ze zintegrowanego uwierzytelniania systemu Windows przy użyciu poświadczeń logowania usługi Active Directory użytkownika.|

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
> Istnieje obsługiwana ścieżka migracji [z usług AD RMS do usługi Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) i z [usługi Azure Information Protection do usług AD RMS](/powershell/module/aadrm/Set-AadrmMigrationUrl). Jeśli po wdrożeniu usługi Azure Information Protection zdecydujesz, że nie chcesz już używać tej usługi w chmurze, zobacz [Decommissioning and deactivating Azure Information Protection](../deploy-use/decommission-deactivate.md) (Likwidowanie i dezaktywowanie usługi Azure Information Protection).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


