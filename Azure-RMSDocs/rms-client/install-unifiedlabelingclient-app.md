---
title: Pobierz i zainstaluj ujednolicone, etykietowania klienta Azure Information Protection (wersja zapoznawcza)
description: Instrukcje dla użytkowników zainstalować wersję zapoznawczą usługi Azure Information Protection unified etykietowania klienta Windows, dzięki czemu mogą klasyfikować i chronić swoje dokumenty i wiadomości e-mail.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/17/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 5d2f5c07ebc7f4844b0d35879ae00c7b9066cb6d
ms.sourcegitcommit: 6a732226a3c97fc06fcf815fbbb24a2e2faae209
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49359033"
---
# <a name="download-and-install-the-azure-information-protection-unified-labeling-client-preview"></a>Pobieranie i instalowanie ujednolicone, etykietowania klienta usługi Azure Information Protection (wersja zapoznawcza)

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), system Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

> [!NOTE]
> Ten klient jest w wersji zapoznawczej i może ulec zmianie. Używa ujednolicony sklep etykietowania i pliki do pobrania zasad za pomocą czułości etykiety z Centrum zgodności i zabezpieczeń usługi Office 365. Aby korzystać z tych etykiet, należy najpierw je opublikować z Centrum zabezpieczeń i zgodności. [Więcej informacji](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492)

Musi być kontem lokalnego administratora na komputerze można zainstalować tego klienta w wersji zapoznawczej, tak, aby go umożliwia etykietowanie i ochronę dokumentów oraz wiadomości e-mail.

Ponadto:

- Ujednolicone etykietowania klienta usługi Azure Information Protection wymaga minimalnej wersji platformy Microsoft .NET Framework 4.6.2 i przypadku jego braku Instalator spróbuje pobrać i zainstalować ten wymagany. Jeśli ten wymagany program został zainstalowany w ramach procesu instalacji klienta, należy uruchomić ponownie komputer.

- Jeśli masz Windows 7 z dodatkiem SP1, ujednolicony klient etykietowania usługi Azure Information Protection wymaga określonej aktualizacji — KB 2533623. Jeśli komputer jest wymagana aktualizacja, ale nie jest zainstalowany, instalacja zakończy, ale wyświetleniem komunikatu informującego o tym, że usługi Azure Information Protection unified etykietowania klienta wymaga tej aktualizacji. Dopóki ta aktualizacja zostanie zainstalowana, nie będzie można korzystać ze wszystkich funkcji klienta etykietowania ujednolicone usługi Azure Information Protection. 

## <a name="to-download-and-install-the-azure-information-protection-unified-labeling-client"></a>Aby pobrać i zainstalować ujednoliconego etykietowania klienta usługi Azure Information Protection

Przed zainstalowaniem klienta etykietowania ujednolicone usługi Azure Information Protection, upewnij się, że masz etykiety czułości w Centrum zgodności i zabezpieczeń usługi Office 365, publikowanych dla użytkowników. 

Jeśli masz etykiet, które obecnie są publikowane w witrynie Azure portal usługi Azure Information Protection, możesz to zrobić [migracji tych etykiet](../configure-policy-migrate-labels.md) do Centrum zabezpieczeń i zgodności.

1. Pobierz klienta (wersja zapoznawcza) z [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=57440).

2. Uruchom plik wykonywalny, który został pobrany, **AzInfoProtection_For_Unified_Labeling.exe**. Jeśli zostanie wyświetlony monit o kontynuowanie, kliknij pozycję **Tak**.    

3. Na stronie **Instalowanie klienta usługi Azure Information Protection**:     
    - Wybierz opcję zainstalowania zasad demonstracyjnych, jeśli nie możesz nawiązać połączenia z chmurą, ale chcesz zobaczyć i wypróbować klienta usługi Azure Information Protection przy użyciu zasad lokalnych w celach demonstracyjnych. Gdy klient nawiąże połączenie z Centrum zgodności i zabezpieczeń usługi Office 365, to zasady demonstracyjne zostaną zastąpione zasadami etykiety Twojej organizacji.

    - Po zapoznaniu się z warunkami licencji kliknij przycisk **Zgadzam się**.    

4. Jeśli zostanie wyświetlony monit z pytaniem o kontynuowanie, kliknij przycisk **Tak** i poczekaj na zakończenie instalacji.    

6. Kliknij pozycję **Zamknij**. Przed rozpoczęciem używania usługi Azure Information Protection unified etykietowania klienta:    

    - Jeśli na komputerze jest zainstalowany pakiet Office 2010, uruchom ponownie komputer, a następnie przejdź do następnej sekcji przedstawiającej ostatni krok.    
        
    - W przypadku innych wersji pakietu Office należy uruchomić ponownie wszystkie aplikacje pakietu Office i wszystkie wystąpienia Eksploratora plików. Instalacja jest ukończona i możesz teraz dodawać etykiety oraz chronić swoje dokumenty i wiadomości e-mail przy użyciu klienta.    

### <a name="installing-the-azure-information-protection-unified-labeling-client-with-office-2010"></a>Instalowanie usługi Azure Information Protection unified etykietowania klienta z pakietem Office 2010

Po zainstalowaniu usługi Azure Information Protection unified etykietowania klienta przy użyciu poprzednich instrukcji:

1. Otwórz program Microsoft Word. Jeśli jest to pierwsze uruchomienie aplikacji pakietu Office 2010 po zainstalowaniu klienta usługi Azure Information Protection, zostanie wyświetlone okno dialogowe **Microsoft Azure Information Protection**. Wyświetlany w oknie dialogowym komunikat mówi, że w celu ukończenia procesu logowania wymagane są poświadczenia administratora.

2. W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **OK**.

3. Jeśli zostanie wyświetlone okno dialogowe **Kontrola dostępu użytkownika**, kliknij przycisk **Tak**, aby klient usługi Azure Information Protection mógł zaktualizować rejestr.

Instalacja jest teraz ukończona, a klient etykietowania ujednolicone usługi Azure Information Protection umożliwia etykietowanie i ochronę dokumentów oraz wiadomości e-mail.

## <a name="next-steps"></a>Kolejne kroki

Aby dowiedzieć się więcej na temat ujednoliconego etykietowania przechowywania, czy Office 365 Security & Compliance center teraz używa, przeczytaj następujący wpis w blogu: [informuje o dostępności unified etykietowania management w Centrum zabezpieczeń i zgodności](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492).

