---
title: "Zasady domyślne dla usługi Azure Information Protection"
description: "Dowiedz się, w jaki sposób są skonfigurowane domyślne zasady usługi Azure Information Protection. Jeśli zmodyfikujesz zasady domyślne, możesz odnieść się do tych wartości, aby przywrócić wartości domyślne zasad."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
ms.openlocfilehash: 712d273e735d2c9fc791a1f15c3f8dc9e917a1c3
ms.sourcegitcommit: 5bcb916106021f624a69d620bbcc2c4a51398771
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2017
---
# <a name="the-default-azure-information-protection-policy"></a>Domyślne zasady usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Skorzystaj z poniższych informacji, aby poznać, jak są skonfigurowane domyślne zasady usługi Azure Information Protection.

Gdy administrator po raz pierwszy łączy się z usługą Azure Information Protection przy użyciu witryny Azure Portal, zostaną utworzone zasady domyślne dla tej dzierżawy. Od czasu do czasu firma Microsoft może wprowadzić zmiany w zasadach domyślnych, ale jeśli usługa była już używana przed zmianą zasad domyślnych, poprzednia wersja zasad domyślnych nie zostanie zaktualizowana, ponieważ mogły one zostać skonfigurowane i wdrożone do środowiska produkcyjnego przez użytkownika.

Możesz odwołać się do poniższych wartości, aby powrócić do ustawień domyślnych zasad, lub zaktualizować zasady do najnowszych wartości.

## <a name="current-default-policy"></a>Bieżące zasady domyślne

Jest to wersja lub domyślne zasady z 31 lipca 2017 r.

Ta zasada domyślna jest tworzony tylko wtedy, gdy usługa Azure Rights Management została aktywowana, podczas tworzenia zasady. Jeśli ta usługa nie została aktywowana, domyślne zasady nie konfiguruje ochronę następujących etykiety podrzędne:

- **Poufne\Wszyscy pracownicy**

- **Poufne \ odbiorców**

- **Wysoce poufne\Wszyscy pracownicy** 

- **Poufny \ odbiorców** 

Gdy te etykiety podrzędne nie są automatycznie skonfigurowany do ochrony, domyślne zasady pozostaje taki sam jak [poprzedniego domyślne zasady](#default-policy-before-july-31-2017).

Jeśli ochrona jest stosowana do **wszyscy pracownicy** etykiety podrzędne, ochrona jest konfigurowana przy użyciu domyślnych szablonów, które zostaną automatycznie przekonwertowane na etykiet w portalu Azure. Aby uzyskać więcej informacji na temat tych szablonów, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md).

Począwszy od 30 sierpnia 2017 tej wersji lub domyślne zasady zawiera zlokalizowane wersje etykieta nazwy i opisy. 

#### <a name="more-information-about-the-recipients-only-sub-label"></a>Więcej informacji na temat odbiorców tylko etykieta podrzędna

Użytkownicy widzą tę etykietę tylko w programie Outlook. Nie widzą tę etykietę w programie Word, Excel, PowerPoint lub w Eksploratorze plików. 

Gdy użytkownicy wybierają tej etykiety, opcji programu Outlook nie przesyłaj dalej jest automatycznie stosowana do wiadomości e-mail. Odbiorców, które określają użytkowników nie może przesłać wiadomości e-mail i nie można skopiować Drukuj zawartość lub zapisać załączniki.


