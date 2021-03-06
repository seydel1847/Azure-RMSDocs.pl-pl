---
title: Instalacja zestawu SDK ochrony informacji firmy Microsoft (MIP) i konfiguracji
description: Zawiera wymagania wstępne dotyczące instalacji i konfiguracji, aby można było używać aplikacji utworzonych za pomocą zestawu SDK usługi Microsoft Information Protection.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 01/08/2019
ms.author: bryanla
ms.openlocfilehash: 2f84cfd8a0ae15a66cd624fe591f2891ff549768
ms.sourcegitcommit: adc4621ec4738c0abb6c1fa81a6598a6dfc5ace6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54136239"
---
# <a name="microsoft-information-protection-mip-sdk-setup-and-configuration"></a>Instalacja zestawu SDK ochrony informacji firmy Microsoft (MIP) i konfiguracji 

Przewodnik Szybki Start i samouczków artykułów jest wyśrodkowywana dotyczących tworzenia aplikacji, które używają MIP zestawu SDK, bibliotek i interfejsów API. Ten artykuł pokazuje, jak instalowanie i konfigurowanie subskrypcji usługi Office 365 i stacji roboczej, w ramach przygotowania do przy użyciu zestawu SDK.

Zestaw SDK MIP jest obsługiwane na następujących platformach:  

