---
title: "Często zadawane pytania dotyczące klasyfikacji i etykietowania — AIP"
description: "Masz pytanie związane z usługą Azure Information Protection, które dotyczy klasyfikacji i etykietowania? Zobacz, czy nie znajdziesz tutaj odpowiedzi."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: f35385284e40ad8e40bf9007b92b9b64b4df9280
ms.sourcegitcommit: d814d2876cf56e8fff0b107a5e3ec6df2aeda9ae
translationtype: HT
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Często zadawane pytania dotyczące klasyfikacji i etykietowania w usłudze Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Masz pytanie związane z usługą Azure Information Protection, które dotyczy klasyfikacji i etykietowania?  Zobacz, czy nie znajdziesz tutaj odpowiedzi. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Jakie czynności mogę wykonywać za pomocą funkcji klasyfikacji w usłudze Azure Information Protection?

Kilka minut wystarczy do zapoznania się z naszym samouczkiem Szybki start: [Samouczek Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).

W blogu [dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) i witrynie [Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) będą się pojawiać ogłoszenia o dostępności dodatkowych funkcji i możliwości klasyfikacji. W bieżącej wersji występuje kilka ograniczeń, m.in.:

- Nazwy etykiet i etykietki narzędzi są obsługiwane tylko w jednym języku.

- Brak centralnego rejestrowania dla funkcji klasyfikacji i etykietowania.

- Warunkami klasyfikacji automatycznej muszą być frazy lub wzorce.

- Brak możliwości etykietowania dla aplikacji pakietu Office dla komputerów Mac i urządzeń przenośnych (z systemami iOS lub Android) oraz aplikacji sieci Web pakietu Office (Office Online).

- Brak integracji klasyfikacji i etykietowania z programem Exchange Online i usługą SharePoint Online.

- Zestaw SDK dla deweloperów i partnerów nie obejmuje jeszcze klasyfikacji i etykietowania.

W wersji z lutego usunięto wiele wcześniejszych ograniczeń. Aby uzyskać więcej informacji, zobacz [wpis w blogu](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/).

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>Czy muszę być administratorem globalnym, aby konfigurować klasyfikację i etykiety?

Aby skonfigurować zasady usługi Azure Information Protection, już nie musisz logować się do witryny Azure Portal jako administrator globalny usługi Azure Active Directory. Możesz również teraz użyć konta mającego rolę administratora zabezpieczeń.

Jeśli w trakcie instalacji [klienta usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) wybrano opcję zainstalowania zasad demonstracyjnych, zalogowanie się do portalu nie jest konieczne do wyświetlenia i wypróbowania funkcji etykietowania. Zasada demonstracyjna instaluje lokalnie zasadę domyślną usługi Azure Information Protection, co umożliwia próby etykietowania dokumentów i wiadomości e-mail, ale nie pozwala na zmianę ani dodanie nowej etykiety bez rejestrowania się w witrynie Azure Portal. 

## <a name="which-options-in-the-azure-portal-are-p2"></a>Które opcje w witrynie Azure Portal to P2?

