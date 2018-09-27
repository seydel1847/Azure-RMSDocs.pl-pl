---
title: Pojęcia — uwierzytelniania delegowanego implementacji (C++)
description: Ten artykuł pomoże Ci zrozumieć, jak zaimplementować delegata uwierzytelniania w języku C++.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a282d6a996cd1fd6a14b06fc9294f7aed793420c
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214546"
---
# <a name="implementing-an-authentication-delegate-c"></a>Implementowanie delegata uwierzytelniania (C++)

Zestaw SDK MIP zaimplementować delegata uwierzytelniania obsługi wezwań do uwierzytelnienia i odpowiada za pomocą tokenu. Nie sam implementuje uzyskanie tokenu. Proces pobierania tokenu zależy od dewelopera i odbywa się przez rozszerzenie `mip::AuthDelegate` klasy, w szczególności `AcquireOAuth2Token` funkcja elementu członkowskiego.

## <a name="building-authdelegateimpl"></a>Tworzenie AuthDelegateImpl

Aby rozszerzyć klasę bazową `mip::AuthDelegate`, utworzymy nową klasę o nazwie `sample::auth::AuthDelegateImpl`. Ta klasa implementuje `AcquireOAuth2Token` funkcje i ustawia konstruktora, aby wykonać nasze parametry uwierzytelniania.

### <a name="authdelegateimplh"></a>auth_delegate_impl.h

Na przykład domyślny konstruktor akceptuje tylko nazwy użytkownika, hasło i aplikacji [identyfikator aplikacji](/azure/active-directory/develop/developer-glossary.md#application-id-client-id). Będą one przechowywane w zmiennych prywatnych `mUserName`, `mPassword`, i `mClientId`.

Ważne jest, aby te informacje należy pamiętać, takiego jak dostawca tożsamości lub identyfikator URI zasobu nie są niezbędne do zaimplementowania przynajmniej nie w `AuthDelegateImpl` konstruktora. Czy informacje są przekazywane jako część `AcquireOAuth2Token` w `OAuth2Challenge` obiektu. Zamiast tego będzie przekazywać te informacje do `AcquireToken` wywołania `AcquireOAuth2Token`.

```cpp
//auth_delegate_impl.h
#include <string.h>
#include "mip/common_types.h"

namespace sample {
namespace auth {
class AuthDelegateImpl final : public mip::AuthDelegate { //extend mip::AuthDelegate base class
public:
  AuthDelegateImpl() = delete;

  //constructor accepts username, password, and clientId, all plain strings.
  AuthDelegateImpl(
    const std::string& userName,
    const std::string& password,
    const std::string& clientId
  );

  bool AcquireOAuth2Token(const mip::Identity& identity, const OAuth2Challenge& challenge, OAuth2Token& token) override;

private:
  std::string mUserName;
  std::string mPassword;
  std::string mClientId;
};

}
}
```

### <a name="authdelegateimplcpp"></a>auth_delegate_impl.cpp

`AcquireOAuth2Token` to, gdzie będzie nawiązywane połączenia do dostawcy protokołu OAuth2. W przykładzie poniżej miejsca są dwa wywołania `AcquireToken()`. W praktyce nastąpi tylko jedno wywołanie. Tych implementacji zostały omówione w sekcjach podano w obszarze [następne kroki](#next-steps)

```cpp
//auth_delegate_impl.cpp
#include "auth_delegate_impl.h"
#include <stdexcept>
#include "auth.h" //contains the auth class used later for token acquisition

using std::runtime_error;
using std::string;

namespace sample {
namespace auth {

AuthDelegateImpl::AuthDelegateImpl(
    const string& userName,
    const string& password,
    const string& clientId)
    : mUserName(userName),
    mPassword(password),
    mClientId(clientId) {
}

//Here we could simply add our token acquisition code to AcquireOAuth2Token
//Instead, that code is implemented in auth.h/cpp to demonstrate calling an external library
bool AuthDelegateImpl::AcquireOAuth2Token(
    const mip::Identity& /*identity*/, //This won't be used
    const OAuth2Challenge& challenge,
    const OAuth2Token& token) {

      //sample::auth::AcquireToken is the code where the token acquisition routine is implemented.
      //AcquireToken() returns a string that contains the OAuth2 token.

      //Simple example for getting hard coded token. Comment out if not used.
      string accessToken = sample::auth::AcquireToken();

      //Practical example for calling external OAuth2 library with provided authentication details.
      string accessToken = sample::auth::AcquireToken(mUserName, mPassword, mClientId, challenge.GetAuthority(), challenge.GetResource());  

      //set the passed in OAuth2Token value to the access token acquired by our provider
      token.SetAccessToken(accessToken);
      return true;
    }
}
}
```

## <a name="next-steps"></a>Następne kroki

Aby ukończyć implementację uwierzytelniania, jest niezbędne do utworzenia kod związany z `AcquireToken()` funkcji. Poniższe przykłady omówiono w nim na kilka sposobów w celu uzyskania tokenu.

- [Przykład uzyskanie tokenu prosty/programu PowerShell]()
- [Przykładem tokenu w języku Python]()
- [Przykład uwierzytelniania platformy node.js]()
