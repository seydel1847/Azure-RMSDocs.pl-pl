---
title: Przewodnik Szybki Start — Utwórz listę etykiet czułości w dzierżawie ochronę informacji firmy Microsoft (MIP) przy użyciu zestawu SDK MIP C++
description: Przewodnik Szybki Start omawiający Użyj zestawu SDK usługi Microsoft Information Protection C++, aby wyświetlić listę etykiet czułości w dzierżawie.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 40248694a479632e2554c2d97f775bf99318de88
ms.sourcegitcommit: d5669b9bcc4aebabf64e8891eda4e20ea3acb2a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046958"
---
# <a name="quickstart-list-sensitivity-labels-c"></a>Szybki Start: Lista etykiet czułość (C++)

Ten przewodnik Szybki Start dowiesz się, jak używać interfejsu API plików MIP, aby wyświetlić listę etykiet czułości skonfigurowanych dla Twojej organizacji.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli jeszcze nie, pamiętaj przed kontynuowaniem należy spełnić następujące wymagania wstępne:

- Pełne [Szybki Start: Inicjowanie aplikacji klienta (C++)](quick-app-initialization-cpp.md) najpierw tworzy moduł uruchamiający rozwiązania Visual Studio. Przewodnik Szybki Start to "Lista etykiet czułości" opiera się na poprzedniej wersji, do tworzenia odpowiedniego rozwiązania początkowego.
- Opcjonalnie: Przejrzyj [etykiet klasyfikacji](concept-classification-labels.md) pojęcia.

## <a name="add-logic-to-list-the-sensitivity-labels"></a>Dodaj logikę, aby wyświetlić listę etykiet czułości

Dodaj logikę, aby wyświetlić listę etykiet ważność Twojej organizacji, za pomocą obiektu aparatu plików. 

1. Otwórz rozwiązanie programu Visual Studio został utworzony w poprzedniej "Szybki Start: Inicjowanie aplikacji klienta (C++)" artykułu.

2. Za pomocą **Eksploratora rozwiązań**, otwórz plik .cpp w projekcie, który zawiera implementację `main()` metody. Domyślnie taką samą nazwę jak projekt zawierający go, co zostało określone podczas tworzenia projektu. 

3. Dodaj następujący kod `using` dyrektywy po `using mip::FileEngine;`, w górnej części pliku:

   ```cpp
   using std::endl;
   ```

4. Kierunku końca `main()` treść poniżej zamykającego nawiasu klamrowego `}` z `catch` bloku i nowsze wersje `return 0;` (tam, gdzie Przerwano w poprzednim przewodniku Szybki Start), Wstaw następujący kod:

   ```cpp
   // List sensitivity labels
   cout << "\nSensitivity labels for your organization:\n";
   auto labels = engine->ListSensitivityLabels();
   for (const auto& label : labels)
   {
      cout << label->GetName() << " : " << label->GetId() << endl;

      for (const auto& child : label->GetChildren())
      {
        cout << "->  " << child->GetName() << " : " << child->GetId() << endl;
      }
   }
   system("pause");
   ``` 

## <a name="create-a-powershell-script-to-generate-access-tokens"></a>Tworzenie skryptu programu PowerShell, aby wygenerować tokeny dostępu

Używasz poniższy skrypt programu PowerShell do generowania tokenów dostępu, zgodnie z żądaniem z zestawu SDK. Skrypt używa `Get-ADALToken` polecenia cmdlet z modułu ADAL.PS wcześniej zainstalowany, a w "Zestaw SDK MIP instalacja i konfiguracja". 

1. Utwórz plik skryptu programu PowerShell (z rozszerzeniem .ps1) i skopiuj/Wklej poniższy skrypt do pliku:

   - Aktualizacja `$appId` i `$redirectUri` zmiennych, dopasowując wartości określone w Twojej rejestracji aplikacji usługi Azure AD. 
   - `$authority` i `$resourceUrl` są aktualizowane później, w poniższej sekcji.

   ```powershell
   $authority = '<authority-url>'                   # Enforced by MIP SDK
   $resourceUrl = '<resource-url>'                  # Enforced by MIP SDK; matches a resource/API URL requested in the app registration
   $appId = '0edbblll-8773-44de-b87c-b8c6276d41eb'  # App ID of the Azure AD app registration
   $redirectUri = 'bltest://authorize'              # Must match the redirect URI of the Azure AD app registration
   $response = Get-ADALToken -Resource $resourceUrl -ClientId $appId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:RefreshSession 
   $response.AccessToken | clip                     # Copy the access token text to the clipboard
   ```

2. Zapisz plik skryptu, aby można było uruchomić później, zgodnie z żądaniem przez aplikację kliencką.

