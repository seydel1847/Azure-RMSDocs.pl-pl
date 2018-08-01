---
title: Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 3
description: Faza 3 migracji z usługi AD RMS do usługi Azure Information Protection obejmująca krok 7 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 07da614bf7971ee4ef89ec9ec3830be188483201
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39371768"
---
# <a name="migration-phase-3---client-side-configuration"></a>Faza 3 migracji — konfiguracja po stronie klienta

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Skorzystaj z poniższych informacji dotyczących fazy 3 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują krok 7 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-7-reconfigure-windows-computers-to-use-azure-information-protection"></a>Krok 7. Ponownie skonfiguruj komputery Windows, aby korzystać z usługi Azure Information Protection

Dla komputerów Windows, które używają aplikacji klasycznych Szybka instalacja pakietu Office 2016:

- Można ponownie skonfigurować tych klientów do użycia usługi Azure Information Protection przy użyciu przekierowania DNS. Jest preferowaną metodą migracji klienta, ponieważ jest to najprostszy. Jednak ta metoda jest ograniczony do aplikacji klasycznych pakietu Office 2016 (lub nowsza) kliknij polecenie do uruchomienia dla komputerów Windows.
    
    Ta metoda wymaga, aby utworzyć nowy SRV rejestrowania i zestaw NTFS odmówić uprawnień dla użytkowników na punkt końcowy publikowania usług AD RMS.

- Komputery Windows, które nie używają Szybka instalacja pakietu Office 2016:
    
    Nie można użyć przekierowania DNS i zamiast tego należy użyć edycji rejestru. Jeśli masz kombinację pakiety Office 2016 i innych wersji pakietu Office, można użyć tej metody pojedynczego wszystkie komputery Windows lub kombinacji przekierowania DNS oraz edytowania rejestru. 
    
    Zmiany w rejestrze zostaną zastosowane łatwiejsze do edycji i wdrażając skrypty, które można pobrać. 

Zobacz następujące sekcje, aby uzyskać więcej informacji o sposobie. ponowne konfigurowanie klientów Windows.

## <a name="client-reconfiguration-by-using-dns-redirection"></a>Ponowna konfiguracja klienta za pomocą przekierowania DNS

Ta metoda jest przydatna tylko w przypadku klienci Windows aplikacji klasycznych Szybka instalacja pakietu Office 2016 (lub nowsza). 

1. Utwórz rekord DNS SRV w następującym formacie:
    
    `_rmsredir._http._tcp.<AD RMS cluster>. <TTL> IN SRV <priority> <weight> <port> <your tenant URL>.`
    
    Aby uzyskać  *\<klastra usług AD RMS >*, określ nazwę FQDN klastra usług AD RMS. Na przykład **rmscluster.contoso.com**.
    
    Alternatywnie Jeśli masz tylko usługi AD RMS klastra w tej domenie, można określić tylko nazwę domeny klastra usług AD RMS. W naszym przykładzie wyniesie **contoso.com**. Po określeniu nazwy domeny w tym rekordzie przekierowania ma zastosowanie do wszystkich klastrów AD RMS w danej domenie.
    
    *\<Port >* numer zostanie zignorowany.
    
    Aby uzyskać  *\<adresu URL dzierżawy\>*, określić własny [adres URL usługi Azure Rights Management dla dzierżawy](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).
    
    Jeśli używasz roli serwera DNS w systemie Windows Server służy poniższa tabela przedstawia przykład sposobu określania właściwości rekordu SRV w konsoli Menedżera DNS.
    
    |Pole|Wartość|  
    |-----------|-----------|  
    |**Domeny**|_tcp.rmscluster.contoso.com|  
    |**Usługa**|_rmsredir|  
    |**Protokół**|_http|  
    |**Priorytet**|0|  
    |**Waga**|0|  
    |**Numer portu**|80|  
    |**Host oferujący tę usługę**|5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com|  

