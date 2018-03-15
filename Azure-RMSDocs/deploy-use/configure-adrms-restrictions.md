---
title: "HYOK ochrony usługi Azure Information Protection"
description: "Poniższe informacje pozwalają zidentyfikować ograniczenia, wymagania wstępne i zalecenia w przypadku wybrania rozwiązania HYOK (AD RMS) i korzystania z usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/14/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ms.openlocfilehash: a0329d66ee71ee815c0700a63172617d1fddf30a
ms.sourcegitcommit: 29d3d4760131eb2642e17b0732f852b6d8cfe314
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="hold-your-own-key-hyok-requirements-and-restrictions-for-ad-rms-protection"></a>Wymagania i ograniczenia dotyczące rozwiązania „hold your own key” (HYOK) dla ochrony za pomocą usług AD RMS

>*Dotyczy: Azure Information Protection*

Najbardziej poufne dokumenty i wiadomości e-mail zwykle są chronione za pomocą usługi Azure Rights Management (Azure RMS), która zapewnia następujące korzyści:

- Nie wymaga infrastruktury serwera, co sprawia, że wdrożenie, i obsługa rozwiązania są szybsze i tańsze niż w przypadku rozwiązania lokalnego.

- Łatwiejsze udostępnianie zawartości partnerom i użytkownikom z innych organizacji przy użyciu uwierzytelniania opartego na chmurze.

- Ścisła integracja z usługami Office 365, takimi jak wyszukiwanie, przeglądarki sieci Web, widoki przestawne, ochrona przed złośliwym oprogramowaniem, zbieranie elektronicznych materiałów dowodowych i aplikacja Delve.

- Śledzenie i odwoływanie dokumentów, powiadomienia e-mail dotyczące udostępnionych poufnych dokumentów.

Usługa Azure RMS chroni dokumenty i wiadomości e-mail organizacji przy użyciu klucza prywatnego dla organizacji, który jest zarządzany przez firmę Microsoft (ustawienie domyślne) lub przez użytkownika (scenariusz „bring your own key”, BYOK). Informacje chronione za pomocą usługi Azure RMS nigdy nie są wysyłane do chmury, a chronione dokumenty i wiadomości e-mail nie są przechowywane na platformie Azure, chyba że jawnie je tam przechowujesz lub korzystasz z innej usługi w chmurze, która przechowuje je na platformie Azure. Aby uzyskać więcej informacji na temat opcji klucza dzierżawy, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md). 

Niektóre organizacje mogą jednak wymagać ochrony wybranych dokumentów i wiadomości e-mail przy użyciu klucza przechowywanego i obsługiwanego lokalnie. Przykładowo może to być wymagane ze względu na obowiązujące przepisy i zachowanie zgodności.  

Ta konfiguracja jest czasami określana jako „hold your own key” (HYOK) i jest obsługiwana przez usługę Azure Information Protection, gdy masz działające wdrożenie usług Active Directory Rights Management Services (AD RMS) spełniające wymagania opisane w następnej sekcji.

W tym scenariuszu HYOK zasady praw i klucz prywatny organizacji, który chroni te zasady, są zarządzane i przechowywane lokalnie, podczas gdy zasady usługi Azure Information Protection dotyczące etykietowania i klasyfikacji pozostają zarządzane i przechowywane na platformie Azure. Podobnie jak w przypadku ochrony za pomocą usługi Azure RMS, informacje chronione za pomocą usług AD RMS nigdy nie są wysyłane do chmury.

> [!NOTE]
> Tej konfiguracji należy używać tylko w razie konieczności i tylko dla dokumentów i wiadomości e-mail, które tego wymagają. Ochrona za pomocą usług AD RMS nie zapewnia wymienionych korzyści, które daje ochrona za pomocą usługi Azure RMS, a jej celem jest „nieprzezroczystość danych za wszelką cenę”.
>
> Nawet w organizacjach używających tej konfiguracji jest ona zazwyczaj przydatna dla mniej niż 10% zawartości wymagającej ochrony. Tej funkcji należy używać tylko w przypadku dokumentów lub wiadomości e-mail spełniających następujące kryteria:
> 
> **Zawartość ma najwyższej klasyfikacji w Twojej organizacji ("Top Secret") i dostęp jest ograniczony do kilku osób**
> 
> **Zawartość nie jest udostępniane poza organizacją**
> 
> **Zawartość jest tylko używane w sieci wewnętrznej**
> 
> **Zawartość nie musi być używane na komputerach Mac lub urządzenie przenośne**

