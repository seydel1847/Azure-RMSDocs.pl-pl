---
title: Samouczek Szybki start krok 5 | Azure Information Protection
description: "Krok 5 samouczka wprowadzającego, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection w swojej organizacji. Wystarczy około 30 minut."
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4e59a3b3-f0f4-4535-8b96-cac68303d855
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1af9f3b3451bf8ceafbaf3cddd2b26c37fe9d597
ms.openlocfilehash: d607c19d37da6b6fb23513067e9e30f33f0260de


---


# Krok 5. Praktyczne udostępnianie plików chronionych i śledzenie dokumentu 

>*Dotyczy: Azure Information Protection*

W tym ostatnim kroku samouczka odszukaj utworzony wcześniej dokument programu Word, który prześlesz do współpracownika. W ramach tego samouczka nie jest istotne, jaki tekst zawiera dokument. Niemniej dobrze będzie wpisać jakiś tekst, aby łatwiej potwierdzić, że autoryzowany odbiorca mógł go odczytać.

Następnie możesz bezpiecznie udostępnić ten dokument pocztą e-mail. 

## Bezpieczne udostępnianie dokumentu w wiadomościach e-mail

1.  Otwórz dokument w programie Word. Zobaczysz, że ponownie zastosowano automatycznie domyślną etykietę **Wewnętrzny**. 

2.  Na karcie **Narzędzia główne** w grupie **RMS** kliknij pozycję **Udostępnij chronioną zawartość**, a następnie kliknij pozycję **Udostępnij chronioną zawartość** w menu:

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 5 — udostępnianie chronionej zawartości](../media/share-protected-callout.png)

    Zobaczysz okno dialogowe **Udostępnianie chronionej zawartości**, podobne do poniższej ilustracji:

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 5 — okno dialogowe Udostępnianie chronionej zawartości](../media/example-share-protected-dialog.png)

3. W polu **UŻYTKOWNICY** wprowadź co najmniej jeden służbowy adres e-mail, jak w przypadku wysyłania dokumentu do osoby, z którą współpracuje organizacja. Możesz też wpisać adres e-mail współpracownika. Upewnij się, że podajesz służbowe adresy e-mail, np. **joannam@contoso.com** lub **pmichalski@fabrikam.com**, ponieważ obecnie usługa Azure Information Protection nie obsługuje osobistych adresów e-mail. 

    Nie musisz martwić się tym, czy odbiorca wiadomości również ma usługę Azure Information Protection.

4. Wybierz opcję **Przeglądający — tylko wyświetlanie**.

    Oznacza to, że odbiorcy będą mogli wyświetlić dokument, ale nie będą mogli go edytować ani drukować.

5. Wybierz opcję **Wyślij mi wiadomość e-mail, gdy ktoś spróbuje otworzyć te dokumenty**.

    Otrzymasz wiadomość e-mail z powiadomieniem za każdym razem, gdy któryś z odbiorców spróbuje otworzyć załącznik, a także wtedy, gdy ktoś inny spróbuje go otworzyć, np. jeśli jeden z odbiorców prześle wiadomość e-mail dalej do współpracownika. Jeśli dokument zostanie przekazany, zobaczysz, że nastąpiła odmowa dostępu oraz otrzymasz dane użytkownika. Możesz zdecydować, czy wysłać tej osobie kopię dokumentu, którą będzie mogła otworzyć.

6. Wybierz opcję **Zezwalaj mi na natychmiastowe odwołanie dostępu do tych dokumentów**.

    Ta opcja wymaga od odbiorców połączenia internetowego za każdym razem, gdy próbują otworzyć załącznik, ale niesie ze sobą dodatkową korzyść: jeśli w późniejszym czasie wycofasz dokument, odbiorcy nie będą mogli go otworzyć przy kolejnej próbie. 

