---
title: Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 3
description: Faza 3 migracji z usługi AD RMS do usługi Azure Information Protection obejmująca krok 7 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e5e1f0fa043a0a15ef34c9e4d5690e974cf6bddd
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="migration-phase-3---client-side-configuration"></a>Faza 3 migracji — konfiguracja po stronie klienta

>*Dotyczy: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Skorzystaj z poniższych informacji dotyczących fazy 3 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują krok 7 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-7-reconfigure-windows-computers-to-use-azure-information-protection"></a>Krok 7. Ponownie skonfiguruj komputery z systemem Windows do użycia usługi Azure Information Protection

Dla komputerów z systemem Windows, które używają aplikacje komputerowe pakietu Office 2016 kliknij polecenie do uruchomienia:

- Można ponownie skonfigurować tych klientów do użycia usługi Azure Information Protection przy użyciu przekierowania DNS. Ponieważ to najprostszy jest preferowaną metodą migracji klientów. Jednak ta metoda jest ograniczone do pakietu Office 2016 (lub nowsza) kliknij polecenie do uruchomienia aplikacji klasycznych dla komputerów z systemem Windows.
    
    Ta metoda wymaga, aby utworzyć nowy SRV rejestrowania i zestaw NTFS odmówić uprawnień dla użytkowników w punkcie końcowym publikacji usług AD RMS.

- Dla komputerów z systemem Windows, które nie używają kliknij przycisk Uruchom pakiet Office 2016:
    
    Nie można użyć przekierowania DNS i zamiast tego należy użyć edycji rejestru. Jeśli masz kombinację pakietu Office 2016 i innych wersji pakietu Office, można użyć tej metody pojedynczego dla wszystkich komputerów z systemem Windows lub kombinację przekierowania DNS oraz edytowania rejestru. 
    
    Zmiany w rejestrze zostaną zastosowane łatwiejsze edycji i wdrażając skrypty, które można pobrać. 

Znajduje się w następujących sekcjach, aby uzyskać więcej informacji o sposobie ponowne konfigurowanie klientów systemu Windows.

## <a name="client-reconfiguration-by-using-dns-redirection"></a>Ponowna konfiguracja klienta przy użyciu przekierowania DNS

Ta metoda jest odpowiednie tylko dla klientów systemu Windows, które są uruchamiane aplikacje komputerowe pakietu Office 2016 (lub nowsza) kliknij polecenie do uruchomienia. 

1. Utwórz rekord DNS SRV w następującym formacie:
    
    `_rmsredir._http._tcp.<AD RMS cluster>. <TTL> IN SRV <priority> <weight> <port> <your tenant URL>.`
    
    Aby uzyskać  *\<klaster usług AD RMS >*, określ nazwę FQDN klastra usług AD RMS. Na przykład **rmscluster.contoso.com**.
    
    Alternatywnie Jeśli masz tylko jednego klastra usług AD RMS w danej domenie, można określić tylko nazwę domeny do klastra AD RMS. W naszym przykładzie, który będzie **contoso.com**. Po określeniu nazwy domeny w tym rekordzie przekierowanie ma zastosowanie do wszystkich klastrach usług AD RMS w danej domenie.
    
     *\<Port >* numer zostanie zignorowany.
    
    Aby uzyskać  *\<adres URL dzierżawy\>*, określić własne [adres URL usługi Azure Rights Management dla swojej dzierżawy](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).
    
    Jeśli używasz roli serwera DNS w systemie Windows Server służy poniższa tabela jako przykład sposobu określania właściwości rekord SRV w konsoli Menedżera DNS.
    
    |Pole|Wartość|  
    |-----------|-----------|  
    |**Domeny**|_tcp.rmscluster.contoso.com|  
    |**Usługa**|_rmsredir|  
    |**Protokół**|_http|  
    |**Priorytet**|0|  
    |**Waga**|0|  
    |**Numer portu**|80|  
    |**Host oferujący tę usługę**|5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com|  

