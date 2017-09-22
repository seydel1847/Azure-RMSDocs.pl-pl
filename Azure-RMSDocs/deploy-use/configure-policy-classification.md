---
title: "Konfigurowanie warunków dla etykiety usługi Azure Information Protection"
description: "W przypadku skonfigurowania warunków dla etykiety możesz automatycznie przypisywać etykietę do dokumentu lub wiadomości e-mail. Możesz też monitować użytkowników o wybranie zalecanej etykiety."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: aa41d4f34f0ed43682f9ba426ec18204457980c3
ms.sourcegitcommit: 2f1936753adf8d2fbea780d0a3878afa621daab5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2017
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

W przypadku skonfigurowania warunków dla etykiety możesz automatycznie przypisywać etykietę do dokumentu lub wiadomości e-mail. Możesz też monitować użytkowników o wybranie zalecanej etykiety: 

- Automatyczna klasyfikacja ma zastosowanie do programów Word, Excel i PowerPoint, gdy zapisywane są pliki oraz programu Outlook, gdy wysyłane są wiadomości e-mail. Nie możesz użyć automatycznej klasyfikacji wobec plików, które wcześniej zostały oznaczone ręcznie.
 
- Zalecana klasyfikacja ma zastosowanie do programów Word, Excel i PowerPoint, gdy zapisywane są pliki.

