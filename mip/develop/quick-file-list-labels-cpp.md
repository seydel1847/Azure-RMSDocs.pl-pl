---
title: Przewodnik Szybki Start — Utwórz listę etykiet czułości w dzierżawie ochronę informacji firmy Microsoft (MIP) przy użyciu zestawu SDK MIP C++
description: Przewodnik Szybki Start omawiający Użyj zestawu SDK usługi Microsoft Information Protection C++, aby wyświetlić listę etykiet czułości w dzierżawie.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 77d473897d7e56c99db5210525dbccee6199b4ab
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214367"
---
# <a name="quickstart-list-sensitivity-labels-c"></a>Szybki Start: Lista etykiet czułość (C++)

Ten przewodnik Szybki Start dowiesz się, jak używać interfejsu API plików MIP, aby wyświetlić listę etykiet czułości skonfigurowanych dla Twojej organizacji.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli jeszcze nie, pamiętaj przed kontynuowaniem należy spełnić następujące wymagania wstępne:

- Pełne [Szybki Start: Inicjowanie aplikacji klienta (C++)](quick-app-initialization-cpp.md) najpierw tworzy moduł uruchamiający rozwiązania Visual Studio. Ten przewodnik Szybki Start zależy od poprzedniego odpowiednie tworzenia rozwiązania początkowego.
- Opcjonalnie: Przejrzyj [etykiet klasyfikacji](concept-classification-labels.md) pojęcia.

## <a name="add-logic-to-list-the-sensitivity-labels"></a>Dodaj logikę, aby wyświetlić listę etykiet czułości

Dodaj logikę, aby wyświetlić listę etykiet ważność Twojej organizacji, za pomocą obiektu aparatu plików. Jak wspomniano w komentarzach do kodu, wywołanie usługi `AcquireOAuth2Token()` metoda jest również wyzwalany, przez wywołanie `engineFuture.get()`.

1. Otwórz rozwiązanie programu Visual Studio został utworzony w poprzedniej "Szybki Start: Inicjowanie aplikacji klienta (C++)" artykułu.

2. Za pomocą **Eksploratora rozwiązań**, otwórz plik .cpp w projekcie, który zawiera implementację `main()` metody. Domyślnie taką samą nazwę jak projekt zawierający go, co zostało określone podczas tworzenia projektu. 

3. Dodaj następujący kod `using` dyrektywy po `using mip::FileEngine;`, w górnej części pliku:

   ```cpp
   using std::endl;
   ```

4. W treści `main()`, między `profile->AddEngineAsync(engineSettings, enginePromise);` i `return 0;` instrukcji (tam, gdzie Przerwano w poprzednim przewodniku Szybki Start), Wstaw następujący kod:

   ```cpp
   // Get engine object and list sensitivity labels
     try
     {
      // Get File engine asynchronously; also triggers AcquireOAuth2Token() call 
      auto engine = engineFuture.get();  
        
      // List sensitivity labels
      auto labels = engine->ListSensitivityLabels(); 
      for (const auto& label : labels)
      {
        cout << label->GetName() << " : " << label->GetId() << endl;

        for (const auto& child : label->GetChildren())
        {
          cout << "->  " << child->GetName() << " : " << child->GetId() << endl;
        }
      }
   }
   catch (const std::exception& e)
   {
      cout << "An exception occurred... is the access token incorrect/expired?\n\n" << e.what() << "'\n";
   }
   ``` 

## <a name="update-the-token-acquisition-logic-with-a-valid-access-token"></a>Aktualizowanie logiki uzyskanie tokenu przy użyciu tokenu dostępu nie jest ważna

