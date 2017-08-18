---
title: "Wymagania dotyczące usługi Azure Information Protection — pełny artykuł"
description: "Określanie wymagań wstępnych dotyczących wdrażania usługi Azure Information Protection w organizacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 10cf9371-a61b-495f-9d42-898448806994
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 2a5791dfd571091e8c9e510447b0a5b36818a8df
ms.sourcegitcommit: 17f593b099dddcbb1cf0422353d594ab964b2736
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/11/2017
---
# <a name="requirements-for-azure-information-protection"></a>Wymagania dotyczące usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*


Przed wdrożeniem usługi Azure Information Protection w organizacji upewnij się, że następujące wymagania wstępne zostały spełnione. 

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Subskrypcja usługi Azure Information Protection|Przejrzyj [informacje o subskrypcji](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) oraz [listę funkcji](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection, aby upewnić się, że subskrypcja organizacji obejmuje funkcje usługi Azure Information Protection, których chcesz użyć.|
|Azure Active Directory|Aby obsługiwać uwierzytelnianie użytkowników na potrzeby usługi Azure Information Protection, organizacja musi mieć katalog usługi Azure Active Directory (Azure AD). Ponadto jeśli chcesz użyć kont użytkowników z katalogu lokalnego (AD DS), musisz również skonfigurować integrację katalogów.<br /><br />Jeśli Twoje konta są federacyjne (na przykład używane są usługi AD FS), muszą korzystać z uwierzytelniania zintegrowanego systemu Windows. Uwierzytelnianie oparte na formularzach nie jest obsługiwane w przypadku usługi Azure Information Protection.<br /><br />Uwierzytelnianie wieloskładnikowe jest obsługiwane przez usługę Azure Information Protection, jeśli masz wymagane oprogramowanie klienckie i prawidłowo skonfigurowaną infrastrukturę obsługującą to uwierzytelnianie.<br /><br />Aby uzyskać więcej informacji, zobacz [Azure Active Directory requirements for Azure Information Protection](requirements-azure-ad.md) (Wymagania usługi Azure Active Directory dotyczące usługi Azure Information Protection).|
|Urządzenia klienckie|Użytkownicy muszą mieć urządzenia klienckie (komputer lub urządzenie przenośne) z systemem operacyjnym, który obsługuje usługę Azure Information Protection.<br /><br />Następujące urządzenia obsługują klienta usługi Azure Information Protection, co pozwala użytkownikom klasyfikować i oznaczać ich wiadomości e-mail i dokumenty pakietu Office:<br /><br />— Windows 10 (x86, x64)<br /><br />— Windows 8.1 (x86, x64)<br /><br />— Windows 8 (x86, x64)<br /><br />— Windows 7 z dodatkiem Service Pack 1 (x86, x64)<br /><br />Gdy klient chroni dane za pomocą usługi Azure Rights Management, mogą być one używane przez te same urządzenia (z systemem Windows, Mac, iOS lub Android), które obsługują usługę Azure Rights Management. <br /><br />Aby uzyskać szczegółowe informacje na temat urządzeń obsługujących usługę Azure Rights Management, zobacz [Client devices that support Azure Rights Management data protection](../get-started/requirements-client-devices.md) (Urządzenia klienckie obsługujące ochronę danych usługi Azure Rights Management).|
|Aplikacje|Klient usługi Azure Information Protection obsługuje etykietowanie i ochronę plików oraz wiadomości e-mail, które zostały utworzone przez aplikacje **Word**, **Excel**, **PowerPoint** i **Outlook** pochodzące z następujących pakietów Office:<br /><br />— Office Professional Plus 2016<br /><br />— Office Professional Plus 2013 z dodatkiem Service Pack 1<br /><br />— Office Professional Plus 2010<br /><br />Aby uzyskać więcej informacji na temat aplikacji obsługujących usługę Azure Rights Management, zobacz [Applications that support Azure Rights Management data protection](requirements-applications.md) (Aplikacje obsługujące ochronę danych usługi Azure Rights Management).|
|Infrastruktura obsługująca łączność z Internetem i zależnymi usługami w chmurze|Jeśli jest używana zapora lub podobne aktywne urządzenie sieciowe wymagające skonfigurowania określonych połączeń sieciowych, zapoznaj się z informacjami o usłudze **Azure Rights Management (RMS)** w sekcji [Portal usługi Office 365 i udostępnianie](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) w następującym artykule o pakiecie Office: [Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Aby zawsze mieć dostęp do aktualnych wersji tych informacji, subskrybuj źródło danych RSS, postępując zgodnie z instrukcjami podanymi w tym artykule pakietu Office.<br /><br />Oprócz informacji zawartych w artykule dotyczącym pakietu Office skorzystaj z poniższych uwag dotyczących usługi Azure Information Protection:<br /><br />— Zezwalaj na ruch HTTPS na porcie TCP 443 do witryny **api.informationprotection.azure.com**.<br /><br />— Nie kończ połączenia TLS między klientem i usługą (np. w celu przeprowadzenia inspekcji na poziomie pakietu). Spowoduje to przerwanie przypinania certyfikatu, którego klienci usługi RMS używają razem z urzędami certyfikacji zarządzanymi przez firmę Microsoft do zabezpieczania komunikacji z usługą Azure RMS.<br /><br />— Jeśli używasz serwera proxy sieci Web, który wymaga uwierzytelniania, musisz skonfigurować go do korzystania ze zintegrowanego uwierzytelniania systemu Windows przy użyciu poświadczeń logowania usługi Active Directory użytkownika.|

Następujące produkty serwera lokalnego są obsługiwane przez usługę Azure Rights Management działającą w ramach usługi Azure Information Protection:

-   Exchange Server

-   SharePoint Server

-   Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików

Aby uzyskać informacje o dodatkowych wymaganiach dla tego scenariusza, zobacz [On-premises servers that support Azure Rights Management data protection](requirements-servers.md) (Serwery lokalne obsługujące ochronę danych usługi Azure Rights Management).

> [!IMPORTANT]
> Poniższy scenariusz wdrożenia nie jest obsługiwany, chyba że jest używana ochrona usług AD RMS w ramach usługi Azure Information Protection — konfiguracja HYOK („Hold Your Own Key”):
> 
> -   Uruchamianie usług AD RMS i Azure RMS równocześnie w tej samej organizacji, z wyjątkiem procesu migracji, zgodnie z opisem zawartym w temacie [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).
> 
> Istnieje obsługiwana ścieżka migracji [z usług AD RMS do usługi Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) i z [usługi Azure Information Protection do usług AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Jeśli po wdrożeniu usługi Azure Information Protection zdecydujesz, że nie chcesz już używać tej usługi w chmurze, zobacz [Decommissioning and deactivating Azure Information Protection](../deploy-use/decommission-deactivate.md) (Likwidowanie i dezaktywowanie usługi Azure Information Protection).

## <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Wymagania usługi Azure Active Directory dotyczące usługi Azure Information Protection

Aby korzystać z usługi Azure Information Protection, musisz mieć katalog usługi Azure AD. Możesz użyć konta organizacji w tym katalogu do logowania się do klasycznego portalu Azure, w którym można na przykład konfigurować szablony usługi Rights Management i zarządzać nimi.

Jeśli organizacja nie ma jeszcze subskrypcji platformy Azure, możesz ją uzyskać, tworząc konto do użycia na potrzeby bezpłatnej wersji próbnej: przejdź na stronę [wprowadzenia do platformy Azure](https://account.windowsazure.com/organization) i postępuj zgodnie z instrukcjami.

Więcej informacji można znaleźć w następujących zasobach dokumentacji usługi Azure Active Directory:

-   [Co to jest katalog usługi Azure AD Directory?](/active-directory/active-directory-whatis)

-   [Jak subskrypcje platformy Azure są kojarzone z usługą Azure Active Directory?](/active-directory/active-directory-how-subscriptions-associated-directory)

Jeśli chcesz zintegrować katalog usługi Azure AD z lokalnymi lasami usługi AD, zobacz artykuł [Integrowanie tożsamości użytkownika lokalnego z usługą Azure Active Directory](/active-directory/active-directory-aadconnect).

> [!NOTE]
> Jeśli masz urządzenia przenośne lub komputery Mac, które przeprowadzają uwierzytelnianie lokalne za pomocą usług AD FS lub odpowiednika dostawcy uwierzytelniania:
> 
> -   Musisz używać usług AD FS na serwerze z minimalną wersją **Windows Server 2012 R2** lub alternatywnego dostawcy uwierzytelniania, który obsługuje protokół OAuth 2.0.

### <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>Uwierzytelnianie wieloskładnikowe i usługa Azure Information Protection
Aby używać uwierzytelniania wieloskładnikowego z usługą Azure Information Protection, należy spełnić co najmniej jedno z następujących wymagań:

-   Office 2013 (minimalna wersja):

    -   Jeśli masz pakiet Office 2013, musisz również zainstalować [aktualizację pakietu Office 2013 (KB3054853) z 9 czerwca 2015](https://support.microsoft.com/kb/3054853). Aby uzyskać więcej informacji na temat tej aktualizacji i sposobu wdrażania logowania opartego na bibliotece ADAL (Active Directory Authentication Library) w pakiecie Office 2013 w ramach nowoczesnego uwierzytelniania, zobacz wpis dotyczący [anonsowania publicznej wersji nowoczesnego uwierzytelniania w pakiecie Office 2013](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) na blogu pakietu Office.

-   Aplikacja do udostępniania usługi Rights Management dla systemu Windows:

    -   Musisz zainstalować minimalną wersję 1.0.1908.0 (numer wersji można sprawdzić w Panelu sterowania, przechodząc do opcji Programy i funkcje). Aby uzyskać więcej informacji o aplikacji do udostępniania, zobacz artykuł [Aplikacja do udostępniania usługi Rights Management dla systemu Windows](../rms-client/sharing-app-windows.md).

-   Aplikacja do udostępniania usługi Rights Management dla urządzeń przenośnych i komputerów Mac:

    -   Upewnij się, że zainstalowano najnowszą wersję. Obsługa usługi MFA została dodana w wydaniu aplikacji RMS sharing z września 2015 r.

Następnie skonfiguruj rozwiązanie MFA:

-   W przypadku dzierżaw zarządzanych przez firmę Microsoft (masz usługę Azure Active Directory lub Office 365):

    -   Skonfiguruj usługę Azure MFA, aby wymusić jej użycie przez użytkowników. Aby uzyskać instrukcje, zobacz artykuł [Wprowadzenie do korzystania z usługi Azure Multi-Factor Authentication w chmurze](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) w dokumentacji usługi Multi-Factor Authentication.

        Aby uzyskać więcej informacji na temat usługi Azure MFA, zobacz artykuł [Co to jest usługa Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication)

-   W przypadku dzierżaw federacyjnych (serwery federacyjne działają lokalnie):

    -   Skonfiguruj serwery federacyjne dla usługi Azure Active Directory lub Office 365. Jeśli na przykład używasz usług AD FS, zobacz artykuł [Konfigurowanie dodatkowych metod uwierzytelniania dla usług AD FS](https://technet.microsoft.com/library/dn758113.aspx) w witrynie TechNet.

        Aby uzyskać więcej informacji na temat tego scenariusza, zobacz wpis [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) (Praca z usługą Office 365 — usprawniony program tożsamości) na blogu pakietu Office.

## <a name="client-devices-that-support-azure-rights-management-data-protection"></a>Urządzenia klienckie obsługujące ochronę danych usługi Azure Rights Management

Poniższe sekcje służą do identyfikowania urządzeń, które obsługują usługę Azure Rights Management zapewniającą ochronę danych w ramach usługi Azure Information Protection.

### <a name="computers"></a>Komputery
Następujące komputerowe systemy operacyjne obsługują usługę Azure Rights Management:

-   **Windows 7** (x86, x64)

-   **Windows 8** (x86, x64)

-   **Windows 8.1** (x86, x64)

-   **Windows 10** (x86, x64)

-   **Mac OS X**: minimalna wersja Mac OS X 10.8 (Mountain Lion)

### <a name="mobile-devices"></a>Urządzenia przenośne
Następujące systemy operacyjne urządzeń przenośnych obsługują usługę Azure Rights Management:

-   **Windows Phone**: Windows Phone 8.1

-   **Telefony i tablety z systemem Android**: minimalna wersja systemu Android — 4.0.3

-   **Urządzenia iPhone i iPad**: minimalna wersja systemu iOS — 7.0

-   **Tablety z systemem Windows**: Windows 10 Mobile i Windows 8.1 RT

## <a name="applications-that-support-azure-rights-management-data-protection"></a>Aplikacje obsługujące ochronę danych usługi Azure Rights Management

Poniższa tabela służy do identyfikowania aplikacji, które natywnie obsługują usługę Azure Rights Management (Azure RMS) zapewniającą ochronę danych w ramach usługi Azure Information Protection. 

Dla tych aplikacji obsługa usługi Rights Management jest ściśle zintegrowana za pomocą interfejsów API usługi Rights Management w celu obsługi ograniczeń użycia. Te aplikacje są również znane jako aplikacje obsługujące usługę RMS.

O ile nie wskazano inaczej, obsługiwane możliwości dotyczą zarówno usługi Azure RMS, jak i AD RMS. Ponadto obsługa usług AD RMS w systemach iOS, Android, OS X i Windows Phone 8.1 wymaga [rozszerzenia usług Active Directory Rights Management Services dla urządzeń przenośnych](https://technet.microsoft.com/library/dn673574.aspx).

Informacje dotyczące kolumn tabeli:

-   **Chroniony plik PDF:** pliki, które mają rozszerzenie nazwy PPDF i są tworzone automatycznie podczas używania aplikacji RMS sharing do udostępniania plików pakietu Office i plików PDF pocztą e-mail. Aplikacja RMS sharing oraz aplikacja Azure Information Protection dla systemów iOS i Android zawierają czytnik dla chronionych plików PDF. Jeśli wcześniej utworzono pliki PDF chronione za pomocą usługi Azure RMS lub AD RMS, można nadal odczytywać je na urządzeniach z systemem Windows, iOS lub Android przy użyciu programów Foxit Reader i Nitro Pro.

-   **Poczta e-mail:** klienci poczty e-mail z listy mogą chronić wiadomości e-mail, które będą automatycznie chronić wszystkie dołączone pliki. W tym scenariuszu funkcja podglądu klienta umożliwia wyświetlanie chronionej zawartości (wiadomości i załączników) autoryzowanym odbiorcom. Jednak jeśli sama wiadomość e-mail nie jest chroniona, ale załącznik jest chroniony, funkcja podglądu klienta nie może wyświetlić chronionego załącznika autoryzowanym odbiorcom.

-   **Inne typy plików:** pliki tekstowe i pliki obrazów mają następujące rozszerzenia nazw: TXT, XML, JPG i JPEG. Rozszerzenia nazw tych plików zmieniają się po objęciu plików natywną ochroną zapewnianą przez usługę Rights Management, a pliki stają się plikami tylko do odczytu. Pliki, które nie mogą być chronione w sposób natywny, mają rozszerzenie nazwy pliku pfile, co oznacza, że zostały objęte ogólną ochroną przez usługę Rights Management. Aby uzyskać więcej informacji, zobacz [Przewodnik administratora aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-admin-guide.md).


|**System operacyjny urządzenia**|Word, Excel, PowerPoint|Chroniony plik PDF|Poczta e-mail|Inne typy plików|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Pakiet Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Aplikacje mobilne pakietu Office (tylko usługa Azure RMS) [[1]](#footnote-1)<br /><br />Office Online [[2]](#footnote-2)|Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />Aplikacja do udostępniania usługi RMS|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Outlook Web App (OWA) [[3]](#footnote-3)<br /><br />Poczta systemu Windows [[4]](#footnote-4)|Aplikacja RMS sharing dla systemu Windows: tekst, obrazy, plik PFILE<br /><br />Siemens JT2Go: pliki JT (tylko Windows 10)|
|**iOS**|Pakiet Office dla urządzeń iPad i iPhone [[5]](#footnote-5)<br /><br />Office Online [[2]](#footnote-2)<br /><br />TITUS Docs|Aplikacja Azure Information Protection [[1]](#footnote-1)<br /><br /> Foxit Reader<br /><br />TITUS Docs|Aplikacja Azure Information Protection [[1]](#footnote-1)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Program Outlook dla urządzeń iPad i iPhone [[4]](#footnote-4)<br /><br />OWA dla systemu iOS [[3]](#footnote-3)<br /><br />TITUS Mail|Aplikacja Azure Information Protection [[1]](#footnote-1): tekst, obrazy<br /><br />TITUS Docs: plik PFILE|
|**Android**|Aplikacja GigaTrust dla systemu Android<br /><br />Office Online [[2]](#footnote-2)<br /><br />Office Mobile (tylko usługi Azure RMS) [[1]](#footnote-1)|Aplikacja Azure Information Protection [[1]](#footnote-1)<br /><br />Aplikacja GigaTrust dla systemu Android<br /><br />Foxit Reader<br /><br />Aplikacja RMS sharing [[1]](#footnote-1)|9Folders [[4]](#footnote-4)<br /><br />Aplikacja Azure Information Protection [[1]](#footnote-1)<br /><br />Aplikacja GigaTrust dla systemu Android [[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Aplikacja Outlook dla systemu Android [[4]](#footnote-4)<br /><br />OWA dla systemu Android [[3]](#footnote-3) i [[7]](#footnote-7)<br /><br />Poczta e-mail Samsung (urządzenia S3 i nowsze) [[7]](#footnote-7)<br /><br />TITUS Classification for Mobile|Aplikacja Azure Information Protection [[1]](#footnote-1): tekst, obrazy|
|**OS X**|Office 2011 (tylko usługi AD RMS)<br /><br />Office 2016 dla komputerów Mac<br /><br />Office Online [[2]](#footnote-2)|Foxit Reader<br /><br />Aplikacja RMS sharing [[1]](#footnote-1)|Outlook 2011 (tylko usługi AD RMS)<br /><br />Outlook 2016 dla komputerów Mac<br /><br />Outlook dla komputerów Mac|Aplikacja RMS sharing [[1]](#footnote-1): tekst, obrazy, plik PFILE|
|**Windows 10 Mobile**|Aplikacje mobilne pakietu Office (tylko usługa Azure RMS) [[1]](#footnote-1)|Nieobsługiwane|Citrix WorxMail [[6]](#footnote-6)<br /><br />Poczta programu Outlook|Nieobsługiwane|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[2]](#footnote-2)|Nieobsługiwane|Outlook 2013 RT<br /><br />Aplikacja poczty dla systemu Windows<br /><br />Poczta systemu Windows [[4]](#footnote-4)|Siemens JT2Go: pliki JT|
|**Windows Phone 8.1**|Office Mobile (tylko usługi AD RMS)|Aplikacja RMS sharing [[1]](#footnote-1)|Outlook Mobile [[4]](#footnote-4)|Aplikacja RMS sharing [[1]](#footnote-1): tekst, obrazy, plik PFILE|
|**Blackberry 10**|Nieobsługiwane|Nieobsługiwane|Poczta e-mail Blackberry [[4]](#footnote-4)|Nieobsługiwane|


##### <a name="footnote-1"></a>Przypis 1
Obsługuje wyświetlanie zawartości chronionej.

##### <a name="footnote-2"></a>Przypis 2 
Obsługuje wyświetlanie chronionych dokumentów po przekazaniu niechronionego dokumentu do chronionej biblioteki usług SharePoint Online i OneDrive dla Firm. 

##### <a name="footnote-3"></a>Przypis 3
Jeśli adresat chronionej wiadomości e-mail nie korzysta z serwera poczty Exchange lub jeśli nadawca należy do innej organizacji, tę zawartość można otworzyć wyłącznie przy użyciu wzbogaconego klienta poczty e-mail, na przykład programu Outlook. Nie będzie można użyć do tego programu Outlook Web Access.

##### <a name="footnote-4"></a>Przypis 4
Używa funkcji Exchange ActiveSync IRM, którą musi włączyć administrator programu Exchange. Użytkownicy mogą przeglądać chronione wiadomości e-mail, odpowiadać nadawcy i opowiadać wszystkim nadawcom, ale nie mogą chronić nowych wiadomości e-mail.

Jeśli adresat chronionej wiadomości e-mail nie korzysta z serwera poczty Exchange lub jeśli nadawca należy do innej organizacji, tę zawartość można otworzyć wyłącznie przy użyciu wzbogaconego klienta poczty e-mail, na przykład programu Outlook. Nie można otworzyć tej zawartości przy użyciu usługi Outlook Web Access ani mobilnych klientów poczty używających funkcji Exchange Active Sync IRM.

##### <a name="footnote-5"></a>Przypis 5
Obsługuje wyświetlanie i edytowanie chronionych dokumentów. Aby uzyskać więcej informacji, zobacz następujący wpis w blogu pakietu Office: [Azure Rights Management support comes to Office for iPad and iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) (Obsługa usługi Azure Rights Management dołączana do pakietu Office dla urządzeń iPad i iPhone).

##### <a name="footnote-6"></a>Przypis 6
Aby uzyskać więcej informacji, zobacz [dokumentację produktu WorxMail](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html) firmy Citrix.

##### <a name="footnote-7"></a>Przypis 7
Aby uzyskać więcej informacji, zobacz następujący wpis na blogu pakietu Office: [OWA for Android now available on select devices](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/) (Program OWA dla systemu Android teraz dostępny na wybranych urządzeniach).

## <a name="more-information-about-azure-rms-support-for-office"></a>Więcej informacji na temat obsługi usługi Azure RMS dla pakietu Office

Usługa Azure RMS jest ściśle zintegrowana z aplikacjami Word, Excel, PowerPoint i Outlook, w których ta funkcja jest często określana jako Zarządzanie prawami do informacji (IRM, Information Rights Management). Następujące wersje klienta pakietu Office obsługują ochronę plików i wiadomości e-mail przy użyciu usługi Azure RMS:

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010

Wszystkie wersje pakietu Office (z wyjątkiem pakietu Office 2007) obsługują chronioną zawartość.

Usługa Azure RMS z pakietem Office Professional Plus 2010 lub Office Professional 2010:

- Wymaga aplikacji do udostępniania usługi Rights Management dla systemu Windows

- Nieobsługiwana w systemie Windows 10

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>Więcej informacji na temat aplikacji Azure Information Protection dla systemów iOS i Android

Aplikacja RMS sharing dla systemu iOS i Android została zastąpiona przez aplikację Azure Information Protection. Zawiera ona te same funkcje i dodatkowo obsługuje chronione prawami wiadomości e-mail i pliki PDF w usłudze SharePoint Online.

Jeśli Twoje urządzenia z systemami iOS i Android są zarejestrowane w usłudze Microsoft Intune, możesz wdrożyć tę aplikację i zarządzać nią za pomocą aplikacji zarządzanej przez zasady. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i wdrażanie zasad zarządzania aplikacjami mobilnymi w konsoli usługi Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) w dokumentacji usługi Intune. W kroku 2 tej dokumentacji usługi Intune należy skorzystać z instrukcji dotyczących publikowania aplikacji zarządzanej przez zasady.

Aby uzyskać więcej informacji, zobacz [FAQ for Microsoft Azure Information Protection app for iOS and Android](../rms-client/mobile-app-faq.md) (Aplikacja Microsoft Azure Information Protection dla systemów iOS i Android — często zadawane pytania).


### <a name="more-information-about-the-rights-management-sharing-application"></a>Więcej informacji na temat aplikacji do udostępniania usługi Rights Management

Aby uzyskać więcej informacji o aplikacji do udostępniania usługi Rights Management, zobacz następujące zasoby:

-   [Przewodnik administratora aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-admin-guide.md)

-   [Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-user-guide.md)

Aby uzyskać więcej informacji o aplikacji do udostępniania usługi Rights Management dla platform urządzeń przenośnych, zobacz następujące zasoby:

-   Pobierz odpowiednią aplikację za pomocą linków na [stronie usługi Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)

-   [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Microsoft Rights Management dla platform urządzeń przenośnych](https://technet.microsoft.com/dn451248)

> [!NOTE]
> Aplikacja RMS sharing dla systemów iOS i Android została obecnie zastąpiona przez aplikację Azure Information Protection.

### <a name="more-information-about-other-applications-that-support-azure-rms"></a>Więcej informacji o innych aplikacjach, które obsługują usługę Azure RMS

Oprócz aplikacji wyszczególnionych w tabeli, z usługą Azure RMS można integrować każdą aplikację obsługującą interfejsy API usługi RMS, w tym:

- Aplikacje biznesowe, które są zapisywane we własnym zakresie za pomocą zestawu RMS SDK

- Aplikacje od dostawców oprogramowania, które zostały napisane przy użyciu zestawu RMS SDK

Aby uzyskać więcej informacji o zestawie SDK, zobacz artykuł [Zestaw Microsoft Rights Management SDK](../develop/developers-guide.md).

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Aplikacje, które nie są obsługiwane przez usługi Azure RMS

Następujące aplikacje nie są obecnie obsługiwane przez usługę Azure RMS:

-   Microsoft Office 2011 dla komputerów Mac

-   Microsoft OneDrive dla Firm dla programu SharePoint Server 2013

-   Przeglądarka plików XPS
 
Ponadto aplikacja RMS sharing ma następujące ograniczenia:

-   W przypadku komputerów z systemem Windows: wymaga co najmniej systemu Windows 7 z dodatkiem Service Pack 1

## <a name="on-premises-servers-that-support-azure-rights-management-data-protection"></a>Serwery lokalne obsługujące ochronę danych usługi Azure Rights Management

Następujące produkty serwera lokalnego są obsługiwane przez usługę Azure Information Protection podczas używania łącznika usługi Azure Rights Management. Ten łącznik działa jako interfejs komunikacji (przekaźnik) między serwerami lokalnymi i usługą Azure Rights Management, która służy usłudze Azure Information Protection do ochrony wiadomości e-mail i dokumentów pakietu Office. 

Aby użyć tego łącznika, należy skonfigurować synchronizację katalogów między lasami usługi Active Directory a usługą Azure Active Directory.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Ponieważ serwery plików z systemem Windows Server 2008 R2 nie mają wbudowanej akcji zadania zarządzania plikami, która pozwala na zastosowanie ochrony przy użyciu usługi Rights Management, w tym scenariuszu nie można używać łącznika usługi Rights Management. Można jednak użyć pliku klasyfikacji infrastruktury i usługi Azure RMS w tych systemach operacyjnych w przypadku konfigurowania niestandardowego zadania zarządzania plikami, aby uruchomić plik wykonywalny lub skrypt służący do ochrony plików przy użyciu usługi Azure RMS. Na przykład skrypt programu Windows PowerShell, który używa [poleceń cmdlet ochrony usługi RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).
    > 
    > Można również używać tych poleceń cmdlet na serwerach z nowszymi wersjami systemu Windows Server, ponieważ umożliwiają one ochronę wszystkich typów plików. Łącznik usługi RMS chroni tylko pliki pakietu Office. Dokładne instrukcje można znaleźć w temacie [Ochrona za pomocą usługi RMS z użyciem infrastruktury klasyfikacji plików (FCI)](../rms-client/configure-fci.md).

Łącznik usługi Rights Management jest obsługiwany w systemach Windows Server 2012 R2, Windows Server 2012 i Windows Server 2008 R2.

Aby uzyskać więcej informacji o sposobie konfigurowania łącznika usługi Rights Management na wymienionych serwerach lokalnych, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
