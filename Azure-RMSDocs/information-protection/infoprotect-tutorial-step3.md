---
title: "Samouczek Szybki start dla usługi Azure Information Protection, krok 3 | Azure Rights Management"
description: "Krok 3 samouczka wprowadzającego, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection dla swojej organizacji. Wystarczą 4 proste kroki, które powinny zająć mniej niż 15 minut."
author: cabailey
manager: mbaldwin
ms.date: 07/11/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: 7f85c673cd1e8055d6a27dcc49b5da18a7e12f98
ms.openlocfilehash: 41ebf56c55d94e9aecf9538d474c8fa2c77ae83e


---

# Krok 3: Zainstaluj klienta usługi Azure Information Protection 

*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

W tym kroku nastąpi instalacja klienta usługi Azure Information Protection, dzięki czemu właśnie skonfigurowana zasada zostanie pobrana do komputera z systemem Windows i w aplikacjach pakietu Office zostaną wyświetlone etykiety. 

1. Na komputerze z zainstalowanym pakietem Office (program Word nie może być otwarty) [pobierz klienta usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) z Centrum pobierania firmy Microsoft. 

2. Uruchom program **AZInfoProtection.exe** i postępuj zgodnie z monitami, aby zainstalować klienta.

    W przypadku tego samouczka nie ma znaczenia, czy wybierzesz opcję instalacji zasady demonstracyjnej, ponieważ nasza właśnie skonfigurowana zasada zostanie pobrana z systemu Azure i zastąpi zasadę demonstracyjną, jeśli ją zainstalowano. Można jednak użyć opcji zasady demonstracyjnej, jeśli chcesz po prostu zapoznać się z etykietami domyślnymi bez nawiązywania połączenia z usługą Azure Information Protection. 

3. Sprawdź, czy klient został zainstalowany, otwierając program Word i nowy pusty dokument (nie należy go w tym momencie zapisywać). Jeśli zostanie wyświetlony monit, aby wprowadzić nazwę użytkownika i hasło, wprowadź szczegóły konta administratora globalnego. Podczas ładowania dokumentu powinny zostać wyświetlone dwa nowe obiekty:

    - Na karcie **Narzędzia główne**: nowa grupa **Ochrona** z przyciskiem **Chroń**.

        Kliknij przycisk **Chroń**  >  **Pomoc i opinie** i w oknie dialogowym **Microsoft Azure Information Protection** potwierdź swój status klienta. Powinna zostać wyświetlona informacja **Zainstalowano zasadę Information Protection** i godzina ostatniego połączenia. Sprawdź, czy jest wyświetlana Twoja nazwa użytkownika odpowiednia dla Twojej dzierżawy.

    - Pod wstążką jest wyświetlany nowy pasek o nazwie Information Protection. Jest na nim wyświetlany tytuł **Ważność** i skonfigurowana przez nas etykieta domyślna **Wewnętrzne**. 


![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zainstalowany klient](../media/word2013-callouts.png)

Wszystko jest przygotowane do ostatniego kroku, w którym przekonamy się, jak działają funkcje klasyfikowania, etykietowania i ochrony.

>[!div class="step-by-step"]
[&#171; Krok 2](infoprotect-tutorial-step2.md)
[Krok 4 &#187;](infoprotect-tutorial-step4.md)


<!--HONumber=Jul16_HO3-->

