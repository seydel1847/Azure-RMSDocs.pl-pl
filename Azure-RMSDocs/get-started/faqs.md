---
title: "Często zadawane pytania dotyczące usługi Azure Information Protection"
description: "Niektóre często zadawane pytania dotyczące usługi Azure Information Protection i jej usługi ochrony danych, Azure Rights Management (Azure RMS)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: cbceb3f3e68c558576cc275793dac6feb3b9245b
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Często zadawane pytania dotyczące usługi Azure Information Protection
<a id="frequently-asked-questions-for-azure-information-protection" class="xliff"></a>

>*Dotyczy: Azure Information Protection, Office 365*

Masz pytanie dotyczące usługi Azure Information Protection lub usługi Azure Rights Management (Azure RMS)? Zobacz, czy nie znajdziesz tutaj odpowiedzi.

Te strony zawierające często zadawane pytania będą regularnie aktualizowane, a nowe informacje będą publikowane w comiesięcznych ogłoszeniach o aktualizacji dokumentacji na [blogu dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services).

## Na czym polega różnica między usługą Azure Information Protection i usługą Azure Rights Management?
<a id="whats-the-difference-between-azure-information-protection-and-azure-rights-management" class="xliff"></a>

Usługa Azure Information Protection udostępnia funkcje klasyfikacji, etykietowania i ochrony dokumentów i wiadomości e-mail organizacji. Ta technologia ochrony korzysta z usługi Azure Rights Management; która jest obecnie składnikiem usługi Azure Information Protection.

## Czym jest rola zarządzania tożsamościami dla usługi Azure Information Protection?
<a id="what-is-the-role-of-identity-management-for-azure-information-protection" class="xliff"></a>

