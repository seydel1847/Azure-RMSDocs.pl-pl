---
title: Cennik i ograniczenia dotyczące funkcji BYOK — Azure Information Protection
description: Zrozumienie ograniczeń klawiszy zarządzany przez klienta (znana jako "Użyj własnego klucza", byok) z usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ccbca7f0309e03128ebbe0544e55b341ece47d0f
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="byok-pricing-and-restrictions"></a>Cennik i ograniczenia dotyczące funkcji BYOK

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Organizacje, które mają subskrypcję obejmującą usługę Azure Information Protection, mogą konfigurować dzierżawę usługi Azure Information Protection do użycia klucza zarządzanego przez klienta (BYOK) i [rejestrować jego użycie](../deploy-use/log-analyze-usage.md) bez dodatkowych opłat. 

Klucz musi być przechowywany w magazynie kluczy Azure, co wymaga subskrypcji platformy Azure. Aby użyć klucza chronionego przez moduł HSM, należy użyć warstwę Premium magazynu kluczy Azure. Użycie klucza w usłudze Azure Key Vault generuje opłatę miesięczną. Aby uzyskać więcej informacji, zobacz [stronę z cenami usługi Azure Key Vault](https://azure.microsoft.com/pricing/details/key-vault/).

Gdy używasz usługi Azure Key Vault dla klucza dzierżawy usługi Azure Information Protection, zalecane jest użycie dedykowanych magazynu kluczy dla tego klucza do zapewnienia, że jest on używany przez usługę Azure Rights Management. Taka konfiguracja powoduje, że wywołania przez inne usługi, nie spowoduje przekroczenie [usługi limity](/azure/key-vault/key-vault-service-limits) dla magazynu kluczy, które ograniczyć czas odpowiedzi dla usługi Azure Rights Management.  

Ponadto ponieważ każda usługa, która zwykle używa usługi Azure Key Vault ma wymagania dotyczące różnych zarządzania kluczami, firma Microsoft zaleca oddzielnej subskrypcji platformy Azure dla tego magazynu kluczy ułatwić zabezpieczenie przed błędnej konfiguracji. 

Jednak jeśli chcesz udostępnić subskrypcji platformy Azure z innych usług używających usługi Azure Key Vault, upewnij się, że subskrypcja współużytkuje wspólny zbiór Administratorzy. To oznacza, że administratorzy mogą używać tej subskrypcji ma dobrą znajomością wszystkich kluczy, których mają dostęp do, aby były rzadziej misconfigure je. Na przykład udostępnionej subskrypcji platformy Azure w przypadku administratorów związane z kluczem dzierżawy usługi Azure Information Protection tej samej osoby administrowanie kluczy dla usługi Office 365 klienta klucza i CRM Online. Jednak jeśli administratorów, którzy zarządzają kluczy dla klucza klienta lub CRM Online nie są tego samego osoby, które administrować klucza dzierżawy usługi Azure Information Protection, następnie firma Microsoft zaleca się, że nie mają subskrypcji platformy Azure dla usługi Azure Information Protection.

## <a name="benefits-of-using-azure-key-vault"></a>Zalety używania usługi Azure Key Vault

Oprócz rejestrowania użycia usługi Azure Information Protection można dla dodatkowej pewności porównać uzyskane w ten sposób dane z [zarejestrowanymi danymi dotyczącymi użycia usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-logging/) w celu niezależnego potwierdzenia, że tylko usługa Azure Rights Management korzysta z tego klucza. W razie potrzeby można natychmiast odwołać dostęp do klucza, usuwając uprawnienia w magazynie kluczy.

Inne zalety używania usługi Azure Key Vault do zarządzania kluczem dzierżawy usługi Azure Information Protection:

- Usługa Azure Key Vault to scentralizowane rozwiązanie do zarządzania kluczami zapewniające spójne środowisko zarządzania dla wielu usług chmurowych, a nawet lokalnych, korzystających z szyfrowania.

- Usługa Azure Key Vault obsługuje szereg wbudowanych interfejsów do zarządzania kluczami, takich jak program PowerShell, interfejs wiersza polecenia, interfejsy API REST oraz portal Azure. Inne usługi i narzędzia zostały zintegrowane z usługą Key Vault w celu zapewnienia funkcji zoptymalizowanych pod kątem konkretnych zadań, takich jak monitorowanie. Można na przykład analizować dzienniki użycia kluczy za pośrednictwem funkcji analizy dzienników pakietu Operations Management Suite, konfigurować alerty uruchamiane w przypadku spełnienia określonych kryteriów itp.

- Usługa Azure Key Vault zapewnia separację ról, będącą uznanym najlepszym rozwiązaniem w dziedzinie zabezpieczeń. Administratorzy usługi Azure Information Protection mogą skoncentrować się na zarządzaniu klasyfikacją i ochroną danych, natomiast administratorzy usługi Azure Key Vault — na zarządzaniu kluczami i ewentualnymi szczególnymi zasadami wymaganymi na potrzeby zabezpieczeń lub zgodności.

- W niektórych organizacjach obowiązują ograniczenia dotyczące lokalizacji przechowywania klucza głównego. Usługa Azure Key Vault zapewnia wysoki poziom kontroli nad lokalizacją przechowywania klucza głównego, ponieważ jest dostępna w wielu regionach platformy Azure. Obecnie można wybrać 28 regiony platformy Azure i można oczekiwać, że ten numer, aby zwiększyć. Aby uzyskać więcej informacji, zobacz [produkty dostępne według regionu] (https://azure.microsoft.com/regions/services/) w witrynie platformy Azure.

Oprócz funkcji zarządzania kluczami usługa Azure Key Vault zapewnia administratorom zabezpieczeń jednolite środowisko zarządzania przechowywaniem certyfikatów i informacji poufnych (na przykład haseł), a także zarządzaniem nimi i dostępem do nich, dla innych usług i aplikacji korzystających z szyfrowania. 

Aby uzyskać więcej informacji na temat usługi Azure Key Vault, zobacz [Co to jest usługa Azure Key Vault?](/azure/key-vault/key-vault-whatis) i odwiedź [blog zespołu usługi Azure Key Vault](https://cloudblogs.microsoft.com/kv/), zawierający najnowsze informacje oraz wyjaśnienie sposobu korzystania z tej technologii przez inne usługi.

## <a name="restrictions-when-using-byok"></a>Ograniczenia w przypadku korzystania z rozwiązania BYOK

BYOK i rejestrowania użycia współpracuje z każdą aplikacją, która integruje się z usługą Azure Rights Management, używanego przez usługi Azure Information Protection. To obejmuje usługi w chmurze takich jak SharePoint Online, lokalnych serwerów z programem Exchange i SharePoint, które korzystają z usługi Azure Rights Management przy użyciu łącznika usługi RMS i aplikacji klienckich, takich jak pakiet Office 2016 i Office 2013. Możesz pobrać dzienniki użycia klucza, niezależnie od tego, które aplikacja zgłasza żądania do usługi Azure Rights Management.

Jeśli uprzednio włączono usługi IRM programu Exchange Online zaimportować zaufaną domenę publikacji (TPD) z usługi Azure RMS, postępuj zgodnie z instrukcjami [skonfigurować nowe możliwości szyfrowanie wiadomości usługi Office 365, rozszerzający usługi Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) Aby włączyć nowe funkcje w usłudze Exchange Online, które obsługują usługi Azure Information Protection korzysta ze strategii BYOK.

## <a name="next-steps"></a>Następne kroki

Jeśli wprowadzono decyzja o zarządzanie własnym kluczem, przejdź do [wdrażanie klucza dzierżawy usługi Azure Information Protection](plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key).

Jeśli decydujesz się pozostanie z domyślnej konfiguracji, w której firma Microsoft zarządza z kluczem dzierżawy, zobacz [następne kroki](plan-implement-tenant-key.md#next-steps) sekcji Planowanie i wdrażanie artykuł klucza dzierżawy usługi Azure Information Protection.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
