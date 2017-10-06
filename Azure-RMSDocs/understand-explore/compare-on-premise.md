---
title: "Porównanie usług Azure Information Protection i AD RMS"
description: "Jeśli usługa Active Directory Rights Management Services (AD RMS) jest Ci znana lub była wcześniej wdrażana, być może zastanawiasz się, jakie byłyby wyniki porównania jej z usługą Azure Information Protection pod kątem funkcjonalności i wymagań."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/03/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 60765865a0c422f4baac72ed88a6bca9b96ed66f
ms.sourcegitcommit: 4d730631ea8c16c7150b794722bb23921f1b2008
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2017
---
# <a name="comparing-azure-information-protection-and-ad-rms"></a>Porównanie usług Azure Information Protection i AD RMS

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Jeśli usługa Active Directory Rights Management Services (AD RMS) jest Ci znana lub była wcześniej wdrażana, być może zastanawiasz się, jakie byłyby wyniki porównania jej z usługą Azure Information Protection pod kątem funkcjonalności i wymagań rozwiązania do ochrony informacji.

Niektóre główne różnice związane z usługą Azure Information Protection:

- **Brak wymaganej infrastruktury serwerów**: usługa Azure Information Protection nie wymaga dodatkowych serwerów ani certyfikatów PKI, których potrzebują usługi AD RMS, ponieważ te kwestie są obsługiwane na platformie Microsoft Azure. Dzięki temu to rozwiązanie w chmurze jest szybsze do wdrożenia i łatwiejsze w utrzymaniu.

- **Uwierzytelnianie oparte na chmurze**: usługa Azure Information Protection używa usługi Azure AD do uwierzytelniania, zarówno w przypadku użytkowników wewnętrznych, jak i użytkowników z innych organizacji. Oznacza to, że użytkowników mobilnych można uwierzytelnić nawet wtedy, gdy nie są oni połączeni z siecią wewnętrzną, i łatwiej można udostępnić chronioną zawartość użytkownikom z innych organizacji. Wiele organizacji ma już konta użytkowników w usłudze Azure AD, ponieważ działają na nich usługi platformy Azure lub usługa Office 365. W przeciwnym razie usługa RMS dla użytkowników indywidualnych umożliwia użytkownikom tworzenie bezpłatnych kont. Do udostępniania chronionej zawartości usług AD RMS innej organizacji wymagane jest skonfigurowanie relacji jawnego zaufania z każdą organizacją.

- **Wbudowana obsługa urządzeń przenośnych**: aby usługa Azure RMS obsługiwała urządzenia przenośne i komputery Mac, nie trzeba wprowadzać żadnych zmian wdrożenia. Aby obsługiwać te urządzenia za pomocą usług AD RMS, należy zainstalować rozszerzenie dla urządzeń przenośnych, skonfigurować usługi AD FS na potrzeby federacji i utworzyć dodatkowe rekordy publicznej usługi DNS.

- **Szablony domyślne**: usługa Azure Information Protection tworzy dwa szablony domyślne od razu po aktywacji usługi ochrony, dzięki czemu można łatwo natychmiast objąć ochroną ważne dane. Usługa AD RMS nie ma szablonów domyślnych.

- **Szablony działów**: usługa Azure Information Protection obsługuje szablony działów jako ustawienie konfiguracji dodatkowych tworzonych szablonów. To ustawienie umożliwia określenie, którzy użytkownicy widzą szablon w aplikacjach klienckich (np. aplikacjach pakietu Office), dzięki czemu mogą oni łatwiej wybrać prawidłowe zasady zdefiniowane dla różnych grup użytkowników. Usługi AD RMS nie obsługują szablonów działów.

- **Śledzenie i odwoływanie dokumentów**: usługa Azure Information Protection obsługuje te funkcje przy użyciu klienta usługi Azure Information Protection. Usługa AD RMS nie zapewnia obsługi tych funkcji.

- **Klasyfikacja i etykietowanie**: usługa Azure Information Protection obsługuje te funkcje przy użyciu klienta usługi Azure Information Protection zintegrowanego z aplikacjami pakietu Office i Eksploratorem plików, natomiast usługa AD RMS nie zapewnia obsługi tych funkcji.


Ponadto — ponieważ usługa Azure Information Protection to usługa w chmurze — może ona dostarczać nowe funkcje i poprawki szybciej niż lokalne rozwiązanie oparte na serwerze. W systemie Windows Server 2016 nie są planowane żadne nowe funkcje usług AD RMS.

Dalsze szczegółowe informacje i inne różnice przedstawiono w poniższej tabeli zawierającej porównanie funkcji usług Azure Information Protection i AD RMS oraz korzyści wynikających z ich używania. Jeśli masz pytania dotyczące porównania w zakresie zabezpieczeń, zobacz sekcję [Formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) tego artykułu.

> [!NOTE]
> Aby ułatwić to porównanie, niektóre informacje podane w tym miejscu są powtórzeniem informacji z artykułu [Wymagania dotyczące usługi Azure Information Protection](../get-started/requirements-azure-rms.md). Użyj tego źródła, aby uzyskać bardziej szczegółową pomoc techniczną oraz informacje o wersji usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

