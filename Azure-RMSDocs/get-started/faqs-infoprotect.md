---
title: "Często zadawane pytania dotyczące klasyfikacji i etykietowania — AIP"
description: "Masz pytanie dotyczące aktualnej zapoznawczej usługi Azure Information Protection? Zobacz, czy nie znajdziesz tutaj odpowiedzi."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: dfa89dc4c216807fdebd57dce202a7983a18d9fb
ms.lasthandoff: 02/24/2017


---

# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Często zadawane pytania dotyczące klasyfikacji i etykietowania w usłudze Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Masz pytanie związane z usługą Azure Information Protection, które dotyczy klasyfikacji i etykietowania?  Zobacz, czy nie znajdziesz tutaj odpowiedzi. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Jakie czynności mogę wykonywać za pomocą funkcji klasyfikacji w usłudze Azure Information Protection?

Klient usługi Azure Information Protection dodaje do aplikacji pakietu Microsoft Office pasek usługi Information Protection, który umożliwia wyświetlanie etykiet klasyfikacji danych i ich przypisywanie do dokumentów pakietu Office i wiadomości e-mail.

Klasyfikację można zastosować domyślnie, ręcznie, w ramach opcji zalecanej lub automatycznie — w przypadku wykrycia poufnych danych. Etykiety umożliwiają także automatyczną ochronę danych poprzez użycie usługi Rights Management do zarządzania prawami dostępu. Korzystając z Eksploratora plików i klikając prawym przyciskiem myszy plik, wiele plików lub folder, można sklasyfikować i objąć ochroną także inne pliki oprócz dokumentów pakietu Office i wiadomości e-mail. Uruchamiając program PowerShell z wiersza polecenia, można szybciej dokonać klasyfikacji plików oraz chronić pliki w trybie zbiorczym.

Etykiety i zachowanie klasyfikacji są skonfigurowane w portalu Azure. Wbudowane zasady domyślne mogą służyć do szybkiej oceny usługi Azure Information Protection lub do pełnego dostosowania własnych zasad. Można zmienić kolory, nazwy i kolejność etykiet klasyfikacji widocznych dla użytkowników. Można również skonfigurować etykietki narzędzi i wizualne oznaczenia klasyfikacji, takie jak nagłówek, stopka lub znak wodny.

Kilka minut wystarczy do zapoznania się z naszym samouczkiem Szybki start: [Samouczek Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).

Obecna wersja ma następujące ograniczenia: W blogu [dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) i witrynie [Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) będą się pojawiać ogłoszenia o dostępności dodatkowych funkcji i możliwości:

- Nazwy etykiet i etykietki narzędzi są obsługiwane tylko w jednym języku.

- Brak centralnego rejestrowania dla funkcji klasyfikacji i etykietowania.

- Warunkami klasyfikacji automatycznej muszą być frazy lub wzorce.

- Aplikacje pakietu Office dla komputerów Mac i urządzeń przenośnych (iOS i Android) ani aplikacje sieci Web pakietu Office (Office Online) nie są jeszcze obsługiwane.

- Brak integracji z programem Exchange Online i usługą SharePoint Online.

- Zestaw SDK dla deweloperów i partnerów nie jest dostępny.

Niektóre spośród wymienionych wcześniej ograniczeń są teraz dostępne w lutowej wersji nowego klienta. Aby uzyskać więcej informacji, zobacz wpis na blogu.


## <a name="do-i-need-to-be-a-global-admin-to-try-azure-information-protection"></a>Czy muszę być administratorem globalnym, aby wypróbować usługę Azure Information Protection?

Aby skonfigurować zasady usługi Azure Information Protection, musisz zalogować się do portalu Azure jako administrator globalny usługi Azure Active Directory.

