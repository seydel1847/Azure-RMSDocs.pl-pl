---
title: Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android
description: Niektóre często zadawane pytania dotyczące korzystania z aplikacji Azure Information Protection dla systemów iOS i Android
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/31/2018
ms.topic: conceptual
ms.service: information-protection
ms.custom: askipteam
ms.assetid: 539b4ff8-5d3b-4c4d-9c84-c14da83ff76d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 29c7d333131c0b85b9cdb83e9a2212420f60077f
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393649"
---
# <a name="faqs-for-microsoft-azure-information-protection-app-for-ios-and-android"></a>Często zadawane pytania dotyczące aplikacji Azure Information Protection dla systemów iOS i Android

*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Na tej stronie znajdują się niektóre często zadawane pytania dotyczące korzystania z aplikacji Azure Information Protection dla systemów iOS i Android.

## <a name="what-can-i-do-with-the-azure-information-protection-app"></a>Co można zrobić przy użyciu aplikacji Azure Information Protection?

Ta aplikacja umożliwia wyświetlanie wiadomości e-mail chronionych prawami (plików .rpmsg), jeśli aplikacja poczty e-mail nie obsługuje natywnie ochrony danych za pomocą usługi Rights Management. Ta aplikacja umożliwia także wyświetlanie chronionych prawami dokumentów PDF, obrazów i pliki tekstowe, które są chronione prawami. 

Ponieważ ta aplikacja jest przeglądarka, nie możesz użyć go do tworzenia nowych chronionych wiadomości e-mail, odpowiadać na lub tworzenia lub edytowania plików chronionych. Ponadto aplikacja nie może otworzyć załączniki plików, które można wyświetlić. Na przykład załączniki w chronionych plików PDF, dokumentów lub wiadomości e-mail chronionych prawami.

## <a name="can-i-open-pdf-files-that-are-in-sharepoint-protected-libraries-and-onedrive-for-business"></a>Czy mogę otwierać pliki PDF z chronionych bibliotek programów SharePoint i OneDrive dla Firm?

Tak, można otwierać chronione pliki PDF udostępnione przez innych użytkowników za pośrednictwem programów SharePoint i OneDrive dla Firm. Naciśnij link, a następnie wybierz tę aplikację, aby otworzyć go za jej pomocą. 

Ta aplikacja umożliwia również otwieranie plików PDF objętych ochroną poza programem SharePoint i OneDrive dla Firm (chronionych plików PDF i .ppdf).

## <a name="can-my-mobile-device-run-the-azure-information-protection-app"></a>Czy na moim urządzeniu przenośnym można uruchomić aplikację Azure Information Protection?

Aplikacja Azure Information Protection wymaga co najmniej systemu **iOS 8** lub **Android 4.4**.

Jeśli masz jedną z tych wersji lub wyższą od nich, możesz zainstalować i uruchomić aplikację na swoim urządzeniu przenośnym:

- Jeśli urządzenie przenośne jest zarządzane przez usługę Microsoft Intune, możesz mieć możliwość zainstalowania aplikacji Azure Information Protection z poziomu portalu firmy.

- Jeśli urządzenie przenośne nie jest zarządzane przez usługę Microsoft Intune lub aplikacja Azure Information Protection nie jest dostępna z poziomu portalu firmy, możesz zainstalować aplikację bezpośrednio ze sklepu iTunes i sklepu Google Play lub klikając ikonę iOS lub Android w sekcji **Urządzenia przenośne** na [stronie pobierania usługi Azure Information Protection](https://portal.azurerms.com/#/download). 

## <a name="how-do-i-get-started-with-the-viewer-app"></a>Jak zacząć korzystać z aplikacji przeglądarki?

Po zainstalowaniu aplikacji nie musisz wykonywać żadnych innych czynności. Zaczekaj, aż otrzymasz chronioną wiadomość e-mail lub plik, który chcesz wyświetlić, a następnie wybierz pozycję **Przeglądarka usługi AIP**, aby go otworzyć. Następnie zostanie wyświetlona prośba o zalogowanie do konta służbowego lub o wybranie certyfikatu. Po uwierzytelnieniu poświadczeń możesz odczytywać zawartość.

Jednak jeśli nie chcesz czekać, można użyć zgodnie z poniższymi instrukcjami, aby wysłać do siebie chronioną wiadomość e-mail lub plik, aby wyświetlić: [Rozpoczynanie pracy z aplikacją Microsoft Azure Information Protection dla systemów iOS i Android](mobile-app-get-started.md) 

## <a name="what-credentials-should-i-use-to-sign-in-to-this-app"></a>Jakich poświadczeń należy używać do logowania się do tej aplikacji?

Jeśli Twoja organizacja ma już usług AD RMS w środowisku lokalnym (z rozszerzeniem urządzeniami przenośnymi) lub korzysta z usługi Azure Rights Management, zaloguj się przy użyciu swoje poświadczenia służbowe. 

Jeśli Twojego osobistego adresu e-mail został użyty do ochrony pliku, Użyj poświadczeń z BEZPŁATNEJ [konta Microsoft](https://signup.live.com) do logowania.

## <a name="can-i-sign-up-for-the-free-account-with-my-personal-email-address-such-as-a-hotmail-or-gmail-account"></a>Czy mogę utworzyć bezpłatne konto za pomocą mojego osobistego adresu e-mail, takiego jak konto usługi Hotmail lub Gmail?

Tak, po zastosowaniu do konta Microsoft, można określić adres e-mail usługi Hotmail lub Gmail lub innego adresu e-mail, którego jesteś właścicielem. 

Jednak mimo że ten program może otworzyć plików chronionych przy użyciu tego konta, nie wszystkie aplikacje mogą otwierania chronionej zawartości, gdy konto Microsoft służy do uwierzytelniania. [Więcej informacji](../secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

## <a name="which-file-extensions-can-i-open-with-this-app"></a>Jakie rozszerzenia plików można otworzyć za pomocą tej aplikacji?

Można otworzyć pliki rpmsg, pdf, ppdf, pjpg, pjpeg, ptiff, ppng, ptxt i pxml oraz kilka innych formatów plików tekstowych oraz obrazów.

Pełną listę rozszerzeń nazw plików tekstowych i obrazów można znaleźć w pierwszej tabeli sekcji [Typy plików, dla których jest obsługiwana klasyfikacja i ochrona](client-admin-guide-file-types.md#supported-file-types-for-classification-and-protection) w podręczniku administratora.

##  <a name="how-do-i-provide-feedback-about-this-app"></a>Jak wyrazić swoją opinię na temat tej aplikacji?

W aplikacji przejdź do pozycji **Ustawienia** > **Wyślij opinię**.


## <a name="my-question-has-not-been-answeredwhat-should-i-do"></a>Na moje pytanie nie udzielono odpowiedzi. Co mam zrobić?

Opublikuj swoje pytanie na naszym [witryny usługi Yammer](https://www.yammer.com/AskIPTeam).
