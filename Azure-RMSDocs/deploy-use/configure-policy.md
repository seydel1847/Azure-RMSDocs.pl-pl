---
title: Konfigurowanie zasad | Azure Information Protection
description: "Aby skonfigurować klasyfikację, etykiety i ochronę, musisz skonfigurować zasady usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/13/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8ad1ff05f642571bfe7f4170cb88e29d05515e59
ms.openlocfilehash: 2ad10e378c14dbaef09ccd321379a0dbd7c0d23d


---

# <a name="configuring-azure-information-protection-policy"></a>Konfigurowanie zasad usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Aby skonfigurować klasyfikację, etykiety i ochronę, musisz skonfigurować zasady usługi Azure Information Protection. Te zasady są pobierane na komputery z zainstalowanym [klientem usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Aby skonfigurować zasady usługi Azure Information Protection:

1. W nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator globalny.

2. Przejdź do bloku **Azure Information Protection**: na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information Protection**. Spośród wyników wybierz **Azure Information Protection**. 

    Zostanie wyświetlony blok **Azure Information Protection**, w którym można otworzyć zasady **Globalne**, które mają zastosowanie do wszystkich użytkowników. Opcjonalnie możesz również dodawać i edytować zasady należące do zakresów. **Globalne** zasady usługi Azure Information Protection zawierają następujące elementy, które można skonfigurować:

    - Etykiety, dzięki którym można klasyfikować dokumenty i wiadomości e-mail.

    - Tytuł i etykietka narzędzia paska usługi Information Protection, które użytkownicy zobaczą w swoich aplikacjach pakietu Office.

    - Opcja wymuszenia klasyfikacji w momencie zapisywania dokumentów i wysyłania wiadomości e-mail przez użytkowników.

    - Opcja ustawienia etykiety domyślnej jako punktu wyjścia dla klasyfikowania dokumentów i wiadomości e-mail.

    - Opcja monitowania użytkowników o podanie przyczyny wybrania etykiety, która ma niższą charakterystykę niż oryginalna.

    - Opcja udostępniania linku do niestandardowej pomocy dla użytkowników.

Usługa Azure Information Protection zawiera [zasady domyślne](configure-policy-default.md), które uwzględniają etykiety: **Osobiste**, **Publiczne**, **Wewnętrzne**, **Poufne** i **Tajne**. Możesz użyć domyślnych etykiet bez wprowadzania zmian, dostosować etykiety lub usunąć je, a także utworzyć nowe etykiety.

Po wprowadzeniu zmian w bloku Azure Information Protection kliknij przycisk **Zapisz**, aby zapisać te zmiany lub kliknij przycisk **Odrzuć**, aby przywrócić stan do ostatnio zapisanych ustawień. 

Po zakończeniu wprowadzania żądanych zmian kliknij przycisk **Opublikuj**. 

Klient usługi Azure Information Protection sprawdza zmiany podczas uruchamiania obsługiwanej aplikacji pakietu Office i pobiera zmiany jako zasady usługi Azure Information Protection.

## <a name="configuring-your-organizations-policy"></a>Konfigurowanie zasad organizacji

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

## <a name="next-steps"></a>Następne kroki

Aby uzyskać przykład konfigurowania zasad domyślnych i zobaczyć efekty w aplikacji pakietu Office, wypróbuj [Samouczek Szybki start dla usługi Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Feb17_HO2-->