4.  Kliknij przycisk **Wyślij**, aby wyświetlić wiadomość e-mail gotową do wysłania do określonych odbiorców z domyślnym tekstem instrukcji. Na przykład:

    ![Przykładowa wiadomość e-mail w przypadku udostępniania dokumentów chronionych](../media/example-email-share-protected.png)
    
    **UWAGA**: jeśli program Outlook był otwarty w momencie instalacji klienta usługi Azure Information Protection, nie będzie wyświetlany pasek Information Protection widoczny na powyższym rysunku. Nie jest on używany na tym etapie przedstawiającym udostępnianie dokumentów chronionych, dlatego nie jest konieczne zamknięcie i ponowne otwarcie programu Outlook w celu ukończenia samouczka. Jeśli program Outlook został otwarty po zainstalowaniu klienta usługi Azure Information Protection, zobaczysz że ta wiadomość e-mail, podobnie jak dokument Word przy pierwszym otwarciu, ma domyślnie etykietę **Wewnętrzny** w związku ze skonfigurowaniem tego ustawienia globalnego w zasadach usługi Azure Information Protection.
    
    Możesz zauważyć dwa załączniki: oryginalny dokument programu Word oraz plik o tej samej nazwie, ale z rozszerzeniem **ppdf**. Wersja ppdf to chroniony plik PDF utworzony automatycznie przez aplikację RMS sharing na wypadek, jeśli odbiorca nie dysponuje wersją pakietu Office obsługującą dokumenty chronione. Ten dodatkowy plik umożliwia odbiorcy odczyt dokumentu chronionego przy użyciu przeglądarki zainstalowanej wraz z aplikacją RMS sharing.

    Kliknij przycisk **Wyślij** w wiadomości e-mail.

Chroniony dokument został wysłany, więc możesz teraz poprosić adresatów o jego odebranie i otworzenie. Nie zamykaj jednak programu Word, ponieważ będziemy z niego korzystać ponownie w ostatnim kroku związanym ze śledzeniem udostępnionego dokumentu.

## Poproś odbiorców o otworzenie przesłanego dokumentu

Odbiorcy mogą użyć różnych urządzeń do odczytania chronionego dokumentu wysłanego w załączniku do wiadomości e-mail. Mogą to zrobić na urządzeniach iPad, iPhone, tabletach i telefonach z systemem Android, komputerach Mac i komputerach z systemem Windows.

