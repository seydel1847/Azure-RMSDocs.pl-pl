---
title: "Najlepsze rozwiązania w zakresie zabezpieczeń | Microsoft Information Protection"
description: "W przypadku aplikacji z włączoną obsługą usługi RMS optymalnym rozwiązaniem jest zastosowanie najlepszych rozwiązań w zakresie usługi Azure Information Protection."
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.assetid: 4e9f72d5-9e7c-43e1-bb8a-5972dd22dcee
ms.service: information-protection
ms.technology: techgroup-identity
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: 37b91a1b3e0a25f6014198998609d33dcc0979ae
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="security-best-practices-for-azure-information-protection"></a>Najlepsze rozwiązania w zakresie zabezpieczeń dla usługi Azure Information Protection

Zestaw SDK (Software Development Kit) usługi Azure Information Protection (AIP) zapewnia niezawodny system do publikowania i używania wszystkich typów informacji chronionych. Aby system AIP był maksymalnie efektywny, aplikacje z obsługą usługi AIP należy tworzyć przy użyciu najlepszych rozwiązań usługi AIP. Aplikacje z obsługą usługi AIP są pomocne w utrzymaniu bezpieczeństwa danego ekosystemu. Identyfikowanie zagrożeń związanych z bezpieczeństwem i ograniczenie zagrożeń wprowadzanych podczas tworzenia aplikacji pomaga zminimalizować prawdopodobieństwo mniej bezpiecznego wdrażania oprogramowania.

