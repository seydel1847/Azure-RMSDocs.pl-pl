---
title: Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 1
description: Faza 1 migracji z usługi AD RMS do usługi Azure Information Protection obejmująca kroki od 1 do 3 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/11/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: d954d3ee-3c48-4241-aecf-01f4c75fa62c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 3a695268605a16564573d64c1f48447ea9b8cf45
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151116"
---
# <a name="migration-phase-1---preparation"></a>Faza 1 migracji — przygotowanie

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Skorzystaj z poniższych informacji dotyczących fazy 1 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują kroki od 1 do 3 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) i przygotowują środowisko do migracji, nie wpływając na użytkowników.


## <a name="step-1-install-the-aadrm-powershell-module-and-identify-your-tenant-url"></a>Krok 1: Instalowanie modułu AADRM programu PowerShell i identyfikowanie adresu URL dzierżawy

Zainstaluj w module AADRM, tak że można skonfigurować i zarządzać usługą, która zapewnia ochronę danych usługi Azure Information Protection.

Aby uzyskać instrukcje, zobacz [Instalowanie modułu AADRM programu PowerShell](./install-powershell.md).

> [!NOTE]
> Jeśli ten moduł programu Windows PowerShell został już wcześniej pobrany, wykonaj następujące polecenie, aby sprawdzić, czy numer wersji nie jest niższy niż **2.9.0.0**: `(Get-Module aadrm -ListAvailable).Version`

Aby wykonać niektóre z instrukcji migracji, musisz znać adres URL usługi Azure Rights Management dla swojej dzierżawy, aby móc go podstawić po pojawieniu się odwołań do elementu *\<Twój adres URL dzierżawy\>*. Adres URL usługi Azure Rights Management ma następujący format: **{identyfikator GUID}.rms.[Region].aadrm.com**.

Na przykład: **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

### <a name="to-identify-your-azure-rights-management-service-url"></a>Aby ustalić swój adres URL usługi Azure Rights Management

1. Połącz się z usługą Azure Rights Management i po wyświetleniu monitu podaj poświadczenia administratora globalnego swojej dzierżawy:
    
        Connect-AadrmService
    
2. Pobierz konfigurację dzierżawy:
    
        Get-AadrmConfiguration
    
3. Skopiuj wartość wyświetlaną dla elementu **LicensingIntranetDistributionPointUrl** i usuń z tego ciągu fragment `/_wmcs\licensing`. 
    
    Co jeszcze pozostało jest adres URL usługi Azure Rights Management dla dzierżawy usługi Azure Information Protection. Ta wartość jest często obcinana do *adresu URL dzierżawy* w poniższych instrukcjach migracji.
    
    Możesz sprawdzić, czy masz prawidłową wartość, uruchamiając następujące polecenie programu PowerShell:
    
            (Get-AadrmConfiguration).LicensingIntranetDistributionPointUrl -match "https:\/\/[0-9A-Za-z\.-]*" | Out-Null; $matches[0]

## <a name="step-2-prepare-for-client-migration"></a>Krok 2. Przygotowanie do migracji klientów

W przypadku większości migracji niepraktyczne jest migrowanie wszystkich klientów naraz, więc prawdopodobnie będziesz wykonywać migrację klientów partiami. Oznacza to, że przez pewien czas niektórzy klienci będą korzystali z usługi Azure Information Protection, podczas gdy inni będą nadal korzystać z usług AD RMS. W celu obsługi użytkowników jeszcze nie poddanych migracji i już zmigrowanych użyj kontrolek dołączania i wdróż skrypt przed migracją. Ten krok jest wymagany podczas procesu migracji, aby użytkownicy, których migracji jeszcze nie dokonano, mogli korzystać z zawartości chronionej przez zmigrowanych użytkowników, którzy teraz używają usługi Azure Rights Management.

1. Utwórz grupę, na przykład o nazwie **AIPMigrated**. Grupę tę można utworzyć w usłudze Active Directory i synchronizować z chmurą albo utworzyć ją w usłudze Office 365 lub Azure Active Directory. Na razie nie przypisuj żadnych użytkowników do tej grupy. Na późniejszym etapie, kiedy użytkownicy będą migrowani, dodasz ich do tej grupy.

    Zanotuj identyfikator obiektu tej grupy. Aby go uzyskać, możesz użyć usługi Azure AD PowerShell — na przykład w przypadku wersji 1.0 modułu użyj polecenia [Get-MsolGroup](/powershell/msonline/v1/Get-MsolGroup). Możesz także skopiować identyfikator obiektu grupy z witryny Azure Portal.

