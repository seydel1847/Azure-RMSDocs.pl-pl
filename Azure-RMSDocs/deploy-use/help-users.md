---
title: "Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management | Azure Information Protection"
description: "Informacje ułatwiające zapewnienie wskazówek dla użytkowników, administratorów i działu pomocy technicznej po wdrożeniu i skonfigurowaniu usługi Azure Rights Management z poziomu usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4cdac14d3a77ea7bcce23b914bc3be0a1f46d2b5
ms.openlocfilehash: 0af15bf3238d020b1ee45b45bc780256c88b5e55


---

# <a name="helping-users-to-protect-files-by-using-the-azure-rights-management-service"></a>Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

Po wdrożeniu i skonfigurowaniu usługi Azure Information Protection w Twojej organizacji należy zapewnić pomoc i wskazówki dla użytkowników, administratorów i działu pomocy technicznej:

-   **Informacje dla użytkowników końcowych:**

    Powiadom użytkowników, jak i kiedy należy chronić dokumenty i wiadomości e-mail zawierające informacje poufne. Jeśli to możliwe, podaj te informacje w odniesieniu do istniejących przepływów pracy, dzięki czemu użytkownicy będą mogli włączyć dodatkowe czynności do znanych sobie procesów, zamiast wprowadzać zupełnie nowe procesy. Poinformuj ich o korzyściach (i czynnikach ryzyka) specyficznych dla prowadzonej działalności, a także przekaż wskazówki dotyczące sytuacji, w których należy chronić pliki i wiadomości e-mail. Jeśli skonfigurowano [szablony niestandardowe](configure-custom-templates.md), udostępnij instrukcje dotyczące wyboru szablonów w przypadku, gdy nazwa i opis są niewystarczające.

    > [!TIP]
    > Przykładowe filmy dla użytkowników końcowych:
    >
    > -   [Środowisko użytkownika usługi Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience)
    > -   [Śledzenie i odwoływanie dokumentów w usłudze Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Informacje dla administratorów:**

    Niektóre aplikacje automatycznie stosują ochronę informacji przy użyciu zasad i ustawień skonfigurowanych przez administratorów. W przypadku tych aplikacji konieczne może być zapewnienie instrukcji dla innych administratorów, którzy zarządzają tymi aplikacjami i usługami. Aby uzyskać więcej informacji, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md) i [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](configure-applications.md).

