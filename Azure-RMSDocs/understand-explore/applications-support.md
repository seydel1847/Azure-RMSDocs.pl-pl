---
# required metadata

title: Jak aplikacje obsługują usługę Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Jak aplikacje obsługują usługę Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Poniższe informacje pozwalają lepiej zrozumieć, w jaki sposób najczęściej używane aplikacje (takie jak aplikacje pakietu Office — Word, Excel, PowerPoint i Outlook) i usługi (takie jak programy Exchange i SharePoint) użytkownika końcowego mogą korzystać z usługi Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] w celu ochrony danych organizacji. 
> [!NOTE]
> Aby sprawdzić aplikacje i wersje obsługiwane przez usługę [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS), zobacz [Wymagania dotyczące usługi Azure Rights Management](../get-started/requirements-azure-rms.md)..

W niektórych przypadkach ochrona informacji jest stosowana automatycznie, zgodnie ze skonfigurowanymi zasadami. Dotyczy to na przykład bibliotek programu SharePoint, plików klasyfikowanych i reguł transportu programu Exchange. W innych przypadkach użytkownicy muszą sami zastosować ochronę informacji z poziomu aplikacji przez wybranie szablonu lub wybranie określonych opcji. Dotyczy to na przykład sytuacji, gdy użytkownicy udostępniają plik pocztą e-mail, lub ochrony miejscowej plików przez ograniczenie dostępu lub użycia dla wybranych użytkowników lub dla użytkowników spoza organizacji.

Szablony ułatwiają użytkownikom (i administratorom, którzy konfigurują zasady) stosowanie odpowiedniego poziomu ochrony i ograniczenie dostępu do osób wewnątrz organizacji. Chociaż usługa [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] dostarcza dwa szablony domyślne, prawdopodobnie zajdzie potrzeba utworzenia szablonów niestandardowych, aby ograniczyć sytuacje, w których użytkownicy muszą określać poszczególne opcje. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md)..

W przypadkach, gdy użytkownicy muszą sami stosować ochronę informacji, należy pamiętać o udostępnieniu im instrukcji oraz wskazówek, jak i kiedy mają to robić. Instrukcje powinny być specyficzne dla aplikacji i wersji, z których użytkownicy korzystają, oraz sposobu, w jaki z nich korzystają, a wskazówki dotyczące sposobu i sytuacji stosowania ochrony informacji powinny być odpowiednie dla Twojej firmy. Aby uzyskać więcej informacji, zobacz [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](../deploy-use/help-users.md)..

Informacje o sposobach konfigurowania tych aplikacji dla usługi Azure RMS opisano w temacie [Konfigurowanie aplikacji dla usługi Azure Rights Management](../deploy-use/configure-applications.md)..

> [!TIP]
> Przykłady i zrzuty ekranu aplikacji korzystających z usługi Azure RMS można znaleźć w artykule [Azure RMS w działaniu: co widzą administratorzy i użytkownicy](what-admins-users-see.md)..

## Następne kroki

Dowiedz się więcej na temat sposobu obsługi usługi Azure RMS przez następujące aplikacje i serwery:

-   [Aplikacja RMS sharing dla systemu Windows i platform urządzeń przenośnych](sharing-app-support.md)

-   [Aplikacje i usługi pakietu Office](office-apps-services-support.md)

-   [Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików](file-server-support.md)

-   [Inne aplikacje, które obsługują interfejsy API usługi RMS](api-support.md)



<!--HONumber=Apr16_HO4-->

