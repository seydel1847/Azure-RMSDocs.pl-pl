---
title: "Jak tworzyć konta usługi RMS dla użytkowników indywidualnych — AIP"
description: "Instrukcje dotyczące rejestrowania się w ramach tego bezpłatnego konta oraz informacje techniczne dotyczące sposobu działania tego procesu."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/24/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a60731bd-f78d-4f00-bb3e-354637b312ab
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d1c45c2b97fb3f278a8ecd3ebe9fe37af3ea5d0f
ms.sourcegitcommit: 0fa5dd38c9d66ee2ecb47dfdc9f2add12731485e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2017
---
# <a name="how-users-sign-up-for-rms-for-individuals"></a>Jak tworzyć konta usługi RMS dla użytkowników indywidualnych

>*Dotyczy: Azure Information Protection*

Aby zarejestrować się i uzyskać bezpłatne konto, musisz wysłać żądanie, przechodząc do [strony usługi Microsoft Azure Information Protection](https://aka.ms/rms-signup) i podając swój służbowy adres e-mail. Najczęściej spotykaną metodą nastąpi przekierowanie do tej strony rejestracji jest, jeśli pojawi się wiadomość e-mail z załącznikiem chronionym. Wiadomości e-mail zawiera instrukcje, jak zarejestrować się. 

Po wykonaniu tych instrukcji, otrzymasz wiadomość e-mail w odpowiedzi od firmy Microsoft, a następnie ukończ proces tworzenia konta, wprowadzając szczegóły, aby utworzyć konto. Po zakończeniu tego procesu, Ostatnia strona zawiera łącza do klienta usługi Azure Information Protection lub przeglądarki dla różnych urządzeń, link do podręcznika użytkownika i link do bieżącej listy aplikacje, które natywnie obsługują ochrony usługi Rights Management. 

## <a name="to-sign-up-for-rms-for-individuals"></a>Aby utworzyć konto usługi RMS dla użytkowników indywidualnych

1.  Jeśli używasz komputera z systemem Windows, komputera Mac lub urządzenia przenośnego, przejdź na [stronę usługi Microsoft Azure Information Protection](https://aka.ms/rms-signup).

2.  Wpisz adres e-mail używany dla organizacji, taki jak **janetm@contoso.com** lub **p.dover@fabrikam.com**.

    > [!IMPORTANT]
    > Osobiste konta e-mail nie są obsługiwane, dlatego nie należy wprowadzać konta Microsoft (wcześniej znanego jako konto usługi Microsoft Live ID) ani innego konta osobistego od usługodawcy internetowego, z którego można korzystać w domu.

3. Kliknij przycisk **Zarejestruj się**.

    Firma Microsoft używa Twój adres e-mail, aby sprawdzić, czy Twoja organizacja już ma [subskrypcji usługi Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) lub [subskrypcji usługi Office 365, która obejmuje ochrona danych za pomocą usługi Azure Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). W przypadku znalezienia albo te subskrypcje nie wymagają usług RMS dla użytkowników indywidualnych. Użytkownik jest zalogowany natychmiast i samoobsługowego tworzenia konta usługi RMS dla użytkowników indywidualnych zostanie anulowane. Jeśli jeden z te subskrypcje nie zostanie odnaleziony, kontynuować do następnego kroku.

4. Poczekaj na wiadomość e-mail z potwierdzeniem, która zostanie wysłana na podany adres e-mail. Zostanie ona nadana przez zespół usługi Office 365 (support@email.microsoftonline.com) i będzie miała temat **Ukończ rejestrację w usłudze Microsoft Azure Information Protection**.

5. Po otrzymaniu tej wiadomości e-mail, kliknij przycisk **tak, to ja** Zweryfikuj swój adres e-mail i ukończyć proces tworzenia konta.

6. Zostanie teraz wyświetlona strona **Jeszcze coś**, na której trzeba będzie podać szczegóły konta. Wpisz swoje imię i nazwisko, podaj i potwierdź hasło, a następnie kliknij pozycję **Rozpocznij**.

7. Po utworzeniu konta, zobacz nowej strony Microsoft Azure Information Protection, gdy można pobrać i zainstalować klienta usługi Azure Information Protection lub kliknij przycisk [Podręcznik użytkownika](../rms-client/client-user-guide.md) łącze do praktycznych instrukcji dla komputerów z systemem Windows.

Teraz konto zostało utworzone i możesz już chronić pliki oraz odczytywać pliki chronione przez innych. Po wyświetleniu monitu o zalogowanie się w celu włączenia ochrony plików lub odczytania chronionych plików wprowadź taki sam adres e-mail i hasło co użyte podczas tworzenia konta usługi RMS dla użytkowników indywidualnych.

## <a name="technical-overview-of-the-sign-up-process"></a>Omówienie techniczne procesu tworzenia konta
Usługa RMS dla użytkowników indywidualnych korzysta z samoobsługowego procesu tworzenia konta, który jest już używana przez inne usługi używające technologii chmurowych firmy Microsoft do uwierzytelniania użytkowników.

Oto co dzieje się w tle, gdy użytkownik tworzy konto usługi RMS dla użytkowników indywidualnych, a jego organizacja nie ma subskrypcji usługi Office 365 ani platformy Azure, a w związku z tym nie ma na platformie Azure katalogu służącego do uwierzytelniania użytkowników:

1. Gdy pierwszy użytkownik z organizacji wysyła żądanie dotyczące subskrypcji usługi RMS dla użytkowników indywidualnych, nazwa domeny podana w jego adresie e-mail jest sprawdzana pod kątem już istniejącego skojarzenia z dzierżawą platformy Azure. Jeśli dzierżawa nie istnieje, następuje automatyczne utworzenie nowej dzierżawy i katalogu platformy Azure dla organizacji z kontem pierwszego użytkownika. W odróżnieniu od płatnej lub wersji próbnej subskrypcji Azure pierwsze konto nie jest administratorem globalnym, ale użytkownik standardowy. Nowe konto używa adresu e-mail i hasła podanego przez użytkownika.

    > [!NOTE]
    > Niektórych nazw domen nie można używać do tworzenia katalogu, a co za tym idzie — na potrzeby usługi RMS dla użytkowników indywidualnych.

    Jeśli zostanie znaleziony istniejącej dzierżawy, jest sprawdzany aby zobaczyć, czy zawiera ona już subskrypcję usługi Azure Information Protection. Jeśli subskrypcja nie zostanie znaleziona, można dodać bezpłatną subskrypcję usługi RMS dla użytkowników indywidualnych.

2. Organizacja otrzymuje subskrypcję usługi RMS dla użytkowników indywidualnych. Teraz ten użytkownik może zostać uwierzytelnione przez Azure i tego użytkownika można chronić pliki i odczytywać pliki chronione udostępnione przez innych za pomocą usługi Azure Rights Management. Aby chronić pliki i odczytywać pliki chronione, użytkownik musi mieć aplikacji obsługujących usługę RMS, takie jak aplikacje pakietu Office lub wolnych [klienta Azure Information Protection](../rms-client/aip-client.md).

3. Gdy drugi użytkownik z tej samej organizacji wyśle żądanie dotyczące subskrypcji usługi RMS dla użytkowników indywidualnych, nowe konto użytkownika zostanie dodane do utworzonego wcześniej katalogu platformy Azure za pomocą należącej do organizacji subskrypcji usługi RMS dla użytkowników indywidualnych. Drugi użytkownik może robić wszystko, które można wykonać pierwszy użytkownik (chronić pliki i odczytywać pliki chronione). Ale dodatkowo ci dwaj użytkownicy mogą teraz łatwiej współpracować w bezpieczny sposób ponieważ domyślnych szablonów możliwości szybkiego stosowania do plików, które ograniczają dostęp do kont w usłudze Azure directory używanych w organizacji.

4. Kolejni użytkownicy z tej samej organizacji wykonują te same czynności, dodawanie kont użytkowników do usługi Azure directory organizacji rejestracji. Im więcej kont zostanie dodanych do katalogu, tym większa grupa użytkowników będzie mogła bezpiecznie współpracować z innymi pracownikami i partnerami. Łatwiejsze stanie się również uniemożliwianie nieupoważnionym osobom odczytywania plików, do których nie powinny mieć dostępu.

W trakcie tego procesu organizacja nie jest obciążana żadnymi opłatami, a dział IT nie musi wykonywać żadnych czynności. Jednak dział IT może wybrać, wykonaj jedną z następujących czynności:

- **Zarządzanie kontami i procesem tworzenia kont**: administratorzy IT mogą przejąć prawo własności katalogu i kont tworzonych automatycznie na platformie Azure. Mogą oni następnie zarządzać kontami, wdrażając rozwiązania do integracji katalogu, takie jak synchronizacja haseł i logowanie jednokrotne. Mogą również uniemożliwiać użytkownikom tworzenie kont lub rejestrowanie się w usłudze RMS dla użytkowników indywidualnych.
    
    Aby uzyskać więcej informacji, zobacz [Metody kontrolowania przez administratorów kont utworzonych dla usług RMS dla użytkowników indywidualnych](rms-for-individuals-take-control.md).

- **Zarządzanie usługami Rights Management**: administratorzy IT mogą przekonwertować subskrypcję usługi RMS dla użytkowników indywidualnych dla organizacji na płatną subskrypcję obejmującą usługę Azure Rights Management. W takiej sytuacji istniejące konta i katalog platformy Azure zostaną zachowane w celu łatwego przeniesienia danych istniejących użytkowników, którzy korzystali z usługi RMS dla użytkowników indywidualnych. Wszystkie pliki, które użytkownicy chronili wcześniej nadal są chronione przy użyciu tych samych zasad, a osoby, którym udzielono uprawnień do użycia plików mogą nadal używać plików w taki sam sposób.
    
    Wybór takiej metody postępowania sprawi, że organizacja osiągnie korzyści polegające na możliwości integracji usługi Rights Management ze swoimi przepływami pracy, usługami i magazynami danych. Ponadto można teraz zarządzać usługą Rights Management, ponieważ użytkownik kontroluje powiązany z organizacją klucz dzierżawy usługi Azure Rights Management. Można teraz wykonać następujące czynności:
    
    - Konfiguracja programu Exchange i SharePoint do obsługi usługi Azure Rights Management, nawet jeśli te usługi są uruchomione lokalnie. Programy Exchange i SharePoint są obsługiwane w sposób natywny w usługach online przez łącznik przeznaczony dla serwerów lokalnych. Aby uzyskać więcej informacji, zobacz następujące tematy:
    
        - Sekcje dotyczące usług Exchange Online i SharePoint Online w temacie [Usługa Office 365: konfiguracja dla klientów i usług online](../deploy-use/configure-office365.md)
        
        - [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md)
        
    - Wykonaj zbieranie elektronicznych materiałów dowodowych na firmowych danych, aby autoryzowanych użytkowników i usług można w razie potrzeby odszyfrowywać pliki, które były chronione. Aby uzyskać więcej informacji, zobacz [Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).
    
    - Działania logowania do usługi Rights Management. Rejestrowanie jest bardzo przydatna, ponieważ nie tylko możesz monitorować pliki, które są chronione i kto pomyślnie uzyskuje tych chronionych plików, ale mogą też wskazać podejrzanego zachowania nieupoważnionych osób, które próbujesz uzyskać dostęp do chronionych plików. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).
    
    - Udostępnić użytkownikom możliwości śledzenia i odwoływania chronionych dokumentów, jeśli te funkcje są obsługiwane przez subskrypcję. Aby uzyskać więcej informacji, zobacz temat [Śledzenie i odwoływanie dokumentów](../rms-client/client-track-revoke.md) w [podręczniku użytkownika usługi Azure Information Protection](../rms-client/client-user-guide.md).
    
    - Implementuje bring własnych rozwiązań klucza (BYOK), aby klucz dzierżawy usługi Azure Information Protection jest tworzony i zarządzany przez użytkownika. Aby uzyskać więcej informacji, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md).


## <a name="next-steps"></a>Następne kroki
Zobacz [Metody kontrolowania przez administratorów kont utworzonych dla usług RMS dla użytkowników indywidualnych](rms-for-individuals-take-control.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]