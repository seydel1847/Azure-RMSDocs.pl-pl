---
title: Podręcznik administratora klienta usługi Azure Information Protection
description: Instrukcje i informacje dla administratorów sieci przedsiębiorstwa odpowiedzialnych za wdrażanie klienta usługi Azure Information Protection dla systemu Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/02/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 33a5982f-7125-4031-92c2-05daf760ced1
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: be6477edae471bddbcf3a5d4e6c7bb0cfcec1e4e
ms.sourcegitcommit: 4f22874c3c2fb9632d57932148664c40b3907a78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2018
ms.locfileid: "52831259"
---
# <a name="azure-information-protection-client-administrator-guide"></a>Podręcznik administratora klienta usługi Azure Information Protection

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, systemu Windows Server 2008 R2*

Informacje zawarte w tym przewodniku są przydatne dla osób odpowiedzialnych za klienta usługi Azure Information Protection w sieci przedsiębiorstwa lub chcącym uzyskać więcej informacji technicznych, niż jest dostępnych w [podręczniku użytkownika klienta usługi Azure Information Protection](client-user-guide.md). 

Przykład:

- Opis różnych składników tego klienta i określenie, czy należy je zainstalować

- Jak zainstalować klienta dla użytkowników, z informacjami na temat wymagań wstępnych, opcji instalacji i parametrów oraz weryfikowania

- Jak obsłużyć konfiguracje niestandardowe, które często wymagają edycji rejestru

- Lokalizowanie plików klienta i dzienników użycia

- Identyfikowanie typów plików obsługiwanych przez klienta

- Konfigurowanie i używanie witryny śledzenia dokumentów dla użytkowników

- Użycie klienta z programem PowerShell w celu sterowania z poziomu wiersza polecenia

**Czy masz pytanie, na które nie ma odpowiedzi w tej dokumentacji?** Odwiedź [witrynę Yammer usługi Azure Information Protection](https://www.yammer.com/AskIPTeam). 

## <a name="technical-overview-of-the-azure-information-protection-client"></a>Omówienie aspektów technicznych klienta usługi Azure Information Protection

Klient usługi Azure Information Protection zawiera następujące elementy:

- Dodatek pakietu Office, który jest instalowany jest pasek usługi Azure Information Protection dla użytkowników wybrać etykiety klasyfikacji, a **Chroń** przycisk na Wstążce udostępniający dodatkowe opcje. Dla programu Outlook **nie przesyłaj dalej** przycisk jest również dostępny dla wstążki.

- Opcje dostępne po kliknięciu prawym przyciskiem myszy w oknie Eksploratora plików Windows, które pozwalają użytkownikom stosować etykiety klasyfikacji i ochronę plików.

- Przeglądarka do wyświetlania chronionych plików, gdy natywna aplikacja nie może ich otworzyć.

- Moduł środowiska PowerShell pozwalający dodawać i usuwać etykiety klasyfikacji oraz włączać i wyłączać ochronę plików. 
    
    Ten moduł zawiera polecenia cmdlet, aby zainstalować i skonfigurować [skanera usługi Azure Information Protection](../deploy-aip-scanner.md) , które jest uruchamiane jako usługa w systemie Windows Server. Ta usługa umożliwia odnajdywanie, klasyfikowanie i ochrona plików w magazynach danych, takich jak udziały sieciowe i biblioteki programu SharePoint Server.

- Klient usługi Rights Management komunikujący się z usługą Azure Rights Management (Azure RMS) lub usługami Active Directory Rights Management (AD RMS).

Klient usługi Azure Information Protection najlepiej nadaje się do pracy z usługami Azure — usługą Azure Information Protection i jej usługami ochrony danych, Azure Rights Management. Jednak z pewnymi ograniczeniami klient usługi Azure Information Protection działa też z lokalną wersją usług Rights Management — AD RMS. Obszerne porównanie funkcji obsługiwanych przez usługi Azure Information Protection i AD RMS można znaleźć w artykule [Porównanie usług Azure Information Protection i AD RMS](../compare-on-premise.md). 

Jeśli korzystasz z usług AD RMS i chcesz przeprowadzić migrację do usługi Azure Information Protection, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../migrate-from-ad-rms-to-azure-rms.md).


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Czy należy wdrożyć klienta usługi Azure Information Protection?

