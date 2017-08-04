---
title: "Używanie środowiska PowerShell z klientem usługi Azure Information Protection"
description: "Instrukcje i informacje dla administratorów dotyczące zarządzania klientem usługi Azure Information Protection przy użyciu środowiska PowerShell."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4f9d2db7-ef27-47e6-b2a8-d6c039662d3c
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 618e8b6a160ccc699658bf8c317c40ed2ded3bee
ms.sourcegitcommit: 87f0c7a8f9f1fdf7eece0f9d0c114ecf91f57683
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="using-powershell-with-the-azure-information-protection-client"></a>Używanie środowiska PowerShell z klientem usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Polecenia programu PowerShell są instalowane automatycznie podczas instalowania klienta Azure Information Protection. Dzięki temu można zarządzać klientem przy użyciu poleceń, które można umieścić w skryptów do automatyzacji.

Polecenia cmdlet są instalowane przy użyciu modułu programu PowerShell **AzureInformationProtection**. Ten moduł zastępuje moduł RMSProtection instalowany razem z narzędziem RMS Protection Tool. Jeśli przed instalacją klienta usługi Azure Information Protection było już zainstalowane narzędzie RMS Protection Tool, moduł RMSProtection zostanie automatycznie odinstalowany.

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

- Można wyłączyć ochronę chronionych wiadomości e-mail programu Outlook (pliki rpmsg) znajdujących się w folderze osobistym programu Outlook (.pst), ale nie można wyłączyć ochrony plików rpmsg znajdujących się poza folderem osobistym.

Przed rozpoczęciem korzystania z tych poleceń cmdlet zapoznaj się z dodatkowymi wymaganiami wstępnymi i instrukcjami odnoszącymi się do wdrożenia:

