---
title: Porównanie usług Azure Information Protection i AD RMS
description: Jeśli usługa Active Directory Rights Management Services (AD RMS) jest Ci znana lub była wcześniej wdrażana, być może zastanawiasz się, jakie byłyby wyniki porównania jej z usługą Azure Information Protection pod kątem funkcjonalności i wymagań.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/16/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: bc93e9674c2f37f1e78487e5c5d051d63a5ed630
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42804767"
---
# <a name="comparing-azure-information-protection-and-ad-rms"></a>Porównanie usług Azure Information Protection i AD RMS

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Jeśli usługa Active Directory Rights Management Services (AD RMS) jest Ci znana lub była wcześniej wdrażana, być może zastanawiasz się, jakie byłyby wyniki porównania jej z usługą Azure Information Protection pod kątem funkcjonalności i wymagań rozwiązania do ochrony informacji.

Niektóre główne różnice związane z usługą Azure Information Protection:

- **Brak wymaganej infrastruktury serwerów**: Azure Information Protection nie wymaga dodatkowych serwerów ani certyfikatów PKI, których potrzebuje usług AD RMS, ponieważ Microsoft Azure dba o tych dla Ciebie. Dzięki temu to rozwiązanie w chmurze jest szybsze do wdrożenia i łatwiejsze w utrzymaniu.

- **Uwierzytelnianie oparte na chmurze**: usługa Azure Information Protection używa usługi Azure AD do uwierzytelniania, zarówno w przypadku użytkowników wewnętrznych, jak i użytkowników z innych organizacji. Oznacza to, że użytkowników mobilnych można uwierzytelnić nawet wtedy, gdy nie są oni połączeni z siecią wewnętrzną, i łatwiej można udostępnić chronioną zawartość użytkownikom z innych organizacji. Wiele organizacji ma już konta użytkowników w usłudze Azure AD, ponieważ działają na nich usługi platformy Azure lub usługa Office 365. Ale jeśli nie, usługa RMS dla użytkowników indywidualnych umożliwia użytkownikom tworzenie bezpłatnego konta lub konta Microsoft, może służyć do [aplikacje, które obsługują uwierzytelnianie usługi Azure Information Protection](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents). Do udostępniania chronionej zawartości usług AD RMS innej organizacji wymagane jest skonfigurowanie relacji jawnego zaufania z każdą organizacją.

- **Wbudowana obsługa urządzeń przenośnych**: aby usługa Azure RMS obsługiwała urządzenia przenośne i komputery Mac, nie trzeba wprowadzać żadnych zmian wdrożenia. Aby obsługiwać te urządzenia za pomocą usług AD RMS, należy zainstalować rozszerzenie dla urządzeń przenośnych, skonfigurować usługi AD FS na potrzeby federacji i utworzyć dodatkowe rekordy publicznej usługi DNS.

- **Szablony domyślne**: Azure Information Protection tworzy dwa szablony domyślne, zaraz po aktywacji usługi ochrony, który można łatwo natychmiast objąć ochroną ważne dane. Usługa AD RMS nie ma szablonów domyślnych.

- **Szablony działów**: usługa Azure Information Protection obsługuje szablony działów jako ustawienie konfiguracji dodatkowych tworzonych szablonów. Ta konfiguracja pozwala określić podzbiór użytkowników, aby wyświetlić określone szablony w aplikacjach klienckich. Ograniczenie liczby szablonów, które użytkownicy zobaczą sprawia, że jest ona łatwiej wybrać prawidłowe zasady zdefiniowane dla różnych grup użytkowników. Usługi AD RMS nie obsługują szablonów działów.

- **Śledzenie i odwoływanie dokumentów**: usługa Azure Information Protection obsługuje te funkcje przy użyciu klienta usługi Azure Information Protection. Usługa AD RMS nie zapewnia obsługi tych funkcji.

- **Klasyfikacja i etykietowanie**: usługa Azure Information Protection obsługuje te funkcje przy użyciu klienta usługi Azure Information Protection zintegrowanego z aplikacjami pakietu Office i Eksploratorem plików, natomiast usługa AD RMS nie zapewnia obsługi tych funkcji.


Ponadto — ponieważ usługa Azure Information Protection to usługa w chmurze — może ona dostarczać nowe funkcje i poprawki szybciej niż lokalne rozwiązanie oparte na serwerze. W systemie Windows Server 2016 nie są planowane żadne nowe funkcje usług AD RMS.

Dalsze szczegółowe informacje i inne różnice przedstawiono w poniższej tabeli zawierającej porównanie funkcji usług Azure Information Protection i AD RMS oraz korzyści wynikających z ich używania. Jeśli masz pytania dotyczące porównania w zakresie zabezpieczeń, zobacz sekcję [Formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) tego artykułu.

> [!NOTE]
> Aby ułatwić to porównanie, niektóre informacje podane w tym miejscu są powtórzeniem informacji z artykułu [Wymagania dotyczące usługi Azure Information Protection](requirements.md). Aby uzyskać bardziej szczegółowe informacje pomocy technicznej i wersji usługi Azure Rights Management, należy użyć tego źródła.

