---
title: "Często zadawane pytania dotyczące usługi Azure Information Protection"
description: "Niektóre często zadawane pytania dotyczące usługi Azure Information Protection i jej usługi ochrony danych, Azure Rights Management (Azure RMS)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/06/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 23c2b24a830b6d1ab7e0712fc1d1d70056f5d736
ms.sourcegitcommit: d32d1f5afa5ee9501615a6ecc4af8a4cd4901eae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Często zadawane pytania dotyczące usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Masz pytanie dotyczące usługi Azure Information Protection lub usługi Azure Rights Management (Azure RMS)? Zobacz, czy nie znajdziesz tutaj odpowiedzi.

Te strony — często zadawane pytania są regularnie aktualizowana, a nowe informacje będą publikowane w comiesięcznych ogłoszeniach o aktualizacji dokumentacji na [pakietu Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services&content-type=updates).

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Na czym polega różnica między usługą Azure Information Protection i usługą Azure Rights Management?

Usługa Azure Information Protection udostępnia funkcje klasyfikacji, etykietowania i ochrony dokumentów i wiadomości e-mail organizacji. Ta technologia ochrony korzysta z usługi Azure Rights Management; która jest obecnie składnikiem usługi Azure Information Protection.

## <a name="what-is-the-role-of-identity-management-for-azure-information-protection"></a>Czym jest rola zarządzania tożsamościami dla usługi Azure Information Protection?

