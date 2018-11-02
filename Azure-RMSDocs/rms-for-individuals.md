---
title: Usługi RMS dla użytkowników indywidualnych i Azure Information Protection
description: Informacje o usłudze RMS dla użytkowników indywidualnych, bezpłatnej subskrypcji samoobsługowej dla użytkowników, którzy otrzymali chronionych plików, ale ci użytkownicy nie mogą zostać uwierzytelnieni, ponieważ dział IT nie będzie zarządzała kontem ich na platformie Azure.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/02/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 40cc70864d68b4bdcc1081f908539663ba8366a8
ms.sourcegitcommit: d969a82dc801f3d653163de2b18a3a772607b74c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "50915567"
---
# <a name="rms-for-individuals-and-azure-information-protection"></a>Usługi RMS dla użytkowników indywidualnych i Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Usługa RMS dla użytkowników indywidualnych to bezpłatna subskrypcja samoobsługowa dla użytkowników, którzy muszą otwierać pliki chronione za pomocą usługi Azure Information Protection. Jeśli Ci użytkownicy nie uwierzytelniony przez usługę Azure Active Directory, bezpłatnej usługi rejestracji można utworzyć konto w usłudze Azure Active Directory dla użytkownika. W wyniku tych użytkownicy mogą teraz uwierzytelniane przy użyciu swojego adresu e-mail firmy i odczytania chronionych plików na komputerach lub urządzeniach przenośnych.

Samoobsługowe tworzenie konta usługi Azure Active Directory korzysta z usługi RMS dla użytkowników indywidualnych. Jeśli użytkownicy utworzyli konta dla Twojej organizacji za pomocą tej subskrypcji z uprawnieniami administratora dla Twojej organizacji, może przejąć własności i [przejęcie kontroli nad ich kont](/azure/active-directory/users-groups-roles/domains-admin-takeover#external-admin-takeover). 


> [!NOTE]
> Bezpłatna subskrypcja jest jedną opcję, aby mieć pewność, że upoważnione osoby spoza organizacji mogą zawsze odczytać plików, które organizacja chroni. Innym rozwiązaniem jest e-mail dokumentów przy użyciu [szyfrowanie wiadomości usługi Office 365 dzięki nowym funkcjom](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). To rozwiązanie poczty e-mail działa w przypadku wszystkich adresów e-mail na wszystkich urządzeniach i jest zalecany sposób bezpiecznie udostępniać informacje i wyświetlić dokumenty pakietu Office w przeglądarce osobom spoza organizacji.
> 
> Innym rozwiązaniem jest użycie kont Microsoft. Jednak nie wszystkie aplikacje można otworzyć chronionej zawartości, gdy konto Microsoft służy do uwierzytelniania. [Więcej informacji](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents) 

Aby utworzyć bezpłatne konto, użytkownicy, przejdź do [strony programu Microsoft Azure Information Protection](https://aka.ms/rms-signup)i podaj swój służbowy adres e-mail. Otrzyma wiadomość e-mail w odpowiedzi od firmy Microsoft, a następnie można ukończyć proces rejestracji, wprowadzając wymagane szczegóły, aby utworzyć swoje konto. 

Po utworzeniu konta ostatnia strona wyświetla łącza, aby pobrać klienta usługi Azure Information Protection lub przeglądarki na różnych urządzeniach, link do podręcznika użytkownika i link do bieżącej listy aplikacji, które natywnie obsługują usługę Rights Management. 

## <a name="to-sign-up-for-rms-for-individuals"></a>Aby utworzyć konto usługi RMS dla użytkowników indywidualnych

1. Jeśli używasz komputera z systemem Windows, komputera Mac lub urządzenia przenośnego, przejdź na [stronę usługi Microsoft Azure Information Protection](https://aka.ms/rms-signup).

2. Wpisz adres e-mail, który został użyty do ochrony dokumentu, które należy otworzyć.

3. Kliknij przycisk **Zarejestruj się**.

    Firma Microsoft używa Twój adres e-mail, aby sprawdzić, czy Twoja organizacja ma już [subskrypcja usługi Azure Information Protection Premium](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) lub [subskrypcji usługi Office 365, która obejmuje ochronę danych za pomocą platformy Azure Ochrona informacji](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). Jeśli jedno z tych subskrypcji zostaną znalezione, nie potrzebujesz usługi RMS dla użytkowników indywidualnych. Użytkownik jest zalogowany natychmiast i samoobsługowego tworzenia konta usługi RMS dla użytkowników indywidualnych została anulowana. Jeśli jeden z tych subskrypcji nie zostanie znalezione, przejdź do następnego kroku.

4. Poczekaj na wiadomość e-mail z potwierdzeniem, która zostanie wysłana na podany adres e-mail. Zostanie ona nadana przez zespół usługi Office 365 (support@email.microsoftonline.com) i będzie miała temat **Ukończ rejestrację w usłudze Microsoft Azure Information Protection**.

5. Po otrzymaniu wiadomości e-mail kliknij **tak, to ja** zweryfikować swój adres e-mail i ukończyć proces rejestracji.

6. Zostanie teraz wyświetlona strona **Jeszcze coś**, na której trzeba będzie podać szczegóły konta. Wpisz swoje imię i nazwisko, podaj i potwierdź hasło, a następnie kliknij pozycję **Rozpocznij**.

7. Po utworzeniu konta zobaczysz nową stronę Microsoft Azure Information Protection, gdzie można pobrać i zainstalować klienta usługi Azure Information Protection lub kliknij przycisk [Podręcznik użytkownika](./rms-client/client-user-guide.md) link do instrukcji odnoszących się do Windows komputery.

Teraz Twoje konto jest tworzone, jeśli zostanie wyświetlony monit logować się do odczytywać pliki chronione, wprowadź ten sam adres e-mail i hasło, których użyto podczas tworzenia konta usługi RMS dla użytkowników indywidualnych.

> [!IMPORTANT]
> Mimo że teraz można również chronić pliki za pomocą tego konta, nie zostanie aż Twoja organizacja ma [subskrypcji próbnej lub płatnej](https://azure.microsoft.com/pricing/details/information-protection/) usługi Azure Information Protection. Jeśli ochrony plików i wiadomości e-mail przy użyciu tej bezpłatnej subskrypcji, a następnie przejmuje kontrolę nad kontem w Twojej organizacji, wcześniej chronionej zawartości mogą stać się niedostępne.


## <a name="next-steps"></a>Kolejne kroki
Usługi RMS dla użytkowników indywidualnych to przykład za pomocą samoobsługowej, jest obsługiwane przez usługę Azure Active Directory. Aby uzyskać więcej informacji o tym, jak to działa, zobacz [co to jest Samoobsługowa usługi Azure Active Directory?](/azure/active-directory/users-groups-roles/directory-self-service-signup) w dokumentacji usługi Azure Active Directory.