Jeśli jednak w trakcie instalacji [klienta usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) wybrano opcję zainstalowania zasad demonstracyjnych, zalogowanie się do portalu nie jest konieczne do wyświetlenia i wypróbowania funkcji etykietowania. Zasada demonstracyjna instaluje lokalnie zasadę domyślną usługi Azure Information Protection, co umożliwia próby etykietowania dokumentów i wiadomości e-mail, ale nie pozwala na zmianę ani dodanie nowej etykiety bez rejestrowania się w portalu Azure. 

## <a name="which-options-in-the-azure-portal-are-p1-or-p2"></a>Które opcje witryny Azure Portal to P1 i P2?

Aby sprawdzić, które funkcje została uwzględnione w subskrypcji **Azure Information Protection Premium 1** (P1) w porównaniu z subskrypcją **Azure Information Protection Premium 2** (P2), zobacz [listę funkcji](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection. Zasadniczo zaawansowane funkcje, takie jak automatyczna klasyfikacja i HYOK (utrzymanie własnego klucza, ang. hold your own key), są powiązane z subskrypcją Premium 2 usługi Azure Information Protection.

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Czy usługa Azure Information Protection obsługuje scenariusze lokalne i hybrydowe?

Usługa Azure Information Protection to rozwiązanie oparte na chmurze. Jeśli interesuje Cię wdrożenie usługi Azure Information Protection dla scenariusza hybrydowego, skontaktuj się z zespołem usługi Information Protection, wysyłając wiadomość e-mail na adres askipteam@microsoft.com.

## <a name="how-do-computers-get-the-policy-information-from-azure-information-protection-and-how-often-is-it-refreshed"></a>Jak komputery uzyskują informacje o zasadach od usługi Azure Information Protection i jak często są one odświeżane?

Przy każdym otwarciu aplikacji pakietu Office klient usługi Azure Information Protection sprawdza, czy jest dostępna nowsza wersja zasad usługi. Ponadto aplikacje pakietu Office przeprowadzają sprawdzanie co 24 godziny. Jeśli istnieje nowsza wersja, klient pobiera ją za pomocą łącza HTTPS w celu zabezpieczenia danych. 

Jeśli podczas publikowania nowych zasad usługi Azure Information Protection załadowanych jest wiele wystąpień aplikacji pakietu Office, musisz zamknąć wszystkie instancje, aby pobrać najnowszą wersję zasad. Przykładowo, jeśli masz otwarte dwa dokumenty programu Word i chcesz przetestować zaktualizowane zasady usługi Azure Information Protection tylko w jednym dokumencie: zamknij oba dokumenty programu Word i otwórz ponownie dokument, którego chcesz użyć wraz z najnowszymi zasadami.

## <a name="where-can-files-be-stored-to-use-azure-information-protection"></a>Gdzie mogą być przechowywane pliki korzystające z usługi Azure Information Protection? 

Ponieważ usługa Azure Information Protection nadaje trwałe etykiety i chroni pliki oraz wiadomości e-mail, nie ma znaczenia, gdzie są przechowywane pliki.

## <a name="can-i-classify-only-new-data-or-can-i-also-classify-existing-data"></a>Czy mogę klasyfikować tylko nowe dane, czy też również dane istniejące?

Akcje zasady usługi Azure Information Protection stają się aktywne przy zapisywaniu dokumentów i wysyłaniu wiadomości e-mail, zarówno w przypadku nowej zawartości, jak i zmian w zawartości istniejącej.

Jeśli masz klienta w najnowszej wersji, możesz również szybko sklasyfikować (i opcjonalnie objąć ochroną) istniejące pliki z poziomu Eksploratora plików. 

## <a name="can-i-use-azure-information-protection-for-classification-only-without-enforcing-encryption-and-restricting-usage-rights"></a>Czy usługi Azure Information Protection można używać wyłącznie do klasyfikowania, bez wymuszania szyfrowania i ograniczania prawa użytkowania?

Tak. Zasady usługi Azure Information Protection można tak skonfigurować, aby były stosowane tylko klasyfikacje bez ochrony (jeśli typ pliku obsługuje tę akcję). W zasadzie można oczekiwać, że będzie się tak dziać w większości już wdrożonych sieci, w których należy chronić tylko podzbiór dokumentów lub wiadomości e-mail wymagających specjalnego zarządzania danymi.

## <a name="how-does-automatic-classification-work"></a>Jak działa automatyczna klasyfikacja?

W portalu Azure można użyć wstępnie zdefiniowanych wzorców, takich jak numer karty kredytowej lub numer ubezpieczenia społecznego w USA. Możesz zdefiniować niestandardowy ciąg lub szablon będący warunkiem automatycznej klasyfikacji.

Podobny przykład pojawia się w [samouczku Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md). 

Dokładność klasyfikacji zależy od sposobu skonfigurowania reguły klasyfikacji, która opiera się na warunkach. Obecnie warunki obsługują wzorce tekstu i wyrażenia regularne. Aby uzyskać informacje o wszystkich dostępnych opcjach wraz z sugerowanymi przykładami do testowania, zobacz temat [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection](../deploy-use/configure-policy-classification.md). Wykrywanie jest uruchamiane przy zapisywaniu dokumentu lub wysyłaniu wiadomości e-mail.

Aby zapewnić najlepszą jakość obsługi i ciągłość prowadzenia działalności biznesowej, warto rozpocząć od wydawania zaleceń użytkownikom, a nie od wprowadzania czynności w pełni zautomatyzowanych. Dzięki temu użytkownicy mają wybór pomiędzy akceptacją etykietowania lub akcji ochronnych a odrzuceniem takiego zalecenia.   

## <a name="can-azure-information-protection-prompt-users-to-classify-files-themselves-rather-than-use-automatic-classification"></a>Czy usługa Azure Information Protection monituje użytkowników o samodzielne klasyfikowanie plików zamiast używania automatycznej klasyfikacji? 

Tak. Użyj portalu Azure, aby skonfigurować, czy używać automatycznej klasyfikacji, czy wydawać zalecenie użytkownikom, nadając opcji **Wybierz sposób stosowania etykiet: automatycznie lub zalecając użytkownikowi ** wartość **Zalecenie**.

Podobny przykład pojawia się w [samouczku Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).  

## <a name="can-i-force-all-documents-to-be-classified"></a>Czy można wymusić klasyfikowania wszystkich dokumentów?

Tak. Jeśli wymagasz, aby użytkownicy klasyfikowali wszystkie zapisywane pliki, w witrynie Azure Portal nadaj ustawieniu zasad **Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę** wartość **Wł.**. 

## <a name="can-i-remove-classification-from-a-file"></a>Czy można usunąć klasyfikację z pliku?

Tak. Ta procedura została omówiona w podręczniku użytkownika: [Usuwanie etykiet klasyfikacji i ochrony z plików i wiadomości e-mail](../rms-client/client-remove-label-protection.md) 

## <a name="can-i-prompt-users-to-justify-why-they-are-changing-the-classification-level"></a>Czy można monitować użytkowników o uzasadnienie, dlaczego zmieniają poziom klasyfikacji?

Tak. Aby się upewnić, że użytkownicy uzasadniają swoje zmiany klasyfikacji, w witrynie Azure Portal należy opcji **Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę** nadać wartość **Włączone**. W takim przypadku wykonywana czynność oraz stosowne uzasadnienie zostaną zapisane w ich lokalnym dzienniku zdarzeń systemu Windows: **Dzienniki aplikacji i usług** > **Microsoft Azure Information Protection**.

## <a name="how-can-i-automatically-protect-the-content-after-its-been-classified"></a>Jak automatycznie chronić zawartość po jej zakwalifikowaniu?

W portalu Azure można wybrać szablon usługi Rights Management, aby automatycznie chronić zawartość zgodnie z określonym poziomem klasyfikacji.

Podobny przykład pojawia się w [samouczku Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md). Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management](../deploy-use/configure-policy-protection.md).

