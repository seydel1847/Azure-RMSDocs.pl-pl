---
# required metadata

title: Omówienie | Azure RMS
description: Usługi Rights Management (RMS) to technologia ochrony informacji, która pomaga w zabezpieczaniu informacji cyfrowych przed nieautoryzowanym użyciem.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: B546B6C1-ADC1-4EBD-95E2-B4A74E4E980B
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Przegląd

Usługi Rights Management (RMS) to technologia ochrony informacji, która pomaga w zabezpieczaniu informacji cyfrowych przed nieautoryzowanym użyciem. Przy użyciu aplikacji obsługujących prawa właściciele zawartości mogą zdefiniować użytkowników, którzy mogą otwierać, modyfikować, drukować i przekazywać zawartość oraz podejmować inne związane z nią działania.

## Przegląd

W usługach AD RMS uwzględniono składniki [serwera](ad-rms-server.md) i [klienta](ad-rms-client.md). Składnik serwera działający na platformie Azure lub w systemie Windows Server zawiera wiele usług sieci Web.

Składnik [klienta](ad-rms-client.md) może działać w systemie operacyjnym klienta lub serwera i zawiera funkcje umożliwiające aplikacji szyfrowanie i odszyfrowywanie zawartości, pobieranie szablonów i list odwołania, uzyskiwanie licencji i certyfikatów z serwera oraz wykonywanie innych zadań związanych z zarządzaniem prawami.

Aby uzyskać więcej informacji, zobacz temat [Typy aplikacji](application-types.md).

Poniżej przedstawiono kilka scenariuszy, w których można stosować aplikacje utworzone przy użyciu zestawu Rights Management Services SDK 2.1.

-   Kancelaria prawna chce zapobiec drukowaniu i przekazywaniu dalej poufnych wiadomości e-mail.
-   Deweloperzy oprogramowania CAD i oprogramowania produkcyjnego chcą ograniczyć dostęp do rysunków do niewielkiej grupy użytkowników z działu badawczego bez konieczności korzystania z haseł.
-   Właściciele witryny internetowej dotyczącej projektów graficznych chcą korzystać z pojedynczej licencji, która umożliwia bezpłatne wyświetlanie kopii obrazów w niskiej rozdzielczości, ale wymaga opłaty w celu uzyskania dostępu do wersji o wysokiej rozdzielczości.
-   Właściciele biblioteki dokumentów online chcą włączyć prawa do wyświetlania, drukowania i edycji dokumentów na podstawie tożsamości użytkownika.
-   Firma chce publikować poufne informacje o pracownikach w wewnętrznej witrynie sieci Web, która ogranicza uprawnienia do wyświetlania i edycji do określonych użytkowników.

Aby uzyskać więcej informacji na temat serwera usług AD RMS, klienta usług AD RMS i ich funkcji, zobacz zawartość TechNet dotyczącą [dokumentacji usług AD RMS dla specjalistów IT](https://TechNet.Microsoft.Com/en-us/library/cc771234.aspx).

Pozostałe tematy w tej sekcji dotyczą architektury usług RMS i ich implementacji.

## W tej sekcji

| Temat | Opis |
|-------|-------------|
|[Klient](ad-rms-client.md) |W tym temacie opisano przeznaczenie i funkcję klienta Rights Management Services Client 2.1 |
|[Serwer](ad-rms-server.md) | W tym temacie opisano przeznaczenie i funkcje serwera usług RMS na potrzeby platformy Azure i systemu Windows Server.|


## Tematy pokrewne

* [Koncepcje związane z usługami RMS](application-types.md)
* [Wprowadzenie](getting-started-with-ad-rms-2-0.md)
* [Dokumentacja usług AD RMS dla specjalistów IT](https://TechNet.Microsoft.Com/en-us/library/cc771234.aspx)
 

 


<!--HONumber=Jun16_HO2-->

