---
title: Ochrona funkcji HYOK dla usługi Azure Information Protection
description: Omówienie ochrony HYOK (AD RMS) przy użyciu usługi Azure Information Protection, jego obsługiwane scenariusze, ograniczenia, wymagania wstępne i zalecenia.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ms.openlocfilehash: d1613d30dbb59395254ca5bd56222c15fcb75058
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393569"
---
# <a name="hold-your-own-key-hyok-protection-for-azure-information-protection"></a>Przytrzymaj własne ochrony klucza (HYOK) dla usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Skorzystaj z poniższych informacji, aby zrozumieć, co utrzymywać własne ochrony klucza (HYOK) jest usługi Azure Information Protection i jak jest inna niż domyślna ochrona oparta na chmurze. Przed użyciem funkcji HYOK ochrony, upewnij się, że rozumiesz, gdy jest odpowiednie, obsługiwane scenariusze, ograniczenia i wymagania. 

## <a name="cloud-based-protection-vs-hyok"></a>Ochrona oparta na chmurze programu vs. HYOK

W przypadku ochrony najbardziej poufnych dokumentów i wiadomości e-mail przy użyciu usługi Azure Information Protection, możesz to robić przez zastosowanie klucza oparta na chmurze, korzystającą z ochrony usługi Azure Rights Management (Azure RMS) w celu zapewnia następujące korzyści:

- Nie wymaga infrastruktury serwera, co sprawia, że wdrożenie, i obsługa rozwiązania są szybsze i tańsze niż w przypadku rozwiązania lokalnego.

- Łatwiejsze udostępnianie zawartości partnerom i użytkownikom z innych organizacji przy użyciu uwierzytelniania opartego na chmurze.

- Ścisła integracja z innymi usługami platformy Azure i usługi Office 365, takich jak wyszukiwanie, przeglądarki sieci web, widoki przestawne, złośliwym oprogramowaniem, zbieranie elektronicznych materiałów dowodowych i aplikacji Delve.

- Śledzenie i odwoływanie dokumentów, powiadomienia e-mail dotyczące udostępnionych poufnych dokumentów.

Klucz oparte na chmurze chroni dokumenty i wiadomości e-mail organizacji przy użyciu klucza prywatnego dla organizacji, który jest zarządzany przez firmę Microsoft (ustawienie domyślne), lub przez użytkownika ("bring your own key" lub BYOK). Aby uzyskać więcej informacji na temat opcji klucza dzierżawy, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](plan-implement-tenant-key.md).

Dokumentów i wiadomości e-mail możesz chronić może znajdować się w chmurze lub lokalnie. Aby uzyskać więcej informacji na temat sposobu działania procesu ochrony dla tego klucza oparta na chmurze, zobacz [co to jest Azure Rights Management?](what-is-azure-rms.md )

Usługi Office 365 i aplikacji działających w chmurze dla Twojej dzierżawy można zintegrować z usługi Azure Information Protection, aby firmy ważne funkcje, takie jak usługi wyszukiwania, indeksowania, archiwizacji i chroniące przed złośliwym kodem w dalszym ciągu działać bezproblemowo zawartości który jest chroniony przez usługę Azure Information Protection. Ta możliwość odczytu zaszyfrowaną zawartość dla tych scenariuszy często nazywa się "rozsądkiem ponad danymi". Na przykład jest tę możliwość, która umożliwia usłudze Exchange Online odszyfrowywania wiadomości e-mail w poszukiwaniu złośliwego oprogramowania, skanowanie i systemem reguły zapobieganie utracie danych zaszyfrowanych wiadomości e-mail.

Jednak wymagania prawne, organizacje kilka może być konieczne szyfrowanie zawartości przy użyciu klucza, która jest odizolowana od chmury. Izolacja oznacza to, czy zaszyfrowana zawartość mogą być odczytywane tylko przez lokalnymi aplikacjami i usługami lokalnymi. Ta opcja zarządzania kluczami jest obsługiwana przez usługę Azure Information Protection i jest określany jako "hold your own key" lub funkcji HYOK. Gdy używasz usługi Azure Information Protection z rozwiązaniem HYOK dzierżawy ma zarówno klucz oparte na chmurze, jak i klucz w środowisku lokalnym.

## <a name="hyok-guidance-and-best-practices"></a>Wskazówki dotyczące rozwiązania HYOK i najlepsze rozwiązania

