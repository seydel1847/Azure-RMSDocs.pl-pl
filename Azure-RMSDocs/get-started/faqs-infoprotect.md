---
title: "Często zadawane pytania dotyczące klasyfikacji i etykietowania — AIP"
description: "Masz pytanie związane z usługą Azure Information Protection, które dotyczy klasyfikacji i etykietowania? Zobacz, czy nie znajdziesz tutaj odpowiedzi."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: 80efd633bc814af1ac28e4b6bf2d0b3062b27d01
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Często zadawane pytania dotyczące klasyfikacji i etykietowania w usłudze Azure Information Protection
<a id="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection" class="xliff"></a>

>*Dotyczy: Azure Information Protection, Office 365*

Masz pytanie związane z usługą Azure Information Protection, które dotyczy klasyfikacji i etykietowania?  Zobacz, czy nie znajdziesz tutaj odpowiedzi. 

## Jakie czynności mogę wykonywać za pomocą funkcji klasyfikacji w usłudze Azure Information Protection?
<a id="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection" class="xliff"></a>

Kilka minut wystarczy do zapoznania się z naszym samouczkiem Szybki start: [Samouczek Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).

W blogu [dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) i witrynie [Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) będą się pojawiać ogłoszenia o dostępności dodatkowych funkcji i możliwości klasyfikacji. W bieżącej wersji występuje kilka ograniczeń, m.in.:

- Nazwy etykiet i etykietki narzędzi są obsługiwane tylko w jednym języku. Obsługa wielu języków jest obecnie dostępna w wersji zapoznawczej. Więcej informacji można znaleźć w sekcji [Konfigurowanie etykiet w różnych językach](../deploy-use/configure-policy-languages.md).

- Brak centralnego rejestrowania dla funkcji klasyfikacji i etykietowania.

- Warunkami klasyfikacji automatycznej muszą być frazy lub wzorce.

- Brak możliwości etykietowania dla aplikacji pakietu Office dla komputerów Mac i urządzeń przenośnych (z systemami iOS lub Android) oraz aplikacji sieci Web pakietu Office (Office Online).

- Brak integracji klasyfikacji i etykietowania z programem Exchange Online i usługą SharePoint Online.

- Zestaw SDK dla deweloperów i partnerów nie obejmuje jeszcze klasyfikacji i etykietowania.

W wersji z lutego usunięto wiele wcześniejszych ograniczeń. Aby uzyskać więcej informacji, zobacz [wpis w blogu](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/).

## Czy muszę być administratorem globalnym, aby konfigurować klasyfikację i etykiety?
<a id="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels" class="xliff"></a>

Aby skonfigurować zasady usługi Azure Information Protection, już nie musisz logować się do witryny Azure Portal jako administrator globalny usługi Azure Active Directory. Możesz również teraz użyć konta mającego rolę administratora zabezpieczeń.

Jeśli w trakcie instalacji [klienta usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) wybrano opcję zainstalowania zasad demonstracyjnych, zalogowanie się do portalu nie jest konieczne do wyświetlenia i wypróbowania funkcji etykietowania. Zasada demonstracyjna instaluje lokalnie zasadę domyślną usługi Azure Information Protection, co umożliwia próby etykietowania dokumentów i wiadomości e-mail, ale nie pozwala na zmianę ani dodanie nowej etykiety bez rejestrowania się w witrynie Azure Portal. 

## Które opcje w witrynie Azure Portal to P2?
<a id="which-options-in-the-azure-portal-are-p2" class="xliff"></a>

