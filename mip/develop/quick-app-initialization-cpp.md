---
title: Przewodnik Szybki Start — inicjowanie dla klientów ochrony informacji firmy Microsoft (MIP) zestawu SDK C++
description: Przewodnik Szybki Start omawiający pisania logiki inicjowania dla klienta ochrony informacji firmy Microsoft (MIP) zestawu SDK aplikacji.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 9405f98ea2b1be79a4de8b487b407fbebc8fe923
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214458"
---
# <a name="quickstart-client-application-initialization-c"></a>Szybki Start: Inicjowanie aplikacji klienta (C++)

Ten przewodnik Szybki Start opisano, jak zaimplementować wzorzec inicjowanie klienta, używany przez zestaw SDK języka C++ MIP w czasie wykonywania. 

> [!NOTE]
> Kroki opisane w tym przewodniku Szybki Start są wymagane dla dowolnej aplikacji klienckiej, która używa pliku MIP, zasad lub interfejsów API ochrony. Chociaż ten przewodnik Szybki Start pokazuje sposób użycia interfejsów API plików, ten sam wzorzec ma zastosowanie do klientów za pomocą zasad i interfejsów API ochrony. Przewodniki Szybki Start w przyszłości powinno się odbywać pojedynczo, zgodnie z każdej z nich jest oparta na poprzedni, z tym kontem jest pierwszy.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli jeszcze nie, należy koniecznie:

- Wykonaj kroki [SDK ochronę informacji firmy Microsoft (MIP), instalacja i Konfiguracja](setup-configure-mip.md). Ten przewodnik Szybki Start, zależy od prawidłowego zestawu SDK instalacji i konfiguracji.
- Opcjonalnie:
  - Przegląd [obiektów profilu i aparat](concept-profile-engine-cpp.md). Obiekty profilu i aparat są uniwersalne koncepcji, wymagane przez klientów, którzy używają interfejsów API MIP, plik/zasady/ochrony. 
  - Przegląd [pojęć dotyczących uwierzytelniania](concept-authentication-cpp.md) Aby dowiedzieć się, jak uwierzytelnianie i zgody są implementowane przez aplikację zestawu SDK i klienta.
  - Przegląd [pojęcia obserwatora](concept-async-observers.md) dowiedzieć się więcej o obserwatorów i sposobu ich implementacji. Zestaw SDK MIP sprawia, że użycie wzorca obserwatora w celu wdrożenia powiadomienia o zdarzeniach asynchronicznych.

## <a name="create-a-visual-studio-solution-and-project"></a>Tworzenie projektu i rozwiązania Visual Studio

Najpierw utworzymy i skonfigurować początkowe rozwiązania Visual Studio i projekt, na którym zostanie skompilowany Szybki Start. 

