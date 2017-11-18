---
title: "Podręcznik administratora klienta usługi Azure Information Protection"
description: "Instrukcje i informacje dla administratorów sieci przedsiębiorstwa odpowiedzialnych za wdrażanie klienta usługi Azure Information Protection dla systemu Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/17/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 33a5982f-7125-4031-92c2-05daf760ced1
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: b77ee56fdee5f26797a2ea6ff2b40dd22633516b
ms.sourcegitcommit: 0ef66a8479b4105c00bf1b1df46d2ddf044b7670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="azure-information-protection-client-administrator-guide"></a>Podręcznik administratora klienta usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Informacje zawarte w tym przewodniku są przydatne dla osób odpowiedzialnych za klienta usługi Azure Information Protection w sieci przedsiębiorstwa lub chcącym uzyskać więcej informacji technicznych, niż jest dostępnych w [podręczniku użytkownika klienta usługi Azure Information Protection](client-user-guide.md). 

Na przykład:

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

- Dodatek pakietu Office, instalujący pasek usługi Azure Information Protection, użytkownicy mogą wybierać etykiety klasyfikacji i **Chroń** na Wstążce, aby wyświetlić dodatkowe opcje. Dla programu Outlook **nie przesyłaj dalej** przycisku jest także dodawane do wstążki.

- Opcje dostępne po kliknięciu prawym przyciskiem myszy w oknie Eksploratora plików Windows, które pozwalają użytkownikom stosować etykiety klasyfikacji i ochronę plików.

- Przeglądarka do wyświetlania chronionych plików, gdy natywna aplikacja nie może ich otworzyć.

- Moduł środowiska PowerShell pozwalający dodawać i usuwać etykiety klasyfikacji oraz włączać i wyłączać ochronę plików. 
    
    Ten moduł zawiera polecenia cmdlet, aby zainstalować i skonfigurować [skanera usługi Azure Information Protection](../deploy-use/deploy-aip-scanner.md) (obecnie w wersji zapoznawczej) który działa jako usługa w systemie Windows Server. Ta usługa pozwala odnajdywania, klasyfikowania i chronić pliki na magazyny danych, takich jak udziały sieciowe i biblioteki programu SharePoint Server.

- Klient usługi Rights Management komunikujący się z usługą Azure Rights Management (Azure RMS) lub usługami Active Directory Rights Management (AD RMS).

Klient usługi Azure Information Protection najlepiej nadaje się do pracy z usługami Azure — usługą Azure Information Protection i jej usługami ochrony danych, Azure Rights Management. Jednak z pewnymi ograniczeniami klient usługi Azure Information Protection działa też z lokalną wersją usług Rights Management — AD RMS. Obszerne porównanie funkcji obsługiwanych przez usługi Azure Information Protection i AD RMS można znaleźć w artykule [Porównanie usług Azure Information Protection i AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). 

Jeśli korzystasz z usług AD RMS i chcesz przeprowadzić migrację do usługi Azure Information Protection, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Czy należy wdrożyć klienta usługi Azure Information Protection?

Dokonaj wdrożenia klienta usługi Azure Information Protection w następujących przypadkach:

- Chcesz klasyfikować (i ewentualnie chronić) dokumenty i wiadomości e-mail, wybierając etykiety w aplikacjach pakietu Office (Word, Excel, PowerPoint, Outlook).

- Chcesz klasyfikować (i ewentualnie chronić) dokumenty i wiadomości e-mail za pomocą Eksploratora plików, który obsługuje dodatkowe typy plików, wybór wielokrotny i foldery.

- Chcesz uruchamiać skrypty, które klasyfikują (i ewentualnie chronią) dokumenty za pomocą poleceń środowiska PowerShell.

- Chcesz uruchomić usługa, która umożliwia odnalezienie, klasyfikuje (i opcjonalnie chroni) plików, które są przechowywane w firmie. Ta usługa skanera jest obecnie w wersji zapoznawczej.