Opcje w witrynie Azure Portal, które wymagają usługi **Azure Information Protection Premium 2** (P2), mają teraz komunikat podręczny z informacjami umożliwiający ich zidentyfikowanie. Aby uzyskać więcej informacji o tym, które funkcje są uwzględnione w subskrypcjach P1 i P2, zobacz [listę funkcji](https://www.microsoft.com/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection.

## Czy plik może mieć więcej niż jedną klasyfikację?
<a id="can-a-file-have-more-than-one-classification" class="xliff"></a>

Użytkownicy mogą jednocześnie wybrać tylko jedną etykietę dla każdego dokumentu lub wiadomości e-mail, co skutkuje często utworzeniem tylko jednej klasyfikacji. Jeśli jednak użytkownicy wybiorą etykietę podrzędną, spowoduje to w rzeczywistości zastosowanie dwóch etykiet jednocześnie: etykiety podstawowej i pomocniczej. Dzięki użyciu etykiet podrzędnych plik może mieć dwie klasyfikacje, które wprowadzają relację typu element nadrzędny/podrzędny na potrzeby dodatkowego poziomu kontroli.

Na przykład etykieta **Poufne** może zawierać etykiety podrzędne, takie jak **Prawne** i **Finanse**. Tym etykietom podrzędnym można przypisać różne wizualne oznaczenia klasyfikacji i różne szablony usługi Rights Management. Użytkownik nie może wybrać bezpośrednio etykiety **Poufne**, a tylko jedną z jej etykiet podrzędnych, na przykład **Prawne**. W efekcie widzi on, że została ustawiona etykieta **Tajne\Prawne**. Metadane dla tego pliku zawierają jedną niestandardową właściwość tekstową dla etykiety **Poufne**, jedną niestandardową właściwość tekstową dla etykiety **Prawne** i jeszcze jedną właściwość, która zawiera obie wartości (**Poufne Prawne**). 

Jeśli korzystasz z etykiet podrzędnych, nie konfiguruj wizualnych oznaczeń, ochrony i warunków dla etykiety podstawowej. Jeśli korzystasz z poziomów podrzędnych, skonfiguruj te ustawienia tylko dla etykiet podrzędnych. Jeśli skonfigurujesz te ustawienia dla etykiety podstawowej i jej etykiety podrzędnej, pierwszeństwo mają ustawienia etykiety podrzędnej.

## Czy gdy wiadomość e-mail jest oznaczona, pewne załączniki automatycznie uzyskają tę samą etykietę?
<a id="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling" class="xliff"></a>

Nie. Jeśli wiadomość e-mail zawierająca załączniki zostanie oznaczona, załączniki te nie odziedziczą tej samej etykiety. Załączniki pozostaną bez etykiety lub zachowają oddzielnie przydzieloną etykietę. Jednak jeśli etykieta wiadomości e-mail zawiera ochronę, ochrona ta jest stosowana także do załączników.

## Jak rozwiązania DLP i inne aplikacje integrują się z usługą Azure Information Protection?
<a id="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection" class="xliff"></a>

Ponieważ usługa Azure Information Protection używa do klasyfikacji trwałych metadanych, w tym etykiety w postaci zwykłego tekstu, te informacje są odczytywane przez rozwiązania DLP i inne aplikacje. W plikach te metadane są przechowywane we właściwościach niestandardowych. W wiadomościach e-mail te informacje znajdują się w nagłówkach wiadomości.

## Czym różni się klasyfikacja wiadomości e-mail usługi Azure Information Protection od klasyfikacji wiadomości e-mail stosowanej w programie Exchange?
<a id="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification" class="xliff"></a>

Klasyfikacja wiadomości programu Exchange to starsza funkcja umożliwiająca klasyfikowanie wiadomości e-mail, wdrożona niezależnie od klasyfikacji usługi Azure Information Protection. 

Jednakże te dwa rozwiązania można zintegrować tak, aby podczas klasyfikowania przez użytkownika wiadomości e-mail w aplikacji sieci Web Outlook lub w niektórych aplikacjach poczty w urządzeniach przenośnych następowało automatyczne klasyfikowanie w ramach usługi Azure Information Protection i dodawanie odpowiadających jej oznaczeń etykiet. 

Tego samego sposobu można użyć do zastosowania etykiet w programie Outlook w sieci Web oraz w aplikacjach poczty dla urządzeń przenośnych.

Czynności konfiguracyjne są opisane w sekcji [Integracja klasyfikacji wiadomości programu Exchange z usługą Azure Information Protection dla rozwiązań etykietowania urządzeń przenośnych](../rms-client/client-admin-guide-customizations.md#integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution). 



[!INCLUDE[Commenting house rules](../includes/houserules.md)]
