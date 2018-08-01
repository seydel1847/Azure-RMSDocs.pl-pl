---
title: Zgodność i informacje dotyczące usługi Azure Information Protection
description: Dodatkowe informacje na temat usługi Azure Information Protection dotyczące na przykład kwestii prawnych, zgodności i umów SLA.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/12/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: b3a7127b-6d24-4439-bc4e-2a0a325e8ea3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b19b118a700f86c89ce1b727a4f75c1c7017d2c8
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39369796"
---
# <a name="compliance-and-supporting-information-for-azure-information-protection"></a>Zgodność i informacje dodatkowe dotyczące usługi Azure Information Protection

Usługa Azure Information Protection obsługuje inne usługi i korzysta z nich. Jeśli szukasz informacji związanych z usługą Azure Information Protection, ale niedotyczących sposobu korzystania z usługi Azure Information Protection, sprawdź następujące zasoby:

## <a name="suitability-for-different-countries"></a>Przydatności do różnych krajów

Biorąc pod uwagę zmienności między prawem i regulacjami w różnych krajach, różnych przypadków użycia i scenariuszy i różnymi wymaganiami, między różnych firm sektorów, konieczne będzie zapoznaj się z Twojego doradca prawny pomagające uzyskać odpowiedzi, czy usługa Azure Ochrona informacji jest odpowiednia dla Twojego kraju.

Jednak niektóre istotne informacje, które mogą pomóc Twojej doradca prawny wykonać oznaczenie:

- Usługa Azure Information Protection używa algorytmu AES 256 i AES 128 umożliwiającej szyfrowanie dokumentów. [Więcej informacji](../understand-explore/how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Wszystkie klucze szyfrowania używane przez usługę Azure Information Protection są chronione przy użyciu klucza głównego klienta, który używa szyfrowania RSA 2048 bitów. Szyfrowanie RSA 1024, ale jest również obsługiwane w przypadku zapewnienia zgodności. [Więcej informacji](../understand-explore/how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Klucze główne właściwe dla klienta są zarządzane przez firmę Microsoft lub udostępnione przez klienta w module HSM firmy Thales przy użyciu "[Użyj własnego klucza](../plan-design/plan-implement-tenant-key.md)" (BYOK). Usługa Azure Information Protection obsługuje także ograniczenie funkcjonalności przy użyciu klucza w środowisku lokalnym za pomocą "[przechowywać własny klucz](../deploy-use/configure-adrms-restrictions.md)" (HYOK) dla zawartości, która jest zależna od wymogów, które wskazują, że nie powinny być chronione przy użyciu klucz oparte na chmurze.

- Usługi Azure Information Protection znajduje się w regionalnych centrach danych na całym świecie. Usługi Azure Information Protection kluczy i zasady zawsze pozostają w obrębie regionu, w którym pierwotnie wdrożono.
 
- Usługa Azure Information Protection nie przesyła zawartości dokumentu z klientów do usługi Azure Information Protection. Zawartość operacje szyfrowania i odszyfrowywania są wykonywane w miejscu na urządzeniu klienckim. Lub oparta na usłudze renderowanie, te operacje są wykonywane w ramach usługi, która jest renderowania zawartości. [Więcej informacji](../understand-explore/how-does-it-work.md)

## <a name="legal-and-privacy"></a>Informacje prawne i ochrona prywatności

- Informacje o umowie dotyczącej usług Microsoft Azure: [Umowa dotycząca usług Microsoft Azure](http://azure.microsoft.com/support/legal/subscription-agreement/)

- Informacje o ochronie prywatności w usługach Microsoft Azure: [Zasady zachowania poufności informacji usług Microsoft Azure](http://azure.microsoft.com/support/legal/privacy-statement/)

## <a name="security-compliance-and-auditing"></a>Zabezpieczenia, zgodność i inspekcja

Zobacz sekcję dotyczącą [wymagań związanych z zabezpieczeniami, zgodnością i przepisami](../understand-explore/azure-rms-problems-it-solves.md#security-compliance-and-regulatory-requirements) w artykule [Jakie problemy rozwiązuje usługa Azure RMS?](../understand-explore/azure-rms-problems-it-solves.md), aby poznać informacje o poszczególnych certyfikatach usługi Azure Rights Management. Ponadto:

- Zewnętrzne certyfikaty usługi Azure Information Protection: [Centrum zaufania systemu Microsoft Azure](http://azure.microsoft.com/support/trust-center/)

- Informacje dotyczące standardu FIPS 140: [FIPS 140 Validation](https://technet.microsoft.com/library/security/cc750357.aspx)

Szczegółowe informacje techniczne dotyczące sposobu działania technologii ochrony można znaleźć w temacie [Jak działa usługa Azure RMS](../understand-explore/how-does-it-work.md) 

## <a name="service-level-agreements"></a>Umowy dotyczące poziomu usług

- [Umowa SLA dla usługi Azure Information Protection](https://azure.microsoft.com/support/legal/sla/information-protection/v1_0/)

- [Umowa SLA dla usługi Azure Active Directory](https://azure.microsoft.com/support/legal/sla/active-directory/v1_0/)

- [Umowa SLA dla usługi Azure Key Vault](https://azure.microsoft.com/support/legal/sla/key-vault/v1_0/)

## <a name="documentation"></a>Dokumentacja

- Dokumentacja usługi Azure Active Directory: [Azure Active Directory](/active-directory/)

- Biblioteka usługi Office 365: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

