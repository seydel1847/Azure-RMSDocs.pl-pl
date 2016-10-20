---
title: "Usuwanie ochrony z pliku za pomocą aplikacji RMS sharing | Azure Information Protection"
description: "Instrukcje dotyczące usuwania ochrony z pliku, który był wcześniej chroniony za pomocą aplikacji RMS sharing."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: da95b938-eaad-4c83-a21e-ff1d4872aae4
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aac3c6c7b5167d729d9ac89d9ae71c50dd1b6a10
ms.openlocfilehash: ceb726e47c4eb9413b7d7eb5b1469e2a99992dda


---

# Usuwanie ochrony z pliku za pomocą aplikacji do udostępniania usługi Rights Management

>*Dotyczy: Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Aby usunąć ochronę z pliku, który był wcześniej chroniony za pomocą aplikacji RMS sharing, skorzystaj z opcji **Usuń ochronę** w Eksploratorze plików.

> [!IMPORTANT]
> Aby usunąć ochronę, musisz być właścicielem pliku.

## Aby usunąć ochronę z pliku

1.  W Eksploratorze plików kliknij plik prawym przyciskiem myszy (np. plik Przykład.ptxt), wybierz polecenie **Chroń za pomocą usługi RMS**, kliknij pozycję **Włącz ochronę miejscową**, a następnie kliknij pozycję **Usuń ochronę**:

    ![Opcja menu Usuń ochronę w aplikacji RMS sharing](../media/ADRMS_MSRMSApp_RemoveProtection.png)

    Może zostać wyświetlony monit o podanie poświadczeń.

Uwaga: Jeśli te opcje nie są wyświetlane, być może aplikacja RMS sharing nie jest zainstalowana na danym komputerze, nie zainstalowano najnowszej wersji albo trzeba ponownie uruchomić komputer w celu ukończenia instalacji. Aby uzyskać więcej informacji na temat sposobu instalowania aplikacji do udostępniania, zobacz [Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](install-sharing-app.md).

Oryginalny chroniony plik zostaje usunięty (np. Przykład.ptxt) i zastąpiony plikiem o takiej samej nazwie, ale z rozszerzeniem nazwy pliku niechronionego (np. Przykład.txt).

## Przykłady i inne instrukcje
Aby uzyskać instrukcje i przykłady dotyczące korzystania z aplikacji do udostępniania usługi Rights Management, zapoznaj się z następującymi sekcjami podręcznika użytkownika aplikacji do udostępniania usługi Rights Management:

-   [Przykłady korzystania z aplikacji RMS sharing](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Co chcesz zrobić?](sharing-app-user-guide.md#what-do-you-want-to-do)

## Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)



<!--HONumber=Sep16_HO4-->