- Chcesz wyświetlać chronione dokumenty, gdy natywna aplikacja wyświetlająca je nie jest zainstalowana lub nie może otworzyć tych dokumentów.

- Chcesz po prostu chronić pliki za pomocą Eksploratora plików lub poleceń środowiska Powershell.

- Chcesz umożliwić użytkownikom i administratorom śledzenie i odwoływanie chronionych dokumentów.

- Chcesz usuwać szyfrowanie z plików i kontenerów (wyłączać ochronę) w trybie zbiorczym na potrzeby odzyskiwania danych.

- Korzystasz z pakietu Office 2010 i chcesz chronić dokumenty i wiadomości e-mail za pomocą usługi Azure Rights Management.

Przykład przedstawiający klienta Azure Information Protection dodatku dla aplikacji pakietu Office, Wyświetlanie etykiety klasyfikacji dla Twojej organizacji i nowych **Chroń** na Wstążce:

![Pasek usługi Azure Information Protection z zasadami domyślnymi](../media/word2016-calloutsv2.png)

## <a name="installing-and-supporting-the-azure-information-protection-client"></a>Instalowanie i obsługa klienta Azure Information Protection

Klienta usługi Azure Information Protection można zainstalować za pomocą usługi Windows Update, plik wykonywalny lub plik Instalatora Windows. Aby uzyskać więcej informacji o poszczególnych opcjach wyboru i instrukcje, zobacz [instalowania klienta usługi Azure Information Protection dla użytkowników](client-admin-guide-install.md).  

Użyj poniższych sekcji, aby uzyskać dodatkowe informacje o instalowaniu klienta. 

### <a name="installation-checks-and-troubleshooting"></a>Kontroli instalacji i rozwiązywanie problemów

Gdy klient jest zainstalowany, użyj **Pomoc i opinie** opcję, aby otworzyć **Microsoft Azure Information Protection** okno dialogowe:

- W aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** wybierz kolejno opcje **Chroń**, a następnie **Pomoc i opinie**.

- Korzystając z Eksploratora plików, zaznacz plik, pliki lub folder, kliknij je prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**, a następnie wybierz opcję **Pomoc i opinie**. 

#### <a name="help-and-feedback-section"></a>Sekcja **Pomoc i opinie**

Link **Powiedz mi więcej** domyślnie prowadzi do witryny internetowej usługi [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection), ale można go skonfigurować dla niestandardowego adresu URL jako jedno z [ustawień zasad](../deploy-use/configure-policy-settings.md) w zasadach usługi Azure Information Protection.

