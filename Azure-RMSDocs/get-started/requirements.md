---
title: Wymagania dotyczące usługi Azure Information Protection
description: Określanie wymagań wstępnych dotyczących wdrażania usługi Azure Information Protection w organizacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/04/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 380b2f715ead6f3f8c8e497c911ff425c12424e8
ms.sourcegitcommit: 40ac805183589a1c8ef22bc1bd9556bcc92f65e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2018
---
# <a name="requirements-for-azure-information-protection"></a>Wymagania dotyczące usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Przed wdrożeniem usługi Azure Information Protection w organizacji upewnij się, że następujące wymagania wstępne zostały spełnione. 

## <a name="subscription-for-azure-information-protection"></a>Subskrypcja usługi Azure Information Protection

**Dla klasyfikacji, etykietowania i ochrony**: musisz mieć [planu usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/). 

**Aby uzyskać tylko do ochrony**: musisz mieć [planu usługi Office 365, która obejmuje usługi Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Aby upewnić się, że organizacji Subskrypcja obejmuje funkcje usługi Azure Information Protection, które chcesz użyć, należy zapoznać się z listą funkcji z [cennik usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection) strony.

> [!TIP]
> Wyszukiwanie, aby zobaczyć, czy plan usługi Office 365 lub Exchange Online autonomiczne, planowanie obsługuje [nowe funkcje z szyfrowanie wiadomości usługi Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801), aby wysłać chronionych wiadomości e-mail do osobistych adresów e-mail? Na przykład Gmail, Yahoo i firmy Microsoft. Sprawdź następujące zasoby:
>
> [Opis usługi Online programu Exchange](https://technet.microsoft.com/library/exchange-online-service-description.aspx)
>
> [Office 365 Education](https://technet.microsoft.com/library/mt844095.aspx)
>
> [Usługi Office 365 dla instytucji rządowych USA](https://technet.microsoft.com/library/mt774581.aspx)

Jeśli masz pytania dotyczące subskrypcji lub licencji, nie umieszczaj ich na tej stronie, tylko skontaktuj się z konsultantem ds. klientów firmy Microsoft lub [Pomocą techniczną firmy Microsoft](information-support.md#to-contact-microsoft-support).

## <a name="azure-active-directory"></a>Azure Active Directory

Aby obsługiwać uwierzytelnianie i autoryzację użytkowników na potrzeby usługi Azure Information Protection, organizacja musi korzystać z usługi Azure Active Directory (Azure AD). Ponadto jeśli chcesz użyć kont użytkowników z katalogu lokalnego (AD DS), musisz również skonfigurować integrację katalogów.

Rejestracji jednokrotnej (SSO) jest obsługiwana dla usługi Azure Information Protection, dzięki czemu użytkownicy nie są wielokrotnie monitowani o podanie poświadczeń. Jeśli używasz innego dostawcy rozwiązania do federacyjnego skontaktuj się z danym dostawcą konfigurowania usługi Azure AD. WS-Trust jest typowe wymagania dotyczące tych rozwiązań w celu obsługi logowania jednokrotnego. 

Uwierzytelnianie wieloskładnikowe jest obsługiwane przez usługę Azure Information Protection, jeśli masz wymagane oprogramowanie klienckie i prawidłowo skonfigurowaną infrastrukturę obsługującą to uwierzytelnianie.

Dostęp warunkowy jest obsługiwana w wersji zapoznawczej dla dokumentów chronionych przez usługę Azure Information Protection. Aby uzyskać więcej informacji, zobacz poniższe często zadawane pytania: [widać usługi Azure Information Protection znajduje się w aplikacji w chmurze dostępnych dla dostępu warunkowego, jak to działa?](faqs.md#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

Aby uzyskać więcej informacji na temat wymagań dotyczących uwierzytelniania, zobacz artykuł [Wymagania usługi Azure Active Directory dotyczące usługi Azure Information Protection](requirements-azure-ad.md). 

Aby uzyskać więcej informacji na temat wymagań dotyczących kont użytkowników i grup do autoryzacji, zobacz artykuł [Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection](../plan-design/prepare.md).

## <a name="client-devices"></a>Urządzenia klienckie

Użytkownicy muszą mieć urządzenia klienckie (komputer lub urządzenie przenośne) z systemem operacyjnym, który obsługuje usługę Azure Information Protection.

Następujące urządzenia obsługują klienta usługi Azure Information Protection, co pozwala użytkownikom klasyfikować i oznaczać swoje dokumenty i wiadomości e-mail:

- Windows 10 (x86, x64)

- Windows 8.1 (x86, x64)

- Windows 8 (x86, x64)

- Windows 7 z dodatkiem Service Pack 1 (x86, x64)

- Windows Server 2016 

- Systemy Windows Server 2012 R2 i Windows Server 2012

- Windows Server 2008 R2 

W przypadku wymienionych wersji serwerowych klient usługi Azure Information Protection jest obsługiwany przez usługi pulpitu zdalnego. W przypadku usuwania profilów użytkowników podczas korzystania z klienta usługi Azure Information Protection z usługami pulpitu zdalnego nie usuwaj folderu **%Appdata%\Microsoft\Protect**.

Dane chronione przez klienta usługi Azure Information Protection za pomocą usługi Azure Rights Management mogą być używane przez [te same urządzenia](requirements-client-devices.md), które obsługują usługę Azure Rights Management.

## <a name="applications"></a>Aplikacje

Klient usługi Azure Information Protection umożliwia etykietowanie i ochronę dokumentów oraz wiadomości e-mail za pośrednictwem aplikacji pakietu Office **Word**, **Excel**, **PowerPoint** i **Outlook** pochodzących z dowolnych z następujących pakietów Office:

- Office 365 ProPlus z aplikacjami w wersji 2016 lub 2013 (instalacja z użyciem szybkiej instalacji lub Instalatora Windows)
    
    Te wersje pakietu Office są dołączone do większości, ale nie wszystkie subskrypcji usługi Office 365, które obejmują ochronę danych z usługi Azure Information Protection. Sprawdź swoje informacje subskrypcji, aby sprawdzać, czy usługi Office 365 ProPlus uwzględnione. Zawiera ona również te informacje w [arkusz danych usługi Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

- Office Professional Plus 2016

- Office Professional Plus 2013 z dodatkiem Service Pack 1

- Office Professional Plus 2010 z dodatkiem Service Pack 2

Inne wersje pakietu Office nie mogą chronić dokumentów i wiadomości e-mail przy użyciu usługi Rights Management. W przypadku tych wersji usługa Azure Information Protection jest obsługiwana wyłącznie do klasyfikowania. W rezultacie etykiety, które mają zastosowanie ochrony nie są wyświetlane dla użytkowników usługi Azure Information Protection paska lub z **Chroń** na Wstążce pakietu Office. 

Klient usługi Azure Information Protection nie obsługuje wielu wersji pakietu Office na tym samym komputerze. Ten klient nie obsługuje również przełączania kont użytkowników w pakiecie Office.

Aby uzyskać więcej informacji na temat wersji pakietów Office obsługujących usługę ochrony danych, zobacz [Aplikacje obsługujące ochronę danych usługi Azure Rights Management](requirements-applications.md).

## <a name="firewalls-and-network-infrastructure"></a>Zapory i infrastruktura sieciowa

Jeśli jest używana zapora lub podobne pośredniczące urządzenie sieciowe skonfigurowane pod kątem zezwalania na określone połączenia, zapoznaj się z informacjami o usłudze **Azure Rights Management (RMS)** w sekcji [Portal usługi Office 365 i udostępnianie](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US#bkmk_portal-identity) następującego artykułu o pakiecie Office: [Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Aby zawsze mieć dostęp do aktualnych wersji tych informacji, subskrybuj źródło danych RSS, postępując zgodnie z instrukcjami podanymi w tym artykule pakietu Office.

Oprócz informacji zawartych w artykule dotyczącym pakietu Office skorzystaj z poniższych uwag dotyczących usługi Azure Information Protection:

- Zezwalaj na ruch HTTPS na porcie TCP 443 do witryny **api.informationprotection.azure.com**.

- Zezwalaj na ruch HTTPS na porcie TCP 443 do **mobile.pipe.aria.microsoft.com**.

- Jeśli używasz internetowego serwera proxy, który wymaga uwierzytelniania, musisz skonfigurować go do korzystania ze zintegrowanego uwierzytelniania systemu Windows przy użyciu poświadczeń logowania usługi Active Directory użytkownika.

- Nie kończ połączenia TLS Usługa klienta (na przykład w celu przeprowadzenia inspekcji na poziomie pakietu) do usługi Azure Rights Management. Spowoduje to przerwanie przypinania, że klienci usług RMS za pomocą CAs zarządzany przez firmę Microsoft do zabezpieczania komunikacji z usługą Azure Rights Management certyfikatu.
    
    - Porada: Ze względu na sposób Chrome wyświetlania bezpiecznych połączeń na pasku adresu, można użyć tej przeglądarki można szybko sprawdzić, czy połączenie klienta zostało zakończone przed osiągnie usługi Azure Rights Management. Wprowadź następujący adres URL na pasku adresu przeglądarki: `https://admin.na.aadrm.com/admin/admin.svc` 
    
        Nie martw się o Wyświetla okna przeglądarki. Zamiast tego kliknij kłódki na pasku adresu, aby wyświetlić informacje o lokacji. Informacje o lokacji pozwala sprawdzić wystawiający urząd certyfikacji (CA). Jeśli certyfikat nie jest wystawiany przez CA firmy Microsoft, jest bardzo prawdopodobne, bezpieczne połączenie Usługa klienta jest przerywane i wymaga ponownej konfiguracji na zaporze. Na poniższej ilustracji przedstawiono przykład Microsoft wystawiający urząd certyfikacji. Jeśli zobaczysz, że wewnętrzny urząd certyfikacji wystawił certyfikat, ta konfiguracja nie jest zgodny z usługi Azure Information Protection.
        
        ![Sprawdzanie wystawionego certyfikatu dla usługi Azure Information Protection połączeń](../media/certificate-checking.png)

### <a name="on-premises-servers"></a>Serwery lokalne

Następujące produkty serwera lokalnego są obsługiwane przez usługę Azure Rights Management działającą w ramach usługi Azure Information Protection:

- Exchange Server

- SharePoint Server

- Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików

Aby uzyskać informacje o dodatkowych wymaganiach dla tego scenariusza, zobacz [On-premises servers that support Azure Rights Management data protection](requirements-servers.md) (Serwery lokalne obsługujące ochronę danych usługi Azure Rights Management).

### <a name="coexistence-of-ad-rms-with-azure-rms"></a>Współistnienie usług AD RMS z usługami Azure RMS

Poniższy scenariusz wdrożenia nie jest obsługiwany, chyba że jest używana ochrona usług AD RMS w ramach usługi Azure Information Protection — konfiguracja HYOK („Hold Your Own Key”):

- Uruchamianie usług AD RMS i Azure RMS równocześnie w tej samej organizacji, z wyjątkiem procesu migracji, zgodnie z opisem zawartym w temacie [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

Istnieje obsługiwana ścieżka migracji [z usług AD RMS do usługi Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) i z [usługi Azure Information Protection do usług AD RMS](/powershell/module/aadrm/Set-AadrmMigrationUrl). Jeśli po wdrożeniu usługi Azure Information Protection zdecydujesz, że nie chcesz już używać tej usługi w chmurze, zobacz [Decommissioning and deactivating Azure Information Protection](../deploy-use/decommission-deactivate.md) (Likwidowanie i dezaktywowanie usługi Azure Information Protection).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


