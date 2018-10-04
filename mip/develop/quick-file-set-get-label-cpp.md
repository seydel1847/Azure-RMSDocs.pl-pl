---
title: Przewodnik Szybki Start — zestaw i get etykiety ważności, z pliku przy użyciu zestawu SDK MIP C++
description: Przewodnik Szybki Start informacjami na temat używania zestawu SDK usługi Microsoft Information Protection C++ ustawiać i pobierać etykieta poufności w pliku.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 651fc73c00f18d06ad1a824337a096331bc7e897
ms.sourcegitcommit: d677088db8588fb2cc4a5d7dd296e76d0d9a2e9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251747"
---
# <a name="quickstart-set-and-get-a-sensitivity-label-c"></a>Szybki Start: Ustawianie i pobieranie etykiety ważności (C++)

Ten przewodnik Szybki Start przedstawiono sposób użycia interfejsów API plików MIP. Przy użyciu jednej z etykiety ważności, które wymienionych w poprzednim przewodniku Szybki Start, umożliwia obsługę plików Ustawianie/pobieranie etykiety w pliku. Plik, który klasa procedury obsługi udostępnia różne operacje pobierania/ustawienie etykiety lub ochrony, dla obsługiwanych typów plików.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli jeszcze nie, pamiętaj przed kontynuowaniem należy spełnić następujące wymagania wstępne:

- Pełne [Szybki Start: Lista etykiet czułość (C++)](quick-file-list-labels-cpp.md) najpierw tworzy moduł uruchamiający rozwiązania Visual Studio, aby wyświetlić listę etykiet poufności w organizacji. To "Zestaw i get etykieta poufności" Szybki Start opiera się na poprzedni.
- Opcjonalnie: Przejrzyj [plików obsługi w zestawie SDK MIP](concept-handler-file-cpp.md) pojęcia.

## <a name="implement-an-observer-class-to-monitor-the-file-handler-object"></a>Implementowanie klasy obserwatora do monitorowania obiekt programu obsługi plików

Podobnie jak obserwatora zaimplementowano (dla pliku profilu i aparat) podczas inicjowania aplikacji Szybki Start, teraz implementuje klasę obserwatora obiektu obsługi plików.

Utwórz podstawową implementację klasy obserwatora, rozszerzając zestawu SDK `mip::FileHandler::Observer` klasy. Obserwator jest tworzone i używane później do monitorowania operacji na plikach program obsługi.

1. Otwórz rozwiązanie programu Visual Studio, pracuje w poprzednim "Szybki Start: Lista etykiet czułość (C++)" artykułu.

2. Dodaj nową klasę do projektu, który generuje pliki zarówno nagłówek/h, jak i implementację/.cpp:

   - W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu ponownie, wybierz **Dodaj**, a następnie wybierz **klasy**.
   - Na **Dodaj klasę** okno dialogowe:
     - W **Nazwa klasy** wprowadź "filehandler_observer". Należy zauważyć, że zarówno **plik .h klasy** i **plik .cpp** pola są wypełniane automatycznie, na podstawie nazwy.
     - Po zakończeniu kliknij przycisk **OK** przycisku.