Użyj linku **Wyślij opinię**, aby wysłać propozycje lub prośby do zespołu usługi Information Protection. Nie należy używać tej opcji w celu uzyskania pomocy technicznej. W takim przypadku należy zapoznać się z artykułem [Opcje pomocy technicznej i zasoby społecznościowe](../get-started/information-support.md#support-options-and-community-resources). 

Funkcja **Wyeksportuj dzienniki** umożliwia automatyczne zebranie i dołączenie plików dziennika klienta usługi Azure Information Protection w przypadku wyświetlenia prośby o ich przesłanie zespołowi pomocy technicznej firmy Microsoft. Ta opcja umożliwia także wysyłanie plików dziennika zespołowi pomocy technicznej przez użytkowników końcowych.

**Resetowanie ustawień** wylogowaniu się użytkownika, usuwa obecnie pobranych zasady usługi Azure Information Protection i resetuje ustawienia użytkownika dla usługi Azure Rights Management.

##### <a name="more-information-about-the-reset-settings-option"></a>Więcej informacji na temat opcji Resetowanie ustawień

- Nie trzeba być administratorem lokalnym, aby używać tej opcji, a ta akcja nie jest rejestrowana w Podglądzie zdarzeń. 

- O ile pliki nie zostały zablokowane, ta akcja spowoduje usunięcie wszystkich plików w poniższych lokalizacjach. Te pliki obejmują certyfikaty klienta, szablony usługi Rights Management, zasady usługi Azure Information Protection i buforowane poświadczenia użytkowników. Pliki dzienników klienta nie są usuwane.
    
    - %LocalAppData%\Microsoft\DRM
    
    - %LocalAppData%\Microsoft\MSIPC
    
    - %LocalAppData%\Microsoft\MSIP\Policy.msip
    
    - %LocalAppData%\Microsoft\MSIP\TokenCache

- Następujące ustawienia i klucze rejestru zostaną usunięte. Jeśli ustawienia dla każdej z tych kluczy rejestru wartości niestandardowych, te należy ponownie skonfigurować po zresetowaniu klienta. 
    
    Zwykle sieciach firmowych, te ustawienia są skonfigurowane za pomocą zasad grupy, w którym to przypadku one są automatycznie ponownie po odświeżeniu zasad grupy na komputerze. Jednak może być niektórych ustawień, które są skonfigurowane jednorazowo przy użyciu skryptu, lub skonfigurować ręcznie. W takich sytuacjach należy wykonać dodatkowe kroki, aby ponownie skonfigurować te ustawienia. Na przykład komputerów może uruchomić skrypt jednorazowo można skonfigurować ustawienia dla przekierowanie do usługi Azure Information Protection, ponieważ jest przeprowadzana migracja z usług AD RMS i nadal ma punkt połączenia usługi w sieci. Po przywróceniu klienta, komputer musi ponownie uruchom ten skrypt.
    
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

Klient usługi Azure Information Protection obsługuje te same języki, które obsługuje usługi Office 365. Aby uzyskać listę tych języków, zobacz **usługi Office 365, Exchange Online Protection i usługi Power BI** sekcji z [dostępność międzynarodowa](https://products.office.com/business/international-availability) strony z pakietu Office.

Te języki, opcje menu, okna dialogowe i komunikaty z usługi Azure Information Protection klienta są wyświetlane w języku użytkownika. Brak jednego Instalator, który wykryje języka aby dodatkowa konfiguracja nie jest niezbędne do zainstalowania klienta usługi Azure Information Protection dla różnych języków. 

Etykieta nazwy i opisy, które określisz nie są automatycznie translacji podczas konfigurowania etykiet w zasadach usługi Azure Information Protection. Począwszy od 30 sierpnia 2017 bieżącego [domyślne zasady](../deploy-use/configure-policy-default.md) oferuje obsługę w przypadku niektórych języków. Dla użytkowników zobaczyć etykiet w ich preferowany język Podaj własne tłumaczenia i skonfigurować zasady usługi Azure Information Protection, które mają być używane te tłumaczenia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiet w różnych językach dla usługi Azure Information Protection](../deploy-use/configure-policy-languages.md). Oznaczenia wizualne nie są tłumaczone i nie obsługuje więcej niż jednym języku.

## <a name="uninstalling-the-azure-information-protection-client"></a>Odinstalowywanie klienta usługi Azure Information Protection

Do odinstalowania klienta, można użyć dowolnej z następujących opcji:

- Odinstaluj program za pomocą Panelu sterowania: kliknij kolejno pozycje **Microsoft Azure Information Protection** > **Odinstaluj**

- Uruchom ponownie plik wykonywalny (np. **AzInfoProtection.exe**) i na stronie **Modyfikowanie ustawień** kliknij pozycję **Odinstaluj**. 

- Uruchom plik wykonywalny z opcją **/uninstall**. Na przykład: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Następne kroki
Aby zainstalować klienta, zobacz [instalowania klienta usługi Azure Information Protection dla użytkowników](client-admin-guide-install.md).

Jeśli klient został już zainstalowany, zobacz następujące dodatkowe informacje potrzebne do obsługi tego klienta:

- [Dostosowania](client-admin-guide-customizations.md)

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
