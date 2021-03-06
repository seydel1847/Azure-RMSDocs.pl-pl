---
title: Pojęcia — przy użyciu programu PowerShell w celu uzyskania tokenu dostępu.
description: Ten artykuł pomoże Ci zrozumieć, jak można uzyskać tokenu dostępu OAuth2 przy użyciu programu PowerShell. Jest to wymagane przez implementację delegata uwierzytelniania.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a5ce346d044a9a56d37777e569582087026c9ce6
ms.sourcegitcommit: fa0be701b85b1fba5e75428714bb4525dd739a93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223889"
---
# <a name="acquire-an-access-token-powershell"></a>Uzyskiwanie tokenu dostępu (PowerShell)

Ten przykład pokazuje sposób wywołania zewnętrznego skryptu programu PowerShell w celu uzyskania tokenu protokołu OAuth2. Jest to wymagane przez implementację delegata uwierzytelniania.

Ten kod nie jest przeznaczony do użycia w środowisku produkcyjnym, ale mogą być używane do programowania i zrozumienie pojęcia dotyczące uwierzytelniania. 

## <a name="sampleauthacquiretoken"></a>Przykładowe:: auth::AcquireToken()

### <a name="authh"></a>auth.h

Możemy utworzyć pojedynczą funkcję o nazwie AcquireToken. Ponieważ wartość zwracana będzie twardych kodowane w ramach tego samouczka, firma Microsoft akceptuje nie parametrów, a następnie po prostu zwrócenia ciągu (token).

```cpp
//auth.h
#include <string>

namespace sample {
  namespace auth {
    std::string AcquireToken();
  }
}
```

### <a name="authcpp"></a>auth.cpp

Nasz plik źródłowy zwraca wartość tokenu, który będzie zakodowana w przyszłym kroku.

```cpp
//auth.cpp
#include <string>
#include "auth.h"

namespace sample {
  namespace auth {
    string AcquireToken() {
      std::string mToken = "your token here";
      return mToken;
    }
  }
}
```

## <a name="mint-a-token"></a>Mennic tokenu

Na koniec trudniej zdobyć token do umieszczenia w zmiennej mToken. Poniższy przykład pokazuje skrypt programu PowerShell, który może służyć do szybkiego uzyskiwania tokenu protokołu OAuth2 za pośrednictwem programu PowerShell, na Windows i biblioteki ADAL. Token ten zostanie ustanowione dla tylko końcowego Centrum zgodności i zabezpieczeń usługi Office 365. W związku z tym działań ochrony zakończy się niepowodzeniem, chyba, że adres URL zasobu jest aktualizowana. Zaleca się od razu przejść do [następne kroki](#next-steps) sekcji, jeśli chcesz przetestować etykietowania i ochrony w tym momencie.

### <a name="install-adalpshttpswwwpowershellgallerycompackagesadalps31942-from-ps-gallery"></a>Zainstaluj [ADAL.PS](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2) z galerii PS

```PowerShell
Install-Module -Name ADAL.PS
```

### <a name="use-get-adaltoken-to-obtain-the-access-token"></a>Uzyskiwanie tokenu dostępu przy użyciu Get ADALToken

```PowerShell
#Install the ADAL.PS package if it's not installed.
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps }

$authority = "https://login.windows.net/common/oauth2/authorize" 
#this is the security and compliance center endpoint
$resourceUrl = "https://dataservice.o365filtering.com"
#clientId and redirectUri are from the RMS Sharing Application. 
#Once custom app registration is supported, a custom id and uri will be required. 
$clientId = "0edbblll-8773-44de-b87c-b8c6276d41eb"
$redirectUri = "com.microsoft.rms-sharing-for-win://authorize"

$response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip
```

Skopiuj token ze Schowka w celu auth.cpp jako wartość pozycji `string mToken`, zastępując ciąg "token tutaj" powyżej. Uruchamiając ponownie skrypt może być wymagane, w zależności od tego, jak długo trwa następujące kroki.


