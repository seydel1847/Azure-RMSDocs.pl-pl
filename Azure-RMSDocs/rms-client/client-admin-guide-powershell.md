---
title: "Używanie środowiska PowerShell z klientem usługi Azure Information Protection"
description: "Instrukcje i informacje dla administratorów dotyczące zarządzania klientem usługi Azure Information Protection przy użyciu środowiska PowerShell."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4f9d2db7-ef27-47e6-b2a8-d6c039662d3c
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: e39097a4786ddd71082eda4a5b445b3fb682f6b7
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Używanie środowiska PowerShell z klientem usługi Azure Information Protection
<a id="using-powershell-with-the-azure-information-protection-client" class="xliff"></a>

>*Dotyczy: usługi zarządzania prawami dostępu w usłudze Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Podczas instalowania klienta usługi Azure Information Protection instalowane są też polecenia środowiska PowerShell, dzięki czemu możliwe jest automatycznie zarządzanie klientem poprzez uruchamianie poleceń zawartych w skryptach automatyzacji.

Polecenia cmdlet są instalowane wraz z modułem PowerShell **AzureInformationProtection**, który zastępuje moduł RMSProtection zainstalowany razem z narzędziem RMS Protection Tool. Jeśli przed instalacją klienta usługi Azure Information Protection było już zainstalowane narzędzie RMS Protection Tool, moduł RMSProtection zostanie automatycznie odinstalowany.

Moduł AzureInformationProtection obejmuje wszystkie polecenia cmdlet usługi Rights Management z narzędzia RMS Protection Tool i trzy nowe polecenia cmdlet, które korzystają z usługi Azure Information Protection (AIP) na potrzeby etykietowania:

|Polecenie cmdlet dotyczące etykietowania|Przykład użycia|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)|W przypadku folderu udostępnionego wskazuje wszystkie pliki z określoną etykietą.|
|[Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification)|W przypadku folderu udostępnionego sprawdź zawartość pliku, a następnie automatycznie nadaj etykiety plikom bez etykiet, zgodnie z warunkami określonymi przez użytkownika.|
|[Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)|W przypadku folderu udostępnionego dodaje określoną etykietę do wszystkich plików, które nie mają etykiety.|

Aby wyświetlić listę wszystkich poleceń cmdlet oraz odpowiednią dokumentację pomocy zobacz temat [AzureInformationProtection Module](/powershell/module/azureinformationprotection) (Moduł AzureInformationProtection). W sesji programu PowerShell wpisz `Get-Help <cmdlet name> -online`, aby wyświetlić najnowszą pomoc w obsługiwanych językach innych niż angielski.  

Ten moduł instaluje się w lokalizacji **\ProgramFiles (x86)\Microsoft Azure Information Protection** i dodaje ten folder do zmiennej systemowej **PSModulePath**. Plik .dll tego modułu nosi nazwę **AIP.dll**.

Podobnie jak w przypadku modułu RMSProtection, bieżąca wersja modułu AzureInformationProtection ma następujące ograniczenia:

- Można wyłączyć ochronę folderów osobistych programu Outlook (pliki pst), ale obecnie nie można objąć ochroną natywną tych plików ani innych plików kontenera za pomocą tego modułu PowerShell.

- Można wyłączyć ochronę chronionych wiadomości e-mail programu Outlook (pliki .rpmsg) znajdujących się w folderze osobistym programu Outlook (.pst), ale nie można wyłączyć ochrony plików .rpmsg znajdujących się poza folderem osobistym.

Przed rozpoczęciem korzystania z tych poleceń cmdlet zapoznaj się z dodatkowymi wymaganiami wstępnymi i instrukcjami odnoszącymi się do wdrożenia:

