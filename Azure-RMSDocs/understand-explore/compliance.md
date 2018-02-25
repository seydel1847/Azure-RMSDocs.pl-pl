---
title: "Zgodność i informacje dotyczące usługi Azure Information Protection"
description: "Dodatkowe informacje na temat usługi Azure Information Protection dotyczące na przykład kwestii prawnych, zgodności i umów SLA."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: b3a7127b-6d24-4439-bc4e-2a0a325e8ea3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ef0b40db5dbbb66d7cbf45028862576a58886051
ms.sourcegitcommit: 240378d216e386ad760460c50b7a664099c669e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="compliance-and-supporting-information-for-azure-information-protection"></a>Zgodność i informacje dodatkowe dotyczące usługi Azure Information Protection

Usługa Azure Information Protection obsługuje inne usługi i korzysta z nich. Jeśli szukasz informacji związanych z usługą Azure Information Protection, ale niedotyczących sposobu korzystania z usługi Azure Information Protection, sprawdź następujące zasoby:

## <a name="suitability-for-different-countries"></a>Przydatności dla różnych krajów

Mając zmienności między przepisom eksportowym obowiązującym w różnych krajach, innych przypadków użycia i scenariusze i różne wymagania dotyczące między różne sektory, należy zapoznać się z doradca prawny ma pomóc odpowiedzieć czy Azure Ochrona informacji jest odpowiednie dla danego kraju.

Jednak niektóre istotne informacje, które mogą ułatwić z doradcą prawnym wykonać oznaczenie:

- Usługa Azure Information Protection używa AES 256 i AES 128 do szyfrowania dokumentów. [Więcej informacji](../understand-explore/how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Wszystkie klucze szyfrowania używany przez usługę Azure Information Protection są chronione przy użyciu klucza głównego właściwe dla klienta, który używa szyfrowania RSA 2048 bitów. Szyfrowanie RSA 1024, ale jest również obsługiwane dla zapewnienia zgodności. [Więcej informacji](../understand-explore/how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Klucze główne właściwe dla klienta są zarządzane przez firmę Microsoft lub udostępnione przez klienta w module HSM firmy Thales przy użyciu "[własnego klucza](../plan-design/plan-implement-tenant-key.md)" (BYOK). Usługa Azure Information Protection obsługuje również ograniczoną funkcjonalność przy użyciu lokalnego klucza za pomocą "[przechowywać własny klucz](../deploy-use/configure-adrms-restrictions.md)" (HYOK) dla zawartości, których dotyczy wymagania, które wskazują, że jej nie powinien być chroniony za klucz oparte na chmurze.

- Usługa Azure Information Protection znajduje się w regionalnych centrach danych na całym świecie. Azure Information Protection kluczy i zasady zawsze pozostają w regionie, w którym pierwotnie została wdrożona.
 
- Usługa Azure Information Protection nie przesyła zawartości dokumentu z klientów do usługi Azure Information Protection. Zawartości operacje szyfrowania i odszyfrowywania są wykonywane w miejscu na urządzeniu klienckim. Lub dla opartych na usługach renderowania operacje te są wykonywane w ramach usługi, która jest renderowania zawartości. [Więcej informacji](../understand-explore/how-does-it-work.md)

## <a name="legal-and-privacy"></a>Informacje prawne i ochrona prywatności

- Informacje o umowie dotyczącej usług Microsoft Azure: [Umowa dotycząca usług Microsoft Azure](http://azure.microsoft.com/support/legal/subscription-agreement/)

- Informacje o ochronie prywatności w usługach Microsoft Azure: [Zasady zachowania poufności informacji usług Microsoft Azure](http://azure.microsoft.com/support/legal/privacy-statement/)

## <a name="security-compliance-and-auditing"></a>Zabezpieczenia, zgodność i inspekcja

Zobacz sekcję dotyczącą [wymagań związanych z zabezpieczeniami, zgodnością i przepisami](../understand-explore/azure-rms-problems-it-solves.md#security-compliance-and-regulatory-requirements) w artykule [Jakie problemy rozwiązuje usługa Azure RMS?](../understand-explore/azure-rms-problems-it-solves.md), aby poznać informacje o poszczególnych certyfikatach usługi Azure Rights Management. Ponadto:

- Zewnętrzne certyfikaty usługi Azure Information Protection: [Centrum zaufania systemu Microsoft Azure](http://azure.microsoft.com/support/trust-center/)

- Informacje dotyczące standardu FIPS 140: [FIPS 140 Validation](https://technet.microsoft.com/library/security/cc750357.aspx)

Szczegółowe informacje techniczne dotyczące sposobu działania technologii ochrony można znaleźć w temacie [Jak działa usługa Azure RMS](../understand-explore/how-does-it-work.md) 

## <a name="service-level-agreements"></a>Umowy dotyczące poziomu usług

- Umowa dotycząca poziomu usług dla usługi Azure Information Protection według wybranego regionu: [pobierz ze strony wyszukiwania licencjonowania produktów](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

    - Na przykład kliknij pozycję **OnlineSvcsConsolidatedSLA(WW)(English)(March2016)**, aby pobrać umowę dotyczącą poziomu usług dla Ameryki Północnej z marca 2016 r.

-   Umowa dotycząca poziomu usług dla usługi Azure Active Directory: [Umowy dotyczące poziomu usług](http://azure.microsoft.com/support/legal/sla/)

## <a name="documentation"></a>Dokumentacja

- Dokumentacja usługi Azure Active Directory: [Azure Active Directory](/active-directory/)

- Biblioteka usługi Office 365: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