## <a name="can-a-file-have-more-than-one-classification"></a>Czy plik może mieć więcej niż jedną klasyfikację?

Użytkownicy mogą jednocześnie wybrać tylko jedną etykietę dla każdego dokumentu lub wiadomości e-mail, co skutkuje często utworzeniem tylko jednej klasyfikacji. Jeśli jednak użytkownicy wybiorą etykietę podrzędną, spowoduje to w rzeczywistości zastosowanie dwóch etykiet jednocześnie: etykiety podstawowej i pomocniczej. Dzięki użyciu etykiet podrzędnych plik może mieć dwie klasyfikacje, które wprowadzają relację typu element nadrzędny/podrzędny na potrzeby dodatkowego poziomu kontroli.

Na przykład etykieta **Tajne** może zawierać etykiety podrzędne, takie jak **Prawne** i **Finanse**. Tym etykietom podrzędnym można przypisać różne wizualne oznaczenia klasyfikacji i różne szablony usługi Rights Management. Użytkownik nie może wybrać bezpośrednio etykiety **Tajne**, tylko jedną z jej etykiet podrzędnych, na przykład **Prawne**. W efekcie widzą oni, że została ustawiona etykieta **Tajne \ Prawne**. Metadane dla tego pliku zawierają jedną niestandardową właściwość tekstową dla etykiety **Tajne**, jedną niestandardową właściwość tekstową dla etykiety **Prawne** i jeszcze jedną właściwość, która zawiera obie wartości (**Tajne Prawne**). 

