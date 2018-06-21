---
title: Zadania, które były wykonywane w aplikacji RMS sharing — AIP
description: Instrukcje dla użytkowników, którzy zrezygnowali z korzystania z aplikacji RMS sharing na rzecz klienta usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d7bc2478-c22f-4e19-9992-012658362b25
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 58b0ab62b260e407aa9ae6a36b4a063fe147889b
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
ms.locfileid: "30206863"
---
# <a name="user-guide-tasks-that-you-used-to-do-with-the-rms-sharing-application"></a>Podręcznik użytkownika: Zadania, które pozwala wykonać za pomocą aplikacji RMS sharing

>*Dotyczy: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, systemu Windows Server 2008 R2*
>
>Czy należysz do grona osób, które przeszły ostatnio z aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management (znanej także jako „RMS sharing”) na klienta usługi Azure Information Protection? 

Poniższe informacje ułatwią Ci szybkie rozpoczęcie korzystania z aplikacji.

|Aplikacja RMS sharing|Jak wykonać to zadanie przy użyciu klienta usługi Azure Information Protection
|-----------|--------------------|
|Ochrona pliku na urządzeniu <br /><br />Znana także jako funkcja „Włącz ochronę miejscową”|Aplikacje pakietu Office: wybierz etykietę, która ustawia wymaganą ochronę, lub ustaw uprawnienia niestandardowe.<br /><br />Pozostałe pliki: użyj opcji menu Eksploratora plików **Klasyfikuj i chroń**, aby otworzyć okno dialogowe **Klasyfikuj i chroń — Azure Information Protection**. Wybierz etykietę, która odnosi się do odpowiedniej ochrony, lub określ własne uprawnienia niestandardowe. <br /><br />Aby uzyskać więcej informacji, zobacz temat [Klasyfikowanie i ochrona pliku lub wiadomości e-mail](client-classify-protect.md).
|Ochrona pliku udostępnionego pocztą e-mail <br /><br />Funkcja znana także pod nazwą „Udostępnij chronioną zawartość”|Za pomocą programu Outlook, zastosowania etykiety wymagane w przypadku ochrony wiadomości e-mail lub wybierz programu Outlook **nie przesyłaj dalej** opcji. Niechronionej załączników, które mają [obsługiwany typ pliku](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) są automatycznie chronione.<br /><br />Uwaga: Aby śledzić chroniony dokument tej wiadomości e-mail możesz, najpierw go chronić i dołączenie go do wiadomości e-mail.<br /><br />Aby uzyskać więcej informacji, zobacz temat [Klasyfikowanie i ochrona pliku lub wiadomości e-mail](client-classify-protect.md).
|Zmienianie uprawnień do chronionych plików <br /><br />Funkcja znana także pod nazwą „Włącz ponownie ochronę”|Dotyczy aplikacji pakietu Office, w których jest wyświetlany pasek usługi Azure Information Protection: wybierz etykietę, która odnosi się do odpowiedniej ochrony.<br /><br />Dotyczy innych plików oraz sytuacji, w których klient usługi Azure Information Protection działa w [trybie z samą ochroną](client-protection-only-mode.md): użyj opcji **Klasyfikuj i chroń** w menu Eksploratora plików, aby otworzyć okno dialogowe **Klasyfikuj i chroń — Azure Information Protection**. Wybierz etykietę, która odnosi się do odpowiedniej ochrony, lub określ własne uprawnienia niestandardowe.<br /><br />Aby uzyskać więcej informacji, zobacz temat [Klasyfikowanie i ochrona pliku lub wiadomości e-mail](client-classify-protect.md).
|Śledzenie i odwoływanie dokumentów|Dotyczy aplikacji pakietu Office: otwórz dokument, a następnie na karcie **Narzędzia główne** wybierz grupę **Ochrona** i opcje **Chroń** > **Śledź i odwołuj**<br /><br />W oknie Eksploratora plików: kliknij prawym przyciskiem myszy plik lub folder > **Klasyfikuj i chroń**. Następnie w oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** kliknij opcję **Śledź i odwołuj**. <br /><br />Aby uzyskać więcej informacji, zobacz temat [Śledzenie i odwoływanie dokumentów](client-track-revoke.md).
|Wyświetlanie i używanie chronionych plików|Musisz mieć zainstalowany chronionych dokumentów pakietu Office pakietu Office. Viewer ochrony informacji Azure można otworzyć wiele plików chronionych, dzięki czemu można je odczytać i również wydrukować i zapisać te pliki, jeśli masz uprawnienia, aby wykonać tych czynności. Przeglądarka jest instalowana automatycznie razem z klientem, ale można ją zainstalować także oddzielnie.<br /><br />Aby uzyskać więcej informacji, zobacz temat [Otwieranie plików chronionych](client-view-use-files.md).
|Usuwanie ochrony z pliku|Użyj opcji menu Eksploratora plików **Klasyfikuj i chroń**, aby otworzyć okno dialogowe **Klasyfikuj i chroń — Azure Information Protection**. <br /><br />W przypadku jednego pliku usuń zaznaczenie opcji **Ochrona przy użyciu uprawnień niestandardowych**. W przypadku wielu plików lub folderu kliknij opcję **Usuń uprawnienia niestandardowe**.<br /><br />Aby uzyskać więcej informacji, zobacz temat [Usuwanie etykiet klasyfikacji i ochrony z plików i wiadomości e-mail](client-remove-label-protection.md).|

## <a name="cant-find-the-option-youre-looking-for"></a>Nie możesz znaleźć szukanej opcji?

Jeśli szukasz konkretnej opcji znanej z aplikacji RMS sharing, zapoznaj się z poniższą tabelą.

|Opcja w aplikacji RMS sharing|Informacje
|-----------|--------------------|
|**Udostępnij chronioną zawartość**|Ta opcja nie jest już dostępna na wstążce pakietu Office. Zamiast udostępniać zawartość bezpośrednio z poziomu aplikacji pakietu Office, przejdź do Eksploratora plików, kliknij prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń**, aby objąć ochroną kopię dokumentu z uprawnieniami niestandardowymi, a następnie udostępnić plik przy użyciu wybranego klienta poczty e-mail lub lokalizacji udostępniania. <br /><br /> Dokumentu niechronionego można także dołączyć do wiadomości e-mail możesz chronić i dokument jest chroniony automatycznie z ograniczeniami. Nie można jednak śledzenie i odwoływanie tego dokumentu.
|**Wyślij mi wiadomość e-mail, gdy ktoś spróbuje otworzyć te dokumenty**|Witryna śledzenia dokumentów umożliwia skonfigurowanie preferowanego ustawienia powiadomień e-mail: znajdź udostępniony przez siebie dokument chroniony i wybierz kolejno pozycje **Ustawienia** > **Powiadomienia e-mail**
|**Zezwalaj mi na natychmiastowe odwołanie dostępu do tych dokumentów**|Ta opcja nie jest już dostępna. Skonfiguruj szablony, które nie zezwalają na dostęp w trybie offline. Dodatkowo zastanów się nad skróceniem okresu ważności użytkowania licencji dla dzierżawcy poprzez uruchomienie polecenia [Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime).







[!INCLUDE[Commenting house rules](../includes/houserules.md)]  
