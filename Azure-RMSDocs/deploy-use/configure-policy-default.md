---
title: "Zasady domyślne dla usługi Azure Information Protection"
description: "Dowiedz się, w jaki sposób są skonfigurowane domyślne zasady usługi Azure Information Protection. Jeśli zmodyfikujesz zasady domyślne, możesz odnieść się do tych wartości, aby przywrócić wartości domyślne zasad."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
ms.openlocfilehash: 3a2c5af41023021893f0eb751321e798ea523e8c
ms.sourcegitcommit: d5ce1bce5e63b3e510033ff9d4d246dd3511ed7c
translationtype: HT
---
# <a name="the-default-azure-information-protection-policy"></a>Domyślne zasady usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Skorzystaj z poniższych informacji, aby poznać, jak są skonfigurowane domyślne zasady usługi Azure Information Protection. Jeśli zmodyfikujesz zasady domyślne, możesz odnieść się do tych wartości, aby przywrócić wartości domyślne zasad.


## <a name="information-protection-bar"></a>Pasek usługi Information Protection

|Ustawienie|Wartość|
|-------------------------------|---------------------------|
|Tytuł|Czułość|
|Etykietka narzędzia|Ważność informacji składa się z czterech różnych poziomów (Publiczne, Wewnętrzne, Poufne, Tajne), dzięki czemu użytkownik może zidentyfikować ryzyko ujawnienia informacji nieautoryzowanym użytkownikom wewnątrz firmy lub poza nią.|

## <a name="labels"></a>Etykiety

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Osobiste|Wyłącznie do użytku osobistego. Te dane nie będą monitorowane przez organizację. Informacje osobiste nie mogą zawierać żadnych danych związanych z firmą.|**Włączone**: Włączone <br /><br />**Kolor**: Jasnozielony<br /><br />**Oznaczenia wizualne**: Brak <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Publiczne|Te informacje są informacjami wewnętrznymi. Mogą ich używać osoby wewnątrz firmy i poza nią.|**Włączone**: Włączone <br /><br />**Kolor**: Zielony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Wewnętrzne|Te informacje zawierają szerokie spektrum wewnętrznych danych firmowych, których mogą używać wszyscy pracownicy. Dane można udostępniać autoryzowanym klientom i partnerom biznesowym. Przykładami informacji wewnętrznych są zasady firmowe i większość komunikacji wewnętrznej.|**Włączone**: Włączone <br /><br />**Kolor**: Niebieski <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Poufne|Te dane zawierają poufne informacje biznesowe. Udostępnianie tych danych nieautoryzowanym użytkownikom może zaszkodzić organizacji. Przykładami informacji poufnych są informacje dotyczące pracowników, poszczególnych projektów lub umów z klientami oraz dane dotyczące konta sprzedaży.|**Włączone**: Włączone <br /><br />**Kolor**: Pomarańczowy<br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Tajne|Te dane uwzględniają wysoce poufne informacje, które należy chronić w firmie. Udostępnianie danych tajnych nieautoryzowanym użytkownikom może poważnie zaszkodzić organizacji. Przykładami informacji tajnych są informacje umożliwiające identyfikację poszczególnych osób, rekordy klientów, kod źródłowy i wstępnie ogłoszone raporty finansowe.|**Włączone**: Włączone <br /><br />**Kolor**: Czerwony<br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|

## <a name="sub-labels"></a>Etykiety podrzędne

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Tajne \ Cała firma|Te dane obejmują poufne informacje biznesowe, do których mają dostęp wszyscy pracownicy firmy.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|
|Tajne \ Moja grupa|Te dane obejmują poufne informacje biznesowe, do których mają dostęp tylko grupy pracowników.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Brak|

## <a name="global-settings"></a>Ustawienia globalne

|Ustawienie|Wartość|
|-------------------------------|---------------------------|
|Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę (stosowaną automatycznie lub przez użytkowników)|Wyłączone|
|Wybierz etykietę domyślną|Brak|
|Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę|Wyłączone|


## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]