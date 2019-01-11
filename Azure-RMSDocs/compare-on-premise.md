---
title: Porównanie usługi Azure Information Protection i AD RMS — AIP
description: Jeśli usługa Active Directory Rights Management Services (AD RMS) jest Ci znana lub była wcześniej wdrażana, być może zastanawiasz się, jakie byłyby wyniki porównania jej z usługą Azure Information Protection pod kątem funkcjonalności i wymagań.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 127b1c00a3b9e76da5b05032ef93287399cf0db7
ms.sourcegitcommit: bc082cffaa698b89b28aef7034290553c26f667b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411834"
---
# <a name="comparing-azure-information-protection-and-ad-rms"></a>Porównanie usług Azure Information Protection i AD RMS

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Jeśli jest Ci znana lub była wcześniej wdrażana Active Directory Rights Management Services (AD RMS), być może zastanawiasz się, porównanie usługi Azure Information Protection pod kątem funkcjonalności i wymagań jako rozwiązania do ochrony informacji.

Niektóre główne różnice związane z usługą Azure Information Protection:

- **Brak wymaganej infrastruktury serwerów**: Usługa Azure Information Protection nie wymaga dodatkowych serwerów ani certyfikatów PKI, których potrzebuje usług AD RMS, ponieważ Microsoft Azure dba o tych dla Ciebie. Dzięki temu to rozwiązanie w chmurze jest szybsze do wdrożenia i łatwiejsze w utrzymaniu.

- **Uwierzytelnianie oparte na chmurze**: Usługa Azure Information Protection używa usługi Azure AD do uwierzytelniania, zarówno w przypadku użytkowników wewnętrznych, jak i użytkowników z innych organizacji. Oznacza to, że użytkowników mobilnych można uwierzytelnić nawet wtedy, gdy nie są oni połączeni z siecią wewnętrzną, i łatwiej można udostępnić chronioną zawartość użytkownikom z innych organizacji. Wiele organizacji ma już konta użytkowników w usłudze Azure AD, ponieważ działają na nich usługi platformy Azure lub usługa Office 365. Ale jeśli nie, usługa RMS dla użytkowników indywidualnych umożliwia użytkownikom tworzenie bezpłatnego konta lub konta Microsoft, może służyć do [aplikacje, które obsługują uwierzytelnianie usługi Azure Information Protection](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents). Do udostępniania chronionej zawartości usług AD RMS innej organizacji wymagane jest skonfigurowanie relacji jawnego zaufania z każdą organizacją.

- **Wbudowana obsługa urządzeń przenośnych**: Aby usługa Azure RMS obsługiwała urządzenia przenośne i komputery Mac są wymagane żadne zmiany wdrożenia. Aby obsługiwać te urządzenia za pomocą usług AD RMS, należy zainstalować rozszerzenie dla urządzeń przenośnych, skonfigurować usługi AD FS na potrzeby federacji i utworzyć dodatkowe rekordy publicznej usługi DNS.

- **Szablony domyślne**: Usługa Azure Information Protection tworzy domyślne szablony natychmiast po aktywacji usługi ochrony, który można łatwo natychmiast objąć ochroną ważne dane. Usługa AD RMS nie ma szablonów domyślnych.

- **Szablony dla działów**: Znany także jako szablony o określonym zakresie. Usługa Azure Information Protection obsługuje szablony działów dodatkowych tworzonych szablonów. Ta konfiguracja pozwala określić podzbiór użytkowników, aby wyświetlić określone szablony w aplikacjach klienckich. Ograniczenie liczby szablonów, które użytkownicy zobaczą sprawia, że jest ona łatwiej wybrać prawidłowe zasady zdefiniowane dla różnych grup użytkowników. Usługi AD RMS nie obsługują szablonów działów.

- **Śledzenie i odwoływanie dokumentów**: Usługa Azure Information Protection obsługuje te funkcje przy użyciu klienta usługi Azure Information Protection, natomiast Usługa AD RMS nie zapewnia.

- **Klasyfikacja i etykietowanie**: Usługa Azure Information Protection obsługuje te funkcje przy użyciu klienta usługi Azure Information Protection, która integruje się z aplikacjami pakietu Office i Eksploratorem plików, natomiast Usługa AD RMS nie zapewnia. 


Ponadto — ponieważ usługa Azure Information Protection to usługa w chmurze — może ona dostarczać nowe funkcje i poprawki szybciej niż lokalne rozwiązanie oparte na serwerze. Nie istnieją żadne nowe funkcje zaplanowane dla usług AD RMS w systemie Windows Server.

Aby uzyskać więcej szczegółowych informacji i inne różnice skorzystaj z poniższej tabeli dla porównania side-by-side, funkcji i zalet usługi Azure Information Protection i AD RMS. Jeśli masz pytania dotyczące porównania w zakresie zabezpieczeń, zobacz sekcję [Formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) tego artykułu.

