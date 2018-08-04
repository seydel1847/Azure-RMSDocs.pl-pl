---
title: Samouczek Szybki start dla usługi Azure Information Protection
description: Samouczek wprowadzający, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection w swojej organizacji. Wystarczy około 20 minut.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1260b9e5-dba1-41de-84fd-609076587842
ms.openlocfilehash: b060288efd080397f754d6aecd71abc4bbaabf81
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39488814"
---
# <a name="quick-start-tutorial-for-azure-information-protection"></a>Samouczek Szybki start dla usługi Azure Information Protection 

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Dzięki temu samouczkowi możesz szybko wypróbować usługę Azure Information Protection w swojej organizacji. Wystarczy 5 prostych kroków, które powinny zająć około 20 minut. Ten samouczek został stworzony jako samodzielna demonstracja przedstawiająca skrótowo niektóre funkcje oferowane przez usługę Azure Information Protection. Nie obejmuje on wszystkich dostępnych funkcji i nie jest przeznaczony do stosowania jako instrukcja wdrożenia dla organizacji. Jeśli chcesz wdrożyć usługę Azure Information Protection w swojej organizacji, zobacz [dokumentację planu wdrażania](deployment-roadmap.md). 

Ten samouczek jest przeznaczony dla administratorów oraz konsultantów IT i ma na celu ułatwienie oceny usługi Azure Information Protection jako rozwiązania do ochrony informacji w organizacji. W środowisku produkcyjnym administrator przeprowadzi konfigurację zasad usługi Information Protection, a następnie zainstaluje klienta u użytkowników. Kroki oznaczania dokumentów i bezpiecznego udostępniania ich pocztą e-mail oraz śledzenia wykonują użytkownicy. Niniejszy samouczek zawiera wszystkie te kroki w celu zaprezentowania kompletnego scenariusza klasyfikowania, etykietowania i chronienia danych organizacji. 

W przypadku wystąpienia problemów podczas wykonywania instrukcji zamieszczonych w tym samouczku lub używania usługi Azure Information Protection albo jeśli chcesz dowiedzieć się, co sądzą inni, odwiedź [witrynę usługi Yammer poświęconą usłudze Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all).

## <a name="prerequisites"></a>Wymagania wstępne 
Do ukończenia tego samouczka będą potrzebne:

- Subskrypcja, która obejmuje usługę Azure Information Protection na potrzeby klasyfikacji, etykietowania i ochrony. Ten samouczek zawiera niektóre zaawansowane funkcje, takie jak automatyczna klasyfikacja danych z zaleceniami użytkowników oraz witryna śledzenia dokumentów. Upewnij się, że masz subskrypcję do obsługi tych funkcji w tym samouczku. Aby uzyskać więcej informacji, zobacz Lista funkcji z [cennika usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection) strony.
    
    Jeśli nie masz subskrypcji obejmującej te funkcje, możesz utworzyć konto w celu skorzystania z bezpłatnej wersji próbnej planu [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7).
    
  > [!TIP] 
  > Jeśli potrzebujesz subskrypcji, uzyskaj ją z wyprzedzeniem, ponieważ czasami ukończenie tego procesu może wymagać trochę czasu.

- Konto administratora globalnego do logowania w witrynie Azure portal, aby aktywować ochronę i konfigurowanie zasad usługi Azure Information Protection. Alternatywnie, można użyć konta które ma jedną z następujących ról administracyjnych: [Administrator usługi Information Protection lub Administrator zabezpieczeń](/azure/active-directory/active-directory-assign-admin-roles-azure-portal). To konto musi również mieć adres e-mail i działającą usługę poczty e-mail, takich jak Exchange Online.

- Komputer z systemem Windows (co najmniej Windows 7 z dodatkiem SP1), na którym jest zainstalowana usługa Office 365 ProPlus z aplikacjami w wersji 2016 lub 2013, pakiet Office Professional Plus 2016, Office Professional Plus 2013 z dodatkiem Service Pack 1 lub Office Professional Plus 2010 z dodatkiem Service Pack 2. 
    
    Te aplikacje za pomocą usługi Azure Information Protection, konieczne jest posiadanie [subskrypcji usługi Office 365, która obejmuje przy użyciu usługi Azure Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). Na przykład usługi Office 365 E3 lub Office 365 E5 subskrypcję. Korzystać z licencji z tej subskrypcji, musi być zalogowano do aplikacji pakietu Office.

Zaczynamy!

>[!div class="step-by-step"]
[&#187; Krok 1](infoprotect-tutorial-step1.md)