Poproś odbiorców o odczytanie wysłanej wiadomości e-mail. Przy założeniu, że jest to pierwszy raz, kiedy otrzymali załączniki chronione przez usługę Rights Management, poproś ich o kliknięcie linku do instrukcji. Spowoduje to wyświetlenie strony [Witamy w usłudze Microsoft RMS!](https://portal.azurerms.com/#/rmshelp) zawierającej instrukcje związane z instalacją aplikacji RMS sharing. W razie potrzeby będą mogli się zarejestrować i uzyskać bezpłatne konto. Następnie będą mogli odczytać chroniony załącznik.

### Instrukcje dla odbiorcy: aby wyświetlić załącznik z chronionym dokumentem

1. Otwórz jeden z załączników, aby przeczytać dokument:
    
    - Jeśli masz na urządzeniu wersję pakietu Office, która obsługuje usługę Rights Management:
    
        -  Otwórz dokument o rozszerzeniu **docx**.
        
    - Jeśli nie ma wersji pakietu Office, która obsługuje usługę Rights Management lub jeśli nie masz pewności lub po prostu chcesz wypróbować przeglądarkę aplikacji RMS sharing: 
    
        - Otwórz dokument o rozszerzeniu **ppdf**.

2.  Jeśli zobaczysz monit o podanie nazwy użytkownika i hasła, podaj nazwę użytkownika w takim samym formacie jak format adresu e-mail użytego do wysłania tej wiadomości e-mail i załącznika. Na przykład **joannam@contoso.com** lub **pmichalski@fabrikam.com**. Wpisz hasło podane podczas rejestracji w usłudze RMS dla użytkowników indywidualnych. Lub, jeśli organizacja ma usługę w chmurze, taką jak Office 365, lub też używa platformy Azure, wprowadź zwykłe hasło służbowe.

3. Odczytaj zawartość dokumentu po jego otwarciu. Jako że dokument jest plikiem tylko do odczytu, nie możesz zmieniać jego zawartości.

Opcjonalnie odbiorca może przesłać wiadomość e-mail dalej do innych osób, które nie zostały uwzględnione w oryginalnej wiadomości e-mail. Te osoby nie będą mogły otworzyć załącznika. Gdy otrzymają monit o nazwę użytkownika, nastąpi odmowa dostępu do dokumentu.

Teraz po otwarciu załącznika przez odbiorcę (opcjonalnie po jego przesłaniu do innej osoby) możesz oczekiwać na powiadomienie e-mail z raportem o tym działaniu. Jednak wiadomości e-mail mogą się z czasem zagubić, dlatego lepszym sposobem na śledzenie dostępu do dokumentu jest użycie witryny śledzenia dokumentu. Metoda ta jest omówiona w ostatnim kroku samouczka.

## Aby śledzić chroniony dokument

1.  W programie Word na karcie **Narzędzia główne** w grupie **RMS** kliknij pozycję **Udostępnij chronioną zawartość**, a następnie kliknij pozycję **Śledź użycie** w menu:

    ![Opcja śledzenia użycia](../media/track-usage-callout.png)

    Spowoduje to przejście do witryny śledzenia dokumentów.

2.  Jeśli zobaczysz stronę **Chroń i udostępniaj na własnych warunkach**, kliknij opcję **Zaloguj się** i podaj ponownie nazwę użytkownika i hasło.

3.  Na stronie **Twoje dokumenty udostępnione** zobaczysz nazwę udostępnionego dokumentu. W tym momencie jest to jedyny wyświetlany plik, ale liczba pozycji na liście będzie rosnąć wraz z udostępnianiem kolejnych dokumentów chronionych.

    Na tej stronie możesz zobaczyć czas udostępnienia dokumentu (kiedy wysłano wiadomość e-mail z chronionym dokumentem), datę ostatniej aktywności oraz nazwę odbiorcy, do którego wysłano wiadomość e-mail. Kliknij nazwę dokumentu, aby uzyskać dodatkowe informacje.

4.  Na nowej stronie, która zawiera nazwę klikniętego pliku, zobaczysz szczegółowe informacje dotyczące wyłącznie tego dokumentu oraz listę opcji dostępnych dla tego dokumentu (**Lista**, **Oś czasu**, **Mapa**, **Ustawienia**).

    Klikaj poszczególne opcje, aby poznać różne sposoby śledzenia chronionego dokumentu. Lub (nadal na stronie **Podsumowanie**) kliknij opcję **Otwórz w programie Excel**, aby wyeksportować informacje do arkusza kalkulacyjnego, albo kliknij opcję **Odwołaj dostęp**, aby zatrzymać udostępnianie dokumentu.

Możesz powrócić do tej witryny, aby śledzić dalszą aktywność dotyczącą chronionego dokumentu lub w razie potrzeby wycofać dostęp. Możesz również uzyskać dostęp do witryny z urządzenia przenośnego lub tabletu, korzystając z przeglądarki i następującego linku: [śledzenie dokumentu](http://go.microsoft.com/fwlink/?LinkId=529562)



|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Pełne instrukcje i alternatywne metody ochrony plików udostępnianych za pośrednictwem poczty e-mail|[Ochrona plików udostępnianych pocztą e-mail za pomocą aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-protect-by-email.md)|
|Informacje o opcjach dostępnych w oknie dialogowym **Udostępnianie chronionej zawartości**|[Opcje w oknach dialogowych aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management](../rms-client/sharing-app-dialog-box.md)|
|Informacje o bezpłatnych kontach umożliwiających rejestrację innych użytkowników|[Usługa RMS dla użytkowników indywidualnych i usługa Azure Rights Management](../understand-explore/rms-for-individuals.md)|
|Informacje o korzystaniu z witryny śledzenia dokumentów|[Śledzenie i odwoływanie dokumentów](../rms-client/sharing-app-track-revoke.md)


## Następne kroki

Po zapoznaniu się z domyślnymi zasadami usługi Azure Information Protection i sposobami ich dostosowywania oraz z działaniem etykietowania dla programu Word poeksperymentuj z innymi ustawieniami i zobacz, jak działają w innych aplikacjach pakietu Office obsługujących usługę Azure Information Protection: Excel, PowerPoint i Outlook. Jeśli te aplikacje były otwarte podczas instalowania klienta Azure Information Protection, zamknij je i otwórz przed podjęciem próby używania usługi Azure Information Protection.

Spróbuj udostępnić więcej dokumentów i śledź ich użycie oraz potwierdź sposób działania funkcji odwoływania dokumentów.

Następnie przydatne może być przeczytanie niektórych [często zadawanych pytań](faqs.md) dotyczących usługi Azure Information Protection oraz zapoznanie się z innymi artykułami dokumentacji. Jeśli jednak chcesz już rozpocząć wdrażanie usługi Azure Information Protection, następnym krokiem powinien być [plan wdrażania usługi Azure Information Protection](../plan-design/deployment-roadmap.md). 


<!--HONumber=Sep16_HO4-->


