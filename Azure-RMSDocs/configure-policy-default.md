---
title: Zasady domyślne dla usługi Azure Information Protection
description: Dowiedz się, w jaki sposób są skonfigurowane domyślne zasady usługi Azure Information Protection. Jeśli zmodyfikujesz zasady domyślne, możesz odnieść się do tych wartości, aby przywrócić wartości domyślne zasad.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.openlocfilehash: d74dfcd35dca2f3ab5e88a66eaaba37b13636e4d
ms.sourcegitcommit: fa0be701b85b1fba5e75428714bb4525dd739a93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223980"
---
# <a name="the-default-azure-information-protection-policy"></a>Domyślne zasady usługi Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Skorzystaj z poniższych informacji, aby poznać, jak są skonfigurowane domyślne zasady usługi Azure Information Protection.

Gdy administrator najpierw łączy się z usługą Azure Information Protection przy użyciu witryny Azure portal, domyślne zasady usługi Azure Information Protection dla tej dzierżawy jest tworzony. Od czasu do czasu Microsoft może wprowadzić zmiany w tym zasady domyślne, ale jeśli usługa była już używana, przed zmianą zasad domyślnych, poprzednia wersja zasad domyślnych usługi Azure Information Protection nie zostanie zaktualizowany, ponieważ może być skonfigurowane i wdrożone w środowisku produkcyjnym.

Możesz odwoływać się następujące wartości, aby przywrócić ustawienia domyślne zasady usługi Azure Information Protection lub aktualizacji zasad usługi Azure Information Protection do najnowszych wartości.

## <a name="current-default-policy"></a>Bieżące zasady domyślne

Ta wersja domyślne zasady usługi Azure Information Protection jest od 31 lipca 2017 r.