-   **Informacje dla działu pomocy technicznej:**

    Jednym z najbardziej przydatnych narzędzi dla działu pomocy technicznej jest [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437). Operatorzy pomocy technicznej mogą uruchomić to narzędzie z opcją administratora usługi Azure RMS oraz mogą poprosić użytkowników o jego uruchomienie z opcją użytkownika usługi Azure RMS. Narzędzie może być pomocne nie tylko w identyfikowaniu problemów, ale także w rozwiązaniu problemów, które zostaną znalezione. W przypadku problemów nierozwiązanych umożliwia rejestrowanie informacji w dziennikach śledzenia.

    W przypadku uprawnionych żądań pełnych praw dostępu do dokumentów chronionych, na przykład żądania działu prawnego lub menedżera po odejściu pracownika z organizacji, upewnij się, że dział pomocy technicznej dysponuje procesami pozwalającymi na obsługę żądania za pomocą [funkcji administratora](configure-super-users.md) usługi Azure Rights Management.

    Oto niektóre typowe problemy zgłaszane przez użytkowników:

    -   **Pomoc dotycząca logowania:**

        Użytkownicy mogą otrzymać monit o wprowadzenie poświadczeń, gdy usługa Azure Rights Management wymaga uwierzytelnienia użytkownika i nie może użyć buforowanych poświadczeń. Należy użyć służbowego lub szkolnego konta użytkownika i hasła skojarzonego z dzierżawą usługi Office 365 lub dzierżawą usługi Azure Active Directory. Nie należy korzystać z konta Microsoft (dawniej identyfikator Microsoft Live ID) ani osobistego konta e-mail użytkownika, ponieważ nie są one obecnie obsługiwane przez usługę Azure Rights Management. Przekaż użytkownikom i działowi pomocy technicznej instrukcje dotyczące wyboru konta, którego należy użyć w przypadku wyświetlenia monitu o poświadczenia podczas korzystania z tych aplikacji razem z usługą Azure Rights Management.

    -   **Problemy dotyczące ochrony lub używania zawartości:**

        Upewnij się, że użytkownicy mają odpowiednie instrukcje dotyczące aplikacji, z których korzystają, oraz używają aplikacji i urządzeń, które są obsługiwane przez usługę Azure Rights Management. Aby uzyskać więcej informacji o obsługiwanych aplikacjach i urządzeniach, zobacz [Wymagania dotyczące usługi Azure Rights Management](../get-started/requirements-azure-rms.md).

        Jeśli użytkownik zaobserwuje błąd podczas próby ochrony lub korzystania z zawartości, poproś go o uruchomienie narzędzia [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) jako użytkownik usługi Azure RMS.

        Jeśli użytkownik zgłasza, że może otworzyć chronioną zawartość, ale nie ma potrzebnych praw, poproś go o uruchomienie narzędzia [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) jako użytkownik usługi Azure RMS oraz pobierz i wyświetl szablony. W ten sposób możesz potwierdzić, że szablony zostały pomyślnie pobrane przez użytkownika, oraz sprawdzić, jakie uprawnienia zapewniają te szablony. Problem może polegać na tym, że użytkownik nie należy do prawidłowej grupy, która jest skonfigurowana dla danego szablonu, lub że szablon wymaga ponownej konfiguracji dla użytkownika.

Skorzystaj z poniższych sekcji zawierających informacje dotyczące aplikacji, aby ułatwić użytkownikom ochronę ważnych dokumentów i wiadomości e-mail.

## <a name="using-information-protection-with-the-azure-information-protection-client"></a>Korzystanie z ochrony informacji zapewnianej przez klienta usługi Azure Information Protection
Klient usługi Azure Information Protection może być wymagany w przypadku użytkowników, aby możliwa były ochrona i używanie chronionych dokumentów i wiadomości e-mail, jeśli użytkownicy ci korzystają z pakietu Office 2010. Ponadto jego stosowanie jest zalecane także w przypadku komputerów i urządzeń przenośnych.

Oprócz ułatwiania użytkownikom ochrony ważnych dokumentów klient usługi Azure Information Protection umożliwia śledzenie dokumentów, które zostały objęte ochroną, i w razie potrzeby odwołanie dostępu do nich.

Aby uzyskać instrukcje dotyczące używania tego klienta dla komputerów z systemem Windows, zobacz [podręcznik użytkownika klienta usługi Azure Information Protection ](../rms-client/client-user-guide.md).


## <a name="using-information-protection-with-office-365-office-2016-or-office-2013"></a>Korzystanie z ochrony informacji w usłudze Office 365 oraz w pakiecie Office 2016 lub Office 2013
Jeśli używasz usługi Azure Rights Management, ale nie masz zainstalowanego klienta usługi Azure Information Protection, użytkownicy nie będą widzieć paska usługi Azure Information Protection w swoich aplikacjach klasycznych pakietu Office ani przycisku **Chroń** na wstążce lub opcji **Klasyfikuj i chroń** w Eksploratorze plików, który ułatwia korzystanie z tych elementów do ochrony plików. Tacy użytkownicy muszą wykonać instrukcje podobne do opisanych poniżej.

> [!TIP]
> Aby znaleźć pomoc dotyczącą aplikacji i instrukcje korzystania z ochrony informacji przy użyciu tych aplikacji, wyszukaj ciąg **IRM** razem z nazwą i wersją aplikacji.

#### <a name="to-protect-a-document-in-word-2013"></a>Aby chronić dokument w programie Word 2013

1.  W programie Microsoft Word utwórz nowy dokument.

