---
title: Jak serwery plików, które używają infrastruktury FCI obsługują usługę Azure RMS w Efektywnych
description: Informacje dotyczące sposobu używania infrastruktury klasyfikacji plików systemu Windows Server z usługami Azure RMS podczas wdrażania łącznika usług RMS w celu automatycznej ochrony dokumentów pakietu Office.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/17/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8fdad425-5daf-4ce1-822f-9d2fb0b87df1
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f36e39ba4fbd04fca9277bd45986e021c82df0a5
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="how-file-servers-that-run-windows-server-and-use-file-classification-infrastructure-fci-support-azure-rights-management"></a>Jak serwery plików, systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików (FCI) obsługują usługę Azure Rights Management

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Podczas konfigurowania używania infrastruktury klasyfikacji plików w systemie Windows Server funkcja Menedżer zasobów serwera plików może przeskanować lokalne pliki i ustalić, czy zawierają one poufne dane. Pliki spełniające to kryterium są oznaczane za pomocą właściwości klasyfikacji zdefiniowanych przez administratora. W ramach infrastruktury klasyfikacji plików można następnie automatycznie podjąć odpowiednie działania zgodnie z klasyfikacją. Jedno z tych działań obejmuje zastosowanie ochrony informacji za pomocą usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] oraz wdrożenie łącznika usługi Rights Management (nazywanego także łącznikiem usługi RMS). Dzięki temu pliki pakietu Office są automatycznie chronione przez usługę Azure RMS.

Aby chronić wszystkie typy plików, nie należy używać łącznika usługi RMS, ale zamiast tego należy uruchomić skrypt programu Windows PowerShell, która używa polecenia cmdlet z [moduł usługi Azure Information Protection](../rms-client/client-admin-guide-powershell.md).

Zasady klasyfikacji są w pełni konfigurowalne i wysoce rozszerzalne, dzięki czemu można zapobiec potencjalnym wyciekom danych pochodzącym od nieautoryzowanych i autoryzowanych użytkowników. Możliwe jest nawet zmniejszenie ryzyka wycieku danych pochodzącego od administratorów sieci, ponieważ można skonfigurować zasady, które nie wymagają, aby mieli oni dostęp do plików.

Aby uzyskać instrukcje dotyczące wdrażania i konfigurowania łącznika usługi RMS dla plików pakietu Office, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

Aby uzyskać instrukcje dotyczące używania skryptu programu Windows PowerShell dla wszystkich typów plików, zobacz [Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików &#40;FCI&#41; w systemie Windows Server](../rms-client/configure-fci.md).



## <a name="next-steps"></a>Następne kroki
Gdy już wiesz, na czym polega obsługa usługi Azure RMS w aplikacjach i usługach, może Cię zainteresować porównanie usługi Azure RMS z usługami Active Directory Rights Management (AD RMS) — lokalną wersją usługi Rights Management. Porównanie funkcji, wymagań i opcji zabezpieczeń można znaleźć w temacie [Porównanie usług Azure Rights Management i AD RMS](compare-azure-rms-ad-rms.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

