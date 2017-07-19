---
title: "Konfigurowanie zasad usługi Azure Information Protection"
description: "Aby skonfigurować klasyfikację, etykiety i ochronę, musisz skonfigurować zasady usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 7a4922384a228457b683653e80afe4b8c8db6df2
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="configuring-azure-information-protection-policy"></a>Konfigurowanie zasad usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Aby skonfigurować klasyfikację, etykiety i ochronę, musisz skonfigurować zasady usługi Azure Information Protection. Te zasady są pobierane na komputery z zainstalowanym [klientem usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

## <a name="subscription-support"></a>Obsługa subskrypcji

Zasady usługi Azure Information Protection obsługują różne poziomy subskrypcji:

- Subskrypcja P2 usługi Azure Information Protection: obsługa wszystkich funkcji klasyfikacji, etykietowania i ochrony.

- Subskrypcja P1 usługi Azure Information Protection: obsługa większości funkcji klasyfikacji, etykietowania i ochrony, ale nie automatycznej klasyfikacji ani funkcji HYOK.

- Usługa Office 365 obejmująca usługę Azure Rights Management: obsługa ochrony, ale nie klasyfikacji i etykietowania.

Opcje, które wymagają subskrypcji P2 usługi Azure Information Protection, są teraz identyfikowane w portalu.

Jeśli masz kombinację subskrypcji dla użytkowników w Twojej dzierżawie, spoczywa na Tobie obowiązek upewnienia się, że zasady usługi Azure Information Protection, które użytkownicy pobierają, nie zawierają tych opcji konfiguracji, do których używania ich konto nie ma licencji. Podczas konfigurowania opcji, w przypadku których nie wszyscy użytkownicy mają licencję, użyj zasad z określonym zakresem, tak aby użytkownicy nie byli skonfigurowani do używania tych funkcji, na których używanie mają licencję.

Aby uzyskać więcej informacji o subskrypcjach, zobacz temat [Jaka subskrypcja jest potrzebna do korzystania z usługi Azure Information Protection i jakie funkcje obejmuje ta subskrypcja?](../get-started/faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)

Aby uzyskać więcej informacji o sposobie konfigurowania zasad z określonym zakresem, zobacz temat [Konfigurowanie zasad dla konkretnych użytkowników poprzez użycie zasad o określonym zakresie](configure-policy-scope.md).

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Jak skonfigurować zasady usługi Azure Information Protection

1. W nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator zabezpieczeń lub administrator globalny.

2. Przejdź do bloku **Azure Information Protection**: na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information Protection**. Spośród wyników wybierz **Azure Information Protection**. 
    
    Przy pierwszym łączeniu się z usługą automatycznie zostanie otwarta strona **Szybki start**. W celu skonfigurowania zasad, które uzyskają wszyscy użytkownicy, kliknij opcję **Zasady globalne**, aby otworzyć blok **Zasady: globalne**. Ten blok jest automatycznie otwierany dla kolejnych połączeń z usługą, aby wyświetlić i edytować globalne zasady, który uzyskają wszyscy użytkownicy. 
    
    Zasady usługi Azure Information Protection zawierają następujące elementy, które można skonfigurować:
    
    - Etykiety, dzięki którym można klasyfikować dokumenty i wiadomości e-mail.
    
    - Tytuł i etykietka narzędzia paska usługi Information Protection, które użytkownicy zobaczą w swoich aplikacjach pakietu Office.
    
    - Opcja wymuszenia klasyfikacji w momencie zapisywania dokumentów i wysyłania wiadomości e-mail przez użytkowników.
    
    - Opcja ustawienia etykiety domyślnej jako punktu wyjścia dla klasyfikowania dokumentów i wiadomości e-mail.
    
    - Opcja monitowania użytkowników o podanie przyczyny wybrania etykiety, która ma niższą charakterystykę niż oryginalna.
    
    - Opcja automatycznego określania etykiety wiadomości e-mail na podstawie jej załączników.
    
    - Opcja udostępniania linku do niestandardowej pomocy dla użytkowników.

Usługa Azure Information Protection obejmuje [domyślne zasady](configure-policy-default.md), które zawierają pięć głównych etykiet. Etykiety te mogą być używane dla pełnego zakresu danych, które organizacja zazwyczaj tworzy i przechowuje, od danych osobowych o najniższej klasyfikacji do wysoce poufnych danych o najwyższej klasyfikacji. 

Możesz użyć domyślnych etykiet bez wprowadzania zmian, dostosować etykiety lub usunąć je, a także utworzyć nowe etykiety. Aby uzyskać więcej informacji, użyj linków z następnej sekcji w celu ułatwienia znalezienia odpowiednich opcji i sposobów ich konfigurowania. 

Po wprowadzeniu zmian w bloku Azure Information Protection kliknij przycisk **Zapisz**, aby zapisać te zmiany lub kliknij przycisk **Odrzuć**, aby przywrócić stan do ostatnio zapisanych ustawień. 

Po zakończeniu wprowadzania żądanych zmian kliknij przycisk **Opublikuj**. 

Klient usługi Azure Information Protection sprawdza zmiany podczas uruchamiania obsługiwanej aplikacji pakietu Office i pobiera zmiany jako najnowsze zasady usługi Azure Information Protection. Dodatkowe wyzwalacze powodujące odświeżenie zasad na komputerze klienckim:

- Kliknięcie prawym przyciskiem myszy w celu sklasyfikowania i ochrony pliku lub folderu.

- Uruchamianie [poleceń cmdlet programu PowerShell](../rms-client/client-admin-guide-powershell.md) mających na celu etykietowanie oraz ochronę (Get-AIPFileStatus, Set-AIPFileClassification i Set-AIPFileLabel).

- Upływ kolejnych 24 godzin.

>[!NOTE]
>Gdy klient pobierze zasady, przygotuj się na odczekanie paru minut, zanim staną się w pełni funkcjonalne. Rzeczywisty czas może być różny w zależności od takich czynników, jak rozmiar i złożoność konfiguracji zasad oraz łączność sieciowa. Jeśli wynikowe działanie etykiet nie odpowiada najnowszym zmianom, zaczekaj do 15 minut i spróbuj ponownie.

### <a name="configuring-your-organizations-policy"></a>Konfigurowanie zasad organizacji

Skorzystaj z poniższych informacji, aby skonfigurować zasady usługi Azure Information Protection:

- [Domyślne zasady usługi Information Protection](configure-policy-default.md)

- [Konfigurowanie ustawień zasad](configure-policy-settings.md)

- [Tworzenie nowej etykiety](configure-policy-new-label.md)

- [Usuwanie lub zmiana kolejności etykiet](configure-policy-delete-reorder.md)

- [Zmiana lub dostosowanie istniejącej etykiety](configure-policy-change-label.md)

- [Konfigurowanie etykiety w celu zastosowania ochrony](configure-policy-protection.md)

- [Konfigurowanie etykiety w celu zastosowania oznaczeń wizualnych](configure-policy-markings.md)

- [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej](configure-policy-classification.md)

- [Konfigurowanie zasad dla konkretnych użytkowników poprzez użycie zasad o określonym zakresie](configure-policy-scope.md)

- [Konfigurowanie szablonów i zarządzanie nimi](configure-policy-templates.md)

- [Konfigurowanie etykiet w różnych językach](configure-policy-languages.md)

## <a name="next-steps"></a>Następne kroki

Aby uzyskać przykład konfigurowania zasad domyślnych i zobaczyć efekty w aplikacji pakietu Office, wypróbuj [Samouczek Szybki start dla usługi Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
