---
title: "Samouczek Szybki start — krok 1 — AIP"
description: "Krok 1 samouczka wprowadzającego, dzięki któremu można szybko wypróbować usługę Azure Information Protection — aktywowanie usługi Azure Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: adc2baa875595d5044b47a9f014cc1381ba85dc2
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Krok 1. Aktywowanie usługi Rights Management
<a id="step-1-activate-the-rights-management-service" class="xliff"></a>
 
>*Dotyczy: Azure Information Protection*

> [!NOTE]
>Jeśli wiesz, że usługa Azure Rights Management dla dzierżawy została już aktywowana, możesz przejść bezpośrednio do [następnego kroku](infoprotect-tutorial-step2.md). 
>
>Jeśli nie masz pewności, czy ta usługa została aktywowana, użyj instrukcji podanych w tym kroku, aby to sprawdzić.

Po aktywowaniu usługi Azure Rights Management możesz chronić najbardziej poufne dokumenty i wiadomości e-mail organizacji oraz śledzić wykorzystanie chronionych dokumentów po udostępnieniu ich innym osobom. Istnieją różne metody aktywowania tej usługi, w tym zastosowanie usługi Windows PowerShell i wykorzystanie portali administracyjnych.

W przypadku tego samouczka przejdziemy bezpośrednio do strony aktywacji w portalu administracyjnym dla administratorów usługi Office 365. Jednak jeśli wolisz przejść do tej strony z portalu administracyjnego usługi Office 365, a nie bezpośrednio, zobacz pełne instrukcje w dokumencie [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md). Tych pełnych instrukcji należy użyć także w przypadku posiadania dostępu do witryny Azure Portal, ale nie portalu administracyjnego Office 365.

## Aktywowanie usługi Rights Management
<a id="to-activate-the-rights-management-service" class="xliff"></a>

1. Otwórz nowe okno przeglądarki i przejdź bezpośrednio do [strony aktywacji usługi Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) dla administratorów usługi Office 365.
    
    Po wyświetleniu monitu o zalogowanie użyj konta administratora globalnego usługi Office 365.

2. Na stronie **Rights Management** kliknij pozycję **Aktywuj**. Jeśli na tym przycisku znajduje się napis **dezaktywuj**, usługa jest już aktywna i możesz przejść bezpośrednio do [następnego kroku](infoprotect-tutorial-step2.md). 

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 1 — aktywacja usługi](../media/info-protect-activate.png)

3. Po wyświetleniu monitu **Czy chcesz aktywować usługę Rights Management?** kliknij pozycję **aktywuj**, aby potwierdzić.

    Zostanie wyświetlony komunikat **Usługa Rights Management została aktywowana** wraz z opcją dezaktywowania tej usługi (może być konieczne ręczne odświeżenie strony).

    Tym razem nie klikaj pozycji **Funkcje zaawansowane**. Kliknięcie tej pozycji spowoduje wyświetlenie klasycznego portalu Azure, umożliwiającego konfigurowanie szablonów niestandardowych, które nie są potrzebne w tym samouczku. Zamiast tego możesz zamknąć tę stronę.

To wszystko, co musisz zrobić w pierwszym kroku tego samouczka. W przypadku wdrożenia produkcyjnego prawdopodobnie zechcesz skonfigurować niestandardowe szablony zastępujące lub uzupełniające dwa domyślne szablony usługi Azure Rights Management. Jednak w naszym samouczku szablony niestandardowe nie są potrzebne, dlatego możesz teraz przejść do kroku 2.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje o aktywacji usługi Azure Rights Management|[Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md)|
|Informacje na temat szablonów domyślnych i sposobu tworzenia nowych szablonów niestandardowych|[Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management](../deploy-use/configure-custom-templates.md)|

>[!div class="step-by-step"]
[&#171; Wprowadzenie](infoprotect-quick-start-tutorial.md)
[Krok 2 &#187;](infoprotect-tutorial-step2.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
