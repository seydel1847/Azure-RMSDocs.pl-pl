---
title: "Konfigurowanie praw użytkowania dla usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4d6e0af200410b5af4e290ee0e6f94725916ecde
ms.openlocfilehash: e9f2fe16494af2286d8ed77d0894bb5229e7c246


---

# Konfigurowanie praw użytkowania dla usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Jeśli ustawiasz ochronę plików lub wiadomości e-mail za pomocą usługi Azure Rights Management (Azure RMS) bez użycia szablonu, musisz własnoręcznie skonfigurować prawa użytkowania. Ponadto konfigurując szablony niestandardowe dla usługi Azure RMS, wybierasz prawa użytkowania, które zostaną automatycznie zastosowane po wybraniu szablonu przez użytkowników, administratorów lub skonfigurowane usługi. Na przykład w klasycznym portalu platformy Azure możesz wybrać role, które powodują ustawienie logicznego grupowania praw użytkowania, albo skonfigurować poszczególne prawa.

Niniejszy artykuł pomoże Ci skonfigurować prawa użytkowania dla używanej aplikacji oraz zrozumieć, jak te prawa będą interpretowane przez aplikacje.

## Prawa użytkowania wraz z opisami
Poniższe sekcje zawierają listę i opisy praw użytkowania obsługiwanych przez usługę Rights Management oraz sposób ich wykorzystania i interpretowania. Są one wyświetlane według **nazwy pospolitej**, która jest często spotykanym sposobem na wyświetlenie prawa użytkowania lub odniesienie się do niego. Jest to przyjaźniejsza wersja jednowyrazowej wartości używanej w kodzie (wartość **Kodowanie w zasadach**). **Stała lub wartość API** jest nazwą zestawu SDK wywołania MSIPC API używanego podczas pisania aplikacji obsługujących usługę RMS. Wywołanie sprawdza prawa użytkowania lub dodaje prawo użytkowania do zasad.


### Edytuj zawartość, Edytuj

Zezwala użytkownikowi na modyfikowanie, rozmieszczanie, formatowanie lub filtrowanie zawartości wewnątrz aplikacji. Nie nadaje prawa do zapisywania edytowanej kopii.

**Kodowanie w zasadach**: DOCEDIT

**Implementacja w prawach niestandardowych pakietu Office**: jako część opcji *Zmiana* i *Pełna kontrola*.

**Nazwa w klasycznym portalu Azure**: *Edytuj zawartość*

**Nazwa w szablonach usługi AD RMS**: *Edytuj*

**Stała lub wartość API**: *nie dotyczy*

---

### Zapisywanie

Umożliwia użytkownikowi zapisanie dokumentu w jego bieżącej lokalizacji.

**Kodowanie w zasadach**: EDIT

**Implementacja w prawach niestandardowych pakietu Office**: jako część opcji *Zmiana* i *Pełna kontrola*.

**Nazwa w klasycznym portalu Azure**: *Zapisz plik*

**Nazwa w szablonach usługi AD RMS**: *Zapisz*

**Stała lub wartość interfejsu API**: IPC_GENERIC_WRITE L"EDIT"

W aplikacjach pakietu Office to prawo umożliwia użytkownikowi modyfikowanie dokumentu.

---

### Komentarz

Pozwala dodawać adnotacje i komentarze do zawartości.

**Kodowanie w zasadach**: COMMENT

**Implementacja w prawach niestandardowych pakietu Office**: nie zaimplementowane.

**Nazwa w klasycznym portalu Azure**: nie zaimplementowane.

**Nazwa w szablonach usługi AD RMS:** nie zaimplementowane.

**Stała lub wartość interfejsu API**: IPC_GENERIC_COMMENT L"COMMENT

To prawo jest dostępne w zestawie SDK oraz jest dostępne w formie zasad ad hoc w module RMS Protection w środowisku Windows PowerShell. Zostało zaimplementowane w niektórych aplikacjach dostawców oprogramowania. Nie jest jednak powszechnie używane i obecnie nie jest obsługiwane przez aplikacje pakietu Office.

---

### Zapisz jako, Eksportuj

Włącza opcję zapisu zawartości w pliku o innej nazwie (Zapisz jako). W przypadku dokumentów pakietu Office plik może zostać zapisany bez ochrony.

