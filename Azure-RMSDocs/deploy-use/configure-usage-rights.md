---
title: "Konfigurowanie praw użytkowania dla usługi Azure Rights Management — AIP"
description: "Informacje pomagające zrozumieć i zidentyfikować określone prawa, które są używane w przypadku ochrony plików lub wiadomości e-mail przy użyciu usługi Azure Rights Management w ramach usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 62ea1579b61b096e1f7fe6900d72b1b8077c9ff1
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2017
---
# <a name="configuring-usage-rights-for-azure-rights-management"></a>Konfigurowanie praw użytkowania dla usługi Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

Jeśli ustawiasz ochronę plików lub wiadomości e-mail za pomocą usługi Azure Rights Management w ramach usługi Azure Information Protection bez użycia szablonu, musisz własnoręcznie skonfigurować prawa użytkowania. Ponadto podczas konfigurowania szablonów lub etykiety dla ochrony usługi Azure Rights Management, wybierz prawa użytkowania, które zostaną automatycznie zastosowane w przypadku wybrania szablonu lub etykieta przez użytkowników, administratorów lub skonfigurowane usługi. Na przykład w portalu Azure można wybrać role, które powodują ustawienie logicznego grupowania praw użytkowania, lub można skonfigurować poszczególne prawa.

Niniejszy artykuł pomoże Ci skonfigurować prawa użytkowania dla używanej aplikacji oraz zrozumieć, jak te prawa będą interpretowane przez aplikacje.

## <a name="usage-rights-and-descriptions"></a>Prawa użytkowania wraz z opisami
Poniższa tabela zawiera listę i opisy praw użytkowania obsługiwanych przez usługę Rights Management oraz sposób ich wykorzystania i interpretowania. Są one wyświetlane według **nazwy pospolitej**, która jest często spotykanym sposobem na wyświetlenie prawa użytkowania lub odniesienie się do niego. Jest to przyjaźniejsza wersja jednowyrazowej wartości używanej w kodzie (wartość **Kodowanie w zasadach**). 

**Stała lub wartość API** jest nazwą zestawu SDK wywołania MSIPC API używanego podczas pisania aplikacji obsługujących usługę RMS. Wywołanie sprawdza prawa użytkowania lub dodaje prawo użytkowania do zasad.


