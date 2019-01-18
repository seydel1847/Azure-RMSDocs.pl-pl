---
title: Wdrażanie skanera usługi Azure Information Protection (Zachowaj)
description: Instrukcje dotyczące instalowania, konfigurowania i uruchamiania bieżącą wersję zapoznawczą skanera usługi Azure Information Protection, aby dowiedzieć się, klasyfikowanie i ochrona plików w magazynach danych.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 09cd758d0e35cf3b23291e5995007c3f110480d2
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54394356"
---
# <a name="deploying-the-preview-version-of-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>Wdrażanie skanera usługi Azure Information Protection do automatycznego klasyfikowania i ochrony plików w wersji zapoznawczej

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), system Windows Server 2016, Windows Server 2012 R2*

> [!NOTE]
> Ten artykuł jest przeznaczony dla bieżącej wersji zapoznawczej skanera usługi Azure Information Protection. Wersje w wersji zapoznawczej mogą ulec zmianie.
> 
> Aby uzyskać instrukcje wdrażania ogólnie dostępnej wersji skanera, zobacz [wdrażanie skanera usługi Azure Information Protection do automatycznego klasyfikowania i ochrony plików](deploy-aip-scanner.md).
> 
> Jeśli uaktualniasz z ogólnie dostępnej wersji skanera do wersji zapoznawczej, zobacz [uaktualnianie skanera usługi Azure Information Protection](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).

Aby dowiedzieć się więcej na temat wersji zapoznawczych skanera usługi Azure Information Protection i jak pomyślnie zainstalować, skonfigurować i uruchomić go, należy użyć tych informacji. 

Ten skaner działa jako usługa w systemie Windows Server i umożliwia odnajdywanie, klasyfikowanie i ochrona plików w następujące magazyny danych:

- Foldery lokalne na komputerze systemu Windows Server, który działa skaner.

- Ścieżki UNC udziały sieciowe, które używają protokołu bloku komunikatów serwera (SMB).

- Witryny i biblioteki dla programu SharePoint Server 2016 i SharePoint Server 2013. SharePoint 2010, jest również obsługiwana dla klientów, którzy mają [rozszerzoną obsługę w tej wersji programu SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).

