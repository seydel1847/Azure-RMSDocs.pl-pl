---
title: "Samouczek Szybki start dla usługi Azure Information Protection"
description: "Samouczek wprowadzający, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection w swojej organizacji. Wystarczy około 20 minut."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1260b9e5-dba1-41de-84fd-609076587842
ms.openlocfilehash: 13dbb47088c33f72bdb0acdbb7cba1245df14f7f
ms.sourcegitcommit: 7b773ca5bf1abf30e527c34717ecb2dc96f88033
translationtype: HT
---
# <a name="quick-start-tutorial-for-azure-information-protection"></a>Samouczek Szybki start dla usługi Azure Information Protection 

>*Dotyczy: Azure Information Protection*

Dzięki temu samouczkowi możesz szybko wypróbować usługę Azure Information Protection w swojej organizacji. Wystarczy 5 prostych kroków, które powinny zająć około 20 minut. Ten samouczek został stworzony jako samodzielna demonstracja przedstawiająca skrótowo niektóre funkcje oferowane przez usługę Azure Information Protection. Nie obejmuje on wszystkich dostępnych funkcji i nie jest przeznaczony do stosowania jako instrukcja wdrożenia dla organizacji. Jeśli chcesz wdrożyć usługę Azure Information Protection w swojej organizacji, zobacz [dokumentację planu wdrażania](../plan-design/deployment-roadmap.md). 

Ten samouczek jest przeznaczony dla administratorów oraz konsultantów IT i ma na celu ułatwienie oceny usługi Azure Information Protection jako rozwiązania do ochrony informacji w organizacji. W środowisku produkcyjnym administrator przeprowadzi konfigurację zasad usługi Information Protection, a następnie zainstaluje klienta u użytkowników. Kroki oznaczania dokumentów i bezpiecznego udostępniania ich pocztą e-mail oraz śledzenia wykonują użytkownicy. Niniejszy samouczek zawiera wszystkie te kroki w celu zaprezentowania kompletnego scenariusza klasyfikowania, etykietowania i chronienia danych organizacji. 

W przypadku wystąpienia problemów podczas wykonywania instrukcji zamieszczonych w tym samouczku lub używania usługi Azure Information Protection albo jeśli chcesz dowiedzieć się, co sądzą inni, odwiedź [witrynę usługi Yammer poświęconą usłudze Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all).

## <a name="prerequisites"></a>Wymagania wstępne 
Do ukończenia tego samouczka będą potrzebne następujące elementy:

- Subskrypcja, która obejmuje usługę Azure Information Protection na potrzeby klasyfikacji, etykietowania i ochrony. Ten samouczek zawiera niektóre zaawansowane funkcje, takie jak automatyczna klasyfikacja danych z zaleceniami użytkowników oraz witryna śledzenia dokumentów. Upewnij się, że Twoja subskrypcja obsługuje te funkcje. Aby uzyskać więcej informacji, zapoznaj się z [informacjami o subskrypcji](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) i [listą funkcji](https://www.microsoft.com/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection.
    
    Jeśli nie masz subskrypcji obejmującej te funkcje, możesz utworzyć konto w celu skorzystania z bezpłatnej wersji próbnej planu [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7).
    
- Subskrypcja platformy Azure, która umożliwia skonfigurowanie zasad usługi Azure Information Protection w portalu Azure. Jeśli organizacja nie ma jeszcze subskrypcji platformy Azure, możesz ją uzyskać, tworząc konto do użycia na potrzeby bezpłatnej wersji próbnej: przejdź na stronę [wprowadzenia do platformy Azure](https://account.windowsazure.com/organization) i postępuj zgodnie z instrukcjami.

  > [!TIP] 
  > Jeśli potrzebujesz jednej lub większej liczby subskrypcji, uzyskaj je z wyprzedzeniem, ponieważ czasami ukończenie tego procesu może wymagać trochę czasu.

- Konto administratora globalnego do logowania się w portalu Azure w celu konfigurowania zasad usługi Azure Information Protection. To konto musi mieć również adres e-mail i działającą usługę poczty e-mail (na przykład Exchange Online lub Exchange Server).

- Komputer z systemem Windows (co najmniej Windows 7 z dodatkiem SP1), na którym jest zainstalowana usługa Office 365 ProPlus z aplikacjami w wersji 2016 lub 2013, pakiet Office Professional Plus 2016, Office Professional Plus 2013 z dodatkiem Service Pack 1 lub Office Professional Plus 2010. 

Zaczynamy!

>[!div class="step-by-step"]
[&#187; Krok 1](infoprotect-tutorial-step1.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

