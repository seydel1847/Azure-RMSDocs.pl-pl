---
title: Wymagania platformy Azure AD dla usługi Azure Information Protection — AIP
description: Identyfikowanie wymagań usługi Azure AD dotyczących używania usługi Azure Information Protection w celu pomyślnego uwierzytelniania użytkowników.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d52b6fe3c290a6a012d66a39f60633cfb3e08504
ms.sourcegitcommit: 5b4eb0e17fb831d338d8c25844e9e6f4ca72246d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53173353"
---
# <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Wymagania usługi Azure Active Directory dotyczące usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Musi mieć katalog usługi Azure AD, aby używać usługi Azure Information Protection. Używasz konta z tego katalogu do logowania w witrynie Azure Portal, gdzie, na przykład, można skonfigurować i zarządzać etykiety usługi Azure Information Protection i szablony usługi Azure Rights Management.

Jeśli masz subskrypcję obejmującą usługę Azure Information Protection bądź Azure Rights Management, katalogiem usługi Azure AD jest automatycznie utworzone automatycznie w razie potrzeby.  

Aby uzyskać więcej informacji na temat usługi Azure AD, zobacz [co to jest katalog usługi Azure AD?](/azure/active-directory/fundamentals/active-directory-whatis)

Do integracji katalogu usługi Azure AD z lokalnymi lasami usługi AD, zobacz [integrowanie lokalnych domen Active Directory z usługą Azure Active Directory](/azure/architecture/reference-architectures/identity/azure-ad).

### <a name="scenarios-that-have-specific-requirements"></a>Scenariusze, które wiążą się z określonymi wymaganiami 

Komputery z zainstalowanym pakietem Office 2010: 

- Na potrzeby uwierzytelniania w usłudze Azure Information Protection oraz w powiązanej usłudze ochrony danych Azure Rights Management takie komputery wymagają użycia [klienta usługi Azure Information Protection](./rms-client/aip-client.md) (zalecane rozwiązanie) lub [aplikacji do udostępniania usługi Rights Management dla systemu Windows](./rms-client/sharing-app-windows.md).

- W przypadku kont federacyjnych (na przykład w warunkach użycia usługi AD FS) wymagane jest zastosowanie uwierzytelniania zintegrowanego systemu Windows. W tym scenariuszu uwierzytelnianie oparte na formularzach nie umożliwi uwierzytelnienia użytkowników w ramach usługi Azure Information Protection.

Obsługiwanie uwierzytelniania opartego na certyfikacie:

- Aplikacje Azure Information Protection dla systemów iOS i Android obsługują uwierzytelnianie oparte na certyfikatach. Instrukcje dotyczące konfigurowania uwierzytelniania opartego na certyfikatach znajdują się w temacie [Get started with certificate-based authentication in Azure Active Directory](/azure/active-directory/active-directory-certificate-based-authentication-get-started) (Wprowadzenie do uwierzytelniania opartego na certyfikatach w usłudze Azure Active Directory).

Wartość nazwy UPN użytkowników nie odpowiada ich adresowi e-mail:

- Ta konfiguracja nie jest zalecana. Jeśli nie możesz zmienić nazwy UPN, skonfiguruj alternatywny identyfikator logowania dla użytkowników i poinformuj ich, jak mają logować się do pakietu Office przy użyciu tej alternatywnej nazwy logowania. Aby uzyskać więcej informacji, zobacz artykuły [Konfigurowanie alternatywnego identyfikatora logowania](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id) i [Aplikacje pakietu Office okresowo monitują o poświadczenia usług SharePoint Online, OneDrive i Lync Online](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online).
    
    Jeśli nazwa domeny w wartości nazwy UPN jest domeną zweryfikowaną dla dzierżawy, dodaj wartość nazwy UPN użytkownika jako inny adres e-mail do atrybutu proxyAddresses usługi Azure AD. Dzięki temu użytkownik może być autoryzowany w usłudze Azure Rights Management, jeśli jego wartość nazwy UPN została określona w momencie udzielania praw użytkowania. Aby uzyskać więcej informacji na ten temat oraz na temat sposobu autoryzowania kont użytkowników, zobacz artykuł [Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection](prepare.md).

Urządzenia przenośne lub komputery Mac, które przeprowadzają uwierzytelnianie lokalne za pomocą usług AD FS lub odpowiednika dostawcy uwierzytelniania:

