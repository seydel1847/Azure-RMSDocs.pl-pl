---
title: "Pobieranie i instalowanie aplikacji RMS sharing — AIP"
description: "Instrukcje dotyczące interaktywnego instalowania aplikacji RMS sharing dla systemu Windows, dzięki czemu możliwe jest bezpieczne udostępnianie dokumentów innym osobom."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9c954f750c6f49d3db1bf6383efa2805f291682c
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="download-and-install-the-rights-management-sharing-application"></a>Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Aby zainstalować aplikację RMS sharing, nie trzeba być administratorem lokalnym. Jeśli nim nie jesteś i korzystasz z pakietu Office 2010, obowiązują jednak pewne ograniczenia. Aby uzyskać więcej informacji, zobacz sekcję [Jeśli nie jesteś administratorem lokalnym i używasz pakietu Office 2010](#if-you-are-not-a-local-administrator-and-use-office-2010) w dalszej części tej strony.

## <a name="to-download-and-install-the-rights-management-sharing-application"></a>Aby pobrać i zainstalować aplikację Rights Management sharing

1.  Przejdź do strony usługi [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) w witrynie firmy Microsoft w sieci Web.

2.  W sekcji **Komputery** kliknij ikonę **aplikacji RMS dla systemu Windows** i zapisz plik **Setup.exe**, aby zainstalować aplikację do udostępniania usługi Microsoft Rights Management.

3.  Kliknij dwukrotnie pobrany plik Setup.exe. Jeśli zostanie wyświetlony monit o kontynuowanie, kliknij pozycję **Tak**.

4.  Na stronie **Instalacja usług Microsoft RMS** kliknij pozycję **Dalej** i poczekaj na zakończenie instalacji.

    > [!NOTE]
    > Aplikacja RMS sharing wymaga programu Microsoft .NET Framework w wersji co najmniej 4.0. Instalator sprawdza, czy ten program jest zainstalowany, a jeśli nie jest — zostanie wyświetlony komunikat z linkiem umożliwiającym jego zainstalowanie.

5.  Po zakończeniu instalacji kliknij pozycję **Uruchom ponownie**, aby ponownie uruchomić komputer i ukończyć instalację. Możesz również kliknąć pozycję **Zamknij**, aby uruchomić komputer ponownie później i ukończyć instalację.

Teraz możesz już chronić swoje pliki i otwierać pliki chronione udostępnione przez innych.

## <a name="if-you-are-not-a-local-administrator-and-use-office-2010"></a>Jeśli nie jesteś administratorem lokalnym i używasz pakietu Office 2010
Jeśli zalogujesz się na komputerze, nie mając lokalnych praw administracyjnych, a Instalator wykryje, że jest zainstalowany pakiet Office 2010, zobaczysz ostrzeżenie informujące, że w tej sytuacji niektóre działania nie są możliwe. Scenariusze są następujące:

-   Jeśli Twoja organizacja korzysta z usługi Azure Rights Management z usługi Azure Information Protection, a nie z lokalnej wersji usługi Rights Management:

    -   Funkcje zarządzania prawami do informacji (IRM) pakietu Office nie będą dostępne. Dotyczy to na przykład opcji **Nie przekazuj** w przypadku wiadomości e-mail oraz uprawnień związanych z **ograniczeniami dostępu**, ustawianymi w menu **Plik** w programach Word i Excel. Można użyć opcji Udostępnij chronioną zawartość, dostępnej na wstążce, oraz opcji wyświetlanych po kliknięciu prawym przyciskiem myszy w Eksploratorze plików.

-   Jeśli Twoja organizacja używa lokalnej wersji usługi Rights Management, a nie usługi Azure Rights Management z usługi Azure Information Protection:

    -   Nie będzie można odczytywać dokumentów chronionych wysłanych przez osoby z innej organizacji, która korzysta z usługi Azure Rights Management.

Jeśli nie jesteś administratorem lokalnym i używasz usługi Office 365 lub pakietu Office 2013, nie zobaczysz tego komunikatu (te scenariusze są obsługiwane).

Możesz kontynuować instalację, uwzględniając te znane ograniczenia. Możesz też zatrzymać instalację i ponownie ją uruchomić, korzystając z opcji **Uruchom jako administrator** podczas uruchamiania pliku Setup.exe w kroku 3, albo poprosić administratora o zainstalowanie aplikacji za Ciebie. Administrator może [użyć skryptu instalacji](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application), tak aby aplikacja została zainstalowana automatycznie.

## <a name="examples-and-other-instructions"></a>Przykłady i inne instrukcje
Aby uzyskać instrukcje i przykłady dotyczące korzystania z aplikacji do udostępniania usługi Rights Management, zapoznaj się z następującymi sekcjami podręcznika użytkownika aplikacji do udostępniania usługi Rights Management:

-   [Przykłady korzystania z aplikacji do udostępniania usługi RMS](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Co chcesz zrobić?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
