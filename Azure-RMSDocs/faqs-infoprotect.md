---
title: Często zadawane pytania dotyczące klasyfikacji i etykietowania — AIP
description: Masz pytanie związane z usługą Azure Information Protection, które dotyczy klasyfikacji i etykietowania? Zobacz, czy nie znajdziesz tutaj odpowiedzi.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/27/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: ac127067999876d82434f3aab9e744a2eb174641
ms.sourcegitcommit: 5b4eb0e17fb831d338d8c25844e9e6f4ca72246d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53173506"
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Często zadawane pytania dotyczące klasyfikacji i etykietowania w usłudze Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Masz pytanie związane z usługą Azure Information Protection, które dotyczy klasyfikacji i etykietowania?  Zobacz, czy nie znajdziesz tutaj odpowiedzi. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Jakie czynności mogę wykonywać za pomocą funkcji klasyfikacji w usłudze Azure Information Protection?

Wypróbuj nasze [edytować zasady i Utwórz nową etykietę](infoprotect-quick-start-tutorial.md) samouczka, aby zobaczyć, w tym pracę w ciągu kilku minut.

Zwróć uwagę na anonsów, [pakietu Enterprise Mobility + Security blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity/label-name/Azure%20Information%20Protection) i naszej [witryny usługi Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) klasyfikacji dodatkowe funkcje i możliwości będą się dostępne. W bieżącej wersji występuje kilka ograniczeń, m.in.:

- Brak możliwości etykietowania w aplikacjach sieci web pakietu Office (Office Online).

- Brak integracji klasyfikacji i etykietowania z programem Exchange Online i usługą SharePoint Online.

