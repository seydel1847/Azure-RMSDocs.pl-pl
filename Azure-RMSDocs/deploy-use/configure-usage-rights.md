---
title: "Konfigurowanie praw użytkowania dla usługi Azure Rights Management — AIP"
description: "Informacje pomagające zrozumieć i zidentyfikować określone prawa, które są używane w przypadku ochrony plików lub wiadomości e-mail przy użyciu usługi Azure Rights Management w ramach usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/27/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: faa00eee76e6c084db1a4dfb1d477e491fae5fee
ms.sourcegitcommit: 3e9b3c2206807e82cc4721a50862b74152906f63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="configuring-usage-rights-for-azure-rights-management"></a>Konfigurowanie praw użytkowania dla usługi Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

Jeśli ustawiasz ochronę plików lub wiadomości e-mail za pomocą usługi Azure Rights Management w ramach usługi Azure Information Protection bez użycia szablonu, musisz własnoręcznie skonfigurować prawa użytkowania. Ponadto podczas konfigurowania szablonów lub etykiety dla ochrony usługi Azure Rights Management, wybierz prawa użytkowania, które zostaną automatycznie zastosowane w przypadku wybrania szablonu lub etykieta przez użytkowników, administratorów lub skonfigurowane usługi. Na przykład w portalu Azure można wybrać role, które powodują ustawienie logicznego grupowania praw użytkowania, lub można skonfigurować poszczególne prawa.

Niniejszy artykuł pomoże Ci skonfigurować prawa użytkowania dla używanej aplikacji oraz zrozumieć, jak te prawa będą interpretowane przez aplikacje.

> [!NOTE] 
> Aby informacje były kompletne ten artykuł zawiera wartości z klasycznego portalu Azure, która została wycofana 08 stycznia 2018.
>
> Aby przeprowadzić migrację do nowego portalu, zobacz [zadań, które są używane z klasycznego portalu Azure](migrate-portal.md).

## <a name="usage-rights-and-descriptions"></a>Prawa użytkowania wraz z opisami
Poniższa tabela zawiera listę i opisy praw użytkowania obsługiwanych przez usługę Rights Management oraz sposób ich wykorzystania i interpretowania. Są one wyświetlane według ich **nazwa pospolita**, która jest zazwyczaj jak napotkać wyświetlenie prawa użytkowania lub odwołuje się do, przyjaźniejsza wersja jednowyrazowej wartości używanej w kodzie ( **kodowanie w zasadach** wartości). 

**Stała lub wartość API** jest nazwą zestawu SDK wywołania MSIPC API używanego podczas pisania aplikacji obsługujących usługę RMS. Wywołanie sprawdza prawa użytkowania lub dodaje prawo użytkowania do zasad.