|Azure Information Protection|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Obsługuje usługę zarządzania prawami do informacji (IRM) w usługach Microsoft Online, takich jak Exchange Online i SharePoint Online, a także usłudze Office 365.<br /><br />Obsługuje również lokalne produkty serwerowe firmy Microsoft, takie jak Exchange Server i SharePoint Server, oraz serwery plików z systemem Windows Server i infrastrukturą klasyfikacji plików.|Obsługuje produkty serwerowe firmy Microsoft, takie jak Exchange Server i SharePoint Server, oraz serwery plików z systemem Windows Server i infrastrukturą klasyfikacji plików.|
|Automatycznie włącza bezpiecznej współpracy nad dokumentami z dowolnego organizację, która również korzysta z usługi Azure AD do uwierzytelniania. Oznacza to, że organizacje mogą chronić dokumenty, które mają wewnętrznych lub z innymi organizacjami.|Bezpiecznej współpracy nad dokumentami spoza organizacji wymaga uwierzytelniania relacji zaufania, aby zostać jawnie zdefiniowany w bezpośredniej relacji point-to-point między dwiema organizacjami. Należy skonfigurować zaufanych domen użytkowników (TUD) lub federacyjnych relacji zaufania tworzonych za pomocą usługi Active Directory Federation Services (AD FS).|
|Wyślij chronionych wiadomości e-mail (opcjonalnie z załączników dokumentu pakietu Office, które są automatycznie chronione) do użytkowników, gdy żadna relacja zaufania uwierzytelniania nie istnieje. Ten scenariusz jest możliwe przy użyciu federacji z dostawców sieci społecznościowych lub jednorazowy kod dostępu i przeglądarki sieci web do wyświetlenia.|Nie obsługuje wysyłanie chronionych wiadomości e-mail, gdy żadna relacja zaufania uwierzytelniania nie istnieje.|
|Udostępnia dwa domyślne szablony zasad praw, które ograniczają dostęp do zawartości do organizacji użytkownika. Jeden szablon umożliwia przeglądanie chronionej zawartości w trybie tylko do odczytu, a drugi oferuje uprawnienia do zapisu lub modyfikowania chronionej zawartości.<br /><br />Można również tworzyć własne szablony niestandardowe, w tym szablony działu widoczne tylko dla podzbioru użytkowników. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](../deploy-use/configure-policy-templates.md).<br /><br />Ponadto użytkownicy mogą definiować własne zestawy uprawnień, jeśli szablony są niewystarczające.|Brak bez szablonów domyślnych; należy utworzyć i dystrybuować. Aby uzyskać więcej informacji, zobacz [Zagadnienia dotyczące szablonów zasad usług AD RMS](http://go.microsoft.com/fwlink/?LinkId=154765).<br /><br />Ponadto użytkownicy mogą definiować własne zestawy uprawnień, jeśli szablony są niewystarczające.|
|Minimalna obsługiwana wersja pakietu Microsoft Office to Office 2010, który wymaga [klienta usługi Azure Information Protection](../rms-client/aip-client.md) lub aplikacji RMS sharing.<br /><br />Microsoft Office dla komputerów Mac:<br /><br />– Microsoft Office dla komputerów Mac 2016: obsługiwany<br /><br />– Microsoft Office dla komputerów Mac 2011: nieobsługiwany|Minimalna obsługiwana wersja pakietu Microsoft Office to Office 2007.<br /><br />Microsoft Office dla komputerów Mac:<br /><br />– Microsoft Office dla komputerów Mac 2016: obsługiwany<br /><br />– Microsoft Office dla komputerów Mac 2011: obsługiwany|
|Obsługuje [klienta usługi Azure Information Protection](../rms-client/aip-client.md) dla systemów Windows, iOS i Android. Komputery Mac i urządzenia Windows Phone w dalszym ciągu są obsługiwane przez aplikację RMS sharing.<br /><br />Ponadto klient usługi Azure Information Protection obsługuje następujące funkcje i elementy:<br /><br />– Udostępnianie informacji osobom w innej organizacji.<br /><br />– Witryna śledzenia dokumentów dla użytkowników z możliwością odwoływania dokumentu.|Obsługuje [klienta usługi Azure Information Protection](../rms-client/aip-client.md) dla systemów Windows, iOS i Android. Komputery Mac i urządzenia Windows Phone w dalszym ciągu są obsługiwane przez aplikację RMS sharing. Udostępnianie nie dotyczy jednak użytkowników w innej organizacji ani witryny śledzenia dokumentów z możliwością odwoływania dokumentu.|
|Korzystając z klienta usługi Azure Information Protection, można klasyfikować i chronić większość [typów plików](../rms-client/client-admin-guide-file-types.md).<br /><br />W przypadku innych aplikacji zapoznaj się z tabelą w artykule [Aplikacje, które obsługują ochronę danych usługi Azure Rights Management](../get-started/requirements-applications.md).|Korzystając z klienta usługi Azure Information Protection, można klasyfikować większość [typów plików](../rms-client/client-admin-guide-file-types.md).<br /><br />W przypadku innych aplikacji zapoznaj się z tabelą w artykule [Aplikacje, które obsługują ochronę danych usługi Azure Rights Management](../get-started/requirements-applications.md).|
|Minimalna obsługiwana wersja klienta systemu Windows to Windows 7 z dodatkiem SP1.|Minimalna obsługiwana wersja klienta systemu Windows to Windows Vista z dodatkiem Service Pack 2.|
|Obsługa urządzeń przenośnych dotyczy systemów Windows Phone, Android, iOS i Windows RT.<br /><br />Obsługa poczty e-mail przy użyciu usługi IRM programu Exchange ActiveSync dotyczy również wszystkich platform urządzeń przenośnych z włączoną obsługą tego protokołu.|Obsługa urządzeń przenośnych dotyczy systemów Windows Phone, Android, iOS i Windows RT oraz wymaga [rozszerzenia usług Active Directory Rights Management (AD RMS) dla urządzeń przenośnych](http://technet.microsoft.com/library/dn673574.aspx).<br /><br />Obsługa poczty e-mail przy użyciu usługi IRM programu Exchange ActiveSync dotyczy wszystkich platform urządzeń przenośnych z włączoną obsługą tego protokołu.|
|Obsługuje usługę Multi-Factor Authentication (MFA) na komputerach i urządzeniach przenośnych.<br /><br />Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie wieloskładnikowe i usługa Azure Information Protection](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-information-protection).|Obsługuje uwierzytelnianie karty inteligentnej, jeśli usługi IIS zostały skonfigurowane do wysyłania żądań certyfikatów.|
|Bez dodatkowej konfiguracji obsługuje tryb kryptograficzny 2, który oferuje lepsze zabezpieczenia długości kluczy i algorytmów szyfrowania.<br /><br />Aby uzyskać więcej informacji, zobacz sekcję [Formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) w tym artykule oraz artykuł [Tryby kryptograficzne usług AD RMS](http://go.microsoft.com/fwlink/?LinkId=266659).|Domyślnie obsługuje tryb kryptograficzny 1 i wymaga dodatkowej konfiguracji do obsługi trybu kryptograficznego 2 w celu uzyskania silniejszych zabezpieczeń.<br /><br />Aby uzyskać więcej informacji, zobacz sekcję [Formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) w tym artykule oraz artykuł [Tryby kryptograficzne usług AD RMS](http://go.microsoft.com/fwlink/?LinkId=266659).|
|Obsługuje migrację z usług AD RMS i w razie potrzeby do usług AD RMS:<br /><br />- [Migrowanie z usług AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)<br /><br />- [Likwidowanie i dezaktywowanie usługi Azure Information Protection](../deploy-use/decommission-deactivate.md)|Obsługuje migrację z usługi Azure Information Protection i do usługi Azure Information Protection:<br /><br />- [Likwidowanie i dezaktywowanie usługi Azure Rights Management](../deploy-use/decommission-deactivate.md)<br /><br />- [Migrowanie z usług AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)|
|Aby możliwe było stosowanie funkcji ochrony zawartości, wymagana jest licencja usługi Azure Information Protection lub Azure Rights Management z usługą Office 365. Do korzystania z zawartości chronionej przez usługę Azure Information Protection (dotyczy również użytkowników z innej organizacji) nie jest wymagana żadna licencja.<br /><br />Aby uzyskać więcej informacji, zapoznaj się z [listą funkcji](https://www.microsoft.com/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection.|Wymaga licencji usługi RMS do ochrony zawartość oraz do korzystania z zawartości chronionej przez usługi AD RMS.<br /><br />Aby uzyskać więcej informacji na temat licencjonowania usług AD RMS, zobacz artykuł [Licencje dostępu klienta i zarządzanie licencjami](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx), aby uzyskać informacje ogólne. Jeśli potrzebujesz informacji szczegółowych, skontaktuj się z partnerem firmy Microsoft lub przedstawicielem firmy Microsoft.|

## <a name="cryptographic-controls-for-signing-and-encryption"></a>Formanty kryptograficzne podpisywania i szyfrowania
Usługa Azure Information Protection domyślnie używa szyfrowania RSA 2048 dla wszystkich operacji szyfrowania kluczem publicznym i algorytmu SHA 256 w przypadku operacji podpisywania. Porównując: usługi AD RMS obsługują szyfrowanie RSA 1024 i RSA 2048 oraz algorytm SHA 1 lub SHA 256 w przypadku operacji podpisywania.

Usługi Azure Information Protection i AD RMS używają szyfrowania AES 128 w przypadku szyfrowania symetrycznego.

Usługa Azure Information Protection jest zgodna z FIPS 140-2, gdy rozmiar klucza dzierżawy wynosi 2048 bitów i jest to ustawienie domyślne po aktywowaniu usługi Azure Rights Management. 

Aby uzyskać więcej informacji na temat formantów kryptograficznych, zobacz temat [Formanty kryptograficzne używane przez usługę Azure RMS: algorytmy i długości kluczy](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).


## <a name="next-steps"></a>Następne kroki
Jeśli chcesz przeprowadzić migrację z usługi AD RMS do usługi Azure Information Protection, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

