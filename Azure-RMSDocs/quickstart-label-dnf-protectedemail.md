---
title: Przewodnik Szybki Start — Konfigurowanie etykiety w celu użytkownikom łatwy sposób chronić wiadomości e-mail zawierające poufne informacje — AIP
description: Skonfiguruj etykietę chroniącą wiadomość e-mail dla użytkownika, automatycznie stosując ochrony nie przesyłaj dalej.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 217fbdc45967b5677f554410bca2ac1da58552d2
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023502"
---
# <a name="quickstart-configure-a-label-for-users-to-easily-protect-emails-that-contain-sensitive-information"></a>Szybki Start: Konfigurowanie etykiety w celu użytkownikom łatwy sposób chronić wiadomości e-mail zawierające poufne informacje

W tym przewodniku Szybki Start skonfigurujesz istniejącą etykietę, aby automatycznie zastosować ustawienie ochrony nie przesyłaj dalej.

Bieżące zasady usługi Azure Information Protection zawiera już dwóch etykiet, które mają tę konfigurację:

- **Poufne \ tylko adresaci**

- **Wysoce poufne \ tylko adresaci**

Jednak jeśli zasady jest starsza lub jeśli ochrony nie został aktywowany w momencie zasadami organizacji został utworzony, nie będziesz mieć tych etykiet. 

Aby zakończyć tę konfigurację w ciągu 5 minut.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik Szybki Start, potrzebne są:

1. Subskrypcja, która obejmuje usługi Azure Information Protection Plan 1 lub Plan 2.
    
    Jeśli nie masz jedną z tych subskrypcji, możesz utworzyć [bezpłatne](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) konta dla Twojej organizacji.

2. Został dodany do bloku usługi Azure Information Protection do witryny Azure portal i potwierdza, że aktywacji usługi ochrony.

    Jeśli potrzebujesz pomocy przy użyciu tych akcji, zobacz [Szybki Start: rozpoczęcie pracy w witrynie Azure portal](quickstart-viewpolicy.md).

3. Istniejącej etykiety usługi Azure Information Protection do skonfigurowania. 
    
    Można użyć jednego z domyślnych etykiet lub etykiet, który został utworzony. Jeśli potrzebujesz, aby uzyskać pomoc przy tworzeniu nowej etykiety, zobacz [Szybki Start: Tworzenie nowej etykiety usługi Azure Information Protection pod kątem określonych użytkowników](quickstart-label-specificusers.md).

4. Aby przetestować nową etykietę: klient usługi Azure Information Protection musi być zainstalowany na komputerach użytkowników. 
    
    Aby osobiście wypróbować jej etykiety, należy zainstalować klienta, przechodząc do [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) i Pobierz **AzInfoProtection.exe** ze strony usługi Azure Information Protection.

5. Aby przetestować nową etykietę: komputer z systemem Windows (co najmniej Windows 7 z dodatkiem Service Pack 1), a na tym komputerze, zalogowano Cię do aplikacji pakietu Office z jednej z następujących kategorii:
    
    - Usługa Office 365 z aplikacji pakietu Office 2016 (minimalna wersja 1805, kompilacja 9330.2078). Aby użyć tej opcji, Twoje konto musi mieć przypisaną licencję usługi Azure Rights Management. Ta licencja jest dołączone do subskrypcji usługi Azure Information Protection.
    
    - Usługi Office 365 Proplus z wersji aplikacji 2016 lub 2013 (Instalacja kliknij polecenie do uruchomienia lub opartych na Instalatorze Windows).
    
    - Office Professional Plus 2016.
    
    - Office Professional Plus 2013 z dodatkiem Service Pack 1.
    
    - Office Professional Plus 2010 z dodatkiem Service Pack 2.

Aby uzyskać pełną listę wymagań wstępnych do używania usługi Azure Information Protection, zobacz [wymagania dotyczące usługi Azure Information Protection](requirements.md).

## <a name="configure-an-existing-label-to-apply-the-do-not-forward-protection"></a>Skonfiguruj istniejącą etykietę do stosowania ochrony nie przesyłaj dalej

