---
title: "Operacje cyklu życia klucza dzierżawy zarządzane przez klienta | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: 496edca2e2323e17216858e2ab4844fdb0aa1fb0


---


# Operacje cyklu życia klucza dzierżawy zarządzane przez klienta

*Dotyczy usług: Azure Rights Management, Office 365*

Jeśli samodzielnie zarządzasz swoim kluczem dzierżawy dla usługi Azure Rights Management (zgodnie ze scenariuszem BYOK, ang. Bring Your Own Key — „użyj własnego klucza”), użyj poniższych sekcji w celu uzyskania dodatkowych informacji na temat operacji cyklu życia związanych z tą topologią.

## Odwołanie klucza dzierżawy
Po anulowaniu subskrypcji usługi Azure RMS usługa ta wstrzymuje korzystanie z klucza dzierżawy, co nie wymaga żadnej akcji ze strony użytkownika.

## Ponowne tworzenie klucza dzierżawy
Ponowne tworzenie jest nazywane także wycofywaniem klucza. Klucza dzierżawy nie należy tworzyć ponownie, jeśli nie jest to naprawdę konieczne. Starsze programy klienckie, takie jak Office 2010, nie zostały zaprojektowane do bezproblemowej zmiany klucza. W tym scenariuszu należy usunąć stan usługi RMS na komputerach przy użyciu zasad grupy lub równoważnego mechanizmu. Występują jednak określone zdarzenia, które mogą wymusić ponowne utworzenie klucza dzierżawy. Na przykład:

-   Firma została podzielona na dwie lub więcej firm. Po ponownym utworzeniu klucza dzierżawy nowa firma nie będzie miała dostępu do nowej zawartości publikowanej przez pracowników. Mogą oni uzyskać dostęp do starej zawartości, jeśli dysponują kopią starego klucza dzierżawy.

-   Uważasz, że zostało naruszone bezpieczeństwo kopii głównej klucza dzierżawy, która należy do Ciebie.

Po ponownym utworzeniu klucza dzierżawy nowa zawartość jest chroniona przy użyciu nowego klucza dzierżawy. Następuje to etapowo, w związku z czym przez pewien czas część nowej zawartości będzie nadal chroniona przez stary klucz dzierżawy. Zawartość chroniona wcześniej jest nadal chroniona przez stary klucz dzierżawy. W celu obsługi tego scenariusza usługa Azure RMS zachowuje stary klucz dzierżawy, co pozwala na wydawanie licencji dla starszej zawartości.

Aby ponownie utworzyć klucz dzierżawy, wygeneruj i utwórz nowy klucz przez Internet lub osobiście, korzystając z instrukcji opisanych w sekcji dotyczącej [wdrażania scenariusza BYOK („użyj własnego klucza”)](..\plan-design\plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) w temacie [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](..\plan-design\plan-implement-tenant-key.md).

## Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy
Twoim obowiązkiem jest utworzenie kopii zapasowej klucza dzierżawy. Jeśli klucz dzierżawy wygenerowano za pomocą sprzętowego modułu zabezpieczeń firmy Thales, to aby utworzyć kopię zapasową klucza, wystarczy utworzyć kopię zapasową pliku stokenizowanego klucza, pliku środowiska zabezpieczeń oraz kart administratora.

Jeśli klucz przeniesiono zgodnie z instrukcjami opisanymi w sekcji dotyczącej [wdrażania scenariusza BYOK](../plan-design/plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) w artykule [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](../plan-design/plan-implement-tenant-key.md), usługa Azure RMS utrwali plik stokenizowanego klucza w celu zapewnienia ochrony przed awariami jakichkolwiek węzłów usługi Azure RMS. Jednak nie należy traktować tego działania jako utworzenia pełnej kopii zapasowej. Na przykład w razie konieczności użycia kopii klucza w postaci zwykłego tekstu poza sprzętowym modułem zabezpieczeń firmy Thales usługa Azure RMS nie będzie w stanie automatycznie pobrać kopii klucza, ponieważ jej przywrócenie nie będzie możliwe.

## Eksport klucza dzierżawy
W przypadku korzystania z modelu BYOK nie można wyeksportować klucza dzierżawy z usługi Azure RMS. Przywrócenie kopii klucza znajdującej się w usłudze Azure RMS nie jest możliwe. Jeśli chcesz usunąć ten klucz i uniemożliwić jego używanie, skontaktuj się z działem obsługi klienta firmy Microsoft.

## Reakcja na naruszenie zabezpieczeń
Żaden system zabezpieczeń, niezależnie od jego siły, nie jest kompletny bez procedur reakcji na naruszenie zabezpieczeń. Klucz dzierżawy może zostać naruszony lub skradziony. Nawet w przypadku zapewnienia odpowiedniej ochrony klucza mogą występować luki w zabezpieczeniach dotyczące obecnej generacji technologii sprzętowych modułów zabezpieczeń, długości kluczy i algorytmów.

Firma Microsoft ma dedykowany zespół, który reaguje na przypadki naruszenia zabezpieczeń produktów i usług. Bezpośrednio po uzyskaniu wiarygodnego raportu o incydencie zespół ten bada jego zakres, przyczynę i środki naprawcze. Jeśli dane zdarzenie dotyczy Twoich zasobów, firma Microsoft powiadomi o tym administratorów dzierżawy usługi Azure RMS pocztą e-mail, korzystając z adresu podanego podczas rejestrowania subskrypcji.

W przypadku naruszenia zabezpieczeń najlepsze działanie, które może podjąć użytkownik lub firma Microsoft, zależy od zakresu naruszenia. Firma Microsoft zapewnia wsparcie w tym procesie. Poniższa tabela zawiera typowe sytuacje i prawdopodobne reakcje, choć dokładna reakcja jest zależna od informacji uzyskanych w trakcie badania.

|Opis zdarzenia|Prawdopodobna reakcja|
|------------------------|-------------------|
|Przeciek klucza dzierżawy.|Utwórz ponownie klucz dzierżawy Zobacz [Ponowne tworzenie klucza dzierżawy](#re-key-your-tenant-key).|
|Nieautoryzowana osoba lub złośliwe oprogramowanie uzyskało prawa do korzystania z klucza dzierżawy, ale nie nastąpił przeciek samego klucza.|Ponowne utworzenie klucza dzierżawy nie jest pomocne w tym przypadku, problem wymaga analizy przyczyny. Jeśli za uzyskanie dostępu przez nieautoryzowaną osobę odpowiada proces lub błąd oprogramowania, sytuację należy rozwiązać.|
|Odkryto lukę w zabezpieczeniach obecnej generacji technologii sprzętowych modułów zabezpieczeń.|Firma Microsoft musi zaktualizować sprzętowe moduły zabezpieczeń. W przypadku podejrzeń, że usterka spowodowała ujawnienie kluczy, firma Microsoft wyśle instrukcje do wszystkich klientów dotyczące odnowienia kluczy dzierżawy.|
|Odkryto lukę w zabezpieczeniach algorytmu RSA lub długości klucza albo ataki siłowe stały się wykonalne.|Firma Microsoft musi zaktualizować usługę Azure RMS o obsługę nowych algorytmów i dłuższych kluczy o większej odporności, a także poinstruować wszystkich klientów o konieczności odnowienia kluczy dzierżawy.|





<!--HONumber=Jun16_HO4-->


