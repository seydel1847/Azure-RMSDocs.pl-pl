---
title: HYOK ochrony usługi Azure Information Protection
description: Omówienie ochrony HYOK (AD RMS) z usługi Azure Information Protection, jego obsługiwane scenariusze ograniczenia, wymagania wstępne i zalecenia.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/01/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ms.openlocfilehash: 5ded2edb2ea3fe05cc09750c4cdb53bc03d5fbae
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32327470"
---
# <a name="hold-your-own-key-hyok-protection-for-azure-information-protection"></a>Przytrzymaj ochrony własnego klucza (HYOK) dla usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Skorzystaj z poniższych informacji, aby zrozumieć, co blokady jest ochrona własnego klucza (HYOK) dla usługi Azure Information Protection i jak jest inna niż domyślna ochrona oparta na chmurze. Przed użyciem ochrony HYOK, upewnij się, że rozumiesz, gdy jest ona odpowiednia, obsługiwane scenariusze, ograniczenia i wymagania. 

## <a name="cloud-based-protection-vs-hyok"></a>Vs ochrony opartej na chmurze. HYOK

W przypadku ochrony najbardziej poufne dokumenty i wiadomości e-mail przy użyciu usługi Azure Information Protection, należy to robić przez zastosowanie oparte na chmurze klucz, który używa ochrony usługi Azure Rights Management (Azure RMS) w celu zapewnia następujące korzyści:

- Nie wymaga infrastruktury serwera, co sprawia, że wdrożenie, i obsługa rozwiązania są szybsze i tańsze niż w przypadku rozwiązania lokalnego.

- Łatwiejsze udostępnianie zawartości partnerom i użytkownikom z innych organizacji przy użyciu uwierzytelniania opartego na chmurze.

- Ścisła integracja z innymi usługami platformy Azure i usługi Office 365, takich jak wyszukiwanie, przeglądarki sieci web, widoki przestawne, przed złośliwym oprogramowaniem, zbieranie elektronicznych materiałów dowodowych i aplikacja Delve.

- Śledzenie i odwoływanie dokumentów, powiadomienia e-mail dotyczące udostępnionych poufnych dokumentów.

Klucz oparte na chmurze chroni dokumenty i wiadomości e-mail organizacji przy użyciu klucza prywatnego dla organizacji, który jest zarządzany przez firmę Microsoft (ustawienie domyślne) lub zarządzanego przez użytkownika ("bring your own key" lub scenariusza BYOK). Aby uzyskać więcej informacji na temat opcji klucza dzierżawy, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md).

Dokumenty i wiadomości e-mail, które należy chronić może być przechowywane w chmurze lub lokalnie. Aby uzyskać więcej informacji na temat działania procesu ochrony dla tego klucza oparta na chmurze, zobacz [co to jest usługa Azure Rights Management?](../understand-explore/what-is-azure-rms.md )

Usługi Office 365 i aplikacji opartych na chmurze dla dzierżawy można zintegrować z usługi Azure Information Protection, aby firm ważne funkcje, takie jak usługi wyszukiwania, indeksowania, archiwizacji i przed złośliwym oprogramowaniem w dalszym ciągu współdziała bezproblemowo zawartości która jest chroniona przez usługę Azure Information Protection. To pozwala na odczyt zaszyfrowaną zawartość w tych scenariuszach często nazywa się "rozsądkiem ponad danymi". Na przykład jest tę możliwość, umożliwiający usłudze Exchange Online odszyfrowywania wiadomości e-mail dla złośliwego oprogramowania, skanowanie i do uruchamiania zasady zapobiegania (DLP) utrata danych na zaszyfrowanych wiadomości e-mail.

Jednak wymagania prawne organizacjach kilka może być konieczne do zaszyfrowania zawartości za pomocą klucza jest izolowana z chmury. Izolacja oznacza, że zaszyfrowaną zawartość może zostać odczytana tylko przez lokalnymi aplikacjami i usługami lokalnymi. Ta opcja zarządzania kluczami jest obsługiwana przez usługę Azure Information Protection i jest określany jako "hold your own key" lub HYOK. Gdy używasz usługi Azure Information Protection z rozwiązaniem HYOK dzierżawy ma zarówno klucz oparte na chmurze, jak i klucz lokalnie.

