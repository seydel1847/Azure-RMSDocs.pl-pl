---
title: Konfigurowanie etykiety i szablony dla różnych języków usługi Azure Information Protection
description: Możesz dodać obsługę innych języków dla etykiet, które użytkownicy widzą na pasku Information Protection, a także wszystkie szablony, które użytkownicy widzą, podając językach w ramach zasad usługi Azure Information Protection i importowanie tłumaczenia.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a0e89fd0-795b-4e7a-aea9-ff6fc9163bde
ms.openlocfilehash: 4131e3afae338d906011a9fe02a941baa61cf892
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32326807"
---
# <a name="how-to-configure-labels-and-templates-for-different-languages-in-azure-information-protection"></a>Jak skonfigurować szablony dla różnych języków i etykiety usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Mimo że domyślne etykiety dla usługi Azure Information Protection obsługuje wiele języków, musisz skonfigurować obsługę etykieta nazwy i opisy, które określisz. Tej konfiguracji, należy wykonać następujące czynności:

1. Wybierz języki, które korzystają użytkownicy. 

2. Eksportuj do pliku z bieżącej etykiety nazwy i opisy.

3. Przeprowadź edycję pliku do dostarczania tłumaczenia.

4. Zaimportuj plik do zasad usługi Azure Information Protection.

Można również skonfigurować szablony dla różnych języków, gdy mają zastosowanie jednej z następujących warunków. Ta konfiguracja jest odpowiednia, jeśli użytkownicy lub Administratorzy chcesz wyświetlać bieżący nazwę i opis szablonu w zlokalizowanych językach.

- Szablon został utworzony w klasycznym portalu Azure lub za pomocą programu PowerShell, a szablon nie jest połączony z etykietą za pomocą **wybierz szablon wstępnie zdefiniowany** ustawienia ochrony.

- Nie masz subskrypcji, która obsługuje etykiety, dzięki czemu tylko tworzenie i Zarządzanie szablonami w portalu Azure.

Wybierz języki, które odpowiadają ustawieniom językowym użytkowników dla pakietu Office i systemu Windows. Te nazwy etykiet i opisy są następnie wyświetlane na pasku usługi Azure Information Protection w aplikacji pakietu Office oraz w oknie dialogowym **Klasyfikacja i ochrona — usługa Azure Information Protection**. Aby uzyskać więcej informacji o wybranym języku, zobacz sekcję [Określanie wyświetlanego języka przez klienta Azure Information Protection](#how-the-azure-information-protection-client-determines-the-language-to- display). 

## <a name="to-configure-labels-and-templates-for-different-languages"></a>Aby skonfigurować szablony dla różnych języków i etykiety

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **ZARZĄDZAJ** > **języków** opcji menu: na **usługi Azure Information Protection — języków** bloku, wybierz opcję **dodać nowy język dla Tłumaczenie**. Wybierz języki, które chcesz dodać, a następnie wybierz **OK**. Możesz wpisać nazwę języka w polu wyszukiwania, lub przewiń listę dostępnych języków

3. Języki wybrane jest teraz wyświetlany na **usługi Azure Information Protection — języków** bloku:
    
    - Aby dodać innego języka, wybierz **dodać nowy język do tłumaczenia** i powtórz poprzedni krok. 
        
        > [!NOTE]
        > Pamiętaj, aby wybierać języki używane przez użytkowników w pakiecie Office oraz w systemie Windows. W niektórych przypadkach może to wymagać dwóch różnych ustawienia komputera.
        
    - Jeśli zmienisz zdanie na temat dowolnego dodanego języka, wybierz odpowiedni wpis z listy, a następnie kliknij pozycję **Usuń**.

4. Jeśli na liście znajdują się wszystkie wybrane przez Ciebie języki, zaznacz pole wyboru obok pozycji **NAZWA JĘZYKA**, aby wybrać wszystkie wpisy (lub też wybierz poszczególne wpisy), a następnie kliknij przycisk **Eksportuj**, aby zapisać w pliku lokalną kopię istniejących nazw etykiet i opisów. 
    
    Pobrany plik ma nazwę **exported localization.zip** i jest zapisany w lokalnym folderze Pobrane. Jest również dostępny po wybraniu jego nazwy pliku na pasku stanu w portalu Azure.

5. Wyodrębnij pliki z pliku **exported localization.zip**, tak aby otrzymać pliki xml dla każdego języka wybranego do pobrania. 

6. Dokonaj edycji każdego pliku xml: dla każdego ciągu w znacznikach `<LocalizedText>` i podaj tłumaczenia dla wszystkich wybranych języków. 

7. Po zakończeniu edycji wszystkich plików xml utwórz nowy skompresowany folder (zip) zawierającego te pliki. Skompresowany folder może mieć dowolną nazwę, ale musi mieć rozszerzenie zip.

8. Wróć do **usługi Azure Information Protection — języków** bloku, a następnie wybierz **importu**. Należy pamiętać, że jeśli ta opcja jest niedostępna, należy najpierw wyczyścić pole wyboru w obszarze **NAZWA JĘZYKA** lub pola wyboru indywidualnie wybranych języków.
    
    Po zakończeniu importowania zlokalizowanej nazwy i opisy pobrać użytkowników.

## <a name="how-the-azure-information-protection-client-determines-the-language-to-display"></a>Jak klient usługi Azure Information Protection określa język używany do wyświetlania

Po pobraniu przez użytkowników zasad usługi Azure Information Protection umożliwiających obsługę innych języków, język nazw etykiet i etykietek narzędzi widziany przez użytkowników jest określany w następujący sposób:

**Dla etykiet i etykietek narzędzi, które użytkownicy widzą na pasku usługi Azure Information Protection w aplikacjach pakietu Office:**

- W przypadku bezpośredniej zgodności z językiem aplikacji pakietu Office, nazwy etykiet i opisy są wyświetlane w tym języku.

- W przypadku niezgodności z językiem aplikacji pakietu Office nazwy etykiet i opisy są wyświetlane w języku podanym jako domyślny dla wszystkich użytkowników. Tym językiem jest zazwyczaj angielski, który jest używany w domyślnych zasadach.

**Dla etykiet i etykietek narzędzi, które użytkownicy widzą po kliknięciu prawym przyciskiem myszy w celu klasyfikowania i ochrony plików lub folderów:**

- W przypadku bezpośredniej zgodności z językiem systemu operacyjnego, nazwy etykiet i opisy są wyświetlane w tym języku.

- W przypadku niezgodności z językiem systemu operacyjnego nazwy etykiet i opisy są wyświetlane w języku podanym jako domyślny dla wszystkich użytkowników. Tym językiem jest zazwyczaj angielski, który jest używany w domyślnych zasadach.

## <a name="when-localized-label-names-are-not-used"></a>Gdy nie są używane zlokalizowane nazwy etykiet

W następujących scenariuszach zlokalizowanych nazw etykiety (i sublabel) nie są używane. W celu zachowania spójności w dzierżawie domyślny język jest zawsze używany dla następujących elementów:

- Dzienniki użycia klienta

- PowerShell (dane wyjściowe polecenia Get-AIPFileStatus)

- Metadane dokumentów i nagłówki wiadomości e-mail


## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu opcji, których można używać dla etykiet oraz innych ustawień dla zasad usługi Azure Information Protection, użyj linków w [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy) sekcji.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


