---
title: Konfigurowanie bezpiecznej współpracy nad dokumentami przy użyciu usługi Azure Information Protection
description: Przepływ pracy end-to-end do współpracy nad dokumentami, które są chronione przez usługę Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/21/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 4895c429-959f-47c7-9007-b8f032f6df6f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 1b11f50bcf2090129211f3dd09cff867cfbdcb7b
ms.sourcegitcommit: 80de8762953bdea2553c48b02259cd107d0c71dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51026659"
---
# <a name="configuring-secure-document-collaboration-by-using-azure-information-protection"></a>Konfigurowanie bezpiecznej współpracy nad dokumentami za pomocą usługi Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Gdy używasz usługi Azure Information Protection, możesz chronić swoje dokumenty, bez obniżania oczekiwanego poziomu współpracy dla autoryzowanych użytkowników. Większość dokumentów, że jeden użytkownik tworzy i następnie udostępnia innym osobom do wyświetlania i edytowania będą mieć dokumentów pakietu Office z programu Word, Excel i PowerPoint. Te dokumenty obsługują ochronę natywną, co oznacza, że oprócz funkcji ochrony autoryzacji i szyfrowania, obsługują one również ograniczonych uprawnień dla dokładniejszej kontroli. 

Te uprawnienia są nazywane praw użytkowania i uwzględniać uprawnień, takich jak wyświetlanie, edytowanie, drukowania. Można zdefiniować poszczególne prawa użytkowania, gdy dokument jest chroniony lub można zdefiniować grupowania praw użytkowania, o nazwie poziomów uprawnień. Poziomy uprawnień należy wybrać prawa użytkowania, które są zwykle używane ze sobą, na przykład recenzent i współautor. Aby uzyskać więcej informacji na temat praw użytkowania i poziomy uprawnień, zobacz [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](configure-usage-rights.md).

Podczas konfigurowania tych uprawnień można określić użytkowników, którzy są do:

- **Dla użytkowników w organizacji lub w innej organizacji korzystającej z usługi Azure Active Directory**: można określić konta użytkowników usługi Azure AD, grupy usługi Azure AD lub wszystkich użytkowników należących do organizacji. 

- **Dla użytkowników, którzy nie mają konta usługi Azure Active Directory**: Określ adres e-mail, która będzie służyć za pomocą konta Microsoft. To konto może już istnieć lub użytkownicy mogą tworzyć je w momencie ich otworzyć dokument chroniony. 
    
    Aby otworzyć dokumenty za pomocą konta Microsoft, użytkownicy muszą używać pakietu Office 2016 kliknij do uruchomienia. Inne wersje pakietu Office i wersje zrobić jeszcze obsługi otwierania pakietu Office chronionych dokumentów za pomocą konta Microsoft.

- **Każdy uwierzytelniony użytkownik**: Ta opcja jest odpowiednia dla Jeśli nie potrzebujesz do kontrolowania, kto uzyskuje dostęp do chronionych dokumentów, zapewniając użytkownikowi może zostać uwierzytelniony. Uwierzytelnianie może być przez usługę Azure AD przy użyciu konta Microsoft, lub nawet federacyjnego dostawcy społecznościowych lub jednorazowy kod dostępu, gdy zawartość jest chroniona przez nowe możliwości szyfrowanie wiadomości usługi Office 365. 

Jako administrator możesz skonfigurować etykiety usługi Azure Information Protection do zastosowania, uprawnienia i autoryzowanych użytkowników. Taka konfiguracja ułatwia bardzo dla użytkowników i innych administratorów, aby zastosować ustawienia ochrony poprawne ponieważ one po prostu zastosować etykietę bez konieczności określania żadnych szczegółów. Przewodnik po przykładzie, aby chronić dokument, który obsługuje bezpiecznej współpracy z wewnętrznych i zewnętrznych użytkowników można znaleźć w poniższych sekcjach.


## <a name="example-configuration-for-a-label-to-apply-protection-to-support-internal-and-external-collaboration"></a>Przykładową konfigurację etykiety w celu zastosowania ochrony do obsługi współpracy wewnętrznych i zewnętrznych

W tym przykładzie przedstawiono konfigurowanie istniejącej etykiety w celu zastosowania ochrony, tak aby użytkownicy z Twojej organizacji mogą współpracować nad dokumentami wszystkim użytkownikom z innej organizacji, który ma usługi Office 365 lub Azure AD, w grupie z innej organizacji, która ma Office 365 lub Azure AD, a użytkownik nie ma konta w usłudze Azure AD i zamiast tego użyje adresu e-mail usługi Gmail.

Ponieważ w tym scenariuszu dostęp jest ograniczony do konkretnych osób, nie zawiera ustawienia dla wszystkich uwierzytelnionych użytkowników. Aby uzyskać przykład sposobu konfigurowania etykietę z tym ustawieniem, zobacz [przykład 5: etykiety, która szyfruje zawartość, ale nie ogranicza kto ma dostęp do jego](configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it).  