> [!NOTE]
> Aby ułatwić to porównanie, niektóre informacje podane w tym miejscu są powtórzeniem informacji z artykułu [Wymagania dotyczące usługi Azure Information Protection](requirements.md). Aby uzyskać bardziej szczegółowe informacje pomocy technicznej i wersji usługi Azure Rights Management, należy użyć tego źródła.

|Azure Information Protection|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Obsługuje informacji na temat usługi rights management (IRM) funkcji w usługach Online firmy Microsoft, takich jak Exchange Online i SharePoint Online, a także usługi Office 365.<br /><br />Obsługuje również lokalne produkty serwerowe firmy Microsoft, takich jak Exchange Server, SharePoint Server i serwery plików, z systemem Windows Server i infrastrukturą klasyfikacji plików (FCI).|Obsługuje lokalne produkty serwerowe firmy Microsoft, takich jak Exchange Server, SharePoint Server i serwery plików, z systemem Windows Server i infrastrukturą klasyfikacji plików (FCI).|
|Automatycznie włącza bezpiecznej współpracy nad dokumentami z dowolnej organizacji, która również używa usługi Azure AD do uwierzytelniania. Oznacza to, że organizacje będą mogli chronić dokumenty, które współużytkują one wewnętrznie lub z innymi organizacjami.|Bezpiecznej współpracy nad dokumentami spoza organizacji wymaga uwierzytelniania zaufania jawnie zdefiniowanych w bezpośredniej relacji point-to-point między dwiema organizacjami. Należy skonfigurować zaufanych domen użytkowników (TUD) lub federacyjnych relacji zaufania, które tworzysz przy użyciu usługi Active Directory Federation Services (AD FS).|
|Wysłać chronioną wiadomość e-mail (opcjonalnie, za pomocą załączników dokumentu pakietu Office, które są automatycznie chronione) do użytkowników, gdy istnieje relacja zaufania uwierzytelniania. W tym scenariuszu jest możliwe przy użyciu Federacji dostawców sieci społecznościowych lub jednorazowy kod dostępu i przeglądarki sieci web do wyświetlenia.|Nie obsługuje wysyłanie chronionych wiadomości e-mail, gdy istnieje relacja zaufania uwierzytelniania.|
|Udostępnia domyślne szablony ochrony, które ograniczają dostęp do zawartości do Twojej organizacji; jeden, który zawiera tylko do odczytu przeglądanie chronionej zawartości i inny szablon, który zapewnia zapisu lub modyfikowania uprawnień dla zawartości chronionej.<br /><br />Można również utworzyć własne szablony niestandardowe, które obejmują szablony dla działów, które są widoczne tylko dla podzbioru użytkowników. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md).<br /><br />Ponadto użytkownicy mogą definiować własne zestawy uprawnień, jeśli szablony są niewystarczające.|Brak szablonów domyślną; należy utworzyć, a następnie dystrybucję własnych szablonów. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące szablonów zasad AD RMS](https://go.microsoft.com/fwlink/?LinkId=154765).<br /><br />Ponadto użytkownicy mogą definiować własne zestawy uprawnień, jeśli szablony są niewystarczające.|
|Minimalna obsługiwana wersja pakietu Microsoft Office to Office 2010, który wymaga [klienta Azure Information Protection](./rms-client/aip-client.md) lub aplikację RMS sharing.<br /><br />Microsoft Office dla komputerów Mac:<br /><br />– Microsoft Office dla komputerów Mac 2016: Obsługiwane|Minimalna obsługiwana wersja pakietu Microsoft Office to Office 2010.<br /><br />Microsoft Office dla komputerów Mac:<br /><br />– Microsoft Office dla komputerów Mac 2016: Obsługiwane|
|Obsługuje [klienta usługi Azure Information Protection](./rms-client/aip-client.md) dla systemów Windows, iOS i Android. Komputery Mac i Windows Phone, nadal są obsługiwane przez aplikację RMS sharing.<br /><br />Ponadto klient usługi Azure Information Protection obsługuje następujące funkcje i elementy:<br /><br />– Udostępnianie informacji osobom w innej organizacji.<br /><br />– Witryna śledzenia dokumentów dla użytkowników z możliwością odwoływania dokumentu.|Obsługuje [klienta usługi Azure Information Protection](./rms-client/aip-client.md) dla systemów Windows, iOS i Android. Komputery Mac i urządzenia Windows Phone w dalszym ciągu są obsługiwane przez aplikację RMS sharing. Udostępnianie nie dotyczy jednak użytkowników w innej organizacji ani witryny śledzenia dokumentów z możliwością odwoływania dokumentu.|
|Korzystając z klienta usługi Azure Information Protection, można klasyfikować i chronić większość [typów plików](./rms-client/client-admin-guide-file-types.md).<br /><br />W przypadku innych aplikacji zapoznaj się z tabelą w artykule [Aplikacje, które obsługują ochronę danych usługi Azure Rights Management](./requirements-applications.md).|Korzystając z klienta usługi Azure Information Protection, można klasyfikować większość [typów plików](./rms-client/client-admin-guide-file-types.md).<br /><br />W przypadku innych aplikacji zapoznaj się z tabelą w artykule [Aplikacje, które obsługują ochronę danych usługi Azure Rights Management](./requirements-applications.md).|
|Minimalna obsługiwana wersja klienta Windows to Windows 7 z dodatkiem SP1.|Minimalna obsługiwana wersja klienta Windows to Windows 7 z dodatkiem SP1.|
|Obsługa urządzeń przenośnych dotyczy Windows Phone, Android, iOS i Windows RT.<br /><br />Pomoc techniczna pocztą e-mail za pomocą programu Exchange ActiveSync IRM jest również obsługiwana na wszystkich platformach urządzeń przenośnych, które obsługują tego protokołu.|Obsługa urządzeń przenośnych dotyczy Windows Phone, Android, iOS i Windows RT oraz wymaga [Active Directory Rights zarządzania rozszerzenia usług urządzeń przenośnych](https://technet.microsoft.com/library/dn673574.aspx).<br /><br />Obsługa poczty e-mail przy użyciu usługi IRM programu Exchange ActiveSync dotyczy wszystkich platform urządzeń przenośnych z włączoną obsługą tego protokołu.|
|Obsługuje usługę Multi-Factor Authentication (MFA) na komputerach i urządzeniach przenośnych.<br /><br />Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie wieloskładnikowe i usługa Azure Information Protection](./requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-information-protection).|Obsługuje uwierzytelnianie karty inteligentnej, jeśli usługi IIS zostały skonfigurowane do wysyłania żądań certyfikatów.|
|Obsługuje tryb kryptograficzny 2 bez dodatkowej konfiguracji, który oferuje lepsze zabezpieczenia długości kluczy i algorytmów szyfrowania.<br /><br />Aby uzyskać więcej informacji, zobacz [formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) sekcję w tym artykule i [tryby kryptograficzne usług AD RMS](https://go.microsoft.com/fwlink/?LinkId=266659).|Domyślnie obsługuje trybu kryptograficznego 1 i wymaga dodatkowej konfiguracji do obsługi trybu kryptograficznego 2 w celu uzyskania silniejszych zabezpieczeń.<br /><br />Aby uzyskać więcej informacji, zobacz [formanty kryptograficzne podpisywania i szyfrowania](#cryptographic-controls-for-signing-and-encryption) sekcję w tym artykule i [tryby kryptograficzne usług AD RMS](https://go.microsoft.com/fwlink/?LinkId=266659).|
|Obsługuje migrację z usług AD RMS i w razie potrzeby do usług AD RMS:<br /><br />- [Migrowanie z usług AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)<br /><br />- [Likwidowanie i dezaktywowanie usługi Azure Information Protection](decommission-deactivate.md)|Obsługuje migrację z usługi Azure Information Protection i do usługi Azure Information Protection:<br /><br />- [Likwidowanie i dezaktywowanie usługi Azure Rights Management](decommission-deactivate.md)<br /><br />- [Migrowanie z usług AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)|
|Aby możliwe było stosowanie funkcji ochrony zawartości, wymagana jest licencja usługi Azure Information Protection lub Azure Rights Management z usługą Office 365. Do korzystania z zawartości chronionej przez usługę Azure Information Protection (dotyczy również użytkowników z innej organizacji) nie jest wymagana żadna licencja.<br /><br />Aby uzyskać więcej informacji, zapoznaj się z [listą funkcji](https://www.microsoft.com/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection.|Wymaga licencji usługi RMS do ochrony zawartość oraz do korzystania z zawartości chronionej przez usługi AD RMS.<br /><br />Aby uzyskać więcej informacji na temat licencjonowania usług AD RMS, zobacz artykuł [Licencje dostępu klienta i zarządzanie licencjami](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx), aby uzyskać informacje ogólne. Jeśli potrzebujesz informacji szczegółowych, skontaktuj się z partnerem firmy Microsoft lub przedstawicielem firmy Microsoft.|

## <a name="cryptographic-controls-for-signing-and-encryption"></a>Formanty kryptograficzne podpisywania i szyfrowania
Usługa Azure Information Protection domyślnie używa szyfrowania RSA 2048 dla wszystkich kluczem publicznym i algorytmu SHA 256 w przypadku operacji podpisywania. W odróżnieniu od usługi AD RMS obsługują szyfrowanie RSA 1024 i RSA 2048 oraz algorytm SHA 1 lub SHA 256 w przypadku operacji podpisywania.

Zarówno usługi Azure Information Protection i AD RMS używają szyfrowania AES 128 w przypadku szyfrowania symetrycznego.

Usługa Azure Information Protection jest zgodna z trybem FIPS 140-2, gdy dzierżawy rozmiar klucza to 2048 bitów, co jest ustawieniem domyślnym, po aktywowaniu usługi Azure Rights Management. 

Aby uzyskać więcej informacji na temat formantów kryptograficznych, zobacz [formanty kryptograficzne używane przez usługę Azure RMS: Algorytmy i długości kluczy](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).


## <a name="next-steps"></a>Następne kroki
Jeśli chcesz przeprowadzić migrację z usługi AD RMS do usługi Azure Information Protection, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)