## <a name="hyok-guidance-and-best-practices"></a>HYOK wskazówek i najlepszych rozwiązań

Używaj ochrony HYOK tylko dla dokumentów i wiadomości e-mail, które wymagają klucza szyfrowania, aby być odizolowany od chmury. Ochrona HYOK nie zapewnia wymienionych korzyści, które można uzyskać, gdy używasz ochrony klucza opartej na chmurze i jej często odbywa się kosztem "nieprzezroczystość danych". Oznacza to wyrażenie, że tylko lokalne aplikacje i usługi będą mogli otworzyć chronione HYOK danych; oparte na chmurze usługi i aplikacje nie przyczyny HYOK chronionych danych.

Nawet w przypadku organizacji, które używają ochrony HYOK jest zazwyczaj odpowiednia dla niewielkiej liczby dokumentów, które muszą być chronione. Wskazówki używać go tylko dla dokumentów i spełniają następujące kryteria:

- Zawartość ma najwyższej klasyfikacji w Twojej organizacji ("Top Secret") i dostęp jest ograniczony do kilku osób

- Zawartość nie jest udostępniane poza organizacją

- Zawartość jest tylko używane w sieci wewnętrznej

Ponieważ HYOK ochrony jest dostępna opcja konfiguracji administratora dla etykiety, przepływy pracy użytkownika pozostają takie same, niezależnie od tego, czy ochrona używa klucza oparta na chmurze lub HYOK.

[Zakres zasad](configure-policy-scope.md) są dobrym sposobem upewnij się, że tylko użytkownicy muszą zastosować ochronę HYOK etykiety, które są skonfigurowane dla ochrony HYOK. 

## <a name="supported-scenarios-for-hyok"></a>Obsługiwane scenariusze dotyczące rozwiązania HYOK

Aby zastosować ochronę HYOK, korzystanie z usługi Azure Information Protection etykiet. 

W poniższej tabeli wymieniono obsługiwane scenariusze ochrony zawartości przy użyciu etykiety, które są skonfigurowane dla HYOK i otwieranie (zużywa) zawartości chronionej przez HYOK.

|Platforma|Aplikacji|Obsługiwane|
|----------------------|----------|-----------|
|Windows|Klient usługi Azure Information Protection z pakietu Office 2016 i Office 2013 <br /><br />-Word, Excel, PowerPoint|Ochrona: tak<br /><br />Użycie: tak|
|Windows|Klient usługi Azure Information Protection z pakietu Office 2016 i Office 2013 <br /><br />-Outlook|Ochrona: tak<br /><br />Użycie: tak|
|Windows|Klient usługi Azure Information Protection z Eksploratora plików|Ochrona: tak <br /><br />Użycie: tak|
|Windows|Azure Information Protection podglądu|Ochrona: Nie dotyczy<br /><br />Użycie: tak|
|Windows|Klient usługi Azure Information Protection przy użyciu etykietowania poleceń cmdlet programu PowerShell|Ochrona: tak<br /><br />Użycie: tak|
|Windows|Skaner usługi Azure Information Protection|Ochrona: tak<br /><br />Użycie: tak|
|Windows|Aplikacja do udostępniania Rights Management|Ochrona: Nie<br /><br />Użycie: tak|
|System macOS|Pakiet Office dla komputerów Mac <br /><br /> -Word, Excel, PowerPoint|Ochrona: Nie<br /><br />Użycie: tak|
|System macOS|Pakiet Office dla komputerów Mac<br /><br />-Outlook|Ochrona: Nie<br /><br />Użycie: tak|
|System macOS|Aplikacja do udostępniania Rights Management|Ochrona: Nie<br /><br />Użycie: tak|
|iOS|Office Mobile <br /><br />-Word, Excel, PowerPoint|Ochrona: Nie<br /><br />Użycie: tak|
|iOS|Office Mobile <br /><br />-Outlook|Ochrona: Nie<br /><br />Użycie: nie|
|iOS|Azure Information Protection podglądu|Ochrona: Nie dotyczy<br /><br />Użycie: tak|
|Android|Office Mobile <br /><br />-Word, Excel, PowerPoint|Ochrona: Nie<br /><br />Użycie: tak|
|Android|Office Mobile <br /><br />-Outlook|Ochrona: Nie<br /><br />Użycie: nie|
|Android|Azure Information Protection podglądu|Ochrona: Nie dotyczy<br /><br />Użycie: tak|
|sieci Web|Program Outlook w sieci web|Ochrona: Nie<br /><br />Użycie: nie|
|sieci Web|Office Online<br /><br />-Word, Excel, PowerPoint|Ochrona: Nie<br /><br />Użycie: nie|
|Uniwersalny|Uniwersalnych aplikacji pakietu Office<br /><br />-Word, Excel, PowerPoint|Ochrona: Nie<br /><br />Użycie: nie|


