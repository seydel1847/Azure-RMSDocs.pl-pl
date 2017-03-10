---
title: "Cennik i ograniczenia dotyczące funkcji BYOK — Azure Information Protection"
description: "Informacje na temat ograniczeń związanych z używaniem kluczy zarządzanych przez klienta (model używania własnego klucza — BYOK, Bring Your Own Key) z usługami Azure RMS."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ab3b25ebd04565f8cd0e9236c1241f38d4a2e8b2
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="byok-pricing-and-restrictions"></a>Cennik i ograniczenia dotyczące funkcji BYOK

>*Dotyczy: Azure Information Protection, Office 365*


Organizacje, które mają subskrypcję obejmującą usługę Azure Information Protection, mogą konfigurować dzierżawę usługi Azure Information Protection do użycia klucza zarządzanego przez klienta (BYOK) i [rejestrować jego użycie](../deploy-use/log-analyze-usage.md) bez dodatkowych opłat. 

Klucz musi być przechowywany w usłudze Azure Key Vault, co wymaga płatnej (lub próbnej) subskrypcji platformy Azure. Należy również używać warstwy Premium usługi Azure Key Vault do obsługi kluczy chronionych przez moduł HSM. Za korzystanie z klucza chronionego przez moduł HSM w usłudze Azure Key Vault naliczana jest opłata miesięczna. Aby uzyskać więcej informacji, zobacz [stronę z cenami usługi Azure Key Vault](https://azure.microsoft.com/en-us/pricing/details/key-vault/).

W przypadku używania usługi Azure Key Vault do zarządzania kluczem dzierżawy usługi Azure Information Protection zalecane jest użycie osobnego magazynu kluczy i osobnej subskrypcji dla tego klucza, co pozwala zapewnić, że jest on używany tylko przez usługę Azure Rights Management. 

## <a name="benefits-of-using-azure-key-vault"></a>Zalety używania usługi Azure Key Vault

Oprócz rejestrowania użycia usługi Azure Information Protection można dla dodatkowej pewności porównać uzyskane w ten sposób dane z [zarejestrowanymi danymi dotyczącymi użycia usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-logging/) w celu niezależnego potwierdzenia, że tylko usługa Azure Rights Management korzysta z tego klucza. W razie potrzeby można natychmiast odwołać dostęp do klucza, usuwając uprawnienia w magazynie kluczy.

Inne zalety używania usługi Azure Key Vault do zarządzania kluczem dzierżawy usługi Azure Information Protection:

- Usługa Azure Key Vault to scentralizowane rozwiązanie do zarządzania kluczami zapewniające spójne środowisko zarządzania dla wielu usług chmurowych, a nawet lokalnych, korzystających z szyfrowania.

- Usługa Azure Key Vault obsługuje szereg wbudowanych interfejsów do zarządzania kluczami, takich jak program PowerShell, interfejs wiersza polecenia, interfejsy API REST oraz portal Azure. Inne usługi i narzędzia zostały zintegrowane z usługą Key Vault w celu zapewnienia funkcji zoptymalizowanych pod kątem konkretnych zadań, takich jak monitorowanie. Można na przykład analizować dzienniki użycia kluczy za pośrednictwem funkcji analizy dzienników pakietu Operations Management Suite, konfigurować alerty uruchamiane w przypadku spełnienia określonych kryteriów itp.

- Usługa Azure Key Vault zapewnia separację ról, będącą uznanym najlepszym rozwiązaniem w dziedzinie zabezpieczeń. Administratorzy usługi Azure Information Protection mogą skoncentrować się na zarządzaniu klasyfikacją i ochroną danych, natomiast administratorzy usługi Azure Key Vault — na zarządzaniu kluczami i ewentualnymi szczególnymi zasadami wymaganymi na potrzeby zabezpieczeń lub zgodności.

- W niektórych organizacjach obowiązują ograniczenia dotyczące lokalizacji przechowywania klucza głównego. Usługa Azure Key Vault zapewnia wysoki poziom kontroli nad lokalizacją przechowywania klucza głównego, ponieważ jest dostępna w wielu regionach platformy Azure. Obecnie można wybrać region platformy Azure spośród 28 dostępnych, a w przyszłości planowane jest zwiększenie tej liczby. Aby uzyskać więcej informacji, zobacz stronę [Dostępne produkty według regionu] (https://azure.microsoft.com/regions/services/) w witrynie platformy Azure.

Oprócz funkcji zarządzania kluczami usługa Azure Key Vault zapewnia administratorom zabezpieczeń jednolite środowisko zarządzania przechowywaniem certyfikatów i informacji poufnych (na przykład haseł), a także zarządzaniem nimi i dostępem do nich, dla innych usług i aplikacji korzystających z szyfrowania. 

Aby uzyskać więcej informacji na temat usługi Azure Key Vault, zobacz [Co to jest usługa Azure Key Vault?](https://azure.microsoft.com/documentation/articles/key-vault-whatis/) i odwiedź [blog zespołu usługi Azure Key Vault](https://blogs.technet.microsoft.com/kv/), zawierający najnowsze informacje oraz wyjaśnienie sposobu korzystania z tej technologii przez inne usługi.


## <a name="restrictions-when-using-byok"></a>Ograniczenia w przypadku korzystania z rozwiązania BYOK

Jeśli istnieją użytkownicy, którzy zarejestrowali się w celu korzystania z bezpłatnego konta przy użyciu usługi RMS dla użytkowników indywidualnych, nie można użyć rozwiązania BYOK ani rejestrowania użycia, ponieważ ta konfiguracja nie ma administratora dzierżawy do skonfigurowania tych funkcji.


> [!NOTE]
> Więcej informacji o usługach RMS dla użytkowników indywidualnych zawiera temat [Usługa RMS dla użytkowników indywidualnych i usługa Azure Rights Management](../understand-explore/rms-for-individuals.md).

![Funkcja BYOK nie obsługuje usługi Exchange Online](../media/RMS_BYOK_noExchange.png)

Funkcja BYOK i rejestrowanie użycia współdziałają bezproblemowo z każdą aplikacją, która integruje się z usługą Azure Rights Management (Azure RMS) używaną przez usługę Azure Information Protection. Dotyczy to usług w chmurze, takich jak SharePoint Online, serwerów lokalnych z programem Exchange i SharePoint, które współpracują z usługą Azure RMS za pomocą łącznika usługi RMS, a także aplikacji klienckich, np. Office 2016 i Office 2013. Dzienniki użycia klucza uzyskasz niezależnie od tego, która aplikacja zgłasza żądania dotyczące usługi Azure RMS.

Istnieje jeden wyjątek: obecnie **usługa Azure RMS BYOK nie jest zgodna z usługą Exchange Online**. Użytkownikom usługi Exchange Online zaleca się wdrożenie usługi Azure RMS w domyślnym trybie zarządzania kluczami, w którym firma Microsoft generuje klucze i zarządza nimi. Istnieje możliwość skorzystania z funkcji BYOK w późniejszym czasie, na przykład wtedy, gdy dla usługi Exchange Online zostanie zapewniona obsługa trybu BYOK usługi Azure RMS. Jeśli nie możesz czekać, istnieje inne rozwiązanie. Możesz wdrożyć usługę Azure RMS z funkcją BYOK już teraz, ale będzie ona mieć ograniczoną funkcjonalność w przypadku usługi Exchange Online (niechronione wiadomości e-mail i załączniki pozostaną w pełni funkcjonalne):

-   Nie można wyświetlać chronionych wiadomości e-mail i załączników w usłudze Outlook Web Access.

-   Nie można wyświetlać chronionych wiadomości e-mail na urządzeniach przenośnych, które używają programu Exchange ActiveSync z funkcją IRM.

-   Odszyfrowywanie transportu (np. w celu przeprowadzenia skanowania w poszukiwaniu złośliwego oprogramowania) oraz dziennika nie jest możliwe, dlatego chronione wiadomości e-mail i załączniki będą pomijane.

-   Reguły ochrony transportu i zapobiegania utracie danych (DLP), które wymuszają zasady IRM, są niedostępne, dlatego nie można wdrożyć ochrony RMS za pomocą tych metod.

-   Podczas wyszukiwania chronionych wiadomości e-mail na serwerze zostaną one pominięte.

W przypadku korzystania z usługi Azure RMS BYOK z ograniczoną funkcjonalnością usługi RMS w usłudze Exchange Online usługa RMS będzie współpracować z klientami poczty e-mail w programie Outlook w systemach Windows i Mac. Nie będzie współpracować z żadnym innym klientem poczty e-mail, który nie używa programu Exchange ActiveSync z funkcją IRM.

Jeśli użytkownik migruje do usługi Azure RMS z usług AD RMS, możliwe że zaimportował klucz jako zaufaną domenę publikacji (TPD) do usługi Exchange Online (co jest nazywane rozwiązaniem BYOK w terminologii programu Exchange, jednak różni się od rozwiązania BYOK usługi Azure Key Vault). W tym scenariuszu należy usunąć zaufaną domenę publikacji z usługi Exchange Online, aby uniknąć konfliktów szablonów i zasad. Aby uzyskać więcej informacji, zobacz temat [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) w bibliotece poleceń cmdlet usługi Exchange Online.

Czasami wyjątek usługi Azure RMS BYOK dla usługi Exchange Online nie stanowi problemu w praktyce. Przykładowo jest tak w przypadku organizacji potrzebujących funkcji BYOK i rejestrowania, które uruchamiają swoje aplikacje do obsługi danych (Exchange, SharePoint, Office) lokalnie i używają usługi Azure RMS w celu korzystania z funkcji, która nie jest łatwo dostępna z lokalną usługą AD RMS (np. w przypadku współpracy z innymi firmami i uzyskiwaniem dostępu z klientów mobilnych). Zarówno funkcja BYOK, jak i możliwość rejestrowania będą działać prawidłowo w tym scenariuszu, a organizacja zachowa pełną kontrolę nad swoją subskrypcją usługi Azure RMS.

## <a name="next-steps"></a>Następne kroki

Jeśli zdecydujesz się na zarządzanie własnym kluczem, przejdź do tematu [Wdrażanie klucza dzierżawy usługi Azure Rights Management](plan-implement-tenant-key.md#implementing-your-azure-information-protection-tenant-key).

Jeśli zdecydujesz się nadal używać domyślnej konfiguracji, w której firma Microsoft zarządza kluczem dzierżawy, zobacz sekcję [Następne kroki](plan-implement-tenant-key.md#next-steps) w artykule Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