**Kodowanie w zasadach:** EXPORT

**Implementacja w prawach niestandardowych pakietu Office**: jako część opcji *Zmiana* i *Pełna kontrola*.

**Nazwa w klasycznym portalu Azure:** *Eksportuj zawartość (Zapisz jako)*

**Nazwa w szablonach usługi AD RMS:** *Eksportuj (Zapisz jako)*

**Stała lub wartość interfejsu API**: IPC_GENERIC_EXPORT L"EXPORT"

To uprawnienie umożliwia też użytkownikowi korzystanie z innych opcji eksportu w aplikacjach, np. opcji *Wyślij do programu OneNote*.

---

### Prześlij dalej

Włącza opcję przekazywania dalej wiadomości e-mail oraz dodawania adresatów w wierszach *Do* i *DW*. To prawo dotyczy tylko wiadomości e-mail, a nie dokumentów.

**Kodowanie w zasadach:** FORWARD

**Implementacja w prawach niestandardowych pakietu Office:** odmowa przy użyciu standardowych zasad *Nie przekazuj*.

**Nazwa w klasycznym portalu Azure:** *Prześlij dalej*

**Nazwa w szablonach usługi AD RMS:** *Prześlij dalej*

**Stała lub wartość interfejsu API:** IPC_EMAIL_FORWARD L"FORWARD"

Nie zezwala osobie przekazującej wiadomość dalej na przyznanie praw innym użytkownikom jako części akcji przekazywania.

---

### Pełna kontrola

Przyznaje wszystkie prawa do dokumentu. Można wykonywać wszystkie dostępne akcje.

**Kodowanie w zasadach:** OWNER

**Implementacja w prawach niestandardowych pakietu Office**: jako opcja niestandardowa *Pełna kontrola*.

**Nazwa w klasycznym portalu Azure:** *Pełna kontrola*

**Nazwa w szablonach usługi AD RMS:** *Pełna kontrola*

**Stała lub wartość interfejsu API:** IPC_GENERIC_ALL L"OWNER"

Obejmuje możliwość usunięcia ochrony.

---

### Drukowanie

Włącza opcje związane z drukowaniem zawartości.

**Kodowanie w zasadach:** PRINT

**Implementacja w prawach niestandardowych pakietu Office:** jako opcja *Drukuj zawartość* w uprawnieniach niestandardowych. Nie jest to ustawienie określane dla poszczególnych odbiorców.

**Nazwa w klasycznym portalu Azure:** *Drukuj*

**Nazwa w szablonach usługi AD RMS:** *Drukuj*

**Stała lub wartość interfejsu API:** IPC_GENERIC_PRINT L"PRINT

---

### Odpowiedz

Włącza opcję Odpowiedz w kliencie poczty e-mail bez możliwości zmiany w wierszach *Do* lub *DW*.

**Kodowanie w zasadach:** REPLY

**Implementacja w prawach niestandardowych pakietu Office**: nie dotyczy

**Nazwa w klasycznym portalu Azure:** *Odpowiedz*

**Nazwa w szablonach usługi AD RMS:** *Odpowiedz*

**Stała lub wartość interfejsu API:** IPC_EMAIL_REPLY

---

### Odpowiedz wszystkim

Włącza opcję *Odpowiedz wszystkim* w kliencie poczty e-mail, ale nie zezwala użytkownikom na dodawanie odbiorców w wierszach *Do* lub *DW*.

**Kodowanie w zasadach:** REPLYALL

**Implementacja w prawach niestandardowych pakietu Office**: nie dotyczy

**Nazwa w klasycznym portalu Azure:** *Odpowiedz wszystkim*

**Nazwa w szablonach usługi AD RMS:** *Odpowiedz wszystkim*

**Stała lub wartość interfejsu API:** IPC_EMAIL_REPLYALL L"REPLYALL"

---

### Wyświetl, Otwórz, Odczytaj

Umożliwia użytkownikom otworzenie dokumentu i wyświetlenie zawartości.

**Kodowanie w zasadach:** VIEW

**Implementacja w prawach niestandardowych pakietu Office**: jako zasady niestandardowe *Odczytaj*, opcja *Wyświetl*.