1. Otwórz program Visual Studio 2017, wybierz opcję **pliku** menu **New**, **projektu**. W **nowy projekt** okno dialogowe:
     - W okienku po lewej stronie w obszarze **zainstalowane**, **inne języki**, wybierz opcję **Visual C++**.
     - W środkowym okienku wybierz **Windows aplikacji konsoli**
     - W dolnym okienku zaktualizować projekt **nazwa**, **lokalizacji**i zawierający **Nazwa rozwiązania** odpowiednio.
     - Po zakończeniu kliknij przycisk **OK** przycisk w prawym dolnym rogu.

     [![Tworzenie rozwiązania w usłudze Visual Studio](media/quick-app-initialization-cpp/create-vs-solution.png)](media/quick-app-initialization-cpp/create-vs-solution.png#lightbox)


2. Skonfiguruj ustawienia projektu:
   - W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu (bezpośrednio pod węzłem top/rozwiązania) i wybierz **właściwości**. 
   - Na górze/po prawej stronie **stron właściwości** okno dialogowe, kliknij przycisk **programu Configuration Manager...** . Na **programu Configuration Manager** okna dialogowego, ustaw konfigurację"aktywne rozwiązanie" **debugowania**i docelowej "platforma rozwiązania aktywnego" do **x64**. Kliknij przycisk **Zamknij** po zakończeniu.
   - W obszarze **właściwości konfiguracji**, wybierz opcję **katalogi VC ++** węzła.
   - Wybierz **Dołącz katalogi** wiersza, a następnie kliknij listę rozwijaną po prawej stronie, a następnie **< Edytuj >**, a następnie wprowadź ścieżki do zestawu SDK obejmują podkatalogów (.h) w polu najważniejsze. Określ pełnej ścieżki do `file\include`, `protection\include`, `upe\include` podkatalogów (ale nie lepszy), w ramach ścieżki, w którym zainstalowano zestaw SDK. Kliknij przycisk **OK**. 

        [![Tworzenie rozwiązania w usłudze Visual Studio](media/quick-app-initialization-cpp/set-include-lib-path-properties.png)](media/quick-app-initialization-cpp/set-include-lib-path-properties.png#lightbox)

   - Powtórz poprzedni krok dla **katalogi bibliotek** wiersza, wprowadzając ścieżki do podkatalogów binarne biblioteki statycznej (lib) zestawu SDK. Należy użyć ścieżek, które pasuje do bieżącej konfiguracji kompilacji dla rozwiązania. W tym przewodniku Szybki Start, określ bezwzględny lub względny ścieżki do `file\bins\debug\amd64`, `protection\bins\debug\amd64`, `upe\bins\debug\amd64` podkatalogów.

   - W obszarze **właściwości konfiguracji**, otwórz **konsolidatora** , a następnie wybierz węzeł **dane wejściowe** węzła. 
   - Wybierz **dodatkowe zależności** wiersza, a następnie kliknij listę rozwijaną po prawej stronie, a następnie **< Edytuj >**. W tym miejscu możesz dodać nazwy bibliotek statycznych zestawu SDK. Dodaj `mip_protection_sdk.lib;mip_file_sdk.lib;mip_upe_sdk.lib;` do listy bibliotek w górnym pola. Kliknij przycisk **OK**. 
   - Kliknij przycisk **OK** na **stron właściwości** okno dialogowe po zakończeniu.

     [![Tworzenie rozwiązania w usłudze Visual Studio](media/quick-app-initialization-cpp/set-static-libs.png)](media/quick-app-initialization-cpp/set-static-libs.png#lightbox)

## <a name="implement-an-observer-class"></a>Implementowanie klasy obserwatora

Teraz Utwórz podstawową implementację klasy obserwatora, rozszerzając zestawu SDK `mip::FileProfile::Observer` klasy. Obserwator jest tworzone i używane później, plik profilu i obiektów aparatu plików.

1. Dodaj nową klasę do projektu, który generuje pliki zarówno nagłówek/h, jak i implementację/.cpp:

   - W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu ponownie, wybierz **Dodaj**, a następnie wybierz **klasy**.
   - Na **Dodaj klasę** okno dialogowe:
     - W **Nazwa klasy** wprowadź "profile_observer". Należy zauważyć, że zarówno **plik .h klasy** i **plik .cpp** pola są wypełniane automatycznie, na podstawie nazwy.
     - Po zakończeniu kliknij przycisk **OK** przycisku.

     [![Program Visual Studio Dodaj klasę](media/quick-app-initialization-cpp/add-class.png)](media/quick-app-initialization-cpp/add-class.png#lightbox)

2. Po wygenerowaniu pliki .h i .cpp dla klasy, oba pliki są otwarte w edytorze grupy kart. Teraz zaktualizować każdego pliku, aby zaimplementować nowej klasie obserwatora:

   - Zaktualizuj "profile_observer.h", usuwając zaznaczenie/wygenerowany `profile_observer` klasy. **Nie** Usuń dyrektywy preprocesora, generowane przez poprzedniego kroku (#pragma, #include). Następnie skopiuj/Wklej następujące źródło do pliku, po wszelkie istniejące dyrektywy preprocesora:

     ```cpp
     #include <memory>
     #include "mip/file/file_profile.h"

     class ProfileObserver final : public mip::FileProfile::Observer {
     public:
          ProfileObserver() { }
          void OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context) override;
          void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
          void OnAddEngineSuccess(const std::shared_ptr<mip::FileEngine>& engine, const std::shared_ptr<void>& context) override;
          void OnAddEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
     };
     ```

   - Zaktualizuj "profile_observer.cpp", usuwając zaznaczenie/wygenerowany `profile_observer` Implementacja klasy. **Nie** Usuń dyrektywy preprocesora, generowane przez poprzedniego kroku (#pragma, #include). Następnie skopiuj/Wklej następujące źródło do pliku, po wszelkie istniejące dyrektywy preprocesora:

     ```cpp
     #include <future>

     using std::promise;
     using std::shared_ptr;
     using std::static_pointer_cast;
     using mip::FileEngine;
     using mip::FileProfile;

     void ProfileObserver::OnLoadSuccess(const shared_ptr<FileProfile>& profile, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileProfile>>>(context);
          promise->set_value(profile);
     }

     void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileProfile>>>(context);
          promise->set_exception(error);
     }

     void ProfileObserver::OnAddEngineSuccess(const shared_ptr<FileEngine>& engine, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileEngine>>>(context);
          promise->set_value(engine);
     }

     void ProfileObserver::OnAddEngineFailure(const std::exception_ptr& error, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileEngine>>>(context);
          promise->set_exception(error);
     }
     ```

3. Opcjonalnie użyj F6 (**Kompiluj rozwiązanie**) próba uruchomienia testu kompilacji/łącze rozwiązania, aby upewnić się, że pomyślnie skompilowana przed kontynuowaniem.

## <a name="implement-an-authentication-delegate"></a>Implementowanie delegata uwierzytelniania

Zestaw SDK MIP implementuje uwierzytelniania za pomocą funkcji rozszerzalności klasy, która udostępnia mechanizm do udostępniania pracy uwierzytelniania za pomocą aplikacji klienckiej. Klient musi uzyskać odpowiedni dostęp OAuth2 tokenu pod warunkiem do zestawu SDK MIP w czasie wykonywania. 

Teraz Utwórz implementację dla delegata uwierzytelniania, rozszerzając zestawu SDK `mip::AuthDelegate` klasy i zastępowanie/wdrażanie `mip::AuthDelegate::AcquireOAuth2Token()` czystą funkcję wirtualną. Delegowanie uwierzytelniania jest tworzone i używane później, plik profilu i obiektów aparatu plików.

1. Za pomocą tego samego programu Visual Studio "Dodaj klasę" funkcji używanych w kroku #1 w poprzedniej sekcji, Dodaj klasę do projektu. W tej chwili wprowadź "auth_delegate" **Nazwa klasy** pola. 

2. Teraz zaktualizować każdy plik, aby zaimplementować nowej klasie delegata uwierzytelniania:

   - Zaktualizuj "auth_delegate.h", zastępując wszystkie wygenerowany `auth_delegate` klasy kodu za pomocą następujących źródła. **Nie** Usuń dyrektywy preprocesora, generowane przez poprzedniego kroku (#pragma, #include):

     ```cpp
     #include <string>
     #include "mip/common_types.h"

     class AuthDelegateImpl final : public mip::AuthDelegate {
     public:
          AuthDelegateImpl() = delete;        // Prevents default constructor
          
          AuthDelegateImpl(
            const std::string& appId)         // AppID for registered AAD app
            : mAppId(appId) {};

          bool AcquireOAuth2Token(            // Called by MIP SDK to get a token
            const mip::Identity& identity,    // Identity of the account to be authenticated, if known
            const OAuth2Challenge& challenge, // Authority (AAD tenant issuing token), and resource (API being accessed; "aud" claim).
            OAuth2Token& token) override;     // Token handed back to MIP SDK
     private:
          std::string mAppId;
     };
     ```

   - Zaktualizuj "auth_delegate.cpp", zastępując wszystkie wygenerowany `auth_delegate` Implementacja klasy przy użyciu następujących źródła. **Nie** Usuń dyrektywy preprocesora, generowane przez poprzedniego kroku (#pragma, #include). 

     > [!IMPORTANT]
     > Poniższy kod tokenu jest celowo niekompletne. Firma Microsoft przetestuje później przy użyciu tokenu dostępu statyczne.  
     > W środowisku produkcyjnym, musi to zostać zastąpione przez kod, który dynamicznie wyświetli monit o uwierzytelnienie i uzyskuje token, za pomocą:
     > - appId i odpowiedzi/redirect URI określone w rejestracji aplikacji usługi Azure AD (odpowiedzi/identyfikator URI przekierowania **musi** odpowiadać Twojej rejestracji aplikacji)
     > - Urząd i identyfikator URI zasobu przekazywane przez zestaw SDK w `challenge` argumentu (identyfikator URI zasobu **musi** dopasowania uprawnień interfejsu API rejestracji aplikacji)
     > - poświadczenia aplikacji/użytkownika ("natywnego" klienci OAuth2 powinien monit o podanie poświadczeń użytkownika i korzystać z tego przepływu "Kod autoryzacji". OAuth2 "poufne klienci" można użyć własnych, bezpiecznych poświadczeń z usługą flow "poświadczeń klienta" (na przykład usługi) lub monit o podanie poświadczeń użytkownika przy użyciu usługi flow "Kod autoryzacji" (np. aplikacji sieci web)).
     >
     > Uzyskanie tokenu protokołu OAuth2 jest protokołem złożone i zazwyczaj są realizowane za pomocą biblioteki. Jest TokenAcquireOAuth2Token() **tylko** wywoływane przez zestaw SDK MIP, zgodnie z potrzebami.

     ```cpp
     using std::string;

     bool AuthDelegateImpl::AcquireOAuth2Token(const mip::Identity& identity, const OAuth2Challenge& challenge, OAuth2Token& token) 
     {
            // TODO: replace with token acquisition code
            const string authority = challenge.GetAuthority();
            const string resourceURI = challenge.GetResource();
            string accessToken = "<access-token>";

            // Pass access token back to MIP SDK
            token.SetAccessToken(accessToken);

          // True = successful token acquisition; False = failure
          return true;
     }
     ``` 
3. Opcjonalnie użyj F6 (**Kompiluj rozwiązanie**) próba uruchomienia testu kompilacji/łącze rozwiązania, aby upewnić się, że pomyślnie skompilowana przed kontynuowaniem.

## <a name="implement-a-consent-delegate"></a>Implementowanie delegata zgody

Usługa Azure AD wymaga aplikacja otrzyma zgody, zanim uzyskają dostęp do zabezpieczonych zasobów przy użyciu tożsamości konta usługi. Zgody jest rejestrowana jako trwałe potwierdzenie uprawnień w dzierżawie konta, w ramach danego konta (zgoda użytkownika) lub wszystkich kont (zgoda administratora) dla aplikacji dostępu do żądanego zasobu interfejsu API/uprawnienia. Zgoda odbywa się w różnych scenariuszach, na podstawie interfejsu API i poziom uprawnień, które dąży aplikacji, a konto używane do logowania i tokenu nabycia: 

- konta z *tej samej dzierżawie* gdy Twoja aplikacja będzie zarejestrowana, jeśli użytkownika lub administratora nie została jawnie wstępnie zgody dostęp za pośrednictwem funkcji "Udziel uprawnień".
- konta z *innej dzierżawy* Jeśli Twoja aplikacja będzie zarejestrowana jako wielodostępne, a administrator dzierżawy nie zostało wstępnie wyraził zgodę dla wszystkich użytkowników z wyprzedzeniem.

Teraz tworzenie implementację dla delegata zgody, rozszerzając zestawu SDK `mip::ConsentDelegate` klasy i zastępowanie/wdrażanie `mip::AuthDelegate::GetUserConsent()` czystą funkcję wirtualną. Zgody delegatowi jest tworzone i używane później, plik profilu i obiektów aparatu plików.

1. Przy użyciu tej samej funkcji "Dodaj klasę" Visual Studio używaliśmy wcześniej, Dodaj klasę do projektu. W tej chwili wprowadź "consent_delegate" **Nazwa klasy** pola. 

2. Teraz zaktualizować każdy plik, aby zaimplementować nowej klasie delegata zgody:

   - Zaktualizuj "consent_delegate.h", zastępując wszystkie wygenerowany `consent_delegate` klasy kodu za pomocą następujących źródła. **Nie** Usuń dyrektywy preprocesora, generowane przez poprzedniego kroku (#pragma, #include):

     ```cpp
     #include "mip/common_types.h"
     #include <string>

     class ConsentDelegateImpl final : public mip::ConsentDelegate {
     public:
          ConsentDelegateImpl() = default;
          virtual mip::Consent GetUserConsent(const std::string& url) override;
     };
     ```

   - Zaktualizuj "consent_delegate.cpp", zastępując wszystkie wygenerowany `consent_delegate` Implementacja klasy przy użyciu następujących źródła. **Nie** Usuń dyrektywy preprocesora, generowane przez poprzedniego kroku (#pragma, #include). 

     ```cpp
     #include <iostream>
     using mip::Consent;
     using std::string;

     Consent ConsentDelegateImpl::GetUserConsent(const string& url) 
     {
          // Accept the consent to connect to the url
          std::cout << "SDK will connect to: " << url << std::endl;
          return Consent::AcceptAlways;
     }
     ``` 
3. Opcjonalnie użyj F6 (**Kompiluj rozwiązanie**) próba uruchomienia testu kompilacji/łącze rozwiązania, aby upewnić się, że pomyślnie skompilowana przed kontynuowaniem.

## <a name="construct-a-file-profile-and-engine"></a>Utworzyć plik profilu i aparatu

Jak wspomniano wcześniej, obiekt profilu i aparat są wymagane dla klientów z zestawu SDK przy użyciu interfejsów API MIP. Wykonaj kodowania części tego przewodnika Szybki Start, dodając kod do tworzenia wystąpień obiektów aparatu i profilu: 

1. Z **Eksploratora rozwiązań**, otwórz plik .cpp w projekcie, który zawiera implementację `main()` metody. Domyślnie taką samą nazwę jak projekt zawierający go, co zostało określone podczas tworzenia projektu.

2. Usuń wygenerowane implementacji `main()`. **Nie** Usuń dyrektywy preprocesora, generowane przez program Visual Studio podczas tworzenia projektu (#pragma, #include). Po dowolnej dyrektywy preprocesora, Dołącz następujący kod:

   ```cpp
   #include "auth_delegate.h"
   #include "consent_delegate.h"
   #include "profile_observer.h"

   using std::promise;
   using std::future;
   using std::make_shared;
   using std::shared_ptr;
   using std::string;
   using std::cout;
   using mip::ApplicationInfo; 
   using mip::FileProfile;
   using mip::FileEngine;

   int main()
   {
     // Construct/initialize objects used by the application's profile object
     ApplicationInfo appInfo{"0edbblll-8773-44de-b87c-b8c6276d41eb",    // ApplicationInfo object (App ID, friendly name)
                 "AppInitialization Quickstart" };
     auto profileObserver = make_shared<ProfileObserver>();         // Observer object                  
     auto authDelegateImpl = make_shared<AuthDelegateImpl>(         // Authentication delegate object (App ID)
                 "0edbblll-8773-44de-b87c-b8c6276d41eb");
     auto consentDelegateImpl = make_shared<ConsentDelegateImpl>(); // Consent delegate object
 
     // Construct/initialize profile object
     FileProfile::Settings profileSettings("",      // Path for logging/telemetry/state; blank = C:
       true,                                        // true = use in-memory state storage (vs disk)
       authDelegateImpl,                            
       consentDelegateImpl,                     
       profileObserver,                         
       appInfo);                                    

     // Set up promise/future connection for async profile operations; load profile asynchronously
     auto profilePromise = make_shared<promise<shared_ptr<FileProfile>>>();
     auto profileFuture = profilePromise->get_future();
     mip::FileProfile::LoadAsync(profileSettings, profilePromise);
     auto profile = profileFuture.get();

     // Construct/initialize engine object
     FileEngine::Settings engineSettings("1",       // User-defined engine ID
       "Client data",                               // User-defined engine state        
       "en-US");                                    // Locale (default = en-US)

     // Set up promise/future connect for async engine operations; add engine to profile asynchronously
     auto enginePromise = make_shared<promise<shared_ptr<FileEngine>>>();
     auto engineFuture = enginePromise->get_future();
     profile->AddEngineAsync(engineSettings, enginePromise);

     return 0;
   }

   ``` 

3. Teraz nie końcowego skompilować aplikację i usuń wszelkie błędy. Kod powinien pomyślnie, kompilacji, ale nie będzie jeszcze działała poprawnie, dopóki nie zostaną wykonane kolejnego przewodnika Szybki Start.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy kod inicjowania jest pełna, możesz przystąpić do kolejnego przewodnika Szybki Start, której rozpocznie się interfejsy API plików MIP.

> [!div class="nextstepaction"]
> [Utwórz listę etykiet czułości](quick-file-list-labels-cpp.md)
