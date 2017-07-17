---
title: "Wymagania dotyczące usługi Azure Active Directory dla usługi AIP"
description: "Identyfikowanie wymagań usługi Azure AD dotyczących używania usługi Azure Information Protection w celu pomyślnego uwierzytelniania użytkowników."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ac14cb491c39f57c7a0f81d71300db3917587cd9
ms.sourcegitcommit: 55c36739e1d9f3f0cf2e1777fe4302b443a49b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2017
---
# Wymagania usługi Azure Active Directory dotyczące usługi Azure Information Protection
<a id="azure-active-directory-requirements-for-azure-information-protection" class="xliff"></a>

>*Dotyczy: Azure Information Protection, Office 365*

Aby korzystać z usługi Azure Information Protection, musisz mieć katalog usługi Azure AD. Możesz użyć konta organizacji w tym katalogu do logowania się do klasycznego portalu Azure, w którym można na przykład konfigurować szablony usługi Rights Management i zarządzać nimi.

Jeśli organizacja nie ma jeszcze subskrypcji platformy Azure, możesz ją uzyskać, tworząc konto do użycia na potrzeby bezpłatnej wersji próbnej. Przejdź na stronę [Wprowadzenie do usługi Azure](https://account.windowsazure.com/organization) i postępuj zgodnie z instrukcjami.

Więcej informacji można znaleźć w następujących zasobach dokumentacji usługi Azure Active Directory:

-   [Co to jest katalog usługi Azure AD Directory?](/active-directory/active-directory-whatis)

-   [Jak subskrypcje platformy Azure są kojarzone z usługą Azure Active Directory?](/active-directory/active-directory-how-subscriptions-associated-directory)

Jeśli chcesz zintegrować katalog usługi Azure AD z lokalnymi lasami usługi AD, zobacz artykuł [Integrowanie tożsamości użytkownika lokalnego z usługą Azure Active Directory](/active-directory/active-directory-aadconnect).

### Scenariusze, które wiążą się z określonymi wymaganiami
<a id="scenarios-that-have-specific-requirements" class="xliff"></a> 

Komputery z zainstalowanym pakietem Office 2010: 

- Na potrzeby uwierzytelniania w usłudze Azure Information Protection oraz w powiązanej usłudze ochrony danych Azure Rights Management takie komputery wymagają użycia [klienta usługi Azure Information Protection](../rms-client/aip-client.md) (zalecane rozwiązanie) lub [aplikacji do udostępniania usługi Rights Management dla systemu Windows](../rms-client/sharing-app-windows.md).

- W przypadku kont federacyjnych (na przykład w warunkach użycia usługi AD FS) wymagane jest zastosowanie uwierzytelniania zintegrowanego systemu Windows. W tym scenariuszu uwierzytelnianie oparte na formularzach nie umożliwi uwierzytelnienia użytkowników w ramach usługi Azure Information Protection.

Obsługiwanie uwierzytelniania opartego na certyfikacie:

- Aplikacje Azure Information Protection dla systemów iOS i Android obsługują uwierzytelnianie oparte na certyfikatach. Instrukcje dotyczące konfigurowania uwierzytelniania opartego na certyfikatach znajdują się w temacie [Get started with certificate-based authentication in Azure Active Directory](/azure/active-directory/active-directory-certificate-based-authentication-get-started) (Wprowadzenie do uwierzytelniania opartego na certyfikatach w usłudze Azure Active Directory).

Wartość nazwy UPN użytkowników nie odpowiada ich adresowi e-mail:

- Ta konfiguracja nie jest zalecana. Jeśli nie możesz zmienić nazwy UPN, skonfiguruj alternatywny identyfikator logowania dla użytkowników i poinformuj ich, jak mają logować się do pakietu Office przy użyciu tej alternatywnej nazwy logowania. Aby uzyskać więcej informacji, zobacz artykuły [Konfigurowanie alternatywnego identyfikatora logowania](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id) i [Aplikacje pakietu Office okresowo monitują o poświadczenia usług SharePoint Online, OneDrive i Lync Online](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online).
    
    Jeśli nazwa domeny w wartości nazwy UPN jest domeną zweryfikowaną dla dzierżawy, dodaj wartość nazwy UPN użytkownika jako inny adres e-mail do atrybutu proxyAddresses usługi Azure AD. Dzięki temu użytkownik może być autoryzowany w usłudze Azure Rights Management, jeśli jego wartość nazwy UPN została określona w momencie udzielania praw użytkowania. Aby uzyskać więcej informacji na ten temat oraz na temat sposobu autoryzowania kont użytkowników, zobacz artykuł [Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection](../plan-design/prepare.md).

Urządzenia przenośne lub komputery Mac, które przeprowadzają uwierzytelnianie lokalne za pomocą usług AD FS lub za pośrednictwem innego dostawcy uwierzytelniania, którego usługi stanowią ich odpowiednik:

- Musisz używać usług AD FS na serwerze z minimalną wersją **Windows Server 2012 R2** lub alternatywnego dostawcy uwierzytelniania, który obsługuje protokół OAuth 2.0.

## Uwierzytelnianie wieloskładnikowe i usługa Azure Information Protection
<a id="multi-factor-authentication-mfa-and-azure-information-protection" class="xliff"></a>
Aby używać uwierzytelniania wieloskładnikowego z usługą Azure Information Protection, należy spełnić co najmniej jedno z następujących wymagań:

-   Office 2013 (minimalna wersja):

    -   Jeśli masz pakiet Office 2013, konieczne może się okazać zainstalowanie dodatkowej aktualizacji do obsługi biblioteki Active Directory Authentication Library (ADAL). Na przykład [aktualizacja pakietu Office 2013 (KB3054853) z 9 czerwca 2015 r.](https://support.microsoft.com/kb/3054853). Aby uzyskać więcej informacji na temat tej aktualizacji i sposobu wdrażania logowania opartego na bibliotece ADAL (Active Directory Authentication Library) w pakiecie Office 2013 w ramach nowoczesnego uwierzytelniania, zobacz wpis dotyczący [anonsowania publicznej wersji nowoczesnego uwierzytelniania w pakiecie Office 2013](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) na blogu pakietu Office.

- Klient usługi Azure Information Protection:

    - [Klient usługi Azure Information Protection](../rms-client/aip-client.md) dla systemów Windows, iOS i Android zawsze obsługiwał uwierzytelnianie wieloskładnikowe od momentu swojej premiery. Nie jest wymagana żadna wersja minimalna. 

-   Aplikacja do udostępniania usługi Rights Management dla systemu Windows:

    - Musisz zainstalować minimalną wersję 1.0.1908.0 (numer wersji można sprawdzić w Panelu sterowania, przechodząc do opcji Programy i funkcje). Aplikacja RMS sharing została obecnie zastąpiona przez klienta usługi Azure Information Protection. Aby uzyskać więcej informacji o aplikacji do udostępniania, zobacz artykuł [Aplikacja do udostępniania usługi Rights Management dla systemu Windows](../rms-client/sharing-app-windows.md).

-   Aplikacja do udostępniania usługi Rights Management dla urządzeń przenośnych i komputerów Mac:

    -   Upewnij się, że zainstalowano najnowszą wersję. Obsługa usługi MFA została dodana w wydaniu aplikacji RMS sharing z września 2015 r.

Następnie skonfiguruj rozwiązanie MFA:

-   W przypadku dzierżaw zarządzanych przez firmę Microsoft (masz usługę Azure Active Directory lub Office 365):

    - Skonfiguruj usługę Azure MFA, aby wymusić jej użycie przez użytkowników. Aby uzyskać instrukcje, zobacz artykuł [Wprowadzenie do korzystania z usługi Azure Multi-Factor Authentication w chmurze](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) w dokumentacji usługi Multi-Factor Authentication.

        Aby uzyskać więcej informacji na temat usługi Azure MFA, zobacz artykuł [Co to jest usługa Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication)

- W przypadku dzierżaw federacyjnych (serwery federacyjne działają lokalnie):

    - Skonfiguruj serwery federacyjne dla usługi Azure Active Directory lub Office 365. Jeśli na przykład używasz usług AD FS, zobacz artykuł [Konfigurowanie dodatkowych metod uwierzytelniania dla usług AD FS](https://technet.microsoft.com/library/dn758113.aspx) w witrynie TechNet.

        Aby uzyskać więcej informacji na temat tego scenariusza, zobacz wpis [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) (Praca z usługą Office 365 — usprawniony program tożsamości) na blogu pakietu Office.

Łącznik usługi Rights Management nie obsługuje uwierzytelniania wieloskładnikowego. W przypadku wdrożenia tego łącznika dla serwerów lokalnych, musisz użyć konta łącznika, które nie wymaga uwierzytelniania wieloskładnikowego.

## Następne kroki
<a id="next-steps" class="xliff"></a>
Aby sprawdzić pozostałe wymagania, zobacz [Requirements for Azure Information Protection](requirements-azure-rms.md) (Wymagania dotyczące usługi Azure Information Protection).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
