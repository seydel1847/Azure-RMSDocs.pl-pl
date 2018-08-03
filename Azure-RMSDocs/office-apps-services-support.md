---
title: Jak aplikacje pakietu Office i usługi obsługują usługę Azure RMS z usługi AIP
description: Jak aplikacje pakietu Office dla użytkowników końcowych takich jak Word i Outlook i pakietu Office usług, takich jak Exchange i SharePoint, można użyć usługi Azure Rights Management z usługi AIP w celu ochrony danych organizacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 6c500c099a382d4a4a070b05a55043bc66dc9543
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39475245"
---
# <a name="how-office-applications-and-services-support-azure-rights-management"></a>Jak aplikacje pakietu Office i usługi obsługują usługę Azure Rights Management 

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Aplikacje pakietu Office dla użytkowników końcowych oraz usługi pakietu Office można użyć usługi Azure Rights Management z usługi Azure Information Protection, aby chronić dane Twojej organizacji. Te aplikacje pakietu Office to Word, Excel, PowerPoint i Outlook. Usługi pakietu Office to Exchange i SharePoint. Konfiguracje pakietu Office, które obsługują usługę Azure Rights Management, często używany jest termin **information rights management (IRM)**.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Aplikacje pakietu Office: Word, Excel, PowerPoint i Outlook
Te aplikacje natywnie obsługują usługę Azure Rights Management i Pozwól użytkownikom na stosowanie ochrony do zapisanego dokumentu lub wiadomości e-mail do wysłania. Użytkownicy mogą stosować szablony w celu zastosowania ochrony. Lub dla programu Word, Excel i PowerPoint, użytkownicy mogą wybrać dostosowywać ustawienia dotyczące dostępu, uprawnień i ograniczeń dotyczących użycia. 

Na przykład użytkowników można skonfigurować dokument programu Word, dzięki czemu jest możliwy tylko dla osób w Twojej organizacji. Można też kontrolować, czy arkusz kalkulacyjny programu Excel może być edytowany, lub ograniczone tylko do odczytu lub zapobiec drukowaniu. Pliki zależne od czasu czas wygaśnięcia można skonfigurować dla Jeśli plik nie jest możliwy. Tę konfigurację można robić bezpośrednio przez użytkowników lub przez zastosowanie szablonu. W przypadku programu Outlook użytkownicy mogą także wybrać opcję **Nie przekazuj**, która zapobiega wyciekowi danych.

Oprócz macierzystą obsługę pakietu Office, usługi Azure Rights Management, aplikacje te obsługują także pasek usługi Azure Information Protection, który został zainstalowany przy użyciu [klienta Azure Information Protection](./rms-client/aip-client.md). Ten pasek wyświetla etykiety, które ułatwiają użytkownikom automatyczne stosowanie ochrony dokumentów i wiadomości e-mail zawierających poufne dane.

Jeśli chcesz już skonfigurować aplikacje pakietu Office i klienta usługi Azure Information Protection:

- Aby skonfigurować aplikacje pakietu Office, zobacz [Aplikacje pakietu Office: konfiguracja dla klientów](./deploy-use/configure-office-apps.md).

- Aby zainstalować i skonfigurować klienta usługi Azure Information Protection, zobacz [Klient usługi Azure Information Protection: instalacja i konfiguracja klienta](./deploy-use/configure-client.md).

## <a name="exchange-online-and-exchange-server"></a>Usługa Exchange Online i program Exchange Server
Gdy używasz usługi Exchange Online lub Exchange Server, można skonfigurować informacji usługi rights management (IRM) opcje, które obsługują usługę Azure Rights Management. Ta konfiguracja pozwala zapewnić następujących rozwiązań do ochrony programu Exchange:

-   **Protokół Exchange ActiveSync IRM** umożliwia urządzeniom przenośnym zabezpieczanie wiadomości e-mail i korzystanie z chronionych wiadomości.

-   Wyślij wiadomość e-mail obsługę ochrony **programu Outlook w sieci web**, która jest zaimplementowana podobnie jak w kliencie programu Outlook. Ta konfiguracja pozwala użytkownikom chronić wiadomości e-mail za pomocą szablonów lub przez określenie poszczególnych opcji. Użytkownicy mogą odczytywać i używać chronionych wiadomości e-mail wysyłanych do nich.

-   **Reguły ochrony** dla klientów programu Outlook skonfigurowane przez administratora do automatyczne stosowanie szablonów ochrony do wiadomości e-mail przeznaczonych dla określonych odbiorców. Na przykład wewnętrzne wiadomości e-mail wysyłane do działu prawnego mogą być odczytywane tylko przez personel działu prawnego i nie mogą być przesyłane dalej. Przed wysłaniem wiadomości e-mail użytkownicy mogą zobaczyć, jakie zabezpieczenia zostały w niej zastosowane, oraz usunąć tę ochronę zgodnie ze swoimi preferencjami. Wiadomości e-mail są szyfrowane przed ich wysłaniem. Więcej informacji zawierają artykuły dotyczące [reguł ochrony programu Outlook](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) oraz [tworzenia reguły ochrony programu Outlook](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) dostępne w bibliotece programu Exchange.

