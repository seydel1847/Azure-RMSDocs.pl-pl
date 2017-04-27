---
title: "Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 1"
description: "Faza 1 migracji z usługi AD RMS do usługi Azure Information Protection obejmująca kroki od 1 do 3 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d954d3ee-3c48-4241-aecf-01f4c75fa62c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: adb5ad1f599c5996044ad2fce0e1e5889d81c81b
ms.sourcegitcommit: 237ce3a0cc4921da5a08ed5753e6491403298194
translationtype: HT
---
# <a name="migration-phase-1---preparation"></a>Faza 1 migracji — przygotowanie

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Skorzystaj z poniższych informacji dotyczących fazy 1 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują kroki od 1 do 3 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) i przygotowują środowisko do migracji, nie wpływając na użytkowników.


## <a name="step-1-download-the-azure-rights-management-administration-tool-and-identify-your-tenant-url"></a>Krok 1. Pobieranie narzędzia Azure Rights Management Administration Tool i identyfikowanie adresu URL dzierżawy

Przejdź do Centrum pobierania Microsoft i pobierz narzędzie [Azure Rights Management Administration Tool](https://go.microsoft.com/fwlink/?LinkId=257721), które zawiera moduł administracyjny usługi Azure Rights Management dla programu Windows PowerShell. Usługa Azure Rights Management (Azure RMS) udostępnia funkcję ochrony danych dla usługi Azure Information Protection.

Zainstaluj narzędzie. Instrukcje znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

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
    
    To, co pozostanie, jest adresem URL usługi Azure Rights Management dla Twojej dzierżawy usługi Azure Information Protection, często w skrócie określanym jako *Twój adres URL dzierżawy* w poniższych instrukcjach migracji.

## <a name="step-2-prepare-for-client-migration"></a>Krok 2. Przygotowanie do migracji klientów

W przypadku większości migracji niepraktyczne jest migrowanie wszystkich klientów naraz, więc prawdopodobnie będziesz wykonywać migrację klientów partiami. Oznacza to, że przez pewien czas niektórzy klienci będą korzystali z usługi Azure Information Protection, podczas gdy inni będą nadal korzystać z usług AD RMS. W celu obsługi użytkowników jeszcze nie poddanych migracji i już zmigrowanych użyj kontrolek dołączania i wdróż skrypt przed migracją. Ten krok jest wymagany podczas procesu migracji, aby użytkownicy, których migracji jeszcze nie dokonano, mogli korzystać z zawartości chronionej przez zmigrowanych użytkowników, którzy teraz używają usługi Azure Rights Management.

1. Utwórz grupę, na przykład o nazwie **AIPMigrated**. Grupę tę można utworzyć w usłudze Active Directory i synchronizować z chmurą albo utworzyć ją w usłudze Office 365 lub Azure Active Directory. Na razie nie przypisuj żadnych użytkowników do tej grupy. Na późniejszym etapie, kiedy użytkownicy będą migrowani, dodasz ich do tej grupy.

    Zanotuj identyfikator obiektu tej grupy. Aby go uzyskać, możesz użyć usługi Azure AD PowerShell — na przykład w przypadku wersji 1.0 modułu użyj polecenia [Get-MsolGroup](/powershell/msonline/v1/Get-MsolGroup). Możesz także skopiować identyfikator obiektu grupy z witryny Azure Portal.

2. Skonfiguruj tę grupę dla kontrolek dołączania, aby zezwolić tylko użytkownikom w tej grupie na używanie usługi Azure Rights Management do ochrony zawartości. W tym celu w sesji programu PowerShell połącz się z usługą Azure Rights Management i po wyświetleniu monitu podaj swoje poświadczenia administratora globalnego:

        Connect-Aadrmservice

    Następnie skonfiguruj tę grupę dla kontrolek dołączania, podstawiając identyfikator obiektu grupy w miejsce podanego w tym przykładzie, i po wyświetleniu monitu wprowadź **Y**, aby potwierdzić:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fba99fed-32a0-44e0-b032-37b419009501"

3. [Pobierz następujący plik](https://go.microsoft.com/fwlink/?LinkId=524619) zawierający skrypty migracji klienta:
    
    **ClientMigration.zip**
    
4. Wyodrębnij pliki i postępuj zgodnie z instrukcjami w pliku **PrepareClient.cmd**, aby zawierał nazwę serwera dla ekstranetowego adresu URL licencjonowania klastra usług AD RMS. 
    
    Aby zlokalizować tę nazwę, w konsoli usług Active Directory Rights Management kliknij nazwę klastra. Z informacji **Szczegóły klastra** skopiuj nazwę serwera z wartości **Licencjonowanie** w sekcji ekstranetowych adresów URL klastra. Na przykład: **rmscluster.contoso.com**.

    > [!IMPORTANT]
    > Instrukcje zawierają opis zastępowania przykładowych adresów **adrms.contoso.com** adresami Twoich serwerów usługi AD RMS. Gdy to robisz, należy sprawdzić, czy nie występują żadne dodatkowe spacje przed adresami lub po nich, które spowodują przerwanie skryptu migracji i są bardzo trudne do zidentyfikowania jako główna przyczyna problemu. Niektóre narzędzia do edycji automatycznie dodają spację po wklejeniu tekstu.
    >

5. Wdróż ten skrypt na wszystkich komputerach z systemem Windows, aby zapewnić, że podczas migracji klienci, którzy nie zostali jeszcze poddani migracji, będą nadal komunikować się z usługami AD RMS nawet w przypadku, gdy korzystają z zawartości chronionej przez zmigrowanych klientów, którzy teraz używają usługi Azure Rights Management.

    W celu wdrożenia tego skryptu można użyć zasad grupy lub innego mechanizmu wdrażania oprogramowania.

## <a name="step-3-prepare-your-exchange-deployment-for-migration"></a>Krok 3. Przygotowanie wdrożenia programu Exchange na potrzeby migracji

Jeśli używasz lokalnej instalacji programu Exchange lub usługi Exchange Online, mogły one zostać wcześniej zintegrowane z Twoim wdrożeniem usług AD RMS. W tym kroku skonfigurujesz je, aby użyć istniejącej konfiguracji usług AD RMS do obsługi zawartości chronionej przez usługę Azure RMS. 

Upewnij się, że masz [adres URL usługi Azure Rights Management dla swojej dzierżawy](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url), aby móc zastąpić tą wartością element *&lt;YourTenantURL&gt;* w poniższych poleceniach. Uruchom te zestawy poleceń jeden raz dla każdej organizacji programu Exchange.

**Jeśli zintegrowano usługę Exchange Online z usługami AD RMS**: otwórz sesję programu Exchange Online PowerShell i uruchom następujące polecenia programu PowerShell pojedynczo lub w skrypcie:

    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -internallicensingenabled $true 

**Jeśli zintegrowano lokalną instalację programu Exchange z usługami AD RMS**: uruchom następujące polecenia programu PowerShell pojedynczo lub w skrypcie: 

    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -RefreshServerCertificates
    Set-IRMConfiguration -internallicensingenabled $true
    IISReset

Ponadto, w przypadku lokalnej instalacji programu Exchange, na każdym serwerze Exchange należy dodać wartości rejestru.


W przypadku programu Exchange 2013 i Exchange 2016:


**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://\<Twój adres URL dzierżawy\>/_wmcs/licensing

**Dane:** https://\<Adres URL licencjonowania usług AD RMS w sieci ekstranet\>/_wmcs/licensing


---

W przypadku programu Exchange 2010:


**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://\<Twój adres URL dzierżawy\>/_wmcs/licensing

**Dane:** https://\<Adres URL licencjonowania usług AD RMS w sieci ekstranet>/_wmcs/licensing


---


Po uruchomieniu tych poleceń, jeśli serwery Exchange były skonfigurowane do obsługi zawartości chronionej przez usługi AD RMS, będą również obsługiwały zawartość chronioną przez usługę Azure RMS po migracji. Dopóki nie zostanie wykonany późniejszy krok w procesie migracji, będą nadal używały usług AD RMS do obsługi chronionej zawartości.



## <a name="next-steps"></a>Następne kroki
Przejdź do [fazy 2 — konfiguracji po stronie serwera](migrate-from-ad-rms-phase2.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