|Prawe|Opis|Implementacja|
|-------------------------------|---------------------------|-----------------|
|Nazwa pospolita: **Edytuj zawartość, Edytuj** <br /><br />Kodowanie w zasadach: **DOCEDIT**|Zezwala użytkownikowi na modyfikowanie, rozmieszczanie, formatowanie lub filtrowanie zawartości wewnątrz aplikacji. Nie nadaje prawa do zapisywania edytowanej kopii.|W prawach niestandardowych pakietu Office: jako część opcji **Zmiana** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Edytuj zawartość**<br /><br />Nazwa w witrynie Azure Portal: zawarte w opcji **Edytuj i zapisz**<br /><br />Nazwa w szablonach usługi AD RMS: **Edytuj** <br /><br />Stała lub wartość interfejsu API: nie dotyczy.|
|Nazwa pospolita: **Zapisz** <br /><br />Kodowanie w zasadach: **EDIT**|Umożliwia użytkownikowi zapisanie dokumentu w jego bieżącej lokalizacji.<br /><br />W aplikacjach pakietu Office to prawo umożliwia użytkownikowi modyfikowanie dokumentu.|W prawach niestandardowych pakietu Office: jako część opcji **Zmiana** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Zapisz plik**<br /><br />Nazwa w witrynie Azure Portal: zawarte w opcji **Edytuj i zapisz**<br /><br />Nazwa w szablonach usługi AD RMS: **Zapisz** <br /><br />Stała API lub wartość API: `IPC_GENERIC_WRITE L"EDIT"`|
|Nazwa pospolita: **Komentarz** <br /><br />Kodowanie w zasadach: **COMMENT**|Pozwala dodawać adnotacje i komentarze do zawartości.<br /><br />To uprawnienie jest dostępne w zestawie SDK oraz jest dostępne w formie zasad ad hoc w usłudze Azure Information Protection i w module RMS Protection w środowisku Windows PowerShell. Zostało też zaimplementowane w niektórych aplikacjach dostawców oprogramowania. Nie jest jednak powszechnie używane i obecnie nie jest obsługiwane przez aplikacje pakietu Office.|W prawach niestandardowych pakietu Office: nie zaimplementowane. <br /><br />Nazwa w klasycznym portalu Azure: nie zaimplementowane.<br /><br />Nazwa w witrynie Azure Portal: nie zaimplementowane.<br /><br />Nazwa w szablonach usługi AD RMS: nie zaimplementowane. <br /><br />Stała API lub wartość API: `IPC_GENERIC_COMMENT L"COMMENT`|
|Nazwa pospolita: **Zapisz jako, Eksportuj** <br /><br />Kodowanie w zasadach: **EXPORT**|Włącza opcję zapisu zawartości w pliku o innej nazwie (Zapisz jako). W przypadku dokumentów pakietu Office i klienta usługi Azure Information Protection plik można zapisać bez ochrony.<br /><br />To uprawnienie umożliwia też użytkownikowi korzystanie z innych opcji eksportu w aplikacjach, np. opcji **Wyślij do programu OneNote**.<br /><br /> Uwaga: jeśli nie udzielono tego uprawnienia, aplikacje pakietu Office umożliwiają użytkownikowi zapis dokumentu pod nową nazwą, jeśli wybrany format pliku natywnie obsługuje ochronę za pomocą usługi Microsoft Rights Management.|W prawach niestandardowych pakietu Office: jako część opcji **Zmiana** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Eksportuj zawartość (Zapisz jako)** <br /><br />Nazwa w witrynie Azure Portal: zawarte w opcji **Pełna kontrola**<br /><br />Nazwa w szablonach usługi AD RMS: **Eksportuj (Zapisz jako)** <br /><br />Stała API lub wartość API: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Nazwa pospolita: **Prześlij dalej** <br /><br />Kodowanie w zasadach: **FORWARD**|Włącza opcję przesyłania dalej wiadomości e-mail oraz dodawania adresatów w wierszach **Do** i **DW**. To prawo dotyczy tylko wiadomości e-mail, a nie dokumentów.<br /><br />Nie zezwala osobie przekazującej wiadomość dalej na przyznanie praw innym użytkownikom jako części akcji przekazywania. <br /><br />Gdy przyznasz to uprawnienie, przyznaj również uprawnienie **Edytuj zawartość, Edytuj** (nazwa pospolita), aby upewnić się, że oryginalna wiadomość e-mail stanowi część przesłanej dalej wiadomości e-mail, a nie załącznik. To uprawnienie jest również wymagane, gdy wysyłasz wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacji sieci Web programu Outlook.|W prawach niestandardowych pakietu Office: odmowa przy użyciu standardowych zasad **Nie przekazuj**.<br /><br />Nazwa w klasycznym portalu Azure: **Prześlij dalej**<br /><br />Nazwa w witrynie Azure Portal: **Prześlij dalej**<br /><br />Nazwa w szablonach usługi AD RMS: **Prześlij dalej** <br /><br />Stała API lub wartość API: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Nazwa pospolita: **Pełna kontrola** <br /><br />Kodowanie w zasadach: **OWNER**|Przyznaje wszystkie prawa do dokumentu. Można wykonywać wszystkie dostępne akcje.<br /><br />Obejmuje możliwość usunięcia ochrony i ponownego włączenia ochrony dokumentu. <br /><br />Pamiętaj, że to prawo użycia nie jest takie samo jak [właściciela usługi Rights Management](#rights-management-issuer-and-rights-management-owner).|W prawach niestandardowych pakietu Office: jako opcja niestandardowa **Pełna kontrola**.<br /><br />Nazwa w klasycznym portalu Azure: **Pełna kontrola**<br /><br />Nazwa w witrynie Azure Portal: **Pełna kontrola**<br /><br />Nazwa w szablonach usługi AD RMS: **Pełna kontrola** <br /><br />Stała API lub wartość API: `IPC_GENERIC_ALL L"OWNER"`|
|Nazwa pospolita: **Drukuj** <br /><br />Kodowanie w zasadach: **PRINT**|Włącza opcje związane z drukowaniem zawartości.|W prawach niestandardowych pakietu Office: jako opcja **Drukuj zawartość** w uprawnieniach niestandardowych. Nie jest to ustawienie określane dla poszczególnych odbiorców.<br /><br />Nazwa w klasycznym portalu Azure: **Drukuj**<br /><br />Nazwa w witrynie Azure Portal: **Drukuj**<br /><br />Nazwa w szablonach usługi AD RMS: **Drukuj** <br /><br />Stała API lub wartość API: `IPC_GENERIC_PRINT L"PRINT"`|
|Nazwa pospolita: **Odpowiedz** <br /><br />Kodowanie w zasadach: **REPLY**|Włącza opcję **Odpowiedz** w kliencie poczty e-mail bez możliwości zmiany w wierszach **Do** lub **DW**.<br /><br />Gdy przyznasz to uprawnienie, przyznaj również uprawnienie **Edytuj zawartość, Edytuj** (nazwa pospolita), aby upewnić się, że oryginalna wiadomość e-mail stanowi część przesłanej dalej wiadomości e-mail, a nie załącznik. To uprawnienie jest również wymagane, gdy wysyłasz wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacji sieci Web programu Outlook.|W prawach niestandardowych pakietu Office: nie dotyczy.<br /><br />Nazwa w klasycznym portalu Azure: **Odpowiedz**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz** <br /><br />Stała API lub wartość API: `IPC_EMAIL_REPLY`|
|Nazwa pospolita: **Odpowiedz wszystkim** <br /><br />Kodowanie w zasadach: **REPLYALL**|Włącza opcję **Odpowiedz wszystkim** w kliencie poczty e-mail, ale nie zezwala użytkownikowi na dodawanie odbiorców w wierszach **Do** lub **DW**.<br /><br />Gdy przyznasz to uprawnienie, przyznaj również uprawnienie **Edytuj zawartość, Edytuj** (nazwa pospolita), aby upewnić się, że oryginalna wiadomość e-mail stanowi część przesłanej dalej wiadomości e-mail, a nie załącznik. To uprawnienie jest również wymagane, gdy wysyłasz wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacji sieci Web programu Outlook.|W prawach niestandardowych pakietu Office: nie dotyczy.<br /><br />Nazwa w klasycznym portalu Azure: **Odpowiedz wszystkim**<br /><br />Nazwa w witrynie Azure Portal: **Odpowiedz wszystkim**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz wszystkim** <br /><br />Stała API lub wartość API: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Nazwa pospolita: **Wyświetl, Otwórz, Odczytaj** <br /><br />Kodowanie w zasadach: **VIEW**|Umożliwia użytkownikom otworzenie dokumentu i wyświetlenie zawartości.|W prawach niestandardowych pakietu Office: jako zasady niestandardowe **Odczytaj**, opcja **Wyświetl**.<br /><br />Nazwa w klasycznym portalu Azure: **Wyświetl**<br /><br />Nazwa w witrynie Azure Portal: **Wyświetl zawartość**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz wszystkim** <br /><br />Stała API lub wartość API: `IPC_GENERIC_READ L"VIEW"`|
|Nazwa pospolita: **Kopiuj** <br /><br />Kodowanie w zasadach: **EXTRACT**|Włącza opcje kopiowania danych (w tym przechwytywania ekranu) z dokumentu do tego samego lub innego dokumentu.<br /><br />W niektórych aplikacjach pozwala także na zapisanie całego dokumentu w postaci niechronionej.|W prawach niestandardowych pakietu Office: jako opcja zasady niestandardowej **Zezwalaj użytkownikom z dostępem do odczytu na kopiowanie zawartości**.<br /><br />Nazwa w klasycznym portalu Azure: **Kopiuj i Wyodrębnij zawartość**<br /><br />Nazwa w witrynie Azure Portal: **Kopiuj i wyodrębnij zawartość**<br /><br />Nazwa w szablonach usługi AD RMS: **Wyodrębnij** <br /><br />Stała API lub wartość API: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Nazwa pospolita: **Włącz makra** <br /><br />Kodowanie w zasadach: **OBJMODEL**|Włącza opcję uruchamiania makr lub innych rozwiązań programistycznych albo zezwala na zdalny dostęp do zawartości w dokumencie.|W prawach niestandardowych pakietu Office: jako opcja zasad niestandardowych **Zezwalaj na dostęp programistyczny**. Nie jest to ustawienie określane dla poszczególnych odbiorców.<br /><br />Nazwa w klasycznym portalu Azure: **Zezwalaj na makra**<br /><br />Nazwa w witrynie Azure Portal: zawarte we wszystkich prawach, które możesz wybrać, ponieważ to uprawnienie jest wymagane dla paska usługi Azure Information Protection w aplikacjach pakietu Office.<br /><br />Nazwa w szablonach usługi AD RMS: **Zezwalaj na makra** <br /><br />Stała lub wartość interfejsu API: nie zaimplementowane.|

## <a name="rights-included-in-permissions-levels"></a>Prawa zawarte w poziomach uprawnień

Niektóre aplikacje grupują prawa użytkowania w poziomach uprawnień. Dzięki temu można łatwiej wybrać prawa użytkowania, które zazwyczaj stosuje się wspólnie. Te poziomy uprawnień upraszczają skomplikowane działania po stronie użytkowników, którzy mogą wybrać opcje oparte na rolach.  Na przykład **Recenzent** i **Współautor**. Chociaż opcje te często są dostępne z podsumowaniem praw, to mogą one nie obejmować wszystkich praw wymienionych w poprzedniej tabeli.

W tabeli poniżej znajduje się lista poziomów uprawnień i pełna lista praw w nich zawartych.

|Poziom uprawnień|Aplikacje|Zawarte prawa (nazwa pospolita)|
|---------------------|----------------|---------------------------------|
|Przeglądanie|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br /> Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Odpowiedz; Odpowiedz wszystkim; Zezwalaj na makra [[1]](#footnote-1)<br /><br />Uwaga: Dla wiadomości e-mail użyj opcji Recenzent zamiast tego poziomu uprawnień, aby upewnić się, że odpowiedź na wiadomość e-mail została odebrana jako wiadomość e-mail, a nie jako załącznik. Opcja Recenzent jest również wymagana podczas wysyłania wiadomości e-mail do innej organizacji korzystającej z klienta programu Outlook lub aplikacji sieci Web programu Outlook.|
|Recenzent|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Odpowiedz; Odpowiedz wszystkim [[2]](#footnote-2); Prześlij dalej [[2]](#footnote-2); Zezwalaj na makra [[1]](#footnote-1)|
|Współautor|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Kopiuj; Wyświetl prawa; Zezwalaj na makra; Zapisz jako, Eksportuj [[3]](#footnote-3); Drukuj; Odpowiedz [[2]](#footnote-2); Odpowiedz wszystkim [[2]](#footnote-2); Prześlij dalej [[2]](#footnote-2)|
|Współwłaściciel|Klasyczny portal Azure <br /><br />Witryna Azure Portal<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows<br /><br />Klient usługi Azure Information Protection dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Kopiuj; Wyświetl prawa; Zezwalaj na makra; Zapisz jako, Eksportuj; Drukuj; Odpowiedz [[2]](#footnote-2); Odpowiedz wszystkim [[2]](#footnote-2); Prześlij dalej [[2]](#footnote-2); Pełna kontrola|

----

###### <a name="footnote-1"></a>Przypis 1

W przypadku klienta usługi Azure Information Protection dla systemu Windows to prawo jest obecnie wymagane dla paska usługi Information Protection w aplikacjach pakietu Office.

###### <a name="footnote-2"></a>Przypis 2
Nie dotyczy klienta usługi Azure Information Protection dla systemu Windows ani aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management dla systemu Windows.

###### <a name="footnote-3"></a>Przypis 3
Nie uwzględniono w kliencie usługi Azure Information Protection dla systemu Windows. W tym kliencie prawo użycia eksportu obejmuje możliwość usunięcia ochrony.


## <a name="rights-included-in-the-default-templates"></a>Prawa zawarte w domyślnych szablonach
W szablonach domyślnych zawarte są następujące prawa:

|Nazwa wyświetlana|Zawarte prawa (nazwa pospolita)|
|----------------|---------------------------------|
|&lt;*nazwa organizacji*&gt; *— tylko wgląd poufny* <br /><br />lub<br /><br /> *Wysoce poufne\Wszyscy pracownicy*|Wyświetl, Otwórz, Odczytaj|
|&lt;*nazwa organizacji*&gt; *— poufne* <br /><br />lub <br /><br />*Poufne\Wszyscy pracownicy*|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość; Edytuj; Wyświetl prawa; Zezwalaj na makra; Prześlij dalej; Odpowiedz; Odpowiedz wszystkim|

## <a name="do-not-forward-option-for-emails"></a>Opcja Nie przekazuj dotycząca wiadomości e-mail

Klienci i usługi programu Exchange (na przykład klient programu Outlook, aplikacja Outlook Web Access i reguły transportu programu Exchange) mają jedną dodatkową opcję ochrony praw do informacji na potrzeby wiadomości e-mail: **Nie przekazuj**. 

Mimo że ta opcja jest dostępna dla użytkowników (i administratorów programu Exchange) w sposób sugerujący, że jest to domyślny szablon usługi Rights Management, który można wybrać, opcja **Nie przekazuj** nie jest szablonem. Tłumaczy to, dlaczego nie widać go w portalu Azure podczas przeglądania i zarządzania szablonami usługi Azure Rights Management. Zamiast tego opcje **Nie przekazuj** stanowią zestaw uprawnień dynamicznie stosowany przez użytkowników względem ich adresatów wiadomości e-mail.

Gdy opcja **Nie przekazuj** jest stosowana do wiadomości e-mail, adresaci nie mogą przekazać takiej wiadomości e-mail, wydrukować jej, skopiować z niej informacji, zapisać załączników ani zapisać załączników pod inną nazwą. Na przykład w kliencie programu Outlook przycisk Prześlij dalej jest niedostępny, opcje menu **Zapisz jako**, **Zapisz załącznik** i **Drukuj** nie są dostępne oraz nie można dodawać ani zmieniać adresatów w polach **Do**, **DW** i **UDW**.

Jest to ważna różnica między stosowaniem opcji **Nie przekazuj** i stosowaniem szablonu, za pomocą którego nie są przyznawane uprawnienia do przekazywania wiadomości e-mail: opcja **Nie przekazuj** używa dynamicznej listy autoryzowanych użytkowników opartej na wybranych przez użytkownika adresatach pierwotnej wiadomości e-mail. Prawa w szablonie zawierają natomiast statyczną listę autoryzowanych użytkowników określonych wcześniej przez administratora. Na czym polega różnica? Zostanie to wytłumaczone na przykładzie: 

Użytkownik chce wysłać pewne informacje w wiadomości e-mail do określonych osób w dziale marketingu, które nie powinny być udostępniane nikomu innemu. Czy w takiej sytuacji użytkownik powinien chronić wiadomość e-mail za pomocą szablonu ograniczającego prawa (do wyświetlania, odpowiedzi i zapisywania) tylko do działu marketingu?  Czy może powinna zostać użyta opcja **Nie przekazuj**? Obie te opcje spowodują, że adresaci nie będą mogli przekazywać wiadomości e-mail. 

- W przypadku zastosowania szablonu adresaci będą jednak mogli nadal udostępniać informacje innym użytkownikom w dziale marketingu. Na przykład adresat będzie mógł użyć Eksploratora Windows do przeciągnięcia i upuszczenia wiadomości e-mail do współdzielonej lokalizacji lub dysku USB. W takiej sytuacji każdy użytkownik z działu marketingu (oraz właściciel wiadomości e-mail), który ma dostęp do tej lokalizacji, będzie mógł wyświetlać informacje zawarte w wiadomości e-mail.
 
- Jeśli natomiast użytkownik zastosuje opcję **Nie przekazuj**, adresaci nie będą mogli udostępniać informacji nikomu innemu w dziale marketingu za pomocą przenoszenia wiadomości e-mail do innej lokalizacji. W takim scenariuszu tylko pierwotni adresaci (oraz właściciel wiadomości e-mail) będą mogli wyświetlać informacje zawarte w wiadomości e-mail.

> [!NOTE] 
> Użyj opcji **Nie przekazuj**, jeśli ważne jest, aby tylko wybrani przez nadawcę adresaci mogli wyświetlać informacje zawarte w wiadomości e-mail. Użyj szablonu na potrzeby wiadomości e-mail do ograniczenia praw do grupy osób określonych wcześniej przez administratora, niezależnie od adresatów wybranych przez nadawcę.

## <a name="rights-management-issuer-and-rights-management-owner"></a>Wystawca usługi Rights Management i właściciel usługi Rights Management

Gdy dokument lub wiadomość e-mail są chronione za pomocą usługi Azure Rights Management, konto, które automatycznie chroni zawartość, staje się wystawcą usługi Rights Management dla tej zawartości. To konto jest rejestrowane jako pole **issuer** w [dziennikach użycia](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs). 

Wystawca usługi Rights Management ma zawsze przyznawane prawo użycia Pełna kontrola do dokumentu lub wiadomości e-mail, a ponadto:

- Jeśli ustawienia ochrony zawierają datę wygaśnięcia, wystawca usługi Rights Management nadal może otwierać i edytować dokument lub wiadomość e-mail po tej dacie.

- Wystawca usługi Rights Management zawsze ma dostęp do dokumentu lub wiadomości e-mail w trybie offline.

- Wystawca usługi Rights Management nadal może otworzyć dokument po jego odwołaniu. 

Domyślnie to konto jest także **właścicielem usługi Rights Management** dla tej zawartości, czyli jest to przypadek, gdy ochrona jest inicjowana przez użytkownika, który utworzył dokument lub wiadomość e-mail. Jednak istnieją pewne scenariusze, gdy administrator lub usługa może chronić zawartość w imieniu użytkowników. Na przykład:

- Administrator zapewnia zbiorczą ochronę plików w udziale plików: konto administratora w usłudze Azure AD chroni dokumenty dla użytkowników.

- Łącznik usługi Rights Management chroni dokumenty pakietu Office w folderze systemu Windows Server: główne konto usługi w usłudze Azure AD, które jest utworzone dla łącznika usługi RMS, chroni dokumenty dla użytkowników.

W tych scenariuszach wystawca usługi Rights Management może przypisać właściciela usługi Rights Management do innego konta, korzystając z zestawów SDK usługi Azure Information Protection lub programu PowerShell. Na przykład w przypadku używania polecenia cmdlet programu PowerShell [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) z klientem usługi Azure Information Protection możesz określić parametr **OwnerEmail**, aby przypisać właściciela usługi Rights Management do innego konta. 

Gdy wystawca usługi Rights Management realizuje ochronę w imieniu użytkowników, przypisanie właściciela usługi Rights Management zapewnia, że oryginalny właściciel dokumentu lub wiadomości e-mail ma ten sam poziom kontroli dla swojej chronionej zawartości, jakby on sam zainicjował ochronę. 

Na przykład użytkownik, który utworzył dokument, może go wydrukować, mimo że teraz jest chroniony za pomocą szablonu, który nie zawiera prawa użycia Drukuj. Ten sam użytkownik ma zawsze dostęp do swojego dokumentu niezależnie od ustawienia dostępu w trybie offline lub daty wygaśnięcia, które mogą być skonfigurowane w tym szablonie. Ponadto, ponieważ właściciel usługi Rights Management ma prawo użycia Pełna kontrola, ten użytkownik może również ponownie chronić dokument w celu umożliwienia dostępu dodatkowym użytkownikom (w tym momencie użytkownik staje się wystawcą usługi Rights Management oraz właścicielem usługi Rights Management) i ten użytkownik może nawet usunąć ochronę. Jednak tylko wystawca usługi Rights Management może śledzić i odwoływać dokument.

Właściciel usługi Rights Management dla dokumentu lub wiadomości e-mail jest rejestrowany jako pole **owner-email** w [dziennikach użycia](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs).

Pamiętaj, że właściciel usługi Rights Management jest niezależny od właściciela systemu plików systemu Windows. Często to ta sama osoba, ale mogą to też być różne osoby, nawet jeśli nie używasz zestawów SDK ani programu PowerShell.

## <a name="see-also"></a>Zobacz też
[Konfigurowanie i zarządzanie nimi szablonów usługi Azure Information Protection](configure-policy-templates.md))

[Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](configure-super-users.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

