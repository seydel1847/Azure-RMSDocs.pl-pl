---
title: Najlepsze rozwiązania dotyczące Information Protection
description: Aplikacje z obsługą usług RMS najlepiej są tworzone przy użyciu najlepszych rozwiązań Information Protection.
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 12/13/2018
ms.topic: conceptual
ms.assetid: 4e9f72d5-9e7c-43e1-bb8a-5972dd22dcee
ms.service: information-protection
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: 3b22a8723a232cd05349a19987686c25dc5f320f
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54070302"
---
# <a name="security-best-practices-for-information-protection"></a>Najlepsze rozwiązania dotyczące Information Protection

Informacje o ochronie Software Development Kit (SDK) zapewnia niezawodny system do publikowania i używania wszystkich typów informacji chronionych. Aby ułatwić systemu można maksymalnie efektywny, aplikacje korzystające z ochrony informacji muszą zostać skompilowane przy użyciu najlepszych rozwiązań. Aplikacje wspólną odpowiedzialność w ułatwienia zapewniania bezpieczeństwa danego ekosystemu. Identyfikowanie zagrożeń związanych z bezpieczeństwem i ograniczenie zagrożeń wprowadzanych podczas tworzenia aplikacji pomaga zminimalizować prawdopodobieństwo mniej bezpiecznego wdrażania oprogramowania.

Informacje te stanowią uzupełnienie umowy prawnej, którą należy podpisać do uzyskania certyfikatów cyfrowych dla aplikacji za pomocą zestawów SDK.

## <a name="subjects-not-covered"></a>Kwestie nieuwzględnione

Mimo że istotne zagadnienia dotyczące tworzenia środowiska deweloperskiego i bezpiecznych aplikacji znajdują się w następujących tematach, są one poza zakres tego artykułu:

- **Zarządzanie procesem tworzenia oprogramowania** — Zarządzanie konfiguracją, zabezpieczania kodu źródłowego, minimalizowania dostępu do debugowanego kodu i przypisywania priorytetu do usterek. Dla niektórych klientów bezpieczniejszego procesu tworzenia oprogramowania jest sprawą do nich. Niektórzy klienci samodzielnie określają cały proces tworzenia aplikacji.
- **Typowe błędy kodowania** — informacje w celu uniknięcia przepełnienia buforu. Z ogólnymi zagrożeniami i ograniczeniami można zapoznać się w najnowszej wersji książki „Writing Secure Code” napisanej przez Michaela Howarda i Davida LeBlanca (Microsoft Press, 2002).
- **Metody socjotechniczne** — zawiera informacje o zabezpieczeniach proceduralnych i strukturalnych zabezpieczenia, aby lepiej chronić kodu na podstawie wykorzystania przez deweloperów lub inne osoby w organizacji producenta.
- **Bezpieczeństwo fizyczne** — zawiera informacje na temat blokowania dostępu do bazy kodu i podpisywania certyfikatów.
- **Wdrożenie lub dystrybucja oprogramowania w wersji wstępnej** — zawiera informacje na temat dystrybucji oprogramowania w wersji beta.
- **Zarządzanie siecią** — zawiera informacje o systemach wykrywania nieautoryzowanego dostępu w sieciach fizycznych.

## <a name="threat-models-and-mitigations"></a>Modele zagrożeń i ograniczenia

Posiadacze informacji cyfrowych muszą możliwość oceny środowisk, w których ich zasoby będą odszyfrowywane. Oświadczenie o minimalnych standardach bezpieczeństwa zapewnia posiadacze informacji przy użyciu framework wykrywania i oceny poziomu zabezpieczeń aplikacji.

W niektórych branżach, np. w sektorze rządowym i służbie zdrowia, obowiązują procesy certyfikacji i akredytacji oraz standardy, które mogą dotyczyć produktu. Spełnienie tych minimalnych zaleceń dotyczących bezpieczeństwa nie zastępuje unikatowych wymagań akredytacji klientów. Standardy bezpieczeństwa mają jednak pomóc w przygotowaniu do bieżących i przyszłych wymagań klientów, a każda inwestycja wdrożona na wczesnym etapie cyklu tworzenia będzie korzystna dla aplikacji. Te wytyczne są zalecenia, a nie formalny program certyfikacji firmy Microsoft.

Istnieje kilka głównych kategorii luk w zabezpieczeniach w systemie usług zarządzania uprawnieniami, np.:

