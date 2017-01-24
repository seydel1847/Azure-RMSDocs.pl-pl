---
title: "Pobieranie i instalowanie klienta usługi Azure Information Protection | Azure Information Protection"
description: "Instrukcje dla użytkowników umożliwiające zainstalowanie klienta usługi Azure Information Protection dla systemu Windows w celu umożliwienia klasyfikowania i ochrony dokumentów oraz wiadomości e-mail."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 22af60687ad030e686ba843ced6d450487353a0e
ms.openlocfilehash: 72266181c5334ed7e03b2022df61c4065f1c3ac7


---

# <a name="download-and-install-the-azure-information-protection-client"></a>Pobieranie i instalowanie klienta usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

**[Ta wersja klienta jest w wersji zapoznawczej i może ulec zmianie.]**

Jeśli klient usługi Azure Information Protection nie został zainstalowany przez administratora, można zainstalować go samodzielnie. Aby to zrobić, należy mieć uprawnienia administratora lokalnego na komputerze. 

### <a name="office-2010-only"></a>Tylko pakiet Office 2010

W przypadku korzystania z tej wersji pakietu Office klient usługi Azure Information Protection musi ustawić klucze rejestru wymagające uprawnień administratora: 

Postępuj zgodnie z instrukcjami, aby pobrać i zainstalować klienta, a następnie postępuj zgodnie z instrukcjami w następnej sekcji dotyczącej pakietu Office 2010.

## <a name="to-download-and-install-the-azure-information-protection-client"></a>Pobieranie i instalowanie klienta usługi Azure Information Protection

1.  Odwiedź [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) i pobierz **wersję zapoznawczą** klienta usługi Azure Information Protection.

2. Kliknij dwukrotnie pobrany plik wykonywalny. 

3. Na stronie **Instalowanie klienta usługi Azure Information Protection**: 
    
    - Wybierz opcję zainstalowania zasad demonstracyjnych, jeśli nie możesz nawiązać połączenia z chmurą, ale chcesz zobaczyć i wypróbować klienta usługi Azure Information Protection przy użyciu zasad lokalnych w celach demonstracyjnych. Gdy klient nawiąże połączenie z usługą Azure Information Protection, te zasady demonstracyjne zostaną zastąpione zasadami usługi Azure Information Protection obowiązującymi w organizacji.
    
    - Po zapoznaniu się z warunkami licencji kliknij przycisk **Zgadzam się**.

4. Jeśli zostanie wyświetlony monit z pytaniem o kontynuowanie, kliknij przycisk **Tak** i poczekaj na zakończenie instalacji.

3. Kliknij pozycję **Zamknij**. Przed rozpoczęciem korzystania z klienta usługi Azure Information Protection:

    - Jeśli na komputerze jest zainstalowany pakiet Office 2010, uruchom ponownie komputer, a następnie przejdź do następnej sekcji przedstawiającej ostatni krok.
    
    - W przypadku innych wersji pakietu Office należy uruchomić ponownie wszystkie aplikacje pakietu Office i wszystkie wystąpienia Eksploratora plików. Instalacja jest ukończona i możesz teraz etykietować oraz chronić swoje dokumenty i wiadomości e-mail przy użyciu klienta.

> [!NOTE]
> W przypadku systemu Windows 7 z dodatkiem SP1 klient usługi Azure Information Protection wymaga określonej aktualizacji ([KB 2533623](https://support.microsoft.com/en-us/kb/2533623)). Jeśli na komputerze nie jest zainstalowana wymagana aktualizacja, przy próbie uruchomienia klienta zostanie wyświetlony komunikat informujący o konieczności zainstalowania danej aktualizacji przed rozpoczęciem korzystania ze wszystkich funkcji klienta usługi Azure Information Protection.

### <a name="installing-the-azure-information-protection-client-with-office-2010"></a>Instalowanie klienta usługi Azure Information Protection z pakietem Office 2010

Po wykonaniu poprzednich instrukcji i zainstalowaniu klienta usługi Azure Information Protection:

1. Otwórz program Microsoft Word. Jeśli jest to pierwsze uruchomienie aplikacji pakietu Office 2010 po zainstalowaniu klienta usługi Azure Information Protection, zostanie wyświetlone okno dialogowe **Microsoft Azure Information Protection**. Wyświetlany w oknie dialogowym komunikat mówi, że w celu ukończenia procesu logowania wymagane są poświadczenia administratora.

2. W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **OK**.

2. Jeśli zostanie wyświetlone okno dialogowe **Kontrola dostępu użytkownika**, kliknij przycisk **Tak**, aby klient usługi Azure Information Protection mógł zaktualizować rejestr.

Instalacja jest ukończona i możesz teraz etykietować oraz chronić swoje dokumenty i wiadomości e-mail przy użyciu usługi Azure Information Protection.

## <a name="other-instructions"></a>Inne instrukcje
Aby uzyskać instrukcje dotyczące wykonywania określonych czynności, zobacz następujące sekcje z podręcznika użytkownika usługi Azure Information Protection:

-   [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Dodatkowe informacje dla administratorów
[Instalowanie klienta usługi Azure Information Protection](info-protect-client.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


