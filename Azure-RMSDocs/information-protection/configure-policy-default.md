---
title: "Domyślne zasady usługi Azure Information Protection | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/21/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 977cbf2f45cab75aaca9c2a16dd1564c2af2fe4a


---

# Domyślne zasady usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Skorzystaj z poniższych informacji, aby poznać, jak są skonfigurowane domyślne zasady usługi Azure Information Protection. Jeśli zmodyfikujesz zasady domyślne, możesz odnieść się do tych wartości, aby przywrócić wartości domyślne zasad.

## Pasek usługi Information Protection

Tytuł: **Ważność**

Etykietka narzędzia: **Ważność informacji składa się z czterech różnych poziomów (Publiczne, Wewnętrzne, Poufne, Tajne), dzięki czemu użytkownik może zidentyfikować ryzyko ujawnienia informacji nieautoryzowanym użytkownikom wewnątrz firmy lub poza nią.**


## Etykiety

Istnieje 5 etykiet domyślnych o następujących ustawieniach:

### **Osobiste**

Etykietka narzędzia: **Wyłącznie do użytku osobistego. Te dane nie będą monitorowane przez organizację. Informacje osobiste nie mogą zawierać żadnych danych związanych z firmą.**

Kolor: Jasnozielony

Oznaczenia wizualne: Brak

Warunki: Brak

Ochrona: Nie

----


### **Publiczne**

Etykietka narzędzia: **Te informacje są informacjami wewnętrznymi. Mogą ich używać osoby wewnątrz firmy i poza nią.**

Kolor: Zielony

Oznaczenia wizualne: Brak

Warunki: Brak

Ochrona: Nie

----

### **Wewnętrzne**

Etykietka narzędzia: **Te informacje zawierają szerokie spektrum wewnętrznych danych firmowych, których mogą używać wszyscy pracownicy. Dane można udostępniać autoryzowanym klientom i partnerom biznesowym. Przykładami informacji wewnętrznych są zasady firmowe i większość komunikacji wewnętrznej.**

Kolor: Niebieski

Oznaczenia wizualne: Stopka (dokument i wiadomość e-mail)

Warunki: Brak

Ochrona: Nie

----

### **Poufne**

Etykietka narzędzia: **Te dane zawierają poufne informacje biznesowe. Udostępnianie tych danych nieautoryzowanym użytkownikom może zaszkodzić organizacji. Przykładami informacji poufnych są informacje dotyczące pracowników, poszczególnych projektów lub umów z klientami oraz dane dotyczące konta sprzedaży.**

Kolor: Pomarańczowy

Oznaczenia wizualne: Stopka (dokument i wiadomość e-mail)

Warunki: Brak

Ochrona: Nie

----

### **Tajne**

Etykietka narzędzia: **Te dane uwzględniają wysoce poufne informacje, które należy chronić w firmie. Udostępnianie danych tajnych nieautoryzowanym użytkownikom może poważnie zaszkodzić organizacji. Przykładami tajnych informacji są informacje umożliwiające identyfikację poszczególnych osób, rekordy klientów, kod źródłowy i wstępnie ogłoszone raporty finansowe.**

Kolor: Czerwony

Oznaczenia wizualne: Stopka (dokument i wiadomość e-mail)

Warunki: Brak

Ochrona: Nie

----


## Etykiety podrzędne

Istnieją 2 domyślne etykiety podrzędne o następujących ustawieniach:

### Tajne > **Cała firma**

Etykietka narzędzia: **Te dane obejmują poufne informacje biznesowe, do których mają dostęp wszyscy pracownicy firmy.**

Oznaczenia wizualne: Brak

Warunki: Brak

Ochrona: Nie

----

### Tajne > **Moja grupa**

Etykietka narzędzia: **Te dane obejmują poufne informacje biznesowe, do których mają dostęp tylko grupy pracowników.**

Oznaczenia wizualne: Brak

Warunki: Brak

Ochrona: Nie

## Ustawienia globalne

**Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę (stosowaną automatycznie lub przez użytkowników)**: Wył.

**Wybierz etykietę domyślną**: Brak

**Użytkownicy muszą uzasadniać obniżenie charakterystyki (np. z Poufne na Publiczne)**: Wył.

## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy). 



<!--HONumber=Jul16_HO5-->