Aby skanować i oznaczyć pliki w chmurze repozytoriów, należy użyć [Cloud App Security](https://docs.microsoft.com/cloud-app-security/).

## <a name="overview-of-the-azure-information-protection-scanner"></a>Omówienie skanera usługi Azure Information Protection

Po skonfigurowaniu usługi [zasad usługi Azure Information Protection](configure-policy.md) dla etykiet, które są stosowane automatycznej klasyfikacji plików, które wykrywa ten skaner może następnie oznaczone etykietą. Etykiety klasyfikować i opcjonalnie stosować ochronę lub usunąć ochronę:

![Omówienie architektury skanera usługi Azure Information Protection](./media/infoprotect-scanner.png)

Skaner można sprawdzić wszystkie pliki, które umożliwia indeksowanie Windows, korzystając z interfejsu IFilters, które są zainstalowane na komputerze. Następnie aby określić, czy pliki muszą etykietowania, skaner używa usługi Office 365 wbudowane utraty prevention (DLP) poufności informacji typy danych i wykrywania wzorca lub wzorców wyrażeń regularnych usługi Office 365. Ponieważ skaner korzysta z klienta Azure Information Protection, można klasyfikować i ochrony tej samej [typy plików](./rms-client/client-admin-guide-file-types.md).

Można uruchomić skanera odnajdywania tylko w trybie, której użyć raportów, aby sprawdzić, co się stanie, jeśli pliki zostały oznaczone. Alternatywnie można uruchomić skanera, aby automatycznie zastosować etykiety. Można również uruchomić skanera, aby odnaleźć plików, które zawierają typy informacji poufnych, bez konieczności konfigurowania etykiety dla warunków automatycznej klasyfikacji.

Należy zauważyć, że skaner nie wykrywa i etykiety w czasie rzeczywistym. Systematyczne przeszukiwania za pomocą plików w magazynach danych, które określisz i można skonfigurować ten cykl, aby uruchomić jeden raz lub wielokrotnie.

Można określić typy plików ze skanowaniem lub Wyklucz ze skanowania, definiując listę typów plików w ramach konfiguracji skanera.


## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Wymagania wstępne dotyczące skanera usługi Azure Information Protection
Przed zainstalowaniem skanera usługi Azure Information Protection, upewnij się, że zostały spełnione następujące wymagania.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Komputera systemu Windows Server, aby uruchomić usługę skanera:<br /><br />-4 rdzenie procesora<br /><br />-8 GB pamięci RAM<br /><br />— 10 GB wolnego miejsca (średni) na pliki tymczasowe|Windows Server 2016 lub Windows Server 2012 R2. <br /><br />Uwaga: Do celów testowania lub ewaluacji w środowisku nieprodukcyjnym, można użyć w systemie operacyjnym klienta Windows, który jest [obsługiwane przez klienta usługi Azure Information Protection](requirements.md#client-devices).<br /><br />Ten komputer może być komputer fizyczny lub wirtualny, która ma szybkie i niezawodne połączenie sieciowe w magazynach danych, do przeskanowania.<br /><br /> Skaner wymaga wystarczająca ilość miejsca, aby utworzyć pliki tymczasowe dla każdego pliku, która skanuje, cztery pliki na każdy rdzeń. Zalecana ilość miejsca o rozmiarze 10 GB umożliwia 4 procesory skanowanie 16 plików, w których każdy może mieć rozmiar pliku 625 MB. <br /><br />Upewnij się, że ten komputer ma [łączności z Internetem](requirements.md#firewalls-and-network-infrastructure) wymaganych dla usługi Azure Information Protection. Jeśli połączenie z Internetem nie jest możliwe ze względu na zasady organizacji, zobacz [wdrażanie skanera za pomocą alternatywnej konfiguracji](#deploying-the-scanner-with-alternative-configurations) sekcji.|
|Program SQL Server do przechowywania konfiguracji skanera:<br /><br />— Lokalnego lub zdalnego wystąpienia<br /><br />— Rolę administratora systemu do zainstalowania skanera|SQL Server 2012 jest minimalna wersja w następujących wersjach:<br /><br />— Program SQL Server Enterprise<br /><br />— Program SQL Server Standard<br /><br />- SQL Server Express<br /><br />Skaner usługi Azure Information Protection obsługuje wielu baz danych konfiguracji na tego samego wystąpienia programu SQL server po określeniu nazwy profilu niestandardowego, skanera.<br /><br />Gdy zainstalujesz skanera, a Twoje konto ma rolę Sysadmin, proces instalacji automatycznie tworzy bazy danych konfiguracji skanera i przyznaje roli db_owner wymagane konto usługi, na którym uruchomiono skaner. Jeśli nie można udzielić roli Sysadmin lub zasady organizacji wymaga bazy danych można utworzyć i skonfigurować ręcznie, zobacz [wdrażanie skanera za pomocą alternatywnej konfiguracji](#deploying-the-scanner-with-alternative-configurations) sekcji.<br /><br />Rozmiar bazy danych konfiguracji różnią się w przypadku każdego wdrożenia, ale zalecamy przydzielić 500 MB, co 1 000 000 plików, które chcesz przeprowadzić skanowanie. |
|Konto usługi, aby uruchomić usługę skanera|Poza uruchamianiem usługi skanera, to konto jest uwierzytelniany w usłudze Azure AD i pobierze zasady usługi Azure Information Protection. To konto musi być kontem usługi Active Directory i synchronizowane z usługą Azure AD. Jeśli to konto nie może zsynchronizować ze względu na zasady organizacji, zobacz [wdrażanie skanera za pomocą alternatywnej konfiguracji](#deploying-the-scanner-with-alternative-configurations) sekcji.<br /><br />To konto usługi ma następujące wymagania:<br /><br />- **Zaloguj się na lokalnie** prawo. To uprawnienie jest wymagane do instalacji i konfiguracji skanera, ale nie dla operacji. Należy przyznać to uprawnienie, do konta usługi, ale możesz usunąć to uprawnienie, po potwierdzeniu, że skaner może odnajdywania, klasyfikowania i ochrony plików. Jeśli udzielenia tego prawa, nawet w przypadku krótkim czasie nie jest możliwe ze względu na zasady organizacji, zobacz [wdrażanie skanera za pomocą alternatywnej konfiguracji](#deploying-the-scanner-with-alternative-configurations) sekcji.<br /><br />- **Zaloguj się jako usługa** prawo. To prawo automatycznie przyznawane konto usługi podczas instalacji skanera i to uprawnienie jest wymagane do instalacji, konfiguracji i działania skanera. <br /><br />— Uprawnienia do repozytoriów danych: Należy przyznać **odczytu** i **zapisu** uprawnienia dla skanowania plików, a następnie zastosowanie funkcji klasyfikacji i ochrony plików, które spełniają warunki określone w zasadach usługi Azure Information Protection. Aby uruchomić skanera odnajdywania tylko w trybie, **odczytu** uprawnienie jest wystarczająca.<br /><br />— Dla etykiety, które ponownie włączyć ochronę lub usunięcie ochrony: Aby upewnić się, że skaner zawsze ma dostęp do chronionych plików, należy to konto [superużytkowników](configure-super-users.md) usługi Azure Rights Management service i upewnij się, że funkcja superużytkowników jest włączona. Aby uzyskać więcej informacji na temat wymagania dotyczące konta do stosowania ochrony zobacz [przygotowywanie użytkowników i grup usługi Azure Information Protection](prepare.md). Ponadto, jeśli udało Ci się wdrożyć [kontrolek dołączania](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) kontroli wdrażania etapowego, upewnij się, że to konto znajduje się w swojej kontrolki dołączania zostały skonfigurowane.|
|Wersja zapoznawcza klienta usługi Azure Information Protection jest zainstalowany na komputerze z systemem Windows Server|Należy zainstalować pełnego klienta do skanera. Nie należy instalować klienta przy użyciu tylko moduł programu PowerShell.<br /><br />Aby uzyskać instrukcje dotyczące instalacji klienta, zobacz [podręczniku administratora](./rms-client/client-admin-guide.md). Jeśli wcześniej zainstalowano skaner i teraz należy uaktualnić go do nowszej wersji, zobacz [uaktualnianie skanera usługi Azure Information Protection](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).|
|Etykiety skonfigurowane, korzystające z klasyfikacji automatycznej i, opcjonalnie, ochrona|Aby uzyskać więcej informacji o sposobach konfigurowania etykiety dla warunków i stosowanie ochrony:<br /> - [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej](configure-policy-classification.md)<br /> - [Konfigurowanie etykiety w celu ochrony usługi Rights Management](configure-policy-protection.md) <br /><br />Porada: Można użyć instrukcji od [samouczek](infoprotect-quick-start-tutorial.md) testowanie skanera etykietą, która wyszukuje numery kart kredytowych w dokumencie programu Word przygotowany. Jednak trzeba będzie zmienić konfigurację etykiet tak, aby opcja **wybierz sposób stosowania tej etykiety** jest ustawiona na **automatyczne**, zamiast **zalecane**. Następnie należy usunąć etykietę z dokumentu (jeśli ma zastosowanie) i skopiuj plik do repozytorium danych skanera. Szybkie testowanie, może to być folderem lokalnym na komputerze skanera.<br /><br /> Mimo że można uruchomić skanera, nawet jeśli nie skonfigurowano etykiet powodujących stosowanie automatycznej klasyfikacji, w tym scenariuszu nie jest objęty z tymi instrukcjami. [Więcej informacji](#using-the-scanner-with-alternative-configurations)|
|Dla dokumentów pakietu Office do skanowania:<br /><br />-97 – 2003, formaty plików i formaty Office Open XML dla programu Word, Excel i PowerPoint|Aby uzyskać więcej informacji na temat typów plików, które obsługuje skanera dla tych plików formatów, zobacz [typy plików obsługiwane przez klienta usługi Azure Information Protection](./rms-client/client-admin-guide-file-types.md)|
|W przypadku długich ścieżek:<br /><br />— Maksymalnie 260 znaków, chyba że skaner jest zainstalowany na Windows 2016 i komputer jest skonfigurowany do obsługi długich ścieżek|Windows 10 i Windows Server 2016 obsługuje ścieżkę długości większej niż 260 znaków, z następującymi [ustawienie zasad grupy](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/): **Lokalne zasady komputera** > **konfiguracji komputera** > **Szablony administracyjne** > **wszystkie ustawienia**  >  **NTFS** > **Win32 włączyć długie ścieżki**<br /><br /> Aby uzyskać więcej informacji na temat obsługi długie ścieżki plików, zobacz [maksymalnego ograniczenia długości ścieżki](https://docs.microsoft.com/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) sekcji dokumentacji dla deweloperów systemu Windows 10.

Jeśli nie spełnia wszystkie wymagania w tabeli, ponieważ są one zabronione przez zasady organizacji, zobacz następną sekcję wariantów.

Jeśli są spełnione wszystkie wymagania, przejść bezpośrednio do [Konfigurowanie sekcji skanera](#configure-the-scanner-in-the-azure-portal).

### <a name="deploying-the-scanner-with-alternative-configurations"></a>Wdrażanie skanera za pomocą alternatywnej konfiguracji

Wymagania wstępne wymienione w tabeli wymagań domyślne skanera zaleca się, ponieważ są to najprostsza konfiguracja wdrożenia skanera. Powinny one być odpowiednia dla początkowej fazie testowania, aby sprawdzić, możliwości skanera. Jednak w środowisku produkcyjnym, zasady organizacji może uniemożliwiać wymagania w zakresie domyślne ze względu na co najmniej jedną z następujących ograniczeń:

- Serwery nie są dozwolone łączności z Internetem

- Nie można udzielić Sysadmin lub baz danych muszą być tworzone i konfigurowane ręcznie

- Nie można udzielić kont usług **logować się lokalnie** prawo

- Konta usług, nie można zsynchronizować z usługą Azure Active Directory, ale serwery mają łączność z Internetem

Skaner może pomieścić te ograniczenia, ale mogą wymagać dodatkowej konfiguracji.


#### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>Ograniczenie: Skaner serwera nie może mieć połączenie z Internetem

Postępuj zgodnie z instrukcjami dotyczącymi [rozłączonym komputerze](./rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers). Następnie wykonaj następujące czynności:

1. Skonfiguruj skanera w witrynie Azure portal, tworząc profil skanera. Aby uzyskać pomoc dotyczącą tego kroku zobacz [skonfigurować skaner w witrynie Azure portal](#configure-the-scanner-in-the-azure-portal).

2. Eksportowanie profilu skanera z **usługi Azure Information Protection — profile (wersja zapoznawcza)** bloku przy użyciu **wyeksportować** opcji.

3. Na koniec w sesji programu PowerShell, uruchom [AIPScannerConfiguration importu](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration) i określ plik zawierający ustawienia wyeksportowane.

Należy pamiętać, że w tej konfiguracji skaner nie można zastosować ochronę (lub wyłączania ochrony) przy użyciu klucza oparta na chmurze w Twojej organizacji. Zamiast tego skaner jest ograniczona do przy użyciu etykiet, które są stosowane tylko klasyfikacja lub ochrony używające [HYOK](configure-adrms-restrictions.md). 

#### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>Ograniczenie: Nie można udzielić Sysadmin lub baz danych muszą być tworzone i konfigurowane ręcznie

Jeśli może otrzymać roli Sysadmin tymczasowo, aby zainstalować skaner, możesz usunąć tę rolę po zakończeniu instalacji skanera. Podczas używania tej konfiguracji bazy danych jest tworzone automatycznie, a konto usługi dla skaner automatycznie otrzymuje wymaganych uprawnień. Jednak konto użytkownika, który konfiguruje skaner wymaga roli db_owner dla bazy danych konfiguracji skanera i należy ręcznie przyznać tej roli w celu konta użytkownika.

Jeśli użytkownik nie może otrzymać roli Sysadmin nawet tymczasowo, należy ręcznie utworzyć bazę danych, przed zainstalowaniem skanera. Podczas używania tej konfiguracji należy przypisać następujące role:
    
|Konto|Rola na poziomie bazy danych|
|--------------------------------|---------------------|
|Konto usługi dla skanera|db_owner|
|Konto użytkownika dla instalacji|db_owner|
|Konto użytkownika dla konfiguracji skanera |db_owner|

Zazwyczaj użyje tego samego konta użytkownika do zainstalowania i skonfigurowania skanera. Jednak jeśli używasz różnych kont, oba wymagają roli db_owner dla bazy danych konfiguracji skanera:

- Jeśli nie określisz nazwę własnego profilu skaner, nazwie bazy danych konfiguracji **AIPScanner_\<nazwa_komputera >**. 

- Jeśli określisz nazwę profilu, ma nazwę bazy danych konfiguracji **AIPScanner_\<nazwa_profilu >**.

#### <a name="restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right"></a>Ograniczenie: Nie można udzielić kontu usługi skanera **logować się lokalnie** prawo

Jeśli zasady organizacji uniemożliwiają **logować się lokalnie** kliknij prawym przyciskiem myszy dla kont usług, ale możliwe **logowanie w trybie wsadowym** , postępuj zgodnie z instrukcjami dotyczącymi [określanie i użycia tokenu parametr dla polecenia Set-AIPAuthentication](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) w podręczniku administratora.

#### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>Ograniczenie: Konto usługi skanera, nie można zsynchronizować z usługą Azure Active Directory, ale serwer nie ma łączności z Internetem

Może mieć jedno konto, aby uruchomić usługę skanera i użyj innego konta do uwierzytelniania w usłudze Azure Active Directory:

- Skaner konta usługi można użyć lokalnego konta Windows lub konto usługi Active Directory.

- Dla konta usługi Azure Active Directory, postępuj zgodnie z instrukcjami dotyczącymi [określanie i użyj parametru tokenu dla polecenia Set-AIPAuthentication](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) w podręczniku administratora.


## <a name="configure-the-scanner-in-the-azure-portal"></a>Konfigurowanie skanera w witrynie Azure portal

Przed zainstalowaniem skaner, lub uaktualnienie wersji ogólnie dostępnej skanera, należy utworzyć profil skanera w witrynie Azure portal. Można skonfigurować profil dla ustawień skanera i repozytoria danych do skanowania.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.
    
2. Znajdź **skanera** opcje menu, a następnie wybierz **profile (wersja zapoznawcza)**.
    
    Ta opcja jest nadal zetknie się dzierżaw, jeśli nie ma go na liście, można otworzyć bloku bezpośrednio przy użyciu następującego łącza: https://portal.azure.com/?ScannerConfiguration=true#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade

3. Na **usługi Azure Information Protection — profile (wersja zapoznawcza)** bloku wybierz **Dodaj**:
    
    ![Dodaj profil skanera usługi Azure Information Protection](./media/scanner-add-profile.png)

4. Na **dodać nowy profil** bloku, określ nazwę skanera, który jest używany do identyfikowania jej konfiguracji ustawienia i dane repozytoria do skanowania. Na przykład można określić **Europa** wskaż lokalizację geograficzną repozytoria danych, które będzie obejmować skanera. Gdy później zainstalować lub uaktualnić skaner, musisz określić taką samą nazwę profilu.
    
    Opcjonalnie określ opis do celów administracyjnych, aby pomóc w zidentyfikowaniu skanera nazwa profilu.

5. Dla tej konfiguracji początkowej, należy skonfigurować następujące ustawienia, a następnie wybierz **Zapisz** , ale nie zamykaj bloku:
    
    - **Harmonogram**: Zachowaj wartość domyślną **ręczne**
    - **Typy informacji, które mają zostać odnalezione**: Zmień **tylko zasad**
    - **Konfigurowanie repozytoriów**: Nie należy konfigurować w tej chwili, ponieważ najpierw należy zapisać profil.
    - **Wymuszanie**: Wybierz **wyłączone**
    - **Pliki na podstawie zawartości etykiet**: Zachowaj wartość domyślną **na**
    - **Etykieta domyślna**: Zachowaj wartość domyślną **zasady domyślne**
    - **Pliki relabel**: Zachowaj wartość domyślną **wyłączone**
    - **Zachowaj "Data modyfikacji", "Data ostatniej modyfikacji" i "Zmodyfikowany przez"**: Zachowaj wartość domyślną **na**
    - **Typy plików do skanowania**: Zachowaj ustawienie domyślne typy plików dla **wykluczenia**
    - **Domyślnym właścicielem**: Zachowaj wartość domyślną **konto skanera**

6. Teraz, gdy profil, który jest tworzony i zapisywany, jesteś gotowy powrócić do **skonfigurować repozytoriów** opcję, aby określić magazynów danych do przeskanowania. W przypadku witryn programu SharePoint i bibliotek można określić foldery lokalne, ścieżki UNC i adresy URL serwerów programu SharePoint. 
    
    Program SharePoint Server 2016 i SharePoint Server 2013 są obsługiwane dla programu SharePoint. Program SharePoint Server 2010 jest również obsługiwane w przypadku [rozszerzoną obsługę w tej wersji programu SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).
    
    Aby dodać pierwszy dane przechowywane na **dodać nowy profil** bloku wybierz **skonfigurować repozytoriów** otworzyć **repozytoriów** bloku:
    
    ![Konfigurowanie repozytoria danych skanera usługi Azure Information Protection](./media/scanner-repositories-bar.png)

7. Na **repozytoriów** bloku wybierz **Dodaj**:
    
    ![Dodaj repozytorium danych skanera usługi Azure Information Protection](./media/scanner-repository-add.png)

8. Na **repozytorium** bloku, określ ścieżkę do repozytorium danych. 
    
    Symbole wieloznaczne nie są obsługiwane i lokalizacje WebDav nie są obsługiwane.
    
    Przykłady:
    
    Aby uzyskać ścieżkę lokalną: `C:\Folder`
    
    Dla udziału sieciowego: `C:\Folder\Filename`
    
    Aby uzyskać ścieżkę UNC:`\\Server\Folder`
    
    Dla biblioteki programu SharePoint: `http://sharepoint.contoso.com/Shared%20Documents/Folder`
    
    > [!TIP]
    > Jeśli dodasz ścieżki programu SharePoint dla "Dokumenty udostępnione":
    >
     >- Określ **dokumenty udostępnione** w ścieżce, jeśli chcesz przeprowadzić skanowanie wszystkich dokumentów i folderów z udostępnionych dokumentów. Na przykład: `http://sp2013/Shared Documents`
     >
     >- Określ **dokumenty** w ścieżce, jeśli chcesz przeprowadzić skanowanie wszystkich dokumentów i folderów z podfolderu w folderze Dokumenty udostępnione. Na przykład: `http://sp2013/Documents/Sales Reports`
    
    Dla pozostałych ustawień w tym bloku, nie należy zmieniać w przypadku tej konfiguracji początkowej, ale pozostawić je jako **profilu domyślnego**. Oznacza to, że repozytorium danych dziedziczy ustawienia z profilu skanera. 
    
    Wybierz pozycję **Zapisz**.

9. Jeśli chcesz dodać innego repozytorium danych, powtórz kroki 7 i 8.

10. Możesz teraz zamknąć **dodać nowy profil** bloku i wyświetlić nazwy profilu wyświetlana w **usługi Azure Information Protection — profile (wersja zapoznawcza)** bloku wraz z **harmonogram** przedstawiający kolumny **ręczne** i **WYMUŚ** kolumna jest pusta.

Teraz możesz zainstalować skaner profilem skanera nowo utworzony.

## <a name="install-the-scanner"></a>Zainstaluj skaner

1. Zaloguj się do komputera systemu Windows Server, który będzie uruchamiany skanera. Użyj konta mającego uprawnienia administratora lokalnego i ma uprawnienia do zapisu w bazie danych master programu SQL Server.

2. Otwórz sesję programu Windows PowerShell, za pomocą **Uruchom jako administrator** opcji.

3. Uruchom [AIPScanner instalacji](/powershell/module/azureinformationprotection/Install-AIPScanner) polecenia cmdlet, określając wystąpienia programu SQL Server, na którym chcesz utworzyć bazę danych dla skanera usługi Azure Information Protection, a nazwa profilu skanera, który określono w poprzedniej sekcji: 
    
    ```
    Install-AIPScanner -SqlServerInstance <database name> -Profile <profile name>
    ```
    
    Przykłady, przy użyciu nazwy profilu **Europa**:
    
    Dla domyślnego wystąpienia: `Install-AIPScanner -SqlServerInstance SQLSERVER1 -Profile Europe`
    
    Dla nazwanego wystąpienia: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER -Profile Europe`
    
    For SQL Server Express: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS -Profile Europe`
    
    Po wyświetleniu monitu podaj poświadczenia dla konta usługi skaner (\<domena\nazwa_użytkownika >) i hasło.

4. Sprawdź, czy usługa jest teraz zainstalowany za pomocą **narzędzia administracyjne** > **usług**. 
    
    Nosi nazwę zainstalowanej usługi **skaner ochrony informacji Azure** i jest skonfigurowany do uruchamiania przy użyciu konta usługi skanera, który został utworzony.

Po zainstalowaniu skaner należy można pobrać tokenu dla konta usługi skanera w celu uwierzytelnienia usługi Azure AD, aby uruchomić nienadzorowaną skanera. 

## <a name="get-an-azure-ad-token-for-the-scanner"></a>Pobierz usługę Azure AD token skanera

Token usługi Azure AD umożliwia skanera konto usługi uwierzytelniania w usłudze Azure Information Protection.

1. Wróć do witryny Azure portal, aby utworzyć dwie aplikacje usługi Azure AD, które są potrzebne do określenia tokenu dostępu do uwierzytelniania. Po początkowej logowania interaktywnego token ten umożliwia skanera nieinteraktywnego uruchomienia.
    
    Aby utworzyć te aplikacje, postępuj zgodnie z instrukcjami [jak oznaczyć pliki w trybie nieinteraktywnym usługi Azure Information Protection](./rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) w podręczniku administratora.

2. Z komputera systemu Windows Server, jeśli przyznano konta usługi skanera **logować się lokalnie** prawa do instalacji: Zaloguj się przy użyciu tego konta, a następnie uruchom sesję programu PowerShell. Uruchom [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), określając wartości, które zostały skopiowane z poprzedniego kroku:
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application> -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application>
    ```
    
    Po wyświetleniu monitu podaj hasło dla poświadczeń konta usługi dla usługi Azure AD, a następnie kliknij przycisk **Akceptuj**.
    
    Jeśli nie można udzielić konta usługi skanera **logować się lokalnie** prawa do instalacji: Postępuj zgodnie z instrukcjami w [określanie i użyj parametru tokenu dla polecenia Set-AIPAuthentication](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) sekcji w podręczniku administratora. 

Skaner zawiera teraz token do uwierzytelniania w usłudze Azure AD, który jest ważny przez jeden rok, dwa lata lub nigdy nie wygasa, zgodnie z konfiguracją programu **sieci Web/interfejs API aplikacji** w usłudze Azure AD. Po wygaśnięciu ważności tokenu, należy powtórzyć kroki 1 i 2.

Teraz możesz uruchamiać swoje pierwsze skanowanie w trybie odnajdowania.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-scanner"></a>Uruchomić cykl odnajdowania i wyświetlać raporty dla skanera

1. W witrynie Azure portal wróć do usługi Azure Information Protection można uruchomić skanera. Z **skanera** opcji menu, wybierz opcję **węzłów**. Wybierz węzeł skanera, a następnie **Skanuj teraz** opcji:
    
    ![Zainicjować skanowanie w poszukiwaniu skanera usługi Azure Information Protection](./media/scanner-scan-now.png)
    
    Alternatywnie w sesji programu PowerShell, uruchom następujące polecenie:
    
        Start-AIPScan

2. Poczekaj, aż skanera zakończyć jego cyklu. Podczas skaner ma za pośrednictwem wszystkich plików w magazynach danych, które można określić, skaner zatrzymuje, mimo że usługa skaner jest uruchomiona:
    
        - From the **Azure Information Protection - Nodes** blade, the value for the **STATUS** column changes from **Scanning** to **Idle**.
        
        - Using PowerShell, you can run `Get-AIPScannerStatus` to monitor the status change.
        
        - Check the local Windows **Applications and Services** event log, **Azure Information Protection**. This log also reports when the scanner has finished scanning, with a summary of results. Look for the informational event ID **911**.

3. Przejrzyj raporty, które są przechowywane w lokalizacji %*localappdata*% \Microsoft\MSIP\Scanner\Reports. Podsumowanie pliki txt obejmują czas potrzebny do skanowania liczby skanowanych plików i liczby plików ma dopasowania dla typów informacji. Pliki CSV mają więcej szczegółów dla każdego pliku. Ten folder przechowuje maksymalnie 60 raporty każdy cykl skanowania oraz wszystkich, ale jest skompresowany najnowszy raport, aby zminimalizować ilość wymaganego miejsca na dysku.
    
    > [!NOTE]
    > Poziom rejestrowania można zmienić za pomocą *ReportLevel* parametrem [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/set-aipscannerconfiguration), ale nie można zmienić lokalizację folderu raportu lub nazwy. Należy rozważyć użycie połączenie katalogów dla folderu, jeśli chcesz przechowywać sprawozdania na inny wolumin lub partycji.
    >
    > Na przykład za pomocą [Mklink](/windows-server/administration/windows-commands/mklink) polecenia: `mklink /j C:\Users\aipscannersvc\AppData\Local\Microsoft\MSIP\Scanner\Reports D:\Scanner_reports`
    
    Z naszych ustawieniem **tylko zasady** dla **typy informacji, które mają zostać odnalezione**tylko pliki, które spełniają warunki zostały skonfigurowane dla automatycznej klasyfikacji znajdują się szczegółowe raporty. Jeśli nie widzisz wszystkie etykiety zastosowane, sprawdź, czy dana konfiguracja etykiety obejmuje automatyczne zamiast zalecana klasyfikacja.
    
    > [!TIP]
    > Skanery wysyłać tych informacji do usługi Azure Information Protection co pięć minut, dzięki czemu można wyświetlić wyniki w czasie zbliżonym do rzeczywistego w witrynie Azure portal. Aby uzyskać więcej informacji, zobacz [raportowania usługi Azure Information Protection](reports-aip.md). 
        
    Wyniki są nie zgodnie z oczekiwaniami, należy ponownie skonfigurować warunki, które określono dla Ciebie etykiet w zasadach usługi Azure Information Protection. Jeśli tak jest rzeczywiście, powtórz kroki od 1 do 3, dopóki nie będziesz gotowy zmienić konfigurację do zastosowania klasyfikacji i opcjonalnie ochrony. 

Gdy wszystko będzie gotowe automatycznie oznaczyć pliki, które wykrywa skaner, przejdź do następnej procedury. 

## <a name="configure-the-scanner-to-apply-classification-and-protection"></a>Konfigurowanie skanera do zastosowania funkcji klasyfikacji i ochrony

Jeśli postępujesz zgodnie z tymi instrukcjami skaner jednym czasie i w trybie tylko do raportowania. Aby zmienić te ustawienia, należy dokonać edycji profilu skanera:

1. Po powrocie **[usługi Azure Information Protection — profile (wersja zapoznawcza)](https://portal.azure.com/?ScannerConfiguration=true#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade)** bloku, wybierz profil skanera, aby go edytować.

2. Na \< **nazwa profilu**> bloku, Zmień następujące dwa ustawienia, a następnie wybierz **Zapisz**:
    
   - **Harmonogram**: Zmień **zawsze**
   - **Wymuszanie**: Wybierz **na**
    
     Istnieją inne ustawienia konfiguracji, które można zmienić. Na przykład czy atrybuty pliku zostaną zmienione i czy skaner może relabel plików. Korzystanie z informacji pomocy okno podręczne, aby dowiedzieć się więcej informacji na temat każdego ustawienia konfiguracji.

3. Zanotuj wartość w bieżącym czasem i uruchomić skanera ponownie z **usługi Azure Information Protection — węzły** bloku:
    
    ![Zainicjować skanowanie w poszukiwaniu skanera usługi Azure Information Protection](./media/scanner-scan-now.png)
    
    Można również uruchomić następujące polecenie w sesji programu PowerShell:
    
        Start-AIPScan

4. Monitorowanie dziennika zdarzeń dla typu informacyjny **911** ponownie z czasem sygnatury później niż podczas uruchamiania skanowania w poprzednim kroku. 
    
    Sprawdź, raporty, aby zobaczyć szczegółowe informacje, które pliki zostały oznaczone, jakie klasyfikacji została zastosowana do każdego pliku i tego, czy ochrona została zastosowana do nich. Możesz też użyć witryny Azure portal, aby wyraźniej widzieć te informacje.

Ponieważ firma Microsoft skonfigurowany harmonogram uruchamiany w sposób ciągły i, gdy skaner pracował przechodzi przez wszystkie pliki, automatycznie uruchamia nowy cykl tak, aby wszystkie nowe i zmienione pliki zostaną odnalezione.


## <a name="how-files-are-scanned"></a>Jak pliki są skanowane

Skaner jest uruchamiany za pośrednictwem następujących procesów, gdy skanuje pliki.

### <a name="1-determine-whether-files-are-included-or-excluded-for-scanning"></a>1. Określić, czy pliki są dołączone lub wykluczone skanowania 
Skaner automatycznie pomija pliki, które są [wykluczane z klasyfikacji i ochrony](./rms-client/client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection), takich jak pliki wykonywalne i pliki systemowe.

Możesz zmienić to zachowanie, definiując listę typów plików ze skanowaniem lub Wyklucz ze skanowania. Można określić tę listę pod kątem skaner na są domyślnie stosowane do wszystkich repozytoriów danych. Ponadto można określić listę dla każdego repozytorium danych. Aby określić tej listy, użyj **typy w celu skanowania plików** ustawienia w profilu skanera:

![Konfiguruj typy plików do skanowania w poszukiwaniu skanera usługi Azure Information Protection](./media/scanner-file-types.png)

### <a name="2-inspect-and-label-files"></a>2. Sprawdzanie i oznaczyć pliki

Skaner następnie używa filtrów do skanowania obsługiwanych typów plików. Te same filtry są używane przez system operacyjny Windows Search i indeksowania. Bez przeprowadzania dodatkowej konfiguracji Windows IFilter jest używane do skanowania typów plików, które są używane przez program Word, Excel, PowerPoint i dla dokumentów PDF i pliki tekstowe.

Pełną listę typów plików, które są obsługiwane przez domyślny i dodatkowe informacje, jak skonfigurować istniejące filtry, które zawierają pliki zip i plików TIFF, zobacz [typy plików obsługiwane w celu przeprowadzenia inspekcji](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-inspection).

Po inspekcji następujące typy plików można etykiety za pomocą warunków, które określono dla etykiety. Lub, jeśli używasz trybu odnajdywania te pliki mogą być zgłaszane zawiera warunki, które określona dla etykiety lub wszystkich typów znane poufne informacje. 

Jednak skaner nie etykiety pliki w następujących okolicznościach:

- Jeśli klasyfikacja i ochrona nie stosuje się etykietę, a typ pliku nie [obsługuje tylko Klasyfikacja](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-classification-only).

- Jeśli stosuje się etykietę klasyfikacji i ochrony, ale skaner nie chroni typu pliku.
    
    Domyślnie skaner chroni tylko typów plików pakietu Office i plików PDF, wtedy, gdy są chronione przy użyciu standardu ISO do szyfrowania plików PDF. Inne typy plików mogą być chronione, kiedy należy [edytować rejestr](#editing-the-registry-for-the-scanner) zgodnie z opisem w poniższej sekcji.

Na przykład po sprawdzeniu plików mających rozszerzenie nazwy pliku txt, skaner nie można zastosować etykietę, który skonfigurowano na potrzeby klasyfikacji, ale nie ochrony, ponieważ typ pliku txt nie obsługuje tylko do klasyfikacji. Jeśli etykieta jest skonfigurowany dla klasyfikacji i ochrony, a edycji rejestru dla typu pliku txt, skaner można oznaczyć plik. 

> [!TIP]
> W trakcie tego procesu Jeśli skaner zatrzymuje i nie wykona skanowanie dużej liczby plików w repozytorium, konieczne może być zwiększenie liczby portów dynamicznych dla systemu operacyjnego, obsługującym pliki. Serwer zaostrzanie poziomu zabezpieczeń dla programu SharePoint może być jednym z powodów dlaczego skaner przekracza liczbę dozwolonych połączeń i w związku z tym zatrzymuje.
> 
> Aby sprawdzić, czy jest to przyczyną skanera zatrzymywania, sprawdzić, jeśli następujący komunikat o błędzie jest rejestrowany dla skanera w lokalizacji %*localappdata*%\Microsoft\MSIP\Logs\MSIPScanner.iplog (zip w przypadku wielu dzienników dla): **Nie można nawiązać połączenia z serwerem zdalnym---> System.Net.Sockets.SocketException: Tylko jedno użycie każdego adresu gniazda (adres protokołu/network/port) jest normalnie dozwolone IP:port**
>
> Aby uzyskać więcej informacji na temat sposobu wyświetlania bieżącego zakresu portów i zwiększyć zakres, zobacz [ustawień, które można modyfikować, aby zwiększyć wydajność sieci](https://docs.microsoft.com/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).

### <a name="3-label-files-that-cant-be-inspected"></a>3. Oznacz pliki, których nie można przeprowadzić inspekcji
Dla typów plików, których nie można przeprowadzić inspekcji skaner ma zastosowanie etykiety domyślnej w zasadach usługi Azure Information Protection lub etykiety domyślnej, konfigurowanego do skanera.

Tak jak w poprzednim kroku skaner nie może oznaczyć pliki w następujących okolicznościach:

- Jeśli klasyfikacja i ochrona nie stosuje się etykietę, a typ pliku nie [obsługuje tylko Klasyfikacja](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-classification-only).

- Jeśli stosuje się etykietę klasyfikacji i ochrony, ale skaner nie chroni typu pliku.
    
    Domyślnie skaner chroni tylko typów plików pakietu Office i plików PDF, wtedy, gdy są chronione przy użyciu standardu ISO do szyfrowania plików PDF. Inne typy plików mogą być chronione, kiedy należy [edytować rejestr](#editing-the-registry-for-the-scanner) zgodnie z opisem.


### <a name="editing-the-registry-for-the-scanner"></a>Edytując rejestr skanera

Aby zmienić domyślne zachowanie skanera ochronę typów plików innych niż pliki pakietu Office i plików PDF, należy ręcznie zmodyfikować rejestr i określić dodatkowe typy plików, które mają być chronione i typ ochrony (natywny lub ogólny). Aby uzyskać instrukcje, zobacz [Konfiguracja interfejsu API plików](develop/file-api-configuration.md) we wskazówkach dla deweloperów. W tej dokumentacji dla deweloperów ochrona ogólna jest określana jako „PFile”. Ponadto, określone skanera:

- Skaner ma swój własny domyślne zachowanie: Tylko formatów plików pakietu Office i dokumentów PDF są chronione domyślnie. W przypadku braku modyfikacji rejestru innych typów plików nie będą oznaczone lub objęte ochroną przez skaner.

- Jeśli chcesz, aby takie samo zachowanie domyślne dla ochrony klienta usługi Azure Information Protection, w którym wszystkie pliki są automatycznie chronione przy użyciu ochrony natywnej lub ogólnej: Określ `*` symboli wieloznacznych jako klucza rejestru i `Default` jako dane wartości.

Podczas edycji rejestru ręcznie utworzyć **MSIPC** klucza i **FileProtection** klucz, jeśli nie istnieją, a także klucz dla każdego rozszerzenia nazwy pliku.

Na przykład skanera w celu ochrony obrazów TIFF oprócz plików pakietu Office i plików PDF, rejestru, po zakończeniu edycji, będzie wyglądać podobnie do poniższej ilustracji. Jako plik obrazu TIFF, pliki obsługują ochronę natywną i wynikowy rozszerzenie nazwy pliku jest ptiff.

![Edytując rejestr skanera w celu zastosowania ochrony](./media/editregistry-scanner.png)

Aby uzyskać listę typów plików tekstowych i obrazów, które podobnie obsługują ochronę natywną, ale musi być określona w rejestrze, zobacz [obsługiwane typy plików do klasyfikacji i ochrony](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection) w podręczniku administratora.

Dla plików, które nie obsługują ochronę natywną, określ rozszerzenie nazwy pliku jako nowy klucz i **PFile** dla ochrony ogólnej. Wynikowy rozszerzenie nazwy pliku dla chronionych plików to pfile.


## <a name="when-files-are-rescanned"></a>Kiedy pliki są ponownie skanowana

Dla pierwszego cyklu skanowania skaner sprawdza wszystkie pliki w magazynach danych skonfigurowane, a następnie w przypadku skanowania kolejnych tylko nowe lub zmodyfikowane pliki są kontrolowane. 

Można wymusić skanera, aby sprawdzić wszystkie pliki ponownie z **usługi Azure Information Protection — węzły** bloku w witrynie Azure portal. Wybierz skaner z listy, a następnie wybierz **ponownego skanowania wszystkich plików** opcji:

![Zainicjuj ponownego skanowania skanera usługi Azure Information Protection](./media/scanner-rescan-files.png)

Ponownie sprawdzanie wszystkich plików jest przydatne w przypadku, gdy chcesz, aby raporty mają obejmować wszystkie pliki i wybór tej konfiguracji jest zwykle używany podczas pracy w trybie wykrywania skanera. Po zakończeniu pełnego skanowania typ skanowania automatycznie zmienia się przyrostowe, aby w przypadku kolejne skanowania są skanowane tylko nowe lub zmodyfikowane pliki.

Ponadto wszystkie pliki są kontrolowane wraz z skaner pobraniem zasad usługi Azure Information Protection, który zawiera warunki, nowe lub zostały zmienione. Skaner odświeża zasady co godzinę, a gdy usługa zostanie uruchomiona i zasad jest starsza niż jedna godzina.  

> [!TIP]
> Jeśli musisz odświeżyć zasady w terminie wcześniejszym niż ten interwał jedną godzinę, na przykład okresie testowania: Ręcznie usuń plik zasad **Policy.msip** z obu **%LocalAppData%\Microsoft\MSIP\Policy.msip** i **%LocalAppData%\Microsoft\MSIP\Scanner**. Następnie uruchom ponownie usługę skanera informacji platformy Azure.
> 
> Jeśli zmienisz ustawienia ochrony w zasadach, również poczekaj 15 minut od po zapisaniu ustawień ochrony przed ponownym uruchomieniem usługi.

Skaner pobraniu zasad, który miał żadne warunki automatycznej skonfigurowane kopię pliku zasad w folderze skanera, nie powoduje aktualizacji. W tym scenariuszu należy usunąć plik zasad **Policy.msip** z obu **%LocalAppData%\Microsoft\MSIP\Policy.msip** i **%LocalAppData%\Microsoft\MSIP\Scanner**zanim skaner można użyć pliku nowo pobrane zasady, który zawiera etykiety poprawnie uznał warunki automatycznej.

## <a name="editing-in-bulk-for-the-data-repository-settings"></a>Edytowanie w trybie zbiorczym ustawień repozytorium danych

W przypadku repozytoria danych, które zostały dodane do profilu skanera, można użyć **wyeksportować** i **importu** opcji, aby szybko wprowadzać zmiany w ustawieniach. Na przykład dla repozytoriów danych programu SharePoint, chcesz dodać nowy typ pliku, które mają zostać wykluczone ze skanowania.

Zamiast edytowania każdego repozytorium danych w witrynie Azure portal, należy użyć **wyeksportować** opcję **repozytoriów** bloku:

![Eksportowanie ustawień repozytorium danych skanera](./media/export-scanner-repositories.png)

Ręcznie Edytuj plik, aby wprowadzić zmiany, a następnie użyj **importu** opcji w tym samym bloku.

## <a name="using-the-scanner-with-alternative-configurations"></a>Za pomocą skanera usługi za pomocą alternatywnej konfiguracji

Istnieją dwa scenariusze alternatywne, które skanera usługi Azure Information Protection obsługuje, gdzie etykiety nie trzeba skonfigurować wszelkie warunki: 

- Stosowanie etykiety domyślnej, do wszystkich plików w repozytorium danych.
    
    W przypadku tej konfiguracji należy ustawić **etykiety domyślnej** do **niestandardowe**i wybierz etykietę do wykorzystania.
    
    Zawartość tych plików nie są kontrolowane i wszystkich plików w repozytorium danych są oznaczone etykietami zgodnie z etykiety domyślnej, określony dla profilu skanera lub repozytorium danych.
    

- Zidentyfikuj wszystkie warunki niestandardowe i typy znanych informacji poufnych.
    
    W przypadku tej konfiguracji należy ustawić **typy informacji, które mają zostać odnalezione** do **wszystkich**.
    
    Skaner używa warunki niestandardowe, które zostały określone przez etykiet w zasadach usługi Azure Information Protection i listę typów informacji, które są dostępne do określenia dla etykiet w zasadach usługi Azure Information Protection. To ustawienie pozwala poufne informacje, które mogą nie należy pamiętać były, ale kosztem skanowania ze stawkami za usługi skanera.
    
    Następnego przewodnika Szybki Start dla wersji ogólnie dostępnej skanera wykorzystują tę konfigurację: [Szybki start: Jakie informacje poufne masz](quickstart-findsensitiveinfo.md).

## <a name="optimizing-the-performance-of-the-scanner"></a>Optymalizacja wydajności skanera

Aby zmaksymalizować wydajność skanera:

- **Masz szybkie i niezawodne połączenie sieciowe między komputerem skanera i magazyn danych zeskanowane**
    
    Na przykład umieścić komputer skanera w tej samej sieci lokalnej lub (preferowany), w tym samym segmencie sieci do przechowywania danych skanowane.
    
    Jakość połączenia sieciowego ma wpływ na wydajność skanera, ponieważ inspekcji plików, skaner przesyła zawartość plików z komputera z uruchomioną usługą skanera. Zmniejsz (lub wyeliminować) liczby przeskoków sieciowych, te dane musi przyjechać również zmniejszyć obciążenie w sieci. 

- **Upewnij się, że na komputerze skanera dostępnego procesora zasobów**
    
    Inspekcja zawartości pliku i szyfrowania i odszyfrowywania plików to akcje, obciążenie procesora. Monitorowanie typowych skanowania cykle swoich magazynów określone dane ustalić, czy brak zasobów procesora negatywnego wpływu na wydajność skanera.
    
- **Skanuj folderów lokalnych na komputerze z uruchomioną usługą skanera**
    
    W przypadku folderów do skanowania na serwerze Windows zainstaluj skaner na innym komputerze i skonfigurować te foldery, tak jak w sieciowych udziałach do skanowania. Oddzielanie dwie funkcje obsługi plików i skanowanie plików oznacza zasoby obliczeniowe dla tych usług nie są konkurującymi ze sobą.

Jeśli to konieczne, należy zainstalować wiele wystąpień skanera. Skaner usługi Azure Information Protection obsługuje wielu baz danych konfiguracji na tego samego wystąpienia programu SQL server po określeniu nazwy profilu niestandardowego, skanera.

Inne czynniki, które mają wpływ na wydajność skanera:

- Bieżący czas ładowania i odpowiedzi oraz magazynów danych, które zawierają pliki do skanowania

- Czy skaner działa w trybie wykrywania, czy tryb wymuszania
    
    Tryb odnajdywania zazwyczaj ma wyższy skanowanie szybkości niż w trybie wymuszania, ponieważ odnajdywania wymaga pojedynczego pliku odczytać akcji, natomiast wymusić tryb wymaga, aby odczytywać i zapisywać akcji.

- Zmiana warunków w usługi Azure Information Protection
    
    Twoje pierwsze cykl skanowania w poszukiwaniu po skaner musi sprawdzić każdy plik będzie trwać dłużej niż skanowania kolejnych cykli, które domyślnie inspekcji tylko nowych i zmienionych plików. Jednak w przypadku zmiany warunków w zasadach usługi Azure Information Protection, wszystkie pliki są skanowane ponownie, zgodnie z opisem w [poprzedniej sekcji](#when-files-are-rescanned).

- Wybranego poziom rejestrowania
    
    Możesz wybrać między **debugowania**, **informacje**, **błąd** i **poza** raportów skanera. **Wyłącz** skutkuje najlepszą wydajność; **Debugowania** znacznie spowalnia skaner i powinna być używana tylko w przypadku rozwiązywania problemów. Aby uzyskać więcej informacji, zobacz *ReportLevel* parametr [AIPScannerConfiguration zestaw](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) polecenia cmdlet.

- Same pliki:
    
    - Pliki pakietu Office są szybsze zeskanowane niż pliki PDF.
    
    - Niechronione pliki przebiegają szybciej skanować niż chronionych plików.
    
    - Duże pliki oczywiście skanowanie trwało dłużej niż małe pliki.

- Dodatkowo:
    
    - Upewnij się, że konto usługi, na którym uruchomiono skaner ma wyłącznie prawa, które zostały udokumentowane w artykule [wymagania wstępne skanera](#prerequisites-for-the-azure-information-protection-scanner) sekcji, a następnie skonfiguruj [zaawansowane właściwości klienta](./rms-client/client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) wyłączyć niskim poziom skaner integralności.
    
    - Skaner przebiega szybciej, korzystając z [alternatywnej konfiguracji](#using-the-scanner-with-alternative-configurations) do zastosowania etykiety domyślnej do wszystkich plików, ponieważ skaner nie Sprawdź zawartość pliku.
    
    - Skaner działa wolniej, gdy używasz [alternatywnej konfiguracji](#using-the-scanner-with-alternative-configurations) Aby zidentyfikować wszystkie warunki niestandardowe i typy znanych informacji poufnych.
    

## <a name="list-of-cmdlets-for-the-scanner"></a>Listę poleceń cmdlet skanera

Możesz teraz skonfigurować skanera w witrynie Azure portal, poleceń cmdlet z poprzednich wersji, skonfigurowanych repozytoriów danych i listy typów plików skanowanych obecnie są przestarzałe. 

Polecenia cmdlet, które będą pozostawały obejmują polecenia cmdlet, które Instalowanie i uaktualnianie skanera, zmienianie bazy danych konfiguracji skanera i profilu, zmiany lokalne poziomu raportowania i zaimportować ustawienia konfiguracji dla odłączonych komputerów. 

Pełna lista poleceń cmdlet, która obsługuje wersję zapoznawczą skaner: 

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)

- [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner)


## <a name="event-log-ids-and-descriptions-for-the-scanner"></a>Identyfikatory i opisy skanera dziennika zdarzeń

Następujące sekcje zawierają do identyfikowania możliwych identyfikatorów zdarzeń i opisy skanera. Te zdarzenia są rejestrowane na serwerze, który uruchamia usługę skanera w Windows **aplikacji i usług** dziennika zdarzeń **usługi Azure Information Protection**.

-----

Informacje o **910**

**Skaner cyklu pracę.**

To zdarzenie jest rejestrowane, gdy usługa skanera została uruchomiona i rozpocznie skanowanie w poszukiwaniu plików w danych repozytoriów, określonych przez użytkownika.

----

Informacje o **911**

**Cykl skanera zostało zakończone.**

To zdarzenie jest rejestrowane, gdy skanera zostało zakończone ręcznie lub skaner zakończył cykl ciągłe harmonogramu.

Jeśli skaner została skonfigurowana do uruchamiania ręcznego, zamiast ciągle, aby skanować pliki ponownie, należy ustawić **harmonogram** do **ręczne** lub **zawsze** profil skanera, a następnie Uruchom ponownie usługę.

----

## <a name="next-steps"></a>Następne kroki

Są Państwo zainteresowani implementacji tego skanera zespołu inżynierów usług podstawowych i operacje w programie Microsoft?  Przeczytaj techniczną analizę przypadku: [Automatyzowanie ochrony danych za pomocą skanera usługi Azure Information Protection](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

Możesz się zastanawiać: [Jaka jest różnica między infrastruktury klasyfikacji plików systemu Windows Server i skaner usługi Azure Information Protection?](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

Program PowerShell umożliwia również interaktywnie klasyfikować i chronić pliki z komputera stacjonarnego. Aby uzyskać więcej informacji na temat tego i innych scenariuszy korzystających z programu PowerShell, zobacz [przy użyciu programu PowerShell z klientem usługi Azure Information Protection](./rms-client/client-admin-guide-powershell.md).


