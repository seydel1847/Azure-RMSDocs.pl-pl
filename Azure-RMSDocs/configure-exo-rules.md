---
title: Konfigurowanie usługi Exchange Online reguły przepływu poczty dla etykiety usługi Azure Information Protection
description: Instrukcje i przykłady, aby skonfigurować usługi Exchange Online reguły przepływu poczty dla etykiety usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ba4e4a4d-5280-4e97-8f5c-303907db1bf5
ms.reviewer: shakella
ms.suite: ems
ms.openlocfilehash: c6f220e995aa785c44d4227884da2c7379918a8d
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305475"
---
# <a name="configuring-exchange-online-mail-flow-rules-for-azure-information-protection-labels"></a>Konfigurowanie reguły przepływu poczty usługi Exchange Online dla etykiety usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Skorzystaj z poniższych informacji, pomoże Ci w skonfigurowaniu reguły przepływu poczty programu Exchange Online korzystanie z etykiet usługi Azure Information Protection i zastosowanie dodatkową ochronę dla konkretnych scenariuszy. Przykład:

- Jest etykiety domyślnej **ogólne**, nie ma zastosowania ochrony. Dla wiadomości e-mail przy użyciu tej etykiety, które są wysyłane na zewnątrz należy zastosować dodatkowe nie przesyłaj dalej ochrony akcji.

- Jeśli załącznik z **poufne \ partnerzy** etykiety jest wysyłany pocztą e-mail do osób spoza organizacji i wiadomości e-mail nie jest chroniony, zastosuj akcję dodatkową ochronę tylko do szyfrowania.

Reguły przepływu poczty, informujące o objęciu ochroną jako akcję są ignorowane, jeśli wiadomość e-mail jest już chroniona. Na przykład wiadomości e-mail, który jest chroniony przez nie przesyłaj dalej nie można zmienić przez reguły przepływu poczty programu Exchange do korzystania z opcji tylko do szyfrowania.  

