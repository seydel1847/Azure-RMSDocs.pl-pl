---
title: Konfigurowanie zasad o określonym zakresie dla usługi Azure Information Protection
description: Aby skonfigurować inne ustawienia i etykiety dla poszczególnych użytkowników, należy skonfigurować dla usługi Azure Information Protection zasady należące do zakresów.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/22/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 78fb739de9af22f2e1ab8414482ac16b68a1893e
ms.sourcegitcommit: 94d1c7c795e305444e9fde17ad73e46f242bcfa9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2018
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>Konfigurowanie zasad usługi Azure Information Protection odnoszących się do konkretnych użytkowników przy użyciu zasad o określonym zakresie

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

>[!NOTE]
> W tym artykule odzwierciedla najnowsze aktualizacje do portalu Azure, które pozwalają tworzyć etykiety niezależnie od globalnych zasad lub zakresie zasad. Opcję, aby opublikować zasady zostaną również usunięte. Jeśli dzierżawy nie jest jeszcze zaktualizowane dla tych zmian — na przykład nadal zobacz **publikowania** opcja dla usługi Azure Information Protection i nie ma **klasyfikacje** opcji menu — należy odczekać kilka dni i następnie wróć do niniejszych instrukcji.

Po pobraniu na komputery z zainstalowanym [klientem usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) zasad usługi Azure Information Protection do wszystkich użytkowników mają zastosowanie ustawienia i etykiety z domyślnych zasad lub zmiany skonfigurowane na potrzeby zasad globalnych. Aby uzupełnić je pod kątem określonych użytkowników, wybierając dla nich różne ustawienia i etykiety, należy utworzyć **zasady o określonym zakresie** skonfigurowane na potrzeby tych użytkowników.

Wszyscy użytkownicy uzyskują dostęp do globalnych zasad, które obejmują tytuł paska i etykietkę narzędzia, ustawienia globalne oraz globalne etykiety. Jeśli dla konkretnych użytkowników skonfigurowano zasady o określonym zakresie, użytkownicy ci będą otrzymywać dodatkowe ustawienia i etykiety. 

Zasady o określonym zakresie, podobnie jak etykiety, są uporządkowane w portalu Azure. Jeśli użytkownik jest skonfigurowany pod kątem kilku zakresów, zasada mająca zastosowanie w jego przypadku zostanie obliczona przed pobraniem. Zostanie zastosowane ostatnie ustawienie zasad według porządku. Etykiety, które widzi użytkownik, to etykiety z globalnych zasad oraz wszelkie dodatkowe etykiety należące do zasad o określonym zakresie, które mają zastosowanie do użytkownika. 

Jako że zasada o określonym zakresie zawsze dziedziczy etykiety i ustawienia z zasad globalnych, podczas tworzenia lub edytowania zasady o określonym zakresie wyświetlane są etykiety z zasad globalnych. Podczas edycji zasady o określonym zakresie nie można edytować etykiet z zasad globalnych. Można jednak dodać sublabels do dziedziczonej etykiety.

Na przykład jeśli globalne zasady uwzględniają etykietę o nazwie **Poufne**, to etykietę tę widzą wszyscy użytkownicy. Nie można usunąć ani zmienić jej kolejność o zakresie zasad. Ale warto utworzyć zakresie zasady dla działu marketingu, który dodaje nowe sublabel do poufne, tak, aby zobaczyć tych użytkowników **poufne \ promocji**. Tworzymy inne zasady zakresami dla działu sprzedaży, który dodaje nowe sublabel do poufne, tak, aby zobaczyć tych użytkowników **poufne \ partnerów**. Każdy sublabel może być skonfigurowany pod kątem różnych ustawień i sublabel jest widoczna tylko dla użytkowników w odpowiednich działów.

Aby skonfigurować zasadę usługi Azure Information Protection o określonym zakresie:

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.

    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **zasady** opcji menu: na **usługi Azure Information Protection — zasady** bloku, wybierz opcję **Dodaj nowy zasady**. Zostanie wyświetlony **zasad** bloku, który wyświetla z istniejących globalne zasady, gdzie można teraz skonfigurować nowej, zakres zasad.

3. Określ nazwę i opis zasady, które będą widoczne wyłącznie dla administratorów w portalu Azure. Nazwa musi być unikatowa dla dzierżawy. Następnie wybierz **Określ, które użytkownicy/grupy uzyskać te zasady**, a w kolejnych blokach Wyszukaj i wybierz użytkowników i grupy dla tej zasady. Etykiety i ustawienia skonfigurowane w ramach tych zasad o określonym zakresie zostaną zastosowane tylko do tych użytkowników.
    
    Ze względu na wydajność jest członkostwa grupy dla zasad w zakresie [pamięci podręcznej](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection).

4. Teraz Dodaj nowe etykiety lub skonfiguruj ustawienia zasad w zakresie. Zasady globalne są zawsze stosowane w pierwszej kolejności, można je jednak uzupełnić z użyciem nowych etykiet, które zastąpią ustawienia globalne. Na przykład w przypadku, gdy zasady globalne nie uwzględniają etykiety domyślnej, można skonfigurować różne etykiety domyślne dla różnych zasad o określonych zakresach odwołujących się do poszczególnych działów.

    Aby uzyskać pomoc w konfigurowaniu etykiet lub ustawień, użyj łączy w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).

6. Podobnie jak podczas edycji zasad globalnych po wprowadzeniu zmian w bloku Azure Information Protection kliknij przycisk **Zapisz**, aby zapisać wprowadzone zmiany, lub przycisk **Odrzuć**, aby przywrócić stan z ostatnio zapisanymi ustawieniami. 

7. Po zakończeniu wprowadzania zmian, które mają dla tego zakresu zasad w początkowym **usługi Azure Information Protection — zasady** bloku, upewnij się, że tych zasad w zakresie znajduje się w kolejności, będzie on stosowany. Należy zwrócić na to uwagę szczególnie wówczas, gdy dla tego samego użytkownika wybrano wiele zasad o określonym zakresie. Aby zmienić kolejność, wybierz menu kontekstowe (**...** ) i wybierz **Przenieś w górę** lub **Przenieś w dół**. 

Klient usługi Azure Information Protection sprawdza zmiany podczas każdego uruchomienia obsługiwanej aplikacji pakietu Office lub otwarcia Eksploratora plików. Klient pobiera wszelkie zmiany zasad globalnych lub zasad o określonym zakresie, które mają zastosowanie do danego użytkownika.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać przykład konfigurowania zasad domyślnych i zobaczyć efekty w aplikacji pakietu Office, wypróbuj [Samouczek Szybki start dla usługi Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
