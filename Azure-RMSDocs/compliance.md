---
title: Zgodność i informacje dotyczące usługi Azure Information Protection
description: Dodatkowe informacje na temat usługi Azure Information Protection, na przykład kwestii prawnych, zgodności i umów SLA.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: b3a7127b-6d24-4439-bc4e-2a0a325e8ea3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 96746e39d564c87471205fa442976a3904ddf992
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023825"
---
# <a name="compliance-and-supporting-information-for-azureinformation-protection"></a>Zgodność i dodatkowe informacje na temat usługi Azure Information Protection

Usługa Azure Information Protection obsługuje inne usługi, a także opiera się na inne usługi. Jeśli szukasz informacji związanych z usługą Azure Information Protection, ale niedotyczących sposobu korzystania z usługi Azure Information Protection, sprawdź następujące zasoby:

## <a name="suitability-for-different-countries"></a>Przydatności do różnych krajów

Biorąc pod uwagę zmienności między prawem i regulacjami w różnych krajach, różnych przypadków użycia i scenariuszy i różnymi wymaganiami, między różnych firm sektorów, konieczne będzie zapoznaj się z Twojego doradca prawny pomagające uzyskać odpowiedzi, czy usługa Azure Ochrona informacji jest odpowiednia dla Twojego kraju.

Jednak niektóre istotne informacje, które mogą pomóc Twojej doradca prawny wykonać oznaczenie:

- Usługa Azure Information Protection używa algorytmu AES 256 i AES 128 umożliwiającej szyfrowanie dokumentów. [Więcej informacji](./how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Wszystkie klucze szyfrowania używane przez usługę Azure Information Protection są chronione przy użyciu klucza głównego klienta, który używa szyfrowania RSA 2048 bitów. Szyfrowanie RSA 1024, ale jest również obsługiwane w przypadku zapewnienia zgodności. [Więcej informacji](./how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Klucze główne właściwe dla klienta są zarządzane przez firmę Microsoft lub udostępnione przez klienta w module HSM firmy Thales przy użyciu "[Użyj własnego klucza](plan-implement-tenant-key.md)" (BYOK). Usługa Azure Information Protection obsługuje także ograniczenie funkcjonalności przy użyciu klucza w środowisku lokalnym za pomocą "[przechowywać własny klucz](configure-adrms-restrictions.md)" (HYOK) dla zawartości, która jest zależna od wymogów, które wskazują, że nie powinny być chronione przy użyciu klucz oparte na chmurze.

- Usługi Azure Information Protection znajduje się w regionalnych centrach danych na całym świecie. Usługi Azure Information Protection kluczy i zasady zawsze pozostają w obrębie regionu, w którym pierwotnie wdrożono.
 
- Usługa Azure Information Protection nie przesyła zawartości dokumentu z klientów do usługi Azure Information Protection. Zawartość operacje szyfrowania i odszyfrowywania są wykonywane w miejscu na urządzeniu klienckim. Lub oparta na usłudze renderowanie, te operacje są wykonywane w ramach usługi, która jest renderowania zawartości. [Więcej informacji](./how-does-it-work.md)

## <a name="legal-and-privacy"></a>Informacje prawne i ochrona prywatności

- Aby uzyskać informacje o umowach Microsoft Azure: [umowę Microsoft Azure](http://azure.microsoft.com/support/legal/subscription-agreement/)

- Aby uzyskać informacje o ochronie prywatności Microsoft Azure: [Microsoft Azure — zasady zachowania poufności informacji](http://azure.microsoft.com/support/legal/privacy-statement/)

## <a name="security-compliance-and-auditing"></a>Zabezpieczenia, zgodność i inspekcja

Zobacz sekcję dotyczącą [wymagań związanych z zabezpieczeniami, zgodnością i przepisami](./what-is-azure-rms.md#security-compliance-and-regulatory-requirements) w artykule [Jakie problemy rozwiązuje usługa Azure RMS?](./azure-rms-problems-it-solves.md), aby poznać informacje o poszczególnych certyfikatach usługi Azure Rights Management. Ponadto:

- Zewnętrzne certyfikaty usługi Azure Information Protection: [Microsoft Azure Trust Center](http://azure.microsoft.com/support/trust-center/)

- Informacje dotyczące standardu FIPS 140: [FIPS 140 Validation](https://technet.microsoft.com/library/security/cc750357.aspx)

Szczegółowe informacje techniczne dotyczące sposobu działania technologii ochrony można znaleźć w temacie [Jak działa usługa Azure RMS](./how-does-it-work.md) 

## <a name="service-level-agreements"></a>Umowy dotyczące poziomu usług

- [Umowa SLA dla usługi Azure Information Protection](https://azure.microsoft.com/support/legal/sla/information-protection/v1_0/)

- [Umowa SLA dla usługi Azure Active Directory](https://azure.microsoft.com/support/legal/sla/active-directory/v1_0/)

- [Umowa SLA dla usługi Azure Key Vault](https://azure.microsoft.com/support/legal/sla/key-vault/v1_0/)

## <a name="documentation"></a>Dokumentacja

- Dokumentacja usługi Azure Active Directory: [usługi Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis)

- Dokumentacja pakietu usługi Office 365 Enterprise: [usługi Office 365](https://docs.microsoft.com/en-us/Office365/Enterprise/)