Można rozszerzyć te przykłady oraz jak je zmodyfikować. Na przykład dodać więcej warunków. Aby uzyskać więcej informacji na temat konfigurowania reguły przepływu poczty, zobacz [reguły przepływu poczty (reguł transportu) w usłudze Exchange Online] (https://technet.microsoft.com/library/jj919238(v=exchg.150\).aspx) w dokumentacji usługi Exchange Online.

Aby uzyskać więcej informacji na temat konfigurowania reguły przepływu poczty do szyfrowania wiadomości e-mail, zobacz [zdefiniować reguły przepływu poczty do szyfrowania wiadomości e-mail w usłudze Office 365](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8) w dokumentacji pakietu Office. 

## <a name="where-labels-are-stored-in-emails-and-documents"></a>Gdy etykiety są przechowywane w wiadomości e-mail i dokumentów

Ponieważ etykiety usługi Azure Information Protection jest przechowywany w metadanych przepływu poczty reguł w programie Exchange Online można przeczytać te informacje dotyczące wiadomości i załączników dokumentu:

- W wiadomościach e-mail te informacje są przechowywane w nagłówku x: **msip_labels: MSIP_Label_\<GUID > _Enabled = True;** 

- Dla dokumentów programu Word (doc i .docx), arkusze kalkulacyjne programu Excel (xls i xlsx), prezentacje programu PowerPoint (ppt i pptx) i dokumenty PDF (PDF) te metadane są przechowywane w następującymi niestandardowymi właściwościami: **MSIP_Label_\<GUID > _Enabled = True**  

Aby określić identyfikator GUID dla etykiety, Znajdź wartość Identyfikatora etykiety na **etykiety** bloku, wyświetlanie lub konfigurowanie zasad usługi Azure Information Protection w witrynie Azure portal. Dla plików, które mają stosowane etykiety, można również uruchomić [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) polecenia cmdlet programu PowerShell w celu zidentyfikowania identyfikatora GUID (MainLabelId lub SubLabelId). Jeśli etykieta ma etykiet podrzędnych, zawsze określać identyfikator GUID po prostu etykiety podrzędnej, a nie etykieta nadrzędnej.

Przed skonfigurowaniem reguł przepływu poczty, upewnij się, że znasz identyfikator GUID etykiety usługi Azure Information Protection, którego chcesz używać.

## <a name="example-configurations"></a>Przykładowe konfiguracje

W poniższych przykładach należy utworzyć nowe reguły przepływu poczty wykonując następujące kroki:

1. W przeglądarce sieci web przy użyciu konta służbowego lub szkolnego, któremu udzielono uprawnienia administratora globalnego Zaloguj się do usługi Office 365. 

2. Wybierz kafelek **Administrator**.

3. W Centrum administracyjnym usługi Office 365, wybierz **centra administracyjne** > **Exchange**.

4. W Centrum administracyjnym programu Exchange: **przepływu poczty** > **reguły** > **+** > **Utwórz nową regułę** . 

> [!TIP]
> Jeśli masz problemy z interfejsem użytkownika, podczas konfigurowania reguł, spróbuj innej przeglądarki, takich jak program Internet Explorer.

Przykłady mają pojedynczego warunku, która dotyczy ochrony, gdy wiadomość e-mail są wysyłane poza organizację. Aby uzyskać więcej informacji na temat innych warunków, które można wybrać, zobacz [warunki reguły przepływu poczty i wyjątków (predykatów) w usłudze Exchange Online] (https://technet.microsoft.com/library/jj919235(v=exchg.150\).aspx).


### <a name="example-1-rule-that-applies-the-do-not-forward-option-to-emails-that-are-labeled-general-when-they-are-sent-outside-the-organization"></a>Przykład 1: Reguła, która dotyczy opcję nie przesyłaj dalej wiadomości e-mail, które są oznaczone etykietami **ogólne** kiedy są wysyłane poza organizację

W tym przykładzie **ogólne** etykieta ma identyfikator GUID 0e421e6d-ea17-4fdb-8f01-93a3e71333b8. Zastąp swoje własne etykiety lub sublabel identyfikator GUID, który chcesz użyć z tą regułą. 

W zasadach usługi Azure Information Protection, ta etykieta została skonfigurowana jako etykieta domyślna klasyfikowanie wiadomości e-mail jako **ogólne** i etykiety, nie ma zastosowania ochrony. 

1. W **nazwa**, wpisz nazwę reguły, takie jak `Apply Do Not Forward for General emails sent externally`.
 
2. Aby uzyskać **Zastosuj tę regułę, jeśli**: Wybierz **odbiorcy znajduje się**, wybierz opcję **poza organizację**, a następnie wybierz pozycję **OK**.

3. Wybierz **więcej opcji**, a następnie wybierz pozycję **Dodaj warunek**.
 
4. Aby uzyskać **i**: Wybierz **nagłówek komunikatu**, a następnie wybierz pozycję **zawiera dowolną z tych słów**:
     
    a. Wybierz **wprowadź tekst**, a następnie wprowadź `msip_labels`.
     
    b. Wybierz **wprowadź wyrazy**, a następnie wprowadź `MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;`
    
    c. Wybierz **+**, a następnie wybierz pozycję **OK**.

5. Aby uzyskać **wykonaj następujące czynności**: Wybierz **modyfikacji zabezpieczeń wiadomości** > **Zastosuj szyfrowanie wiadomości usługi Office 365 i ochrony praw** > **nie przesyłaj dalej**, a następnie Wybierz **OK**.
    
    Reguły konfiguracji powinna teraz wyglądać podobnie do poniższej:  ![Reguły przepływu poczty usługi Exchange Online skonfigurowano dla etykiety usługi Azure Information Protection — przykład1](./media/aip-exo-rule-ex1.png)

7. Wybierz **Zapisz** 

Aby uzyskać więcej informacji na temat opcji nieprzekazywania zobacz [opcję nie przekazuj dotycząca wiadomości e-mail](configure-usage-rights.md#do-not-forward-option-for-emails).

### <a name="example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization"></a>Przykład 2: Reguła, która dotyczy opcji tylko do szyfrowania wiadomości e-mail ma załączniki, które są oznaczone **poufne \ partnerzy** i te wiadomości e-mail są wysyłane poza organizację

W tym przykładzie **poufne \ partnerzy** etykietę podrzędną ma identyfikator GUID 0e421e6d-ea17-4fdb-8f01-93a3e71333b8. Zastąp swoje własne etykiety lub sublabel identyfikator GUID, który chcesz użyć z tą regułą. 

Ta etykieta służy do klasyfikowania i ochrony dokumentów, których używasz do współpracy z partnerem.   

1. W **nazwa**, wpisz nazwę reguły, takie jak `Apply Encrypt to emails sent externally if protected attachments`.
 
2. Aby uzyskać **Zastosuj tę regułę, jeśli**: Wybierz **odbiorcy znajduje się**, wybierz opcję **poza organizację**, a następnie wybierz pozycję **OK**.

3. Wybierz **więcej opcji**, a następnie wybierz pozycję **Dodaj warunek**.
 
4. Aby uzyskać **i**: Wybierz **żadnego załącznika**, a następnie wybierz pozycję **ma następujące właściwości wraz ze wszystkimi tych słów**:
     
    a. Wybierz **+**  >  **określać właściwości niestandardowych załącznika**.
  
    b. Aby uzyskać **właściwość**, wprowadź `MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled`.
    
    c. Aby uzyskać **wartość**, wprowadź `True`
    
    d. Wybierz **Zapisz**, a następnie wybierz pozycję **OK**.

5. Aby uzyskać **wykonaj następujące czynności**: Wybierz **modyfikacji zabezpieczeń wiadomości** > **Zastosuj szyfrowanie wiadomości usługi Office 365 i ochrony praw** > **Szyfruj**, a następnie wybierz pozycję **OK**.
    
    Reguły konfiguracji powinna teraz wyglądać podobnie do poniższej:  ![Reguły przepływu poczty usługi Exchange Online skonfigurowano dla etykiety usługi Azure Information Protection — przykład1](./media/aip-exo-rule-ex2.png)

6. Wybierz **Zapisz** 

Aby uzyskać więcej informacji na temat opcji szyfrowania, zobacz [opcja tylko do szyfrowania wiadomości e-mail](configure-usage-rights.md#encrypt-only-option-for-emails).


## <a name="next-steps"></a>Następne kroki

Aby uzyskać informacje na temat tworzenia i konfigurowania etykiet do korzystania z usługi Exchange Online reguły przepływu poczty, zobacz [zasad konfigurowania usługi Azure Information Protection](configure-policy.md).

Ponadto ułatwia klasyfikowanie wiadomości e-mail, które zawierają załączniki, należy wziąć pod uwagę przy użyciu następujących usługi Azure Information Protection [ustawienie zasad](configure-policy-settings.md): **W przypadku wiadomości e-mail z załącznikami Zastosuj etykietę, która odpowiada najwyższej klasyfikacji tych załączników**.