Użyj funkcji HYOK ochrony tylko dla dokumentów i wiadomości e-mail, które wymagają klucza szyfrowania, aby być odizolowany od chmury. Ochrona za pomocą funkcji HYOK nie zapewnia wymienionych korzyści, które otrzymujesz, gdy używasz opartych na chmurze ochrona klucza i często jest kosztem "nieprzezroczystość danych". Oznacza to frazy, że tylko lokalne aplikacje i usługi będą mogli otworzyć chronione HYOK danych; oparte na chmurze usług i aplikacji nie może podejmować HYOK chronionych danych.

Nawet w przypadku organizacji, które używają funkcji HYOK ochrony jest zazwyczaj jest odpowiednia dla niewielkiej liczby dokumentów, które mają być chronione. Należy używać go tylko dla dokumentów i spełniają następujące kryteria:

- Zawartość została sklasyfikowana jako w Twojej organizacji ("ściśle tajne") i dostęp jest ograniczony do kilku osób

- Zawartość nie jest udostępniana poza organizacją

- Zawartość jest używana tylko w sieci wewnętrznej

Ponieważ ochrona HYOK jest dostępna opcja konfiguracji administratora dla etykiety, przepływami pracy użytkownika pozostają takie same, niezależnie od tego, czy ochrona używa klucza oparta na chmurze lub funkcji HYOK.

[Zasady z określonym zakresem](configure-policy-scope.md) są dobrym sposobem, aby upewnić się, czy tylko użytkowników, którzy potrzebują do stosowania ochrony HYOK Zobacz etykiety, które są skonfigurowana pod kątem ochrony funkcji HYOK. 

## <a name="supported-scenarios-for-hyok"></a>Obsługiwane scenariusze dotyczące rozwiązania HYOK

Aby zastosować ochronę HYOK, korzystanie z etykiet usługi Azure Information Protection. 

W poniższej tabeli wymieniono obsługiwane scenariusze ochrony zawartości przy użyciu etykiet, które są skonfigurowane dla funkcji HYOK i otwierania (Korzystanie z) z zawartości chronionej przez HYOK.

|Platforma|Aplikacja|Obsługiwane|
|----------------------|----------|-----------|
|Windows|Klient usługi Azure Information Protection z pakietem Office 2016 lub Office 2013 <br /><br />— Word, Excel, PowerPoint|Ochrona: Tak<br /><br />Użycie: Tak|
|Windows|Klient usługi Azure Information Protection z pakietem Office 2016 lub Office 2013 <br /><br />-Programu outlook|Ochrona: Tak<br /><br />Użycie: Tak|
|Windows|Klient usługi Azure Information Protection z Eksploratorem plików|Ochrona: Tak <br /><br />Użycie: Tak|
|Windows|Przeglądarka usługi Azure Information Protection|Ochrona: Nie dotyczy<br /><br />Użycie: Tak|
|Windows|Klient usługi Azure Information Protection przy użyciu programu PowerShell, poleceń cmdlet etykietowania|Ochrona: Tak<br /><br />Użycie: Tak|
|Windows|Skaner usługi Azure Information Protection|Ochrona: Tak<br /><br />Użycie: Tak|
|Windows|Aplikacja do udostępniania usługi Rights Management|Ochrona: Nie<br /><br />Użycie: Tak|
|MacOS|Pakiet Office dla komputerów Mac <br /><br /> — Word, Excel, PowerPoint|Ochrona: Nie<br /><br />Użycie: Tak|
|MacOS|Pakiet Office dla komputerów Mac<br /><br />-Programu outlook|Ochrona: Nie<br /><br />Użycie: Tak|
|MacOS|Aplikacja do udostępniania usługi Rights Management|Ochrona: Nie<br /><br />Użycie: Tak|
|iOS|Office Mobile <br /><br />— Word, Excel, PowerPoint|Ochrona: Nie<br /><br />Użycie: Tak|
|iOS|Office Mobile <br /><br />-Outlook|Ochrona: Nie<br /><br />Użycie: Nie|
|iOS|Przeglądarka usługi Azure Information Protection|Ochrona: Nie dotyczy<br /><br />Użycie: Tak|
|Android|Office Mobile <br /><br />— Word, Excel, PowerPoint|Ochrona: Nie<br /><br />Użycie: Tak|
|Android|Office Mobile <br /><br />-Programu outlook|Ochrona: Nie<br /><br />Użycie: Nie|
|Android|Przeglądarka usługi Azure Information Protection|Ochrona: Nie dotyczy<br /><br />Użycie: Tak|
|sieć Web|Program Outlook w sieci web|Ochrona: Nie<br /><br />Użycie: Nie|
|sieć Web|Office Online<br /><br />— Word, Excel, PowerPoint|Ochrona: Nie<br /><br />Użycie: Nie|
|Uniwersalny|Uniwersalne aplikacje pakietu Office<br /><br />— Word, Excel, PowerPoint|Ochrona: Nie<br /><br />Użycie: Nie|


