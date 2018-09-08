---
title: Terminologia dla deweloperów dotycząca usługi AIP | Dokumentacja firmy Microsoft
description: Zbiór definicji dotyczących usług Rights Management Services.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: adb1f868-0da7-431b-83d1-86f41c2da4ae
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8ddf0b8722111ff2cd4c433337c4e0c930b02009
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151561"
---
# <a name="terms"></a>Terminologia

Zbiór definicji dotyczących usług Azure Information Protection.

**Przestarzały algorytm**  
Modalne ustawienie implementujące starszy schemat ochrony zawartości, w szczególności odnoszący się do trybu szyfrowania ECB. W tym zestawie SDK to ustawienie umożliwia wygenerowanie licencji zgodnych z biblioteką MSDRM używaną przez [zestaw AD Rights Management Services SDK](https://msdn.microsoft.com/library/windows/desktop/cc530379.aspx).

To ustawienie może spowodować, że aplikacja będzie chronić zawartość w sposób, który nie jest zgodny ze standardami klientów dotyczącymi ochrony zawartości.

To ustawienie uniemożliwi aplikacji korzystanie z rozszerzeń kryptograficznych dodanych do zestawu Microsoft Rights Management SDK 3.0 lub nowszego.

**Format Microsoft Protected File**

Domyślny format pliku (zwany także formatem PFile) dla usług AD RMS, pełniący funkcję standardu dla aplikacji z obsługą usług RMS.

Format PFile jest niewidoczny dla dewelopera aplikacji, ponieważ jest wbudowany w zestaw Microsoft Rights Management SDK 4.2.