1. Wybierz etykiety, która jest już zasad globalnych lub zasad o określonym zakresie. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Upewnij się, że **Ustaw uprawnienia** jest zaznaczone i wybierz **Dodaj uprawnienia**.

3. Na **Dodaj uprawnienia** bloku: 
    
    - Wewnętrzny grupy: Wybierz **przeglądania katalogu** aby wybrać grupę, która musi być włączona obsługa poczty e-mail.
    
    - Dla wszystkich użytkowników w pierwszym organizację zewnętrzną: Wybierz **wprowadź szczegóły** i wpisz nazwę domeny w dzierżawie tej organizacji. Na przykład fabrikam.com.
    
    - Grupy w drugiej organizacji zewnętrznych: na **wprowadź szczegóły** karty, wpisz adres e-mail grupy w dzierżawie tej organizacji. Na przykład sales@contoso.com.
    
    - Dla użytkownika, który nie ma konta usługi Azure AD: na **wprowadź szczegóły** karty, wpisz adres e-mail użytkownika. Na przykład bengi.turan@gmail.com. 

4. Aby udzielić tych samych uprawnień do tych użytkowników: dla **wybierz uprawnienia z wstępnie ustawionych**, wybierz opcję **współwłaściciel**, **Współautor**, **recenzenta**, lub **niestandardowe** wybrać, które chcesz udzielić uprawnień.
    
    Na przykład skonfigurowane uprawnienia może wyglądać podobnie do poniższej:
        
    ![Konfigurowanie uprawnień dla bezpiecznej współpracy](./media/collaboration-permissions.png)

5. Kliknij przycisk **OK** na **Dodaj uprawnienia** bloku.

6. Na **ochrony** bloku kliknij **OK**.

7. Na **etykiety** bloku wybierz **Zapisz**. 

## <a name="applying-the-label-that-supports-secure-collaboration"></a>Stosowanie etykiety, która obsługuje bezpiecznej współpracy

Teraz, gdy ta etykieta jest skonfigurowany, można zastosować go do dokumentów w różne sposoby, które obejmują następujące czynności:

|Różne sposoby, aby zastosować etykietę|Więcej informacji|
|---------------|----------|
|Użytkownik wybierze etykietę ręcznie, gdy dokument zostanie utworzony w aplikacji pakietu Office.|Użytkownicy wybrać etykietę z **Chroń** przycisk na Wstążce pakietu Office lub na pasku usługi Azure Information Protection.|
|Użytkownicy są monitowani o wybranie etykiety, po zapisaniu nowego dokumentu.|Skonfigurowano usługi Azure Information Protection [ustawienie zasad](configure-policy-settings.md) o nazwie **wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**.|
|Użytkownik udostępnia dokumentu za pośrednictwem poczty e-mail i ręcznie wybierze etykietę w programie Outlook.|Użytkownicy wybrać etykietę z **Chroń** przycisk na Wstążce pakietu Office lub z paska usługi Azure Information Protection i dołączony dokument jest chroniony automatycznie przy użyciu tych samych ustawień.|
|Administrator ma zastosowanie etykiety do dokumentu przy użyciu programu PowerShell.|Użyj [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) polecenia cmdlet, aby zastosować etykietę do określonego dokumentu lub wszystkie dokumenty w folderze.|
|Ponadto skonfigurowano etykietę do stosowania automatycznej klasyfikacji, które można teraz stosować za pomocą skanera usługi Azure Information Protection lub programu PowerShell.|Zobacz [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection](configure-policy-classification.md).|

Do przeprowadzenia tego instruktażu, ręcznie zastosować etykietę, tworząc dokument w aplikacji pakietu Office: 

1. Na komputerze klienckim Jeśli masz już aplikację pakietu Office, Otwórz, najpierw zamknij i otwórz ponownie, aby pobrać najnowsze zmiany zasad, które zawierają nowo skonfigurowanego etykiety. 

2. Zastosuj etykietę do dokumentu i zapisz go.

Udostępnianie chronionego dokumentu, dołączając ją do poczty e-mail i wyślij go do osób, masz uprawnień do edytowania dokumentu.

## <a name="opening-and-editing-the-protected-document"></a>Otwieranie i edytowanie chronionych dokumentów

Gdy użytkownicy, którzy uwierzytelniona otworzyć dokument do edycji, dokument jest otwierany z Baner, informujące o tym, że uprawnienia są ograniczone. Przykład:

![Transparencie informacyjnym przykład uprawnienia usługi Azure Information Protection](./media/example-restricted-access-banner.png)

Jeśli wybiorą **uprawnienia widok** przycisku, zobaczy, do których mają uprawnienia. W poniższym przykładzie użytkownik może wyświetlić i edytować dokument:

