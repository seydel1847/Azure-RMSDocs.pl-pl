---
title: Pomaganie użytkownikom w chronieniu plików za pomocą usługi Azure RMS —AIP
description: Informacje ułatwiające zapewnienie wskazówek dla użytkowników, administratorów i działu pomocy technicznej po wdrożeniu i skonfigurowaniu usługi Azure Rights Management z poziomu usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 0243961b4dfdf3bb8c8b04059793098b26880615
ms.sourcegitcommit: aae04d78ff301921a4e29ac23bd932fb24a83dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34444269"
---
# <a name="helping-users-to-protect-files-by-using-the-azure-rights-management-service"></a>Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Po wdrożeniu i skonfigurowaniu usługi Azure Information Protection w Twojej organizacji należy zapewnić pomoc i wskazówki dla użytkowników, administratorów i działu pomocy technicznej:

-   **Informacje użytkownika końcowego**
    
    Powiadom użytkowników, jak i kiedy należy chronić dokumenty i wiadomości e-mail zawierające informacje poufne. Jeśli to możliwe, podaj te informacje w odniesieniu do istniejących przepływów pracy, dzięki czemu użytkownicy będą mogli włączyć dodatkowe czynności do znanych sobie procesów, zamiast wprowadzać zupełnie nowe procesy. Poinformuj ich o korzyściach (i czynnikach ryzyka) specyficznych dla prowadzonej działalności, a także przekaż wskazówki dotyczące sytuacji, w których należy chronić pliki i wiadomości e-mail. Jeśli skonfigurowano [szablony](configure-policy-templates.md), Udostępnij instrukcje dotyczące wyboru, jeśli nie jest wystarczające wybrać prawidłową nazwę i opis szablonu.
    
    > [!TIP]
    > Przykładowe filmy dla użytkowników końcowych:
    > -   [Microsoft Azure Information Protection](https://youtu.be/ToShAUdlrPo?list=PL8nfc9haGeb6qSm1kLU8n3Zqg398764h5)
    > -   [Śledzenie i odwoływanie dokumentów w usłudze Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Informacje o Administratorze**
    
    Niektóre aplikacje automatycznie stosują ochronę informacji przy użyciu zasad i ustawień skonfigurowanych przez administratorów. W przypadku tych aplikacji konieczne może być zapewnienie instrukcji dla innych administratorów, którzy zarządzają tymi aplikacjami i usługami. 
    
    Aby uzyskać więcej informacji, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md) i [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](configure-applications.md).
    
-   **Informacje pomocy technicznej**
    
    Jeśli użytkownicy mają klienta Azure Information Protection, Operatorzy pomocy technicznej może poprosić o użyj **Pomoc i opinie** opcję informacje, takie jak czy nie obsługuje ochrony, a obecnie podpisem jest pakietu Office na koncie użytkownika. Można także użyć tej opcji, aby zbierać pliki dziennika i zresetować klienta. Aby uzyskać więcej informacji, zobacz Podręcznik administratora: [zainstalować sprawdzanie i rozwiązywanie problemów z](../rms-client/client-admin-guide.md#installation-checks-and-troubleshooting).
    
    W przypadku uprawnionych żądań pełnych praw dostępu do dokumentów chronionych upewnij się, że dział pomocy technicznej dysponuje procesami pozwalającymi na obsługę żądania za pomocą [funkcji administratora](configure-super-users.md) usługi Azure Rights Management. Na przykład te żądania może pochodzić z działu prawnego lub Menedżera po odejściu pracownika z organizacji.
    
    Niektóre typowe problemy zgłaszane przez użytkowników mogą należeć do następujących kategorii:
    
    - **Pomoc dotycząca logowania**
        
        Użytkownicy mogą otrzymać monit o wprowadzenie poświadczeń, gdy usługa Azure Rights Management wymaga uwierzytelnienia użytkownika i nie może użyć buforowanych poświadczeń. Wymagane poświadczenia są zwykle pracy użytkownika lub konto służbowe i hasła, który jest skojarzony z dzierżawą usługi Office 365 lub dzierżawy usługi Azure Active Directory. Mimo że usługa Azure Rights Management może uwierzytelniać konta usługi Azure AD, niektóre aplikacje można również otworzyć chronionej zawartości, gdy konto Microsoft służy do uwierzytelniania. [Więcej informacji](../get-started/secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents) 
        
        Przekaż użytkownikom i pomocy technicznej z instrukcjami dotyczącymi konto, które będzie używane podczas użytkownicy są monitowani o podanie poświadczeń gdy aplikacje, które korzystają z usługi Azure Rights Management.
        
    - **Problemy dotyczące ochrony lub korzystanie z zawartości**
        
        Upewnij się, że użytkownicy mają odpowiednie instrukcje dla aplikacji, które używają i używają aplikacji i urządzeń, które są obsługiwane przez usługę Azure Rights Management. Aby uzyskać więcej informacji o obsługiwanych aplikacjach i urządzeniach, zobacz [Wymagania dotyczące usługi Azure Rights Management](../get-started/requirements-azure-rms.md).
        
        Aby upewnić się, że konkretny użytkownik lub grupa może zostać autoryzowana przez usługi Azure Active Directory w celu ochrony lub korzystania z zawartości chronionej, należy użyć weryfikację w [przygotowywanie użytkowników i grup usługi Azure Information Protection](../plan-design/prepare.md).
        
        Jeśli użytkownik zgłasza, że zostaną one otwarte zawartości chronionej, ale nie mają prawa, które są im niezbędne, problem może być, że użytkownik nie jest poprawne grupy, która jest skonfigurowana dla szablonu usługi Rights Management. Lub może to oznaczać, że [szablon wymaga ponownej konfiguracji](configure-policy-templates.md) dla użytkownika lub grupy. 
        
        Jeśli prawa, jakie użytkownicy mają są niezgodne z oczekiwaniami, sprawdź opis praw i implementacji specyficzne dla aplikacji z [tabeli prawa użytkowania](../deploy-use/configure-usage-rights.md#usage-rights-and-descriptions).

Użyj poniższych sekcji informacje specyficzne dla aplikacji, aby ułatwić użytkownikom ochronę dokumentów i wiadomości e-mail.

## <a name="using-information-protection-with-the-azure-information-protection-client"></a>Korzystanie z ochrony informacji zapewnianej przez klienta usługi Azure Information Protection

Jeśli użytkownicy mają pakiet Office 2010, do ochrony i korzystania z chronionych dokumentów i wiadomości e-mail wymagany jest klient usługi Azure Information Protection (lub starsza aplikacja do udostępniania usług RMS). Jednak klienta Azure Information Protection jest także zalecana dla wszystkich komputerów i urządzeń przenośnych, które obsługują tę usługę.

Oprócz ułatwiania użytkownikom ochrony dokumentów i wiadomości e-mail klienta Azure Information Protection umożliwia śledzenie dokumentów, które zostały objęte ochroną. Śledzone dokumenty mogą być również odwoływane, w przypadku gdy autoryzowani wcześniej użytkownicy utracili prawo dostępu do nich.

Aby uzyskać instrukcje dotyczące używania tego klienta dla komputerów z systemem Windows, zobacz [podręcznik użytkownika klienta usługi Azure Information Protection ](../rms-client/client-user-guide.md).


## <a name="using-information-protection-with-office-365-office-2016-or-office-2013"></a>Korzystanie z ochrony informacji w usłudze Office 365 oraz w pakiecie Office 2016 lub Office 2013
Jeśli używasz usługi Azure Rights Management i nie zainstalowano klienta Azure Information Protection, użytkownicy nie widzą na pasku usługi Azure Information Protection w swoich aplikacji komputerowych pakietu Office. Również nie były widoczne **Chroń** na Wstążce, lub **Klasyfikuj i chronić** w Eksploratorze plików. Te dodatki ułatwiają użytkownikom ochronę plików i wiadomości e-mail. Tacy użytkownicy muszą wykonać instrukcje podobne do opisanych poniżej.

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

1.  W programie Outlook utwórz wiadomość e-mail, która jest skierowana do odbiorcy w Twojej organizacji.

2.  Na karcie **OPCJE** kliknij pozycję **Uprawnienie**, a następnie wybierz opcję. Na przykład: **nie przesyłaj dalej**, lub **\<nazwa firmy > — poufne**, lub **\<nazwa firmy > — poufne tylko do wyświetlania**.

3.  Wyślij wiadomość.

Podobnie jak w przypadku wyświetlania dokumentu chronionego, po otwarciu chronionej wiadomości e-mail adresaci zostają najpierw uwierzytelnieni. Jeśli użytkownik jest uprawniony do wyświetlenia wiadomości e-mail, zostanie ona otwarta z ograniczonymi [prawami użytkowania](../deploy-use/configure-usage-rights.md), które zostały określone dla danego użytkownika. 

Na przykład, jeśli wiadomość e-mail jest chroniona za pomocą opcji **Nie przesyłaj dalej**, na wstążce nie jest dostępny przycisk Prześlij dalej.

#### <a name="to-protect-an-email-message-using-outlook-on-the-web"></a>Ochrona wiadomości e-mail przy użyciu programu Outlook w sieci Web

1.  W programie Outlook w sieci Web utwórz wiadomość e-mail zaadresowaną do odbiorcy w Twojej organizacji.

2.  Kliknij pozycję **...**, kliknij pozycję **Ustaw uprawnienie**, a następnie wybierz opcję. Na przykład: **nie przesyłaj dalej** lub **nie odpowiadaj wszystkim**. Lub,  **\<nazwa firmy > — poufne** lub  **\<nazwa firmy > — poufne tylko wyświetlić**.

3.  Wyślij wiadomość.

Podobnie jak w przypadku wyświetlania dokumentu chronionego, po otwarciu wiadomości e-mail adresaci zostają najpierw uwierzytelnieni. Jeśli użytkownik jest uprawniony do wyświetlenia wiadomości e-mail, zostanie ona otwarta z ograniczonymi [prawami użytkowania](../deploy-use/configure-usage-rights.md), które zostały określone dla danego użytkownika. 

Na przykład, jeśli została wybrana opcja **Nie odpowiadaj wszystkim**, opcja **ODPOWIEDZ WSZYSTKIM** w oknie komunikatu jest niedostępna.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

