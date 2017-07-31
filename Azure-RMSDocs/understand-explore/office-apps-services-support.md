---
title: "Korzystanie z aplikacji i usług pakietu Office z usługą Azure Information Protection"
description: "Sposób, w jaki aplikacje pakietu Office dla użytkowników końcowych (takie jak Word, Excel, PowerPoint i Outlook) oraz usługi pakietu Office (na przykład Exchange i SharePoint) mogą używać usługi Azure Rights Management, aby chronić dane organizacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 96707d0790747b4dac668508f58e9584f4649370
ms.sourcegitcommit: 72208cabecaa233cdade0dae0c448037370f2c2c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/28/2017
---
# <a name="office-applications-and-services"></a>Aplikacje i usługi pakietu Office

>*Dotyczy: Azure Information Protection, Office 365*

Aplikacje pakietu Office dla użytkowników końcowych oraz usługi pakietu Office (na przykład Exchange i SharePoint) mogą korzystać z usługi Azure Rights Management w ramach usługi Azure Information Protection, aby ułatwić ochronę danych organizacji. Te aplikacje pakietu Office to Word, Excel, PowerPoint i Outlook. Usługi pakietu Office to Exchange i SharePoint. 

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Aplikacje pakietu Office: Word, Excel, PowerPoint i Outlook
Te aplikacje natywnie obsługują usługę Rights Management i korzystają z usług zarządzania prawami do informacji (IRM), pozwalając użytkownikom na stosowanie ochrony do zapisanego dokumentu lub wiadomości e-mail do wysłania. Użytkownicy mogą stosować szablony lub, w przypadku programów Word, Excel i PowerPoint, dostosowywać ustawienia dotyczące dostępu, uprawnień i ograniczeń użytkowania. 

Na przykład użytkownicy mogą tak skonfigurować dokument programu Word, aby był on dostępny tylko dla osób z danej organizacji. Można określić, czy arkusz kalkulacyjny programu Excel jest dostępny do edycji lub ograniczyć jego właściwości tylko do odczytu albo uniemożliwić jego drukowanie. W przypadku plików ważnych przez określony czas można skonfigurować czas wygaśnięcia (bezpośrednio przez działania użytkowników lub przez zastosowanie szablonu), po upływie którego dostęp do pliku nie będzie już możliwy. W przypadku programu Outlook, oprócz możliwości wyboru szablonu, użytkownicy mogą wybrać opcję **Nie przekazuj**, która zapobiega wyciekowi danych.

Oprócz natywnych Usług zarządzania prawami do informacji (IRM), aplikacje te obsługują pasek usługi Azure Information Protection, który jest instalowany z [klientem usługi Azure Information Protection](../rms-client/aip-client.md). Ten pasek wyświetla etykiety, które ułatwiają użytkownikom automatyczne stosowanie ochrony usługi Rights Management do dokumentów i wiadomości e-mail zawierających poufne dane.

Jeśli chcesz już skonfigurować aplikacje pakietu Office i klienta usługi Azure Information Protection:

- Aby skonfigurować aplikacje pakietu Office, zobacz [Aplikacje pakietu Office: konfiguracja dla klientów](../deploy-use/configure-office-apps.md).

- Aby zainstalować i skonfigurować klienta usługi Azure Information Protection, zobacz [Klient usługi Azure Information Protection: instalacja i konfiguracja klienta](../deploy-use/configure-client.md).

## <a name="exchange-online-and-exchange-server"></a>Usługa Exchange Online i program Exchange Server
W przypadku używania usługi Exchange Online lub programu Exchange Server można zastosować integrację usług zarządzania prawami do informacji (IRM) i korzystać z dodatkowych rozwiązań w zakresie ochrony informacji:

-   **Protokół Exchange ActiveSync IRM** umożliwia urządzeniom przenośnym zabezpieczanie wiadomości e-mail i korzystanie z chronionych wiadomości.

-   Obsługa usługi RMS w aplikacji **Outlook Web App**, zaimplementowana podobnie jak w przypadku klienta programu Outlook, pozwala użytkownikom chronić wiadomości e-mail za pomocą szablonów lub przez określenie poszczególnych opcji oraz odczytywać chronione wiadomości e-mail, które są wysyłane do nich, i używać tych wiadomości.

