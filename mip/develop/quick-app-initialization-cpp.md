---
title: Przewodnik Szybki Start — inicjowanie dla klientów ochrony informacji firmy Microsoft (MIP) zestawu SDK C++
description: Przewodnik Szybki Start omawiający pisania logiki inicjowania dla klienta ochrony informacji firmy Microsoft (MIP) zestawu SDK aplikacji.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 578c5aa69faa986663ea6c164d94e5940580167d
ms.sourcegitcommit: 76e1b7c0255700813590be62d94b19338bf6c201
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48866140"
---
# <a name="quickstart-client-application-initialization-c"></a>Szybki Start: Inicjowanie aplikacji klienta (C++)

Ten przewodnik Szybki Start opisano, jak zaimplementować wzorzec inicjowanie klienta, używany przez zestaw SDK języka C++ MIP w czasie wykonywania. 

> [!NOTE]
> Kroki opisane w tym przewodniku Szybki Start są wymagane dla dowolnej aplikacji klienckiej, która używa pliku MIP, zasad lub interfejsów API ochrony. Chociaż ten przewodnik Szybki Start pokazuje sposób użycia interfejsów API plików, ten sam wzorzec ma zastosowanie do klientów za pomocą zasad i interfejsów API ochrony. Przewodniki Szybki Start w przyszłości powinno się odbywać pojedynczo, zgodnie z każdej z nich jest oparta na poprzedni, z tym kontem jest pierwszy.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli jeszcze nie, należy koniecznie:

- Wykonaj kroki [SDK ochronę informacji firmy Microsoft (MIP), instalacja i Konfiguracja](setup-configure-mip.md). Ta "klienta Inicjowanie aplikacji" Szybki Start opiera się na właściwe instalacji zestawu SDK i konfiguracji.
- Opcjonalnie:
  - Przegląd [obiektów profilu i aparat](concept-profile-engine-cpp.md). Obiekty profilu i aparat są uniwersalne koncepcji, wymagane przez klientów, którzy używają interfejsów API MIP, plik/zasady/ochrony. 
  - Przegląd [pojęć dotyczących uwierzytelniania](concept-authentication-cpp.md) Aby dowiedzieć się, jak uwierzytelnianie i zgody są implementowane przez aplikację zestawu SDK i klienta.
  - Przegląd [pojęcia obserwatora](concept-async-observers.md) dowiedzieć się więcej o obserwatorów i sposobu ich implementacji. Zestaw SDK MIP sprawia, że użycie wzorca obserwatora w celu wdrożenia powiadomienia o zdarzeniach asynchronicznych.

## <a name="create-a-visual-studio-solution-and-project"></a>Tworzenie projektu i rozwiązania Visual Studio

Najpierw utworzymy i skonfigurować początkowe rozwiązania Visual Studio oraz projektu, na którym zostanie skompilowany inne Przewodniki Szybki Start. 