Użytkownicy nie wiedzą, czy z etykietą jest skojarzona ochrona zapewniana przez usługi AD RMS czy usługę Azure RMS. Z powodu ograniczeń dotyczących ochrony przez usługę AD RMS należy się upewnić, że użytkownikom udzielono jasnych wskazówek dotyczących wyboru etykiet powodujących stosowanie ochrony AD RMS. 

[Zasady o określonym zakresie](configure-policy-scope.md) stanowią dobry sposób zapewnienia, że wyłącznie użytkownicy, którzy powinni stosować ochronę AD RMS, będą widzieli etykiety skonfigurowane w celu zastosowania ochrony AD RMS. 

## <a name="additional-limitations-when-using-hyok"></a>Dodatkowe ograniczenia podczas używania funkcji HYOK

Oprócz braku obsługi wymienionych korzyści, które można uzyskać, korzystając z ochrony przy użyciu usług Azure RMS, ochrona za pomocą usług AD RMS z usługą Azure Information Protection ma następujące ograniczenia:

- Brak obsługi pakietu Office 2010 lub Office 2007.

- Poinstruować użytkowników, aby nie wybierz **nie przesyłaj dalej** w programie Outlook, lub podaj dokładne wskazówki. 

    Mimo że można skonfigurować etykietę **nie przesyłaj dalej** Aby użyć HYOK lub usługi Azure Rights Management, użytkownicy mogą również wybrać nie przesyłaj dalej samodzielnie. Tę opcję można wybrać przy użyciu **nie przesyłaj dalej** znajdującego się na **komunikat** karty wstążki pakietu Office lub za pomocą opcji menu programu Outlook. **Nie przesyłaj dalej** opcji menu znajduje się w **pliku** > **uprawnienia**i z **uprawnienia** przycisk z **opcje** kartę na Wstążce. 
    
    Klienta usługi Azure Information Protection zawsze używa usług Azure RMS, gdy użytkownicy wybierają **nie przesyłaj dalej** przycisku w programie Outlook. Jeśli nie chcesz, aby ten problem, można ukryć ten przycisk, ustawiając [ustawienie zasad](../deploy-use/configure-policy-settings.md) **dodać do Wstążki programu Outlook przycisk nie przesyłaj dalej** do **poza**. 
    
    Gdy użytkownicy wybierają **nie przesyłaj dalej** z opcją menu programu Outlook można wybrać z usługi Azure RMS lub AD RMS, ale nie będzie wiadomo, rozwiązania do wiadomości e-mail. Jeśli usługi AD RMS jest używany, gdy powinna być używana usługa Azure RMS, osoby, które są udostępniane zewnętrznie nie można otworzyć te wiadomości e-mail

- Jeśli skonfigurujesz uprawnienia zdefiniowane przez użytkownika dla programu Word, Excel, PowerPoint i Eksploratora plików: W Eksploratorze plików, ochrona jest zawsze stosowana przy użyciu usług Azure RMS zamiast ochrony HYOK (AD RMS). To ograniczenie nie dotyczy bieżąca wersja klienta.

- Jeśli w programie Outlook użytkownik wybierze etykietę powodującą zastosowanie ochrony AD RMS, a następnie zmieni zdanie przed wysłaniem wiadomości e-mail i wybierze etykietę, która dotyczy ochrony za pomocą usługi Azure RMS, nowo wybrana etykieta nie zostanie zastosowana. Użytkownik zobaczy następujący komunikat: **Usługa Azure Information Protection nie może zastosować tej etykiety. Nie masz uprawnień do wykonania tej akcji.**
    
    Jedynym rozwiązaniem problemu jest zamknięcie wiadomości e-mail i rozpoczęcie od początku. Takie samo ograniczenie występuje w podobnym przypadku, gdy użytkownik najpierw wybrał etykietę dotyczącą ochrony za pomocą usługi Azure RMS, a następnie zmienił ją na etykietę, który dotyczy ochrony z użyciem usług AD RMS.

## <a name="requirements-for-hyok"></a>Wymagania dotyczące rozwiązania HYOK

Sprawdź, czy wdrożenie usług AD RMS spełnia następujące wymagania, aby zapewniać ochronę za pomocą usług AD RMS dla usługi Azure Information Protection.

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

- Skonfigurowano synchronizację katalogów między lokalną usługą Active Directory i usługą Azure Active Directory, a użytkownicy, którzy będą korzystać z ochrony usług AD RMS, są skonfigurowani w celu logowania jednokrotnego.

- Jeśli będziesz udostępniać dokumenty lub wiadomości e-mail chronione za pomocą usług AD RMS użytkownikom spoza organizacji: usługi AD RMS są skonfigurowane dla jawnie zdefiniowanych relacji zaufania w bezpośredniej relacji point-to-point z innymi organizacjami przy użyciu zaufanych domen użytkowników (TUD) lub federacyjnych relacji zaufania, które są tworzone za pomocą usług Active Directory Federation Services (AD FS).