> [!NOTE]
> **Teraz w wersji zapoznawczej**:
> - Scentralizowane raportowanie dla klasyfikacji i etykietowania. Aby uzyskać więcej informacji, zobacz [centralnej funkcji raportowania usługi Azure Information Protection](reports-aip.md).
> - Możliwości w aplikacji pakietu Office dla urządzeń przenośnych (iOS i Android) i komputerów Mac dla klientów, którzy są w wyrażeniu zgody na uczestnictwo w celu etykietowanie [Office niejawnego programu testów](https://support.office.com/article/what-is-office-insider-f4208185-b63a-4b68-9c7a-9a32d2411c16). Aby uzyskać więcej informacji, zobacz [zastosować etykiety ważności do dokumentów i wiadomości e-mail w pakiecie Office](https://aka.ms/officemipdocs).


Poprosić o nowe funkcje i oddawać głosy na żądania, odwiedzając [witryny UserVoice](https://msip.uservoice.com/) usługi Azure Information Protection.

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>Czy muszę być administratorem globalnym, aby konfigurować klasyfikację i etykiety?

Z rolą Administrator usługi Information Protection nowo wprowadzonych zostanie teraz udzielona odpowiedź na stronie głównej — często zadawane pytania: [Musisz być administratorem globalnym, aby skonfigurować usługę Azure Information Protection, czy można to oddelegować do innych administratorów?](faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators)

Jeśli w trakcie instalacji [klienta usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) wybrano opcję zainstalowania zasad demonstracyjnych, zalogowanie się do portalu nie jest konieczne do wyświetlenia i wypróbowania funkcji etykietowania. Zasada demonstracyjna instaluje lokalnie zasadę domyślną usługi Azure Information Protection, co umożliwia próby etykietowania dokumentów i wiadomości e-mail, ale nie można zmienić ani dodanie nowej etykiety bez rejestrowania się w witrynie Azure portal. 

## <a name="can-a-file-have-more-than-one-classification"></a>Czy plik może mieć więcej niż jedną klasyfikację?

Użytkownicy mogą jednocześnie wybrać tylko jedną etykietę dla każdego dokumentu lub wiadomości e-mail, co skutkuje często utworzeniem tylko jednej klasyfikacji. Jednakże jeśli użytkownicy wybiorą etykietę podrzędną, to rzeczywistości zastosowanie dwóch etykiet jednocześnie; etykiety podstawowej i pomocniczej. Korzystając z etykiet podrzędnych plik może mieć dwie klasyfikacje, które wprowadzają relację dodatkowy poziom kontroli.

Na przykład etykieta **poufne** może zawierać etykiet podrzędnych, takie jak **prawne** i **Finance**. Przypisać różne wizualne oznaczenia klasyfikacji i różne szablony usługi Rights Management można zastosować do tych etykiet podrzędnych. Użytkownik nie może wybrać **poufne** bezpośrednio etykiety, tylko jedną z jej etykiet podrzędnych, takich jak **prawne**. W efekcie widzi on, że została ustawiona etykieta **Tajne\Prawne**. Metadane dla tego pliku zawierają jedną niestandardową właściwość tekstową dla etykiety **Poufne**, jedną niestandardową właściwość tekstową dla etykiety **Prawne** i jeszcze jedną właściwość, która zawiera obie wartości (**Poufne Prawne**). 

Użycie opcji etykiet podrzędnych, nie należy konfigurować oznaczenia wizualne, ochronę i warunków dla etykiety podstawowej. Gdy używasz poziomy podrzędne, należy skonfigurować te ustawienia na etykietę podrzędną w tylko. Jeśli skonfigurujesz te ustawienia dotyczące etykiety podstawowej i jej etykiety podrzędnej ustawienia na etykietę podrzędną wyższy priorytet.

## <a name="how-do-i-prevent-somebody-from-removing-or-changing-a-label"></a>Jak zapobiec ktoś usuwanie i zmienianie etykiety

Mimo że istnieje [ustawienie zasad](configure-policy-settings.md) , wymaga od użytkowników do stanu, dlaczego one obniżany etykietę klasyfikacji, usunięcie etykiety lub usunięcie ochrony, to ustawienie nie zapobiega te akcje. Aby uniemożliwić użytkownikom usuwanie i zmienianie etykiety, musi już chroniona zawartość i uprawnienia ochrony nie użytkownikowi należy przydzielić Eksport lub Pełna kontrola [prawa użytkowania](configure-usage-rights.md). 

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Czy gdy wiadomość e-mail jest oznaczona, pewne załączniki automatycznie uzyskają tę samą etykietę?

Nie. Jeśli wiadomość e-mail zawierająca załączniki zostanie oznaczona, załączniki te nie odziedziczą tej samej etykiety. Załączniki pozostaną bez etykiety lub zachowają oddzielnie przydzieloną etykietę. Jeśli etykieta wiadomości e-mail, Ustawia ochronę, ochrona ta jest stosowana do załączników pakietu Office.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Jak rozwiązania DLP i inne aplikacje integrują się z usługą Azure Information Protection?

Ponieważ usługi Azure Information Protection używa trwałych metadanych do klasyfikacji, która zawiera etykiety zwykłego tekstu, te informacje mogą być odczytywane przez rozwiązania DLP i inne aplikacje. 

Aby uzyskać więcej informacji i przykłady użycia tego metadanych przy użyciu usługi Exchange Online reguły przepływu poczty, zobacz [konfigurowania usługi Exchange Online reguły przepływu poczty dla etykiety usługi Azure Information Protection](configure-exo-rules.md).

## <a name="can-i-create-a-document-template-that-automatically-includes-the-classification"></a>Można utworzyć szablon dokumentu, który automatycznie dołącza klasyfikacji?

Tak. Można skonfigurować etykietę w celu [zastosowanie nagłówka lub stopki, która zawiera nazwę etykiety](configure-policy-markings.md). Ale jeśli który nie spełnia wymagań, można utworzyć szablon dokumentu, który ma formatowanie i Dodaj klasyfikacji jako kod pola. 

Na przykład może być tabelą w nagłówku w dokumencie, który wyświetla klasyfikacji. Możesz też korzystać konkretne sformułowania wprowadzenie, który odwołuje się Klasyfikacja dokumentów.

Aby dodać ten kod pola w dokumencie:

1. Oznaczania dokumentów i zapisz go. Ta akcja tworzy nowe pola metadanych, które można teraz używać kodu pola.

2. W dokumencie, umieść kursor w miejscu, w którym chcesz dodać etykiety klasyfikacji i następnie **Wstaw** zaznacz **tekstu** > **Szybkie części**  >  **Pola**.

3. W **pola** okno dialogowe z **kategorie** listy rozwijanej wybierz **informacji o dokumencie**. Następnie w **pola nazwy** listy rozwijanej wybierz **DocProperty**.

4. Z **właściwość** listy rozwijanej wybierz **czułości**i wybierz **OK**.

Bieżącą etykietę klasyfikacji jest wyświetlana w dokumencie, a ta wartość będzie odświeżana automatycznie przy każdym Otwórz dokument, lub użyj szablonu. Dlatego jeśli zmieni się etykieta klasyfikację, która jest wyświetlana dla tego pola kodu jest automatycznie aktualizowana w dokumencie.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Czym różni się klasyfikacja wiadomości e-mail usługi Azure Information Protection od klasyfikacji wiadomości e-mail stosowanej w programie Exchange?

Klasyfikacja wiadomości programu Exchange to starsza funkcja umożliwiająca klasyfikowanie wiadomości e-mail, wdrożona niezależnie od klasyfikacji usługi Azure Information Protection. 

Jednakże te dwa rozwiązania można zintegrować tak, aby podczas klasyfikowania przez użytkownika wiadomości e-mail w aplikacji sieci Web Outlook lub w niektórych aplikacjach poczty w urządzeniach przenośnych następowało automatyczne klasyfikowanie w ramach usługi Azure Information Protection i dodawanie odpowiadających jej oznaczeń etykiet. 

Tego samego sposobu można użyć do zastosowania etykiet w programie Outlook w sieci Web oraz w aplikacjach poczty dla urządzeń przenośnych.

Czynności konfiguracyjne są opisane w sekcji [Integracja klasyfikacji wiadomości programu Exchange z usługą Azure Information Protection dla rozwiązań etykietowania urządzeń przenośnych](./rms-client/client-admin-guide-customizations.md#integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution). 



