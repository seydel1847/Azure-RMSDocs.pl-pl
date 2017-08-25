---
title: "Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 3"
description: "Faza 3 migracji z usługi AD RMS do usługi Azure Information Protection obejmująca krok 7 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/22/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 35bd2d176cb71c54a489d4f4b8faca4d668a7867
ms.sourcegitcommit: c960f1d2140dea11e54cbeb37d53d1512621d90c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2017
---
# <a name="migration-phase-3---client-side-configuration"></a>Faza 3 migracji — konfiguracja po stronie klienta

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Skorzystaj z poniższych informacji dotyczących fazy 3 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują krok 7 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-7-reconfigure-clients-to-use-azure-information-protection"></a>Krok 7. Ponownie skonfiguruj klientów do korzystania z usługi Azure Information Protection

W przypadku klientów urządzeń przenośnych i komputerów Mac:

- Usuń rekordy SRV systemu DNS, które zostały utworzone podczas wdrażania [rozszerzenia usługi AD RMS dla urządzeń przenośnych](http://technet.microsoft.com/library/dn673574.aspx).

W przypadku klientów systemu Windows:

- Następujące skrypty migracji umożliwia ponowne konfigurowanie klientów usług AD RMS. Skrypty te resetowania konfiguracji na komputerach z systemem Windows do użycia usługi Azure Rights Management zamiast usług AD RMS: 
    
    **CleanUpRMS.cmd**
    
    - Usuwa zawartość wszystkich folderów i kluczy rejestru używanych przez klienta usług AD RMS do przechowywania jego konfiguracji. Informacje te obejmują lokalizację klastra usług AD RMS klienta.
    
    **MigrateClient.cmd**
    
    - Konfiguruje klienta w celu zainicjowania środowiska użytkownika (bootstrap) dla usługi Azure Rights Management.
    
    - Konfiguruje klienta do łączenia się z usługą Azure Rights Management, aby uzyskać licencję użytkowania dla zawartości chronionej przez Twój klaster usług AD RMS. 

Gdy wszyscy klienci Windows nie można migrować na raz, uruchom następujące procedury dla partii klientów. Każdego użytkownika posiadającego komputer z systemem Windows, którego chcesz migrować w partii, dodaj do grupy **AIPMigrated** utworzonej wcześniej.

### <a name="windows-client-reconfiguration-by-using-registry-edits"></a>Ponowna konfiguracja klienta Windows za pomocą edycji rejestru

1. Wróć do skryptów migracji **CleanUpRMS.cmd** i **MigrateClient.cmd**, które wyodrębniono wcześniej.

2.  Postępuj zgodnie z instrukcjami skryptu **MigrateClient.cmd** w celu zmodyfikowania skryptu, tak aby zawierał adres URL usługi Azure Rights Management Twojej dzierżawy oraz nazwy serwerów dla adresu URL licencjonowania klastra usług AD RMS w sieci ekstranet i adresu URL licencjonowania klastra usług AD RMS w sieci intranet.

    > [!IMPORTANT]
    > Tak jak poprzednio, uważaj, aby nie wprowadzić dodatkowych spacji przed adresami lub po nich.
    > 
    > Ponadto jeśli serwery usług AD RMS używają certyfikatów serwera SSL/TLS, sprawdź, czy wartości adresu URL licencjonowania obejmują numer portu **443** wewnątrz ciągu. Na przykład: https:// rms.treyresearch.net:443/_wmcs/licensing. Te informacje można znaleźć w konsoli usług Active Directory Rights Management Services po kliknięciu nazwy klastra i wyświetleniu informacji **Szczegóły klastra**. Jeśli widzisz numer portu 443 zawarty w adresie URL, uwzględnij tę wartość podczas modyfikowania skryptu. Na przykład https://rms.treyresearch.net:**443**. 

    Jeśli musisz pobrać adres URL usługi Azure Rights Management do podstawienia w elemencie *&lt;YourTenantURL&gt;* (Twój adres URL dzierżawy), skorzystaj ponownie z instrukcji w sekcji [Aby ustalić swój adres URL usługi Azure Rights Management](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3.  Uruchom **CleanUpRMS.cmd** , a następnie **MigrateClient.cmd** na komputerach klienckich systemu Windows, które są używane przez członków **AIPMigrated** grupy. Na przykład utwórz obiekt zasad grupy, który uruchamia te skrypty, i przypisz go do tej grupy użytkowników.

## <a name="next-steps"></a>Następne kroki
Aby kontynuować migrację, przejdź do [fazy 4 — konfiguracji usług pomocniczych](migrate-from-ad-rms-phase3.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]