|Azure Information Protection|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Obsługuje usługę zarządzania prawami do informacji (IRM) w usługach Microsoft Online, takich jak Exchange Online i SharePoint Online, a także usłudze Office 365.<br /><br />Obsługuje również lokalne produkty serwerowe firmy Microsoft, takie jak Exchange Server i SharePoint Server, oraz serwery plików z systemem Windows Server i infrastrukturą klasyfikacji plików.|Obsługuje produkty serwerowe firmy Microsoft, takie jak Exchange Server i SharePoint Server, oraz serwery plików z systemem Windows Server i infrastrukturą klasyfikacji plików.|
|Automatycznie włącza bezpiecznej współpracy nad dokumentami z dowolnej organizacji, która również używa usługi Azure AD do uwierzytelniania. Oznacza to, że organizacje będą mogli chronić dokumenty, które współużytkują one wewnętrznie lub z innymi organizacjami.|Bezpiecznej współpracy nad dokumentami spoza organizacji wymaga uwierzytelniania zaufania jawnie zdefiniowanych w bezpośredniej relacji point-to-point między dwiema organizacjami. Należy skonfigurować zaufanych domen użytkowników (TUD) lub federacyjnych relacji zaufania, które tworzysz przy użyciu usługi Active Directory Federation Services (AD FS).|
|Wysłać chronioną wiadomość e-mail (opcjonalnie, za pomocą załączników dokumentu pakietu Office, które są automatycznie chronione) do użytkowników, gdy istnieje relacja zaufania uwierzytelniania. W tym scenariuszu jest możliwe przy użyciu Federacji dostawców sieci społecznościowych lub jednorazowy kod dostępu i przeglądarki sieci web do wyświetlenia.|Nie obsługuje wysyłanie chronionych wiadomości e-mail, gdy istnieje relacja zaufania uwierzytelniania.|
|Udostępnia dwa domyślne szablony zasad praw, które ograniczają dostęp do zawartości do organizacji użytkownika. Jeden szablon umożliwia przeglądanie chronionej zawartości w trybie tylko do odczytu, a drugi oferuje uprawnienia do zapisu lub modyfikowania chronionej zawartości.<br /><br />Można również utworzyć własne szablony niestandardowe, które obejmują szablony dla działów, które są widoczne tylko dla podzbioru użytkowników. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md).<br /><br />Ponadto użytkownicy mogą definiować własne zestawy uprawnień, jeśli szablony są niewystarczające.|Brak szablonów domyślną; należy utworzyć, a następnie dystrybucję własnych szablonów. Aby uzyskać więcej informacji, zobacz [Zagadnienia dotyczące szablonów zasad usług AD RMS](http://go.microsoft.com/fwlink/?LinkId=154765).<br /><br />Ponadto użytkownicy mogą definiować własne zestawy uprawnień, jeśli szablony są niewystarczające.|
|Minimalna obsługiwana wersja pakietu Microsoft Office to Office 2010, który wymaga [klienta usługi Azure Information Protection](./rms-client/aip-client.md) lub aplikacji RMS sharing.<br /><br />Microsoft Office dla komputerów Mac:<br /><br />– Microsoft Office dla komputerów Mac 2016: obsługiwany|Minimalna obsługiwana wersja pakietu Microsoft Office to Office 2010.<br /><br />Microsoft Office dla komputerów Mac:<br /><br />– Microsoft Office dla komputerów Mac 2016: obsługiwany|
|Obsługuje [klienta usługi Azure Information Protection](./rms-client/aip-client.md) dla systemów Windows, iOS i Android. Komputery Mac i Windows Phone, nadal są obsługiwane przez aplikację RMS sharing.<br /><br />Ponadto klient usługi Azure Information Protection obsługuje następujące funkcje i elementy:<br /><br />– Udostępnianie informacji osobom w innej organizacji.<br /><br />– Witryna śledzenia dokumentów dla użytkowników z możliwością odwoływania dokumentu.|Obsługuje [klienta usługi Azure Information Protection](./rms-client/aip-client.md) dla systemów Windows, iOS i Android. Komputery Mac i urządzenia Windows Phone w dalszym ciągu są obsługiwane przez aplikację RMS sharing. Udostępnianie nie dotyczy jednak użytkowników w innej organizacji ani witryny śledzenia dokumentów z możliwością odwoływania dokumentu.|
|Korzystając z klienta usługi Azure Information Protection, można klasyfikować i chronić większość [typów plików](./rms-client/client-admin-guide-file-types.md).<br /><br />W przypadku innych aplikacji zapoznaj się z tabelą w artykule [Aplikacje, które obsługują ochronę danych usługi Azure Rights Management](./requirements-applications.md).|Korzystając z klienta usługi Azure Information Protection, można klasyfikować większość [typów plików](./rms-client/client-admin-guide-file-types.md).<br /><br />W przypadku innych aplikacji zapoznaj się z tabelą w artykule [Aplikacje, które obsługują ochronę danych usługi Azure Rights Management](./requirements-applications.md).|
|Minimalna obsługiwana wersja klienta systemu Windows to Windows 7 z dodatkiem SP1.|Minimalna obsługiwana wersja klienta systemu Windows to Windows 7 z dodatkiem SP1.|
|Obsługa urządzeń przenośnych dotyczy systemów Windows Phone, Android, iOS i Windows RT.<br /><br />Obsługa poczty e-mail przy użyciu usługi IRM programu Exchange ActiveSync dotyczy również wszystkich platform urządzeń przenośnych z włączoną obsługą tego protokołu.|Obsługa urządzeń przenośnych dotyczy systemów Windows Phone, Android, iOS i Windows RT oraz wymaga [rozszerzenia usług Active Directory Rights Management (AD RMS) dla urządzeń przenośnych](http://technet.microsoft.com/library/dn673574.aspx).<br /><br />Obsługa poczty e-mail przy użyciu usługi IRM programu Exchange ActiveSync dotyczy wszystkich platform urządzeń przenośnych z włączoną obsługą tego protokołu.|
|Obsługuje usługę Multi-Factor Authentication (MFA) na komputerach i urządzeniach przenośnych.<br /><br />Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie wieloskładnikowe i usługa Azure Information Protection](./requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-information-protection).|Obsługuje uwierzytelnianie karty inteligentnej, jeśli usługi IIS zostały skonfigurowane do wysyłania żądań certyfikatów.|
|Bez dodatkowej konfiguracji obsługuje tryb kryptograficzny 2, który oferuje lepsze zabezpieczenia długości kluczy i algorytmów szyfrowania.<br /><br />Aby uzyskać więcej informacji, zobacz sekcję [Formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) w tym artykule oraz artykuł [Tryby kryptograficzne usług AD RMS](http://go.microsoft.com/fwlink/?LinkId=266659).|Domyślnie obsługuje tryb kryptograficzny 1 i wymaga dodatkowej konfiguracji do obsługi trybu kryptograficznego 2 w celu uzyskania silniejszych zabezpieczeń.<br /><br />Aby uzyskać więcej informacji, zobacz sekcję [Formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) w tym artykule oraz artykuł [Tryby kryptograficzne usług AD RMS](http://go.microsoft.com/fwlink/?LinkId=266659).|
|Obsługuje migrację z usług AD RMS i w razie potrzeby do usług AD RMS:<br /><br />- [Migrowanie z usług AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)<br /><br />- [Likwidowanie i dezaktywowanie usługi Azure Information Protection](decommission-deactivate.md)|Obsługuje migrację z usługi Azure Information Protection i do usługi Azure Information Protection:<br /><br />- [Likwidowanie i dezaktywowanie usługi Azure Rights Management](decommission-deactivate.md)<br /><br />- [Migrowanie z usług AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)|
|Aby możliwe było stosowanie funkcji ochrony zawartości, wymagana jest licencja usługi Azure Information Protection lub Azure Rights Management z usługą Office 365. Nie jest wymagana licencja na korzystanie z zawartości chronionej przez usługę Azure Information Protection (. / dotyczy również użytkowników z innej organizacji).<br /><br />Aby uzyskać więcej informacji, zapoznaj się z [listą funkcji](https://www.microsoft.com/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection.|Wymaga licencji usługi RMS do ochrony zawartość oraz do korzystania z zawartości chronionej przez usługi AD RMS.<br /><br />Aby uzyskać więcej informacji na temat licencjonowania usług AD RMS, zobacz artykuł [Licencje dostępu klienta i zarządzanie licencjami](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx), aby uzyskać informacje ogólne. Jeśli potrzebujesz informacji szczegółowych, skontaktuj się z partnerem firmy Microsoft lub przedstawicielem firmy Microsoft.|

## <a name="cryptographic-controls-for-signing-and-encryption"></a>Formanty kryptograficzne podpisywania i szyfrowania
Usługa Azure Information Protection domyślnie używa szyfrowania RSA 2048 dla wszystkich operacji szyfrowania kluczem publicznym i algorytmu SHA 256 w przypadku operacji podpisywania. Porównując: usługi AD RMS obsługują szyfrowanie RSA 1024 i RSA 2048 oraz algorytm SHA 1 lub SHA 256 w przypadku operacji podpisywania.

Usługi Azure Information Protection i AD RMS używają szyfrowania AES 128 w przypadku szyfrowania symetrycznego.

Usługa Azure Information Protection jest zgodna z trybem FIPS 140-2, gdy dzierżawy rozmiar klucza to 2048 bitów, co jest ustawieniem domyślnym, po aktywowaniu usługi Azure Rights Management. 

Aby uzyskać więcej informacji na temat formantów kryptograficznych, zobacz temat [Formanty kryptograficzne używane przez usługę Azure RMS: algorytmy i długości kluczy](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).


## <a name="next-steps"></a>Kolejne kroki
Jeśli chcesz przeprowadzić migrację z usługi AD RMS do usługi Azure Information Protection, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)

