---
title: "Usługi RMS dla użytkowników indywidualnych i Azure Information Protection"
description: "Informacje dotyczące usługi RMS dla użytkowników indywidualnych, czyli bezpłatnej subskrypcji samoobsługowej przeznaczonej dla użytkowników, którzy otrzymali poufne pliki chronione za pomocą usługi Azure Rights Management, ale nie mogą zostać uwierzytelnieni, ponieważ nie mają konta platformy Azure zarządzanego przez dział IT organizacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/22/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a3dbed8d244847b9f649cdeff6714215b35a42de
ms.sourcegitcommit: cd3320fa34acb90f05d5d3e0e83604cdd46bd9a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2017
---
# <a name="rms-for-individuals-and-azure-information-protection"></a>Usługi RMS dla użytkowników indywidualnych i Azure Information Protection

>*Dotyczy: Azure Information Protection*

Usługa RMS dla użytkowników indywidualnych to bezpłatna subskrypcja samoobsługowa dla użytkowników w organizacji, którzy muszą otwierać pliki chronione przez usługę Azure Rights Management z usługi Azure Information Protection. Jeśli Ci użytkownicy nie może zostać uwierzytelnione przez usługę Azure Active Directory i ich organizacja nie ma zarządzania prawami dostępu w usłudze Active Directory (AD RMS), tej bezpłatnej tworzenia konta usługi można utworzyć konto w usłudze Azure Active Directory dla użytkownika. W związku z tym te użytkownicy mogą teraz uwierzytelniania przy użyciu adresu e-mail firmy i następnie odczytywać pliki chronione na komputerach lub urządzeniach przenośnych.

Przy użyciu [klienta Azure Information Protection](../rms-client/client-user-guide.md) na komputerach z systemem Windows tych użytkowników można również chronić swoje pliki, ale ta możliwość jest przeznaczony tylko do użycia próbnego i mogą zostać usunięte w przyszłości.

Usługa RMS dla użytkowników indywidualnych to przykład subskrypcji samoobsługowej, obsługiwanej przez usługę Azure Active Directory. Aby uzyskać więcej informacji o tym, jak to działa, zobacz [What is Self-Service Signup for Azure?](/active-directory/active-directory-self-service-signup) (Czym jest rejestracja samoobsługowa na platformie Azure?). 

> [!IMPORTANT]
> Bezpłatna subskrypcja jest jedną opcję, aby zapewnić, że upoważnione osoby spoza organizacji, zawsze może odczytywać pliki, chronione w organizacji. Inną możliwością jest wykonanie e-mail dokumentów przy użyciu [szyfrowanie wiadomości usługi Office 365 z nowych funkcji](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). To rozwiązanie poczty e-mail działa dla wszystkich adresów e-mail na wszystkich urządzeniach i jest zalecanym sposobem bezpiecznie udostępnić informacje i dokumenty pakietu Office pocztą e-mail do osób spoza organizacji. 

## <a name="next-steps"></a>Następne kroki
Aby uzyskać szczegółowe instrukcje oraz zapoznać się z opisem technicznym procesów działających w tle, zobacz [Jak utworzyć konto usługi RMS dla użytkowników indywidualnych](rms-for-individuals-user-sign-up.md). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
