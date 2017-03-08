---
title: "Często zadawane pytania dotyczące usługi Azure Information Protection"
description: "Niektóre często zadawane pytania dotyczące usługi Azure Information Protection i jej usługi ochrony danych, Azure Rights Management (Azure RMS)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/24/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 37ce3f1596878e28962119faef22bc1c61a067f8
ms.openlocfilehash: 0bb42f7ec5f2c1768c9eaaa7890b8b46853abd99
ms.lasthandoff: 02/25/2017


---

# <a name="frequently-asked-questions-for-azure-information-protection"></a>Często zadawane pytania dotyczące usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Masz pytanie dotyczące usługi Azure Information Protection lub usługi Azure Rights Management (Azure RMS)? Zobacz, czy nie znajdziesz tutaj odpowiedzi.

Te strony zawierające często zadawane pytania będą regularnie aktualizowane, a nowe informacje będą publikowane w comiesięcznych ogłoszeniach o aktualizacji dokumentacji na [blogu dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services).

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Na czym polega różnica między usługą Azure Information Protection i usługą Azure Rights Management?

Usługa Azure Information Protection udostępnia funkcje klasyfikacji, etykietowania i ochrony dokumentów i wiadomości e-mail organizacji. Ta technologia ochrony korzysta z usługi Azure Rights Management; która jest obecnie składnikiem usługi Azure Information Protection.

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Jaka subskrypcja jest potrzebna do korzystania z usługi Azure Information Protection i jakie funkcje obejmuje ta subskrypcja?
Zapoznaj się z [informacjami o subskrypcji](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) i [listą funkcji](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection. 

Jeśli masz subskrypcję usługi Office 365 obejmującą usługę Rights Management, pobierz [arkusz danych dotyczący licencjonowania usługi Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) ze strony **Funkcje**.

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Czy usługa Azure Information Protection obsługuje scenariusze lokalne i hybrydowe?

Tak. Mimo, że usługa Azure Information Protection jest rozwiązaniem opartym na chmurze, może służyć do klasyfikacji, etykietowania oraz ochrony dokumentów i wiadomości e-mail, które są przechowywane lokalnie oraz w chmurze.

Jeśli używasz programu Exchange Server, SharePoint Server oraz serwerów plików systemu Windows, możesz wdrożyć [łącznik usługi Rights Management](../deploy-use/deploy-rms-connector.md), by serwery te lokalne mogły używać usługi Azure Rights Management do ochrony wiadomości e-mail i dokumentów. Można także przeprowadzić synchronizację i federację kontrolerów domeny usługi Active Directory z usługą Azure AD, aby usprawnić środowisko uwierzytelniania dla użytkowników, na przykład za pomocą programu [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Usługa Azure Rights Management automatycznie generuje certyfikaty XrML i zarządza nimi zgodnie z wymaganiami, dlatego nie korzysta z lokalnej infrastruktury kluczy publicznych. Aby uzyskać więcej informacji o używaniu certyfikatów przez usługę Azure Rights Management, zobacz sekcję [Wskazówki dotyczące działania usługi Azure RMS: pierwsze użycie, ochrona zawartości, zużycie zawartości](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) w artykule [Jak działa usługa Azure RMS?](../understand-explore/how-does-it-work.md).

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Podobno nowa wersja ma być wkrótce dostępna dla usługi Azure Information Protection — kiedy zostanie ona wydana?

Dokumentacja techniczna nie zawiera informacji o kolejnych wersjach. W przypadku tego typu informacji i zapowiedzi dotyczących wersji zapoznaj się z [blogiem dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services) i pobierz najnowsze aktualizacje kanału [Dan Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy) w serwisie Twitter. Jeśli interesuje Cię wersja pakietu Office, sprawdź również [blog dotyczący pakietu Office](https://blogs.office.com/).

## <a name="where-can-i-find-supporting-information-for-azure-information-protectionsuch-as-legal-compliance-and-slas"></a>Gdzie można znaleźć dodatkowe informacje na temat usługi Azure Information Protection dotyczące na przykład kwestii prawnych oraz związanych ze zgodnością i umowami SLA?

Zobacz [Zgodność i informacje dodatkowe dotyczące usługi Azure Information Protection](../understand-explore/compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Jak zgłosić problem lub wysłać opinię dotyczącą usługi Azure Information Protection?

Aby skorzystać z pomocy technicznej, użyj standardowych kanałów pomocy lub [skontaktuj się z pomocą techniczną firmy Microsoft](information-support.md#to-contact-microsoft-support).

Aby przekazać opinie, w tym sugestie dotyczące ulepszeń i nowych funkcji, w aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** kliknij przycisk **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **Wyślij opinię**. Spowoduje to wysłanie wiadomości e-mail do zespołu usługi Information Protection i automatyczne dołączenie plików dziennika z Twojego komputera. 

Zachęcamy także do kontaktowania się z naszymi inżynierami za pośrednictwem [strony usługi Azure Information Protection w witrynie Yammer](https://www.yammer.com/askipteam/). 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>Co należy zrobić, jeśli mojego pytania nie ma na tej liście?

Przejrzyj najpierw często zadawane pytania dotyczące klasyfikacji i etykietowania lub ochrony danych. Usługa Azure Rights Management (Azure RMS) udostępnia technologię ochrony danych dla usługi Azure Information Protection i może być używana razem z funkcjami klasyfikacji i etykietowania lub bez nich: 

- [Często zadawane pytania dotyczące klasyfikacji i etykietowania](faqs-infoprotect.md)

- [Często zadawane pytania dotyczące ochrony danych](faqs-rms.md)

W przypadku nieznalezienia odpowiedzi na pytanie skorzystaj z linków i zasobów wymienionych w artykule [Informacje i pomoc techniczna dla usługi Azure Information Protection](information-support.md).

Istnieją także często zadawane pytania sformułowane pod kątem użytkowników końcowych:

- [Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android](../rms-client/mobile-app-faq.md)

- [Często zadawane pytania dotyczące aplikacji RMS sharing dla komputerów Mac i telefonów Windows Phone](https://technet.microsoft.com/dn451248)

- [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Rights Management dla systemu Windows](https://technet.microsoft.com/dn467883)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


