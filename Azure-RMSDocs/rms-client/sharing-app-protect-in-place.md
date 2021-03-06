---
title: Ochrona miejscowa za pomocą aplikacji RMS sharing — AIP
description: Instrukcje dotyczące sposobu bezpiecznego przechowywania pliku na komputerze, serwerze lub innym urządzeniu magazynującym.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 33920329-5247-4f6c-8651-6227afb4a1fa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9156f7af9cb7915595f911b6d0ff8fa70332d8d7
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023451"
---
# <a name="protect-a-file-on-a-device-protect-in-place-by-using-the-rights-management-sharing-application"></a>Ochrona pliku na urządzeniu (ochrona miejscowa) za pomocą aplikacji do udostępniania usługi Rights Management

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Miejscowa ochrona pliku polega na zastąpieniu nim oryginalnego pliku, który nie jest chroniony. Następnie można pozostawić plik w jego obecnej lokalizacji, skopiować do innego folderu lub na inne urządzenie albo udostępnić folder zawierający plik — aplik cały czas będzie chroniony. Chroniony plik można także dołączyć do wiadomości e-mail, chociaż zalecaną metodą udostępniania pliku chronionego pocztą e-mail jest bezpośrednie dołączenie go z poziomu Eksploratora plików lub aplikacji pakietu Office (zobacz [Ochrona plików udostępnianych pocztą e-mail za pomocą aplikacji do udostępniania usługi Rights Management](sharing-app-protect-by-email.md)).

> [!TIP]
> Jeśli podczas próby włączenia ochrony plików są wyświetlane błędy, zobacz [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Microsoft Rights Management dla systemu Windows](https://go.microsoft.com/fwlink/?LinkId=303971).

## <a name="to-protect-a-file-on-a-device-protect-in-place"></a>Aby chronić plik na urządzeniu (ochrona miejscowa)

1.  W Eksploratorze plików wybierz plik, który ma być chroniony. Kliknij prawym przyciskiem myszy, wybierz pozycję **Chroń za pomocą usługi RMS**, a następnie wybierz pozycję **Włącz ochronę miejscową**. Przykład:

    ![Opcja menu Ochrona miejscowa](../media/ADRMS_MSRMSApp_SP_CompanyDefined.png)

    > [!NOTE]
    > Jeśli opcja **Chroń za pomocą usługi RMS** nie jest wyświetlana, możliwe, że aplikacja RMS sharing nie jest zainstalowana na danym komputerze albo trzeba ponownie uruchomić komputer w celu ukończenia instalacji. Aby uzyskać więcej informacji o sposobie instalowania aplikacji do udostępniania usługi RMS, zobacz [Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](install-sharing-app.md).

2.  Wykonaj jedną z następujących czynności:

    -   Wybierz szablon zasad: są to wstępnie zdefiniowane uprawnienia, które zwykle ograniczają dostęp i użycie do osób w danej organizacji. Jeśli na przykład nazwa organizacji to „Contoso, Ltd”, może zostać wyświetlona pozycja **Contoso, Ltd — tylko wyświetlanie poufne**. Jeśli po raz pierwszy włączasz ochronę pliku na tym komputerze, najpierw musisz wybrać pozycję **Ochrona zdefiniowana przez firmę** w celu pobrania szablonów.

        Przy następnym kliknięciu opcji **Włącz ochronę miejscową**, zostanie wyświetlonych do 10 szablonów do wyboru. Jeśli dostępnych jest ponad 10 szablonów i odpowiedni szablon nie jest wyświetlany, kliknij pozycję **Ochrona zdefiniowana przez firmę** w celu pobrania i wyświetlenia wszystkich szablonów.

        Podczas wybierania szablonu zasad można zdecydować się na ochronę wielu plików i folderu. Wybranie folderu powoduje ochronę wszystkich plików znajdujących się w tym folderze, ale nowe pliki w nim tworzone nie będą już automatycznie chronione.

    -   Wybierz opcję **Uprawnienia niestandardowe**: wybierz tę opcję, jeśli szablony nie umożliwiają ustawienia odpowiedniego poziomu ochrony lub jeśli chcesz jawnie ustawić opcje ochrony. Określ odpowiednie opcje dla tego pliku w oknie dialogowym [Dodawanie ochrony](sharing-app-dialog-box.md), a następnie kliknij przycisk **Zastosuj**.

3.  Przez chwilę może zostać wyświetlone okno dialogowe informujące, że plik jest chroniony, po czym nastąpi powrót do Eksploratora plików. Wybrany plik lub pliki są teraz chronione. W niektórych przypadkach (kiedy dodanie ochrony powoduje zmianę rozszerzenia nazwy pliku) oryginalny plik znajdujący się w Eksploratorze plików zostaje zastąpiony nowym plikiem oznaczonym ikoną kłódki sygnalizującą ochronę za pomocą usługi Rights Management. Przykład:

    ![Chroniony plik z ikoną kłódki dla aplikacji RMS sharing](../media/ADRMS_MSRMSApp_Pfile.png)

Jeśli zmienisz zdanie o uprawnieniach lub później zajdzie potrzeba ich zmodyfikowania, po prostu ponownie uruchom ochronę pliku.

Jeśli później będzie konieczne usunięcie ochrony z pliku, zobacz [Usuwanie ochrony z pliku za pomocą aplikacji do udostępniania usługi Rights Management](sharing-app-remove-protection.md).

## <a name="examples-and-other-instructions"></a>Przykłady i inne instrukcje
Aby uzyskać instrukcje i przykłady dotyczące korzystania z aplikacji do udostępniania usługi Rights Management, zapoznaj się z następującymi sekcjami podręcznika użytkownika aplikacji do udostępniania usługi Rights Management:

-   [Przykłady korzystania z aplikacji do udostępniania usługi RMS](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Co chcesz zrobić?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)
