---
title: Konfigurowanie praw użytkowania dla usługi Azure Rights Management — AIP
description: Informacje pomagające zrozumieć i zidentyfikować określone prawa, które są używane w przypadku ochrony plików lub wiadomości e-mail przy użyciu usługi Azure Rights Management w ramach usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/14/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a7bf1e202fdff99375054647e04d44d44eecdb85
ms.sourcegitcommit: 5b48131ace3bbaf82f22fcb7eedf735c2f73d962
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429903"
---
# <a name="configuring-usage-rights-for-azure-rights-management"></a>Konfigurowanie praw użytkowania dla usługi Azure Rights Management

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Jeśli ustawiasz ochronę plików lub wiadomości e-mail za pomocą usługi Azure Rights Management w ramach usługi Azure Information Protection bez użycia szablonu, musisz własnoręcznie skonfigurować prawa użytkowania. Ponadto podczas konfigurowania szablonów lub etykiety dla ochrony usługi Azure Rights Management, wybierasz prawa użytkowania, które zostaną automatycznie zastosowane po wybraniu szablonu lub etykieta przez użytkowników, administratorów lub skonfigurowane usługi. Na przykład w witrynie Azure portal możesz wybrać role, które powodują ustawienie logicznego grupowania praw użytkowania, lub możesz skonfigurować poszczególne prawa.

Niniejszy artykuł pomoże Ci skonfigurować prawa użytkowania dla używanej aplikacji oraz zrozumieć, jak te prawa będą interpretowane przez aplikacje.

> [!NOTE] 
> Aby informacje były kompletne ten artykuł zawiera wartości z klasycznego portalu Azure, który został wycofany 08 stycznia 2018 r.
>
> Aby ułatwić migrację do nowego portalu, zobacz [zadania, które były wykonywane przy użyciu klasycznego portalu Azure](migrate-portal.md).

## <a name="usage-rights-and-descriptions"></a>Prawa użytkowania wraz z opisami
Poniższa tabela zawiera listę i opisy praw użytkowania obsługiwanych przez usługę Rights Management oraz sposób ich wykorzystania i interpretowania. Są one wyświetlane według ich **nazwa pospolita**, który zazwyczaj jest sposobem na wyświetlenie prawa użytkowania lub do których odwołuje się, jak to przyjaźniejsza wersja jednowyrazowej wartości używanej w kodzie ( **kodowanie w zasadach** wartości). 

**Stała lub wartość API** jest nazwą zestawu SDK wywołania MSIPC API używanego podczas pisania aplikacji obsługujących usługę RMS. Wywołanie sprawdza prawa użytkowania lub dodaje prawo użytkowania do zasad.