## <a name="additional-limitations-when-using-hyok"></a>Dodatkowe ograniczenia podczas używania funkcji HYOK

Ponadto za pomocą funkcji HYOK ochrony za pomocą etykiety usługi Azure Information Protection ma następujące ograniczenia:

- Nie obsługuje pakietu Office w wersjach starszych niż pakiet Office 2013.

- Usługi Office 365 i innych usług online nie będzie można odszyfrować chroniony HYOK dokumentów i wiadomości e-mail, aby sprawdzić zawartość i podejmować działania na nich. To ograniczenie rozszerza HYOK chronionych dokumentów i wiadomości e-mail chronione za pomocą łącznika usługi Rights Management. 
    
    Ta utrata funkcji HYOK chronionych wiadomości e-mail zawiera skanery złośliwego oprogramowania, rozwiązania zapobieganie utracie danych, reguł routingu wiadomości e-mail, rejestrowanie, zbierania elektronicznych materiałów dowodowych, archiwizowanie rozwiązań i program Exchange ActiveSync. Ponadto użytkownicy nie wiedzą, dlaczego niektóre urządzenia nie można otworzyć wiadomości e-mail chronione HYOK i może to spowodować wywołania do pomocy technicznej. Ze względu na ograniczenia te wiele zaleca się używać rozwiązania HYOK ochrony dla wiadomości e-mail.

## <a name="implementing-hyok"></a>Implementowanie rozwiązania HYOK

HYOK jest obsługiwana przez usługę Azure Information Protection, gdy masz działające wdrożenie Active Directory Rights Management Services (AD RMS), wymagania, które są opisane w następnej sekcji. W tym scenariuszu zasad praw użytkowania i klucz prywatny organizacji, który chroni te zasady są zarządzane i przechowywane lokalnie, podczas zasad usługi Azure Information Protection, etykietowania i klasyfikacji pozostają zarządzane i przechowywane na platformie Azure. 

Nie należy mylić HYOK i Azure Information Protection przy użyciu pełne wdrożenie usług AD RMS i Azure Information Protection lub jako alternatywa dla migracji usługi AD RMS do usługi Azure Information Protection. HYOK jest obsługiwana tylko przez zastosowanie etykiety, nie oferuje równoważności funkcji za pomocą usług AD RMS i nie obsługuje wszystkie konfiguracje wdrożenia usług AD RMS:

