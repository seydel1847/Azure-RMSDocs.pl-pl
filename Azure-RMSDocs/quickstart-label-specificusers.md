---
title: Przewodnik Szybki Start — Tworzenie nowej etykiety usługi Azure Information Protection pod kątem określonych użytkowników — AIP
description: Utwórz i skonfiguruj nową etykietę, która klasyfikuje dokumentów i wiadomości e-mail pod kątem określonych użytkowników przy użyciu zasad o określonym zakresie.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 1a8af09681411e49936c067c6161376c9d4f9f16
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023578"
---
# <a name="quickstart-create-a-new-azure-information-protection-label-for-specific-users"></a>Szybki Start: Tworzenie nowej etykiety usługi Azure Information Protection pod kątem określonych użytkowników

W tym przewodniku Szybki Start utworzysz nową etykietę, która tylko przez określonych użytkowników można zobaczyć i zastosować klasyfikować i chronić swoje dokumenty i wiadomości e-mail.

Ta konfiguracja korzysta z zasad o określonym zakresie.

Aby zakończyć tę konfigurację w mniej niż 10 minut.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik Szybki Start, potrzebne są:

1. Subskrypcja, która obejmuje usługi Azure Information Protection Plan 1 lub Plan 2.
    
    Jeśli nie masz jedną z tych subskrypcji, możesz utworzyć [bezpłatne](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) konta dla Twojej organizacji.

2. Został dodany do bloku usługi Azure Information Protection do witryny Azure portal i potwierdza, że aktywacji usługi ochrony.

    Jeśli potrzebujesz pomocy przy użyciu tych akcji, zobacz [Szybki Start: rozpoczęcie pracy w witrynie Azure portal](quickstart-viewpolicy.md).

3. Pocztą e-mail grupę z włączoną obsługą w usłudze Azure AD, która zawiera użytkowników, którzy będą zobaczyć i zastosować nową etykietę.
    
    Jeśli nie masz odpowiednich grup, utwórz ją o nazwie **zespół ds. sprzedaży** i Dodaj co najmniej jednego użytkownika.

4. Aby przetestować nową etykietę: klient usługi Azure Information Protection musi być zainstalowany na komputerach użytkowników. 
    
    Aby osobiście wypróbować jej etykiety, należy zainstalować klienta, przechodząc do [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) i Pobierz **AzInfoProtection.exe** ze strony usługi Azure Information Protection.

Aby uzyskać pełną listę wymagań wstępnych do używania usługi Azure Information Protection, zobacz [wymagania dotyczące usługi Azure Information Protection](requirements.md).
    
## <a name="create-a-new-label"></a>Tworzenie nowej etykiety

