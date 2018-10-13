---
title: Jak aplikacje pakietu Office i usługi obsługują usługę Azure RMS z usługi AIP
description: Jak aplikacje pakietu Office dla użytkowników końcowych takich jak Word i Outlook i pakietu Office usług, takich jak Exchange i SharePoint, można użyć usługi Azure Rights Management z usługi AIP w celu ochrony danych organizacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/13/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 22df24a7af17dd87dd6f3947e39ea72d7b7b1372
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169944"
---
# <a name="how-office-applications-and-services-support-azure-rights-management"></a>Jak aplikacje pakietu Office i usługi obsługują usługę Azure Rights Management 

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Aplikacje pakietu Office dla użytkowników końcowych oraz usługi pakietu Office można użyć usługi Azure Rights Management z usługi Azure Information Protection, aby chronić dane Twojej organizacji. Te aplikacje pakietu Office to Word, Excel, PowerPoint i Outlook. Usługi pakietu Office to Exchange i SharePoint. Konfiguracje pakietu Office, które obsługują usługę Azure Rights Management, często używany jest termin **information rights management (IRM)**.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Aplikacje pakietu Office: Word, Excel, PowerPoint i Outlook
Te aplikacje natywnie obsługują usługę Azure Rights Management i Pozwól użytkownikom na stosowanie ochrony do zapisanego dokumentu lub wiadomości e-mail do wysłania. Użytkownicy mogą stosować [szablony](configure-policy-templates.md) celu zastosowania ochrony. Lub dla programu Word, Excel i PowerPoint, użytkownicy mogą wybrać dostosowywać ustawienia dotyczące dostępu, uprawnień i ograniczeń dotyczących użycia.

Na przykład użytkowników można skonfigurować dokument programu Word, dzięki czemu jest możliwy tylko dla osób w Twojej organizacji. Można też kontrolować, czy arkusz kalkulacyjny programu Excel może być edytowany, lub ograniczone tylko do odczytu lub zapobiec drukowaniu. Pliki zależne od czasu czas wygaśnięcia można skonfigurować dla Jeśli plik nie jest możliwy. Tę konfigurację można robić bezpośrednio przez użytkowników lub przez zastosowanie szablonu ochrony. W przypadku programu Outlook użytkownicy mogą także wybrać opcję **Nie przekazuj**, która zapobiega wyciekowi danych.

Oprócz macierzystą obsługę pakietu Office, usługi Azure Rights Management, aplikacje te obsługują także pasek usługi Azure Information Protection, który został zainstalowany przy użyciu [klienta Azure Information Protection](./rms-client/aip-client.md). Ten pasek wyświetla etykiety, które ułatwiają użytkownikom automatyczne stosowanie ochrony dokumentów i wiadomości e-mail zawierających poufne dane.

Jeśli chcesz już skonfigurować aplikacje pakietu Office i klienta usługi Azure Information Protection:

- Aby skonfigurować aplikacje pakietu Office, zobacz [Aplikacje pakietu Office: konfiguracja dla klientów](configure-office-apps.md).

- Aby zainstalować i skonfigurować klienta usługi Azure Information Protection, zobacz [Klient usługi Azure Information Protection: instalacja i konfiguracja klienta](configure-client.md).

## <a name="exchange-online-and-exchange-server"></a>Usługa Exchange Online i program Exchange Server
Gdy używasz usługi Exchange Online lub Exchange Server, można skonfigurować opcje usługi Azure Information Protection. Ta konfiguracja pozwala zapewnić następujących rozwiązań do ochrony programu Exchange:

-   **Protokół Exchange ActiveSync IRM** umożliwia urządzeniom przenośnym zabezpieczanie wiadomości e-mail i korzystanie z chronionych wiadomości.

-   Wyślij wiadomość e-mail obsługę ochrony **programu Outlook w sieci web**, która jest zaimplementowana podobnie jak w kliencie programu Outlook. Ta konfiguracja pozwala użytkownikom chronić wiadomości e-mail przy użyciu szablonów ochrony lub opcji. Użytkownicy mogą odczytywać i używać chronionych wiadomości e-mail wysyłanych do nich.

-   **Reguły ochrony** dla klientów programu Outlook skonfigurowane przez administratora do automatyczne stosowanie szablonów ochrony i opcje poczty e-mail przeznaczonych dla określonych odbiorców. Na przykład wewnętrzne wiadomości e-mail wysyłane do działu prawnego mogą być odczytywane tylko przez personel działu prawnego i nie mogą być przesyłane dalej. Przed wysłaniem wiadomości e-mail użytkownicy mogą zobaczyć, jakie zabezpieczenia zostały w niej zastosowane, oraz usunąć tę ochronę zgodnie ze swoimi preferencjami. Wiadomości e-mail są szyfrowane przed ich wysłaniem. Więcej informacji zawierają artykuły dotyczące [reguł ochrony programu Outlook](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) oraz [tworzenia reguły ochrony programu Outlook](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) dostępne w bibliotece programu Exchange.

