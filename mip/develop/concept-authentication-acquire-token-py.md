---
title: Pojęcia — przy użyciu języka Python w celu uzyskania tokenu dostępu.
description: Ten artykuł pomoże Ci zrozumieć, jak używać języka Python w celu uzyskania tokenu dostępu OAuth2. Jest to wymagane przez implementację delegata uwierzytelniania.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: c574edb5f272b08f1fc13cc0e48fca6aa4d111a9
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214647"
---
# <a name="acquire-an-access-token-python"></a>Uzyskiwanie tokenu dostępu (Python)

Ten przykład pokazuje sposób wywołania zewnętrznego skryptu języka Python w celu uzyskania tokenu protokołu OAuth2. Jest to wymagane przez implementację delegata uwierzytelniania.

Ten kod nie jest przeznaczony do użycia w środowisku produkcyjnym, ale mogą być używane do programowania i zrozumienie pojęcia dotyczące uwierzytelniania. Próbka jest dla wielu platform.

## <a name="prerequisites"></a>Wymagania wstępne

Aby uruchomić poniższy przykład, następujące musi być kompletny:

- Zainstaluj język Python 2.7
- Implementowanie [utils.h/cpp]() w projekcie TODO: link do źródła w przykładowego repozytorium
- [auth.PY]() powinien zostać dodany do projektu, a istnieje w tym samym katalogu co pliki binarne na konferencji build.

## <a name="sampleauthacquiretoken"></a>Przykładowe:: auth::AcquireToken()

W [przykład proste uwierzytelnianie](), firma Microsoft przedstawiono prosty `AcquireToken()` funkcja, która trwała żadnych parametrów i zwracane twardy kodowanego wartość tokenu. W tym przykładzie firma Microsoft będzie przeciążenia AcquireToken() akceptują parametry uwierzytelniania i wywoływać zewnętrznego skryptu języka Python, aby powrócić do tokenu.

### <a name="authh"></a>auth.h

W auth.h `AcquireToken()` jest przeciążona i przeciążonej funkcji i zaktualizowano parametry są następujące:

```cpp
//auth.h
#include <string>

namespace sample {
  namespace auth {
    std::string AcquireToken();

    std::string AcquireToken(
        const std::string& userName, //A string value containing the user's UPN.
        const std::string& password, //The user's password in plaintext
        const std::string& clientId, //The AAD client ID of your application.
        const std::string& resource, //The resource URL for which an OAuth2 token is required. Provided by challenge object.
        const std::string& authority); //The authentication authority endpoint. Provided by challenge object.
    }
}
```

Pierwsze trzy parametry będzie dostępna przez użytkownika danych wejściowych lub twardych kodowane w aplikacji. Ostatnie dwa parametry są dostarczane przez zestaw SDK do delegata uwierzytelniania. 


### <a name="authcpp"></a>auth.cpp

W auth.cpp możemy dodać definicję przeciążonej funkcji, a następnie zdefiniować kod wymagany do wywołania skrypt w języku Python. Funkcja akceptuje wszystkie podane parametry i przekazuje je do skryptu języka Python. Skrypt jest wykonywany i zwraca token w formacie ciągu.

```cpp
#include "auth.h"
#include "utils.h"

#include <fstream>
#include <functional>
#include <memory>
#include <string>

using std::string;
using std::runtime_error;

namespace sample {
    namespace auth {

    string AcquireToken() { //ignore in this sample
    }

    //This function implements token acquisition in the application by calling an external Python script.
    //The Python script requires username, password, clientId, resource, and authority.
    //Username, Password, and ClientId are provided by the user/developer
    //Resource and Authority are provided as part of the OAuth2Challenge object that is passed in by the SDK to the AuthDelegate.
    string AcquireToken(
        const string& userName,
        const string& password,
        const string& clientId,
        const string& resource,
        const string& authority) {

    string cmd = "python";
    if (sample::FileExists("auth.py"))
        cmd += " auth.py -u ";

    else
        throw runtime_error("Unable to find auth script.");

    cmd += userName;
    cmd += " -p ";
    cmd += password;
    cmd += " -a ";
    cmd += authority;
    cmd += " -r ";
    cmd += resource;
    cmd += " -c ";
    cmd += (!clientId.empty() ? clientId : "6b069eef-9dde-4a29-b402-8ce866edc897");

    string result = sample::Execute(cmd.c_str());
    if (result.empty())
        throw runtime_error("Failed to acquire token. Ensure Python is installed correctly.");

    return result;
    }
    }
}

```

