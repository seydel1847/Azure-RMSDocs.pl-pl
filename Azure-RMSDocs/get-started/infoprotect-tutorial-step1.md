---
title: "Samouczek Szybki start — krok 1 — AIP"
description: "Krok 1 samouczka wprowadzającego, dzięki któremu można szybko wypróbować usługę Azure Information Protection — aktywowanie usługi Azure Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/12/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: e80d47d1a477c03296b9a2e0eb4373929cfaa66b
ms.sourcegitcommit: 94a9b6714c555b95f6064088e77ed94f08224a15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2017
---
# <a name="step-1-activate-the-rights-management-service"></a>Krok 1. Aktywowanie usługi Rights Management
 
>*Dotyczy: Azure Information Protection*

> [!NOTE]
>Nawet jeśli już aktywowano usługę Azure Rights Management dla swojej dzierżawy, należy wykonać ten krok, aby potwierdzić stan aktywacji. Instrukcje zawierają logowanie do portalu Azure i Tworzenie bloku Azure Information Protection, aby przejść do kroku 2. 

Po aktywowaniu usługi Azure Rights Management możesz chronić najbardziej poufne dokumenty i wiadomości e-mail organizacji oraz śledzić wykorzystanie chronionych dokumentów po udostępnieniu ich innym osobom. Istnieją różne metody aktywowania tej usługi, w tym zastosowanie usługi Windows PowerShell i wykorzystanie portali administracyjnych.

W tym samouczku użyjemy portalu Azure etykiety dla użytkowników należy również skonfigurować. 

## <a name="to-activate-the-azure-rights-management-service"></a>Aby aktywować usługę Azure Rights Management

1. Zaloguj się do [portalu Azure](https://portal.azure.com) jako administrator globalny lub Administrator zabezpieczeń dla dzierżawy.

2. W menu centralnym kliknij przycisk **Nowy**, a następnie z listy **MARKETPLACE** wybierz opcję **Zabezpieczenia i tożsamość**. 
    
3.  Na **zabezpieczeń + Identyfikuj** bloku z **POLECANE aplikacje** listy, wybierz **usługi Azure Information Protection**. Następnie na **usługi Azure Information Protection** bloku, kliknij przycisk **Utwórz**.
    
    Ta akcja tworzy **usługi Azure Information Protection** bloku, dzięki czemu przy następnym zalogowaniu do portalu można wybrać usługę z Centrum **więcej usług** listy. 
    
    > [!TIP] 
    > Wybierz opcję **Przypnij do pulpitu nawigacyjnego**, aby utworzyć kafelek usługi **Azure Information Protection** na pulpicie nawigacyjnym, dzięki czemu można będzie pominąć krok przeglądania w poszukiwaniu usługi przy następnym zalogowaniu w witrynie portalu.

4. Należy zwrócić uwagę na informację znajdującą się na stronie **Szybki start**, która zostanie automatycznie otwarta przy pierwszym połączeniu z usługą. Możesz do niej wrócić później. W tym samouczku, wybierz **ustawienia RMS** lub **aktywacji ochrony**. Ta opcja jest w trakcie zmieniana. 

5. Możesz teraz zobaczyć, czy usługa Azure Rights Management została aktywowana dla Twojej dzierżawy. 
    
    - Jeśli usługa została aktywowana, zobaczysz potwierdzenie, takie jak następujące:
        
        ![Azure Information Protection stanu usługi Azure RMS](../media/info-protect-azurerms-activated.png)
        
    - Jeśli usługa nie została aktywowana, zobacz się, że to odzwierciedlenie w informacje o stanie oraz opcja jej aktywowania. Na przykład:
        
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