[!INCLUDE [MIP SDK platform support](../include/mip-sdk-platform-support.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Pamiętaj przed rozpoczęciem pracy, zobacz następujące tematy:

- [Co to jest Centrum zgodności i zabezpieczeń usługi Office 365?](https://docs.microsoft.com/office365/securitycompliance/security-and-compliance)
- [Co to jest usługa Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection)
- [Jak działa ochrona usługi Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

> [!IMPORTANT]
> **Aby chronić prywatność użytkowników, należy poprosić użytkownika o zgodę przed włączeniem automatycznego rejestrowania.** Poniższy przykład jest standardową wiadomość używaną przez firmę Microsoft do powiadamiania o rejestrowaniu:
>
> *Włączając rejestrowanie błędów i wydajności, zgadzasz na wysyłanie do firmy Microsoft informacji o błędach i wydajności. Firma Microsoft będzie automatycznie zbierać dane dotyczące błędów i wydajności w Internecie („Dane”). Firma Microsoft używa tych Danych w celu zapewniania i zwiększania jakości, bezpieczeństwa i integralności swoich produktów i usług. Na przykład analizujemy wydajność i niezawodność, sprawdzając, jakich funkcji używasz, jak szybko funkcje reagują, jaka jest wydajność urządzenia, jakie są interakcje z interfejsem użytkownika oraz jakie problemy wystąpiły podczas pracy z produktem. Dane będą również zawierać informacje o konfiguracji oprogramowania, takie jak aktualnie działające oprogramowanie i adres IP.*

## <a name="sign-up-for-an-office-365-subscription"></a>Zamów subskrypcję usługi Office 365

Wiele przykładowych zestawach SDK wymaga dostępu do subskrypcji usługi Office 365. Jeśli jeszcze nie, należy koniecznie Zarejestruj się w jednym z następujących typów subskrypcji:

| Name (Nazwa) | Zarejestruj się |
|------|---------|
| Usługi Office 365 Enterprise E3 wersji próbnej (30-dniowej bezpłatnej wersji próbnej) | https://go.microsoft.com/fwlink/p/?LinkID=403802 |
| Office 365 Enterprise E3 lub E5 | https://products.office.com/business/office-365-enterprise-e3-business-software |
| Pakiet Enterprise Mobility i zabezpieczeń E3 lub E5 | https://www.microsoft.com/cloud-platform/enterprise-mobility-security |
| Usługa Azure Information Protection Premium P1 lub P2 | https://azure.microsoft.com/pricing/details/information-protection/ |
| Rozwiązania Microsoft 365 E3 i E5, F1 | https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans | 

## <a name="configure-sensitivity-labels"></a>Konfiguruj etykiety ważności

Jeśli obecnie używasz usługi Azure Information Protection, należy przeprowadzić migrację etykiet do Centrum zgodności i zabezpieczeń usługi Office 365. Aby uzyskać więcej informacji na temat procesu, zobacz [jak przeprowadzić migrację etykiety usługi Azure Information Protection do Centrum zgodności i zabezpieczeń usługi Office 365](/azure/information-protection/configure-policy-migrate-labels). 

## <a name="configure-your-client-workstation"></a>Konfigurowanie stacji roboczej użytkownika

Następnie wykonaj poniższe kroki, aby upewnić się, komputer kliencki jest przygotowana i skonfigurowana poprawnie.

1. Jeśli używasz stacji roboczej systemu Windows 10:

   - Za pomocą usługi Windows Update, zaktualizować swojej maszyny, do wersji Windows 10 Fall Creators Update (wersja 1709) lub nowszej. Aby sprawdzić bieżącą wersją:
     - Kliknij ikonę Windows, w lewym dolnym rogu.
     - Wpisz "O Twój komputer" i naciśnij klawisz "Enter".
     - Przewiń w dół do **specyfikacje Windows** i poszukaj w obszarze **wersji**.

   - Upewnij się, że "Tryb dewelopera" jest włączona na stacji roboczej:
     - Kliknij ikonę Windows, w lewym dolnym rogu.
     - Wpisz "Przy użyciu funkcji dla deweloperów" i naciśnij klawisz "Enter", gdy pojawi się **używanie funkcji dla deweloperów** elementu show.
     - Na **ustawienia** okno dialogowe, **dla deweloperów** wybierz kartę, w obszarze "Używanie funkcji dla deweloperów," **tryb dewelopera** opcji.
     - Zamknij **ustawienia** okna dialogowego.

2. Zainstaluj [programu Visual Studio 2017](https://visualstudio.microsoft.com/downloads/)z następującymi pakietami roboczymi i składniki opcjonalne:
   - **Programowanie na platformie Windows uniwersalnej** Windows obciążenie, oraz następującymi opcjonalnymi składnikami:
     - **C++ Universal Windows Platform tools**
     - **Zestaw SDK systemu Windows 10 SDK 10.0.16299.0** lub nowszy, jeśli nie jest domyślnie włączone
   - **Programowanie aplikacji klasycznych w języku C++** Windows obciążenie, oraz następującymi opcjonalnymi składnikami:
     - **Zestaw SDK systemu Windows 10 SDK 10.0.16299.0** lub nowszy, jeśli nie jest domyślnie włączone 

     [![Instalator programu Visual Studio](media/setup-mip-client/visual-studio-install.png)](media/setup-mip-client/visual-studio-install.png#lightbox)

3. Zainstaluj [modułu programu PowerShell ADAL.PS](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2). 

   - Ponieważ aby zainstalować moduły są wymagane uprawnienia administratora, najpierw musisz albo:

     - Zaloguj się do komputera przy użyciu konta z uprawnieniami administratora.
     - Uruchom sesję programu Windows PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator).

   - Następnie uruchom `install-module -name adal.ps` polecenia cmdlet:

     ```powershell
     PS C:\WINDOWS\system32> install-module -name adal.ps

     Untrusted repository
     You are installing the modules from an untrusted repository. If you trust this repository, change its
     InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
     'PSGallery'?
     [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): A

     PS C:\WINDOWS\system32>
     ```

4. Pobierz przykłady zestawu SDK z usługi GitHub 

   - Jeśli nie masz jeszcze, najpierw utwórz [profilu GitHub](https://github.com/join).
   - Zainstaluj najnowszą wersję [narzędziami klienckimi Git Software Freedom Conservancy (Git Bash)](https://git-scm.com/download/)
   - Korzystając z powłoki Git Bash, Pobierz liczba zainteresowania:
     - Użyj następującego zapytania, aby wyświetlić repozytoria: https://github.com/Azure-Samples?utf8=%E2%9C%93&q=MipSdk. 
     - Używanie systemu Git Bash, należy użyć `git clone https://github.com/azure-samples/<repo-name>` do pobierania każdego przykładowego repozytorium.

5. Pobierz zestaw SDK danych binarnych a plikami nagłówka

   Plik zip zawierający nagłówki i plików binarnych zestawu SDK dla wszystkich platform można znaleźć w https://aka.ms/mipsdkbinaries. Plik zip zawiera kilka plików .zip dodatkowe, jeden dla każdej platformy i interfejsu API. Nazwy plików w następujący sposób, gdzie \<interfejsu API\> = `file`, `protection`, lub `upe`, i \<OS\> = platformy: `mip_sdk_<API>_<OS>_1.0.0.0.zip (or .tar.gz)`.

   Na przykład będzie ZIP dla interfejsu API ochrony danych binarnych i nagłówków w systemie Debian: `mip_sdk_protection_debian9_1.0.0.0.tar.gz`.

   Każdy plik zip lub pliku tar zawiera trzy katalogi:

   - **Pojemniki:** Skompilowane pliki binarne dla każdej architektury platformy, jeśli ma to zastosowanie.
   - **Obejmują:** Pliki nagłówków zestawu SDK usługi Microsoft Information Protection
   - **Przykłady:** Kod źródłowy dla przykładowych aplikacji

   Jeśli wykonujesz rozwoju Visual Studio, zestaw SDK można również zainstalować przy użyciu konsoli Menedżera pakietów NuGet:

    ```console
    Install-Package Microsoft.InformationProtection.File
    Install-Package Microsoft.InformationProtection.Policy
    Install-Package Microsoft.InformationProtection.Protection
    ```  
    
6. Ścieżki plików binarnych zestawu SDK (biblioteki dołączanej dynamicznie (dll)), należy dodać do zmiennej środowiskowej PATH. Zmiennej PATH umożliwia zależne biblioteki DLL ma zostać odnaleziona w czasie wykonywania przez aplikacje klienckie:
   - Kliknij ikonę Windows, w lewym dolnym rogu.
   - Wpisz "Path", a następnie naciśnij klawisz "Enter", gdy pojawi się **Edytuj zmienne środowiskowe systemu** elementu show.
   - Na **właściwości systemu** okno dialogowe, kliknij przycisk **zmienne środowiskowe**.
   - Na **zmienne środowiskowe** okno dialogowe, kliknij przycisk **ścieżki** zmiennej wiersz pod **zmienne użytkownika dla \<użytkownika\>**, następnie kliknij przycisk **Edytuj...** .
   - Na **zmiennej środowiskowej edycji** okno dialogowe, kliknij przycisk **New**, co powoduje utworzenie nowego wiersza można edytować. Przy użyciu pełnej ścieżki do poszczególnych `file\bins\debug\amd64`, `protection\bins\debug\amd64`, i `upe\bins\debug\amd64` podkatalogi, Dodaj nowy wiersz dla każdego. Katalog zestawu SDK są przechowywane w `<API>\bins\<target>\<platform>` format, gdzie:
     - \<INTERFEJS API\> = `file`, `protection`, `upe`
     - \<docelowy\> = `debug`, `release`
     - \<Platforma\>  =  `amd64` (alias: x64), `x86`itp.
   
   - Po zakończeniu aktualizowania **ścieżki** zmiennej, kliknij przycisk **OK**. Następnie kliknij przycisk **OK** po zwróceniu do **zmienne środowiskowe** okna dialogowego.

## <a name="register-a-client-application-with-azure-active-directory"></a>Rejestrowanie aplikacji klienta za pomocą usługi Azure Active Directory

W ramach subskrypcji usługi Office 365, w procesie inicjowania obsługi jest tworzony skojarzonych dzierżawę usługi Azure Active Directory (Azure AD). Dzierżawy usługi Azure AD zapewnia zarządzanie tożsamościami i dostępem dla usługi Office 365 *kont użytkowników* i *kont aplikacji*. Aplikacje, które wymagają dostępu do zabezpieczonych interfejsy API (takie jak API MIP), wymagają konta aplikacji.

Dla uwierzytelniania i autoryzacji w czasie wykonywania, kont są reprezentowane przez *podmiotu zabezpieczeń*, który jest tworzony na podstawie informacji o tożsamości dla konta. Podmiotów zabezpieczeń, które reprezentują konta aplikacji są określane jako [ *nazwy głównej usługi*](/azure/active-directory/develop/developer-glossary#service-principal-object). 

Aby zarejestrować konto do aplikacji w usłudze Azure AD do użycia z przewodników Szybki Start i zestawu SDK MIP próbek:

  > [!IMPORTANT] 
  > Aby otworzyć Zarządzanie dzierżawą usługi Azure AD dla tworzenia kont, musisz zalogować się do witryny Azure portal przy użyciu konta użytkownika, który jest elementem członkowskim [roli "Właściciel" w ramach subskrypcji](/azure/billing/billing-add-change-azure-subscription-administrator). W zależności od konfiguracji dzierżawy, konieczne może być członkiem roli katalogu "Globalnego administratora", aby [rejestrowania aplikacji](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps).
  > Zaleca się testowanie za pomocą konta z ograniczeniami. Upewnij się, że konto ma tylko uprawnienia do uzyskania dostępu do wymaganych punktów końcowych SCC. Hasła jako zwykły tekst przekazywane za pośrednictwem wiersza polecenia mogą być zbierane przez systemy rejestrowania.

1. Postępuj zgodnie z instrukcjami w [rejestrowanie aplikacji w usłudze Azure AD, zarejestruj nową aplikację](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad#register-a-new-application-using-the-azure-portal) sekcji. Do celów testowych, użyj następujących wartości dla danej właściwości, zgodnie z rzeczywistym kroków przewodnika: 
    - **Typ aplikacji** — wybierz "Native", jak przedstawiona przez zestaw SDK są aplikacje konsoli natywnie zainstalowanych aplikacji. Natywne aplikacje są traktowane jako "publicznej" klientów przez OAuth2, ponieważ są w stanie użycia magazynu poświadczeń aplikacji w bezpieczny sposób. W odróżnieniu od dla "poufne" aplikacji na serwerze, na przykład aplikacji sieci web, który jest zarejestrowany w jej własnych poświadczeń. 
    - **Identyfikator URI przekierowania** — ponieważ zestaw SDK używa konsoli proste aplikacje klienckie, użyj identyfikatora URI w formacie `<app-name>://authorize`.

2. Po zakończeniu będziesz zostać zwrócona do **zarejestrowana aplikacja** strony dla Twojej nowej rejestracji aplikacji. Skopiuj i Zapisz identyfikator GUID w **identyfikator aplikacji** pola, ponieważ będzie on potrzebny do przewodników Szybki Start. 

3. Następnie kliknij przycisk **ustawienia** można dodać interfejsów API i uprawnień, do których klient będzie potrzebował dostępu. Na **ustawienia** kliknij **wymagane uprawnienia**.

4. Teraz dodasz MIP interfejsów API i uprawnienia, które aplikacja będzie wymagać w czasie wykonywania:
   - Na **wymagane uprawnienia** kliknij **Dodaj**. 
   - Na **dostępu Dodaj interfejs API** kliknij **wybierz interfejs API**.
   - Na **wybierz interfejs API** stronie, kliknij przycisk "**usługi Microsoft Rights Management**" interfejsu API, a następnie kliknij przycisk **wybierz**.
   - Na **Włącz dostęp za pomocą** stronie uprawnienia dostępne w interfejsie API, kliknij przycisk "**tworzenie i dostęp do chronionej zawartości dla użytkowników**" i kliknij przycisk **wybierz**, następnie  **Gotowe**.

5. Powtórz krok #4, ale tym razem, gdy można uzyskać dostęp do **wybierz interfejs API** strony, należy wyszukać interfejsu API.
   - Na **wybierz interfejs API** strony, w polu wyszukiwania wpisz "**usługi synchronizacji do ochrony informacji firmy Microsoft**", a następnie kliknij polecenie interfejsu API i kliknij przycisk **wybierz**.
   - Na **Włącz dostęp za pomocą** stronie uprawnienia dostępne w interfejsie API, kliknij przycisk "**odczytu wszystkich ujednoliconego zasad użytkownik ma dostęp do**" i kliknij przycisk **wybierz**, następnie  **Gotowe**

6. Wstecz w czasie **wymagane uprawnienia** kliknij **Udziel uprawnień**, następnie **tak**. Ten krok umożliwia wstępne zgody do aplikacji przy użyciu tej rejestracji dostęp do interfejsów API w ramach określonych uprawnień. Jeśli zalogowano się jako administrator globalny zgody jest rejestrowane dla wszystkich użytkowników w dzierżawie, działających aplikacji; w przeciwnym razie dotyczy tylko z Twoim kontem użytkownika. 

Po zakończeniu rejestracji aplikacji i uprawnienia do interfejsu API powinien wyglądać podobnie do poniższego przykładu:

   [![Rejestracja aplikacji w usłudze Azure AD](media/setup-mip-client/aad-app-registration.png)](media/setup-mip-client/aad-app-registration.png#lightbox)


Aby uzyskać więcej informacji na temat dodawania interfejsów API i uprawnienia do rejestracji, zobacz [aktualizowanie aplikacji w usłudze Azure AD Konfigurowanie aplikacji klienckiej dostęp do interfejsów API sieci web](/azure/active-directory/develop/quickstart-v1-update-azure-ad-app#configure-a-client-application-to-access-web-apis). Tutaj znajdziesz informacje na temat dodawania interfejsów API i uprawnienia wymagane przez aplikację kliencką.  

## <a name="request-an-information-protection-integration-agreement-ipia"></a>Żądanie Umowy integracyjnej usługi Information Protection (IPIA, Information Protection Integration Agreement)

Przed wydaniem aplikacji utworzonych za pomocą MIP, możesz poprosić o i wykonać formalną umowę z firmą Microsoft.

1. Uzyskaj umowę IPIA, wysyłając na adres [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=Requesting%20IPIA%20for%20<company-name>) wiadomość e-mail z następującymi informacjami:

   **Temat:** Żądanie umowy IPIA dla *nazwa firmy*

   W treści wiadomości e-mail umieść następujące dane:
   - Nazwa aplikacji i produktu
   - Imię i nazwisko osoby żądającej
   - Adres e-mail osoby żądającej

2. Po otrzymaniu żądania umowy IPIA wyślemy formularz (jako dokument programu Word). Zapoznaj się z warunkami i postanowieniami umowy IPIA i wróć do formularza [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=IPIA%20Response%20for%20<company-name>) w celu podania następujących informacji:

   - Prawna nazwa firmy
   - Stan/prowincja (USA/Kanada) lub kraj siedziby
   - Adres URL firmy
   - Adres e-mail osoby upoważnionej do kontaktu
   - Dodatkowe adresy firmy (opcjonalnie)
   - Nazwa aplikacji firmy
   - Krótki opis aplikacji
   - *Identyfikator dzierżawy Azure*
   - *Identyfikator aplikacji* dla aplikacji
   - Dane kontaktowe, adres e-mail i telefon do firmy do korespondencji w sytuacjach krytycznych

3. Po otrzymaniu formularza wyślemy Ci link do ostatecznej postaci umowy IPIA, którą należy cyfrowo podpisać. Następnie zostanie ona podpisana przez przedstawiciela firmy Microsoft, co spowoduje zawarcie umowy.

### <a name="already-have-a-signed-ipia"></a>Masz już podpisaną umowę IPIA?

Jeśli masz już podpisaną umowę IPIA i chcesz dodać nowy *Identyfikator aplikacji* dla aplikacji, którą chcesz wydać, wyślij wiadomość e-mail na adres [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=Updating%20IPIA%20for%20<company-name>) i przekaż nam następujące informacje:

- Nazwa aplikacji firmy
- Krótki opis aplikacji
- Identyfikator dzierżawy Azure (nawet jeśli jest taki sam, jak poprzednio)
- Identyfikator aplikacji dla aplikacji
- Dane kontaktowe, adres e-mail i telefon do firmy do korespondencji w sytuacjach krytycznych

Po wysłaniu wiadomości e-mail odczekaj do 72 godzin na potwierdzenie przez nas odbioru.

## <a name="next-steps"></a>Następne kroki

- Przed rozpoczęciem sekcji przewodników Szybki Start, upewnij się dowiedzieć się o [obserwatorów w zestawie SDK MIP](concept-async-observers.md), zgodnie z zestawu SDK MIP została zaprojektowana jako prawie całkowicie asynchronicznego.
- Jeśli zechcesz Zdobądź praktyczne doświadczenie z zestawem SDK, skorzystaj z [Szybki Start: Inicjowanie aplikacji klienta (C++)](quick-app-initialization-cpp.md).


