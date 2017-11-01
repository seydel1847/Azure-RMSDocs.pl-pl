---
title: "Często zadawane pytania dotyczące usługi Azure RMS — AIP"
description: "Niektóre często zadawane pytania dotyczące usługi ochrony danych Azure Rights Management (Azure RMS) z usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 190ad05c5f505f2c0247c04bf271c8c12cac2ea9
ms.sourcegitcommit: 832d3ef5f9c41d6adb18a8cf5304f6048cc7252e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Często zadawane pytania dotyczące ochrony danych w usłudze Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

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

## <a name="can-i-now-use-byok-with-exchange-online"></a>Można teraz używać funkcji BYOK z usługą Exchange Online?

Tak, możesz teraz użyć BYOK z usługą Exchange Online po zgodnie z instrukcjami w [skonfigurować nowe możliwości szyfrowanie wiadomości usługi Office 365, rozszerzający usługi Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Instrukcje te umożliwiają nowych funkcji w usłudze Exchange Online, które obsługują korzysta ze strategii BYOK dla usługi Azure Information Protection, jak również nowe szyfrowanie wiadomości usługi Office 365.

Aby uzyskać więcej informacji na temat tej zmiany, zobacz anons blogu: [szyfrowanie wiadomości usługi Office 365 z nowych funkcji](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)

## <a name="where-can-i-find-information-about-third-party-solutions-that-integrate-with-azure-rms"></a>Gdzie można znaleźć informacje o rozwiązaniach innych firm, które integrują się z usługą Azure RMS?

Wielu dostawców oprogramowania już ma lub wdraża rozwiązania zintegrowane z usługą Azure Rights Management. Liczba takich rozwiązań rośnie szybko. Może być bardzo przydatne zapoznanie się [rozwiązań RMS englightened](requirements-applications.md#rms-enlightened-solutions) listę i Pobierz najnowsze aktualizacje z [Microsoft Mobility@MSFTMobility ](https://twitter.com/MSFTMobility) w serwisie Twitter. Jeśli jednak masz konkretne pytanie, wyślij wiadomość e-mail do zespołu usługi Information Protection na adres askipteam@microsoft.com.

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>Czy istnieje pakiet zarządzania lub podobny mechanizm monitorowania dla łącznika usługi RMS?

Mimo że łącznik usługi Rights Management rejestruje informacje, ostrzeżenia i komunikaty o błędach w dzienniku zdarzeń, nie istnieje pakiet administracyjny, który obejmuje monitorowanie tych zdarzeń. Jednak lista zdarzeń i ich opisów wraz dodatkowymi informacjami ułatwiającymi podejmowanie działań naprawczych jest opisana w sekcji [Monitorowanie łącznika usługi Azure Rights Management](../deploy-use/monitor-rms-connector.md).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators"></a>Czy trzeba być administratorem globalnym, aby skonfigurować usługę Azure RMS, czy można to oddelegować do innych administratorów?

Administratorzy globalni dla dzierżawy usługi Office 365 lub dzierżawy usługi Azure AD mogą oczywiście uruchamiać wszystkie zadania administracyjne dla usługi Azure Rights Management. Jednak jeśli chcesz przypisać uprawnienia administracyjne do innych użytkowników, możesz to zrobić przy użyciu polecenia cmdlet programu PowerShell usługi Azure RMS [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator). Tę rolę administracyjną można przypisać według konta użytkownika lub grupy. Dostępne są dwie role: **Administrator globalny** i **Administrator łącznika**. 

Tak jak te nazwy sugerują, pierwsza rola przyznaje uprawnienia do uruchamiania wszystkich zadań administracyjnych dla usługi Azure Rights Management (bez nadawania użytkownikom roli administratora globalnego dla innych usług w chmurze), a druga rola przyznaje uprawnienia do uruchamiania tylko łącznika usługi Rights Management (RMS).

Dodatkowe kwestie, na które należy zwrócić uwagę:

- Tylko administratorzy globalni dla usługi Office 365 i Administratorzy globalni dla usługi Azure AD można użyć Centrum administracyjnego usługi Office 365 lub klasycznego portalu Azure do konfigurowania usługi Azure RMS. Jeśli używasz portalu Azure do usługi Azure Information Protection, można również zalogować się jako administrator zabezpieczeń.

- Użytkownicy, którym przypisywana jest rola administratora globalnego usługi Azure RMS, muszą używać poleceń cmdlet programu PowerShell usługi Azure RMS do konfigurowania usługi Azure RMS. W celu łatwiejszego znalezienia odpowiednich poleceń cmdlet służących do wykonywania określonych zadań, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](../deploy-use/administer-powershell.md).

- Jeśli skonfigurowano [kontrolki dołączania](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), nie ma to wpływu na możliwość administrowania usługą Azure RMS, z wyjątkiem łącznika usługi RMS. Na przykład jeśli kontrolki dołączania zostały skonfigurowane w taki sposób, że możliwość ochrony zawartości jest ograniczona do grupy Dział IT, konto używane do instalowania i konfigurowania łącznika usługi RMS musi należeć do tej grupy. 

- Żaden administrator usługi Azure RMS (na przykład administrator globalny dzierżawy lub administratora globalnego usługi Azure RMS) może automatycznie usunąć ochrony dokumentów lub wiadomości e-mail, które były chronione przez usługę Azure RMS. Tylko użytkownicy przypisani do funkcji administratorów usługi Azure RMS mogą to zrobić i może to mieć miejsce tylko po włączeniu funkcji administratorów. Jednak administrator globalny dzierżawy i dowolny administrator globalny usługi Azure RMS może przypisywać użytkowników jako administratorów (dotyczy to również ich własnego konta). Mogą oni również włączyć funkcję administratorów. Te akcje są rejestrowane w dzienniku administratora usługi Azure RMS. Aby uzyskać więcej informacji, zobacz sekcję najlepszych praktyk dotyczących zabezpieczeń w temacie [Konfigurowanie superużytkowników usług Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md). 

>[!NOTE]
> Szablony i nowe opcje dotyczące konfigurowania ochrony usługi Azure Rights Management został przeniesiony do portalu Azure obsługuje Administratorzy zabezpieczeń oprócz dostępu administratora globalnego. 

## <a name="how-do-i-create-a-new-custom-template-in-the-azure-portal"></a>Jak utworzyć nowy szablon niestandardowy w portalu Azure?

Szablony niestandardowe zostały przeniesione do portalu Azure, gdzie można nadal nimi zarządzać jako szablon lub przekonwertować je na etykiety. Aby utworzyć nowy szablon, utwórz nową etykietę, a następnie skonfiguruj ustawienia ochrony danych dla usługi Azure RMS. Spowoduje to utworzenie w sposób niewidoczny dla użytkownika nowego szablonu dostępnego dla usług oraz aplikacji integrujących się z szablonami usługi Rights Management.

Aby uzyskać więcej informacji na temat szablonów w portalu Azure, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](../deploy-use/configure-policy-templates.md).

