---
title: Bezpiecznej współpracy nad dokumentami przy użyciu usługi Azure Information Protection
description: Przepływ pracy na trasie do współpracy nad dokumentami, które są chronione przez usługę Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4895c429-959f-47c7-9007-b8f032f6df6f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d5c24747bcb05f7004f7d42b0145ce6cc1bbade5
ms.sourcegitcommit: aae04d78ff301921a4e29ac23bd932fb24a83dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="secure-document-collaboration-by-using-azure-information-protection"></a>Bezpiecznej współpracy nad dokumentami za pomocą usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Gdy używasz usługi Azure Information Protection, można chronić dokumenty bez ograniczania współpracy dla autoryzowanych użytkowników. Większość dokumentów, że jeden użytkownik tworzy i następnie udostępnia innym użytkownikom, aby wyświetlić i edytować będzie można dokumentami pakietu Office Word, Excel i PowerPoint. Te dokumenty obsługują ochronę natywną, co oznacza, że oprócz funkcji ochrony autoryzacji i szyfrowania, one również obsługiwać ograniczonych uprawnień dla bardziej szczegółową kontrolę. 

Te uprawnienia są nazywane prawa użytkowania i obejmować uprawnienia takie jak widok, edytować, drukować. Prawa użytkowania poszczególnych można zdefiniować, kiedy dokument jest chroniony, albo można zdefiniować grupowania praw użytkowania, nazywany poziomy uprawnień. Poziomy uprawnień należy wybrać prawa użytkowania, które zazwyczaj stosuje się wspólnie, na przykład: recenzent i współautor. Aby uzyskać więcej informacji na temat prawa użytkowania i poziomy uprawnień, zobacz [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](../deploy-use/configure-usage-rights.md).

Podczas konfigurowania tych uprawnień, można również określić użytkowników, którzy są do:

- **Dla użytkowników w organizacji lub inna organizacja, która używa usługi Azure Active Directory**: można określić konta użytkowników usługi Azure AD, grup usługi Azure AD lub wszyscy użytkownicy w organizacji. 

- **Dla użytkowników, którzy nie mają konta usługi Azure Active Directory**: Określ adres e-mail, który będzie używany przy użyciu konta Microsoft. To konto może już istnieć lub użytkownicy mogą tworzyć go w tym czasie zostaną one otwarte chronionego dokumentu. 
    
    Aby otworzyć dokumenty przy użyciu konta Microsoft, użytkownicy mogą używać pakietu Office 2016 kliknij do uruchomienia. Inne wersje pakietu Office i wersje nie nie zostały jeszcze obsługiwane Otwieranie pakietu Office chronionych dokumentów przy użyciu konta Microsoft.

Jako administrator możesz skonfigurować etykiety usługi Azure Information Protection, aby zastosować uprawnienia i autoryzowanych użytkowników. Taka konfiguracja ułatwia bardzo dla użytkowników i innych administratorów, aby zastosować ustawienia poprawny ponieważ stosują po prostu Etykieta bez konieczności określania żadnych szczegółów. Poniższe sekcje zawierają wskazówki przykład, aby chronić dokument, który obsługuje bezpiecznej współpracy z wewnętrznych i zewnętrznych użytkowników.


## <a name="example-configuration-for-a-label-to-apply-protection-to-support-internal-and-external-collaboration"></a>Przykładowa konfiguracja etykiety w celu zastosowania ochrony współpracę wewnętrznych i zewnętrznych

W tym przykładzie przedstawiono konfigurowanie istniejącej etykiety w celu zastosowania ochrony, tak aby użytkownicy z organizacji mogą współpracować nad dokumentami z wszystkich użytkowników z innej organizacji, która ma usługi Office 365 lub Azure AD, grupę z innej organizacji, która ma Office 365 lub Azure AD, a użytkownik nie ma konta w usłudze Azure AD i zamiast tego użyje swój adres e-mail w usłudze Gmail. 

1. Wybierz etykiety, który jest już w zakresie zasad lub globalnych zasad. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
2. Upewnij się, że **ustawić uprawnienia** jest zaznaczone i wybierz **dodać uprawnienia**.

