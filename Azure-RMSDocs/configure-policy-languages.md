---
title: Konfigurowanie etykiety i szablony w różnych językach dla usługi Azure Information Protection
description: Możesz dodać obsługę innych języków dla etykiet, które użytkownicy zobaczą na pasku usługi Information Protection i wszystkie szablony, które użytkownicy zobaczą, określając język w zasadach usługi Azure Information Protection i importując tłumaczenia.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a0e89fd0-795b-4e7a-aea9-ff6fc9163bde
ms.openlocfilehash: 191a89d62abcb4faefd7f23f2353ed785450d12e
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491284"
---
# <a name="how-to-configure-labels-and-templates-for-different-languages-in-azure-information-protection"></a>Jak skonfigurować etykiety i szablony w różnych językach dla usługi Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Mimo że domyślne etykiety usługi Azure Information Protection obsługuje wiele języków, należy skonfigurować obsługę nazwy etykiet i opisy, które określisz. Ta konfiguracja wymaga, należy wykonać następujące czynności:

1. Wybierz języki, które korzystają użytkownicy. 

2. Wyeksportuj swoje nazwy bieżących etykiet i opisy w pliku.

3. Edytuj plik, aby dokonać tłumaczenia.

4. Zaimportuj plik do zasad usługi Azure Information Protection.

Zastosowanie jednej z następujących warunków, można również skonfigurować szablony w różnych językach. Ta konfiguracja jest odpowiednia w przypadku użytkowników lub administratorów potrzeba wyświetlenia bieżącej nazwę i opis szablonu w zlokalizowanych językach.

- Szablon został utworzony w klasycznej witrynie Azure portal lub za pomocą programu PowerShell i szablonu nie jest połączony z etykiety za pomocą **wybierz wstępnie zdefiniowany szablon** ustawienia ochrony.

- Nie masz subskrypcji, która obsługuje etykiety, dzięki czemu tylko tworzenie i Zarządzanie szablonami w witrynie Azure portal.

Wybierz języki, które odpowiadają ustawieniom językowym użytkowników dla pakietu Office i systemu Windows. Te nazwy etykiet i opisy są następnie wyświetlane na pasku usługi Azure Information Protection w aplikacji pakietu Office oraz w oknie dialogowym **Klasyfikacja i ochrona — usługa Azure Information Protection**. Aby uzyskać więcej informacji o wybranym języku, zobacz sekcję [Określanie wyświetlanego języka przez klienta Azure Information Protection](#how-the-azure-information-protection-client-determines-the-language-to- display). 

## <a name="to-configure-labels-and-templates-for-different-languages"></a>Aby skonfigurować etykiety i szablony w różnych językach

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **ZARZĄDZAJ** > **języków** opcji menu: na **usługi Azure Information Protection — języki** bloku wybierz **Dodaj nowy język na potrzeby Tłumaczenie**. Wybierz języki, które chcesz dodać, a następnie wybierz pozycję **OK**. Możesz wpisać nazwę języka, w polu wyszukiwania, lub przewiń listę dostępnych języków

3. Wybrane języki są teraz wyświetlane na **usługi Azure Information Protection — języki** bloku:
    
    - Aby dodać inny język, wybierz **Dodaj nowy język do tłumaczenia** i powtórz ten krok. 
        
        > [!NOTE]
        > Pamiętaj, aby wybierać języki używane przez użytkowników w pakiecie Office oraz w systemie Windows. W niektórych przypadkach może to wymagać dwóch różnych ustawienia komputera.
        
    - Jeśli zmienisz zdanie na temat dowolnego dodanego języka, wybierz odpowiedni wpis z listy, a następnie kliknij pozycję **Usuń**.

4. Jeśli na liście znajdują się wszystkie wybrane przez Ciebie języki, zaznacz pole wyboru obok pozycji **NAZWA JĘZYKA**, aby wybrać wszystkie wpisy (lub też wybierz poszczególne wpisy), a następnie kliknij przycisk **Eksportuj**, aby zapisać w pliku lokalną kopię istniejących nazw etykiet i opisów. 
    
    Pobrany plik ma nazwę **exported localization.zip** i jest zapisany w lokalnym folderze Pobrane. Jest również dostępny po wybraniu jego nazwy pliku na pasku stanu w portalu Azure.

5. Wyodrębnij pliki z pliku **exported localization.zip**, tak aby otrzymać pliki xml dla każdego języka wybranego do pobrania. 

6. Dokonaj edycji każdego pliku xml: dla każdego ciągu w znacznikach `<LocalizedText>` i podaj tłumaczenia dla wszystkich wybranych języków. 

7. Po zakończeniu edycji wszystkich plików xml utwórz nowy skompresowany folder (zip) zawierającego te pliki. Skompresowany folder może mieć dowolną nazwę, ale musi mieć rozszerzenie zip.

8. Wróć do **usługi Azure Information Protection — języki** bloku, a następnie wybierz **importu**. Należy pamiętać, że jeśli ta opcja jest niedostępna, należy najpierw wyczyścić pole wyboru w obszarze **NAZWA JĘZYKA** lub pola wyboru indywidualnie wybranych języków.
    
    Po zakończeniu importowania zlokalizowane nazwy i opisy zostaną przekazane do użytkowników.

## <a name="how-the-azure-information-protection-client-determines-the-language-to-display"></a>Jak klient usługi Azure Information Protection określa język używany do wyświetlania

Po pobraniu przez użytkowników zasad usługi Azure Information Protection umożliwiających obsługę innych języków, język nazw etykiet i etykietek narzędzi widziany przez użytkowników jest określany w następujący sposób:

**Dla etykiet i etykietek narzędzi, które użytkownicy widzą na pasku usługi Azure Information Protection w aplikacjach pakietu Office:**

- W przypadku bezpośredniej zgodności z językiem aplikacji pakietu Office, nazwy etykiet i opisy są wyświetlane w tym języku.

- W przypadku niezgodności z językiem aplikacji pakietu Office nazwy etykiet i opisy są wyświetlane w języku podanym jako domyślny dla wszystkich użytkowników. Tym językiem jest zazwyczaj angielski, który jest używany w domyślnych zasadach.

**Dla etykiet i etykietek narzędzi, które użytkownicy widzą po kliknięciu prawym przyciskiem myszy w celu klasyfikowania i ochrony plików lub folderów:**

- W przypadku bezpośredniej zgodności z językiem systemu operacyjnego, nazwy etykiet i opisy są wyświetlane w tym języku.

- W przypadku niezgodności z językiem systemu operacyjnego nazwy etykiet i opisy są wyświetlane w języku podanym jako domyślny dla wszystkich użytkowników. Tym językiem jest zazwyczaj angielski, który jest używany w domyślnych zasadach.

## <a name="when-localized-label-names-are-not-used"></a>Gdy nie są używane zlokalizowane nazwy etykiet

W następujących scenariuszach zlokalizowane nazwy etykiet (i etykietę podrzędną) nie są używane. W celu zachowania spójności w dzierżawie domyślny język jest zawsze używany dla następujących elementów:

- Dzienniki użycia klienta

- PowerShell (dane wyjściowe polecenia Get-AIPFileStatus)

- Metadane dokumentów i nagłówki wiadomości e-mail


## <a name="next-steps"></a>Kolejne kroki

Aby uzyskać więcej informacji na temat konfigurowania opcji, które można wprowadzić etykiety i inne ustawienia zasad usługi Azure Information Protection, użyj linków w [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy) sekcji.



