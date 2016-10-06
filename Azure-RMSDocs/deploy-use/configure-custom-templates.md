---
title: "Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management | Azure Information Protection"
description: "Informacje i instrukcje dla administratorów służące do konfigurowania szablonów praw użytkowania i zarządzania nimi. Szablony ułatwiają użytkownikom i innym administratorom stosowanie zasad umożliwiających dostęp do poufnych plików tylko autoryzowanym użytkownikom."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d5b6a1fc3fa0a19f3a6b65aa7b8815eda7432cd7
ms.openlocfilehash: d8db7f0346fad1b9c46423875d1e559d41987686


---

# Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

Po [aktywacji](activate-service.md) usługi Azure Rights Management użytkownicy automatycznie otrzymują możliwość korzystania z dwóch domyślnych szablonów ułatwiających stosowanie zasad zarządzania uprawnieniami, które ograniczają dostęp do poufnych plików do grona upoważnionych użytkowników w organizacji. Wspomniane dwa szablony obejmują następujące ograniczenia zasad praw:

-   Wyświetlanie chronionej zawartości w trybie tylko do odczytu

    -   Nazwa wyświetlana: **&lt;nazwa organizacji&gt; — tylko wgląd poufny**

    -   Określone uprawnienie: Wyświetl zawartość

-   Uprawnienia Odczyt lub Modyfikacja odnoszące się do chronionej zawartości

    -   Nazwa wyświetlana: **&lt;nazwa organizacji&gt; — poufne**

    -   Określone uprawnienia: Wyświetl zawartość, Zapisz plik, Edytuj zawartość, Wyświetl przypisane prawa, Zezwalaj na makra, Przekaż, Odpowiedz, Odpowiedz wszystkim

Ponadto [aplikacja do udostępniania usług RMS](../rms-client/sharing-app-windows.md) pozwala użytkownikom na definiowanie własnych zestawów uprawnień. W przypadku klienta programu Outlook i usługi Outlook Web Access użytkownicy mogą wybrać opcję [Nie przekazuj](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails).

W przypadku wielu organizacji domyślne szablony są wystarczające. Użytkownicy mogą jednak także tworzyć własne, niestandardowe szablony zasad praw. Poniżej przedstawiono okoliczności, które mogą sprzyjać tworzeniu szablonów niestandardowych:

-   Użytkownik chce, aby szablon przyznał prawa osobom należącym do określonej grupy członków organizacji, a nie wszystkim użytkownikom.

-   Użytkownik chce, aby wyświetlać i wybierać szablon (szablon dla działu) z poziomu aplikacji mogła tylko określona grupa użytkowników należących do organizacji, a nie wszyscy użytkownicy w jej obrębie.

-   Użytkownik chce zdefiniować niestandardowe prawa dla szablonu, np. Wyświetl i Edytuj, ale nie Kopiuj i Drukuj.

-   Użytkownik chce skonfigurować dodatkowe opcje w szablonie, które obejmują datę wygaśnięcia i to, czy do zawartości można uzyskać dostęp bez połączenia z Internetem.

Aby użytkownicy mogli wybrać szablon niestandardowy, który zawiera ustawienia takie jak te, należy najpierw utworzyć szablon niestandardowy, skonfigurować go, a następnie opublikować. Prawdopodobnie będziesz potrzebować tylko kilka szablonów, ale można mieć maksymalnie 500 szablonów niestandardowych zapisanych na platformie Azure. 

Poniższe informacje pozwalają skonfigurować szablony niestandardowe i zarządzać nimi:

-   [Tworzenie, konfiguracja i publikacja szablonu niestandardowego](create-template.md)

-   [Kopiowanie szablonu](copy-template.md)

-   [Usuwanie (archiwizacja) szablonu](remove-template.md)

-   [Odświeżanie szablonów dla użytkowników](refresh-templates.md)

-   [Zarządzanie szablonami za pomocą programu PowerShell](configure-templates-with-powershell.md)





<!--HONumber=Sep16_HO4-->


