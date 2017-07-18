---
title: "Konfigurowanie szablonów niestandardowych dla usługi Azure RMS — AIP"
description: "Informacje i instrukcje dla administratorów służące do konfigurowania szablonów praw użytkowania i zarządzania nimi. Szablony ułatwiają użytkownikom i innym administratorom stosowanie zasad umożliwiających dostęp do poufnych plików tylko autoryzowanym użytkownikom."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d141589c9dc9d90cf3a507db77f624c849f955b5
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="configuring-custom-templates-for-the-azure-rights-management-service"></a>Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

Po [aktywacji](activate-service.md) usługi Azure Rights Management użytkownicy automatycznie otrzymują możliwość korzystania z dwóch domyślnych szablonów ułatwiających stosowanie zasad zarządzania uprawnieniami, które ograniczają dostęp do poufnych plików do grona upoważnionych użytkowników w organizacji. Wspomniane dwa szablony obejmują następujące ograniczenia zasad praw:

-   Wyświetlanie chronionej zawartości w trybie tylko do odczytu

    -   Nazwa wyświetlana: **&lt;nazwa organizacji&gt; — tylko wgląd poufny**

    -   Określone uprawnienie: Wyświetl zawartość

-   Uprawnienia Odczyt lub Modyfikacja odnoszące się do chronionej zawartości

    -   Nazwa wyświetlana: **&lt;nazwa organizacji&gt; — poufne**

    -   Określone uprawnienia: Wyświetl zawartość, Zapisz plik, Edytuj zawartość, Wyświetl przypisane prawa, Zezwalaj na makra, Przekaż, Odpowiedz, Odpowiedz wszystkim

Ponadto [klient usługi Azure Information Protection](../rms-client/aip-client.md) umożliwia użytkownikom zdefiniowanie własnego zestawu uprawnień. W przypadku klienta programu Outlook i usługi Outlook Web Access użytkownicy mogą wybrać opcję [Nie przekazuj](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails).

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

> [!TIP]
> Szablony i nowe opcje dotyczące konfigurowania ochrony usługi Azure Rights Management są przenoszone do portalu Azure. Ta funkcja jest obecnie dostępna w wersji zapoznawczej. Aby uzyskać więcej informacji, zobacz następujące powiadomienie we wpisie na blogu: [Azure Information Protection unified administration now in Preview](https://blogs.technet.microsoft.com/enterprisemobility/2017/04/26/azure-information-protection-unified-administration-now-in-preview/) (Ujednolicona administracja usługą Azure Information Protection w wersji zapoznawczej) 


[!INCLUDE[Commenting house rules](../includes/houserules.md)]