Utworzono zasadę domyślną usługi Azure Information Protection, po aktywowaniu usługi Azure Rights Management, co ma miejsce dla nowych dzierżaw, począwszy od lutego 2018 r. Aby uzyskać więcej informacji, zobacz wpis na blogu [ulepszenia ochrony stosu usługi Azure Information Protection](https://cloudblogs.microsoft.com/enterprisemobility/2018/03/08/improvements-to-the-protection-stack-in-azure-information-protection).

Zasadę domyślną usługi Azure Information Protection jest tworzona, jeśli trzeba ręcznie [aktywacji usługi](activate-service.md) przed usługi Azure Information Protection zasady zostały utworzone. 

Jeśli usługa nie została aktywowana, domyślne zasady usługi Azure Information Protection nie konfiguruje ochronę następujących etykiet podrzędnych:

- **Poufne\Wszyscy pracownicy**

- **Poufne \ tylko adresaci**

- **Wysoce poufne\Wszyscy pracownicy** 

- **Wysoce poufne \ tylko adresaci** 

Podczas tych etykiet podrzędnych nie są automatycznie skonfigurowany do ochrony, domyślne zasady usługi Azure Information Protection pozostaje taka sama jak [poprzednie zasady domyślne](#default-policy-before-july-31-2017).

Gdy ochrona jest stosowana do **wszyscy pracownicy** etykiet podrzędnych, ochrona jest konfigurowana przy użyciu szablonów domyślnych, które są automatycznie konwertowane do etykiet w witrynie Azure portal. Aby uzyskać więcej informacji na temat tych szablonów, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md).

Począwszy od 30 sierpnia 2017 r. Ta wersja domyślne zasady usługi Azure Information Protection zawiera wersje wielojęzycznych nazwy etykiet i opisy. 

#### <a name="more-information-about-the-recipients-only-sublabel"></a>Więcej informacji na temat etykietę podrzędną tylko adresaci

Użytkownicy widzą tę etykietę tylko w programie Outlook. Ta etykieta w programie Word, Excel, PowerPoint lub Eksploratora plików nie jest widoczna. 

Gdy użytkownicy wybiorą etykietę, opcję programu Outlook nie przesyłaj dalej jest automatycznie stosowana do wiadomości e-mail. Adresatów, którzy użytkownicy określić nie może przesłać wiadomości e-mail i nie można skopiować Drukuj zawartość lub zapisuje żadnych załączników.


### <a name="labels"></a>Etykiety

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Osobiste|Dane niebiznesowe, tylko do użytku osobistego.|**Włączone**: Włączone <br /><br />**Kolor**: Jasnozielony<br /><br />**Oznaczenia wizualne**: Brak <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Public|Dane biznesowe, które są specjalnie przygotowane i zatwierdzone do użytku publicznego.|**Włączone**: Włączone <br /><br />**Kolor**: Zielony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Ogólne|Dane biznesowe, które nie są przeznaczone do użytku publicznego. Jednak mogą one być udostępniane partnerom zewnętrznym w razie potrzeby. Do przykładów należą wewnętrzna książka telefoniczna firmy, schematy organizacyjne, standardy wewnętrzne i większość komunikacji wewnętrznej.|**Włączone**: Włączone <br /><br />**Kolor**: Niebieski <br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufne|Wrażliwe dane biznesowe, które mogą spowodować szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. Do przykładów należą kontrakty, raporty dotyczące zabezpieczeń, podsumowania prognoz i dane konta sprzedaży.|**Włączone**: Włączone <br /><br />**Kolor**: Pomarańczowy<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Wysoce poufne|Bardzo wrażliwe dane biznesowe, które spowodują szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. Do przykładów należą dane pracowników i klientów, hasła, kod źródłowy i wstępnie zapowiadane raporty finansowe.|**Włączone**: Włączone <br /><br />**Kolor**: Czerwony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|


### <a name="sublabels"></a>Etykiet podrzędnych

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Poufne\Wszyscy pracownicy|Dane poufne, które wymagają ochrony, możliwe do wyświetlenia przez wszystkich pracowników z pełnymi uprawnieniami. Właściciele danych mogą śledzić i odwoływać zawartość.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Azure (klucz w chmurze) [[1]](#footnote-1)|
|Poufne\Każdy (niechronione)|Dane, które nie wymagają ochrony. Używaj tej opcji z rozwagą w sytuacjach uzasadnionych potrzebami biznesowymi.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako poufne <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufne \ tylko adresaci|Poufne dane, które wymagają ochrony i mogą być wyświetlane tylko przez adresatów.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (adres e-mail)<br /><br />Sklasyfikowane jako poufne <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Ustaw uprawnienia zdefiniowane przez użytkownika (wersja zapoznawcza) w programie Outlook Zastosuj nie przesyłaj dalej|
|Wysoce poufne\Wszyscy pracownicy|Wysoce poufne dane, dla których wszyscy pracownicy mają uprawnienia do wyświetlania, edycji i udzielania odpowiedzi dla tej zawartości. Właściciele danych mogą śledzić i odwoływać zawartość.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako wysoce poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Azure (klucz w chmurze) [[2]](#footnote-2)|
|Wysoce poufne\Każdy (niechronione)|Dane, które nie wymagają ochrony. Używaj tej opcji z rozwagą w sytuacjach uzasadnionych potrzebami biznesowymi.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />Sklasyfikowane jako wysoce poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Wysoce poufne \ tylko adresaci|Wysoce poufne dane, które wymagają ochrony i mogą być wyświetlane tylko przez adresatów.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Stopka (adres e-mail)<br /><br />Sklasyfikowane jako wysoce poufne <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Ustaw uprawnienia zdefiniowane przez użytkownika (wersja zapoznawcza) w programie Outlook Zastosuj nie przesyłaj dalej|

###### <a name="footnote-1"></a>Przypis 1
Uprawnienia ochrony odpowiadają [szablonu domyślnego](configure-policy-templates.md#default-templates), **poufne \ wszyscy pracownicy**.

###### <a name="footnote-2"></a>Przypis 2 
Uprawnienia ochrony odpowiadają [szablonu domyślnego](configure-policy-templates.md#default-templates), **wysoce poufne \ wszyscy pracownicy**.


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


## <a name="default-policy-before-july-31-2017"></a>Zasady domyślne sprzed 31 lipca 2017 r.

Należy zauważyć, że opisy w tych zasadach odnoszą się do danych, które wymagają ochrony, jak również do śledzenia i odwoływania danych. Zasady nie konfigurują ochrony dla tych etykiet, więc musisz wykonać dodatkowe kroki w celu spełnienia wymagań tego opisu. Na przykład skonfigurować etykietę do stosowania ochrony lub przy użyciu rozwiązania zapobieganie utracie danych. Zanim można będzie śledzić i odwoływać dokument za pomocą witryny śledzenia dokumentów, dokument musi chronione przez usługę Azure Rights Management i śledzone przez osobę, która dokument został objęty ochroną. 


### <a name="labels"></a>Etykiety

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Osobiste|Dane niebiznesowe, tylko do użytku osobistego.|**Włączone**: Włączone <br /><br />**Kolor**: Jasnozielony<br /><br />**Oznaczenia wizualne**: Brak <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Public|Dane biznesowe, które są specjalnie przygotowane i zatwierdzone do użytku publicznego.|**Włączone**: Włączone <br /><br />**Kolor**: Zielony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Ogólne|Dane biznesowe, które nie są przeznaczone do użytku publicznego. Jednak mogą one być udostępniane partnerom zewnętrznym w razie potrzeby. Do przykładów należą wewnętrzna książka telefoniczna firmy, schematy organizacyjne, standardy wewnętrzne i większość komunikacji wewnętrznej.|**Włączone**: Włączone <br /><br />**Kolor**: Niebieski <br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufne|Wrażliwe dane biznesowe, które mogą spowodować szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. Do przykładów należą kontrakty, raporty dotyczące zabezpieczeń, podsumowania prognoz i dane konta sprzedaży.|**Włączone**: Włączone <br /><br />**Kolor**: Pomarańczowy<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Wysoce poufne|Bardzo wrażliwe dane biznesowe, które spowodują szkody w działalności firmy, jeśli zostaną udostępnione nieuprawnionym osobom. Do przykładów należą dane pracowników i klientów, hasła, kod źródłowy i wstępnie zapowiadane raporty finansowe.|**Włączone**: Włączone <br /><br />**Kolor**: Czerwony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|


### <a name="sublabels"></a>Etykiet podrzędnych

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
|Public|Te informacje są informacjami wewnętrznymi. Mogą ich używać osoby wewnątrz firmy i poza nią.|**Włączone**: Włączone <br /><br />**Kolor**: Zielony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Wewnętrzne|Te informacje zawierają szerokie spektrum wewnętrznych danych firmowych, których mogą używać wszyscy pracownicy. Dane można udostępniać autoryzowanym klientom i partnerom biznesowym. Przykładami informacji wewnętrznych są zasady firmowe i większość komunikacji wewnętrznej.|**Włączone**: Włączone <br /><br />**Kolor**: Niebieski <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail): <br /><br />Ważność: Wewnętrzne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufne|Te dane zawierają poufne informacje biznesowe. Udostępnianie tych danych nieautoryzowanym użytkownikom może zaszkodzić organizacji. Przykładami informacji poufnych są informacje dotyczące pracowników, poszczególnych projektów lub umów z klientami oraz dane dotyczące konta sprzedaży.|**Włączone**: Włączone <br /><br />**Kolor**: Pomarańczowy<br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail):<br /><br /> Ważność: Poufne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Tajne|Te dane uwzględniają wysoce poufne informacje, które należy chronić w firmie. Udostępnianie danych tajnych nieautoryzowanym użytkownikom może poważnie zaszkodzić organizacji. Przykładami informacji tajnych są informacje umożliwiające identyfikację poszczególnych osób, rekordy klientów, kod źródłowy i wstępnie ogłoszone raporty finansowe.|**Włączone**: Włączone <br /><br />**Kolor**: Czerwony<br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail):<br /><br /> Ważność: Tajne<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|


### <a name="sublabels"></a>Etykiet podrzędnych

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


## <a name="next-steps"></a>Kolejne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy). 
