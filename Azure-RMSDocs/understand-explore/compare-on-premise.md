---
title: "Porównanie usług Azure Information Protection i AD RMS | Azure Information Protection"
description: "Jeśli usługa Active Directory Rights Management Services (AD RMS) jest Ci znana lub była wcześniej wdrażana, być może zastanawiasz się, jakie byłyby wyniki porównania jej z usługą Azure Information Protection pod kątem funkcjonalności i wymagań."
author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4591d5c45104108ccf151bb1d7a9382652e585a6
ms.openlocfilehash: 36adf768bdb5a0937af3563665bbe139c86ff250


---

# Porównanie usług Azure Information Protection i AD RMS

>*Dotyczy: Active Directory Rights Management, Azure Information Protection, Office 365*

Jeśli usługa Active Directory Rights Management Services (AD RMS) jest Ci znana lub była wcześniej wdrażana, być może zastanawiasz się, jakie byłyby wyniki porównania jej z usługą Azure Information Protection pod kątem funkcjonalności i wymagań rozwiązania do ochrony informacji.

Niektóre główne różnice związane z usługą Azure Information Protection:

- **Brak wymaganej infrastruktury serwerów**: usługa Azure Information Protection nie wymaga dodatkowych serwerów ani certyfikatów PKI, których potrzebują usługi AD RMS, ponieważ te kwestie są obsługiwane na platformie Microsoft Azure. Dzięki temu to rozwiązanie w chmurze jest szybsze do wdrożenia i łatwiejsze w utrzymaniu.

- **Uwierzytelnianie oparte na chmurze**: usługa Azure Information Protection używa usługi Azure AD do uwierzytelniania, zarówno w przypadku użytkowników wewnętrznych, jak i użytkowników z innych organizacji. Oznacza to, że użytkowników mobilnych można uwierzytelnić nawet wtedy, gdy nie są oni połączeni z siecią wewnętrzną, i łatwiej można udostępnić chronioną zawartość użytkownikom z innych organizacji. Wiele organizacji ma już konta użytkowników w usłudze Azure AD, ponieważ działają na nich usługi platformy Azure lub usługa Office 365. W przeciwnym razie usługa RMS dla użytkowników indywidualnych umożliwia użytkownikom tworzenie bezpłatnych kont. Do udostępniania chronionej zawartości usług AD RMS innej organizacji wymagane jest skonfigurowanie relacji jawnego zaufania z każdą organizacją.

- **Wbudowana obsługa urządzeń przenośnych**: aby usługa Azure RMS obsługiwała urządzenia przenośne i komputery Mac, nie trzeba wprowadzać żadnych zmian wdrożenia. Aby obsługiwać te urządzenia za pomocą usług AD RMS, należy zainstalować rozszerzenie dla urządzeń przenośnych, skonfigurować usługi AD FS na potrzeby federacji i utworzyć dodatkowe rekordy publicznej usługi DNS.

- **Szablony domyślne**: usługa Azure Information Protection tworzy dwa szablony domyślne od razu po aktywacji usługi ochrony, dzięki czemu można łatwo natychmiast objąć ochroną ważne dane. Usługa AD RMS nie ma szablonów domyślnych.

- **Szablony działów**: usługa Azure Information Protection obsługuje szablony działów jako ustawienie konfiguracji dodatkowych tworzonych szablonów. To ustawienie umożliwia określenie, którzy użytkownicy widzą szablon w aplikacjach klienckich (np. aplikacjach pakietu Office), dzięki czemu mogą oni łatwiej wybrać prawidłowe zasady zdefiniowane dla różnych grup użytkowników. Usługi AD RMS nie obsługują szablonów działów.

- **Śledzenie dokumentów, odwoływanie i powiadamianie e-mail**: usługa Azure Information Protection obsługuje te funkcje przy użyciu aplikacji RMS sharing, natomiast usługa AD RMS nie oferuje ich obsługi.

- **Klasyfikacja i etykietowanie**: usługa Azure Information Protection obsługuje te funkcje przy użyciu paska usługi Azure Information Protection zintegrowanego z aplikacjami pakietu Office, natomiast usługa AD RMS nie zapewnia obsługi tych funkcji.


Ponadto — ponieważ usługa Azure Information Protection to usługa w chmurze — może ona dostarczać nowe funkcje i poprawki szybciej niż lokalne rozwiązanie oparte na serwerze. W systemie Windows Server 2016 nie są planowane żadne nowe funkcje usług AD RMS.