![Okno dialogowe przykład uprawnienia usługi Azure Information Protection](./media/example-permisisons-popup.png)

Uwaga: Jeśli dokument jest otwarty przez użytkowników zewnętrznych, którzy również korzystają z usługi Azure Information Protection, aplikacji pakietu Office nie są wyświetlane etykiety klasyfikacji dla dokumentu, chociaż nadal żadnych oznaczeń wizualnych, z etykiety. Zamiast tego użytkowników zewnętrznych można zastosować własne etykiety, zgodnie z taksonomii klasyfikacji używanych w organizacji. Jeśli tych użytkowników zewnętrznych następnie odesłania dokumentu edytowanego do Ciebie, pakietu Office wyświetla etykiety klasyfikacji usługi oryginalnego po ponownym otwarciu dokumentu.

Przed otwarciem dokumentu chronionego, jedną z następujących uwierzytelniania przepływy możliwe z następujących czynności:

- W przypadku użytkowników, którzy mają konta usługi Azure AD używają poświadczeń usługi Azure AD można uwierzytelnić za pomocą usługi Azure AD i dokument zostanie otwarty. 

- Dla użytkownika, który nie ma konta usługi Azure AD, jeśli ich nie zalogowano do pakietu Office przy użyciu konta, które ma uprawnienia do otwierania dokumentu, zobaczą **kont** strony. 
    
   Na **kont** wybierz opcję **Dodaj konto**:
   
    ![Dodawanie konta Microsoft, aby otworzyć dokument chroniony](./media/add-account-msa.png)

   Na **Zaloguj** wybierz opcję **Zrób to!** i postępuj zgodnie z monitami, aby utworzyć nowe konto Microsoft z adresem e-mail, który został użyty do udzielenia uprawnień:
    
    ![Tworzenie konta Microsoft, aby otworzyć dokument chroniony](./media/create-account-msa.png)
    
    Po utworzeniu nowego konta Microsoft, konta lokalnego przełącza się do tego nowego konta Microsoft, a użytkownik może następnie otwórz dokument.


### <a name="supported-scenarios-for-opening-protected-documents"></a>Obsługiwane scenariusze otwierania chronionych dokumentów

Następujące podsumowania tabeli różnych metod uwierzytelniania, które są obsługiwane w przypadku wyświetlania i edytowania chronionych dokumentów.

Ponadto następujące scenariusze obsługuje wyświetlanie dokumentów:

- Przeglądarka usługi Azure Information Protection, Windows oraz systemów iOS i Android można otwierać pliki przy użyciu konta Microsoft. 

- Podczas dostawców sieci społecznościowych i jednorazowe kody dostępu są używane do uwierzytelniania za pomocą usługi Exchange Online i nowe funkcje z szyfrowanie wiadomości usługi Office 365, przeglądarki może otworzyć chronione załączniki. 

|Platformy do wyświetlania i edycji dokumentów: <br />Word, Excel, PowerPoint|Metoda uwierzytelniania:<br />Azure AD|Metoda uwierzytelniania:<br />Konto Microsoft|
|---------------|----------|-----------|-----------|
|Windows|Tak [[1]](#footnote-1)|Tak [[2]](#footnote-2)|
|iOS|Tak [[1]](#footnote-1)|Nie|
|Android|Tak [[1]](#footnote-1)|Nie|
|Z systemem MacOS|Tak [[1]](#footnote-1)|Nie|

###### <a name="footnote-1"></a>Przypis 1
Obsługuje konta użytkowników, grup z włączoną obsługą poczty e-mail, wszystkie elementy członkowskie. Konta użytkowników i grupy z włączoną obsługą poczty e-mail może zawierać konta gościa. Wszystkie elementy członkowskie wykluczyć konta gościa.

###### <a name="footnote-2"></a>Przypis 2
Obecnie obsługiwane przez pakiet Office 2016 kliknij do uruchomienia tylko.




## <a name="next-steps"></a>Kolejne kroki

Zobacz inne [przykładowe konfiguracje](configure-policy-protection.md#example-configurations) etykiet w celu zastosowania ochrony dla typowych scenariuszy. Ten artykuł zawiera także szczegółowe informacje o ustawienia ochrony.

Aby uzyskać więcej informacji o inne opcje i ustawienia, które można skonfigurować dla etykiety, zobacz [zasad konfigurowania usługi Azure Information Protection](configure-policy.md). 

Etykiety, która została skonfigurowana w tym artykule również utworzenie szablonu ochrony tej samej nazwie. Masz aplikacje i usługi, które integrują się z szablonami ochrony z usługi Azure Information Protection, można zastosować ten szablon. Na przykład rozwiązania DLP i reguły przepływu poczty. Program Outlook w sieci web automatycznie Wyświetla szablony ochrony z globalnych zasad usługi Azure Information Protection. 




