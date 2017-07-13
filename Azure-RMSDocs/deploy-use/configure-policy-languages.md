---
title: "Konfigurowanie etykiet w różnych językach dla usługi Azure Information Protection"
description: "Możesz dodać obsługę innych języków dla etykiet, które użytkownicy będą widzieć na pasku Information Protection, określając język w ramach zasad usługi Azure Information Protection i importując tłumaczenia."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a0e89fd0-795b-4e7a-aea9-ff6fc9163bde
ms.openlocfilehash: ec99bf36e8904a7304a9d33c32d17ba92e2e22d2
ms.sourcegitcommit: 8b768e7e249e124f24acdf630d165eaf743f9c21
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2017
---
# Konfigurowanie etykiet w różnych językach dla usługi Azure Information Protection
<a id="how-to-configure-labels-for-different-languages-in-azure-information-protection" class="xliff"></a>

>*Dotyczy: Azure Information Protection*

>[!NOTE]
>Ta funkcja jest obecnie dostępna w wersji zapoznawczej, która powinna być używana razem z wersją **zapoznawczą** klienta usługi Azure Information Protection do pobrania z [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Domyślnie nazwy i opisy etykiet obsługują jeden język wyświetlany dla wszystkich użytkowników w organizacji. Można dodać obsługę innych języków, wybierając potrzebne, eksportując do pliku nazwy bieżących etykiet i opisy, edytując plik, aby dokonać tłumaczenia, a następnie importując go z powrotem do zasad usługi Azure Information Protection.

Wybierz języki, które odpowiadają ustawieniom językowym użytkowników dla pakietu Office i systemu Windows. Te nazwy etykiet i opisy są następnie wyświetlane na pasku usługi Azure Information Protection w aplikacji pakietu Office oraz w oknie dialogowym **Klasyfikacja i ochrona — usługa Azure Information Protection**. Aby uzyskać więcej informacji o wybranym języku, zobacz sekcję [Określanie wyświetlanego języka przez klienta Azure Information Protection](#how-the-azure-information-protection-client-determines-the-language-to- display). 

## Aby skonfigurować etykiety do wyświetlenia w różnych językach
<a id="to-configure-labels-to-display-in-different-languages" class="xliff"></a>

1. Jeśli jeszcze tego nie zrobiono, w nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator zabezpieczeń lub administrator globalny, a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. W początkowym bloku **Azure Information Protection** zlokalizuj pozycję **ZARZĄDZAJ**, a następnie wybierz **Języki (wersja zapoznawcza)**.

3. W bloku **Azure Information Protection — języki (wersja zapoznawcza)** zlokalizuj pierwszy język, który chcesz dodać, wpisując jego nazwę w polu wyszukiwania lub przewijając listę dostępnych języków. 

4. Wybierz swój język i kliknij przycisk **OK**.

5. W następnym bloku zobaczysz wybrany język dodany do listy:
    
    - Aby dodać następny język, wybierz pozycję **Dodaj nowy język do tłumaczenia** i powtórz kroki 3 i 4. 
        
        > [!NOTE]
        > Pamiętaj, aby wybierać języki używane przez użytkowników w pakiecie Office oraz w systemie Windows. W niektórych przypadkach może to wymagać dwóch różnych ustawienia komputera.
        
    - Jeśli zmienisz zdanie na temat dowolnego dodanego języka, wybierz odpowiedni wpis z listy, a następnie kliknij pozycję **Usuń**.

6. Jeśli na liście znajdują się wszystkie wybrane przez Ciebie języki, zaznacz pole wyboru obok pozycji **NAZWA JĘZYKA**, aby wybrać wszystkie wpisy (lub też wybierz poszczególne wpisy), a następnie kliknij przycisk **Eksportuj**, aby zapisać w pliku lokalną kopię istniejących nazw etykiet i opisów. 
    
    Pobrany plik ma nazwę **exported localization.zip** i jest zapisany w lokalnym folderze Pobrane. Jest również dostępny po wybraniu jego nazwy pliku na pasku stanu w portalu Azure.

7. Wyodrębnij pliki z pliku **exported localization.zip**, tak aby otrzymać pliki xml dla każdego języka wybranego do pobrania. 

8. Dokonaj edycji każdego pliku xml: dla każdego ciągu w znacznikach `<LocalizedText>` i podaj tłumaczenia dla wszystkich wybranych języków. 

9. Po zakończeniu edycji wszystkich plików xml utwórz nowy skompresowany folder (zip) zawierającego te pliki. Skompresowany folder może mieć dowolną nazwę, ale musi mieć rozszerzenie zip.

10. Wróć do bloku portalu Azure i wybierz pozycję **Importuj**. Należy pamiętać, że jeśli ta opcja jest niedostępna, należy najpierw wyczyścić pole wyboru w obszarze **NAZWA JĘZYKA** lub pola wyboru indywidualnie wybranych języków.
    
    Po zakończeniu importowania przetłumaczone nazwy etykiet i opisy zostaną przekazane do użytkowników po kolejnym opublikowaniu przez Ciebie zasad usługi Azure Information Protection. Możesz kliknąć opcję **Publikuj** w bloku **Zasady globalne** lub **Zasady z określonym zakresem**.

## Jak klient usługi Azure Information Protection określa język używany do wyświetlania
<a id="how-the-azure-information-protection-client-determines-the-language-to-display" class="xliff"></a>

Po pobraniu przez użytkowników zasad usługi Azure Information Protection umożliwiających obsługę innych języków, język nazw etykiet i etykietek narzędzi widziany przez użytkowników jest określany w następujący sposób:

**Dla etykiet i etykietek narzędzi, które użytkownicy widzą na pasku usługi Azure Information Protection w aplikacjach pakietu Office:**

- W przypadku bezpośredniej zgodności z językiem aplikacji pakietu Office, nazwy etykiet i opisy są wyświetlane w tym języku.

- W przypadku niezgodności z językiem aplikacji pakietu Office nazwy etykiet i opisy są wyświetlane w języku podanym jako domyślny dla wszystkich użytkowników. Tym językiem jest zazwyczaj angielski, który jest używany w domyślnych zasadach.

**Dla etykiet i etykietek narzędzi, które użytkownicy widzą po kliknięciu prawym przyciskiem myszy w celu klasyfikowania i ochrony plików lub folderów:**

- W przypadku bezpośredniej zgodności z językiem systemu operacyjnego, nazwy etykiet i opisy są wyświetlane w tym języku.

- W przypadku niezgodności z językiem systemu operacyjnego nazwy etykiet i opisy są wyświetlane w języku podanym jako domyślny dla wszystkich użytkowników. Tym językiem jest zazwyczaj angielski, który jest używany w domyślnych zasadach.

## Gdy nie są używane zlokalizowane nazwy etykiet
<a id="when-localized-label-names-are-not-used" class="xliff"></a>

W następujących scenariuszach zlokalizowane nazwy etykiet (i etykiet podrzędnych) nie są używane. W celu zachowania spójności w dzierżawie domyślny język jest zawsze używany dla następujących elementów:

- Dzienniki użycia klienta

- PowerShell (dane wyjściowe polecenia Get-AIPFileStatus)

- Metadane dokumentów i nagłówki wiadomości e-mail


## Następne kroki
<a id="next-steps" class="xliff"></a>

Aby uzyskać więcej informacji o konfigurowaniu opcji etykiet oraz innych ustawień zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


