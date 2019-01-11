---
title: Aplikacje obsługujące ochronę danych za pomocą usługi RMS — AIP
description: Identyfikowanie aplikacji, które korzystają z interfejsów API usługi RMS w celu natywnej obsługi usługi Azure Rights Management w ramach usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/15/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 51883da128580be5f6bfd4dd725b8dfdf10f844f
ms.sourcegitcommit: 5b48131ace3bbaf82f22fcb7eedf735c2f73d962
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429886"
---
# <a name="applications-that-support-azure-rights-management-data-protection"></a>Aplikacje obsługujące ochronę danych usługi Azure Rights Management

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Użyj następujących tabel, aby zidentyfikować aplikacje i rozwiązania, które natywnie obsługują usługę Azure Rights Management (Azure RMS) zapewniającą ochronę danych dla usługi Azure Information Protection.

W przypadku tych aplikacji i rozwiązań obsługa usługi Rights Management jest ściśle zintegrowana za pomocą interfejsów API usługi Rights Management w celu umożliwienia obsługi ograniczeń użycia. Te aplikacje i rozwiązania są również określane jako „aplikacje i rozwiązania z obsługą usług RMS”.

O ile nie wskazano inaczej, obsługiwane możliwości dotyczą zarówno usługi Azure RMS, jak i AD RMS. Ponadto obsługa usług AD RMS w systemach iOS, Android, macOS i Windows Phone 8.1 wymaga [Active Directory Rights zarządzania rozszerzenia usług urządzeń przenośnych](https://technet.microsoft.com/library/dn673574.aspx).

## <a name="rms-enlightened-applications"></a>Aplikacje z obsługą usług RMS

Poniższa tabela zawiera informacje na temat dostarczanych przez firmę Microsoft oraz dostawców oprogramowania aplikacji klienckich z obsługą usług RMS. 

Informacje o przeglądaniu chronionych dokumentów PDF, zobacz [czytelnicy chronione pliki PDF Microsoft Information Protection](./rms-client/protected-pdf-readers.md).

Informacje dotyczące kolumn tabeli:

-   **Adres e-mail:** Klienci poczty e-mail, które są wymienione mogą chronić wiadomości e-mail, co automatycznie umożliwia ochronę wszystkich dołączonych plików pakietu Office, które nie są już chronione. W tym scenariuszu funkcja podglądu klienta umożliwia wyświetlanie chronionej zawartości (wiadomości i załączników) autoryzowanym odbiorcom. Jednak jeśli sama wiadomość e-mail nie jest chroniona, ale załącznik jest, funkcja podglądu klienta nie ma możliwości wyświetlania chronionego załącznika autoryzowanym odbiorcom. 
    
    Porada: Do obsługi poczty e-mail klientów, które nie obsługują ochrona wiadomości e-mail, należy rozważyć użycie [usługi Exchange Online reguły przepływu poczty, aby zastosować tę ochronę](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8).

-   **Inne typy plików**: Plików tekstowych i obrazów obejmują pliki, które mają rozszerzenie nazwy pliku, takie jak txt, XML, jpg i JPEG. Rozszerzenia nazw tych plików zmieniają się po objęciu plików natywną ochroną zapewnianą przez usługę Rights Management, a pliki stają się plikami tylko do odczytu. Pliki, które nie mogą być chronione w sposób natywny, mają rozszerzenie nazwy pliku pfile, co oznacza, że zostały objęte ogólną ochroną przez usługę Rights Management. Aby uzyskać więcej informacji, zobacz sekcję [Obsługiwane typy plików](./rms-client/client-admin-guide-file-types.md) w podręczniku administratora klienta usługi Azure Information Protection.


|**System operacyjny urządzenia**|Word, Excel, PowerPoint|Email|Inne typy plików|
|---------------------------|-----------------------|-----------------|---------|
|**Windows**|Pakiet Office 2010<br /><br />Pakiet Office 2013<br /><br />Office 2016 <br /><br />Office Online (wyświetlanie chronionych dokumentów) [[1]](#footnote-1)<br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Program Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)<br /><br />Poczta systemu Windows [[4]](#footnote-4) |Klient usługi Azure Information Protection dla Windows: Tekst, obrazy, pliki pfile<br /><br />Aplikacja RMS sharing dla Windows: Tekst, obrazy, pliki pfile<br /><br />Wtyczka SealPath RMS dla programu AutoCAD: .dwg|
|**iOS**|GigaTrust<br /><br /> Office Mobile (wyświetlanie i edytowanie chronionych dokumentów)<br /><br />Office Online [[1]](#footnote-1)<br /><br />TITUS Docs<br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Aplikacja Azure Information Protection (wyświetlanie chronionej wiadomości e-mail)<br /><br />Praca blackBerry<br /><br />Citrix WorxMail <br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Program Outlook dla urządzeń iPad i iPhone [[4]](#footnote-4)<br /><br />TITUS Mail <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Aplikacja Azure Information Protection (Ochrona tekst i obrazy wyświetlania)<br /><br />TITUS Docs: Pfile|
|**Android**|Aplikacja Gigatrust dla systemu Android<br /><br />Office Online [[1]](#footnote-1)<br /><br />Office Mobile <br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|9Folders [[4]](#footnote-4)<br /><br />Aplikacja Azure Information Protection (wyświetlanie chronionych wiadomości e-mail)<br /><br />Praca blackBerry <br /><br />Aplikacja Gigatrust dla systemu Android [[4]](#footnote-4)<br /><br />Citrix WorxMail <br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Aplikacja Outlook dla systemu Android [[4]](#footnote-4)<br /><br />Poczta E-mail Samsung (warstwa S3 i nowsze) [[4]](#footnote-4)<br /><br />TITUS Classification for Mobile <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Aplikacja Azure Information Protection (wyświetlanie chroniony tekst i obrazy)|
|**macOS**|Office 2016 dla komputerów Mac<br /><br />Office Online [[1]](#footnote-1)<br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Outlook 2016 dla komputerów Mac<br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Aplikacja (wyświetlanie chroniony tekst, obrazy, pliki objęte ochroną) RMS sharing|
|**Windows 10 Mobile**|Aplikacje mobilne pakietu Office (wyświetlanie chronionych dokumentów za pomocą usługi Azure RMS) <br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Citrix WorxMail <br /><br />Poczta programu Outlook (wyświetlanie chronionych wiadomości e-mail) <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Nieobsługiwane|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[1]](#footnote-1)<br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Outlook 2013 RT<br /><br />Aplikacja poczty dla systemu Windows<br /><br />Przeglądarki sieci Web [[3]](#footnote-3)<br /><br />Poczta systemu Windows [[4]](#footnote-4)|Siemens JT2Go: Pliki JT|
|**Windows Phone 8.1**|Office Mobile (tylko usługi AD RMS)<br /><br />Przeglądarki sieci Web [[2]](#footnote-2)|Outlook Mobile [[4]](#footnote-4) <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Aplikacja (wyświetlanie chroniony tekst, obrazy, pliki objęte ochroną) RMS sharing|
|**Blackberry 10**|Przeglądarki sieci Web [[2]](#footnote-2)|Poczta e-mail Blackberry [[4]](#footnote-4) <br /><br />Przeglądarki sieci Web [[3]](#footnote-3)|Nieobsługiwane|

###### <a name="footnote-1"></a>Przypis 1
Obsługiwane tylko w przypadku usługi SharePoint Online i OneDrive dla firm i dokumenty są chronione przed są przekazywane do chronionej biblioteki usług.

###### <a name="footnote-2"></a>Przypis 2
Dla [załączniki Office](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) które są chronione przy użyciu [szyfrowanie wiadomości usługi Office 365 dzięki nowym funkcjom](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

###### <a name="footnote-3"></a>Przypis 3
Jeżeli nadawca i odbiorca są częścią tej samej organizacji. Lub jeden z następujących warunków:

- Nadawca i odbiorca korzystają z usługi Exchange Online.

- Nadawca używa lokalnego programu Exchange w ramach konfiguracji hybrydowych. 

###### <a name="footnote-4"></a>Przypis 4
Używa funkcji Exchange ActiveSync IRM, którą musi włączyć administrator programu Exchange. Użytkownicy mogą przeglądać, odpowiedzi i odpowiedzi, że wszystkie dla chronionych wiadomości e-mail, ale użytkownicy nie mogą chronić nowych wiadomości e-mail.
 
Jeśli nie można renderować wiadomości w aplikacji poczty e-mail, ponieważ nie włączono funkcji Exchange ActiveSync IRM, adresat może wyświetlić wiadomość e-mail w przeglądarce sieci web, gdy nadawca korzysta z usługi Exchange Online lub lokalnego programu Exchange w ramach konfiguracji hybrydowych. 



### <a name="more-information-about-azure-rms-support-for-office"></a>Więcej informacji na temat obsługi usługi Azure RMS dla pakietu Office

Usługa Azure RMS jest ściśle zintegrowana z aplikacjami Word, Excel, PowerPoint i Outlook, w których ta funkcja jest często określana jako Zarządzanie prawami do informacji (IRM, Information Rights Management). 

Patrz również: [Opis usługi aplikacji pakietu Office](https://technet.microsoft.com/library/office-applications-service-description.aspx)

#### <a name="windows-computers-for-information-rights-management-irm"></a>Komputery Windows Zarządzanie prawami informacji (IRM)

Następujące pakiety klienta pakietu Office obsługują ochronę plików i wiadomości e-mail na komputerach Windows za pomocą usługi Azure Rights Management:

- Usługa Office 365 z aplikacji pakietu Office 2016 (minimalna wersja 1805, kompilacja 9330.2078) po użytkownik ma przypisaną licencję usługi Azure Rights Management (nazywanego także usługi Azure Information Protection dla usługi Office 365)

- Usługi Office 365 ProPlus: Pakiety Office 2016 i Office 2013
    
    Te wersje pakietu Office są dołączane do większości, ale nie wszystkie subskrypcje usługi Office 365, które obejmują funkcji ochrony danych z usługi Azure Information Protection. Sprawdzanie informacji o subskrypcji, aby sprawdzić, czy jest dołączone usługi Office 365 ProPlus warunki. Można również znaleźć te informacje w [arkusz danych usługi Azure Information Protection](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010 z dodatkiem Service Pack 2

Wszystkie wersje pakietu Office (z wyjątkiem pakietu Office 2007) obsługują chronioną zawartość.

Kiedy używasz usługi Azure Rights Management przy użyciu pakietu Office Professional Plus 2010 i dodatkiem Service Pack 2 lub Office Professional 2010 z dodatkiem Service Pack 2:

- Wymaga klienta usługi Azure Information Protection, Windows lub aplikacji do udostępniania usługi Rights Management dla Windows.

- Nie są obsługiwane w systemie Windows 10.

- Nie obsługuje uwierzytelniania opartego na formularzach dla kont użytkowników federacyjnych. Te konta muszą korzystać z uwierzytelniania zintegrowane systemu Windows.

- Nie obsługuje nadrzędnych ochrony szablonu przy użyciu uprawnień niestandardowych, które użytkownik wybierze za pomocą klienta usługi Azure Information Protection. W tym scenariuszu najpierw należy usunąć oryginalną ochronę można było zastosować uprawnienia niestandardowe.

#### <a name="mac-computers-for-information-rights-management-irm"></a>Komputery Mac Zarządzanie prawami informacji (IRM)

Następujące pakiety klienta pakietu Office obsługują ochronę plików i wiadomości e-mail w systemie macOS przy użyciu usługi Azure RMS:

- Usługi Office 365 ProPlus: Office 2016

- Office Standard 2016 dla komputerów Mac

Wszystkie wersje pakietu Office 2016 dla komputerów Mac pomocy technicznej co umożliwia korzystanie z zawartości chronionej.

Porada: Aby rozpocząć pracę z ochrona dokumentów za pomocą pakietu Office dla komputerów Mac, może być przydatne następujące często zadawane pytania: [Jak skonfigurować komputer Mac, aby chronić i śledzić dokumenty?](faqs-rms.md#how-do-i-configure-a-mac-computer-to-protect-and-track-documents)

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>Więcej informacji na temat aplikacji Azure Information Protection dla systemów iOS i Android

Aplikacja przeglądarki usługi Azure Information Protection dla systemów iOS i Android zastępuje aplikację RMS sharing dla tych urządzeń. Zawiera ona te same funkcje i dodatkowo obsługuje chronione prawami wiadomości e-mail i pliki PDF w usłudze SharePoint Online.

Jeśli Twoje urządzenia z systemami iOS i Android są zarejestrowane w usłudze Microsoft Intune, możesz wdrożyć tę aplikację i zarządzać nią za pomocą aplikacji zarządzanej przez zasady. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i wdrażanie zasad zarządzania aplikacjami mobilnymi w konsoli usługi Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) w dokumentacji usługi Intune. W kroku 2 tej dokumentacji usługi Intune należy skorzystać z instrukcji dotyczących publikowania aplikacji zarządzanej przez zasady.

Aby uzyskać więcej informacji, zobacz [FAQ for Microsoft Azure Information Protection app for iOS and Android](./rms-client/mobile-app-faq.md) (Aplikacja Microsoft Azure Information Protection dla systemów iOS i Android — często zadawane pytania).


### <a name="more-information-about-the-azure-information-protection-client-for-windows"></a>Więcej informacji na temat klienta usługi Azure Information Protection dla systemu Windows

Klient zastępuje aplikację RMS sharing dla systemu Windows.

Aby uzyskać więcej informacji, zobacz następujące zasoby:

- [Podręcznik administratora klienta usługi Azure Information Protection](./rms-client/client-admin-guide.md)

- [Podręcznik użytkownika klienta usługi Azure Information Protection](./rms-client/client-user-guide.md)

- [Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android](./rms-client/mobile-app-faq.md)

Pobierz odpowiednią aplikację, korzystając z linków na [stronie usługi Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970).

### <a name="more-information-about-the-rights-management-sharing-application"></a>Więcej informacji na temat aplikacji do udostępniania usługi Rights Management

Ta aplikacja zostaje zastąpiona przez klienta usługi Azure Information Protection. Jest nadal wymagane dla urządzeń przenośnych Windows Phone, wyświetlanie chronionych plików. 

Dla komputerów Mac oferuje przeglądarka chronionych plików PDF (ppdf) chroniony tekst, obrazy i objęte ochroną plików. Aplikacja RMS sharing dla komputerów Mac umożliwia również ochronę, pliki obrazów, ale nie w innych plikach. Aby chronić pliki pakietu Office, należy użyć pakietu Office dla komputerów Mac. 

Aby uzyskać więcej informacji, zobacz następujące zasoby:

-   [Przewodnik administratora aplikacji do udostępniania usługi Rights Management](./rms-client/sharing-app-admin-guide.md)

-   [Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](./rms-client/sharing-app-user-guide.md)

-   [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Microsoft Rights Management dla platform urządzeń przenośnych](https://technet.microsoft.com/dn451248)

Pobierz przeglądarkę dla komputerów Mac i Windows Phone, korzystając z linków na [strony programu Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970).


### <a name="more-information-about-other-applications-that-support-azure-information-protection"></a>Więcej informacji o innych aplikacjach, które obsługują usługę Azure Information Protection

Poza aplikacjami z tabeli z usługą Azure Information Protection może zostać zintegrowana także każda aplikacja, która obsługuje interfejsy API dla usługi Azure Rights Management, w tym:

- Aplikacje biznesowe tworzone w firmach za pomocą zestawów RMS SDK

- Aplikacje od dostawców oprogramowania napisane przy użyciu zestawów RMS SDK.

Aby uzyskać więcej informacji, zobacz [przewodnik dewelopera usługi Azure Information Protection](./develop/developers-guide.md).

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Aplikacje, które nie są obsługiwane przez usługi Azure RMS

Następujące aplikacje nie są obecnie obsługiwane przez usługę Azure RMS:

-   Microsoft OneDrive dla firm dla programu SharePoint Server 2013

-   Przeglądarka plików XPS

Ponadto aplikacji RMS sharing i klienta usługi Azure Information Protection dotyczą następujące ograniczenia:

-   Komputery Windows: Wymaga minimalnej wersji systemu Windows 7 z dodatkiem Service Pack 1

## <a name="rms-enlightened-solutions"></a>Rozwiązania z obsługą usług RMS

Poniższa tabela zawiera informacje na temat dostarczanych przez dostawców oprogramowania rozwiązań z obsługą usług RMS.

Jeśli jesteś dostawcą oprogramowania i dysponujesz rozwiązaniem, które nie zostało wymienione w tej tabeli, zarejestruj swoją aplikację w usłudze Azure AD. Aby uzyskać więcej informacji, zobacz artykuł [Jak zarejestrować aplikację w usłudze Azure AD i włączyć dla niej obsługę usługi RMS](./develop/authentication-integration.md).


|Produkt|Dostawca|Opis|
|-------------------------------|---------------------------|-----------------|
|Bezwzględne|Bezwzględne|Ochrona przed utratą danych (DLP) zapewniająca ochronę zawartości.|
|Content Locker|VMware|Zapisywanie, używanie i tworzenie chronionej zawartości.|
|Controle|TakeControle|Zbieranie elektronicznych materiałów dowodowych poprzez etykietowanie i ochronę.|
|Forcepoint|Forcepoint DLP|Punkt końcowy danych utraty prevention (DLP) rozwiązanie do wymuszania zasad zabezpieczeń danych organizacji.|
|Halocore|Secude|Ochrona plików wyeksportowanych ze środowisk SAP.|
|MaaS 360|IBM|Integracja w celu umożliwienia użycia i ochrony dokumentów.|
|Mobiliya|Mobiliya|Zabezpiecza dokumenty z repozytoriów Documentum firmy EMC.
|Ramessys|Ramessys|Integracja pod kątem obsługi produktów Chemcart i Documentum.
|Sealpath|Sealpath Technologies|Integracja z narzędziami projektowymi CAD, takimi jak AutoCAD i Siemens Jt2GO.
|SecRMM|Sqaudra Technologies |Ochrona dokumentów z nośników wymiennych.
|Security Sheriff|CryptZone |Zarządzanie dostępem w usłudze SharePoint i ochrona dokumentów w oparciu o ich klasyfikację i uprawnienia dostępu.
|Ochrona przed utratą danych firmy Symantec|Symantec |Wykrywanie i monitorowanie plików chronionych.

## <a name="next-steps"></a>Następne kroki
Aby sprawdzić pozostałe wymagania, zobacz [Requirements for Azure Information Protection](requirements.md) (Wymagania dotyczące usługi Azure Information Protection).

Aby uzyskać informacje o obsłudze usługi Azure RMS przez najczęściej używane aplikacje, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](./applications-support.md).

Informacje o sposobach konfigurowania najczęściej używanych aplikacji dla usługi Azure RMS opisano w temacie [Konfigurowanie aplikacji dla usługi Azure Rights Management](configure-applications.md).