-   **Reguły przepływu poczty** skonfigurowane przez administratora do automatyczne stosowanie szablonów ochrony lub opcji wiadomości e-mail. Te reguły są oparte na właściwości, takie jak nadawca, odbiorca, temat wiadomości i zawartość. Te reguły są podobne do reguł ochrony, ale nie zezwalaj użytkownikom na usuwanie ochrony, ponieważ ochrona jest ustawiony przez usługę Exchange, a nie przez klienta. Ponieważ ochrona jest ustawiony przez usługę, nie ma znaczenia, jakiego urządzenia lub systemu operacyjnego, jakie użytkownicy mają. Aby uzyskać więcej informacji, zobacz [przepływu reguł (reguł transportu) do obsługi poczty w usłudze Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) i [tworzenia reguły ochrony transportu](https://technet.microsoft.com/library/dd302432.aspx) dla lokalnego programu Exchange.

-   **Zasady (DLP) zapobiegania utracie danych** zawierających zestawy warunków filtrowania wiadomości e-mail i podjąć działania w celu zapobieżenia utracie danych dla poufnych lub wrażliwych informacji. Jedną z czynności, które można określić jest zastosować szyfrowanie jako ochrony, określając jedną z opcji lub szablonów ochrony. Po wykryciu poufnych danych użytkowników, które mogą wymagać zastosowania ochrony można porad dotyczących zasad. Aby uzyskać więcej informacji, zobacz [ochrony przed utratą danych](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) w dokumentacji programu Exchange Online.

-   **Szyfrowanie wiadomości usługi Office 365** , obsługuje wysyłanie chronionej wiadomości e-mail i dokumentów pakietu Office chronionych jako załączniki do dowolnego adresu e-mail, na dowolnym urządzeniu. Dla kont użytkowników, które nie używają usługi Azure AD w środowisku sieci web obsługuje dostawców tożsamości społecznościowych lub jednorazowy kod dostępu. Aby uzyskać więcej informacji, zobacz [skonfigurować nowe możliwości szyfrowanie wiadomości usługi Office 365 korzystających z usługi Azure Information Protection](/office365/securitycompliance/set-up-new-message-encryption-capabilities) w dokumentacji usługi Office 365. Aby pomóc Ci znaleźć dodatkowe informacje dotyczące tej konfiguracji, zobacz [szyfrowanie wiadomości usługi Office 365](https://docs.microsoft.com/office365/securitycompliance/ome).

Jeśli używasz lokalnego programu Exchange, służy funkcje IRM z usługą Azure Rights Management, wdrażając łącznik usługi Azure Rights Management. Ten łącznik działa jako przekaźnik między serwerami w środowisku lokalnym i usługą Azure Rights Management.

Aby uzyskać więcej informacji na temat szablonów ochrony, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md).

Dla opcji więcej informacji na temat wiadomości e-mail, który służy do ochrony wiadomości e-mail, zobacz [opcję nie przekazuj dotycząca wiadomości e-mail](configure-usage-rights.md#do-not-forward-option-for-emails) i [opcja tylko do szyfrowania wiadomości e-mail](configure-usage-rights.md#encrypt-only-option-for-emails).

Jeśli masz wszystko gotowe do skonfigurowania programu Exchange do ochrony wiadomości e-mail:

- W przypadku usługi Exchange Online, zobacz artykuł [Usługa Exchange Online: konfiguracja usługi IRM](configure-office365.md#exchange-online-irm-configuration).

- W przypadku lokalnej instalacji programu Exchange, zobacz [Wdrażanie łącznika usługi Azure Rights Management](deploy-rms-connector.md).


## <a name="sharepoint-online-and-sharepoint-server"></a>Usługa SharePoint Online i program SharePoint Server

Korzystając z usługi SharePoint Online lub SharePoint Server, możesz chronić dokumenty przy użyciu funkcji zarządzania prawami praw informacje programu SharePoint. Ta funkcja umożliwia administratorom chronić listy lub biblioteki, tak aby po użytkownik wyewidencjonuje dokument, pobrany plik pozostaje chroniony i tylko autoryzowane osoby można wyświetlać i używać zgodnie z zasadami ochrony informacji, które określisz. Na przykład można przypisać plikowi właściwość tylko do odczytu albo uniemożliwić kopiowanie tekstu, zapisywanie lokalnej kopii pliku czy drukowanie jego zawartości.

Dokumenty programu Word, PowerPoint, Excel i plików PDF obsługuje tę ochronę usługi IRM programu SharePoint. Domyślnie ochrona jest ograniczona do osoby, która pobiera dokument. To ustawienie domyślne można zmienić za pomocą opcji konfiguracji, o nazwie **Zezwalaj na ochronę grupy**, która rozszerza ochronę na grupie, która została określona. Na przykład można określić grupy, która ma uprawnienia do edycji dokumentów w bibliotece, tak, aby w tej samej grupy użytkowników można edytować dokument poza programem SharePoint, niezależnie od tego, z którym użytkownik pobrał dokument. Lub można określić grupę, która nie ma udzielone uprawnienia w programie SharePoint, ale użytkownicy w grupie należy uzyskać dostęp do dokumentów, poza programem SharePoint. 

W przypadku list programu SharePoint i bibliotek ochrona ta jest zawsze konfigurowana przez administratora, nigdy przez użytkownika końcowego. Ustaw uprawnienia na poziomie witryny, a te uprawnienia domyślnie są dziedziczone przez wszystkie listy lub biblioteki w tej witrynie. W przypadku korzystania z usługi SharePoint Online użytkownicy mogą również skonfigurować ochronę usługi IRM w bibliotece usługi OneDrive dla Firm.

Dla dokładniejszej kontroli możesz skonfigurować w witrynie listę lub bibliotekę, aby zatrzymać dziedziczenie uprawnień z elementu nadrzędnego. Następnie możesz skonfigurować uprawnienia usługi IRM na tym samym poziomie (listy lub biblioteki), które będą wówczas określane jako „unikatowe uprawnienia”. Jednak uprawnienia są zawsze ustawiane na poziomie kontenera. Nie możesz ustawić uprawnień dla poszczególnych plików. 

Usługę IRM należy najpierw włączyć dla programu SharePoint. Następnie określ uprawnienia usługi IRM dla biblioteki. W przypadku usług SharePoint Online i OneDrive dla Firm użytkownicy mogą także określić uprawnienia usługi IRM do własnej biblioteki usługi OneDrive dla Firm. Program SharePoint nie korzysta z szablonów zasad praw, chociaż możesz wybrać określone ustawienia konfiguracji programu SharePoint, odpowiadające pewnym ustawieniom, które możesz określić za pomocą szablonów.

Jeśli używasz programu SharePoint Server, możesz użyć ochrony za pomocą usługi IRM, wdrażając łącznik usługi Azure Rights Management. Ten łącznik działa jako przekaźnik między Twoimi serwerami lokalnymi a usługą Rights Management w chmurze. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](deploy-rms-connector.md).

> [!NOTE]
> Obecnie istnieją pewne ograniczenia dotyczące używania usługi IRM z programem SharePoint:
> 
> - Nie można używać domyślnych lub niestandardowych ochrony szablonów, zarządzanych w witrynie Azure portal. 
> 
> - Pliki, które mają rozszerzenie nazwy pliku ppdf chronionych plików PDF nie są obsługiwane. Aby uzyskać więcej informacji na temat wyświetlania chronionych plików PDF, zobacz [czytelnicy chronione pliki PDF Microsoft Information Protection](./rms-client/protected-pdf-readers.md).
> 
> - Współtworzenia, gdy więcej niż jedna osoba edytuje dokument, w tym samym czasie, nie jest obsługiwane. Aby edytować dokument w bibliotece chronioną przez IRM, musi najpierw zapoznaj się z dokumentu i pobierz go i poddać go edycji w aplikacji pakietu Office. W związku z tym tylko jedna osoba może edytować dokument w danym momencie.

W przypadku bibliotek, które nie są chronioną przez IRM, jeśli chroniony plik, który zostanie przekazany do programu SharePoint lub OneDrive, następujące nie działają z tym plikiem: Współtworzenie, Office Online, wyszukiwania, podglądu dokumentu, miniatury, zbierania elektronicznych materiałów dowodowych i ochrony przed utratą danych (DLP).

Podczas korzystania z ochrony za pomocą usługi IRM z programem SharePoint usługa Azure Rights Management stosuje ograniczenia dotyczące użycia i szyfrowanie danych względem dokumentów w trakcie ich pobierania z programu SharePoint, a nie w momencie ich utworzenia w programie SharePoint lub przekazania do biblioteki. Informacje dotyczące ochrony dokumentów przed ich pobraniem można znaleźć w artykule dotyczącym [szyfrowania danych w usługach OneDrive dla Firm i SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) dostępnym w dokumentacji programu SharePoint.

Chociaż nie jest już nowy w następującym wpisie w blogu usługi Office 365 zawiera pewne dodatkowe informacje, które mogą okazać się przydatne: [What's New with Information Rights Management in SharePoint and SharePoint Online](https://www.microsoft.com/en-us/microsoft-365/blog/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

Jeśli chcesz już skonfigurować program SharePoint dla usługi IRM:

- W przypadku usługi SharePoint Online, zobacz [SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration).

- W przypadku programu SharePoint Server, zobacz [Wdrażanie łącznika usługi Azure Rights Management](deploy-rms-connector.md).


## <a name="next-steps"></a>Kolejne kroki

Jeśli masz usługę Office 365, może zainteresować Cię artykuł dotyczący [rozwiązań do ochrony plików w usłudze Office 365](/office365/enterprise/microsoft-cloud-it-architecture-resources#BKMK_O365fileprotect), w którym opisano zalecane możliwości ochrony plików w usłudze Office 365.

Aby dowiedzieć się, jak inne aplikacje i usługi obsługują usługę Azure Rights Management w ramach usługi Azure Information Protection, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md).

Jeśli chcesz rozpocząć wdrażanie, co obejmuje skonfigurowanie tych aplikacji i usług, zobacz [Plan wdrażania usługi Azure Information Protection](deployment-roadmap.md).
