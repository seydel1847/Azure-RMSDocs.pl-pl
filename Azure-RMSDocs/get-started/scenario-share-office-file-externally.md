---
title: "Scenariusz usługi AIP — udostępnianie plików pakietu Office użytkownikom zewnętrznym"
description: "W tym scenariuszu i dodatkowej dokumentacji użytkownika jest używana ochrona usługi Azure Rights Management, dzięki czemu użytkownicy mogą bezpiecznie przesyłać pliki pakietu Office w wiadomościach e-mail do osób w innej organizacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c10a4d7b-f57a-4a43-b66e-477777be59cc
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 89c563ebcf62dc80cbda15048780adf5e414e70b
ms.sourcegitcommit: 7b773ca5bf1abf30e527c34717ecb2dc96f88033
translationtype: HT
---
# <a name="scenario---share-an-office-file-with-users-in-another-organization"></a>Scenariusz — udostępnianie plików pakietu Office użytkownikom z innej organizacji

>*Dotyczy: Azure Information Protection, Office 365*

W tym scenariuszu i dodatkowej dokumentacji użytkownika jest używana technologia usługi Azure Rights Management z usługi Azure Information Protection, dzięki czemu użytkownicy mogą bezpiecznie przesyłać pliki pakietu Office w wiadomościach e-mail do osób w innej organizacji. Plik pakietu Office może być na przykład dokumentem programu Word, arkuszem kalkulacyjnym programu Excel lub prezentacją programu PowerPoint. Może on zawierać informacje o cenach dla partnera, listę produktów dla odsprzedawcy lub listę pozycji czasów dostawy do potencjalnych klientów. Jeśli użytkownicy będą postępować zgodnie z instrukcjami, plik dołączony do wiadomości e-mail będzie chroniony za pomocą usługi Azure Rights Management.

Ten scenariusz sprawdza się w następujących okolicznościach:

-   Pracownik ma wysłać poza organizację informacje w formie załącznika z dokumentem pakietu Office za pośrednictwem poczty e-mail.

-   Dokument zawiera niepubliczne informacje, które jednak nie są przeznaczone wyłącznie do użytku wewnętrznego.

-   Odbiorcy nie muszą tych informacji udostępniać innym osobom, drukować ani uwzględniać we własnej dokumentacji. Jeśli tak nie jest, można zmienić instrukcje użytkownika i zamiast uprawnień tylko do wyświetlania wybrać inną opcję umożliwiającą adresatowi zmianę załącznika.

-   Pracownik prawdopodobnie będzie chciał wiedzieć, kiedy dokument zostanie otwarty przez użytkownika zewnętrznego.

## <a name="deployment-instructions"></a>Instrukcje dotyczące wdrażania
![Instrukcje dla administratora dotyczące szybkiego wdrażania usługi Azure RMS](../media/AzRMS_AdminBanner.png)

Zanim przejdziesz do dokumentacji użytkownika, upewnij się, że zostały spełnione następujące wymagania.

## <a name="requirements-for-this-scenario"></a>Wymagania dotyczące tego scenariusza
Aby zrealizować instrukcje dotyczące tego scenariusza, należy spełnić następujące wymagania:

