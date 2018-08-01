---
title: Często zadawane pytania dotyczące usługi Azure RMS — AIP
description: Niektóre często zadawane pytania dotyczące usługi ochrony danych Azure Rights Management (Azure RMS) z usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.custom: askipteam
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 47aa87d9e7392eafeffa8d8c94c20b4fab295927
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39374178"
---
# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Często zadawane pytania dotyczące ochrony danych w usłudze Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Masz pytanie dotyczące usługi ochrony danych Azure Rights Management z usługi Azure Information Protection? Zobacz, czy nie znajdziesz tutaj odpowiedzi.

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>Czy pliki muszą znajdować się w chmurze, aby mogły być chronione przez usługę Azure Rights Management?
Nie, to powszechne nieporozumienie. Usługa Azure Rights Management (ani firma Microsoft) nie widzi ani nie przechowuje danych użytkownika w ramach procesu ochrony informacji. Chronione informacje nie są wysyłane na platformę Azure ani na niej przechowywane, chyba że użytkownik jawnie zapisze je na platformie Azure lub w innej usłudze chmurowej, która magazynuje dane na tej platformie.

Aby uzyskać więcej informacji, zobacz temat [How does Azure RMS work? Under the hood](../understand-explore/how-does-it-work.md) (Jak działa usługa RMS? Kulisy), aby dowiedzieć się, jak tajna receptura coli, utworzona i przechowywana lokalnie, jest chroniona przez usługę Azure Rights Management, ale pozostaje zapisana lokalnie.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Jaka jest różnica między szyfrowaniem w usłudze Azure Rights Management i szyfrowaniem w innych usługach firmy Microsoft w chmurze?

Firma Microsoft udostępnia wiele technologii szyfrowania, które umożliwiają ochronę danych dla różnych i często uzupełniających się scenariuszy. Na przykład, gdy usługa Office 365 oferuje szyfrowania podczas spoczynku dla danych przechowywanych w usłudze Office 365, usługa Azure Rights Management z usługi Azure Information Protection niezależnie szyfruje Twoje dane tak, aby były chronione bez względu na to, gdzie się znajdują lub jak są przesyłane.

Te technologie szyfrowania uzupełniają się, a ich użycie wymaga niezależnego ich włączenia i skonfigurowania. Gdy to zrobisz, możesz mieć możliwość użycia własnego klucza szyfrowania w scenariuszu znanym także jako „BYOK”. Włączenie funkcji BYOK dla jednej z tych technologii nie wpływa na inne. Na przykład możesz użyć funkcji BYOK dla usługi Azure Information Protection i nie używać jej dla innych technologii szyfrowania i na odwrót. Klucze używane przez te różne technologie mogą być takie same lub różne w zależności od sposobu, w jaki skonfigurujesz opcje szyfrowania dla każdej usługi.

## <a name="whats-the-difference-between-byok-and-hyok-and-when-should-i-use-them"></a>Jaka jest różnica między funkcjami BYOK i HYOK i kiedy należy ich używać?

Funkcja **Bring your own key** (BYOK) w kontekście usługi Azure Information Protection jest używana w przypadku tworzenia własnego lokalnego klucza w celu zastosowania ochrony przy użyciu usługi Azure Rights Management. Ten klucz jest następnie przenoszony do sprzętowego modułu zabezpieczeń (HSM) w magazynie kluczy Azure, w którym nadal jesteś jego właścicielem i możesz nim zarządzać. Jeśli tego nie zrobisz, ochrona Azure Rights Management będzie używać klucza, który jest automatycznie tworzony i zarządzany w systemie Azure. Konfiguracja domyślna jest określana jako „zarządzana przez Microsoft” w odróżnieniu od „zarządzanej przez klienta” (opcja BYOK).

Aby uzyskać więcej informacji o funkcji BYOK i wyborze tej topologii klucza dla Twojej organizacji, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md).

Funkcja **Hold your own key** (HYOK) w kontekście usługi Azure Information Protection jest przeznaczona dla niewielkiej liczby organizacji, w przypadku których pewne dokumenty lub wiadomości e-mail nie mogą być chronione za pomocą klucza przechowywanego w chmurze. W przypadku takich organizacji to ograniczenie obowiązuje nawet wówczas, jeśli utworzono klucz i zarządza się nim przy użyciu funkcji BYOK. To ograniczenie może obowiązywać z powodów prawnych lub wymogów zgodności z przepisami, zaś funkcja HYOK powinna być stosowana tylko do informacji klasyfikowanych jako „ściśle tajne”, które nigdy nie będą udostępniane poza organizację i będą wykorzystywane tylko w sieci wewnętrznej, a dostęp do nich nie będzie uzyskiwany z urządzeń przenośnych.