2. Ustaw Odmów uprawnień dla użytkowników pakietu Office 2016 na punkt końcowy publikowania usług AD RMS:

    a. Na jednym z serwerów usług AD RMS w klastrze Uruchom konsolę Menedżera usług Internet Information Services (IIS).

    b. Przejdź do **domyślna witryna sieci Web** > **_wmcs** > **licencjonowania** > **publish.asmx**

    c. Kliknij prawym przyciskiem myszy **publish.asmx** > **właściwości** > **edycji**

    d. W **uprawnienia dla publish.asmx** okno dialogowe, wybierz opcję **użytkowników** Aby ustawić przekierowywanie dla wszystkich użytkowników, lub kliknij przycisk **Dodaj** , a następnie określ grupę, która zawiera Użytkownicy, którzy mają przekierowania.
    
    Nawet wtedy, gdy wszyscy użytkownicy korzystają z pakietu Office 2016, można wybrać określone początkowo podzbioru użytkowników w ramach migracji stopniowej.
    
    e. Wybrane grupy, wybierz **Odmów** dla **Odczyt i wykonanie** i **odczytu** uprawnienia, a następnie kliknij przycisk **OK** dwa razy.

    f. Aby upewnić się, że ta konfiguracja działa zgodnie z oczekiwaniami, spróbuj połączyć się z plikiem publish.asmx bezpośrednio z przeglądarki. Powinny pojawić następujący komunikat o błędzie, który wyzwala klienta uruchomiony pakiet Office 2016, aby wyszukać rekordu SRV:
    
    **Komunikat o błędzie 401.3: nie masz uprawnień do przeglądania tego katalogu lub strony przy użyciu poświadczeń dostarczonych (odmowa dostępu z powodu listy kontroli dostępu).**


## <a name="client-reconfiguration-by-using-registry-edits"></a>Ponowna konfiguracja klienta za pomocą edycji rejestru

Ta metoda jest odpowiednia dla wszystkich klientów systemu Windows i powinien być używany, jeśli nie jest uruchomiony, ale starszej wersji pakietu Office 2016. Ta metoda używa dwa skrypty migracji, aby ponownie skonfigurować klientów usług AD RMS:

- Migrate-Client.cmd

- Migrate-User.cmd

Skrypt konfiguracji klienta (migracji Client.cmd) konfiguruje ustawienia poziomu komputera w rejestrze, co oznacza, że należy uruchomić w kontekście zabezpieczeń, które można wprowadzić zmiany. Zwykle oznacza to jeden z następujących metod:

- Uruchom skrypt jako skryptu uruchamiania komputera za pomocą zasad grupy.

- Instalacja oprogramowania zasad grupy umożliwia przypisywanie skryptu na komputerze.

- Za pomocą rozwiązania wdrożenia oprogramowania można wdrożyć skrypt na komputerach. Na przykład użyć programu System Center Configuration Manager [pakiety i programy](/sccm/apps/deploy-use/packages-and-programs). W oknie właściwości pakietu i programu w obszarze **tryb uruchamiania**, określ, że skrypt jest uruchamiany z uprawnieniami administracyjnymi na urządzeniu. 

- Użyj skryptu logowania, jeśli użytkownik ma uprawnienia administratora lokalnego.

Skrypt konfiguracji użytkownika (migracji User.cmd) umożliwia skonfigurowanie ustawień na poziomie użytkownika i czyści magazynu licencji klienta. Oznacza to, że ten skrypt należy uruchomić w kontekście użytkownika, do rzeczywistych. Przykład:

- Za pomocą skryptu logowania.

- Instalacja oprogramowania zasad grupy umożliwia publikowanie skryptów do uruchomienia przez użytkownika.

- Za pomocą rozwiązania wdrożenia oprogramowania do wdrożenia skryptu dla użytkowników. Na przykład użyć programu System Center Configuration Manager [pakiety i programy](/sccm/apps/deploy-use/packages-and-programs). W oknie właściwości pakietu i programu w obszarze **tryb uruchamiania**, określ, że skrypt jest uruchamiany z uprawnieniami użytkownika. 