1. Otwórz program Visual Studio 2017, wybierz opcję **pliku** menu **New**, **projektu**. W **nowy projekt** okno dialogowe:
   - W okienku po lewej stronie w obszarze **zainstalowane**, **inne języki**, wybierz opcję **Visual C++**.
   - W środkowym okienku wybierz **Windows aplikacji konsoli**
   - W dolnym okienku zaktualizować projekt **nazwa**, **lokalizacji**i zawierający **Nazwa rozwiązania** odpowiednio.
   - Po zakończeniu kliknij przycisk **OK** przycisk w prawym dolnym rogu.

     [![Tworzenie rozwiązania w usłudze Visual Studio](media/quick-app-initialization-cpp/create-vs-solution.png)](media/quick-app-initialization-cpp/create-vs-solution.png#lightbox)

2. Dodaj pakiet Nuget interfejsu API plików zestawu SDK MCI do projektu:
   - W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu (bezpośrednio pod węzłem top/rozwiązania) i wybierz **Zarządzaj pakietami NuGet...** :
   - Gdy **Menedżera pakietów NuGet** Otwiera zakładkę w obszarze kart edytora grupy:
     - Wybierz **Przeglądaj**.
     - Wprowadź "Microsoft.InformationProtection" w polu wyszukiwania.
     - Wybierz pakiet "Microsoft.InformationProtection.File".
     - Kliknij przycisk "Zainstaluj", a następnie kliknij przycisk "OK", kiedy **podgląd zmian** Wyświetla okno dialogowe potwierdzenia.
   
     [![Program Visual Studio Dodaj pakiet NuGet](media/quick-app-initialization-cpp/add-nuget-package.png)](media/quick-app-initialization-cpp/add-nuget-package.png#lightbox)
 
## <a name="implement-an-observer-class-to-monitor-the-file-profile-and-engine-objects"></a>Implementowanie klasy obserwatora do monitorowania obiektów profilu i aparat plików

Teraz Utwórz podstawową implementację klasy obserwatora pliku profilu, rozszerzając zestawu SDK `mip::FileProfile::Observer` klasy. Obserwator jest tworzone i używane później do monitorowania podczas ładowania pliku obiektu profilu i Dodawanie obiektu aparat w profilu.

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

Zestaw SDK MIP implementuje uwierzytelniania za pomocą funkcji rozszerzalności klasy, która udostępnia mechanizm do udostępniania pracy uwierzytelniania za pomocą aplikacji klienckiej. Klient musi uzyskać odpowiedni token dostępu OAuth2 i zapewnienie SDK MIP w czasie wykonywania. 

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
          std::string mToken;
          std::string mAuthority;
          std::string mResource;
     };
     ```

   - Zaktualizuj "auth_delegate.cpp", zastępując wszystkie wygenerowany `auth_delegate` Implementacja klasy przy użyciu następujących źródła. **Nie** Usuń dyrektywy preprocesora, generowane przez poprzedniego kroku (#pragma, #include). 

     > [!IMPORTANT]
     > Poniższy kod tokenu nie nadaje się do użytku produkcyjnego. W środowisku produkcyjnym, to należy zastąpić kod, który dynamicznie uzyskuje token, za pomocą:
     > - appId i odpowiedzi/redirect URI określone w rejestracji aplikacji usługi Azure AD (odpowiedzi/identyfikator URI przekierowania **musi** odpowiadać Twojej rejestracji aplikacji)
     > - Adres URL urzędu i zasobów przekazywane przez zestaw SDK w `challenge` argumentu (adres URL zasobu **musi** dopasowania uprawnień interfejsu API rejestracji aplikacji)
     > - Prawidłowe aplikacji/poświadczenia użytkownika, jeśli konto odpowiada `identity` argument przekazywany przez zestaw SDK. Klienci "natywnego" OAuth2 należy monit o podanie poświadczeń użytkownika i korzystać z tego przepływu "Kod autoryzacji". OAuth2 "poufne klienci" można użyć własnych, bezpiecznych poświadczeń z usługą flow "poświadczeń klienta" (na przykład usługi), lub monit o podanie poświadczeń użytkownika przy użyciu usługi flow "Kod autoryzacji" (np. aplikacji sieci web). 
     >
     > Uzyskanie tokenu protokołu OAuth2 jest protokołem złożone i zazwyczaj są realizowane za pomocą biblioteki. Nosi nazwę TokenAcquireOAuth2Token() **tylko** przez zestaw SDK MIP, zgodnie z potrzebami.

     ```cpp
     #include <iostream>
     using std::cout;
     using std::cin;
     using std::string;

     bool AuthDelegateImpl::AcquireOAuth2Token(const mip::Identity& identity, const OAuth2Challenge& challenge, OAuth2Token& token) 
     {
          // Acquire a token manually, reuse previous token if same authority/resource. In production, replace with token acquisition code.
          string authority = challenge.GetAuthority();
          string resource = challenge.GetResource();
          if (mToken == "" || (authority != mAuthority || resource != mResource))
          {
              cout << "\nRun the PowerShell script to generate an access token using the following values, then copy/paste it below:\n";
              cout << "Set $authority to: " + authority + "\n";
              cout << "Set $resourceUrl to: " + resource + "\n";
              cout << "Sign in with user account: " + identity.GetEmail() + "\n";
              cout << "Enter access token: ";
              cin >> mToken;
              mAuthority = authority;
              mResource = resource;
              system("pause");
          }

          // Pass access token back to MIP SDK
          token.SetAccessToken(mToken);

          // True = successful token acquisition; False = failure
          return true;
     }
     ``` 
3. Opcjonalnie użyj F6 (**Kompiluj rozwiązanie**) próba uruchomienia testu kompilacji/łącze rozwiązania, aby upewnić się, że pomyślnie skompilowana przed kontynuowaniem.

## <a name="implement-a-consent-delegate"></a>Implementowanie delegata zgody

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
     // Construct/initialize objects required by the application's profile object
     ApplicationInfo appInfo{"<application-id>",                    // ApplicationInfo object (App ID, friendly name)
                 "<friendly-name>" };
     auto profileObserver = make_shared<ProfileObserver>();         // Observer object                  
     auto authDelegateImpl = make_shared<AuthDelegateImpl>(         // Authentication delegate object (App ID)
                 "<application-id>");
     auto consentDelegateImpl = make_shared<ConsentDelegateImpl>(); // Consent delegate object
 
     // Construct/initialize profile object
     FileProfile::Settings profileSettings("",    // Path for logging/telemetry/state
       true,                                      // true = use in-memory state storage (vs disk)
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
     FileEngine::Settings engineSettings(
       mip::Identity("<engine-account>"),         // Engine identity (account used for authentication)
       "<engine-state>",                          // User-defined engine state      
       "en-US");                                  // Locale (default = en-US)

     // Set up promise/future connection for async engine operations; add engine to profile asynchronously
     auto enginePromise = make_shared<promise<shared_ptr<FileEngine>>>();
     auto engineFuture = enginePromise->get_future();
     profile->AddEngineAsync(engineSettings, enginePromise);
     std::shared_ptr<FileEngine> engine; 
     try
     {
       engine = engineFuture.get();             
     }
     catch (const std::exception& e)
     {
       cout << "An exception occurred... is the access token incorrect/expired?\n\n"
        << e.what() << "'\n";
       system("pause");
       return 1;
     }

      return 0;
     }

   ``` 

3. Zastąp wartości symboli zastępczych w kodzie źródłowym, po prostu wklejony, używając następujących wartości:

   | Symbol zastępczy | Wartość | Przykład |
   |:----------- |:----- |:--------|
   | \<Identyfikator aplikacji\> | Identyfikator aplikacji usługi Azure AD przypisane do aplikacji zarejestrowanych w "Instalacja zestawu MIP SDK and configuration" (2 wystąpienia).  | 0edbblll-8773-44de-b87c-b8c6276d41eb |
   | \<Przyjazna nazwa\> | Zdefiniowane przez użytkownika przyjazną nazwę dla aplikacji. | AppInitialization |
   | \<Aparat konta\> | Konto używane dla tożsamości aparatu. Podczas uwierzytelniania przy użyciu konta użytkownika podczas uzyskanie tokenu musi być zgodna wartość. | user1@tenant.onmicrosoft.com |
   | \<Stan aparatu\> | Stan użytkownika ma zostać skojarzony z aparatem. | MyAppState |


4. Teraz nie końcowego skompilować aplikację i usuń wszelkie błędy. Kod powinien pomyślnie, kompilacji, ale nie będzie jeszcze działała poprawnie, dopóki nie zostaną wykonane kolejnego przewodnika Szybki Start. Jeśli aplikacja zostanie uruchomiona, zobaczysz dane wyjściowe podobne do następujących. Nie masz token dostępu, aby zapewnić, dopóki nie zostaną wykonane kolejnego przewodnika Szybki Start.

   ```console
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://syncservice.o365syncservice.com/
   Be sure to sign in with user account:
   Enter access token:
   ```

## <a name="next-steps"></a>Następne kroki

Teraz, gdy kod inicjowania jest pełna, możesz przystąpić do kolejnego przewodnika Szybki Start, której rozpocznie się interfejsy API plików MIP.

> [!div class="nextstepaction"]
> [Utwórz listę etykiet czułości](quick-file-list-labels-cpp.md)
