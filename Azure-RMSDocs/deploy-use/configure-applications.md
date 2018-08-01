---
title: Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management — AIP
description: Instrukcje dla administratorów dotyczące konfigurowania aplikacji i usług do pracy z usługą zabezpieczającą Azure Rights Management w ramach usługi Azure Information Protection. Dotyczy to na przykład aplikacji pakietu Office, takich jak Word 2013 i Word 2010 oraz usług, takich jak Exchange Online (zasady transportu, zapobieganie utracie danych, blokowanie przesyłania dalej i szyfrowanie wiadomości) oraz SharePoint Online (biblioteki chronione).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/26/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 74797de21007667ee8f70456f3b5b3f4c559d7a0
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39370272"
---
# <a name="configuring-applications-for-azure-rights-management"></a>Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!NOTE]
> Te informacje są przeznaczone dla administratorów i doradców IT, którzy wdrożyli usługę Azure Information Protection. Jeśli szukasz pomocy dla użytkowników i informacji na temat sposobu używania funkcji usługi Rights Management dla określonej aplikacji lub sposobu otwierania pliku z ochroną praw, skorzystaj z pomocy i wskazówek dołączonych do aplikacji.
>
> Na przykład w przypadku aplikacji pakietu Office kliknij ikonę Pomoc i wprowadź terminy wyszukiwania, takie jak **Rights Management** lub **IRM**. Aby uzyskać instrukcje dotyczące klienta usługi Azure Information Protection dla komputerów z systemem Windows, zobacz [podręcznik użytkownika klienta usługi Azure Information Protection ](../rms-client/client-user-guide.md).

Po wdrożeniu usługi Azure Information Protection dla organizacji użyj następujących informacji, aby skonfigurować aplikacje i usługi oraz klienta usługi Azure Information Protection. Przykładem są aplikacje pakietu Office, takie jak Word 2016, Word 2013 i Word 2010. Dotyczy to także usług takich jak Exchange Online (zasady transportu, zapobieganie utracie danych, blokowanie przesyłania dalej i szyfrowanie wiadomości) oraz SharePoint Online (biblioteki chronione). Aby dowiedzieć się, jak wspomniane aplikacje i usługi obsługują ochronę danych w ramach usługi Azure Information Protection, zobacz temat [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md).

> [!IMPORTANT]
> Aby uzyskać informacje na temat obsługiwanych wersji i innych wymagań, zobacz [Wymagania dotyczące usługi Azure Rights Management](../get-started/requirements-azure-rms.md).

-   [Office 365: konfiguracja dla klientów i usług online](configure-office365.md)

    -   [Usługa Exchange Online: konfiguracja usługi IRM](configure-office365.md#exchange-online-irm-configuration)

    -   [SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)

- [Aplikacje pakietu Office: konfiguracja dla klientów](configure-office-apps.md)

    -   [Pakiety Office 2016 i Office 2013](configure-office-apps.md#office-2016-and-office-2013)

    -   [Pakiet Office 2010](configure-office-apps.md#office-2010)

-   [Klient usługi Azure Information Protection: instalacja i konfiguracja klienta](configure-sharing-app.md)

-   [Aplikacja do udostępniania usługi Rights Management: instalacja i konfiguracja dla klientów](configure-sharing-app.md)


Aby skonfigurować serwery lokalne, takie jak Exchange Server i SharePoint Server, zobacz [Wdrażanie łącznika usługi Azure Rights Management](deploy-rms-connector.md).

Oprócz tych aplikacji i usług istnieją inne aplikacje obsługujące interfejsy API usługi Rights Management. Do tej kategorii należą aplikacje biznesowe, które są tworzone we własnym zakresie za pomocą zestawu Rights Management SDK, i aplikacje od dostawców oprogramowania tworzone przy użyciu zestawu Rights Management SDK. W przypadku tych aplikacji postępuj zgodnie z instrukcjami dostarczonymi z aplikacją.

## <a name="next-steps"></a>Kolejne kroki
Po skonfigurowaniu aplikacji do obsługi usługi Azure Rights Management użyj [planu wdrożenia usługi Azure Information Protection](../plan-design/deployment-roadmap.md), aby sprawdzić, czy istnieją inne czynności konfiguracyjne, które należy wykonać przed wdrożeniem usługi Azure Information Protection dla użytkowników i administratorów. Jeśli nie, przydatne mogą być następujące informacje operacyjne:

- [Weryfikowanie usługi Azure Rights Management](verify.md)

- [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](help-users.md)

- [Rejestrowanie i analizowanie usługi Azure Rights Management](log-analyze-usage.md)

- [Operacje związane z kluczem dzierżawy usługi Azure Information Protection](operations-tenant-key.md)


