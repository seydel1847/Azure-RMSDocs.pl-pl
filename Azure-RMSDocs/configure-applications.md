---
title: Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management — AIP
description: Instrukcje dla administratorów dotyczące konfigurowania aplikacji i usług do pracy z usługą zabezpieczającą Azure Rights Management w ramach usługi Azure Information Protection. Dotyczy to na przykład aplikacji pakietu Office, takich jak Word 2013 i Word 2010 oraz usług, takich jak Exchange Online (zasady transportu, zapobieganie utracie danych, blokowanie przesyłania dalej i szyfrowanie wiadomości) oraz SharePoint Online (biblioteki chronione).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/31/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 99c0871d879d7326a4142b99753acfe00cd27cf5
ms.sourcegitcommit: 73b5884ee9fe8aabb1a9fc9baace64d5fd433f4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54324084"
---
# <a name="configuring-applications-for-azure-rights-management"></a>Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!NOTE]
> Te informacje są przeznaczone dla administratorów i doradców IT, którzy wdrożyli usługę Azure Information Protection. Jeśli szukasz pomocy dla użytkowników i informacji na temat sposobu używania funkcji usługi Rights Management dla określonej aplikacji lub sposobu otwierania pliku z ochroną praw, skorzystaj z pomocy i wskazówek dołączonych do aplikacji.
>
> Na przykład w przypadku aplikacji pakietu Office kliknij ikonę Pomoc i wprowadź terminy wyszukiwania, takie jak **Rights Management** lub **IRM**. Aby uzyskać instrukcje dotyczące klienta usługi Azure Information Protection dla komputerów z systemem Windows, zobacz [podręcznik użytkownika klienta usługi Azure Information Protection ](./rms-client/client-user-guide.md).

Po wdrożeniu usługi Azure Information Protection dla organizacji użyj następujących informacji, aby skonfigurować aplikacje i usługi oraz klienta usługi Azure Information Protection. Przykładem są aplikacje pakietu Office, takie jak Word 2016, Word 2013 i Word 2010. Dotyczy to także usług takich jak Exchange Online (zasady transportu, zapobieganie utracie danych, blokowanie przesyłania dalej i szyfrowanie wiadomości) oraz SharePoint Online (biblioteki chronione). Aby dowiedzieć się, jak wspomniane aplikacje i usługi obsługują ochronę danych w ramach usługi Azure Information Protection, zobacz temat [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md).

> [!IMPORTANT]
> Aby uzyskać informacje na temat obsługiwanych wersji i innych wymagań, zobacz [Wymagania dotyczące usługi Azure Rights Management](requirements.md).

-   [Office 365: Konfiguracja dla klientów i usług online](configure-office365.md)

    -   [Usługa Exchange Online: Konfiguracja usługi IRM](configure-office365.md#exchange-online-irm-configuration)

    -   [SharePoint Online i OneDrive dla firm: Konfiguracja usługi IRM](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)

- [Aplikacje pakietu Office: Konfiguracja dla klientów](configure-office-apps.md)

    -   [Pakiety Office 2016 lub Office 2013](configure-office-apps.md#office-2016-and-office-2013)

    -   [Office 2010](configure-office-apps.md#office-2010)

-   [Klient usługi Azure Information Protection: Instalacja i konfiguracja dla klientów](configure-client.md)

-   [Aplikacja do udostępniania usługi Rights Management: Instalacja i konfiguracja dla klientów](configure-sharing-app.md)


Aby skonfigurować serwery lokalne, takie jak Exchange Server i SharePoint Server, zobacz [Wdrażanie łącznika usługi Azure Rights Management](deploy-rms-connector.md).

Oprócz tych aplikacji i usług istnieją inne aplikacje obsługujące interfejsy API usługi Rights Management. Do tej kategorii należą aplikacje biznesowe, które są tworzone we własnym zakresie za pomocą zestawu Rights Management SDK, i aplikacje od dostawców oprogramowania tworzone przy użyciu zestawu Rights Management SDK. W przypadku tych aplikacji postępuj zgodnie z instrukcjami dostarczonymi z aplikacją.

## <a name="next-steps"></a>Następne kroki
Po skonfigurowaniu aplikacji do obsługi usługi Azure Rights Management użyj [planu wdrożenia usługi Azure Information Protection](deployment-roadmap.md), aby sprawdzić, czy istnieją inne czynności konfiguracyjne, które należy wykonać przed wdrożeniem usługi Azure Information Protection dla użytkowników i administratorów. Jeśli nie, przydatne mogą być następujące informacje operacyjne:

- [Weryfikowanie usługi Azure Rights Management](verify.md)

- [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](help-users.md)

- [Rejestrowanie i analizowanie usługi Azure Rights Management](log-analyze-usage.md)

- [Operacje związane z kluczem dzierżawy usługi Azure Information Protection](operations-tenant-key.md)