|Prawo użytkowania|Opis|Implementacja|
|-------------------------------|---------------------------|-----------------|
|Nazwa pospolita: **Edytuj zawartość, Edytuj** <br /><br />Kodowanie w zasadach: **DOCEDIT**|Zezwala użytkownikowi na modyfikowanie, rozmieszczanie, formatowanie lub filtrowanie zawartości wewnątrz aplikacji. Nie nadaje prawa do zapisywania edytowanej kopii.|W prawach niestandardowych pakietu Office: jako część opcji **Zmiana** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Edytuj zawartość**<br /><br />Nazwa w portalu Azure: **Edytuj zawartość, Edytuj (DOCEDIT)**<br /><br />Nazwa w szablonach usługi AD RMS: **Edytuj** <br /><br />Stała lub wartość interfejsu API: nie dotyczy.|
|Nazwa pospolita: **Zapisz** <br /><br />Kodowanie w zasadach: **EDIT**|Umożliwia użytkownikowi zapisanie dokumentu w jego bieżącej lokalizacji.<br /><br />W aplikacjach pakietu Office to prawo umożliwia użytkownikowi modyfikowanie dokumentu.|W prawach niestandardowych pakietu Office: jako część opcji **Zmiana** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Zapisz plik**<br /><br />Nazwa w portalu Azure: **Zapisz (Edytuj)**<br /><br />Nazwa w szablonach usługi AD RMS: **Zapisz** <br /><br />Stała API lub wartość API: `IPC_GENERIC_WRITE L"EDIT"`|
|Nazwa pospolita: **Komentarz** <br /><br />Kodowanie w zasadach: **COMMENT**|Pozwala dodawać adnotacje i komentarze do zawartości.<br /><br />To uprawnienie jest dostępne w zestawie SDK oraz jest dostępne w formie zasad ad hoc w usłudze Azure Information Protection i w module RMS Protection w środowisku Windows PowerShell. Zostało też zaimplementowane w niektórych aplikacjach dostawców oprogramowania. Nie jest jednak powszechnie używane i obecnie nie jest obsługiwane przez aplikacje pakietu Office.|W prawach niestandardowych pakietu Office: nie zaimplementowane. <br /><br />Nazwa w klasycznym portalu Azure: nie zaimplementowane.<br /><br />Nazwa w witrynie Azure Portal: nie zaimplementowane.<br /><br />Nazwa w szablonach usługi AD RMS: nie zaimplementowane. <br /><br />Stała API lub wartość API: `IPC_GENERIC_COMMENT L"COMMENT`|
|Nazwa pospolita: **Zapisz jako, Eksportuj** <br /><br />Kodowanie w zasadach: **EXPORT**|Włącza opcję zapisu zawartości w pliku o innej nazwie (Zapisz jako). <br /><br />Dokumenty pakietu Office i klienta usługi Azure Information Protection plik można być zapisany bez ochrony i również przełączona do trybu nowe ustawienia i uprawnienia. Te dozwolone akcje oznacza, że użytkownik, który ma te uprawnienia można zmienić lub usunąć etykiety usługi Azure Information Protection chronionego dokumentu lub wiadomości e-mail. <br /><br />To uprawnienie umożliwia też użytkownikowi korzystanie z innych opcji eksportu w aplikacjach, np. opcji **Wyślij do programu OneNote**.<br /><br /> Uwaga: jeśli nie udzielono tego uprawnienia, aplikacje pakietu Office umożliwiają użytkownikowi zapis dokumentu pod nową nazwą, jeśli wybrany format pliku natywnie obsługuje ochronę za pomocą usługi Microsoft Rights Management.|W prawach niestandardowych pakietu Office: jako część opcji **Zmiana** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Eksportuj zawartość (Zapisz jako)** <br /><br />Nazwa w portalu Azure: **Zapisz jako, Eksportuj (EKSPORTUJ)**<br /><br />Nazwa w szablonach usługi AD RMS: **Eksportuj (Zapisz jako)** <br /><br />Stała API lub wartość API: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Nazwa pospolita: **Prześlij dalej** <br /><br />Kodowanie w zasadach: **FORWARD**|Włącza opcję przesyłania dalej wiadomości e-mail oraz dodawania adresatów w wierszach **Do** i **DW**. To prawo dotyczy tylko wiadomości e-mail, a nie dokumentów.<br /><br />Nie zezwala osobie przekazującej wiadomość dalej na przyznanie praw innym użytkownikom jako części akcji przekazywania. <br /><br />Gdy przyznasz to uprawnienie, przyznaj również uprawnienie **Edytuj zawartość, Edytuj** (nazwa pospolita), aby upewnić się, że oryginalna wiadomość e-mail stanowi część przesłanej dalej wiadomości e-mail, a nie załącznik. To uprawnienie jest również wymagane, gdy wysyłasz wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacji sieci Web programu Outlook. Lub użytkowników w organizacji, które są wykluczone z usługi Azure Rights Management usługi, ponieważ zostały zaimplementowane [kontrolki dołączania](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|W prawach niestandardowych pakietu Office: odmowa przy użyciu standardowych zasad **Nie przekazuj**.<br /><br />Nazwa w klasycznym portalu Azure: **Prześlij dalej**<br /><br />Nazwa w portalu Azure: **do przodu (Prześlij)**<br /><br />Nazwa w szablonach usługi AD RMS: **Prześlij dalej** <br /><br />Stała API lub wartość API: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Nazwa pospolita: **Pełna kontrola** <br /><br />Kodowanie w zasadach: **OWNER**|Przyznaje wszystkie prawa do dokumentu. Można wykonywać wszystkie dostępne akcje.<br /><br />Obejmuje możliwość usunięcia ochrony i włącz ponownie ochronę dokumentu. <br /><br />Pamiętaj, że to prawo użycia nie jest takie samo jak [właściciela usługi Rights Management](#rights-management-issuer-and-rights-management-owner).|W prawach niestandardowych pakietu Office: jako opcja niestandardowa **Pełna kontrola**.<br /><br />Nazwa w klasycznym portalu Azure: **Pełna kontrola**<br /><br />Nazwa w portalu Azure: **pełnej kontroli (właściciela)**<br /><br />Nazwa w szablonach usługi AD RMS: **Pełna kontrola** <br /><br />Stała API lub wartość API: `IPC_GENERIC_ALL L"OWNER"`|
|Nazwa pospolita: **Drukuj** <br /><br />Kodowanie w zasadach: **PRINT**|Włącza opcje związane z drukowaniem zawartości.|W prawach niestandardowych pakietu Office: jako opcja **Drukuj zawartość** w uprawnieniach niestandardowych. Nie jest to ustawienie określane dla poszczególnych odbiorców.<br /><br />Nazwa w klasycznym portalu Azure: **Drukuj**<br /><br />Nazwa w portalu Azure: **drukowania (drukowania)**<br /><br />Nazwa w szablonach usługi AD RMS: **Drukuj** <br /><br />Stała API lub wartość API: `IPC_GENERIC_PRINT L"PRINT"`|
|Nazwa pospolita: **Odpowiedz** <br /><br />Kodowanie w zasadach: **REPLY**|Włącza opcję **Odpowiedz** w kliencie poczty e-mail bez możliwości zmiany w wierszach **Do** lub **DW**.<br /><br />Gdy przyznasz to uprawnienie, przyznaj również uprawnienie **Edytuj zawartość, Edytuj** (nazwa pospolita), aby upewnić się, że oryginalna wiadomość e-mail stanowi część przesłanej dalej wiadomości e-mail, a nie załącznik. To uprawnienie jest również wymagane, gdy wysyłasz wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacji sieci Web programu Outlook. Lub użytkowników w organizacji, które są wykluczone z usługi Azure Rights Management usługi, ponieważ zostały zaimplementowane [kontrolki dołączania](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|W prawach niestandardowych pakietu Office: nie dotyczy.<br /><br />Nazwa w klasycznym portalu Azure: **Odpowiedz**<br /><br />Nazwa w klasycznym portalu Azure: **odpowiedzi (odpowiedź)**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz** <br /><br />Stała API lub wartość API: `IPC_EMAIL_REPLY`|
|Nazwa pospolita: **Odpowiedz wszystkim** <br /><br />Kodowanie w zasadach: **REPLYALL**|Włącza opcję **Odpowiedz wszystkim** w kliencie poczty e-mail, ale nie zezwala użytkownikowi na dodawanie odbiorców w wierszach **Do** lub **DW**.<br /><br />Gdy przyznasz to uprawnienie, przyznaj również uprawnienie **Edytuj zawartość, Edytuj** (nazwa pospolita), aby upewnić się, że oryginalna wiadomość e-mail stanowi część przesłanej dalej wiadomości e-mail, a nie załącznik. To uprawnienie jest również wymagane, gdy wysyłasz wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacji sieci Web programu Outlook. Lub użytkowników w organizacji, które są wykluczone z usługi Azure Rights Management usługi, ponieważ zostały zaimplementowane [kontrolki dołączania](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|W prawach niestandardowych pakietu Office: nie dotyczy.<br /><br />Nazwa w klasycznym portalu Azure: **Odpowiedz wszystkim**<br /><br />Nazwa w portalu Azure: **Odpowiedz wszystkim (ODPOWIEDZ wszystkim)**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz wszystkim** <br /><br />Stała API lub wartość API: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Nazwa pospolita: **Wyświetl, Otwórz, Odczytaj** <br /><br />Kodowanie w zasadach: **VIEW**|Umożliwia użytkownikom otworzenie dokumentu i wyświetlenie zawartości.|W prawach niestandardowych pakietu Office: jako zasady niestandardowe **Odczytaj**, opcja **Wyświetl**.<br /><br />Nazwa w klasycznym portalu Azure: **Wyświetl**<br /><br />Nazwa w portalu Azure: **Wyświetl, Otwórz, Odczytaj (Widok)**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz wszystkim** <br /><br />Stała API lub wartość API: `IPC_GENERIC_READ L"VIEW"`|
|Nazwa pospolita: **Kopiuj** <br /><br />Kodowanie w zasadach: **EXTRACT**|Włącza opcje kopiowania danych (w tym przechwytywania ekranu) z dokumentu do tego samego lub innego dokumentu.<br /><br />W niektórych aplikacjach pozwala są także do całego dokumentu można zapisać w postaci niechronionej.|W prawach niestandardowych pakietu Office: jako opcja zasady niestandardowej **Zezwalaj użytkownikom z dostępem do odczytu na kopiowanie zawartości**.<br /><br />Nazwa w klasycznym portalu Azure: **Kopiuj i Wyodrębnij zawartość**<br /><br />Nazwa w portalu Azure: **kopiowania (EXTRACT)**<br /><br />Nazwa w szablonach usługi AD RMS: **Wyodrębnij** <br /><br />Stała API lub wartość API: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Nazwa pospolita: **Wyświetl prawa** <br /><br />Kodowanie w zasadach: **VIEWRIGHTSDATA**|Umożliwia użytkownikowi wyświetlenie zasad zastosowanych do dokumentu.|W prawach niestandardowych pakietu Office: nie zaimplementowane.<br /><br />Nazwa w klasycznym portalu Azure: **Wyświetl przypisane prawa**<br /><br />Nazwa w portalu Azure: **widoku praw (VIEWRIGHTSDATA)**.<br /><br />Nazwa w szablonach usługi AD RMS: **Wyświetl prawa** <br /><br />Stała API lub wartość API: `IPC_READ_RIGHTS L"VIEWRIGHTSDATA"`|
|Nazwa pospolita: **Zmień prawa** <br /><br />Kodowanie w zasadach: **EDITRIGHTSDATA**|Umożliwia użytkownikowi zmianę zasad mających zastosowanie do dokumentu. Obejmuje możliwość usunięcia ochrony.|W prawach niestandardowych pakietu Office: nie zaimplementowane.<br /><br />Nazwa w klasycznym portalu Azure: **Zmień prawa**<br /><br />Nazwa w portalu Azure: **Edycja praw (EDITRIGHTSDATA)**.<br /><br />Nazwa w szablonach usługi AD RMS: **Zmień prawa** <br /><br />Stała API lub wartość API: `PC_WRITE_RIGHTS L"EDITRIGHTSDATA"`|
|Nazwa pospolita: **Włącz makra** <br /><br />Kodowanie w zasadach: **OBJMODEL**|Włącza opcję uruchamiania makr lub innych rozwiązań programistycznych albo zezwala na zdalny dostęp do zawartości w dokumencie.|W prawach niestandardowych pakietu Office: jako opcja zasad niestandardowych **Zezwalaj na dostęp programistyczny**. Nie jest to ustawienie określane dla poszczególnych odbiorców.<br /><br />Nazwa w klasycznym portalu Azure: **Zezwalaj na makra**<br /><br />Nazwa w portalu Azure: **Zezwalaj na makra (OBJMODEL)**<br /><br />Nazwa w szablonach usługi AD RMS: **Zezwalaj na makra** <br /><br />Stała lub wartość interfejsu API: nie zaimplementowane.|

## <a name="rights-included-in-permissions-levels"></a>Prawa zawarte w poziomach uprawnień

Niektóre aplikacje grupują prawa użytkowania w poziomach uprawnień. Dzięki temu można łatwiej wybrać prawa użytkowania, które zazwyczaj stosuje się wspólnie. Te poziomy uprawnień upraszczają skomplikowane działania po stronie użytkowników, którzy mogą wybrać opcje oparte na rolach.  Na przykład **Recenzent** i **Współautor**. Chociaż opcje te często są dostępne z podsumowaniem praw, to mogą one nie obejmować wszystkich praw wymienionych w poprzedniej tabeli.

Lista poziomów uprawnień i Pełna lista praw użytkowania, które zawierają, skorzystaj z poniższej tabeli. Prawa użytkowania są wyświetlane według ich [nazwa pospolita](#usage-rights-and-descriptions).

|Poziom uprawnień|Aplikacje|Zawarte prawa użytkowania|
|---------------------|----------------|---------------------------------|
|Przeglądanie|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br /> Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Wyświetl prawa; Odpowiedź [[1]](#footnote-1); Odpowiedz wszystkim [[1]](#footnote-1); Zezwalaj na makra [[2]](#footnote-2)<br /><br />Uwaga: Dla wiadomości e-mail użyj opcji Recenzent zamiast tego poziomu uprawnień, aby upewnić się, że odpowiedź na wiadomość e-mail została odebrana jako wiadomość e-mail, a nie jako załącznik. Opcja Recenzent jest również wymagana podczas wysyłania wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacji sieci Web programu Outlook. Lub użytkowników w organizacji, które są wykluczone z usługi Azure Rights Management usługi, ponieważ zostały zaimplementowane [kontrolki dołączania](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|
|Recenzent|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Wyświetl prawa; Odpowiedź: Odpowiedz wszystkim [[3]](#footnote-3); Przekazuj [[3]](#footnote-3); Zezwalaj na makra [[2]](#footnote-2)|
|Współautor|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Skopiuj; Wyświetl prawa; Zezwalaj na makra; Zapisz jako, Eksportuj [[4]](#footnote-4); Drukowanie; Odpowiedź [[3]](#footnote-3); Odpowiedz wszystkim [[3]](#footnote-3); Przekazuj [[3]](#footnote-3)|
|Współwłaściciel|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Skopiuj; Wyświetl prawa; Zmień prawa; Zezwalaj na makra; Zapisz jako, Eksportuj; Drukowanie; Odpowiedź [[3]](#footnote-3); Odpowiedz wszystkim [[3]](#footnote-3); Przekazuj [[3]](#footnote-3); Pełna kontrola|

----

###### <a name="footnote-1"></a>Przypis 1

Nie jest uwzględniony w portalu Azure.

###### <a name="footnote-2"></a>Przypis 2

W przypadku klienta usługi Azure Information Protection dla systemu Windows to prawo jest obecnie wymagane dla paska usługi Information Protection w aplikacjach pakietu Office.

###### <a name="footnote-3"></a>Przypis 3
Nie dotyczy klienta usługi Azure Information Protection dla systemu Windows ani aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management dla systemu Windows.

###### <a name="footnote-4"></a>Przypis 4
Nie jest dostępna w portalu Azure lub klient usługi Azure Information Protection dla systemu Windows.

## <a name="rights-included-in-the-default-templates"></a>Prawa zawarte w domyślnych szablonach
W poniższej tabeli wymieniono prawa użytkowania, które są uwzględniane podczas tworzenia szablonów domyślnych. Prawa użytkowania są wyświetlane według ich [nazwa pospolita](#usage-rights-and-descriptions).

Te szablony domyślne są tworzone, gdy zostało zakupione w ramach Twojej subskrypcji i nazwy i praw użytkowania mogą być [zmienić](configure-policy-templates.md) w portalu Azure. 

|Nazwa wyświetlana szablonu|Prawa użytkowania 6 października 2017 do bieżącej daty|Prawa użytkowania przed 6 października 2017 r.|
|----------------|--------------------|----------|
|\<*Nazwa organizacji > — tylko wgląd poufny* <br /><br />lub<br /><br /> *Wysoce poufne\Wszyscy pracownicy*|Wyświetl, Otwórz, Odczytaj; Skopiuj; Wyświetl prawa; Zezwalaj na makra; Drukowanie; Prześlij dalej; Odpowiedź; Odpowiedz wszystkim; Zapisz; Edytuj zawartość, Edytuj|Wyświetl, Otwórz, Odczytaj|
|\<*Nazwa organizacji > — poufne* <br /><br />lub <br /><br />*Poufne\Wszyscy pracownicy*|Wyświetl, Otwórz, Odczytaj; Zapisz jako, Eksportuj; Skopiuj; Wyświetl prawa; Zmień prawa; Zezwalaj na makra; Drukowanie; Prześlij dalej; Odpowiedź; Odpowiedz wszystkim; Zapisz; Edytuj zawartość, Edytuj; Pełna kontrola|Wyświetl, Otwórz, Odczytaj; Zapisz jako, Eksportuj; Edytuj zawartość, Edytuj; Wyświetl prawa; Zezwalaj na makra; Prześlij dalej; Odpowiedź; Odpowiedz wszystkim|

## <a name="do-not-forward-option-for-emails"></a>Opcja Nie przekazuj dotycząca wiadomości e-mail

Klienci programu Exchange i usługi (na przykład klient programu Outlook, aplikacja Outlook Web Access i reguły transportu programu Exchange) mają opcję ochrony praw dodatkowe informacje na potrzeby wiadomości e-mail: **nie przesyłaj dalej**. 

Mimo że ta opcja jest dostępna dla użytkowników (i administratorów programu Exchange) w sposób sugerujący, że jest to domyślny szablon usługi Rights Management, który można wybrać, opcja **Nie przekazuj** nie jest szablonem. Tłumaczy to, dlaczego nie widać go w portalu Azure podczas przeglądania i zarządzania szablonami usługi Azure Rights Management. Zamiast tego opcje **Nie przekazuj** stanowią zestaw uprawnień dynamicznie stosowany przez użytkowników względem ich adresatów wiadomości e-mail.

Gdy **nie przesyłaj dalej** jest stosowana do wiadomości e-mail, wiadomości e-mail są szyfrowane i musi zostać uwierzytelniony adresatów. Następnie adresatów nie może przekazać lub wydrukować go, skopiować z niej, lub zapisywanie załączników lub zapisać pod inną nazwą. Na przykład w kliencie programu Outlook przycisk Prześlij dalej nie jest dostępne, **Zapisz jako**, **Zapisz załącznik**, i **drukowania** menu Opcje nie są dostępne i nie można dodać lub zmieniać adresatów w **do**, **DW**, lub **UDW** pola.

Jest to ważna różnica między stosowaniem opcji **Nie przekazuj** i stosowaniem szablonu, za pomocą którego nie są przyznawane uprawnienia do przekazywania wiadomości e-mail: opcja **Nie przekazuj** używa dynamicznej listy autoryzowanych użytkowników opartej na wybranych przez użytkownika adresatach pierwotnej wiadomości e-mail. Prawa w szablonie zawierają natomiast statyczną listę autoryzowanych użytkowników określonych wcześniej przez administratora. Na czym polega różnica? Zostanie to wytłumaczone na przykładzie: 

Użytkownik chce wysłać pewne informacje w wiadomości e-mail do określonych osób w dziale marketingu, które nie powinny być udostępniane nikomu innemu. Czy w takiej sytuacji użytkownik powinien chronić wiadomość e-mail za pomocą szablonu ograniczającego prawa (do wyświetlania, odpowiedzi i zapisywania) tylko do działu marketingu?  Czy może powinna zostać użyta opcja **Nie przekazuj**? Obie te opcje spowodują, że adresaci nie będą mogli przekazywać wiadomości e-mail. 

- W przypadku zastosowania szablonu adresaci będą jednak mogli nadal udostępniać informacje innym użytkownikom w dziale marketingu. Na przykład adresat będzie mógł użyć Eksploratora Windows do przeciągnięcia i upuszczenia wiadomości e-mail do współdzielonej lokalizacji lub dysku USB. W takiej sytuacji każdy użytkownik z działu marketingu (oraz właściciel wiadomości e-mail), który ma dostęp do tej lokalizacji, będzie mógł wyświetlać informacje zawarte w wiadomości e-mail.
 
- Jeśli natomiast użytkownik zastosuje opcję **Nie przekazuj**, adresaci nie będą mogli udostępniać informacji nikomu innemu w dziale marketingu za pomocą przenoszenia wiadomości e-mail do innej lokalizacji. W takim scenariuszu tylko pierwotni adresaci (oraz właściciel wiadomości e-mail) będą mogli wyświetlać informacje zawarte w wiadomości e-mail.

> [!NOTE] 
> Użyj opcji **Nie przekazuj**, jeśli ważne jest, aby tylko wybrani przez nadawcę adresaci mogli wyświetlać informacje zawarte w wiadomości e-mail. Użyj szablonu na potrzeby wiadomości e-mail do ograniczenia praw do grupy osób określonych wcześniej przez administratora, niezależnie od adresatów wybranych przez nadawcę.

## <a name="encrypt-only-option-for-emails"></a>Opcja tylko do szyfrowania wiadomości e-mail

Exchange Online korzysta z nowych funkcji dla szyfrowanie wiadomości usługi Office 365, Nowa opcja wiadomości e-mail staje się dostępna: **tylko Szyfruj**.

Ta opcja jest wdrażany dzierżawców korzystających z usługi Exchange Online początkowo tylko dla programu Outlook w sieci web i jako inną opcję ochrony praw do reguły transportu. Aby uzyskać więcej informacji, zobacz następujące powiadomienie post blog zespołu pakietu Office: [szyfrowania zetknie się tylko w szyfrowanie wiadomości usługi Office 365](https://aka.ms/omefeb2018).

Gdy ta opcja jest zaznaczona, wiadomości e-mail są szyfrowane i musi zostać uwierzytelniony adresatów. Następnie odbiorcy mają wszystkie prawa użytkowania, z wyjątkiem Pełna kontrola. Ta kombinacja prawa użytkowania oznacza, że adresaci nie obowiązują żadne ograniczenia, z wyjątkiem tego, że nie będą oni mogli usunąć ochronę. Na przykład adresat można skopiować, drukować i przekazywać wiadomości e-mail. Podobnie wszystkie dokumenty pakietu Office, które są dołączone i automatycznie chronione może zostać zapisany, skopiowane i drukowana.

## <a name="rights-management-issuer-and-rights-management-owner"></a>Wystawca usługi Rights Management i właściciel usługi Rights Management

Gdy dokument lub wiadomość e-mail są chronione za pomocą usługi Azure Rights Management, konto, które automatycznie chroni zawartość, staje się wystawcą usługi Rights Management dla tej zawartości. To konto jest rejestrowane jako pole **issuer** w [dziennikach użycia](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs). 

Wystawca usługi Rights Management ma zawsze przyznawane prawo użycia Pełna kontrola do dokumentu lub wiadomości e-mail, a ponadto:

- Jeśli ustawienia ochrony zawierają datę wygaśnięcia, wystawca usługi Rights Management nadal może otwierać i edytować dokument lub wiadomość e-mail po tej dacie.

- Wystawca usługi Rights Management zawsze ma dostęp do dokumentu lub wiadomości e-mail w trybie offline.

- Wystawca usługi Rights Management nadal może otworzyć dokument po jego odwołaniu. 

Domyślnie to konto jest także **właścicielem usługi Rights Management** dla tej zawartości, czyli jest to przypadek, gdy ochrona jest inicjowana przez użytkownika, który utworzył dokument lub wiadomość e-mail. Jednak istnieją pewne scenariusze, gdy administrator lub usługa może chronić zawartość w imieniu użytkowników. Przykład:

- Administrator zapewnia zbiorczą ochronę plików w udziale plików: konto administratora w usłudze Azure AD chroni dokumenty dla użytkowników.

- Łącznik usługi Rights Management chroni dokumenty pakietu Office w folderze systemu Windows Server: główne konto usługi w usłudze Azure AD, które jest utworzone dla łącznika usługi RMS, chroni dokumenty dla użytkowników.

W tych scenariuszach wystawca usługi Rights Management może przypisać właściciela usługi Rights Management do innego konta, korzystając z zestawów SDK usługi Azure Information Protection lub programu PowerShell. Na przykład w przypadku używania polecenia cmdlet programu PowerShell [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) z klientem usługi Azure Information Protection możesz określić parametr **OwnerEmail**, aby przypisać właściciela usługi Rights Management do innego konta. 

Gdy wystawca usługi Rights Management realizuje ochronę w imieniu użytkowników, przypisanie właściciela usługi Rights Management zapewnia, że oryginalny właściciel dokumentu lub wiadomości e-mail ma ten sam poziom kontroli dla swojej chronionej zawartości, jakby on sam zainicjował ochronę. 

Na przykład użytkownik, który utworzył dokument, może go wydrukować, mimo że teraz jest chroniony za pomocą szablonu, który nie zawiera prawa użycia Drukuj. Ten sam użytkownik ma zawsze dostęp do swojego dokumentu niezależnie od ustawienia dostępu w trybie offline lub daty wygaśnięcia, które mogą być skonfigurowane w tym szablonie. Ponadto właściciela zarządzania prawami ma prawo użytkowania Pełna kontrola, ten użytkownik może również Włącz ponownie ochronę dokumentu do udostępnienia dodatkowych użytkowników (w takim przypadku użytkownik staje się wystawcy Rights Management, a także właściciela usługi Rights Management), a nawet usunąć ochrony tego użytkownika. Jednak tylko wystawca usługi Rights Management może śledzić i odwoływać dokument.

Właściciel usługi Rights Management dla dokumentu lub wiadomości e-mail jest rejestrowany jako pole **owner-email** w [dziennikach użycia](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs).

Pamiętaj, że właściciel usługi Rights Management jest niezależny od właściciela systemu plików systemu Windows. Często to ta sama osoba, ale mogą to też być różne osoby, nawet jeśli nie używasz zestawów SDK ani programu PowerShell.

## <a name="rights-management-use-license"></a>Licencji użytkowania Rights Management

Po otwarciu dokumentu lub wiadomości e-mail, który jest chroniony przez usługę Azure Rights Management, licencji użytkowania usługi Rights Management dla tej zawartości jest przyznane użytkownikowi. Ta licencja Użyj jest certyfikatu, który zawiera prawa użytkowania użytkownika do dokumentu lub wiadomości e-mail oraz klucz szyfrowania, który został użyty do zaszyfrowania zawartości. Licencji użytkowania zawiera także datę wygaśnięcia, jeśli tego ustawienia i jak długo licencji użytkowania jest nieprawidłowa.

W czasie trwania licencji użytkowania użytkownik nie jest ponownie uwierzytelnić lub reauthorized. Dzięki temu użytkownik nadal otworzyć chroniony dokument lub wiadomość e-mail bez połączenia z Internetem. Po wygaśnięciu okresu ważności licencji użycia, następnym razem, użytkownik uzyskuje dostęp do chronionego dokumentu lub wiadomości e-mail, użytkownik musi ponownie uwierzytelnić i reauthorized. 

Gdy dokumenty i wiadomości e-mail są chronione za pomocą etykiety lub szablon, który definiuje ustawienia ochrony, można zmienić te ustawienia w etykiecie lub w szablonie bez konieczności włącz ponownie ochronę zawartości. Jeżeli użytkownik ma już dostępu do zawartości, zmiany zaczynają obowiązywać po wygaśnięciu ich licencji użytkowania. Jednak użytkownicy zastosować uprawnienia niestandardowe (znanej także jako zasad ad hoc praw) i te uprawnienia konieczna zmiana po dokumentu lub wiadomości e-mail są chronione, tej zawartości musi być chronione ponownie przy użyciu nowe uprawnienia. Uprawnienia niestandardowe dla wiadomości e-mail są implementowane przy użyciu opcji nie przesyłaj dalej.

Domyślnie używać okresu ważności licencji, dzierżawa to 30 dni i tę wartość można skonfigurować za pomocą polecenia cmdlet programu PowerShell [AadrmMaxUseLicenseValidityTime zestawu](/powershell/module/aadrm/set-aadrmmaxuselicensevaliditytime). Bardziej restrykcyjne ustawienie można skonfigurować do stosowania ochrony za pomocą etykiety lub szablonu:

- Po skonfigurowaniu etykiety lub szablonu w portalu Azure, użyj okresu ważności licencji przyjmuje wartość **zezwala na dostęp offline Ustawianie**. 
    
    Więcej informacji oraz wskazówki dotyczące tego ustawienia w portalu Azure można znaleźć tabeli w kroku 9 z [jak konfigurowanie etykiety pod kątem ochrony usługi Rights Management](configure-policy-protection.md).

- Po skonfigurowaniu szablonu przy użyciu programu PowerShell, użyj okresu ważności licencji przyjmuje wartość z *LicenseValidityDuration* parametru w [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) i [ Dodaj-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate) polecenia cmdlet.
    
    Aby uzyskać więcej informacji i wskazówek, aby skonfigurować to ustawienie za pomocą programu PowerShell zobacz Pomoc dla poszczególnych poleceń cmdlet.


## <a name="see-also"></a>Zobacz też
[Konfigurowanie i zarządzanie nimi szablonów usługi Azure Information Protection](configure-policy-templates.md)

[Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](configure-super-users.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

