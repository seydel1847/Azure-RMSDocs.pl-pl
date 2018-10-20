---
title: Pojęcia — interfejsy API w zestawie SDK MIP.
description: Ten artykuł pomoże zrozumieć 3 typy interfejsów API w zestawie SDK MIP, jak są ze sobą powiązane i przypadki użycia dla każdej.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 10/16/2018
ms.author: bryanla
ms.openlocfilehash: 5c3f7ee97bfe003f2f215ba95ba196894ab8e197
ms.sourcegitcommit: cc65c3851d4b8169a1a62c83afaf0f75402f7631
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/20/2018
ms.locfileid: "49476191"
---
# <a name="microsoft-information-protection-sdk---api-concepts"></a>Usługi Microsoft Information Protection SDK — pojęcia dotyczące interfejsu API

Zestaw SDK ochronę informacji firmy Microsoft (MIP) składa się z trzech interfejsów API, jak pokazano na poniższym diagramie:

[![Interfejs API zestawu SDK MIP diagramu](media/concept-apis-use-cases/mip-sdk-components.png)](media/concept-apis-use-cases/mip-sdk-components.png#lightbox)

W zależności od potrzeb aplikacji możesz chcieć interfejsu w warstwie interfejsu API plików lub może być konieczna pomoc bezpośrednio z warstwami zasad lub interfejsie API ochrony.

## <a name="file-api"></a>Interfejs API plików

Interfejs API plików jest klasą abstrakcyjną ochrony i interfejsów API zasad. Oferuje ona łatwy w użyciu interfejsów odczytywanie etykiety z usługi, zastosowanie etykiety do typów zdefiniowanych plików i odczytywanie etykiety z tych typów plików. Interfejs API plików będzie używane przez miejsce w dowolnej aplikacji lub usługi:

- obsługiwany typ pliku jest używana.
- etykiety musi być zapisu lub odczytu
- zawartość musi być chroniona lub odszyfrować

### <a name="file-api-use-cases"></a>Przypadki użycia interfejsu API plików

- Możesz teraz inżynier oprogramowania, w instytucji usług finansowych. Chcesz mieć pewność, że dane z aplikacji biznesowych, zwykle eksportowany w formacie programu Excel, są oznaczone etykietami na eksport na podstawie zawartości. Interfejs API plików może służyć do listy dostępnych etykiet, a następnie zastosuj odpowiednią etykietę do obsługiwany format.

- Broker zabezpieczeń dostępu do chmury (CASB) są opracowywane w danej organizacji. Klienci, poproś o możliwość stosowania etykiet MIP dla Microsoft Office i PDF, dokumentów. Interfejs API plików umożliwia wyświetlanie listy skonfigurowanych etykiet, wówczas klientów do tworzenia reguł, które mają zastosowanie w danej etykiety. Interfejs API plików, przyjęcie identyfikator etykiety będzie zajmiemy się resztą, pliki spełniające kryteria klienta.

- Twoja organizacja udostępnia rozwiązania zapobiegania utracie danych oparta na usłudze lub CASB, które monitoruje aplikacje SaaS dla działania pliku. Aby ograniczyć ryzyko utraty danych lub zagrożenia, gdzie dane są chronione przez MIP, usługi wymaga skanowania zawartości plików chronionych. Za pomocą interfejsu API plików w obsługiwanych formatów, gdy usługa stanie się użytkownika uprzywilejowanego jest to możliwe:

  1. Usuwanie ochrony
  2. skanowanie zawartości ograniczony lub wrażliwych informacji
  3. odrzucić wynik w postaci zwykłego tekstu
  4. zastosować reguły usługi do raportu lub eliminowania ryzyka, jeśli znaleziono

## <a name="policy-api"></a>Zasady interfejsu API

Zasady interfejsu API lub uniwersalnych zasad aparatu (UPE), zapewnia możliwość dla deweloperów oprogramowania, które można pobrać zasad etykietowania dla określonego użytkownika. Go można następnie "compute" działania należy podjąć te etykiety.

Zasady interfejsu API jest używany przede wszystkim przez aplikacje klienckie, gdzie deweloper określa interfejs i format pliku. Jest również używany podczas jedynym wymaganiem jest bezpośrednio pobrać zasady użytkownika, a nie plików etykiet. 

### <a name="policy-api-use-cases"></a>Przypadki użycia interfejsów API zasad

- Oprogramowanie do projektowania 3D, który używa formatu pliku własności są opracowywane w danej organizacji. Klienci Użyj MIP, a do zastosowania etykiet w sposób natywny za pomocą aplikacji. Jako inżynier oprogramowania używasz zasad interfejsu API i formant niestandardowy do wyświetlania etykiet dostępne dla tego uwierzytelnionego użytkownika. Po użytkownik wybierze etykietę, możesz wywołać metody akcji obliczeniowych interfejsu API. Interfejs API informuje dokładnie co powinny być stosowane metadanych, zawartość, oznaczania i ochrony.

- Organizację usługi ochrony przed utratą danych (DLP), która umożliwia klientom Konfigurowanie zasad DLP obowiązujących w portalu witryny Administracja centralna. Masz użytkowników, którzy Użyj MIP, a musi odczytać lub stosowanie etykiet usługi AIP, jako część zasad DLP. Jako programista można użyć zasad interfejsu API w celu uzyskania listy etykiet dla organizacji klienta. Można następnie odczytać te etykiety jako część reguły DLP lub zastosować informacji etykiety jako część Akcja reguły.

## <a name="protection-api"></a>Ochrona interfejsu API

Ochrona interfejsu API zapewnia możliwość dla deweloperów oprogramowania przekonwertować strumienie zwykłego tekstu w zarządzanej prawami strumieni i na odwrót.

### <a name="protection-api-use-cases"></a>Przypadki użycia interfejsu API ochrony

- 3d drukowania oprogramowania przy użyciu formatu pliku moralnych opracowywane w danej organizacji. Chcesz użyć MCI do ochrony pliku, dzięki czemu można drukować tylko przez określonych użytkowników. Przy użyciu interfejsu API ochrony, aby stosować ochrony do pliku, aby tylko autoryzowani użytkownicy mogą otwierać i drukować. 

- Organizację rozwiązania zbierania elektronicznych materiałów dowodowych, która przetwarza skrzynek pocztowych programu Exchange i. Pliki PST. Twoja aplikacja potrzebuje do Zezwalaj użytkownikom na odszyfrowywania wiadomości, aby wykonać zbierania elektronicznych materiałów dowodowych. Przy użyciu analizatora niestandardowego komunikatu/RPMSG i wystarczająco uprzywilejowanego, można użyć interfejsu API usługi RMS, aby:
  - odszyfrowania zaszyfrowanych plików
  - skanowanie zawartości
  - odrzucenia, jeśli poza zakres lub pakietu, jeśli komputer znajduje się w zakresie

## <a name="next-steps"></a>Kolejne kroki

Teraz, gdy masz ogólne informacje o dostępnych interfejsach API MIP i sposoby ich używania, kontynuuj [pojęć dotyczących obiektu profilu i aparat](concept-profile-engine-cpp.md). Te pojęcia mają zasadnicze znaczenie i zastosować do wszystkich zestawów MIP API.