### <a name="labels"></a>Etykiety

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Osobiste|Dane niebiznesowe, tylko do użytku osobistego.|**Włączone**: Włączone <br /><br />**Kolor**: Jasnozielony<br /><br />**Oznaczenia wizualne**: Brak <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Publiczne|Dane biznesowe, które są specjalnie przygotowane i zatwierdzone do użytku publicznego.|**Włączone**: Włączone <br /><br />**Kolor**: Zielony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Ogólne|Dane biznesowe, które nie są przeznaczone do użytku publicznego. Jednak mogą one być udostępniane partnerom zewnętrznym w razie potrzeby. Do przykładów należą wewnętrzna książka telefoniczna firmy, schematy organizacyjne, standardy wewnętrzne i większość komunikacji wewnętrznej.|**Włączone**: Włączone <br /><br />**Kolor**: Niebieski <br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufne|Wrażliwe dane biznesowe, które mogą spowodować szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. Do przykładów należą kontrakty, raporty dotyczące zabezpieczeń, podsumowania prognoz i dane konta sprzedaży.|**Włączone**: Włączone <br /><br />**Kolor**: Pomarańczowy<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Wysoce poufne|Bardzo wrażliwe dane biznesowe, które spowodują szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. Do przykładów należą dane pracowników i klientów, hasła, kod źródłowy i wstępnie zapowiadane raporty finansowe.|**Włączone**: Włączone <br /><br />**Kolor**: Czerwony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|


