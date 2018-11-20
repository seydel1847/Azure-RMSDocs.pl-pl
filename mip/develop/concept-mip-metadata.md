---
title: Pojęcia — etykieta metadane w zestawie SDK MIP
description: Ten artykuł pomoże zrozumieć metadanych, który jest generowany przez zestawu SDK usługi Microsoft Information Protection.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/08/2018
ms.author: tommos
ms.openlocfilehash: 9f9e4768a01d3d82f7b9563cb907533e53c7a228
ms.sourcegitcommit: 03c9d1131177041e320d1bdbbdd92852a0d1d5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52156858"
---
# <a name="microsoft-information-protection-sdk---metadata"></a>Usługi Microsoft Information Protection SDK — metadanych

Zestawu SDK usługi Microsoft Information Protection generuje zestaw metadanych, który ma zostać zastosowany do pliku. Te metadane są reprezentacją etykiety. W tym dokumencie opisano metadanych, które generuje zestawu SDK, aby zastosować do wiadomości e-mail, dokumenty i inne rekordy.

## <a name="labels"></a>Etykiety

Etykiety w zestawu SDK usługi Microsoft Information Protection są stosowane do informacje, aby opisać poufności informacji. Etykieta dane są utrwalane do pliku lub rekordu w zestawie par klucz wartość, które opisują etykiety. Nazwa metadanych jest oparta na następującą strukturę:

`DefinedPrefix_ElementType_GlobalIdentifier_AttributeName`

Gdy stosowane do danych z Microsoft Information Protection, wynik jest:

`MSIP_Label_GUID_Enabled = true`

Identyfikator GUID jest unikatowy identyfikator dla każdej etykiety w organizacji.

## <a name="microsoft-information-protection-sdk-metadata"></a>Metadane zestawu SDK ochrony informacji firmy Microsoft

Zestaw SDK MIP stosuje następujący zestaw metadanych.

| Atrybut | Typ lub wartość                 | Opis                                                                                                                                                                                                                                        | Obowiązkowe |
|-----------|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| **Włączone**   | Wartość PRAWDA lub FAŁSZ                 | Ten atrybut wskazuje, czy Klasyfikacja reprezentowany przez ten zestaw par klucz wartość jest włączona dla elementu danych. Produkty DLP zwykle Sprawdź istnienie tego klucza, aby zidentyfikować etykietę klasyfikacji. | Tak       |
| **Identyfikator witryny**    | GUID                          | Identyfikator dzierżawy usługi Azure Active Directory                                                                                                                                                                                                                   | Tak       |
| **Identyfikator akcji**  | GUID                          | Identyfikator akcji jest zmieniany na każdym razem, gdy ustawiono etykiety. Dzienniki inspekcji będą zawierać actionID starych i nowych, aby umożliwić tworzenie łańcucha z etykietowanie działania w elemencie danych.                                                                                 | Tak       |
| **Metoda**    | Standard, uprzywilejowanego lub automatyczne        | Za pomocą mip::AssignmentMethod                                                                                                                                                                                                                 | Nie        |
| **SetDate**   | Format danych usługi rozszerzonej ISO 8601 | Sygnatura czasowa gdy etykiety została ustawiona.                                                                                                                                                                                                              | Nie        |
| **Nazwa**      | ciąg                        | Unikatowa nazwa etykiety w ramach dzierżawy. Nie musi koniecznie odpowiadać, aby wyświetlić nazwę.                                                                                                                                                              | Nie      |
| **ContentBits** | liczba całkowita | Maska bitów, opisujący typy zawartości, oznaczenie, które stosuje się do pliku. CONTENT_HEADER = 0X1, CONTENT_FOOTER = 0X2, ZNAKU WODNEGO = 0X4
 | Nie |

Po zastosowaniu do pliku, wynik jest podobna do poniższej tabeli.

| Klucz                                                         | Wartość                                |
|-------------------------------------------------------------|--------------------------------------|
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Enabled     | true                                 |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SetDate     | 2018-11-08T21:13:16-0800             |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Method      | Uprzywilejowany                           |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Name        | Poufne                         |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SiteId      | cb46c030-1825-4E81-a295-151c039dbf02 |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ContentBits | 2                                    |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ActionId    | 88124cf5-1340-457d-90e1-0000a9427c99 |

## <a name="extending-metadata-with-custom-attributes"></a>Rozszerzanie metadanych za pomocą atrybutów niestandardowych

Niestandardowych metadanych może być dołączane za pomocą pliku i zasady interfejsu API. Atrybuty niestandardowe, musisz utrzymywać base `MSIP_Label_GUID` prefiks. 

Na przykład aplikacji napisanych przez firmę Contoso Corporation należy zastosować metadanych wskazująca, których system wygenerowany plik etykietami. Aplikacja mogła tworzyć nowe etykiety, prefiksem `MSIP_Label_GUID`. Nazwa dostawcy oprogramowania i atrybutu niestandardowego są dołączane do długości prefiksu do wygenerowania niestandardowych metadanych.

```
MSIP_Label_f048e7b8-f3aa-4857-bf32-a317f4bc3f29_ContosoCorp_GeneratedBy = HRReportingSystem
```

> [!Note]
> Aby zachować zgodność w typowych aplikacjach, maksymalna długość dla każdego klucza i wartości to 255 znaków.

## <a name="versioning"></a>Przechowywanie wersji

Wraz z upływem czasu atrybuty będzie zastosowane, modyfikować lub wycofane. Oczekuje się, że aplikacje będą nadal obsługiwać te starych lub wycofane atrybutów, jako element zastępujący wartości w całym przedsiębiorstwie mogą zająć lata.

Podczas zastępowania atrybutu za pomocą nowszej wersji, sufiks wersja powinna być dodana do atrybutu:

`MSIP_Label_GUID_EnabledV2 = True | False | Condition`

## <a name="email"></a>Poczta e-mail

Metadane, poczta e-mail zachowuje, parę klucza i wartości formatowania podobny do dokumentów. Główną różnicą jest to, że wszystkie atrybuty są serializowane w nagłówku jedną wiadomość e-mail o nazwie **MSIP_Labels**. Pary klucz/wartość są rozdzielane znakami średnika i odstępem i umieszczone w nowym nagłówku.

Przy użyciu metadanych przykładowe powyżej:

```
MSIP_Labels: MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Enabled=true; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SetDate=2018-11-08T21:13:16-0800; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Method=Privileged; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Name=Confidential; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SiteId=cb46c030-1825-4e81-a295-151c039dbf02; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ContentBits=2; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ActionId=88124cf5-1340-457d-90e1-0000a9427c99
```
