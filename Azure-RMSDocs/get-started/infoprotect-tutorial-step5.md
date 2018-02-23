---
title: "Samouczek Szybki start — krok 5 — AIP"
description: "Krok 5 samouczka wprowadzającego do szybkiego wypróbowania usługi Azure Information Protection — udostępnianie plików chronionych i śledzenie dokumentu."
keywords: 
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/18/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4e59a3b3-f0f4-4535-8b96-cac68303d855
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 6d62b6dd588b035ded582a87f5faf04a04df6ab6
ms.sourcegitcommit: 2f1936753adf8d2fbea780d0a3878afa621daab5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2017
---
# <a name="step-5-see-sharing-of-protected-files-in-action-and-track-your-document"></a>Krok 5. Praktyczne udostępnianie plików chronionych i śledzenie dokumentu 

>*Dotyczy: Azure Information Protection*

W tym ostatnim kroku samouczka odszukaj utworzony wcześniej dokument programu Word lub arkusz kalkulacyjny programu Excel, który prześlesz do współpracownika. W ramach tego samouczka nie jest istotne, jaki tekst zawiera dokument. Niemniej dobrze będzie wpisać jakiś tekst, aby łatwiej potwierdzić, że autoryzowany odbiorca mógł go odczytać.

Następnie możesz bezpiecznie udostępnić ten dokument pocztą e-mail. 

## <a name="to-safely-share-your-document-by-email"></a>Bezpieczne udostępnianie dokumentu w wiadomościach e-mail

1. W oknie Eksploratora plików kliknij prawym przyciskiem myszy dokument, a następnie wybierz opcję **Klasyfikuj i chroń**. Zostanie wyświetlone okno dialogowe **Klasyfikuj i chroń — Azure Information Protection**:

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 5 — kliknięcie prawym przyciskiem myszy w celu wyboru opcji Klasyfikuj i chroń](../media/classify-protect-dialog.png)

2. Wybierz obszar **Ochrona przy użyciu uprawnień niestandardowych**, który zawiera dodatkowe opcje.

3. W przypadku opcji **Wybieranie uprawnień** zachowaj domyślną wartość **Przeglądający — tylko wyświetlanie**.

    Wybór tego ustawienia powoduje, że odbiorcy będą mogli wyświetlić dokument, ale nie będą mogli go edytować ani drukować.

4. W polu **Wybieranie użytkowników** wprowadź co najmniej jeden służbowy adres e-mail — tak jak w przypadku wysyłania dokumentu do osoby, z którą współpracuje organizacja. Aby określić więcej niż jeden adres, użyj średnika lub naciśnij klawisz Enter. 

    Upewnij się, określ adres e-mail biznesowych, takich jak **janetm@contoso.com** lub **p.dover@fabrikam.com** , ponieważ obecnie usługa Azure Information Protection nie obsługuje osobistych adresów e-mail dla tego Scenariusz. 

    Alternatywnie kliknij **Wybierz użytkowników, grup lub organizacji** ikonę, aby wybrać adres e-mail współpracownika:

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 5 — ochrona przy użyciu uprawnień niestandardowych](../media/protect-custom-permissions.png)  
    
    Po określeniu adresów skopiuj je do schowka — będą potrzebne na późniejszym etapie.

5. Kliknij przycisk **Zastosuj** i poczekaj na pojawienie się komunikatu **Ukończona praca**, aby zobaczyć wyniki. Następnie kliknij przycisk **Zamknij**.

4. W oknie Eksploratora plików ponownie kliknij plik prawym przyciskiem myszy, a następnie wybierz kolejno opcje **Wyślij do** > **Adresat poczty**. Wykonanie tych czynności spowoduje dołączenie dokumentu do wiadomości e-mail z domyślnym tekstem, który zostanie zmieniony.

5. Przed zmianą domyślnego tekstu wklej wybrane wcześniej adresy e-mail w polu **Do**. 

