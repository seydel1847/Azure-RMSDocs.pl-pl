---
title: Samouczek Szybki start krok 1 | Azure Information Protection
description: "Krok 1 samouczka wprowadzającego, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection w swojej organizacji. Wystarczy około 30 minut."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: edb98a61d247b51319a1eb172f9978e3d64d0e1b


---

# <a name="step-1-activate-the-rights-management-service"></a>Krok 1. Aktywowanie usługi Rights Management
 
>*Dotyczy: Azure Information Protection*

> [!NOTE]
>Jeśli już aktywowano usługę Azure Rights Management dla dzierżawy — przejdź wprost do [następnego kroku](infoprotect-tutorial-step2.md). 

Po aktywowaniu usługi Azure Rights Management, możesz chronić najbardziej poufne dokumenty i wiadomości e-mail organizacji oraz śledzić ich wykorzystanie po udostępnieniu ich innym osobom. Istnieją różne metody aktywowania tej usługi, w tym zastosowanie usługi Windows PowerShell i przejście przez portale administracyjne.

W tym samouczku przejdziemy bezpośrednio do strony aktywacji dla administratorów pakietu Office 365, czyli strony identycznej dla klasycznego portalu Office 365 i wersji zapoznawczej centrum administracji Office 365. 

Jeśli wolisz przejść do tej strony z portalu administracyjnego pakietu Office 365, a nie bezpośrednio, zobacz pełne instrukcje w dokumencie [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md). Tych pełnych instrukcji należy użyć także w przypadku posiadania dostępu do witryny Azure Portal, ale nie portalu administracyjnego Office 365.

## <a name="to-activate-the-rights-management-service"></a>Aktywowanie usługi Rights Management

1. Otwórz nowe okno przeglądarki i przejdź bezpośrednio do [strony aktywacji usługi Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) dla administratorów usługi Office 365.
    
    Po wyświetleniu monitu o zalogowanie użyj konta administratora globalnego usługi Office 365.

2. Na stronie **Rights Management** kliknij pozycję **Aktywuj**.

3. Po wyświetleniu monitu **Czy chcesz aktywować usługę Rights Management?** kliknij pozycję **Aktywuj**.

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



<!--HONumber=Nov16_HO2-->