Użytkownik musi mieć prawidłową nazwę użytkownika i hasło dostępu do zawartości chronionej przez usługę Azure Information Protection. Aby uzyskać więcej informacji na temat sposobu, w jaki usługa Azure Information Protection ułatwia zabezpieczanie danych, zobacz temat [Rola usługi Azure Information Protection w zabezpieczaniu danych](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Jaka subskrypcja jest potrzebna do korzystania z usługi Azure Information Protection i jakie funkcje obejmuje ta subskrypcja?
Zapoznaj się z [informacjami o subskrypcji](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) i [listą funkcji](https://www.microsoft.com/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection. 

Jeśli masz subskrypcję usługi Office 365 obejmującą usługę Rights Management, pobierz [arkusz danych dotyczący licencjonowania usługi Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) ze strony **Funkcje**.

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>Czy klient usługi Azure Information Protection służy wyłącznie do obsługi subskrypcji, które obejmują klasyfikowanie i etykietowanie?

Nie. Choć większość prezentacji i pokazów poświęconych klientowi usługi Azure Information Protection pokazuje obsługę klasyfikacji i etykietowania, to z usługi tej można korzystać również w odniesieniu do subskrypcji obejmujących wyłącznie ochronę z użyciem usługi Azure Rights Management.

Po zainstalowaniu klienta usługi Azure Information Protection dla systemu Windows bez zasad usługi Azure Information Protection klient automatycznie działa w [trybie tylko do ochrony](../rms-client/client-protection-only-mode.md). W tym trybie użytkownicy mogą łatwo stosować szablony usługi Rights Management oraz uprawnienia niestandardowe. W przypadku wykupienia w późniejszym czasie subskrypcji, która obejmuje funkcje klasyfikacji i etykietowania, klient automatycznie przełączy się do trybu standardowego po pobraniu zasad usługi Azure Information Protection.

Jeśli obecnie używasz aplikacji dla systemu Windows do udostępniania usługi Rights Management, firma Microsoft zaleca, Zastąp tę aplikację przy użyciu klienta usługi Azure Information Protection. 31 stycznia 2019 zakończy się obsługa aplikacji do udostępniania. Zachęcamy do zapoznania się z tematem [Zadania, które były wykonywane w aplikacji RMS sharing](../rms-client/upgrade-client-app.md), który zawiera informacje przydatne w okresie przejściowym.

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Czy usługa Azure Information Protection obsługuje scenariusze lokalne i hybrydowe?

Tak. Mimo, że usługa Azure Information Protection jest rozwiązaniem opartym na chmurze, może służyć do klasyfikacji, etykietowania oraz ochrony dokumentów i wiadomości e-mail, które są przechowywane lokalnie oraz w chmurze.

Jeśli używasz programu Exchange Server, SharePoint Server oraz serwerów plików systemu Windows, możesz wdrożyć [łącznik usługi Rights Management](../deploy-use/deploy-rms-connector.md), by serwery te lokalne mogły używać usługi Azure Rights Management do ochrony wiadomości e-mail i dokumentów. Można także przeprowadzić synchronizację i federację kontrolerów domeny usługi Active Directory z usługą Azure AD, aby usprawnić środowisko uwierzytelniania dla użytkowników, na przykład za pomocą programu [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Usługa Azure Rights Management automatycznie generuje certyfikaty XrML i zarządza nimi zgodnie z wymaganiami, dlatego nie korzysta z lokalnej infrastruktury kluczy publicznych. Aby uzyskać więcej informacji o używaniu certyfikatów przez usługę Azure Rights Management, zobacz sekcję [Wskazówki dotyczące działania usługi Azure RMS: pierwsze użycie, ochrona zawartości, zużycie zawartości](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) w artykule [Jak działa usługa Azure RMS?](../understand-explore/how-does-it-work.md).

## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Widać, że usługi Azure Information Protection znajduje się w aplikacji w chmurze dostępnych dla dostępu warunkowego, jak to działa?

Tak, w publicznej wersji zapoznawczej, oferty, można teraz skonfigurować dostęp warunkowy do usługi Azure AD dla usługi Azure Information Protection.

Po otwarciu dokumentu, która jest chroniona przez usługę Azure Information Protection, Administratorzy mogą teraz zablokować lub udzielić dostępu użytkownikom w swojej dzierżawy, oparte na formanty standardowe dostępu warunkowego. Wymaganie uwierzytelniania wieloskładnikowego (MFA) jest jednym z najczęściej wymaganych warunków. Inny jedna jest, że urządzenia muszą być [zgodne z zasadami usługi Intune](/intune/conditional-access-intune-common-ways-use) , aby na przykład urządzenia przenośne spełnia Twoje wymagania dotyczące hasła i minimalna wersja systemu operacyjnego, a komputery muszą być przyłączone do domeny.

Więcej informacji oraz przykłady przewodnik, zobacz następującym wpisie w blogu: [zasady dostępu warunkowego dla usługi Azure Information Protection](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/).

Informacje dodatkowe:

- Dla komputerów z systemem Windows: W bieżącej wersji zapoznawczej, zasady dostępu warunkowego dla usługi Azure Information Protection są oceniane po [zainicjowaniu środowiska użytkownika](../understand-explore/how-does-it-work.md#initializing-the-user-environment) (ten proces jest nazywany również uruchamianie), a następnie na 30 dni.

- Można dostosować, jak często uzyskać obliczone zasad dostępu warunkowego. Można to zrobić, konfigurując okres ważności tokenu. Aby uzyskać więcej informacji, zobacz [można skonfigurować tokenu okresy istnienia w usłudze Azure Active Directory](/azure/active-directory/active-directory-configurable-token-lifetimes).

- Zaleca się, że nie dodawaj kont administratorów do zasad dostępu warunkowego, ponieważ tych kont nie będzie mógł uzyskać dostępu do bloku usługi Azure Information Protection w portalu Azure.

- Jeśli używasz wielu aplikacji w chmurze dla dostępu warunkowego, może nie być wyświetlana **Microsoft Azure Information Protection** wyświetlane na liście, aby wybrać. W takim przypadku należy użyć pola wyszukiwania w górnej części listy. Zacznij wpisywać tekst "Microsoft Azure Information Protection" do filtrowania dostępnych aplikacji. Jeśli masz subskrypcję obsługiwanych, zostanie wyświetlony **Microsoft Azure Information Protection** do wybrania. 

## <a name="whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365"></a>Jaka jest różnica między etykiety usługi Azure Information Protection i etykiety w usłudze Office 365?

Etykiety usługi Azure Information Protection umożliwiają stosowanie spójne zasady klasyfikacji i ochrony dokumentów i wiadomości e-mail, czy są one lokalnie lub w chmurze. Ta klasyfikacja i ochrona jest niezależna od której jest przechowywana zawartość lub jak jest przenoszony. [Etykiety w Office 365 zabezpieczeń i zgodności](https://support.office.com/article/af398293-c69d-465e-a249-d74561552d30) można klasyfikować dokumenty i wiadomości e-mail do inspekcji i przechowywania w przypadku tej zawartości w usługi Office 365. 

Obecnie stosowane i zarządzania tymi etykiety oddzielnie, lecz firma Microsoft pracuje w kierunku kompleksowy i ujednoliconego strategii etykietowania dla wielu usług, które obejmują usługi Azure Information Protection, usługi Office 365, Microsoft Cloud App Security i Windows Ochrona informacji. Ten sam schemat etykietowania i magazynu będzie także dostępna dla dostawców oprogramowania. Aby uzyskać więcej informacji, zobacz sesji Microsoft Ignite 2017 [ochrona cyklu pełnych danych przy użyciu funkcji ochrony informacji firmy Microsoft](https://myignite.microsoft.com/videos/55397).

## <a name="whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner"></a>Jaka jest różnica między infrastruktury klasyfikacji plików systemu Windows Server i skanera usługi Azure Information Protection?

Przez jakiś czas flaguje za pomocą infrastruktury klasyfikacji plików systemu Windows Server można klasyfikować dokumenty oraz chronić je przy użyciu [łącznik usługi Rights Management](../deploy-use/deploy-rms-connector.md) (tylko w Office dokumenty) lub [programu PowerShell skrypt](../rms-client/configure-fci.md) (wszystkich typów plików). 

Można teraz używać [skanera usługi Azure Information Protection](../deploy-use/deploy-aip-scanner.md), obecnie w wersji zapoznawczej. Skaner używa klienta Azure Information Protection i zasady usługi Azure Information Protection, aby dokumenty etykiety (wszystkich typów plików), następnie sklasyfikowanych i chronionych opcjonalnie tych dokumentów.

Główne różnice między te dwa rozwiązania:

|Windows Server infrastruktury klasyfikacji plików|Skaner usługi Azure Information Protection|
|--------------------------------|-------------------------------------|
|Obsługiwane magazyny danych: <br /><br />-Lokalnych folderów w systemie Windows Server|Obsługiwane magazyny danych: <br /><br />-Lokalnych folderów w systemie Windows Server<br /><br />— Windows plików, udziały i Magazyn dołączony do sieci<br /><br />— SharePoint Server 2016 i SharePoint Server 2013|
|Tryb operacyjne: <br /><br />-Czasu rzeczywistego|Tryb operacyjne: <br /><br />-Systematycznie przeszukuje magazynów danych i tego cyklu można uruchomić jeden raz lub wielokrotnie|

Obecnie ma różnicy w ustawieniu [właściciela zarządzania prawami](../deploy-use/configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) dla plików, które są chronione na lokalnego folderu lub udziału sieciowego. Domyślnie dla obu rozwiązań właściciela zarządzania prawami jest ustawiony na konto, które chroni plik, ale można zastąpić to ustawienie:

- Infrastruktury klasyfikacji plików w systemie Windows Server: Ustawianie właściciela usługi Rights Management jako jednego konta dla wszystkich plików lub dynamiczne określanie właściciela zarządzania prawami dla każdego pliku. Aby ustawić dynamicznie właściciela zarządzania prawami, należy użyć **- OwnerMail [E-mail właściciela pliku źródłowego]** parametr i wartość. Ta konfiguracja pobiera adres e-mail użytkownika z usługi Active Directory przy użyciu nazwy konta użytkownika w pliku właściwości właściciela.

- Skanera usługi Azure Information Protection: można ustawić właściciela zarządzania prawami jednego konta dla wszystkich plików w magazynie określone dane, ale nie można ustawić dynamicznie właściciela zarządzania prawami dla każdego pliku. Aby ustawić konta, określ **- DefaultOwner** parametr [profilu repozytorium danych](/powershell/module/azureinformationprotection/Set-AIPScannerRepository?view=azureipps#optional-parameters).

Gdy skaner chroni pliki w witrynach programu SharePoint i bibliotek, właściciela zarządzania prawami dynamicznie ustawiono dla każdego pliku przy użyciu wartości autora programu SharePoint.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Podobno nowa wersja ma być wkrótce dostępna dla usługi Azure Information Protection — kiedy zostanie ona wydana?

Dokumentacja techniczna nie zawiera informacji o kolejnych wersjach. Dla tego typu informacji i zapowiedzi dotyczących wersji, zobacz [pakietu Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services) i Pobierz najnowsze aktualizacje z [Microsoft Mobility@MSFTMobility ](https://twitter.com/MSFTMobility) w serwisie Twitter. Jeśli interesuje Cię wersja pakietu Office, sprawdź również [blog dotyczący pakietu Office](https://blogs.office.com/).

## <a name="where-can-i-find-supporting-information-for-azure-information-protectionsuch-as-legal-compliance-and-slas"></a>Gdzie można znaleźć dodatkowe informacje na temat usługi Azure Information Protection dotyczące na przykład kwestii prawnych oraz związanych ze zgodnością i umowami SLA?

Zobacz [Zgodność i informacje dodatkowe dotyczące usługi Azure Information Protection](../understand-explore/compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Jak zgłosić problem lub wysłać opinię dotyczącą usługi Azure Information Protection?

Aby skorzystać z pomocy technicznej, użyj standardowych kanałów pomocy lub [skontaktuj się z pomocą techniczną firmy Microsoft](information-support.md#to-contact-microsoft-support).

Aby przekazać opinie, w tym sugestie dotyczące ulepszeń i nowych funkcji, w aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** kliknij przycisk **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **Prześlij opinię**. Ta opcja powoduje otwarcie wiadomości e-mail do wysłania do zespołu Information Protection.

Zachęcamy także do kontaktowania się z naszymi inżynierami za pośrednictwem [strony usługi Azure Information Protection w witrynie Yammer](https://www.yammer.com/askipteam/). 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>Co należy zrobić, jeśli mojego pytania nie ma na tej liście?

Po pierwsze Przejrzyj poniższe często zadawane pytania, które są specyficzne dla klasyfikacji i etykietowania lub specyficzne dla ochrony danych. Usługa Azure Rights Management (Azure RMS) zapewnia technologii ochrony danych usługi Azure Information Protection. Usługa Azure RMS można z klasyfikacji i etykietowania lub samodzielnie. 

- [Często zadawane pytania dotyczące klasyfikacji i etykietowania](faqs-infoprotect.md)

- [Często zadawane pytania dotyczące ochrony danych](faqs-rms.md)

W przypadku nieznalezienia odpowiedzi na pytanie skorzystaj z linków i zasobów wymienionych w artykule [Informacje i pomoc techniczna dla usługi Azure Information Protection](information-support.md).

Ponadto są przeznaczone dla użytkowników końcowych często zadawane pytania:

- [Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android](../rms-client/mobile-app-faq.md)

- [Często zadawane pytania dotyczące aplikacji RMS sharing dla komputerów Mac i telefonów Windows Phone](https://technet.microsoft.com/dn451248)

- [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Rights Management dla systemu Windows](https://technet.microsoft.com/dn467883)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]