|Prawa użytkowania|Opis|Wdrażanie|
|-------------------------------|---------------------------|-----------------|
|Nazwa pospolita: **Edytuj zawartość, Edytuj** <br /><br />Kodowanie w zasadach: **DOCEDIT**|Zezwala użytkownikowi na modyfikowanie, rozmieszczanie, formatowanie, lub sortowanie zawartości wewnątrz aplikacji. Nie nadaje prawa do zapisywania edytowanej kopii.<br /><br />W programie Word chyba że usługi Office 365 ProPlus za pomocą minimalnej wersji [1807](https://docs.microsoft.com/officeupdates/monthly-channel-2018#version-1807-july-25), to prawo nie jest wystarczające włączyć lub wyłączyć **śledzenie zmian**, lub aby korzystać ze wszystkich śledzenie zmian funkcji jako recenzenta. Zamiast tego należy używać śledzenia zmian ma następujące wymagania opcje po prawej stronie: **Pełna kontrola**. |Prawach niestandardowych pakietu Office: W ramach opcji **Zmień** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Edytuj zawartość**<br /><br />Nazwa w witrynie Azure portal: **Edytuj zawartość, Edytuj (DOCEDIT)**<br /><br />Nazwa w szablonach usługi AD RMS: **Edytowanie** <br /><br />Stała API lub wartość API: Nie dotyczy.|
|Nazwa pospolita: **Zapisz** <br /><br />Kodowanie w zasadach: **EDYTUJ**|Umożliwia użytkownikowi zapisanie dokumentu w bieżącej lokalizacji.<br /><br />W aplikacjach pakietu Office to prawo zezwala użytkownikowi na modyfikowanie dokumentu i zapisz go na nową lokalizację i nazwę, jeśli wybrany format pliku natywnie obsługuje ochronę usługi Rights Management. Ograniczenia formatu pliku gwarantuje, że oryginalna ochrony nie można usunąć z pliku.|Prawach niestandardowych pakietu Office: W ramach opcji **Zmień** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Zapisz plik**<br /><br />Nazwa w witrynie Azure portal: **Zapisz (EDIT)**<br /><br />Nazwa w szablonach usługi AD RMS: **Zapisz** <br /><br />Stała API lub wartość API: `IPC_GENERIC_WRITE L"EDIT"`|
|Nazwa pospolita: **Komentarz** <br /><br />Kodowanie w zasadach: **KOMENTARZ**|Pozwala dodawać adnotacje i komentarze do zawartości.<br /><br />To uprawnienie jest dostępne w zestawie SDK oraz jest dostępne w formie zasad ad hoc w usłudze Azure Information Protection i w module RMS Protection w środowisku Windows PowerShell. Zostało też zaimplementowane w niektórych aplikacjach dostawców oprogramowania. Nie jest jednak powszechnie używane i obecnie nie jest obsługiwane przez aplikacje pakietu Office.|Prawach niestandardowych pakietu Office: Nie zaimplementowano. <br /><br />Nazwa w klasycznym portalu Azure: Nie zaimplementowano.<br /><br />Nazwa w witrynie Azure portal: Nie zaimplementowano.<br /><br />Nazwa w szablonach usługi AD RMS: Nie zaimplementowano. <br /><br />Stała API lub wartość API: `IPC_GENERIC_COMMENT L"COMMENT`|
|Nazwa pospolita: **Zapisz jako, Eksportuj** <br /><br />Kodowanie w zasadach: **EKSPORTUJ**|Włącza opcję zapisu zawartości w pliku o innej nazwie (Zapisz jako). <br /><br />Dla dokumentów pakietu Office i klienta usługi Azure Information Protection plik może być zapisany bez ochrony i również ponownie objęta ochroną przy użyciu nowych ustawień i uprawnień. Te dozwolone operacje oznacza, że użytkownik, który ma te uprawnienia można zmienić lub usunąć etykiety usługi Azure Information Protection z chronionego dokumentu lub wiadomości e-mail. <br /><br />To uprawnienie umożliwia też użytkownikowi korzystanie z innych opcji eksportu w aplikacjach, np. opcji **Wyślij do programu OneNote**.<br /><br /> Uwaga: Jeśli nie udzieleniu tego prawa zabezpieczeń aplikacji pakietu Office umożliwia użytkownikowi zapis dokumentu pod nową nazwą, jeśli wybrany format pliku natywnie obsługuje ochronę usługi Rights Management.|Prawach niestandardowych pakietu Office: Jako część **Pełna kontrola** opcji. <br /><br />Nazwa w klasycznym portalu Azure: **Eksportuj zawartość (Zapisz jako)** <br /><br />Nazwa w witrynie Azure portal: **Zapisz jako, Eksportuj (EXPORT)**<br /><br />Nazwa w szablonach usługi AD RMS: **Eksportuj (Zapisz jako)** <br /><br />Stała API lub wartość API: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Nazwa pospolita: **do przodu** <br /><br />Kodowanie w zasadach: **DO PRZODU**|Włącza opcję przesyłania dalej wiadomości e-mail oraz dodawania adresatów w wierszach **Do** i **DW**. To prawo dotyczy tylko wiadomości e-mail, a nie dokumentów.<br /><br />Nie zezwala osobie przekazującej wiadomość dalej na przyznanie praw innym użytkownikom jako części akcji przekazywania. <br /><br />Gdy przyznasz to uprawnienie również przyznać **Edytuj zawartość, Edytuj** kliknij prawym przyciskiem myszy (nazwa pospolita), a ponadto przydziel **Zapisz** prawa (nazwa pospolita), aby upewnić się, że chronionej wiadomości e-mail nie jest dostarczana jako załącznik. Również określić tych praw, podczas wysyłania wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacja Outlook web app. Lub, aby użytkownicy w Twojej organizacji, którzy są wykluczeni z przy użyciu usługi Azure Rights Management service, ponieważ udało Ci się wdrożyć [kontrolek dołączania](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|Prawach niestandardowych pakietu Office: Odmowa dostępu w przypadku użycia standardowej zasady **Nie przesyłaj dalej**.<br /><br />Nazwa w klasycznym portalu Azure: **do przodu**<br /><br />Nazwa w witrynie Azure portal: **Prześlij dalej (FORWARD)**<br /><br />Nazwa w szablonach usługi AD RMS: **do przodu** <br /><br />Stała API lub wartość API: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Nazwa pospolita: **Pełna kontrola** <br /><br />Kodowanie w zasadach: **WŁAŚCICIEL**|Przyznaje wszystkie prawa do dokumentu. Można wykonywać wszystkie dostępne akcje.<br /><br />Obejmuje możliwość usunięcia ochrony i ponownego włączenia ochrony dokumentu. <br /><br />Pamiętaj, że to prawo użycia nie jest takie samo jak [właściciela usługi Rights Management](#rights-management-issuer-and-rights-management-owner).|Prawach niestandardowych pakietu Office: Jako opcja niestandardowa **Pełna kontrola**.<br /><br />Nazwa w klasycznym portalu Azure: **Pełna kontrola**<br /><br />Nazwa w witrynie Azure portal: **Pełna kontrola (OWNER)**<br /><br />Nazwa w szablonach usługi AD RMS: **Pełna kontrola** <br /><br />Stała API lub wartość API: `IPC_GENERIC_ALL L"OWNER"`|
|Nazwa pospolita: **Drukuj** <br /><br />Kodowanie w zasadach: **DRUKUJ**|Włącza opcje związane z drukowaniem zawartości.|Prawach niestandardowych pakietu Office: Jako opcja **Drukuj zawartość** w obszarze uprawnień niestandardowych. Nie jest to ustawienie określane dla poszczególnych odbiorców.<br /><br />Nazwa w klasycznym portalu Azure: **Drukuj**<br /><br />Nazwa w witrynie Azure portal: **Drukuj (PRINT)**<br /><br />Nazwa w szablonach usługi AD RMS: **Drukuj** <br /><br />Stała API lub wartość API: `IPC_GENERIC_PRINT L"PRINT"`|
|Nazwa pospolita: **Odpowiedz** <br /><br />Kodowanie w zasadach: **ODPOWIEDZ**|Włącza opcję **Odpowiedz** w kliencie poczty e-mail bez możliwości zmiany w wierszach **Do** lub **DW**.<br /><br />Gdy przyznasz to uprawnienie również przyznać **Edytuj zawartość, Edytuj** kliknij prawym przyciskiem myszy (nazwa pospolita), a ponadto przydziel **Zapisz** prawa (nazwa pospolita), aby upewnić się, że chronionej wiadomości e-mail nie jest dostarczana jako załącznik. Również określić tych praw, podczas wysyłania wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacja Outlook web app. Lub, aby użytkownicy w Twojej organizacji, którzy są wykluczeni z przy użyciu usługi Azure Rights Management service, ponieważ udało Ci się wdrożyć [kontrolek dołączania](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|Prawach niestandardowych pakietu Office: Nie dotyczy.<br /><br />Nazwa w klasycznym portalu Azure: **Odpowiedz**<br /><br />Nazwa w klasycznym portalu Azure: **Odpowiedz (REPLY)**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz** <br /><br />Stała API lub wartość API: `IPC_EMAIL_REPLY`|
|Nazwa pospolita: **Odpowiedz wszystkim** <br /><br />Kodowanie w zasadach: **REPLYALL**|Włącza opcję **Odpowiedz wszystkim** w kliencie poczty e-mail, ale nie zezwala użytkownikowi na dodawanie odbiorców w wierszach **Do** lub **DW**.<br /><br />Gdy przyznasz to uprawnienie również przyznać **Edytuj zawartość, Edytuj** kliknij prawym przyciskiem myszy (nazwa pospolita), a ponadto przydziel **Zapisz** prawa (nazwa pospolita), aby upewnić się, że chronionej wiadomości e-mail nie jest dostarczana jako załącznik. Również określić tych praw, podczas wysyłania wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacja Outlook web app. Lub, aby użytkownicy w Twojej organizacji, którzy są wykluczeni z przy użyciu usługi Azure Rights Management service, ponieważ udało Ci się wdrożyć [kontrolek dołączania](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|Prawach niestandardowych pakietu Office: Nie dotyczy.<br /><br />Nazwa w klasycznym portalu Azure: **Odpowiedz wszystkim**<br /><br />Nazwa w witrynie Azure portal: **Odpowiedz wszystkim (REPLY ALL)**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz wszystkim** <br /><br />Stała API lub wartość API: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Nazwa pospolita: **Wyświetl, Otwórz, Odczytaj** <br /><br />Kodowanie w zasadach: **WIDOK**|Umożliwia użytkownikom otworzenie dokumentu i wyświetlenie zawartości.<br /><br /> W programie Excel, to prawo nie jest wystarczające posortować dane, które wymaga następujących po prawej stronie: **Edytuj zawartość, Edytuj**. Aby filtrować dane w programie Excel, potrzebne są następujące dwa uprawnienia: **Edytuj zawartość, Edytuj** i **kopiowania**.|Prawach niestandardowych pakietu Office: Jako niestandardowa zasada **Odczytaj**, opcja **Wyświetl**.<br /><br />Nazwa w klasycznym portalu Azure: **Widok**<br /><br />Nazwa w witrynie Azure portal: **Wyświetl, Otwórz, Odczytaj (VIEW)**<br /><br />Nazwa w szablonach usługi AD RMS: **Odczyt** <br /><br />Stała API lub wartość API: `IPC_GENERIC_READ L"VIEW"`|
|Nazwa pospolita: **Kopiuj** <br /><br />Kodowanie w zasadach: **WYODRĘBNIJ**|Włącza opcje kopiowania danych (w tym przechwytywania ekranu) z dokumentu do tego samego lub innego dokumentu.<br /><br />W niektórych aplikacjach pozwala są także całego dokumentu do zapisania w postaci niechronionej.<br /><br />W programie Skype dla firm i podobne aplikacje do udostępniania ekranu Prezenter musi mieć to prawo do przedstawienia pomyślnie chronionego dokumentu. Jeśli Prezenter nie ma tego prawa, uczestników nie może wyświetlić dokument i wyświetlane jako blacked do nich.|Prawach niestandardowych pakietu Office: Jako opcja **Zezwalaj użytkownikom z dostępem do odczytu na kopiowanie zawartości** zasady niestandardowej.<br /><br />Nazwa w klasycznym portalu Azure: **Kopiuj i Wyodrębnij zawartość**<br /><br />Nazwa w witrynie Azure portal: **Kopiuj (EXTRACT)**<br /><br />Nazwa w szablonach usługi AD RMS: **Wyodrębnij** <br /><br />Stała API lub wartość API: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Nazwa pospolita: **Wyświetl prawa** <br /><br />Kodowanie w zasadach: **VIEWRIGHTSDATA**|Umożliwia użytkownikowi wyświetlenie zasad zastosowanych do dokumentu.|Prawach niestandardowych pakietu Office: Nie zaimplementowano.<br /><br />Nazwa w klasycznym portalu Azure: **Wyświetl przypisane prawa**<br /><br />Nazwa w witrynie Azure portal: **Wyświetl prawa (VIEWRIGHTSDATA)**.<br /><br />Nazwa w szablonach usługi AD RMS: **Wyświetl prawa** <br /><br />Stała API lub wartość API: `IPC_READ_RIGHTS L"VIEWRIGHTSDATA"`|
|Nazwa pospolita: **Zmień prawa** <br /><br />Kodowanie w zasadach: **EDITRIGHTSDATA**|Umożliwia użytkownikowi zmianę zasad mających zastosowanie do dokumentu. Obejmuje możliwość usunięcia ochrony.|Prawach niestandardowych pakietu Office: Nie zaimplementowano.<br /><br />Nazwa w klasycznym portalu Azure: **Zmień prawa**<br /><br />Nazwa w witrynie Azure portal: **Edytuj prawa (EDITRIGHTSDATA)**.<br /><br />Nazwa w szablonach usługi AD RMS: **Edytuj prawa** <br /><br />Stała API lub wartość API: `PC_WRITE_RIGHTS L"EDITRIGHTSDATA"`|
|Nazwa pospolita: **Zezwalaj na makra** <br /><br />Kodowanie w zasadach: **OBJMODEL**|Włącza opcję uruchamiania makr lub innych rozwiązań programistycznych albo zezwala na zdalny dostęp do zawartości w dokumencie.|Prawach niestandardowych pakietu Office: Jako opcja **Zezwalaj na dostęp programistyczny** zasady niestandardowej. Nie jest to ustawienie określane dla poszczególnych odbiorców.<br /><br />Nazwa w klasycznym portalu Azure: **Zezwalaj na makra**<br /><br />Nazwa w witrynie Azure portal: **Zezwalaj na makra (OBJMODEL)**<br /><br />Nazwa w szablonach usługi AD RMS: **Zezwalaj na makra** <br /><br />Stała API lub wartość API: Nie zaimplementowano.|

## <a name="rights-included-in-permissions-levels"></a>Prawa zawarte w poziomach uprawnień

Niektóre aplikacje grupują prawa użytkowania w poziomach uprawnień. Dzięki temu można łatwiej wybrać prawa użytkowania, które zazwyczaj stosuje się wspólnie. Te poziomy uprawnień upraszczają skomplikowane działania po stronie użytkowników, którzy mogą wybrać opcje oparte na rolach.  Na przykład **Recenzent** i **Współautor**. Chociaż opcje te często są dostępne z podsumowaniem praw, to mogą one nie obejmować wszystkich praw wymienionych w poprzedniej tabeli.

Lista poziomów uprawnień i Pełna lista prawa użytkowania, które zawierają, skorzystaj z poniższej tabeli. Prawa użytkowania są wyświetlane według ich [nazwa pospolita](#usage-rights-and-descriptions).

|poziom uprawnień|Aplikacje|Zawarte prawa do użytkowania|
|---------------------|----------------|---------------------------------|
|Przeglądanie|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br /> Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Wyświetl prawa; Odpowiedź [[1]](#footnote-1); Odpowiedz wszystkim [[1]](#footnote-1); Zezwalaj na makra [[2]](#footnote-2)<br /><br />Uwaga: Dla wiadomości e-mail użyj opcji recenzent zamiast tego poziomu uprawnień, aby upewnić się, że odpowiedź na wiadomość e-mail została odebrana jako wiadomość e-mail, a nie jako załącznik. Opcja Recenzent jest również wymagana podczas wysyłania wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacji Outlook Web App. Lub, aby użytkownicy w Twojej organizacji, którzy są wykluczeni z przy użyciu usługi Azure Rights Management service, ponieważ udało Ci się wdrożyć [kontrolek dołączania](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|
|Recenzent|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Wyświetl prawa; Odpowiedź: Odpowiedz wszystkim [[3]](#footnote-3); Do przodu [[3]](#footnote-3); Zezwalaj na makra [[2]](#footnote-2)|
|Współautor|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Kopiowania; Wyświetl prawa; Zezwalaj na makra; Zapisz jako, Eksportuj [[4]](#footnote-4); Drukuj; Odpowiedź [[3]](#footnote-3); Odpowiedz wszystkim [[3]](#footnote-3); Do przodu [[3]](#footnote-3)|
|Współwłaściciel|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Kopiowania; Wyświetl prawa; Zmień prawa; Zezwalaj na makra; Zapisz jako, Eksportuj; Drukuj; Odpowiedź [[3]](#footnote-3); Odpowiedz wszystkim [[3]](#footnote-3); Do przodu [[3]](#footnote-3); Pełna kontrola|

----

###### <a name="footnote-1"></a>Przypis 1

Nie są uwzględnione w witrynie Azure portal.

###### <a name="footnote-2"></a>Przypis 2

W przypadku klienta usługi Azure Information Protection dla systemu Windows to prawo jest obecnie wymagane dla paska usługi Information Protection w aplikacjach pakietu Office.

###### <a name="footnote-3"></a>Przypis 3
Nie dotyczy klienta usługi Azure Information Protection dla systemu Windows ani aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management dla systemu Windows.

###### <a name="footnote-4"></a>Przypis 4
Nie jest dostępna w witrynie Azure portal lub klienta usługi Azure Information Protection dla Windows.

## <a name="rights-included-in-the-default-templates"></a>Prawa zawarte w domyślnych szablonach
W poniższej tabeli wymieniono prawa użytkowania, które są zawarte w domyślnych szablonach są tworzone. Prawa użytkowania są wyświetlane według ich [nazwa pospolita](#usage-rights-and-descriptions).

Te szablony domyślne są tworzone podczas zakupu subskrypcji i nazwy i praw użytkowania mogą być [zmienione](configure-policy-templates.md) w witrynie Azure portal. 

|Nazwa wyświetlana szablonu|Prawa użytkowania 6 października 2017 r. do bieżącej daty|Prawa użytkowania, zanim 6 października 2017 r.|
|----------------|--------------------|----------|
|\<*Nazwa organizacji > — poufne tylko do wyświetlania* <br /><br />lub<br /><br /> *Wysoce poufne\Wszyscy pracownicy*|Wyświetl, Otwórz, Odczytaj; Kopiowania; Wyświetl prawa; Zezwalaj na makra; Drukuj; Do przodu; Odpowiedź; Odpowiedz wszystkim; Zapisz; Edytuj zawartość, Edytuj|Wyświetl, Otwórz, Odczytaj|
|\<*Nazwa organizacji > — poufne* <br /><br />lub <br /><br />*Poufne\Wszyscy pracownicy*|Wyświetl, Otwórz, Odczytaj; Zapisz jako, Eksportuj; Kopiowania; Wyświetl prawa; Zmień prawa; Zezwalaj na makra; Drukuj; Do przodu; Odpowiedź; Odpowiedz wszystkim; Zapisz; Edytuj zawartość, Edytuj; Pełna kontrola|Wyświetl, Otwórz, Odczytaj; Zapisz jako, Eksportuj; Edytuj zawartość, Edytuj; Wyświetl prawa; Zezwalaj na makra; Do przodu; Odpowiedź; Odpowiedz wszystkim|

## <a name="do-not-forward-option-for-emails"></a>Opcja Nie przekazuj dotycząca wiadomości e-mail

Klienci programu Exchange i usługi (na przykład klient programu Outlook, aplikacji Outlook w sieci web, reguły przepływu poczty programu Exchange i akcje DLP dla programu Exchange) mają opcję ochrony praw dodatkowe informacje dla wiadomości e-mail: **Nie przesyłaj dalej**. 

Mimo że ta opcja jest dostępna dla użytkowników (i administratorów programu Exchange) w sposób sugerujący, że jest to domyślny szablon usługi Rights Management, który można wybrać, opcja **Nie przekazuj** nie jest szablonem. Tłumaczy to, dlaczego nie jest widoczna w witrynie Azure portal podczas wyświetlania i zarządzać szablonami ochrony. Zamiast tego **nie przesyłaj dalej** opcja to zestaw praw użytkowania, dynamicznie stosowany przez użytkowników do ich adresatów wiadomości e-mail.

Gdy **nie przesyłaj dalej** opcja jest stosowana do wiadomości e-mail, wiadomości e-mail są szyfrowane i adresaci muszą zostać uwierzytelnione. Adresaci nie może następnie przesyła je, wydrukować lub kopiować. Na przykład w kliencie programu Outlook przycisk Prześlij dalej nie jest dostępna, **Zapisz jako** i **drukowania** opcje menu nie są dostępne i nie możesz dodawać ani zmieniać adresatów w **do**, **DW**, lub **UDW** pola.

Niechronione [dokumentów pakietu Office](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) dołączonych do wiadomości e-mail automatycznie dziedziczy te same ograniczenia. Prawa użytkowania stosowana do tych dokumentów są **Edytuj zawartość, Edytuj**; **Zapisz**; **Wyświetl, Otwórz, Odczytaj**; i **Zezwalaj na makra**. Jeśli mają prawa do użytkowania różnych dla załącznika wiadomości lub załącznika nie jest dokumentu pakietu Office obsługującej tę ochronę dziedziczone, włączenia ochrony pliku, przed dołączeniem do wiadomości e-mail. Następnie można przypisać prawa użytkowania określonych, potrzebnych dla pliku. 

### <a name="difference-between-do-not-forward-and-not-granting-the-forward-usage-right"></a>Różnica między nie przesyłaj dalej, a nie przyznania prawa użytkowania do przodu

Jest to ważna różnica między stosowaniem **nie przesyłaj dalej** opcja i stosuje szablon, którego nie są przyznawane **do przodu** użycie bezpośrednio na adres e-mail: **Nie przesyłaj dalej** opcja używa dynamicznej listy autoryzowanych użytkowników, który jest oparty na wybranych przez użytkownika adresatach pierwotnej wiadomości e-mail; prawa w szablonie mają statyczną listę autoryzowanych użytkowników, które administrator ma wcześniej określona. Na czym polega różnica? Zostanie to wytłumaczone na przykładzie: 

Użytkownik chce wysłać pewne informacje w wiadomości e-mail do określonych osób w dziale marketingu, które nie powinny być udostępniane nikomu innemu. Czy w takiej sytuacji użytkownik powinien chronić wiadomość e-mail za pomocą szablonu ograniczającego prawa (do wyświetlania, odpowiedzi i zapisywania) tylko do działu marketingu?  Czy może powinna zostać użyta opcja **Nie przekazuj**? Obie te opcje spowodują, że adresaci nie będą mogli przekazywać wiadomości e-mail. 

- W przypadku zastosowania szablonu adresaci będą jednak mogli nadal udostępniać informacje innym użytkownikom w dziale marketingu. Na przykład adresat będzie mógł użyć Eksploratora Windows do przeciągnięcia i upuszczenia wiadomości e-mail do współdzielonej lokalizacji lub dysku USB. W takiej sytuacji każdy użytkownik z działu marketingu (oraz właściciel wiadomości e-mail), który ma dostęp do tej lokalizacji, będzie mógł wyświetlać informacje zawarte w wiadomości e-mail.
 
- Jeśli natomiast użytkownik zastosuje opcję **Nie przekazuj**, adresaci nie będą mogli udostępniać informacji nikomu innemu w dziale marketingu za pomocą przenoszenia wiadomości e-mail do innej lokalizacji. W takim scenariuszu tylko pierwotni adresaci (oraz właściciel wiadomości e-mail) będą mogli wyświetlać informacje zawarte w wiadomości e-mail.

> [!NOTE] 
> Użyj opcji **Nie przekazuj**, jeśli ważne jest, aby tylko wybrani przez nadawcę adresaci mogli wyświetlać informacje zawarte w wiadomości e-mail. Użyj szablonu na potrzeby wiadomości e-mail do ograniczenia praw do grupy osób określonych wcześniej przez administratora, niezależnie od adresatów wybranych przez nadawcę.

## <a name="encrypt-only-option-for-emails"></a>Tylko szyfrowanie dotycząca wiadomości e-mail

Exchange Online korzysta z nowych funkcji dla szyfrowanie wiadomości usługi Office 365, Nowa opcja wiadomości e-mail staje się dostępne: **Tylko szyfrowanie**.

Ta opcja jest dostępna dla dzierżaw korzystających z usługi Exchange Online i można wybrać w programie Outlook w sieci web, jako inną opcję ochrony praw dla reguły przepływu poczty, jako akcję DLP usługi Office 365 i programu Outlook w przypadku usługi Office 365 ProPlus z minimalną wersją [1804](/officeupdates/monthly-channel-2018#outlook-feature-updates-4). Aby uzyskać więcej informacji zobacz następujący wpis na blogu zespołu programu pakietu Office: [Szyfrowanie wprowadza się tylko w szyfrowanie wiadomości usługi Office 365](https://aka.ms/omefeb2018).

Gdy ta opcja jest zaznaczona, wiadomości e-mail są szyfrowane i adresaci muszą zostać uwierzytelnione. Następnie adresaci mają wszystkie prawa użytkowania, z wyjątkiem **Zapisz jako, Eksportuj** i **Pełna kontrola**. Ta kombinacja praw użytkowania oznacza, że adresaci nie ma żadnych ograniczeń, z tą różnicą, że ich nie można usunąć ochrony. Na przykład adresata można skopiować z wiadomości e-mail, drukować i przesyła je. 

Podobnie, domyślnie niechronionej [dokumentów pakietu Office](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) dołączonych do wiadomości e-mail dziedziczyć te same uprawnienia. Te dokumenty są chronione automatycznie, a po ich pobraniu, można je zapisać, edytować, skopiować i wydruku w aplikacjach pakietu Office przez adresatów. Gdy dokument zostanie zapisany przez odbiorcę, aby można było zapisać nową nazwę i inny format. Jednak tylko te formaty plików, które obsługują ochronę są dostępne, aby nie można zapisać dokumentu bez ochrony, oryginalnym. Jeśli mają prawa do użytkowania różnych dla załącznika wiadomości lub załącznika nie jest dokumentu pakietu Office obsługującej tę ochronę dziedziczone, włączenia ochrony pliku, przed dołączeniem do wiadomości e-mail. Następnie można przypisać prawa użytkowania określonych, potrzebnych dla pliku.

Alternatywnie, można zmienić to dziedziczenie ochrony dokumentów, określając `Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true` z [programu Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps). Jeśli nie potrzebujesz zachować oryginalne ochronę dokumentu po użytkownik jest uwierzytelniony, należy używać tej konfiguracji. Kiedy odbiorcy otwierają wiadomości e-mail, dokument nie jest chroniony.

Jeśli potrzebujesz dołączonego dokumentu, aby zachować oryginalną ochronę, zobacz [zabezpieczanie współpracy nad dokumentami przy użyciu usługi Azure Information Protection](secure-collaboration-documents.md).

Uwaga: Jeśli widzisz odwołania do **DecryptAttachmentFromPortal**, ten parametr jest teraz przestarzała w przypadku [Set-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/set-irmconfiguration?view=exchange-ps). Jeśli nie zostały wcześniej ustawione tego parametru, nie jest dostępna. 

## <a name="rights-management-issuer-and-rights-management-owner"></a>Wystawca usługi Rights Management i właściciel usługi Rights Management

Gdy dokument lub wiadomość e-mail są chronione za pomocą usługi Azure Rights Management, konto, które automatycznie chroni zawartość, staje się wystawcą usługi Rights Management dla tej zawartości. To konto jest rejestrowane jako pole **issuer** w [dziennikach użycia](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs). 

Wystawca usługi Rights Management ma zawsze przyznawane prawo użycia Pełna kontrola do dokumentu lub wiadomości e-mail, a ponadto:

- Jeśli ustawienia ochrony zawierają datę wygaśnięcia, wystawca usługi Rights Management nadal może otwierać i edytować dokument lub wiadomość e-mail po tej dacie.

- Wystawca usługi Rights Management zawsze ma dostęp do dokumentu lub wiadomości e-mail w trybie offline.

- Wystawca usługi Rights Management nadal może otworzyć dokument po jego odwołaniu. 

Domyślnie to konto jest także **właścicielem usługi Rights Management** dla tej zawartości, czyli jest to przypadek, gdy ochrona jest inicjowana przez użytkownika, który utworzył dokument lub wiadomość e-mail. Jednak istnieją pewne scenariusze, gdy administrator lub usługa może chronić zawartość w imieniu użytkowników. Przykład:

- Administrator zapewnia zbiorczą ochronę plików w udziale plików: Konto administratora w usłudze Azure AD chroni dokumenty dla użytkowników.

- Łącznik usługi Rights Management chroni dokumenty pakietu Office w folderze systemu Windows Server: Konto główne usługi w usłudze Azure AD, który jest tworzony dla łącznika usługi RMS chroni dokumenty dla użytkowników.

W tych scenariuszach wystawca usługi Rights Management może przypisać właściciela usługi Rights Management do innego konta, korzystając z zestawów SDK usługi Azure Information Protection lub programu PowerShell. Na przykład w przypadku używania polecenia cmdlet programu PowerShell [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) z klientem usługi Azure Information Protection możesz określić parametr **OwnerEmail**, aby przypisać właściciela usługi Rights Management do innego konta. 

Gdy wystawca usługi Rights Management realizuje ochronę w imieniu użytkowników, przypisanie właściciela usługi Rights Management zapewnia, że oryginalny właściciel dokumentu lub wiadomości e-mail ma ten sam poziom kontroli dla swojej chronionej zawartości, jakby on sam zainicjował ochronę. 

Na przykład użytkownik, który utworzył dokument, może go wydrukować, mimo że teraz jest chroniony za pomocą szablonu, który nie zawiera prawa użycia Drukuj. Ten sam użytkownik ma zawsze dostęp do swojego dokumentu niezależnie od ustawienia dostępu w trybie offline lub daty wygaśnięcia, które mogą być skonfigurowane w tym szablonie. Ponadto ponieważ właściciel usługi Rights Management ma prawo użycia Pełna kontrola, ten użytkownik może również ponownie włączyć ochronę dokumentu do udostępnienia dodatkowych użytkowników (w tym momencie użytkownik staje się wystawcą usługi Rights Management, a także właścicielem usługi Rights Management), i ten użytkownik może nawet usunąć ochronę. Jednak tylko wystawca usługi Rights Management może śledzić i odwoływać dokument.

Właściciel usługi Rights Management dla dokumentu lub wiadomości e-mail jest rejestrowany jako pole **owner-email** w [dziennikach użycia](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs).

Pamiętaj, że właściciel usługi Rights Management jest niezależny od właściciela systemu plików systemu Windows. Często to ta sama osoba, ale mogą to też być różne osoby, nawet jeśli nie używasz zestawów SDK ani programu PowerShell.

## <a name="rights-management-use-license"></a>Licencji użytkowania usługi Rights Management

Po otwarciu dokumentu lub wiadomości e-mail, który został objęty ochroną przez usługę Azure Rights Management, użytkownik zostanie ustanowione licencji użytkowania usługi Rights Management dla tej zawartości. Ta licencja użytkowania to certyfikat, który zawiera użytkownika praw użytkowania dla dokumentu lub wiadomości e-mail oraz klucz szyfrowania, który został użyty do zaszyfrowania zawartości. Licencji użytkowania zawiera także datę wygaśnięcia, jeżeli tego ustawienia, a ile licencji użytkowania jest nieprawidłowa.

Użytkownik musi mieć licencję użytkowania prawidłowy do otwierania zawartości, oprócz swojego certyfikatu konta praw (RAC), czyli certyfikatu, który przyznał, kiedy [zainicjowaniu środowiska użytkownika](how-does-it-work.md#initializing-the-user-environment) , a następnie odnowione 31 dni.

Na czas trwania licencji użytkowania użytkownik nie jest ponownie uwierzytelniany lub reauthorized zawartości. Dzięki temu użytkownik nadal otworzyć chroniony dokument lub wiadomość e-mail, bez połączenia z Internetem. Po wygaśnięciu okresu ważności licencji użytkowania, następnym razem użytkownik uzyskuje dostęp do chronionego dokumentu lub wiadomości e-mail, użytkownik musi być ponownie uwierzytelniany i reauthorized. 

Gdy dokumenty i wiadomości e-mail są chronione za pomocą etykiety lub szablonu, który definiuje ustawienia ochrony, możesz zmienić te ustawienia etykiety lub szablonu, bez konieczności ponownego włączenia ochrony zawartości. Jeżeli użytkownik ma już dostępu do zawartości, zmiany zaczęły obowiązywać, po wygaśnięciu licencji użytkowania, ich. Jednak gdy użytkownikom stosowanie uprawnień niestandardowych (znany także jako ad hoc zasad praw) i te uprawnienia, musisz zmienić po dokumentu lub wiadomości e-mail jest chroniona, tej zawartości muszą być chronione ponownie przy użyciu nowych uprawnień. Uprawnień niestandardowych dla wiadomości e-mail są implementowane przy użyciu opcji nie przesyłaj dalej.

Domyślnie używać okres ważności licencji, dla dzierżawy wynosi 30 dni i tę wartość można skonfigurować za pomocą polecenia cmdlet programu PowerShell [Set-AadrmMaxUseLicenseValidityTime](/powershell/module/aadrm/set-aadrmmaxuselicensevaliditytime). Bardziej restrykcyjne ustawienie można skonfigurować do stosowania ochrony przy użyciu etykiety lub szablonu:

- Po skonfigurowaniu etykiety lub szablonu w witrynie Azure portal, okres ważności licencji użytkowania przyjmuje wartość **zezwala na dostęp w trybie offline, ustawianie**. 
    
    Aby uzyskać więcej informacji i wskazówek, aby skonfigurować to ustawienie w witrynie Azure portal, zobacz [informacji na temat ustawień ochrony](configure-policy-protection.md#information-about-the-protection-settings) tabeli z instrukcjami konfigurowania etykiety dla ochrony usługi Rights Management.

- Po skonfigurowaniu szablonu przy użyciu programu PowerShell, okres ważności licencji użytkowania przyjmuje wartość *LicenseValidityDuration* parametru w [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) i [ Dodaj-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate) polecenia cmdlet.
    
    Aby uzyskać więcej informacji i wskazówek, aby skonfigurować to ustawienie przy użyciu programu PowerShell zobacz Pomoc dla każdego polecenia cmdlet.

## <a name="see-also"></a>Zobacz też
[Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md)

[Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](configure-super-users.md)