1. Otwórz nowe okno przeglądarki i zaloguj się do [witryny Azure portal](https://portal.azure.com) jako administrator globalny. Następnie przejdź do **usługi Azure Information Protection**. 
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.
    
    Jeśli nie jesteś administratorem globalnym, użyj następującego linku, dla alternatywnej ról: [logowania się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal)

2. Z **klasyfikacje** > **etykiety** opcji menu: na **usługi Azure Information Protection — etykiety** bloku, wybierz etykietę, którą chcesz skonfigurować do zastosowania ochrony. 

3. W bloku **Etykieta** znajdź opcję **Ustaw uprawnienia dla dokumentów i wiadomości e-mail zawierających tę etykietę**. Wybierz **chronić**, a następnie **ochrony**:
    
    ![Konfigurowanie ochrony dla etykiety usługi Azure Information Protection](./media/info-protect-protection-bar-configured.png).

4. Na **ochrony** bloku, upewnij się, że **Azure (klucz w chmurze)** jest zaznaczone.
    
5. Wybierz **Ustaw uprawnienia zdefiniowane przez użytkownika (wersja zapoznawcza)**.

6. Upewnij się, że wybrano następujące opcje: **w programie Outlook Zastosuj nie przesyłaj dalej**.

7. Jeśli zaznaczone, wyczyść będzie następująca opcja: **w programie Word, Excel, PowerPoint i Eksploratora plików Monituj użytkownika o uprawnienia niestandardowe**.

8. Kliknij przycisk **OK** na **ochrony** bloku, a następnie kliknij **Zapisz** na **etykiety** bloku.

Etykiety jest teraz skonfigurowane wyświetlane tylko w programie Outlook w celu zastosowania ochrony nie przesyłaj dalej wiadomości e-mail.

## <a name="test-your-new-label"></a>Testowanie nowej etykiety

Etykiety skonfigurowane wyświetla tylko w programie Outlook i nadaje się do wiadomości e-mail wysłanych na każdy adresat spoza Twojej organizacji, w przypadku usługi Exchange Online skonfigurowano na potrzeby [nowe funkcje w szyfrowanie wiadomości usługi Office 365](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e).

1. Na komputerze otwórz program Outlook, a następnie utwórz nową wiadomość e-mail. Jeśli program Outlook jest już otwarty, uruchom ponownie, aby wymusić odświeżenie zasad.

2. Określ adresatów jakiś tekst wiadomości e-mail, a następnie zastosować etykietę, który został utworzony. 
    
    Wiadomości e-mail sklasyfikowane zgodnie z nazwę etykiety i jest chroniony za pomocą ograniczeń nie przesyłaj dalej.

3. Wyślij wiadomość e-mail. 

Wynik jest, że adresatów nie może przesyłać dalej wiadomości e-mail, drukować, kopiować, lub Zapisz załączniki lub zapisać wiadomość e-mail z inną nazwą. Chronionej wiadomości e-mail może zostać odczytany przez dowolnego użytkownika, na dowolnym urządzeniu.

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Jeśli nie chcesz zachować tę konfigurację i zwracać etykiety w taki sposób, że nie ma zastosowania ochrony, wykonaj następujące czynności:

1. Z **klasyfikacje** > **etykiety** opcji menu: na **usługi Azure Information Protection — etykiety** bloku, wybierz etykietę, został skonfigurowany. 

3. Na **etykiety** bloku Znajdź **ustawić uprawnienia dla dokumentów i wiadomości e-mail zawierających tę etykietę**, wybierz opcję **nieskonfigurowane**i wybierz **Zapisz**.

## <a name="next-steps"></a>Kolejne kroki

Ten przewodnik Szybki Start zawiera minimalne opcje, tak że można szybko skonfigurować etykietę, która ułatwia użytkownikom chronić wiadomości e-mail. Jednak w przypadku zbyt restrykcyjne lub nie restrykcyjne wystarczająco konfiguracji Zobacz przykładowe konfiguracje:

- [Etykieta dla chronionych wiadomości e-mail, obsługującego mniej restrykcyjne uprawnienia niż nie przesyłaj dalej](configure-policy-protection.md#example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward)

- [Etykiety, która szyfruje zawartość, ale nie ogranicza kto ma dostęp](configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it)

Aby uzyskać pełne instrukcje jak konfigurowanie etykiety ochrony, która odnosi zobacz [sposobu konfigurowania etykiety dla ochrony usługi Rights Management](configure-policy-protection.md). 
