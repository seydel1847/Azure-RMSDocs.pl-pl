---
title: "Podręcznik administratora klienta usługi Azure Information Protection | Azure Information Protection"
description: "Instrukcje i informacje dla administratorów sieci przedsiębiorstwa odpowiedzialnych za wdrażanie klienta usługi Azure Information Protection dla systemu Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f82c7964b16ad984ad920059e2f61f19ad0f471a
ms.openlocfilehash: dff30520c149c29663c340b70a12c427b31659b9


---


# <a name="azure-information-protection-client-administrator-guide"></a>Podręcznik administratora klienta usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*


Poniższe informacje przydadzą się osobom odpowiedzialnym za klienta usługi Azure Information Protection w sieci przedsiębiorstwa lub chcącym uzyskać więcej informacji technicznych, niż jest dostępnych w [podręczniku użytkownika klienta usługi Azure Information Protection](client-user-guide.md).

Klient usługi Azure Information Protection zawiera następujące elementy:

- Dodatek do pakietu Office instalujący pasek usługi Azure Information Protection, który umożliwia użytkownikom wybieranie etykiet klasyfikacji, oraz przycisk **Chroń** na Wstążce udostępniający dodatkowe opcje.

- Opcje dostępne po kliknięciu prawym przyciskiem myszy w oknie Eksploratora plików Windows, które pozwalają użytkownikom stosować etykiety klasyfikacji i ochronę plików.

- Przeglądarka do wyświetlania chronionych plików, gdy natywna aplikacja nie może ich otworzyć.

- Moduł środowiska PowerShell pozwalający dodawać i usuwać etykiety klasyfikacji oraz włączać i wyłączać ochronę plików.

- Klient usługi Rights Management komunikujący się z usługą Azure Rights Management (Azure RMS) lub usługami Active Directory Rights Management (AD RMS).

Klient usługi Azure Information Protection najlepiej nadaje się do pracy z usługami Azure — usługą Azure Information Protection i jej usługami ochrony danych, Azure Rights Management. Jednak z pewnymi ograniczeniami klient usługi Azure Information Protection działa też z lokalną wersją usług Rights Management — AD RMS. Obszerne porównanie funkcji obsługiwanych przez usługi Azure Information Protection i AD RMS można znaleźć w artykule [Porównanie usług Azure Information Protection i AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). Jeśli korzystasz z usług AD RMS i chcesz przeprowadzić migrację do usługi Azure Information Protection, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

