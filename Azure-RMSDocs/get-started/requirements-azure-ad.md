---
title: "Wymagania dotyczące usługi Azure Active Directory | Azure Information Protection"
description: "Identyfikowanie wymagań usługi Azure AD dotyczących używania usługi Azure Information Protection w celu pomyślnego uwierzytelniania użytkowników."
author: cabailey
manager: mbaldwin
ms.date: 09/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 976281d2b1f9c87bbb0806fef98b2520772c507c
ms.openlocfilehash: 5be497b09ed1b1342747508611a1cc06ad0edf02


---

# Wymagania usługi Azure Active Directory dotyczące usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Aby korzystać z usługi Azure Information Protection, musisz mieć katalog usługi Azure AD. Możesz użyć konta organizacji w tym katalogu do logowania się do klasycznego portalu Azure, w którym można na przykład konfigurować szablony usługi Rights Management i zarządzać nimi.

Jeśli organizacja nie ma jeszcze subskrypcji platformy Azure, możesz ją uzyskać, tworząc konto do użycia na potrzeby bezpłatnej wersji próbnej: przejdź na stronę [wprowadzenia do platformy Azure](https://account.windowsazure.com/organization) i postępuj zgodnie z instrukcjami.

Więcej informacji można znaleźć w następujących zasobach dokumentacji usługi Azure Active Directory:

-   [Co to jest katalog usługi Azure AD?](/active-directory/active-directory-whatis)

-   [Jak subskrypcje platformy Azure są kojarzone z usługą Azure Active Directory?](/active-directory/active-directory-how-subscriptions-associated-directory)

Jeśli chcesz zintegrować katalog usługi Azure AD z lokalnymi lasami usługi AD, zobacz artykuł [Integrowanie tożsamości użytkownika lokalnego z usługą Azure Active Directory](/active-directory/active-directory-aadconnect).

> [!NOTE]
> Jeśli masz urządzenia przenośne lub komputery Mac, które przeprowadzają uwierzytelnianie lokalne za pomocą usług AD FS lub odpowiednika dostawcy uwierzytelniania:
> 
> -   Musisz używać usług AD FS na serwerze z minimalną wersją **Windows Server 2012 R2** lub alternatywnego dostawcy uwierzytelniania, który obsługuje protokół OAuth 2.0.

## Uwierzytelnianie wieloskładnikowe i usługa Azure Information Protection
Aby używać uwierzytelniania wieloskładnikowego z usługą Azure Information Protection, należy spełnić co najmniej jedno z następujących wymagań:

-   Office 2013 (minimalna wersja):

    -   Jeśli masz pakiet Office 2013, musisz również zainstalować [aktualizację pakietu Office 2013 (KB3054853) z 9 czerwca 2015](https://support.microsoft.com/kb/3054853). Aby uzyskać więcej informacji na temat tej aktualizacji i sposobu wdrażania logowania opartego na bibliotece ADAL (Active Directory Authentication Library) w pakiecie Office 2013 w ramach nowoczesnego uwierzytelniania, zobacz wpis dotyczący [anonsowania publicznej wersji nowoczesnego uwierzytelniania w pakiecie Office 2013](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) na blogu pakietu Office.

-   Aplikacja do udostępniania usługi Rights Management dla systemu Windows:

    -   Musisz zainstalować minimalną wersję 1.0.1908.0 (numer wersji można sprawdzić w Panelu sterowania, przechodząc do opcji Programy i funkcje). Aby uzyskać więcej informacji o aplikacji do udostępniania, zobacz artykuł [Aplikacja do udostępniania usługi Rights Management dla systemu Windows](../rms-client/sharing-app-windows.md).

-   Aplikacja do udostępniania usługi Rights Management dla urządzeń przenośnych i komputerów Mac:

    -   Upewnij się, że zainstalowano najnowszą wersję. Obsługa usługi MFA została dodana w wydaniu aplikacji RMS sharing z września 2015 r.

Następnie skonfiguruj rozwiązanie MFA:

-   W przypadku dzierżaw zarządzanych przez firmę Microsoft (masz usługę Azure Active Directory lub Office 365):

    -   Skonfiguruj usługę Azure MFA, aby wymusić jej użycie przez użytkowników. Aby uzyskać instrukcje, zobacz artykuł [Wprowadzenie do korzystania z usługi Azure Multi-Factor Authentication w chmurze](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) w dokumentacji usługi Multi-Factor Authentication.

        Aby uzyskać więcej informacji na temat usługi Azure MFA, zobacz artykuł [Co to jest usługa Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication)

-   W przypadku dzierżaw federacyjnych (serwery federacyjne działają lokalnie):

    -   Skonfiguruj serwery federacyjne dla usługi Azure Active Directory lub Office 365. Jeśli na przykład używasz usług AD FS, zobacz artykuł [Konfigurowanie dodatkowych metod uwierzytelniania dla usług AD FS](https://technet.microsoft.com/library/dn758113.aspx) w witrynie TechNet.

        Aby uzyskać więcej informacji na temat tego scenariusza, zobacz wpis [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) (Praca z usługą Office 365 — usprawniony program tożsamości) na blogu pakietu Office.

## Następne kroki
Aby sprawdzić pozostałe wymagania, zobacz [Requirements for Azure Information Protection](requirements-azure-rms.md) (Wymagania dotyczące usługi Azure Information Protection).




<!--HONumber=Sep16_HO5-->


