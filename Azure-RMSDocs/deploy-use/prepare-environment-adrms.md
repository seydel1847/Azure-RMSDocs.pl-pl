---
title: "Przygotowanie środowiska do korzystania z usług Azure RMS i AD RMS"
description: "W tej sekcji znajdują się wskazówki mające zastosowanie w przypadku wdrożenia usługi Azure Rights Management wraz z usługami AD RMS."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5ab34172a4e822373161752142d9e082014285e1
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>Przygotowywanie środowiska na potrzeby usługi Azure Rights Management w przypadku używania również usług Active Directory Rights Management Services (AD RMS)

>*Dotyczy: Azure Information Protection, Office 365*

Zastosuj ważne wskazówki, jeśli już używasz Active Directory Rights Management Services (AD RMS) i jeden z następujących scenariuszy:

- [Zakupiono subskrypcję obejmującą usługę Azure Rights Management w lub po 2018 lutego](#your-subscription-was-purchased-during-or-after-february-2018).

- [Zobacz opcję, aby aktywować ochrony podczas konfigurowania zasad usługi Azure Information Protection w portalu Azure](#you-see-an-option-to activate-azure-rights-management-when-you-configure-azure-information-protection)

## <a name="your-subscription-was-purchased-during-or-after-february-2018"></a>Subskrypcja została zakupiona podczas lub po 2018 lutego

Jeśli zakupiono subskrypcję obejmującą usługę Azure Rights Management, podczas lub po Februrary 2018, usługa Azure Rights Management została aktywowana domyślnie. Jeśli używane są również Active Directory Rights Management Services (AD RMS), ta kombinacja nie jest zgodna. Bez dodatkowych kroków niektóre komputery mogą automatycznie rozpocząć korzystanie z usługi Azure Rights Management i także połączyć się z klastrem usług AD RMS. W tym scenariuszu nie jest obsługiwana i została niewiarygodne wyniki, dlatego należy jak najszybciej dezaktywowanie usługi Azure Rights Management. 

Gdy wszystko będzie gotowe przenieść komputery z usług AD RMS do usługi Azure Rights Management, można uruchomić procesu migracji. Jeden z kroków procesu migracji jest ponowne aktywowanie usługi, ale wykonać ten krok po wyeksportowaniu informacji o konfiguracji z usług AD RMS do usługi Azure Rights Management. Ta kolejność zapewnia, że dokumenty i wiadomości e-mail, które były chronione przez usługi AD RMS nadal mogą być otwierane.

Pierwszym krokiem jest dezaktywowanie usługi Azure Rights Management.

### <a name="step-1-deactivate-azure-rights-management"></a>Krok 1: Dezaktywowanie usługi Azure Rights Management
Wykonaj kroki jednej z poniższych procedur, aby zdezaktywować usługę [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Możesz również użyć polecenia cmdlet programu Windows PowerShell, [Disable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx), aby zdezaktywować usługę [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Aby zdezaktywować usługę Rights Management w centrum administracyjnym usługi Office 365

1. Przejdź na [stronę usługi Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) dla administratorów usługi Office 365.
    
    Po wyświetleniu monitu o zalogowanie użyj konta administratora globalnego usługi Office 365.

2. Na stronie **Rights Management** kliknij pozycję **Dezaktywuj**.

3.  Po wyświetleniu monitu **czy chcesz dezaktywować usługę Rights Management?** kliknij **dezaktywować**.

Teraz powinien pojawić się komunikat **Usługa Rights Management nie została aktywowana** oraz opcja jej aktywowania.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Aby zdezaktywować usługę Rights Management w portalu Azure

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.
    
    Jeśli nie zostało to jeszcze dostęp do bloku usługi Azure Information Protection przed, zobacz jednorazowe [dodatkowe kroki](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time) można dodać tego bloku do portalu.

2. Na początkowej **usługi Azure Information Protection** bloku, wybierz opcję **aktywacji ochrony**. 

3.  Na **usługi Azure Information Protection — aktywacji ochrony** bloku, wybierz opcję **Dezaktywuj**. Wybierz **tak** o potwierdzenie wyboru.

Wyświetla pasek informacji **dezaktywacji zakończyło się pomyślnie** i **Dezaktywuj** zastąpione programem **Aktywuj**. 

### <a name="step-2-start-planning-for-migration"></a>Krok 2. Rozpoczynanie planowania migracji

Zobacz wskazówki dotyczące migracji: [Migrowanie z usług AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Zobacz opcję, aby aktywować ochrony po skonfigurowaniu usługi Azure Information Protection

**Usługi Azure Information Protection — aktywacji ochrony** blok zawiera opcję, aby aktywować usługę Azure Rights Management (Azure RMS).  

Jeśli używane są również usługi Active Directory Rights Management Services (AD RMS), nie należy wybierać opcji **Aktywuj**. Aktywacja usługi Azure Rights Management w przypadku korzystania również z usług AD RMS nie jest zgodną kombinacją. Ten scenariusz nie jest obsługiwany, a jego wyniki nie są wiarygodne, więc istotne jest, aby w tym momencie nie aktywować usługi Azure Rights Management.  

Gdy wszystko będzie gotowe do przeniesienia komputerów z usług AD RMS do usługi Azure Rights Management, możliwe będzie rozpoczęcie procesu migracji. Jednym z kroków procesu migracji jest aktywowanie usługi, ale należy to wykonać po wyeksportowaniu informacji o konfiguracji z usług AD RMS do usługi Azure Rights Management. Przeprowadzenie tego procesu gwarantuje, że dokumenty i wiadomości e-mail chronione przez usługi AD RMS nadal będą mogły być otwierane. 

Jeśli usługa Azure Rights Management nie została aktywowana, nadal można używać usługi Azure Information Protection dla etykiet, w przypadków których stosowane jest tylko klasyfikowanie. Tworzone są specjalne zasady domyślne, które nie obejmują funkcji ochrony danych. Te opcje konfiguracji pozostają niedostępne do momentu aktywowania usługi Azure Rights Management.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Krok 1. Konfigurowanie zasad usługi Azure Information Protection pod kątem klasyfikowania i etykietowania — bez ochrony

Z poziomu początkowego bloku **Azure Information Protection** wybierz pozycję **Zasady globalne**, aby wyświetlić i skonfigurować zasady domyślne, które nie obejmują opcji ochrony danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad usługi Azure Information Protection](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Krok 2. Rozpoczynanie planowania migracji

Zobacz wskazówki dotyczące migracji: [Migrowanie z usług AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

### <a name="step-3-start-to-configure-labels-for-protection"></a>Krok 3. Rozpoczynanie konfigurowania etykiet na potrzeby ochrony

Po aktywowaniu usługi Azure Rights Management w ramach procesu migracji można skonfigurować etykiety na potrzeby ochrony danych. Jednak w przypadku migrowania użytkowników w partiach, upewnij się, ograniczone etykiety, które stosują ochronę tylko użytkownikom zmigrowane.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