- [Usługa Azure Information Protection i usługa Azure Rights Management](#azure-information-protection-service-and-azure-rights-management-service)

    - Dotyczy przypadku, gdy używany jest tryb obejmujący tylko klasyfikację lub klasyfikację z ochroną Rights Management: masz subskrypcję, która obejmuje usługę Azure Information Protection (na przykład Enterprise Mobility + Security).
    - Dotyczy przypadku, gdy używany jest tryb obejmujący tylko ochronę za pomocą usługi Azure Rights Management: masz subskrypcję, która obejmuje usługę Azure Rights Management (na przykład usługi Office 365 E3 i Office 365 E5).

- [Usługi Active Directory Rights Management](#active-directory-rights-management-services)

    - Dotyczy przypadku, gdy używany jest tryb obejmujący tylko ochronę za pomocą lokalnej wersji usługi Azure Rights Management; Usługi Active Directory Rights Management (AD RMS).


## Usługa Azure Information Protection i usługa Azure Rights Management
<a id="azure-information-protection-service-and-azure-rights-management-service" class="xliff"></a>

Przeczytaj tę sekcję przed rozpoczęciem używania poleceń środowiska PowerShell, jeśli Twoja organizacja korzysta z usługi Azure Information Protection i usługi ochrony danych Azure Rights Management lub po prostu z usługi Azure Rights Management.


### Wymagania wstępne
<a id="prerequisites" class="xliff"></a>

Oprócz wymagań wstępnych dotyczących instalacji modułu AzureInformationProtection istnieją dodatkowe wymagania wstępne dotyczące usługi Azure Information Protection i usługi ochrony danych Azure Rights Management:

1. Usługa Azure Rights Management musi być aktywowana.

2. Aby usunąć ochronę plików dla innych osób używających Twojego konta: 
    
    - W organizacji musi być włączona funkcja administratora, a Twoje konto musi być skonfigurowane jako konto administratora usługi Azure Rights Management.

3. Aby bezpośrednio włączać lub wyłączać ochronę plików bez interakcji z użytkownikiem: 
    
    - Utwórz konto jednostki usługi, uruchom polecenie Set-RMSServerAuthentication i ewentualnie ustaw tę jednostkę jako administratora usługi Azure Rights Management.

4. W przypadku regionów poza Ameryką Północną: 
    
    - Edytuj rejestr, aby włączyć uwierzytelnianie w usłudze.

#### Wymaganie wstępne 1: usługa Azure Rights Management musi być aktywowana
<a id="prerequisite-1-the-azure-rights-management-service-must-be-activated" class="xliff"></a>

To wymaganie wstępne dotyczy zarówno sytuacji, gdy stosowana jest ochrona danych za pomocą etykiet, jak i bezpośredniego połączenia z usługą Azure Rights Management w celu zastosowania ochrony danych.

Jeśli dzierżawca usługi Azure Information Protection nie został aktywowany, zobacz instrukcje dotyczące [aktywowania usługi Azure Rights Management](../deploy-use/activate-service.md).

#### Wymaganie wstępne 2: usuwanie ochrony plików dla innych osób używających Twojego konta
<a id="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account" class="xliff"></a>

Typowe scenariusze dotyczące usuwania ochrony plików dla innych osób obejmują odnajdywanie lub odzyskiwanie danych. Jeśli jest stosowana ochrona przy użyciu etykiet, można ją usunąć, ustawiając nową etykietę, która nie stosuje ochrony, lub usuwając etykietę. Wygodniejszym rozwiązaniem jest jednak połączenie się bezpośrednio z usługą Azure Rights Management w celu usunięcia ochrony.

Musisz mieć prawa użytkowania usługi Rights Management do usuwania ochrony plików lub być administratorem. W przypadku odnajdywania lub odzyskiwania danych zwykle jest używana funkcja administratora. Aby włączyć tę funkcję i skonfigurować swoje konto jako administrator, zobacz artykuł [Konfigurowanie superużytkowników usług Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).

#### Wymaganie wstępne 3: włączanie lub wyłączanie ochrony plików bez interakcji z użytkownikiem
<a id="prerequisite-3-to-protect-or-unprotect-files-without-user-interaction" class="xliff"></a>

Obecnie nie można dołączać etykiet w sposób nieinteraktywny, ale można połączyć się bezpośrednio z usługą Azure Rights Management w sposób nieinteraktywny w celu włączenia lub wyłączenia ochrony plików.

Należy użyć jednostki usługi do połączenia się z usługą Azure Rights Management w sposób nieinteraktywny, co można zrobić za pomocą polecenia cmdlet `Set-RMSServerAuthentication`. Należy to zrobić dla każdej sesji środowiska Windows PowerShell korzystającej z poleceń cmdlet, które bezpośrednio łączą się z usługą Azure Rights Management. Przed uruchomieniem tego polecenia cmdlet upewnij się, że masz te trzy identyfikatory:

- Identyfikator BposTenantId

- Identyfikator AppPrincipalId

- Klucz symetryczny

W następnych sekcjach opisano sposób uzyskiwania tych identyfikatorów.

##### Uzyskiwanie identyfikatora BposTenantId
<a id="to-get-the-bpostenantid" class="xliff"></a>

W module Windows PowerShell usługi Azure RMS uruchom polecenie cmdlet Get-AadrmConfiguration:

1. Jeśli ten moduł nie został jeszcze zainstalowany na komputerze, zobacz artykuł [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

2. Uruchom sesję środowiska Windows PowerShell przy użyciu opcji **Uruchom jako administrator**.

3. Użyj polecenia cmdlet `Connect-AadrmService`, aby połączyć się z usługą Azure Rights Management:
    
        Connect-AadrmService
    
    Po wyświetleniu monitu wprowadź poświadczenia administratora dzierżawy usługi Azure Information Protection (zazwyczaj jest używane konto administratora globalnego usługi Azure Active Directory lub Office 365).
    
4. Uruchom polecenie `Get-AadrmConfiguration` i utwórz kopię wartości BPOSId.
    
    Poniżej podano przykład raportu uzyskanego za pomocą polecenia Get-AadrmConfiguration:
    
            BPOSId                                   : 23976bc6-dcd4-4173-9d96-dad1f48efd42
        
            RightsManagement ServiceId               : 1a302373-f233-440600909-4cdf305e2e76
        
            LicensingIntranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
        
            LicensingExtranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
        
            CertificationIntranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification
        
            CertificationExtranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification

5. Zakończ połączenie z usługą:
    
        Disconnect-AadrmService

##### Uzyskiwanie identyfikatora AppPrincipalId i klucza symetrycznego
<a id="to-get-the-appprincipalid-and-symmetric-key" class="xliff"></a>

Utwórz nową jednostkę usługi, uruchamiając polecenie cmdlet `New-MsolServicePrincipal` z modułu MSOnline PowerShell usługi Azure Active Directory i postępuj zgodnie z poniższymi instrukcjami. 

> [!IMPORTANT]
> Do tworzenia tej jednostki usługi nie należy używać nowszego polecenia cmdlet programu Azure AD PowerShell, New-AzureADServicePrincipal. Usługi Azure Rights Management nie obsługują polecenia New-AzureADServicePrincipal. 

1. Jeśli moduł MSOnline nie został jeszcze zainstalowany na komputerze, uruchom polecenie `Install-Module MSOnline`.

2. Uruchom sesję środowiska Windows PowerShell przy użyciu opcji **Uruchom jako administrator**.

3. Użyj polecenia cmdlet **Connect-MsolService**, aby nawiązać połączenie z usługą Azure AD:
    
        Connect-MsolService
    
    Po wyświetleniu monitu wprowadź poświadczenia administratora dzierżawy usługi Azure AD (zazwyczaj jest używane konto administratora globalnego usługi Azure Active Directory lub Office 365).

4. Uruchom polecenie cmdlet New-MsolServicePrincipal, aby utworzyć nową jednostkę usługi:
    
        New-MsolServicePrincipal
    
    Po wyświetleniu monitu wprowadź wybraną nazwę wyświetlaną dla tej jednostki usługi, która pomoże później zidentyfikować jej przeznaczenie jako konta do połączenia się z usługą Azure Rights Management w celu włączania i wyłączania ochrony plików.
    
    Przykład raportu uzyskanego za pomocą polecenia New-MsolServicePrincipal:
    
        Supply values for the following parameters:
        
        DisplayName: AzureRMSProtectionServicePrincipal
        The following symmetric key was created as one was not supplied
        zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=
        
        Display Name: AzureRMSProtectionServicePrincipal
        ServicePrincipalNames: (b5e3f7g1-b5c2-4c96-a594-a0807f65bba4)
        ObjectId: 23720996-593c-4122-bfc7-1abb5a0b5109
        AppPrincialId: b5e3f76a-b5c2-4c96-a594-a0807f65bba4
        TrustedForDelegation: False
        AccountEnabled: True
        Addresses: ()
        KeyType: Symmetric
        KeyId: 8ef61651-ca11-48ea-a350-25834a1ba17c
        StartDate: 3/7/2014 4:43:59 AM
        EndDate: 3/7/2014 4:43:59 AM
        Usage: Verify

5. Z tego raportu zanotuj klucz symetryczny i identyfikator AppPrincialId.

    Zapisanie kopii klucza symetrycznego jest szczególnie ważne, ponieważ później nie będzie możliwości pobrania go w całości, więc jeśli użytkownik go nie zna, będzie musiał utworzyć nową jednostkę usługi przy następnym uwierzytelnianiu w usłudze Azure Rights Management.

Korzystając z tych instrukcji i opierając się na naszych przykładach, uzyskaliśmy trzy identyfikatory wymagane do uruchomienia polecenia Set-RMSServerAuthentication:

- Identyfikator dzierżawcy: **23976bc6-dcd4-4173-9d96-dad1f48efd42**

- Klucz symetryczny: **zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=**

- Identyfikator AppPrincipalId: **b5e3f76a-b5c2-4c96-a594-a0807f65bba4**

Nasze przykładowe polecenie będzie więc wyglądać następująco:

    Set-RMSServerAuthentication -Key zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=-AppPrincipalId b5e3f76a-b5c2-4c96-a594-a0807f65bba4-BposTenantId 23976bc6-dcd4-4173-9d96-dad1f48efd42

Jak pokazano w przypadku poprzedniego polecenia, można dostarczać wartości za pomocą jednego polecenia lub po prostu wpisać polecenie Set-RMSServerAuthentication i podawać kolejno wartości po wyświetleniu monitu. Po zakończeniu działania polecenia zobaczysz komunikat „**The RmsServerAuthentication is set to ON**” (Parametr RmsServerAuthentication został włączony), co oznacza, że klient działa teraz w „trybie serwera”. Ten komunikat nie potwierdza pomyślnego ukończenia uwierzytelniania z użyciem podanych przez Ciebie wartości, ale wskazuje, że przełączanie do trybu serwera powiodło się.

Istnieje możliwość ustawienia tej jednostki usługi jako administratora. Dzięki temu będzie można jej zawsze użyć do wyłączenia ochrony plików dla innych użytkowników. Podobnie jak w przypadku konfigurowania konta użytkownika standardowego jako administratora, można użyć tego samego polecenia cmdlet usługi Azure RMS [Add-AadrmSuperUser](/powershell/aadrm/vlatest/Add-AadrmSuperUser.md), ale dla parametru **-ServicePrincipalId** należy podać wartość identyfikatora AppPrincipalId.

Aby uzyskać więcej informacji na temat administratorów, zobacz artykuł [Konfigurowanie superużytkowników usług Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).

> [!NOTE]
> Aby użyć swojego konta użytkownika do uwierzytelnienia w usłudze Azure Rights Management, nie ma potrzeby uruchamiania polecenia Set-RMSServerAuthentication przed włączeniem lub wyłączeniem ochrony plików albo pobraniem szablonów.

#### Wymaganie wstępne 4: dotyczy regionów poza Ameryką Północną
<a id="prerequisite-4-for-regions-outside-north-america" class="xliff"></a>

W przypadku uwierzytelniania platformy Azure poza regionem Ameryki Północnej należy dokonać edycji rejestru w opisany poniżej sposób. Jeśli Twój dzierżawca usługi Azure Information Protection znajduje się w Ameryce Północnej, nie wykonuj tego kroku:

1. Ponownie uruchom polecenie cmdlet Get-AadrmConfiguration i zanotuj wartości parametrów **CertificationExtranetDistributionPointUrl** i **LicensingExtranetDistributionPointUrl**.

2. Na każdym komputerze, na którym będą uruchamiane polecenia cmdlet AzureInformationProtection, otwórz Edytor rejestru i przejdź do:`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC`

3. Jeśli nie widzisz klucza **ServiceLocation**, utwórz go, tak aby ścieżka rejestru miała postać **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation**

4. Dla klucza **ServiceLocation** utwórz dwa klucze (o ile nie istnieją) o nazwach **EnterpriseCertification** i **EnterprisePublishing**. 
    
    Podczas tworzenia tych kluczy REG_SZ nie należy zmieniać nazwy „(wartość domyślna)”, ale edytować je, aby ustawić wartość danych:

    - Dla klucza **EnterpriseCertification** wklej wartość parametru CertificationExtranetDistributionPointUrl.
    
    - Dla klucza **EnterprisePublishing** wklej wartość parametru LicensingExtranetDistributionPointUrl.

5. Zamknij Edytor rejestru. Nie ma potrzeby ponownego uruchamiania komputera. Jeśli jednak używasz konta jednostki usługi, a nie swojego konta użytkownika, należy po wprowadzeniu zmian w rejestrze uruchomić polecenie Set-RMSServerAuthentication.

### Przykładowe scenariusze użycia poleceń cmdlet usługi Azure Information Protection i Azure Rights Management
<a id="example-scenarios-for-using-the-cmdlets-for-azure-information-protection-and-the-azure-rights-management-service" class="xliff"></a>

Korzystanie z etykiet do klasyfikowania i ochrony plików jest bardziej efektywne, ponieważ potrzebne są tylko dwa polecenia cmdlet, które mogą być uruchamiane osobno lub razem: [Get-AIPFileStatus](/powershell/azureinformationprotection/vlatest/get-aipfilestatus) i [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel). Skorzystaj z pomocy dotyczącej obu tych poleceń cmdlet, aby uzyskać dodatkowe informacje i przykłady.

Aby włączać i wyłączać ochronę plików przy wykorzystaniu bezpośredniego połączenia z usługą Azure Rights Management, należy zazwyczaj uruchamiać serię poleceń cmdlet, zgodnie z poniższym opisem.

Po pierwsze, w razie potrzeby uwierzytelnienia w usłudze Azure Rights Management przy użyciu jednostki usługi zamiast własnego konta, w sesji środowiska Powershell wpisz:

    Set-RMSServerAuthentication

Po wyświetleniu monitu wprowadź trzy identyfikatory zgodnie z opisem w sekcji [Wymagania wstępne 3: włączanie lub wyłączanie ochrony plików bez interakcji z użytkownikiem](client-admin-guide-powershell.md#prerequisite-3-to-protect-or-unprotect-files-without-user-interaction).

Zanim będzie można korzystać z ochrony plików, należy pobrać na komputer szablony usługi Rights Management i określić, który z nich będzie używany wraz z odpowiadającym im numerem identyfikacyjnym. Z raportu można też skopiować identyfikator szablonu:

    Get-RMSTemplate
    
Raport będzie wyglądał podobnie do poniższego:

    TemplateId        : {82bf3474-6efe-4fa1-8827-d1bd93339119}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content cannot be modified.
    Name              : Contoso, Ltd - Confidential View Only
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    
    TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content can be modified but cannot be copied and printed.
    Name              : Contoso, Ltd - Confidential
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    FromTemplate      : True

Należy pamiętać, że jeśli nie zostanie uruchomione polecenie Set-RMSServerAuthentication, uwierzytelnianie w usłudze Azure Rights Management będzie odbywać się przy użyciu własnego konta użytkownika. Jeśli użytkownik pracuje na komputerze przyłączonym do domeny, jego bieżące poświadczenia będą zawsze używane automatycznie. Jeśli użytkownik pracuje na komputerze w grupie roboczej, zostanie wyświetlony monit o zalogowanie się do usługi Azure — poświadczenia te zostaną zapisane w pamięci podręcznej i będą używane przy kolejnych poleceniach. W tym scenariuszu późniejsze logowanie się jako inny użytkownik będzie wymagało użycia polecenia cmdlet `Clear-RMSAuthentication`.

Znasz teraz identyfikator szablonu i możesz użyć go w poleceniu cmdlet `Protect-RMSFile`, aby chronić pojedynczy plik lub wszystkie pliki w folderze. Na przykład: jeśli chcesz chronić tylko jeden plik i zastąpić plik oryginalny, używając szablonu „Contoso, Ltd. — poufne”:

    Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

Raport będzie wyglądał podobnie do poniższego:

    InputFile             EncryptedFile
    ---------             -------------
    C:\Test.docx          C:\Test.docx

Aby chronić wszystkie pliki w folderze, użyj parametru **-Folder** z literą dysku i ścieżką lub ścieżką UNC. Na przykład:

    Protect-RMSFile -Folder \Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

Raport będzie wyglądał podobnie do poniższego:

    InputFile                          EncryptedFile
    ---------                          -------------
    \Server1\Documents\Test1.docx     \Server1\Documents\Test1.docx
    \Server1\Documents\Test2.docx     \Server1\Documents\Test2.docx
    \Server1\Documents\Test3.docx     \Server1\Documents\Test3.docx
    \Server1\Documents\Test4.docx     \Server1\Documents\Test4.docx

Jeśli rozszerzenie nazwy pliku nie zmienia się po zastosowaniu ochrony, zawsze można użyć polecenia cmdlet `Get-RMSFileStatus` później, aby sprawdzić, czy plik jest chroniony. Na przykład:

    Get-RMSFileStatus -File \Server1\Documents\Test1.docx

Raport będzie wyglądał podobnie do poniższego:

    FileName                              Status
    --------                              ------
    \Server1\Documents\Test1.docx         Protected

Aby usunąć ochronę pliku, użytkownik musi mieć uprawnienia właściciela lub uprawnienia do wyodrębniania, począwszy od momentu włączenia ochrony pliku, lub musi uruchamiać polecenia cmdlet jako administrator. Następnie należy użyć polecenia cmdlet Unprotect. Na przykład:

    Unprotect-RMSFile C:\test.docx -InPlace

Raport będzie wyglądał podobnie do poniższego:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx

Należy pamiętać, że jeśli do szablonów usługi Rights Management zostaną wprowadzone zmiany, należy pobrać je ponownie przy użyciu polecenia `Get-RMSTemplate -force`. 

## Usługi Active Directory Rights Management
<a id="active-directory-rights-management-services" class="xliff"></a>

Przeczytaj tę sekcję przed rozpoczęciem korzystania z poleceń środowiska PowerShell w celu włączania lub wyłączania ochrony plików, jeśli Twoja organizacja używa tylko usług Active Directory Rights Management.


### Wymagania wstępne
<a id="prerequisites" class="xliff"></a>

Oprócz wymagań wstępnych instalacji modułu AzureInformationProtection konto musi mieć uprawnienia odczytu i wykonywania, aby mieć dostęp do pliku ServerCertification.asmx:

1. Zaloguj się do serwera usług AD RMS.

2. Kliknij pozycję **Start**, a następnie **Komputer**.

3. W Eksploratorze plików przejdź do lokalizacji %systemdrive%\Initpub\wwwroot\_wmsc\Certification.

4. Kliknij prawym przyciskiem myszy plik **ServerCertification.asmx**, następnie kliknij polecenie **Właściwości**.

5. W oknie dialogowym **Właściwości pliku ServerCertification.asmx** kliknij kartę **Zabezpieczenia**. 

6. Kliknij przycisk **Kontynuuj** lub **Edytuj**. 

7. W oknie dialogowym **Uprawnienia dla pliku ServerCertification.asmx** kliknij przycisk **Dodaj**. 

8. Dodaj nazwę swojego konta. Jeśli inni administratorzy usługi AD RMS również używają tych poleceń cmdlet do włączania i wyłączania ochrony plików, należy dodać także ich nazwy.

9. Upewnij się, że w kolumnie **Zezwalaj** są zaznaczone pola wyboru **Odczyt i wykonywanie** oraz **Odczyt**.

10. Kliknij dwukrotnie przycisk **OK**.

### Przykładowe scenariusze używania poleceń cmdlet dotyczące usług Active Directory Rights Management
<a id="example-scenarios-for-using-the-cmdlets-for-active-directory-rights-management-services" class="xliff"></a>

Typowy scenariusz użycia tych poleceń cmdlet obejmuje ochronę wszystkich plików w folderze przy użyciu szablonu zasad lub usunięcie ochrony pliku. 

Po pierwsze, jeśli masz więcej niż jedno wdrożenie usługi AD RMS, konieczne będzie uzyskanie nazw serwerów usługi AD RMS. Można to osiągnąć przy użyciu polecenia cmdlet Get-RMSServer, które wyświetla listę dostępnych serwerów:

    Get-RMSServer

Raport będzie wyglądał podobnie do poniższego:

    Number of RMS Servers that can provide templates: 2 
    ConnectionInfo             DisplayName          AllowFromScratch
    --------------             -------------        ----------------
    Microsoft.InformationAnd…  RmsContoso                       True
    Microsoft.InformationAnd…  RmsFabrikam                      True

Zanim będzie można korzystać z ochrony plików, należy uzyskać listę szablonów RMS i określić, który z nich będzie używany wraz z odpowiadającym numerem identyfikacyjnym. Dopiero wtedy, gdy masz więcej niż jedno wdrożenie usługi AD RMS, będzie trzeba określić również serwer RMS. 

Z raportu można też skopiować identyfikator szablonu:

    Get-RMSTemplate -RMSServer RmsContoso

Raport będzie wyglądał podobnie do poniższego:

    TemplateId        : {82bf3474-6efe-4fa1-8827-d1bd93339119}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content cannot be modified.
    Name              : Contoso, Ltd - Confidential View Only
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    
    
    TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content can be modified but cannot be copied and printed.
    Name              : Contoso, Ltd - Confidential
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    FromTemplate      : True

Znasz teraz identyfikator szablonu i możesz użyć go w poleceniu cmdlet Protect-RMSFile, aby chronić pojedynczy plik lub wszystkie pliki w folderze. Na przykład: jeśli chcesz chronić tylko jeden plik i zastąpić plik oryginalny, używając szablonu „Contoso, Ltd. — poufne”:

    Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

Raport będzie wyglądał podobnie do poniższego:

    InputFile             EncryptedFile
    ---------             -------------
    C:\Test.docx          C:\Test.docx   

Aby chronić wszystkie pliki w folderze, użyj parametru -Folder z literą dysku i ścieżką lub ścieżką UNC. Na przykład:

    Protect-RMSFile -Folder \\Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

Raport będzie wyglądał podobnie do poniższego:

    InputFile                          EncryptedFile
    ---------                          -------------
    \\Server1\Documents\Test1.docx     \\Server1\Documents\Test1.docx   
    \\Server1\Documents\Test2.docx     \\Server1\Documents\Test2.docx   
    \\Server1\Documents\Test3.docx     \\Server1\Documents\Test3.docx   
    \\Server1\Documents\Test4.docx     \\Server1\Documents\Test4.docx   

Jeśli rozszerzenie nazwy pliku nie zmienia się po zastosowaniu ochrony RMS, zawsze można użyć polecenia cmdlet Get-RMSFileStatus później, aby sprawdzić, czy plik jest chroniony. Na przykład: 

    Get-RMSFileStatus -File \\Server1\Documents\Test1.docx

Raport będzie wyglądał podobnie do poniższego:

    FileName                              Status
    --------                              ------
    \\Server1\Documents\Test1.docx        Protected

Aby usunąć ochronę pliku, użytkownik musi mieć uprawnienia właściciela lub uprawnienia do wyodrębniania, począwszy od momentu włączenia ochrony pliku, lub musi być administratorem w usłudze AD RMS. Następnie należy użyć polecenia cmdlet Unprotect. Na przykład:

    Unprotect-RMSFile C:\test.docx -InPlace

Raport będzie wyglądał podobnie do poniższego:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx


## Następne kroki
<a id="next-steps" class="xliff"></a>
Aby korzystać z pomocy polecenia cmdlet w sesji środowiska PowerShell należy użyć polecenia cmdlet Get-Help <cmdlet name>, gdzie <cmdlet name> to nazwa polecenia cmdlet, które chcesz zbadać. Na przykład: 

    Get-Help Get-RMSTemplate

Zobacz następujące artykuły, aby uzyskać dodatkowe informacje potrzebne do obsługi klienta usługi Azure Information Protection:

- [Dostosowania](client-admin-guide-customizations.md)

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