## <a name="ive-protected-a-document-and-now-want-to-change-the-usage-rights-or-add-usersdo-i-need-to-reprotect-the-document"></a>I był chroniony dokument i chcesz teraz zmienić prawa użytkowania lub dodanie użytkowników, należy włączyć ją ponownie dokument?

Jeśli dokument był chroniony za pomocą etykiety lub szablonu, jest niepotrzebna włączyć ją ponownie dokument. Zmodyfikować etykiety lub szablon wprowadzania zmian do prawa użytkowania lub dodać nowej grupy (lub użytkowników), a następnie zapisz i opublikować te zmiany:

- Gdy użytkownik nie dostęp do dokumentu, przed wprowadzeniem zmian, zmiany zaczynają obowiązywać natychmiast po otwarciu dokumentu. 

- Gdy użytkownik ma już dostęp do dokumentu, zmiany zostaną zastosowane po ich [licencję użytkowania](../deploy-use/configure-usage-rights.md#rights-management-use-license) wygaśnie. Włącz ponownie ochronę dokumentu, tylko wtedy, gdy nie może czekać na licencji użytkowania wygaśnie. Efektywne ponownej ochrony tworzy nową wersję dokumentu, a w związku z tym nowej licencji użytkowania dla użytkownika.

Jeśli skonfigurowano już grupę dla wymaganych uprawnień, można zmienić członkostwo grupy, aby dołączyć lub wykluczyć użytkowników i nie istnieje potrzeba aby zmienić etykietę lub szablonu. Może być małe opóźnienia, aby zmiany zaczęły obowiązywać, ponieważ członkostwo w grupie jest [pamięci podręcznej](../plan-design/prepare.md#group-membership-caching-by-azure-rights-management) przez usługę Azure Rights Management.

Jeśli dokument był chroniony za pomocą uprawnień niestandardowych, nie można zmienić uprawnień dla istniejącego dokumentu. Należy ponownie ochrony dokumentu oraz określić wszyscy użytkownicy i wszystkie prawa użytkowania, które są wymagane do tej nowej wersji dokumentu. Włączyć ją ponownie chroniony dokument, musi mieć prawo użytkowania Pełna kontrola. 

## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Mam hybrydowe wdrożenie programu Exchange — niektórzy użytkownicy korzystają z usługi Exchange Online, inni z programu Exchange Server. Czy usługa Azure RMS obsługuje taką sytuację?
Oczywiście, a dodatkową korzyścią jest to, że użytkownicy będą mogli w łatwy sposób chronić wiadomości e-mail i załączniki, a także korzystać z nich w obu wdrożeniach programu Exchange. W przypadku takiej konfiguracji należy najpierw [aktywować usługę Azure RMS](../deploy-use/activate-service.md) i [włączyć usługę IRM dla usługi Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), a następnie [wdrożyć i skonfigurować łącznik usługi RMS](../deploy-use/deploy-rms-connector.md) dla programu Exchange Server.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azure-rms"></a>Czy korzystanie z tej ochrony w środowisku produkcyjnym wymusza na firmie korzystanie z tego rozwiązania lub powoduje ryzyko utraty dostępu do zawartości chronionej za pomocą usługi Azure RMS?
Nie, zawsze zachowujesz kontrolę nad swoimi danymi i możesz nadal uzyskiwać do nich dostęp, nawet jeśli zrezygnujesz z używania usługi Azure Rights Management. Aby uzyskać więcej informacji, zobacz artykuł [Likwidowanie i dezaktywowanie usługi Azure Rights Management](../deploy-use/decommission-deactivate.md).

Jednak zanim zlikwidujesz usługi Azure Rights Management, chcielibyśmy usłyszeć Twoja i poznać powód podjęcia tej decyzji. Jeśli usługa Azure Rights Management nie spełnia określonych wymagań biznesowych, należy skontaktować się z nami i sprawdzić, czy w najbliższej przyszłości planowane jest wprowadzenie nowych funkcji lub czy są dostępne opcje alternatywne. Wyślij wiadomość e-mail na adres [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS), a chętnie omówimy Twoje wymagania techniczne i biznesowe.

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Czy można kontrolować, którzy użytkownicy w przedsiębiorstwie mogą korzystać z usługi Azure RMS do ochrony zawartości?
Tak, usługa Azure Rights Management zawiera mechanizmy dodawania użytkowników wymagane w tym scenariuszu. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [konfigurowania funkcji kontroli dołączania użytkowników we wdrożeniu etapowym](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) w artykule [Activating Azure Rights Management](../deploy-use/activate-service.md) (Aktywowanie usługi Azure Rights Management).

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>Czy można uniemożliwić udostępnianie przez użytkowników dokumentów chronionych określonym organizacjom?
Jedną z największych zalet używania usługi Azure Rights Management do ochrony danych jest obsługiwanie współpracy między firmami bez konieczności jawnego konfigurowania zaufania dla każdej organizacji partnerskiej, ponieważ usługa Azure AD sama obsługuje uwierzytelnianie.

Nie ma administracyjnej możliwości uniemożliwiania bezpiecznego udostępniania dokumentów przez użytkowników określonym organizacjom. Na przykład chcesz zablokować organizację, której nie ufasz lub która prowadzi konkurencyjną działalność. Uniemożliwienie usłudze Azure Rights Management wysyłania chronionych dokumentów do użytkowników w takich organizacjach nie miałoby sensu, ponieważ użytkownicy mogliby wówczas udostępniać dokumenty bez ochrony, co byłoby zdecydowanie niepożądane. W takiej sytuacji wskazanie osoby udostępniającej poufne dokumenty firmy i ich odbiorców w takich organizacjach byłoby niemożliwe. Można to zrobić, jeśli dokument (lub wiadomość e-mail) podlega ochronie za pomocą usługi Azure Rights Management.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>W jaki sposób może zostać uwierzytelniony użytkownik spoza mojej firmy, któremu udostępniam chroniony dokument?

Domyślnie usługa Azure Rights Management używa konta usługi Azure Active Directory i powiązanego adresu e-mail do uwierzytelniania użytkowników, dzięki czemu współpracy business-to-business bezproblemowe dla administratorów. Jeśli inna organizacja używa usług Azure, użytkownicy mają już konta w usłudze Azure Active Directory, nawet jeśli te konta są tworzone i zarządzane lokalnie, a następnie synchronizowane z platformą Azure. Jeśli organizacja korzysta z usługi Office 365, to ta usługa również używa usługi Azure Active Directory do obsługi kont użytkowników. Jeśli organizacja użytkownika nie posiada kont zarządzanych na platformie Azure, użytkownicy mogą rejestrować się w celu uzyskania [usług RMS dla osób indywidualnych](../understand-explore/rms-for-individuals.md), co powoduje utworzenie niezarządzanej dzierżawy platformy Azure i katalogu dla organizacji z kontem użytkownika, tak aby ten użytkownik (i kolejni) mógł zostać uwierzytelniony do korzystania z usługi Azure Rights Management.

Metody uwierzytelniania w przypadku tych kont mogą się różnić w zależności od tego, jak administrator drugiej organizacji skonfigurował konta w usłudze Azure Active Directory. Można na przykład korzystać z haseł utworzonych dla tych kont, uwierzytelniania wieloskładnikowego (MFA), federacji lub haseł utworzonych w usługach domenowych Active Directory i następnie zsynchronizowanych z usługą Azure Active Directory.

Jeśli musisz chronić wiadomość e-mail z załącznikiem dokumentu pakietu Office użytkownikowi, który nie ma konta w usłudze Azure AD, zmiana metody uwierzytelniania. Usługa Azure Rights Management jest Sfederowane z niektórymi dostawcami popularnych tożsamości społecznościowych, takich jak usługi Gmail. Jeśli dostawca poczty e-mail użytkownika jest obsługiwany, użytkownicy mogą logować się do tej usługi i dostawcy poczty e-mail jest odpowiedzialna za ich uwierzytelnianie. Jeśli nie jest obsługiwana przez dostawcę poczty e-mail użytkownika lub jako preferencji użytkownika poprosić o jednorazowy kod dostępu, który ich uwierzytelnia i wyświetla wiadomość e-mail z chronionego dokumentu w przeglądarce sieci web.

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>Czy mogę dodać użytkowników zewnętrznych (osoby spoza firmy) do szablonów niestandardowych?

Tak. Po przekonwertowaniu szablonu z etykietą w portalu Azure, można skonfigurować [ustawienia ochrony](../deploy-use/configure-policy-protection.md) o dodanie uprawnień dla użytkowników i grup z spoza organizacji, a nawet dla wszystkich użytkowników w innej organizacji. Lub tej konfiguracji można wykonać za pomocą programu PowerShell.

Aby uzyskać więcej informacji na temat konwertowania szablonów niestandardowych etykiet, aby następnie można łatwo dodać użytkowników zewnętrznych, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](../deploy-use/configure-policy-templates.md).

## <a name="what-type-of-groups-can-i-use-with-azure-rms"></a>Typ grupy można używać z usługą Azure RMS?
W przypadku większości scenariuszy można użyć dowolnego typu grupy w usłudze Azure AD, która ma adres e-mail. Ta zasadą zawsze ma zastosowanie, gdy przypisywanie praw użytkowania, ale istnieją pewne wyjątki do administrowania usługą Azure Rights Management. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące usługi Azure Information Protection dla grupy kont](../plan-design/prepare.md#azure-information-protection-requirements-for-group-accounts).

## <a name="how-do-i-send-a-protected-email-to-a-gmail-or-hotmail-account"></a>Jak wysłać chronioną wiadomość e-mail na konto Gmail lub Hotmail?

Korzystając z usługi Exchange Online i usługa Azure Rights Management, po prostu wysłaniem wiadomości e-mail do użytkownika jako chronionej wiadomości. Na przykład można wybrać nowy **Chroń** przycisk paska poleceń w programie Outlook w sieci Web, użyj programu Outlook **nie przesyłaj dalej** przyciskiem lub menu opcji. Alternatywnie możesz wybrać etykietę usługi Azure Information Protection, która automatycznie stosuje nie przesyłaj dalej dla Ciebie i klasyfikuje wiadomości e-mail. 

Odbiorcy zobaczą opcję, aby zalogować się do swojego konta usługi Gmail, Yahoo lub firmy Microsoft, a następnie mieć możliwość odczytu chronionych wiadomości e-mail. Ich można również wybrać opcję dla jednorazowy kod dostępu odczytać wiadomość e-mail w przeglądarce.

Aby obsługiwać ten scenariusz, Exchange Online musi być włączony dla usługi Azure Rights Management i nowe możliwości w szyfrowanie wiadomości usługi Office 365. Aby uzyskać więcej informacji na temat tej konfiguracji, zobacz [usługi Exchange Online: Konfiguracja usługi IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

Aby uzyskać więcej informacji na temat nowych funkcji, które obejmują obsługi wszystkich kont e-mail na wszystkich urządzeniach, zobacz następującym wpisie w blogu: [o nowych funkcji dostępnych w szyfrowanie wiadomości usługi Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Jakie urządzenia i typy plików są obsługiwane przez usługę Azure RMS?
Aby uzyskać listę urządzeń obsługujących usługę Azure Rights Management, zobacz [Urządzenia klienckie obsługujące ochronę danych usługi Azure Rights Management](../get-started/requirements-client-devices.md). Ponieważ nie wszystkie obsługiwane urządzenia obsługują obecnie wszystkie funkcje usługi Rights Management, należy również zapoznać się z tabelą zawierającą informacje na temat [aplikacji z obsługą usług RMS](../get-started/requirements-applications.md#rms-enlightened-applications).

Usługa Azure Rights Management obsługuje wszystkie typy plików. W przypadku plików tekstowych, obrazów, plików pakietu Microsoft Office (Word, Excel, PowerPoint), plików pdf oraz niektórych typów plików innych aplikacji usługa Azure Rights Management zapewnia natywną ochronę obejmującą zarówno szyfrowanie, jak i wymuszanie praw (uprawnień). W przypadku pozostałych aplikacji i typów plików ochrona ogólna zapewnia hermetyzację plików oraz uwierzytelnianie umożliwiające weryfikację, czy użytkownik jest uprawniony do otwarcia pliku.

Aby uzyskać listę rozszerzeń nazw plików, które są natywnie obsługiwane przez usługę Azure Rights Management, zobacz temat [Typy plików obsługiwane przez klienta usługi Azure Information Protection](../rms-client/client-admin-guide-file-types.md). Rozszerzenia nazw plików, które nie są wymienione na liście, są obsługiwane przy użyciu klienta usługi Azure Information Protection, który automatycznie stosuje do tych plików ochronę ogólną.

## <a name="how-do-i-configure-a-mac-computer-to-protect-and-track-documents"></a>Jak skonfigurować komputer Mac, aby chronić i śledzić dokumenty?

Najpierw upewnij się, że zainstalowano pakiet Office dla komputerów Mac przy użyciu linku instalacji oprogramowania https://portal.office.com. Aby uzyskać pełne instrukcje, zobacz temat [Pobieranie i instalacja lub ponowna instalacja usługi Office 365 lub pakietu Office 2016 na komputerach PC lub Mac](https://support.office.com/en-us/article/Download-and-install-or-reinstall-Office-365-or-Office-2016-on-a-PC-or-Mac-4414EAAF-0478-48BE-9C42-23ADC4716658).

Otwórz program Outlook i utwórz profil przy użyciu konta służbowego usługi Office 365. Następnie utwórz nową wiadomość i wykonaj następujące czynności w celu skonfigurowania pakietu Office, tak aby chronić dokumenty i wiadomości e-mail przy użyciu usługi Azure Rights Management:

1. W nowej wiadomości na karcie **Opcje** kliknij pozycję **Uprawnienia**, a następnie kliknij przycisk **Sprawdź poświadczenia**.

2. Po wyświetleniu monitu podaj szczegóły konta służbowego usługi Office 365, a następnie wybierz przycisk **Zaloguj**. 
    
    Spowoduje to pobranie szablonów usługi Azure Rights Management, a opcja **Sprawdź poświadczenia** zostanie zastąpiona przez kilka opcji, m.in **Brak ograniczeń**, **Nie przesyłaj dalej** oraz wszystkie szablony usługi Azure Rights Management opublikowane dla Twojej dzierżawy. Możesz teraz anulować tę nową wiadomość.

Aby chronić wiadomość e-mail lub dokument: na karcie **Opcje** kliknij pozycję **Uprawnienia** i wybierz opcję lub szablon chroniący wiadomość e-mail lub dokument.

Śledzenie dokumentu po zapewnieniu ochrony: na komputerze z systemem Windows, na którym zainstalowano klienta usługi Azure Information Protection, zarejestruj dokument w witrynie śledzenia dokumentów za pomocą aplikacji pakietu Office lub Eksploratora plików. Aby uzyskać instrukcje, zobacz temat [Śledzenie i odwoływanie dokumentów](../rms-client/client-track-revoke.md). Na komputerze Mac można teraz użyć przeglądarki internetowej, aby przejść do witryny śledzenia dokumentu (https://track.azurerms.com) w celu śledzenia i odwoływania dokumentu.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>Czy po otwarciu dokumentu pakietu Office chronionego przez usługę RMS skojarzony plik tymczasowy jest również chroniony przez usługę RMS?
Nie. W tym scenariuszu skojarzony plik tymczasowy nie zawiera danych z oryginalnego dokumentu, tylko dane wprowadzone przez użytkownika w czasie, w którym ten oryginalny plik był otwarty. W przeciwieństwie do oryginalnego pliku plik tymczasowy oczywiście nie jest przeznaczony do udostępniania i pozostanie na urządzeniu, chroniony przez lokalne zabezpieczenia, takie jak funkcja BitLocker i system szyfrowania plików.

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>Wygląda na to, że funkcja, której potrzebuję, nie współpracuje z chronionymi bibliotekami programu SharePoint. Czy obsługa tej funkcji jest planowana?
Obecnie program SharePoint obsługuje chronionego przez usługi RMS dokumenty przy użyciu usługi IRM chronione bibliotek, które nie obsługują szablony usługi Rights Management, śledzenia dokumentów i innych funkcji. Więcej informacji można znaleźć w sekcji dotyczącej [usługi SharePoint Online i programu SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) w artykule [Office applications and services](../understand-explore/office-apps-services-support.md) (Aplikacje i usługi pakietu Office).

Użytkownicy zainteresowani konkretną funkcją, która nie jest jeszcze obsługiwana, powinni śledzić ogłoszenia na [blogu dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services).

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>Jak skonfigurować usługę OneDrive dla Firm w usłudze SharePoint Online, tak aby użytkownicy mogli bezpiecznie udostępniać pliki wewnątrz i na zewnątrz firmy?
Domyślnie tej usługi nie konfiguruje administrator usługi Office 365, lecz robią to użytkownicy.

Podobnie jak administrator witryny programu SharePoint włącza i konfiguruje usługę IRM dla biblioteki programu SharePoint, której jest właścicielem, usługa OneDrive dla Firm jest zaprojektowana tak, aby użytkownicy włączali i konfigurowali usługę IRM dla własnej biblioteki usługi OneDrive dla Firm. Można jednak zrobić to dla nich, korzystając ze środowiska PowerShell. Instrukcje można znaleźć w sekcji [SharePoint Online and OneDrive for Business: IRM Configuration](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) (Usługi SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM) artykułu [Office 365: Configuration for clients and online services](../deploy-use/configure-office365.md) (Usługa Office 365: konfiguracja dla klientów i usług online).

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>Czy istnieją jakieś wskazówki ułatwiające pomyślne wdrożenie?

Po nadzorowaniu wielu wdrożeń i wysłuchaniu opinii naszych klientów, partnerów, konsultantów i inżynierów pomocy technicznej możemy udzielić jednej podstawowej wskazówki opartej na naszym doświadczeniu: **projektuj i wdrażaj proste zasady**.

Ponieważ usługa Azure Information Protection umożliwia bezpieczne udostępnianie dowolnym osobom, można pozwolić sobie na ambitne podejście do zasięgu ochrony danych. Ale ostrożnego podejścia podczas konfigurowania uprawnień ograniczenia użycia. W przypadku wielu organizacji największe znaczenie biznesowe pochodzi z zapobiegając równocześnie wyciekowi danych przez ograniczenie dostępu do osób w danej organizacji. Oczywiście w razie potrzeby można wprowadzić bardziej szczegółowe ograniczenia — uniemożliwiać drukowanie, edycję itd. Ale zachować szczegółowe ograniczenia jako wyjątek w przypadku dokumentów wymagających naprawdę specjalnej ochrony, a nie implementuje te bardziej restrykcyjnych praw użytkowania na jeden dzień, ale zaplanować podejście etapowe.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>Jak odzyskać dostęp do plików, które były chronione przez pracownika, który opuścił organizację?
Użyj [funkcja superużytkowników](../deploy-use/configure-super-users.md), który przyznaje użytkowania Pełna kontrola praw do autoryzowanych użytkowników dla wszystkich dokumentów i wiadomości e-mail, które są chronione przez dzierżawy. Administratorów mogą zawsze odczytać tę chronioną zawartość, a w razie potrzeby usuń ochronę lub Włącz ochronę ponownie dla różnych użytkowników. Ta sama funkcja w razie potrzeby umożliwia autoryzowanym usługom indeksowanie i przeprowadzanie inspekcji plików.

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>Podczas testowania odwołania w witrynie śledzenia dokumentów wyświetlany jest komunikat informujący, że użytkownicy mogą nadal uzyskiwać dostęp do dokumentu przez okres do 30 dni — czy ten okres można skonfigurować?

Tak. Ten komunikat odzwierciedla [licencję użytkowania](../deploy-use/configure-usage-rights.md#rights-management-use-license) dla tego określonego pliku. 

W przypadku odwołania pliku ta akcja może zostać wymuszona tylko wtedy, gdy użytkownik jest uwierzytelniany w usłudze Azure Rights Management. Na przykład jeśli plik ma 30-dniowy okres ważności licencji użytkowania, a użytkownik ma już otwarty dokument, ten użytkownik będzie mieć nadal dostęp do dokumentu w okresie ważności licencji użytkowania. Po wygaśnięciu licencji użytkowania użytkownik musi zostać ponownie uwierzytelniony. Nastąpi wtedy odmowa dostępu, ponieważ dokument będzie już odwołany.

To odwołanie nie dotyczy użytkownika, który włączył ochronę dokumentu, czyli [wystawcy usługi Rights Management](../deploy-use/configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) — ma on zawsze dostęp do swoich dokumentów. 

Wartość domyślna dla okresu ważności licencji używany dla dzierżawy to 30 dni i to ustawienie może być zastąpiona przez bardziej restrykcyjne ustawienie w etykiecie lub w szablonie. Aby uzyskać więcej informacji o licencji użytkowania i sposobie konfigurowania go, zobacz [licencję użytkowania usługi Rights Management](../deploy-use/configure-usage-rights.md#rights-management-use-license) dokumentacji.

## <a name="can-rights-management-prevent-screen-captures"></a>Czy usługa Rights Management może uniemożliwiać przechwytywanie ekranu?
Przez nieprzyznanie [prawa użytkowania](../deploy-use/configure-usage-rights.md) **Kopiowanie** usługa Rights Management może zapobiegać przechwytywaniu ekranu za pomocą wielu typowych narzędzi na różnych platformach Windows (Windows 7, Windows 8.1, Windows 10, Windows Phone) i Android. Jednak urządzenia z systemem iOS i komputery Mac nie zezwalają żadnej aplikacji na zapobieganie przechwytywaniu ekranu. Podobna sytuacja ma miejsce w przypadku przeglądarek (na przykład używanych łącznie z aplikacjami Outlook Web App i Office Online), które również nie mogą uniemożliwiać przechwytywania ekranu.

Uniemożliwianie przechwytywania ekranu może pomóc uniknąć przypadkowego lub wynikającego z niedbałości ujawnienia poufnych lub wrażliwych informacji. Użytkownik może jednak udostępniać dane wyświetlane na ekranie różnymi sposobami, a wykonanie zrzutu ekranu jest tylko jedną z nich. Użytkownik chcący udostępnić wyświetlane informacje może na przykład zrobić zdjęcie ekranu aparatem w telefonie, przepisać dane lub po prostu słownie przekazać je innej osobie.

Jak dowodzą te przykłady, nawet jeśli wszystkie platformy i całe oprogramowanie obsługuje interfejsy API usługi Rights Management pod kątem blokowania przechwytywania ekranu, sama technologia nie może zapobiec udostępnieniu przez użytkowników poufnych danych. Usługa Rights Management może pomóc chronić ważne dane za pomocą zasad autoryzacji i użycia, ale to rozwiązanie do zarządzania prawami w przedsiębiorstwie powinno być stosowane razem z innymi środkami kontroli. Przekłady obejmują wdrożenie zabezpieczeń fizycznych, dokładne monitorowanie osób mających uprawnienia dostępu do danych organizacji oraz inwestowanie w edukację użytkowników, tak aby wiedzieli, których danych nie należy udostępniać.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>Jaka jest różnica między ochroną wiadomości e-mail za pomocą ustawienia Nie przesyłaj dalej i szablonem bez prawa do przesyłania dalej?

Niezależnie od nazwy i wyglądu ustawienie **Nie przesyłaj dalej** nie jest przeciwieństwem prawa do przesyłania dalej ani szablonem. Jest to zestaw praw obejmujących ograniczenia przesyłania dalej wiadomości e-mail, kopiowania, drukowania i zapisywania załączników. Prawa są dynamicznie stosowane do użytkowników za pośrednictwem wybranych adresatów, a nie statycznie przypisane przez administratora. Więcej informacji można znaleźć w sekcji [Opcja Nie przekazuj dotycząca wiadomości e-mail](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) w artykule [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](../deploy-use/configure-usage-rights.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


