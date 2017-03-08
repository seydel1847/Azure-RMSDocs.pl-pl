---
title: "Często zadawane pytania dotyczące usługi Azure RMS — AIP"
description: "Niektóre często zadawane pytania dotyczące usługi ochrony danych Azure Rights Management (Azure RMS) z usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/22/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dccc643ae49521262d5327b4d3d98801f88b3894
ms.openlocfilehash: ed200df12b3d0665920091c7772ed88a79143e70
ms.lasthandoff: 02/25/2017


---

# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Często zadawane pytania dotyczące ochrony danych w usłudze Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Masz pytanie dotyczące usługi ochrony danych Azure Rights Management z usługi Azure Information Protection? Zobacz, czy nie znajdziesz tutaj odpowiedzi. 

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>Czy pliki muszą znajdować się w chmurze, aby mogły być chronione przez usługę Azure Rights Management?
Nie, to powszechne nieporozumienie. Usługa Azure Rights Management (ani firma Microsoft) nie widzi ani nie przechowuje danych użytkownika w ramach procesu ochrony informacji. Chronione informacje nie są wysyłane na platformę Azure ani na niej przechowywane, chyba że użytkownik jawnie zapisze je na platformie Azure lub w innej usłudze chmurowej, która magazynuje dane na tej platformie. 

Aby uzyskać więcej informacji, zobacz temat [How does Azure RMS work? Under the hood](../understand-explore/how-does-it-work.md) (Jak działa usługa RMS? Kulisy), aby dowiedzieć się, jak tajna receptura coli, utworzona i przechowywana lokalnie, jest chroniona przez usługę Azure Rights Management, ale pozostaje zapisana lokalnie.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Jaka jest różnica między szyfrowaniem w usłudze Azure Rights Management i szyfrowaniem w innych usługach firmy Microsoft w chmurze?

Firma Microsoft udostępnia wiele technologii szyfrowania, które umożliwiają ochronę danych dla różnych i często uzupełniających się scenariuszy. Na przykład, gdy usługa Office 365 oferuje szyfrowania podczas spoczynku dla danych przechowywanych w usłudze Office 365, usługa Azure Rights Management z usługi Azure Information Protection niezależnie szyfruje Twoje dane tak, aby były chronione bez względu na to, gdzie się znajdują lub jak są przesyłane.

Te technologie szyfrowania uzupełniają się, a ich użycie wymaga niezależnego ich włączenia i skonfigurowania. Gdy to zrobisz, możesz mieć możliwość pobrania własnego klucza szyfrowania w scenariuszu znanym także jako „BYOK”. Włączenie funkcji BYOK dla jednej z tych technologii nie wpływa na inne. Na przykład możesz użyć funkcji BYOK dla usługi Azure Information Protection i nie używać jej dla innych technologii szyfrowania i na odwrót. Klucze używane przez te różne technologie mogą być takie same lub różne w zależności od sposobu, w jaki skonfigurujesz opcje szyfrowania dla każdej usługi.

## <a name="whats-the-difference-between-byok-and-hyok-and-when-should-i-use-them"></a>Jaka jest różnica między funkcjami BYOK i HYOK i kiedy należy ich używać?

Funkcja **Bring your own key** (BYOK) w kontekście usługi Azure Information Protection jest używana w przypadku tworzenia własnego lokalnego klucza w celu zastosowania ochrony przy użyciu usługi Azure Rights Management. Ten klucz jest następnie przenoszony do sprzętowego modułu zabezpieczeń (HSM) w magazynie kluczy Azure, w którym nadal jesteś jego właścicielem i możesz nim zarządzać. Jeśli tego nie zrobisz, ochrona Azure Rights Management będzie używać klucza, który jest automatycznie tworzony i zarządzany w systemie Azure. Konfiguracja domyślna jest określana jako „zarządzana przez Microsoft” w odróżnieniu od „zarządzanej przez klienta” (opcja BYOK).

