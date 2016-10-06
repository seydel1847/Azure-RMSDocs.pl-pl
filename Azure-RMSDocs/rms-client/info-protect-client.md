---
title: "Instalowanie klienta usługi Azure Information Protection | Azure Information Protection"
description: "Instrukcje dotyczące instalowania klienta, który dodaje pasek usługi Information Protection do aplikacji pakietu Office, dzięki czemu można wybrać etykiety klasyfikacji dla dokumentów i wiadomości e-mail."
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: 003e76733657bb97c5447e2cdc44049d111d33fa
ms.openlocfilehash: 2892b091e300b0ef15ca09524d233474bd5de193


---

# Instalowanie klienta usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

Aby klasyfikować dokumenty i wiadomości e-mail przy użyciu usługi Azure Information Protection, musisz najpierw zainstalować klienta usługi Azure Information Protection. Ta instalacja dodaje pasek usługi Information Protection do aplikacji pakietu Office (Word, Excel, PowerPoint, Outlook), który wyświetla etykiety klasyfikacji dla Twojej organizacji, a także nową grupę **Ochrona** na karcie **Narzędzia główne** (Word, Excel, PowerPoint), która zawiera przycisk o nazwie **Chroń**:

Na poniższej ilustracji przedstawiono ten pasek usługi Information Protection oraz etykiety z [zasad domyślnych](../deploy-use/configure-policy-default.md):

![Pasek usługi Azure Information Protection z zasadami domyślnymi](../media/info-protect-bar-default.png)

Pobierz klienta usługi Azure Information Protection z [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Przed zainstalowaniem klienta sprawdź, czy masz wymagane wersje systemu operacyjnego i aplikacji dla klienta usługi Azure Information Protection: [Wymagania dla usługi Azure Information Protection](../get-started/requirements-azure-rms.md).


## Aby zainstalować klienta usługi Azure Information Protection ręcznie

1. Po [pobraniu klienta](https://www.microsoft.com/en-us/download/details.aspx?id=53018) uruchom program **AzInfoProtection.exe** i postępuj zgodnie z monitami, aby zainstalować klienta. Ta instalacja wymaga lokalnych uprawnień administracyjnych.

    Wybierz opcję zainstalowania zasad demonstracyjnych, jeśli nie możesz nawiązać połączenia z usługą Office 365 lub Azure Active Directory, ale chcesz zobaczyć i wypróbować klienta usługi Azure Information Protection przy użyciu zasad lokalnych w celach demonstracyjnych. Gdy klient nawiąże połączenie z usługą Azure Information Protection, te zasady demonstracyjne zostaną zastąpione zasadami usługi Azure Information Protection obowiązującymi w organizacji. 

2. Aby rozpocząć użytkowanie klienta usługi Azure Information Protection: jeśli Twój komputer ma uruchomiony pakiet Office 2010, uruchom ponownie komputer. W przypadku innych wersji pakietu Office uruchom ponownie wszystkie aplikacje pakietu Office.

## Aby zainstalować klienta usługi Azure Information Protection dla użytkowników

Możesz użyć skryptu i zautomatyzować instalację klienta Azure Information Protection, korzystając z opcji wiersza polecenia. Aby wyświetlić te opcje instalacji, uruchom polecenie `AzInfoProtection.exe /help`.

Na przykład, aby zainstalować klienta w trybie dyskretnym: `AzInfoProtection.exe /passive | quiet`

## Aby odinstalować klienta usługi Azure Information Protection

Można użyć dowolnej z tych opcji:

- Odinstaluj program za pomocą Panelu sterowania: kliknij kolejno pozycje **Microsoft Azure Information Protection** > **Odinstaluj**

- Uruchom ponownie plik **AzInfoProtection.exe** i na stronie **Modyfikowanie ustawień** kliknij pozycję **Odinstaluj**. 

- Uruchom `AzInfoProtection.exe /uninstall`


## Aby zweryfikować instalację lub stan połączenia albo zgłosić problem

1. Otwórz aplikację pakietu Office i na karcie **Narzędzia główne** w grupie **Ochrona** kliknij kolejno przyciski **Chroń** oraz **Pomoc i opinie**.

2. W oknie dialogowym **Microsoft Azure Information Protection** zwróć uwagę na następujące elementy:

    - Wartość **Ostatnie połączenie** umożliwia określenie ostatniego momentu połączenia klienta z usługą Azure Information Protection w organizacji. Gdy klient łączy się z usługą, automatycznie pobiera najnowsze zasady, jeśli wykryje zmiany w porównaniu z obecnymi zasadami. Jeśli wprowadzono zmiany zasad po wyświetlonym czasie, zamknij i ponownie otwórz aplikację pakietu Office.

    - Wyświetlona nazwa użytkownika identyfikuje konto używane do uwierzytelniania w usłudze Azure Information Protection. Ta nazwa użytkownika musi pasować do konta używanego w usłudze Office 365 lub Azure Active Directory.

    - Wersja klienta usługi Azure Information Protection.

    - Link **Wyślij opinię** umożliwia automatyczne dołączanie dzienników klienta do wiadomości e-mail, którą można wysłać do zespołu usługi Information Protection w celu zbadania.

## Skróty klawiaturowe dla paska usługi Azure Information Protection

Aby uzyskać dostęp do paska usługi Azure Information Protection za pomocą skrótów klawiaturowych, użyj następujących kombinacji klawiszy:

- Naciśnij klawisze **Ctrl** + **Shift** + **~** 

Następnie użyj klawisza Tab, aby wybrać etykiety i inne kontrolki na pasku (ikona **Ukryj etykiety** i ikona **Usuń etykiety**), a następnie naciśnij klawisz Enter, aby je wybrać.


## Lokalizacje plików

Pliki klienta:   

- Dla 64-bitowych systemów operacyjnych: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Dla 32-bitowych systemów operacyjnych: **\Program Files\Microsoft Azure Information Protection**

Pliki dziennika klienta i plik obecnie zainstalowanych zasad:

- Dla 64- i 32-bitowych systemów operacyjnych: **%localappdata%\Microsoft\MSIP**


## Następne kroki

Aby zmienić etykiety na pasku usługi Information Protection, musisz skonfigurować zasady usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad usługi Azure Information Protection](../deploy-use/configure-policy.md).

Aby uzyskać przykład konfigurowania zasad domyślnych i zobaczyć efekty w aplikacji pakietu Office, wypróbuj [Samouczek Szybki start dla usługi Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md). 



<!--HONumber=Sep16_HO4-->

