---
title: Często zadawane pytania dotyczące klasyfikacji i etykietowania — AIP
description: Masz pytanie związane z usługą Azure Information Protection, które dotyczy klasyfikacji i etykietowania? Zobacz, czy nie znajdziesz tutaj odpowiedzi.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: 24e99c6645832bcddbbf881a2b5728af3589f1e5
ms.sourcegitcommit: b17432ed155394111c878eb57b5fa7adf9df9755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Często zadawane pytania dotyczące klasyfikacji i etykietowania w usłudze Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Masz pytanie związane z usługą Azure Information Protection, które dotyczy klasyfikacji i etykietowania?  Zobacz, czy nie znajdziesz tutaj odpowiedzi. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Jakie czynności mogę wykonywać za pomocą funkcji klasyfikacji w usłudze Azure Information Protection?

Kilka minut wystarczy do zapoznania się z naszym samouczkiem Szybki start: [Samouczek Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).

W blogu [dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-information-protection) i witrynie [Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) będą się pojawiać ogłoszenia o dostępności dodatkowych funkcji i możliwości klasyfikacji. W bieżącej wersji występuje kilka ograniczeń, m.in.:

- Brak centralnego rejestrowania dla funkcji klasyfikacji i etykietowania.

- Mając na uwadze możliwości w aplikacji pakietu Office dla urządzeń przenośnych (iOS i Android) i komputerów Mac lub aplikacji sieci web pakietu Office (Office Online).

- Brak integracji klasyfikacji i etykietowania z programem Exchange Online i usługą SharePoint Online.