Aby uzyskać więcej informacji o funkcji BYOK i wyborze tej topologii klucza dla Twojej organizacji, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md). 

Funkcja **Hold your own key** (HYOK) w kontekście usługi Azure Information Protection jest przeznaczona dla niewielkiej liczby organizacji, w przypadku których pewne dokumenty lub wiadomości e-mail nie mogą być chronione za pomocą klucza przechowywanego w chmurze. W przypadku takich organizacji to ograniczenie obowiązuje nawet wówczas, jeśli utworzono klucz i zarządza się nim przy użyciu funkcji BYOK. To ograniczenie może obowiązywać z powodów prawnych lub wymogów zgodności z przepisami, zaś funkcja HYOK powinna być stosowana tylko do informacji klasyfikowanych jako „ściśle tajne”, które nigdy nie będą udostępniane poza organizację i będą wykorzystywane tylko w sieci wewnętrznej, a dostęp do nich nie będzie uzyskiwany z urządzeń przenośnych. 

Dla tych wyjątków (stanowiących zwykle nie więcej niż 10% całej chronionej zawartości) organizacja może wykorzystać rozwiązanie lokalne Active Directory Rights Management Services w celu utworzenia klucza, który pozostanie w środowisku lokalnym. Dzięki temu rozwiązaniu komputery pobierają zasady usługi Azure Information Protection z chmury, ale określona zawartość będzie chroniona przy użyciu lokalnego klucza.

Aby uzyskać więcej informacji o funkcji HYOK i upewnić się, że dobrze zrozumiano jej ograniczenia oraz wskazówki dotyczące jej stosowania, patrz [Wymagania i ograniczenia dotyczące rozwiązania „hold your own key” (HYOK) dla ochrony za pomocą usług AD RMS](../deploy-use/configure-adrms-restrictions.md).

## <a name="where-can-i-find-information-about-3rd-party-solutions-that-integrate-with-azure-rms"></a>Gdzie można znaleźć informacje o rozwiązaniach innych firm, które integrują się z usługą Azure RMS?

Wielu dostawców oprogramowania już ma lub wdraża rozwiązania zintegrowane z usługą Azure Rights Management. Liczba takich rozwiązań rośnie bardzo szybko. Dla użytkowników może być bardzo przydatne zapoznanie się z [blogiem dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) i śledzenie najnowszych aktualizacji kanału [Dan Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy) w serwisie Twitter. Jeśli jednak masz konkretne pytanie, wyślij wiadomość e-mail do zespołu usługi Information Protection na adres askipteam@microsoft.com.

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>Czy istnieje pakiet zarządzania lub podobny mechanizm monitorowania dla łącznika usługi RMS?

Mimo że łącznik usługi Rights Management rejestruje informacje, ostrzeżenia i komunikaty o błędach w dzienniku zdarzeń, nie istnieje pakiet administracyjny, który obejmuje monitorowanie tych zdarzeń. Jednak lista zdarzeń i ich opisów wraz dodatkowymi informacjami ułatwiającymi podejmowanie działań naprawczych jest opisana w sekcji [Monitorowanie łącznika usługi Azure Rights Management](../deploy-use/monitor-rms-connector.md).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators"></a>Czy trzeba być administratorem globalnym, aby skonfigurować usługę Azure RMS, czy można to oddelegować do innych administratorów?

Administratorzy globalni dla dzierżawy usługi Office 365 lub dzierżawy usługi Azure AD mogą oczywiście uruchamiać wszystkie zadania administracyjne dla usługi Azure Rights Management. Jednak jeśli chcesz przypisać uprawnienia administracyjne do innych użytkowników, możesz to zrobić przy użyciu polecenia cmdlet programu PowerShell usługi Azure RMS [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/dn629417.aspx). Tę rolę administracyjną można przypisać według konta użytkownika lub grupy. Dostępne są dwie role: **Administrator globalny** i **Administrator łącznika**. 

