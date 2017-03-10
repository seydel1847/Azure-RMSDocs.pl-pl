---
title: "Obsługiwane formaty plików | Azure RMS"
description: "Bieżąca wersja interfejsu API plików obsługuje natywną ochronę plików pakietu MS Office i plików PDF oraz ochronę PFile dla wszystkich pozostałych formatów plików."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: EC831494-7F2C-4C70-9063-B02CDDEA14EE
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 780a2a4dc96c602cabcec69bffd4b8584097ca7b
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="supported-file-formats"></a>Obsługiwane formaty plików

Interfejs API plików obsługuje formaty natywne i PFile.

## <a name="supported-file-formats"></a>Obsługiwane formaty plików

Bieżąca wersja interfejsu API plików obsługuje natywną ochronę plików pakietu Microsoft Office i plików PDF (Portable Document File) oraz ochronę PFile dla wszystkich pozostałych formatów plików. Dla plików PDF można opcjonalnie stosować ochronę PFile.

-   **Ochrona natywna**. W przypadku ochrony natywnej plik jest szyfrowany do formatu pliku usługi AD RMS opartego na jego typie MIME (rozszerzeniu nazwy pliku). Pliki chronione natywnie przy użyciu interfejsu API plików są zgodne z formatem oczekiwanym przez aplikacje z obsługą usługi AD RMS korzystające z ochrony natywnej (na przykład pakiet Office 2013, pakiet Office 2010 i czytnik plików PDF FoxIt). Ochrona natywna jest obsługiwana tylko w przypadku plików pakietu Office, plików PDF i niektórych innych typów plików. Aby uzyskać więcej informacji na temat typów plików, które obsługują ochronę natywną, zobacz [Konfiguracja interfejsu API plików](file-api-configuration.md).
-   **Ochrona PFile**. W przypadku ochrony PFile pliki są szyfrowane przy użyciu formatu AD RMS Protected File (PFile). Plik jest szyfrowany do pliku z rozszerzeniem pfile. Ochrona PFile jest obsługiwana przez wszystkie typy plików z wyjątkiem plików pakietu Office.

Administratorzy mogą ustawić klucze rejestru, aby określić, czy pliki mają być chronione na podstawie ich rozszerzenia nazwy pliku i jak te pliki mają być chronione. Aby uzyskać więcej informacji na temat konfigurowania ochrony plików podczas korzystania z interfejsu API plików, zobacz [Konfiguracja interfejsu API plików](file-api-configuration.md).

## <a name="related-topics"></a>Tematy pokrewne

* [Uwagi dla deweloperów](developer-notes.md)
* [Konfiguracja interfejsu API plików](file-api-configuration.md)
 
[!INCLUDE[Commenting house rules](../includes/houserules.md)]