- Poproś użytkowników, aby uruchomić skrypt, gdy są zalogowani do komputera.

Dwa skrypty obejmują numer wersji i nie ponowne uruchomienie do czasu zmiany numer wersji. Oznacza to, że można pozostawić skrypty w miejscu do czasu ukończenia migracji. Jednak jeśli wprowadzisz zmiany do skryptów, które mają komputerów i użytkowników, aby ponownie uruchomić na komputerach z systemem Windows, należy zaktualizować następujący wiersz w obu skryptów do wartości większej:

    SET Version=20170427

Skrypt konfiguracji użytkownika jest przeznaczony do uruchomienia po skryptu konfiguracji klienta i używa tego, czy numer wersji. Zatrzymuje go, jeśli skrypt konfiguracji klienta z tej samej wersji nie został uruchomiony. Tego wyboru gwarantuje, że dwa skrypty są uruchamiane w prawo sekwencji. 

Gdy wszyscy klienci Windows nie można migrować na raz, uruchom następujące procedury dla partii klientów. Każdego użytkownika posiadającego komputer z systemem Windows, którego chcesz migrować w partii, dodaj do grupy **AIPMigrated** utworzonej wcześniej.

### <a name="modifying-the-scripts-for-registry-edits"></a>Modyfikowanie skryptów do edycji rejestru

1. Wróć do skrypty migracji **Client.cmd migracji** i **User.cmd migracji**, którego wyodrębniono wcześniej podczas pobrane te skrypty w [fazie przygotowywania](migrate-from-ad-rms-phase1.md#step-2-prepare-for-client-migration).

2.  Postępuj zgodnie z instrukcjami **Client.cmd migracji** zmodyfikować skrypt zawiera adres URL usługi Azure Rights Management w swojej dzierżawy, a także z serwerów nazw dla usług AD RMS klastra ekstranetowy adres URL licencjonowania i intranet adres URL licencjonowania. Następnie należy zwiększyć wersja skryptu, który wcześniej wyjaśniono. Dobrym rozwiązaniem dla śledzenia wersji skryptu jest użycie dzisiejszej daty w następującym formacie: RRRRMMDD
    
    > [!IMPORTANT]
    > Tak jak poprzednio, uważaj, aby nie wprowadzić dodatkowych spacji przed adresami lub po nich.
    > 
    > Ponadto jeśli serwery usług AD RMS używają certyfikatów serwera SSL/TLS, sprawdź, czy wartości adresu URL licencjonowania obejmują numer portu **443** wewnątrz ciągu. Na przykład: https:// rms.treyresearch.net:443/_wmcs/licensing. Informacje te można znaleźć w konsoli usługi zarządzania prawami dostępu w usłudze Active Directory, po kliknięciu nazwy klastra i widoku **szczegółów klastra** informacji. Jeśli widzisz numer portu 443 zawarty w adresie URL, uwzględnij tę wartość podczas modyfikowania skryptu. Na przykład https://rms.treyresearch.net: **443**. 
    
    Jeśli musisz pobrać adres URL usługi Azure Rights Management do podstawienia w elemencie *&lt;YourTenantURL&gt;* (Twój adres URL dzierżawy), skorzystaj ponownie z instrukcji w sekcji [Aby ustalić swój adres URL usługi Azure Rights Management](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3. Korzystając z instrukcji na początku tego kroku Konfigurowanie metody wdrożenia skryptu do uruchomienia **Client.cmd migracji** i **User.cmd migracji** na komputerach klienckich z systemem Windows, które są używane przez Członkowie grupy AIPMigrated. 

## <a name="next-steps"></a>Następne kroki
Aby kontynuować migrację, przejdź do [fazy 4 — konfiguracji usług pomocniczych](migrate-from-ad-rms-phase4.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]