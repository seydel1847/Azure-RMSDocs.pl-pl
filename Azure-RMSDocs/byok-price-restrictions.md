---
title: Cennik i ograniczenia dotyczące funkcji BYOK — Azure Information Protection
description: Omówienie ograniczeń, gdy używasz kluczy zarządzanych przez klienta (znana jako "bring your own key", byok) za pomocą usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/28/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 57914b0268102e8f7f5049ee1c63b58bf54c9a14
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44149146"
---
# <a name="byok-pricing-and-restrictions"></a>Cennik i ograniczenia dotyczące funkcji BYOK

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Organizacje, które mają subskrypcję obejmującą usługę Azure Information Protection można skonfigurować ich dzierżawy usługi Azure Information Protection do użycia klucza zarządzanego przez klienta (BYOK) i [rejestrować ich użycie](./log-analyze-usage.md). 

Klucz musi być przechowywany w usłudze Azure Key Vault, który wymaga subskrypcji platformy Azure. Aby użyć klucza chronionego przez moduł HSM, należy użyć warstwy usługi Azure Key Vault — wersja Premium. Użycie klucza w usłudze Azure Key Vault generuje opłatę miesięczną. Aby uzyskać więcej informacji, zobacz [stronę z cenami usługi Azure Key Vault](https://azure.microsoft.com/pricing/details/key-vault/).

Gdy używasz usługi Azure Key Vault dla klucza dzierżawy usługi Azure Information Protection, zaleca się, że używasz dedykowanego magazynu kluczy dla tego klucza, aby mieć pewność, że jest używana przez usługę Azure Rights Management. Ta konfiguracja gwarantuje, że wywołania przez inne usługi spowoduje przekroczenie [limitów usług](/azure/key-vault/key-vault-service-limits) dla usługi key vault, która może ograniczać czasy odpowiedzi dla usługi Azure Rights Management.  

Ponadto ponieważ każda usługa, która zwykle używa usługi Azure Key Vault ma wymagania dotyczące różnych zarządzania kluczami, firma Microsoft zaleca oddzielną subskrypcję platformy Azure dla tego magazynu kluczy ułatwić zabezpieczenie przed błędnej konfiguracji. 

Jednak jeśli chcesz udostępnić subskrypcji platformy Azure przy użyciu innych usług używających usługi Azure Key Vault, upewnij się, że subskrypcja udostępnia wspólny zbiór Administratorzy. W ten sposób oznacza, że administratorzy, którzy korzystają z tej subskrypcji mają dobrej znajomości sposobu wszystkie klucze mają dostęp do, aby były one mniej prawdopodobne misconfigure je. Na przykład udostępnionej subskrypcji systemu Azure w przypadku administratorów związane z kluczem dzierżawy usługi Azure Information Protection tej samej osoby, które administrowania klucze dla klucz klienta usługi Office 365 i CRM Online. Ale jeśli administratorów, którzy zarządzają kluczy dla klucza klienta lub CRM Online nie są w tej samej osoby, które administrowania klucz dzierżawy usługi Azure Information Protection, następnie zalecamy nie mają subskrypcji platformy Azure dla usługi Azure Information Protection.

## <a name="benefits-of-using-azure-key-vault"></a>Zalety używania usługi Azure Key Vault

Oprócz rejestrowania użycia usługi Azure Information Protection można dla dodatkowej pewności porównać uzyskane w ten sposób dane z [zarejestrowanymi danymi dotyczącymi użycia usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-logging/) w celu niezależnego potwierdzenia, że tylko usługa Azure Rights Management korzysta z tego klucza. W razie potrzeby można natychmiast odwołać dostęp do klucza, usuwając uprawnienia w magazynie kluczy.

Inne zalety używania usługi Azure Key Vault do zarządzania kluczem dzierżawy usługi Azure Information Protection:

- Usługa Azure Key Vault to scentralizowane rozwiązanie do zarządzania kluczami zapewniające spójne środowisko zarządzania dla wielu usług chmurowych, a nawet lokalnych, korzystających z szyfrowania.

- Usługa Azure Key Vault obsługuje szereg wbudowanych interfejsów do zarządzania kluczami, takich jak program PowerShell, interfejs wiersza polecenia, interfejsy API REST oraz portal Azure. Inne usługi i narzędzia zostały zintegrowane z usługą Key Vault w celu zapewnienia funkcji zoptymalizowanych pod kątem konkretnych zadań, takich jak monitorowanie. Można na przykład analizować dzienniki użycia kluczy za pośrednictwem funkcji analizy dzienników pakietu Operations Management Suite, konfigurować alerty uruchamiane w przypadku spełnienia określonych kryteriów itp.

- Usługa Azure Key Vault zapewnia separację ról, będącą uznanym najlepszym rozwiązaniem w dziedzinie zabezpieczeń. Administratorzy usługi Azure Information Protection mogą skoncentrować się na zarządzaniu klasyfikacją i ochroną danych, natomiast administratorzy usługi Azure Key Vault — na zarządzaniu kluczami i ewentualnymi szczególnymi zasadami wymaganymi na potrzeby zabezpieczeń lub zgodności.

- W niektórych organizacjach obowiązują ograniczenia dotyczące lokalizacji przechowywania klucza głównego. Usługa Azure Key Vault zapewnia wysoki poziom kontroli nad lokalizacją przechowywania klucza głównego, ponieważ jest dostępna w wielu regionach platformy Azure. Obecnie możesz wybrać spośród 28 regiony platformy Azure i można oczekiwać, że zwiększenie tej liczby. Aby uzyskać więcej informacji, zobacz [dostępne produkty według regionu] (https://azure.microsoft.com/regions/services/) strony w witrynie platformy Azure.

Oprócz funkcji zarządzania kluczami usługa Azure Key Vault zapewnia administratorom zabezpieczeń jednolite środowisko zarządzania przechowywaniem certyfikatów i informacji poufnych (na przykład haseł), a także zarządzaniem nimi i dostępem do nich, dla innych usług i aplikacji korzystających z szyfrowania. 

Aby uzyskać więcej informacji na temat usługi Azure Key Vault, zobacz [Co to jest usługa Azure Key Vault?](/azure/key-vault/key-vault-whatis) i odwiedź [blog zespołu usługi Azure Key Vault](https://cloudblogs.microsoft.com/kv/), zawierający najnowsze informacje oraz wyjaśnienie sposobu korzystania z tej technologii przez inne usługi.

## <a name="restrictions-when-using-byok"></a>Ograniczenia w przypadku korzystania z rozwiązania BYOK

Funkcja BYOK i rejestrowanie użycia współpracują bezproblemowo z każdą aplikacją, która integruje się z usługą Azure Rights Management, który jest używany przez usługi Azure Information Protection. Dotyczy to usług w chmurze takich jak SharePoint Online, lokalne serwery z programem Exchange i SharePoint, które korzystają z usługi Azure Rights Management przy użyciu łącznika usługi RMS, a aplikacje klienckie, takie jak pakiet Office 2016 lub Office 2013. Możesz pobrać dzienniki użycia klucza, niezależnie od tego, które aplikacja zgłasza żądania do usługi Azure Rights Management.

Jeśli zostało wcześniej włączone usługi Exchange Online IRM, importując zaufaną domenę publikacji (TPD) z usługi Azure RMS, postępuj zgodnie z instrukcjami [skonfigurować nowe możliwości szyfrowanie wiadomości usługi Office 365 korzystających z usługi Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) włączyć nowych funkcji w usłudze Exchange Online, które obsługują korzystania z rozwiązania BYOK usługi Azure Information Protection.

## <a name="next-steps"></a>Kolejne kroki

Jeśli wprowadzono decyzję, aby zarządzać własnym kluczem, przejdź do strony [wdrażanie klucza dzierżawy usługi Azure Information Protection](plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key).

Jeśli zdecydujesz się nadal używać domyślnej konfiguracji, której firma Microsoft zarządza z kluczem dzierżawy, zobacz [następne kroki](plan-implement-tenant-key.md#next-steps) sekcji Planowanie i wdrażanie artykułu klucza dzierżawy usługi Azure Information Protection.