Dokonaj wdrożenia klienta usługi Azure Information Protection w następujących przypadkach:

- Chcesz klasyfikować (i ewentualnie chronić) dokumenty i wiadomości e-mail, wybierając etykiety w aplikacjach pakietu Office (Word, Excel, PowerPoint, Outlook).

- Chcesz klasyfikować (i ewentualnie chronić) dokumenty i wiadomości e-mail za pomocą Eksploratora plików, który obsługuje dodatkowe typy plików, wybór wielokrotny i foldery.

- Chcesz uruchamiać skrypty, które klasyfikują (i ewentualnie chronią) dokumenty za pomocą poleceń środowiska PowerShell.

- Chcesz uruchomić to usługa, która umożliwia odnajdywanie, klasyfikują (i opcjonalnie — chroni) plików, które są przechowywane lokalnie.

- Chcesz wyświetlać chronione dokumenty, gdy natywna aplikacja wyświetlająca je nie jest zainstalowana lub nie może otworzyć tych dokumentów.

- Chcesz po prostu chronić pliki za pomocą Eksploratora plików lub poleceń środowiska Powershell.

- Chcesz umożliwić użytkownikom i administratorom śledzenie i odwoływanie chronionych dokumentów.

- Chcesz usuwać szyfrowanie z plików i kontenerów (wyłączać ochronę) w trybie zbiorczym na potrzeby odzyskiwania danych.

- Korzystasz z pakietu Office 2010 i chcesz chronić dokumenty i wiadomości e-mail za pomocą usługi Azure Rights Management.

Przykład przedstawiający klienta usługi Azure Information Protection dodatku dla aplikacji pakietu Office wyświetla etykiety klasyfikacji dla Twojej organizacji i nowy **Chroń** przycisk na Wstążce:

![Pasek usługi Azure Information Protection z zasadami domyślnymi](../media/word2016-calloutsv2.png)

## <a name="installing-and-supporting-the-azure-information-protection-client"></a>Instalacji i obsługi klienta usługi Azure Information Protection

Klient usługi Azure Information Protection można zainstalować za pomocą Windows Update, plik wykonywalny lub plik Instalatora Windows. Aby uzyskać więcej informacji o poszczególnych opcjach wyboru i instrukcje, zobacz [zainstalować klienta usługi Azure Information Protection dla użytkowników](client-admin-guide-install.md).  

Następujące sekcje zawierają informacje do dodatkowych informacji dotyczących instalowania klienta. 

### <a name="installation-checks-and-troubleshooting"></a>Kontroli instalacji i rozwiązywania problemów

Gdy klient jest zainstalowany, użyj **Pomoc i opinie** opcję, aby otworzyć **Microsoft Azure Information Protection** okno dialogowe:

- W aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** wybierz kolejno opcje **Chroń**, a następnie **Pomoc i opinie**.

- Korzystając z Eksploratora plików, zaznacz plik, pliki lub folder, kliknij je prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**, a następnie wybierz opcję **Pomoc i opinie**. 

#### <a name="help-and-feedback-section"></a>Sekcja **Pomoc i opinie**

Link **Powiedz mi więcej** domyślnie prowadzi do witryny internetowej usługi [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection), ale można go skonfigurować dla niestandardowego adresu URL jako jedno z [ustawień zasad](../configure-policy-settings.md) w zasadach usługi Azure Information Protection.

