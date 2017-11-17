---
title: "Przygotowanie środowiska do korzystania z usług Azure RMS i AD RMS"
description: "W tej sekcji znajdują się wskazówki mające zastosowanie w przypadku wdrożenia usługi Azure Rights Management wraz z usługami AD RMS."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b20bbc1fe0de90b9b0151098e1b77d3c7a98c431
ms.sourcegitcommit: e9a24fc5303b21f5eeebf16afed44db0d163ac77
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>Przygotowywanie środowiska na potrzeby usługi Azure Rights Management w przypadku używania również usług Active Directory Rights Management Services (AD RMS)

>*Dotyczy: Azure Information Protection, Office 365*

Są to ważne wskazówki, gdy używane są usługi Active Directory Rights Management Services (AD RMS) i ma zastosowanie następujący scenariusz:

## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Zobacz opcję, aby aktywować ochrony po skonfigurowaniu usługi Azure Information Protection

**Usługi Azure Information Protection — aktywacji ochrony** blok zawiera opcję, aby aktywować usługę Azure Rights Management (Azure RMS). 

Jeśli używane są również usługi Active Directory Rights Management Services (AD RMS), nie należy wybierać opcji **Aktywuj**. Aktywacja usługi Azure Rights Management w przypadku korzystania również z usług AD RMS nie jest zgodną kombinacją. Ten scenariusz nie jest obsługiwany, a jego wyniki nie są wiarygodne, więc istotne jest, aby w tym momencie nie aktywować usługi Azure Rights Management. 

Gdy wszystko będzie gotowe do przeniesienia komputerów z usług AD RMS do usługi Azure Rights Management, możliwe będzie rozpoczęcie procesu migracji. Jednym z kroków procesu migracji jest aktywowanie usługi, ale należy to wykonać po wyeksportowaniu informacji o konfiguracji z usług AD RMS do usługi Azure Rights Management. Przeprowadzenie tego procesu gwarantuje, że dokumenty i wiadomości e-mail chronione przez usługi AD RMS nadal będą mogły być otwierane.

Jeśli usługa Azure Rights Management nie została aktywowana, nadal można używać usługi Azure Information Protection dla etykiet, w przypadków których stosowane jest tylko klasyfikowanie. Tworzone są specjalne zasady domyślne, które nie obejmują funkcji ochrony danych. Te opcje konfiguracji pozostają niedostępne do momentu aktywowania usługi Azure Rights Management.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Krok 1. Konfigurowanie zasad usługi Azure Information Protection pod kątem klasyfikowania i etykietowania — bez ochrony

Z poziomu początkowego bloku **Azure Information Protection** wybierz pozycję **Zasady globalne**, aby wyświetlić i skonfigurować zasady domyślne, które nie obejmują opcji ochrony danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad usługi Azure Information Protection](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Krok 2. Rozpoczynanie planowania migracji

Postępuj zgodnie ze wskazówkami dotyczącymi migracji: [Migrowanie z usług AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

### <a name="step-3-start-to-configure-labels-for-protection"></a>Krok 3. Rozpoczynanie konfigurowania etykiet na potrzeby ochrony

Po aktywowaniu usługi Azure Rights Management w ramach procesu migracji można skonfigurować etykiety na potrzeby ochrony danych. Jednak jeśli migrowanie użytkowników odbywa się w partiach, upewnij się, że etykiety służące do stosowania ochrony mają [zakres ograniczony](configure-policy-scope.md) jedynie do właśnie zmigrowanych użytkowników.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