**Nazwa w klasycznym portalu Azure:** *Wyświetl zawartość*

**Nazwa w szablonach usługi AD RMS:** *Wyświetl*

**Stała lub wartość interfejsu API:** IPC_GENERIC_READ L"VIEW"

---

### Kopiuj

Włącza opcje kopiowania danych (w tym przechwytywania ekranu) z dokumentu do tego samego lub innego dokumentu.

**Kodowanie w zasadach:** EXTRACT

**Implementacja w prawach niestandardowych pakietu Office:** Jako opcja *Zezwalaj użytkownikom z dostępem do odczytu na kopiowanie zawartości* zasady niestandardowej.

**Nazwa w klasycznym portalu Azure:** *Kopiuj i Wyodrębnij zawartość*

**Nazwa w szablonach usługi AD RMS:** *Wyodrębnij*

**Stała lub wartość interfejsu API:** IPC_GENERIC_EXTRACT L"EXTRACT"

W niektórych aplikacjach pozwala także na zapisanie całego dokumentu w postaci niechronionej.

---


### Włącz makra

Włącza opcję uruchamiania makr lub innych rozwiązań programistycznych albo zezwala na zdalny dostęp do zawartości w dokumencie.

**Kodowanie w zasadach:** OBJMODEL

**Implementacja w prawach niestandardowych pakietu Office**: jako opcja zasad niestandardowych *Zezwalaj na dostęp programistyczny*. Nie jest to ustawienie określane dla poszczególnych odbiorców.

**Nazwa w klasycznym portalu Azure:** *Zezwalaj na makra*

**Nazwa w szablonach usługi AD RMS:** *Zezwalaj na makra*

**Stała lub wartość interfejsu API**: nie dotyczy


## Prawa zawarte w poziomach uprawnień

Niektóre aplikacje grupują prawa użytkowania w poziomach uprawnień. Dzięki temu można łatwiej wybrać prawa użytkowania, które zazwyczaj stosuje się wspólnie. Te poziomy uprawnień upraszczają skomplikowane działania po stronie użytkowników, którzy mogą wybrać opcje oparte na rolach.  Na przykład **Osoba dokonująca przeglądu** i **Współautor**. Chociaż opcje te często są dostępne z podsumowaniem praw, to mogą one nie obejmować wszystkich praw wymienionych w poprzedniej tabeli.

W tabeli poniżej znajduje się lista poziomów uprawnień i pełna lista praw w nich zawartych.

