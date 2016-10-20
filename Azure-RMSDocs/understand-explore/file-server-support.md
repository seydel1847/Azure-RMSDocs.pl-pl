---
title: "Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików | Azure Information Protection"
description: "Informacje dotyczące sposobu używania infrastruktury klasyfikacji plików systemu Windows Server z usługami Azure RMS podczas wdrażania łącznika usług RMS w celu automatycznej ochrony dokumentów pakietu Office."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8fdad425-5daf-4ce1-822f-9d2fb0b87df1
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2c0f3b58a2f1b5233c262bb67cc4a485557ba997
ms.openlocfilehash: 64c718f91d1d2f516bcac6dd949eef5ef379a306


---


# Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików

>*Dotyczy: Azure Information Protection, Office 365*


Podczas konfigurowania używania infrastruktury klasyfikacji plików w systemie Windows Server funkcja Menedżer zasobów serwera plików może przeskanować lokalne pliki i ustalić, czy zawierają one poufne dane. Pliki spełniające to kryterium są oznaczane za pomocą właściwości klasyfikacji zdefiniowanych przez administratora. W ramach infrastruktury klasyfikacji plików można następnie automatycznie podjąć odpowiednie działania zgodnie z klasyfikacją. Jedno z tych działań obejmuje zastosowanie ochrony informacji za pomocą usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] oraz wdrożenie łącznika usługi Rights Management (nazywanego także łącznikiem usługi RMS). Dzięki temu pliki pakietu Office są automatycznie chronione przez usługę Azure RMS.

Aby chronić wszystkie typy plików, nie należy używać łącznika usługi RMS. Zamiast tego należy uruchomić skrypt programu Windows PowerShell przy użyciu poleceń cmdlet udostępnianych przez narzędzie [RMS Protection Tool](https://www.microsoft.com/en-us/download/details.aspx?id=47256).

Zasady klasyfikacji są w pełni konfigurowalne i wysoce rozszerzalne, dzięki czemu można zapobiec potencjalnym wyciekom danych pochodzącym od nieautoryzowanych i autoryzowanych użytkowników. Możliwe jest nawet zmniejszenie ryzyka wycieku danych pochodzącego od administratorów sieci, ponieważ można skonfigurować zasady, które nie wymagają, aby mieli oni dostęp do plików.

Aby uzyskać instrukcje dotyczące wdrażania i konfigurowania łącznika usługi RMS dla plików pakietu Office, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

Aby uzyskać instrukcje dotyczące używania skryptu programu Windows PowerShell dla wszystkich typów plików, zobacz [Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików &#40;FCI&#41; w systemie Windows Server](../rms-client/configure-fci.md).



## Następne kroki
Gdy już wiesz, na czym polega obsługa usługi Azure RMS w aplikacjach i usługach, może Cię zainteresować porównanie usługi Azure RMS z usługami Active Directory Rights Management (AD RMS) — lokalną wersją usługi Rights Management. Porównanie funkcji, wymagań i opcji zabezpieczeń można znaleźć w temacie [Porównanie usług Azure Rights Management i AD RMS](compare-azure-rms-ad-rms.md).





<!--HONumber=Sep16_HO4-->