Tak jak te nazwy sugerują, pierwsza rola przyznaje uprawnienia do uruchamiania wszystkich zadań administracyjnych dla usługi Azure Rights Management (bez nadawania użytkownikom roli administratora globalnego dla innych usług w chmurze), a druga rola przyznaje uprawnienia do uruchamiania tylko łącznika usługi Rights Management (RMS).

Dodatkowe kwestie, na które należy zwrócić uwagę:

- Tylko administratorzy globalni usługi Office 365 i administratorzy globalni usługi Azure AD mogą używać portali zarządzania (centrum administracyjne usługi Office 365 lub klasyczny portal Azure) do konfigurowania usługi Azure RMS. Użytkownicy, którym przypisywana jest rola administratora globalnego usługi Azure RMS, muszą używać poleceń cmdlet programu PowerShell usługi Azure RMS do konfigurowania usługi Azure RMS. W celu łatwiejszego znalezienia odpowiednich poleceń cmdlet służących do wykonywania określonych zadań, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](../deploy-use/administer-powershell.md).

- Jeśli skonfigurowano [kontrolki dołączania](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), nie ma to wpływu na możliwość administrowania usługą Azure RMS, z wyjątkiem łącznika usługi RMS. Na przykład jeśli kontrolki dołączania zostały skonfigurowane w taki sposób, że możliwość ochrony zawartości jest ograniczona do grupy Dział IT, konto używane do instalowania i konfigurowania łącznika usługi RMS musi należeć do tej grupy. 

- Żaden administrator usługi Azure RMS (administrator globalny dzierżawy lub administrator globalny usługi Azure RMS) nie może automatycznie usunąć ochrony dokumentów lub wiadomości e-mail, które były chronione przez usługę Azure RMS. Tylko użytkownicy przypisani do funkcji administratorów usługi Azure RMS mogą to zrobić i może to mieć miejsce tylko po włączeniu funkcji administratorów. Jednak administrator globalny dzierżawy i dowolny administrator globalny usługi Azure RMS może przypisywać użytkowników jako administratorów (dotyczy to również ich własnego konta). Mogą oni również włączyć funkcję administratorów. Te akcje są rejestrowane w dzienniku administratora usługi Azure RMS. Aby uzyskać więcej informacji, zobacz sekcję najlepszych praktyk dotyczących zabezpieczeń w temacie [Konfigurowanie superużytkowników usług Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md). 


## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Mam hybrydowe wdrożenie programu Exchange — niektórzy użytkownicy korzystają z usługi Exchange Online, inni z programu Exchange Server. Czy usługa Azure RMS obsługuje taką sytuację?
Oczywiście, a dodatkową korzyścią jest to, że użytkownicy będą mogli w łatwy sposób chronić wiadomości e-mail i załączniki, a także korzystać z nich w obu wdrożeniach programu Exchange. W przypadku takiej konfiguracji należy najpierw [aktywować usługę Azure RMS](../deploy-use/activate-service.md) i [włączyć usługę IRM dla usługi Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), a następnie [wdrożyć i skonfigurować łącznik usługi RMS](../deploy-use/deploy-rms-connector.md) dla programu Exchange Server.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azure-rms"></a>Czy korzystanie z tej ochrony w środowisku produkcyjnym wymusza na firmie korzystanie z tego rozwiązania lub powoduje ryzyko utraty dostępu do zawartości chronionej za pomocą usługi Azure RMS?
Nie, zawsze zachowujesz kontrolę nad swoimi danymi i możesz nadal uzyskiwać do nich dostęp, nawet jeśli zrezygnujesz z używania usługi Azure Rights Management. Aby uzyskać więcej informacji, zobacz artykuł [Likwidowanie i dezaktywowanie usługi Azure Rights Management](../deploy-use/decommission-deactivate.md).