**Czy masz pytanie, na które nie ma odpowiedzi w tej dokumentacji?** Odwiedź [witrynę Yammer usługi Azure Information Protection](https://www.yammer.com/AskIPTeam). 


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Czy należy wdrożyć klienta usługi Azure Information Protection?

Dokonaj wdrożenia klienta usługi Azure Information Protection w następujących przypadkach:

- Chcesz klasyfikować (i ewentualnie chronić) dokumenty i wiadomości e-mail, wybierając etykiety w aplikacjach pakietu Office (Word, Excel, PowerPoint, Outlook).

- Chcesz klasyfikować (i ewentualnie chronić) dokumenty i wiadomości e-mail za pomocą Eksploratora plików, który obsługuje dodatkowe typy plików, wybór wielokrotny i foldery.

- Chcesz uruchamiać skrypty, które klasyfikują (i ewentualnie chronią) dokumenty za pomocą poleceń środowiska PowerShell.

- Chcesz wyświetlać chronione dokumenty, gdy natywna aplikacja wyświetlająca je nie jest zainstalowana lub nie może otworzyć tych dokumentów.

- Chcesz po prostu chronić pliki za pomocą Eksploratora plików lub poleceń środowiska Powershell.

- Chcesz umożliwić użytkownikom i administratorom śledzenie i odwoływanie chronionych dokumentów.

- Chcesz usuwać szyfrowanie z plików i kontenerów (wyłączać ochronę) w trybie zbiorczym na potrzeby odzyskiwania danych.

- Korzystasz z pakietu Office 2010 i chcesz chronić dokumenty i wiadomości e-mail za pomocą usługi Azure Rights Management.

Przykład ukazujący dodatek klienta usługi Azure Information Protection w aplikacjach pakietu Office, który wyświetla etykiety klasyfikacji dla danej organizacji i nowy przycisk **Chroń** na Wstążce:

![Pasek usługi Azure Information Protection z zasadami domyślnymi](../media/info-protect-bar-default.png)

## <a name="how-to-install-the-azure-information-protection-client-for-users"></a>Jak zainstalować klienta usługi Azure Information Protection dla użytkowników

Przed zainstalowaniem klienta sprawdź, czy masz wymagane wersje systemu operacyjnego i aplikacji dla klienta usługi Azure Information Protection: [Wymagania dla usługi Azure Information Protection](../get-started/requirements-azure-rms.md). 

Ponadto:

- Do zainstalowania pełnej wersji klienta usługi Azure Information Protection wymagany jest program Microsoft .NET Framework w wersji 4.6.2 lub wyższej. W przypadku jego braku Instalator spróbuje pobrać i zainstalować ten wymagany program. Jeśli ten wymagany program jest instalowany w ramach instalacji klienta, należy uruchomić ponownie komputer.

- Jeśli przeglądarka usługi Azure Information Protection jest instalowana oddzielnie, wymagany jest program Microsoft .NET Framework w wersji 4.5.2 lub wyższej. W przypadku jego braku Instalator nie pobierze i nie zainstaluje tego programu.

- Komputery z systemem Windows 7 z dodatkiem Service Pack1 wymagają aktualizacji [KB 2533623](https://support.microsoft.com/en-us/kb/2533623), którą można zainstalować po zainstalowaniu klienta. Jeśli ta aktualizacja jest wymagana i nie została wcześniej zainstalowana, zostanie wyświetlony monit o jej zainstalowanie.

> [!NOTE]
> Instalacja wymaga lokalnych uprawnień administracyjnych.

Klienta usługi Azure Information Protection można zainstalować nie tylko w sposób opisany w poniższych instrukcjach. Znajduje się on również w wykazie usługi Microsoft Update, dzięki czemu można zainstalować i zaktualizować klienta przy użyciu dowolnej usługi aktualizacji oprogramowania korzystającej z wykazu. 

1. Pobierz klienta usługi Azure Information Protection z [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 

2. W przypadku instalacji domyślnej wystarczy uruchomić plik wykonywalny **AzInfoProtection.exe**. Jednak aby wyświetlić opcje instalacji, należy najpierw uruchomić plik wykonywalny z parametrem **/help**: `AzInfoProtection.exe /help`

   Przykład instalacji klienta w trybie dyskretnym: `AzInfoProtection.exe /quiet`
   
   Przykład instalacji jedynie poleceń cmdlets środowiska PowerShell w trybie dyskretnym: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
   
   Jeśli instalujesz klienta na komputerach z pakietem Office 2010, a użytkownicy nie są administratorami lokalnymi na swoich komputerach, należy dodatkowo określić parametr **ServiceLocation** (niewidoczny w oknie pomocy). Aby uzyskać więcej informacji, zobacz następną sekcję.

3. W przypadku instalacji interaktywnej wybierz opcję zainstalowania **zasad demonstracyjnych**, jeśli nie możesz nawiązać połączenia z usługą Office 365 lub Azure Active Directory, ale chcesz zobaczyć i wypróbować klienta usługi Azure Information Protection przy użyciu zasad lokalnych w celach demonstracyjnych. Gdy klient nawiąże połączenie z usługą Azure Information Protection, te zasady demonstracyjne zostaną zastąpione zasadami usługi Azure Information Protection obowiązującymi w organizacji.
    
4. Aby ukończyć instalację: 

    - Ponownie uruchom komputer, jeśli jest na nim zainstalowany pakiet Office 2010. 
        
        Jeśli klienta zainstalowano bez parametru ServiceLocation, przy pierwszym uruchomieniu dowolnej aplikacji pakietu Office korzystającej z paska usługi Azure Information Protection (na przykład Word) należy potwierdzić wszystkie monity o zaktualizowanie rejestru w związku z pierwszym uruchomieniem. Klucze rejestru są wypełniane przy użyciu [odnajdywania usług](../rms-client/client-deployment-notes.md#rms-service-discovery). 
    
    - W przypadku innych wersji pakietu Office należy uruchomić ponownie wszystkie aplikacje pakietu Office i wszystkie wystąpienia Eksploratora plików. 
        


### <a name="additional-instructions-for-office-2010-only"></a>Dodatkowe instrukcje dotyczące tylko pakietu Office 2010

W przypadku instalowania klienta dla użytkowników pakietu Office 2010 nieposiadających lokalnych uprawnień administracyjnych należy określić parametr ServiceLocation i adres URL usługi Azure Rights Management. Te parametr i wartość tworzą oraz ustawiają następujące klucze rejestru:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

Zidentyfikuj wartość do określenia dla parametru ServiceLocation, wykonując następującą procedurę. 

#### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>Aby zidentyfikować wartość do określenia dla parametru ServiceLocation

1. Z poziomu sesji programu PowerShell najpierw uruchom polecenie [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice) i określ poświadczenia administratora, aby nawiązać połączenie z usługą Azure Rights Management. Następnie uruchom polecenie [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration). 
 
    Jeśli jeszcze nie zainstalowano modułu programu PowerShell dla usługi Azure Rights Management, zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

2. Opierając się na danych wyjściowych, zidentyfikuj wartość **LicensingIntranetDistributionPointUrl**.

    Na przykład: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. Usuń element **/_wmcs/licensing** z tego ciągu. Na przykład: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    Wynikowy ciąg jest wartością do określenia dla parametru ServiceLocation.

Przykład instalacji klienta w trybie dyskretnym dla pakietu Office 2010 i usługi Azure RMS: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


## <a name="to-uninstall-the-azure-information-protection-client"></a>Aby odinstalować klienta usługi Azure Information Protection

Można użyć dowolnej z tych opcji:

- Odinstaluj program za pomocą Panelu sterowania: kliknij kolejno pozycje **Microsoft Azure Information Protection** > **Odinstaluj**

- Uruchom ponownie plik wykonywalny (np. **AzInfoProtection.exe**) i na stronie **Modyfikowanie ustawień** kliknij pozycję **Odinstaluj**. 

- Uruchom plik wykonywalny z opcją **/uninstall**. Na przykład: `AzInfoProtection.exe /uninstall`


## <a name="to-verify-installation-connection-status-or-send-feedback"></a>Aby zweryfikować instalację, stan połączenia albo zgłosić problem

1. Otwórz aplikację pakietu Office i na karcie **Narzędzia główne** w grupie **Ochrona** kliknij kolejno przyciski **Chroń** oraz **Pomoc i opinie**.

2. W oknie dialogowym **Microsoft Azure Information Protection** zwróć uwagę na następujące elementy:

    - W sekcji **stanu klienta**: użyj wartości **Wersja**, aby sprawdzić, czy instalacja zakończyła się pomyślnie. Ponadto możesz zobaczyć, kiedy klient został ostatnio połączony z usługą Azure Protection Information w Twojej organizacji i kiedy ostatnio zainstalowano lub zaktualizowano zasady usługi Azure Information Protection. Gdy klient łączy się z usługą, automatycznie pobiera najnowsze zasady, jeśli wykryje zmiany w porównaniu z obecnymi zasadami. Jeśli wprowadzono zmiany zasad po wyświetlonym czasie, zamknij i ponownie otwórz aplikację pakietu Office.
    
        Zobaczysz również wyświetloną nazwę użytkownika, która identyfikuje konto używane do uwierzytelniania w usłudze Azure Information Protection. Ta nazwa użytkownika musi pasować do konta używanego w usłudze Office 365 lub Azure Active Directory, które należy do dzierżawy skonfigurowanej dla usługi Azure Information Protection.

    - W sekcji **Pomoc i opinie**: **link Powiedz mi więcej** domyślnie prowadzi do witryny sieci Web usługi [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection), ale można go skonfigurować dla niestandardowego adresu URL jako jedno z [ustawień zasad](../deploy-use/configure-policy-settings.md) w zasadach usługi Azure Information Protection.
        
        Użyj linku **Wyślij opinię**, aby wysłać propozycje lub prośby do zespołu usługi Information Protection. Nie należy używać tej opcji w celu uzyskania pomocy technicznej. W takim przypadku należy zapoznać się z artykułem [Opcje pomocy technicznej i zasoby społecznościowe](../get-started/information-support.md#support-options-and-community-resources). 
    
        Aby uzyskać informacje diagnostyczne i dowiedzieć się, jak zresetować klienta, kliknij pozycję **Uruchom diagnostykę**. Po zakończeniu testów diagnostycznych kliknij pozycję **Kopiuj wyniki**, aby wkleić informacje w wiadomości e-mail, którą można wysłać do działu pomocy technicznej firmy Microsoft. Po zakończeniu testów możesz także zresetować klienta.
        
        Więcej informacji na temat opcji **Resetuj**:
        
        - Nie trzeba być administratorem lokalnym, aby używać tej opcji, a ta akcja nie jest rejestrowana w Podglądzie zdarzeń. 
        
        - Jeśli pliki są zablokowane, ta akcja powoduje usunięcie wszystkich plików z lokalizacji **%localappdata%\Microsoft\MSIPC**, w której przechowywane są certyfikaty klienta i szablony zarządzania prawami. Nie powoduje ona usunięcia zasad usługi Azure Information Protection, plików dzienników klienta ani wylogowania użytkownika.
        
        - Następuje usunięcie klucza rejestru i ustawień: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. Jeśli konfigurujesz ustawienia tego klucza rejestru (np. ustawienia przekierowywania do dzierżawy usługi Azure Information Protection, ponieważ migrujesz z usług AD RMS i nadal masz w sieci punkt połączenia usługi), musisz ponownie skonfigurować ustawienia rejestru po zresetowaniu klienta.
        
        - Po zresetowaniu klienta musisz ponownie zainicjować środowisko użytkownika (ta czynność jest również znana jako „uruchamianie”), w którym będą pobierane certyfikaty klienta i najnowsze szablony. W tym celu zamknij wszystkie wystąpienia pakietu Office i uruchom ponownie aplikację pakietu Office. Ta akcja spowoduje również sprawdzenie, czy zostały pobrane najnowsze zasady usługi Azure Information Protection. Wykonaj tę czynność przed ponownym uruchomieniem testów diagnostycznych.


## <a name="next-steps"></a>Następne kroki
Po zainstalowaniu klienta usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Feb17_HO2-->


