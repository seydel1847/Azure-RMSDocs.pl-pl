---
title: Przewodnik Szybki Start — wprowadzenie do usługi Azure Information Protection w witrynie Azure portal — AIP
description: Jeśli Twoja organizacja jest całkiem nowe dla usługi Azure Information Protection, zacznij tutaj dodać usługę do witryny Azure portal, upewnij się, Usługa ochrony jest aktywowana i wyświetlić zasady.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: f5cf70b0827e36ffae6644634ef198385ef6d11a
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023519"
---
# <a name="quickstart-get-started-with-azure-information-protection-in-the-azure-portal"></a>Szybki Start: Rozpoczynanie pracy z usługą Azure Information Protection w witrynie Azure portal

W tym przewodniku Szybki Start możesz dodać usługi Azure Information Protection w witrynie Azure Portal, upewnij się, Usługa ochrony jest aktywowana i wyświetlanie Twojej organizacji domyślne zasady. 

Ten przewodnik Szybki Start można zakończyć w ciągu 5 minut.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik Szybki Start, potrzebne są:

- Subskrypcja, która obejmuje usługi Azure Information Protection Plan 1 lub Plan 2.
    
    Jeśli nie masz jedną z tych subskrypcji, możesz utworzyć [bezpłatne](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) konta dla Twojej organizacji.

Aby uzyskać pełną listę wymagań wstępnych do używania usługi Azure Information Protection, zobacz [wymagania dotyczące usługi Azure Information Protection](requirements.md).

## <a name="add-azure-information-protection-to-the-azure-portal"></a>Dodawanie usługi Azure Information Protection w witrynie Azure Portal

Usługa Azure Information Protection nie jest automatycznie dostępny w witrynie Azure portal. Należy go dodać.

1. Zaloguj się do [witryny Azure portal](https://portal.azure.com) przy użyciu konta administratora globalnego dla dzierżawy. 
    
    Jeśli nie jesteś administratorem globalnym, użyj następującego linku, dla alternatywnej ról: [logowania się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal)

2. W menu Centrum wybierz **Utwórz zasób**, a następnie w polu wyszukiwania w portalu Marketplace wpisz **usługi Azure Information Protection**. 
    
3. Wybierz z listy wyników **usługi Azure Information Protection**. Następnie na **usługi Azure Information Protection** bloku kliknij **Utwórz**.
    
    > [!TIP] 
    > Opcjonalnie można zaznaczyć **Przypnij do pulpitu nawigacyjnego** utworzyć **usługi Azure Information Protection** kafelka na pulpicie nawigacyjnym, dzięki czemu można pominąć, przechodząc do usługi przy następnym logowaniu do portalu.
    
    Kliknij przycisk **Utwórz** ponownie.

## <a name="confirm-the-protection-service-is-activated"></a>Upewnij się, że usługa ochrony jest aktywowana.

Usługa ochrony jest teraz aktywowana automatycznie dla nowych dzierżaw, ale to dobry pomysł, aby potwierdzić, że nie musi ręcznie uaktywnić. 

1. Na **usługi Azure Information Protection** bloku wybierz **Zarządzaj** > **Aktywacja ochrony**.

2. Upewnij się, czy ochrona jest aktywowana dla Twojej dzierżawy: 
    
    - Jeśli ochrona została aktywowana, zostanie wyświetlony po potwierdzeniu:
        
        ![Stan usługi Azure Information Protection dla usługi Azure RMS](./media/info-protect-azurerms-activated.png)
        
    - Jeśli nie włączono ochronę, zobaczysz to odzwierciedlenie w informacje o stanie oraz opcja jej aktywowania:
        
        ![Stan usługi Azure Information Protection dla usługi Azure RMS](./media/info-protect-azurerms-deactivated.png)

3. Jeśli ochrona nie zostanie aktywowany, wybierz opcję **Aktywuj**. 

    Po zakończeniu aktywacji Wyświetla pasek informacji **Aktywacja została zakończona pomyślnie**.

## <a name="view-your-organizations-default-policy---labels-and-policy-settings"></a>Wyświetlanie Twojej organizacji domyślne zasady — ustawienia zasad i etykiet

Przy pierwszym nawiązaniu połączenia z usługą Azure Information Protection przy użyciu witryny Azure portal utworzyć zasady domyślne dla Twojej dzierżawy. Zasada domyślna zawiera etykiety i ustawienia, których można użyć jako — jest lub dostosować.

1. Wybierz **klasyfikacje** > **zasady** > **Global** Aby wyświetlić domyślne zasady usługi Azure Information Protection, które są tworzone dla dzierżawy.
    
2. Poświęć kilka minut, o których zapoznawanie się z etykiet, które są wyświetlane:
    
    - Etykiety klasyfikacji: **Osobiste**, **Publiczne**, **Ogólne**, **Poufne** i **Wysoce poufne**. Dwie ostatnie etykiety rozszerzyć, aby wyświetlić etykiet podrzędnych, które zawierają przykłady klasyfikacji można podkategorie:
    
    - W przypadku domyślnej konfiguracji niektóre etykiety nie mają skonfigurowane oznaczenia wizualne. Znaczniki wizualne są stopka, nagłówek i znak wodny. W zależności od zasady domyślne niektóre etykiety może być również ma ustawionej ochrony. Przykład: 
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zasada domyślna](./media/info-protect-policy-default-labelsv2.png)
    
3. Po etykietach w **Konfiguruj ustawienia wyświetlania i Zastosuj Information Protection, użytkownicy końcowi** sekcji Zobacz też niektóre ustawienia zasad. Na przykład nie jest domyślne etykiety, dokumentów i wiadomości e-mail nie muszą mieć etykietę i użytkownicy nie muszą uzasadniać zmiany etykiet:
    
    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zasada domyślna](./media/info-protect-policy-default-settings.png) 

4. Ponieważ są tylko wyświetlania etykiety i ustawienia, możesz zamknąć wszystkich blokach, które zostały otwarte.

## <a name="next-steps"></a>Kolejne kroki

Teraz, gdy wiesz, etykiety i ustawienia zasad w witrynie Azure portal, mogą być przydatne następującego samouczka w następnym kroku: [edytować zasady i Utwórz nową etykietę dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).

Alternatywnie, aby uzyskać szczegółowe instrukcje dotyczące konfigurowania wszystkie aspekty zasad usługi Azure Information Protection, zobacz [Konfigurowanie zasad usługi Azure Information Protection](configure-policy.md).
