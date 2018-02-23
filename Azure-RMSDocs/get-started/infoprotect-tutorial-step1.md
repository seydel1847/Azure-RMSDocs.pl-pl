---
title: "Samouczek Szybki start — krok 1 — AIP"
description: "Krok 1 samouczka wprowadzającego, można szybko wypróbować usługę Azure Information Protection — aktywowanie usługi ochrony."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: 952431771e89e934be4a725ece4f3d9cd47165fe
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="step-1-activate-protection"></a>Krok 1: Aktywowanie ochrony
 
>*Dotyczy: Azure Information Protection*

> [!NOTE]
>Nawet wtedy, gdy usługa usługi Azure Rights Management została aktywowana dla Twojej dzierżawy, należy wykonać ten krok, aby potwierdzić stan aktywacji. Instrukcje zawierają logowanie do portalu Azure i Tworzenie bloku Azure Information Protection, dzięki czemu możesz przejść do kroku 2.

Po aktywowaniu usługi Azure Rights Management, można chronić najbardziej poufne dokumenty i wiadomości e-mail w organizacji. Można także śledzić, jak te dokumenty chronione są używane podczas udostępniać innym użytkownikom. 

Istnieją różne sposoby aktywacji ochrony. Można użyć programu PowerShell i portale administratora. Jednak w tym samouczku używamy portalu Azure etykiety dla użytkowników należy również skonfigurować. 

## <a name="to-activate-the-azure-rights-management-service"></a>Aby aktywować usługę Azure Rights Management

1. Zaloguj się do [portalu Azure](https://portal.azure.com) przy użyciu konta administratora globalnego dla dzierżawy. 
    
    Jeśli nie jesteś administratorem globalnym, możesz użyć jednego z następujących [ról administracyjnych](/azure/active-directory/active-directory-assign-admin-roles-azure-portal): **administratora ochrony informacji** lub **Administrator zabezpieczeń**.

2. W menu centralnym kliknij **Utwórz zasób**, a następnie, z **MARKETPLACE** listy, wybierz **bezpieczeństwo i Obsługa tożsamości**. 
    
3.  Na **zabezpieczeń + Identyfikuj** bloku z **POLECANE aplikacje** listy, wybierz **usługi Azure Information Protection**. Następnie na **usługi Azure Information Protection** bloku, kliknij przycisk **Utwórz**.
    
    Ta akcja tworzy **usługi Azure Information Protection** bloku, dzięki czemu przy następnym zalogowaniu do portalu można wybrać usługę z Centrum **wszystkie usługi** listy. 
    
    > [!TIP] 
    > Wybierz opcję **Przypnij do pulpitu nawigacyjnego**, aby utworzyć kafelek usługi **Azure Information Protection** na pulpicie nawigacyjnym, dzięki czemu można będzie pominąć krok przeglądania w poszukiwaniu usługi przy następnym zalogowaniu w witrynie portalu.

4. Należy zwrócić uwagę na informację znajdującą się na stronie **Szybki start**, która zostanie automatycznie otwarta przy pierwszym połączeniu z usługą. Możesz do niej wrócić później. W tym samouczku, wybierz **aktywacji ochrony**. 

5. Możesz teraz zobaczyć, czy usługa Azure Rights Management została aktywowana dla Twojej dzierżawy. 
    
    - Jeśli usługa została aktywowana, zostanie wyświetlony po potwierdzeniu:
        
        ![Azure Information Protection stanu usługi Azure RMS](../media/info-protect-azurerms-activated.png)
        
    - Jeśli usługa nie została aktywowana, pojawić się, że to odzwierciedlenie w informacje o stanie i opcję aktywacji:
        
        ![Azure Information Protection stanu usługi Azure RMS](../media/info-protect-azurerms-deactivated.png)

6. Jeśli usługa nie została aktywowana, wybierz **Aktywuj**. 

    Po zakończeniu aktywacji Wyświetla pasek informacji **aktywacji zakończyło się pomyślnie**.

To wszystko, co musisz zrobić w pierwszym kroku tego samouczka. Możesz przejść do kroku 2.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje o aktywacji usługi Azure Rights Management|[Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md)|


>[!div class="step-by-step"]
[&#171; Wprowadzenie](infoprotect-quick-start-tutorial.md)
[Krok 2 &#187;](infoprotect-tutorial-step2.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