## <a name="build-and-test-the-application"></a>Tworzenie i testowanie aplikacji

Na koniec Skompiluj i testowanie aplikacji klienckiej. 

1. Użyj F6 (**Kompiluj rozwiązanie**) do tworzenia aplikacji klienckiej. Jeśli żadne błędy kompilacji, należy użyć F5 (**Rozpocznij debugowanie**) do uruchamiania aplikacji.

2. Jeśli projektu kompilacji i zostanie wykonane pomyślnie, aplikacja wyświetli monit o podanie tokenu dostępu, zawsze wywołuje zestawu SDK usługi `AcquireOAuth2Token()` metody. Możesz ponownie używać wcześniej wygenerowany token, jeśli zostanie wyświetlony monit wielokrotnie i wymagane wartości są takie same:

   ```cmd
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://syncservice.o365syncservice.com/
   Be sure to sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token:
   ```

3. Aby podać odpowiedzi na monit powyżej, wróć do skryptu programu PowerShell oraz:

   - Aktualizacja `$authority` i `$resourceUrl` zmiennych. Muszą one odpowiadać wartości, które są określone w danych wyjściowych konsoli w kroku #2. Te wartości są podane przez zestaw SDK MIP w `challenge` parametru `AcquireOAuth2Token()`:
     - `$authority` powinien być `https://login.windows.net/common/oauth2/authorize`
     - `$resourceUrl` powinien być `https://syncservice.o365syncservice.com/` lub `https://aadrm.com`
   - Uruchom skrypt programu PowerShell. `Get-ADALToken` Polecenia cmdlet Wyzwalacze usługi Azure AD monitu dotyczącego uwierzytelniania podobny do poniższego przykładu. Należy określić to samo konto, podana w danych wyjściowych konsoli w kroku #2. Po pomyślnym zalogowaniu token dostępu zostaną umieszczone w Schowku.

     [![Program Visual Studio uzyskania tokenu logowania](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Może trzeba będzie również wyrazić zgodę, aby umożliwić aplikacji dostęp do interfejsów API MIP podczas pracy w ramach konta logowania. Dzieje się tak, gdy rejestracja aplikacji usługi Azure AD nie jest wstępnie wyraził zgodę (zgodnie z opisem w "zestaw SDK MIP instalacja i konfiguracja") lub logujesz się przy użyciu konta z innej dzierżawy (innej niż ta, których Twoja aplikacja będzie zarejestrowana). Po prostu kliknij **Akceptuj** do rejestrowania Twojej zgody.

     [![Visual Studio wyrażania zgody.](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

4. Po dostarczeniu tokeny dostępu, dane wyjściowe z konsoli powinien być wyświetlony etykiety ważności, podobny do poniższego przykładu:

   ```cmd
   Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
   Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
   General : f42a3342-8706-4288-bd31-ebb85995028z
   Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
   Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z

   Press any key to continue . . .
   ```

   > [!NOTE]
   > Skopiuj i Zapisz identyfikator jednego lub więcej etykiet czułość (na przykład `f42a3342-8706-4288-bd31-ebb85995028z`), ponieważ użyjesz go w kolejnym przewodniku Szybki Start.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="problems-during-execution-of-powershell-script"></a>Problemy podczas wykonywania skryptu programu PowerShell 

| Podsumowanie | Komunikat o błędzie | Rozwiązanie |
|---------|---------------|----------|
| Nieprawidłowy identyfikator URI przekierowania w rejestracji aplikacji lub skryptu środowiska PowerShell (AADSTS50011) |*AADSTS50011: Odpowiedź adres url określony w żądaniu nie odpowiada adresy URL odpowiedzi skonfigurowane dla aplikacji: "ac6348d6-0d2f-4786-af33-07ad46e69bfc".* | Sprawdź przekierowania URI używany, wykonując jedną z następujących czynności:<br><br><li>Zaktualizuj identyfikator URI przekierowania w konfiguracji aplikacji usługi Azure AD, aby dopasować skryptu programu PowerShell. Zobacz [MIP SDK instalacja i Konfiguracja](setup-configure-mip.md#register-a-client-application-with-azure-active-directory) Aby sprawdzić, czy zostały poprawnie skonfigurowane właściwości identyfikatora URI przekierowania.<br><li>Aktualizacja `redirectUri` zmiennych w skrypcie programu PowerShell, aby dopasować rejestracji aplikacji. |
| Nieprawidłowe konto logowania (AADSTS50020) | *AADSTS50020: Konto użytkownika "user@domain.com"od dostawcy tożsamości"https://sts.windows.net/72f988bl-86f1-41af-91ab-2d7cd011db47/" nie istnieje w dzierżawie "Organizacji name" i nie ma dostępu do aplikacji "0edbblll-8773-44de-b87c-b8c6276d41eb" w tej dzierżawie.* | Wykonaj jedną z następujących czynności:<br><br><li>Ponownie uruchom skrypt programu PowerShell, ale pamiętaj użyć konta z tą samą dzierżawą, gdzie aplikacja usługi Azure AD jest zarejestrowany.<br><li>Jeśli Twoje konto logowania była poprawna, sesji programu PowerShell hosta już być uwierzytelniane przy użyciu innego konta. W tym przypadku zakończenia, który następnie otwórz ponownie host skryptów, a następnie spróbuj ponownie uruchomić.<br><li>Jeśli używasz tego przewodnika Szybki Start z aplikacją sieci web (a nie w trybie macierzystym), a następnie konieczne będzie zalogowanie się przy użyciu konta z innej dzierżawy, upewnij się, że włączono rejestrację aplikacji usługi Azure AD do użycia z wieloma dzierżawami. Sprawdź przy użyciu funkcji "Edytuj Manifest" w rejestracji aplikacji i upewnij się, określa on `"availableToOtherTenants": true,`. |
| Niepoprawne uprawnienia w rejestracji aplikacji (AADSTS65005) | *AADSTS65005: Nieprawidłowy zasób. Klient zażądał dostępu do zasobu, który nie znajduje się w żądanych uprawnień w rejestracji aplikacji klienta. Identyfikatora aplikacji klienckiej: 0edbblll-8773-44de-b87c-b8c6276d41eb. Wartość zasobu z żądania: https://syncservice.o365syncservice.com/. Identyfikator aplikacji zasobu: 43-bdda-6ed9a579b725 870c4f2e-85b6 - 4d. Lista prawidłowych zasobów z rejestracji aplikacji: 00000002-0000-0000-c000-000000000000.* | Aktualizowanie żądanych uprawnień w konfiguracji aplikacji usługi Azure AD. Zobacz [MIP SDK instalacja i Konfiguracja](setup-configure-mip.md#register-a-client-application-with-azure-active-directory) Aby sprawdzić, czy zostały poprawnie skonfigurowane żądań uprawnień w Twojej rejestracji aplikacji. |

### <a name="problems-during-execution-of-c-application"></a>Problemy podczas wykonywania aplikacji C++

| Podsumowanie | Komunikat o błędzie | Rozwiązanie |
|---------|---------------|----------|
| Nieprawidłowy token dostępu | *Wystąpił wyjątek... jest token dostępu, nieprawidłowy/wygasły? <br> <br>Wywołania API nie powiodło się: profile_add_engine_async nie powiodło się: [klasy mip::PolicySyncException] nie powiodło się uzyskiwania zasad, żądanie nie powiodło się z kodem stanu http: 401, x-ms-diagnostics: [2000001; Przyczyna = "token OAuth przesłane z Nie można przeanalizować żądania. "; error_category = "invalid_token"], identyfikator korelacji: [35bc0023-3727-4eff-8062-000006d5d672] "<br><br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (proces 29924) został zakończony z kodem 0.<br> <br>Naciśnij dowolny klawisz, aby zamknąć to okno...* | Jeśli projekt jest kompilowany pomyślnie, ale zostaną wyświetlone dane wyjściowe podobne do lewej, prawdopodobnie masz token z nieprawidłowymi lub wygasłymi w swojej `AcquireOAuth2Token()` metody. Wróć do [aktualizowanie logiki uzyskanie tokenu](#update-the-token-acquisition-logic-with-a-valid-access-token) i ponownie je generować aktualizacji tokenem dostępu `AcquireOAuth2Token()` ponownie i ponownej kompilacji/wykonaj test ponownie. Możesz również sprawdzić i sprawdź token i jego oświadczenia, za pomocą polecenia [jwt.ms](https://jwt.ms/) aplikacji jednej strony sieci web. |
| Czułość etykiety nie są konfigurowane. | n/d | Jeśli projekt jest kompilowany pomyślnie, ale masz żadnych danych wyjściowych w oknie konsoli, upewnij się, że etykiety ważności Twojej organizacji są poprawnie skonfigurowane. Zobacz [MIP SDK instalacja i Konfiguracja](setup-configure-mip.md)w obszarze "Zdefiniować ustawienia taksonomii i ochrony etykiety", aby uzyskać szczegółowe informacje.  |

## <a name="next-steps"></a>Następne kroki

Teraz, kiedy znasz sposób wyświetlenia listy etykiety ważności dla Twojej organizacji, wypróbuj kolejnego przewodnika Szybki Start:

> [!div class="nextstepaction"]
> [Ustawianie i pobieranie etykieta poufności](quick-file-set-get-label-cpp.md)
