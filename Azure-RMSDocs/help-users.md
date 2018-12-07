---
title: Pomaganie użytkownikom w chronieniu plików za pomocą usługi Azure RMS —AIP
description: Informacje ułatwiające zapewnienie wskazówek dla użytkowników, administratorów i działu pomocy technicznej po wdrożeniu i skonfigurowaniu usługi Azure Rights Management z poziomu usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 43bc10ce43a4ba7a26958e562c4acc6e245ad76a
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53024080"
---
# <a name="helping-users-to-protect-files-by-using-the-azure-rights-management-service"></a>Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Po wdrożeniu i skonfigurowaniu usługi Azure Information Protection w Twojej organizacji należy zapewnić pomoc i wskazówki dla użytkowników, administratorów i działu pomocy technicznej:

-   **Informacje dla użytkowników końcowych**
    
    Powiadom użytkowników, jak i kiedy należy chronić dokumenty i wiadomości e-mail zawierające informacje poufne. Jeśli to możliwe, podaj te informacje w odniesieniu do istniejących przepływów pracy, dzięki czemu użytkownicy będą mogli włączyć dodatkowe czynności do znanych sobie procesów, zamiast wprowadzać zupełnie nowe procesy. Poinformuj ich o korzyściach (i czynnikach ryzyka) specyficznych dla prowadzonej działalności, a także przekaż wskazówki dotyczące sytuacji, w których należy chronić pliki i wiadomości e-mail. Jeśli skonfigurowano [szablony](configure-policy-templates.md), Udostępnij instrukcje dotyczące wyboru, jeśli nie jest wystarczające wybrać właściwy nazwę i opis szablonu.
    
    > [!TIP]
    > Przykładowe filmy dla użytkowników końcowych:
    > -   [Microsoft Azure Information Protection](https://youtu.be/ToShAUdlrPo?list=PL8nfc9haGeb6qSm1kLU8n3Zqg398764h5)
    > -   [Śledzenie i odwoływanie dokumentów w usłudze Azure RMS](https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Informacje o Administratorze**
    
    Niektóre aplikacje automatycznie stosują ochronę informacji przy użyciu zasad i ustawień skonfigurowanych przez administratorów. W przypadku tych aplikacji konieczne może być zapewnienie instrukcji dla innych administratorów, którzy zarządzają tymi aplikacjami i usługami. 
    
    Aby uzyskać więcej informacji, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md) i [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](configure-applications.md).
    
-   **Informacje dla działu pomocy**
    
    Jeśli użytkownicy korzystają z klienta Azure Information Protection, Operatorzy pomocy technicznej mogą ich poprosić o użycie **Pomoc i opinie** opcję informacje, takie jak czy nie obsługuje ochrony i aktualnie zalogowanego jest wersja pakietu Office na koncie użytkownika. Ta opcja umożliwia również zbierać pliki dziennika i zresetować klienta. Aby uzyskać więcej informacji, zobacz w podręczniku administratora: [zainstalować sprawdzanie i rozwiązywanie problemów z](./rms-client/client-admin-guide.md#installation-checks-and-troubleshooting).
    
    W przypadku uprawnionych żądań pełnych praw dostępu do dokumentów chronionych upewnij się, że dział pomocy technicznej dysponuje procesami pozwalającymi na obsługę żądania za pomocą [funkcji administratora](configure-super-users.md) usługi Azure Rights Management. Na przykład tych żądań może pochodzić z działu prawnego lub Menedżera po odejściu pracownika z organizacji.
    
    Niektóre typowe problemy zgłaszane przez użytkowników mogą należeć do następujących kategorii:
    
    - **Pomoc dotycząca logowania**
        
        Użytkownicy mogą otrzymać monit o wprowadzenie poświadczeń, gdy usługa Azure Rights Management wymaga uwierzytelnienia użytkownika i nie może użyć buforowanych poświadczeń. Wymagane poświadczenia są zwykle dla pracy lub konta służbowego użytkownika i hasło skojarzone z dzierżawą usługi Office 365 lub dzierżawy usługi Azure Active Directory. Mimo że usługę Azure Rights Management może uwierzytelnić konta usługi Azure AD, niektóre aplikacje można również otworzyć chronionej zawartości, gdy konto Microsoft służy do uwierzytelniania. [Więcej informacji](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents) 
        
        Przekaż użytkownikom i pomocy technicznej, z instrukcjami dotyczącymi konta, którego należy użyć, gdy użytkownicy są monitowani o poświadczenia, gdy mają one aplikacje, które korzystają z usługi Azure Rights Management.
        
    - **Problemy dotyczące ochrony lub używania zawartości**
        
        Upewnij się, że użytkownicy mają odpowiednie instrukcje dotyczące aplikacji, które używają oraz używają aplikacji i urządzeń, które są obsługiwane przez usługę Azure Rights Management. Aby uzyskać więcej informacji o obsługiwanych aplikacjach i urządzeniach, zobacz [Wymagania dotyczące usługi Azure Rights Management](requirements.md).
        
        Aby upewnić się, że konkretny użytkownik lub grupa może być autoryzowane przez usługę Azure Active Directory ich użyciu chronić ani korzystać z zawartości chronionej, należy użyć testy weryfikacyjne opisane w [przygotowywanie użytkowników i grup usługi Azure Information Protection](prepare.md).
        
        Jeśli użytkownik zgłasza, że będzie mogła otworzyć zawartości chronionej, ale nie mają oni uprawnienia, które są im niezbędne, problem może być, że użytkownik nie jest członkiem właściwej grupy, który jest skonfigurowany dla szablonu usługi Rights Management. Lub może to oznaczać, że [szablon wymaga ponownej konfiguracji](configure-policy-templates.md) dla użytkownika lub grupy. 
        
        Jeśli prawa, które mają użytkownicy są niezgodne z oczekiwaniami, sprawdź opis praw i implementacji specyficznych dla aplikacji z [tabeli praw użytkowania](configure-usage-rights.md#usage-rights-and-descriptions).

Następujące sekcje zawierają informacje specyficzne dla aplikacji dla aby ułatwić użytkownikom ochronę dokumentów oraz wiadomości e-mail.

## <a name="using-information-protection-with-the-azure-information-protection-client"></a>Korzystanie z ochrony informacji zapewnianej przez klienta usługi Azure Information Protection

Jeśli użytkownicy mają pakiet Office 2010, klient usługi Azure Information Protection (lub starsza aplikacja, aplikacja RMS sharing) jest wymagana do ochrony i korzystania z chronionych dokumentów i wiadomości e-mail. Jednak klienta usługi Azure Information Protection jest także zalecana dla wszystkich komputerów i urządzeń przenośnych, które obsługują tę usługę.

Oprócz ułatwiania użytkownikom ochrony dokumentów i wiadomości e-mail, klient usługi Azure Information Protection umożliwia śledzenie dokumentów, które zostały objęte ochroną. Śledzone dokumenty mogą być również odwoływane, w przypadku gdy autoryzowani wcześniej użytkownicy utracili prawo dostępu do nich.

Aby uzyskać instrukcje dotyczące używania tego klienta dla komputerów z systemem Windows, zobacz [podręcznik użytkownika klienta usługi Azure Information Protection ](./rms-client/client-user-guide.md).


## <a name="using-information-protection-with-office365-office-2016-or-office2013"></a>Korzystanie z ochrony informacji za pomocą usługi Office 365, pakietu Office 2016 lub Office 2013
Jeśli używasz usługi Azure Rights Management i nie masz zainstalowanego klienta usługi Azure Information Protection, użytkownicy nie widzą paska usługi Azure Information Protection w swoich aplikacjach klasycznych pakietu Office. Również nie były widoczne **Chroń** przycisk na Wstążce lub **Klasyfikuj i Chroń** w Eksploratorze plików. Te dodatki ułatwiają użytkownikom ochronę plików i wiadomości e-mail. Tacy użytkownicy muszą wykonać instrukcje podobne do opisanych poniżej.

> [!TIP]
> Aby znaleźć pomoc dotyczącą aplikacji i instrukcje korzystania z ochrony informacji przy użyciu tych aplikacji, wyszukaj ciąg **IRM** razem z nazwą i wersją aplikacji.

#### <a name="to-protect-a-document-in-word2013"></a>Aby chronić dokument w programie Word 2013

1.  W programie Microsoft Word utwórz dokument.

2.  W menu **Plik** kliknij pozycję **Informacje**, kliknij pozycję **Chroń dokument**, a następnie kliknij pozycję **Ogranicz dostęp**.

3. Wybierz szablon, aby szybko zastosować odpowiednie prawa użytkowania, lub wybierz pozycję **Ogranicz dostęp** i samodzielnie wybierz prawa użytkowania.

    > [!NOTE]
    > Jeśli usługi Rights Management na komputerze, nie będą wcześniej używano **Ogranicz dostęp** opcja łączy się z usługą Azure Rights Management i zostanie wyświetlony monit o poświadczenia w celu skonfigurowania klienta IRM pakietu Office. Następnie można wybrać szablon i prawa użytkowania.

3.  Zapisz dokument.

Po otwarciu dokumentu przez innych użytkowników najpierw zostanie wykonane ich uwierzytelnienie. Jeśli użytkownik nie jest uprawniony do otwierania tego dokumentu, dokument nie zostanie otwarty. Jeśli użytkownik jest uprawniony do otwierania tego dokumentu, dokument zostanie otwarty z ograniczonymi [prawami użytkowania](configure-usage-rights.md) określonymi dla danego użytkownika. 

Na przykład prawo użytkowania Tylko do wyświetlania nie zezwala na edycję lub zapis dokumentu przez użytkownika, nawet jeśli plik zostanie wcześniej skopiowany do innej lokalizacji. 

Prawa użytkowania są wyświetlane w górnej części dokumentu na transparencie informującym o ograniczeniach. Na transparencie mogą zostać wyświetlone uprawnienia zastosowane do dokumentu lub link umożliwiający ich wyświetlenie.

#### <a name="to-protect-an-email-message-using-outlook2013-and-exchange-online"></a>Aby chronić wiadomość e-mail przy użyciu programu Outlook 2013 i usługi Exchange Online

1.  W programie Outlook utwórz wiadomość e-mail, która jest skierowana do odbiorcy w Twojej organizacji.

2.  Na karcie **OPCJE** kliknij pozycję **Uprawnienie**, a następnie wybierz opcję. Na przykład: **nie przesyłaj dalej**, lub **\<nazwa firmy > — poufne**, lub **\<nazwa firmy > — poufne tylko do wyświetlania**.

3.  Wyślij wiadomość.

Podobnie jak w przypadku wyświetlania dokumentu chronionego, po otwarciu chronionej wiadomości e-mail adresaci zostają najpierw uwierzytelnieni. Jeśli użytkownik jest uprawniony do wyświetlenia wiadomości e-mail, zostanie ona otwarta z ograniczonymi [prawami użytkowania](configure-usage-rights.md), które zostały określone dla danego użytkownika. 

Na przykład, jeśli wiadomość e-mail jest chroniona za pomocą opcji **Nie przesyłaj dalej**, na wstążce nie jest dostępny przycisk Prześlij dalej.

#### <a name="to-protect-an-email-message-using-outlook-on-the-web"></a>Ochrona wiadomości e-mail przy użyciu programu Outlook w sieci Web

1.  W programie Outlook w sieci Web utwórz wiadomość e-mail zaadresowaną do odbiorcy w Twojej organizacji.

2.  Kliknij pozycję **...**, kliknij pozycję **Ustaw uprawnienie**, a następnie wybierz opcję. Na przykład: **nie przesyłaj dalej** lub **nie odpowiadaj wszystkim**. Ewentualnie  **\<nazwa firmy > — poufne** lub  **\<nazwa firmy > — poufne tylko wyświetlanie**.

3.  Wyślij wiadomość.

Podobnie jak w przypadku wyświetlania dokumentu chronionego, po otwarciu wiadomości e-mail adresaci zostają najpierw uwierzytelnieni. Jeśli użytkownik jest uprawniony do wyświetlenia wiadomości e-mail, zostanie ona otwarta z ograniczonymi [prawami użytkowania](configure-usage-rights.md), które zostały określone dla danego użytkownika. 

Na przykład, jeśli została wybrana opcja **Nie odpowiadaj wszystkim**, opcja **ODPOWIEDZ WSZYSTKIM** w oknie komunikatu jest niedostępna.


