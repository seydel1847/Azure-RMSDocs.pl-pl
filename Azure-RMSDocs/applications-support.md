---
title: Jak aplikacje obsługują usługę Azure Rights Management z usługi AIP
description: Omówienie sposobu, w jaki najczęściej używane aplikacje (takie jak aplikacje pakietu Office — Word, Excel, PowerPoint i Outlook) oraz usługi (takie jak Exchange i SharePoint) użytkownika końcowego mogą korzystać z usługi Azure Rights Management w ramach usługi Azure Information Protection w celu ochrony firmowych dokumentów i wiadomości e-mail.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 1b14ef6999f0852474f6f9de5eef2902f8863a8c
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305193"
---
# <a name="how-applications-support-the-azure-rights-management-service"></a>Jak aplikacje obsługują usługę Azure Rights Management

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Skorzystaj z poniższych informacji, aby lepiej zrozumieć, w jaki sposób najczęściej używane aplikacje dla użytkowników końcowych i usług przy użyciu usługi Azure Rights Management z usługi Azure Information Protection do ochrony dokumentów i wiadomości e-mail w organizacji. Aplikacje te obejmują programu Word, Excel, PowerPoint i Outlook. Usługi obejmują programy Exchange i SharePoint.

> [!NOTE]
> Aby sprawdzić obsługiwane przez usługę Azure Rights Management aplikacje i ich wersje, zobacz [aplikacje obsługujące technologię ochrony danych usługi Azure Rights](./requirements-applications.md).

W niektórych przypadkach usługa Azure Rights Management stosuje ochronę automatycznie, zgodnie z zasadami skonfigurowanymi przez administratorów. Dotyczy to na przykład bibliotek programu SharePoint i reguł transportu programu Exchange. W innych przypadkach użytkownicy końcowi muszą sami zastosować ochronę z poziomu ich aplikacji. Na przykład użytkownikom wybrać klasyfikację, etykiety to znaczy skonfigurowana pod kątem zastosowania ochrony, lub wybierz szablon lub wybierz konkretne opcje. Ochrona stosowana przez użytkowników jest typowa, gdy użytkownicy ochrony udostępnianego pliku i one również ograniczyć dostęp lub możliwość użycia dla wybranych użytkowników lub dla użytkowników spoza organizacji.

Szablony ułatwiają użytkownikom (i administratorom, którzy konfigurują zasady) stosowanie odpowiedniego poziomu ochrony i ograniczenie dostępu do osób wewnątrz organizacji. Mimo że usługę Azure Rights Management zawiera dwa szablony domyślne, prawdopodobnie zajdzie potrzeba utworzenia szablonów niestandardowych, aby ograniczyć sytuacje, użytkownicy i Administratorzy muszą określać poszczególne opcje. Aby uzyskać więcej informacji na temat szablonów, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md).

Dla przypadków, w których użytkownicy muszą sami zastosować ochronę, należy koniecznie udostępnieniu im instrukcji oraz wskazówek jak i kiedy mają to robić. Wprowadź instrukcje specyficzne dla aplikacji i wersji, które używają i jak ich używać ich. Zawierają także wskazówki dotyczące kiedy i w jaki sposób użytkownicy stosuje ochrony, która jest odpowiednia dla Twojej firmy. Aby uzyskać więcej informacji, zobacz [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](help-users.md).

Informacje o sposobach konfigurowania tych aplikacji dla usługi Azure Rights Management w ramach usługi Azure Information Protection podano w temacie [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](configure-applications.md).

Z usługą Rights Management mogą być na różne sposoby zintegrowane usługi wyszukiwania. Przykład: 

- Exchange Online i Exchange Server używać indeksowania po stronie usługi, tak aby chronione wiadomości e-mail przez użytkownika są automatycznie wyświetlane w wynikach wyszukiwania. 

- SharePoint Online i SharePoint Server dotyczą plików tylko podczas pobierania ochrony usługi Rights Management. Ta implementacja oznacza, że wyniki indeksowanie i wyszukiwanie w programie SharePoint nie dotyczy to rozwiązanie ochrony dokumentów. Jednakże jeśli dokument, który ma być przechowywany w programie SharePoint i w tym dokumencie nie powinien być zwracany w wynikach wyszukiwania, ochrona dokumentu przed przekazaniem go do programu SharePoint.

- Wyszukiwanie z pulpitu Windows używa indeksu udostępnionego między różnymi użytkownikami urządzenia, tak aby zabezpieczyć dane w chronionych dokumentów, indeksowania chronionych plików. Oznacza to, że mimo że wyniki wyszukiwania nie uwzględniają plików, które mają być chronione, możesz mieć pewność, pliki, które zawierają dane poufne nie są wyświetlane w wynikach wyszukiwania dla innych użytkowników, którzy mogą zalogować się do komputera lub podłącz do komputera. 

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o sposobie obsługi wszystkich następujące aplikacje i usługi usługi Azure Rights Management:

-   [Aplikacja do udostępniania usługi RMS dla systemu Windows i platform urządzeń przenośnych](sharing-app-support.md)

-   [Aplikacje i usługi pakietu Office](office-apps-services-support.md)

-   [Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików](file-server-support.md)

-   [Inne aplikacje, które obsługują interfejsy API usługi RMS](api-support.md)

