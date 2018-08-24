---
title: Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection
description: Sprawdź, czy masz konta użytkowników i grup, których potrzebujesz do rozpoczęcia klasyfikowania, oznaczania etykietami i ochrony dokumentów oraz wiadomości e-mail w organizacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.service: information-protection
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 661fac0fc006bb79fc07603482e5e1f7e64ca4c3
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42806351"
---
# <a name="preparing-users-and-groups-for-azure-information-protection"></a>Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Przed wdrożeniem usługi Azure Information Protection w organizacji upewnij się, że w usłudze Azure AD istnieją konta użytkowników i grup dla dzierżawy organizacji.

Istnieją różne sposoby tworzenia tych kont użytkowników i grup, w tym:

- Tworzenie użytkowników w centrum administracyjnym usługi Office 365, a grup w centrum administracyjnym usługi Exchange Online.

- Tworzenie użytkowników i grup w witrynie Azure Portal.

- Tworzenie użytkowników i grup za pomocą poleceń cmdlet programu Azure AD PowerShell i usługi Exchange Online.

- Tworzenie użytkowników i grup w lokalnej usłudze Active Directory i synchronizowanie ich z usługą Azure AD.

- Tworzenie użytkowników i grup w innym katalogu i synchronizowanie ich z usługą Azure AD.

W przypadku tworzenia użytkowników i grup za pomocą pierwszych trzech metod z tej listy następuje ich automatyczne utworzenie w usłudze Azure AD, a usługa Azure Information Protection może bezpośrednio korzystać z tych kont. Jednak wiele sieci przedsiębiorstw używa katalogu lokalnego do tworzenia użytkowników i grup oraz zarządzania nimi. Usługa Azure Information Protection nie może bezpośrednio korzystać z tych kont; należy je zsynchronizować z usługą Azure AD.

## <a name="how-users-and-groups-are-used-by-azure-information-protection"></a>Jak usługa Azure Information Protection korzysta z użytkowników i grup

Istnieją trzy scenariusze dotyczące korzystania z użytkowników i grup w usłudze Azure Information Protection:

**Do przypisywania etykiet do użytkowników** podczas konfigurowania zasad usługi Azure Information Protection, dzięki czemu w dokumentach i wiadomościach e-mail można stosować etykiety. Tych użytkowników i grupy mogą wybierać tylko administratorzy:

- Domyślne zasady usługi Azure Information Protection są automatycznie przypisywane do wszystkich użytkowników w usłudze Azure AD dla dzierżawy. Można jednak również przypisać dodatkowe etykiety do określonych użytkowników lub grup, korzystając z zasad w zakresie.     

**Do przypisywania praw użytkowania i kontroli dostępu** w przypadku chronienia dokumentów i wiadomości e-mail przy użyciu usługi Azure Rights Management. Tych użytkowników i grupy mogą wybierać administratorzy i użytkownicy:

- Prawa użytkowania określają, czy użytkownik może otworzyć dokument lub wiadomość e-mail, i jak może ich używać, na przykład czy może je tylko odczytywać, odczytywać i drukować, czy też odczytywać i edytować. 

- Opcje kontroli dostępu obejmują sprawdzanie daty wygaśnięcia ważności oraz tego, czy do uzyskania dostępu jest wymagane połączenie z Internetem. 

**Do konfigurowania usługi Azure Rights Management** w celu obsługi określonych scenariuszy. Z tego względu te grupy mogą wybierać tylko administratorzy. Przykłady obejmują konfigurowanie następujących elementów:

- Administratorzy — dzięki temu wyznaczone usługi lub osoby mogą otwierać zaszyfrowaną zawartość, jeśli jest to wymagane do zbierania elektronicznych materiałów dowodowych lub odzyskiwania danych.

- Delegowana administracja usługą Azure Rights Management.

- Kontrolki dołączania do obsługi wdrożenia etapowego.

## <a name="azure-information-protection-requirements-for-user-accounts"></a>Wymagania dotyczące usługi Azure Information Protection odnośnie do kont użytkowników

W przypadku przypisywania etykiet:

- Wszystkie konta użytkowników w usłudze Azure AD mogą być używane do konfigurowania zasad w zakresie, które służą do przypisywania dodatkowych etykiet do użytkowników.