3. Na **dodać uprawnienia** bloku: 
    
    - Wewnętrzny grupy: Wybierz **przeglądania katalogu** wybierz grupy, która musi być włączona obsługa poczty e-mail.
    
    - Dla wszystkich użytkowników w organizacji zewnętrznych pierwszy: Wybierz **wprowadź szczegóły** i wpisz nazwę domeny w dzierżawie w organizacji. Na przykład fabrikam.com.
    
    - Grupy w drugiej organizacji zewnętrznych: na **wprowadź szczegóły** , wpisz adres e-mail grupy w dzierżawie w organizacji. Na przykład sales@contoso.com.
    
    - Dla użytkownika, który nie ma konta usługi Azure AD: na **wprowadź szczegóły** , wpisz adres e-mail użytkownika. Na przykład bengi.turan@gmail.com. 

4. Udzielenia te same uprawnienia dla tych użytkowników: dla **wybierz uprawnienia z ustawienie wstępne**, wybierz pozycję **współwłaściciel**, **Współautor**, **Weryfikacja**, lub **niestandardowy** wybierz uprawnienia, które chcesz udzielić.
    
    Na przykład uprawnienia użytkownika skonfigurowanego może wyglądać podobnie do poniższej:
        
    ![Konfigurowanie uprawnień na potrzeby bezpiecznej współpracy](../media/collaboration-permissions.png)



5. Kliknij przycisk **OK** na **dodać uprawnienia** bloku.

6. Na **ochrony** bloku, kliknij przycisk **OK**. 

## <a name="applying-the-label-that-supports-secure-collaboration"></a>Stosowania etykiety, który obsługuje bezpiecznej współpracy

Teraz, gdy ta etykieta jest skonfigurowany, można można zastosować do dokumentów na różne sposoby, które są następujące:

|Różne sposoby zastosować etykiety|Więcej informacji|
|---------------|----------|
|Inny użytkownik wybierze etykiety ręcznie, podczas tworzenia dokumentu w aplikacjach pakietu Office.|Użytkownicy wybierz etykietę z **Chroń** przycisk wstążki pakietu Office, lub na pasku usługi Azure Information Protection.|
|Użytkownicy są monitowani o wybierz etykietę, podczas zapisywania nowego dokumentu.|Skonfigurowano usługi Azure Information Protection [ustawienie zasad](../deploy-use/configure-policy-settings.md) o nazwie **wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę**.|
|Użytkownik udostępnia dokument pocztą e-mail i ręcznie wybiera etykiety w programie Outlook.|Użytkownicy wybierz etykietę z **Chroń** przycisk na Wstążce Office lub pasek usługi Azure Information Protection i dołączony dokument jest chroniony automatycznie z tymi samymi ustawieniami.|
|Administrator stosuje etykietę do dokumentu za pomocą programu PowerShell.|Użyj [AIPFileLabel zestaw](/powershell/module/azureinformationprotection/set-aipfilelabel) polecenia cmdlet, aby zastosować etykiety do określonego dokumentu lub wszystkie dokumenty w folderze.|
|Ponadto skonfigurowaniu etykiety w celu zastosowania automatycznej klasyfikacji, które teraz mogą być stosowane przy użyciu usługi Azure Information Protection skanera lub programu PowerShell.|Zobacz [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection](../deploy-use/configure-policy-classification.md).|

W tym przewodniku ręcznie zastosować etykiety, podczas tworzenia dokumentu w aplikacji pakietu Office: 

1. Na komputerze klienckim Jeśli masz już otworzyć aplikacji pakietu Office, najpierw zamknij i otwórz ponownie, aby pobrać najnowsze zmiany zasad obejmujących nowo skonfigurowanego etykiety. 

2. Zastosuj etykietę do dokumentu i zapisz go.

Udostępnij dokument chroniony przy dołączeniu go do poczty e-mail i wysyłania go do osoby autoryzowane do edycji dokumentu.

## <a name="opening-and-editing-the-protected-document"></a>Otwieranie i edytowanie chronionych dokumentów

W przypadku użytkowników, którzy autoryzacji można otworzyć dokument do edycji, dokument zostanie otwarty z Baner informacyjny z informacją o tym, że uprawnienia są ograniczone. Przykład:

