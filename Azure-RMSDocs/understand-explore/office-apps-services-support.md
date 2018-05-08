---
title: Jak aplikacje pakietu Office i usługi obsługują usługę Azure RMS w Efektywnych
description: Jak aplikacje pakietu Office przez użytkownika końcowego, takich jak Word i Outlook i Office usług, takich jak programy Exchange i SharePoint, można użyć usługi Azure Rights Management z Efektywnych w celu ochrony danych organizacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: caf89d6df51adcd556db319a8140cbe936102ef3
ms.sourcegitcommit: fa64f9c2a4d367d7586d64def0fd02764ad2e00b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2018
---
# <a name="how-office-applications-and-services-support-azure-rights-management"></a>Jak aplikacje pakietu Office i usługi obsługują usługę Azure Rights Management 

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Aplikacje pakietu Office przez użytkownika końcowego i usługi pakietu Office można użyć usługi Azure Rights Management z usługi Azure Information Protection w celu ochrony danych organizacji. Te aplikacje pakietu Office to Word, Excel, PowerPoint i Outlook. Usługi pakietu Office to Exchange i SharePoint. Konfiguracje pakietu Office, które obsługują usługę Azure Rights Management, często używany jest termin **prawami do informacji (IRM) zarządzania**.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Aplikacje pakietu Office: Word, Excel, PowerPoint i Outlook
Te aplikacje natywnie obsługują usługę Azure Rights Management, pozwalając użytkownikom na stosowanie ochrony do zapisanego dokumentu lub wiadomości e-mail do wysłania. Użytkownicy mogą stosować szablony do zastosowania ochrony. Lub dla programu Word, Excel i PowerPoint, użytkownicy mogą wybrać dostosowywać ustawienia dotyczące dostępu, uprawnień i ograniczeń użycia. 

Na przykład użytkownicy mogą skonfigurować dokument programu Word, dzięki czemu jest możliwy tylko dla osób w organizacji. Lub arkusz kalkulacyjny programu Excel może być edytowany, lub ograniczone tylko do odczytu lub uniemożliwić jego drukowanie. Pliki zależne od czasu można skonfigurować czas wygaśnięcia dla podczas mogą już być dostępu do pliku. Ta konfiguracja może się bezpośrednio przez użytkowników lub przez zastosowanie szablonu. W przypadku programu Outlook użytkownicy mogą także wybrać opcję **Nie przekazuj**, która zapobiega wyciekowi danych.

Oprócz Office macierzystą obsługę usługi Azure Rights Management, te aplikacje obsługują także pasek usługi Azure Information Protection, który jest instalowany z [klienta Azure Information Protection](../rms-client/aip-client.md). Ten pasek zostaną wyświetlone etykiety, które ułatwia użytkownikom automatyczne stosowanie ochrony do dokumentów i wiadomości e-mail zawierające poufne dane.

Jeśli chcesz już skonfigurować aplikacje pakietu Office i klienta usługi Azure Information Protection:

- Aby skonfigurować aplikacje pakietu Office, zobacz [Aplikacje pakietu Office: konfiguracja dla klientów](../deploy-use/configure-office-apps.md).

- Aby zainstalować i skonfigurować klienta usługi Azure Information Protection, zobacz [Klient usługi Azure Information Protection: instalacja i konfiguracja klienta](../deploy-use/configure-client.md).

## <a name="exchange-online-and-exchange-server"></a>Usługa Exchange Online i program Exchange Server
Korzystając z usługi Exchange Online lub Exchange Server, można skonfigurować informacji rights management (IRM) opcje, które obsługują usługę Azure Rights Management. Taka konfiguracja pozwala zapewnić następujące rozwiązania ochrony programu Exchange:

-   **Protokół Exchange ActiveSync IRM** umożliwia urządzeniom przenośnym zabezpieczanie wiadomości e-mail i korzystanie z chronionych wiadomości.

-   Wyślij wiadomość e-mail obsługę ochrony **programu Outlook w sieci web**, która jest zaimplementowana podobnie jak klient programu Outlook. Taka konfiguracja pozwala użytkownikom chronić wiadomości e-mail za pomocą szablonów lub przez określenie poszczególnych opcji. Użytkownicy mogą odczytywać i wykorzystywać chronione wiadomości e-mail wysyłanych do nich.

-   **Zasady ochrony** dla klientów programu Outlook skonfigurowane przez administratora do automatyczne stosowanie szablonów ochrony poczty e-mail przeznaczonych dla określonych odbiorców. Na przykład wewnętrzne wiadomości e-mail wysyłane do działu prawnego mogą być odczytywane tylko przez personel działu prawnego i nie mogą być przesyłane dalej. Przed wysłaniem wiadomości e-mail użytkownicy mogą zobaczyć, jakie zabezpieczenia zostały w niej zastosowane, oraz usunąć tę ochronę zgodnie ze swoimi preferencjami. Wiadomości e-mail są szyfrowane przed ich wysłaniem. Więcej informacji zawierają artykuły dotyczące [reguł ochrony programu Outlook](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) oraz [tworzenia reguły ochrony programu Outlook](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) dostępne w bibliotece programu Exchange.

