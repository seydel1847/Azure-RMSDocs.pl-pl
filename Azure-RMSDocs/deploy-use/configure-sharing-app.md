---
# required metadata

title: Aplikacja do udostępniania usługi Rights Management&colon; instalacja i konfiguracja dla klientów | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b9af5dc3-73d4-4147-b7ef-f6803b0d5216

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Aplikacja do udostępniania usługi Rights Management: instalacja i konfiguracja dla klientów

*Dotyczy usług: Azure Rights Management, Office 365*

Aplikacja do udostępniania usługi Rights Management (RMS) jest wymagana do użycia usługi Azure RMS z pakietem Office 2010 na komputerach klienckich i jest zalecana dla wszystkich komputerów i urządzeń przenośnych, które obsługują usługę Azure RMS. Aplikacja RMS sharing integruje się z aplikacjami pakietu Office, instalując dodatek dla pakietu Office ułatwiający użytkownikom ochronę plików i wiadomości e-mail bezpośrednio z poziomu wstążki. Zapewnia ona również ogólną ochronę typów plików, dla których usługa Azure RMS nie zapewnia natywnej ochrony, oraz korzystanie z witryny śledzenia dokumentów umożliwiającej użytkownikom śledzenie i odwoływanie chronionych plików.

## Aplikacja RMS sharing dla systemu Windows: instalacja i konfiguracja
Aby zainstalować i skonfigurować aplikację RMS sharing dla systemu Windows dla wdrożenia w przedsiębiorstwie, skorzystaj z [Podręcznika użytkownika aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-admin-guide.md)..

> [!TIP]
> Jeśli chcesz szybko zainstalować i przetestować aplikację RMS sharing na jednym komputerze, zobacz [Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](../rms-client/install-sharing-app.md) w [Podręczniku użytkownika aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-user-guide.md)..

## Aplikacja RMS sharing dla platform urządzeń przenośnych: instalacja i zarządzanie
Aby zainstalować aplikację RMS sharing dla platform urządzeń przenośnych, możesz pobrać odpowiednią aplikację przy użyciu linków na [stronie usługi Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970). Aby używać usługi Azure RMS z tą aplikacją, nie trzeba nic konfigurować.

**Jeśli masz usługę Microsoft Intune**: aplikacja RMS sharing zawiera zestaw SDK (Software Development Kit) aplikacji usługi Microsoft Intune, dlatego dostępne są następujące opcje:

-   W przypadku urządzeń zarejestrowanych przez usługę Intune możesz wdrożyć aplikację RMS sharing i zarządzać tą aplikacją na urządzeniach z systemem iOS lub Android. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i wdrażanie zasad zarządzania aplikacjami mobilnymi w konsoli usługi Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) w dokumentacji usługi Intune. W kroku 2 postępuj zgodnie z instrukcjami, aby opublikować aplikację zarządzaną przez zasady.

-   W przypadku urządzeń, które nie zostały zarejestrowane przez usługę Intune, możesz zarządzać aplikacją RMS sharing dla urządzeń z systemem Android. Aby uzyskać więcej informacji, zobacz [Tworzenie i wdrażanie zasad zarządzania aplikacjami mobilnymi przy użyciu usługi Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)..



<!--HONumber=Apr16_HO4-->