Dalsze szczegółowe informacje i inne różnice przedstawiono w poniższej tabeli zawierającej porównanie funkcji usług Azure Information Protection i AD RMS oraz korzyści wynikających z ich używania. Jeśli masz pytania dotyczące porównania w zakresie zabezpieczeń, zobacz sekcję [Formanty kryptograficzne podpisywania i szyfrowania](compare-azure-rms-ad-rms.md#cryptographic-controls-for-signing-and-encryption) tego artykułu.

> [!NOTE]
> Aby ułatwić to porównanie, niektóre informacje podane w tym miejscu są powtórzeniem informacji z artykułu [Wymagania dotyczące usługi Azure Information Protection](../get-started/requirements-azure-rms.md). Użyj tego źródła, aby uzyskać bardziej szczegółową pomoc techniczną oraz informacje o wersji usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

|Azure Information Protection|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Obsługuje usługę zarządzania prawami do informacji (IRM) w usługach Microsoft Online, takich jak Exchange Online i SharePoint Online, a także usłudze Office 365.<br /><br />Obsługuje również lokalne produkty serwerowe firmy Microsoft, takie jak Exchange Server i SharePoint Server, oraz serwery plików z systemem Windows Server i infrastrukturą klasyfikacji plików.|Obsługuje produkty serwerowe firmy Microsoft, takie jak Exchange Server i SharePoint Server, oraz serwery plików z systemem Windows Server i infrastrukturą klasyfikacji plików.|
|Umożliwia nawiązywanie niejawnych relacji zaufania między organizacjami i użytkownikami w dowolnej organizacji. Oznacza to, że chroniona zawartość może być udostępniana między użytkownikami w danej organizacji lub między organizacjami, jeśli użytkownicy mają usługę [!INCLUDE[o365_1](../includes/o365_1_md.md)] lub [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] albo tworzą konta usługi RMS dla użytkowników indywidualnych.|Relacje zaufania muszą być jawnie definiowane w formie bezpośredniej relacji typu punkt-punkt między dwiema organizacjami przy użyciu zaufanych domen użytkowników (TUD) lub federacyjnych relacji zaufania tworzonych za pomocą usług federacyjnych Active Directory (AD FS).|
|Udostępnia dwa domyślne szablony zasad praw, które ograniczają dostęp do zawartości do organizacji użytkownika. Jeden szablon umożliwia przeglądanie chronionej zawartości w trybie tylko do odczytu, a drugi oferuje uprawnienia do zapisu lub modyfikowania chronionej zawartości.<br /><br />Można również tworzyć własne szablony niestandardowe, w tym szablony działu widoczne tylko dla podzbioru użytkowników. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).<br /><br />Ponadto użytkownicy mogą definiować własne zestawy uprawnień, jeśli szablony są niewystarczające.|Nie ma domyślnych szablonów zasad praw — trzeba je utworzyć i dystrybuować. Aby uzyskać więcej informacji, zobacz [Zagadnienia dotyczące szablonów zasad usług AD RMS](http://go.microsoft.com/fwlink/?LinkId=154765).<br /><br />Ponadto użytkownicy mogą definiować własne zestawy uprawnień, jeśli szablony są niewystarczające.|
|Minimalna obsługiwana wersja pakietu Microsoft Office to Office 2010, który wymaga [aplikacji RMS sharing](../rms-client/sharing-app-windows.md).<br /><br />Microsoft Office dla komputerów Mac:<br /><br />– Microsoft Office dla komputerów Mac 2016: obsługiwany<br /><br />– Microsoft Office dla komputerów Mac 2011: nieobsługiwany|Minimalna obsługiwana wersja pakietu Microsoft Office to Office 2007.<br /><br />Microsoft Office dla komputerów Mac:<br /><br />– Microsoft Office dla komputerów Mac 2016: obsługiwany<br /><br />– Microsoft Office dla komputerów Mac 2011: obsługiwany|
|Obsługuje [aplikację do udostępniania usługi RMS](../rms-client/sharing-app-windows.md) dla systemu Windows, komputerów Mac i urządzeń przenośnych.<br /><br />Ponadto aplikacja do udostępniania usługi RMS obsługuje następujące możliwości:<br /><br />– Udostępnianie informacji osobom w innej organizacji.<br /><br />– Powiadomienia e-mail informujące nadawcę o próbie otwarcia chronionego załącznika.<br /><br />– Witryna śledzenia dokumentów dla użytkowników z możliwością odwoływania dokumentu.|Obsługuje [aplikację do udostępniania usługi RMS](../rms-client/sharing-app-windows.md) dla systemu Windows, komputerów Mac i urządzeń przenośnych. Udostępnianie nie dotyczy jednak użytkowników w innej organizacji, powiadomień e-mail ani witryny śledzenia dokumentów z możliwością odwoływania dokumentu.|
|Wszystkie typy plików można objąć [ochroną natywną lub ogólną](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic) przy użyciu aplikacji do udostępniania usługi RMS.<br /><br />W przypadku innych aplikacji zapoznaj się z tabelą w artykule [Aplikacje, które obsługują ochronę danych usługi Azure Rights Management](../get-started/requirements-applications.md).|Wszystkie typy plików można objąć [ochroną natywną lub ogólną](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic) przy użyciu aplikacji do udostępniania usługi RMS.<br /><br />W przypadku innych aplikacji zapoznaj się z tabelą w artykule [Aplikacje, które obsługują ochronę danych usługi Azure Rights Management](../get-started/requirements-applications.md).|
|Minimalna obsługiwana wersja klienta systemu Windows to Windows 7.|Minimalna obsługiwana wersja klienta systemu Windows to Windows Vista z dodatkiem Service Pack 2.|
|Obsługa urządzeń przenośnych dotyczy systemów Windows Phone, Android, iOS i Windows RT.<br /><br />Obsługa poczty e-mail przy użyciu usługi IRM programu Exchange ActiveSync dotyczy również wszystkich platform urządzeń przenośnych z włączoną obsługą tego protokołu.|Obsługa urządzeń przenośnych dotyczy systemów Windows Phone, Android, iOS i Windows RT oraz wymaga [rozszerzenia usług Active Directory Rights Management (AD RMS) dla urządzeń przenośnych](http://technet.microsoft.com/library/dn673574.aspx).<br /><br />Obsługa poczty e-mail przy użyciu usługi IRM programu Exchange ActiveSync dotyczy wszystkich platform urządzeń przenośnych z włączoną obsługą tego protokołu.|
|Obsługuje usługę Multi-Factor Authentication (MFA) na komputerach i urządzeniach przenośnych.<br /><br />Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie wieloskładnikowe i usługa Azure Information Protection](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-rms).|Obsługuje uwierzytelnianie karty inteligentnej, jeśli usługi IIS zostały skonfigurowane do wysyłania żądań certyfikatów.|
|Bez dodatkowej konfiguracji obsługuje tryb kryptograficzny 2, który oferuje lepsze zabezpieczenia długości kluczy i algorytmów szyfrowania.<br /><br />Aby uzyskać więcej informacji, zobacz sekcję [Formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) w tym artykule oraz artykuł [Tryby kryptograficzne usług AD RMS](http://go.microsoft.com/fwlink/?LinkId=266659).|Domyślnie obsługuje tryb kryptograficzny 1 i wymaga dodatkowej konfiguracji do obsługi trybu kryptograficznego 2 w celu uzyskania silniejszych zabezpieczeń.<br /><br />Aby uzyskać więcej informacji, zobacz sekcję [Formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) w tym artykule oraz artykuł [Tryby kryptograficzne usług AD RMS](http://go.microsoft.com/fwlink/?LinkId=266659).|
|Obsługuje migrację z usług AD RMS i w razie potrzeby do usług AD RMS:<br /><br />- [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)<br /><br />- [Likwidowanie i dezaktywowanie usługi Azure Information Protection](../deploy-use/decommission-deactivate.md)|Obsługuje migrację z usługi Azure Information Protection i do usługi Azure Information Protection:<br /><br />- [Likwidowanie i dezaktywowanie usługi Azure Rights Management](../deploy-use/decommission-deactivate.md)<br /><br />- [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)|
|Wymaga licencji usługi Azure Information Protection na potrzeby ochrony zawartości. Do korzystania z zawartości chronionej przez usługę Azure Information Protection (dotyczy również użytkowników z innej organizacji) nie jest wymagana licencja usługi Azure Information Protection.<br /><br />Aby uzyskać więcej informacji, zapoznaj się z [listą funkcji](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection.|Wymaga licencji usługi RMS do ochrony zawartość oraz do korzystania z zawartości chronionej przez usługi AD RMS.<br /><br />Aby uzyskać więcej informacji na temat licencjonowania usług AD RMS, zobacz artykuł [Licencje dostępu klienta i zarządzanie licencjami](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx), aby uzyskać informacje ogólne. Jeśli potrzebujesz informacji szczegółowych, skontaktuj się z partnerem firmy Microsoft lub przedstawicielem firmy Microsoft.|

## Formanty kryptograficzne podpisywania i szyfrowania
Usługa Azure Information Protection zawsze używa szyfrowania RSA 2048 dla wszystkich operacji szyfrowania kluczem publicznym i algorytmu SHA 256 w przypadku operacji podpisywania. Porównując: usługi AD RMS obsługują szyfrowanie RSA 1024 i RSA 2048 oraz algorytm SHA 1 lub SHA 256 w przypadku operacji podpisywania.

Usługi Azure Information Protection i AD RMS używają szyfrowania AES 128 w przypadku szyfrowania symetrycznego.

Usługa Azure Information Protection jest zgodna z trybem FIPS 140-2, jeśli klucz dzierżawy jest tworzony i zarządzany przez firmę Microsoft (opcja domyślna) lub jeśli zarządzasz własnym kluczem dzierżawy (opcja znana jako BYOK). Aby uzyskać więcej informacji na temat zarządzania dzierżawą, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md).

## Następne kroki
Jeśli chcesz przeprowadzić migrację z usługi AD RMS do usługi Azure Information Protection, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)





<!--HONumber=Oct16_HO1-->


