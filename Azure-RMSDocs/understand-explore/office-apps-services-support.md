---
title: "Aplikacje i usługi pakietu Office | Azure Information Protection"
description: "Sposób, w jaki aplikacje pakietu Office dla użytkowników końcowych (takie jak Word, Excel, PowerPoint i Outlook) oraz usługi pakietu Office (na przykład Exchange i SharePoint) mogą używać usługi Azure Rights Management, aby chronić dane organizacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4cdac14d3a77ea7bcce23b914bc3be0a1f46d2b5
ms.openlocfilehash: d2d33329457e181b55489834daf595da81bc7ada


---


# <a name="office-applications-and-services"></a>Aplikacje i usługi pakietu Office

>*Dotyczy: Azure Information Protection, Office 365*

Aplikacje pakietu Office dla użytkowników końcowych (takie jak Word, Excel, PowerPoint i Outlook) oraz usługi pakietu Office (na przykład Exchange i SharePoint) mogą korzystać z usługi Azure Rights Management w ramach usługi Azure Information Protection, aby chronić dane organizacji.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Aplikacje pakietu Office: Word, Excel, PowerPoint i Outlook
Te aplikacje natywnie obsługują usługę Rights Management i korzystają z usług zarządzania prawami do informacji (IRM), pozwalając użytkownikom na stosowanie ochrony do zapisanego dokumentu lub wiadomości e-mail do wysłania. Użytkownicy mogą stosować szablony lub, w przypadku programu Word, Excel i PowerPoint, ściśle dostosowywać ustawienia dotyczące dostępu, uprawnień i ograniczeń użytkowania. 

Na przykład użytkownicy mogą tak skonfigurować dokument programu Word, aby był on dostępny tylko dla osób z danej organizacji. Można określić, czy arkusz kalkulacyjny programu Excel jest dostępny do edycji lub ograniczyć jego właściwości tylko do odczytu albo uniemożliwić jego drukowanie. W przypadku plików ważnych przez określony czas można skonfigurować czas wygaśnięcia (bezpośrednio przez działania użytkowników lub przez zastosowanie szablonu), po upływie którego dostęp do pliku nie będzie już możliwy. W przypadku programu Outlook, oprócz możliwości wyboru szablonu, użytkownicy mogą wybrać opcję **Nie przekazuj**, która zapobiega wyciekowi danych.

Oprócz natywnych Usług zarządzania prawami do informacji (IRM), aplikacje te obsługują pasek usługi Azure Information Protection, który jest instalowany z [klientem usługi Azure Information Protection](../rms-client/aip-client.md ). Ten pasek wyświetla etykiety, które ułatwiają użytkownikom automatyczne stosowanie ochrony usługi Rights Management do dokumentów i wiadomości e-mail zawierających poufne dane.

## <a name="exchange-online-and-exchange-server"></a>Usługa Exchange Online i program Exchange Server
W przypadku używania usługi Exchange Online lub programu Exchange Server można zastosować integrację usług zarządzania prawami do informacji (IRM) i korzystać z dodatkowych rozwiązań w zakresie ochrony informacji:

-   **Protokół Exchange ActiveSync IRM** umożliwia urządzeniom przenośnym zabezpieczanie wiadomości e-mail i korzystanie z chronionych wiadomości.

-   Obsługa usługi RMS w aplikacji **Outlook Web App**, zaimplementowana podobnie jak w przypadku klienta programu Outlook, pozwala użytkownikom chronić wiadomości e-mail za pomocą szablonów lub przez określenie poszczególnych opcji oraz odczytywać chronione wiadomości e-mail, które są wysyłane do nich, i używać tych wiadomości.

-   **Reguły ochrony** dla klientów programu Outlook skonfigurowane przez administratora, aby umożliwić automatyczne stosowanie szablonów usługi Rights Management do wiadomości e-mail przeznaczonych dla określonych odbiorców. Na przykład wewnętrzne wiadomości e-mail wysyłane do działu prawnego mogą być odczytywane tylko przez personel działu prawnego i nie mogą być przesyłane dalej. Przed wysłaniem wiadomości e-mail użytkownicy mogą zobaczyć, jakie zabezpieczenia do niej zastosowano, i — domyślnie — mogą je usunąć zgodnie ze swoimi preferencjami. Wiadomości e-mail są szyfrowane przed ich wysłaniem. Więcej informacji zawierają artykuły dotyczące [reguł ochrony programu Outlook](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) oraz [tworzenia reguły ochrony programu Outlook](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) dostępne w bibliotece programu Exchange.