-   **Reguły przepływu poczty** komunikaty skonfigurowane przez administratora do automatyczne stosowanie szablonów ochrony do poczty e-mail. Te reguły są oparte na właściwości, takie jak nadawca, odbiorca, temat wiadomości i zawartość. Te reguły są podobne do reguł ochrony, ale nie należy zezwalać użytkownikom na usuwanie ochrony. Zasady można zastosować do programu Outlook w sieci web i wiadomości e-mail, które są wysyłane przez urządzenia przenośne. Ponadto te zasady nie należy szyfrować wiadomości e-mail przed wysłaniem ich z klienta. Więcej informacji zawiera artykuł dotyczący [tworzenia reguły ochrony transportu](https://technet.microsoft.com/library/dd302432.aspx) dostępny w bibliotece programu Exchange.

-   **Zasady (DLP) zapobiegania utracie danych** zawierają zestawy warunków filtrowania wiadomości e-mail i podjąć działania w celu zapobieżenia utracie danych dla poufnych lub wrażliwych informacji. Przykładami poufnych lub wrażliwych informacji osobistych informacji o karcie kredytowej. Po wykryciu poufnych danych użytkowników, które mogą wymagać zastosowania ochrony można porad dotyczących zasad. Aby uzyskać więcej informacji, zobacz [ochrony przed utratą danych] (https://technet.microsoft.com/library/jj150527(v=exchg.160\).aspx) w bibliotece programu Exchange.

-   **Szyfrowanie wiadomości usługi Office 365** , obsługuje wysyłanie chronionej wiadomości e-mail i dokumentów pakietu Office chronionych jako załączniki do dowolnego adresu, na dowolnym urządzeniu. Dla kont użytkowników, które nie używają usługi Azure AD w środowisku sieci web obsługuje dostawców tożsamości społecznościowych lub jednorazowy kod dostępu. Aby uzyskać więcej informacji, zobacz [skonfigurować nowe możliwości szyfrowanie wiadomości usługi Office 365 korzystających z usługi Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) z witryny sieci Web pakietu Office.

Jeśli używasz lokalnego programu Exchange, służy funkcje IRM z usługą Azure Rights Management, wdrażając łącznik usługi Azure Rights Management. Ten łącznik działa jako przekaźnik między serwerami w środowisku lokalnym i usługą Azure Rights Management.

Jeśli chcesz już skonfigurować program Exchange dla usługi IRM:

- W przypadku usługi Exchange Online, zobacz artykuł [Usługa Exchange Online: konfiguracja usługi IRM](./deploy-use/configure-office365.md#exchange-online-irm-configuration).

- W przypadku lokalnej instalacji programu Exchange, zobacz [Wdrażanie łącznika usługi Azure Rights Management](./deploy-use/deploy-rms-connector.md).


## <a name="sharepoint-online-and-sharepoint-server"></a>Usługa SharePoint Online i program SharePoint Server

Korzystając z usługi SharePoint Online lub SharePoint Server, możesz chronić dokumenty przy użyciu funkcji zarządzania prawami praw informacje programu SharePoint. Ta funkcja umożliwia administratorom chronić listy lub biblioteki, tak aby po użytkownik wyewidencjonuje dokument, pobrany plik pozostaje chroniony i tylko autoryzowane osoby można wyświetlać i używać zgodnie z zasadami ochrony informacji, które określisz. Na przykład można przypisać plikowi właściwość tylko do odczytu albo uniemożliwić kopiowanie tekstu, zapisywanie lokalnej kopii pliku czy drukowanie jego zawartości.

Dokumenty programu Word, PowerPoint, Excel i plików PDF obsługuje tę ochronę usługi IRM programu SharePoint. Domyślnie ochrona jest ograniczona do osoby, która pobiera dokument. Możesz zmienić to ustawienie domyślne za pomocą opcji konfiguracji, która rozszerza ochronę dla wszystkich użytkowników, którzy mają dostęp do dokumentu w programie SharePoint lub grupie, która została określona.

W przypadku list programu SharePoint i bibliotek ochrona ta jest zawsze konfigurowana przez administratora, nigdy przez użytkownika końcowego. Ustaw uprawnienia na poziomie witryny, a te uprawnienia domyślnie są dziedziczone przez wszystkie listy lub biblioteki w tej witrynie. W przypadku korzystania z usługi SharePoint Online użytkownicy mogą również skonfigurować ochronę usługi IRM w bibliotece usługi OneDrive dla Firm.

Dla dokładniejszej kontroli możesz skonfigurować w witrynie listę lub bibliotekę, aby zatrzymać dziedziczenie uprawnień z elementu nadrzędnego. Następnie możesz skonfigurować uprawnienia usługi IRM na tym samym poziomie (listy lub biblioteki), które będą wówczas określane jako „unikatowe uprawnienia”. Jednak uprawnienia są zawsze ustawiane na poziomie kontenera. Nie możesz ustawić uprawnień dla poszczególnych plików. 

Usługę IRM należy najpierw włączyć dla programu SharePoint. Następnie określ uprawnienia usługi IRM dla biblioteki. W przypadku usług SharePoint Online i OneDrive dla Firm użytkownicy mogą także określić uprawnienia usługi IRM do własnej biblioteki usługi OneDrive dla Firm. Program SharePoint nie korzysta z szablonów zasad praw, chociaż możesz wybrać określone ustawienia konfiguracji programu SharePoint, odpowiadające pewnym ustawieniom, które możesz określić za pomocą szablonów.

Jeśli używasz programu SharePoint Server, możesz użyć ochrony za pomocą usługi IRM, wdrażając łącznik usługi Azure Rights Management. Ten łącznik działa jako przekaźnik między Twoimi serwerami lokalnymi a usługą Rights Management w chmurze. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](./deploy-use/deploy-rms-connector.md).

> [!NOTE]
> Obecnie istnieją pewne ograniczenia dotyczące używania usługi IRM z programem SharePoint:
> 
> - Nie można używać domyślnych lub niestandardowych ochrony szablonów, zarządzanych w witrynie Azure portal. 
> 
> - Pliki, które mają rozszerzenie nazwy pliku ppdf chronionych plików PDF nie są obsługiwane. Pliki, które mają rozszerzenie nazwy pliku PDF są obsługiwane, a po pobraniu mogą otwierać aplikacji PDF, która natywnie obsługuje usługę Rights Management. Na przykład klient usługi Azure Information Protection dla Windows zawiera podgląd tych chronionych plików PDF. Alternatywne przeglądarki plików PDF są wymienione w [tabeli aplikacji obsługujących usługę RMS](./requirements-applications.md#rms-enlightened-applications).
> 
> - Współtworzenie, gdy więcej niż jedna osoba edytuje dokument, w tym samym czasie, nie jest obsługiwane. Aby edytować dokument w bibliotece chronioną przez IRM, musi najpierw zapoznaj się z dokumentu i pobierz go i poddać go edycji w aplikacji pakietu Office. W związku z tym tylko jedna osoba może edytować dokument w danym momencie.

W przypadku bibliotek, które nie są chronioną przez IRM, jeśli chroniony plik, który zostanie przekazany do programu SharePoint lub OneDrive, następujące nie działają z tym plikiem: Współtworzenie, Office Online, wyszukiwania, podglądu dokumentu, miniatury, zbierania elektronicznych materiałów dowodowych i ochrony przed utratą danych (DLP).

Podczas korzystania z ochrony za pomocą usługi IRM z programem SharePoint usługa Azure Rights Management stosuje ograniczenia dotyczące użycia i szyfrowanie danych względem dokumentów w trakcie ich pobierania z programu SharePoint, a nie w momencie ich utworzenia w programie SharePoint lub przekazania do biblioteki. Informacje dotyczące ochrony dokumentów przed ich pobraniem można znaleźć w artykule dotyczącym [szyfrowania danych w usługach OneDrive dla Firm i SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) dostępnym w dokumentacji programu SharePoint.

Chociaż nie jest już nowy w następującym wpisie w blogu usługi Office 365 zawiera pewne dodatkowe informacje, które mogą okazać się przydatne: [What's New with Information Rights Management in SharePoint and SharePoint Online](https://www.microsoft.com/en-us/microsoft-365/blog/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

Jeśli chcesz już skonfigurować program SharePoint dla usługi IRM:

- W przypadku usługi SharePoint Online, zobacz [SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM](./deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration).

- W przypadku programu SharePoint Server, zobacz [Wdrażanie łącznika usługi Azure Rights Management](./deploy-use/deploy-rms-connector.md).


## <a name="next-steps"></a>Kolejne kroki

Jeśli masz usługę Office 365, może zainteresować Cię artykuł dotyczący [rozwiązań do ochrony plików w usłudze Office 365](/office365/enterprise/microsoft-cloud-it-architecture-resources#BKMK_O365fileprotect), w którym opisano zalecane możliwości ochrony plików w usłudze Office 365.

Aby dowiedzieć się, jak inne aplikacje i usługi obsługują usługę Azure Rights Management w ramach usługi Azure Information Protection, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md).

Jeśli chcesz rozpocząć wdrażanie, co obejmuje skonfigurowanie tych aplikacji i usług, zobacz [Plan wdrażania usługi Azure Information Protection](./plan-design/deployment-roadmap.md).
