---
title: Konfigurowanie zasad o określonym zakresie dla usługi Azure Information Protection
description: Aby skonfigurować inne ustawienia i etykiety dla poszczególnych użytkowników, należy skonfigurować dla usługi Azure Information Protection zasady należące do zakresów.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: b40431632d02445d12e1faac012c28c1b1e6f8e2
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169961"
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>Konfigurowanie zasad usługi Azure Information Protection odnoszących się do konkretnych użytkowników przy użyciu zasad o określonym zakresie

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Po pobraniu na komputery z zainstalowanym [klientem usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) zasad usługi Azure Information Protection do wszystkich użytkowników mają zastosowanie ustawienia i etykiety z domyślnych zasad lub zmiany skonfigurowane na potrzeby zasad globalnych. Aby uzupełnić je pod kątem określonych użytkowników, wybierając dla nich różne ustawienia i etykiety, należy utworzyć **zasady o określonym zakresie** skonfigurowane na potrzeby tych użytkowników.

Dla aplikacji, które obsługują klienta usługi Azure Information Protection wszyscy użytkownicy uzyskują globalnych zasad, które zawiera tytuł paska i etykietka narzędzia, ustawienia globalne oraz globalne etykiety. Jeśli dla konkretnych użytkowników skonfigurowano zasady o określonym zakresie, użytkownicy ci będą otrzymywać dodatkowe ustawienia i etykiety. 

Należy pamiętać, że oprócz aplikacjami klasycznymi pakietu Office, które obsługują klienta usługi Azure Information Protection, etykiety, również są obsługiwane przy użyciu programu PowerShell i skanera usługi Azure Information Protection. Oznacza to, że można tworzyć i konfigurować zasady o określonym zakresie dla kont, przeznaczonych do uruchamiania poleceń programu PowerShell lub skaner. 

Zasady o określonym zakresie, podobnie jak etykiety, są uporządkowane w portalu Azure. Jeśli użytkownik jest skonfigurowany pod kątem kilku zakresów, zasada mająca zastosowanie w jego przypadku zostanie obliczona przed pobraniem. Zostanie zastosowane ostatnie ustawienie zasad według porządku. Etykiety, które widzi użytkownik, to etykiety z globalnych zasad oraz wszelkie dodatkowe etykiety należące do zasad o określonym zakresie, które mają zastosowanie do użytkownika.

Jako że zasada o określonym zakresie zawsze dziedziczy etykiety i ustawienia z zasad globalnych, podczas tworzenia lub edytowania zasady o określonym zakresie wyświetlane są etykiety z zasad globalnych. Podczas edycji zasady o określonym zakresie nie można edytować etykiet z zasad globalnych. Można jednak dodać etykiet podrzędnych do etykiet odziedziczonych z zasad.

Na przykład jeśli globalne zasady uwzględniają etykietę o nazwie **Poufne**, to etykietę tę widzą wszyscy użytkownicy. Nie można usunąć ani zmienić kolejność go przy użyciu zasad o określonym zakresie. Można jednak utworzyć zasady o określonym zakresie dla działu marketingu, który dodaje nowy etykietę podrzędną do etykiety poufne, dzięki czemu użytkownicy zobaczą **poufne \ promocje**. Powstaje również inne zasady o określonym zakresie dla działu sprzedaży, który dodaje nowy etykietę podrzędną do etykiety poufne, dzięki czemu użytkownicy zobaczą **poufne \ partnerzy**. Każdy etykietę podrzędną można skonfigurować różne ustawienia i etykiety podrzędnej jest widoczna tylko dla użytkowników w poszczególnych działach.

Aby skonfigurować zasadę usługi Azure Information Protection o określonym zakresie:

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.

    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **zasady** opcji menu: na **usługi Azure Information Protection — zasady** bloku wybierz **Dodaj nową zasady**. Zostanie wyświetlony **zasad** bloku, który wyświetla Twoje istniejące globalnych zasad, gdzie można teraz skonfigurować nową, zasad o określonym zakresie.

3. Określ nazwę i opis zasady, które będą widoczne wyłącznie dla administratorów w portalu Azure. Nazwa musi być unikatowa dla dzierżawy. Następnie wybierz pozycję **Określ użytkowników i grup, które pobrać tę zasadę**, a w kolejnych blokach Wyszukaj i wybierz użytkowników i grup dla tych zasad. Etykiety i ustawienia skonfigurowane w ramach tych zasad o określonym zakresie zostaną zastosowane tylko do tych użytkowników.
    
    Ze względu na wydajność członkostwo w grupie dla zasad o określonym zakresie jest [pamięci podręcznej](prepare.md#group-membership-caching-by-azure-information-protection).

4. Teraz Dodaj nowe etykiety lub skonfigurować ustawienia zasad o określonym zakresie. Zasady globalne są zawsze stosowane w pierwszej kolejności, można je jednak uzupełnić z użyciem nowych etykiet, które zastąpią ustawienia globalne. Na przykład w przypadku, gdy zasady globalne nie uwzględniają etykiety domyślnej, można skonfigurować różne etykiety domyślne dla różnych zasad o określonych zakresach odwołujących się do poszczególnych działów.

    Aby uzyskać pomoc w konfigurowaniu etykiet lub ustawień, użyj łączy w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).

6. Podobnie jak podczas edycji zasad globalnych po wprowadzeniu zmian w bloku Azure Information Protection kliknij przycisk **Zapisz**, aby zapisać wprowadzone zmiany, lub przycisk **Odrzuć**, aby przywrócić stan z ostatnio zapisanymi ustawieniami. 

7. Po zakończeniu wprowadzania zmian, które mają zasady o określonym zakresie, w pierwszym **usługi Azure Information Protection — zasady** bloku, upewnij się, że te zasady o określonym zakresie w kolejności, chcesz go zastosować. Należy zwrócić na to uwagę szczególnie wówczas, gdy dla tego samego użytkownika wybrano wiele zasad o określonym zakresie. Aby zmienić kolejność, wybierz menu kontekstowe (**...** ) i wybierz **Przenieś w górę** lub **Przenieś w dół**. 

Klient usługi Azure Information Protection sprawdza zmiany podczas każdego uruchomienia obsługiwanej aplikacji pakietu Office lub otwarcia Eksploratora plików. Klient pobiera wszelkie zmiany zasad globalnych lub zasad o określonym zakresie, które mają zastosowanie do danego użytkownika.

## <a name="next-steps"></a>Kolejne kroki

Aby uzyskać przykład konfigurowania zasad domyślnych i zobaczyć efekty w aplikacji pakietu Office, wypróbuj [Samouczek Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).

