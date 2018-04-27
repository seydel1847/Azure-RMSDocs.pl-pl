---
title: Samouczek Szybki start — krok 1 — AIP
description: Krok 1 samouczka wprowadzającego, można szybko wypróbować usługę Azure Information Protection — aktywowanie usługi ochrony.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/22/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: 5dcc63f6ffbd7402c94258fe0d8677908c603e1f
ms.sourcegitcommit: 94d1c7c795e305444e9fde17ad73e46f242bcfa9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2018
---
# <a name="step-1-activate-protection"></a>Krok 1: Aktywowanie ochrony
 
>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
>Nawet w przypadku ochrony został aktywowany dla swojej dzierżawy, należy wykonać ten krok, aby potwierdzić stan aktywacji. Instrukcje zawierają logowanie do portalu Azure i Tworzenie bloku Azure Information Protection, dzięki czemu możesz przejść do kroku 2.

Po aktywowaniu usługi Azure Information Protection ochrony można chronić w organizacji najbardziej poufne dokumenty i wiadomości e-mail. Można także śledzić, jak te dokumenty chronione są używane podczas udostępniać innym użytkownikom. 

Istnieją różne sposoby aktywacji ochrony. Można użyć programu PowerShell i portale administratora. Jednak w tym samouczku używamy portalu Azure etykiety dla użytkowników należy również skonfigurować. 

## <a name="to-activate-protection"></a>Aby aktywować ochrony

1. Zaloguj się do [portalu Azure](https://portal.azure.com) przy użyciu konta administratora globalnego dla dzierżawy. 
    
    Jeśli nie jesteś administratorem globalnym, możesz użyć jednego z następujących [ról administracyjnych](/azure/active-directory/active-directory-assign-admin-roles-azure-portal): **administratora ochrony informacji** lub **Administrator zabezpieczeń**.

2. W menu centralnym kliknij **Utwórz zasób**, a następnie, z **MARKETPLACE** listy, wybierz **bezpieczeństwo i Obsługa tożsamości**. 
    
3.  Na **zabezpieczeń + Identyfikuj** bloku z **POLECANE aplikacje** listy, wybierz **usługi Azure Information Protection**. Następnie na **usługi Azure Information Protection** bloku, kliknij przycisk **Utwórz**.
    
    Ta akcja tworzy **usługi Azure Information Protection** bloku, dzięki czemu przy następnym zalogowaniu do portalu można wybrać usługę z Centrum **wszystkie usługi** listy. 
    
    > [!TIP] 
    > Wybierz opcję **Przypnij do pulpitu nawigacyjnego**, aby utworzyć kafelek usługi **Azure Information Protection** na pulpicie nawigacyjnym, dzięki czemu można będzie pominąć krok przeglądania w poszukiwaniu usługi przy następnym zalogowaniu w witrynie portalu.

4. Należy zwrócić uwagę na informację znajdującą się na stronie **Szybki start**, która zostanie automatycznie otwarta przy pierwszym połączeniu z usługą. Możesz do niej wrócić później. W tym samouczku, wybierz **ZARZĄDZAJ** > **aktywacji ochrony**. 

5. Możesz teraz zobaczyć, czy ochrona jest aktywowana dla Twojej dzierżawy. 
    
    - Jeśli włączono ochronę, zostanie wyświetlony po potwierdzeniu:
        
        ![Azure Information Protection stanu usługi Azure RMS](../media/info-protect-azurerms-activated.png)
        
    - Jeśli nie włączono ochrony, zobacz się, że to odzwierciedlenie w informacje o stanie i opcję aktywacji:
        
        ![Azure Information Protection stanu usługi Azure RMS](../media/info-protect-azurerms-deactivated.png)

6. Jeśli ochrona nie jest aktywowany, wybierz **Aktywuj**. 

    Po zakończeniu aktywacji Wyświetla pasek informacji **aktywacji zakończyło się pomyślnie**.

To wszystko, co musisz zrobić w pierwszym kroku tego samouczka. Możesz przejść do kroku 2.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Temat aktywowania ochrony|[Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md)|


>[!div class="step-by-step"]
[&#171; Wprowadzenie](infoprotect-quick-start-tutorial.md)
[Krok 2 &#187;](infoprotect-tutorial-step2.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
