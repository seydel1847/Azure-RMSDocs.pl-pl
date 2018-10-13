---
title: Chronione czytelnicy PDF Microsoft Information Protection
description: ''
keywords: ''
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/13/2018
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.assetid: aab59e02-930b-4a17-8442-2d5d081fe1a6
ms.reviewer: kartikka
ms.suite: ems
ms.openlocfilehash: ab3d141394a9a042a8a3e15e35d1daffab20ad98
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49170352"
---
# <a name="supported-pdf-readers-for-microsoft-information-protection"></a>Obsługiwane czytniki PDF Microsoft Information Protection

Skorzystaj z poniższych informacji, aby dowiedzieć się więcej na temat dokumentów PDF, które są oznaczone etykietami klasyfikacji i ochrony oraz jak wyświetlać te dokumenty.

Współpraca między firmami Microsoft i Adobe zapewnia bardziej uproszczoną i spójne środowisko dla dokumentów PDF, które zostały sklasyfikowane i opcjonalnie chronione. Ta współpraca zapewnia obsługę integracji z funkcjami macierzystymi programu Adobe Acrobat dzięki rozwiązaniom Microsoft Information Protection, takich jak [usługi Azure Information Protection](../what-is-information-protection.md). 

Integracji z funkcjami macierzystymi ma następujące zalety:

- Możesz wyświetlić dokumenty PDF, które są chronione, ponieważ zawierają one poufne informacje.

- Widać wartości klasyfikacji dla Twojej organizacji etykiety, która została zastosowana do dokumentu.

- Obsługa standardu ISO do szyfrowania plików PDF.
    
    Ten format chronionych plików PDF musi być [włączone przez administratora](client-admin-guide-customizations.md#protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption). Po wykonaniu tej konfiguracji rozszerzenia nazwy pliku pozostaje jako PDF i nie zmienia się na ppdf.

Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [od października, użyj Adobe Acrobat czytnika plików PDF chronionych przez Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Starting-October-use-Adobe-Acrobat-Reader-for-PDFs-protected-by/ba-p/262738)

## <a name="supported-pdf-readers"></a>Obsługiwane czytniki PDF

Następujące czytniki PDF można otwierać chronione pliki PDF, zgodne ze standardem do szyfrowania plików PDF ISO:

|System operacyjny|Obsługiwane czytniki i link pobierania|
|----------------|-----------------------------------|
|Windows 10 i wcześniejszymi wersjami<br />za pomocą Windows 7 z dodatkiem Service Pack 1|Adobe Acrobat Reader (preferowany):<br />-  [Adobe ogólne warunki użytkowania](https://www.adobe.com/legal/terms.html) <br />- [Pobierz wersję zapoznawczą](https://ardownload2.adobe.com/pub/adobe/reader/win/AcrobatDC/misc/MIP_Preview/1900820120/Adobe_MIP_Preview_1900820120.zip) <br /><br /> Przeglądarka usługi Azure Information Protection: [pobierania](https://go.microsoft.com/fwlink/?linkid=838993)<br /><br />Programów Foxit Reader: [pobierania](https://www.foxitsoftware.com/pdf-reader/)|
|Android|Usługa Azure Information Protection app: [pobierania](https://go.microsoft.com/fwlink/?LinkId=325340)|
|iOS|Usługa Azure Information Protection app: [pobierania](https://go.microsoft.com/fwlink/?LinkId=325338)|

### <a name="support-for-previous-formats"></a>Obsługa formatów poprzedniej

Czytelnicy PDF w następnym Obsługa tabel chronionych dokumentów PDF, mających ppdf nazwa extensionand starszych formatów plików, które mają rozszerzenie nazwy pliku PDF.

Obecnie usługa SharePoint Online i lokalnego programu SharePoint na użytek starszego formatu dokumenty PDF w bibliotekach chronioną przez IRM.


|System operacyjny|Obsługiwane czytniki|
|----------------|-----------------------------------|
|Windows 10 i wcześniejszymi wersjami<br />za pomocą Windows 7 z dodatkiem Service Pack 1|Przeglądarka usługi Azure Information Protection<br /><br />Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />Aplikacja do udostępniania usługi RMS|
|Android|Usługa Azure Information Protection app<br /><br />Foxit MobilePDF za pomocą usługi RMS<br /><br />Aplikacja GigaTrust dla systemu Android|
|iOS|Usługa Azure Information Protection app<br /><br />Foxit MobilePDF za pomocą usługi RMS<br /><br />TITUS Docs|