3. Po wygenerowaniu pliki .h i .cpp dla klasy, oba pliki są otwarte w edytorze grupy kart. Teraz zaktualizować każdego pliku, aby zaimplementować nowej klasie obserwatora:

   - Zaktualizuj "filehandler_observer.h", usuwając zaznaczenie/wygenerowany `filehandler_observer` klasy. **Nie** Usuń dyrektywy preprocesora, generowane przez poprzedniego kroku (#pragma, #include). Następnie skopiuj/Wklej następujące źródło do pliku, po wszelkie istniejące dyrektywy preprocesora:

     ```cpp
     #include <memory>
     #include "mip/file/file_engine.h"
     #include "mip/file/file_handler.h"

     class FileHandlerObserver final : public mip::FileHandler::Observer {
     public:
        FileHandlerObserver() { }
        // Observer implementation
        void OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) override;
        void OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
        void OnCommitSuccess(bool committed, const std::shared_ptr<void>& context) override;
        void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;       
     };
     ```

   - Zaktualizuj "filehandler_observer.cpp", usuwając zaznaczenie/wygenerowany `filehandler_observer` Implementacja klasy. **Nie** Usuń dyrektywy preprocesora, generowane przez poprzedniego kroku (#pragma, #include). Następnie skopiuj/Wklej następujące źródło do pliku, po wszelkie istniejące dyrektywy preprocesora:

     ```cpp
     void FileHandlerObserver::OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
        promise->set_value(fileHandler);
     }

     void FileHandlerObserver::OnCreateFileHandlerFailure(const std::exception_ptr & error, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
        promise->set_exception(error);
     }

     void FileHandlerObserver::OnCommitSuccess(bool committed, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<bool>>(context);
        promise->set_value(committed);
     }

     void FileHandlerObserver::OnCommitFailure(const std::exception_ptr & error, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<bool>>(context);
        promise->set_exception(error);
     }
     ```

4. Opcjonalnie użyj F6 (**Kompiluj rozwiązanie**) próba uruchomienia testu kompilacji/łącze rozwiązania, aby upewnić się, że pomyślnie skompilowana przed kontynuowaniem.

## <a name="add-logic-to-set-and-get-a-sensitivity-label"></a>Dodaj logikę do ustawiania i pobierania etykiety ważności

Dodaj logikę do ustawiania i pobierania etykieta poufności w pliku, za pomocą obiektu aparatu plików. 

1. Za pomocą **Eksploratora rozwiązań**, otwórz plik .cpp w projekcie, który zawiera implementację `main()` metody. Domyślnie taką samą nazwę jak projekt zawierający go, co zostało określone podczas tworzenia projektu. 

2. Dodaj następujący kod `#include` i `using` dyrektywy poniżej odpowiednie istniejące dyrektywy w górnej części pliku:

   ```cpp
   #include "filehandler_observer.h" 
   #include "mip/file/file_handler.h" 

   using mip::FileHandler;
   ```
3. Kierunku końca `main()` treść poniżej `system("pause");` i nowsze wersje `return 0;` (tam, gdzie Przerwano w poprzednim przewodniku Szybki Start), Wstaw następujący kod:

   ```cpp
   // Set up async FileHandler for input file operations
   string filePathIn = "<input-file-path>";
   std::shared_ptr<FileHandler> handler;
   try
   {
        auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
        auto handlerFuture = handlerPromise->get_future();
        engine->CreateFileHandlerAsync(filePathIn, mip::ContentState::REST, std::make_shared<FileHandlerObserver>(), handlerPromise);
        handler = handlerFuture.get();
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid input file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Set a label on input file
   try
   {
        string labelId = "<label-id>";
        cout << "\nApplying Label ID " << labelId << " to " << filePathIn << endl;
        mip::LabelingOptions labelingOptions(mip::AssignmentMethod::PRIVILEGED, mip::ActionSource::MANUAL);
        handler->SetLabel(labelId, labelingOptions);
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid label ID?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Commit changes, save as a different/output file
   string filePathOut = "<output-file-path>";
   try
   {
        cout << "Committing changes" << endl;
        auto commitPromise = std::make_shared<std::promise<bool>>();
        auto commitFuture = commitPromise->get_future();
        handler->CommitAsync(filePathOut, commitPromise);
        if (commitFuture.get()) {
            cout << "\nLabel committed to file: " << filePathOut << endl;
        }
        else {
            cout << "Failed to label: " + filePathOut << endl;
            return 1;
        }
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid commit file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }
   system("pause");

   // Set up async FileHandler for output file operations
   try
   {
        auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
        auto handlerFuture = handlerPromise->get_future();
        engine->CreateFileHandlerAsync(filePathOut, mip::ContentState::REST, std::make_shared<FileHandlerObserver>(), handlerPromise);
        handler = handlerFuture.get();
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid output file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Get the label from output file
   try
   {
        cout << "\nGetting the label committed to file: " << filePathOut << endl;
        auto label = handler->GetLabel();
        cout << "Name: " + label->GetLabel()->GetName() << endl;
        cout << "Id: " + label->GetLabel()->GetId() << endl;
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid label ID?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }
   system("pause");
   ```

4. Zastąp wartości symboli zastępczych w kodzie źródłowym, po prostu wklejony, używając następujących wartości:

   | Symbol zastępczy | Wartość |
   |:----------- |:----- |
   | \<ścieżki pliku dane wejściowe\> | Pełna ścieżka do testu wejściowy plik, na przykład: `c:\\Test\\Test.docx`. |
   | \<Identyfikator etykiety\> | Identyfikator etykiety ważności, skopiowane z poziomu konsoli, na przykład dane wyjściowe w poprzednim przewodniku Szybki Start: `f42a3342-8706-4288-bd31-ebb85995028z`. |
   | \<Ścieżka pliku wyjściowego\> | Pełna ścieżka do pliku wyjściowego, który będzie oznaczone kopię pliku wejściowego, na przykład: `c:\\Test\\Test_labeled.docx`. |

## <a name="build-and-test-the-application"></a>Tworzenie i testowanie aplikacji

Tworzenie i testowanie aplikacji klienckiej. 

1. Użyj F6 (**Kompiluj rozwiązanie**) do tworzenia aplikacji klienckiej. Jeśli żadne błędy kompilacji, należy użyć F5 (**Rozpocznij debugowanie**) do uruchamiania aplikacji.

2. Jeśli projektu kompilacji i zostanie wykonane pomyślnie, aplikacja wyświetli monit o podanie tokenu dostępu, zawsze wywołuje zestawu SDK usługi `AcquireOAuth2Token()` metody. Wcześniej w przewodniku "List czułości etykiety" Szybki Start uruchomisz skrypt programu PowerShell w celu uzyskania tokenu za każdym razem przy użyciu podanych wartości. `AcquireOAuth2Token()` podejmie próbę użycia tokenu wcześniej wygenerowany, jeśli kierowany i zasobów są takie same:

   ```console
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://syncservice.o365syncservice.com/
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Sensitivity labels for your organization:
   Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
   Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
   General : f42a3342-8706-4288-bd31-ebb85995028z
   Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
   Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z
   Press any key to continue . . .

   Applying Label ID 074e457c-5848-4542-9a6f-34a182080e7z to c:\Test\Test.docx
   Committing changes

   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://aadrm.com
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Label committed to file: c:\Test\Test_labeled.docx
   Press any key to continue . . .

   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/94f69844-8d34-4794-bde4-3ac89ad2b664/oauth2/authorize
   Set $resourceUrl to: https://aadrm.com
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Getting the label committed to file: c:\Test\Test_labeled.docx
   Name: Confidential
   Id: 074e457c-5848-4542-9a6f-34a182080e7z
   Press any key to continue . . .
   ```

Stosowanie etykiety, można sprawdzić, otwierając plik wyjściowy i wizualnie Sprawdzanie ustawień ochrony informacji dokumentu.

> [!NOTE]
> Jeśli masz etykietowania dokumentów pakietu Office, ale nie jest podpisany przy użyciu konta z dzierżawy usługi Azure Active Directory (AD), gdzie token dostępu został uzyskany (i etykiet czułości są skonfigurowane), użytkownik może zostać wyświetlony monit logowania przed otwarciem dokumentu oznakowanych. 