2. Odmów uprawnień dla użytkowników pakietu Office 2016 należy ustawić na punkt końcowy publikowania usług AD RMS:

    a. Na jednym z serwerów usługi AD RMS w klastrze Uruchom konsolę Menedżera usług Internet Information Services (IIS).

    b. Przejdź do **domyślna witryna sieci Web** > **_wmcs** > **licencjonowania** > **licensing.asmx**

    c. Kliknij prawym przyciskiem myszy **licensing.asmx** > **właściwości** > **edycji**

    d. W **uprawnienia dla licensing.asmx** okno dialogowe, wybierz opcję **użytkowników** Jeśli chcesz ustawić przekierowywanie dla wszystkich użytkowników, lub kliknij przycisk **Dodaj** i następnie określ grupę, zawiera użytkowników, które chcesz przekierować.
    
    Nawet wtedy, gdy wszyscy użytkownicy korzystają z pakietu Office 2016, możesz preferować początkowo określić podzbioru użytkowników w ramach migracji stopniowej.
    
    e. Wybrane grupy, wybierz **Odmów** dla **Odczyt i wykonanie** i **odczytu** uprawnień, a następnie kliknij **OK** dwa razy.

    f. Upewnij się, że ta konfiguracja działa prawidłowo, spróbuj połączyć się z plikiem licensing.asmx bezpośrednio w przeglądarce. Powinny pojawić się następujący komunikat o błędzie, co powoduje wyzwolenie kliencie z uruchomioną pakiety Office 2016 do wyszukiwania dla rekordu SRV:
    
    **Komunikat o błędzie 401.3: nie masz uprawnień do wyświetlenia tego katalogu lub strony przy użyciu poświadczeń dostarczonych (odmowa dostępu z powodu list usługi Access Control).**


## <a name="client-reconfiguration-by-using-registry-edits"></a>Ponowna konfiguracja klienta za pomocą edycji rejestru

Ta metoda jest odpowiednia dla wszystkich klientów Windows i można używać, jeśli nie są uruchamiane pakiety Office 2016, ale starszej wersji. Ta metoda używa dwóch skryptów migracji, aby ponowne konfigurowanie klientów usług AD RMS:

- Migrate-Client.cmd

- Migrate-User.cmd

Skrypt konfiguracji klientów (migrowanie Client.cmd) umożliwia skonfigurowanie ustawienia na poziomie komputera w rejestrze, co oznacza, że musi być uruchamiane w kontekście zabezpieczeń, które można wprowadzić te zmiany. Zwykle oznacza to jedną z następujących metod:

- Uruchom skrypt jako skrypt uruchamiania komputera za pomocą zasad grupy.

- Przypisz skrypt do komputera za pomocą instalacji oprogramowania zasad grupy.

- Aby wdrożyć skrypt na komputerach przy użyciu rozwiązania wdrożenia oprogramowania. Na przykład użyć programu System Center Configuration Manager [pakiety i programy](/sccm/apps/deploy-use/packages-and-programs). W oknie właściwości pakietu i programu w obszarze **tryb uruchamiania**, określić, że skrypt jest uruchamiany z uprawnieniami administracyjnymi na urządzeniu. 

- Użyj skryptu logowania, jeśli użytkownik ma uprawnienia administratora lokalnego.

Skrypt konfiguracji użytkownika (migrowanie User.cmd) konfiguruje ustawienia na poziomie użytkownika i czyści magazynu licencji klienta. Oznacza to, że ten skrypt należy uruchomić w kontekście rzeczywisty użytkownik. Przykład:

- Użyj skryptu logowania.

- Instalacja oprogramowania zasad grupy umożliwia publikowanie skrypt do uruchomienia przez użytkownika.

- Aby wdrożyć skrypt do użytkowników przy użyciu rozwiązania wdrożenia oprogramowania. Na przykład użyć programu System Center Configuration Manager [pakiety i programy](/sccm/apps/deploy-use/packages-and-programs). W oknie właściwości pakietu i programu w obszarze **tryb uruchamiania**, określ, czy skrypt jest uruchamiany z uprawnieniami użytkownika. 

