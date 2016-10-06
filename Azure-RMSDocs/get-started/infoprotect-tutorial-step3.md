---
title: Samouczek Szybki start krok 3 | Azure Information Protection
description: "Krok 3 samouczka wprowadzającego, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection w swojej organizacji. Wystarczy około 30 minut."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: b5c87669c965d1e67b47dcfbd8ba97f1da41d104
ms.openlocfilehash: 042e168452d2b5cbc1eeec4fc06a3b0f137a5caf


---

# Krok 3. Instalowanie klienta i aplikacji 

>*Dotyczy: Azure Information Protection*

W tym kroku nastąpi najpierw instalacja klienta usługi Azure Information Protection, dzięki czemu właśnie skonfigurowana zasada zostanie pobrana do komputera z systemem Windows i w aplikacjach pakietu Office zostaną wyświetlone etykiety.

Następnie nastąpi instalacja aplikacji RMS sharing umożliwiającej bezpieczne udostępnianie dokumentów pocztą e-mail oraz śledzenie ich wykorzystania. 

Obie te instalacje integrują się z aplikacjami pakietu Office i obecnie konieczna jest ich oddzielna instalacja.


## Instalowanie klienta usługi Azure Information Protection

1. Na komputerze z zainstalowanym pakietem Office (program Word nie może być otwarty) [pobierz klienta usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) z Centrum pobierania firmy Microsoft. 

2. Uruchom plik **AzInfoProtection.exe** i postępuj zgodnie z monitami, aby zainstalować klienta.

    W przypadku tego samouczka nie ma znaczenia, czy wybierzesz opcję instalacji zasady demonstracyjnej, ponieważ nasza właśnie skonfigurowana zasada zostanie pobrana z systemu Azure i zastąpi zasadę demonstracyjną, jeśli ją zainstalowano. Można jednak użyć opcji zasady demonstracyjnej, jeśli chcesz po prostu zapoznać się z etykietami domyślnymi bez nawiązywania połączenia z usługą Azure Information Protection. 

## Instalowanie aplikacji RMS sharing 

1. Przejdź do strony usługi [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) w witrynie firmy Microsoft w sieci Web.

2. W sekcji **Komputery** kliknij ikonę **aplikacji RMS dla systemu Windows** i zapisz plik **Setup.exe**, aby zainstalować aplikację do udostępniania usługi Microsoft Rights Management.

3. Na stronie **Instalacja usług Microsoft RMS** kliknij pozycję **Dalej** i poczekaj na zakończenie instalacji. Następnie kliknij pozycję **Uruchom ponownie**, jeśli zostanie wyświetlony monit o ponowne uruchomienie komputera, lub kliknij pozycję **Zamknij** w celu zakończenia instalacji.


## Sprawdź instalacje

Sprawdź, czy instalacje zakończyły się pomyślnie, otwierając program Word i nowy pusty dokument (nie należy go w tym momencie zapisywać). Jeśli zostanie wyświetlony monit, aby wprowadzić nazwę użytkownika i hasło, wprowadź szczegóły konta administratora globalnego. 

Podczas ładowania dokumentu powinny zostać wyświetlone trzy nowe obiekty:

- Na karcie **Narzędzia główne**: nowa grupa **Ochrona** z przyciskiem **Chroń**.

    Kliknij przycisk **Chroń**  >  **Pomoc i opinie** i w oknie dialogowym **Microsoft Azure Information Protection** potwierdź swój status klienta. Powinna zostać wyświetlona informacja **Zainstalowano zasadę Information Protection** i godzina ostatniego połączenia. Sprawdź, czy jest wyświetlana Twoja nazwa użytkownika odpowiednia dla Twojej dzierżawy.

- Także na karcie **Narzędzia główne**: nowa grupa **RMS** z przyciskiem **Udostępnij chronioną zawartość**.

- Pod wstążką jest wyświetlany nowy pasek o nazwie Information Protection. Jest na nim wyświetlany tytuł **Ważność** i skonfigurowana przez nas etykieta domyślna **Wewnętrzne**. 
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zainstalowany klient](../media/word2013-callouts2.png)

Teraz możesz zobaczyć usługę Azure Information Protection w działaniu.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje o instalowaniu klienta usługi Azure Information Protection|[Instalowanie klienta usługi Azure Information Protection](../rms-client/info-protect-client.md)|
|Informacje dotyczące instalowania aplikacji RMS sharing i instrukcje dla użytkowników|[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-user-guide.md)|
|Informacje dotyczące skryptowej instalacji aplikacji do udostępniania usługi Rights Management dla systemu Windows i dodatkowe informacje techniczne|[Przewodnik administratora aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-admin-guide.md)|


>[!div class="step-by-step"]
[&#171; Krok 2](infoprotect-tutorial-step2.md)
[Krok 4 &#187;](infoprotect-tutorial-step4.md)


<!--HONumber=Sep16_HO4-->