## <a name="python-script"></a>Skrypt w języku Python

Ten skrypt uzyskuje tokeny uwierzytelniania bezpośrednio za pośrednictwem żądania prostego protokołu http. To jest uwzględniana tylko jako oznacza, że można uzyskać tokenów uwierzytelniania do użycia przez przykładowych aplikacji i nie jest przeznaczona do użycia w kodzie produkcyjnym. Skrypt działa wyłącznie w odniesieniu do dzierżawy, które obsługują zwykłe stare uwierzytelnianie http nazwy użytkownika i hasła. Uwierzytelnianie wieloskładnikowe lub uwierzytelniania opartego na certyfikatach zakończy się niepowodzeniem.

TODO: Powinien można po prostu przejść do repozytorium, a nie dokumentów? 

```python
import getopt
import sys
import json
import urllib
import urllib2
import re

def printUsage():
  print('auth.py -u <username> -p <password> -a <authority> -r <resource> -c <clientId>')

def main(argv):
  try:
    options, args = getopt.getopt(argv, 'hu:p:a:r:c:')
  except getopt.GetoptError:
    printUsage()
    sys.exit(-1)

  username = ''
  password = ''
  authority = ''
  resource = ''
  clientId = ''

  for option, arg in options:
    if option == '-h':
      printUsage()
      sys.exit()
    elif option == '-u':
      username = arg
    elif option == '-p':
      password = arg
    elif option == '-a':
      authority = arg
    elif option == '-r':
      resource = arg
    elif option == '-c':
      clientId = arg

  if username == '' or password == '' or authority == '' or resource == '' or clientId == '':
    printUsage()
    sys.exit(-1)

  # Find everything after the last '/' and replace it with 'token'
  if not authority.endswith('token'):
    regex = re.compile('^(.*[\/])')
    match = regex.match(authority)
    authority = match.group()
    authority = authority + 'token'

  # Build REST call
  headers = {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Accept': 'application/json'
  }

  params = {
    'resource': resource,
    'client_id': clientId,
    'grant_type': 'password',
    'username': username,
    'password': password
  }

  req = urllib2.Request(
    url = authority,
    headers = headers,
    data = urllib.urlencode(params))

  f = urllib2.urlopen(req)
  response = f.read()
  f.close()
  sys.stdout.write(json.loads(response)['access_token'])

if __name__ == '__main__':
  main(sys.argv[1:])
```

## <a name="update-acquireoauth2token"></a>Aktualizuj AcquireOAuth2Token

Na koniec zaktualizuj `AcquireOAuth2Token` działa w programach `AuthDelegateImpl` wywołać przeciążonego `AcquireToken` funkcji. Zasób i urząd adresy URL są pobierane, zapoznając się `challenge.GetResource()` i `challenge.GetAuthority()`. `OAuth2Challenge` Jest przekazywany do pełnomocnika uwierzytelniania po dodaniu silnika. Tej pracy jest wykonywane przez zestaw SDK i nie wymaga dalszej pracy przez dewelopera. 

```cpp
bool AuthDelegateImpl::AcquireOAuth2Token(
    const mip::Identity& /*identity*/,
    const OAuth2Challenge& challenge,
    OAuth2Token& token) {

    //call our AcquireToken function, passing in username, password, clientId, and getting the resource/authority from the OAuth2Challenge object
    string accessToken = sample::auth::AcquireToken(mUserName, mPassword, mClientId, challenge.GetResource(), challenge.GetAuthority());
    token.SetAccessToken(accessToken);
    return true;
}
```

Gdy `engine` jest dodawany zestaw SDK wywoła "AcquireOAuth2Token funkcję, przekazując wyzwanie, wykonywanie skryptu języka Python, odbiera token, a następnie prezentować token do usługi.


