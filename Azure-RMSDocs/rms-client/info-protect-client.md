---
title: "Instalowanie klienta usługi Azure Information Protection | Azure Information Protection"
description: "Instrukcje dotyczące instalowania klienta, który dodaje pasek usługi Information Protection do aplikacji pakietu Office, dzięki czemu można wybrać etykiety klasyfikacji dla dokumentów i wiadomości e-mail."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: 23c437479c756f2a9335606e686f117d514a38f6
ms.openlocfilehash: 71972b0a057b1958dfa5e5b4af41b65d5080a086


---

# <a name="installing-the-azure-information-protection-client"></a>Instalowanie klienta usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Aby klasyfikować dokumenty i wiadomości e-mail przy użyciu usługi Azure Information Protection, musisz najpierw zainstalować klienta usługi Azure Information Protection. Ta instalacja dodaje pasek usługi Information Protection do aplikacji pakietu Office (Word, Excel, PowerPoint, Outlook), który wyświetla etykiety klasyfikacji dla Twojej organizacji, a także nową grupę **Ochrona** na karcie **Narzędzia główne** (Word, Excel, PowerPoint), która zawiera przycisk o nazwie **Chroń**:

Na poniższej ilustracji przedstawiono ten pasek usługi Information Protection oraz etykiety z [zasad domyślnych](../deploy-use/configure-policy-default.md):

![Pasek usługi Azure Information Protection z zasadami domyślnymi](../media/info-protect-bar-default.png)

