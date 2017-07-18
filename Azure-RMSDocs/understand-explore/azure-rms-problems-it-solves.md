---
title: "Problemy rozwiązywane przez usługę Azure Rights Management — AIP"
description: "Identyfikowanie wymagań lub problemów, które może mieć organizacja, a także poznanie sposobów ich rozwiązywania przy użyciu technologii Azure RMS."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/26/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: b551c62d-5ac6-4359-85b3-90693e77b37f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 65b9d369308505e74e0dde8d96973f9985d209a0
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="what-problems-does-azure-rms-solve"></a>Jakie problemy rozwiązuje usługa Azure RMS?

>*Dotyczy: Azure Information Protection, Office 365*

Użyj poniższej tabeli, aby zidentyfikować wymagania biznesowe lub problemy, które może mieć organizacja w zakresie ochrony dokumentów i wiadomości e-mail, a także poznać sposoby ich rozwiązywania przy użyciu technologii Azure Rights Management (Azure RMS).

Azure RMS to technologia ochrony używana przez usługę [Azure Information Protection](what-is-information-protection.md).

|Wymaganie lub problem|Rozwiązanie przy użyciu usługi Azure RMS|
|--------------------------|-----------------------|
|Ochrona wielu typów plików|√ We wczesnych implementacjach usługi Rights Management tylko pliki pakietu Office mogły być chronione za pomocą ochrony natywnej usługi Rights Management. Teraz **ochrona ogólna**, która była najpierw oferowana przez aplikację do udostępniania usługi Rights Management, a teraz jest oferowana przez klienta usługi Information Protection oznacza, że obsługiwanych jest więcej [typów plików](../rms-client/client-admin-guide-file-types.md).|
|Ochrona plików w każdym miejscu|√ Gdy plik jest [chroniony](../rms-client/client-classify-protect.md), ochrona jest z nim skojarzona, nawet jeśli plik zostanie zapisany lub skopiowany do magazynu pozostającego poza kontrolą działu IT (np. do usługi w chmurze).|
|Bezpieczne udostępnianie informacji|√ Gdy plik jest [chroniony](../rms-client/client-classify-protect.md), można go bezpiecznie udostępniać innym osobom. Na przykład załącznik do wiadomości e-mail lub link do witryny programu SharePoint. Jeśli w wiadomości e-mail zawarte są poufne informacje, można chronić tę wiadomość lub po prostu użyć opcji nieprzekazywania dalej w programie Outlook. <br /><br />Dołączenie chronionego pliku ma tę zaletę w stosunku do ochrony całej wiadomości e-mail, że tekst nie jest szyfrowany i można w nim zawrzeć instrukcje dotyczące pierwszego użycia, jeśli wiadomość jest wysyłana na zewnątrz organizacji. Każdy może przeczytać te instrukcje, jednak ze względu na to, że dołączony dokument jest chroniony, tylko autoryzowani użytkownicy będą mogli go otworzyć, nawet jeśli wiadomość e-mail lub dokument zostaną przesłane dalej do innych osób.|
|Inspekcja i monitorowanie|√ Możesz [przeprowadzać inspekcję i monitorowanie użycia](../deploy-use/log-analyze-usage.md) plików chronionych, nawet po opuszczeniu przez nie granic organizacji.<br /><br />Załóżmy, że pracujesz dla firmy Contoso, Ltd. Pracujesz nad wspólnym projektem z trzema osobami z firmy Fabrikam, Inc. Wysyłasz do tych trzech osób pocztą e-mail dokument, który chronisz i ograniczasz, aby był tylko do odczytu. Inspekcja usługi Azure Rights Management może podać następujące informacje:<br /><br />— czy i kiedy wybrane osoby z firmy Fabrikam otworzyły dokument;<br /><br />— czy inne osoby, których nie podano, próbowały (bez powodzenia) otworzyć dokument — prawdopodobnie ponieważ został przekazany albo zapisany w lokalizacji udostępnionej innym osobom;<br /><br />— czy dowolna osoba z wybranych próbowała (bez powodzenia) drukować lub zmieniać dokument.<br /><br />Ponadto [witryna śledzenia dokumentów](../rms-client/client-track-revoke.md) umożliwia użytkownikom i administratorom śledzenie i w razie potrzeby odwoływanie dostępu do chronionych dokumentów.|
|Obsługa powszechnie używanych urządzeń, nie tylko komputerów z systemem Windows|√ [Obsługiwane urządzenia](../get-started/requirements-client-devices.md) obejmują:<br /><br />— komputery i telefony z systemem Windows<br /><br />— komputery Mac<br /><br />— tablety i telefony z systemem iOS<br /><br />— tablety i telefony z systemem Android|
|Obsługa współpracy między firmami (B2B)|√ Ponieważ Azure Rights Management to usługa w chmurze, nie istnieje potrzeba jawnego konfigurowania relacji zaufania z innymi organizacjami przed udostępnieniem im chronionej zawartości. Jeżeli korzystają już one z usługi Office 365 lub katalogu usługi Azure AD, współpraca między organizacjami jest obsługiwana automatycznie. W przeciwnym razie użytkownicy mogą rejestrować się w ramach darmowej subskrypcji [usługi RMS dla osób indywidualnych](rms-for-individuals.md).|
|Obsługa usług lokalnych, jak również usługi Office 365|√ Oprócz [bezproblemowej współpracy z usługą Office 365](office-apps-services-support.md) po wdrożeniu [łącznika usługi RMS](../deploy-use/deploy-rms-connector.md) można także korzystać z usługi Azure Rights Management w połączeniu z następującymi usługami lokalnymi:<br /><br />— Exchange Server<br /><br />— SharePoint Server<br /><br />— System Windows Server z uruchomioną infrastrukturą klasyfikacji plików|
|Łatwa aktywacja|√ [Aktywowanie usługi Rights Management](../deploy-use/activate-service.md) dla użytkowników wymaga zaledwie kilku kliknięć w portalu zarządzania. Jeśli wolisz posługiwać się wierszem poleceń, wystarczą dwa polecenia w oknie programu PowerShell.|
|Dostosowana do potrzeb możliwość skalowania w organizacji|√ Ponieważ Azure Rights Management to usługa w chmurze, której elastyczność skalowania w górę i w dół zapewnia platforma Azure, nie trzeba aprowizować ani wdrażać dodatkowych serwerów lokalnych.|
|Możliwość tworzenia prostych i elastycznych zasad|√ [Dostosowane szablony zasad praw](../deploy-use/configure-custom-templates.md) stanowią rozwiązanie szybkie i łatwe, dzięki któremu administratorzy mogą stosować zasady, a użytkownicy mogą stosować odpowiedni poziom ochrony do każdego dokumentu, a także ograniczać dostęp do osób wewnątrz organizacji.<br /><br />Na przykład dokument strategii dla całej firmy może być udostępniony wszystkim pracownikom z zastosowaniem zasady tylko do odczytu dla wszystkich pracowników wewnętrznych. Natomiast dostęp do bardziej poufnego dokumentu, takiego jak raport finansowy, może zostać ograniczony tylko do dyrektorów.|
|Szerokie wsparcie aplikacji|√ Usługa Azure Rights Management ściśle integruje się z aplikacjami i usługami Microsoft Office, a także oferuje rozszerzone wsparcie dla innych aplikacji za pomocą [klienta usługi Azure Information Protection](../rms-client/aip-client.md ).<br /><br />√ Zestawy [Azure Information Protection SDK](../develop/developers-guide.md) dostarczają wewnętrznym deweloperom i dostawcom oprogramowania interfejsy API do programowania niestandardowych aplikacji do udostępniania usługi RMS.<br /><br />Aby uzyskać więcej informacji, zobacz artykuł [Inne aplikacje, które obsługują interfejsy API usługi Rights Management](api-support.md).|
|Dział IT musi zachować kontrolę nad danymi|√ Organizacje mogą wybrać zarządzanie własnym kluczem dzierżawcy z zastosowaniem rozwiązania „[Bring Your Own Key](../plan-design/plan-implement-tenant-key.md)” (BYOK) i przechowywać klucz dzierżawcy w sprzętowych modułach zabezpieczeń (HSM).<br /><br />√ Obsługa inspekcji i [rejestrowanie użycia](../deploy-use/log-analyze-usage.md) pozwala analizować szczegółowe informacje biznesowe, monitorować nadużycia oraz (w przypadku przecieku informacji) dokonywać analizy śledczej.<br /><br />√ Delegowanie dostępu za pomocą [funkcji administratorów](../deploy-use/configure-super-users.md) pozwala zagwarantować, że dział IT zawsze ma dostęp do zawartości chronionej, nawet jeśli dokument był chroniony przez pracownika, który opuścił organizację. W odróżnieniu od tego podejścia rozwiązania szyfrowania równorzędnego niosą ryzyko utraty dostępu do danych firmowych.<br /><br />√ Synchronizacja [wyłącznie atrybutów katalogu wymaganych przez usługę Azure RMS](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) do obsługi tożsamości wspólnych dla lokalnych kont usługi Active Directory przy użyciu [narzędzia synchronizacji katalogów](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison), np. Azure AD Connect.<br /><br />√ Włączanie logowania jednokrotnego bez replikacji haseł w chmurze za pomocą usług AD FS.<br /><br />√ Organizacje mogą w dowolnie wybranym momencie przestać korzystać z usługi Azure Rights Management bez utraty dostępu do zawartości, która była wcześniej chroniona przez tę usługę. Aby uzyskać więcej informacji na temat opcji likwidowania, zobacz artykuł [Likwidowanie i dezaktywowanie usługi Azure Rights Management](../deploy-use/decommission-deactivate.md) Ponadto organizacje, które wdrożyły usługę Active Directory Rights Management Services (AD RMS), mogą [migrować do usługi Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md) bez utraty dostępu do danych, które wcześniej były chronione przez usługę AD RMS.|
> [!TIP]
> Jeśli znasz lokalną wersję usługi Rights Management, Active Directory Rights Management Services (AD RMS), może Cię zainteresować tabela porównawcza z artykułu [Porównanie usług Azure Rights Management i AD RMS](compare-azure-rms-ad-rms.md).