6. Opcjonalnie możesz także wprowadzić dowolny temat w polu **Temat**, na przykład: **Udostępniam chroniony dokument**. 

7. Zmodyfikuj opis domyślnej wiadomości, aby był on odpowiedni dla Twoich odbiorców. Pamiętaj o dodaniu do pliku poniższego tekstu:

    **Ten plik został przeze mnie objęty ochroną w ramach usługi Microsoft Azure Information Protection. Jeśli korzystasz z takiego pliku po raz pierwszy, zapoznaj się z instrukcjami: https://aka.ms/rms-signup.** 

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 5 — udostępnianie chronionego dokumentu za pośrednictwem poczty e-mail](../media/share-protected-emailv2.png)

    Kliknij pozycję **Wyślij**.

Chroniony dokument został wysłany, więc możesz teraz poprosić adresatów o jego odebranie i otworzenie. 

## <a name="ask-your-recipients-to-open-the-emailed-document"></a>Poproś odbiorców o otworzenie przesłanego dokumentu

Odbiorcy mogą użyć różnych urządzeń do odczytania chronionego dokumentu wysłanego w załączniku do wiadomości e-mail. Mogą to zrobić na urządzeniach iPad, iPhone, tabletach i telefonach z systemem Android, komputerach Mac i komputerach z systemem Windows.

Poproś odbiorców o odczytanie wysłanej wiadomości e-mail. Przy założeniu, że jest to pierwszy raz, kiedy otrzymali załączniki chronione przez usługę Rights Management, poproś ich o kliknięcie linku do instrukcji. Zostanie wyświetlona **strona powitalna** usługi Microsoft Azure Information Protection z monitem o podanie służbowego adresu e-mail.

Po kliknięciu przez użytkownika opcji **Zarejestruj się** usługa Azure Information Protection sprawdza, czy organizacja użytkownika ma subskrypcję, która obejmuje usługi ochrony danych Azure Rights Management. Jeśli nie, użytkownik może poprosić o założenie bezpłatnego konta.

### <a name="instructions-for-recipient-to-view-the-protected-document-attachment"></a>Instrukcje dla odbiorcy: aby wyświetlić załącznik z chronionym dokumentem

1. Na komputerze lub urządzeniu przenośnym z zainstalowanym pakietem Office otwórz załącznik, aby odczytać dokument.  

2.  Jeśli zobaczysz monit o podanie nazwy użytkownika i hasła, podaj nazwę użytkownika w takim samym formacie jak format adresu e-mail użytego do wysłania tej wiadomości e-mail i załącznika. Na przykład **janetm@contoso.com** lub **p.dover@fabrikam.com**. Wpisz hasło podane podczas rejestracji w usłudze RMS dla użytkowników indywidualnych. Lub, jeśli organizacja ma usługę w chmurze, taką jak Office 365, lub też używa platformy Azure, wprowadź zwykłe hasło służbowe.

3. Odczytaj zawartość dokumentu po jego otwarciu. Jako że dokument jest plikiem tylko do odczytu, nie możesz zmieniać jego zawartości.

Opcjonalnie odbiorca może przesłać wiadomość e-mail dalej do innych osób, które nie zostały uwzględnione w oryginalnej wiadomości e-mail. Te osoby nie będą mogły otworzyć załącznika. Gdy otrzymają monit o nazwę użytkownika, nastąpi odmowa dostępu do dokumentu.

Teraz, po otwarciu załącznika przez odbiorcę (opcjonalnie po jego przesłaniu do innej osoby), możesz śledzić dokument.

## <a name="to-track-your-protected-document"></a>Aby śledzić chroniony dokument

1.  Otwórz dokument, który został przez Ciebie objęty ochroną i udostępniony. Ten baner potwierdza niestandardowe ustawienia ochrony, które zostały wybrane:

    ![Baner potwierdzający niestandardowe ustawienia ochrony](../media/information-banner-custom-protection.png)

