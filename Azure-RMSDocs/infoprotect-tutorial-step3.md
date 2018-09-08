---
title: Samouczek Szybki start — krok 3 — AIP
description: Krok 3 samouczka wprowadzającego, dzięki któremu można szybko wypróbować usługę Azure Information Protection — zainstalowanie klienta.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/28/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
ms.openlocfilehash: 203964dfb153b45c515fa93c8cb6b69ebe3fbd37
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151643"
---
# <a name="step-3-install-the-client"></a>Krok 3. Zainstalowanie klienta

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

W tym kroku nastąpi instalacja klienta usługi Azure Information Protection, dzięki czemu właśnie skonfigurowana zasada zostanie pobrana do komputera z systemem Windows i w aplikacjach pakietu Office zostaną wyświetlone etykiety.


## <a name="install-the-azure-information-protection-client"></a>Instalowanie klienta usługi Azure Information Protection

1. Na komputerze z zainstalowanym pakietem Office (ale nie jest obecnie otwarty program Word), przejdź do [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) i Pobierz **AzInfoProtection.exe**.
    
2. Uruchom plik wykonywalny, który został pobrany właśnie i postępuj zgodnie z monitami, aby zainstalować klienta.
    
    W przypadku tego samouczka nie ma znaczenia, czy wybierzesz opcję instalacji zasady demonstracyjnej, ponieważ nasza właśnie skonfigurowana zasada zostanie pobrana z systemu Azure i zastąpi zasadę demonstracyjną, jeśli ją zainstalowano. Można jednak użyć opcji zasady demonstracyjnej, jeśli chcesz po prostu zapoznać się z etykietami domyślnymi bez nawiązywania połączenia z usługą Azure Information Protection. 

## <a name="verify-the-installation"></a>Weryfikacja instalacji

Sprawdź, czy instalacja zakończyła się pomyślnie, otwierając program Word i nowy pusty dokument (na tym etapie nie ma potrzeby jego zapisu). Jeśli zostanie wyświetlony monit, aby wprowadzić nazwę użytkownika i hasło, wprowadź szczegóły konta administratora globalnego. 

Jeśli klient został zainstalowany po raz pierwszy, wyświetlona zostanie strona **Gratulacje** z podstawowymi instrukcjami. Po ich przeczytaniu kliknij **Zamknij**.

Podczas ładowania dokumentu powinny zostać wyświetlone dwa nowe obiekty:

![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zainstalowany klient](./media/word2016-calloutsv2.png)

- Na karcie **Narzędzia główne**: nowa grupa **Ochrona** z przyciskiem **Chroń**.
    
    Kliknij przycisk **Chroń**  >  **Pomoc i opinie** i w oknie dialogowym **Microsoft Azure Information Protection** potwierdź swój status klienta. Powinna zostać wyświetlona informacja **Połączono jako** i nazwa użytkownika. Powinna także zostać wyświetlona godzina i data ostatniego połączenia oraz data instalacji zasad usługi Information Protection. Sprawdź, czy jest wyświetlana Twoja nazwa użytkownika odpowiednia dla Twojej dzierżawy.

- Pod wstążką jest wyświetlany nowy pasek o nazwie Information Protection. Wyświetla tytuł **czułości**i etykiety, które widzieliśmy w witrynie Azure portal. 

Teraz możesz zobaczyć usługę Azure Information Protection w działaniu.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje o instalowaniu klienta usługi Azure Information Protection|[Pobieranie i instalowanie klienta usługi Azure Information Protection](./rms-client/install-client-app.md)|
|Instrukcje dla administratora dotyczące klienta usługi Azure Information Protection|[Podręcznik administratora klienta usługi Azure Information Protection](./rms-client/client-admin-guide.md)|


>[!div class="step-by-step"]
[&#171; Krok 2](infoprotect-tutorial-step2.md)
[Krok 4 &#187;](infoprotect-tutorial-step4.md)