- Aby uzyskać więcej informacji na temat scenariuszy, HYOK obsługuje ochronę zawartości i korzystanie z zawartości chronionej, zobacz [obsługiwane scenariusze dotyczące rozwiązania HYOK](#supported-scenarios-for-hyok) sekcji.

- Aby uzyskać instrukcje dotyczące migracji z usług AD RMS, zobacz [Migrowanie z usług AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

- Aby uzyskać więcej informacji o wymaganiach dotyczących wdrożenia usług AD RMS zobacz następną sekcję.

### <a name="requirements-for-ad-rms-to-support-hyok"></a>Wymagania dotyczące usług AD RMS do obsługi funkcji HYOK

Wdrożenie usług AD RMS muszą spełniać poniższe wymagania, aby zapewnić ochronę rozwiązania HYOK dla etykiety usługi Azure Information Protection.

- Konfiguracja usług AD RMS:
    
  - Minimalną wersję systemu Windows Server 2012 R2: Wymagane w środowiskach produkcyjnych, lecz do celów testowania lub ewaluacji, można użyć minimalnej wersji systemu Windows Server 2008 R2 z dodatkiem Service Pack 1.
    
  - Jeden z następujących topologii:
        
    - Pojedynczy las z jeden klaster główny usług AD RMS. 
        
    - Wiele lasów z niezależnych klastrów głównego usług AD RMS i użytkownicy nie mają dostępu do zawartości, która jest chroniona przez użytkowników w innych lasach.
        
    - Klastry wielu lasów z usługami AD RMS w każdym z nich. Każdy klaster usług AD RMS udostępnia adres URL licencjonowania, który wskazuje na tym samym klastrze usług AD RMS. W tym klastrze usług AD RMS, należy zaimportować wszystkie certyfikaty zaufanego użytkownika domeny (TUD) ze wszystkich innych klastrów usług AD RMS. Aby uzyskać więcej informacji na temat tej topologii, zobacz [zaufanej domeny użytkownika](https://technet.microsoft.com/library/dd983944(v=ws.10).aspx).
        
    Jeśli masz wiele klastrów AD RMS w oddzielnym lesie, należy usunąć wszystkich etykiet, w ramach globalnych zasad, które zabezpieczać HYOK (AD RMS) i skonfiguruj [zasad o określonym zakresie](configure-policy-scope.md) dla każdego klastra. Następnie Przypisz użytkowników dla każdego klastra, do ich zasad o określonym zakresie, upewniając się, że nie należy używać grup, które mogłyby spowodować użytkownika są przypisane do więcej niż jedna zasada o określonym zakresie. Wynik powinien być, że każdy użytkownik ma etykiety dla jednego klastra usług AD RMS. 
    
  - [Tryb kryptograficzny 2](https://technet.microsoft.com/library/hh867439.aspx): Tryb można potwierdzić, sprawdzając właściwości klastra AD RMS, **ogólne** kartę.
    
  - Każdy serwer usług AD RMS jest skonfigurowany jako adres URL certyfikacji. [Instrukcje](#configuring-ad-rms-servers-to-locate-the-certification-url) 
    
  - Punkt połączenia usługi (SCP) nie jest zarejestrowany w usłudze Active Directory: Punkt połączenia usługi nie jest używany, korzystając z ochrony usług AD RMS za pomocą usługi Azure Information Protection. 
    
      - Jeśli masz zarejestrowany punkt połączenia usługi dla wdrożenia usług AD RMS, musisz go usunąć, aby [odnajdywanie usług](./rms-client/client-deployment-notes.md#rms-service-discovery) dla ochrony za pomocą usługi Azure Rights Management powiodło się. 
        
      - Jeśli instalujesz nowy klaster AD RMS dla usługi HYOK, pomiń krok, aby zarejestrować punkt połączenia z usługą podczas konfiguracji pierwszego węzła. Dla każdego dodatkowego węzła upewnij się, że serwer jest skonfigurowany dla adresu URL certyfikacji przed Dodaj rolę usług AD RMS i Dołącz do istniejącego klastra.
    
  - Serwery usług AD RMS są skonfigurowane do używania protokołu SSL/TLS z ważnym certyfikatem x.509 jest zaufany przez klientów nawiązujących połączenie: Wymagane dla środowisk produkcyjnych, ale nie są wymagane do celów testowania lub ewaluacji.
    
  - Skonfigurowane szablony praw.
    
  - Nie jest skonfigurowany dla usługi IRM programu Exchange.
    
  - Dla urządzeń przenośnych i komputerów Mac: [Active Directory Rights zarządzania rozszerzenia usług urządzeń przenośnych](https://technet.microsoft.com/library/dn673574.aspx) jest zainstalowany i skonfigurowany.

- Skonfigurowano synchronizację katalogów między w lokalnej usłudze Active Directory i Azure Active Directory i użytkowników, którzy będą korzystać z ochrony HYOK skonfigurowanymi pod kątem logowania jednokrotnego.

- Jeśli będziesz udostępniać dokumenty lub wiadomości e-mail chronione za pomocą funkcji HYOK innym osobom spoza organizacji: Usługi AD RMS jest skonfigurowane dla jawnie zdefiniowanych relacji zaufania w bezpośredniej relacji point-to-point z innymi organizacjami przy użyciu zaufanych domen użytkowników (TUD) lub federacyjnych relacji zaufania, które są tworzone za pomocą usługi Active Directory Federation Services (AD FS).

- Użytkownicy mają pakiet Office 2016 Professional Plus lub Office 2013 Professional Plus z dodatkiem Service Pack 1, systemem Windows 7 z dodatkiem SP1 lub nowszym. Należy zauważyć, że pakiety Office 2010 i Office 2007 nie są obsługiwane w tym scenariuszu.
    
    - Dla pakietu Office 2016, Microsoft Installer (.msi)-na podstawie wersji: Zainstalowano [aktualizacji 4018295 dla programu Microsoft Office 2016, wydanej w dniu 6 marca 2018](https://support.microsoft.com/en-us/help/4018295/march-6-2018-update-for-office-2016-kb4018295).

> [!IMPORTANT]
> Do zrealizowania wysokiego bezpieczeństwa, które oferuje ochronę HYOK, zaleca się, że serwery AD RMS nie znajdują się w sieci Obwodowej i czy są one używane przez tylko urządzenia zarządzane. 
> 
> Ponadto zaleca się, aby klaster AD RMS używał sprzętowego modułu zabezpieczeń (HSM, Hardware Security Module), dzięki czemu klucz prywatny certyfikatu licencjodawcy serwera (SLC, Server Licensor Certificate) nie może być ujawniony lub skradziony, jeśli wdrożenie usług AD RMS zostanie kiedykolwiek naruszone lub gdy jego zabezpieczenia zostaną złamane. 

Aby uzyskać informacje na temat wdrażania oraz instrukcje dotyczące usług AD RMS, zobacz [Usługi Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx) w bibliotece systemu Windows Server. 


### <a name="configuring-ad-rms-servers-to-locate-the-certification-url"></a>Konfigurowanie serwerów usług AD RMS, aby znaleźć adres URL certyfikacji

1. Na każdym serwerze usług AD RMS w klastrze Utwórz wpis rejestru:

    `Computer\HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\GICURL = "<string>"`
    
    Aby uzyskać \<wartość ciągu >, określ jedną z następujących czynności:
    
    - W przypadku klastrów usług AD RMS za pomocą certyfikatu SSL/TLS:

            https://<cluster_name>/_wmcs/certification/certification.asmx
    
    - Dla usług AD RMS klastrów nie przy użyciu protokołu SSL/TLS (testowanie tylko sieci):
        
            http://<cluster_name>/_wmcs/certification/certification.asmx

2. Uruchom ponownie usługi IIS.

### <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Lokalizowanie informacji używanych do określania ochrony usług AD RMS za pomocą etykiety usługi Azure Information Protection

Po skonfigurowaniu etykiety dla **HYOK (AD RMS)** ochrony, należy określić adres URL licencjonowania klastra usług AD RMS. Ponadto należy określić szablon, skonfigurowanego dla uprawnień przyznać użytkownikom lub pozwolić użytkownikom na definiowanie uprawnień i użytkowników. 

Można znaleźć identyfikator GUID szablonu i licencjonowania wartości adresu URL konsoli usługi zarządzania prawami dostępu w usłudze Active Directory:

- Aby zlokalizować identyfikator GUID szablonu: Rozwiń klaster, a następnie kliknij przycisk **szablonów zasad praw**. Z informacji o **dystrybuowanych szablonach zasad praw**, możesz następnie skopiować identyfikator GUID szablonu, którego chcesz użyć. Przykład: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Aby znaleźć adres URL licencjonowania: Kliknij nazwę klastra. Z informacji o **szczegółach klastra** skopiuj wartość **licencjonowania** minus ciąg **/_wmcs/licensing**. Na przykład: https://rmscluster.contoso.com 
    
    Jeśli masz zarówno wartość licencjonowania ekstranetu, jak również wartość licencjonowania intranetu i są one różne: Podaj wartość ekstranetu tylko wtedy, gdy będziesz udostępniać chronione dokumenty lub wiadomości e-mail partnerom zdefiniowanym za pomocą jawnej relacji zaufania point-to-point. W przeciwnym razie użyj wartości intranetowej i upewnij się, że wszystkie komputery klienckie korzystające z ochrony za pomocą usług AD RMS nawiązują połączenie przy użyciu połączenia intranetowego(na przykład komputery zdalne używają połączenia sieci VPN).


## <a name="next-steps"></a>Następne kroki

Aby skonfigurować etykiety dla ochrony HYOK, zobacz [sposobu konfigurowania etykiety dla ochrony usługi Rights Management](configure-policy-protection.md). 