Użytkownik musi mieć prawidłową nazwę użytkownika i hasło dostępu do zawartości chronionej przez usługę Azure Information Protection. Aby uzyskać więcej informacji na temat sposobu, w jaki usługa Azure Information Protection ułatwia zabezpieczanie danych, zobacz temat [Rola usługi Azure Information Protection w zabezpieczaniu danych](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## Jaka subskrypcja jest potrzebna do korzystania z usługi Azure Information Protection i jakie funkcje obejmuje ta subskrypcja?
<a id="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included" class="xliff"></a>
Zapoznaj się z [informacjami o subskrypcji](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) i [listą funkcji](https://www.microsoft.com/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection. 

Jeśli masz subskrypcję usługi Office 365 obejmującą usługę Rights Management, pobierz [arkusz danych dotyczący licencjonowania usługi Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) ze strony **Funkcje**.

## Czy klient usługi Azure Information Protection służy wyłącznie do obsługi subskrypcji, które obejmują klasyfikowanie i etykietowanie?
<a id="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling" class="xliff"></a>

Nie. Choć większość prezentacji i pokazów poświęconych klientowi usługi Azure Information Protection pokazuje obsługę klasyfikacji i etykietowania, to z usługi tej można korzystać również w odniesieniu do subskrypcji obejmujących wyłącznie ochronę z użyciem usługi Azure Rights Management.

Po zainstalowaniu klienta usługi Azure Information Protection dla systemu Windows bez zasad usługi Azure Information Protection klient automatycznie działa w [trybie tylko do ochrony](../rms-client/client-protection-only-mode.md). W tym trybie użytkownicy mogą łatwo stosować szablony usługi Rights Management oraz uprawnienia niestandardowe. W przypadku wykupienia w późniejszym czasie subskrypcji, która obejmuje funkcje klasyfikacji i etykietowania, klient automatycznie przełączy się do trybu standardowego po pobraniu zasad usługi Azure Information Protection.

Zalecamy, aby użytkownicy korzystający z aplikacji RMS sharing dla systemu Windows zrezygnowali z tego rozwiązania na rzecz usługi Azure Information Protection. Obsługa aplikacji RMS sharing będzie dostępna wyłącznie do 31 stycznia 2018 r. Zachęcamy do zapoznania się z tematem [Zadania, które były wykonywane w aplikacji RMS sharing](../rms-client/upgrade-client-app.md), który zawiera informacje przydatne w okresie przejściowym.

## Czy usługa Azure Information Protection obsługuje scenariusze lokalne i hybrydowe?
<a id="does-azure-information-protection-support-on-premises-and-hybrid-scenarios" class="xliff"></a>

Tak. Mimo, że usługa Azure Information Protection jest rozwiązaniem opartym na chmurze, może służyć do klasyfikacji, etykietowania oraz ochrony dokumentów i wiadomości e-mail, które są przechowywane lokalnie oraz w chmurze.

Jeśli używasz programu Exchange Server, SharePoint Server oraz serwerów plików systemu Windows, możesz wdrożyć [łącznik usługi Rights Management](../deploy-use/deploy-rms-connector.md), by serwery te lokalne mogły używać usługi Azure Rights Management do ochrony wiadomości e-mail i dokumentów. Można także przeprowadzić synchronizację i federację kontrolerów domeny usługi Active Directory z usługą Azure AD, aby usprawnić środowisko uwierzytelniania dla użytkowników, na przykład za pomocą programu [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Usługa Azure Rights Management automatycznie generuje certyfikaty XrML i zarządza nimi zgodnie z wymaganiami, dlatego nie korzysta z lokalnej infrastruktury kluczy publicznych. Aby uzyskać więcej informacji o używaniu certyfikatów przez usługę Azure Rights Management, zobacz sekcję [Wskazówki dotyczące działania usługi Azure RMS: pierwsze użycie, ochrona zawartości, zużycie zawartości](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) w artykule [Jak działa usługa Azure RMS?](../understand-explore/how-does-it-work.md).

## Podobno nowa wersja ma być wkrótce dostępna dla usługi Azure Information Protection — kiedy zostanie ona wydana?
<a id="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released" class="xliff"></a>

Dokumentacja techniczna nie zawiera informacji o kolejnych wersjach. W przypadku tego typu informacji i zapowiedzi dotyczących wersji zapoznaj się z [blogiem dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services) i pobierz najnowsze aktualizacje kanału [Dan Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy) w serwisie Twitter. Jeśli interesuje Cię wersja pakietu Office, sprawdź również [blog dotyczący pakietu Office](https://blogs.office.com/).

## Gdzie można znaleźć dodatkowe informacje na temat usługi Azure Information Protection dotyczące na przykład kwestii prawnych oraz związanych ze zgodnością i umowami SLA?
<a id="where-can-i-find-supporting-information-for-azure-information-protectionsuch-as-legal-compliance-and-slas" class="xliff"></a>

Zobacz [Zgodność i informacje dodatkowe dotyczące usługi Azure Information Protection](../understand-explore/compliance.md).

## Jak zgłosić problem lub wysłać opinię dotyczącą usługi Azure Information Protection?
<a id="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection" class="xliff"></a>

Aby skorzystać z pomocy technicznej, użyj standardowych kanałów pomocy lub [skontaktuj się z pomocą techniczną firmy Microsoft](information-support.md#to-contact-microsoft-support).

Aby przekazać opinie, w tym sugestie dotyczące ulepszeń i nowych funkcji, w aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** kliknij przycisk **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **Prześlij opinię**. Spowoduje to otwarcie wiadomości e-mail, która zostanie wysłana do zespołu ochrony informacji. Zachęcamy także do kontaktowania się z naszymi inżynierami za pośrednictwem [strony usługi Azure Information Protection w witrynie Yammer](https://www.yammer.com/askipteam/). 

## Co należy zrobić, jeśli mojego pytania nie ma na tej liście?
<a id="what-do-i-do-if-my-question-isnt-here" class="xliff"></a>

Przejrzyj najpierw często zadawane pytania dotyczące klasyfikacji i etykietowania lub ochrony danych. Usługa Azure Rights Management (Azure RMS) udostępnia technologię ochrony danych dla usługi Azure Information Protection i może być używana razem z funkcjami klasyfikacji i etykietowania lub bez nich: 

- [Często zadawane pytania dotyczące klasyfikacji i etykietowania](faqs-infoprotect.md)

- [Często zadawane pytania dotyczące ochrony danych](faqs-rms.md)

W przypadku nieznalezienia odpowiedzi na pytanie skorzystaj z linków i zasobów wymienionych w artykule [Informacje i pomoc techniczna dla usługi Azure Information Protection](information-support.md).

Istnieją także często zadawane pytania sformułowane pod kątem użytkowników końcowych:

- [Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android](../rms-client/mobile-app-faq.md)

- [Często zadawane pytania dotyczące aplikacji RMS sharing dla komputerów Mac i telefonów Windows Phone](https://technet.microsoft.com/dn451248)

- [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Rights Management dla systemu Windows](https://technet.microsoft.com/dn467883)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]

