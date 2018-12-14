---
title: Klient usługi Azure Information Protection &colon; instalowanie i konfigurowanie
description: Informacje dla administratorów dotyczące wdrażania klienta usługi Azure Information Protection na komputerach z systemem Windows i urządzeniach przenośnych.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: b1a19ae7-db26-40da-9e21-6620af3d0b02
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9dfe8c6921b50faddb6ee8f24c39fe6f33e1fd4d
ms.sourcegitcommit: 5b4eb0e17fb831d338d8c25844e9e6f4ca72246d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53173319"
---
# <a name="azure-information-protection-client-installation-and-configuration-for-clients"></a>Klient usługi Azure Information Protection: Instalacja i konfiguracja dla klientów

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Na komputerach z uruchomionym pakietem Office 2010 na potrzeby uwierzytelniania w usługach Azure Rights Management i Azure Information Protection jest wymagany klient usługi Azure Information Protection (lub aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management). Instalacja tego klienta jest zalecana także w przypadku wszystkich komputerów z systemem Windows oraz urządzeń z systemami iOS i Android obsługującymi usługi Azure Rights Management i Azure Information Protection. 

Klient usługi Azure Information Protection integruje się z aplikacjami pakietu Office, instalując dodatek dla pakietu Office ułatwiający użytkownikom dodawanie do plików etykiet oraz ochronę plików i wiadomości e-mail bezpośrednio ze wstążki pakietu Office. W ramach tego klienta są dostępne opcje z zakresu oznaczania etykietami oraz ochrony rodzajów plików, dla których usługa Azure Rights Management nie zapewnia natywnej ochrony, przeglądarka plików objętych ochroną oraz witryna do śledzenia dokumentów, która umożliwia użytkownikom śledzenie i odwoływanie chronionych plików.

## <a name="the-azure-information-protection-client-for-windows-installation-and-configuration"></a>Klient usługi Azure Information Protection dla Windows: Instalacja i Konfiguracja
Informacje o instalacji i konfiguracji klienta dla przedsiębiorstw w systemie Windows znajdują się w [podręczniku administratora usługi Azure Information Protection](./rms-client/client-admin-guide.md).

> [!TIP]
> Aby szybko zainstalować i przetestować klienta usługi Azure Information Protection dla pojedynczego komputera, zobacz temat [Pobieranie i instalowanie klienta usługi Azure Information Protection](./rms-client/install-client-app.md) w [podręczniku użytkownika klienta usługi Azure Information Protection](./rms-client/client-user-guide.md).

## <a name="the-azure-information-protection-client-for-ios-and-android-installation-and-management"></a>Klient usługi Azure Information Protection dla systemów iOS i Android: Instalacja i zarządzanie
Aby zainstalować klienta usługi Azure Information Protection dla tych popularnych platform przenośnych, możesz pobrać odpowiednią aplikację, korzystając z linków na [stronie usługi Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970). Nie jest wymagana żadna konfiguracja.

> [!NOTE]
> W przypadku komputerów Mac i urządzeń z systemem Windows Phone linki z tej strony umożliwiają pobranie aplikacji RMS sharing dla urządzeń przenośnych. Te urządzenia nie obsługują obecnie klienta usługi Azure Information Protection.

**Jeśli masz Microsoft Intune**: Aplikacja Azure Information Protection zawiera Microsoft Intune App Software Development Kit, gdy systemami iOS i Android są rejestrowane przez usługę Intune, można wdrożyć i zarządzać przeglądarka usługi Azure Information Protection dla tych urządzeń. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i wdrażanie zasad zarządzania aplikacjami mobilnymi w konsoli usługi Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) w dokumentacji usługi Intune. W kroku 2 postępuj zgodnie z instrukcjami, aby opublikować aplikację zarządzaną przez zasady.