## <a name="additional-limitations-when-using-hyok"></a>Dodatkowe ograniczenia podczas używania funkcji HYOK

Ponadto przy użyciu ochrony HYOK z etykietami usługi Azure Information Protection ma następujące ograniczenia:

- Brak obsługi pakietu Office 2010 lub Office 2007.

- Usługi Office 365 i innych usług online nie będzie można odszyfrować chroniony HYOK dokumentów i wiadomości e-mail, aby sprawdzić zawartość i podejmuje odpowiednie działania na nich. To ograniczenie rozszerza HYOK chronione dokumenty i wiadomości e-mail, które są chronione za pomocą łącznika usługi Rights Management. 
    
    Ta utrata funkcjonalności do obsługi poczty e-mail chronione HYOK obejmuje skanery złośliwego oprogramowania, rozwiązania zapobiegania (DLP) utraty danych, reguły routingu poczty, rejestrowanie, zbieranie elektronicznych materiałów dowodowych, archiwizacji rozwiązań i programu Exchange ActiveSync. Ponadto użytkownicy nie będą Dowiedz się, dlaczego niektóre urządzenia nie można otworzyć ich wiadomości e-mail chronionych HYOK i może to spowodować wywołania do pomocy technicznej. Ze względu na ograniczenia te wiele nie zaleca się stosowanie ochrony HYOK dla wiadomości e-mail.

## <a name="implementing-hyok"></a>Implementowanie rozwiązania HYOK

HYOK jest obsługiwana przez usługę Azure Information Protection, gdy masz działające wdrożenie Active Directory Rights Management Services (AD RMS) z wymaganiami opisanymi w następnej sekcji. W tym scenariuszu zasad praw użytkowania i klucz prywatny organizacji, który chroni te zasady są zarządzane i przechowywane lokalnie, podczas zasady usługi Azure Information Protection dla etykietowania i klasyfikacji pozostają zarządzane i przechowywane na platformie Azure. 

Nie należy mylić HYOK i usługi Azure Information Protection przy użyciu pełnego wdrożenia usług AD RMS i Azure Information Protection lub jako alternatywę do migracji usług AD RMS do usługi Azure Information Protection. HYOK jest obsługiwana tylko przez zastosowanie etykiety, nie oferują funkcji parzystości z usługami AD RMS i nie obsługuje wszystkie konfiguracje wdrożenia usług AD RMS:

