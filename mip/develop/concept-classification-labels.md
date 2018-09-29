---
title: Pojęcia — etykiety klasyfikacji
description: Ten artykuł pomoże w zrozumieniu sposobu używania etykiet klasyfikacji danych.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a32193194b9806dbab5066db27192265566ca44f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446655"
---
# <a name="microsoft-information-protection-sdk---classification-label-concepts"></a>Usługi Microsoft Information Protection SDK — pojęcia etykietę klasyfikacji

W ramach strategii ochrony danych kompleksowe organizacje powinny zaimplementować systemem klasyfikacji danych, który przedstawia poziomy poufności danych w organizacji, a następnie atrybuty dokumentu są mapowane na te klasyfikacje.

Atrybuty powiązane z klasyfikacją zwykle obejmują **ryzyka** dla organizacji, jeśli tego dokumentu lub dane powinny zostać utracone lub widzianych przez podmioty. W znanych systemie klasyfikacji dla instytucji rządowych Stanów Zjednoczonych istnieją trzy poziomy klasyfikacji. Każdy ma definicji który opisuje stosowania tej klasyfikacji:

* **Najważniejsze klucz tajny**: stosuje się do informacji, nieuprawnionym ujawnieniem, z których można oczekiwać zaszkodzić wyjątkowo duże bezpieczeństwo narodowe, która może określić lub opisać oryginalnego urzędu klasyfikacji .
* **Klucz tajny**: stosuje się do informacji, nieuprawnionym ujawnieniem, z których można oczekiwać poważnie zaszkodzić bezpieczeństwo narodowe, która może określić lub opisać oryginalnego urzędu klasyfikacji.
* **Poufne**: stosuje się do informacji, nieuprawnionym ujawnieniem, z których można oczekiwać zaszkodzić bezpieczeństwo narodowe, która może określić lub opisać oryginalnego urzędu klasyfikacji.
* **Niesklasyfikowane**: to nie jest w rzeczywistości klasyfikacji, ale raczej braku jednego z trzech powyższych.

Aby zdefiniować listę podobny do wartości domyślnych w usłudze Azure Information Protection, w komercyjnej lub w sektorze prywatnym aplikacji firma Microsoft przy użyciu wartości pieniężnych dołączone.

* **Wysoce poufne**: stosuje się do informacji, nieuprawnionym ujawnieniem, z których można oczekiwać spowodować szkody większą niż USD $1 M.
* **Poufne**: stosuje się do informacji, nieuprawnionym ujawnieniem, z których można oczekiwać spowodować szkody większa niż USD zdobycia 100 tysięcy.
* **Ogólne**: stosuje się do informacji, nieuprawnionym ujawnieniem, z których można oczekiwać spowodować niewielkie mierzalne szkody.
* **Publiczne**: stosuje się do informacji przeznaczonych do użytku publicznego, zewnętrznych. 
* **Niebiznesowe**: stosuje się do informacji, które nie jest powiązana z działalności firmy, bezpośrednie lub pośrednie.

Każda Klasyfikacja opisuje ryzyko dla firmy w przypadku nieuprawnionym ujawnieniem tych informacji. Po określeniu tych klasyfikacji i warunków, powinny zostać określone atrybuty pomaga zrozumieć, którą klasyfikację należy zastosować właścicielom danych.

## <a name="labeling"></a>Etykietowania

Czynność kojarzenie klasyfikację danych przy użyciu zestawu danych jest określany jako **etykietowania**. Ponieważ zestaw SDK MIP jest obsługa stosowania klasyfikacji **etykiety** do dokumentów, firma Microsoft nie można znaleźć klasyfikacji, ale zamiast etykiet. Użytkownik lub proces ma już **sklasyfikowane** dane na podstawie wiedzy z informacji: MIP zestaw SDK będzie następnie **etykiety** informacje.

## <a name="labels-in-the-mip-sdk"></a>Etykiety w zestawie SDK MIP

Etykiety są podstawowym składnikiem MIP SDK. Etykiety dysków, tagowanie, ochrony i oznaczanie zawartości wszystkich dokumentów korzystały z zestawu SDK. Zestaw SDK wykonywać następujące czynności:

* Zastosowanie etykiety do dokumentów
* Przeczytaj istniejących etykiet w dokumentach
* Zmień istniejące etykiety i upoważnienie uzasadnienie, jeśli jest to wymagane przez zasady
* Usunięcie etykiety z dokumentu

Etykieta będzie miała zastosowanie ochrony i oznaczanie zawartości na podstawie konfiguracji etykiety zdefiniowane przez administratorów w Centrum zabezpieczeń i zgodności. 

## <a name="miplabel-vs-mipcontentlabel"></a>MIP::Label a mip::ContentLabel

Dwa rodzaje etykiety istnieje w zestawie SDK MIP. `Label` i `ContentLabel`.

* Etykieta: Etykieta, które mogą być stosowane przez użytkownika lub procesu, zgodnie z definicją w organizacji zasad.
* ContentLabel: Etykieta, która już istnieje dla dokumentu lub informacji. Go mogą być odczytu, zaktualizowane lub usunięte. 

Innymi słowy `ContentLabel` jest `Label` która została zastosowana do informacji.

## <a name="metadata"></a>Metadane

Zestaw SDK również obsługiwane dodawanie dodatkowe metadane do dokumentów w postaci par klucz/wartość. Jeśli Twoja organizacja ma podrzędną klasyfikacje lub tagi, które opisują informacje w sposób bardziej szczegółowe, zestaw SDK może służyć do zastosowania tych metadanych.

## <a name="next-steps"></a>Kolejne kroki

Aby uzyskać szczegółowe informacje na temat systemu klasyfikacji dla instytucji rządowych Stanów Zjednoczonych, zobacz https://www.gpo.gov/fdsys/pkg/FR-2010-01-05/html/E9-31418.htm.