Pobierz klienta usługi Azure Information Protection z [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Obecnie można zainstalować ogólnie dostępną wersję usługi oraz jej wersję zapoznawczą. Wersja zapoznawcza zawiera nowe funkcje, które użytkownik może wypróbować, i może ulec zmianie. Aby uzyskać więcej informacji, zobacz następujące powiadomienie we wpisie w blogu: [Azure Information Protection December preview now available](https://blogs.technet.microsoft.com/enterprisemobility/2016/12/07/azure-information-protection-december-preview-now-available/) (Dostępna jest grudniowa wersja zapoznawcza usługi Azure Information Protection)

Przed zainstalowaniem klienta sprawdź, czy masz wymagane wersje systemu operacyjnego i aplikacji dla klienta usługi Azure Information Protection: [Wymagania dla usługi Azure Information Protection](../get-started/requirements-azure-rms.md). Ponadto w przypadku klienta w wersji zapoznawczej na komputerach z systemem Windows 7 z dodatkiem SP1 wymagana jest aktualizacja [KB 2533623](https://support.microsoft.com/en-us/kb/2533623), którą można zainstalować po zainstalowaniu klienta. Jeśli wymagana aktualizacja nie została wcześniej zainstalowana, zostanie wyświetlony monit o jej zainstalowanie.

## <a name="to-install-the-azure-information-protection-client-manually"></a>Aby zainstalować klienta usługi Azure Information Protection ręcznie

1. Po [pobraniu klienta](https://www.microsoft.com/en-us/download/details.aspx?id=53018) uruchom plik wykonywalny, taki jak **AzInfoProtection.exe**, i postępuj zgodnie z monitami, aby zainstalować klienta. Ta instalacja wymaga lokalnych uprawnień administracyjnych.

    Wybierz opcję zainstalowania zasad demonstracyjnych, jeśli nie możesz nawiązać połączenia z usługą Office 365 lub Azure Active Directory, ale chcesz zobaczyć i wypróbować klienta usługi Azure Information Protection przy użyciu zasad lokalnych w celach demonstracyjnych. Gdy klient nawiąże połączenie z usługą Azure Information Protection, te zasady demonstracyjne zostaną zastąpione zasadami usługi Azure Information Protection obowiązującymi w organizacji. 

2. Aby rozpocząć użytkowanie klienta usługi Azure Information Protection: jeśli Twój komputer ma uruchomiony pakiet Office 2010, uruchom ponownie komputer. W przypadku innych wersji pakietu Office uruchom ponownie wszystkie aplikacje pakietu Office.

## <a name="to-install-the-azure-information-protection-client-for-users"></a>Aby zainstalować klienta usługi Azure Information Protection dla użytkowników

Możesz użyć skryptu i zautomatyzować instalację klienta Azure Information Protection, korzystając z opcji wiersza polecenia. Aby wyświetlić opcje instalacji, uruchom plik wykonywalny z opcją **/help**. Na przykład: `AzInfoProtection.exe /help`.

Przykład instalacji klienta w trybie dyskretnym: `AzInfoProtection.exe /passive | quiet`

Klient usługi Azure Information Protection w wersji ogólnodostępnej znajduje się również w wykazie usługi Microsoft Update, dzięki czemu można zainstalować i zaktualizować klienta przy użyciu dowolnej usługi aktualizacji oprogramowania korzystającej z wykazu. Wersje zapoznawcze klienta nie znajdują się w wykazie usługi Microsoft Update.

## <a name="to-uninstall-the-azure-information-protection-client"></a>Aby odinstalować klienta usługi Azure Information Protection

Można użyć dowolnej z tych opcji:

- Odinstaluj program za pomocą Panelu sterowania: kliknij kolejno pozycje **Microsoft Azure Information Protection** > **Odinstaluj**

- Uruchom ponownie plik wykonywalny (np. **AzInfoProtection.exe**) i na stronie **Modyfikowanie ustawień** kliknij pozycję **Odinstaluj**. 

- Uruchom plik wykonywalny z opcją **/uninstall**. Na przykład: `AzInfoProtection.exe /uninstall`


## <a name="to-verify-installation-connection-status-or-report-a-problem"></a>Aby zweryfikować instalację lub stan połączenia albo zgłosić problem

1. Otwórz aplikację pakietu Office i na karcie **Narzędzia główne** w grupie **Ochrona** kliknij kolejno przyciski **Chroń** oraz **Pomoc i opinie**.

2. W oknie dialogowym **Microsoft Azure Information Protection** zwróć uwagę na następujące elementy:

    - W sekcji **stanu klienta**: użyj wartości **Wersja**, aby sprawdzić, czy instalacja zakończyła się pomyślnie. Ponadto możesz zobaczyć, kiedy klient został ostatnio połączony z usługą Azure Protection Information w Twojej organizacji i kiedy ostatnio zainstalowano lub zaktualizowano zasady usługi Azure Information Protection. Gdy klient łączy się z usługą, automatycznie pobiera najnowsze zasady, jeśli wykryje zmiany w porównaniu z obecnymi zasadami. Jeśli wprowadzono zmiany zasad po wyświetlonym czasie, zamknij i ponownie otwórz aplikację pakietu Office.
    
        Zobaczysz również wyświetloną nazwę użytkownika, która identyfikuje konto używane do uwierzytelniania w usłudze Azure Information Protection. Ta nazwa użytkownika musi pasować do konta używanego w usłudze Office 365 lub Azure Active Directory, które należy do dzierżawy skonfigurowanej dla usługi Azure Information Protection.

    - W sekcji **Pomoc i opinie**: **link Powiedz mi więcej** domyślnie prowadzi do witryny sieci Web usługi [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection), ale można go skonfigurować dla niestandardowego adresu URL jako jedno z [ustawień zasad](../deploy-use/configure-policy-settings.md) w zasadach usługi Azure Information Protection.
        
        Użyj linku **Wyślij opinię**, aby automatycznie dołączyć dzienniki klienta do wiadomości e-mail, którą można wysłać do zespołu usługi Information Protection w celu zbadania problemu. 
    
        Aby uzyskać informacje diagnostyczne i dowiedzieć się, jak zresetować klienta, kliknij pozycję **Uruchom diagnostykę**. Po zakończeniu testów diagnostycznych kliknij pozycję **Kopiuj wyniki**, aby wkleić informacje w wiadomości e-mail, którą można wysłać do działu pomocy technicznej firmy Microsoft. Po zakończeniu testów możesz także zresetować klienta.
        
        Więcej informacji na temat opcji **Resetuj**:
        
        - Nie trzeba być administratorem lokalnym, aby używać tej opcji, a ta akcja nie jest rejestrowana w Podglądzie zdarzeń. 
        
        - Jeśli pliki są zablokowane, ta akcja powoduje usunięcie wszystkich plików z lokalizacji **%localappdata%\Microsoft\MSIPC**, w której przechowywane są certyfikaty klienta i szablony zarządzania prawami. Nie powoduje ona usunięcia zasad usługi Azure Information Protection, plików dzienników klienta ani wylogowania użytkownika.
        
        - Następuje usunięcie klucza rejestru i ustawień: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. Jeśli konfigurujesz ustawienia tego klucza rejestru (np. ustawienia przekierowywania do dzierżawy usługi Azure Information Protection, ponieważ migrujesz z usług AD RMS i nadal masz w sieci punkt połączenia usługi), musisz ponownie skonfigurować ustawienia rejestru po zresetowaniu klienta.
        
        - Po zresetowaniu klienta musisz ponownie zainicjować środowisko użytkownika (ta czynność jest również znana jako „uruchamianie”), w którym będą pobierane certyfikaty klienta i najnowsze szablony. W tym celu zamknij wszystkie wystąpienia pakietu Office i uruchom ponownie aplikację pakietu Office. Ta akcja spowoduje również sprawdzenie, czy zostały pobrane najnowsze zasady usługi Azure Information Protection. Wykonaj tę czynność przed ponownym uruchomieniem testów diagnostycznych.


## <a name="usage-logging"></a>Rejestrowanie użycia

**[Ta funkcja wymaga wersji zapoznawczej klienta i może ulec zmianie.]**

W przypadku klienta usługi Azure Information Protection w wersji zapoznawczej klient rejestruje aktywność użytkownika w lokalnym dzienniku zdarzeń **aplikacji i usług** systemu Windows, **Azure Information Protection**. Zdarzenia obejmują następujące informacje:

- Data, wersja klienta, identyfikator zasad

- Nazwa zalogowanego użytkownika, nazwa komputera

- Nazwa i lokalizacja pliku

- Działanie:

    - Ustawienie etykiety: identyfikator informacji 101
    
    - Ustawienie etykiety (niższej): identyfikator informacji 102
    
    - Ustawienie etykiety (wyższej): identyfikator informacji 103
    
    - Usunięcie etykiety: identyfikator informacji 104
   
    - Zalecane: identyfikator informacji 105
    
    - Zastosowanie niestandardowej ochrony: identyfikator informacji 201
    
    - Zastosowanie niestandardowej ochrony: identyfikator informacji 202
    
    - Logowanie (operacyjne): identyfikator informacji 902
    
    - Zasady pobierania (operacyjne): identyfikator informacji 901
    
- Źródło akcji:
    
    - Ręczny 
    
    - Zalecane
    
    - Automatyczny  
    
    - System (dla zasad logowania i pobierania)
    
- Etykieta przed akcją i po niej 
    
- Ochrona przed akcją i po niej
    
- Uzasadnienie użytkownika (jeśli ma zastosowanie)
    

## <a name="keyboard-shortcuts-for-the-azure-information-protection-bar"></a>Skróty klawiaturowe dla paska usługi Azure Information Protection

Aby uzyskać dostęp do paska usługi Azure Information Protection za pomocą skrótów klawiaturowych, użyj następujących kombinacji klawiszy:

- Naciśnij klawisze **Ctrl** + **Shift** + **~** 

Następnie użyj klawisza Tab, aby wybrać etykiety i inne kontrolki na pasku (ikona **Ukryj etykiety** i ikona **Usuń etykiety**), a następnie naciśnij klawisz Enter, aby je wybrać.


## <a name="file-locations"></a>Lokalizacje plików

Pliki klienta:   

- Dla 64-bitowych systemów operacyjnych: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Dla 32-bitowych systemów operacyjnych: **\Program Files\Microsoft Azure Information Protection**

Pliki dziennika klienta i plik obecnie zainstalowanych zasad:

- Dla 64- i 32-bitowych systemów operacyjnych: **%localappdata%\Microsoft\MSIP**


## <a name="next-steps"></a>Następne kroki

Aby zmienić etykiety na pasku usługi Information Protection, musisz skonfigurować zasady usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad usługi Azure Information Protection](../deploy-use/configure-policy.md).

Aby uzyskać przykład konfigurowania zasad domyślnych i zobaczyć efekty w aplikacji pakietu Office, wypróbuj [Samouczek Szybki start dla usługi Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

Aby sprawdzić informacje o wersji klienta, zobacz [Historia wersji](client-version-release-history.md).



<!--HONumber=Dec16_HO1-->