Żądanie nowych funkcji oraz oddawać głosy na żądania, odwiedzając [witryny User Voice](https://msip.uservoice.com/) usługi Azure Information Protection.

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>Czy muszę być administratorem globalnym, aby konfigurować klasyfikację i etykiety?

Z rolą administratora ochrony informacji nowo wprowadzonych to pytanie jest teraz odpowiedzi na stronie głównej — często zadawane pytania: [należy być administratorem globalnym, aby skonfigurować usługi Azure Information Protection, lub można oddelegować do innych administratorów?](faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators)

Jeśli w trakcie instalacji [klienta usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) wybrano opcję zainstalowania zasad demonstracyjnych, zalogowanie się do portalu nie jest konieczne do wyświetlenia i wypróbowania funkcji etykietowania. Zasada demonstracyjna instaluje lokalnie zasadę domyślną usługi Azure Information Protection umożliwia próby etykietowania dokumentów i wiadomości e-mail, ale nie można zmienić ani dodanie nowej etykiety bez rejestrowania się w portalu Azure. 

## <a name="can-a-file-have-more-than-one-classification"></a>Czy plik może mieć więcej niż jedną klasyfikację?

Użytkownicy mogą jednocześnie wybrać tylko jedną etykietę dla każdego dokumentu lub wiadomości e-mail, co skutkuje często utworzeniem tylko jednej klasyfikacji. Jednak jeśli użytkownicy wybierają sublabel, faktycznie dotyczy dwóch etykiet w tym samym czasie; Etykieta głównej i dodatkowej etykiety. Przy użyciu sublabels, plik może mieć dwie klasyfikacje, które oznaczają relacji parent\child dodatkowy poziom kontroli.

Na przykład etykieta **poufne** może zawierać takie jak sublabels **prawne** i **Finance**. Aby te sublabels można stosować różne wizualne oznaczenia klasyfikacji i różne szablony usługi Rights Management. Nie można wybrać użytkownika **poufne** etykiety samodzielnie; tylko jeden z jego sublabels, takich jak **prawne**. W efekcie widzi on, że została ustawiona etykieta **Tajne\Prawne**. Metadane dla tego pliku zawierają jedną niestandardową właściwość tekstową dla etykiety **Poufne**, jedną niestandardową właściwość tekstową dla etykiety **Prawne** i jeszcze jedną właściwość, która zawiera obie wartości (**Poufne Prawne**). 

Gdy używasz sublabels nie skonfigurować oznaczenia wizualne, ochronę i warunki w głównej etykiety. Gdy używasz poziomy podrzędne, skonfiguruj te ustawienia na sublabel tylko. Jeśli te ustawienia można skonfigurować na etykiecie głównej i jego sublabel, ustawienia w sublabel mają pierwszeństwo.

## <a name="how-do-i-prevent-somebody-from-removing-or-changing-a-label"></a>Jak zapobiec ktoś z usunięcie lub zmiana etykiety

Mimo że [ustawienie zasad](../deploy-use/configure-policy-settings.md) który wymaga od użytkowników do stanu Dlaczego obniżenia etykiety klasyfikacji, usuwanie etykietę, lub usunięcie ochrony, to ustawienie nie zapobiega te akcje. Aby uniemożliwić użytkownikom usuwanie lub zmiana etykiety, musi już chronione zawartości i uprawnienia ochrony nie Przyznaj użytkownikowi, eksportu lub Pełna kontrola [prawa użytkowania](../deploy-use/configure-usage-rights.md). 

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Czy gdy wiadomość e-mail jest oznaczona, pewne załączniki automatycznie uzyskają tę samą etykietę?

Nie. Jeśli wiadomość e-mail zawierająca załączniki zostanie oznaczona, załączniki te nie odziedziczą tej samej etykiety. Załączniki pozostaną bez etykiety lub zachowają oddzielnie przydzieloną etykietę. Jednak jeśli etykieta wiadomości e-mail zawiera ochronę, ochrona ta jest stosowana także do załączników.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Jak rozwiązania DLP i inne aplikacje integrują się z usługą Azure Information Protection?

Ponieważ usługa Azure Information Protection używa do klasyfikacji trwałych metadanych, w tym etykiety w postaci zwykłego tekstu, te informacje są odczytywane przez rozwiązania DLP i inne aplikacje. 

- Dla dokumentów programu Word (.doc i .docx), arkusze programu Excel (xls i xlsx) prezentacji programu PowerPoint (ppt i pptx) i dokumentów PDF (PDF), te metadane są przechowywane w następujących właściwości niestandardowej: **MSIP_Label_\<GUID > _ Włączone = True**  

- W wiadomości e-mail, te informacje są przechowywane w nagłówku x: **msip_labels: MSIP_Label_\<GUID > _Enabled = True;**  

Aby określić identyfikator GUID dla etykiety, zlokalizowanie wartość Identyfikatora etykiety w bloku etykiety wyświetlanie lub konfigurowanie zasad usługi Azure Information Protection w portalu Azure. Dla plików, które mają zastosowane etykiety, można również uruchomić [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) polecenia cmdlet programu PowerShell w celu zidentyfikowania identyfikatora GUID (MainLabelId lub SubLabelId). Etykiety po sublabels należy zawsze podać identyfikator GUID właśnie sublabel i nie etykiety nadrzędnego.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Czym różni się klasyfikacja wiadomości e-mail usługi Azure Information Protection od klasyfikacji wiadomości e-mail stosowanej w programie Exchange?

Klasyfikacja wiadomości programu Exchange to starsza funkcja umożliwiająca klasyfikowanie wiadomości e-mail, wdrożona niezależnie od klasyfikacji usługi Azure Information Protection. 

Jednakże te dwa rozwiązania można zintegrować tak, aby podczas klasyfikowania przez użytkownika wiadomości e-mail w aplikacji sieci Web Outlook lub w niektórych aplikacjach poczty w urządzeniach przenośnych następowało automatyczne klasyfikowanie w ramach usługi Azure Information Protection i dodawanie odpowiadających jej oznaczeń etykiet. 

Tego samego sposobu można użyć do zastosowania etykiet w programie Outlook w sieci Web oraz w aplikacjach poczty dla urządzeń przenośnych.

Czynności konfiguracyjne są opisane w sekcji [Integracja klasyfikacji wiadomości programu Exchange z usługą Azure Information Protection dla rozwiązań etykietowania urządzeń przenośnych](../rms-client/client-admin-guide-customizations.md#integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution). 



[!INCLUDE[Commenting house rules](../includes/houserules.md)]
