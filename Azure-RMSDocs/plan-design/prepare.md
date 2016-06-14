---
# required metadata

title: Przygotowanie do wdrożenia usługi Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Przygotowanie do wdrożenia usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Po przystąpieniu do subskrypcji usługi w chmurze i utworzeniu organizacji za pomocą konta usługi [!INCLUDE[o365_1](../includes/o365_1_md.md)] lub usługi Azure Active Directory można włączyć usługę [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

Jednak najpierw upewnij się, że istnieją następujące elementy:

-   Konta użytkowników i grupy w chmurze tworzone ręcznie lub automatycznie i zsynchronizowane z usługami domenowymi Active Directory (AD DS).

    Podczas synchronizowania lokalnych kont i grup nie wszystkie atrybuty wymagają zsynchronizowania. Aby uzyskać listę atrybutów, które należy zsynchronizować dla usługi Azure RMS, zobacz [sekcję usługi Azure RMS](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) w dokumentacji usługi Azure Active Directory. W celu ułatwienia wdrażania zalecamy połączenie katalogów lokalnych z usługą Azure Active Directory przy użyciu programu [Azure AD Connect](/active-directory/active-directory-aadconnectsync-whatis). Można jednak użyć dowolnej metody synchronizacji pozwalającej uzyskać ten sam rezultat.

-   Grupy obsługujące pocztę w chmurze, które będą używane z usługą Rights Management. Mogą to być grupy wbudowane lub ręcznie utworzone grupy zawierające użytkowników, którzy będą korzystać z usługi Rights Management.

    Użytkownicy usługi Exchange Online mogą tworzyć grupy obsługujące pocztę i korzystać z nich przy użyciu centrum administracyjnego programu Exchange. W przypadku dostępności lokalnej usługi AD DS, jeśli planowana jest synchronizacja do usługi Azure AD, można utworzyć grupy zabezpieczeń lub grupy dystrybucyjne z obsługą wiadomości e-mail i użyć ich.

## Włączanie usługi Rights Management
Domyślnie usługa [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] jest wyłączona po utworzeniu konta usługi [!INCLUDE[o365_2](../includes/o365_2_md.md)] lub usługi Azure AD. Aby włączyć usługę [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla organizacji, musisz aktywować usługę. Aby uzyskać więcej informacji, zobacz temat [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).





<!--HONumber=Apr16_HO4-->