Opcje w witrynie Azure Portal, które wymagają usługi **Azure Information Protection Premium 2** (P2), mają teraz komunikat podręczny z informacjami umożliwiający ich zidentyfikowanie. Aby uzyskać więcej informacji o tym, które funkcje są uwzględnione w subskrypcjach P1 i P2, zobacz [listę funkcji](https://www.microsoft.com/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection.

## <a name="can-a-file-have-more-than-one-classification"></a>Czy plik może mieć więcej niż jedną klasyfikację?

Użytkownicy mogą jednocześnie wybrać tylko jedną etykietę dla każdego dokumentu lub wiadomości e-mail, co skutkuje często utworzeniem tylko jednej klasyfikacji. Jeśli jednak użytkownicy wybiorą etykietę podrzędną, spowoduje to w rzeczywistości zastosowanie dwóch etykiet jednocześnie: etykiety podstawowej i pomocniczej. Dzięki użyciu etykiet podrzędnych plik może mieć dwie klasyfikacje, które wprowadzają relację typu element nadrzędny/podrzędny na potrzeby dodatkowego poziomu kontroli.

Na przykład etykieta **Poufne** może zawierać etykiety podrzędne, takie jak **Prawne** i **Finanse**. Tym etykietom podrzędnym można przypisać różne wizualne oznaczenia klasyfikacji i różne szablony usługi Rights Management. Użytkownik nie może wybrać bezpośrednio etykiety **Poufne**, a tylko jedną z jej etykiet podrzędnych, na przykład **Prawne**. W efekcie widzi on, że została ustawiona etykieta **Tajne\Prawne**. Metadane dla tego pliku zawierają jedną niestandardową właściwość tekstową dla etykiety **Poufne**, jedną niestandardową właściwość tekstową dla etykiety **Prawne** i jeszcze jedną właściwość, która zawiera obie wartości (**Poufne Prawne**). 

Jeśli korzystasz z etykiet podrzędnych, nie konfiguruj wizualnych oznaczeń, ochrony i warunków dla etykiety podstawowej. Jeśli korzystasz z poziomów podrzędnych, skonfiguruj te ustawienia tylko dla etykiet podrzędnych. Jeśli skonfigurujesz te ustawienia dla etykiety podstawowej i jej etykiety podrzędnej, pierwszeństwo mają ustawienia etykiety podrzędnej.

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Czy gdy wiadomość e-mail jest oznaczona, pewne załączniki automatycznie uzyskają tę samą etykietę?

Nie. Jeśli wiadomość e-mail zawierająca załączniki zostanie oznaczona, załączniki te nie odziedziczą tej samej etykiety. Załączniki pozostaną bez etykiety lub zachowają oddzielnie przydzieloną etykietę. Jednak jeśli etykieta wiadomości e-mail zawiera ochronę, ochrona ta jest stosowana także do załączników.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Jak rozwiązania DLP i inne aplikacje integrują się z usługą Azure Information Protection?

Ponieważ usługa Azure Information Protection używa do klasyfikacji trwałych metadanych, w tym etykiety w postaci zwykłego tekstu, te informacje są odczytywane przez rozwiązania DLP i inne aplikacje. W plikach metadane te są przechowywane we właściwościach niestandardowych; w wiadomościach e-mail znajdują się one w nagłówkach.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Czym różni się klasyfikacja wiadomości e-mail usługi Azure Information Protection od klasyfikacji wiadomości e-mail stosowanej w programie Exchange?

Klasyfikacja wiadomości programu Exchange to starsza funkcja umożliwiająca klasyfikowanie wiadomości e-mail, wdrożona niezależnie od klasyfikacji usługi Azure Information Protection. Jednakże te dwa rozwiązania można zintegrować tak, aby podczas klasyfikowania przez użytkownika wiadomości e-mail w aplikacji sieci web Outlook lub w niektórych aplikacjach poczty w urządzeniach przenośnych następowało automatyczne klasyfikowanie w ramach usługi Azure Information Protection i dodawanie odpowiadających jej oznaczeń etykiet. Program Exchange dodaje klasyfikację, a klient usługi Azure Information Protection stosuje odpowiednie ustawienia etykiet dla danej klasyfikacji.

Mimo że aplikacja sieci web Outlook nie obsługuje jeszcze natywnie klasyfikacji i ochrony usługi Azure Information Protection, można użyć tej samej techniki, aby móc używać własnych etykiet nie tylko z klientem programu Outlook na komputerze, ale też z tym klientem poczty e-mail.

W tym celu: 

1. Użyj polecenia cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) środowiska PowerShell programu Exchange w celu utworzenia klasyfikacji wiadomości z właściwością Name, która mapuje do nazw etykiet użytkownika w zasadach usługi Azure Information Protection. 

2. Utwórz dla każdej etykiety regułę transportu programu Exchange: zastosuj regułę, jeśli właściwości wiadomości obejmują skonfigurowaną przez Ciebie klasyfikację, a następnie zmodyfikuj właściwości wiadomości, aby ustawić nagłówek wiadomości. 

    Informacje, jakie należy określić dla nagłówka wiadomości, można zidentyfikować, sprawdzając nagłówki internetowe wiadomości e-mail wysłanej i sklasyfikowanej za pomocą etykiety usługi Azure Information Protection. Wyszukaj nagłówek **msip_labels** i ciąg, który następuje zaraz po nim, łącznie ze średnikiem. Korzystając z poprzedniego przykładu:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Następnie dla nagłówka wiadomości w regule określ element **msip_labels** dla nagłówka oraz pozostałe elementy ciągu dla wartości nagłówka. Na przykład:
    
    ![Przykładowa reguła transportu usługi Exchange Online, która ustawia nagłówek wiadomości dla określonej etykiety usługi Azure Information Protection](../media/exchange-rule-for-message-header.png)

Zanim to przetestujesz, pamiętaj, że podczas tworzenia lub edytowania reguł transportu często występuje opóźnienie (na przykład trzeba odczekać godzinę). Jednak gdy reguła jest aktywna, w przypadku użytkowników, którzy używają aplikacji Outlook Web Access lub klienta urządzenia przenośnego obsługującego ochronę za pomocą usługi Rights Management, ma miejsce następujący scenariusz: 

- Użytkownicy wybierają klasyfikację wiadomości programu Exchange i wysyłają wiadomość e-mail.

- Reguła programu Exchange wykrywa klasyfikację programu Exchange i odpowiednio modyfikuje nagłówek wiadomości w celu dodania klasyfikacji usługi Azure Information Protection.

- Gdy adresaci korzystający z klienta usługi Azure Information Protection wyświetlają wiadomość e-mail w programie Outlook, widzą przypisane etykiety usługi Azure Information Protection i wszelkie powiązane nagłówki wiadomości e-mail, stopki lub znaki wodne. 

Jeśli etykiety usługi Azure Information Protection zakładają zastosowanie ochrony zarządzania prawami, dodaj tę ochronę do konfiguracji reguły, zaznaczając opcję modyfikacji zabezpieczeń wiadomości, zastosuj ochronę praw, a następnie wybierz szablon RMS lub opcję Nie przesyłaj dalej.

Możesz również skonfigurować reguły transportu na potrzeby mapowania odwrotnego. W tym celu po wykryciu etykiety usługi Azure Information Protection ustaw odpowiednią klasyfikację wiadomości programu Exchange. Wykonaj następujące czynności:

- Dla każdej etykiety usługi Azure Information Protection utwórz regułę transportu, która będzie stosowana, jeśli nagłówek **msip_labels** będzie zawierał nazwę Twojej etykiety (na przykład **Ogólne**), i zastosuj klasyfikację wiadomości mapowaną do tej etykiety.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
