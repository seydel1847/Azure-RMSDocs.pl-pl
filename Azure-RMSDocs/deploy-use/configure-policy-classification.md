---
title: Konfigurowanie warunków dla etykiety usługi Azure Information Protection
description: W przypadku skonfigurowania warunków dla etykiety możesz automatycznie przypisywać etykietę do dokumentu lub wiadomości e-mail. Możesz też monitować użytkowników o wybranie zalecanej etykiety.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: 053d8dfd51d8c79cdc733f4395226c12ab6e2102
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32326756"
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

W przypadku skonfigurowania warunków dla etykiety możesz automatycznie przypisywać etykietę do dokumentu lub wiadomości e-mail. Możesz też monitować użytkowników o wybranie zalecanej etykiety. 

Po skonfigurowaniu tych warunków, można użyć wstępnie zdefiniowanych wzorców, takich jak **numer karty kredytowej** lub **numer ubezpieczenia społecznego USA (SSN)**. Możesz zdefiniować niestandardowy ciąg lub szablon będący warunkiem automatycznej klasyfikacji. Te warunki dotyczą tekstu podstawowego w dokumentach i wiadomościach e-mail oraz nagłówków i stopek. Aby uzyskać więcej informacji o warunkach, zobacz krok 5 w [procedury](#to-configure-recommended-or-automatic-classification-for-a-label).

Aby zapewnić najlepszą jakość obsługi i ciągłość prowadzenia działalności biznesowej, warto rozpocząć od użycia zalecanej klasyfikacji dla użytkownika, a nie od klasyfikacji automatycznej. Ta konfiguracja pozwala użytkownikom akceptowania klasyfikacji i wszystkie skojarzone ochrony lub zignorowania tych sugestii, jeśli nie są odpowiednie do ich dokumentu lub wiadomości e-mail.

Przykład monitu w przypadku konfigurowania warunki do zastosowania etykiety jako akcji zalecanej, ze wskazówką dotyczącą zasad niestandardowych:

![Wykrywanie i zalecenia usługi Azure Information Protection](../media/info-protect-recommend-calloutsv2.png)

W tym przykładzie użytkownik może kliknąć **teraz zmienić** Aby zastosować zalecaną etykietę, lub zignorować zalecenie przez wybranie **odrzucenia**. Jeśli użytkownik zdecydował się zamknąć zalecenie warunek nadal mają zastosowanie, gdy dokument zostanie otwarty następnym razem, ponownie wyświetlone zalecenie etykiety. 

> [!IMPORTANT]
>Nie należy konfigurować etykiety klasyfikacji automatycznej i uprawnienia użytkownika. Opcja uprawnienia zdefiniowane przez użytkownika jest [ustawienie ochrony](configure-policy-protection.md) który umożliwia użytkownikom określanie, kto powinien mieć uprawnienia.
>
>Po skonfigurowaniu etykiety klasyfikacji automatycznej i uprawnienia użytkownika zawartość jest sprawdzany pod kątem warunków, a ustawienie uprawnienia użytkownika nie została zastosowana. Można użyć zalecana klasyfikacja i uprawnienia użytkownika.

## <a name="how-automatic-or-recommended-labels-are-applied"></a>W jaki sposób są stosowane automatycznej lub zalecanej etykiety

- Automatyczna klasyfikacja ma zastosowanie do programu Word, Excel i PowerPoint, gdy dokumenty są zapisywane i dotyczą programu Outlook przy wysyłaniu wiadomości e-mail. 
    
    Nie można używać automatycznej klasyfikacji dokumentów i wiadomości e-mail, które zostały wcześniej oznaczone ręcznie lub wcześniej automatycznie oznaczenie wyższy klasyfikacji. 

- Zalecana klasyfikacja ma zastosowanie do programu Word, Excel i PowerPoint, gdy dokumenty są zapisywane. Nie można użyć zalecana klasyfikacja dla programu Outlook.
    
    Nie można użyć zalecana klasyfikacja dokumentów, które zostały wcześniej oznaczenie wyższy klasyfikacji. 

Aby zmienić to zachowanie, dzięki czemu klienta Azure Information Protection okresowo sprawdza, czy dokumenty reguł warunku, które można określić. Ta konfiguracja wymaga [Zaawansowane ustawienia klienta](../rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background) który jest obecnie w przeglądzie.

### <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>Jak wiele warunków są oceniane, jeśli są zastosowane wobec więcej niż jednej etykiety

1. Etykiety są uporządkowane do oceny zgodnie z ich pozycją określoną w zasadach: etykieta na pierwszej pozycji ma najniższą pozycję (najmniejszą ważność), a ostatnia najwyższą (największa ważność).

2. Zostaje zastosowana etykieta wskazująca najwyższą ważność.
 
3. Ostatni sublabel została zastosowana.


## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Aby skonfigurować zalecaną lub automatyczną klasyfikację dla etykiety

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **etykiety** opcji menu: na **usługi Azure Information Protection — etykiety** bloku, wybierz etykietę do skonfigurowania.

3. W bloku **Etykieta** w sekcji **Konfigurowanie warunków dla automatycznego stosowania tej etykiety** kliknij przycisk **Dodaj nowy warunek**.

4. Na **warunku** bloku, wybierz opcję **typów informacji** Jeśli chcesz użyć wstępnie zdefiniowanego warunku lub **niestandardowy** Jeśli chcesz określić własny:
    - Aby uzyskać **typów informacji**: Wybierz z listy dostępnych warunków, a następnie wybierz minimalną liczbę wystąpień i określa, czy wystąpienie powinno mieć unikatową wartość, aby było uwzględnione w liczbie wystąpień.
        
        Typy informacji za pomocą typów informacji czułości zapobiegania (DLP) utraty danych usługi Office 365 i wykrywania wzorca. Można wybrać z wielu popularnych typów informacji poufnych, niektóre z nich są specyficzne dla różnych regionach. Aby uzyskać więcej informacji, zobacz [jakie dostępne typy informacji poufnych](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) w dokumentacji pakietu Office.
        
        Lista typów informacji, które można wybierać z portalu Azure jest okresowo zaktualizowano wszelkich nowych dodatków pakietu Office DLP. Jednak listy nie obejmuje żadnych typów niestandardowych informacji poufnych, które zostały zdefiniowane i przekazany jako reguła pakiet Office 365 zabezpieczeń & Centrum zgodności. 
        
        Podczas usługi Azure Information Protection typów informacji, które można wybrać, jest używane ustawienie poziomu ufności DLP pakietu Office, ale jest zgodna z najniższą zaufania.
    
    - W przypadku opcji **Niestandardowy**: określ nazwę i frazę do dopasowania, bez znaków cudzysłowu i znaków specjalnych. Następnie określ, czy dopasowywać jako wyrażenie regularne, uwzględniać wielkość liter, a minimalna liczba wystąpień i określa, czy wystąpienie powinno mieć unikatową wartość do uwzględnienia w wystąpieniu liczba.
        
        Wyrażenia regularne użyć wzorców regex usługi Office 365. Aby uzyskać więcej informacji, zobacz [definiujący wyrażenie regularne na podstawie dopasowań](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2) w dokumentacji pakietu Office. Ponadto użytkownik może być bardzo przydatne do odwołania [składni wyrażeń regularnych języka Perl](http://www.boost.org/doc/libs/1_66_0/libs/regex/doc/html/boost_regex/syntax/perl_syntax.html) z zwiększanie wyniku.
        
5. Zdecyduj, czy trzeba będzie zmienić **minimalna liczba wystąpień** i **liczba wystąpień tylko unikatowe wartości**, a następnie wybierz **zapisać**. 
    
    Przykład opcji wystąpień: Wybierz typ informacji numer ubezpieczenia społecznego, Ustaw minimalną liczbę wystąpień na 2 i dokument ma sam numer ubezpieczenia społecznego wymieniony dwukrotnie: Jeśli ustawisz **liczba wystąpień z Unikatowa wartość tylko** do **na**, nie jest spełniony warunek. Jeśli ustawisz tę opcję, **poza**, warunek jest spełniony.

6. Ponownie **etykiety** bloku, skonfiguruj następujące opcje, a następnie kliknij przycisk **zapisać**:
    
    - Wybierz automatyczną lub zalecaną klasyfikację: dla opcji **Wybierz sposób stosowania etykiety: automatycznie lub jako zalecenie dla użytkownika** wybierz wartość **Automatycznie** lub **Zalecenie**.
    
    - Określ tekst monitu dla użytkownika lub wskazówki dotyczącej zasad: zachowaj tekst domyślny lub podaj własny ciąg.

Po kliknięciu **zapisać**, zmiany są automatycznie dostępne dla użytkowników i usług. Nie ma oddzielne Publikuj.

## <a name="next-steps"></a>Następne kroki

Rozważ wdrożenie [skanera usługi Azure Information Protection](deploy-aip-scanner.md), którego można użyć reguł automatycznej klasyfikacji do odnajdywania, klasyfikowania i chronić pliki w sklepach sieci lokalnych i udziałów plików.  

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