Jeśli korzystasz z etykiet podrzędnych, nie konfiguruj wizualnych oznaczeń, ochrony i warunków dla etykiety podstawowej. Jeśli korzystasz z poziomów podrzędnych, skonfiguruj te ustawienia tylko dla etykiet podrzędnych. Jeśli skonfigurujesz te ustawienia dla etykiety podstawowej i jej etykiety podrzędnej, pierwszeństwo mają ustawienia etykiety podrzędnej.

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Czy gdy wiadomość e-mail jest oznaczona, pewne załączniki automatycznie uzyskają tę samą etykietę?

Nie. Jeśli wiadomość e-mail zawierająca załączniki zostanie oznaczona, załączniki te nie odziedziczą tej samej etykiety. Załączniki pozostaną bez etykiety lub zachowają oddzielnie przydzieloną etykietę. Jednak jeśli etykieta wiadomości e-mail zawiera ochronę, ochrona ta jest stosowana także do załączników.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Czym różni się klasyfikacja wiadomości e-mail usługi Azure Information Protection od klasyfikacji wiadomości e-mail stosowanej w programie Exchange?

Klasyfikacja wiadomości programu Exchange to starsza funkcja umożliwiająca klasyfikowanie wiadomości e-mail, wdrożona niezależnie od klasyfikacji usługi Azure Information Protection. Jednakże te dwa rozwiązania można zintegrować tak, aby podczas klasyfikowania przez użytkownika wiadomości e-mail w aplikacji sieci web Outlook lub w niektórych aplikacjach poczty w urządzeniach przenośnych następowało automatyczne klasyfikowanie w ramach usługi Azure Information Protection i dodawanie odpowiadających jej oznaczeń etykiet. Program Exchange dodaje klasyfikację, a klient usługi Azure Information Protection stosuje odpowiednie ustawienia etykiet dla danej klasyfikacji.

Mimo że aplikacja sieci web Outlook nie obsługuje jeszcze natywnie klasyfikacji i ochrony usługi Azure Information Protection, można użyć tej samej techniki, aby móc używać własnych etykiet nie tylko z klientem programu Outlook na komputerze, ale też z tym klientem poczty e-mail.

W tym celu: 

1. Użyj polecenia cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) środowiska PowerShell programu Exchange w celu utworzenia klasyfikacji wiadomości z właściwością Name, która mapuje do nazw etykiet użytkownika w zasadach usługi Azure Information Protection. 

