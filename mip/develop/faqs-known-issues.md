---
title: Często zadawane pytania i znane problemy — zestaw SDK usługi Microsoft Information projekcji.
description: Często zadawane pytania ochronę informacji firmy Microsoft (MIP) zestawu SDK i wskazówki dotyczące rozwiązywania problemów dotyczących problemów i błędów.
author: BryanLa
ms.service: information-protection
ms.topic: troubleshooting
ms.date: 10/19/2018
ms.author: bryanla
ms.openlocfilehash: f213b31d9b0e41ea9c1e076055a90e9f62b31b3a
ms.sourcegitcommit: fa0be701b85b1fba5e75428714bb4525dd739a93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223929"
---
# <a name="microsoft-information-protection-mip-sdk-faqs-and-issues"></a>Często zadawane pytania ochronę informacji firmy Microsoft (MIP) zestawu SDK i problemów

Ten artykuł zawiera odpowiedzi na często zadawane pytania (FAQ) i wskazówki dotyczące rozwiązywania problemów, znanych problemów i typowych błędów.

## <a name="frequently-asked-questions"></a>Często zadawane pytania 

### <a name="question-which-platforms-are-supported-by-the-mip-sdk"></a>Pytanie: które platformy są obsługiwane przez zestaw SDK MIP?

Zestaw SDK MIP jest obsługiwane na następujących platformach:

[!INCLUDE [MIP SDK platform support](../include/mip-sdk-platform-support.md)]

### <a name="question-how-does-the-sdk-handle-strings-and-what-string-type-should-i-be-using-in-my-code"></a>Pytanie: jakie ciągi dojście do zestawu SDK i jakiego typu ciąg powinno użyć w mojej sytuacji w Mój kod?

Zestaw SDK ma być używany dla wielu platform i używa [UTF-8 (Unicode Transformation Format - 8-bitowa)](https://wikipedia.org/wiki/UTF-8) obsługi ciągu. Dokładne wskazówki zależy od używanej platformy:

| Platforma | Wskazówki |
|-|-|
| Windows natywne | Dla klientów z zestawu SDK języka C++, wpisz biblioteki standardowej języka C++ [ `std::string` ](https://wikipedia.org/wiki/C%2B%2B_string_handling) służy do przekazywania ciągów znaków do/z funkcji interfejsu API. Konwersja z UTF-8 odbywa się wewnętrznie przez zestaw SDK MIP. Gdy `std::string` jest zwracana z interfejsu API, należy oczekiwać kodowania UTF-8 i zarządzać w związku z tym, jeśli Konwersja ciągu. W niektórych przypadkach zostanie zwrócony ciąg jako część `uint8_t` vector (na przykład licencją publikowania (PL)), ale powinien być traktowany jako nieprzezroczysty obiekt blob.<br><br>Aby uzyskać więcej informacji i przykładów zobacz:<ul><li>[Funkcja Procedura WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte) Aby uzyskać pomoc dotyczącą konwersji ciągów znaków dwubajtowych do wielobajtowego, takich jak UTF-8.<li>Następujące przykładowe pliki zawarte w [zestaw SDK do pobrania](setup-configure-mip.md#configure-your-client-workstation):<ul><li>Przykładowy ciąg funkcje narzędziowe w `file\samples\common\string_utils.cpp`, do konwersji do i z niej ciągi szerokie UTF-8.<li>Implementacja `wmain(int argc, wchar_t *argv[])` w `file\samples\file\main.cpp`, który używa tych funkcji konwersji ciągu.</li></ul></ul>|
| .NET | Dla zestawu .NET SDK klientów wszystkie ciągi używane, kodowanie domyślne UTF-16 i jest potrzebne nie specjalne konwersji. Konwersja z UTF-16 odbywa się wewnętrznie przez zestaw SDK MIP. |
| Inne platformy | Inne platformy obsługiwane przez zestaw SDK MIP zapewniają natywnej obsługi programu UTF-8. |

## <a name="issues-and-errors-reference"></a>Odwołanie do problemów i błędów

### <a name="error-file-format-not-supported"></a>Błąd: "format pliku nie jest obsługiwany"  

| Error | Rozwiązanie |
|-|-|
|*Nieobsługiwany format pliku*| Ten wyjątek jest wynikiem próby ochrony lub pliku PDF, który został podpisany cyfrowo etykiety lub chroniony hasłem. Zobacz [nową obsługę szyfrowania plików PDF z Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757) Aby uzyskać więcej informacji na temat ochrony i etykietowania plików PDF.|

### <a name="error-failed-to-parse-the-acquired-compliance-policy"></a>Błąd: "nie można przeanalizować zasad nabywane zgodności"  

Pobrać zestaw SDK MIP i uruchomiono przykładowych aplikacji. Spróbuj wyświetlić listę wszystkich etykiet za pomocą przykładowych plików, ale występuje następujący błąd:

| Error | Rozwiązanie |
|-|-|
|*Wystąpił problem: nie można przeanalizować uzyskano zasad zgodności. Nie powiodło się: [klasy mip::CompliancePolicyParserException] tagów nie można odnaleźć: zasady, element NodeType: 15, nazwa: nie znaleziono nazwy, wartość:, elementów nadrzędnych: <SyncFile> <Content>, correlationId: [34668a40-blll-4ef8-b2af-00005aa674z9]*| Oznacza to, że etykiety nie migrację z usługi Azure Information Protection, do ujednoliconego środowiska etykietowania. Postępuj zgodnie z [jak przeprowadzić migrację etykiety usługi Azure Information Protection do Centrum zgodności i zabezpieczeń usługi Office 365](/azure/information-protection/configure-policy-migrate-labels) migracji etykiet, następnie utworzyć zasadę etykiety w Centrum zgodności i zabezpieczeń usługi Office 365. Po zakończeniu tej operacji plik zostanie pomyślnie uruchomiona.|
