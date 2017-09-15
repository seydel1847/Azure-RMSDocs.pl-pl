---
title: "Konfigurowanie warunków dla etykiety usługi Azure Information Protection"
description: "W przypadku skonfigurowania warunków dla etykiety możesz automatycznie przypisywać etykietę do dokumentu lub wiadomości e-mail. Możesz też monitować użytkowników o wybranie zalecanej etykiety."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: 09ee8587e6b254584f70dbe2475063831fd5b845
ms.sourcegitcommit: 6636defa6eca24360f15fb9ef93c2b82dc36cf76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

W przypadku skonfigurowania warunków dla etykiety możesz automatycznie przypisywać etykietę do dokumentu lub wiadomości e-mail. Możesz też monitować użytkowników o wybranie zalecanej etykiety: 

- Automatyczna klasyfikacja ma zastosowanie do programów Word, Excel i PowerPoint, gdy zapisywane są pliki oraz programu Outlook, gdy wysyłane są wiadomości e-mail. Nie możesz użyć automatycznej klasyfikacji wobec plików, które wcześniej zostały oznaczone ręcznie.
 
- Zalecana klasyfikacja ma zastosowanie do programów Word, Excel i PowerPoint, gdy zapisywane są pliki.

Gdy konfigurujesz warunki, można wstępnie zdefiniowanych wzorców, takich jak **numer karty kredytowej** lub **numer ubezpieczenia społecznego USA (SSN)**. Możesz zdefiniować niestandardowy ciąg lub szablon będący warunkiem automatycznej klasyfikacji. Te warunki dotyczą tekstu podstawowego w dokumentach i wiadomościach e-mail oraz nagłówków i stopek. Aby uzyskać więcej informacji o warunkach, zobacz [szczegóły dotyczące typów informacji](#details-about-the-information-types) sekcji.

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

5. Na **warunku** bloku, wybierz opcję **typów informacji** Jeśli chcesz użyć wstępnie zdefiniowanego warunku lub **niestandardowy** Jeśli chcesz określić własny, a następnie kliknij przycisk **Zapisać**:
    - Aby uzyskać **typów informacji**: Wybierz z listy dostępnych warunków, a następnie wybierz minimalną liczbę wystąpień i określa, czy wystąpienie powinno mieć unikatową wartość, aby było uwzględnione w liczbie wystąpień.
        
        Aby korzystać z pełną listą warunki, należy użyć bieżąca wersja klienta usługi Azure Information Protection. Jeśli masz bieżącej wersji ogólnodostępnej klienta następujące pięć warunków obsługiwane są tylko: **kod SWIFT**, **numer karty kredytowej**, **numer rozliczeniowy ABA**, **Numer ubezpieczenia społecznego USA (SSN)**, i **międzynarodowy numer konta bankowego (IBAN)**. [Więcej informacji](#details-about-the-information-types)
    
    - W przypadku opcji **Niestandardowy**: określ nazwę i frazę do dopasowania, bez znaków cudzysłowu i znaków specjalnych. Następnie określ, czy dopasowywać jako wyrażenie regularne, uwzględniać wielkość liter, a minimalna liczba wystąpień i określa, czy wystąpienie powinno mieć unikatową wartość do uwzględnienia w wystąpieniu liczba.
        
        Jeśli bieżąca wersja klienta usługi Azure Information Protection, wyrażeń regularnych Użyj wzorce regex usługi Office 365. Aby uzyskać więcej informacji, zobacz [definiujący wyrażenie regularne na podstawie dopasowań](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2) w dokumentacji pakietu Office. 
        
    **Przykład opcji wystąpień**: wybierz opcję wbudowanych numer ubezpieczenia społecznego, Ustaw minimalną liczbę wystąpień na 2 i dokument ma sam numer ubezpieczenia społecznego wymieniony dwukrotnie: Jeśli ustawisz **liczba wystąpień z tylko unikatowe wartości** do **na**, nie jest spełniony warunek. Jeśli ustawisz tę opcję, **poza**, warunek jest spełniony.

6. W bloku **Etykieta** skonfiguruj następujące opcje i kliknij przycisk **Zapisz**:
    
    - Wybierz automatyczną lub zalecaną klasyfikację: dla opcji **Wybierz sposób stosowania etykiety: automatycznie lub jako zalecenie dla użytkownika** wybierz wartość **Automatycznie** lub **Zalecenie**.
    
    - Określ tekst monitu dla użytkownika lub wskazówki dotyczącej zasad: zachowaj tekst domyślny lub podaj własny ciąg.

7. Aby udostępnić użytkownikom zmiany, w początkowym bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## <a name="details-about-the-information-types"></a>Szczegółowe informacje dotyczące typów informacji

Jeśli bieżąca wersja klienta usługi Azure Information Protection, pełną listę typów informacji, które są widoczne w portalu są obsługiwane:

- Typy informacji za pomocą usługi Office 365 wbudowane utraty zapobiegania (DLP) czułości informacji typy danych i wykrywania wzorca. Można wybrać z wielu popularnych typów informacji poufnych, niektóre z nich są specyficzne dla różnych regionach. Aby uzyskać więcej informacji na temat typów informacji, które można wybrać, zobacz [jakie dostępne typy informacji poufnych](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) w dokumentacji pakietu Office. 

- Lista typów informacji, które można wybierać z portalu Azure jest okresowo zaktualizowano wszelkich nowych dodatków pakietu Office DLP. Jednak listy nie obejmuje żadnych typów niestandardowych informacji poufnych, które zostały zdefiniowane i przekazany jako reguła pakiet Office 365 zabezpieczeń & Centrum zgodności. 

- Podczas usługi Azure Information Protection typów informacji, które można wybrać, jest używane ustawienie poziomu ufności DLP pakietu Office, ale jest zgodna z najniższą zaufania.

Jeśli masz bieżącej wersji ogólnodostępnej klienta następujące typy informacji obsługiwane są tylko:

- [Kod SWIFT](#swift-code )

- [Numer karty kredytowej](#credit-card-number )

- [Numer rozliczeniowy ABA](#aba-routing-number )

- [Numer ubezpieczenia społecznego USA (SSN)](#usa-social-security-number-ssn)

- [Międzynarodowy numer konta bankowego (IBAN)](#international-banking-account-number-iban)

Zobacz następujące sekcje, aby uzyskać więcej informacji na temat poszczególnych typów informacji dla wersji ogólnodostępnej klienta.

### <a name="swift-code"></a>Kod SWIFT

Dopasuj ten typ informacji, jeśli zawartość obejmuje następujące elementy:  

1. Jedna z następujących fraz: **swift**, **swiftnumber**, **swiftroutingnumber** 

2. Kod SWIFT w układzie sformatowanym:  

    a. 4 litery (kod banku)  

    b. 2 litery (kod kraju)  

    c. 2 litery lub cyfry (kod lokalizacji)  

    d. Opcjonalnie 3 litery lub cyfry (kod oddziału)  


Przykłady do testowania:

- **NEDSZAJJXXX Swiftroutingnumber**

- **NEDSZAJJ100 Swiftnumber** 

----


### <a name="credit-card-number"></a>Numer karty kredytowej

Dopasuj ten typ informacji, jeśli zawartość obejmuje następujące elementy:  

- Numer ważnej karty kredytowej, w układzie sformatowanym lub niesformatowanym, który przechodzi przez [kontrolę przy użyciu algorytmu Luhna](https://wikipedia.org/wiki/Luhn_algorithm). Ten typ informacji wykrywa karty wszystkich głównych marek na całym świecie, w tym karty Visa, MasterCard, Discover Card, American Express i Diners.

    - **Sformatowany**:
    
        - 16 cyfr: (dddd-dddd-dddd-dddd)  
        
    - **Niesformatowany**:
    
        - (dddddddddddddddd)  


Przykłady do testowania:

- **4242-4242-4242-4242**

- **4242424242424242** 

----

### <a name="aba-routing-number"></a>Numer rozliczeniowy ABA

Dopasuj ten typ informacji, jeśli zawartość obejmuje następujące elementy:  

1. Co najmniej jedna z następujących fraz: **aba**, **rtn**, **routing number** 

2. Numer rozliczeniowy ABA, który zawiera 9 cyfr, może być sformatowany lub niesformatowany: 

    - **Sformatowany**: 
        
        a. Cztery cyfry, z których pierwsza to 0, 1, 2, 3, 6, 7 lub 8 
        
        b. Łącznik 
        
        c. Cztery cyfry 
        
        d. Łącznik 
        
        e. Cyfra 
        
        Przykład: 3456-9876-1 ABA 
        
    - **Niesformatowany**: 
        
        9 kolejnych cyfr, z których pierwsza to 0, 1, 2, 3, 6, 7 lub 8 
        
        Przykład: 345698761 RTN 
 

Przykłady do testowania:

- **3456-9876-1 ABA**

- **345698761 RTN** 

----

### <a name="usa-social-security-number-ssn"></a>Numer ubezpieczenia społecznego USA (SSN)

Dopasuj ten typ informacji, jeśli zawartość obejmuje następujące elementy:  

1. Co najmniej jedna z następujących fraz: **ssn**, **social security**, **ssid**, **ss#** 

2. Numer ubezpieczenia społecznego: 9 cyfr w układzie sformatowanym lub niesformatowanym:

    - **Sformatowany**: 
    
        - Dziewięć cyfr w następującym formacie: ddd-dd-dddd lub ddd dd dddd 
        
    - **Niesformatowany**: 
    
        - Dziewięć cyfr w następującym formacie: ddddddddd 


Przykłady do testowania:

- **SSN 123-45-6789**

- **SS# 123456789** 


----

### <a name="international-banking-account-number-iban"></a>Międzynarodowy numer konta bankowego (IBAN)

Dopasuj ten typ informacji, jeśli zawartość obejmuje następujące elementy:  

1. Następująca fraza: **IBAN** 

2. Numer IBAN: rozpoczyna się od kodu kraju (dwie litery), następnie zawiera cyfry kontrolne (dwie cyfry) i numer bban (maksymalnie do 30 cyfr).


Przykłady do testowania:

- **GB29 NWBK 6016 1331 9268 19 IBAN**


## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


