---
title: "Operacje cyklu życia klucza dzierżawy usługi AIP zarządzane przez klienta"
description: "Informacje na temat operacji cyklu życia, które są istotne, jeśli samodzielnie zarządzasz swoim kluczem dzierżawy dla usługi Azure Information Protection — zgodnie ze scenariuszem BYOK (Bring Your Own Key)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 781e534566fe01bca4583d2fb5a1a430db77429b
ms.sourcegitcommit: 1dee39e5e3b222b4aab2b6c4284b82927148407e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2017
---
# Operacje cyklu życia klucza dzierżawy zarządzane przez klienta
<a id="customer-managed-tenant-key-lifecycle-operations" class="xliff"></a>

>*Dotyczy: Azure Information Protection, Office 365*

Jeśli samodzielnie zarządzasz swoim kluczem dzierżawy dla usługi Azure Information Protection — zgodnie ze scenariuszem BYOK (Bring Your Own Key) — użyj poniższych sekcji w celu uzyskania dodatkowych informacji na temat operacji cyklu życia związanych z tą topologią.

## Odwołanie klucza dzierżawy
<a id="revoke-your-tenant-key" class="xliff"></a>
W usłudze Azure Key Vault można zmienić uprawnienia dotyczące magazynu kluczy, który zawiera klucz dzierżawy usługi Azure Information Protection, aby usługa Azure Rights Management nie mogła już uzyskać dostępu do tego klucza. Niemniej po wykonaniu tej czynności nikt nie będzie w stanie otworzyć dokumentów i wiadomości e-mail, które zostały wcześniej zabezpieczone przez usługę Azure Rights Management.

Po anulowaniu subskrypcji usługi Azure Information Protection usługa ta wstrzymuje korzystanie z klucza dzierżawy, co nie wymaga żadnej akcji ze strony użytkownika.


## Ponowne tworzenie klucza dzierżawy
<a id="re-key-your-tenant-key" class="xliff"></a>
Ponowne tworzenie jest nazywane także wycofywaniem klucza. Klucza dzierżawy nie należy tworzyć ponownie, jeśli nie jest to naprawdę konieczne. Starsze programy klienckie, takie jak Office 2010, nie zostały zaprojektowane do bezproblemowej zmiany klucza. W tym scenariuszu należy usunąć stan usługi Rights Management na komputerach przy użyciu zasad grupy lub równoważnego mechanizmu. Występują jednak określone zdarzenia, które mogą wymusić ponowne utworzenie klucza dzierżawy. Na przykład:

-   Firma została podzielona na dwie lub więcej firm. Po ponownym utworzeniu klucza dzierżawy nowa firma nie będzie miała dostępu do nowej zawartości publikowanej przez pracowników. Mogą oni uzyskać dostęp do starej zawartości, jeśli dysponują kopią starego klucza dzierżawy.

-   Uważasz, że zostało naruszone bezpieczeństwo kopii głównej klucza dzierżawy, która należy do Ciebie.

Po ponownym utworzeniu klucza dzierżawy nowa zawartość jest chroniona przy użyciu nowego klucza dzierżawy. Następuje to etapowo, w związku z czym przez pewien czas część nowej zawartości będzie nadal chroniona przez stary klucz dzierżawy. Zawartość chroniona wcześniej jest nadal chroniona przez stary klucz dzierżawy. W celu obsługi tego scenariusza usługa Azure Information Protection zachowuje stary klucz dzierżawy, co pozwala na wydawanie licencji dla starszej zawartości.

Aby ponownie utworzyć klucz dzierżawy, najpierw utwórz ponownie klucz dzierżawy usługi Azure Information Protection w usłudze Key Vault. Następnie uruchom ponownie polecenie cmdlet [Use-AadrmKeyVaultKey](/powershell/module/aadrm/use-aadrmkeyvaultkey), określając nowy adres URL klucza.

## Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy
<a id="backup-and-recover-your-tenant-key" class="xliff"></a>
Twoim obowiązkiem jest utworzenie kopii zapasowej klucza dzierżawy. Jeśli klucz dzierżawy wygenerowano za pomocą sprzętowego modułu zabezpieczeń firmy Thales, to aby utworzyć kopię zapasową klucza, wystarczy utworzyć kopię zapasową pliku stokenizowanego klucza, pliku środowiska zabezpieczeń oraz kart administratora.