|Wymaganie|Jeśli potrzebujesz dodatkowych informacji|
|---------------|--------------------------------|
|Zostały przygotowane konta i grupy dla usługi Office 365 lub Azure Active Directory.|[Przygotowanie do korzystania z usługi Azure Information Protection](https://technet.microsoft.com/library/jj585029.aspx)|
|Usługa Azure Rights Management została aktywowana.|[Aktywacja usługi Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Aplikacja do udostępniania usługi Rights Management została wdrożona na komputerach użytkowników z systemem Windows|[Automatyczne wdrażanie aplikacji do udostępniania usługi Microsoft Rights Management](../rms-client/sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application)|
|Użytkownicy korzystają z programu Outlook pakietu Office 2013|Jeśli użytkownicy korzystają z pakietu Office 2016 lub Office 2010, należy odpowiednio zmienić zrzut ekranu, aby odzwierciedlał zawartość wyświetlaną na ekranach użytkowników.|
|Twoja subskrypcja usługi Azure Information Protection obejmuje śledzenie dokumentów|Jeśli Twoja subskrypcja nie obejmuje śledzenia i odwoływania dokumentów, użytkownicy nie będą mogli wykonać wszystkich kroków opisanych w instrukcjach użytkownika. W takim przypadku należy zakupić subskrypcję, która obsługuje te funkcje, lub zmodyfikować instrukcje użytkownika, aby usunąć kroki dotyczące tych funkcji.<br /><br />Zapoznaj się z [listą funkcji](https://www.microsoft.com/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection.|

## <a name="user-documentation-instructions"></a>Instrukcje w dokumentacji użytkownika
Przy użyciu następującego szablonu skopiuj i wklej instrukcje dla użytkownika do wiadomości dla użytkowników końcowych, po czym wprowadź poniższe zmiany, aby odzwierciedlić charakter lokalnego środowiska:

1.  Zastąp zmienną *&lt;nazwa typu dokumentu pakietu Office&gt;* typem dokumentu, który użytkownicy będą wysyłać. Stosuj znaną terminologię charakterystyczną dla ich przepływów pracy, na przykład „cennik”, „czas dostawy” czy „oferta przetargowa” zamiast sformułowań typu „dokument programu Word” czy „arkusz kalkulacyjny programu Excel”. Precyzyjny dobór słów zwiększa prawdopodobieństwo, że użytkownicy zastosują się do instrukcji podczas pracy z dokumentami.

2.  Zastąp *&lt;dane kontaktowe&gt;* instrukcjami dla użytkowników dotyczącymi sposobu kontaktowania się z działem pomocy technicznej, na przykład podaj link do witryny sieci Web, adres e-mail lub numer telefonu.

3.  **Dodatkowe zmiany, które możesz wprowadzić:**

    -   W kroku 2 sugerujemy wybór uprawnienia **Przeglądający — tylko wyświetlanie**, na podstawie którego adresaci będą mieli prawo tylko do odczytu dołączonego dokumentu (ale nie oryginału). Jeśli to ograniczenie nie odpowiada konkretnym wymaganiom biznesowym, zmień tę opcję, wybierając inny zestaw uprawnień, na przykład **Recenzent — wyświetlanie i edytowanie**.

    -   W kroku 3 sugerujemy zaznaczenie pola wyboru **Zezwalaj mi na natychmiastowe odwoływanie dostępu do tych dokumentów**, aby uniknąć opóźnienia, jeśli użytkownicy zdecydują się później na odwołanie dostępu do dokumentu. W przypadku ustawienia tej opcji adresat musi mieć aktywne połączenie internetowe, aby otworzyć załącznik. Ten krok wymaga również subskrypcji obejmującej obsługę śledzenia i odwoływania dokumentów. Usuń ten krok, jeśli nie dotyczy Twoich użytkowników.

    -   W kroku 4 dobrze jest wybrać opcję **Powiadamiaj mnie pocztą e-mail o próbach otwarcia tego dokumentu**. Jeśli użytkownicy śledzą swoje dokumenty za pomocą portalu śledzenia dokumentów, możesz zrezygnować z powiadomienia e-mail i usunąć ten krok.

    -   Kroki nie obejmują ustawiania daty wygaśnięcia. Jeśli informacje nie powinny być dostępne po określonej dacie, dodaj kolejny krok, aby ustawić odpowiedni czas wygaśnięcia, na przykład 90 dni od wysłania wiadomości e-mail.

    > [!NOTE]
    > Aby uzyskać więcej informacji o poszczególnych opcjach, które użytkownicy mogą wybrać, zobacz temat [Opcje okien dialogowych aplikacji do udostępniania usługi Rights Management](https://technet.microsoft.com/library/dn574738.aspx)

4.  Wprowadź wszelkie inne zmiany, które chcesz uwzględnić w tym zestawie instrukcji, a następnie wyślij go do wybranych użytkowników.

W przykładowej dokumentacji przedstawiono potencjalny wygląd odpowiednio dostosowanych instrukcji, które zobaczą użytkownicy.

![Dokumentacja użytkownika dotycząca szablonów na potrzeby szybkiego wdrażania usługi Azure RMS](../media/AzRMS_UsersBanner.png)

### <a name="how-to-share-a-ltname-of-office-document-typegt"></a>Jak udostępnić dokument &lt;nazwa typu dokumentu pakietu Office&gt;

1.  Utwórz wiadomość e-mail, podając adres lub adresy e-mail, wpisz wiadomość i dołącz do wiadomości e-mail dokument *&lt;nazwa typu dokumentu pakietu Office&gt;*. Następnie na karcie **WIADOMOŚĆ** w grupie **RMS** kliknij opcję **Udostępnij chronione**, a następnie kliknij opcję **Udostępnij chronione** ponownie:

    ![Zrzut ekranu — udostępnianie dokumentu pakietu Office za pomocą programu Outlook](../media/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  W oknie dialogowym **Udostępnianie chronionej zawartości** wybierz opcję **Przeglądający — tylko wyświetlanie**:

    ![okno dialogowe Udostępnianie chronionej zawartości — Przeglądający — tylko wyświetlanie](../media/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  Zaznacz pole wyboru **Zezwalaj mi na natychmiastowe odwoływanie dostępu do tych dokumentów**:

    ![okno dialogowe Udostępnianie chronionej zawartości — natychmiastowe odwoływanie](../media/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  Zaznacz pole wyboru **Powiadamiaj mnie pocztą e-mail o próbach otwarcia tego dokumentu**:

    ![okno dialogowe Udostępnianie chronionej zawartości — Powiadamiaj mnie pocztą e-mail](../media/AzRMS_SharedProtected_EmailMe.PNG)

5.  Kliknij pozycję **Wyślij teraz**.

Gdy osoba podana w wierszu **Do**, **DW** lub **UDW** odbierze tę wiadomość e-mail, zobaczy komunikat z instrukcjami odczytania dołączonego dokumentu *&lt;nazwa typu dokumentu pakietu Office&gt;*. Będzie mogła odczytać dokument na różnych urządzeniach, na przykład na urządzeniach iPad i iPhone, tabletach i telefonach z systemem Android, komputerach Mac i komputerach z systemem Windows.

Skorzystaj z [portalu śledzenia dokumentów](https://track.azurerms.com/), aby sprawdzić, czy i kiedy adresat otworzy dołączony dokument &lt;nazwa typu dokumentu pakietu Office&gt;. Gdy zobaczysz, że dokument &lt;nazwa typu dokumentu pakietu Office&gt; został otwarty, możesz skontaktować się z adresatem telefonicznie.

**Potrzebujesz pomocy?**

-   Dodatkowe informacje:

    -   [Ochrona pliku udostępnionego pocztą e-mail](../rms-client/sharing-app-protect-by-email.md)

    -   [Śledzenie i odwoływanie dokumentów](../rms-client/sharing-app-track-revoke.md)

-   Skontaktuj się z działem pomocy technicznej:

    -   *&lt;dane kontaktowe&gt;*

### <a name="example-customized-user-documentation"></a>Przykładowa niestandardowa dokumentacja użytkownika
![Przykładowa dokumentacja użytkownika dotycząca szybkiego wdrażania usługi Azure RMS](../media/AzRMS_ExampleBanner.png)

#### <a name="how-to-share-a-price-list-with-your-customer"></a>Jak udostępnić cennik klientowi

1.  Utwórz wiadomość e-mail, podając adres lub adresy e-mail klienta, wpisz wiadomość i dołącz do wiadomości e-mail najnowszy cennik. Następnie na karcie **WIADOMOŚĆ** w grupie **RMS** kliknij opcję **Udostępnij chronione**, a następnie kliknij opcję **Udostępnij chronione** ponownie:

    ![Zrzut ekranu — udostępnianie dokumentu pakietu Office za pomocą programu Outlook](../media/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  W oknie dialogowym **Udostępnianie chronionej zawartości** wybierz opcję **Przeglądający — tylko wyświetlanie**:

    ![okno dialogowe Udostępnianie chronionej zawartości — Przeglądający — tylko wyświetlanie](../media/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  Zaznacz pole wyboru **Zezwalaj mi na natychmiastowe odwoływanie dostępu do tych dokumentów**:

    ![okno dialogowe Udostępnianie chronionej zawartości — natychmiastowe odwoływanie](../media/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  Zaznacz pole wyboru **Powiadamiaj mnie pocztą e-mail o próbach otwarcia tego dokumentu**:

    ![okno dialogowe Udostępnianie chronionej zawartości — Powiadamiaj mnie pocztą e-mail](../media/AzRMS_SharedProtected_EmailMe.PNG)

5.  Kliknij pozycję **Wyślij teraz**.

Gdy osoba podana w wierszu **Do**, **DW** lub **UDW** odbierze tę wiadomość e-mail, zobaczy komunikat z instrukcjami, jak przeczytać dołączony cennik. Będzie mogła odczytać dokument na różnych urządzeniach, na przykład na urządzeniach iPad i iPhone, tabletach i telefonach z systemem Android, komputerach Mac i komputerach z systemem Windows.

Skorzystaj z [portalu śledzenia dokumentów](https://track.azurerms.com/), aby sprawdzić, czy i kiedy adresat otworzy dołączony cennik. Gdy zobaczysz, że cennik został otwarty, możesz skontaktować się z adresatem telefonicznie.

**Potrzebujesz pomocy?**

-   Dodatkowe informacje:

    -   [Ochrona pliku udostępnionego pocztą e-mail](../rms-client/sharing-app-protect-by-email.md)

    -   [Śledzenie i odwoływanie dokumentów](../rms-client/sharing-app-track-revoke.md)

-   Skontaktuj się z działem pomocy technicznej:

    -   Poczta e-mail: helpdesk@vanarsdelltd.com

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
