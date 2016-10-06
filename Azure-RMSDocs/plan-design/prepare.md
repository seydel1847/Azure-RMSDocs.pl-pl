---
title: "Przygotowanie do ochrony za pomocą usługi Azure Rights Management | Azure Information Protection"
description: "Sprawdź, czy wszystko jest gotowe do użycia usługi Azure Rights Management, aby organizacja mogła chronić dokumenty i wiadomości e-mail."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 46db6ef6f65a06c42909252cf99884cc5eaaefe4
ms.openlocfilehash: 5a3df821c70b8cd308f8fb8cc94ee0cff069a3d9


---

# Przygotowanie do korzystania z usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Przed wdrożeniem usługi Azure Information Protection w organizacji upewnij się, że następujące wymagania zostały spełnione:

-   Konta użytkowników i grupy w chmurze tworzone ręcznie lub automatycznie i zsynchronizowane z usługami domenowymi Active Directory (AD DS).

    Podczas synchronizowania lokalnych kont i grup nie wszystkie atrybuty wymagają zsynchronizowania. Aby uzyskać listę atrybutów, które należy zsynchronizować dla usługi Azure Rights Management używanej przez usługę Azure Information Protection, zobacz [sekcję dotyczącą usługi Azure RMS](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) w dokumentacji usługi Azure Active Directory. W celu ułatwienia wdrażania zalecamy połączenie katalogów lokalnych z usługą Azure Active Directory przy użyciu programu [Azure AD Connect](/active-directory/active-directory-aadconnectsync-whatis). Można jednak użyć dowolnej metody synchronizacji pozwalającej uzyskać ten sam rezultat.

-   Grupy obsługujące pocztę w chmurze, które będą używane z usługą Azure Information Protection. Mogą to być grupy wbudowane lub ręcznie utworzone grupy zawierające użytkowników, którzy będą korzystać z chronionych dokumentów i wiadomości e-mail.

    Użytkownicy usługi Exchange Online mogą tworzyć grupy obsługujące pocztę i korzystać z nich przy użyciu centrum administracyjnego programu Exchange. W przypadku dostępności lokalnej usługi AD DS, jeśli planowana jest synchronizacja do usługi Azure AD, można utworzyć grupy zabezpieczeń lub grupy dystrybucyjne z obsługą wiadomości e-mail i użyć ich.

## Aktywowanie usługi Rights Management w celu ochrony danych
Gdy wszystko jest gotowe do uruchomienia ochrony dokumentów i wiadomości e-mail, aktywuj usługę Rights Management, aby włączyć tę technologię. Aby uzyskać więcej informacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).






<!--HONumber=Sep16_HO4-->


