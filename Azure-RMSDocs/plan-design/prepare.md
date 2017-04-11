---
title: "Przygotowanie do ochrony danych za pomocą usługi Azure Rights Management — AIP"
description: "Sprawdź, czy wszystko jest gotowe do użycia usługi Azure Rights Management, aby organizacja mogła chronić dokumenty i wiadomości e-mail."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4b074f9a9a3d72b4d1ab5810b69e92b4792b0711
ms.sourcegitcommit: 16fec44713c7064959ebb520b9f0857744fecce9
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

### <a name="considerations-if-email-addresses-change"></a>Jeśli adres e-mail ulegnie zmianie

Podczas konfigurowania praw użytkowania odnoszących się do użytkowników lub grup w przypadku ich zaznaczenia według nazwy wyświetlanej następuje zapis wyboru i zostaje użyty adres e-mail danego obiektu. Jeśli adres e-mail ulegnie w późniejszym czasie zmianie, prawa użytkowania nie zostaną pomyślnie przypisane użytkownikom.

W przypadku zmiany adresów e-mail zaleca się dodanie starego adresu e-mail jako adresu e-mail serwera proxy (znanego także jako alias lub alternatywny adres e-mail) użytkownika lub grupy, dzięki czemu prawa użytkowania, które zostały przypisane wcześniej, zostaną zachowane. Jeśli wykonanie tej czynności nie jest możliwe, należy usunąć użytkownika lub grupę z konfiguracji i ponownie wybrać użytkownika lub grupę, aby zapisać zaktualizowany adres e-mail, tak aby nowo chroniona zawartość używała nowego adresu e-mail.

Użycie niestandardowych szablonów usługi Rights Management stanowi przykład sytuacji, w której można wybrać użytkowników lub grupy według nazwy wyświetlanej w celu przypisania praw użytkowania. Użytkowników lub grupy można także wybierać według ich nazwy wyświetlanej podczas konfigurowania uprawnień niestandardowych za pomocą klienta usługi Azure Information Protection.

## <a name="activate-the-rights-management-service-for-data-protection"></a>Aktywowanie usługi Rights Management w celu ochrony danych
Gdy wszystko jest gotowe do uruchomienia ochrony dokumentów i wiadomości e-mail, aktywuj usługę Rights Management, aby włączyć tę technologię. Aby uzyskać więcej informacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