- **Wyciek** — informacje pojawiają się w nieautoryzowanych lokalizacjach.
- **Uszkodzenie** — oprogramowanie lub dane zostają zmodyfikowane w sposób nieautoryzowany.
- **Odmowa** — zasób obliczeniowy nie jest dostępny do użytku.

W tych tematach skoncentrowano się głównie na kwestiach związanych z wyciekiem. Integralność systemu API zależy od jego możliwości wraz z upływem czasu, aby chronić informacje, włączenie dostępu tylko do wyznaczonych jednostek. W tych tematach przedstawiono również kwestie związane z uszkodzeniem danych. Kwestie związane z odmową nie są uwzględnione.

Firma Microsoft nie testu lub przejrzeć wyniki testów związane z spełnienie tego standardu. Partner ten jest odpowiedzialny za zapewnienie, że standardy minimalne zostały spełnione. Firma Microsoft udostępnia dwa dodatkowe poziomy zaleceń, które ułatwią ograniczenie typowych zagrożeń. Ogólnie rzecz biorąc, te sugestie dotyczą dodatku. Na przykład kwestii preferowanych zaleceń przyjęto założenie, że spełniono standardy minimalne, gdy to stosowne, chyba że określono inaczej.

|Poziom standardów|Opis|
|---|---|
|Standard minimalny| Aplikacja obsługuje informacje chronione muszą spełniać standard minimalny, zanim może być podpisana przy użyciu certyfikatu produkcyjnego firmy Microsoft. Partnerzy korzystają zazwyczaj z certyfikatu hierarchii produkcji w momencie ostatecznego wydania oprogramowania. Partner własne wewnętrzne testy są używane do weryfikowania, czy aplikacja spełnia standard minimalny. Spełnienie tego standardu nie jest i nie powinny być interpretowane jako gwarancja bezpieczeństwa ze przez firmę Microsoft. Firma Microsoft nie testu lub przejrzeć wyniki testów związane z spełnienie tego standardu. Partner ten jest odpowiedzialny za zapewnienie, że ten został spełniony.|
|Standard zalecany| Zalecane wytyczne zarówno wykresu ścieżki do lepszych zabezpieczeń aplikacji i prezentują sposób zestaw SDK może się rozwijać, zaimplementowanego większej liczby kryteriów zabezpieczeń. Dostawców może zróżnicować swoich aplikacji, stosując się do bardziej restrykcyjnych wytycznych dotyczących zabezpieczeń.|
|Standard preferowany| Ta warstwa standardowa to najwyższy poziom kategorii zabezpieczeń obecnie zdefiniowany. Dostawcy, którzy tworzą aplikacje sprzedawane jako charakteryzujące się bardzo wysokim poziomem zabezpieczeń, powinni dążyć do tego standardu. Aplikacje zgodne z tym standardem są najmniej narażone na ataki.|

## <a name="malicious-software"></a>Złośliwe oprogramowanie

Firma Microsoft określiła wymagane standardy minimalne, jakie musi spełnić aplikacja, aby chronić zawartość przed złośliwym oprogramowaniem.

### <a name="importing-malicious-software-by-using-address-tables"></a>Importowanie złośliwego oprogramowania przy użyciu tabeli adresów

Zestaw SDK information protection nie obsługuje modyfikacji kodu w czasie wykonywania ani modyfikacji tabeli adresów importowania (IAT). Tabela adresów importowania jest tworzona dla każdej biblioteki DLL załadowanej w obszarze procesu. Określa adresy wszystkich funkcji, które importuje aplikacja. Jeden z powszechnie występujących ataków polega na modyfikacji wpisów IAT w aplikacji, np. w celu wskazania złośliwego oprogramowania. Zestaw SDK zatrzymuje aplikację po wykryciu ataku tego typu.

### <a name="minimum-standard"></a>Standard minimalny

