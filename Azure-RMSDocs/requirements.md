---
title: Wymagania dotyczące usługi Azure Information Protection
description: Określanie wymagań wstępnych dotyczących wdrażania usługi Azure Information Protection w organizacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 92b7ca3feceb70bc9b8b085b58c26231d2ae70ce
ms.sourcegitcommit: 8a4bab8dc6ee4c322a54d79091af04ec9449e5c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51020058"
---
# <a name="requirements-for-azure-information-protection"></a>Wymagania dotyczące usługi Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Przed wdrożeniem usługi Azure Information Protection w organizacji upewnij się, że następujące wymagania wstępne zostały spełnione. 

## <a name="subscription-for-azure-information-protection"></a>Subskrypcja usługi Azure Information Protection

**Dla klasyfikacji, etykietowania i ochrony**: konieczne jest posiadanie [planu usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/). 

**Aby uzyskać tylko do ochrony**: konieczne jest posiadanie [planu usługi Office 365, która obejmuje usługi Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Aby upewnić się, że subskrypcja organizacji obejmuje funkcje usługi Azure Information Protection, które chcesz użyć, zapoznaj się z listą funkcji z [cennika usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection) strony.

> [!TIP]
> Chcesz zobaczyć, jeśli plan usługi Office 365 lub usługi Exchange Online autonomiczny plan obsługuje [nowe możliwości z szyfrowanie wiadomości usługi Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801), do wysyłania chronionych wiadomości e-mail do osobistych adresów e-mail? Na przykład Gmail, Yahoo i firmy Microsoft. Sprawdź następujące zasoby:
>
> [Opis usługi Online programu Exchange](https://technet.microsoft.com/library/exchange-online-service-description.aspx)
>
> [Office 365 Education](https://technet.microsoft.com/library/mt844095.aspx)
>
> [Usługi Office 365 dla instytucji rządowych USA](https://technet.microsoft.com/library/mt774581.aspx)

Jeśli masz pytania dotyczące subskrypcji lub licencji, nie umieszczaj ich na tej stronie, tylko skontaktuj się z konsultantem ds. klientów firmy Microsoft lub [Pomocą techniczną firmy Microsoft](information-support.md#to-contact-microsoft-support).

## <a name="azure-active-directory"></a>Azure Active Directory

Aby obsługiwać uwierzytelnianie i autoryzację użytkowników na potrzeby usługi Azure Information Protection, organizacja musi korzystać z usługi Azure Active Directory (Azure AD). Ponadto jeśli chcesz użyć kont użytkowników z katalogu lokalnego (AD DS), należy skonfigurować także Integracja katalogu.

Logowanie jednokrotne (SSO) jest obsługiwana dla usługi Azure Information Protection, dzięki czemu użytkownicy nie będą regularnie monitowani o podanie poświadczeń. Jeśli używasz innego dostawcy rozwiązania do Federacji, skontaktuj się z danym dostawcą jak skonfigurować go do usługi Azure AD. WS-Trust jest typowym wymogiem dla tych rozwiązań do obsługi logowania jednokrotnego. 

Uwierzytelnianie wieloskładnikowe jest obsługiwane przez usługę Azure Information Protection, jeśli masz wymagane oprogramowanie klienckie i prawidłowo skonfigurowaną infrastrukturę obsługującą to uwierzytelnianie.

Dostęp warunkowy jest obsługiwana w wersji zapoznawczej dla dokumentów chronionych przez usługę Azure Information Protection. Aby uzyskać więcej informacji, zobacz poniższe często zadawane pytania: [widzę, że usługi Azure Information Protection znajduje się w aplikacji w chmurze dostępnych dla dostępu warunkowego — jak to działa?](faqs.md#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

Aby uzyskać więcej informacji na temat wymagań dotyczących uwierzytelniania, zobacz artykuł [Wymagania usługi Azure Active Directory dotyczące usługi Azure Information Protection](requirements-azure-ad.md). 

Aby uzyskać więcej informacji na temat wymagań dotyczących kont użytkowników i grup do autoryzacji, zobacz artykuł [Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection](prepare.md).

## <a name="client-devices"></a>Urządzenia klienckie

Użytkownicy muszą mieć urządzenia klienckie (komputer lub urządzenie przenośne) z systemem operacyjnym, który obsługuje usługę Azure Information Protection.

Następujące urządzenia obsługują klienta usługi Azure Information Protection, co pozwala użytkownikom klasyfikować i oznaczać swoje dokumenty i wiadomości e-mail:

- Windows 10 (x86, x64)
    
    - Brak obsługi dla pisma ręcznego w kompilacji systemu Windows 10 RS4 dla niejawnych testerów. 

- Windows 8.1 (x86, x64)

- Windows 8 (x86, x64)

- Windows 7 z dodatkiem Service Pack 1 (x86, x64)

- Windows Server 2016 

- Systemy Windows Server 2012 R2 i Windows Server 2012

- Windows Server 2008 R2 

Oprócz instalowania klienta usługi Azure Information Protection na komputerach fizycznych, można także zainstalować je na maszynach wirtualnych. Sprawdzić, czy z dostawcą rozwiązania pulpitu wirtualnego ma dodatkowej konfiguracji, który może być konieczne uruchomienie klienta usługi Azure Information Protection. Na przykład w przypadku rozwiązań Citrix, konieczne może być [wyłączyć punkty zaczepienia interfejsu programowania aplikacji Citrix (API)](https://support.citrix.com/article/CTX107825) dla pakietu Office (winword.exe excel.exe, outlook.exe, powerpoint.exe) i (klienta usługi Azure Information Protection msip.App.exe, msip.viewer.exe).

W przypadku wymienionych wersji serwerowych klient usługi Azure Information Protection jest obsługiwany przez usługi pulpitu zdalnego. W przypadku usuwania profilów użytkowników podczas korzystania z klienta usługi Azure Information Protection z usługami pulpitu zdalnego nie usuwaj folderu **%Appdata%\Microsoft\Protect**.

Dane chronione przez klienta usługi Azure Information Protection za pomocą usługi Azure Rights Management mogą być używane przez [te same urządzenia](requirements-client-devices.md), które obsługują usługę Azure Rights Management.

Klient usługi Azure Information Protection ma [dodatkowe wymagania wstępne](./rms-client/client-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-client) wymienione w podręczniku administratora.

## <a name="applications"></a>Aplikacje

Klient usługi Azure Information Protection umożliwia etykietowanie i ochronę dokumentów oraz wiadomości e-mail za pośrednictwem aplikacji pakietu Office **Word**, **Excel**, **PowerPoint** i **Outlook** pochodzących z dowolnych z następujących pakietów Office:

- Usługa Office 365 z aplikacji pakietu Office 2016 (minimalna wersja 1805, kompilacja 9330.2078) po użytkownik ma przypisaną licencję usługi Azure Rights Management (nazywanego także usługi Azure Information Protection dla usługi Office 365)

- Office 365 ProPlus z aplikacjami w wersji 2016 lub 2013 (instalacja z użyciem szybkiej instalacji lub Instalatora Windows)

- Office Professional Plus 2016

- Office Professional Plus 2013 z dodatkiem Service Pack 1

- Office Professional Plus 2010 z dodatkiem Service Pack 2

Inne wersje pakietu Office nie mogą chronić dokumentów i wiadomości e-mail przy użyciu usługi Rights Management. W przypadku tych wersji usługa Azure Information Protection jest obsługiwana wyłącznie do klasyfikowania. W związku z tym, etykiety umożliwiające objęcie ochroną nie są wyświetlane użytkownikom w usłudze Azure Information Protection, pasek lub z **Chroń** przycisk na Wstążce pakietu Office. 

Klient usługi Azure Information Protection nie obsługuje wielu wersji pakietu Office na tym samym komputerze. Ten klient również nie obsługuje przełączania kont użytkowników w pakiecie Office.

Aby uzyskać informacji na temat wersji pakietów Office obsługujących usługę ochrony, zobacz [aplikacje obsługujące ochronę danych usługi Azure Rights Management](requirements-applications.md).

## <a name="firewalls-and-network-infrastructure"></a>Zapory i infrastruktura sieciowa

Jeśli zapora lub podobne pośredniczące urządzenie, które są skonfigurowane do zezwalania na określone połączenia sieciowe, wymagań dotyczących łączności sieciowej znajdują się w artykule o pakiecie Office [URL usługi Office 365 i zakresy adresów IP](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2). Zobacz **Microsoft 365 typowe i Office Online** sekcji.

Oprócz informacji zawartych w artykule dotyczącym pakietu Office skorzystaj z poniższych uwag dotyczących usługi Azure Information Protection:

- Jeśli używasz internetowego serwera proxy, który wymaga uwierzytelniania, musisz skonfigurować go do korzystania ze zintegrowanego uwierzytelniania systemu Windows przy użyciu poświadczeń logowania usługi Active Directory użytkownika.

- Nie przerywaj połączenia TLS między klientem a usługą (na przykład w celu przeprowadzenia inspekcji na poziomie pakietu) do **aadrm.com** adresu URL. Spowoduje to przerwanie przypinania, czy klienci usługi RMS za pomocą zarządzanych przez firmę Microsoft urzędów certyfikacji do zabezpieczania komunikacji z usługą Azure Rights Management certyfikatu.
    
    - Porada: Ze względu na sposób Chrome Wyświetla bezpiecznych połączeń w pasku adresu, można użyć tej przeglądarki można szybko sprawdzić, czy połączenie klienta zostanie zakończony przed osiągnięciem przez nią usługi Azure Rights Management. Wprowadź następujący adres URL w pasku adresu przeglądarki: `https://admin.na.aadrm.com/admin/admin.svc` 
    
        Nie martw się o Wyświetla okno przeglądarki. Zamiast tego kliknij kłódki na pasku adresu, aby wyświetlić informacje o lokacji. Informacje o lokacji pozwala sprawdzić wystawiający urząd certyfikacji (CA). Jeśli certyfikat nie jest wystawiony przez CA firmy Microsoft, jest bardzo prawdopodobne, bezpieczne połączenie usługi klienta zostanie przerwany i wymaga ponownej konfiguracji zapory. Na poniższej ilustracji przedstawiono przykład Microsoft wystawiający urząd certyfikacji. Jeśli widzisz, że wewnętrzny urząd certyfikacji wystawił certyfikat, ta konfiguracja nie jest zgodny z usługi Azure Information Protection.
        
        ![Sprawdzanie wystawionego certyfikatu dla połączenia usługi Azure Information Protection](./media/certificate-checking.png)

### <a name="on-premises-servers"></a>Serwery lokalne

Następujące produkty serwera lokalnego są obsługiwane przez usługę Azure Rights Management działającą w ramach usługi Azure Information Protection:

- Exchange Server

- SharePoint Server

- Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików

Aby uzyskać informacje o dodatkowych wymaganiach dla tego scenariusza, zobacz [On-premises servers that support Azure Rights Management data protection](requirements-servers.md) (Serwery lokalne obsługujące ochronę danych usługi Azure Rights Management).

### <a name="coexistence-of-ad-rms-with-azure-rms"></a>Współistnienie usług AD RMS z usługami Azure RMS

Następujący scenariusz wdrażania nie jest obsługiwana tylko w przypadku korzystania z usług AD RMS dla [ochrony HYOK](configure-adrms-restrictions.md) za pomocą usługi Azure Information Protection (Konfiguracja "hold your own key"):

- Uruchamianie usług AD RMS i Azure RMS obok siebie w tej samej organizacji, z wyjątkiem procesu migracji, zgodnie z opisem w [Migrowanie z usług AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

Istnieje obsługiwana ścieżka migracji [z usług AD RMS do usługi Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx)i z [usługi Azure Information Protection do usług AD RMS](/powershell/module/aadrm/Set-AadrmMigrationUrl). Jeśli po wdrożeniu usługi Azure Information Protection zdecydujesz, że nie chcesz już używać tej usługi w chmurze, zobacz [Decommissioning and deactivating Azure Information Protection](decommission-deactivate.md) (Likwidowanie i dezaktywowanie usługi Azure Information Protection).