Dla tych wyjątków (stanowiących zwykle nie więcej niż 10% całej chronionej zawartości) organizacja może wykorzystać rozwiązanie lokalne Active Directory Rights Management Services w celu utworzenia klucza, który pozostanie w środowisku lokalnym. Dzięki temu rozwiązaniu komputery pobierają zasady usługi Azure Information Protection z chmury, ale określona zawartość będzie chroniona przy użyciu lokalnego klucza.

Aby uzyskać więcej informacji o funkcji HYOK i upewnić się, że dobrze zrozumiano jej ograniczenia oraz wskazówki dotyczące jej stosowania, patrz [Wymagania i ograniczenia dotyczące rozwiązania „hold your own key” (HYOK) dla ochrony za pomocą usług AD RMS](../deploy-use/configure-adrms-restrictions.md).

## <a name="can-i-now-use-byok-with-exchange-online"></a>Czy można teraz używać funkcji BYOK z usługą Exchange Online?

Tak, teraz umożliwia BYOK z usługą Exchange Online w przypadku postępuj zgodnie z instrukcjami wyświetlanymi w [skonfigurować nowe możliwości szyfrowanie wiadomości usługi Office 365 korzystających z usługi Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Instrukcje te umożliwiają nowe możliwości w usłudze Exchange Online, które obsługują przy użyciu funkcji BYOK dla usługi Azure Information Protection, a także nowe szyfrowanie wiadomości usługi Office 365.

Aby uzyskać więcej informacji na temat tej zmiany, zobacz w blogu: [szyfrowanie wiadomości usługi Office 365 dzięki nowym funkcjom](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)

## <a name="where-can-i-find-information-about-third-party-solutions-that-integrate-with-azure-rms"></a>Gdzie można znaleźć informacje o rozwiązaniach innych firm, które integrują się z usługą Azure RMS?

Wielu dostawców oprogramowania już ma lub wdraża rozwiązania zintegrowane z usługą Azure Rights Management. Liczba takich rozwiązań rośnie szybko. Użytkownik może być bardzo przydatne do sprawdzenia [rozwiązania śledzić RMS](requirements-applications.md#rms-enlightened-solutions) listy i Pobierz najnowsze aktualizacje z [Microsoft Mobility@MSFTMobility ](https://twitter.com/MSFTMobility) w serwisie Twitter. Sprawdź również [przewodnik dewelopera](../develop/developers-guide.md) i Publikuj pytania integracji określonego w usługi Azure Information Protection [witryny usługi Yammer](https://www.yammer.com/AskIPTeam).

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>Czy istnieje pakiet zarządzania lub podobny mechanizm monitorowania dla łącznika usługi RMS?

Mimo że łącznik usługi Rights Management rejestruje informacje, ostrzeżenia i komunikaty o błędach w dzienniku zdarzeń, nie istnieje pakiet administracyjny, który obejmuje monitorowanie tych zdarzeń. Jednak lista zdarzeń i ich opisów wraz dodatkowymi informacjami ułatwiającymi podejmowanie działań naprawczych jest opisana w sekcji [Monitorowanie łącznika usługi Azure Rights Management](../deploy-use/monitor-rms-connector.md).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators"></a>Czy trzeba być administratorem globalnym, aby skonfigurować usługę Azure RMS, czy można to oddelegować do innych administratorów?

Z rolą Administrator usługi Information Protection nowo wprowadzonych tego zapytania (i odpowiedzi) teraz został przeniesiony na stronę główną — często zadawane pytania: [muszą być administratorem globalnym, aby skonfigurować usługę Azure Information Protection, czy można to oddelegować do innych administratorów?](faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators)

## <a name="how-do-i-create-a-new-custom-template-in-the-azure-portal"></a>Jak utworzyć nowy szablon niestandardowy w portalu Azure?

Szablony niestandardowe zostały przeniesione do witryny Azure portal, w którym możesz zarządzać nimi jak szablonami lub też przekonwertować je na etykiety. Aby utworzyć nowy szablon, utwórz nową etykietę, a następnie skonfiguruj ustawienia ochrony danych dla usługi Azure RMS. Spowoduje to utworzenie w sposób niewidoczny dla użytkownika nowego szablonu dostępnego dla usług oraz aplikacji integrujących się z szablonami usługi Rights Management.

Aby uzyskać więcej informacji na temat szablonów w witrynie Azure portal, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](../deploy-use/configure-policy-templates.md).

## <a name="ive-protected-a-document-and-now-want-to-change-the-usage-rights-or-add-usersdo-i-need-to-reprotect-the-document"></a>Czy dokument został objęty ochroną, a teraz chcą zmienić praw użytkowania lub dodać użytkowników, należy ponownie włączyć ochronę dokumentu?

Jeśli dokument był chroniony za pomocą etykiety lub szablonu, nie ma potrzeby do ponownego włączenia ochrony dokumentu. Zmodyfikuj etykiety lub szablonu, wprowadzanie zmian do praw użytkowania lub dodać nowe grupy (lub użytkowników), a następnie zapisz i opublikuj te zmiany:

- Gdy użytkownik nie dostęp do dokumentu, przed dokonaniem zmiany, zmiany zaczęły obowiązywać, zaraz po otwarciu dokumentu.

- Po użytkownik ma już dostęp do dokumentu, zmiany zostaną wprowadzone po ich [licencję użytkowania](../deploy-use/configure-usage-rights.md#rights-management-use-license) wygasa. Ponowne włączanie ochrony z dokumentu, tylko wtedy, gdy nie można czekać licencji użytkowania, wygaśnie. Ponowne włączanie ochrony skutecznie tworzy nową wersję dokumentu, a w związku z tym nową licencję użytkowania dla użytkownika.

Alternatywnie Jeśli już skonfigurowano grupę dla wymaganych uprawnień, można zmienić członkostwa w grupie do dołączania lub wykluczania użytkowników i nie ma potrzeby zmiany etykiety lub szablonu. Może odbywać z niewielkim opóźnieniem, aby zmiany zaczęły obowiązywać, ponieważ członkostwo w grupie jest [pamięci podręcznej](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection) przez usługę Azure Rights Management.

Jeśli dokument był chroniony za pomocą uprawnień niestandardowych, nie można zmienić uprawnienia dla istniejącego dokumentu. Należy ponownie chronić dokument i określić wszystkich użytkowników i wszystkie prawa użytkowania, które są wymagane do tej nowej wersji dokumentu. Aby ponownie włączyć ochronę dokumentu chronionego, musi mieć prawo użycia Pełna kontrola.

Porada: Aby sprawdzić, czy dokument był chroniony przez szablon lub przy użyciu uprawnień niestandardowych, należy użyć [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) polecenia cmdlet programu PowerShell. Zawsze wyświetlić opis szablonu **ograniczony dostęp** o uprawnienia niestandardowe, identyfikatorem unikatowy szablonu, które nie są wyświetlane po uruchomieniu [Get-RMSTemplate](/powershell/module/azureinformationprotection/get-rmstemplate).

## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Mam hybrydowe wdrożenie programu Exchange — niektórzy użytkownicy korzystają z usługi Exchange Online, inni z programu Exchange Server. Czy usługa Azure RMS obsługuje taką sytuację?
Oczywiście a dodatkową korzyścią jest, użytkownicy będą mogli bezproblemowo ochrony i korzystania z chronionych wiadomości e-mail i załączników w obu wdrożeniach programu Exchange. W przypadku takiej konfiguracji należy najpierw [aktywować usługę Azure RMS](../deploy-use/activate-service.md) i [włączyć usługę IRM dla usługi Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), a następnie [wdrożyć i skonfigurować łącznik usługi RMS](../deploy-use/deploy-rms-connector.md) dla programu Exchange Server.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azure-rms"></a>Czy korzystanie z tej ochrony w środowisku produkcyjnym wymusza na firmie korzystanie z tego rozwiązania lub powoduje ryzyko utraty dostępu do zawartości chronionej za pomocą usługi Azure RMS?
Nie, zawsze zachowujesz kontrolę nad swoimi danymi i możesz nadal uzyskiwać do nich dostęp, nawet jeśli zrezygnujesz z używania usługi Azure Rights Management. Aby uzyskać więcej informacji, zobacz artykuł [Likwidowanie i dezaktywowanie usługi Azure Rights Management](../deploy-use/decommission-deactivate.md).

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Czy można kontrolować, którzy użytkownicy w przedsiębiorstwie mogą korzystać z usługi Azure RMS do ochrony zawartości?
Tak, usługa Azure Rights Management zawiera mechanizmy dodawania użytkowników wymagane w tym scenariuszu. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [konfigurowania funkcji kontroli dołączania użytkowników we wdrożeniu etapowym](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) w artykule [Activating Azure Rights Management](../deploy-use/activate-service.md) (Aktywowanie usługi Azure Rights Management).

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>Czy można uniemożliwić udostępnianie przez użytkowników dokumentów chronionych określonym organizacjom?
Jedną z największych zalet używania usługi Azure Rights Management do ochrony danych jest obsługiwanie współpracy między firmami bez konieczności jawnego konfigurowania zaufania dla każdej organizacji partnerskiej, ponieważ usługa Azure AD sama obsługuje uwierzytelnianie.

Nie ma administracyjnej możliwości uniemożliwiania bezpiecznego udostępniania dokumentów przez użytkowników określonym organizacjom. Na przykład chcesz zablokować organizację, której nie ufasz lub która prowadzi konkurencyjną działalność. Uniemożliwienie usłudze Azure Rights Management wysyłania chronionych dokumentów do użytkowników w takich organizacjach nie miałoby sensu, ponieważ użytkownicy mogliby wówczas udostępniać dokumenty bez ochrony, co byłoby zdecydowanie niepożądane. W takiej sytuacji wskazanie osoby udostępniającej poufne dokumenty firmy i ich odbiorców w takich organizacjach byłoby niemożliwe. Można to zrobić, jeśli dokument (lub wiadomość e-mail) podlega ochronie za pomocą usługi Azure Rights Management.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>W jaki sposób może zostać uwierzytelniony użytkownik spoza mojej firmy, któremu udostępniam chroniony dokument?

Domyślnie do uwierzytelniania użytkowników, co sprawia, że współpracy między firmami bezproblemowe dla administratorów usługi Azure Rights Management używa konta usługi Azure Active Directory i powiązanego adresu e-mail. Jeśli inna organizacja używa usług Azure, użytkownicy mają już konta w usłudze Azure Active Directory, nawet jeśli te konta są tworzone i zarządzane lokalnie, a następnie synchronizowane z platformą Azure. Jeśli organizacja korzysta z usługi Office 365, to ta usługa również używa usługi Azure Active Directory do obsługi kont użytkowników. Jeśli organizacja użytkownika nie posiada kont zarządzanych na platformie Azure, użytkownicy mogą rejestrować się w celu uzyskania [usług RMS dla osób indywidualnych](../understand-explore/rms-for-individuals.md), co powoduje utworzenie niezarządzanej dzierżawy platformy Azure i katalogu dla organizacji z kontem użytkownika, tak aby ten użytkownik (i kolejni) mógł zostać uwierzytelniony do korzystania z usługi Azure Rights Management.

Metody uwierzytelniania w przypadku tych kont mogą się różnić w zależności od tego, jak administrator drugiej organizacji skonfigurował konta w usłudze Azure Active Directory. Można na przykład korzystać z haseł utworzonych dla tych kont, uwierzytelniania wieloskładnikowego (MFA), federacji lub haseł utworzonych w usługach domenowych Active Directory i następnie zsynchronizowanych z usługą Azure Active Directory.

Inne metody uwierzytelniania:

- Jeśli możesz chronić wiadomość e-mail z załącznikiem dokumentu pakietu Office dla użytkownika, które nie mają konta w usłudze Azure AD, zmienia metodę uwierzytelniania. Usługa Azure Rights Management jest sfederowana z niektórymi dostawcami tożsamości społecznościowej popularne, np. Gmail. Jeśli dostawcy poczty e-mail użytkownika jest obsługiwany, użytkownik może zalogować się do tej usługi, a ich dostawcy poczty e-mail jest odpowiedzialna za ich uwierzytelnianie. Jeśli dostawcy poczty e-mail użytkownika nie jest obsługiwana, lub preferencji, poprosić użytkownika o jednorazowy kod dostępu, który ich uwierzytelnia, a następnie wyświetli wiadomość e-mail z chronionego dokumentu w przeglądarce sieci web.

- Usługa Azure Information Protection można używać kont Microsoft dla obsługiwanych aplikacji. Obecnie nie wszystkie aplikacje można otworzyć chronionej zawartości, gdy konto Microsoft służy do uwierzytelniania. [Więcej informacji](../get-started/secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>Czy mogę dodać użytkowników zewnętrznych (osoby spoza firmy) do szablonów niestandardowych?

Tak. [Ustawienia ochrony](../deploy-use/configure-policy-protection.md) można skonfigurować w witrynie Azure portal umożliwiają dodawanie uprawnień dla użytkowników i grupy spoza organizacji, a nawet wszystkich użytkowników w innej organizacji. Użytkownik może być bardzo przydatne do odwołania przykład krok po kroku [zabezpieczanie współpracy nad dokumentami przy użyciu usługi Azure Information Protection](secure-collaboration-documents.md). 

Należy pamiętać, że jeśli etykiety usługi Azure Information Protection, należy najpierw przekonwertować szablon niestandardowy, etykietę przed rozpoczęciem konfigurowania ustawień ochrony w witrynie Azure portal. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](../deploy-use/configure-policy-templates.md).

Alternatywnie można dodać użytkowników zewnętrznych do szablonów niestandardowych (i etykiet) przy użyciu programu PowerShell. Ta konfiguracja wymaga użyć obiektu definicji praw, którego używasz do celów aktualizacji szablonu:

1. Określ zewnętrzne adresy e-mail i ich prawa w obiekcie definicji praw, za pomocą [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) polecenia cmdlet, aby utworzyć zmienną.

2. Dostarczyć tę zmienną do parametru RightsDefinition za pomocą [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) polecenia cmdlet.

    Po dodaniu użytkowników do istniejącego szablonu, należy zdefiniować obiekty definicji praw dla istniejących użytkowników w szablonach, oprócz nowych użytkowników. W tym scenariuszu może się okazać przydatne **przykład 3: dodawanie nowych użytkowników i praw do szablonu niestandardowego** z [przykłady](/powershell/module/aadrm/set-aadrmtemplateproperty#examples) sekcję polecenia cmdlet.

## <a name="what-type-of-groups-can-i-use-with-azure-rms"></a>Jakiego rodzaju grup można używać z usługą Azure RMS?
W przypadku większości scenariuszy można używać dowolnego typu grupy w usłudze Azure AD, która ma adres e-mail. Ta zasada mówi ma zastosowanie zawsze, gdy przypisujesz prawa użytkowania, ale istnieją pewne wyjątki do administrowania usługą Azure Rights Management. Aby uzyskać więcej informacji, zobacz [wymagania usługi Azure Information Protection dla kont grup](../plan-design/prepare.md#azure-information-protection-requirements-for-group-accounts).

## <a name="how-do-i-send-a-protected-email-to-a-gmail-or-hotmail-account"></a>Jak wysłać chronioną wiadomość e-mail na konto Gmail lub Hotmail?

Gdy używasz usługi Exchange Online i usługą Azure Rights Management, możesz po prostu wysłać wiadomość e-mail użytkownika jako chronionej wiadomości. Na przykład, można wybrać nową **Chroń** przycisk na pasku poleceń w programie Outlook w sieci Web, użyj programu Outlook **nie przesyłaj dalej** przycisku lub menu opcji. Alternatywnie można wybrać etykiety usługi Azure Information Protection, który automatycznie stosuje nie przesyłaj dalej dla Ciebie i klasyfikuje wiadomości e-mail.

Odbiorca widzi opcję, aby zalogować się do swojego konta usługi Gmail, Yahoo lub Microsoft, a następnie może odczytywać chronione wiadomości e-mail. Alternatywnie one wybierz opcję jednorazowy kod dostępu na odczytywanie wiadomości e-mail w przeglądarce.

Do obsługi tego scenariusza Usługa Exchange Online musi być włączona dla usługi Azure Rights Management i nowe możliwości w szyfrowanie wiadomości usługi Office 365. Aby uzyskać więcej informacji na temat tej konfiguracji, zobacz [usługi Exchange Online: Konfiguracja usługi IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

Aby uzyskać więcej informacji na temat nowych funkcji, które obejmują obsługi wszystkich kont e-mail na wszystkich urządzeniach, zobacz następujący wpis w blogu: [ogłoszenie nowych funkcji dostępnych w szyfrowanie wiadomości usługi Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Jakie urządzenia i typy plików są obsługiwane przez usługę Azure RMS?
Aby uzyskać listę urządzeń obsługujących usługę Azure Rights Management, zobacz [Urządzenia klienckie obsługujące ochronę danych usługi Azure Rights Management](../get-started/requirements-client-devices.md). Ponieważ nie wszystkie obsługiwane urządzenia obsługują obecnie wszystkie funkcje usługi Rights Management, należy również zapoznać się z tabelą zawierającą informacje na temat [aplikacji z obsługą usług RMS](../get-started/requirements-applications.md#rms-enlightened-applications).

Usługa Azure Rights Management obsługuje wszystkie typy plików. W przypadku plików tekstowych, obrazów, plików pakietu Microsoft Office (Word, Excel, PowerPoint), plików pdf oraz niektórych typów plików innych aplikacji usługa Azure Rights Management zapewnia natywną ochronę obejmującą zarówno szyfrowanie, jak i wymuszanie praw (uprawnień). W przypadku pozostałych aplikacji i typów plików ochrona ogólna zapewnia hermetyzację plików oraz uwierzytelnianie umożliwiające weryfikację, czy użytkownik jest uprawniony do otwarcia pliku.

Aby uzyskać listę rozszerzeń nazw plików, które są natywnie obsługiwane przez usługę Azure Rights Management, zobacz temat [Typy plików obsługiwane przez klienta usługi Azure Information Protection](../rms-client/client-admin-guide-file-types.md). Rozszerzenia nazw plików, które nie są wymienione na liście, są obsługiwane przy użyciu klienta usługi Azure Information Protection, który automatycznie stosuje do tych plików ochronę ogólną.

## <a name="how-do-i-configure-a-mac-computer-to-protect-and-track-documents"></a>Jak skonfigurować komputer Mac, aby chronić i śledzić dokumenty?

Najpierw upewnij się, że zainstalowano pakiet Office dla komputerów Mac przy użyciu linku instalacji oprogramowania z https://portal.office.com. Aby uzyskać pełne instrukcje, zobacz temat [Pobieranie i instalacja lub ponowna instalacja usługi Office 365 lub pakietu Office 2016 na komputerach PC lub Mac](https://support.office.com/en-us/article/Download-and-install-or-reinstall-Office-365-or-Office-2016-on-a-PC-or-Mac-4414EAAF-0478-48BE-9C42-23ADC4716658).

Otwórz program Outlook i utwórz profil przy użyciu konta służbowego usługi Office 365. Następnie utwórz nową wiadomość i wykonaj następujące czynności w celu skonfigurowania pakietu Office, tak aby chronić dokumenty i wiadomości e-mail przy użyciu usługi Azure Rights Management:

1. W nowej wiadomości na karcie **Opcje** kliknij pozycję **Uprawnienia**, a następnie kliknij przycisk **Sprawdź poświadczenia**.

2. Po wyświetleniu monitu podaj szczegóły konta służbowego usługi Office 365, a następnie wybierz przycisk **Zaloguj**.

    Spowoduje to pobranie szablonów usługi Azure Rights Management, a opcja **Sprawdź poświadczenia** zostanie zastąpiona przez kilka opcji, m.in **Brak ograniczeń**, **Nie przesyłaj dalej** oraz wszystkie szablony usługi Azure Rights Management opublikowane dla Twojej dzierżawy. Możesz teraz anulować tę nową wiadomość.

Aby chronić wiadomość e-mail lub dokument: na karcie **Opcje** kliknij pozycję **Uprawnienia** i wybierz opcję lub szablon chroniący wiadomość e-mail lub dokument.

Śledzenie dokumentu po zapewnieniu ochrony: na komputerze z systemem Windows, na którym zainstalowano klienta usługi Azure Information Protection, zarejestruj dokument w witrynie śledzenia dokumentów za pomocą aplikacji pakietu Office lub Eksploratora plików. Aby uzyskać instrukcje, zobacz temat [Śledzenie i odwoływanie dokumentów](../rms-client/client-track-revoke.md). Na komputerze Mac, można teraz użyć przeglądarki sieci web można przejść do witryny śledzenia dokumentów (https://track.azurerms.com) do śledzenia i odwoływania dokumentu.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>Czy po otwarciu dokumentu pakietu Office chronionego przez usługę RMS skojarzony plik tymczasowy jest również chroniony przez usługę RMS?
Nie. W tym scenariuszu skojarzony plik tymczasowy nie zawiera danych z oryginalnego dokumentu, tylko dane wprowadzone przez użytkownika w czasie, w którym ten oryginalny plik był otwarty. W przeciwieństwie do oryginalnego pliku plik tymczasowy oczywiście nie jest przeznaczony do udostępniania i pozostanie na urządzeniu, chroniony przez lokalne zabezpieczenia, takie jak funkcja BitLocker i system szyfrowania plików.

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>Wygląda na to, że funkcja, której potrzebuję, nie współpracuje z chronionymi bibliotekami programu SharePoint. Czy obsługa tej funkcji jest planowana?
Obecnie program SharePoint obsługuje chronione przez usługę RMS dokumentów za pomocą usługi IRM chronionych bibliotek, które nie obsługują szablonów usługi Rights Management, śledzenia dokumentów i niektórych innych funkcji. Więcej informacji można znaleźć w sekcji dotyczącej [usługi SharePoint Online i programu SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) w artykule [Office applications and services](../understand-explore/office-apps-services-support.md) (Aplikacje i usługi pakietu Office).

Użytkownicy zainteresowani konkretną funkcją, która nie jest jeszcze obsługiwana, powinni śledzić ogłoszenia na [blogu dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-rights-management-services).

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>Jak skonfigurować usługę OneDrive dla Firm w usłudze SharePoint Online, tak aby użytkownicy mogli bezpiecznie udostępniać pliki wewnątrz i na zewnątrz firmy?
Domyślnie tej usługi nie konfiguruje administrator usługi Office 365, lecz robią to użytkownicy.

Podobnie jak administrator witryny programu SharePoint włącza i konfiguruje usługę IRM dla biblioteki programu SharePoint, której jest właścicielem, usługa OneDrive dla Firm jest zaprojektowana tak, aby użytkownicy włączali i konfigurowali usługę IRM dla własnej biblioteki usługi OneDrive dla Firm. Można jednak zrobić to dla nich, korzystając ze środowiska PowerShell. Instrukcje można znaleźć w sekcji [SharePoint Online and OneDrive for Business: IRM Configuration](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) (Usługi SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM) artykułu [Office 365: Configuration for clients and online services](../deploy-use/configure-office365.md) (Usługa Office 365: konfiguracja dla klientów i usług online).

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>Czy istnieją jakieś wskazówki ułatwiające pomyślne wdrożenie?

Po nadzorowaniu wielu wdrożeń i wysłuchaniu opinii naszych klientów, partnerów, konsultantów i inżynierów pomocy technicznej możemy udzielić jednej podstawowej wskazówki opartej na naszym doświadczeniu: **projektuj i wdrażaj proste zasady**.

Ponieważ usługa Azure Information Protection umożliwia bezpieczne udostępnianie dowolnym osobom, można pozwolić sobie na ambitne podejście do zasięgu ochrony danych. Ale konserwatywne podczas konfigurowania praw ograniczenia użycia. W przypadku wielu organizacji największy wpływ na działalność pochodzi z zapobieganie wyciekowi danych przez ograniczenie dostępu do osób w danej organizacji. Oczywiście w razie potrzeby można wprowadzić bardziej szczegółowe ograniczenia — uniemożliwiać drukowanie, edycję itd. Ale zachowaj szczegółowe ograniczenia w przypadku dokumentów wymagających naprawdę specjalnej ochrony, a nie implementują te bardziej restrykcyjne prawa użytkowania na jeden dzień, ale zaplanować podejście etapowe.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>Jak odzyskać dostęp do plików, które były chronione przez pracownika, który opuścił organizację?
Użyj [funkcji superużytkowników](../deploy-use/configure-super-users.md), która przyznaje użycia Pełna kontrola prawami dostępu do grona upoważnionych użytkowników dla wszystkich dokumentów i wiadomości e-mail są chronione przy użyciu swojej dzierżawy. Administratorów można zawsze przeczytaj tę chronioną zawartość, a jeśli to konieczne, usunąć lub ponownie włączyć ochronę dla różnych użytkowników. Ta sama funkcja w razie potrzeby umożliwia autoryzowanym usługom indeksowanie i przeprowadzanie inspekcji plików.

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>Podczas testowania odwołania w witrynie śledzenia dokumentów wyświetlany jest komunikat informujący, że użytkownicy mogą nadal uzyskiwać dostęp do dokumentu przez okres do 30 dni — czy ten okres można skonfigurować?

Tak. Ten komunikat odzwierciedla [licencję użytkowania](../deploy-use/configure-usage-rights.md#rights-management-use-license) dla tego określonego pliku.

W przypadku odwołania pliku ta akcja może zostać wymuszona tylko wtedy, gdy użytkownik jest uwierzytelniany w usłudze Azure Rights Management. Na przykład jeśli plik ma 30-dniowy okres ważności licencji użytkowania, a użytkownik ma już otwarty dokument, ten użytkownik będzie mieć nadal dostęp do dokumentu w okresie ważności licencji użytkowania. Po wygaśnięciu licencji użytkowania użytkownik musi zostać ponownie uwierzytelniony. Nastąpi wtedy odmowa dostępu, ponieważ dokument będzie już odwołany.

To odwołanie nie dotyczy użytkownika, który włączył ochronę dokumentu, czyli [wystawcy usługi Rights Management](../deploy-use/configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) — ma on zawsze dostęp do swoich dokumentów.

Wartość domyślna dla okresu ważności licencji użytkowania dla dzierżawy wynosi 30 dni i to ustawienie może być zastąpiona przez bardziej restrykcyjnym ustawieniem etykiety lub szablonu. Aby uzyskać więcej informacji o licencji użytkowania i sposobu ich konfigurowania, zobacz [licencję użytkowania usługi Rights Management](../deploy-use/configure-usage-rights.md#rights-management-use-license) dokumentacji.

## <a name="can-rights-management-prevent-screen-captures"></a>Czy usługa Rights Management może uniemożliwiać przechwytywanie ekranu?
Przez nieprzyznanie [prawa użytkowania](../deploy-use/configure-usage-rights.md) **Kopiowanie** usługa Rights Management może zapobiegać przechwytywaniu ekranu za pomocą wielu typowych narzędzi na różnych platformach Windows (Windows 7, Windows 8.1, Windows 10, Windows Phone) i Android. Jednak urządzenia z systemem iOS i komputery Mac nie zezwalają żadnej aplikacji na zapobieganie przechwytywaniu ekranu. Podobna sytuacja ma miejsce w przypadku przeglądarek (na przykład używanych łącznie z aplikacjami Outlook Web App i Office Online), które również nie mogą uniemożliwiać przechwytywania ekranu.

Uniemożliwianie przechwytywania ekranu może pomóc uniknąć przypadkowego lub wynikającego z niedbałości ujawnienia poufnych lub wrażliwych informacji. Użytkownik może jednak udostępniać dane wyświetlane na ekranie różnymi sposobami, a wykonanie zrzutu ekranu jest tylko jedną z nich. Użytkownik chcący udostępnić wyświetlane informacje może na przykład zrobić zdjęcie ekranu aparatem w telefonie, przepisać dane lub po prostu słownie przekazać je innej osobie.

Jak dowodzą te przykłady, nawet jeśli wszystkie platformy i całe oprogramowanie obsługuje interfejsy API usługi Rights Management pod kątem blokowania przechwytywania ekranu, sama technologia nie może zapobiec udostępnieniu przez użytkowników poufnych danych. Usługa Rights Management może pomóc chronić ważne dane za pomocą zasad autoryzacji i użycia, ale to rozwiązanie do zarządzania prawami w przedsiębiorstwie powinno być stosowane razem z innymi środkami kontroli. Przekłady obejmują wdrożenie zabezpieczeń fizycznych, dokładne monitorowanie osób mających uprawnienia dostępu do danych organizacji oraz inwestowanie w edukację użytkowników, tak aby wiedzieli, których danych nie należy udostępniać.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>Jaka jest różnica między ochroną wiadomości e-mail za pomocą ustawienia Nie przesyłaj dalej i szablonem bez prawa do przesyłania dalej?

Niezależnie od nazwy i wyglądu ustawienie **Nie przesyłaj dalej** nie jest przeciwieństwem prawa do przesyłania dalej ani szablonem. Jest to zestaw praw obejmujących ograniczenia przesyłania dalej wiadomości e-mail, kopiowania, drukowania i zapisywania załączników. Prawa są dynamicznie stosowane do użytkowników za pośrednictwem wybranych adresatów, a nie statycznie przypisane przez administratora. Więcej informacji można znaleźć w sekcji [Opcja Nie przekazuj dotycząca wiadomości e-mail](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) w artykule [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](../deploy-use/configure-usage-rights.md).

