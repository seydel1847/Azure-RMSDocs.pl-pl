---
title: Jak korzystać ze śledzenia dokumentów | Azure RMS
description: Funkcja śledzenia dokumentów wymaga zrozumienia podstaw zarządzania skojarzonymi metadanymi i rejestracji w usłudze.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 70E10936-7953-49B0-B0DC-A5E7C4772E60
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 1caac2301fd41930856e13b634ead28f7335728f
ms.sourcegitcommit: 93124ef58e471277c7793130f1a82af33dabcea9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2018
ms.locfileid: "27764602"
---
# <a name="how-to-use-document-tracking"></a>Instrukcje: korzystanie ze śledzenia dokumentów

Korzystanie z funkcji śledzenia dokumentów wymaga zrozumienia podstaw zarządzania skojarzonymi metadanymi i rejestracji w usłudze.

## <a name="managing-document-tracking-metadata"></a>Zarządzanie metadanymi śledzenia dokumentów

Każdy system operacyjny obsługujący śledzenie dokumentów charakteryzuje się podobnymi implementacjami. Obejmują one zestaw właściwości reprezentujących metadane, nowy parametr dodany do metod tworzenia zasad użytkowników oraz metodę rejestrowania zasad do śledzenia przy użyciu usługi śledzenia dokumentów.

Z perspektywy operacyjnej śledzenie dokumentów wymaga tylko właściwości **nazwy zawartości** i **typu powiadomienia**.

Sekwencja kroków używanych do konfigurowania śledzenia dokumentów dla danego elementu zawartości to:

-   Utwórz obiekt **metadanych licencji**, a następnie ustaw **nazwę zawartości** i **typ powiadomienia**. Są to jedyne wymagane właściwości.
   - Android — [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx)
   -  iOS — [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx)

Wybierz typ zasad: szablon lub ad hoc:
- W przypadku śledzenia dokumentów na podstawie szablonu utwórz obiekt **zasad użytkownika** przekazujący metadane licencji jako parametr.
  - Android — [UserPolicy.create](https://msdn.microsoft.com/library/dn790887.aspx)
  - iOS — [MSUserPolicy.userPolicyWithTemplateDescriptor](https://msdn.microsoft.com/library/dn790808.aspx)

- W przypadku śledzenia dokumentów ad hoc ustaw właściwość **metadanych licencji** obiektu **deskryptora zasad**.
  - Android — [PolicyDescriptor.setLicenseMetadata](https://msdn.microsoft.com/library/mt573698.aspx)
  - iOS — [MSPolicyDescriptor.licenseMetadata](https://msdn.microsoft.com/library/mt573693.aspx).

    **Uwaga** Obiekt metadanych licencji jest dostępny bezpośrednio tylko podczas procesu konfigurowania śledzenia dokumentów dla danych zasad użytkownika. Po utworzeniu obiektu zasad użytkownika skojarzone metadane licencji nie są dostępne, na przykład zmiana wartości metadanych licencji nie przynosi żadnego efektu.

     

-   Na koniec wywołaj metodę rejestracji platformy w celu śledzenia dokumentów.
  - Android — [UserPolicy.registerForDocTracking asynchronous](https://msdn.microsoft.com/library/mt573699.aspx) lub [UserPolicy.registerForDocTracking synchronous](https://msdn.microsoft.com/library/mt631387.aspx)
  - iOS — [MSUserPolicy.registerForDocTracking](https://msdn.microsoft.com/library/mt573694.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]