1. Wygeneruj token testu za pomocą następującego skryptu programu PowerShell. Skrypt używa `Get-ADALToken` polecenia cmdlet z modułu ADAL.PS zainstalowany wcześniej, w MIP SDK instalacji i konfiguracji. 

   - Utwórz plik skryptu programu PowerShell (z rozszerzeniem .ps1) i skopiuj/Wklej poniższy skrypt do pliku:

     ```powershell
     $authority = 'https://login.windows.net/common/oauth2/authorize'  # Enforced by MIP SDK
     $resourceUrl = 'https://syncservice.o365syncservice.com/'         # Enforced by MIP SDK; matches the URL of the "Microsoft Information Protection Sync Service" resource/API requested by the Azure AD app registration
     $appId = '0edbblll-8773-44de-b87c-b8c6276d41eb'                   # App ID of the Azure AD app registration
     $redirectUri = 'bltest://authorize'                               # Must match the redirect URI of the Azure AD app registration
     $response = Get-ADALToken -Resource $resourceUrl -ClientId $appId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:RefreshSession 
     $response.AccessToken | clip                                      # Copies the access token text to the clipboard
     ```

   - Aktualizacja `$appId` i `redirectUri` zmiennych, które pasują do wartości określonych w Twojej rejestracji aplikacji usługi Azure AD.
   - Zapisz plik skryptu, a następnie uruchomić go za pomocą programu PowerShell. `Get-ADALToken` Polecenia cmdlet Wyzwalacze usługi Azure AD monitu dotyczącego uwierzytelniania podobny do poniższego przykładu. Po pomyślnym zalogowaniu token dostępu zostaną umieszczone w Schowku.

     [![Program Visual Studio Dodaj klasę](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Może trzeba będzie również wyrazić zgodę, aby umożliwić aplikacji dostęp do interfejsów API MIP w ramach konta logowania. Dzieje się tak, gdy rejestracja aplikacji usługi Azure AD nie jest wstępnie wyraził zgodę (zgodnie z opisem w "zestaw SDK MIP instalacja i konfiguracja") lub logujesz się przy użyciu konta z innej dzierżawy (innej niż ta, których Twoja aplikacja będzie zarejestrowana). Po prostu kliknij **Akceptuj** do rejestrowania Twojej zgody.

     [![Program Visual Studio Dodaj klasę](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

2. Natychmiast po ukończeniu kroku #1 powyżej, wróć do programu Visual Studio i użyj **Eksploratora rozwiązań** można otworzyć "auth_delegate.cpp". Przewiń w dół do Twojej `AcquireOAuth2Token()` implementacji i znajdź następujący wiersz kodu. Zastąp `<access-token>` symbolu zastępczego z tokenem umieszczane w Schowku w poprzednim kroku. Token powinien być ciąg, w formacie podobnym do `eyJ0eXAiOi ...`.

   ```cpp
   string accessToken = "<access-token>";
   ``` 

## <a name="build-and-test-the-application"></a>Tworzenie i testowanie aplikacji

Na koniec Skompiluj i testowanie aplikacji klienckiej. Jeśli projekt kompiluje i zostanie wykonane pomyślnie, powinny pojawić się dane wyjściowe podobne do poniższego przykładu w oknie konsoli: 

```cmd
Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
General : f42a3342-8706-4288-bd31-ebb85995028z
Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z

Press any key to continue . . .
```

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
| Nieprawidłowy token dostępu | *Wystąpił wyjątek... jest token dostępu, nieprawidłowy/wygasły? <br> <br>Wywołania API nie powiodło się: profile_add_engine_async nie powiodło się: [klasy mip::PolicySyncException] nie powiodło się uzyskiwania zasad, żądanie nie powiodło się z kodem stanu http: 401, x-ms-diagnostics: [2000001; Przyczyna = "token OAuth przesłane z Nie można przeanalizować żądania. "; error_category = "invalid_token"], identyfikator korelacji: [35bc0023-3727-4eff-8062-000006d5d672] "<br><br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (proces 29924) został zakończony z kodem 0.<br> <br>Naciśnij dowolny klawisz, aby zamknąć to okno...* | Jeśli projekt jest kompilowany pomyślnie, ale zostaną wyświetlone dane wyjściowe podobne do lewej, prawdopodobnie masz token z nieprawidłowymi lub wygasłymi w swojej `AcquireOAuth2Token()` metody. Wróć do [aktualizowanie logiki uzyskanie tokenu](#update-the-token-acquisition-logic) i ponownie je generować aktualizacji tokenem dostępu `AcquireOAuth2Token()` ponownie i ponownej kompilacji/wykonaj test ponownie. Możesz również sprawdzić i sprawdź token i jego oświadczenia, za pomocą polecenia [jwt.ms](https://jwt.ms/) aplikacji jednej strony sieci web. |
| Czułość etykiety nie są konfigurowane. | n/d | Jeśli projekt jest kompilowany pomyślnie, ale masz żadnych danych wyjściowych w oknie konsoli, upewnij się, że etykiety ważności Twojej organizacji są poprawnie skonfigurowane. Zobacz [MIP SDK instalacja i Konfiguracja](setup-configure-mip.md)w obszarze "Zdefiniować ustawienia taksonomii i ochrony etykiety", aby uzyskać szczegółowe informacje.  |


