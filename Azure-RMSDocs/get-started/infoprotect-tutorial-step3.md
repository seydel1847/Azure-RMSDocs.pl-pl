---
title: "Samouczek Szybki start — krok 3 — AIP"
description: "Krok 3 samouczka wprowadzającego, dzięki któremu można szybko wypróbować usługę Azure Information Protection — zainstalowanie klienta."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
ms.openlocfilehash: c3260d82c13c01bb16b22e472d57720777e82f7b
ms.sourcegitcommit: a4f4edcbf0f0a7de74d1dcec9ce6e661c6882a74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="step-3-install-the-client"></a>Krok 3. Zainstalowanie klienta

>*Dotyczy: Azure Information Protection*

W tym kroku nastąpi instalacja klienta usługi Azure Information Protection, dzięki czemu właśnie skonfigurowana zasada zostanie pobrana do komputera z systemem Windows i w aplikacjach pakietu Office zostaną wyświetlone etykiety.


## <a name="install-the-azure-information-protection-client"></a>Instalowanie klienta usługi Azure Information Protection

1. Na komputerze z zainstalowanym pakietem Office (program Word nie może obecnie otwarty), przejdź do [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) i Pobierz **AzInfoProtection.exe**. To jest wersja ogólnej dostępności klienta, który jest obsługiwany w sieciach produkcyjnych. Jednak jeśli wolisz spróbuj bieżąca wersja preview zawierającego wszystkie najnowsze funkcje i poprawki, Pobierz **AzInfoProtection_PREVIEW_1.10.52.0.exe**.
    
    Korzystania z danej wersji klienta, w tym samouczku, ale obrazy zgodna z wersją ogólnej dostępności i samouczek nie zawiera funkcje, które są nowe w wersji preview klienta.

2. Uruchom plik wykonywalny, który został pobrany i postępuj zgodnie z monitami, aby zainstalować klienta.

    W przypadku tego samouczka nie ma znaczenia, czy wybierzesz opcję instalacji zasady demonstracyjnej, ponieważ nasza właśnie skonfigurowana zasada zostanie pobrana z systemu Azure i zastąpi zasadę demonstracyjną, jeśli ją zainstalowano. Można jednak użyć opcji zasady demonstracyjnej, jeśli chcesz po prostu zapoznać się z etykietami domyślnymi bez nawiązywania połączenia z usługą Azure Information Protection. 

## <a name="verify-the-installation"></a>Weryfikacja instalacji

Sprawdź, czy instalacja zakończyła się pomyślnie, otwierając program Word i nowy pusty dokument (na tym etapie nie ma potrzeby jego zapisu). Jeśli zostanie wyświetlony monit, aby wprowadzić nazwę użytkownika i hasło, wprowadź szczegóły konta administratora globalnego. 

Jeśli klient został zainstalowany po raz pierwszy, wyświetlona zostanie strona **Gratulacje** z podstawowymi instrukcjami. Po ich przeczytaniu kliknij **Zamknij**.

Podczas ładowania dokumentu powinny zostać wyświetlone dwa nowe obiekty:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zainstalowany klient](../media/word2016-calloutsv2.png)

- Na karcie **Narzędzia główne**: nowa grupa **Ochrona** z przyciskiem **Chroń**.

    Kliknij przycisk **Chroń**  >  **Pomoc i opinie** i w oknie dialogowym **Microsoft Azure Information Protection** potwierdź swój status klienta. Powinna zostać wyświetlona informacja **Połączono jako** i nazwa użytkownika. Powinna także zostać wyświetlona godzina i data ostatniego połączenia oraz data instalacji zasad usługi Information Protection. Sprawdź, czy jest wyświetlana Twoja nazwa użytkownika odpowiednia dla Twojej dzierżawy.

- Pod wstążką jest wyświetlany nowy pasek o nazwie Information Protection. Wyświetla tytuł **czułości**i etykiety, które widzieliśmy w portalu Azure. 

Teraz możesz zobaczyć usługę Azure Information Protection w działaniu.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje o instalowaniu klienta usługi Azure Information Protection|[Pobieranie i instalowanie klienta usługi Azure Information Protection](../rms-client/install-client-app.md)|
|Instrukcje dla administratora dotyczące klienta usługi Azure Information Protection|[Podręcznik administratora klienta usługi Azure Information Protection](../rms-client/client-admin-guide.md)|


>[!div class="step-by-step"]
[&#171; Krok 2](infoprotect-tutorial-step2.md)
[Krok 4 &#187;](infoprotect-tutorial-step4.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]