- Należy użyć usług AD FS na serwerze z minimalną wersją **systemu Windows Server 2012 R2**, lub alternatywnego dostawcy uwierzytelniania obsługujące protokół OAuth 2.0.

## <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>Uwierzytelnianie wieloskładnikowe i usługa Azure Information Protection
Aby używać uwierzytelniania wieloskładnikowego z usługą Azure Information Protection, należy spełnić co najmniej jedno z następujących wymagań:

-   Office 2013 (minimalna wersja):

    -   Jeśli masz pakiet Office 2013, konieczne może się okazać zainstalowanie dodatkowej aktualizacji do obsługi biblioteki Active Directory Authentication Library (ADAL). Na przykład [aktualizacja pakietu Office 2013 (KB3054853) z 9 czerwca 2015 r](https://support.microsoft.com/kb/3054853). Aby uzyskać więcej informacji na temat tej aktualizacji i sposobu wdrażania logowania opartego na bibliotece ADAL (Active Directory Authentication Library) w pakiecie Office 2013 w ramach nowoczesnego uwierzytelniania, zobacz wpis dotyczący [anonsowania publicznej wersji nowoczesnego uwierzytelniania w pakiecie Office 2013](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) na blogu pakietu Office.

- Klient usługi Azure Information Protection:

    - [Klient usługi Azure Information Protection](./rms-client/aip-client.md) dla systemów Windows, iOS i Android zawsze obsługiwał uwierzytelnianie wieloskładnikowe od momentu swojej premiery. Nie jest wymagana żadna wersja minimalna. 

-   Aplikacja do udostępniania usługi Rights Management dla systemu Windows:

    - Musisz zainstalować minimalną wersję 1.0.1908.0 (numer wersji można sprawdzić w Panelu sterowania, przechodząc do opcji Programy i funkcje). Aplikacja RMS sharing została obecnie zastąpiona przez klienta usługi Azure Information Protection. Aby uzyskać więcej informacji o aplikacji do udostępniania, zobacz artykuł [Aplikacja do udostępniania usługi Rights Management dla systemu Windows](./rms-client/sharing-app-windows.md).

-   Aplikacja do udostępniania usługi Rights Management dla urządzeń przenośnych i komputerów Mac:

    -   Upewnij się, że zainstalowano najnowszą wersję. Obsługa usługi MFA została dodana w wydaniu aplikacji RMS sharing z września 2015 r.

Następnie skonfiguruj rozwiązanie MFA:

-   W przypadku dzierżaw zarządzanych przez firmę Microsoft (masz usługę Azure Active Directory lub Office 365):

    - Skonfiguruj usługę Azure MFA, aby wymusić jej użycie przez użytkowników. Aby uzyskać instrukcje, zobacz artykuł [Wprowadzenie do korzystania z usługi Azure Multi-Factor Authentication w chmurze](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) w dokumentacji usługi Multi-Factor Authentication.

        Aby uzyskać więcej informacji na temat usługi Azure MFA, zobacz artykuł [Co to jest usługa Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication)

- W przypadku dzierżaw federacyjnych (serwery federacyjne działają lokalnie):

    - Skonfiguruj serwery federacyjne dla usługi Azure Active Directory lub Office 365. Jeśli na przykład używasz usług AD FS, zobacz artykuł [Konfigurowanie dodatkowych metod uwierzytelniania dla usług AD FS](https://technet.microsoft.com/library/dn758113.aspx) w witrynie TechNet.

        Aby uzyskać więcej informacji na temat tego scenariusza, zobacz wpis [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) (Praca z usługą Office 365 — usprawniony program tożsamości) na blogu pakietu Office.

Łącznik usługi Rights Management i skaner usługi Azure Information Protection nie obsługują uwierzytelniania Wieloskładnikowego. Jeśli wdrożono łącznik lub skaner następujących kont nie może wymagać uwierzytelniania Wieloskładnikowego:

- Konto, które instaluje i konfiguruje Łącznik.

- Konto główne usługi w usłudze Azure AD **Aadrm_S-1-7-0**, który tworzy łącznik.
 
- Konta usługi, która działa skaner.

## <a name="next-steps"></a>Następne kroki
Aby sprawdzić pozostałe wymagania, zobacz [Requirements for Azure Information Protection](requirements.md) (Wymagania dotyczące usługi Azure Information Protection).