-   **Reguły przepływu poczty** skonfigurowane przez administratora do automatyczne stosowanie szablonów ochrony poczty e-mail wiadomości. Te zasady są oparte na właściwości, takie jak nadawca, odbiorca, temat wiadomości i zawartość. Te reguły są podobne do reguł ochrony, ale nie zezwala użytkownikom na usuwanie ochrony. Zasady można zastosować do programu Outlook w sieci web i wiadomości e-mail wysyłanych przez urządzenia przenośne. Ponadto te zasady nie powodują szyfrowania wiadomości e-mail przed ich wysłaniem z klienta. Więcej informacji zawiera artykuł dotyczący [tworzenia reguły ochrony transportu](https://technet.microsoft.com/library/dd302432.aspx) dostępny w bibliotece programu Exchange.

-   **Zasady (DLP) zapobiegania utracie danych** zawierają zestawy warunków filtrowania wiadomości e-mail i podejmowanie działań w celu uniknięcia utraty poufnych lub wrażliwych informacji. Przykładami poufnych lub wrażliwych informacji osobowych karty kredytowej lub informacji. W przypadku wykrycia poufnych danych użytkownikom alertów, które mogą wymagać zastosowania ochrony można porad dotyczących zasad. Aby uzyskać więcej informacji, zobacz [ochrony przed utratą danych] (https://technet.microsoft.com/library/jj150527(v=exchg.160\)aspx) w bibliotece programu Exchange.

-   **Szyfrowanie wiadomości usługi Office 365** który obsługuje wysyłanie chronionej wiadomości e-mail i ochrony dokumentów pakietu Office jako załączników do dowolnego adresu na dowolnym urządzeniu. Dla kont użytkowników, które nie używają usługi Azure AD środowisko sieci web obsługuje dostawców tożsamości społecznościowych lub jednorazowy kod dostępu. Aby uzyskać więcej informacji, zobacz [skonfigurować nowe możliwości szyfrowanie wiadomości usługi Office 365, rozszerzający usługi Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) z witryny sieci Web pakietu Office.

Użycie lokalnego programu Exchange, używając funkcji IRM z usługą Azure Rights Management, wdrażając łącznik usługi Azure Rights Management. Ten łącznik działa jako przekaźnik między serwerami lokalnymi i usługą Azure Rights Management.

Jeśli chcesz już skonfigurować program Exchange dla usługi IRM:

- W przypadku usługi Exchange Online, zobacz artykuł [Usługa Exchange Online: konfiguracja usługi IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- W przypadku lokalnej instalacji programu Exchange, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).


## <a name="sharepoint-online-and-sharepoint-server"></a>Usługa SharePoint Online i program SharePoint Server

Korzystając z usługi SharePoint Online lub SharePoint Server, możesz chronić dokumenty przy użyciu funkcji programu SharePoint informacji rights management (IRM). Ta funkcja umożliwia administratorom chronić listy lub biblioteki, dzięki czemu, gdy użytkownik wyewidencjonuje dokument, pobrany plik jest chroniony, tak aby tylko upoważnione osoby mogą przeglądać i używanie plików zgodnie z określonymi zasadami ochrony informacji. Na przykład można przypisać plikowi właściwość tylko do odczytu albo uniemożliwić kopiowanie tekstu, zapisywanie lokalnej kopii pliku czy drukowanie jego zawartości.

Dokumenty programu Word, Excel, PowerPoint i PDF obsługuje tę ochronę usługi IRM programu SharePoint. Domyślnie ochrona jest ograniczona do osoby, która pobiera dokument. Możesz zmienić to ustawienie domyślne za pomocą opcji konfiguracji, która rozszerza ochronę dla wszystkich użytkowników, którzy mają dostęp do dokumentu w programie SharePoint lub do określonej grupy.

Dla bibliotek i list programu SharePoint ta ochrona jest zawsze konfigurowane przez administratora, a nie przez użytkownika końcowego. Ustaw uprawnienia na poziomie witryny, a te uprawnienia domyślnie są dziedziczone przez wszystkie listy lub biblioteki w tej witrynie. W przypadku korzystania z usługi SharePoint Online użytkownicy mogą również skonfigurować ochronę usługi IRM w bibliotece usługi OneDrive dla Firm.

Dla dokładniejszej kontroli możesz skonfigurować w witrynie listę lub bibliotekę, aby zatrzymać dziedziczenie uprawnień z elementu nadrzędnego. Następnie możesz skonfigurować uprawnienia usługi IRM na tym samym poziomie (listy lub biblioteki), które będą wówczas określane jako „unikatowe uprawnienia”. Jednak uprawnienia są zawsze ustawiane na poziomie kontenera. Nie możesz ustawić uprawnień dla poszczególnych plików. 

Usługę IRM należy najpierw włączyć dla programu SharePoint. Następnie określ uprawnienia usługi IRM dla biblioteki. W przypadku usług SharePoint Online i OneDrive dla Firm użytkownicy mogą także określić uprawnienia usługi IRM do własnej biblioteki usługi OneDrive dla Firm. Program SharePoint nie korzysta z szablonów zasad praw, chociaż możesz wybrać określone ustawienia konfiguracji programu SharePoint, odpowiadające pewnym ustawieniom, które możesz określić za pomocą szablonów.

Jeśli używasz programu SharePoint Server, możesz użyć ochrony za pomocą usługi IRM, wdrażając łącznik usługi Azure Rights Management. Ten łącznik działa jako przekaźnik między Twoimi serwerami lokalnymi a usługą Rights Management w chmurze. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

> [!NOTE]
> Obecnie istnieją pewne ograniczenia dotyczące używania usługi IRM z programem SharePoint:
> 
> - Nie można użyć domyślnej lub niestandardowej ochrony szablonów, które można zarządzać w portalu Azure. 
> 
> - Pliki, które mają rozszerzenie nazwy pliku ppdf chronione pliki PDF nie są obsługiwane. Pliki, które mają rozszerzenie nazwy pliku PDF są obsługiwane i po pobraniu mogą być otwierane przez aplikację PDF z natywną obsługą usługi Rights Management. Na przykład klient usługi Azure Information Protection dla systemu Windows zawiera podgląd tych chronionych plików PDF. Alternatywne przeglądarki plików PDF są wymienione w [tabeli aplikacji obsługujących usługę RMS](../get-started/requirements-applications.md#rms-enlightened-applications).
> 
> - Współtworzenie, gdy więcej niż jedna osoba modyfikacje dokumentu w tym samym czasie, nie jest obsługiwana. Aby edytować dokument w bibliotece chronione usługa IRM, musi najpierw Wyewidencjonuj dokument i go pobrać, a następnie edytować go w aplikacji pakietu Office. W rezultacie tylko jedna osoba może edytować dokument naraz.

Dla bibliotek, które nie są IRM chronionego, jeśli chroniony plik, który następnie przekazać do programu SharePoint lub usługi OneDrive, następujące nie współpracujesz z tego pliku: współtworzenia, Office Online wyszukiwania, dokumentu podglądu, miniatur, zbieranie elektronicznych materiałów dowodowych i ochrony przed utratą danych (DLP).

Podczas korzystania z ochrony za pomocą usługi IRM z programem SharePoint usługa Azure Rights Management stosuje ograniczenia dotyczące użycia i szyfrowanie danych względem dokumentów w trakcie ich pobierania z programu SharePoint, a nie w momencie ich utworzenia w programie SharePoint lub przekazania do biblioteki. Informacje dotyczące ochrony dokumentów przed ich pobraniem można znaleźć w artykule dotyczącym [szyfrowania danych w usługach OneDrive dla Firm i SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) dostępnym w dokumentacji programu SharePoint.

Następujący wpis na blogu pakietu Office, chociaż nie jest już nowy, zawiera pewne dodatkowe informacje, które mogą się okazać przydatne: [What’s New with Information Rights Management in SharePoint and SharePoint Online](https://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/) (Co nowego w usłudze Information Rights Management w programie SharePoint i usłudze SharePoint Online)

Jeśli chcesz już skonfigurować program SharePoint dla usługi IRM:

- W przypadku usługi SharePoint Online, zobacz [SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration).

- W przypadku programu SharePoint Server, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).


## <a name="next-steps"></a>Następne kroki

Jeśli masz usługę Office 365, może zainteresować Cię artykuł dotyczący [rozwiązań do ochrony plików w usłudze Office 365](/office365/enterprise/microsoft-cloud-it-architecture-resources#BKMK_O365fileprotect), w którym opisano zalecane możliwości ochrony plików w usłudze Office 365.

Aby dowiedzieć się, jak inne aplikacje i usługi obsługują usługę Azure Rights Management w ramach usługi Azure Information Protection, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md).

Jeśli chcesz rozpocząć wdrażanie, co obejmuje skonfigurowanie tych aplikacji i usług, zobacz [Plan wdrażania usługi Azure Information Protection](../plan-design/deployment-roadmap.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]