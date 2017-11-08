---
title: "Wdrażanie usługi Azure Information Protection skanera"
description: "Instrukcje dotyczące instalowania, konfigurowania i uruchamiania skanera usługi Azure Information Protection, aby dowiedzieć się, klasyfikować i chronić pliki na następującą liczbę magazynów danych."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 20d29079-2fc2-4376-b5dc-380597f65e8a
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 22e7ba9589e75013862f008f76fcc4082a847262
ms.sourcegitcommit: f8efd2e462ad44b77205abd6249696c681790937
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
# <a name="deploying-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>Wdrażanie usługi Azure Information Protection skanera można automatycznie klasyfikować i chronić pliki

>*Dotyczy: Azure Information Protection, Windows Server 2016, Windows Server 2012 R2*

> [!NOTE]
> Ta funkcja jest obecnie w wersji zapoznawczej i mogą ulec zmianie.

Dzięki tym informacjom można dowiedzieć się o skanera usługi Azure Information Protection i jak pomyślnie zainstalować, skonfigurować i uruchomić go. 

Ten skaner działa jako usługa systemu Windows Server i umożliwia odnajdywania, klasyfikowania i chronić pliki na następujące magazynów danych:

- Foldery lokalne na komputer z systemem Windows Server z uruchomioną skanera.

- Ścieżki UNC udziały sieciowe, które używają protokołu pliku System CIFS (Common Internet).

- Lokacje i bibliotek programu SharePoint Server 2016 i SharePoint Server 2013.

## <a name="overview-of-the-azure-information-protection-scanner"></a>Omówienie usługi Azure Information Protection skanera

Po skonfigurowaniu sieci [zasad usługi Azure Information Protection](configure-policy.md) dla etykiet, które mają zastosowanie automatycznej klasyfikacji, następnie może być oznaczony jako pliki, które umożliwia odnalezienie tego skanera. Etykiety klasyfikować i opcjonalnie stosowanie ochrony lub usuń ochronę:

![Omówienie usługi Azure Information Protection skanera](../media/infoprotect-scanner.png)

Automatyczna klasyfikacja korzysta z usługi Office 365 wbudowane utraty zapobiegania (DLP) czułości informacji typy danych i wykrywania wzorzec lub wzorce regex usługi Office 365. Ponieważ skaner używa klienta usługi Azure Information Protection, można klasyfikować i chronić je [typów plików](../rms-client/client-admin-guide-file-types.md).

Można uruchomić skanera odnajdywania tylko w trybie, w którym korzystać z raportów do sprawdzenia, co się stanie, jeśli pliki zostały oznaczone jako. Alternatywnie można uruchomić skanera, aby automatycznie zastosować etykiety.

Należy pamiętać, że skaner nie odnajdzie i etykiety w czasie rzeczywistym. Systematycznie przeszukiwania za pomocą plików na magazyny danych, które określisz i można skonfigurować tego cyklu do uruchamiania raz lub wielokrotnie.

## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Wymagania wstępne dotyczące usługi Azure Information Protection skanera
Przed zainstalowaniem skanera usługi Azure Information Protection, upewnij się, że zostały spełnione następujące wymagania.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Komputer serwera systemu Windows do uruchamiania usługi skanera:<br /><br />-4 procesów<br /><br />-4 GB pamięci RAM|Windows Server 2016 lub Windows Server 2012 R2.<br /><br />Ten serwer może być komputer fizyczny lub wirtualny, która ma szybkie i niezawodne połączenie sieciowe do magazynów danych do przeskanowania. <br /><br />Upewnij się, że ten serwer ma [łączności z Internetem](../get-started/requirements.md#firewalls-and-network-infrastructure) wymaganych dla usługi Azure Information Protection. Lub, musisz skonfigurować go jako [odłączonymi komputerami](../rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers).|
|Program SQL Server do przechowywania konfiguracji skanera:<br /><br />-Lokalnego lub zdalnego wystąpienia|SQL Server 2012 R2 jest minimalną wersję dla następujących wersji:<br /><br />-SQL Server Enterprise<br /><br />-SQL Server Standard<br /><br />— Program SQL Server Express|
|Konto usługi, aby uruchomić usługę skanera|To konto musi być konta usługi Active Directory, który jest synchronizowany z usługą Azure AD, z następujących wymagań dodatkowych:<br /><br />- **Logowanie lokalne** prawo. To prawo jest wymagane do instalacji i konfiguracji skanera, ale nie dla operacji. To prawo, do konta usługi, należy przypisać, ale można usunąć tego prawa, po potwierdzeniu, że skaner można odnajdywania, klasyfikowania i ochrony plików.<br /><br />- **Zaloguj się jako usługa** prawo. To prawo jest automatycznie przyznawane kontu usługi podczas instalacji skanera i tego uprawnienia jest wymagany do instalacji, konfiguracji i operacji skanera. <br /><br />-Uprawnienia do przechowywania danych: należy przyznać **odczytu** i **zapisu** uprawnienia skanowanie plików, a następnie zastosowanie i ochronę plików, które spełniają warunki określone w Zasady usługi Azure Information Protection. Aby uruchomić skanera odnajdywania tylko w trybie, **odczytu** jest wystarczające uprawnienia.<br /><br />— Dla etykiet, które Włącz ponownie ochronę lub usuń ochronę: Aby zapewnić, że skaner zawsze ma dostęp do chronionych plików, należy to konto [superużytkowników](configure-super-users.md) usługi Azure Rights Management usługi i upewnij się, że funkcja superużytkowników jest włączona . Aby uzyskać więcej informacji o wymaganiach dotyczących konta stosowania ochrony, zobacz [przygotowywanie użytkowników i grup usługi Azure Information Protection](../plan-design/prepare.md).|
|Klient usługi Azure Information Protection jest zainstalowany na komputerze serwera systemu Windows|Skaner usługi Azure Information Protection wymaga obecnie wersja klienta usługi Azure Information Protection.<br /><br />Jeśli preferowane, można zainstalować klienta z właśnie modułu programu PowerShell (AzureInformationProtection) służący do instalowania i konfigurowania skanera.<br /><br />Aby uzyskać instrukcje dotyczące instalacji klienta, zobacz [Przewodnik administratora](../rms-client/client-admin-guide.md).|
|Skonfigurowany etykiet, które stosowane automatycznej klasyfikacji oraz opcjonalnie ochrony|Aby uzyskać więcej informacji o sposobie konfigurowania warunki, zobacz [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection](/deploy-use/configure-policy-classification.md).<br /><br />Aby uzyskać więcej informacji na temat konfigurowania etykiety w celu zastosowania ochrony plików, zobacz [jak konfigurowanie etykiety pod kątem ochrony usługi Rights Management](../deploy-use/configure-policy-protection.md). |


## <a name="install-the-azure-information-protection-scanner"></a>Zainstaluj skaner usługi Azure Information Protection

1. Za pomocą konta usługi, który został utworzony do uruchomić skanera, zaloguj się do komputera systemu Windows Server, które zostanie uruchomione skanera.

2. Otwórz sesję środowiska Windows PowerShell z **Uruchom jako administrator** opcji.

3. Uruchom [AIPScanner instalacji](/powershell/module/azureinformationprotection/Install-AIPScanner) polecenia cmdlet, określając wystąpienia programu SQL Server, na którym chcesz utworzyć bazę danych dla usługi Azure Information Protection skanera. Po wyświetleniu monitu podaj poświadczenia dla konta usługi skanera (\<azwa_użytkownika >) i hasło: 
    
    ```
    Install-AIPScanner -SqlServerInstance <database name>
    ```
    
    Przykłady:
        
    - Aby użyć domyślnego wystąpienia:`Install-AIPScanner -SqlServerInstance SQLSERVER1`
    
    - Dla wystąpienia nazwanego:`Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER`
    
    - Dla programu SQL Server Express:`Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS`

4. Sprawdź, czy usługa jest teraz zainstalowany za pomocą **narzędzia administracyjne** > **usług**. 
    
    Nosi nazwę zainstalowanej usługi **skanera ochrony informacji Azure** i jest skonfigurowana do uruchamiania za pomocą utworzonego konta usługi skanera.

Teraz, gdy zainstalowano skanera, należy uzyskać token dla konta usługi skanera do uwierzytelniania, co umożliwia uruchamianie nienadzorowanej usługi Azure AD. 

## <a name="get-an-azure-ad-token-for-the-scanner-service-account-to-authenticate-to-the-azure-information-protection-service"></a>Pobierz token dla konta usługi skanera do uwierzytelniania w usłudze Azure Information Protection do usługi Azure AD

1. Z tym samym komputerze z systemem Windows Server lub pulpit Zaloguj się do portalu Azure do utworzenia dwóch aplikacji usługi Azure AD, które są wymagane do określenia tokenu dostępu do uwierzytelniania. Po początkowej interakcyjnego logowania token ten umożliwia skanera nieinteraktywnie Uruchom.
    
    Aby utworzyć te aplikacje, postępuj zgodnie z instrukcjami [jak pliki etykiet nieinteraktywnie dla usługi Azure Information Protection](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) z podręcznika administratora.

2. Z komputera z systemem Windows Server, nadal zalogowany za pomocą konta usługi skanera, uruchom [AIPAuthentication zestaw](/powershell/module/azureinformationprotection/set-aipauthentication), określając wartości, które zostały skopiowane z poprzedniego kroku:
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application>  -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application >
    ```

3. Po wyświetleniu monitu podaj hasło dla poświadczeń konta usługi dla usługi Azure AD, a następnie kliknij przycisk **Akceptuj**.

Skaner ma teraz token do uwierzytelniania usługi Azure AD, które jest ważny przez jeden rok, dwa lata, lub nigdy nie wygasa, zgodnie z konfiguracją programu **sieci Web aplikacji /API** w usłudze Azure AD. Jeśli token jest ważny, należy powtórzyć kroki od 1 do 3.

Teraz możesz określić magazyny danych do skanowania. 

## <a name="specify-data-stores-for-the-azure-information-protection-scanner"></a>Określ następującą liczbę magazynów danych skanera usługi Azure Information Protection

Użyj [AIPScannerRepository Dodaj](/powershell/module/azureinformationprotection/Add-AIPScannerRepository) polecenia cmdlet, aby określić dane są przechowywane do skanowania przez skaner usługi Azure Information Protection. Można określić ścieżki UNC, adresy URL programu SharePoint i foldery lokalne witryny programu SharePoint i bibliotek. 

Obsługiwane wersje programu SharePoint: SharePoint Server 2016 i SharePoint Server 2013.

1. Z tego samego komputera systemu Windows Server w sesji programu PowerShell Dodaj pierwsze dane sklepu, uruchamiając następujące polecenie:
    
        Add-AIPScannerRepository -Path <path>
    
    Na przykład: `Add-AIPScannerRepository -Path \\NAS\Documents`
    
    Inne przykłady można znaleźć [pomocy online](/powershell/module/azureinformationprotection/Add-AIPScannerRepository#examples) tego polecenia cmdlet.

2. Powtórz to polecenie dla wszystkich przechowuje dane chcesz skanować. Jeśli musisz usunąć magazyn danych, który został dodany, użyj [AIPScannerRepository Usuń](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository) polecenia cmdlet.

3. Upewnij się, że został określony w magazynie danych poprawnie, uruchamiając [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository) polecenia cmdlet:
    
        Get-AIPScannerRepository

Z konfiguracji domyślnej skanera możesz teraz gotowy do uruchomienia skanowania pierwszy w trybie odnajdowania.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-azure-information-protection-scanner"></a>Uruchomić cykl odnajdowania i wyświetlania raportów usługi Azure Information Protection skanera

1. Przy użyciu **narzędzia administracyjne** > **usług**, uruchom **skanera ochrony informacji Azure** usługi.

2. Poczekaj, aż skanera ukończyć jego cyklu. Podczas za pomocą wszystkich plików w magazynie danych, które określiłeś ma skanera zatrzymuje usługę. Można użyć lokalnego Windows **aplikacji i usług** dziennika zdarzeń **usługi Azure Information Protection**, aby upewnić się, gdy usługa jest zatrzymana. Należy wyszukać identyfikator zdarzenia informacyjną **911**.

3. Przejrzyj raporty, które są przechowywane w lokalizacji %*localappdata*%\Microsoft\MSIP\Scanner\Reports i które mają format pliku CSV. Z konfiguracji domyślnej skanera tylko te pliki, które spełniają warunki automatycznej klasyfikacji znajdują się w tych raportach.
    
    Wyniki są niezgodne z oczekiwaniami, może być konieczne dostosowania warunków określonych w zasadach usługi Azure Information Protection. Jeśli tak jest, powtórz kroki od 1 do 3, aż wszystko będzie gotowe zmienić konfigurację, aby zastosować klasyfikacji i opcjonalnie ochrony. Zawsze, powtórz te kroki, uruchom następujące polecenie programu PowerShell na komputerze systemu Windows Server:
    
        Set-AIPScannerConfiguration -Schedule OneTime

Gdy wszystko jest gotowe automatycznie etykietę pliki, które umożliwia odnalezienie skanera, przejdź do następnej procedury. 

## <a name="configure-the-azure-information-protection-scanner-to-apply-classification-and-protection-to-discovered-files"></a>Skonfiguruj skanera usługi Azure Information Protection do zastosowania i ochronę plików odnalezionych

W jego domyślne ustawienie skanera ma jeden czasu i w trybie tylko do raportowania. Aby zmienić te ustawienia, należy uruchomić [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) polecenia cmdlet.

1. Na komputerze z systemem Windows Server w sesji programu PowerShell, uruchom następujące polecenie:
    
        Set-AIPScannerConfiguration -ScanMode Enforce -Schedule Continuous
    
    Brak innych ustawień konfiguracyjnych, które można zmienić. Na przykład czy atrybuty plików zostały zmienione, a co jest rejestrowane w raportach. Ponadto jeśli zasady usługi Azure Information Protection zawiera ustawienia, które wymaga wiadomość uzasadnienie, aby obniżyć poziom klasyfikacji lub usuń ochronę, należy określić wiadomości za pomocą tego polecenia cmdlet. Użyj [pomocy online](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration#parameters) Aby uzyskać więcej informacji o każdym ustawieniu konfiguracji. 

2. Przy użyciu **narzędzia administracyjne** > **usług**, uruchom ponownie **skanera ochrony informacji Azure** usługi.

3. Jak wcześniej monitorowanie dziennika zdarzeń i raporty, aby wyświetlić pliki, które zostały oznaczone, jakie klasyfikacji została zastosowana i czy została zastosowana ochrona.

Ponieważ został skonfigurowany harmonogram wykonywania, gdy skaner działał jego sposób za pomocą wszystkich plików, uruchomi nowy cykl tak, aby nowe i zmienione pliki są wykrywane.

## <a name="list-of-cmdlets-for-the-azure-information-protection-scanner"></a>Listę poleceń cmdlet dla usługi Azure Information Protection skanera 

Inne polecenia cmdlet skanera pozwalają zmienić konta usługi i bazy danych dla skanera, Pobierz bieżące ustawienia skanera i odinstaluj usługę skanera. Skaner używa następujących poleceń cmdlet:

- [Dodaj AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository)

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository)

- [AIPScanner instalacji](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Usuń AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository)

- [Zestaw AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Zestaw AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Odinstaluj AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)


## <a name="event-log-ids-and-descriptions"></a>Identyfikatory i opisy dziennika zdarzeń

Skorzystaj z następujących sekcji do identyfikowania możliwych identyfikatorów zdarzeń i opisy skanera. Te zdarzenia są rejestrowane na serwerze z uruchomioną usługę skaner, w oknach **aplikacji i usług** dziennika zdarzeń **usługi Azure Information Protection**.

-----

Informacje o **910**

**Uruchomić skanera cyklu.**

To zdarzenie jest rejestrowane, gdy usługa skanera została uruchomiona i rozpocznie skanowanie w poszukiwaniu plików w repozytoria danych, które można określić.

----

Informacje o **911**

**Zakończono skanera cyklu.**

To zdarzenie jest rejestrowane po zakończeniu jego jednorazowe skanowanie skanera, od czasu uruchomienia serwera lub skaner zakończył cykl ciągłego harmonogramu.

----

Informacje o **913**

**Skaner jest zatrzymana, ponieważ skaner ustawiono wartość Never.**

To zdarzenie jest rejestrowane, gdy skaner jest skonfigurowany do uruchamiania jednego czasu zamiast stale, i usługę Azure Information Protection skanera ręcznego ponownego uruchomienia od czasu uruchomienia komputera.  

Skanowanie plików ponownie, musisz ustawić harmonogram **OneTime** lub **ciągłe**, a następnie ręcznie ponownie uruchom usługę. Aby zmienić harmonogram, użyj [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) polecenia cmdlet i **harmonogram** parametru.

----

Błąd **912**

**Wystąpił nieznany błąd.**

Więcej informacji jest zalogowany szczegółowego raportu, który jest przechowywany w % localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_YYYY_MM_DD_HH_MM.csv.

Skontaktuj się z [Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support) Jeśli to zdarzenie będzie nadal występować, mają być rejestrowane. 

----

Błąd **914**

**Usługa automatycznie została zatrzymana z powodu nieprawidłowych konfiguracji: plik zasad lub jest uszkodzony.**

To zdarzenie jest rejestrowane, gdy klient usługi Azure Information Protection nie ma pliku zasad skanera do uruchomienia.

Zasady usługi Azure Information Protection jest przechowywany w %localappdata%\Microsoft\MSIP i musi być skonfigurowany z etykietami, których warunki do zastosowania automatycznej klasyfikacji. Lub zasady muszą być skonfigurowane dla etykiety domyślnej.

Upewnij się, że zapory nie blokują wymaga połączenia z Internetem. Aby uzyskać więcej informacji, zobacz [zapory i infrastruktury sieci](../get-started/requirements.md#firewalls-and-network-infrastructure) wymagania dotyczące usługi Azure Information Protection. Jeśli połączenie z Internetem nie jest możliwe, wykonaj instrukcje dotyczące obsługi [odłączone komputery](../rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers).


## <a name="next-steps"></a>Następne kroki

Za pomocą programu PowerShell można także interaktywnie klasyfikować i chronić pliki z komputera stacjonarnego. Aby uzyskać więcej informacji dotyczących tego i innych scenariuszy korzystających z programu PowerShell, zobacz [przy użyciu programu PowerShell przy użyciu klienta usługi Azure Information Protection](../rms-client/client-admin-guide-powershell.md).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]