- Aby uzyskać więcej informacji o scenariuszach czy HYOK obsługuje ochronę zawartości i korzystanie z zawartości chronionej, zobacz [obsługiwane scenariusze dotyczące rozwiązania HYOK](#supported-scenarios-for-hyok) sekcji.

- Aby uzyskać instrukcje migracji z usług AD RMS, zobacz [Migrowanie z usług AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

- Aby uzyskać więcej informacji o wymaganiach dotyczących wdrożenia usług AD RMS zobacz następną sekcję.

### <a name="requirements-for-ad-rms-to-support-hyok"></a>Wymagania dotyczące usług AD RMS do obsługi rozwiązania HYOK

Wdrażanie usług AD RMS musi spełniać następujące wymagania w celu zapewnienia ochrony HYOK etykiety usługi Azure Information Protection.

- Konfiguracja usług AD RMS:
    
    - Minimalna wersja systemu Windows Server 2012 R2: wymagana dla środowisk produkcyjnych; w celach związanych z testowaniem lub oceną można użyć minimalnej wersji systemu Windows Server 2008 R2 z dodatkiem Service Pack 1.
    
    - Jeden z następujących topologii:
        
        - Pojedynczy las z jednego klastra głównego usług AD RMS. 
        
        - Wiele lasów z niezależnych klastrów głównego usług AD RMS i użytkownicy nie mają dostępu do zawartości, która jest chroniona przez użytkowników w innych lasach.
        
        - Wiele lasów z usługami AD RMS klastrów w każdej z nich. Każdy klaster usług AD RMS współużytkuje adres URL licencjonowania, który wskazuje do tego samego klastra usług AD RMS. W tym klastrze usług AD RMS należy zaimportować wszystkie certyfikaty zaufanego użytkownika domeny ze wszystkich innych klastrów usług AD RMS. Aby uzyskać więcej informacji na temat tej topologii, zobacz [zaufanej domeny użytkownika] (https://technet.microsoft.com/library/dd983944(v=ws.10\)aspx).
        
    Jeśli masz wiele klastrów usług AD RMS w oddzielnych lasach, usuń wszystkich etykiet w ramach globalnych zasad, które stosują ochronę HYOK (AD RMS) i skonfiguruj [zakres zasad](configure-policy-scope.md) dla każdego klastra. Następnie przypisać użytkowników dla każdego klastra, do jego zakresie zasad, upewniając się, nie używaj grup, które umożliwiałyby użytkownik jest przypisany do więcej niż jedna zasada zakresami. Wynik powinien być, że każdy użytkownik ma etykiety dla jednego klastra usług AD RMS. 
    
    - [Tryb kryptograficzny 2](https://technet.microsoft.com/library/hh867439.aspx): tryb można potwierdzić, sprawdzając właściwości klastra usług AD RMS, **ogólne** kartę.
    
    - Każdy serwer usług AD RMS jest skonfigurowany dla adres URL certyfikacji. [Instrukcje](#configuring-ad-rms-servers-to-locate-the-certification-url) 
    
    - Punkt połączenia usługi nie jest zarejestrowany w usłudze Active Directory: punkt połączenia usługi nie jest używany, gdy korzystasz z ochrony za pomocą usług AD RMS razem z usługą Azure Information Protection. 
    
        - Jeśli masz zarejestrowany punkt połączenia usługi dla wdrożenia usług AD RMS, musisz go usunąć, aby [odnajdywanie usług](../rms-client/client-deployment-notes.md#rms-service-discovery) dla ochrony za pomocą usługi Azure Rights Management powiodło się. 
        
        - Jeśli instalujesz nowy klaster AD RMS dla HYOK, należy pominąć krok, aby zarejestrować punkt połączenia usługi podczas konfigurowania pierwszego węzła. Dla każdego dodatkowego węzła upewnij się, że serwer jest skonfigurowany dla adres URL certyfikacji przed Dodaj rolę usług AD RMS i Dołącz do istniejącego klastra.
    
    - Serwery AD RMS są skonfigurowane do użycia protokołów SSL/TLS z ważnym certyfikatem x.509, który jest zaufany przez klientów nawiązujących połączenie: wymagane dla środowisk produkcyjnych, ale niewymagane w celach związanych z testowaniem lub oceną.
    
    - Skonfigurowane szablony praw.
    
    - Nie jest skonfigurowany dla usługi IRM programu Exchange.
    
    - Dla urządzeń przenośnych i komputerów Mac: [Active Directory Rights Management usług rozszerzenia dla urządzeń przenośnych](https://technet.microsoft.com/library/dn673574.aspx) jest zainstalowana i skonfigurowana.

- Skonfigurowano synchronizację katalogów między lokalnymi usługi Active Directory a usługą Azure Active Directory, a użytkownicy, którzy będą korzystać z ochrony HYOK są skonfigurowane dla logowania jednokrotnego.

- Jeśli udostępnianie dokumentów lub wiadomości e-mail, które są chronione przez HYOK osobom spoza organizacji: usługi AD RMS jest skonfigurowane dla jawnie zdefiniowanych relacji zaufania w bezpośredniej relacji point-to-point z innymi organizacjami przy użyciu zaufanych domen użytkowników (TUD) lub federacyjnych relacji zaufania, które są tworzone za pomocą usługi Active Directory Federation Services (AD FS).

- Użytkownicy mają wersji pakietu Office, który jest Office 2016 Professional Plus lub Office 2013 Professional Plus z dodatkiem Service Pack 1, uruchomiony w systemie Windows 7 z dodatkiem Service Pack 1 lub nowszym. Należy zauważyć, że pakiety Office 2010 i Office 2007 nie są obsługiwane w tym scenariuszu.
    
    - Dla pakietu Office 2016 Microsoft Installer (msi) — na podstawie wersji: zainstalowano [aktualizacji 4018295 dla pakietu Microsoft Office 2016, która została opublikowana 6 marca 2018](https://support.microsoft.com/en-us/help/4018295/march-6-2018-update-for-office-2016-kb4018295).

> [!IMPORTANT]
> Do zrealizowania wysokiego bezpieczeństwa, który zapewnia ochronę HYOK, zalecamy serwerów usług AD RMS nie znajdują się w sieci Obwodowej, i że są one używane przez tylko urządzeń zarządzanych. 
> 
> Ponadto zaleca się, aby klaster AD RMS używał sprzętowego modułu zabezpieczeń (HSM, Hardware Security Module), dzięki czemu klucz prywatny certyfikatu licencjodawcy serwera (SLC, Server Licensor Certificate) nie może być ujawniony lub skradziony, jeśli wdrożenie usług AD RMS zostanie kiedykolwiek naruszone lub gdy jego zabezpieczenia zostaną złamane. 

Aby uzyskać informacje na temat wdrażania oraz instrukcje dotyczące usług AD RMS, zobacz [Usługi Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx) w bibliotece systemu Windows Server. 


### <a name="configuring-ad-rms-servers-to-locate-the-certification-url"></a>Konfigurowanie serwerów usług AD RMS można znaleźć adres URL certyfikacji

1. Na każdym serwerze usług AD RMS w klastrze Utwórz wpis rejestru:

    `Computer\HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\GICURL = "<string>"`
    
    Aby uzyskać \<wartość ciągu >, określ jedną z następujących czynności:
    
    - W przypadku klastrów usług AD RMS za pomocą protokołu SSL/TLS:

            https://<cluster_name>/_wmcs/certification/certification.asmx
    
    - Dla usług AD RMS klastrów nie używa protokołu SSL/TLS (testowanie tylko sieci):
        
            http://<cluster_name>/_wmcs/certification/certification.asmx

2. Uruchom ponownie usługi IIS.

### <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Lokalizowanie informacji używanych do określania ochrony usług AD RMS za pomocą etykiety usługi Azure Information Protection

Po skonfigurowaniu etykiety dla **HYOK (AD RMS)** ochrony, należy określić adres URL licencjonowania klastra usług AD RMS. Ponadto należy określić szablon, skonfigurowanego uprawnień przyznać użytkownikom, lub pozwolić użytkownikom na definiowanie uprawnień i użytkowników. 

Można znaleźć identyfikator GUID szablonu i licencjonowanie wartości adresu URL za pomocą konsoli usługi zarządzania prawami dostępu w usłudze Active Directory:

- Aby zlokalizować identyfikator GUID szablonu: rozwiń klaster, a następnie kliknij przycisk **szablony zasad praw**. Z informacji o **dystrybuowanych szablonach zasad praw**, możesz następnie skopiować identyfikator GUID szablonu, którego chcesz użyć. Na przykład: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Aby znaleźć adres URL licencjonowania: kliknij nazwę klastra. Z informacji o **szczegółach klastra** skopiuj wartość **licencjonowania** minus ciąg **/_wmcs/licensing**. Na przykład: https://rmscluster.contoso.com 
    
    Jeśli masz zarówno wartość licencjonowania ekstranetu, jak i wartość licencjonowania intranetu i są one różne: podaj wartość ekstranetu tylko jeśli będziesz udostępniać chronione dokumenty lub wiadomości e-mail partnerom zdefiniowanym za pomocą jawnej relacji zaufania point-to-point. W przeciwnym razie użyj wartości intranetowej i upewnij się, że wszystkie komputery klienckie korzystające z ochrony za pomocą usług AD RMS nawiązują połączenie przy użyciu połączenia intranetowego(na przykład komputery zdalne używają połączenia sieci VPN).


## <a name="next-steps"></a>Następne kroki

Aby skonfigurować etykietę do ochrony HYOK, zobacz [jak konfigurowanie etykiety pod kątem ochrony usługi Rights Management](../deploy-use/configure-policy-protection.md). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]