- Poproś użytkownika, aby uruchomić skrypt, gdy jest zalogowany na komputerze.

Dwa skrypty obejmują numer wersji i nie ponownie, dopóki nie zostanie zmieniony numer wersji. Oznacza to, że można pozostawić skrypty w miejscu do czasu ukończenia migracji. Jednak w przypadku wprowadzenia zmian do skryptów, które mają komputerów i użytkowników, aby ponownie uruchomić na swoich komputerach Windows, należy zaktualizować następujący wiersz w obu skryptów do wartości większej:

    SET Version=20170427

Skrypt konfiguracji użytkownika jest przeznaczony do działania po skryptu konfiguracji klienta i używa numeru wersji, w tym wyboru. Zatrzymuje go, jeśli nie został uruchomiony skrypt konfiguracji klienta z tej samej wersji. To sprawdzenie gwarantuje, że dwa skrypty są uruchamiane sekwencyjnie prawo. 

Gdy wszyscy klienci Windows nie można migrować tylko raz, uruchom następujące procedury dla partii klientów. Każdego użytkownika posiadającego komputer z systemem Windows, którego chcesz migrować w partii, dodaj do grupy **AIPMigrated** utworzonej wcześniej.

### <a name="modifying-the-scripts-for-registry-edits"></a>Modyfikowanie skryptów do edycji rejestru

1. Wróć do skryptów migracji **Client.cmd migracji** i **User.cmd migracji**, które wyodrębniono wcześniej kiedy pobierany tych skryptów w [etapu przygotowywania](migrate-from-ad-rms-phase1.md#step-2-prepare-for-client-migration).

2.  Postępuj zgodnie z instrukcjami w **Client.cmd migracji** celu zmodyfikowania skryptu, tak aby zawiera adres URL usługi Azure Rights Management swojej dzierżawy, a także nazwy serwerów dla usług AD RMS klastra intranetu i ekstranetu adresu URL licencjonowania adres URL licencjonowania. Następnie należy zwiększyć wersji skryptu wyjaśniono wcześniej. Dobrym rozwiązaniem dla śledzenia wersji skryptu jest użycie bieżącą datę w następującym formacie: RRRRMMDD
    
    > [!IMPORTANT]
    > Tak jak poprzednio, uważaj, aby nie wprowadzić dodatkowych spacji przed adresami lub po nich.
    > 
    > Ponadto jeśli serwery usług AD RMS używają certyfikatów serwera SSL/TLS, sprawdź, czy wartości adresu URL licencjonowania obejmują numer portu **443** wewnątrz ciągu. Na przykład: https://rms.treyresearch.net:443/_wmcs/licensing. Te informacje można znaleźć w konsoli usługi zarządzania prawami dostępu w usłudze Active Directory, po kliknięciu nazwy klastra i wyświetleniu **szczegóły klastra** informacji. Jeśli widzisz numer portu 443 zawarty w adresie URL, uwzględnij tę wartość podczas modyfikowania skryptu. Na przykład https://rms.treyresearch.net:**443**. 
    
    Jeśli musisz pobrać adres URL usługi Azure Rights Management do podstawienia w elemencie *&lt;YourTenantURL&gt;* (Twój adres URL dzierżawy), skorzystaj ponownie z instrukcji w sekcji [Aby ustalić swój adres URL usługi Azure Rights Management](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3. Korzystając z instrukcji na początku tego kroku skonfigurować swoje metody wdrożenia skryptu do uruchomienia **Client.cmd migracji** i **User.cmd migracji** na komputerach klienckich Windows, które są używane przez Członkowie grupy AIPMigrated. 

## <a name="next-steps"></a>Kolejne kroki
Aby kontynuować migrację, przejdź do [fazy 4 — konfiguracji usług pomocniczych](migrate-from-ad-rms-phase4.md).