Jednak zanim zlikwidujesz wdrożenie usługi Azure RMS, chcielibyśmy poznać powód podjęcia takiej decyzji. Jeśli usługa Azure Rights Management nie spełnia określonych wymagań biznesowych, należy skontaktować się z nami i sprawdzić, czy w najbliższej przyszłości planowane jest wprowadzenie nowych funkcji lub czy są dostępne opcje alternatywne. Wyślij wiadomość e-mail na adres [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS), a chętnie omówimy Twoje wymagania techniczne i biznesowe.

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Czy można kontrolować, którzy użytkownicy w przedsiębiorstwie mogą korzystać z usługi Azure RMS do ochrony zawartości?
Tak, usługa Azure Rights Management zawiera mechanizmy dodawania użytkowników wymagane w tym scenariuszu. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [konfigurowania funkcji kontroli dołączania użytkowników we wdrożeniu etapowym](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) w artykule [Activating Azure Rights Management](../deploy-use/activate-service.md) (Aktywowanie usługi Azure Rights Management).

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>Czy można uniemożliwić udostępnianie przez użytkowników dokumentów chronionych określonym organizacjom?
Jedną z największych zalet używania usługi Azure Rights Management do ochrony danych jest obsługiwanie współpracy między firmami bez konieczności jawnego konfigurowania zaufania dla każdej organizacji partnerskiej, ponieważ usługa Azure AD sama obsługuje uwierzytelnianie.

Nie ma administracyjnej możliwości uniemożliwiania bezpiecznego udostępniania dokumentów przez użytkowników określonym organizacjom. Na przykład chcesz zablokować organizację, której nie ufasz lub która prowadzi konkurencyjną działalność. Uniemożliwienie usłudze Azure Rights Management wysyłania chronionych dokumentów do użytkowników w takich organizacjach nie miałoby sensu, ponieważ użytkownicy mogliby wówczas udostępniać dokumenty bez ochrony, co byłoby zdecydowanie niepożądane. W takiej sytuacji wskazanie osoby udostępniającej poufne dokumenty firmy i ich odbiorców w takich organizacjach byłoby niemożliwe. Można to zrobić, jeśli dokument (lub wiadomość e-mail) podlega ochronie za pomocą usługi Azure Rights Management.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>W jaki sposób może zostać uwierzytelniony użytkownik spoza mojej firmy, któremu udostępniam chroniony dokument?
Do uwierzytelnienia użytkownika usługa Azure Rights Management zawsze używa konta usługi Azure Active Directory i powiązanego adresu e-mail, dlatego współpraca między firmami przebiega bez sprawiania problemów administratorom. Jeśli inna organizacja używa usług Azure, użytkownicy mają już konta w usłudze Azure Active Directory, nawet jeśli te konta są tworzone i zarządzane lokalnie, a następnie synchronizowane z platformą Azure. Jeśli organizacja korzysta z usługi Office 365, to ta usługa również używa usługi Azure Active Directory do obsługi kont użytkowników. Jeśli organizacja użytkownika nie posiada kont zarządzanych na platformie Azure, użytkownicy mogą rejestrować się w celu uzyskania [usług RMS dla osób indywidualnych](../understand-explore/rms-for-individuals.md), co powoduje utworzenie niezarządzanej dzierżawy platformy Azure i katalogu dla organizacji z kontem użytkownika, tak aby ten użytkownik (i kolejni) mógł zostać uwierzytelniony do korzystania z usługi Azure Rights Management.

Metody uwierzytelniania w przypadku tych kont mogą się różnić w zależności od tego, jak administrator drugiej organizacji skonfigurował konta w usłudze Azure Active Directory. Można na przykład korzystać z haseł utworzonych dla tych kont, uwierzytelniania wieloskładnikowego (MFA), federacji lub haseł utworzonych w usługach domenowych Active Directory i następnie zsynchronizowanych z usługą Azure Active Directory.

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>Czy mogę dodać użytkowników zewnętrznych (osoby spoza firmy) do szablonów niestandardowych?
Tak. Tworzenie szablonów niestandardowych, które użytkownicy końcowi (i administratorzy) mogą wybierać z poziomu aplikacji, ułatwia i przyspiesza stosowanie ochrony informacji za pomocą określonych wstępnie zdefiniowanych zasad. Jedno z ustawień w szablonie dotyczy użytkownika, który może uzyskiwać dostęp do zawartości. Można wskazać użytkowników i grupy w obrębie własnej organizacji i spoza niej. 

