---
title: "Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android | Azure Information Protection"
description: 
keywords: "Niektóre często zadawane pytania dotyczące korzystania z aplikacji Azure Information Protection dla systemów iOS i Android"
author: cabailey
manager: mbaldwin
ms.date: 11/03/2016
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 539b4ff8-5d3b-4c4d-9c84-c14da83ff76d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2f1930f4657278d25ef6dd369866f16e4ba71644
ms.openlocfilehash: 1cafa88ded2bf951f8af93e4b27cc526735d19e8


---

# <a name="faqs-for-microsoft-azure-information-protection-app-for-ios-and-android"></a>Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android

*Dotyczy: Active Directory Rights Management Services, Azure Information Protection*

Na tej stronie znajdują się niektóre często zadawane pytania dotyczące korzystania z aplikacji Azure Information Protection dla systemów iOS i Android.

## <a name="what-can-i-do-with-the-azure-information-protection-app"></a>Co można zrobić przy użyciu aplikacji Azure Information Protection?

Ta aplikacja umożliwia wyświetlanie wiadomości e-mail chronionych prawami (plików .rpmsg), jeśli aplikacja poczty e-mail nie obsługuje natywnie ochrony danych za pomocą usługi Rights Management. Ta aplikacja umożliwia także wyświetlanie chronionych prawami plików PDF, obrazów i plików tekstowych. Obecnie przy użyciu tej aplikacji nie można tworzyć nowych chronionych wiadomości e-mail, odpowiadać na nie ani tworzyć i edytować plików chronionych.

## <a name="can-i-open-pdf-files-that-are-in-sharepoint-protected-libraries-and-onedrive-for-business"></a>Czy mogę otwierać pliki PDF z chronionych bibliotek programów SharePoint i OneDrive dla Firm?

Tak, można otwierać chronione pliki PDF udostępnione przez innych użytkowników za pośrednictwem programów SharePoint i OneDrive dla Firm. Naciśnij link, a następnie wybierz tę aplikację, aby otworzyć go za jej pomocą. 

## <a name="how-do-i-get-started-with-the-viewer-app"></a>Jak zacząć korzystać z aplikacji przeglądarki?

Na urządzeniu przenośnym należy uzyskać dostęp do jednego z plików obsługiwanych przez aplikację, aby zobaczyć przeglądarkę w działaniu. Na przykład:

- **Plik .rpmsg**: to jest chroniona prawami wiadomość e-mail wyświetlana jako załącznik w wiadomości e-mail, gdy aplikacja poczty e-mail na urządzeniu przenośnym nie obsługuje natywnie ochrony danych za pomocą usługi Rights Management. 
    
    Użyj innego urządzenia, aby wysłać do siebie wiadomość e-mail chronioną prawami, do której można uzyskać dostęp z urządzenia przenośnego. Na przykład użyj programu Outlook na komputerze z systemem Windows. Listę klientów poczty e-mail, które natywnie obsługują usługę Rights Management, można znaleźć w kolumnie POCZTA E-MAIL na stronie [Aplikacje obsługujące ochronę danych usługi Azure Rights Management](../get-started/requirements-applications.md).

- **Plik PDF chroniony prawami**: użyj aplikacji do udostępniania usługi Rights Management z komputera z systemem Windows lub aplikacji PDF, która natywnie obsługuje usługę Rights Management, aby wysłać do siebie plik PDF chroniony prawami jako załącznik wiadomości e-mail. Możesz także przekazać plik PDF do chronionej biblioteki programu SharePoint, a następnie udostępnić go przy użyciu swojego adresu e-mail.

- **Plik ptxt, pjpg lub ppng**: użyj aplikacji RMS sharing usługi Rights Management z komputera z systemem Windows i opcji [Udostępnianie chronionej zawartości](sharing-app-protect-by-email.md), aby wysłać sobie chroniony plik jako załącznik wiadomości e-mail. Aby uzyskać pełną listę typów plików, których można używać do testowania, zobacz pierwszą tabelę w sekcji [Obsługiwane typy plików i rozszerzenia nazw plików](sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) w podręczniku administratora aplikacji do udostępniania usługi Rights Management. 

Aby wyświetlić te pliki w przeglądarce usługi Azure Information Protection, naciśnij załącznik lub link wiadomości e-mail. Po wyświetleniu monitu o wybranie aplikacji do ich otwarcia wybierz aplikację **AIP Viewer**. Zostanie wtedy wyświetlony monit o zalogowanie się do konta służbowego. Po pomyślnym uwierzytelnieniu użytkownika aplikacja usługi Azure Information Protection wyświetli wiadomość e-mail lub plik do odczytu.

## <a name="what-credentials-should-i-use-to-sign-in-to-this-app"></a>Jakich poświadczeń należy używać do logowania się do tej aplikacji?

Jeśli Twoja organizacja korzysta z lokalnej usługi AD RMS (z rozszerzeniem dla urządzeń przenośnych) lub z usługi Azure Rights Management przy użyciu swoich poświadczeń. Jeśli nie, można utworzyć nowe darmowe konto na [stronie usługi Azure Information Protection](https://portal.office.com/signup?sku=rms&ru=https%3A%2F%2Fportal.azurerms.com%2F%23%2Fdownload).

## <a name="can-i-sign-up-for-the-free-account-with-my-personal-email-address-such-as-a-hotmail-or-gmail-account"></a>Czy mogę utworzyć bezpłatne konto za pomocą mojego osobistego adresu e-mail, takiego jak konto usługi Hotmail lub Gmail?

Jeszcze nie. Obecnie można zalogować się tylko z firmowego adresu e-mail (konto służbowe). Firma Microsoft pracuje nad obsługą osobistych adresów e-mail i zaktualizuje ten wpis, gdy będzie to możliwe.

## <a name="which-file-extensions-can-i-open-with-this-app"></a>Jakie rozszerzenia plików można otworzyć za pomocą tej aplikacji?

Można otworzyć pliki RPMSG, PDF, PPDF, PJPG, PTXT i kilka innych formatów plików tekstowych oraz obrazów.

##  <a name="how-do-i-provide-feedback-about-this-app"></a>Jak wyrazić swoją opinię na temat tej aplikacji?

W aplikacji przejdź do pozycji **Ustawienia** > **Wyślij opinię**.


## <a name="my-question-has-not-been-answeredwhat-should-i-do"></a>Na moje pytanie nie udzielono odpowiedzi. Co mam zrobić?

Należy zadać pytanie na naszej [witrynie Yammer](http://www.yammer.com/AskIPTeam) lub [wysłać wiadomość e-mail do zespołu usługi Information Protection](mailto:askIPteam@microsoft.com?subject=Question%20about%20Azure%20Information%20Protection%20app).



<!--HONumber=Nov16_HO1-->


