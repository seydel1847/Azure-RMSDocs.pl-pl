---
title: "Przygotowanie do ochrony danych za pomocą usługi Azure Rights Management — AIP"
description: "Sprawdź, czy wszystko jest gotowe do użycia usługi Azure Rights Management, aby organizacja mogła chronić dokumenty i wiadomości e-mail."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/24/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 034ca391c5b021333e77e8b6b9c389300e4a9da2
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="preparing-for-azure-information-protection"></a>Przygotowanie do korzystania z usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Przed wdrożeniem usługi Azure Information Protection w organizacji upewnij się, że następujące wymagania zostały spełnione:

-   Konta użytkowników i grupy w chmurze tworzone ręcznie lub automatycznie i zsynchronizowane z usługami domenowymi Active Directory (AD DS).

    Podczas synchronizowania lokalnych kont i grup nie wszystkie atrybuty wymagają zsynchronizowania. Aby uzyskać listę atrybutów, które należy zsynchronizować dla usługi Azure Rights Management używanej przez usługę Azure Information Protection, zobacz [sekcję dotyczącą usługi Azure RMS](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) w dokumentacji usługi Azure Active Directory. W celu ułatwienia wdrażania zalecamy połączenie katalogów lokalnych z usługą Azure Active Directory przy użyciu programu [Azure AD Connect](/active-directory/active-directory-aadconnectsync-whatis). Można jednak użyć dowolnej metody synchronizacji pozwalającej uzyskać ten sam rezultat.

-   Grupy obsługujące pocztę w chmurze, które będą używane z usługą Azure Information Protection. Mogą to być grupy wbudowane lub ręcznie utworzone grupy zawierające użytkowników, którzy będą korzystać z chronionych dokumentów i wiadomości e-mail.

    Użytkownicy usługi Exchange Online mogą tworzyć grupy obsługujące pocztę i korzystać z nich przy użyciu centrum administracyjnego programu Exchange. W przypadku dostępności lokalnej usługi AD DS, jeśli planowana jest synchronizacja do usługi Azure AD, można utworzyć grupy zabezpieczeń lub grupy dystrybucyjne z obsługą wiadomości e-mail i użyć ich.

### <a name="group-membership-caching"></a>Buforowanie członkostwa w grupach

Ze względu na wydajność członkostwo w grupach jest buforowane przez usługę Azure Rights Management. Oznacza to, że wszelkie zmiany członkostwa w grupach mogą zacząć obowiązywać po upływie do 3 godzin i ten okres może ulec zmianie. Pamiętaj, aby uwzględnić to opóźnienie we wszystkich zmianach i wykonywanym testowaniu w przypadku korzystania z grup w swojej konfiguracji usługi Azure Rights Management, np. w przypadku konfigurowania [szablonów niestandardowych](../deploy-use/configure-custom-templates.md) lub korzystania z grupy na potrzeby [funkcji superużytkowników](../deploy-use/configure-super-users.md). 

## <a name="activate-the-rights-management-service-for-data-protection"></a>Aktywowanie usługi Rights Management w celu ochrony danych
Gdy wszystko jest gotowe do uruchomienia ochrony dokumentów i wiadomości e-mail, aktywuj usługę Rights Management, aby włączyć tę technologię. Aby uzyskać więcej informacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


