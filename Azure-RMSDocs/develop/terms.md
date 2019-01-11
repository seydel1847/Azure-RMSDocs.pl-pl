---
title: Terminologia dla deweloperów dotycząca usługi AIP | Dokumentacja firmy Microsoft
description: Zbiór definicji dotyczących usług Rights Management Services.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: adb1f868-0da7-431b-83d1-86f41c2da4ae
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 1cf0080c899bc3095ff036f651c1f31f63b70ffe
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071385"
---
# <a name="terms"></a>Terminologia

Zbiór definicji dotyczących usług Azure Information Protection.

**Przestarzały algorytm**  
Modalne ustawienie implementujące starszy schemat ochrony zawartości, w szczególności odnoszący się do trybu szyfrowania ECB. W tym zestawie SDK to ustawienie umożliwia wygenerowanie licencji zgodnych z biblioteką MSDRM używaną przez [zestaw AD Rights Management Services SDK](https://msdn.microsoft.com/library/windows/desktop/cc530379.aspx).

To ustawienie może spowodować, że aplikacja będzie chronić zawartość w sposób, który nie jest zgodny ze standardami klientów dotyczącymi ochrony zawartości.

To ustawienie uniemożliwi aplikacji korzystanie z rozszerzeń kryptograficznych dodanych do wersji Microsoft Rights Management SDK 3.0 lub nowszej.

**Format Microsoft Protected File**

Domyślny format pliku (zwany także formatem PFile) dla usług AD RMS, pełniący funkcję standardu dla aplikacji z obsługą usług RMS.

PFile format jest niewidoczny dla dewelopera aplikacji, ponieważ jest wbudowany w sposób, w jaki zaprojektowano Microsoft Rights Management SDK 4.2.

