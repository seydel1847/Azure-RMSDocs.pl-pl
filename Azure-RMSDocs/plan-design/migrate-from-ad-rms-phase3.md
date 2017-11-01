---
title: "Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 3"
description: "Faza 3 migracji z usługi AD RMS do usługi Azure Information Protection obejmująca krok 7 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/11/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ca2c8156489b55911ee340fd52f85e68b5280915
ms.sourcegitcommit: 3952fc01c6182c143df7f0d2e748594e49bf1da8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2017
---
# <a name="migration-phase-3---client-side-configuration"></a>Faza 3 migracji — konfiguracja po stronie klienta

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Skorzystaj z poniższych informacji dotyczących fazy 3 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują krok 7 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-7-reconfigure-windows-computers-to-use-azure-information-protection"></a>Krok 7. Ponownie skonfiguruj komputery z systemem Windows do użycia usługi Azure Information Protection

W przypadku komputerów z systemem Windows za pomocą dwóch skryptów migracji na ponowne konfigurowanie klientów usług AD RMS:

- Migrowanie Client.cmd

- Migrowanie User.cmd

Skrypt konfiguracji klienta (migracji Client.cmd) konfiguruje ustawienia poziomu komputera w rejestrze, co oznacza, że należy uruchomić w kontekście zabezpieczeń, które można wprowadzić zmiany. Zwykle oznacza to jeden z następujących metod:

- Uruchom skrypt jako skryptu uruchamiania komputera za pomocą zasad grupy.

- Instalacja oprogramowania zasad grupy umożliwia przypisywanie skryptu na komputerze.

- Za pomocą rozwiązania wdrożenia oprogramowania można wdrożyć skrypt na komputerach. Na przykład użyć programu System Center Configuration Manager [pakiety i programy](/sccm/apps/deploy-use/packages-and-programs). W oknie właściwości pakietu i programu w obszarze **tryb uruchamiania**, określ, że skrypt jest uruchamiany z uprawnieniami administracyjnymi na urządzeniu. 

- Użyj skryptu logowania, jeśli użytkownik ma uprawnienia administratora lokalnego.

Skrypt konfiguracji użytkownika (migracji User.cmd) umożliwia skonfigurowanie ustawień na poziomie użytkownika i czyści magazynu licencji klienta. Oznacza to, że ten skrypt należy uruchomić w kontekście użytkownika, do rzeczywistych. Na przykład:

- Za pomocą skryptu logowania.

- Instalacja oprogramowania zasad grupy umożliwia publikowanie skryptów do uruchomienia przez użytkownika.

- Za pomocą rozwiązania wdrożenia oprogramowania do wdrożenia skryptu dla użytkowników. Na przykład użyć programu System Center Configuration Manager [pakiety i programy](/sccm/apps/deploy-use/packages-and-programs). W oknie właściwości pakietu i programu w obszarze **tryb uruchamiania**, określ, że skrypt jest uruchamiany z uprawnieniami użytkownika. 

- Poproś użytkowników, aby uruchomić skrypt, gdy są zalogowani do komputera.

Dwa skrypty obejmują numer wersji i nie ponowne uruchomienie do czasu zmiany numer wersji. Oznacza to, że można pozostawić skrypty w miejscu do czasu ukończenia migracji. Jednak jeśli wprowadzisz zmiany do skryptów, które mają komputerów i użytkowników, aby ponownie uruchomić na komputerach z systemem Windows, należy zaktualizować następujący wiersz w obu skryptów do wartości większej:

    SET Version=20170427

Skrypt konfiguracji użytkownika jest przeznaczony do uruchomienia po skryptu konfiguracji klienta i używa tego, czy numer wersji. Zatrzymał się, jeśli skrypt konfiguracji klienta z tej samej wersji nie został uruchomiony. To sprawdzenie zapewnia, że dwa skrypty są uruchamiane w prawo sekwencji. 

Gdy wszyscy klienci Windows nie można migrować na raz, uruchom następujące procedury dla partii klientów. Każdego użytkownika posiadającego komputer z systemem Windows, którego chcesz migrować w partii, dodaj do grupy **AIPMigrated** utworzonej wcześniej.

### <a name="windows-client-reconfiguration-by-using-registry-edits"></a>Ponowna konfiguracja klienta Windows za pomocą edycji rejestru

1. Wróć do skrypty migracji **Client.cmd migracji** i **User.cmd migracji**, którego wyodrębniono wcześniej podczas pobrane te skrypty w [fazie przygotowywania](migrate-from-ad-rms-phase1.md#step-2-prepare-for-client-migration).

2.  Postępuj zgodnie z instrukcjami **Client.cmd migracji** zmodyfikować skrypt zawiera adres URL usługi Azure Rights Management w swojej dzierżawy, a także z serwerów nazw dla usług AD RMS klastra ekstranetowy adres URL licencjonowania i intranet adres URL licencjonowania. Następnie należy zwiększyć wersja skryptu, który wcześniej wyjaśniono. Dobrym rozwiązaniem dla śledzenia wersji skryptu jest użycie dzisiejszej daty w następującym formacie: RRRRMMDD

    > [!IMPORTANT]
    > Tak jak poprzednio, uważaj, aby nie wprowadzić dodatkowych spacji przed adresami lub po nich.
    > 
    > Ponadto jeśli serwery usług AD RMS używają certyfikatów serwera SSL/TLS, sprawdź, czy wartości adresu URL licencjonowania obejmują numer portu **443** wewnątrz ciągu. Na przykład: https:// rms.treyresearch.net:443/_wmcs/licensing. Te informacje można znaleźć w konsoli usług Active Directory Rights Management Services po kliknięciu nazwy klastra i wyświetleniu informacji **Szczegóły klastra**. Jeśli widzisz numer portu 443 zawarty w adresie URL, uwzględnij tę wartość podczas modyfikowania skryptu. Na przykład https://rms.treyresearch.net:**443**. 

    Jeśli musisz pobrać adres URL usługi Azure Rights Management do podstawienia w elemencie *&lt;YourTenantURL&gt;* (Twój adres URL dzierżawy), skorzystaj ponownie z instrukcji w sekcji [Aby ustalić swój adres URL usługi Azure Rights Management](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3. Korzystając z instrukcji na początku tego kroku Konfigurowanie metody wdrożenia skryptu do uruchomienia **Client.cmd migracji** i **User.cmd migracji** na komputerach klienckich z systemem Windows, które są używane przez Członkowie grupy AIPMigrated. 

## <a name="next-steps"></a>Następne kroki
Aby kontynuować migrację, przejdź do [fazy 4 — konfiguracji usług pomocniczych](migrate-from-ad-rms-phase4.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]