2.  W menu **Plik** kliknij polecenie **Informacje**, po czym kliknij przycisk **Ochrona dokumentu**. Kliknij pozycję **Ogranicz dostęp**, a następnie wybierz szablon, aby szybko zastosować odpowiednie prawa użytkowania, lub wybierz opcję **Ogranicz dostęp** i wybierz prawa użytkowania samodzielnie.

    > [!NOTE]
    > Jeśli korzystasz z usług Rights Management po raz pierwszy, po uzyskaniu kontaktu z usługą [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zostanie wyświetlony monit o podanie poświadczeń w celu skonfigurowania klienta IRM pakietu Office.

3.  Zapisz dokument.

Po otwarciu dokumentu przez innych użytkowników najpierw zostanie wykonane ich uwierzytelnienie. Jeśli użytkownik nie jest uprawniony do otwierania tego dokumentu, dokument nie zostanie otwarty. Jeśli użytkownik jest uprawniony do otwierania tego dokumentu, dokument zostanie otwarty z ograniczonymi prawami użytkowania określonymi dla danego użytkownika. Na przykład prawo użytkowania Tylko do wyświetlania nie zezwala na edycję lub zapis dokumentu przez użytkownika, nawet jeśli plik zostanie wcześniej skopiowany do innej lokalizacji. Prawa użytkowania są wyświetlane w górnej części dokumentu na transparencie informującym o ograniczeniach. Na transparencie mogą zostać wyświetlone uprawnienia zastosowane do dokumentu lub link umożliwiający ich wyświetlenie.

#### <a name="to-protect-an-email-message-using-outlook-2013-and-exchange-online"></a>Aby chronić wiadomość e-mail przy użyciu programu Outlook 2013 i usługi Exchange Online

1.  W programie Outlook utwórz nową wiadomość e-mail zaadresowaną do odbiorcy w Twojej organizacji.

2.  Na karcie **OPCJE** kliknij pozycję **Uprawnienie**, a następnie wybierz opcję. Przykład: **Nie przesyłaj dalej**, **&lt;Nazwa firmy&gt; — Poufne** lub **&lt;Nazwa firmy&gt; — Poufne tylko do wyświetlania**.

3.  Wyślij wiadomość.

Podobnie jak w przypadku wyświetlania dokumentu chronionego, po otrzymaniu wiadomości e-mail adresaci zostają najpierw uwierzytelnieni. Jeśli użytkownik jest uprawniony do wyświetlenia wiadomości e-mail, zostanie ona otwarta z ograniczonymi prawami użytkowania, które zostały określone dla danego użytkownika. Na przykład, jeśli została wybrana opcja **Nie przesyłaj dalej**, na wstążce nie będzie dostępny przycisk Prześlij dalej.

#### <a name="to-protect-an-email-message-using-the-outlook-web-app"></a>Aby chronić wiadomość e-mail przy użyciu aplikacji Outlook Web App

1.  W aplikacji Outlook Web App utwórz nową wiadomość e-mail zaadresowaną do odbiorcy w Twojej organizacji.

2.  Kliknij pozycję **...**, kliknij pozycję **Ustaw uprawnienie**, a następnie wybierz opcję. Przykład: **Nie przesyłaj dalej**, **Nie odpowiadaj wszystkim**, **&lt;Nazwa firmy&gt; — Poufne** lub **&lt;Nazwa firmy&gt; — Poufne tylko do wyświetlania**.

3.  Wyślij wiadomość.

Podobnie jak w przypadku wyświetlania dokumentu chronionego, po otrzymaniu wiadomości e-mail adresaci zostają najpierw uwierzytelnieni. Jeśli użytkownik jest uprawniony do wyświetlenia wiadomości e-mail, zostanie ona otwarta z ograniczonymi prawami użytkowania, które zostały określone dla danego użytkownika. Na przykład, jeśli została wybrana opcja **Nie odpowiadaj wszystkim**, opcja **ODPOWIEDZ WSZYSTKIM** w oknie komunikatu jest niedostępna.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]




<!--HONumber=Feb17_HO2-->