|Poziom uprawnień|Aplikacje|Zawarte prawa (nazwa pospolita)|
|---------------------|----------------|---------------------------------|
|Przeglądanie|Klasyczny portal Azure<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Odpowiedz; Odpowiedz wszystkim|
|Osoba dokonująca przeglądu|Klasyczny portal Azure<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość; Odpowiedz [[1]](#footnote-1); Odpowiedz wszystkim [[1]](#footnote-1); Prześlij dalej [[1]](#footnote-1)|
|Współautor|Klasyczny portal Azure<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Kopiuj; Wyświetl prawa; Zezwalaj na makra; Zapisz jako; Eksportuj; Drukuj; Odpowiedz [[1]](#footnote-1); Odpowiedz wszystkim [[1]](#footnote-1); Prześlij dalej [[1]](#footnote-1)|
|Współwłaściciel|Klasyczny portal Azure<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Kopiuj; Wyświetl prawa; Zezwalaj na makra; Zapisz jako; Eksportuj; Drukuj; Odpowiedz [[1]](#footnote-1); Odpowiedz wszystkim [[1]](#footnote-1); Prześlij dalej [[1]](#footnote-1); Pełna kontrola|

----

###### Przypis 1
Nie dotyczy aplikacji do udostępniania usługi Microsoft Rights Management dla systemu Windows.

## Prawa zawarte w domyślnych szablonach
W szablonach domyślnych zawarte są następujące prawa:

|Nazwa wyświetlana|Zawarte prawa (nazwa pospolita)|
|----------------|---------------------------------|
|&lt;*nazwa organizacji*&gt; *— tylko wgląd poufny*|Wyświetl, Otwórz, Odczytaj|
|&lt;*nazwa organizacji*&gt; *— poufne*|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość; Edytuj; Wyświetl prawa; Zezwalaj na makra; Prześlij dalej; Odpowiedz; Odpowiedz wszystkim|

## Opcja Nie przekazuj dotycząca wiadomości e-mail

Klienci i usługi programu Exchange (na przykład klient programu Outlook, aplikacja Outlook Web Access i reguły transportu programu Exchange) mają jedną dodatkową opcję ochrony praw do informacji na potrzeby wiadomości e-mail: **Nie przekazuj**. 

Mimo że ta opcja jest dostępna dla użytkowników (i administratorów programu Exchange) w sposób sugerujący, że jest to domyślny szablon usługi Rights Management, który można wybrać, opcja **Nie przekazuj** nie jest szablonem. Tłumaczy to, dlaczego ta opcja nie jest widoczna w klasycznym portalu Azure podczas wyświetlania szablonów usług Azure RMS i zarządzania nimi. Zamiast tego opcje **Nie przekazuj** stanowią zestaw uprawnień dynamicznie stosowany przez użytkowników względem ich adresatów wiadomości e-mail.

Gdy opcja **Nie przekazuj** jest stosowana do wiadomości e-mail, adresaci nie mogą przekazać takiej wiadomości e-mail, wydrukować jej, skopiować z niej informacji, zapisać załączników ani zapisać załączników pod inną nazwą. Na przykład w kliencie programu Outlook przycisk Prześlij dalej jest niedostępny, opcje menu **Zapisz jako**, **Zapisz załącznik** i **Drukuj** nie są dostępne oraz nie można dodawać ani zmieniać adresatów w polach **Do**, **DW** i **UDW**.

Jest to ważna różnica między stosowaniem opcji **Nie przekazuj** i stosowaniem szablonu, za pomocą którego nie są przyznawane uprawnienia do przekazywania wiadomości e-mail: opcja **Nie przekazuj** używa dynamicznej listy autoryzowanych użytkowników opartej na wybranych przez użytkownika adresatach pierwotnej wiadomości e-mail. Prawa w szablonie zawierają natomiast statyczną listę autoryzowanych użytkowników określonych wcześniej przez administratora. Na czym polega różnica? Zostanie to wytłumaczone na przykładzie: 

Użytkownik chce wysłać pewne informacje w wiadomości e-mail do określonych osób w dziale marketingu, które nie powinny być udostępniane nikomu innemu. Czy w takiej sytuacji użytkownik powinien chronić wiadomość e-mail za pomocą szablonu ograniczającego prawa (do wyświetlania, odpowiedzi i zapisywania) tylko do działu marketingu?  Czy może powinna zostać użyta opcja **Nie przekazuj**? Obie te opcje spowodują, że adresaci nie będą mogli przekazywać wiadomości e-mail. 

- W przypadku zastosowania szablonu adresaci będą jednak mogli nadal udostępniać informacje innym użytkownikom w dziale marketingu. Na przykład adresat będzie mógł użyć Eksploratora Windows do przeciągnięcia i upuszczenia wiadomości e-mail do współdzielonej lokalizacji lub dysku USB. W takiej sytuacji każdy użytkownik z działu marketingu (oraz właściciel wiadomości e-mail), który ma dostęp do tej lokalizacji, będzie mógł wyświetlać informacje zawarte w wiadomości e-mail.
 
- Jeśli natomiast użytkownik zastosuje opcję **Nie przekazuj**, adresaci nie będą mogli udostępniać informacji nikomu innemu w dziale marketingu za pomocą przenoszenia wiadomości e-mail do innej lokalizacji. W takim scenariuszu tylko pierwotni adresaci (oraz właściciel wiadomości e-mail) będą mogli wyświetlać informacje zawarte w wiadomości e-mail.

> [!NOTE] 
> Użyj opcji **Nie przekazuj**, jeśli ważne jest, aby tylko wybrani przez nadawcę adresaci mogli wyświetlać informacje zawarte w wiadomości e-mail. Użyj szablonu na potrzeby wiadomości e-mail do ograniczenia praw do grupy osób określonych wcześniej przez administratora, niezależnie od adresatów wybranych przez nadawcę.




## Zobacz też
[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](configure-custom-templates.md)




<!--HONumber=Jul16_HO3-->


