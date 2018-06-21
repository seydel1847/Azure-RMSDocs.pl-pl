---
title: Jak aplikacje obsługują usługę Azure Rights Management w Efektywnych
description: Omówienie sposobu, w jaki najczęściej używane aplikacje (takie jak aplikacje pakietu Office — Word, Excel, PowerPoint i Outlook) oraz usługi (takie jak Exchange i SharePoint) użytkownika końcowego mogą korzystać z usługi Azure Rights Management w ramach usługi Azure Information Protection w celu ochrony firmowych dokumentów i wiadomości e-mail.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: af3d103908aff785d48f70cc1cf89a7b9d17643e
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
ms.locfileid: "30207822"
---
# <a name="how-applications-support-the-azure-rights-management-service"></a>Jak aplikacje obsługują usługę Azure Rights Management

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Skorzystaj z poniższych informacji, aby lepiej zrozumieć sposób najczęściej używane przez użytkownika końcowego, aplikacje i usługi można używać usługi Azure Rights Management z usługi Azure Information Protection w celu ochrony dokumentów i wiadomości e-mail w organizacji. Te aplikacje obejmują Word, Excel, PowerPoint i Outlook. Usługi obejmują programy Exchange i SharePoint.

> [!NOTE]
> Aby sprawdzić obsługiwane przez usługę Azure Rights Management aplikacje i ich wersje, zobacz [aplikacje obsługujące technologię ochrony danych usługi Azure Rights](../get-started/requirements-applications.md).

W niektórych przypadkach usługa Azure Rights Management stosuje ochronę automatycznie, zgodnie z zasadami skonfigurowanymi przez administratorów. Dotyczy to na przykład bibliotek programu SharePoint i reguł transportu programu Exchange. W innych przypadkach użytkownicy końcowi zastosować ochronę się z poziomu ich aplikacji. Na przykład użytkownikom wybór klasyfikację etykietę, czyli skonfigurowany tak, aby zastosować ochronę, lub wybierz szablon lub wybierz konkretne opcje. Ochrony stosowany przez użytkowników jest typowe w przypadku, gdy użytkownicy ochrony udostępnianego pliku i one również ograniczanie dostępu lub użycia dla wybranych użytkowników lub dla użytkowników spoza organizacji.

Szablony ułatwiają użytkownikom (i administratorom, którzy konfigurują zasady) stosowanie odpowiedniego poziomu ochrony i ograniczenie dostępu do osób wewnątrz organizacji. Mimo że usługa Azure Rights Management jest dostarczany z dwóch domyślnych szablonów, prawdopodobnie chcesz utworzyć szablony niestandardowe, aby ograniczyć sytuacje, gdy użytkownicy i Administratorzy muszą określać poszczególne opcje. Aby uzyskać więcej informacji o szablonach, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](../deploy-use/configure-policy-templates.md).

Dla przypadków, w którym użytkownicy muszą zastosować ochronę, pamiętaj zapewnić użytkownikom instrukcje i wytyczne jak i kiedy mają to robić. Upewnij instrukcje specyficzne dla aplikacji i wersje, które korzystają z i jak ich z nich korzystać. Zawierają także wskazówki dotyczące kiedy i jak użytkownicy należy stosować ochrony, który jest odpowiedni dla Twojej firmy. Aby uzyskać więcej informacji, zobacz [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](../deploy-use/help-users.md).

Informacje o sposobach konfigurowania tych aplikacji dla usługi Azure Rights Management w ramach usługi Azure Information Protection podano w temacie [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](../deploy-use/configure-applications.md).

Z usługą Rights Management mogą być na różne sposoby zintegrowane usługi wyszukiwania. Przykład: 

- Exchange Online i Exchange Server używać po stronie usługi indeksowania, dzięki czemu chronionych wiadomości e-mail przez użytkownika są automatycznie wyświetlane w wynikach wyszukiwania. 

- SharePoint Online i SharePoint Server zastosowania ochrony usługi Rights Management do plików tylko podczas pobierania. Ta implementacja oznacza, że wyniki indeksowanie i wyszukiwanie w programie SharePoint nie dotyczy to rozwiązanie ochrony dokumentów. Jednak jeśli dokument, który ma być przechowywany w programie SharePoint i ten dokument nie powinien być zwracany w wynikach wyszukiwania, ochrona dokumentu przed przekazaniem go do programu SharePoint.

- Wyszukiwanie z pulpitu systemu Windows używa indeksu udostępnionego między różnymi użytkownikami urządzenia, tak aby zabezpieczyć dane w chronionych dokumentów, indeksowania plików chronionych. Oznacza to, że mimo że wyniki wyszukiwania nie zawierają pliki, które są chronione, można mieć pewność, że pliki zawierające poufne dane są nie być wyświetlane w wynikach wyszukiwania dla innych użytkowników, którzy mogą zalogować się do komputera lub połączenia z Komputerem. 

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej na temat każdego z poniższych aplikacji i usług obsługi usługi Azure Rights Management:

-   [Aplikacja do udostępniania usługi RMS dla systemu Windows i platform urządzeń przenośnych](sharing-app-support.md)

-   [Aplikacje i usługi pakietu Office](office-apps-services-support.md)

-   [Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików](file-server-support.md)

-   [Inne aplikacje, które obsługują interfejsy API usługi RMS](api-support.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
