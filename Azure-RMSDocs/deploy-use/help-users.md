---
title: "Pomaganie użytkownikom w chronieniu plików za pomocą usługi Azure RMS —AIP"
description: "Informacje ułatwiające zapewnienie wskazówek dla użytkowników, administratorów i działu pomocy technicznej po wdrożeniu i skonfigurowaniu usługi Azure Rights Management z poziomu usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 8bc262e8f79b0c0485104b5bb0152dd0609c35c5
ms.sourcegitcommit: 1c3ebf4ad64b55db4fec3ad007fca71ab7d38c02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/18/2017
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

    
    Jeśli użytkownicy uruchamiają klienta usługi Azure Information Protection, operatorzy pomocy technicznej mogą ich poprosić o użycie opcji **Pomoc i opinie**, **Uruchom diagnostykę**, a następnie zresetowanie klienta. Jednak resetowanie nie powoduje wylogowania użytkownika ani ponownego uruchomienia klienta i nie ma możliwości automatycznego korygowania.

    W przypadku uprawnionych żądań pełnych praw dostępu do dokumentów chronionych upewnij się, że dział pomocy technicznej dysponuje procesami pozwalającymi na obsługę żądania za pomocą [funkcji administratora](configure-super-users.md) usługi Azure Rights Management. Mogą to być na przykład żądania z działu prawnego lub żądania menedżera po odejściu pracownika z organizacji. 

    Niektóre typowe problemy zgłaszane przez użytkowników mogą należeć do następujących kategorii:

    -   **Pomoc dotycząca logowania:**

        Użytkownicy mogą otrzymać monit o wprowadzenie poświadczeń, gdy usługa Azure Rights Management wymaga uwierzytelnienia użytkownika i nie może użyć buforowanych poświadczeń. Poświadczenia są wymagane dla służbowych kont użytkowników i haseł skojarzonych z dzierżawcą usługi Office 365 lub dzierżawcą usługi Azure Active Directory. Nie są wymagane w przypadku kont Microsoft (dawniej określanych jako identyfikatory Microsoft Live ID) ani osobistych kont e-mail użytkownika, ponieważ te konta nie są obecnie obsługiwane przez usługę Azure Rights Management. Przekaż użytkownikom i działowi pomocy technicznej instrukcje dotyczące wyboru konta, którego należy użyć w przypadku wyświetlenia monitu o poświadczenia podczas korzystania z tych aplikacji razem z usługą Azure Rights Management.

    -   **Problemy dotyczące ochrony lub używania zawartości:**

        Upewnij się, że użytkownicy mają odpowiednie instrukcje dotyczące aplikacji, z których korzystają, oraz używają aplikacji i urządzeń, które są obsługiwane przez usługę Azure Rights Management. Aby uzyskać więcej informacji o obsługiwanych aplikacjach i urządzeniach, zobacz [Wymagania dotyczące usługi Azure Rights Management](../get-started/requirements-azure-rms.md).

        Procesy uwierzytelniania i autoryzacji są zależne od kont i grup w usłudze Azure Active Directory. Aby potwierdzić, że konkretny użytkownik lub grupa może mieć upoważnienie do korzystania z zawartości chronionej, należy zastosować testy weryfikacyjne opisane w sekcji [Przygotowanie użytkowników i grup do korzystania z usługi Azure Information Protection](../plan-design/prepare.md).

        Jeśli użytkownik zgłasza, że może otworzyć zawartość chronioną, ale nie ma wymaganych praw, problem może polegać na tym, że użytkownik nie jest członkiem właściwej grupy, która została skonfigurowana na potrzeby szablonu usługi Rights Management. Ewentualnie [szablon wymaga ponownego skonfigurowania](configure-policy-template.md) dla użytkownika lub grupy. 
        
        Jeśli prawa, jakimi dysponują użytkownicy są niezgodne z oczekiwaniami, sprawdź ich opis i dowolną implementację specyficzną dla aplikacji w [tabeli praw użytkowania](../deploy-use/configure-usage-rights.md#usage-rights-and-descriptions).

Skorzystaj z poniższych sekcji zawierających informacje dotyczące aplikacji, aby ułatwić użytkownikom ochronę ważnych dokumentów i wiadomości e-mail.

## <a name="using-information-protection-with-the-azure-information-protection-client"></a>Korzystanie z ochrony informacji zapewnianej przez klienta usługi Azure Information Protection
Jeśli użytkownicy mają pakiet Office 2010, do ochrony i korzystania z chronionych dokumentów i wiadomości e-mail wymagany jest klient usługi Azure Information Protection (lub starsza aplikacja do udostępniania usług RMS). Jednak dla wszystkich komputerów i urządzeń przenośnych zalecany jest także klient usługi Azure Information Protection.

Oprócz ułatwiania użytkownikom ochrony ważnych dokumentów i wiadomości e-mail klient usługi Azure Information Protection umożliwia śledzenie dokumentów, które zostały objęte ochroną. Śledzone dokumenty mogą być również odwoływane, w przypadku gdy autoryzowani wcześniej użytkownicy utracili prawo dostępu do nich.

Aby uzyskać instrukcje dotyczące używania tego klienta dla komputerów z systemem Windows, zobacz [podręcznik użytkownika klienta usługi Azure Information Protection ](../rms-client/client-user-guide.md).


## <a name="using-information-protection-with-office-365-office-2016-or-office-2013"></a>Korzystanie z ochrony informacji w usłudze Office 365 oraz w pakiecie Office 2016 lub Office 2013
Jeśli używasz usługi Azure Rights Management, ale nie masz zainstalowanego klienta usługi Azure Information Protection, użytkownicy nie będą widzieć paska usługi Azure Information Protection w swoich aplikacjach klasycznych pakietu Office, przycisku **Chroń** na wstążce ani opcji **Klasyfikuj i chroń** w Eksploratorze plików. Te dodatki ułatwiają użytkownikom ochronę plików i wiadomości e-mail. Tacy użytkownicy muszą wykonać instrukcje podobne do opisanych poniżej.

> [!TIP]
> Aby znaleźć pomoc dotyczącą aplikacji i instrukcje korzystania z ochrony informacji przy użyciu tych aplikacji, wyszukaj ciąg **IRM** razem z nazwą i wersją aplikacji.

#### <a name="to-protect-a-document-in-word-2013"></a>Aby chronić dokument w programie Word 2013

1.  W programie Microsoft Word utwórz dokument.

2.  W menu **Plik** kliknij pozycję **Informacje**, kliknij pozycję **Chroń dokument**, a następnie kliknij pozycję **Ogranicz dostęp**.

3. Wybierz szablon, aby szybko zastosować odpowiednie prawa użytkowania, lub wybierz pozycję **Ogranicz dostęp** i samodzielnie wybierz prawa użytkowania.

    > [!NOTE]
    > Jeśli usługa Rights Management nie była wcześniej używana na komputerze, wybór opcji **Ogranicz dostęp** spowoduje nawiązanie połączenia z usługą [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] i wyświetlenie monitu o podanie poświadczeń w celu skonfigurowania klienta IRM pakietu Office. Następnie można wybrać szablon i prawa użytkowania.

3.  Zapisz dokument.

Po otwarciu dokumentu przez innych użytkowników najpierw zostanie wykonane ich uwierzytelnienie. Jeśli użytkownik nie jest uprawniony do otwierania tego dokumentu, dokument nie zostanie otwarty. Jeśli użytkownik jest uprawniony do otwierania tego dokumentu, dokument zostanie otwarty z ograniczonymi [prawami użytkowania](../deploy-use/configure-usage-rights.md) określonymi dla danego użytkownika. 

Na przykład prawo użytkowania Tylko do wyświetlania nie zezwala na edycję lub zapis dokumentu przez użytkownika, nawet jeśli plik zostanie wcześniej skopiowany do innej lokalizacji. 

Prawa użytkowania są wyświetlane w górnej części dokumentu na transparencie informującym o ograniczeniach. Na transparencie mogą zostać wyświetlone uprawnienia zastosowane do dokumentu lub link umożliwiający ich wyświetlenie.

#### <a name="to-protect-an-email-message-using-outlook-2013-and-exchange-online"></a>Aby chronić wiadomość e-mail przy użyciu programu Outlook 2013 i usługi Exchange Online

1.  W programie Outlook utwórz wiadomość e-mail zaadresowaną do odbiorcy w Twojej organizacji.

2.  Na karcie **OPCJE** kliknij pozycję **Uprawnienie**, a następnie wybierz opcję. Przykład: **Nie przesyłaj dalej**, **&lt;Nazwa firmy&gt; — Poufne** lub **&lt;Nazwa firmy&gt; — Poufne tylko do wyświetlania**.

3.  Wyślij wiadomość.

Podobnie jak w przypadku wyświetlania dokumentu chronionego, po otwarciu chronionej wiadomości e-mail adresaci zostają najpierw uwierzytelnieni. Jeśli użytkownik jest uprawniony do wyświetlenia wiadomości e-mail, zostanie ona otwarta z ograniczonymi [prawami użytkowania](../deploy-use/configure-usage-rights.md), które zostały określone dla danego użytkownika. 

Na przykład, jeśli wiadomość e-mail jest chroniona za pomocą opcji **Nie przesyłaj dalej**, na wstążce nie jest dostępny przycisk Prześlij dalej.

#### <a name="to-protect-an-email-message-using-outlook-on-the-web"></a>Ochrona wiadomości e-mail przy użyciu programu Outlook w sieci Web

1.  W programie Outlook w sieci Web utwórz wiadomość e-mail zaadresowaną do odbiorcy w Twojej organizacji.

2.  Kliknij pozycję **...**, kliknij pozycję **Ustaw uprawnienie**, a następnie wybierz opcję. Przykład: **Nie przesyłaj dalej**, **Nie odpowiadaj wszystkim**, **&lt;Nazwa firmy&gt; — Poufne** lub **&lt;Nazwa firmy&gt; — Poufne tylko do wyświetlania**.

3.  Wyślij wiadomość.

Podobnie jak w przypadku wyświetlania dokumentu chronionego, po otwarciu wiadomości e-mail adresaci zostają najpierw uwierzytelnieni. Jeśli użytkownik jest uprawniony do wyświetlenia wiadomości e-mail, zostanie ona otwarta z ograniczonymi [prawami użytkowania](../deploy-use/configure-usage-rights.md), które zostały określone dla danego użytkownika. 

Na przykład, jeśli została wybrana opcja **Nie odpowiadaj wszystkim**, opcja **ODPOWIEDZ WSZYSTKIM** w oknie komunikatu jest niedostępna.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

