---
title: Omówienie ochrony usługi Azure Rights Management z usługi Azure Information Protection — AIP
description: Informacje dotyczące usługi Azure Rights Management (Azure RMS), technologia ochrony używana przez usługę Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: aeeebcd7-6646-4405-addf-ee1cc74df5df
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: fa7bf6ae5eb60b6fc6b0310c11e9acfbbd3b240c
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53024165"
---
# <a name="what-is-azure-rights-management"></a>Co to jest usługa Azure Rights Management?

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Usługa Azure Rights Management (nazwa często skracana do usługi Azure RMS) to technologia ochrony używana przez [usługi Azure Information Protection](what-is-information-protection.md).

Ta usługa ochrony opartej na chmurze używa szyfrowanie, tożsamość i zasady autoryzacji, aby ułatwić zabezpieczanie plików i wiadomości e-mail i działa na wielu urządzeniach — telefonach, tabletach i komputerach. Informacje można chronić w obrębie organizacji i poza nią, ponieważ ochrona jest powiązana z danymi nawet wtedy, gdy opuszczą one teren organizacji.

Na przykład pracownicy mogą wysłać dokument pocztą e-mail do firmy partnerskiej lub zapisać go na dysku w chmurze. Trwałej ochrony usługi Azure RMS zapewnia nie tylko pomaga zabezpieczyć dane firmowe, ale może również prawnie uprawnioną pod kątem zgodności, wymagania, lub po prostu dla rozwiązań z zakresu zarządzania precyzyjnymi informacjami.

Ale bardzo ważne, upoważnione osoby i usługi (takie jak wyszukiwanie i indeksowanie) mogą nadal odczytywać i sprawdzać dane chronione. Ta funkcja jest utrudnione w przypadku innych rozwiązań do ochrony informacji korzystających z szyfrowania peer-to-peer. Prawdopodobnie słyszałeś tej możliwości, nazywa się "rozsądkiem ponad danymi" i jest to kluczowy element w zachowaniu kontroli nad danymi w organizacji.

Na poniższej ilustracji przedstawiono, jak ta usługa oferuje rozwiązania do ochrony dla usługi Office 365, a także dla lokalnych serwerów i usług. Zobaczysz również, czy ochrona jest obsługiwana przez urządzenia popularnych użytkowników końcowych, z systemem Windows, Mac OS, iOS, Android i Windows Phone.


![Jak działa usługa Azure RMS](./media/AzRMS_elements.png)

Możesz użyć tej ochrony za pomocą subskrypcji usługi Office 365, a także za pomocą subskrypcji usługi Azure Information Protection. Można znaleźć więcej informacji na temat dostępnych subskrypcji i obsługiwanych funkcji, które obsługują one na [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) lokacji.

## <a name="business-problems-solved-by-azure-rights-management"></a>Problemy biznesowe, które można rozwiązać przez usługę Azure Rights Management

Skorzystaj z poniższej tabeli, aby zidentyfikować wymagania biznesowe lub problemy, że w celu ochrony dokumentów i wiadomości e-mail i jak technologię Azure Rights Management ich rozwiązywania przy użyciu może mieć organizacja.


