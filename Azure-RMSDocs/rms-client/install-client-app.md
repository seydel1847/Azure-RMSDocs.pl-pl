---
title: Pobieranie i instalowanie klienta usługi Azure Information Protection
description: Instrukcje dla użytkowników umożliwiające zainstalowanie klienta usługi Azure Information Protection dla systemu Windows w celu umożliwienia klasyfikowania i ochrony dokumentów oraz wiadomości e-mail.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: d45c13a0cf3c7725c5b817339e9aadec96f27477
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305231"
---
# <a name="user-guide-download-and-install-the-azure-information-protection-client"></a>Podręcznik użytkownika: Pobieranie i instalowanie klienta usługi Azure Information Protection

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), system Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

Jeśli klient usługi Azure Information Protection nie został zainstalowany przez administratora, można zainstalować go samodzielnie. Aby zainstalować tego klienta w celu ochrony dokumentów i wiadomości e-mail oraz stosowania dla nich etykiet, trzeba mieć na komputerze uprawnienia administratora lokalnego.

Ponadto:

- Klient usługi Azure Information Protection wymaga programu Microsoft .NET Framework w wersji 4.6.2 lub wyższej. W przypadku jego braku Instalator spróbuje pobrać i zainstalować ten wymagany składnik. Jeśli ten wymagany program został zainstalowany w ramach procesu instalacji klienta, należy uruchomić ponownie komputer.

- W przypadku systemu Windows 7 z dodatkiem SP1 klient usługi Azure Information Protection wymaga określonej aktualizacji — KB 2533623. Jeśli na komputerze jest wymagana aktualizacja, która jednak nie została jeszcze zainstalowana, instalacja zostanie przeprowadzona, ale będzie jej towarzyszył komunikat informujący o konieczności zainstalowania tej aktualizacji na kliencie usługi Azure Information Protection. Dopóki ta aktualizacja nie zostanie zainstalowana, nie będzie można korzystać ze wszystkich funkcji klienta usługi Azure Information Protection. 

## <a name="to-download-and-install-the-azure-information-protection-client"></a>Pobieranie i instalowanie klienta usługi Azure Information Protection    

1.  Przejdź na stronę usługi [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) w witrynie internetowej firmy Microsoft.

    Ta strona zawiera linki dotyczące wszystkich popularnych urządzeń, dzięki czemu można łatwo pobrać aplikację przeglądarki, jeśli zajdzie potrzeba otwierania plików chronionych. Jeśli nie masz na komputerze uprawnień administratora lokalnego, możesz mimo to zainstalować aplikację przeglądarki dla systemu Windows. Jednak wykonanie tych instrukcji powoduje zainstalowanie pełnego klienta, co umożliwi etykietowanie i ochronę plików. 

2. Znajdź sekcję **Klient usługi Azure Information Protection**, a następnie kliknij ikonę systemu Windows. Kliknij przycisk **Pobierz** i zapisz plik **AzInfoProtection.exe**.     

3. Uruchom pobrany plik wykonywalny. Jeśli zostanie wyświetlony monit o kontynuowanie, kliknij pozycję **Tak**.    

4. Na stronie **Instalowanie klienta usługi Azure Information Protection**:     
    - Wybierz opcję zainstalowania zasad demonstracyjnych, jeśli nie możesz nawiązać połączenia z chmurą, ale chcesz zobaczyć i wypróbować klienta usługi Azure Information Protection przy użyciu zasad lokalnych w celach demonstracyjnych. Gdy klient nawiąże połączenie z usługą Azure Information Protection, te zasady demonstracyjne zostaną zastąpione zasadami usługi Azure Information Protection obowiązującymi w organizacji.    

    - Po zapoznaniu się z warunkami licencji kliknij przycisk **Zgadzam się**.    

5. Jeśli zostanie wyświetlony monit z pytaniem o kontynuowanie, kliknij przycisk **Tak** i poczekaj na zakończenie instalacji.    

6. Kliknij pozycję **Zamknij**. Przed rozpoczęciem korzystania z klienta usługi Azure Information Protection:    

    - Jeśli na komputerze jest zainstalowany pakiet Office 2010, uruchom ponownie komputer, a następnie przejdź do następnej sekcji przedstawiającej ostatni krok.    
        
    - W przypadku innych wersji pakietu Office należy uruchomić ponownie wszystkie aplikacje pakietu Office i wszystkie wystąpienia Eksploratora plików. Instalacja jest ukończona i możesz teraz dodawać etykiety oraz chronić swoje dokumenty i wiadomości e-mail przy użyciu klienta.    

### <a name="installing-the-azure-information-protection-client-with-office-2010"></a>Instalowanie klienta usługi Azure Information Protection z pakietem Office 2010    
Po wykonaniu poprzednich instrukcji i zainstalowaniu klienta usługi Azure Information Protection:    

1. Otwórz program Microsoft Word. Jeśli jest to pierwsze uruchomienie aplikacji pakietu Office 2010 po zainstalowaniu klienta usługi Azure Information Protection, zostanie wyświetlone okno dialogowe **Microsoft Azure Information Protection**. Wyświetlany w oknie dialogowym komunikat mówi, że w celu ukończenia procesu logowania wymagane są poświadczenia administratora.

2. W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **OK**.

3. Jeśli zostanie wyświetlone okno dialogowe **Kontrola dostępu użytkownika**, kliknij przycisk **Tak**, aby klient usługi Azure Information Protection mógł zaktualizować rejestr.

Instalacja jest ukończona i możesz teraz etykietować oraz chronić swoje dokumenty i wiadomości e-mail przy użyciu usługi Azure Information Protection.

## <a name="other-instructions"></a>Inne instrukcje    
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

- [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Dodatkowe informacje dla administratorów    
Zobacz [zainstalować klienta usługi Azure Information Protection dla użytkowników](client-admin-guide-install.md) z [podręczniku administratora](client-admin-guide.md).
 
  
