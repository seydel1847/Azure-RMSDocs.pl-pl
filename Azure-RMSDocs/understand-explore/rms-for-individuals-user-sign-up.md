---
title: "Jak tworzyć konta usługi RMS dla użytkowników indywidualnych | Azure Information Protection"
description: "Instrukcje dotyczące rejestrowania się w ramach tego bezpłatnego konta oraz informacje techniczne dotyczące sposobu działania tego procesu."
author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a60731bd-f78d-4f00-bb3e-354637b312ab
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 78b975c2babad347fc5be7956d504c7283508962
ms.openlocfilehash: 093bce2835b0606c127d9bcecab5ec353160833c


---

# Jak tworzyć konta usługi RMS dla użytkowników indywidualnych

>*Dotyczy: Azure Information Protection*

Aby zarejestrować się i uzyskać bezpłatne konto, musisz wysłać żądanie, przechodząc do [strony usługi Microsoft Azure Rights Management](https://portal.office.com/signup?sku=rms&ru=https%3A%2F%2Fportal.azurerms.com%2F%23%2Fdownload) i podając swój służbowy adres e-mail. Najczęściej spotykaną metodą trafienia na stronę rejestracji jest odebranie wiadomości e-mail z chronionym załącznikiem, który zawiera instrukcje dotyczące sposobu tworzenia konta. W odpowiedzi otrzymasz wiadomość e-mail od firmy Microsoft i będziesz w stanie ukończyć proces rejestracji, wprowadzając szczegóły wymagane do utworzenia konta. Po zakończeniu tego procesu zobaczysz stronę, z której możesz pobrać aplikację do udostępniania dla różnych urządzeń oraz na której znajdziesz link do podręcznika użytkownika i link do bieżącej listy aplikacji, które natywnie obsługują usługę Rights Management. 

## Aby utworzyć konto usługi RMS dla użytkowników indywidualnych

1.  Jeśli używasz komputera z systemem Windows, komputera Mac lub urządzenia przenośnego, przejdź na [stronę usługi Microsoft Azure Rights Management](https://portal.office.com/signup?sku=rms&ru=https%3A%2F%2Fportal.azurerms.com%2F%23%2Fdownload).

2.  Wpisz adres e-mail używany dla organizacji, taki jak **joannam@contoso.com** lub **p.michalski@fabrikam.com**.

    > [!IMPORTANT]
    > Osobiste konta e-mail nie są obsługiwane, dlatego nie należy wprowadzać konta Microsoft (wcześniej znanego jako konto usługi Microsoft Live ID) ani innego konta osobistego od usługodawcy internetowego, z którego można korzystać w domu.

3.  Kliknij przycisk **Zarejestruj się**.

    Firma Microsoft użyje Twojego adresu e-mail w celu sprawdzenia, czy Twoja organizacja ma już [płatną subskrypcję obejmującą usługę Azure RMS](../get-started/requirements-subscriptions.md). Jeśli tak, nie potrzebujesz konta usługi RMS dla użytkowników indywidualnych. Nastąpi natychmiastowe zalogowanie, a proces samoobsługowego tworzenia konta usługi RMS dla użytkowników indywidualnych zostanie anulowany. Jeśli płatna subskrypcja usługi Azure RMS nie zostanie znaleziona, nastąpi przejście do następnego kroku.

4.  Poczekaj na wiadomość e-mail z potwierdzeniem, która zostanie wysłana na podany adres e-mail. Zostanie ona nadana przez zespół usługi Office 365 (support@email.microsoftonline.com) i będzie miała temat **Ukończ rejestrację w usłudze Microsoft Azure Rights Management**.

5.  Po otrzymaniu tej wiadomości e-mail kliknij pozycję **Tak, to ja**, aby zweryfikować swój adres e-mail i ukończyć proces rejestracji.

6.  Zostanie teraz wyświetlona strona **Jeszcze coś**, na której trzeba będzie podać szczegóły konta. Wpisz swoje imię i nazwisko, podaj i potwierdź hasło, a następnie kliknij pozycję **Rozpocznij**.

7. Po utworzeniu konta zobaczysz stronę Microsoft Rights Management, z której będzie można pobrać i zainstalować aplikację do udostępniania lub na której będzie można kliknąć link [Więcej informacji](../rms-client/sharing-app-user-guide.md), aby przeczytać podręcznik użytkownika aplikacji do udostępniania.

Teraz konto zostało utworzone i możesz już chronić pliki oraz odczytywać pliki chronione przez innych. Po wyświetleniu monitu o zalogowanie się w celu włączenia ochrony plików lub odczytania chronionych plików wprowadź taki sam adres e-mail i hasło co użyte podczas tworzenia konta usługi RMS dla użytkowników indywidualnych.

## Omówienie techniczne procesu tworzenia konta
Usługa RMS dla użytkowników indywidualnych korzysta z samoobsługowego procesu tworzenia konta, który jest również stosowany przez inne usługi używające technologii firmy Microsoft opartych na chmurze do uwierzytelniania użytkowników.

Oto co dzieje się w tle, gdy użytkownik tworzy konto usługi RMS dla użytkowników indywidualnych, a jego organizacja nie ma subskrypcji usługi Office 365 ani platformy Azure, a w związku z tym nie ma na platformie Azure katalogu służącego do uwierzytelniania użytkowników:

1.  Gdy pierwszy użytkownik z organizacji wysyła żądanie dotyczące subskrypcji usługi RMS dla użytkowników indywidualnych, nazwa domeny podana w jego adresie e-mail jest sprawdzana pod kątem już istniejącego skojarzenia z dzierżawą platformy Azure. Jeśli dzierżawa nie istnieje, następuje automatyczne utworzenie nowej dzierżawy i katalogu platformy Azure dla organizacji z kontem pierwszego użytkownika. W odróżnieniu od płatnej subskrypcji platformy Azure pierwsze konto nie odpowiada administratorowi globalnemu, ale użytkownikowi standardowemu. Nowe konto używa adresu e-mail i hasła podanego przez użytkownika.

    > [!NOTE]
    > Niektórych nazw domen nie można używać do tworzenia katalogu, a co za tym idzie — na potrzeby usługi RMS dla użytkowników indywidualnych.

    W przypadku znalezienia istniejącej dzierżawy nastąpi sprawdzenie, czy ma ona już subskrypcję usługi Azure RMS. Jeśli subskrypcja nie zostanie znaleziona, można dodać bezpłatną subskrypcję usługi RMS dla użytkowników indywidualnych.

2.  Organizacja otrzymuje subskrypcję usługi RMS dla użytkowników indywidualnych. Teraz dany użytkownik może zostać uwierzytelniony przez platformę Azure, a następnie chronić pliki i odczytywać pliki chronione przez inne osoby za pomocą usługi Azure Rights Management. Aby chronić pliki i odczytywać pliki chronione, użytkownik musi mieć aplikację obsługującą usługi RMS, taką jak bezpłatna [aplikacja do udostępniania usługi Rights Management](../rms-client/sharing-app-windows.md).

3.  Gdy drugi użytkownik z tej samej organizacji wyśle żądanie dotyczące subskrypcji usługi RMS dla użytkowników indywidualnych, nowe konto użytkownika zostanie dodane do utworzonego wcześniej katalogu platformy Azure za pomocą należącej do organizacji subskrypcji usługi RMS dla użytkowników indywidualnych. Drugi użytkownik może robić wszystko to, co pierwszy (chronić pliki i odczytywać pliki chronione). Dodatkowo ci dwaj użytkownicy mogą teraz łatwiej współpracować w bezpieczny sposób dzięki możliwości szybkiego stosowania do plików domyślnych szablonów, które ograniczają dostęp do kont w organizacyjnym katalogu platformy Azure.

4.  Kolejni użytkownicy z tej samej organizacji wykonują te same czynności, aby dodać swoje konta (w przypadku tworzenia kont nowych użytkowników) do katalogu platformy Azure w organizacji. Im więcej kont zostanie dodanych do katalogu, tym większa grupa użytkowników będzie mogła bezpiecznie współpracować z innymi pracownikami i partnerami. Łatwiejsze stanie się również uniemożliwianie nieupoważnionym osobom odczytywania plików, do których nie powinny mieć dostępu.

W trakcie tego procesu organizacja nie jest obciążana żadnymi opłatami, a dział IT nie musi wykonywać żadnych czynności. Pracownicy tego działu mogą jednak zdecydować się na wykonanie jednej z poniższych czynności:

-   **Zarządzanie kontami i procesem tworzenia kont**: administratorzy IT mogą przejąć prawo własności katalogu i kont tworzonych automatycznie na platformie Azure. Mogą oni następnie zarządzać kontami, wdrażając rozwiązania do integracji katalogu, takie jak synchronizacja haseł i logowanie jednokrotne. Mogą również uniemożliwiać użytkownikom tworzenie kont lub rejestrowanie się w usłudze RMS dla użytkowników indywidualnych.

    Aby uzyskać więcej informacji, zobacz [Metody kontrolowania przez administratorów kont utworzonych dla usług RMS dla użytkowników indywidualnych](rms-for-individuals-take-control.md).

-   **Zarządzanie usługami Rights Management**: administratorzy IT mogą przekonwertować subskrypcję usługi RMS dla użytkowników indywidualnych dla organizacji na płatną subskrypcję obejmującą usługę Azure Rights Management. W takiej sytuacji istniejące konta i katalog platformy Azure zostaną zachowane w celu łatwego przeniesienia danych istniejących użytkowników, którzy korzystali z usługi RMS dla użytkowników indywidualnych. Wszystkie pliki, które użytkownicy chronili wcześniej, będą nadal chronione za pomocą tych samych zasad, a osoby, którym udzielono uprawnień do użycia plików, będą nadal mogły korzystać z plików w ten sam sposób.

    Wybór takiej metody postępowania sprawi, że organizacja osiągnie korzyści polegające na możliwości integracji usługi Rights Management ze swoimi przepływami pracy, usługami i magazynami danych. Ponadto można teraz zarządzać usługą Rights Management, ponieważ użytkownik kontroluje powiązany z organizacją klucz dzierżawy usługi Azure Rights Management. Można teraz wykonać następujące czynności:

    -   Konfigurowanie programów Exchange i SharePoint do obsługi usługi Azure Rights Management, nawet jeśli są one uruchamiane lokalnie. Programy Exchange i SharePoint są obsługiwane w sposób natywny w usługach online przez łącznik przeznaczony dla serwerów lokalnych. Aby uzyskać więcej informacji, zobacz następujące tematy:

        -   Sekcje dotyczące usług Exchange Online i SharePoint Online w temacie [Usługa Office 365: konfiguracja dla klientów i usług online](../deploy-use/configure-office365.md)

        -   [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md)

    -   Zbieranie elektronicznych materiałów dowodowych związanych z danymi firmowymi. Dzięki temu można w razie potrzeby odszyfrowywać pliki chronione za pomocą usługi Rights Management. Aby uzyskać więcej informacji, zobacz [Konfigurowanie administratorów usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).

    -   Rejestrowanie wszystkich działań na potrzeby usługi Rights Management przy użyciu metody stosowanej w organizacji. Jest to bardzo pomocna funkcja, ponieważ umożliwia nie tylko sprawdzanie, które pliki są obejmowane ochroną i kto pomyślnie uzyskuje do nich dostęp, ale także identyfikowanie podejrzanego zachowania nieupoważnionych osób, które próbują uzyskać dostęp do chronionych plików. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).

    -   Udostępnianie użytkownikom możliwości śledzenia i odwoływania chronionych dokumentów, jeśli te funkcje są obsługiwane przez [subskrypcję usługi Azure RMS](https://technet.microsoft.com/dn858608). Aby uzyskać więcej informacji, zobacz [Śledzenie i odwoływanie plików](../rms-client/sharing-app-track-revoke.md) w [Podręczniku użytkownika aplikacji do udostępniania usług RMS](../rms-client/sharing-app-user-guide.md).

    -   Implementowanie rozwiązania „użyj własnego klucza” (BYOK, bring your own key), aby klucz dzierżawy usługi Azure Rights Management był generowany lokalnie zgodnie z zasadami dotyczącymi infrastruktury IT i bezpiecznie przesyłany do firmy Microsoft za pomocą sprzętowego modułu zabezpieczeń (HSM). Aby uzyskać więcej informacji, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](../plan-design/plan-implement-tenant-key.md).


## Następne kroki
Zobacz [Metody kontrolowania przez administratorów kont utworzonych dla usług RMS dla użytkowników indywidualnych](rms-for-individuals-take-control.md).





<!--HONumber=Oct16_HO1-->


