---
title: Pojęcia — interfejsy API w zestawie SDK MIP.
description: Ten artykuł pomoże zrozumieć 3 typy interfejsów API w zestawie SDK MIP, jak są ze sobą powiązane i przypadki użycia dla każdej.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 02fc1ef3c53cd94c35943a4a093c42968c251cdf
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214471"
---
# <a name="mip-sdk-apis"></a>Interfejsy API zestawu SDK MIP

Zestaw SDK MIP składa się z trzech interfejsów API:

- [Ochrona interfejsu API](#protection-api)
- [Zasady interfejsu API](#policy-api)
- [Interfejs API plików](#file-api)

## <a name="protection-api"></a>Ochrona interfejsu API

Ochrona interfejsu API zapewnia możliwość dla deweloperów oprogramowania przekonwertować strumienie zwykłego tekstu w zarządzanej prawami strumieni i na odwrót.

### <a name="protection-api-use-cases"></a>Przypadki użycia interfejsu API ochrony

- 3d drukowania oprogramowania przy użyciu formatu pliku moralnych opracowywane w danej organizacji. Chcesz użyć MCI do ochrony pliku, dzięki czemu można drukować tylko przez określonych użytkowników. Przy użyciu interfejsu API ochrony, można zastosować ochronę pliku, aby tylko autoryzowani użytkownicy będą mogli otworzyć i/lub drukowania. 

- To rozwiązanie zbierania elektronicznych materiałów dowodowych, która przetwarza skrzynek pocztowych programu Exchange i pliki PST opracowywane w danej organizacji. Aplikacja musi umożliwiać użytkownikowi na odszyfrowanie komunikatów pełni zbierania elektronicznych materiałów dowodowych. Przy użyciu analizatora niestandardowego komunikatu/RPMSG i wystarczająco uprzywilejowanego, można wykorzystać interfejs API usługi RMS, aby odszyfrować zaszyfrowanego pliku, skanowanie zawartości i odrzucić Jeśli poza zakres lub pakietu, jeśli komputer znajduje się w zakresie.

## <a name="policy-api"></a>Zasady interfejsu API

Zasady interfejsu API lub uniwersalnych zasad aparatu (UPE), zapewnia możliwość dla deweloperów oprogramowania, można uzyskać zasad etykietowania dla określonego użytkownika, a następnie "compute" Akcje te etykiety powinno zająć.

Zasady interfejsu API będzie można wykorzystać przede wszystkim przez aplikacje klienckie, gdy tworzenie formantów interfejsu i plik formatu lub gdy jedynym wymaganiem jest, aby uzyskać zasad użytkownika i niekoniecznie bezpośrednio w plikach etykiety. 

### <a name="policy-api-use-cases"></a>Przypadki użycia interfejsów API zasad

- Oprogramowanie do projektowania 3D, który używa formatu pliku własności są opracowywane w danej organizacji. Korzystanie z ochrony informacji firmy Microsoft i chcesz stosować etykiety, natywnie za pośrednictwem aplikacji klientów. Jako inżynier oprogramowania będą używać zasad interfejsu API i formant niestandardowy, aby wyświetlić etykiety, które są dostępne dla tego uwierzytelnionego użytkownika. Po użytkownik wybierze etykietę, możesz wywołać metody akcji obliczeniowych interfejsu API, aby dowiedzieć się dokładnie co powinny być stosowane metadanych, oznaczanie zawartości i ochrony.

- Usługa DLP, która umożliwia klientom Konfigurowanie zasad DLP obowiązujących w portalu witryny Administracja centralna opracowywane w danej organizacji. Masz klienci, którzy korzystania z programu Microsoft Information Protection i chcesz mieć możliwość odczytu lub stosowanie etykiet usługi AIP jako część zasad DLP. Jako inżynier oprogramowania można użyć zasad interfejsu API Aby uzyskać listę etykiet w organizacji klienta, a następnie przeczytaj te etykiety jako część reguły DLP lub zastosować informacji etykiety jako część Akcja reguły.

## <a name="file-api"></a>Interfejs API plików

Interfejs API plików jest klasą abstrakcyjną ochrony i interfejsów API zasad. Zapewnia łatwy w użyciu interfejsów odczytu etykiety z usługi, zastosowanie etykiety do typów zdefiniowanych plików, a także odczytywanie etykiety z tych typów plików. Interfejs API plików będzie używany przez wszystkie usługi lub aplikacji, gdzie uczestniczy obsługiwanego typu plików etykiet muszą być zapisu lub odczytu i zawartość chroniona lub odszyfrować.

### <a name="file-api-use-cases"></a>Przypadki użycia interfejsu API plików

- Możesz teraz inżynier oprogramowania, w instytucji usług finansowych. Chcesz mieć pewność, że dane z aplikacji biznesowych, zwykle eksportowany w formacie programu Excel, są oznaczone etykietami na eksport na podstawie zawartości. Interfejs API plików można Aby wyświetlić listę dostępnych etykiet następnie zastosuj odpowiednią etykietę do obsługiwany format.

- Broker zabezpieczeń dostępu do chmury (CASB) są opracowywane w danej organizacji. Klienci, poproś o możliwość stosowania etykiet MIP dla Microsoft Office i PDF, dokumentów. Następnie umożliwić interfejsu API plików można wyświetlić listę etykiet skonfigurowanych zezwolić klientom do tworzenia zasad, które będzie zastosuj odpowiednią etykietę. Interfejs API, przyjęcie identyfikator etykiety plików będzie zajmiemy się resztą, pliki spełniające kryteria klienta.

- Twoja organizacja udostępnia rozwiązania zapobiegania utracie danych opartych na usługach i/lub CASB, które monitoruje aplikacje SaaS dla działania pliku. Aby ograniczyć ryzyko utraty danych lub zagrożenia, gdzie dane są chronione przez MIP, usługa musi umożliwiać do skanowania zawartości plików chronionych. Za pomocą interfejsu API plików w obsługiwanych formatów, usługa jest użytkownika uprzywilejowanego, można usunąć ochronę, skanowania zawartości, aby ograniczyć lub poufnej zawartości odrzucić wynik w postaci zwykłego tekstu i zastosować reguły usługi do raportu lub eliminowania ryzyka, jeśli znaleziono.