- Nie można zmodyfikować tabeli adresów importowania w procesie aplikacji podczas wykonywania. Aplikacja określa wiele funkcji wywoływanych w czasie wykonywania przez użycie tabel adresów. Nie można zmienić tych tabel, w trakcie lub po czasie wykonywania. Między innymi ograniczenie to oznacza, że nie można wykonać profilowania kodu w aplikacji podpisanej przy użyciu certyfikatu produkcyjnego.
- Nie można wywołać **DebugBreak** funkcji z dowolnej biblioteki DLL określonej w manifeście.
- Nie można wywołać **LoadLibrary** z **DONT_RESOLVE_DLL_REFERENCES** Flaga. Ta flaga wysyła do modułu ładującego polecenie o pomijaniu wiązania zaimportowanych modułów, tym samym modyfikując tabelę adresów importowania.
- Nie można zmienić opóźnionego ładowania, wprowadzenie zmian kolejnych lub czasu wykonywania w przełączniku konsolidatora/delayload.
- Nie można zmienić opóźnionego ładowania przez zapewnienie własnej wersji funkcji pomocnika Delayimp.lib.
- Nie można zwolnić modułów, które są załadowane z opóźnieniem przez moduły uwierzytelnione, gdy istnieje zestaw SDK środowiska ochrony informacji.
- Nie można użyć **`/DELAY:UNLOAD`** przełącznika konsolidatora do włączenia zwalniania opóźnionych modułów.

## <a name="incorrectly-interpreting-license-rights"></a>Niepoprawne interpretowanie praw licencji

Jeśli aplikacja nie poprawnie interpretować i wymuszanie praw wyrażonych w licencji publikowania zestawu SDK, użytkownik może udostępnić informacje w sposób, który nie ma właściciela informacji. Na przykład, gdy aplikacja umożliwia użytkownikowi zapisanie niezaszyfrowanych informacji na nowych nośnikach, jeśli licencja publikowania przyznaje tylko prawo do wyświetlania informacji.

### <a name="azure-information-protection-aip"></a>Usługa Azure Information Protection (AIP)

Systemu ochrony informacji organizuje prawa do kilku grup. Więcej informacji można znaleźć w temacie [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](../configure-usage-rights.md).

AIP umożliwia użytkownikowi odszyfrowywanie informacji lub nie. Informacje nie mają żadnej odziedziczonej ochrony. Jeśli użytkownik ma prawo do odszyfrowania, interfejs API to umożliwia. Aplikacja jest odpowiedzialny za ochronę informacji po zabezpieczeniu lub zarządzania nimi. Aplikacja jest odpowiedzialny za zarządzanie środowiskiem i interfejsem w celu zapobiegania nieautoryzowanemu korzystaniu z informacji. Na przykład wyłączenie **drukowania** i **kopiowania** przyciski, jeśli licencja przyznaje tylko prawo WIDOKU. Przy użyciu pakietu testowego należy sprawdzić, czy aplikacja działa poprawnie na wszystkich prawach licencji, które rozpoznaje.

### <a name="minimum-standard"></a>Standard minimalny

- Wdrożenia klienta praw XrML v.1.2 powinny być zgodne z definicjami tych praw, zgodnie z opisem w specyfikacjach XrML, które są dostępne w witrynie (http://www.xrml.org). Wszelkie prawa właściwe dla aplikacji należy określić dla wszystkich obiektów, które są zainteresowane aplikacją.
- Proces testowania suite i testowania należy sprawdzić, czy aplikacja jest prawidłowo wykonywana zgodnie z uprawnieniami, obsługiwanych przez aplikację. On również sprawdzić, że **nie** działają w ramach nieobsługiwanych uprawnień.
- Jeśli tworzysz aplikację publikowania, musisz upewnić informacje wyjaśniające, prawa wewnętrzne używane. W tym te, które są, a nie są obsługiwane przez aplikację publikującą i jak interpretować te uprawnienia. Użytkownik końcowy powinien także uzyskać z interfejsu użytkownika wyraźne informacje na temat skutków każdego przypadku przydzielenia lub odmowy dostępu do danej informacji.
- Wszelkie prawa, które zostały wyabstrahowane przez włączenie do nowych uprawnień wdrożonych przez aplikację muszą być zamapowane do nowej terminologii. Na przykład nowe uprawnienie o nazwie MENEDŻER powinno obejmować wyodrębnione uprawnienia DRUKUJ, KOPIUJ i EDYTUJ.

### <a name="recommended-standard"></a>Standard zalecany

Brak w tej chwili.

### <a name="preferred-standard"></a>Standard preferowany

Brak w tej chwili.

## <a name="next-steps"></a>Następne kroki

Najlepsze rozwiązania dotyczące wdrażania aplikacji przy użyciu zestawu SDK usługi AIP zawierają następujące artykuły:

- [Modele zagrożeń i ograniczenia](https://msdn.microsoft.com/library/aa362751.aspx)
- [Zagrożenia bezpieczeństwa](https://msdn.microsoft.com/library/aa362736.aspx)
