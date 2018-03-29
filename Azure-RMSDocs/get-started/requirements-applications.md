---
title: Aplikacje obsługujące ochronę danych za pomocą usługi RMS — AIP
description: Identyfikowanie aplikacji, które korzystają z interfejsów API usługi RMS w celu natywnej obsługi usługi Azure Rights Management w ramach usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/28/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 27187bce4247b2807b75ddc75839daf81a45ed7a
ms.sourcegitcommit: aca094874febf59eddf84b0da325f4f1f61404d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="applications-that-support-azure-rights-management-data-protection"></a>Aplikacje obsługujące ochronę danych usługi Azure Rights Management

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Użyj następujących tabel, aby zidentyfikować aplikacje i rozwiązania, które natywnie obsługują usługę Azure Rights Management (Azure RMS) zapewniającą ochronę danych dla usługi Azure Information Protection.

W przypadku tych aplikacji i rozwiązań obsługa usługi Rights Management jest ściśle zintegrowana za pomocą interfejsów API usługi Rights Management w celu umożliwienia obsługi ograniczeń użycia. Te aplikacje i rozwiązania są również określane jako „aplikacje i rozwiązania z obsługą usług RMS”.

O ile nie wskazano inaczej, obsługiwane możliwości dotyczą zarówno usługi Azure RMS, jak i AD RMS. Ponadto obsługa usług AD RMS w systemach iOS, Android, macOS i Windows Phone 8.1 wymaga [rozszerzenia usług Active Directory Rights Management Services dla urządzeń przenośnych](https://technet.microsoft.com/library/dn673574.aspx).

## <a name="rms-enlightened-applications"></a>Aplikacje z obsługą usług RMS

Poniższa tabela zawiera informacje na temat dostarczanych przez firmę Microsoft oraz dostawców oprogramowania aplikacji klienckich z obsługą usług RMS.

Informacje dotyczące kolumn tabeli:

-   **Chroniony plik PDF**: te pliki mają rozszerzenie nazwy pliku PDF lub PPDF.

-   **Poczta e-mail:** klienci poczty e-mail z listy mogą chronić wiadomości e-mail, co automatycznie umożliwia ochronę wszystkich dołączonych i do tej pory niechronionych plików pakietu Office. W tym scenariuszu funkcja podglądu klienta umożliwia wyświetlanie chronionej zawartości (wiadomości i załączników) autoryzowanym odbiorcom. Jednak jeśli sama wiadomość e-mail nie jest chroniona, ale załącznik jest, funkcja podglądu klienta nie ma możliwości wyświetlania chronionego załącznika autoryzowanym odbiorcom.

-   **Inne typy plików:** pliki tekstowe i pliki obrazów mają następujące rozszerzenia nazw: TXT, XML, JPG i JPEG. Rozszerzenia nazw tych plików zmieniają się po objęciu plików natywną ochroną zapewnianą przez usługę Rights Management, a pliki stają się plikami tylko do odczytu. Pliki, które nie mogą być chronione w sposób natywny, mają rozszerzenie nazwy pliku pfile, co oznacza, że zostały objęte ogólną ochroną przez usługę Rights Management. Aby uzyskać więcej informacji, zobacz sekcję [Obsługiwane typy plików](../rms-client/client-admin-guide-file-types.md) w podręczniku administratora klienta usługi Azure Information Protection.


|**System operacyjny urządzenia**|Word, Excel, PowerPoint|Chroniony plik PDF|Poczta e-mail|Inne typy plików|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Pakiet Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Office Online (wyświetlanie dokumentów chronionych) [[1]](#footnote-1)<br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Klient usługi Azure Information Protection dla systemu Windows <br /><br />Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />Aplikacja do udostępniania usługi RMS|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)<br /><br />Poczta systemu Windows [[4]](#footnote-4) |Klient usługi Azure Information Protection dla systemu Windows: tekst, obrazy, pliki PFILE<br /><br />Aplikacja RMS sharing dla systemu Windows: tekst, obrazy, plik PFILE<br /><br />Wtyczka SealPath RMS AutoCAD: .dwg|
|**iOS**|Office Mobile (wyświetlanie i edytowanie chronionych dokumentów)<br /><br />Office Online [[1]](#footnote-1)<br /><br />GigaTrust<br /><br /> TITUS Docs<br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Aplikację usługi Azure Information Protection (wyświetlanie dokumentów chronionych)<br /><br /> Foxit Reader<br /><br />TITUS Docs|Aplikację usługi Azure Information Protection (wyświetlanie chronionych wiadomości e-mail)<br /><br />Citrix WorxMail <br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Program Outlook dla urządzeń iPad i iPhone [[4]](#footnote-4)<br /><br />TITUS Mail <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Aplikację usługi Azure Information Protection (Ochrona tekst i obrazy wyświetlanie)<br /><br />TITUS Docs: plik PFILE|
|**Android**|Aplikacja GigaTrust dla systemu Android<br /><br />Office Online [[1]](#footnote-1)<br /><br />Office Mobile (wyświetlanie i edytowanie chronionych dokumentów) <br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Aplikację usługi Azure Information Protection (wyświetlanie dokumentów chronionych) <br /><br />Aplikacja GigaTrust dla systemu Android<br /><br />Foxit Reader|9Folders [[4]](#footnote-4)<br /><br />Aplikację usługi Azure Information Protection (wyświetlanie chronionych wiadomości e-mail)<br /><br />Aplikacja GigaTrust dla systemu Android [[4]](#footnote-4)<br /><br />Citrix WorxMail <br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Aplikacja Outlook dla systemu Android [[4]](#footnote-4)<br /><br />Poczta E-mail Samsung (S3 i nowsze) [[4]](#footnote-4)<br /><br />TITUS Classification for Mobile <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Aplikację usługi Azure Information Protection (wyświetlanie chroniony tekst i obrazy)|
|**macOS**|Office 2011 (tylko usługi AD RMS)<br /><br />Office 2016 dla komputerów Mac<br /><br />Office Online [[1]](#footnote-1)<br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Foxit Reader<br /><br />(Wyświetlanie dokumentów chronionych) aplikacja RMS sharing|Outlook 2011 (tylko usługi AD RMS)<br /><br />Outlook 2016 dla komputerów Mac<br /><br />Outlook dla komputerów Mac <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Aplikacji (wyświetlanie chroniony tekst, obrazy, pliki objęte ochroną) do udostępniania usług RMS|
|**Windows 10 Mobile**|Aplikacje mobilne pakietu Office (wyświetlanie dokumentów chronionych za pomocą usługi Azure RMS) <br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Nieobsługiwane|Citrix WorxMail <br /><br />Poczta programu Outlook (wyświetlanie chronionych wiadomości e-mail) <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Nieobsługiwane|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[1]](#footnote-1)<br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Nieobsługiwane|Outlook 2013 RT<br /><br />Aplikacja poczty dla systemu Windows<br /><br />Przeglądarki sieci Web [[3]](#footnote-3)<br /><br />Poczta systemu Windows [[4]](#footnote-4)|Siemens JT2Go: pliki JT|
|**Windows Phone 8.1**|Office Mobile (tylko usługi AD RMS)<br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|(Wyświetlanie dokumentów chronionych) aplikacja RMS sharing|Outlook Mobile [[4]](#footnote-4) <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Aplikacji (wyświetlanie chroniony tekst, obrazy, pliki objęte ochroną) do udostępniania usług RMS|
|**Blackberry 10**|Przeglądarki sieci Web [[2]](#footnote-2)|Nieobsługiwane|Poczta e-mail Blackberry [[4]](#footnote-4) <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Nieobsługiwane|


###### <a name="footnote-1"></a>Przypis 1
Obsługiwany tylko w przypadku usługi SharePoint Online i OneDrive dla firm i dokumenty są chronione przed są przekazywane do bibliotek chronionych.

###### <a name="footnote-2"></a>Przypis 2
Dla [załączników Office](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) które są chronione przy użyciu [szyfrowanie wiadomości usługi Office 365 z nowych funkcji](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

###### <a name="footnote-3"></a>Przypis 3
Jeżeli nadawca i odbiorca są częścią tej samej organizacji. Lub jeden z następujących warunków:

- Nadawca i odbiorca korzystają z usługi Exchange Online.

- Nadawca używa lokalnego programu Exchange w konfiguracji hybrydowego. 

###### <a name="footnote-4"></a>Przypis 4
Używa funkcji Exchange ActiveSync IRM, którą musi włączyć administrator programu Exchange. Użytkownicy mogą wyświetlać, odpowiedzi i opowiadać wszystkim chronione wiadomości e-mail, ale użytkownicy nie mogą chronić nowych wiadomości e-mail.
 
Jeśli aplikacja poczty e-mail nie można renderować komunikatu, ponieważ nie włączono funkcji Exchange ActiveSync IRM, adresat może wyświetlić wiadomości e-mail w przeglądarce sieci web, gdy nadawca używa usługi Exchange Online lub do lokalnego programu Exchange w konfiguracji hybrydowego. 



### <a name="more-information-about-azure-rms-support-for-office"></a>Więcej informacji na temat obsługi usługi Azure RMS dla pakietu Office

Usługa Azure RMS jest ściśle zintegrowana z aplikacjami Word, Excel, PowerPoint i Outlook, w których ta funkcja jest często określana jako Zarządzanie prawami do informacji (IRM, Information Rights Management). 

Następujące pakiety klienta pakietu Office obsługują ochronę plików i wiadomości e-mail na komputerach z systemem Windows przy użyciu usługi Azure RMS:

- Usługa Office 365 ProPlus: pakiety Office 2016 i Office 2013
    
    Te wersje pakietu Office są dołączone do większości, ale nie wszystkie subskrypcji usługi Office 365, które obejmują ochronę danych z usługi Azure Information Protection. Sprawdź swoje informacje subskrypcji, aby sprawdzać, czy usługi Office 365 ProPlus uwzględnione. Zawiera ona również te informacje w [arkusz danych usługi Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010 z dodatkiem Service Pack 2

Wszystkie wersje pakietu Office (z wyjątkiem pakietu Office 2007) obsługują chronioną zawartość.

Usługa Azure RMS z pakietem Office Professional Plus 2010 z dodatkiem Service Pack 2 lub pakietem Office Professional 2010 z dodatkiem Service Pack 2:

- Wymaga klienta usługi Azure Information Protection dla systemu Windows lub aplikacji do udostępniania usługi Rights Management dla systemu Windows.

- Nie są obsługiwane w systemie Windows 10.

- Nie obsługuje uwierzytelniania opartego na formularzach dla kont użytkowników federacyjnych. Te konta muszą korzystać z uwierzytelniania zintegrowane systemu Windows.

- Nie obsługuje zastępowanie ochrony szablonu z uprawnień niestandardowych, które użytkownik wybiera z klientem usługi Azure Information Protection. W tym scenariuszu najpierw należy usunąć oryginalną ochronę aby można było zastosować uprawnienia niestandardowe.

Następujące pakiety klienta pakietu Office obsługują ochronę plików i wiadomości e-mail w systemie macOS przy użyciu usługi Azure RMS:

- Office 365 ProPlus: Office 2016

- Office Standard 2016 dla komputerów Mac

Zobacz również: [Office Applications Service Description](https://technet.microsoft.com/library/office-applications-service-description.aspx) (Opis usługi aplikacji pakietu Office)

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>Więcej informacji na temat aplikacji Azure Information Protection dla systemów iOS i Android

Aplikacja RMS sharing dla systemu iOS i Android została zastąpiona przez aplikację Azure Information Protection. Zawiera ona te same funkcje i dodatkowo obsługuje chronione prawami wiadomości e-mail i pliki PDF w usłudze SharePoint Online.

Jeśli Twoje urządzenia z systemami iOS i Android są zarejestrowane w usłudze Microsoft Intune, możesz wdrożyć tę aplikację i zarządzać nią za pomocą aplikacji zarządzanej przez zasady. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i wdrażanie zasad zarządzania aplikacjami mobilnymi w konsoli usługi Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) w dokumentacji usługi Intune. W kroku 2 tej dokumentacji usługi Intune należy skorzystać z instrukcji dotyczących publikowania aplikacji zarządzanej przez zasady.

Aby uzyskać więcej informacji, zobacz [FAQ for Microsoft Azure Information Protection app for iOS and Android](../rms-client/mobile-app-faq.md) (Aplikacja Microsoft Azure Information Protection dla systemów iOS i Android — często zadawane pytania).


### <a name="more-information-about-the-azure-information-protection-client-for-windows"></a>Więcej informacji na temat klienta usługi Azure Information Protection dla systemu Windows

Klient zastępuje aplikację RMS sharing dla systemu Windows.

Więcej informacji można znaleźć w następujących zasobach:

- [Podręcznik administratora klienta usługi Azure Information Protection](../rms-client/client-admin-guide.md)

- [Podręcznik użytkownika klienta usługi Azure Information Protection](../rms-client/client-user-guide.md)

- [Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android](../rms-client/mobile-app-faq.md)

Pobierz odpowiednią aplikację, korzystając z linków na [stronie usługi Microsoft Azure Information Protection](http://go.microsoft.com/fwlink/?LinkId=303970).

### <a name="more-information-about-the-rights-management-sharing-application"></a>Więcej informacji na temat aplikacji do udostępniania usługi Rights Management

Ta aplikacja zostaje zastąpiona przez klienta usługi Azure Information Protection. Nadal zaleca się korzystanie z niej na komputerach Mac i urządzeniach z systemem Windows Phone.

Więcej informacji można znaleźć w następujących zasobach:

-   [Przewodnik administratora aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-admin-guide.md)

-   [Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-user-guide.md)

-   [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Microsoft Rights Management dla platform urządzeń przenośnych](https://technet.microsoft.com/dn451248)

Pobierz aplikację dla komputerów Mac i urządzeń Windows Phone, korzystając z linków na [stronie usługi Microsoft Azure Information Protection ](http://go.microsoft.com/fwlink/?LinkId=303970).


### <a name="more-information-about-other-applications-that-support-azure-information-protection"></a>Więcej informacji o innych aplikacjach, które obsługują usługę Azure Information Protection

Poza aplikacjami z tabeli z usługą Azure Information Protection może zostać zintegrowana także każda aplikacja, która obsługuje interfejsy API dla usługi Azure Rights Management, w tym:

- Aplikacje biznesowe tworzone w firmach za pomocą zestawów RMS SDK

- Aplikacje od dostawców oprogramowania napisane przy użyciu zestawów RMS SDK.

Aby uzyskać więcej informacji, zobacz [przewodnik dewelopera usługi Azure Information Protection](../develop/developers-guide.md).

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Aplikacje, które nie są obsługiwane przez usługi Azure RMS

Następujące aplikacje nie są obecnie obsługiwane przez usługę Azure RMS:

-   Microsoft Office 2011 dla komputerów Mac

-   Microsoft OneDrive dla Firm dla programu SharePoint Server 2013

-   Przeglądarka plików XPS

Ponadto aplikacji RMS sharing i klienta usługi Azure Information Protection dotyczą następujące ograniczenia:

-   W przypadku komputerów z systemem Windows: wymaga co najmniej systemu Windows 7 z dodatkiem Service Pack 1

## <a name="rms-enlightened-solutions"></a>Rozwiązania z obsługą usług RMS

Poniższa tabela zawiera informacje na temat dostarczanych przez dostawców oprogramowania rozwiązań z obsługą usług RMS.

Jeśli jesteś dostawcą oprogramowania i dysponujesz rozwiązaniem, które nie zostało wymienione w tej tabeli, zarejestruj swoją aplikację w usłudze Azure AD. Aby uzyskać więcej informacji, zobacz artykuł [Jak zarejestrować aplikację w usłudze Azure AD i włączyć dla niej obsługę usługi RMS](../develop/authentication-integration.md).


|Produkt|Dostawca|Opis|
|-------------------------------|---------------------------|-----------------|
|Bezwzględne|Bezwzględne|Ochrona przed utratą danych (DLP) zapewniająca ochronę zawartości.|
|Content Locker|VMware|Zapisywanie, używanie i tworzenie chronionej zawartości.|
|Controle|TakeControle|Zbieranie elektronicznych materiałów dowodowych poprzez etykietowanie i ochronę.|
|Forcepoint|Forcepoint DLP|Punkt końcowy utraty zapobiegania (DLP) rozwiązania danych wymuszać zasady zabezpieczeń danych organizacji.|
|Halocore|Secude|Ochrona plików wyeksportowanych ze środowisk SAP.|
|MaaS 360|IBM|Integracja w celu umożliwienia użycia i ochrony dokumentów.|
|Mobiliya|Mobiliya|Zabezpiecza dokumenty z repozytoriów Documentum firmy EMC.
|Ramessys|Ramessys|Integracja pod kątem obsługi produktów Chemcart i Documentum.
|Sealpath|Sealpath Technologies|Integracja z narzędziami projektowymi CAD, takimi jak AutoCAD i Siemens Jt2GO.
|SecRMM|Sqaudra Technologies |Ochrona dokumentów z nośników wymiennych.
|Security Sheriff|CryptZone |Zarządzanie dostępem w usłudze SharePoint i ochrona dokumentów w oparciu o ich klasyfikację i uprawnienia dostępu.
|Ochrona przed utratą danych firmy Symantec|Symantec |Wykrywanie i monitorowanie plików chronionych.

## <a name="next-steps"></a>Następne kroki
Aby sprawdzić pozostałe wymagania, zobacz [Requirements for Azure Information Protection](requirements-azure-rms.md) (Wymagania dotyczące usługi Azure Information Protection).

Aby uzyskać informacje o obsłudze usługi Azure RMS przez najczęściej używane aplikacje, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md).

Informacje o sposobach konfigurowania najczęściej używanych aplikacji dla usługi Azure RMS opisano w temacie [Konfigurowanie aplikacji dla usługi Azure Rights Management](../deploy-use/configure-applications.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