## <a name="security-compliance-and-regulatory-requirements"></a>Wymagania dotyczące zabezpieczeń, zgodności i przepisów prawnych
Usługa Azure Rights Management obsługuje następujące wymagania dotyczące zabezpieczeń, zgodności i przepisów prawnych:

√ Wykorzystanie branżowego standardu kryptografii i obsługa standardu FIPS 140-2. Aby uzyskać więcej informacji, zobacz temat [formanty kryptograficzne używane przez usługę Azure RMS: algorytmy i długości kluczy](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).

√ Obsługa sprzętowych modułów zabezpieczeń (HSM) firmy Thales do przechowywania klucza dzierżawcy w centrach danych Microsoft Azure. W usłudze Azure Rights Management są używane oddzielne środowiska Security World dla centrów danych w Ameryce Północnej, regionie Europy, Bliskiego Wschodu i Afryki (EMEA) oraz Azji. Dzięki temu klucze mogą być używane tylko w danym regionie.

√ Przyznane certyfikaty:

-   ISO/IEC 27001:2013 (obejmuje [ISO/IEC 27018](http://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/))

-   Poświadczenia SOC 2 SSAE 16/ISAE 3402

-   HIPAA BAA

-   Klauzula modelu UE

-   Prawo do działania FedRAMP obejmujące usługę Azure Active Directory w ramach certyfikacji usługi Office 365 wystawione przez urząd HHS

-   PCI DSS poziom 1

Aby uzyskać więcej informacji o tych certyfikatach zewnętrznych, zobacz [Centrum zaufania platformy Azure](http://azure.microsoft.com/support/trust-center/compliance/).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji technicznych na temat działania usługi Azure Rights Management, zobacz [Jak działa usługa Azure RMS?](how-does-it-work.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]