---
title: "Jak aplikacje obsługują usługę Azure Rights Management | Azure Information Protection"
description: "Omówienie sposobu, w jaki najczęściej używane aplikacje (takie jak aplikacje pakietu Office — Word, Excel, PowerPoint i Outlook) oraz usługi (takie jak Exchange i SharePoint) użytkownika końcowego mogą korzystać z usługi Azure Rights Management w ramach usługi Azure Information Protection w celu ochrony firmowych dokumentów i wiadomości e-mail."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c8ffebad1130c8ba084c0feb83aa3ec54692ad54
ms.openlocfilehash: f3e0be224f2a9e587f5be1bbdbbdb3e81b7a4bca


---

# <a name="how-applications-support-the-azure-rights-management-service"></a>Jak aplikacje obsługują usługę Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

Poniższe informacje pozwalają zrozumieć, w jaki sposób najczęściej używane aplikacje (takie jak aplikacje pakietu Office — Word, Excel, PowerPoint i Outlook) oraz usługi (takie jak Exchange i SharePoint) użytkownika końcowego mogą korzystać z technologii Microsoft Azure Rights Management w ramach usługi Azure Information Protection w celu ochrony firmowych dokumentów i wiadomości e-mail. 
> [!NOTE]
> Aby sprawdzić obsługiwane przez usługę Azure Rights Management aplikacje i ich wersje, zobacz [aplikacje obsługujące technologię ochrony danych usługi Azure Rights](../get-started/requirements-applications.md).

W niektórych przypadkach usługa Azure Rights Management stosuje ochronę automatycznie, zgodnie z zasadami skonfigurowanymi przez administratorów. Dotyczy to na przykład bibliotek programu SharePoint, plików klasyfikowanych i reguł transportu programu Exchange. W innych przypadkach użytkownicy końcowi muszą sami zastosować ochronę informacji z poziomu aplikacji przez wybranie szablonu lub określonych opcji. Dotyczy to na przykład sytuacji, gdy użytkownicy udostępniają plik pocztą e-mail, lub ochrony miejscowej plików przez ograniczenie dostępu lub użycia dla wybranych użytkowników lub dla użytkowników spoza organizacji.

Szablony ułatwiają użytkownikom (i administratorom, którzy konfigurują zasady) stosowanie odpowiedniego poziomu ochrony i ograniczenie dostępu do osób wewnątrz organizacji. Chociaż usługa Azure Rights Management dostarcza dwa szablony domyślne, prawdopodobnie zajdzie potrzeba utworzenia szablonów niestandardowych, aby ograniczyć sytuacje, w których użytkownicy muszą określać poszczególne opcje. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

W przypadkach, gdy użytkownicy muszą sami stosować ochronę informacji, należy pamiętać o udostępnieniu im instrukcji oraz wskazówek, jak i kiedy mają to robić. Instrukcje powinny być specyficzne dla aplikacji i wersji, z których użytkownicy korzystają, oraz sposobu, w jaki z nich korzystają, a wskazówki dotyczące sposobu i sytuacji stosowania ochrony informacji powinny być odpowiednie dla Twojej firmy. Aby uzyskać więcej informacji, zobacz [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](../deploy-use/help-users.md).

Informacje o sposobach konfigurowania tych aplikacji dla usługi Azure Rights Management w ramach usługi Azure Information Protection podano w temacie [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](../deploy-use/configure-applications.md).

> [!TIP]
> Przykłady i zrzuty ekranu aplikacji korzystających z usługi Azure Rights Management można znaleźć w artykule [Azure RMS w działaniu: co widzą administratorzy i użytkownicy](what-admins-users-see.md).

Z usługą Rights Management mogą być na różne sposoby zintegrowane usługi wyszukiwania. Na przykład: 

- Usługa Exchange Online i serwer programu Exchange korzystają z indeksowania po stronie usługi, dzięki czemu wiadomości e-mail użytkownika chronione przez usługę RMS są automatycznie wyświetlane w wynikach wyszukiwania. 

- Usługa SharePoint Online i program SharePoint Server stosują do plików mechanizmy ochrony usługi Rights Management tylko podczas pobierania, co oznacza, że to rozwiązanie do ochrony dokumentów nie ma wpływu na indeksowanie i wyniki wyszukiwania w programie SharePoint. Jeśli jednak istnieje dokument, który ma być przechowywany w programie SharePoint i nie powinien być zwracany w wynikach wyszukiwania, usługa RMS chroni taki plik przed przekazaniem go do programu SharePoint.

- Program Wyszukiwanie z pulpitu systemu Windows używa indeksu udostępnionego między różnymi użytkownikami urządzenia, a więc w celu zapewnienia bezpieczeństwa danych w chronionych dokumentach nie indeksuje on plików chronionych przez usługę RMS. W efekcie, mimo że wyniki wyszukiwania nie uwzględniają plików, dla których jest stosowana ochrona, można mieć pewność, że pliki zawierające dane poufne nie będą wyświetlane w wynikach wyszukiwania dla innych użytkowników, którzy mogą zalogować się do danego komputera lub nawiązać z nim połączenie. 



## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej na temat sposobu obsługi usługi Azure Rights Management przez następujące aplikacje i serwery:

-   [Aplikacja do udostępniania usługi RMS dla systemu Windows i platform urządzeń przenośnych](sharing-app-support.md)

-   [Aplikacje i usługi pakietu Office](office-apps-services-support.md)

-   [Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików](file-server-support.md)

-   [Inne aplikacje, które obsługują interfejsy API usługi RMS](api-support.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


