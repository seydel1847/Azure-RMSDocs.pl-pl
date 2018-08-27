---
title: Często zadawane pytania dotyczące usługi Azure Information Protection
description: Niektóre często zadawane pytania dotyczące usługi Azure Information Protection i jej usługi ochrony danych, Azure Rights Management (Azure RMS).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 661f6bb0fa434483593cfc80053100376ec7f0f8
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42806031"
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Często zadawane pytania dotyczące usługi Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Masz pytanie dotyczące usługi Azure Information Protection lub usługi Azure Rights Management (Azure RMS)? Zobacz, czy nie znajdziesz tutaj odpowiedzi.

Te strony — często zadawane pytania są regularnie aktualizowana, a nowe informacje będą publikowane w comiesięcznych ogłoszeniach o aktualizacji dokumentacji na [blog techniczny usługi Azure Information Protection](https://aka.ms/AIPblog).

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Na czym polega różnica między usługą Azure Information Protection i usługą Azure Rights Management?

Usługa Azure Information Protection udostępnia funkcje klasyfikacji, etykietowania i ochrony dokumentów i wiadomości e-mail organizacji. Ta technologia ochrony korzysta z usługi Azure Rights Management; która jest obecnie składnikiem usługi Azure Information Protection.

## <a name="what-is-the-role-of-identity-management-for-azure-information-protection"></a>Czym jest rola zarządzania tożsamościami dla usługi Azure Information Protection?

Użytkownik musi mieć prawidłową nazwę użytkownika i hasło dostępu do zawartości chronionej przez usługę Azure Information Protection. Aby uzyskać więcej informacji na temat sposobu, w jaki usługa Azure Information Protection ułatwia zabezpieczanie danych, zobacz temat [Rola usługi Azure Information Protection w zabezpieczaniu danych](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Jaka subskrypcja jest potrzebna do korzystania z usługi Azure Information Protection i jakie funkcje obejmuje ta subskrypcja?
Zapoznaj się z listą funkcji i informacje o subskrypcji na [cennika usługi Azure Information Protection](https://azure.microsoft.com/en-us/pricing/details/information-protection) strony. 

Jeśli masz subskrypcję usługi Office 365, która obejmuje ochronę danych usługi Azure Rights Management, Pobierz [arkusz danych dotyczący licencjonowania usługi Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf), który zawiera również niektóre często zadawane pytania dotyczące licencjonowania.

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>Czy klient usługi Azure Information Protection służy wyłącznie do obsługi subskrypcji, które obejmują klasyfikowanie i etykietowanie?

Nie. Choć większość prezentacji i pokazów poświęconych klientowi usługi Azure Information Protection pokazuje obsługę klasyfikacji i etykietowania, to z usługi tej można korzystać również w odniesieniu do subskrypcji obejmujących wyłącznie ochronę z użyciem usługi Azure Rights Management.

Po zainstalowaniu klienta usługi Azure Information Protection dla systemu Windows bez zasad usługi Azure Information Protection klient automatycznie działa w [trybie tylko do ochrony](./rms-client/client-protection-only-mode.md). W tym trybie użytkownicy mogą łatwo stosować szablony usługi Rights Management oraz uprawnienia niestandardowe. W przypadku wykupienia w późniejszym czasie subskrypcji, która obejmuje funkcje klasyfikacji i etykietowania, klient automatycznie przełączy się do trybu standardowego po pobraniu zasad usługi Azure Information Protection.

Jeśli obecnie używasz usługi Rights Management sharing dla Windows, zaleca się zastąpić tę aplikację za pomocą klienta usługi Azure Information Protection. Obsługa aplikacji do udostępniania zakończy się 31 stycznia 2019 r. Zachęcamy do zapoznania się z tematem [Zadania, które były wykonywane w aplikacji RMS sharing](./rms-client/upgrade-client-app.md), który zawiera informacje przydatne w okresie przejściowym.

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Musisz być administratorem globalnym, aby skonfigurować usługę Azure Information Protection, czy można to oddelegować do innych administratorów?

Administratorzy globalni dla dzierżawy usługi Office 365 lub dzierżawy usługi Azure AD mogą oczywiście uruchamiać wszystkie zadania administracyjne dla usługi Azure Information Protection. Jednak jeśli chcesz przypisać uprawnienia administracyjne do innych użytkowników, masz następujące opcje:

- **Administrator usługi Information Protection**: rola administratora tej usługi Azure Active Directory pozwala administratorowi, skonfiguruj wszystkie aspekty usługi Azure Information Protection, ale nie do innych usług. Administrator z tą rolą może aktywować i dezaktywować usługę ochrony usługi Azure Rights Management, skonfigurować ustawienia ochrony i etykiety i skonfigurować zasady usługi Azure Information Protection. Ponadto administrator z tą rolą można uruchomić wszystkie polecenia cmdlet programu PowerShell dla [klienta Azure Information Protection](./rms-client/client-admin-guide-powershell.md) i [AADRM module](administer-powershell.md). 
    
    Aby przypisać użytkownika do tej roli administracyjnej, zobacz [przypisać użytkownika do ról administratora w usłudze Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal).

- **Administrator zabezpieczeń**: rola administratora tej usługi Azure Active Directory pozwala administratorowi, skonfiguruj wszystkie aspekty usługi Azure Information Protection w witrynie Azure portal, oprócz konfigurowania niektóre aspekty innych usług platformy Azure. Administrator z tą rolą nie może uruchomić dowolne z [poleceń cmdlet programu PowerShell w module AADRM](administer-powershell.md).
    
    Aby przypisać użytkownika do tej roli administracyjnej, zobacz [przypisać użytkownika do ról administratora w usłudze Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Aby zobaczyć, jakie inne uprawnienia użytkownika z tą rolą, zobacz [dostępnych ról](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) sekcji w dokumentacji usługi Azure Active Directory.

- Usługa Azure Rights Management **administratora globalnego** i **Administrator łącznika**: dla tych ról administratora usługi Azure Rights Management, pierwszy przyznaje użytkownikom uprawnienia do wszystkich [ Polecenia cmdlet programu PowerShell w module AADRM](administer-powershell.md) bez nadawania roli administratora globalnego dla innych usług w chmurze, a druga rola przyznaje uprawnienia do uruchamiania tylko łącznika usługi Rights Management (RMS). Żadna z tych ról administracyjnych nie przyznają uprawnienia do konsol zarządzania lub do korzystania z trybu administratora w witrynie śledzenia dokumentów.

    Można przypisać jedną z tych ról administracyjnych, należy użyć polecenia cmdlet programu PowerShell AADRM [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator).

Dodatkowe kwestie, na które należy zwrócić uwagę:

- Jeśli skonfigurowano [kontrolek dołączania](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), ta konfiguracja nie ma wpływu na możliwość administrowania usługą Azure Information Protection, z wyjątkiem łącznika usługi RMS. Na przykład jeśli kontrolki dołączania zostały skonfigurowane w taki sposób, że możliwość ochrony zawartości jest ograniczona do grupy Dział IT, konto używane do instalowania i konfigurowania łącznika usługi RMS musi należeć do tej grupy. 

- Użytkownicy, którzy są przypisani do roli administracyjnej nie może automatycznie usunąć ochrony dokumentów lub wiadomości e-mail, które były chronione przez usługę Azure Information Protection. Tylko użytkownicy z przypisaną administratorów można to zrobić, a po włączeniu funkcji superużytkowników. Jednak każdy użytkownik, przypisać uprawnienia administracyjne do usługi Azure Information Protection może przypisywać użytkowników jako administratorów również ich własnego konta. Mogą oni również włączyć funkcję administratorów. Te akcje są rejestrowane w dzienniku administratora. Aby uzyskać więcej informacji, zobacz sekcję najlepszych praktyk dotyczących zabezpieczeń w temacie [Konfigurowanie superużytkowników usług Azure Rights Management i usług odnajdywania lub odzyskiwania danych](configure-super-users.md). 


## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Czy usługa Azure Information Protection obsługuje scenariusze lokalne i hybrydowe?

Tak. Mimo, że usługa Azure Information Protection jest rozwiązaniem opartym na chmurze, może służyć do klasyfikacji, etykietowania oraz ochrony dokumentów i wiadomości e-mail, które są przechowywane lokalnie oraz w chmurze.

Jeśli używasz programu Exchange Server, SharePoint Server oraz serwerów plików systemu Windows, możesz wdrożyć [łącznik usługi Rights Management](deploy-rms-connector.md), by serwery te lokalne mogły używać usługi Azure Rights Management do ochrony wiadomości e-mail i dokumentów. Można także przeprowadzić synchronizację i federację kontrolerów domeny usługi Active Directory z usługą Azure AD, aby usprawnić środowisko uwierzytelniania dla użytkowników, na przykład za pomocą programu [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Usługa Azure Rights Management automatycznie generuje certyfikaty XrML i zarządza nimi zgodnie z wymaganiami, dlatego nie korzysta z lokalnej infrastruktury kluczy publicznych. Aby uzyskać więcej informacji o używaniu certyfikatów przez usługę Azure Rights Management, zobacz sekcję [Wskazówki dotyczące działania usługi Azure RMS: pierwsze użycie, ochrona zawartości, zużycie zawartości](./how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) w artykule [Jak działa usługa Azure RMS?](./how-does-it-work.md).

## <a name="what-types-of-data-can-azure-information-protection-classify-and-protect"></a>Jakie typy danych można usługi Azure Information Protection klasyfikować i chronić?

Usługa Azure Information Protection można klasyfikować i chronić wiadomości e-mail i dokumenty, czy są one znajdujących się lokalnie lub w chmurze. Te dokumenty zawierają słowa dokumentów, programu Excel arkusze kalkulacyjne, PowerPoint prezentacje, plików PDF dokumentów, plików tekstowych i pliki obrazów. Aby uzyskać listę obsługiwanych typów dokumentów, zobacz listę [typy plików obsługiwane](./rms-client/client-admin-guide-file-types.md) w podręczniku administratora.

Usługa Azure Information Protection nie klasyfikowania i ochrony danych strukturalnych, takich jak pliki bazy danych, elementy kalendarza, raporty usługi Power BI w Yammerze wpisów, zawartość aplikacji Sway i Notesy programu OneNote.

## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Czy mogę zobaczyć, usługi Azure Information Protection znajduje się w aplikacji w chmurze dostępnych dla dostępu warunkowego — jak to działa?

Tak, w publicznej wersji zapoznawczej oferty, teraz można skonfigurować dostęp warunkowy usługi Azure AD dla usługi Azure Information Protection.

Po otwarciu dokumentu, który jest chroniony przez usługę Azure Information Protection Administratorzy mogą teraz blokować lub udzielić dostępu użytkownikom w ramach ich dzierżawy, oparte na formanty standardowe dostępu warunkowego. Wymaganie uwierzytelniania wieloskładnikowego (MFA) jest jednym z najczęściej żądanej warunków. Inny on, że urządzenia muszą być [zgodne z zasadami usługi Intune](/intune/conditional-access-intune-common-ways-use) , aby na przykład urządzenia przenośne spełniają wymagania dotyczące hasła i minimalną wersję systemu operacyjnego, a komputery muszą być przyłączone do domeny.

Uzyskać więcej informacji i przykłady przewodnika, zobacz następujący wpis w blogu: [zasady dostępu warunkowego dla usługi Azure Information Protection](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/).

Informacje dodatkowe:

- Dla komputerów Windows: w przypadku bieżącej wersji zapoznawczej, zasady dostępu warunkowego usługi Azure Information Protection są oceniane po [zainicjowaniu środowiska użytkownika](./how-does-it-work.md#initializing-the-user-environment) (ten proces jest również nazywany uruchamianie), i następnie na 30 dni.

- Można dostosować, jak często uzyskiwanie oceniane zasady dostępu warunkowego. Można to zrobić, konfigurując okres istnienia tokenu. Aby uzyskać więcej informacji, zobacz [okresów istnienia tokenu można skonfigurować w usłudze Azure Active Directory](/azure/active-directory/active-directory-configurable-token-lifetimes).

- Zaleca się, że należy dodawać konta administratora do swoich zasad dostępu warunkowego, ponieważ te konta nie będzie dostęp do bloku usługi Azure Information Protection w witrynie Azure portal.

- Jeśli używasz wielu aplikacji w chmurze dla dostępu warunkowego, może nie być wyświetlana **Microsoft Azure Information Protection** wyświetlane na liście, aby wybrać. W tym przypadku użyj pola wyszukiwania w górnej części listy. Zacznij wpisywać tekst "Microsoft Azure Information Protection" do filtrowania dostępnych aplikacji. Jeśli masz subskrypcję obsługiwane, zostaną wyświetlone **Microsoft Azure Information Protection** do wybrania. 

## <a name="whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365"></a>Jaka jest różnica między etykiety usługi Azure Information Protection i etykiety w usłudze Office 365?

Etykiety usługi Azure Information Protection pozwalają zastosować spójne zasady klasyfikacji i ochrony dokumentów i wiadomości e-mail, czy są one w środowisku lokalnym lub w chmurze. Ta klasyfikacja i ochrona jest niezależny od której jest przechowywana zawartość lub sposobu przenoszenia. [Etykiety w Office 365 Security & Compliance](https://support.office.com/article/af398293-c69d-465e-a249-d74561552d30) pozwalają klasyfikowania dokumentów i wiadomości e-mail na potrzeby inspekcji i przechowywania w usługach Office 365 po tej zawartości. 

Już dziś Zastosuj i niezależnie zarządzać tych etykiet, ale firma Microsoft pracuje w kierunku kompleksowe i ujednolicone strategii etykietowania dla wielu usług, które obejmują usługi Azure Information Protection, Office 365, Microsoft Cloud App Security i Windows Ochrona informacji. Prawdopodobnie słyszałeś tej strategii, określane jako "Microsoft Information Protection" (MIP). Ten sam schemat etykietowania i magazynu będzie również dostępna dla dostawców oprogramowania. Aby uzyskać więcej informacji, zobacz w blogu, [spójnych zasad etykietowania i ochrony, do usługi Office 365 i Azure Information Protection](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Consistent-labeling-and-protection-policies-coming-to-Office-365/ba-p/161553).

## <a name="whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner"></a>Jaka jest różnica między infrastruktury klasyfikacji plików systemu Windows Server i skaner usługi Azure Information Protection?

Przez jakiś czas dotąd istniała możliwość użycia infrastruktury klasyfikacji plików w systemie Windows Server, aby klasyfikować dokumenty i chronić je przy użyciu [łącznika usługi Rights Management](deploy-rms-connector.md) (tylko w Office dokumenty) lub [programu PowerShell skrypt](./rms-client/configure-fci.md) (wszystkich typów plików). 

Teraz możesz używać [skanera usługi Azure Information Protection](deploy-aip-scanner.md). Skaner używa klienta usługi Azure Information Protection i zasad usługi Azure Information Protection do dokumentów etykiety (wszystkich typów plików), tak, aby następnie sklasyfikowanych i chronionych opcjonalnie tych dokumentów.

Główne różnice między te dwa rozwiązania:

|System Windows Server infrastruktury klasyfikacji plików|Skaner usługi Azure Information Protection|
|--------------------------------|-------------------------------------|
|Obsługiwane magazyny danych: <br /><br />— Foldery lokalne w systemie Windows Server|Obsługiwane magazyny danych: <br /><br />— Foldery lokalne w systemie Windows Server<br /><br />-Windows plików, udziały i Magazyn dołączony do sieci<br /><br />— Program SharePoint Server 2016 i SharePoint Server 2013. Program SharePoint Server 2010 jest również obsługiwana dla klientów, którzy mają [rozszerzoną obsługę w tej wersji programu SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) i korzystający z wersji zapoznawczej skanera.|
|Tryb działania: <br /><br />-Czasu rzeczywistego|Tryb działania: <br /><br />-Systematycznie przeszukuje magazynów danych i tego cyklu można uruchomić pojedynczego lub wielokrotnego|
|Obsługa typów plików: <br /><br />— Wszystkie typy plików są chronione domyślnie <br /><br />-Określonych typów plików, można wykluczyć z ochrony, edytując rejestr|Obsługa typów plików: <br /><br />— Typy plików pakietu office są chronione domyślnie <br /><br />-Określonych typów plików, można dołączyć do ochrony przez edycję rejestru|

Obecnie ma różnicy w ustawieniu [właściciela usługi Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) dla plików, które są chronione na lokalny folder lub udział sieciowy. Domyślnie w przypadku obu rozwiązań właściciela usługi Rights Management jest ustawiony na konto które chroni plik, ale można zastąpić to ustawienie:

- Dla infrastruktury klasyfikacji plików systemu Windows Server: Ustawianie właściciela usługi Rights Management do jednego konta dla wszystkich plików lub dynamicznie określać właściciela usługi Rights Management dla każdego pliku. Aby dynamicznie ustawić właściciela usługi Rights Management, należy użyć **- OwnerMail [E-mail właściciela pliku źródłowego]** parametru i wartości. Ta konfiguracja pobiera adres e-mail użytkownika z usługi Active Directory przy użyciu nazwy konta użytkownika w pliku właściwości właściciela.

- Skanera usługi Azure Information Protection: można ustawić właściciela usługi Rights Management do jednego konta dla wszystkich plików na określony magazyn danych, ale nie można dynamicznie ustawić właściciela usługi Rights Management dla każdego pliku. Aby ustawić konto, należy określić **- DefaultOwner** parametr [profilu repozytorium danych](/powershell/module/azureinformationprotection/Set-AIPScannerRepository?view=azureipps#optional-parameters).

Gdy skaner chroni pliki witryn programu SharePoint i bibliotek, właściciel usługi Rights Management jest dynamicznie ustawić dla każdego pliku przy użyciu wartość autora programu SharePoint.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Podobno nowa wersja ma być wkrótce dostępna dla usługi Azure Information Protection — kiedy zostanie ona wydana?

Dokumentacja techniczna nie zawiera informacji o kolejnych wersjach. Dla tego typu informacji i zapowiedzi wersji, sprawdź [Enterprise Mobility and Security Blog](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services) i Pobierz najnowsze aktualizacje [Microsoft Mobility@MSFTMobility ](https://twitter.com/MSFTMobility) w serwisie Twitter. Jeśli interesuje Cię wersja pakietu Office, sprawdź również [blog dotyczący pakietu Office](https://blogs.office.com/).

## <a name="is-azure-information-protection-suitable-for-my-country"></a>Usługi Azure Information Protection jest odpowiednia dla moim kraju?

Różnych krajów mają różne wymagania i przepisów. Aby pomóc w odpowiedzi na to pytanie w Twojej organizacji, zobacz [przydatności do różnych krajów](./compliance.md#suitability-for-different-countries).

## <a name="how-can-azure-information-protection-help-with-gdpr"></a>Jak usługi Azure Information Protection może pomóc z rozporządzeniem RODO

Aby zobaczyć, jak usługi Azure Information Protection mogą ułatwić osiągnięcie ogólne rozporządzenie o ochronie danych (RODO), zobacz następujący wpis na blogu, z wideo: [365 firmy Microsoft zapewnia pomoc z rozporządzeniem GDPRstrategiiochronyinformacji](https://blogs.office.com/2018/02/22/microsoft-365-provides-an-information-protection-strategy-to-help-with-the-gdpr).

## <a name="where-can-i-find-supporting-information-for-azure-information-protectionsuch-as-legal-compliance-and-slas"></a>Gdzie można znaleźć dodatkowe informacje na temat usługi Azure Information Protection dotyczące na przykład kwestii prawnych oraz związanych ze zgodnością i umowami SLA?
Zobacz [Zgodność i informacje dodatkowe dotyczące usługi Azure Information Protection](./compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Jak zgłosić problem lub wysłać opinię dotyczącą usługi Azure Information Protection?

Aby skorzystać z pomocy technicznej, użyj standardowych kanałów pomocy lub [skontaktuj się z pomocą techniczną firmy Microsoft](information-support.md#to-contact-microsoft-support).

Aby przekazać opinie, w tym sugestie dotyczące ulepszeń i nowych funkcji, w aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** kliknij przycisk **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **Prześlij opinię**. Ta opcja umożliwia otwarcie wiadomości e-mail do wysłania do zespołu usługi Information Protection.

Zachęcamy także do kontaktowania się z naszymi inżynierami za pośrednictwem [strony usługi Azure Information Protection w witrynie Yammer](https://www.yammer.com/askipteam/). 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>Co należy zrobić, jeśli mojego pytania nie ma na tej liście?

Po pierwsze Przejrzyj poniższe często zadawane pytania dotyczące klasyfikacji i etykietowania lub ochrony danych. Usługa Azure Rights Management (Azure RMS) udostępnia technologię ochrony danych usługi Azure Information Protection. Usługa Azure RMS może służyć z klasyfikacji i etykietowania lub samodzielnie. 

- [Często zadawane pytania dotyczące klasyfikacji i etykietowania](faqs-infoprotect.md)

- [Często zadawane pytania dotyczące ochrony danych](faqs-rms.md)

W przypadku nieznalezienia odpowiedzi na pytanie skorzystaj z linków i zasobów wymienionych w artykule [Informacje i pomoc techniczna dla usługi Azure Information Protection](information-support.md).

Ponadto są przeznaczone dla użytkowników końcowych często zadawane pytania:

- [Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android](./rms-client/mobile-app-faq.md)

- [Często zadawane pytania dotyczące aplikacji RMS sharing dla komputerów Mac i telefonów Windows Phone](https://technet.microsoft.com/dn451248)

- [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Rights Management dla systemu Windows](https://technet.microsoft.com/dn467883)