- Użytkownicy mają pakiet Office 2013 Pro Plus z dodatkiem Service Pack 1 lub Office 2016 Pro Plus, uruchomiony w systemie Windows 7 z dodatkiem SP1 lub nowszym. Należy zauważyć, że pakiety Office 2010 i Office 2007 nie są obsługiwane w tym scenariuszu.

> [!IMPORTANT]
> W celu zrealizowania wysokiego bezpieczeństwa, które oferuje ten scenariusz, zaleca się, aby serwery usług AD RMS znajdowały się poza Twoją strefą DMZ i były używane wyłącznie przez dobrze zarządzane komputery (a nie, na przykład, przez urządzenia mobilne lub komputery grupy roboczej). 
> 
> Ponadto zaleca się, aby klaster AD RMS używał sprzętowego modułu zabezpieczeń (HSM, Hardware Security Module), dzięki czemu klucz prywatny certyfikatu licencjodawcy serwera (SLC, Server Licensor Certificate) nie może być ujawniony lub skradziony, jeśli wdrożenie usług AD RMS zostanie kiedykolwiek naruszone lub gdy jego zabezpieczenia zostaną złamane. 

Aby uzyskać informacje na temat wdrażania oraz instrukcje dotyczące usług AD RMS, zobacz [Usługi Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx) w bibliotece systemu Windows Server. 


## <a name="configuring-ad-rms-servers-to-locate-the-certification-url"></a>Konfigurowanie serwerów usług AD RMS można znaleźć adres URL certyfikacji

1. Na każdym serwerze usług AD RMS w klastrze Utwórz wpis rejestru:

    `Computer\HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\GICURL = "<string>"`
    
    Aby uzyskać \<wartość ciągu >, określ jedną z następujących czynności:
    
    - W przypadku klastrów usług AD RMS za pomocą protokołu SSL/TLS:

            https://<cluster_name>/_wmcs/certification/certification.asmx
    
    - Dla usług AD RMS klastrów nie używa protokołu SSL/TLS (testowanie tylko sieci):
        
            http://<cluster_name>/_wmcs/certification/certification.asmx

2. Uruchom ponownie usługi IIS.

## <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Lokalizowanie informacji używanych do określania ochrony usług AD RMS za pomocą etykiety usługi Azure Information Protection

Po skonfigurowaniu etykiety dla **HYOK (AD RMS)** ochrony, należy określić adres URL licencjonowania klastra usług AD RMS. Ponadto należy określić szablon, skonfigurowanego uprawnień przyznać użytkownikom, lub pozwolić użytkownikom na definiowanie uprawnień i użytkowników. 

Można znaleźć identyfikator GUID szablonu i licencjonowanie wartości adresu URL za pomocą konsoli usługi zarządzania prawami dostępu w usłudze Active Directory:

- Aby zlokalizować identyfikator GUID szablonu: rozwiń klaster, a następnie kliknij przycisk **szablony zasad praw**. Z informacji o **dystrybuowanych szablonach zasad praw**, możesz następnie skopiować identyfikator GUID szablonu, którego chcesz użyć. Na przykład: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Aby znaleźć adres URL licencjonowania: kliknij nazwę klastra. Z informacji o **szczegółach klastra** skopiuj wartość **licencjonowania** minus ciąg **/_wmcs/licensing**. Na przykład: https://rmscluster.contoso.com 
    
    Jeśli masz zarówno wartość licencjonowania ekstranetu, jak i wartość licencjonowania intranetu i są one różne: podaj wartość ekstranetu tylko jeśli będziesz udostępniać chronione dokumenty lub wiadomości e-mail partnerom zdefiniowanym za pomocą jawnej relacji zaufania point-to-point. W przeciwnym razie użyj wartości intranetowej i upewnij się, że wszystkie komputery klienckie korzystające z ochrony za pomocą usług AD RMS nawiązują połączenie przy użyciu połączenia intranetowego(na przykład komputery zdalne używają połączenia sieci VPN).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat tej funkcji oraz wskazówki dotyczące jej stosowania, zobacz wpis na blogu: [Azure Information Protection with HYOK (Hold Your Own Key)](https://cloudblogs.microsoft.com/enterprisemobility/2016/08/10/azure-information-protection-with-hyok-hold-your-own-key/) (Usługa Azure Information Protection z rozwiązaniem HYOK — Hold Your Own Key).

Aby skonfigurować etykietę w celu zastosowania ochrony za pomocą usług AD RMS, zobacz [Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management](../deploy-use/configure-policy-protection.md). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]