![Baner informacyjny przykład uprawnienia usługi Azure Information Protection](../media/example-restricted-access-banner.png)

Po zaznaczeniu **Wyświetl uprawnienie** przycisku, zobacz uprawnienia, które mają. W poniższym przykładzie użytkownik może wyświetlać i edytować dokument:

![Okno dialogowe przykład uprawnienia usługi Azure Information Protection](../media/example-permisisons-popup.png)


Przed otwarciem dokumentu, jeden z następujących przepływów uwierzytelniania stanie:

- W przypadku użytkowników, którzy mają konta usługi Azure AD używają swoich poświadczeń usługi Azure AD mają być uwierzytelniani przez usługę Azure AD i dokument zostanie otwarty. 

- Dla użytkownika, który nie ma konta usługi Azure AD, jeśli ich nie jest zalogowany do pakietu Office przy użyciu konta, które ma uprawnienia do otwierania tego dokumentu, zobaczy **kont** strony. 
    
   Na **kont** wybierz pozycję **Dodaj konto**:
   
    ![Dodawanie konta Microsoft, aby otworzyć dokument chroniony](../media/add-account-msa.png)

   Na **Zaloguj** wybierz pozycję **utwórz je!** i postępuj zgodnie z monitami, aby utworzyć nowe konto Microsoft z adresu e-mail, który został użyty Aby udzielić uprawnień:
    
    ![Tworzenie konta Microsoft, aby otworzyć dokument chroniony](../media/create-account-msa.png)
    
    Po utworzeniu nowego konta Microsoft, konta lokalnego zmienia się na tego nowego konta Microsoft i użytkownik może następnie otwórz dokument.


### <a name="supported-scenarios-for-opening-protected-documents"></a>Obsługiwane scenariusze do otwierania chronionych dokumentów

Następujące tabeli podsumowania metody uwierzytelniania innej, które są obsługiwane w przypadku otwieranie i edytowanie chronionych dokumentów.

Ponadto przeglądarka usługi Azure Information Protection dla systemu iOS i Android można otworzyć plików do wyświetlenia za pomocą konta Microsoft.

|Platformy do otwierania i edycji dokumentów: <br />Word, Excel, PowerPoint|Metoda uwierzytelniania:<br />Azure AD|Metoda uwierzytelniania:<br />Konto Microsoft|
|---------------|----------|-----------|-----------|
|Windows|Tak [[1]](#footnote-1)|Tak [[2]](#footnote-2)|
|iOS|Tak [[1]](#footnote-1)|Nie|
|Android|Tak [[1]](#footnote-1)|Nie |
|System macOS|Tak [[1]](#footnote-1)|Nie|

###### <a name="footnote-1"></a>Przypis 1
Obsługuje kont użytkowników, grup z włączoną obsługą poczty e-mail, wszystkie elementy członkowskie. Konta użytkowników i grup z włączoną obsługą poczty e-mail może zawierać konta gościa. Wszystkie elementy członkowskie Wyklucz konta gościa.

###### <a name="footnote-2"></a>Przypis 2
Obecnie obsługiwane przez pakiet Office 2016 kliknij do uruchomienia tylko.


## <a name="next-steps"></a>Następne kroki

Zobacz inne [przykładowe konfiguracje](../deploy-use/configure-policy-protection.md#example-configurations) dla etykiet w celu zastosowania ochrony dla typowych scenariuszy. Ten artykuł zawiera także szczegółowe informacje o ustawieniach ochrony.

Aby uzyskać więcej informacji na temat inne opcje i ustawienia, które można skonfigurować dla etykiety, zobacz [zasad Konfigurowanie usługi Azure Information Protection](../deploy-use/configure-policy.md). 

Etykiety, który został skonfigurowany w tym artykule powoduje również utworzenie szablonu ochrony o tej samej nazwie. Jeśli masz aplikacje i usługi, które integrują się z szablonami ochrony z usługi Azure Information Protection, mają one zastosowanie tego szablonu. Na przykład rozwiązania DLP i reguły przepływu poczty. Program Outlook w sieci web automatycznie wyświetla ochrony szablonów globalnych zasad usługi Azure Information Protection. 


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