2. Utwórz dla każdej etykiety regułę transportu programu Exchange: zastosuj regułę, jeśli właściwości wiadomości obejmują skonfigurowaną przez Ciebie klasyfikację, a następnie zmodyfikuj właściwości wiadomości, aby ustawić nagłówek wiadomości. 

    Informacje, jakie należy określić dla nagłówka wiadomości, można zidentyfikować, sprawdzając właściwości pliku pakietu Office sklasyfikowane za pomocą etykiety usługi Azure Information Protection. Zidentyfikuj właściwość pliku w formacie **MSIP_Label_<GUID>_Enabled** i określ ten ciąg dla nagłówka wiadomości, a następnie wybierz wartość **True** dla nagłówka. Nagłówek wiadomości może na przykład wyglądać podobnie do następującego ciągu: **MSIP_Label_132616b8-f72d-5d1e-aec1-dfd89eb8c5b2_Enabled**


W przypadku użytkowników, którzy używają aplikacji sieci web Outlook lub klienta urządzenia przenośnego, który obsługuje ochronę zarządzania prawami, ma miejsce następujący scenariusz: 

- Użytkownicy wybierają klasyfikację wiadomości programu Exchange i wysyłają wiadomość e-mail.

- Reguła programu Exchange wykrywa klasyfikację programu Exchange i odpowiednio modyfikuje nagłówek wiadomości w celu dodania klasyfikacji usługi Azure Information Protection.

- Gdy adresaci korzystający z klienta usługi Azure Information Protection wyświetlają wiadomość e-mail w programie Outlook, widzą przypisane etykiety usługi Azure Information Protection i wszelkie powiązane nagłówki wiadomości e-mail, stopki lub znaki wodne. 

Jeśli etykiety usługi Azure Information Protection zakładają zastosowanie ochrony zarządzania prawami, dodaj tę ochronę do konfiguracji reguły, zaznaczając opcję modyfikacji zabezpieczeń wiadomości, zastosuj ochronę praw, a następnie wybierz szablon RMS lub opcję Nie przesyłaj dalej.

Możesz również skonfigurować reguły transportu na potrzeby mapowania odwrotnego. W tym celu po wykryciu etykiety usługi Azure Information Protection ustaw odpowiednią klasyfikację wiadomości programu Exchange. Wykonaj następujące czynności:

- Dla każdej etykiety usługi Azure Information Protection utwórz regułę transportu, która będzie stosowana, jeśli nagłówek **msip_labels** będzie zawierał nazwę Twojej etykiety (na przykład **Poufne**), i zastosuj klasyfikację wiadomości mapowaną do tej etykiety.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Jak rozwiązania DLP i inne aplikacje integrują się z usługą Azure Information Protection?

Ponieważ usługa Azure Information Protection używa do klasyfikacji trwałych metadanych, w tym etykiety w postaci zwykłego tekstu, te informacje są odczytywane przez rozwiązania DLP i inne aplikacje. W plikach metadane te są przechowywane we właściwościach niestandardowych; w wiadomościach e-mail znajdują się one w nagłówkach.

## <a name="how-does-document-tracking-and-revocation-work-for-azure-information-protection"></a>Jak działa śledzenie i odwoływanie dokumentów w usłudze Azure Information Protection?

W przypadku plików sklasyfikowanych i chronionych za pomocą usługi Azure Information Protection śledzenie dokumentów jest obsługiwane w najnowszych wersjach klienta usługi Azure Information Protection (1.3.155.2 i późniejszych). 

Aby uzyskać więcej informacji, zobacz temat [Śledzenie i odwoływanie dokumentów chronionych podczas korzystania z usługi Azure Information Protection](../rms-client/client-track-revoke.md).

## <a name="can-i-control-which-users-can-use-azure-information-protection-to-classify-and-protect-content"></a>Czy można kontrolować, którzy użytkownicy mogą używać usługi Azure Information Protection do klasyfikowania i ochrony zawartości?