Aby określić użytkowników spoza organizacji, dodaj ich jako kontakty do grupy wybranej w klasycznym portalu Azure podczas konfigurowania szablonów. Aby określić grupy spoza organizacji, należy użyć modułu [Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md), za pomocą którego można również określić poszczególnych użytkowników zewnętrznych, a nawet wszystkich użytkowników z innej organizacji:

-   **Użyj obiektu definicji praw, aby utworzyć lub zaktualizować szablon**.    Określ zewnętrzne adresy e-mail i ich prawa w obiekcie definicji praw, który następnie zostanie użyty do utworzenia lub zaktualizowania szablonu. Aby określić obiekt definicji praw, utwórz zmienną za pomocą polecenia cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx). Następnie wykonaj polecenie cmdlet [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) (w przypadku nowego szablonu) lub polecenie cmdlet [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) (w przypadku modyfikacji istniejącego szablonu), aby dostarczyć tę zmienną do parametru -RightsDefinition. Jeśli jednak użytkownicy są dodawani do istniejącego szablonu, należy zdefiniować obiekty definicji praw dla istniejących grup w szablonach, a nie tylko dla użytkowników zewnętrznych.

Więcej informacji na temat szablonów niestandardowych można znaleźć w temacie [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

## <a name="does-azure-rms-work-with-dynamic-groups-in-azure-ad"></a>Czy usługa Azure RMS współpracuje z grupami dynamicznymi w usłudze Azure AD?
Funkcja Azure AD Premium pozwala skonfigurować członkostwo dynamiczne w grupach, określając [reguły oparte na atrybucie](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/). Typ grupy zabezpieczeń utworzonej w usłudze Azure AD obsługuje członkostwo dynamiczne, ale nie obsługuje adresu e-mail i dlatego nie może być używany z usługą Azure Rights Management. Teraz można jednak utworzyć w usłudze Azure AD nowy typ grupy, który obsługuje członkostwo dynamiczne, a jednocześnie ma włączoną obsługę poczty. Podczas dodawania nowej grupy w klasycznym portalu Azure można wybrać **TYP GRUPY** **usługi Office 365 Preview**. Ponieważ jest to grupa z włączoną obsługą poczty e-mail, można używać jej wraz z usługą Azure Rights Management.

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Jakie urządzenia i typy plików są obsługiwane przez usługę Azure RMS?
Aby uzyskać listę urządzeń obsługujących usługę Azure Rights Management, zobacz [Urządzenia klienckie obsługujące ochronę danych usługi Azure Rights Management](../get-started/requirements-client-devices.md). Ponieważ nie wszystkie obsługiwane urządzenia obecnie obsługują wszystkie funkcje usługi Rights Management, należy również zapoznać się z tabelą w sekcji [Aplikacje obsługujące ochronę danych usługi Azure Rights Management](../get-started/requirements-applications.md).

Usługa Azure Rights Management obsługuje wszystkie typy plików. W przypadku plików tekstowych, obrazów, plików pakietu Microsoft Office (Word, Excel, PowerPoint), plików pdf oraz niektórych typów plików innych aplikacji usługa Azure Rights Management zapewnia natywną ochronę obejmującą zarówno szyfrowanie, jak i wymuszanie praw (uprawnień). W przypadku pozostałych aplikacji i typów plików ochrona ogólna zapewnia hermetyzację plików oraz uwierzytelnianie umożliwiające weryfikację, czy użytkownik jest uprawniony do otwarcia pliku.

Aby uzyskać listę rozszerzeń nazw plików, które są natywnie obsługiwane przez usługę Azure Rights Management, zobacz temat [Typy plików obsługiwane przez klienta usługi Azure Information Protection](../rms-client/client-admin-guide-file-types.md). Rozszerzenia nazw plików, które nie są wymienione na liście, są obsługiwane przy użyciu klienta usługi Azure Information Protection, który automatycznie stosuje do tych plików ochronę ogólną.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>Czy po otwarciu dokumentu pakietu Office chronionego przez usługę RMS skojarzony plik tymczasowy jest również chroniony przez usługę RMS?

Nie. W tym scenariuszu skojarzony plik tymczasowy nie zawiera danych z oryginalnego dokumentu, tylko dane wprowadzone przez użytkownika w czasie, w którym ten oryginalny plik był otwarty. W przeciwieństwie do oryginalnego pliku plik tymczasowy oczywiście nie jest przeznaczony do udostępniania i pozostanie na urządzeniu, chroniony przez lokalne zabezpieczenia, takie jak funkcja BitLocker i system szyfrowania plików.

## <a name="we-really-want-to-use-byok-with-azure-information-protection-but-learned-that-this-isnt-compatible-with-exchange-onlinewhats-your-advice"></a>Chcemy używać funkcji BYOK z usługą Azure Information Protection, ale dowiedzieliśmy się, że nie jest zgodna z usługą Exchange Online. Jaki jest zalecany sposób postępowania?
Nie pozwólcie, aby to bieżące ograniczenie opóźniło Wam rozpoczęcie korzystania z usługi Azure Rights Management w ramach usługi Azure Information Protection. Użytkownikom usługi Exchange Online chcącym korzystać z funkcji generowania własnych kluczy (BYOK) zaleca się wdrożenie już teraz usługi Azure Information Protection w domyślnym trybie zarządzania kluczami, w którym firma Microsoft generuje klucze i nimi zarządza. Dzięki temu można od razu korzystać z ochrony ważnych plików i wiadomości e-mail z opcją późniejszego wprowadzenia funkcji BYOK (na przykład kiedy usługa Exchange Online będzie już obsługiwać funkcję BYOK). Po wprowadzeniu funkcji BYOK wcześniej chronione dokumenty i wiadomości e-mail będą nadal dostępne przy użyciu zarchiwizowanego klucza.

Jeśli jednak zasady firmy wymagają używania sprzętowego modułu zabezpieczeń (HSM) i w przeciwnym przypadku zablokowałoby to wdrożenie usługi Azure Information Protection, jest możliwe wdrożenie usługi Azure Information Protection z funkcją BYOK już teraz, przy ograniczonych funkcjach ochrony usługi Rights Management w odniesieniu do programu Exchange. Więcej informacji zawiera temat [Cennik i ograniczenia dotyczące funkcji BYOK](../plan-design/byok-price-restrictions.md) w części [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](../plan-design/plan-implement-tenant-key.md).

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>Wygląda na to, że funkcja, której potrzebuję, nie współpracuje z chronionymi bibliotekami programu SharePoint. Czy obsługa tej funkcji jest planowana?
Obecnie program SharePoint obsługuje dokumenty chronione za pomocą usługi Rights Management, korzystając w tym celu z bibliotek chronionych za pomocą usługi IRM, które nie obsługują niestandardowych szablonów, śledzenia dokumentów i niektórych innych funkcji. Więcej informacji można znaleźć w sekcji dotyczącej [usługi SharePoint Online i programu SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) w artykule [Office applications and services](../understand-explore/office-apps-services-support.md) (Aplikacje i usługi pakietu Office).

Użytkownicy zainteresowani konkretną funkcją, która nie jest jeszcze obsługiwana, powinni śledzić ogłoszenia na [blogu dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services).

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>Jak skonfigurować usługę OneDrive dla Firm w usłudze SharePoint Online, tak aby użytkownicy mogli bezpiecznie udostępniać pliki wewnątrz i na zewnątrz firmy?
Domyślnie tej usługi nie konfiguruje administrator usługi Office 365, lecz robią to użytkownicy.

Podobnie jak administrator witryny programu SharePoint włącza i konfiguruje usługę IRM dla biblioteki programu SharePoint, której jest właścicielem, usługa OneDrive dla Firm jest zaprojektowana tak, aby użytkownicy włączali i konfigurowali usługę IRM dla własnej biblioteki usługi OneDrive dla Firm. Można jednak zrobić to dla nich, korzystając ze środowiska PowerShell. Instrukcje można znaleźć w sekcji [SharePoint Online and OneDrive for Business: IRM Configuration](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) (Usługi SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM) artykułu [Office 365: Configuration for clients and online services](../deploy-use/configure-office365.md) (Usługa Office 365: konfiguracja dla klientów i usług online).

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>Czy istnieją jakieś wskazówki ułatwiające pomyślne wdrożenie?
Po nadzorowaniu wielu wdrożeń i wysłuchaniu opinii naszych klientów, partnerów, konsultantów i inżynierów pomocy technicznej możemy udzielić jednej podstawowej wskazówki opartej na naszym doświadczeniu: **projektuj i wdrażaj proste zasady praw**.

Ponieważ usługa Azure Information Protection umożliwia bezpieczne udostępnianie dowolnym osobom, można pozwolić sobie na ambitne podejście do zasięgu ochrony danych. Jednak zasady dotyczące praw należy określać w sposób konserwatywny. W przypadku wielu organizacji najsilniejszy wpływ na prowadzoną działalność ma zapobieganie wyciekowi danych przez stosowanie domyślnego szablonu zasad praw umożliwiającego dostęp wyłącznie osobom z danej organizacji. Oczywiście w razie potrzeby można wprowadzić bardziej szczegółowe ograniczenia — uniemożliwiać drukowanie, edycję itd. Jednak takie szczegółowe ograniczenia należy stosować wyjątkowo, w przypadku dokumentów wymagających naprawdę specjalnej ochrony, i nie implementować ich od razu, ale zaplanować podejście etapowe.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>Jak odzyskać dostęp do plików, które były chronione przez pracownika, który opuścił organizację?
Należy użyć [funkcji superużytkowników](../deploy-use/configure-super-users.md) usługi pozwalającej uprawionym użytkownikom korzystać z pełnych praw użytkowania dotyczących wszystkich licencji na użytkowanie przydzielonych przez dzierżawcę danej organizacji. Ta sama funkcja w razie potrzeby umożliwia autoryzowanym usługom indeksowanie i przeprowadzanie inspekcji plików.

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>Podczas testowania odwołania w witrynie śledzenia dokumentów wyświetlany jest komunikat informujący, że użytkownicy mogą nadal uzyskiwać dostęp do dokumentu przez okres do 30 dni — czy ten okres można skonfigurować?

Tak. Ten komunikat odzwierciedla licencję użytkowania dla tego określonego pliku. Licencja użytkowania to powiązany z dokumentem certyfikat przyznawany użytkownikowi, który otwiera chroniony plik lub wiadomość e-mail. Ten certyfikat zawiera prawa użytkownika dla pliku lub wiadomości e-mail oraz klucz szyfrowania, który został użyty do zaszyfrowania zawartości, a także dodatkowe ograniczenia dostępu zdefiniowane w zasadach dokumentu. Jeśli okres ważności licencji użytkowania zakończył się i użytkownik próbuje otworzyć plik lub wiadomość e-mail, poświadczenia użytkownika muszą zostać ponownie przesłane do usługi Azure Rights Management. 

W przypadku odwołania pliku ta akcja może zostać wymuszona tylko wtedy, gdy użytkownik jest uwierzytelniany w usłudze Azure Rights Management. A więc jeśli plik ma 30-dniowy okres ważności licencji użytkowania, a użytkownik ma już otwarty dokument, ten użytkownik będzie mieć nadal dostęp do dokumentu przez czas trwania licencji użytkowania. Po wygaśnięciu licencji użytkowania użytkownik musi zostać ponownie uwierzytelniony i w tym momencie nastąpi odmowa dostępu, ponieważ dokument będzie już teraz odwołany.

Wartość domyślna dla okresu ważności licencji użytkowania dla dzierżawy wynosi 30 dni. Wartość tę można skonfigurować przy użyciu polecenia cmdlet programu PowerShell [Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx). To ustawienie można przesłonić bardziej restrykcyjnym ustawieniem w szablonie niestandardowym. 

Aby uzyskać dodatkowe informacje i przykłady sposobu działania licencji użytkowania, zobacz szczegółowy opis polecenia [Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx).

## <a name="can-rights-management-prevent-screen-captures"></a>Czy usługa Rights Management może uniemożliwiać przechwytywanie ekranu?
Przez nieprzyznanie [prawa użytkowania](../deploy-use/configure-usage-rights.md) **Kopiowanie** usługa Rights Management może zapobiegać przechwytywaniu ekranu za pomocą wielu typowych narzędzi na różnych platformach Windows (Windows 7, Windows 8.1, Windows 10, Windows Phone) i Android. Jednak urządzenia z systemem iOS i komputery Mac nie zezwalają żadnej aplikacji na zapobieganie przechwytywaniu ekranu. Podobna sytuacja ma miejsce w przypadku przeglądarek (na przykład używanych łącznie z aplikacjami Outlook Web App i Office Online), które również nie mogą uniemożliwiać przechwytywania ekranu.

Uniemożliwianie przechwytywania ekranu może pomóc uniknąć przypadkowego lub wynikającego z niedbałości ujawnienia poufnych lub wrażliwych informacji. Użytkownik może jednak udostępniać dane wyświetlane na ekranie różnymi sposobami, a wykonanie zrzutu ekranu jest tylko jedną z nich. Użytkownik chcący udostępnić wyświetlane informacje może na przykład zrobić zdjęcie ekranu aparatem w telefonie, przepisać dane lub po prostu słownie przekazać je innej osobie.

Jak dowodzą te przykłady, nawet jeśli wszystkie platformy i całe oprogramowanie obsługuje interfejsy API usługi Rights Management pod kątem blokowania przechwytywania ekranu, sama technologia nie może zapobiec udostępnieniu przez użytkowników poufnych danych. Usługa Rights Management może pomóc chronić ważne dane za pomocą zasad autoryzacji i użycia, ale to rozwiązanie do zarządzania prawami w przedsiębiorstwie powinno być stosowane razem z innymi środkami kontroli. Przekłady obejmują wdrożenie zabezpieczeń fizycznych, dokładne monitorowanie osób mających uprawnienia dostępu do danych organizacji oraz inwestowanie w edukację użytkowników, tak aby wiedzieli, których danych nie należy udostępniać.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>Jaka jest różnica między ochroną wiadomości e-mail za pomocą ustawienia Nie przesyłaj dalej i szablonem bez prawa do przesyłania dalej?

Niezależnie od nazwy i wyglądu ustawienie **Nie przesyłaj dalej** nie jest przeciwieństwem prawa do przesyłania dalej ani szablonem. Jest to zestaw praw obejmujących ograniczenia przesyłania dalej wiadomości e-mail, kopiowania, drukowania i zapisywania załączników. Prawa są dynamicznie stosowane do użytkowników za pośrednictwem wybranych adresatów, a nie statycznie przypisane przez administratora. Więcej informacji można znaleźć w sekcji [Opcja Nie przekazuj dotycząca wiadomości e-mail](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) w artykule [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](../deploy-use/configure-usage-rights.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