Gdy konfigurujesz warunki, można wstępnie zdefiniowanych wzorców, takich jak **numer karty kredytowej** lub **numer ubezpieczenia społecznego USA (SSN)**. Możesz zdefiniować niestandardowy ciąg lub szablon będący warunkiem automatycznej klasyfikacji. Te warunki dotyczą tekstu podstawowego w dokumentach i wiadomościach e-mail oraz nagłówków i stopek. Aby uzyskać więcej informacji o warunkach, zobacz krok 5 w [procedury](#to-configure-recommended-or-automatic-classification-for-a-label).

W jaki sposób ocenia się wiele warunków, jeśli są zastosowane wobec więcej niż jednej etykiety:

1. Etykiety są uporządkowane do oceny zgodnie z ich pozycją określoną w zasadach: etykieta na pierwszej pozycji ma najniższą pozycję (najmniejszą ważność), a ostatnia najwyższą (największa ważność).

2. Zostaje zastosowana etykieta wskazująca najwyższą ważność.
 
3. Zostaje zastosowana ostatnia etykieta podrzędna.

> [!TIP]
>Aby zapewnić najlepszą jakość obsługi i ciągłość prowadzenia działalności biznesowej, warto rozpocząć od użycia zalecanej klasyfikacji dla użytkownika, a nie od klasyfikacji automatycznej. Ta konfiguracja pozwala użytkownikom Zaakceptuj etykiet lub akcji ochronnej lub zignorowania tych sugestii, jeśli nie są odpowiednie do ich dokumentu lub wiadomości e-mail.

Przykład monitu w przypadku konfigurowania warunki do zastosowania etykiety jako akcji zalecanej, ze wskazówką dotyczącą zasad niestandardowych:

![Wykrywanie i zalecenia usługi Azure Information Protection](../media/info-protect-recommend-calloutsv2.png)

W tym przykładzie użytkownik może kliknąć **teraz zmienić** Aby zastosować zalecaną etykietę, lub zignorować zalecenie przez wybranie **odrzucenia**.

## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Aby skonfigurować zalecaną lub automatyczną klasyfikację dla etykiety

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i zaloguj się do [portalu Azure](https://portal.azure.com) jako zabezpieczeń administratora lub administratora globalnego. Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. Jeśli etykietę, którą chcesz skonfigurować będą stosowane do wszystkich użytkowników, pozostają **usługi Azure Information Protection — globalne zasady** bloku.
    
    Jeśli trwa etykietę, którą chcesz skonfigurować [zakres zasad](configure-policy-scope.md) tak, aby dotyczył tylko wybrani użytkownicy z **zasady** zaznaczenia menu, wybierz opcję **zakres zasad**. Następnie wybierz zakresie zasad z **zasady usługi Azure Information Protection - zakres** bloku.

3. Z **usługi Azure Information Protection — globalne zasady** bloku lub **zasad:\<name >** bloku, wybierz etykietę, aby skonfigurować. 

4. W bloku **Etykieta** w sekcji **Konfigurowanie warunków dla automatycznego stosowania tej etykiety** kliknij przycisk **Dodaj nowy warunek**.

5. Na **warunku** bloku, wybierz opcję **typów informacji** Jeśli chcesz użyć wstępnie zdefiniowanego warunku lub **niestandardowy** Jeśli chcesz określić własny:
    - Aby uzyskać **typów informacji**: Wybierz z listy dostępnych warunków, a następnie wybierz minimalną liczbę wystąpień i określa, czy wystąpienie powinno mieć unikatową wartość, aby było uwzględnione w liczbie wystąpień.
        
        Typy informacji za pomocą typów informacji czułości zapobiegania (DLP) utraty danych usługi Office 365 i wykrywania wzorca. Można wybrać z wielu popularnych typów informacji poufnych, niektóre z nich są specyficzne dla różnych regionach. Aby uzyskać więcej informacji, zobacz [jakie dostępne typy informacji poufnych](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) w dokumentacji pakietu Office. 
        
        Lista typów informacji, które można wybierać z portalu Azure jest okresowo zaktualizowano wszelkich nowych dodatków pakietu Office DLP. Jednak listy nie obejmuje żadnych typów niestandardowych informacji poufnych, które zostały zdefiniowane i przekazany jako reguła pakiet Office 365 zabezpieczeń & Centrum zgodności. 
        
        Podczas usługi Azure Information Protection typów informacji, które można wybrać, jest używane ustawienie poziomu ufności DLP pakietu Office, ale jest zgodna z najniższą zaufania.
    
    - W przypadku opcji **Niestandardowy**: określ nazwę i frazę do dopasowania, bez znaków cudzysłowu i znaków specjalnych. Następnie określ, czy dopasowywać jako wyrażenie regularne, uwzględniać wielkość liter, a minimalna liczba wystąpień i określa, czy wystąpienie powinno mieć unikatową wartość do uwzględnienia w wystąpieniu liczba.
        
        Wyrażenia regularne użyć wzorców regex usługi Office 365. Aby uzyskać więcej informacji, zobacz [definiujący wyrażenie regularne na podstawie dopasowań](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2) w dokumentacji pakietu Office.
        
6. Zdecyduj, czy trzeba będzie zmienić **minimalna liczba wystąpień** i **liczba wystąpień tylko unikatowe wartości**, a następnie wybierz **zapisać**. 
    
    Przykład opcji wystąpień: Wybierz typ informacji numer ubezpieczenia społecznego, Ustaw minimalną liczbę wystąpień na 2 i dokument ma sam numer ubezpieczenia społecznego wymieniony dwukrotnie: Jeśli ustawisz **liczba wystąpień z Unikatowa wartość tylko** do **na**, nie jest spełniony warunek. Jeśli ustawisz tę opcję, **poza**, warunek jest spełniony.

7. Ponownie **etykiety** bloku, skonfiguruj następujące opcje, a następnie kliknij przycisk **zapisać**:
    
    - Wybierz automatyczną lub zalecaną klasyfikację: dla opcji **Wybierz sposób stosowania etykiety: automatycznie lub jako zalecenie dla użytkownika** wybierz wartość **Automatycznie** lub **Zalecenie**.
    
    - Określ tekst monitu dla użytkownika lub wskazówki dotyczącej zasad: zachowaj tekst domyślny lub podaj własny ciąg.

8. Aby udostępnić użytkownikom zmiany, w początkowym bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


