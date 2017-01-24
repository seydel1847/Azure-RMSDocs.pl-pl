---
title: "Aplikacja RMS sharing&colon; instalacja i konfiguracja dla klientów | Azure Information Protection"
description: "Informacje dla administratorów dotyczące wdrażania aplikacji Rights Management (RMS) sharing na komputerach z systemem Windows i urządzeniach przenośnych."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: b9af5dc3-73d4-4147-b7ef-f6803b0d5216
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 0d15a232bc1f0b1bce94e48c7e9c6f6b9419b5dd


---

# <a name="rights-management-sharing-application-installation-and-configuration-for-clients"></a>Aplikacja do udostępniania usługi Rights Management: instalacja i konfiguracja dla klientów

>*Dotyczy: Azure Information Protection, Office 365*

Aplikacja Rights Management (RMS) sharing jest wymagana do użycia usługi Azure Rights Management z pakietem Office 2010 na komputerach klienckich i jest zalecana dla wszystkich komputerów i urządzeń przenośnych, które obsługują usługę Azure Rights Management w ramach usługi Azure Information Protection. Aplikacja RMS sharing integruje się z aplikacjami pakietu Office, instalując dodatek dla pakietu Office ułatwiający użytkownikom ochronę plików i wiadomości e-mail bezpośrednio z poziomu wstążki. Zapewnia ona również ogólną ochronę typów plików, dla których usługa Azure Rights Management nie zapewnia natywnej ochrony, oraz witrynę do śledzenia dokumentów umożliwiającą użytkownikom śledzenie i odwoływanie chronionych plików.

## <a name="the-rms-sharing-application-for-windows-installation-and-configuration"></a>Aplikacja RMS sharing dla systemu Windows: instalacja i konfiguracja
Aby zainstalować i skonfigurować aplikację do udostępniania usługi RMS dla systemu Windows dla wdrożenia w przedsiębiorstwie, skorzystaj z [Przewodnika administratora aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-admin-guide.md).

> [!TIP]
> Jeśli chcesz szybko zainstalować i przetestować aplikację do udostępniania usługi RMS na jednym komputerze, zobacz [Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](../rms-client/install-sharing-app.md) w [Podręczniku użytkownika aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-user-guide.md).

## <a name="the-rms-sharing-application-for-mobile-platforms-installation-and-management"></a>Aplikacja RMS sharing dla platform urządzeń przenośnych: instalacja i zarządzanie
Aby zainstalować aplikację RMS sharing dla platform urządzeń przenośnych, możesz pobrać odpowiednią aplikację przy użyciu linków na [stronie usługi Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970). Aby używać usługi Azure Rights Management z tą aplikacją, nie trzeba nic konfigurować.

> [!NOTE]
> Aplikacja RMS sharing dla systemów iOS i Android została obecnie zastąpiona przez aplikację Azure Information Protection.

**Jeśli masz konto w usłudze Microsoft Intune**: aplikacja Azure Information Protection obejmuje zestaw Software Development Kit aplikacji w usłudze Microsoft Intune, więc w przypadku rejestrowania urządzeń z systemami iOS i Android w usłudze Intune można wdrożyć aplikację Azure Information Protection i zarządzać nią dla tych urządzeń. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i wdrażanie zasad zarządzania aplikacjami mobilnymi w konsoli usługi Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) w dokumentacji usługi Intune. W kroku 2 postępuj zgodnie z instrukcjami, aby opublikować aplikację zarządzaną przez zasady.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]





<!--HONumber=Jan17_HO4-->