**Zgłosić problem** łącza są wyświetlane w wersji zapoznawczej wersji klienta i nie w wersji ogólnodostępnej. Domyślnie opcja ta wysyła wiadomość e-mail do firmy Microsoft, ale można skonfigurować ciągu HTTP dla użytkowników, określając [Zaawansowane ustawienia klienta](client-admin-guide-customizations.md#modify-the-email-address-for-the-report-an-issue-link). Na przykład określić adres e-mail pomocy technicznej.

Funkcja **Wyeksportuj dzienniki** umożliwia automatyczne zebranie i dołączenie plików dziennika klienta usługi Azure Information Protection w przypadku wyświetlenia prośby o ich przesłanie zespołowi pomocy technicznej firmy Microsoft. Ta opcja umożliwia także wysyłanie plików dziennika zespołowi pomocy technicznej przez użytkowników końcowych.

**Resetowanie ustawień** wylogowaniu się użytkownika, usuwa aktualnie pobrane zasady usługi Azure Information Protection i resetuje ustawienia użytkownika dla usługi Azure Rights Management.

##### <a name="more-information-about-the-reset-settings-option"></a>Więcej informacji na temat opcji resetowania ustawień

- Nie trzeba być administratorem lokalnym, aby używać tej opcji, a ta akcja nie jest rejestrowana w Podglądzie zdarzeń. 

- O ile pliki nie zostały zablokowane, ta akcja spowoduje usunięcie wszystkich plików w poniższych lokalizacjach. Te pliki obejmują certyfikaty klienta, szablony usługi Rights Management, zasady usługi Azure Information Protection i buforowane poświadczenia użytkowników. Pliki dzienników klienta nie są usuwane.
    
    - %LocalAppData%\Microsoft\DRM
    
    - %LocalAppData%\Microsoft\MSIPC
    
    - %LocalAppData%\Microsoft\MSIP\Policy.msip
    
    - %LocalAppData%\Microsoft\MSIP\TokenCache

- Następujące ustawienia i klucze rejestru zostaną usunięte. Jeśli ustawienia dla każdego z tych kluczy rejestru wartości niestandardowych, te należy ponownie skonfigurować po zresetowaniu klienta. 
    
    Zazwyczaj sieciach firmowych, te ustawienia są skonfigurowane za pomocą zasad grupy, w którym to przypadku one są automatycznie przywracane po odświeżeniu zasad grupy na komputerze. Jednak może być pewnym ustawieniom, które są skonfigurowane jeden raz przy użyciu skryptu, lub ręcznie skonfigurowane. W takich sytuacjach należy wykonać dodatkowe kroki, aby ponownie skonfigurować te ustawienia. Na przykład komputerów może uruchomić skrypt, jeden raz można skonfigurować ustawienia przekierowania do usługi Azure Information Protection, ponieważ migrujesz z usług AD RMS i nadal masz punkt połączenia usługi w sieci. Po przywróceniu klienta, komputer musi ponownie uruchomić ten skrypt.
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\16.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Classes\Local Settings\Software\Microsoft\MSIPC    

- Aktualnie zalogowany użytkownik zostanie wylogowany.

#### <a name="client-status-section"></a>Sekcja **Stan klienta**

Użyj wartości **Połączono jako**, aby upewnić się, że wyświetlana nazwa użytkownika identyfikuje konto przeznaczone do użycia w ramach procesu uwierzytelniania usługi Azure Information Protection. Ta nazwa użytkownika musi pasować do konta używanego w usłudze Office 365 lub Azure Active Directory. Konto musi również należeć do dzierżawy skonfigurowanej pod kątem obsługi usługi Azure Information Protection.

Jeśli musisz zalogować się jako inny użytkownik niż ten, który jest aktualnie wyświetlany, zobacz sekcję [Logowanie się jako inny użytkownik](client-admin-guide-customizations.md#sign-in-as-a-different-user).

Zawartość pola **Ostatnie połączenie** informuje o tym, kiedy ostatnio klient połączył się z usługą Azure Information Protection w organizacji. Informację tę można połączyć z datą i godziną z obszaru **Zasady usługi Information Protection zainstalowano**, aby sprawdzić, kiedy ostatnio zainstalowano lub zaktualizowano zasady usługi Azure Information Protection. Gdy klient łączy się z usługą, automatycznie pobiera najnowsze zasady, jeśli wykryje zmiany w porównaniu z obecnymi zasadami lub jeśli minęły 24 godziny. Jeśli wprowadzono zmiany zasad po wyświetlonym czasie, zamknij i ponownie otwórz aplikację pakietu Office.

Jeśli widzisz komunikat **Ten klient nie ma licencji dla pakietu Office Professional Plus**: klient usługi Azure Information Protection wykrył, że zainstalowana wersja pakietu Office nie obsługuje stosowania ochrony usługi Rights Management. W przypadku wykrycia tego braku obsługi etykiety informujące o objęciu ochroną nie są wyświetlane na pasku usługi Azure Information Protection.

Użyj informacji z obszaru **Wersja**, aby potwierdzić, która wersja klienta jest zainstalowana. Należy sprawdzić, czy jest zainstalowana najnowsza wersja wraz z odpowiednimi poprawkami i nowymi funkcjami. W tym celu należy kliknąć link **Co nowego** i sprawdzić zawartość obszaru [Historia wersji](client-version-release-history.md) klienta.

## <a name="support-for-multiple-languages"></a>Obsługa wielu języków

Klient usługi Azure Information Protection obsługuje te same języki, które obsługuje usługi Office 365. Aby uzyskać listę tych języków, zobacz **usługi Office 365, Exchange Online Protection i usługi Power BI** sekcja [dostępność międzynarodowa](https://products.office.com/business/international-availability) strony z pakietu Office.

Dla tych języków, opcje menu, okna dialogowe i komunikaty z usługi Azure Information Protection klienta są wyświetlane w języku użytkownika. Istnieje jeden Instalator, który wykrywa język, dzięki czemu dodatkowa konfiguracja nie jest wymagane do zainstalowania klienta usługi Azure Information Protection dla różnych języków. 

Jednak nazwy etykiet i opisy, które określisz nie są automatycznie przekształcane podczas konfigurowania etykiet w zasadach usługi Azure Information Protection. Począwszy od 30 sierpnia 2017 r. bieżący [domyślne zasady](../configure-policy-default.md) obejmuje obsługę w przypadku niektórych języków. Aby użytkownikom były wyświetlane etykiety w języku preferowanym udostępnić własne tłumaczenia i skonfigurować zasady usługi Azure Information Protection pod kątem ich używania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiet w różnych językach dla usługi Azure Information Protection](../configure-policy-languages.md). Oznaczenia wizualne nie są przekształcane i nie obsługują więcej niż jednym języku.

## <a name="post-installation-tasks"></a>Zadań poinstalacyjnych

Po zainstalowaniu klienta usługi Azure Information Protection, upewnij się, możesz udzielić użytkownikom instrukcje dotyczące sposobu oznaczać swoje dokumenty i wiadomości e-mail i wskazówki dotyczące etykiet, które należy wybrać dla określonych scenariuszy. Przykład:

- Instrukcje dla użytkowników w trybie online: [Podręcznik użytkownika usługi Azure Information Protection](client-user-guide.md)

- Pobierz Podręcznik użytkownika można dostosowywać: [przewodnika wdrażania użytkownika końcowego platformy Azure Information Protection](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf)

### <a name="update-macros-in-excel-spreadsheets"></a>Aktualizowanie makra w arkusze kalkulacyjne programu Excel

Jeśli masz arkusze kalkulacyjne programu Excel, które zawierają makra, należy edytować makra w następujący sposób, aby upewnić się, że są one nadal działać zgodnie z oczekiwaniami po zainstalowaniu klienta usługi Azure Information Protection:

1. Na początku makra, należy dodać:

        Application.EnableEvents = False

2. Na końcu makra należy dodać:

        Application.EnableEvents = True

Aby uzyskać więcej informacji, zobacz [Application.EnableEvents właściwości (Excel)](https://msdn.microsoft.com/vba/excel-vba/articles/application-enableevents-property-excel).

## <a name="upgrading-and-maintaining-the-azure-information-protection-client"></a>Uaktualnianie i obsługi klienta usługi Azure Information Protection

Zespół usługi Azure Information Protection regularnie aktualizuje klienta usługi Azure Information Protection dla nowych funkcji i poprawek. Anonse są wysyłane do zespołu [witryny usługi Yammer](https://www.yammer.com/AskIPTeam).

Jeśli używasz aktualizacji Windows klienta usługi Azure Information Protection automatycznie uaktualnia ogólnie dostępnej wersji klienta, niezależnie od tego, jak klient został zainstalowany. Nowe wersje klienta są publikowane do wykazu kilka tygodni po wydaniu.

Alternatywnie, można ręcznie uaktualnić klienta, pobierając nowej wersji z [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Następnie należy zainstalować nową wersję, aby uaktualnić klienta. Ta metoda musi być uaktualniania wersji (wersja zapoznawcza).

Podczas ręcznego uaktualniania należy odinstalować poprzednią wersję najpierw tylko wtedy, gdy zmieniasz metody instalacji. Na przykład możesz zmienić z pliku wykonywalnego (.exe) wersję klienta do wersji Windows installer (.msi) klienta. Lub, jeśli musisz zainstalować poprzednią wersję klienta. Na przykład masz bieżącej wersji zapoznawczej zainstalowane do testowania i teraz należy powrócić do bieżącej wersji ogólnie dostępnej.

Użyj [zasady historii i pomoc techniczna wydania wersji](client-version-release-history.md) zasady pomocy technicznej dla klienta usługi Azure Information Protection, które wersje są obecnie obsługiwane i co to jest nowe i zmienione funkcje dla obsługiwanych wersji. 

### <a name="upgrading-the-azure-information-protection-scanner"></a>Uaktualnianie skanera usługi Azure Information Protection

Aby uaktualnić skanera usługi Azure Information Protection, należy zainstalować najnowszą wersję klienta usługi Azure Information Protection. Następnie wykonaj następujące Akcja jednorazowa. Po wykonaniu, nie ma potrzeby ponownego skanowania już skanowanych plików.

- Uruchom [AIPScanner aktualizacji](/powershell/module/azureinformationprotection/Update-AIPScanner) po uaktualnieniu klienta usługi Azure Information Protection. Ustawienia konfiguracji dla repozytoriów i skaner zostaną zachowane. Uruchomienie tego polecenia cmdlet są wymagane do aktualizacji schematu bazy danych dla skanera i jeśli to wymagane, konto usługi skanera ma również przyznane usuwanie uprawnień do bazy danych skanera. 
    
    Uruchom to polecenie cmdlet update, nie można uruchomić skanera i zostanie wyświetlony identyfikator zdarzenia przeważnie **1000** w dzienniku zdarzeń Windows za pomocą następujący komunikat o błędzie: **Nieprawidłowa nazwa obiektu "ScannerStatus"**.

## <a name="uninstalling-the-azure-information-protection-client"></a>Odinstalowywanie klienta usługi Azure Information Protection

Aby odinstalować klienta programu, można użyć dowolnej z następujących opcji:

- Odinstaluj program za pomocą Panelu sterowania: kliknij kolejno pozycje **Microsoft Azure Information Protection** > **Odinstaluj**

- Uruchom ponownie plik wykonywalny (np. **AzInfoProtection.exe**) i na stronie **Modyfikowanie ustawień** kliknij pozycję **Odinstaluj**. 

- Uruchom plik wykonywalny z opcją **/uninstall**. Na przykład: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Kolejne kroki
Aby zainstalować klienta, zobacz [zainstalować klienta usługi Azure Information Protection dla użytkowników](client-admin-guide-install.md).

Jeśli klient został już zainstalowany, zobacz następujące czynności, aby uzyskać dodatkowe informacje, przydatnymi przy obsłudze tego klienta:

- [Dostosowania](client-admin-guide-customizations.md)

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)