W przypadku przypisywania praw użytkowania i kontroli dostępu oraz konfigurowania usługi Azure Rights Management:

- Do autoryzowania użytkowników służą dwa atrybuty w usłudze Azure AD: **proxyAddresses** i **userPrincipalName**.

- Atrybut **proxyAddresses usługi Azure AD** przechowuje wszystkie adresy e-mail konta i może być wypełniany na różne sposoby. Na przykład adres e-mail użytkownika usługi Office 365, który ma skrzynkę pocztową usługi Exchange Online, będzie automatycznie przechowywany w tym atrybucie. Jeśli przypiszesz do użytkownika usługi Office 365 alternatywny adres e-mail, zostanie on również zapisany w tym atrybucie. Można go również wypełnić przy użyciu adresów e-mail synchronizowanych z kont lokalnych. 
    
    Usługa Azure Information Protection może używać dowolnej wartości w tym atrybucie proxyAddresses usługi Azure AD, jeśli domena została dodana do dzierżawy („zweryfikowana domena”). Więcej informacji na temat weryfikowania domen można znaleźć w następujących artykułach:
    
    - W przypadku usługi Azure AD: [Dodawanie niestandardowej nazwy domeny do usługi Azure Active Directory](/active-directory/active-directory-add-domain)

    - W przypadku usługi Office 365: [Dodawanie domeny i użytkowników do usługi Office 365](https://go.microsoft.com/fwlinkid/?linkid=847121)

- Atrybut **userPrincipalName usługi Azure AD** jest używany tylko wtedy, gdy konto w dzierżawie nie ma wartości atrybutu proxyAddresses usługi Azure AD. Można na przykład utworzyć użytkownika w witrynie Azure Portal lub utworzyć użytkownika bez skrzynki pocztowej w usłudze Office 365.

### <a name="assigning-usage-rights-and-access-controls-to-external-users"></a>Przypisywanie praw użytkowania i kontroli dostępu do użytkowników zewnętrznych

Oprócz używania atrybutów proxyAddresses i userPrincipalName usługi Azure AD dla użytkowników w dzierżawie usługa Azure Information Protection korzysta z tych atrybutów w ten sam sposób w celu autoryzowania użytkowników z innej dzierżawy.

Inne metody autoryzacji:

- W przypadku adresów e-mail, które nie znajdują się w usłudze Azure AD usługi Azure Information Protection może autoryzować te podczas ich uwierzytelniania przy użyciu konta Microsoft. Jednak nie wszystkie aplikacje można otworzyć chronionej zawartości, gdy konto Microsoft służy do uwierzytelniania. [Więcej informacji](./secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

- Gdy zostanie wysłana wiadomość e-mail za pomocą szyfrowanie wiadomości usługi Office 365 dzięki nowym funkcjom do użytkownika, które nie mają konta w usłudze Azure AD, użytkownik jest najpierw uwierzytelniany przy użyciu federacji z dostawcy tożsamości społecznościowych lub korzystając z jednorazowym kodem dostępu. Adres e-mail określony w chronioną wiadomość e-mail zostanie użyty do autoryzacji użytkownika.

## <a name="azure-information-protection-requirements-for-group-accounts"></a>Wymagania dotyczące usługi Azure Information Protection dla kont grup

W przypadku przypisywania etykiet:

- Do konfigurowania zasad należących do zakresu, które służą do przypisywania dodatkowych etykiet do członków grupy można używać dowolnego typu grupy usługi Azure AD z adresem e-mail zawierającym zweryfikowaną domenę dzierżawy użytkownika. Grupa, która ma adres e-mail, jest często określana mianem grupy z włączoną obsługą poczty.
    
    Można na przykład użyć grupy zabezpieczeń z włączoną obsługą poczty, grupy dystrybucji (statycznej lub dynamicznej) i grupy usługi Office 365. Nie można użyć grupy zabezpieczeń (dynamicznej ani statycznej), ponieważ ten typ grupy nie ma adresu e-mail.

W przypadku przypisywania praw użytkowania i kontroli dostępu:

- W usłudze Azure AD można używać dowolnego typu grupy z adresem e-mail, która zawiera zweryfikowaną domenę dzierżawy użytkownika. Grupa, która ma adres e-mail, jest często określana mianem grupy z włączoną obsługą poczty. 

W przypadku konfigurowania usługi Azure Rights Management:

- W usłudze Azure AD można używać dowolnego typu grupy z adresem e-mail z domeny zweryfikowanej w dzierżawie — z jednym wyjątkiem. Wyjątkiem jest sytuacja, gdy konfigurujesz kontrolki dołączania w celu użycia grupy, która musi być grupą zabezpieczeń w usłudze Azure AD dla dzierżawy.

- Umożliwia dowolną grupę w usłudze Azure AD (z lub bez adresu e-mail) z domeny zweryfikowanej w dzierżawie potrzeby delegowanej administracji usługi Azure Rights Management.

### <a name="assigning-usage-rights-and-access-controls-to-external-groups"></a>Przypisywanie praw użytkowania i kontroli dostępu do grup zewnętrznych

Oprócz używania atrybutu proxyAddresses usługi Azure AD dla grup w dzierżawie usługa Azure Information Protection korzysta z tego atrybutu w taki sam sposób w celu autoryzowania grup z innej dzierżawy.

## <a name="using-accounts-from-active-directory-on-premises-for-azure-information-protection"></a>Używanie kont z lokalnej usługi Active Directory na potrzeby usługi Azure Information Protection

Jeśli masz konta zarządzane lokalnie, które mają być używane w usłudze Azure Information Protection, musisz je zsynchronizować z usługą Azure AD. W celu ułatwienia wdrażania zalecamy użycie programu [Azure AD Connect](/azure/active-directory/connect/active-directory-aadconnect). Możesz jednak użyć dowolnej metody synchronizacji katalogu, która daje ten sam wynik.

Podczas synchronizowania kont nie trzeba synchronizować wszystkich atrybutów. Aby uzyskać listę atrybutów, które należy zsynchronizować, zobacz [sekcję dotyczącą usługi Azure RMS](/azure/active-directory/connect/active-directory-aadconnectsync-attributes-synchronized#azure-rms) w dokumentacji usługi Azure Active Directory.

Po zapoznaniu się z listą atrybutów usługi Azure Rights Management zobaczysz, że w przypadku użytkowników należy zsynchronizować lokalne atrybuty usługi AD, takie jak **mail**, **proxyAddresses** i **userPrincipalName**. Wartości atrybutów **mail** i **proxyAddresses** są synchronizowane z atrybutem proxyAddresses usługi Azure AD. Aby uzyskać więcej informacji, zobacz artykuł [Jak atrybut proxyAddresses jest wypełniany w usłudze Azure AD](https://support.microsoft.com/help/3190357/how-the-proxyaddresses-attribute-is-populated-in-azure-ad)

## <a name="confirming-your-users-and-groups-are-prepared-for-azure-information-protection"></a>Potwierdzanie gotowości użytkowników i grup do użycia w usłudze Azure Information Protection

W celu potwierdzenia, że użytkownicy i grupy mogą być używane w usłudze Azure Information Protection, można użyć programu Azure AD PowerShell. W programie PowerShell można również sprawdzić wartości do użycia podczas ich autoryzowania. 

Jeśli na przykład w sesji programu PowerShell używasz modułu PowerShell w wersji 1, [MSOnline](/powershell/module/msonline/?view=azureadps-1.0), dla usługi Azure Active Directory, najpierw połącz się z usługą i podaj poświadczenia administratora globalnego:

    Connect-MsolService


Uwaga: jeśli to polecenie nie działa, w celu zainstalowania modułu MSOnline możesz uruchomić polecenie `Install-Module MSOnline`.

Następnie skonfiguruj sesję programu PowerShell tak, aby wartości nie były przycinane:

    $Formatenumerationlimit =-1

### <a name="confirm-user-accounts-are-ready-for-azure-information-protection"></a>Potwierdzanie gotowości kont użytkowników do użycia w usłudze Azure Information Protection

Aby potwierdzić konta użytkowników, uruchom następujące polecenie:

    Get-Msoluser | select DisplayName, UserPrincipalName, ProxyAddresses

Najpierw upewnij się, że użytkownicy, których chcesz używać w usłudze Azure Information Protection, są wyświetlani.

Następnie sprawdź, czy kolumna **ProxyAddresses** została wypełniona. Jeśli tak jest, wartości adresów e-mail w tej kolumnie mogą służyć do autoryzacji użytkownika usługi Azure Information Protection.

Jeśli kolumna **ProxyAddresses** nie została wypełniona, do autoryzacji użytkownika w usłudze Azure Rights Management będzie używana wartość **UserPrincipalName**.

Przykład:

|Nazwa wyświetlana|UserPrincipalName|ProxyAddresses
|-------------------|-----------------|--------------------|
|Jagannath Reddy |jagannathreddy@contoso.com|{}|
|Ankur Roy|ankurroy@contoso.com|{SMTP:ankur.roy@contoso.com, smtp: ankur.roy@onmicrosoft.contoso.com}|

W tym przykładzie:

- Konto użytkownika Jagannath Reddy będzie autoryzowane przy użyciu adresu **jagannathreddy@contoso.com**.

-  Konto użytkownika Ankur Roy może być autoryzowane przy użyciu adresu **ankur.roy@contoso.com** i **ankur.roy@onmicrosoft.contoso.com**, ale nie **ankurroy@contoso.com**.

W większości przypadków wartość pola UserPrincipalName będzie zgodna z jedną z wartości pola ProxyAddresses. Jest to zalecana konfiguracja, ale jeśli nie możesz zmienić nazwy UPN na zgodną z adresem e-mail, musisz wykonać następujące czynności:

1. Jeśli nazwa domeny w polu nazwy UPN to zweryfikowana domena dzierżawy usługi Azure AD, dodaj wartość nazwy UPN jako następny adres e-mail w usłudze Azure AD. Umożliwi to używanie wartości nazwy UPN do autoryzowania konta użytkownika na potrzeby usługi Azure Information Protection.

    Jeśli nazwa domeny w polu wartości nazwy UPN nie jest zweryfikowaną domeną dzierżawy, nie można jej używać w usłudze Azure Information Protection. Użytkownika można jednak nadal autoryzować jako członka grupy, jeśli w adresie e-mail grupy jest używana nazwa zweryfikowanej domeny.

2. Jeśli nazwa UPN nie obsługuje routingu (na przykład **ankurroy@contoso.local**), skonfiguruj alternatywny identyfikator logowania dla użytkowników i poinformuj ich, jak mają logować się do pakietu Office przy użyciu tej alternatywnej nazwy logowania. Musisz również ustawić klucz rejestru dla pakietu Office.

    Aby uzyskać więcej informacji, zobacz artykuły [Konfigurowanie alternatywnego identyfikatora logowania](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id) i [Aplikacje pakietu Office okresowo monitują o poświadczenia usług SharePoint Online, OneDrive i Lync Online](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online).

> [!TIP]
> Aby wyeksportować wyniki do arkusza kalkulacyjnego i łatwiej nimi zarządzać, np. wyszukiwać i edytować grupowo na potrzeby importowania, możesz użyć polecenia cmdlet Export-Csv.
>
> Na przykład: `Get-MsolGroup | select DisplayName, ProxyAddresses | Export-Csv -Path UserAccounts.csv`

### <a name="confirm-group-accounts-are-ready-for-azure-information-protection"></a>Potwierdzanie gotowości kont grup do użycia w usłudze Azure Information Protection

Aby potwierdzić konta grupy, użyj następującego polecenia:

    Get-MsolGroup | select DisplayName, ProxyAddresses

Upewnij się, że grupy, których chcesz używać w usłudze Azure Information Protection, są wyświetlane. Adresy e-mail wyświetlonych grup w kolumnie **ProxyAddresses** mogą być używane do autoryzowania członków grupy na potrzeby usługi Azure Rights Management.

Następne sprawdź, czy grupy zawierają użytkowników (lub inne grupy), których chcesz używać w usłudze Azure Information Protection. W tym celu możesz użyć programu PowerShell (na przykład polecenia [Get-MsolGroupMember](/powershell/module/msonline/Get-MsolGroupMember?view=azureadps-1.0)) lub portalu zarządzania.

W przypadku dwóch scenariuszy konfiguracji Azure Rights Management korzystających z grup zabezpieczeń można użyć poniższego polecenia programu PowerShell w celu wyszukiwania identyfikatora obiektu i nazwy wyświetlanej, na podstawie których można będzie identyfikować te grupy. Możesz również użyć witryny Azure Portal w celu wyszukania tych grup i skopiowania wartości identyfikatora obiektu oraz nazwy wyświetlanej:

    Get-MsolGroup | where {$_.GroupType -eq "Security"}

## <a name="considerations-for-azure-information-protection-if-email-addresses-change"></a>Zagadnienia dotyczące usługi Azure Information Protection w przypadku zmiany adresów e-mail

Jeśli zmienisz adres e-mail użytkownika lub grupy, zalecamy dodanie starego adresu e-mail jako drugiego adresu e-mail (znanego także jako adres serwera proxy, alias lub alternatywny adres e-mail) do użytkownika lub grupy. Wykonanie tej czynności spowoduje dodanie starego adresu e-mail do atrybutu proxyAddresses usługi Azure AD. Administrowanie tym kontem zapewnia ciągłość działania w przypadku dowolnych praw użytkowania lub innych konfiguracji zapisanych, gdy stary adres e-mail był w użyciu. 

Jeśli nie możesz tego zrobić, użytkownika lub grupy z nowej wiadomości e-mail adres ryzyka nastąpiła odmowa dostępu do dokumentów i wiadomości e-mail, które były wcześniej chronione za pomocą starego adresu e-mail. W takim przypadku musisz powtórzyć konfigurację ochrony, aby zapisać nowy adres e-mail. Na przykład jeśli użytkownik lub grupa udzielono prawa użytkowania w szablonach lub etykiety, edytować tych szablonów lub etykiety i określ nowy adres e-mail przy użyciu tych samych praw użytkowania, jak udzielenie stary adres e-mail.

Pamiętaj, że zmiana adresu e-mail grupy występuje rzadko, więc jeśli przypisujesz prawa użytkowania do grupy, a nie do poszczególnych użytkowników, zmiana adresu e-mail użytkownika nie ma znaczenia. W tym scenariuszu prawa użytkowania są przypisywane do adresu e-mail grupy, a nie do adresów e-mail poszczególnych użytkowników. Jest to najbardziej prawdopodobna (i zalecana) metoda, której administrator może użyć w celu skonfigurowania praw użytkowania chroniących dokumenty i wiadomości e-mail. Użytkownicy mogą jednak przeważnie przypisywać poszczególnym osobom uprawnienia niestandardowe. Ponieważ nie zawsze wiadomo, czy konto użytkownika lub grupy było używane do udzielania dostępu, najbezpieczniej jest zawsze dodać stary adres e-mail jako drugi adres e-mail.

## <a name="group-membership-caching-by-azure-information-protection"></a>Buforowanie członkostwa w usłudze Azure Information Protection w grupach

Ze względu na wydajność usługi Azure Information Protection buforuje członkostwa w grupie. Oznacza to, że wszelkie zmiany członkostwa w grupach w usłudze Azure AD może potrwać do trzech godzin zaczęły obowiązywać, gdy te grupy są używane przez usługę Azure Information Protection, a ten okres może ulec zmianie. 

Pamiętaj, aby uwzględnić to opóźnienie we wszystkich zmianach i wykonywanym testowaniu w przypadku korzystania z grup do udzielania praw użytkowania lub konfigurowania usługi Azure Rights Management lub po skonfigurowaniu zasad o określonym zakresie.


## <a name="next-steps"></a>Kolejne kroki

Po potwierdzeniu, że użytkownicy i grupy mogą służyć za pomocą usługi Azure Information Protection i wszystko będzie gotowe do uruchomienia ochrony dokumentów i wiadomości e-mail, sprawdź, czy chcesz aktywować usługę Azure Rights Management. Ta usługa musi być aktywowana, aby chronić dokumenty i wiadomości e-mail w organizacji: 

- Począwszy od lutego 2018 r.: Jeśli subskrypcję obejmującą usługę Azure Rights Management lub usługi Azure Information Protection został uzyskany w trakcie lub po miesiącem, usługa automatycznie została aktywowana dla Ciebie. 

- Jeśli Twoja subskrypcja została uzyskany wcześniej lutego 2018 r.: możesz aktywować usługę samodzielnie. 

Aby uzyskać więcej informacji, która obejmuje sprawdzanie stanu aktywacji, zobacz [Aktywacja usługi Azure Rights Management](./activate-service.md).