Można ograniczyć grono użytkowników, którzy mogą klasyfikować i chronić dane, kontrolując dystrybucję klienta usługi Azure Information Protection. Podczas konfigurowania [zasad o określonym zakresie](../deploy-use\configure-policy-scope.md) nowe etykiety dodawane są tylko dla określonych użytkowników. 

Pliki i wiadomości e-mail sklasyfikowane przez usługę Azure Information Protection mogą być używane lub edytowane przez dowolnego użytkownika, z użyciem lub bez zainstalowanego klienta usługi Azure Information Protection. 

## <a name="how-do-i-sign-in-as-a-different-user"></a>Jak zalogować się jako inny użytkownik?

W środowisku produkcyjnym zazwyczaj nie ma potrzeby logowania się jako inny użytkownik w przypadku korzystania z klienta usługi Azure Information Protection. Może to być jednak konieczne, jeśli występuje wielu dzierżawców. Na przykład oprócz dzierżawcy usługi Office 365 lub platformy Azure, którego używa Twoja organizacja, używany jest dzierżawca testowy.

Aby sprawdzić, za pomocą którego konta nastąpiło logowanie, otwórz okno dialogowe **Microsoft Azure Information Protection**, uruchom aplikację pakietu Office i na karcie **Narzędzia główne** w grupie **Ochrona** kliknij opcję **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. Nazwa konta jest widoczna w sekcji **Stan klienta**.

Szczególnie w przypadku korzystania z konta administratora należy koniecznie sprawdzić nazwę domeny zalogowanego konta. Na przykład w przypadku korzystania z konta „Administrator” dla dwóch różnych dzierżawców można łatwo przeoczyć, że logowanie nastąpiło przy użyciu prawidłowej nazwy konta, ale niewłaściwej domeny. Jeśli tak się stało, może wystąpić problem z pobraniem zasad usługi Azure Information Protection albo nie będzie widać oczekiwanych etykiet lub funkcji.

Aby zalogować się jako inny użytkownik, należy edytować rejestr:

1. W Edytorze rejestru przejdź do pozycji **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP** i usuń wartość **TokenCache**.

2. Uruchom ponownie wszystkie otwarte aplikacje pakietu Office i zaloguj się przy użyciu innego konta użytkownika. Jeśli w aplikacji pakietu Office nie został wyświetlony monit o zalogowanie się do usługi Azure Information Protection, wróć do okna dialogowego **Microsoft Azure Information Protection** i kliknij przycisk **Zaloguj** w zaktualizowanej sekcji **Stan klienta**.

Dodatkowo:

- Jeśli chcesz ponownie zainicjować środowisko usługi Azure Rights Management (tzw. „bootstrapping”), możesz to zrobić za pomocą opcji **Resetuj** w [narzędziu Analizator RMS](https://www.microsoft.com/en-us/download/details.aspx?id=46437).

- Aby usunąć aktualnie pobrane zasady usługi Azure Information Protection, usuń plik **Policy.msip** z folderu %localappdata%\Microsoft\MSIP.

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Jak zgłosić problem lub wysłać opinię dotyczącą usługi Azure Information Protection?

Aby skorzystać z pomocy technicznej, użyj standardowych kanałów pomocy lub [skontaktuj się z pomocą techniczną firmy Microsoft](information-support.md#to-contact-microsoft-support).

Aby przekazać opinie, w tym sugestie dotyczące ulepszeń i nowych funkcji, w aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** kliknij przycisk **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **Wyślij opinię**. Spowoduje to wysłanie wiadomości e-mail do zespołu usługi Information Protection i automatyczne dołączenie plików dziennika z Twojego komputera. 

Zachęcamy także do kontaktowania się z naszymi inżynierami za pośrednictwem [strony usługi Azure Information Protection w witrynie Yammer](https://www.yammer.com/askipteam/). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