2. Skonfiguruj tę grupę dla kontrolek dołączania, aby zezwolić tylko użytkownikom w tej grupie na używanie usługi Azure Rights Management do ochrony zawartości. W tym celu w sesji programu PowerShell połącz się z usługą Azure Rights Management i po wyświetleniu monitu podaj swoje poświadczenia administratora globalnego:

        Connect-Aadrmservice

    Następnie skonfiguruj tę grupę dla kontrolek dołączania, podstawiając identyfikator obiektu grupy w miejsce podanego w tym przykładzie, i po wyświetleniu monitu wprowadź **Y**, aby potwierdzić:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fba99fed-32a0-44e0-b032-37b419009501" -Scope WindowsApp

3. [Pobierz następujący plik](https://go.microsoft.com/fwlink/?LinkId=524619) zawierający skrypty migracji klienta:
    
    **Migration-Scripts.zip**
    
4. Wyodrębnij pliki i postępuj zgodnie z instrukcjami w **Client.cmd przygotowanie** tak, aby zawierał nazwę serwera dla usługi AD RMS klastra ekstranetowego adresu URL licencjonowania. 
    
    Aby zlokalizować tę nazwę, w konsoli usług Active Directory Rights Management kliknij nazwę klastra. Z informacji **Szczegóły klastra** skopiuj nazwę serwera z wartości **Licencjonowanie** w sekcji ekstranetowych adresów URL klastra. Na przykład: **rmscluster.contoso.com**.

    > [!IMPORTANT]
    > Instrukcje zawierają opis zastępowania przykładowych adresów **adrms.contoso.com** adresami Twoich serwerów usługi AD RMS. Gdy to robisz, należy sprawdzić, czy nie występują żadne dodatkowe spacje przed adresami lub po nich, które spowodują przerwanie skryptu migracji i są bardzo trudne do zidentyfikowania jako główna przyczyna problemu. Niektóre narzędzia do edycji automatycznie dodają spację po wklejeniu tekstu.
    >

5. Wdróż ten skrypt na wszystkich komputerach z systemem Windows, aby zapewnić, że podczas migracji klienci, którzy nie zostali jeszcze poddani migracji, będą nadal komunikować się z usługami AD RMS nawet w przypadku, gdy korzystają z zawartości chronionej przez zmigrowanych klientów, którzy teraz używają usługi Azure Rights Management.

    W celu wdrożenia tego skryptu można użyć zasad grupy lub innego mechanizmu wdrażania oprogramowania.

## <a name="step-3-prepare-your-exchange-deployment-for-migration"></a>Krok 3. Przygotowanie wdrożenia programu Exchange na potrzeby migracji

Jeśli używasz lokalnej instalacji programu Exchange lub usługi Exchange Online, mogły one zostać wcześniej zintegrowane z Twoim wdrożeniem usług AD RMS. W tym kroku skonfigurujesz je, aby użyć istniejącej konfiguracji usług AD RMS do obsługi zawartości chronionej przez usługę Azure RMS. 

Upewnij się, że masz [adres URL usługi Azure Rights Management dla swojej dzierżawy](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url), aby móc zastąpić tą wartością element *&lt;YourTenantURL&gt;* w poniższych poleceniach. 

**Jeśli zintegrowano usługę Exchange Online z usługami AD RMS**: otwórz sesję programu Exchange Online PowerShell i uruchom następujące polecenia programu PowerShell pojedynczo lub w skrypcie:

    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -internallicensingenabled $true 

**Jeśli z usługami AD RMS zintegrowano lokalny program Exchange**: dla każdej organizacji programu Exchange najpierw dodaj wartości rejestru na każdym serwerze programu Exchange, a następnie uruchom polecenia programu PowerShell: 

Wartości rejestru programów Exchange 2013 i Exchange 2016:

**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://\<Twój adres URL dzierżawy\>/_wmcs/licensing

**Dane:** https://\<Adres URL licencjonowania usług AD RMS w sieci ekstranet\>/_wmcs/licensing

---

Wartości rejestru programu Exchange 2010:

**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://\<Twój adres URL dzierżawy\>/_wmcs/licensing

**Dane:** https://\<Adres URL licencjonowania usług AD RMS w sieci ekstranet>/_wmcs/licensing

---

Polecenia programu PowerShell do uruchamiania pojedynczo lub w skrypcie

    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -RefreshServerCertificates
    Set-IRMConfiguration -internallicensingenabled $true
    IISReset


Po uruchomieniu tych poleceń dla usługi Exchange Online lub lokalnego programu Exchange wdrożenie programu Exchange skonfigurowane do obsługi zawartości chronionej przez usługi AD RMS będzie również obsługiwać zawartość chronioną przez usługę Azure RMS po migracji. Dopóki nie zostanie wykonany późniejszy krok w procesie migracji, wdrożenie programu Exchange będzie nadal używać usług AD RMS do obsługi chronionej zawartości.


## <a name="next-steps"></a>Kolejne kroki
Przejdź do [fazy 2 — konfiguracji po stronie serwera](migrate-from-ad-rms-phase2.md).