Najlepsze rozwiązania w zakresie wdrażania aplikacji przy użyciu zestawu SDK (Software Development Kit) usługi Azure Information Protection obejmują następujące kategorie propozycji:
- [Modele zagrożeń i ograniczenia](https://msdn.microsoft.com/en-us/library/aa362751.aspx)
- [Zagrożenia bezpieczeństwa](https://msdn.microsoft.com/en-us/library/aa362736.aspx)

Informacje te stanowią uzupełnienie umowy prawnej, którą należy podpisać w celu uzyskania certyfikatów cyfrowych potrzebnych do wdrażania aplikacji przy użyciu zestawu SDK usługi AIP.

## <a name="subjects-not-covered-in-these-topics"></a>Kwestie nieuwzględnione w tych tematach
W tematach poniżej przedstawiono skrótowo kwestie istotne w przypadku podejmowania prób tworzenia środowiska deweloperskiego i bezpiecznych aplikacji:
- **Zarządzanie procesem tworzenia oprogramowania** — zawiera informacje na temat zarządzania konfiguracją, zabezpieczania kodu źródłowego, minimalizowania dostępu do debugowanego kodu i przypisywania priorytetu do usterek. Dla niektórych klientów zapewnienie bezpieczniejszego procesu tworzenia oprogramowania jest sprawą najwyższej wagi. Niektórzy klienci samodzielnie określają cały proces tworzenia aplikacji.
- **Typowe błędy kodowania** — zawiera informacje wyjaśniające, jak unikać przepełnienia buforu. Z ogólnymi zagrożeniami i ograniczeniami można zapoznać się w najnowszej wersji książki „Writing Secure Code” napisanej przez Michaela Howarda i Davida LeBlanca (Microsoft Press, 2002).
- **Metody socjotechniczne** — zawiera informacje o zabezpieczeniach proceduralnych i strukturalnych, które zapewniają ochronę przed złośliwym wykorzystaniem kodu przez deweloperów lub inne osoby w organizacji producenta.
- **Bezpieczeństwo fizyczne** — zawiera informacje na temat blokowania dostępu do bazy kodu i podpisywania certyfikatów.
- **Wdrożenie lub dystrybucja oprogramowania w wersji wstępnej** — zawiera informacje na temat dystrybucji oprogramowania w wersji beta.
- **Zarządzanie siecią** — zawiera informacje o systemach wykrywania nieautoryzowanego dostępu w sieciach fizycznych.

## <a name="threat-models-and-mitigations"></a>Modele zagrożeń i ograniczenia
Posiadacze informacji cyfrowych muszą mieć możliwość oceny środowisk, w których ich zasoby będą odszyfrowywane. Oświadczenie o minimalnych standardach bezpieczeństwa może zapewnić posiadaczom informacji podstawy do zapoznania się z poziomem zabezpieczeń aplikacji, którym powierzają swoje informacje, oraz do oceny tego poziomu.

W niektórych branżach, np. w sektorze rządowym i służbie zdrowia, obowiązują procesy certyfikacji i akredytacji oraz standardy, które mogą dotyczyć produktu. Spełnienie tych minimalnych zaleceń dotyczących bezpieczeństwa nie zastępuje unikatowych wymagań akredytacji klientów. Standardy bezpieczeństwa mają jednak pomóc w przygotowaniu do bieżących i przyszłych wymagań klientów, a każda inwestycja wdrożona na wczesnym etapie cyklu tworzenia będzie korzystna dla aplikacji. Są to zalecenia, a nie formalny program certyfikacji firmy Microsoft.

Istnieje kilka głównych kategorii luk w zabezpieczeniach w systemie usług zarządzania uprawnieniami, np.:
- **Wyciek** — informacje pojawiają się w nieautoryzowanych lokalizacjach.
- **Uszkodzenie** — oprogramowanie lub dane zostają zmodyfikowane w sposób nieautoryzowany.
- **Odmowa** — zasób obliczeniowy nie jest dostępny do użytku.

W tych tematach skoncentrowano się głównie na kwestiach związanych z wyciekiem. Integralność systemu API zależy od jego możliwości stałej ochrony informacji przez umożliwianie dostępu tylko do wyznaczonych jednostek. W tych tematach przedstawiono również kwestie związane z uszkodzeniem danych. Kwestie związane z odmową nie zostały opisane.

Firma Microsoft nie sprawdza spełnienia standardów minimalnych ani nie weryfikuje wyników takich testów. To partner całkowicie odpowiada za zagwarantowanie, że standardy minimalne zostały spełnione. Firma Microsoft udostępnia dwa dodatkowe poziomy zaleceń, które ułatwią ograniczenie typowych zagrożeń. Ogólnie rzecz biorąc, zalecenia te pełnią funkcję dodatkową. Na przykład w kwestii preferowanych zaleceń przyjęto założenie, że spełniono standardy minimalne w odniesieniu do elementów, których to dotyczy (chyba że określono inaczej).

|Poziom standardów|    Opis|
|---|---|
|Standard minimalny|  Zanim aplikacja, która obsługuje informacje chronione przy użyciu usługi AIP, będzie mogła zostać podpisana przy użyciu certyfikatu produkcyjnego z firmy Microsoft, należy ustalić, czy spełnia ona standard minimalny. Partnerzy korzystają zazwyczaj z certyfikatu hierarchii produkcji tylko w momencie ostatecznego wydania oprogramowania, jeśli ich testy wewnętrzne wykazały, że aplikacja spełnia standard minimalny. Spełnienie tego standardu nie jest i nie powinno być interpretowane jako gwarancja bezpieczeństwa ze strony firmy Microsoft. Firma Microsoft nie sprawdza spełnienia standardów minimalnych ani nie weryfikuje wyników takich testów. To partner całkowicie odpowiada za zagwarantowanie, że standard ten został spełniony.|
|Standard zalecany|  Zalecane wytyczne wskazują drogę do lepszych zabezpieczeń aplikacji oraz przedstawiają, jak można rozwijać usługę AIP na skutek wdrażania większej liczby kryteriów zabezpieczeń. Dostawcy mogą próbować wyróżnić swoje aplikacje na tle konkurencji, stosując się do bardziej restrykcyjnych wytycznych dotyczących zabezpieczeń.|
|Standard preferowany|    Jest to obecnie najwyższy poziom kategorii zabezpieczeń. Dostawcy, którzy tworzą aplikacje sprzedawane jako charakteryzujące się bardzo wysokim poziomem zabezpieczeń, powinni dążyć do tego standardu. Aplikacje zgodne z tym standardem są najmniej narażone na ataki.|




## <a name="malicious-software"></a>Złośliwe oprogramowanie
Firma Microsoft określiła wymagane standardy minimalne, jakie musi spełnić aplikacja, aby chronić zawartość przed złośliwym oprogramowaniem.

### <a name="importing-malicious-software-by-using-address-tables"></a>Importowanie złośliwego oprogramowania przy użyciu tabeli adresów
Usługa AIP nie obsługuje modyfikacji kodu w czasie wykonywania ani modyfikacji tabeli adresów importowania (IAT). Tabela adresów importowania jest tworzona dla każdej biblioteki DLL załadowanej w obszarze procesu. Określa adresy wszystkich funkcji, które importuje aplikacja. Jeden z powszechnie występujących ataków polega na modyfikacji wpisów IAT w aplikacji, np. w celu wskazania złośliwego oprogramowania. Po wykryciu ataku tego typu usługa AIP zatrzymuje aplikację.

### <a name="minimum-standard"></a>Standard minimalny
- Nie można zmodyfikować tabeli adresów importowania w procesie aplikacji podczas wykonywania. - Aplikacja określa wiele funkcji wywoływanych w czasie wykonywania przez użycie tabel adresów, a tych nie można zmienić w czasie wykonywania lub po nim. Oznacza to (między innymi), że nie można wykonać profilowania kodu w aplikacji podpisanej przy użyciu certyfikatu produkcyjnego.
- Nie można wywołać funkcji **DebugBreak** z dowolnej biblioteki DLL określonej w manifeście.
- Nie można wywołać funkcji **LoadLibrary** przy użyciu zestawu flag **DONT_RESOLVE_DLL_REFERENCES**. Ta flaga wysyła do modułu ładującego polecenie o pomijaniu wiązania zaimportowanych modułów, tym samym modyfikując tabelę adresów importowania.
- Nie można zmienić opóźnionego ładowania przez wprowadzenie zmian kolejnych lub w czasie wykonywania w przełączniku konsolidatora /DELAYLOAD.
- Nie można zmienić opóźnionego ładowania przez zapewnienie własnej wersji funkcji pomocnika Delayimp.lib.
- Nie można zwolnić modułów, które zostały załadowane z opóźnieniem przez moduły uwierzytelnione, gdy istnieje środowisko AIP.
- Nie można użyć przełącznika konsolidatora **/DELAY:UNLOAD** do włączenia zwalniania opóźnionych modułów.


## <a name="incorrectly-interpreting-license-rights"></a>Niepoprawne interpretowanie praw licencji

Jeśli aplikacja nie interpretuje ani nie wymusza prawidłowo praw wyrażonych w licencji wydania AIP, może dojść do niezamierzonego udostępnienia informacji przez ich posiadacza. Dzieje się tak na przykład wtedy, gdy aplikacja umożliwia użytkownikowi zapisanie niezaszyfrowanych informacji na nowych nośnikach, jeśli licencja publikowania uprawnia tylko do wyświetlania informacji.

System AIP organizuje prawa kilku grup. Więcej informacji można znaleźć w temacie [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](../deploy-use/configure-usage-rights.md).

### <a name="azure-information-protection"></a>Azure Information Protection  
Interfejs API umożliwia użytkownikowi odszyfrowywanie informacji lub nie. Same informacje nie mają żadnej odziedziczonej ochrony. Jeśli użytkownik ma prawo do odszyfrowania informacji, interfejs API to umożliwia i aplikacja odpowiada za zarządzanie tymi informacjami lub ich ochronę po ich zabezpieczeniu. Aplikacja odpowiada za zarządzanie środowiskiem i interfejsem w celu zapobiegania nieautoryzowanemu korzystaniu z informacji — np. wyłącza przyciski **Drukuj** i **Kopiuj**, jeśli licencja przyznaje tylko prawo do odtwarzania. Przy użyciu pakietu testowego należy sprawdzić, czy aplikacja działa poprawnie na wszystkich prawach licencji, które rozpoznaje.

### <a name="minimum-standard"></a>Standard minimalny
- Wdrożenia klienta praw XrML v.1.2 powinny być zgodne z definicjami tych praw opisanymi w specyfikacjach XrML, które są dostępne w witrynie http://www.xrml.org. Wszelkie prawa właściwe dla aplikacji należy określić dla wszystkich obiektów, które są zainteresowane aplikacją.
- Za pomocą pakietu testowego i procesu testowania należy sprawdzić, czy aplikacja jest prawidłowo wykonywana zgodnie z uprawnieniami, które obsługuje, i że nie działa w ramach nieobsługiwanych uprawnień.
- Jeśli tworzysz aplikację publikowania, musisz udostępnić informacje wyjaśniające, które prawa wewnętrzne są, a które nie są obsługiwane przez aplikację publikującą, a także, jak te uprawnienia należy interpretować. Użytkownik końcowy powinien także uzyskać z interfejsu użytkownika wyraźne informacje na temat skutków każdego przypadku przydzielenia lub odmowy dostępu do danej informacji.

- Wszelkie uprawnienia wyodrębnione przez włączenie do nowych uprawnień wdrożonych przez aplikację muszą być mapowane do nowej terminologii. Na przykład nowe uprawnienie o nazwie MENEDŻER powinno obejmować wyodrębnione uprawnienia DRUKUJ, KOPIUJ i EDYTUJ.
W tej chwili brak standardów zalecanych.
W tej chwili brak standardów preferowanych.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]