### <a name="sub-labels"></a>Etykiety podrzędne

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Poufne\Wszyscy pracownicy|Dane poufne, które wymagają ochrony, możliwe do wyświetlenia przez wszystkich pracowników z pełnymi uprawnieniami. Właściciele danych mogą śledzić i odwoływać zawartość.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Usługa Azure RMS [[1]](#footnote-1)|
|Poufne\Każdy (niechronione)|Dane, które nie wymagają ochrony. Używaj tej opcji z rozwagą w sytuacjach uzasadnionych potrzebami biznesowymi.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako poufne <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufne \ odbiorców|Dane poufne wymagającego ochrony i które można wyświetlić, tylko adresatów.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (poczta e-mail)<br /><br />Sklasyfikowane jako poufne <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Ustawianie uprawnień zdefiniowanych przez użytkownika (wersja zapoznawcza) w programie Outlook zastosować nie przesyłaj dalej|
|Wysoce poufne\Wszyscy pracownicy|Wysoce poufne dane, dla których wszyscy pracownicy mają uprawnienia do wyświetlania, edycji i udzielania odpowiedzi dla tej zawartości. Właściciele danych mogą śledzić i odwoływać zawartość.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako wysoce poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Usługa Azure RMS [[2]](#footnote-2)|
|Wysoce poufne\Każdy (niechronione)|Dane, które nie wymagają ochrony. Używaj tej opcji z rozwagą w sytuacjach uzasadnionych potrzebami biznesowymi.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako wysoce poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufny \ odbiorców|Ściśle poufnych danych wymagającego ochrony i które można wyświetlić, tylko adresatów.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (poczta e-mail)<br /><br />Sklasyfikowane jako wysoce poufne <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Ustawianie uprawnień zdefiniowanych przez użytkownika (wersja zapoznawcza) w programie Outlook zastosować nie przesyłaj dalej|

###### <a name="footnote-1"></a>Przypis 1
Uprawnienia ochrony odpowiadają [domyślny szablon](configure-policy-templates.md#default-templates), **poufne \ wszyscy pracownicy**.

###### <a name="footnote-2"></a>Przypis 2 
Uprawnienia ochrony odpowiadają [domyślny szablon](configure-policy-templates.md#default-templates), **poufny \ wszyscy pracownicy**.


### <a name="information-protection-bar"></a>Pasek usługi Information Protection

|Ustawienie|Wartość|
|-------------------------------|---------------------------|
|Tytuł|Czułość|
|Etykietka narzędzia|Bieżąca etykieta dla tej zawartości. To ustawienie umożliwia określenie ryzyka dla firmy, jeśli ta zawartość jest udostępniana nieuprawnionym osobom wewnątrz lub na zewnątrz organizacji.|


### <a name="settings"></a>Ustawienia

|Ustawienie|Wartość|
|-------------------------------|---------------------------|
|Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę (stosowaną automatycznie lub przez użytkowników)|Wyłączone|
|Wybierz etykietę domyślną|Brak|
|Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę|Wyłączone|
|W przypadku wiadomości e-mail z załącznikami należy stosować etykiety odpowiadające najwyższej klasyfikacji tych załączników|Wyłączone|
|Podaj niestandardowy adres URL strony sieci Web „Więcej informacji” klienta usługi Azure Information Protection|Pusty|


## <a name="default-policy-before-july-31-2017"></a>Domyślne zasady przed 31 lipca 2017 r.

Należy zauważyć, że opisy w tych zasadach odnoszą się do danych, które wymagają ochrony, jak również do śledzenia i odwoływania danych. Zasady nie konfigurują ochrony dla tych etykiet, więc musisz wykonać dodatkowe kroki w celu spełnienia wymagań tego opisu. Na przykład skonfiguruj etykietę tak, aby zastosować ochronę usług Azure RMS, lub użyj rozwiązania zapobiegającego utracie danych (DLP). Aby można było śledzenia i odwoływania dokumentu za pomocą witryny śledzenia dokumentów, dokument musi chronione przez usługę Azure RMS i śledzone przez osobę, która chronionego dokumentu. 


### <a name="labels"></a>Etykiety

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Osobiste|Dane niebiznesowe, tylko do użytku osobistego.|**Włączone**: Włączone <br /><br />**Kolor**: Jasnozielony<br /><br />**Oznaczenia wizualne**: Brak <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Publiczne|Dane biznesowe, które są specjalnie przygotowane i zatwierdzone do użytku publicznego.|**Włączone**: Włączone <br /><br />**Kolor**: Zielony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Ogólne|Dane biznesowe, które nie są przeznaczone do użytku publicznego. Jednak mogą one być udostępniane partnerom zewnętrznym w razie potrzeby. Do przykładów należą wewnętrzna książka telefoniczna firmy, schematy organizacyjne, standardy wewnętrzne i większość komunikacji wewnętrznej.|**Włączone**: Włączone <br /><br />**Kolor**: Niebieski <br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufne|Wrażliwe dane biznesowe, które mogą spowodować szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. Do przykładów należą kontrakty, raporty dotyczące zabezpieczeń, podsumowania prognoz i dane konta sprzedaży.|**Włączone**: Włączone <br /><br />**Kolor**: Pomarańczowy<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Wysoce poufne|Bardzo wrażliwe dane biznesowe, które spowodują szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. Do przykładów należą dane pracowników i klientów, hasła, kod źródłowy i wstępnie zapowiadane raporty finansowe.|**Włączone**: Włączone <br /><br />**Kolor**: Czerwony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|


### <a name="sub-labels"></a>Etykiety podrzędne

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Poufne\Wszyscy pracownicy|Dane poufne, które wymagają ochrony, możliwe do wyświetlenia przez wszystkich pracowników z pełnymi uprawnieniami. Właściciele danych mogą śledzić i odwoływać zawartość.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufne\Każdy (niechronione)|Dane, które nie wymagają ochrony. Używaj tej opcji z rozwagą w sytuacjach uzasadnionych potrzebami biznesowymi.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako poufne <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Wysoce poufne\Wszyscy pracownicy|Wysoce poufne dane, dla których wszyscy pracownicy mają uprawnienia do wyświetlania, edycji i udzielania odpowiedzi dla tej zawartości. Właściciele danych mogą śledzić i odwoływać zawartość.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako wysoce poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Wysoce poufne\Każdy (niechronione)|Dane, które nie wymagają ochrony. Używaj tej opcji z rozwagą w sytuacjach uzasadnionych potrzebami biznesowymi.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako wysoce poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|

### <a name="information-protection-bar"></a>Pasek usługi Information Protection

|Ustawienie|Wartość|
|-------------------------------|---------------------------|
|Tytuł|Czułość|
|Etykietka narzędzia|Bieżąca etykieta dla tej zawartości. To ustawienie umożliwia określenie ryzyka dla firmy, jeśli ta zawartość jest udostępniana nieuprawnionym osobom wewnątrz lub na zewnątrz organizacji.|


### <a name="settings"></a>Ustawienia

|Ustawienie|Wartość|
|-------------------------------|---------------------------|
|Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę (stosowaną automatycznie lub przez użytkowników)|Wyłączone|
|Wybierz etykietę domyślną|Brak|
|Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę|Wyłączone|
|W przypadku wiadomości e-mail z załącznikami należy stosować etykiety odpowiadające najwyższej klasyfikacji tych załączników|Wyłączone|
|Podaj niestandardowy adres URL strony sieci Web „Więcej informacji” klienta usługi Azure Information Protection|Pusty|

## <a name="default-policy-before-march-21-2017"></a>Zasady domyślne sprzed 21 marca 2017 r.

### <a name="labels"></a>Etykiety

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Osobiste|Wyłącznie do użytku osobistego. Te dane nie będą monitorowane przez organizację. Informacje osobiste nie mogą zawierać żadnych danych związanych z firmą.|**Włączone**: Włączone <br /><br />**Kolor**: Jasnozielony<br /><br />**Oznaczenia wizualne**: Brak <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Publiczne|Te informacje są informacjami wewnętrznymi. Mogą ich używać osoby wewnątrz firmy i poza nią.|**Włączone**: Włączone <br /><br />**Kolor**: Zielony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Wewnętrzne|Te informacje zawierają szerokie spektrum wewnętrznych danych firmowych, których mogą używać wszyscy pracownicy. Dane można udostępniać autoryzowanym klientom i partnerom biznesowym. Przykładami informacji wewnętrznych są zasady firmowe i większość komunikacji wewnętrznej.|**Włączone**: Włączone <br /><br />**Kolor**: Niebieski <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail): <br /><br />Ważność: Wewnętrzne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufne|Te dane zawierają poufne informacje biznesowe. Udostępnianie tych danych nieautoryzowanym użytkownikom może zaszkodzić organizacji. Przykładami informacji poufnych są informacje dotyczące pracowników, poszczególnych projektów lub umów z klientami oraz dane dotyczące konta sprzedaży.|**Włączone**: Włączone <br /><br />**Kolor**: Pomarańczowy<br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail):<br /><br /> Ważność: Poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Tajne|Te dane uwzględniają wysoce poufne informacje, które należy chronić w firmie. Udostępnianie danych tajnych nieautoryzowanym użytkownikom może poważnie zaszkodzić organizacji. Przykładami informacji tajnych są informacje umożliwiające identyfikację poszczególnych osób, rekordy klientów, kod źródłowy i wstępnie ogłoszone raporty finansowe.|**Włączone**: Włączone <br /><br />**Kolor**: Czerwony<br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail):<br /><br /> Ważność: Tajne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|


### <a name="sub-labels"></a>Etykiety podrzędne

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Tajne \ Cała firma|Te dane obejmują poufne informacje biznesowe, do których mają dostęp wszyscy pracownicy firmy.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Tajne \ Moja grupa|Te dane obejmują poufne informacje biznesowe, do których mają dostęp tylko grupy pracowników.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|

### <a name="information-protection-bar"></a>Pasek usługi Information Protection

|Ustawienie|Wartość|
|-------------------------------|---------------------------|
|Tytuł|Czułość|
|Etykietka narzędzia|Ważność informacji składa się z czterech różnych poziomów (Publiczne, Wewnętrzne, Poufne, Tajne), dzięki czemu użytkownik może zidentyfikować ryzyko ujawnienia informacji nieautoryzowanym użytkownikom wewnątrz firmy lub poza nią.|


### <a name="settings"></a>Ustawienia

|Ustawienie|Wartość|
|-------------------------------|---------------------------|
|Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę (stosowaną automatycznie lub przez użytkowników)|Wyłączone|
|Wybierz etykietę domyślną|Brak|
|Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę|Wyłączone|
|Podaj niestandardowy adres URL strony sieci Web „Więcej informacji” klienta usługi Azure Information Protection|Pusty|


## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]