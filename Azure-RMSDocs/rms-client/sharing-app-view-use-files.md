---
title: "Otwieranie plików chronionych za pomocą usługi RMS w aplikacji RMS sharing — AIP"
description: "Instrukcje dotyczące wyświetlania i używania pliku chronionego, co wymaga posiadania zainstalowanej aplikacji Rights Management (RMS) sharing."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e5fa4666-6906-405a-9e0c-2c52d4cd27c8
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 0a510d559573e942b8a2bf392f36a1300dfbfb7a
ms.sourcegitcommit: 1c3ebf4ad64b55db4fec3ad007fca71ab7d38c02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/18/2017
---
# <a name="view-and-use-files-that-have-been-protected-by-rights-management"></a>Wyświetlanie i używanie plików chronionych przez usługę Rights Management

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Gdy [aplikacja do udostępniania usługi Rights Management (RMS) jest zainstalowana na komputerze](install-sharing-app.md), wystarczy kliknąć dwukrotnie chroniony plik, aby go wyświetlić. Plik może być załącznikiem wiadomości e-mail lub może być widoczny w Eksploratorze plików.

> [!NOTE]
> Zanim będzie można wyświetlić chroniony plik, usługa Rights Management musi potwierdzić, że masz uprawnienia do wyświetlenia pliku (sprawdzana jest nazwa użytkownika i hasło). W niektórych sytuacjach te dane są buforowane, w związku z czym monit o podanie poświadczeń nie zostanie wyświetlony. W pozostałych przypadkach jest wyświetlany monit o podanie poświadczeń.
>
> Jeśli Twoja organizacja nie korzysta z usługi Azure Information Protection ani usług AD RMS, możesz poprosić o utworzenie bezpłatnego konta z wykorzystaniem Twoich poświadczeń, co umożliwi Ci otwieranie plików chronionych za pomocą usług RMS:
>
> -   Aby poprosić o utworzenie konta, kliknij link [usług RMS dla użytkowników indywidualnych](http://go.microsoft.com/fwlink/?LinkId=309469).
>
>     Podczas tworzenia konta użyj swojego służbowego adresu e-mail, a nie adresu prywatnego. Jeśli tworzysz konto w związku z otrzymaniem chronionego załącznika pocztą e-mail, użyj tego samego adresu e-mail, który został użyty przez nadawcę do wysłania tej wiadomości e-mail do Ciebie.
> -   Aby uzyskać więcej informacji, zobacz [Usługa RMS dla użytkowników indywidualnych i usługa Azure Rights Management](../understand-explore/rms-for-individuals.md).

## <a name="to-view-a-protected-file"></a>Aby wyświetlić chroniony plik
W Eksploratorze plików lub wiadomości e-mail zawierającej załącznik kliknij dwukrotnie chroniony plik, po czym wprowadź swoje poświadczenia, jeśli zostanie wyświetlony odpowiedni komunikat.

Jeśli są widoczne dwie wersje pliku różniące się rozszerzeniami nazw plików, otwórz plik z rozszerzeniem ppdf tylko w sytuacji, gdy nie możesz otworzyć drugiego pliku. Jeśli nie możesz otworzyć również wersji ppdf, najpierw zainstaluj [aplikację RMS sharing](install-sharing-app.md), która umożliwia otwieranie plików z rozszerzeniem nazwy ppdf.

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz sekcję [Co to za plik ppdf, który jest automatycznie tworzony?](sharing-app-dialog-box.md#whats-the-ppdf-file-thats-automatically-created)

Sposób otwierania pliku zależy od metody jego ochrony, którą można ustalić na podstawie rozszerzenia nazwy pliku. W każdym przypadku otwieranie pliku może podlegać inspekcji tak długo jak plik jest chroniony. Ponadto jeśli plik został wysłany jako załącznik wiadomości e-mail, jego nadawca może otrzymać powiadomienie e-mail o każdym otwarciu tego pliku.

- **Plik ma rozszerzenie *pfile***

    Plik podlega ochronie ogólnej.

    Po otwarciu pliku wyświetlane jest okno dialogowe **chronionego pliku** z aplikacji do udostępniania, które informuje, kto włączył ochronę pliku, i że należy respektować uprawnienia współwłaściciela pliku. Kliknij pozycję **Otwórz**, aby odczytać plik.

    ![Okno dialogowe pliku pfile udostępnionego w wiadomości e-mail w przypadku korzystania z aplikacji RMS sharing](../media/ADRMS_MSRMSApp_PfilePermission.png)

- **Plik ma rozszerzenie *ppdf* albo jest chronionym plikiem tekstowym lub plikiem obrazu (np. *ptxt* lub *pjpg*)**

    Plik jest chroniony natywnie jako kopia tylko do odczytu.

    Plik można otworzyć w przeglądarce instalowanej razem z aplikacją RMS sharing. Ten plik jest tylko do odczytu, nawet jeśli zostanie zapisany w innej lokalizacji lub jego nazwa zostanie zmieniona.

- **Inne rozszerzenia nazwy pliku**

    Plik jest chroniony natywnie.

    Plik można otworzyć, korzystając z aplikacji skojarzonej z rozszerzeniem nazwy oryginalnego pliku, a u góry pliku zostaje wyświetlony baner informujący o ograniczeniach. Na banerze mogą zostać wyświetlone uprawnienia do pliku lub link umożliwiający ich wyświetlenie. Na przykład może zostać wyświetlony poniższy komunikat wymagający kliknięcia pozycji **Uprawnienie jest obecnie ograniczone** w celu wyświetlenia uprawnień zastosowanych do pliku oraz użytkowników, którzy mają do niego dostęp:

    ![Transparent dostępu ograniczonego, jeśli plik jest chroniony](../media/ADRMS_MSRMSApp_RestrictedAccess.png)



Pełna lista rozszerzeń nazw plików obsługiwanych przez usługi Rights Management znajduje się w sekcji [Obsługiwane typy plików i rozszerzenia nazw plików](sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) w [Przewodniku administratora aplikacji RMS sharing](sharing-app-admin-guide.md). Jeśli odpowiednie rozszerzenie nazwy pliku nie jest wyświetlane, użyj funkcji wyszukiwania w sieci Web, aby dowiedzieć się, czy to rozszerzenie nazwy pliku jest obsługiwane przez inną aplikację.

## <a name="to-use-files-that-have-been-protected-for-example-edit-and-print-the-file"></a>Aby korzystać z chronionych plików (na przykład edytować lub drukować je)
Jeśli po otwarciu chronionego pliku chcesz zrobić coś więcej niż tylko odczytać ten plik (na przykład zmodyfikować go, skopiować lub wydrukować), postępuj zgodnie z instrukcjami odpowiednimi dla rozszerzenia nazwy pliku:

- **Plik ma rozszerzenie *pfile***

    Zapisz otwarty plik i nadaj mu nowe rozszerzenie nazwy pliku skojarzone z aplikacją, której chcesz użyć.

    Jeśli na przykład plik był chroniony za pomocą nazwy pliku dokument.vsdx.pfile, wyświetl ten plik i w Eksploratorze plików zapisz go jako dokument.vsdx.

    Nowy plik nie jest już chroniony. Jeśli chcesz go chronić, musisz to zrobić ręcznie. Aby uzyskać instrukcje, zobacz [Ochrona pliku na urządzeniu (ochrona miejscowa) za pomocą aplikacji do udostępniania usługi Rights Management](sharing-app-protect-in-place.md).

- **Plik ma rozszerzenie *ppdf* albo jest chronionym plikiem tekstowym lub plikiem obrazu (np. *ptxt* lub *pjpg*)**

    Możesz jedynie wyświetlić plik, a w przypadku zmiany nazwy lub przeniesienia pliku będzie on nadal chroniony.

- **Inne rozszerzenia nazwy pliku**

    Aby można było używać tych plików, urządzenie musi korzystać z aplikacji, która obsługuje ochronę usługi Rights Management. Te aplikacje noszą nazwę aplikacji obsługujących usługę RMS. Aplikacje pakietu Office 2016, Office 2013 i Office 2010 (takie jak Word, Excel, PowerPoint i Outlook) stanowią przykład aplikacji obsługujących usługę Rights Management. Usługę Rights Management mogą także obsługiwać aplikacje firm innych niż Microsoft oraz aplikacje firmowe używane w danej organizacji.

    Aplikacje obsługujące usługę Rights Management umożliwiają otwieranie plików chronionych przez inne aplikacje obsługujące tę usługę. Zapewniają także zachowanie zastosowanej ochrony, nawet jeśli plik zostanie wyedytowany lub zapisany pod inną nazwą lub w innej lokalizacji. Aplikacje umożliwiają używanie plików zgodnie z przypisanymi im uprawnieniami. Jeśli masz odpowiednie uprawnienia, możesz korzystać z pliku. Na przykład możesz edytować plik, ale nie możesz go drukować.


## <a name="examples-and-other-instructions"></a>Przykłady i inne instrukcje
Aby uzyskać instrukcje i przykłady dotyczące korzystania z aplikacji do udostępniania usługi Rights Management, zapoznaj się z następującymi sekcjami podręcznika użytkownika aplikacji do udostępniania usługi Rights Management:

-   [Przykłady korzystania z aplikacji do udostępniania usługi RMS](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Co chcesz zrobić?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]