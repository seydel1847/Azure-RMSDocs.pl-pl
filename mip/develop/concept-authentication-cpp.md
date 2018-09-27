---
title: Pojęcia — służy do uwierzytelniania w zestawie SDK MIP.
description: Ten artykuł pomoże zrozumieć, jak zestaw SDK MIP implementuje uwierzytelnianie i wymagania dotyczące aplikacji klienckich zapewnić logikę uzyskanie tokenu dostępu OAuth2.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5f7a8409d79802fe96d26bf85ad073c53d8f76b3
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214459"
---
# <a name="authentication"></a>Uwierzytelnianie 

Uwierzytelnianie w zestawie SDK MIP jest wykonywane przez rozszerzenie klasy `mip::AuthDelegate` do zaimplementowania preferowaną metodę uwierzytelniania. `mip::AuthDelegate` zawiera:

- `mip::AuthDelegate::OAuth2Challenge` -klasę, która zarządza informacji urzędu OAuth2 i udostępnia do aplikacji klienckiej.
- `mip::AuthDelegate::OAuth2Token` — Klasa zarządza uzyskanie tokenu dostępu OAuth2 (od aplikacji klienckiej) i tokenu magazynu.
- `mip::AuthDelegate::AcquireOAuth2Token()` -jest czysta funkcja wirtualna, której implementację określa metodę uzyskanie tokenu dostępu. Po wywołaniu przez zestaw SDK go uzyskuje token dostępu, a następnie przekazuje go do logiki uwierzytelniania zestawu SDK.

`mip::AuthDelegate::AcquireOAuth2Token` akceptuje następujące parametry i zwraca wartość typu wartość logiczna wskazująca, czy uzyskanie tokenu zakończyło się pomyślnie:

- `mip::Identity`: Tożsamość użytkownika lub usługę, aby uwierzytelniali się, jeśli jest znany.
- `mip::AuthDelegate::OAuth2Challenge`: Przyjmuje dwa parametry **urząd** i **zasobów**. **Urząd** usługa token zostanie wygenerowany względem. **Zasób** usługa podejmujemy próbę uzyskania dostępu. Zestaw SDK będzie obsługiwać przekazywanie tych parametrów w do delegata, gdy zostanie wywołana.
- `mip::AuthDelegate::OAuth2Token`: Napiszemy tokenu wynik tego obiektu. Będzie można używane przez zestaw SDK, gdy aparat zostanie załadowany. Poza naszej implementacji uwierzytelniania nie powinny być niezbędne do pobierania lub ustawiania tej wartości w dowolnym miejscu.

**Ważne:** aplikacje nie wywołuj `AcquireOAuth2Token` bezpośrednio. Zestaw SDK wywoła tę funkcję, gdy jest to wymagane.

## <a name="consent"></a>Wyrażenie zgody

`mip::Consent` Klasa wyliczenia implementuje metody łatwy w użyciu, która pozwala deweloperom aplikacji zapewniając zgody niestandardowe środowisko oparte na punkt końcowy, który jest uzyskiwany przez zestaw SDK. Powiadomienia mogą informować użytkownika danych, które mają być zbierane, jak pobierać dane, usunięte lub inne informacje wymagane przez prawo lub zgodności zasad. Po użytkownik udziela zgodę, aplikacja może kontynuować. 

(TBD) W tym miejscu GDPR informacje? (TBD) Szczegóły wyjątku?

### <a name="implementation"></a>Implementacja

Zgoda jest implementowany przez rozszerzanie `mip::Consent` bazowa, klasy i wdrażanie `GetUserConsent` do zwrócenia jedną z `mip::Consent` wartości wyliczenia. 

Obiekt pochodzi od `mip::Consent` jest przekazywany do `mip::FileProfile::Settings` lub `mip::ProtectionProfile::Settings` konstruktora.

Gdy użytkownik wykona operację, która wymagałaby zgodę, wywołania SDK `GetUserConsent` metody, przekazując docelowego adresu URL jako parametr. To w przypadku tej metody, gdzie będzie jeden implementować, wyświetlanie informacji niezbędnych do użytkownika, umożliwiając im podejmowanie decyzji na informację, czy zgody na korzystanie z niej. 

Operacje, które będą wyzwalać przepływu wyrażania zgody są:

- Jeden
- Dwa

### <a name="consent-options"></a>Opcji wyrażania zgody

- **AcceptAlways**: zgody i zapamiętać decyzji.
- **Zaakceptuj**: zgody na raz.
- **Odrzuć**: nie zgadza się.

Gdy zestaw SDK zażąda zgody użytkownika przy użyciu tej metody, aplikacja kliencka powinni przedstawić potwierdzenie odpowiedniego adresu URL dla użytkownika. Aplikacje klienckie należy podać kilka sposobów uzyskiwania zgody użytkownika i ponownie odpowiednie wyliczenia zgody, który odpowiada decyzja użytkownika.

### <a name="sample-implementation"></a>Przykładowe zastosowanie

#### <a name="consentdelegateimplh"></a>consent_delegate_impl.h

```cpp
class ConsentDelegateImpl final : public mip::ConsentDelegate {
public:
  ConsentDelegateImpl() = default;
  
  virtual mip::Consent GetUserConsent(const std::string& url) override;

};
```

#### <a name="consentdelegateimplcpp"></a>consent_delegate_impl.cpp

Gdy zestaw SDK wymaga zgody, `GetUserConsent` wywoływana jest metoda *przez zestaw SDK*, oraz adres URL przekazany jako parametr. W poniższym przykładzie użytkownik jest powiadamiany, czy zestaw SDK będzie nawiązać połączenie, podany adres URL, następnie zwraca `Consent::AcceptAlways`. To nie jest świetny przykład, ponieważ użytkownik nie został przedstawiony dzięki szerokiemu wyborowi rzeczywistych.

```cpp
Consent ConsentDelegateImpl::GetUserConsent(const string& url) {
  //Print the consent URL, ask user to choose
  std::cout << "SDK will connect to: " << url << std::endl;

  std::cout << "1) Accept Always" << std::endl;
  std::cout << "2) Accept" << std::endl;
  std::cout << "3) Reject" << std::endl;
  std::cout << "Select an option: ";
  char input;
  std::cin >> input;

  switch (input)
  {
  case '1':
    return Consent::AcceptAlways;
    break;
  case '2':
    return Consent::Accept;
    break;
  case '3':
    return Consent::Reject;
    break;
  default:
    return Consent::Reject;
  }  
}
```

## <a name="next-steps"></a>Kolejne kroki

Dla uproszczenia przykłady ukazujące delegata wdroży uzyskanie tokenu przez wywołanie skryptu zewnętrznego. Ten skrypt mogą zostać zastąpione przez dowolny inny typ skryptu, biblioteki OAuth2 "open source" lub niestandardową biblioteką OAuth2.

- [Uzyskiwanie tokenu dostępu przy użyciu programu PowerShell](concept-authentication-acquire-token-ps.md)
- [Uzyskiwanie tokenu dostępu przy użyciu języka Python](concept-authentication-acquire-token-py.md)