-   **Reguły ochrony** dla klientów programu Outlook skonfigurowane przez administratora, aby umożliwić automatyczne stosowanie szablonów usługi Rights Management do wiadomości e-mail przeznaczonych dla określonych odbiorców. Na przykład wewnętrzne wiadomości e-mail wysyłane do działu prawnego mogą być odczytywane tylko przez personel działu prawnego i nie mogą być przesyłane dalej. Przed wysłaniem wiadomości e-mail użytkownicy mogą zobaczyć, jakie zabezpieczenia zostały w niej zastosowane, oraz usunąć tę ochronę zgodnie ze swoimi preferencjami. Wiadomości e-mail są szyfrowane przed ich wysłaniem. Więcej informacji zawierają artykuły dotyczące [reguł ochrony programu Outlook](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) oraz [tworzenia reguły ochrony programu Outlook](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) dostępne w bibliotece programu Exchange.

-   **Reguły transportu** skonfigurowane przez administratora, aby umożliwić automatyczne stosowanie szablonów usługi Rights Management do wiadomości e-mail na podstawie takich właściwości, jak nadawca, odbiorca, temat wiadomości i zawartość. Są one podobne do reguł ochrony, ale nie zezwalają użytkownikom na usuwanie zabezpieczeń. Reguły transportu nie powodują szyfrowania wiadomości e-mail przed ich wysłaniem z urządzenia klienckiego i można je stosować do programu Outlook Web Access oraz wiadomości e-mail wysyłanych za pomocą urządzeń przenośnych. Więcej informacji zawiera artykuł dotyczący [tworzenia reguły ochrony transportu](https://technet.microsoft.com/library/dd302432.aspx) dostępny w bibliotece programu Exchange.

-   **Zasady ochrony przed utratą danych (DLP)** zawierają zestawy warunków filtrowania wiadomości e-mail i umożliwiają podejmowanie działań w celu uniknięcia utraty poufnych lub wrażliwych informacji (na przykład informacji osobistych lub danych karty kredytowej). W przypadku wykrycia poufnych danych na podstawie informacji zawartych w wiadomości e-mail można używać porad dotyczących zasad w celu monitowania użytkowników o potencjalnej konieczności zastosowania ochrony informacji. Więcej informacji zawiera artykuł [Data loss prevention](https://technet.microsoft.com/library/jj150527(v=exchg.160).aspx) (Ochrona przed utratą danych) dostępny w bibliotece programu Exchange.

-   **Szyfrowanie wiadomości usługi Office 365** korzysta z reguł transportu do wysyłania zaszyfrowanych wiadomości e-mail do osób spoza firmy. Te wiadomości e-mail mogą być odczytywane w przeglądarce z interfejsem podobnym do aplikacji Outlook Web App. W firmowych, zaszyfrowanych wiadomościach e-mail można dostosować tekst klauzuli wyłączenia odpowiedzialności i tekst nagłówka, a nawet dodać logo firmy. Więcej informacji zawiera artykuł [Szyfrowanie wiadomości usługi Office 365](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx) dostępny w witrynie internetowej pakietu Office.

W przypadku korzystania z programu Exchange Server można użyć funkcji ochrony informacji dostępnych w usłudze Azure Rights Management, wdrażając łącznik usługi RMS, który działa jako przekaźnik między serwerami lokalnymi i usługą Azure Rights Management.

Jeśli chcesz już skonfigurować program Exchange dla usługi IRM:

- W przypadku usługi Exchange Online, zobacz artykuł [Usługa Exchange Online: konfiguracja usługi IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- W przypadku lokalnej instalacji programu Exchange, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).


## <a name="sharepoint-online-and-sharepoint-server"></a>Usługa SharePoint Online i program SharePoint Server

Korzystając z usługi SharePoint Online lub programu SharePoint Server, możesz chronić dokumenty przy użyciu usług zarządzania prawami do informacji (IRM). Ta konfiguracja pozwala administratorom chronić listy lub biblioteki, więc gdy użytkownik wyewidencjonuje dokument, pobrany plik pozostaje chroniony i tylko autoryzowane osoby mogą go wyświetlać i używać zgodnie z określonymi przez Ciebie zasadami ochrony informacji. Na przykład można przypisać plikowi właściwość tylko do odczytu albo uniemożliwić kopiowanie tekstu, zapisywanie lokalnej kopii pliku czy drukowanie jego zawartości.

Domyślnie ochrona jest ograniczona do osoby, która pobiera dokument. Można jednak to zmienić za pomocą opcji konfiguracji, która rozszerza ochronę na wszystkich użytkowników mających dostęp do dokumentu w programie SharePoint lub do określonej grupy.

W przypadku list i bibliotek programu SharePoint ochrona informacji jest zawsze konfigurowana przez administratora, nigdy przez użytkownika końcowego. Ustaw uprawnienia na poziomie witryny, a te uprawnienia domyślnie są dziedziczone przez wszystkie listy lub biblioteki w tej witrynie. W przypadku korzystania z usługi SharePoint Online użytkownicy mogą również skonfigurować ochronę usługi IRM w bibliotece usługi OneDrive dla Firm.

Dla dokładniejszej kontroli możesz skonfigurować w witrynie listę lub bibliotekę, aby zatrzymać dziedziczenie uprawnień z elementu nadrzędnego. Następnie możesz skonfigurować uprawnienia usługi IRM na tym samym poziomie (listy lub biblioteki), które będą wówczas określane jako „unikatowe uprawnienia”. Jednak uprawnienia są zawsze ustawiane na poziomie kontenera. Nie możesz ustawić uprawnień dla poszczególnych plików. 

Usługę IRM należy najpierw włączyć dla programu SharePoint. Następnie określ uprawnienia usługi IRM dla biblioteki. W przypadku usług SharePoint Online i OneDrive dla Firm użytkownicy mogą także określić uprawnienia usługi IRM do własnej biblioteki usługi OneDrive dla Firm. Program SharePoint nie korzysta z szablonów zasad praw, chociaż możesz wybrać określone ustawienia konfiguracji programu SharePoint, odpowiadające pewnym ustawieniom, które możesz określić za pomocą szablonów.

Jeśli używasz programu SharePoint Server, możesz użyć ochrony za pomocą usługi IRM, wdrażając łącznik usługi Azure Rights Management. Ten łącznik działa jako przekaźnik między Twoimi serwerami lokalnymi a usługą Rights Management w chmurze. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

> [!NOTE]
> Obecnie istnieją pewne ograniczenia dotyczące używania usługi IRM z programem SharePoint:
> 
> - Nie można używać domyślnych lub niestandardowych szablonów zarządzanych w witrynie Azure Portal. 
> 
> - Chronione pliki PDF z rozszerzeniem nazwy pliku PPDF nie są obsługiwane. Pliki z rozszerzeniem nazwy pliku PDF, które są natywnie chronione przez usługę Rights Management, są obsługiwane w przypadku używania czytnika plików PDF z natywną obsługą usługi Rights Management.
> 
> - Jeśli chroniony plik zostanie przekazany do biblioteki programu SharePoint lub usługi OneDrive dla firm, następujące funkcje nie będą działać z tym plikiem: współtworzenie, Office Online, indeksowanie i wyszukiwanie.

Podczas korzystania z ochrony za pomocą usługi IRM z programem SharePoint usługa Azure Rights Management stosuje ograniczenia dotyczące użycia i szyfrowanie danych względem dokumentów w trakcie ich pobierania z programu SharePoint, a nie w momencie ich utworzenia w programie SharePoint lub przekazania do biblioteki. Informacje dotyczące ochrony dokumentów przed ich pobraniem można znaleźć w artykule dotyczącym [szyfrowania danych w usługach OneDrive dla Firm i SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) dostępnym w dokumentacji programu SharePoint.

Następujący wpis na blogu pakietu Office, chociaż nie jest już nowy, zawiera pewne dodatkowe informacje, które mogą się okazać przydatne: [What’s New with Information Rights Management in SharePoint and SharePoint Online](https://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/) (Co nowego w usłudze Information Rights Management w programie SharePoint i usłudze SharePoint Online)

Jeśli chcesz już skonfigurować program SharePoint dla usługi IRM:

- W przypadku usługi SharePoint Online, zobacz [SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration).

- W przypadku programu SharePoint Server, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).


## <a name="next-steps"></a>Następne kroki

Jeśli masz usługę Office 365, może zainteresować Cię artykuł dotyczący [rozwiązań do ochrony plików w usłudze Office 365](https://technet.microsoft.com/library/dn919927.aspx#BKMK_O365fileprotect), w którym opisano zalecane możliwości ochrony plików w usłudze Office 365.

Aby dowiedzieć się, jak inne aplikacje i usługi obsługują usługę Azure Rights Management w ramach usługi Azure Information Protection, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md).

Jeśli chcesz rozpocząć wdrażanie, co obejmuje skonfigurowanie tych aplikacji i usług, zobacz [Plan wdrażania usługi Azure Information Protection](../plan-design/deployment-roadmap.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]