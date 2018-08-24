---
title: Samouczek Szybki start — krok 1 — AIP
description: Krok 1 samouczka wprowadzającego, dzięki któremu można szybko wypróbować usługę Azure Information Protection — aktywować usługę ochrony.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/28/2018
ms.topic: article
ms.service: information-protection
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: 3d397227420efb8b149eb1ac157702868745ba23
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42805100"
---
# <a name="step-1-activate-protection"></a>Krok 1: Aktywowanie ochrony
 
>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
>Nawet wtedy, gdy ochrona została aktywowana dla Twojej dzierżawy, należy wykonać ten krok, aby potwierdzić stan aktywacji. Instrukcje zawierają logowanie do witryny Azure portal i Tworzenie bloku Azure Information Protection, dzięki czemu możesz przejść do kroku 2.

Po aktywowaniu usługi Azure Information Protection ochrony można chronić w organizacji najbardziej poufne dokumenty i wiadomości e-mail. Można także śledzić używania tych chronionych dokumentów po udostępnieniu ich innym osobom. 

Istnieją różne sposoby, aktywować ochronę. Można użyć programu PowerShell i portale administracyjne. Ale w tym samouczku korzystamy z witryny Azure portal, czyli, gdzie możesz również skonfigurować etykiety dla użytkowników. 

## <a name="to-activate-protection"></a>Aby aktywować ochronę

1. Zaloguj się do [witryny Azure portal](https://portal.azure.com) przy użyciu konta administratora globalnego dla dzierżawy. 
    
    Jeśli nie jesteś administratorem globalnym, możesz użyć jednego z następujących [ról administracyjnych](/azure/active-directory/active-directory-assign-admin-roles-azure-portal): **Administrator usługi Information Protection** lub **Administrator zabezpieczeń**.

2. W menu Centrum wybierz **Utwórz zasób**, a następnie w polu wyszukiwania w portalu Marketplace wpisz **usługi Azure Information Protection**. 
    
3. Wybierz z listy wyników **usługi Azure Information Protection**. Na **usługi Azure Information Protection** bloku kliknij **Utwórz**.
    
    > [!TIP] 
    > Opcjonalnie można zaznaczyć **Przypnij do pulpitu nawigacyjnego** utworzyć **usługi Azure Information Protection** kafelka na pulpicie nawigacyjnym, dzięki czemu można pominąć, przechodząc do usługi przy następnym logowaniu do portalu.
    
    Kliknij przycisk **Utwórz** ponownie.

4. Należy zwrócić uwagę na informację znajdującą się na stronie **Szybki start**, która zostanie automatycznie otwarta przy pierwszym połączeniu z usługą. Możesz do niej wrócić później. Na potrzeby tego samouczka wybierz **ZARZĄDZAJ** > **Aktywacja ochrony**. 

5. Możesz teraz zobaczyć, czy ochrona jest aktywowana dla Twojej dzierżawy. 
    
    - Jeśli ochrona została aktywowana, zostanie wyświetlony po potwierdzeniu:
        
        ![Stan usługi Azure Information Protection dla usługi Azure RMS](./media/info-protect-azurerms-activated.png)
        
    - Jeśli nie włączono ochronę, zobaczysz to odzwierciedlenie w informacje o stanie oraz opcja jej aktywowania:
        
        ![Stan usługi Azure Information Protection dla usługi Azure RMS](./media/info-protect-azurerms-deactivated.png)

6. Jeśli ochrona nie zostanie aktywowany, wybierz opcję **Aktywuj**. 

    Po zakończeniu aktywacji Wyświetla pasek informacji **Aktywacja została zakończona pomyślnie**.

To wszystko, co musisz zrobić w pierwszym kroku tego samouczka. Możesz przejść do kroku 2.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|O aktywowanie ochrony|[Aktywacja usługi Azure Rights Management](activate-service.md)|


>[!div class="step-by-step"]
[&#171; Wprowadzenie](infoprotect-quick-start-tutorial.md)
[Krok 2 &#187;](infoprotect-tutorial-step2.md)