2.  Na karcie **Narzędzia główne** kliknij kolejno pozycje **Chroń** > **Śledź i odwołuj**:

    ![Opcja śledzenia użycia](../media/track-usage-calloutv3.png)

    Spowoduje to przejście do witryny śledzenia dokumentów.

2.  Jeśli zobaczysz stronę **Chroń i udostępniaj na własnych warunkach**, kliknij opcję **Zaloguj się** i podaj ponownie nazwę użytkownika i hasło.

3.  Na stronie **Twoje dokumenty udostępnione** zobaczysz nazwę udostępnionego dokumentu. W tym momencie jest to jedyny wyświetlany plik, ale liczba pozycji na liście będzie rosnąć wraz z udostępnianiem kolejnych dokumentów chronionych.

    Na tej stronie możesz zobaczyć czas udostępnienia dokumentu (kiedy wysłano wiadomość e-mail z chronionym dokumentem), datę ostatniej aktywności oraz nazwę odbiorcy, do którego wysłano wiadomość e-mail. Kliknij nazwę dokumentu, aby uzyskać dodatkowe informacje.

4.  Na nowej stronie, która zawiera nazwę klikniętego pliku, zobaczysz szczegółowe informacje dotyczące wyłącznie tego dokumentu oraz listę opcji dostępnych dla tego dokumentu (**Lista**, **Oś czasu**, **Mapa**, **Ustawienia**).

    Klikaj poszczególne opcje, aby poznać różne sposoby śledzenia chronionego dokumentu. Lub (nadal na stronie **Podsumowanie**) kliknij opcję **Otwórz w programie Excel**, aby wyeksportować informacje do arkusza kalkulacyjnego, albo kliknij opcję **Odwołaj dostęp**, aby zatrzymać udostępnianie dokumentu.

Możesz powrócić do tej witryny, aby śledzić dalszą aktywność dotyczącą chronionego dokumentu lub w razie potrzeby wycofać dostęp. Możesz również uzyskać dostęp do witryny z urządzenia przenośnego lub tabletu, korzystając z przeglądarki i następującego linku: [śledzenie dokumentu](http://go.microsoft.com/fwlink/?LinkId=529562)



|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Pełne instrukcje dotyczące ochrony plików, które można następnie bezpiecznie udostępniać|[Klasyfikowanie i ochrona pliku lub wiadomości e-mail](../rms-client/client-classify-protect.md)|
|Informacje o bezpłatnych kontach umożliwiających rejestrację innych użytkowników|[Usługa RMS dla użytkowników indywidualnych i usługa Azure Rights Management](../understand-explore/rms-for-individuals.md)|
|Informacje o korzystaniu z witryny śledzenia dokumentów|[Śledzenie i odwoływanie dokumentów](../rms-client/client-track-revoke.md)


## <a name="next-steps"></a>Następne kroki

Po zapoznaniu się z domyślnymi zasadami usługi Azure Information Protection i sposobami ich dostosowywania oraz z działaniem etykietowania dla programu Word poeksperymentuj z innymi ustawieniami i zobacz, jak działają w innych aplikacjach pakietu Office obsługujących usługę Azure Information Protection: Excel, PowerPoint i Outlook. Jeśli te aplikacje były otwarte podczas instalowania klienta Azure Information Protection, zamknij je i otwórz przed podjęciem próby używania usługi Azure Information Protection.

Spróbuj udostępnić więcej dokumentów i śledź ich użycie oraz potwierdź sposób działania funkcji odwoływania dokumentów.

Następnie przydatne może być powrót na stronę **Szybki start** w portalu Azure, przeczytanie niektórych [często zadawanych pytań](faqs.md) dotyczących usługi Azure Information Protection oraz zapoznanie się z innymi artykułami dokumentacji. Jeśli jednak chcesz już rozpocząć wdrażanie usługi Azure Information Protection, następnym krokiem powinien być [plan wdrażania usługi Azure Information Protection](../plan-design/deployment-roadmap.md). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]