Najpierw należy utworzyć nowe etykiety.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i zaloguj się do [witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.
    
    Jeśli nie jesteś administratorem globalnym, użyj następującego linku, dla alternatywnej ról: [logowania się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal)

2. Z **klasyfikacje** > **etykiety** opcji menu: na **usługi Azure Information Protection — etykiety** bloku kliknij **Dodaj nową etykietę** .

3. Na **etykiety** bloku Określ co najmniej następujące czynności:
    
    - **Nazwa wyświetlana etykiety**: nazwę nowej etykiety, które użytkownicy będą widzieć i klasyfikacji zawartości, które identyfikują. Na przykład: `Sales - Restricted`.
    
    - **Opis**: etykietka narzędzia, aby ułatwić użytkownikom identyfikację sytuacjach należy wybierać nowej etykiety. Na przykład: `Business data that is restricted to the Sales Team.`

4. Upewnij się, że **włączone** ustawiono **na** (ustawienie domyślne) i wybierz **Zapisz**.

## <a name="add-the-label-to-a-new-scoped-policy"></a>Dodaj etykietę do nowych zasad o określonym zakresie

Teraz Dodaj nowo utworzony etykiety do nowych zasad o określonym zakresie.

1. Z **klasyfikacje** > **zasady** opcji menu: na **usługi Azure Information Protection — zasady** bloku wybierz **Dodaj nową zasady**. 

2. Na **zasad** bloku dla **nazwa_zasad** wprowadź nazwę, która identyfikuje grupę użytkowników, którzy zostanie wyświetlony nowy utworzonej etykiecie. Na przykład `Sales`.

3. Wybierz opcję **Wybierz użytkowników, którzy lub które grupy otrzymają te zasady**.

4. Na **AAD użytkowników i grup** bloku wybierz **Użytkownicy/grupy**. Następnie w nowym **użytkowników/grup** bloku, wyszukaj i wybierz grupę, który został zidentyfikowany w wymaganiach wstępnych. Na przykład **zespół ds. sprzedaży**. Kliknij przycisk **wybierz** w tym bloku, a następnie **OK**.

5. Po powrocie **zasad** bloku wybierz **apletu Dodaj lub usuń etykiety**.

6. Na **zasad: Dodaj lub usuń etykiety** bloku, wybierz etykietę, który został utworzony na przykład **sprzedaż — ograniczone**, a następnie wybierz pozycję **OK**.

7. Po powrocie **zasad** bloku wybierz **Zapisz**. 

Nowe etykiety jest teraz publikowana tylko do członków grupy, który określiłeś. 

## <a name="test-your-new-label"></a>Testowanie nowej etykiety

Aby przetestować tę etykietę, potrzebne są co najmniej dwa komputery, ponieważ klient usługi Azure Information Protection nie obsługuje wielu użytkowników na tym samym komputerze:

 - Na pierwszym komputerze Zaloguj się jako członek grupy zespół ds. sprzedaży. Otwórz program Word i upewnij się, że można nową etykietę. Jeśli program Word jest już otwarty, uruchom ponownie, aby wymusić odświeżenie zasad.

- Na drugim komputerze Zaloguj się jako użytkownik, który nie jest członkiem grupy zespół ds. sprzedaży. Otwórz program Word i upewnij się, że nie zobaczysz nową etykietę. Tak jak poprzednio Jeśli program Word jest już otwarty, uruchom go ponownie.

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Jeśli nie chcesz zachować tej etykiety i zasady o określonym zakresie, wykonaj następujące czynności:

1. Z **klasyfikacje** > **zasady** opcji menu: na **usługi Azure Information Protection — zasady** bloku, wybierz menu kontekstowe (**...** ) dla zasad o określonym zakresie właśnie utworzony. Na przykład **sprzedaży**.

2. Wybierz **usuwanie zasady** i jeśli zostanie wyświetlony monit o potwierdzenie, wybierz **OK**.

3. Z **klasyfikacje** > **etykiety** opcji menu: na **usługi Azure Information Protection — etykieta** bloku, wybierz menu kontekstowe (**...**) dla etykiety właśnie utworzony.  Na przykład **sprzedaż — ograniczone**.

4.  Wybierz **usunąć tę etykietę** i jeśli zostanie wyświetlony monit o potwierdzenie, wybierz **OK**.


## <a name="next-steps"></a>Kolejne kroki

Ten przewodnik Szybki Start zawiera minimalne opcje, dzięki czemu można szybko utworzyć nową etykietę pod kątem określonych użytkowników. Aby uzyskać pełne instrukcje zobacz następujące artykuły:

- [Tworzenie nowej etykiety](configure-policy-new-label.md)

- [Konfigurowanie zasad dla konkretnych użytkowników poprzez użycie zasad o określonym zakresie](configure-policy-scope.md)

Dodatkowo Jeśli chcesz, aby etykiety, aby chronić zawartość w taki sposób, że tylko członkowie zespołu sprzedaży mogą go otworzyć, należy skonfigurować etykietę do stosowania ochrony. Aby uzyskać instrukcje, zobacz [sposobu konfigurowania etykiety dla ochrony usługi Rights Management](configure-policy-protection.md).

