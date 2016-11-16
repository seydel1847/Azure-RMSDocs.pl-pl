---
title: "Wprowadzenie do aplikacji Azure Information Protection dla systemów iOS i Android | Azure Information Protection"
description: 
keywords: "Informacje na temat sposobu wyświetlania wiadomości e-mail lub plików w aplikacji Azure Information Protection dla systemów iOS i Android"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/07/2016
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3d5d18d8-7b2e-456c-bb45-48da4eb55544
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 0a0c6e5f68f016ec6f921b16ff3063599b45f465


---

# <a name="get-started-with-the-microsoft-azure-information-protection-app-for-ios-and-android"></a>Wprowadzenie do aplikacji Microsoft Azure Information Protection dla systemów iOS i Android

*Dotyczy: Active Directory Rights Management Services, Azure Information Protection*

Większość użytkowników używa aplikacji Azure Information Protection automatycznie, jeśli trzeba otworzyć chronioną wiadomość e-mail lub plik. Ale jeśli jesteś administratorem, który chce przetestować aplikację dla użytkowników, lub po prostu chcesz wypróbować aplikację, zanim zajdzie potrzeba jej użycia, możesz skorzystać z poniższych instrukcji.

Na urządzeniu przenośnym należy uzyskać dostęp do jednego z plików obsługiwanych przez aplikację, aby zobaczyć przeglądarkę w działaniu. Na przykład:

- **Plik .rpmsg**: to jest chroniona prawami wiadomość e-mail wyświetlana jako załącznik w wiadomości e-mail, gdy aplikacja poczty e-mail na urządzeniu przenośnym nie obsługuje natywnie ochrony danych za pomocą usługi Rights Management. 
    
    Użyj innego urządzenia, aby wysłać do siebie wiadomość e-mail chronioną prawami, do której można uzyskać dostęp z urządzenia przenośnego. Na przykład użyj programu Outlook na komputerze z systemem Windows. Listę klientów poczty e-mail, które natywnie obsługują usługę Rights Management, można znaleźć w kolumnie POCZTA E-MAIL na stronie [Aplikacje obsługujące ochronę danych usługi Azure Rights Management](../get-started/requirements-applications.md).

- **Plik PDF chroniony prawami**: użyj aplikacji do udostępniania usługi Rights Management z komputera z systemem Windows lub aplikacji PDF, która natywnie obsługuje usługę Rights Management, aby wysłać do siebie plik PDF chroniony prawami jako załącznik wiadomości e-mail. Możesz także przekazać plik PDF do chronionej biblioteki programu SharePoint, a następnie udostępnić go przy użyciu swojego adresu e-mail.

- **Plik ptxt, pjpg lub ppng**: użyj aplikacji RMS sharing usługi Rights Management z komputera z systemem Windows i opcji [Udostępnianie chronionej zawartości](sharing-app-protect-by-email.md), aby wysłać sobie chroniony plik jako załącznik wiadomości e-mail. Aby uzyskać pełną listę typów plików, których można używać do testowania, zobacz pierwszą tabelę w sekcji [Obsługiwane typy plików i rozszerzenia nazw plików](sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) w podręczniku administratora aplikacji do udostępniania usługi Rights Management. 

Aby wyświetlić te pliki w przeglądarce usługi Azure Information Protection, naciśnij załącznik lub link wiadomości e-mail. Po wyświetleniu monitu o wybranie aplikacji do ich otwarcia wybierz aplikację **AIP Viewer**. Zostanie wtedy wyświetlony monit o zalogowanie się do konta służbowego. Po pomyślnym uwierzytelnieniu użytkownika aplikacja usługi Azure Information Protection wyświetli wiadomość e-mail lub plik do odczytu.

## <a name="next-steps"></a>Następne kroki

Jeśli masz inne pytania dotyczące tej aplikacji, sprawdź, czy temat [Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android](mobile-app-faq.md) zawiera już potrzebne odpowiedzi. 

W przypadku innych pytań odwiedź [witrynę Yammer](https://www.yammer.com/AskIPTeam) lub [wyślij wiadomość e-mail do zespołu usługi Information Protection](mailto:askIPteam@microsoft.com?subject=Question%20about%20Azure%20Information%20Protection%20app).



<!--HONumber=Nov16_HO2-->