- [Usługa Azure Information Protection i usługi Azure Rights Management](#azure-information-protection-service-and-azure-rights-management-service)

    - Dotyczy przypadku, gdy używany jest tryb obejmujący tylko klasyfikację lub klasyfikację z ochroną Rights Management: masz subskrypcję, która obejmuje usługę Azure Information Protection (na przykład Enterprise Mobility + Security).
    - Dotyczy przypadku, gdy używany jest tryb obejmujący tylko ochronę za pomocą usługi Azure Rights Management: masz subskrypcję, która obejmuje usługę Azure Rights Management (na przykład usługi Office 365 E3 i Office 365 E5).

- [Usługi Active Directory Rights Management](#active-directory-rights-management-services)

    - Dotyczy przypadku, gdy używany jest tryb obejmujący tylko ochronę za pomocą lokalnej wersji usługi Azure Rights Management; Usługi Active Directory Rights Management (AD RMS).


## <a name="azure-information-protection-and-azure-rights-management-service"></a>Usługa Azure Information Protection i usługi Azure Rights Management

Przeczytaj tę sekcję, przed rozpoczęciem za pomocą poleceń programu PowerShell, jeśli Twoja organizacja korzysta z usługi Azure Information Protection dla klasyfikacji i ochrony lub tylko usługa Azure Rights Management do ochrony danych.


### <a name="prerequisites"></a>Wymagania wstępne

Oprócz wymagań wstępnych dotyczących instalowania modułu AzureInformationProtection istnieją dodatkowe wymagania wstępne dotyczące usługi Azure Information Protection, etykietowania i usługi ochrony danych usługi Azure Rights Management:

1. Usługa Azure Rights Management musi być aktywowana.

2. Aby usunąć ochronę plików dla innych osób używających Twojego konta: 
    
    - W organizacji musi być włączona funkcja administratora, a Twoje konto musi być skonfigurowane jako konto administratora usługi Azure Rights Management.

3. Aby bezpośrednio włączać lub wyłączać ochronę plików bez interakcji z użytkownikiem: 
    
    - Utwórz konto jednostki usługi, uruchom polecenie Set-RMSServerAuthentication i ewentualnie ustaw tę jednostkę jako administratora usługi Azure Rights Management.

4. W przypadku regionów poza Ameryką Północną: 
    
    - Edytuj rejestr, aby włączyć uwierzytelnianie w usłudze.

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>Wymaganie wstępne 1: usługa Azure Rights Management musi być aktywowana

To wymaganie wstępne dotyczy zarówno sytuacji, gdy stosowana jest ochrona danych za pomocą etykiet, jak i bezpośredniego połączenia z usługą Azure Rights Management w celu zastosowania ochrony danych.

Jeśli dzierżawca usługi Azure Information Protection nie został aktywowany, zobacz instrukcje dotyczące [aktywowania usługi Azure Rights Management](../deploy-use/activate-service.md).

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>Wymaganie wstępne 2: usuwanie ochrony plików dla innych osób używających Twojego konta

Typowe scenariusze dotyczące usuwania ochrony plików dla innych osób obejmują odnajdywanie lub odzyskiwanie danych. Jeśli jest stosowana ochrona przy użyciu etykiet, można ją usunąć, ustawiając nową etykietę, która nie stosuje ochrony, lub usuwając etykietę. Wygodniejszym rozwiązaniem jest jednak połączenie się bezpośrednio z usługą Azure Rights Management w celu usunięcia ochrony.

Musisz mieć prawa użytkowania usługi Rights Management do usuwania ochrony plików lub być administratorem. W przypadku odnajdywania lub odzyskiwania danych zwykle jest używana funkcja administratora. Aby włączyć tę funkcję i skonfigurować swoje konto jako administrator, zobacz artykuł [Konfigurowanie superużytkowników usług Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).

#### <a name="prerequisite-3-to-protect-or-unprotect-files-without-user-interaction"></a>Wymaganie wstępne 3: włączanie lub wyłączanie ochrony plików bez interakcji z użytkownikiem

Można połączyć się bezpośrednio do usługi Azure Rights Management nieinteraktywnie do Włączanie lub wyłączanie ochrony plików.

Należy użyć jednostki usługi do połączenia się z usługą Azure Rights Management w sposób nieinteraktywny, co można zrobić za pomocą polecenia cmdlet `Set-RMSServerAuthentication`. Należy to zrobić dla każdej sesji środowiska Windows PowerShell korzystającej z poleceń cmdlet, które bezpośrednio łączą się z usługą Azure Rights Management. Przed uruchomieniem tego polecenia cmdlet, musi mieć tych identyfikatorów:

- Identyfikator BposTenantId

- Identyfikator AppPrincipalId

- Klucz symetryczny

Automatycznie pobrać wartości identyfikatorów i uruchomić polecenia cmdlet Set-RMSServerAuthentication, można użyć następujących poleceń programu PowerShell i instrukcje komentarze. Alternatywnie możesz ręcznie pobrać i określ wartości.

Aby automatycznie pobiera wartości i uruchomić Set-RMSServerAuthentication:

````
# Make sure that you have the AADRM and MSOnline modules installed

$newServicePrincipalName="<new service principal name>"
Connect-AadrmService
$bposTenantID=(Get-AadrmConfiguration).BPOSId
Disconnect-AadrmService
New-MsolServicePrincipal -DisplayName $servicePrincipalName

# Copy the value of the generated symmetric key

$symmetricKey="<value from the display of the New-MsolServicePrincipal command>"
$appPrincipalID=(Get-MsolServicePrincipal | Where { $_.DisplayName -eq $servicePrincipalName }).AppPrincipalId
Set-RMSServerAuthentication -Key $symmetricKey -AppPrincipalId $appPrincipalID -BposTenantId $bposTenantID

````

W kolejnych sekcjach wyjaśniono, jak ręcznie pobrać i określ te wartości z dodatkowymi informacjami na temat każdego z nich.

##### <a name="to-get-the-bpostenantid"></a>Uzyskiwanie identyfikatora BposTenantId

W module Windows PowerShell usługi Azure RMS uruchom polecenie cmdlet Get-AadrmConfiguration:

1. Jeśli ten moduł nie został jeszcze zainstalowany na komputerze, zobacz artykuł [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

2. Uruchom sesję środowiska Windows PowerShell przy użyciu opcji **Uruchom jako administrator**.

3. Użyj polecenia cmdlet `Connect-AadrmService`, aby połączyć się z usługą Azure Rights Management:
    
        Connect-AadrmService
    
    Po wyświetleniu monitu wprowadź poświadczenia administratora dzierżawy usługi Azure Information Protection. Zazwyczaj używasz konta administratora globalnego usługi Azure Active Directory lub Office 365.
    
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

##### <a name="to-get-the-appprincipalid-and-symmetric-key"></a>Uzyskiwanie identyfikatora AppPrincipalId i klucza symetrycznego

Utwórz nową jednostkę usługi, uruchamiając polecenie cmdlet `New-MsolServicePrincipal` z modułu MSOnline PowerShell usługi Azure Active Directory i postępuj zgodnie z poniższymi instrukcjami. 

> [!IMPORTANT]
> Do tworzenia tej jednostki usługi nie należy używać nowszego polecenia cmdlet programu Azure AD PowerShell, New-AzureADServicePrincipal. Usługa Azure Rights Management nie obsługuje polecenia New-AzureADServicePrincipal. 

1. Jeśli moduł MSOnline nie został jeszcze zainstalowany na komputerze, uruchom polecenie `Install-Module MSOnline`.

2. Uruchom sesję środowiska Windows PowerShell przy użyciu opcji **Uruchom jako administrator**.

3. Użyj polecenia cmdlet **Connect-MsolService**, aby nawiązać połączenie z usługą Azure AD:
    
        Connect-MsolService
    
    Po wyświetleniu monitu wprowadź poświadczenia administratora dzierżawy usługi Azure AD (zazwyczaj użytkownik korzysta z konta administratora globalnego dla usługi Azure Active Directory lub Office 365).

4. Uruchom polecenie cmdlet New-MsolServicePrincipal, aby utworzyć nową jednostkę usługi:
    
        New-MsolServicePrincipal
    
    Po wyświetleniu monitu wprowadź wybraną nazwę wyświetlaną dla tej jednostki usługi, która pomoże później zidentyfikować jej przeznaczenie jako konta do łączenia się z usługą Azure Rights Management w celu włączania i wyłączania ochrony plików.
    
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

    Należy utworzyć kopię tego klucza symetrycznego. Ten klucz nie może pobrać później, dlatego jeśli nie znasz go podczas następnie wymagany do uwierzytelniania usługi Azure Rights Management, trzeba utworzyć nową główną nazwę usługi.

Korzystając z tych instrukcji i opierając się na naszych przykładach, uzyskaliśmy trzy identyfikatory wymagane do uruchomienia polecenia Set-RMSServerAuthentication:

- Identyfikator dzierżawcy: **23976bc6-dcd4-4173-9d96-dad1f48efd42**

- Klucz symetryczny: **zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=**

- Identyfikator AppPrincipalId: **b5e3f76a-b5c2-4c96-a594-a0807f65bba4**

Nasze przykładowe polecenie będzie więc wyglądać następująco:

    Set-RMSServerAuthentication -Key zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=-AppPrincipalId b5e3f76a-b5c2-4c96-a594-a0807f65bba4-BposTenantId 23976bc6-dcd4-4173-9d96-dad1f48efd42

Jak pokazano w przypadku poprzedniego polecenia, można dostarczać wartości za pomocą jednego polecenia lub po prostu wpisać polecenie Set-RMSServerAuthentication i podawać kolejno wartości po wyświetleniu monitu. Po zakończeniu działania polecenia zobaczysz komunikat „**The RmsServerAuthentication is set to ON**” (Parametr RmsServerAuthentication został włączony), co oznacza, że klient działa teraz w „trybie serwera”. Ten komunikat nie potwierdza pomyślnego ukończenia uwierzytelniania z użyciem podanych przez Ciebie wartości, ale wskazuje, że przełączanie do trybu serwera powiodło się.

Istnieje możliwość ustawienia tej jednostki usługi jako administratora. Dzięki temu będzie można jej zawsze użyć do wyłączenia ochrony plików dla innych użytkowników. W ten sam sposób jak skonfigurować konto użytkownika standardowego jako superużytkowników, używasz tego samego polecenia cmdlet usługi Azure RMS [Add-AadrmSuperUser](/powershell/aadrm/vlatest/Add-AadrmSuperUser.md), ale określ **ServicePrincipalId** parametru z wartością AppPrincipalId.

Aby uzyskać więcej informacji na temat administratorów, zobacz artykuł [Konfigurowanie superużytkowników usług Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).

> [!NOTE]
> Aby użyć swojego konta użytkownika do uwierzytelnienia w usłudze Azure Rights Management, nie ma potrzeby uruchamiania polecenia Set-RMSServerAuthentication przed włączeniem lub wyłączeniem ochrony plików albo pobraniem szablonów.




#### <a name="prerequisite-4-for-regions-outside-north-america"></a>Wymaganie wstępne 4: dotyczy regionów poza Ameryką Północną

W przypadku uwierzytelniania platformy Azure poza regionem Ameryki Północnej należy dokonać edycji rejestru w opisany poniżej sposób. Jeśli Twój dzierżawca usługi Azure Information Protection znajduje się w Ameryce Północnej, nie wykonuj tego kroku:

1. Ponownie uruchom polecenie cmdlet Get-AadrmConfiguration i zanotuj wartości parametrów **CertificationExtranetDistributionPointUrl** i **LicensingExtranetDistributionPointUrl**.

2. Na każdym komputerze, na którym będą uruchamiane polecenia cmdlet modułu AzureInformationProtection, otwórz edytor rejestru i przejdź do: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC`

3. Jeśli nie widzisz klucza **ServiceLocation**, utwórz go, tak aby ścieżka rejestru miała postać **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation**

4. Dla klucza **ServiceLocation** utwórz dwa klucze (o ile nie istnieją) o nazwach **EnterpriseCertification** i **EnterprisePublishing**. 
    
    Wartości ciągu, który jest automatycznie tworzony tych kluczy nie należy zmieniać nazwy "(ustawienie domyślne)", ale edytować ciąg do ustawienia danych wartości:

    - Dla klucza **EnterpriseCertification** wklej wartość parametru CertificationExtranetDistributionPointUrl.
    
    - Dla klucza **EnterprisePublishing** wklej wartość parametru LicensingExtranetDistributionPointUrl.
    
    Na przykład wpis rejestru dla EnterpriseCertification powinien wyglądać podobnie do następującego:
    
    ![Edycja rejestru dla modułu Azure PowerShell ochrony informacji dla regionów poza Ameryka Północna](../media/registry-example-rmsprotection.png)

5. Zamknij Edytor rejestru. Nie ma potrzeby ponownego uruchamiania komputera. Jeśli jednak używasz konta jednostki usługi, a nie swojego konta użytkownika, należy po wprowadzeniu zmian w rejestrze uruchomić polecenie Set-RMSServerAuthentication.

### <a name="example-scenarios-for-using-the-cmdlets-for-azure-information-protection-and-the-azure-rights-management-service"></a>Przykładowe scenariusze użycia poleceń cmdlet usługi Azure Information Protection i Azure Rights Management

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

Należy pamiętać, że jeśli nie zostanie uruchomione polecenie Set-RMSServerAuthentication, uwierzytelnianie w usłudze Azure Rights Management odbywa się przy użyciu własnego konta użytkownika. Jeśli użytkownik pracuje na komputerze przyłączonym do domeny, jego bieżące poświadczenia są zawsze używane automatycznie. Jeśli użytkownik pracuje na komputerze w grupie roboczej, jest wyświetlany monit o zalogowanie się do platformy Azure — poświadczenia te zostaną zapisane w pamięci podręcznej i będą używane przy kolejnych poleceniach. W tym scenariuszu późniejsze logowanie się jako inny użytkownik będzie wymagało użycia polecenia cmdlet `Clear-RMSAuthentication`.

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

Aby wyłączyć ochronę pliku, musi mieć prawa właściciela lub wyodrębniania z gdy plik jest chroniony. Lub poleceń cmdlet należy uruchomić jako użytkownika nadrzędnego. Następnie należy użyć polecenia cmdlet Unprotect. Na przykład:

    Unprotect-RMSFile C:\test.docx -InPlace

Raport będzie wyglądał podobnie do poniższego:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx

Należy pamiętać, że jeśli do szablonów usługi Rights Management zostaną wprowadzone zmiany, należy pobrać je ponownie przy użyciu polecenia `Get-RMSTemplate -force`. 

## <a name="active-directory-rights-management-services"></a>Usługi Active Directory Rights Management

Przeczytaj tę sekcję przed rozpoczęciem korzystania z poleceń środowiska PowerShell w celu włączania lub wyłączania ochrony plików, jeśli Twoja organizacja używa tylko usług Active Directory Rights Management.


### <a name="prerequisites"></a>Wymagania wstępne

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

### <a name="example-scenarios-for-using-the-cmdlets-for-active-directory-rights-management-services"></a>Przykładowe scenariusze używania poleceń cmdlet dotyczące usług Active Directory Rights Management

Typowy scenariusz użycia tych poleceń cmdlet obejmuje ochronę wszystkich plików w folderze przy użyciu szablonu zasad lub usunięcie ochrony pliku. 

Po pierwsze, jeśli masz więcej niż jedno wdrożenie usług AD RMS, konieczne jest uzyskanie nazw serwerów usług AD RMS. W tym celu można użyć polecenia cmdlet Get-RMSServer, które wyświetla listę dostępnych serwerów:

    Get-RMSServer

Raport będzie wyglądał podobnie do poniższego:

    Number of RMS Servers that can provide templates: 2 
    ConnectionInfo             DisplayName          AllowFromScratch
    --------------             -------------        ----------------
    Microsoft.InformationAnd…  RmsContoso                       True
    Microsoft.InformationAnd…  RmsFabrikam                      True

Zanim będzie można korzystać z ochrony plików, należy uzyskać listę szablonów RMS i określić, który z nich będzie używany wraz z odpowiadającym numerem identyfikacyjnym. Tylko w przypadku więcej niż jednego wdrożenia usług AD RMS trzeba określić także serwer usług RMS. 

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

Jeśli rozszerzenie nazwy pliku nie zmienia się po zastosowaniu ochrony, zawsze służy polecenie cmdlet Get-RMSFileStatus później do sprawdzenia, czy plik jest chroniony. Na przykład: 

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

## <a name="how-to-label-files-non-interactively-for-azure-information-protection"></a>Jak nieinteraktywnie etykietować pliki na potrzeby usługi Azure Information Protection

Począwszy od wersji 1.8.41.0 klienta Azure Information Protection (obecnie w wersji zapoznawczej), polecenia cmdlet służące do etykietowania w trybie nieinteraktywnym można uruchamiać przy użyciu polecenia cmdlet **Set-AIPAuthentication**.

Domyślnie polecenia cmdlet służące do etykietowania są uruchamiane we własnym kontekście użytkownika w interaktywnej sesji programu PowerShell. Aby uruchamiać polecenia w trybie nienadzorowanym, utwórz nowe konto użytkownika usługi Azure AD. Następnie w kontekście tego użytkownika uruchom polecenie cmdlet Set-AIPAuthentication, aby skonfigurować i przechowywać poświadczenia przy użyciu tokenu dostępu z usługi Azure AD. To konto użytkownika jest następnie uwierzytelniane i uruchamiane dla usługi Azure Rights Management. Konto pobiera zasady usługi Azure Information Protection i wszystkie szablony usług Rights Management używane w etykietach.

Przy pierwszym uruchomieniu tego polecenia cmdlet zostanie wyświetlony monit o zalogowanie do usługi Azure Information Protection. Podaj nazwę i hasło konta użytkownika utworzonego na potrzeby pracy w trybie nienadzorowanym. Następnie na tym koncie będzie można uruchamiać polecenia cmdlet nieinteraktywnego etykietowania do momentu wygaśnięcia ważności tokenu uwierzytelniania. Po wygaśnięciu ważności tokenu uruchom polecenie cmdlet ponownie, aby uzyskać nowy token:

Po uruchomieniu tego polecenia cmdlet bez parametrów konto uzyskuje token dostępu, który jest ważny przez 90 dni lub do momentu wygaśnięcia ważności hasła.  

Aby kontrolować moment wygaśnięcia ważności tokenu dostępu, uruchom to polecenie cmdlet z parametrami. Umożliwi to skonfigurowanie tokenu dostępu na jeden rok, dwa lata lub bez określonej daty wygaśnięcia. Ta konfiguracja wymaga zarejestrowania dwóch aplikacji w usłudze Azure Active Directory: **aplikacji sieci Web/interfejsu API** i **aplikacji natywnej**. Parametry tego polecenia cmdlet używają wartości z tych aplikacji.

Po uruchomieniu tego polecenia cmdlet możesz uruchomić polecenia cmdlet etykietowania w kontekście utworzonego konta użytkownika.

### <a name="to-create-and-configure-the-azure-ad-applications-for-set-aipauthentication"></a>Tworzenie i konfigurowanie aplikacji usługi Azure AD na potrzeby polecenia Set-AIPAuthentication

1. W nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com/).

2. W przypadku dzierżawcy usługi Azure AD, który jest używany z usługą Azure Information Protection, przejdź do pozycji **Azure Active Directory** > **Rejestracje aplikacji**. 

3. Wybierz pozycję **Rejestrowanie nowej aplikacji**, aby utworzyć aplikację sieci Web/interfejsu API. Na etykiecie **Utwórz** określ następujące wartości, a następnie kliknij pozycję **Utwórz**:
    
    - Nazwa: **AIPOnBehalfOf**
    
    Jeśli chcesz, podaj inną nazwę. Nazwa musi być unikatowa dla dzierżawy.
    
    - Typ aplikacji: **Aplikacja sieci Web/interfejs API**
    
    - Adres URL logowania: **http://localhost**

4. Wybierz właśnie utworzoną aplikację, na przykład **AIPOnBehalfOf**. Następnie w bloku **Ustawienia** wybierz pozycję **Właściwości**. Z bloku **Właściwości** skopiuj wartość **Identyfikator aplikacji**, a następnie zamknij ten blok. 
    
    Ta wartość jest używana dla parametru `WebAppId` podczas uruchamiania polecenia cmdlet Set-AIPAuthentication.

5. W bloku **Ustawienia** wybierz pozycję **Klucze**. Dodaj nowy klucz, podając opis i wybierając czas trwania (1 rok, 2 lata lub bez daty wygaśnięcia). Następnie wybierz pozycję **Zapisz** i skopiuj ciąg wyświetlony w polu **Wartość**. Ważne jest, aby zapisać ten ciąg, ponieważ nie jest on wyświetlany ponownie i nie można go pobrać. Podobnie jak w przypadku każdego używanego klucza, przechowuj zapisaną wartość w bezpiecznym miejscu i ogranicz dostęp do niej.
    
    Ta wartość jest używana dla parametru `WebAppKey` podczas uruchamiania polecenia cmdlet Set-AIPAuthentication.

6. W bloku **Rejestracje aplikacji** wybierz ponownie pozycję **Rejestrowanie nowej aplikacji**, aby utworzyć aplikację natywną. Na etykiecie **Utwórz** określ następujące wartości, a następnie kliknij pozycję **Utwórz**:
    
    - Nazwa: **AIPClient**
    
    Jeśli chcesz, podaj inną nazwę. Nazwa musi być unikatowa dla dzierżawy.
    
    - Typ aplikacji: **Natywna**
    
    - Adres URL logowania: **http://localhost**

7. Wybierz właśnie utworzoną aplikację, na przykład **AIPClient**. Następnie w bloku **Ustawienia** wybierz pozycję **Właściwości**. Z bloku **Właściwości** skopiuj wartość **Identyfikator aplikacji**, a następnie zamknij ten blok.
    
    Ta wartość jest używana dla parametru `NativeAppId` podczas uruchamiania polecenia cmdlet Set-AIPAuthentication.

8. W bloku **Ustawienia** wybierz pozycję **Wymagane uprawnienia**. 

9. W bloku **Wymagane uprawnienia** kliknij pozycję **Dodaj**, a następnie kliknij pozycję **Wybierz interfejs API**. W polu wyszukiwania wpisz **AIPOnBehalfOf**. Wybierz tę wartość w polu listy, a następnie kliknij pozycję **Wybierz**.

10. W bloku **Włączanie dostępu** wybierz pozycję **AIPOnBehalfOf**, kliknij pozycję **Wybierz**, a następnie kliknij pozycję **Gotowe**.
    
    Konfiguracja dwóch aplikacji została zakończona. Masz teraz wartości potrzebne do uruchomienia polecenia [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) z parametrami.


## <a name="next-steps"></a>Następne kroki
Aby uzyskać pomoc dotyczącą polecenia cmdlet w trakcie sesji programu PowerShell, wpisz ciąg `Get-Help <cmdlet name> cmdlet` i użyj parametru -online w celu zapoznania się z najbardziej aktualnymi informacjami. Na przykład: 

    Get-Help Get-RMSTemplate -online

Zobacz następujące artykuły, aby uzyskać dodatkowe informacje potrzebne do obsługi klienta usługi Azure Information Protection:

- [Dostosowania](client-admin-guide-customizations.md)

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