-   **Reguły transportu** skonfigurowane przez administratora, aby umożliwić automatyczne stosowanie szablonów usługi Rights Management do wiadomości e-mail na podstawie takich właściwości, jak nadawca, odbiorca, temat wiadomości i zawartość. Są one podobne do reguł ochrony, ale nie zezwalają użytkownikom na usuwanie zabezpieczeń. Reguły transportu nie powodują szyfrowania wiadomości e-mail przed ich wysłaniem z urządzenia klienckiego i można je stosować do programu Outlook Web Access oraz wiadomości e-mail wysyłanych za pomocą urządzeń przenośnych. Więcej informacji zawiera artykuł dotyczący [tworzenia reguły ochrony transportu](https://technet.microsoft.com/library/dd302432.aspx) dostępny w bibliotece programu Exchange.

-   **Zasady ochrony przed utratą danych (DLP)** zawierają zestawy warunków filtrowania wiadomości e-mail i umożliwiają podejmowanie działań w celu uniknięcia utraty poufnych lub wrażliwych informacji (na przykład informacji osobistych lub danych karty kredytowej). W przypadku wykrycia poufnych danych na podstawie informacji zawartych w wiadomości e-mail można używać porad dotyczących zasad w celu monitowania użytkowników o potencjalnej konieczności zastosowania ochrony informacji. Więcej informacji zawiera artykuł dotyczący [ochrony przed utratą danych](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) dostępny w bibliotece programu Exchange.

-   **Szyfrowanie wiadomości usługi Office 365** korzysta z reguł transportu do wysyłania zaszyfrowanych wiadomości e-mail do osób spoza firmy. Te wiadomości e-mail mogą być odczytywane w przeglądarce z interfejsem podobnym do aplikacji Outlook Web App. W firmowych, zaszyfrowanych wiadomościach e-mail można dostosować tekst klauzuli wyłączenia odpowiedzialności i tekst nagłówka, a nawet dodać logo firmy. Więcej informacji zawiera artykuł [Szyfrowanie wiadomości usługi Office 365](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx) dostępny w witrynie internetowej pakietu Office.

W przypadku korzystania z programu Exchange Server można użyć funkcji ochrony informacji dostępnych w usłudze Azure Rights Management, wdrażając łącznik usługi RMS, który działa jako przekaźnik między serwerami lokalnymi i usługą Azure Rights Management. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

## <a name="sharepoint-online-and-sharepoint-server"></a>Usługa SharePoint Online i program SharePoint Server
W przypadku używania usługi Exchange Online lub programu SharePoint Server można zastosować integrację usług zarządzania prawami do informacji (IRM), co pozwala administratorom chronić listy lub biblioteki. Gdy użytkownik wyewidencjonuje dokument, plik pozostaje chroniony i tylko autoryzowane osoby mogą go wyświetlać i używać zgodnie z określonymi zasadami ochrony informacji. Na przykład można przypisać plikowi właściwość tylko do odczytu albo uniemożliwić kopiowanie tekstu, zapisywanie lokalnej kopii pliku czy drukowanie jego zawartości.

W przypadku list i bibliotek ochrona informacji jest zawsze włączana przez administratora, nigdy przez użytkownika końcowego. Dodatkowo ochrona nie dotyczy poszczególnych plików, ale jest stosowana na poziomie listy lub biblioteki i obejmuje wszystkie dokumenty znajdujące się w danym kontenerze.  W przypadku korzystania z usługi SharePoint Online użytkownicy mogą również stosować usługę IRM w bibliotece usługi OneDrive dla Firm.

Usługę IRM należy najpierw włączyć dla programu SharePoint. Następnie konfiguruje się usługę zarządzania prawami do informacji dla biblioteki. W przypadku usług SharePoint Online i OneDrive dla Firm użytkownicy mogą także stosować usługę zarządzania prawami do informacji w bibliotece usługi OneDrive dla Firm. Program SharePoint nie korzysta z szablonów zasad praw, chociaż można wybrać określone ustawienia konfiguracji programu SharePoint, ściśle odpowiadające ustawieniom, które można określić za pomocą szablonów.

W przypadku korzystania z programu SharePoint Server można użyć funkcji ochrony informacji dostępnych w usłudze Azure Rights Management, wdrażając łącznik usługi RMS, który działa jako przekaźnik między serwerami lokalnymi i usługą Rights Management w chmurze. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

> [!NOTE]
> Obecnie istnieją pewne ograniczenia dotyczące używania usługi IRM z programem SharePoint:
> 
> - Nie można używać domyślnych lub niestandardowych szablonów zarządzanych w klasycznym portalu Azure.
> - Chronione pliki PDF z rozszerzeniem nazwy pliku PPDF nie są obsługiwane. Pliki z rozszerzeniem nazwy pliku PDF, które są natywnie chronione przez usługę Rights Management, są obsługiwane w przypadku używania czytnika plików PDF z natywną obsługą usługi Rights Management.


Zastosowanie ograniczeń dotyczących użycia i szyfrowania danych przez usługę Azure Rights Management następuje podczas pobierania dokumentów z programu SharePoint, a nie w momencie ich utworzenia w programie SharePoint lub przekazania do biblioteki. Informacje dotyczące ochrony dokumentów przed ich pobraniem można znaleźć w artykule dotyczącym [szyfrowania danych w usługach OneDrive dla Firm i SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) dostępnym w dokumentacji programu SharePoint.

Więcej informacji o korzystaniu z usługi Azure Rights Management z programem SharePoint można znaleźć w następującym wpisie na blogu pakietu Office: [What’s New with Information Rights Management in SharePoint and SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/) (Co nowego w usłudze zarządzania prawami do informacji programu SharePoint i usługi SharePoint Online)

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się, jak inne aplikacje i usługi obsługują usługę Azure Rights Management w ramach usługi Azure Information Protection, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Feb17_HO2-->