Jako że klucz przeniesiono zgodnie z instrukcjami opisanymi w sekcji dotyczącej [wdrażania scenariusza BYOK](../plan-design/plan-implement-tenant-key.md#implementing-your-azure-information-protection-tenant-key) w artykule [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](../plan-design/plan-implement-tenant-key.md), usługa Key Vault utrwali plik stokenizowanego klucza w celu zapewnienia ochrony przed awariami jakichkolwiek węzłów usługi. Ten plik jest powiązany ze środowiskiem zabezpieczeń dla konkretnego regionu lub wystąpienia platformy Azure. Jednak nie należy traktować tego działania jako utworzenia pełnej kopii zapasowej. Na przykład w razie konieczności użycia kopii klucza w postaci zwykłego tekstu poza sprzętowym modułem zabezpieczeń firmy Thales usługa Azure Key Vault nie będzie w stanie automatycznie pobrać kopii klucza, ponieważ jej przywrócenie nie będzie możliwe.

## Eksport klucza dzierżawy
<a id="export-your-tenant-key" class="xliff"></a>
W przypadku korzystania z rozwiązania BYOK nie można wyeksportować klucza dzierżawy ani z usługi Azure Key Vault, ani z usługi Azure Information Protection. Przywrócenie kopii klucza znajdującej się w usłudze Azure Key Vault nie jest możliwe. 

## Reakcja na naruszenie zabezpieczeń
<a id="respond-to-a-breach" class="xliff"></a>
Żaden system zabezpieczeń, niezależnie od jego siły, nie jest kompletny bez procedur reakcji na naruszenie zabezpieczeń. Klucz dzierżawy może zostać naruszony lub skradziony. Nawet w przypadku zapewnienia odpowiedniej ochrony klucza mogą występować luki w zabezpieczeniach dotyczące obecnej generacji technologii sprzętowych modułów zabezpieczeń, długości kluczy i algorytmów.

Firma Microsoft ma dedykowany zespół, który reaguje na przypadki naruszenia zabezpieczeń produktów i usług. Bezpośrednio po uzyskaniu wiarygodnego raportu o incydencie zespół ten bada jego zakres, przyczynę i środki naprawcze. Jeśli dane zdarzenie ma wpływ na Twoje zasoby, firma Microsoft powiadomi o tym administratorów dzierżawy usługi Azure Information Protection pocztą e-mail, korzystając z adresu podanego podczas rejestrowania subskrypcji.

W przypadku naruszenia zabezpieczeń najlepsze działanie, które może podjąć użytkownik lub firma Microsoft, jest zależne od zakresu naruszenia. Firma Microsoft zapewnia wsparcie w tym procesie. Poniższa tabela zawiera typowe sytuacje i prawdopodobne reakcje, choć dokładna reakcja jest zależna od informacji uzyskanych w trakcie badania.

|Opis zdarzenia|Prawdopodobna reakcja|
|------------------------|-------------------|
|Przeciek klucza dzierżawy.|Utwórz ponownie klucz dzierżawy Zobacz [Ponowne tworzenie klucza dzierżawy](#re-key-your-tenant-key).|
|Nieautoryzowana osoba lub złośliwe oprogramowanie uzyskało prawa do korzystania z klucza dzierżawy, ale nie nastąpił przeciek samego klucza.|Ponowne utworzenie klucza dzierżawy nie jest pomocne w tym przypadku, problem wymaga analizy przyczyny. Jeśli za uzyskanie dostępu przez nieautoryzowaną osobę odpowiada proces lub błąd oprogramowania, sytuację należy rozwiązać.|
|Odkryto lukę w zabezpieczeniach obecnej generacji technologii sprzętowych modułów zabezpieczeń.|Firma Microsoft musi zaktualizować sprzętowe moduły zabezpieczeń. W przypadku podejrzeń, że usterka spowodowała ujawnienie kluczy, firma Microsoft wyśle instrukcje do wszystkich klientów dotyczące odnowienia kluczy dzierżawy.|
|Odkryto lukę w zabezpieczeniach algorytmu RSA lub długości klucza albo ataki siłowe stały się wykonalne.|Firma Microsoft musi zaktualizować usługę Azure Key Vault lub Azure Information Protection o obsługę nowych algorytmów i dłuższych kluczy o większej odporności, a także poinstruować wszystkich klientów o konieczności odnowienia kluczy dzierżawy.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