|Wymaganie lub problem|Rozwiązanie przy użyciu usługi Azure RMS|
|--------------------------|-----------------------|
|Ochrona wielu typów plików|√ We wczesnych implementacjach usługi Rights Management, tylko pakietu Office mogły być chronione pliki za pomocą ochrony natywnej usługi Rights Management. Teraz **ochrona ogólna**, która była najpierw oferowana przez aplikację do udostępniania usługi Rights Management, a teraz jest oferowana przez klienta usługi Information Protection oznacza, że obsługiwanych jest więcej [typów plików](./rms-client/client-admin-guide-file-types.md).|
|Ochrona plików w każdym miejscu|√ Gdy plik jest [chronione](./rms-client/client-classify-protect.md), ochrona pozostaje skojarzona z plikiem, nawet jeśli zostanie zapisany lub skopiowany do magazynu, który nie jest pod kontrolą IT, takiego jak Usługa magazynu w chmurze.|
|Bezpieczne udostępnianie informacji|√ Gdy plik jest [chronione](./rms-client/client-classify-protect.md), można bezpiecznie udostępniać innym użytkownikom. Na przykład załącznik do wiadomości e-mail lub link do witryny programu SharePoint. Jeśli w wiadomości e-mail zawarte są poufne informacje, można chronić tę wiadomość lub po prostu użyć opcji nieprzekazywania dalej w programie Outlook. <br /><br />Dołączenie chronionego pliku ma tę zaletę w stosunku do ochrony całej wiadomości e-mail, że tekst nie jest szyfrowany i można w nim zawrzeć instrukcje dotyczące pierwszego użycia, jeśli wiadomość jest wysyłana na zewnątrz organizacji. Każdy może przeczytać te instrukcje, jednak ze względu na to, że dołączony dokument jest chroniony, tylko autoryzowani użytkownicy będą mogli go otworzyć, nawet jeśli wiadomość e-mail lub dokument zostaną przesłane dalej do innych osób.|
|Inspekcja i monitorowanie|√ Możesz [przeprowadzać inspekcję i monitorowanie użycia](log-analyze-usage.md) plików chronionych, nawet w przypadku, po opuszczeniu granic Twojej organizacji.<br /><br />Załóżmy, że pracujesz dla firmy Contoso, Ltd. Pracujesz nad wspólnym projektem z trzema osobami z firmy Fabrikam, Inc. Wysyłasz do tych trzech osób pocztą e-mail dokument, który chronisz i ograniczasz, aby był tylko do odczytu. Funkcja inspekcji usługi Azure Rights Management może podać następujące informacje:<br /><br />— czy i kiedy wybrane osoby z firmy Fabrikam otworzyły dokument;<br /><br />— czy inne osoby, których nie podano, próbowały (bez powodzenia) otworzyć dokument — prawdopodobnie ponieważ został przekazany albo zapisany w lokalizacji udostępnionej innym osobom;<br /><br />— czy dowolna osoba z wybranych próbowała (bez powodzenia) drukować lub zmieniać dokument.<br /><br />Ponadto [witryna śledzenia dokumentów](./rms-client/client-track-revoke.md) umożliwia użytkownikom i administratorom śledzenie i w razie potrzeby odwoływanie dostępu do chronionych dokumentów.|
|Obsługa powszechnie używanych urządzeń, nie tylko komputerów z systemem Windows|√ [urządzenia obsługiwane przez](./requirements-client-devices.md) obejmują:<br /><br />— komputery i telefony z systemem Windows<br /><br />— komputery Mac<br /><br />— tablety i telefony z systemem iOS<br /><br />— tablety i telefony z systemem Android|
|Obsługa współpracy między firmami (B2B)|√ Ponieważ Azure Rights Management to usługa w chmurze, istnieje potrzeba jawnego konfigurowania relacji zaufania z innymi organizacjami przed udostępnieniem chronionej zawartości z nimi. Jeśli ich jeszcze z usługi Office 365 lub katalogu usługi Azure AD, współpraca między organizacjami jest obsługiwana automatycznie. Jeśli tak się nie stanie, użytkownicy mogą zarejestrować się w ramach darmowej [RMS dla użytkowników indywidualnych](rms-for-individuals.md) subskrypcji lub użyj konto Microsoft [aplikacje, które obsługują uwierzytelnianie usługi Azure Information Protection](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents).|
|Obsługa usług lokalnych, jak również usługi Office 365|√ Oprócz [bezproblemowo z usługą Office 365](office-apps-services-support.md), można również użyć usługi Azure Rights Management z następującymi usługami w środowisku lokalnym, podczas wdrażania [łącznika usługi RMS](deploy-rms-connector.md):<br /><br />— Exchange Server<br /><br />— SharePoint Server<br /><br />-Windows Server z uruchomioną infrastrukturą klasyfikacji plików|
|Łatwa aktywacja|√ w przypadku nowych subskrypcji, aktywacja jest automatyczna. W przypadku istniejących subskrypcji [aktywowanie usługi Rights Management](activate-service.md) wymaga zaledwie kilku kliknięć w portalu zarządzania. Jeśli wolisz posługiwać się wierszem poleceń, wystarczą dwa polecenia w oknie programu PowerShell.|
|Dostosowana do potrzeb możliwość skalowania w organizacji|√ Ponieważ Azure Rights Management działa jako usługa w chmurze Azure elastyczność skalowania w górę i, nie trzeba aprowizować ani wdrażać dodatkowych na serwerach lokalnych.|
|Możliwość tworzenia prostych i elastycznych zasad|√ [dostosowane szablony ochrony](configure-policy-templates.md) stanowią rozwiązanie szybkie i łatwe, Administratorzy mogą stosować zasady, a użytkownicy umożliwia stosowanie odpowiedniego poziomu ochrony dla każdego dokumentu i ograniczenie dostępu do osób wewnątrz usługi organizacja.<br /><br />Na przykład dokument strategii dla całej firmy może być udostępniony wszystkim pracownikom z zastosowaniem zasady tylko do odczytu dla wszystkich pracowników wewnętrznych. Natomiast dostęp do bardziej poufnego dokumentu, takiego jak raport finansowy, może zostać ograniczony tylko do dyrektorów.|
|Szerokie wsparcie aplikacji|√ usługi Azure Rights Management ma ścisłą integrację z aplikacjami i usługami Microsoft Office i rozszerzone wsparcie dla innych aplikacji za pomocą [klienta Azure Information Protection](./rms-client/aip-client.md ).<br /><br />√ [Azure Information Protection SDK](./develop/developers-guide.md) zapewniają wewnętrznym deweloperom i dostawcom oprogramowania interfejsy API do programowania niestandardowych aplikacji, które obsługują usługę Azure Information Protection.<br /><br />Aby uzyskać więcej informacji, zobacz artykuł [Inne aplikacje, które obsługują interfejsy API usługi Rights Management](api-support.md).|
|Dział IT musi zachować kontrolę nad danymi|√ Organizacje mogą wybrać Zarządzanie własne klucze dzierżawy oraz używanie "[Bring Your Own Key](plan-implement-tenant-key.md)" (BYOK), rozwiązania i przechowywać klucz dzierżawcy w sprzętowych modułach zabezpieczeń (HSM).<br /><br />√ Obsługa inspekcji i [rejestrowanie użycia](log-analyze-usage.md) tak, aby analizować szczegółowe informacje biznesowe, monitorować nadużycia oraz (Jeśli masz przecieku informacji) wykonywanie analizy śledczej.<br /><br />√ Delegowanie dostępu za pomocą [funkcji superużytkowników](configure-super-users.md) gwarantuje, że dział IT zawsze dostęp do zawartości chronionej, nawet jeśli dokument był chroniony przez pracownika, który opuścił organizację. W odróżnieniu od tego podejścia rozwiązania szyfrowania równorzędnego niosą ryzyko utraty dostępu do danych firmowych.<br /><br />√ Synchronizacja [wyłącznie atrybutów katalogu wymaganych przez usługę Azure RMS](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized#azure-rms) do obsługi tożsamości wspólnych dla lokalnych kont usługi Active Directory za pomocą [rozwiązania tożsamości hybrydowej](/azure/active-directory/hybrid/), takiego jak Azure AD Połącz z.<br /><br />√ Włączanie logowania jednokrotnego na bez replikacji haseł w chmurze za pomocą usług AD FS.<br /><br />√ Organizacje mogą w dowolnie wybranym momencie przestać korzystać z usługi Azure Rights Management bez utraty dostępu do zawartości, która była wcześniej chroniona przez usługę Azure Rights Management. Aby uzyskać więcej informacji na temat opcji likwidowania, zobacz artykuł [Likwidowanie i dezaktywowanie usługi Azure Rights Management](decommission-deactivate.md) Ponadto organizacje, które wdrożyły usługę Active Directory Rights Management Services (AD RMS) może [migracji do usługi Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) bez utraty dostępu do danych, które wcześniej były chronione przez usługi AD RMS.|
> [!TIP]
> Jeśli znasz lokalną wersję usługi Rights Management, Active Directory Rights Management Services (AD RMS), może Cię zainteresować tabela porównawcza z artykułu [Porównanie usług Azure Rights Management i AD RMS](compare-on-premise.md).

## <a name="security-compliance-and-regulatory-requirements"></a>Wymagania dotyczące zabezpieczeń, zgodności i przepisów prawnych
Usługa Azure Rights Management obsługuje następujące zabezpieczeń, zgodności i przepisów:

√ Wykorzystanie branżowego standardu kryptografii i obsługa standardu FIPS 140-2. Aby uzyskać więcej informacji, zobacz temat [formanty kryptograficzne używane przez usługę Azure RMS: algorytmy i długości kluczy](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).

√ Obsługa sprzętowych modułów zabezpieczeń (HSM) do przechowywania klucza dzierżawy usługi Microsoft Azure dane Thales centrów. Usługa Azure Rights Management używa oddzielne środowiska security World dla centrów danych w Ameryce Północnej, EMEA (Europa, Bliski Wschód i Afryka) oraz Azji, dzięki czemu Twoje klucze mogą być używane tylko w danym regionie.

√ przyznane certyfikaty:

-   ISO/IEC 27001: 2013 (. / obejmuje [ISO/IEC 27018](http://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/))

-   Poświadczenia SOC 2 SSAE 16/ISAE 3402

-   HIPAA BAA

-   Klauzula modelu UE

-   FedRAMP usługi Azure Active Directory w ramach certyfikacji usługi Office 365 wystawił urząd Operate przez HHS

-   PCI DSS poziom 1

Aby uzyskać więcej informacji o tych certyfikatach zewnętrznych, zobacz [Centrum zaufania platformy Azure](http://azure.microsoft.com/support/trust-center/compliance/).

## <a name="next-steps"></a>Kolejne kroki

Aby uzyskać więcej informacji technicznych na temat działania usługi Azure Rights Management, zobacz [Jak działa usługa Azure RMS?](how-does-it-work.md)

