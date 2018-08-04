---
title: Używanie środowiska PowerShell z klientem usługi Azure Information Protection
description: Instrukcje i informacje dla administratorów dotyczące zarządzania klientem usługi Azure Information Protection przy użyciu środowiska PowerShell.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/26/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4f9d2db7-ef27-47e6-b2a8-d6c039662d3c
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 263806540ae2d7ef38132529a2d04a68fb705e52
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39489733"
---
# <a name="admin-guide-using-powershell-with-the-azure-information-protection-client"></a>Podręcznik administratora: Przy użyciu programu PowerShell z klientem usługi Azure Information Protection

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, systemu Windows Server 2008 R2*

Polecenia programu PowerShell są instalowane automatycznie podczas instalowania klienta usługi Azure Information Protection. Umożliwia to Zarządzanie klientem poprzez uruchamianie poleceń, które można umieścić w skryptach automatyzacji.

Polecenia cmdlet są instalowane przy użyciu modułu programu PowerShell **AzureInformationProtection**. Ten moduł zawiera wszystkie cmdlet usługi Rights Management z narzędzia RMS Protection Tool (nie jest już obsługiwane). Istnieją również polecenia cmdlet, używanego przez usługi Azure Information Protection do etykietowania. Przykład:

|Polecenie cmdlet dotyczące etykietowania|Przykład użycia|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)|W przypadku folderu udostępnionego wskazuje wszystkie pliki z określoną etykietą.|
|[Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification)|W przypadku folderu udostępnionego sprawdź zawartość pliku, a następnie automatycznie nadaj etykiety plikom bez etykiet, zgodnie z warunkami określonymi przez użytkownika.|
|[Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)|W przypadku folderu udostępnionego dodaje określoną etykietę do wszystkich plików, które nie mają etykiety.|
|[Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)|Oznaczyć pliki nieinteraktywnego, na przykład za pomocą skryptu uruchamianego zgodnie z harmonogramem.|

> [!TIP]
> Aby używać poleceń cmdlet o długości większej niż 260 znaków, należy użyć następującego [ustawienie zasad grupy](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/) dostępna w Rocznicowej aktualizacji systemu Windows 10:<br /> **Lokalne zasady komputera** > **konfiguracji komputera** > **Szablony administracyjne** > **wszystkie ustawienia**  >  **NTFS** > **Win32 włączyć długie ścieżki** 
> 
> Dla systemu Windows Server 2016 można użyć tego samego ustawienia zasad grupy, po zainstalowaniu najnowszych szablonów administracyjnych (ADMX) dla systemu Windows 10.

[Skanera usługi Azure Information Protection] wdrażanie — usługi aip — scanner.md) używa poleceń cmdlet z modułu AzureInformationProtection, aby zainstalować i skonfigurować usługę w systemie Windows Server. Skaner to pozwala następnie odnajdywania, klasyfikowania i ochrony plików w magazynach danych.

Aby wyświetlić listę wszystkich poleceń cmdlet oraz odpowiednią dokumentację pomocy zobacz temat [AzureInformationProtection Module](/powershell/module/azureinformationprotection) (Moduł AzureInformationProtection). W ramach sesji programu PowerShell, wpisz `Get-Help <cmdlet name> -online` Aby wyświetlić najnowszą Pomoc.  

Ten moduł instaluje się w lokalizacji **\ProgramFiles (x86)\Microsoft Azure Information Protection** i dodaje ten folder do zmiennej systemowej **PSModulePath**. Plik .dll tego modułu nosi nazwę **AIP.dll**.

Obecnie zainstalować moduł jako jeden z użytkowników i uruchamiania poleceń cmdlet na tym samym komputerze jako inny użytkownik, należy najpierw uruchomić `Import-Module AzureInformationProtection` polecenia. W tym scenariuszu moduł nie Załaduj przy pierwszym uruchomieniu polecenia cmdlet.

Bieżąca wersja modułu AzureInformationProtection ma następujące ograniczenia:

- Można wyłączyć ochronę folderów osobistych programu Outlook (pliki pst), ale obecnie nie można objąć ochroną natywną tych plików ani innych plików kontenera za pomocą tego modułu PowerShell.

- Można wyłączyć ochronę chronionych wiadomości e-mail programu Outlook (pliki rpmsg) znajdujących się w folderze osobistym programu Outlook (.pst), ale nie można wyłączyć ochrony plików rpmsg znajdujących się poza folderem osobistym.

Przed rozpoczęciem korzystania z tych poleceń cmdlet zapoznaj się z dodatkowymi wymaganiami wstępnymi i instrukcjami odnoszącymi się do wdrożenia:

- [Usługa Azure Information Protection i usługi Azure Rights Management](#azure-information-protection-service-and-azure-rights-management-service)

    - Dotyczy przypadku, gdy używany jest tryb obejmujący tylko klasyfikację lub klasyfikację z ochroną Rights Management: masz subskrypcję, która obejmuje usługę Azure Information Protection (na przykład Enterprise Mobility + Security).
    - Dotyczy przypadku, gdy używany jest tryb obejmujący tylko ochronę za pomocą usługi Azure Rights Management: masz subskrypcję, która obejmuje usługę Azure Rights Management (na przykład usługi Office 365 E3 i Office 365 E5).

- [Usługi Active Directory Rights Management](#active-directory-rights-management-services)

    - Dotyczy przypadku, gdy używany jest tryb obejmujący tylko ochronę za pomocą lokalnej wersji usługi Azure Rights Management; Usługi Active Directory Rights Management (AD RMS).


## <a name="azure-information-protection-and-azure-rights-management-service"></a>Usługa Azure Information Protection i Azure Rights Management

Przeczytaj tę sekcję przed rozpoczęciem używania poleceń programu PowerShell, jeśli Twoja organizacja korzysta z usługi Azure Information Protection dla klasyfikacji i ochrony lub po prostu usługi Azure Rights Management do ochrony danych.


### <a name="prerequisites"></a>Wymagania wstępne

Oprócz wymagań wstępnych dotyczących instalacji modułu AzureInformationProtection istnieją dodatkowe wymagania wstępne dotyczące etykietowania usługi Azure Information Protection i usługi ochrony danych usługi Azure Rights Management:

1. Usługa Azure Rights Management musi być aktywowana.

2. Aby usunąć ochronę plików dla innych osób używających Twojego konta: 
    
    - W organizacji musi być włączona funkcja administratora, a Twoje konto musi być skonfigurowane jako konto administratora usługi Azure Rights Management.

3. Aby bezpośrednio włączać lub wyłączać ochronę plików bez interakcji z użytkownikiem: 
    
    - Utwórz konto jednostki usługi, uruchom polecenie Set-RMSServerAuthentication i ewentualnie ustaw tę jednostkę jako administratora usługi Azure Rights Management.

4. W przypadku regionów poza Ameryką Północną: 
    
    - Edytuj rejestr dla potrzeb odnajdowania usługi.

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>Wymaganie wstępne 1: usługa Azure Rights Management musi być aktywowana

To wymaganie wstępne dotyczy zarówno sytuacji, gdy stosowana jest ochrona danych za pomocą etykiet, jak i bezpośredniego połączenia z usługą Azure Rights Management w celu zastosowania ochrony danych.

Jeśli dzierżawa usługi Azure Information Protection nie został aktywowany, zobacz instrukcje dotyczące aktywacji [Aktywacja usługi Azure Rights Management]-service.md).

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>Wymaganie wstępne 2: usuwanie ochrony plików dla innych osób używających Twojego konta

Typowe scenariusze dotyczące usuwania ochrony plików dla innych osób obejmują odnajdywanie lub odzyskiwanie danych. Jeśli jest stosowana ochrona przy użyciu etykiet, można ją usunąć, ustawiając nową etykietę, która nie stosuje ochrony, lub usuwając etykietę. Wygodniejszym rozwiązaniem jest jednak połączenie się bezpośrednio z usługą Azure Rights Management w celu usunięcia ochrony.

Musisz mieć prawa użytkowania usługi Rights Management do usuwania ochrony plików lub być administratorem. W przypadku odnajdywania lub odzyskiwania danych zwykle jest używana funkcja administratora. Aby włączyć tę funkcję i skonfigurować swoje konto administratora, zobacz [Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych] Konfiguruj super — users.md).

#### <a name="prerequisite-3-to-protect-or-unprotect-files-without-user-interaction"></a>Wymaganie wstępne 3: włączanie lub wyłączanie ochrony plików bez interakcji z użytkownikiem

Możesz połączyć się bezpośrednio do usługi Azure Rights Management — interakcyjnie, aby lub wyłączanie ochrony plików.

Należy użyć konta jednostki usługi do połączenia z usługą Azure Rights Management nieinteraktywnego, co można zrobić za pomocą `Set-RMSServerAuthentication` polecenia cmdlet. Należy to zrobić dla każdej sesji środowiska Windows PowerShell korzystającej z poleceń cmdlet, które bezpośrednio łączą się z usługą Azure Rights Management. Przed uruchomieniem tego polecenia cmdlet konieczne jest posiadanie te trzy identyfikatory:

- Identyfikator BposTenantId

- Identyfikator AppPrincipalId

- Klucz symetryczny

Automatycznie pobrać wartości identyfikatorów i uruchom polecenie cmdlet Set-RMSServerAuthentication, można użyć następujących poleceń programu PowerShell i instrukcje komentarzem. Alternatywnie możesz ręcznie pobrać i określić wartości.

Aby automatycznie uzyskać wartości i uruchomić polecenia Set-RMSServerAuthentication:

````
# Make sure that you have the AADRM and MSOnline modules installed

$ServicePrincipalName="<new service principal name>"
Connect-AadrmService
$bposTenantID=(Get-AadrmConfiguration).BPOSId
Disconnect-AadrmService
Connect-MsolService
New-MsolServicePrincipal -DisplayName $ServicePrincipalName

# Copy the value of the generated symmetric key

$symmetricKey="<value from the display of the New-MsolServicePrincipal command>"
$appPrincipalID=(Get-MsolServicePrincipal | Where { $_.DisplayName -eq $ServicePrincipalName }).AppPrincipalId
Set-RMSServerAuthentication -Key $symmetricKey -AppPrincipalId $appPrincipalID -BposTenantId $bposTenantID

````

W kolejnych sekcjach wyjaśniono, jak ręcznie Pobierz i określ te wartości. więcej informacji o każdej z nich.

##### <a name="to-get-the-bpostenantid"></a>Uzyskiwanie identyfikatora BposTenantId

W module Windows PowerShell usługi Azure RMS uruchom polecenie cmdlet Get-AadrmConfiguration:

1. Jeśli ten moduł nie jest już zainstalowany na komputerze, zobacz powershell.md instalacji [Instalowanie modułu AADRM programu PowerShell]).

2. Uruchom sesję środowiska Windows PowerShell przy użyciu opcji **Uruchom jako administrator**.

3. Użyj polecenia cmdlet `Connect-AadrmService`, aby połączyć się z usługą Azure Rights Management:
    
        Connect-AadrmService
    
    Po wyświetleniu monitu wprowadź poświadczenia administratora dzierżawy usługi Azure Information Protection. Zazwyczaj można używać konta, które jest administratorem globalnym usługi Azure Active Directory lub Office 365.
    
4. Uruchom polecenie `Get-AadrmConfiguration` i utwórz kopię wartości BPOSId.
    
    Przykład danych wyjściowych z Get-AadrmConfiguration:
    
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
    
    Po wyświetleniu monitu wprowadź poświadczenia administratora dzierżawy usługi Azure AD (zazwyczaj należy używać konta, które jest administratorem globalnym usługi Azure Active Directory lub Office 365).

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

    Należy utworzyć kopię tego klucza symetrycznego. Ten klucz nie może pobrać później, więc jeśli nie znasz jego gdy trzeba następnie uwierzytelniania usługi Azure Rights Management, będzie musiał utworzyć nową jednostkę usługi.

Korzystając z tych instrukcji i opierając się na naszych przykładach, uzyskaliśmy trzy identyfikatory wymagane do uruchomienia polecenia Set-RMSServerAuthentication:

- Identyfikator dzierżawcy: **23976bc6-dcd4-4173-9d96-dad1f48efd42**

- Klucz symetryczny: **zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=**

- Identyfikator AppPrincipalId: **b5e3f76a-b5c2-4c96-a594-a0807f65bba4**

Nasze przykładowe polecenie będzie więc wyglądać następująco:

    Set-RMSServerAuthentication -Key zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=-AppPrincipalId b5e3f76a-b5c2-4c96-a594-a0807f65bba4-BposTenantId 23976bc6-dcd4-4173-9d96-dad1f48efd42

Jak pokazano w poprzednim poleceniu, możesz podać wartości za pomocą jednego polecenia, co może zrobić w skrypcie do uruchamiania w trybie nieinteraktywnym. Jednak do celów testowych możesz po prostu wpisz Set-RMSServerAuthentication i podaj wartości jeden po drugim po wyświetleniu monitu. Po zakończeniu wykonywania polecenia klienta działa się teraz w "trybie serwera", który jest odpowiedni do użytku-interactive, takich jak skrypty i infrastruktury klasyfikacji plików w systemie Windows Server.

Rozważ przekształcenie to konto jednostki usługi Administrator: w celu zapewnienia, że konta głównego usługi mogą zawsze wyłączania ochrony plików dla innych użytkowników, można skonfigurować jako administrator. W taki sam sposób jak skonfigurować konta użytkownika standardowego do administratora, używasz tego samego polecenia cmdlet usługi Azure RMS [Add-AadrmSuperUser](/powershell/aadrm/vlatest/Add-AadrmSuperUser.md), ale Określa **ServicePrincipalId** parametr o usługi Wartość identyfikatora AppPrincipalId.

Aby uzyskać więcej informacji na temat administratorów Zobacz [Konfigurowanie superużytkowników usługi Azure Rights Management i odnajdowania usług lub odzyskiwania danych] Konfiguruj super — users.md).

> [!NOTE]
> Aby użyć swojego konta użytkownika do uwierzytelnienia w usłudze Azure Rights Management, nie ma potrzeby uruchamiania polecenia Set-RMSServerAuthentication przed włączeniem lub wyłączeniem ochrony plików albo pobraniem szablonów.

#### <a name="prerequisite-4-for-regions-outside-north-america"></a>Wymaganie wstępne 4: dotyczy regionów poza Ameryką Północną

Korzystając z konta głównego usługi do ochrony plików i pobierania szablonów poza regionem Ameryki Północnej platformy Azure, należy edytować rejestr: 

1. Ponownie uruchom polecenie cmdlet Get-AadrmConfiguration i zanotuj wartości parametrów **CertificationExtranetDistributionPointUrl** i **LicensingExtranetDistributionPointUrl**.

2. Na każdym komputerze, na którym będą uruchamiane polecenia cmdlet AzureInformationProtection Otwórz Edytor rejestru.

3. Przejdź do następującej ścieżki: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation`. 
    
    Jeśli nie widzisz **MSIPC** klucza lub **ServiceLocation** klucza, należy je utworzyć.

4. Dla klucza **ServiceLocation** utwórz dwa klucze (o ile nie istnieją) o nazwach **EnterpriseCertification** i **EnterprisePublishing**. 
    
    Aby uzyskać wartość ciągu, która jest tworzona automatycznie dla tych kluczy nie należy zmieniać nazwy "(wartość domyślna)", ale Edytuj ciąg, aby ustawić jej dane:

    - Dla klucza **EnterpriseCertification** wklej wartość parametru CertificationExtranetDistributionPointUrl.
    
    - Dla klucza **EnterprisePublishing** wklej wartość parametru LicensingExtranetDistributionPointUrl.
    
    Na przykład swój wpis rejestru pod kątem EnterpriseCertification powinien wyglądać podobnie do poniższej:
    
    ![Edytowanie rejestru dla modułu Azure PowerShell ochrony informacji dla regionów poza Ameryką Północną](../media/registry-example-rmsprotection.png)

5. Zamknij Edytor rejestru. Nie ma potrzeby ponownego uruchamiania komputera. Jeśli jednak używasz konta jednostki usługi, a nie swojego konta użytkownika, należy po wprowadzeniu zmian w rejestrze uruchomić polecenie Set-RMSServerAuthentication.

### <a name="example-scenarios-for-using-the-cmdlets-for-azure-information-protection-and-the-azure-rights-management-service"></a>Przykładowe scenariusze użycia poleceń cmdlet usługi Azure Information Protection i Azure Rights Management

Korzystanie z etykiet do klasyfikowania i ochrony plików jest bardziej efektywne, ponieważ potrzebne są tylko dwa polecenia cmdlet, które mogą być uruchamiane osobno lub razem: [Get-AIPFileStatus](/powershell/azureinformationprotection/get-aipfilestatus) i [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel). Skorzystaj z pomocy dotyczącej obu tych poleceń cmdlet, aby uzyskać dodatkowe informacje i przykłady.

Aby włączać i wyłączać ochronę plików przy wykorzystaniu bezpośredniego połączenia z usługą Azure Rights Management, należy zazwyczaj uruchamiać serię poleceń cmdlet, zgodnie z poniższym opisem.

Po pierwsze Jeśli zachodzi potrzeba uwierzytelniania usługi Azure Rights Management, za pomocą konta głównego usługi, zamiast używać własnego konta w sesji programu PowerShell, wpisz:

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

Aby chronić wszystkie pliki w folderze, użyj parametru **-Folder** z literą dysku i ścieżką lub ścieżką UNC. Przykład:

    Protect-RMSFile -Folder \Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

Raport będzie wyglądał podobnie do poniższego:

    InputFile                          EncryptedFile
    ---------                          -------------
    \Server1\Documents\Test1.docx     \Server1\Documents\Test1.docx
    \Server1\Documents\Test2.docx     \Server1\Documents\Test2.docx
    \Server1\Documents\Test3.docx     \Server1\Documents\Test3.docx
    \Server1\Documents\Test4.docx     \Server1\Documents\Test4.docx

Jeśli rozszerzenie nazwy pliku nie zmienia się po zastosowaniu ochrony, zawsze można użyć polecenia cmdlet `Get-RMSFileStatus` później, aby sprawdzić, czy plik jest chroniony. Przykład:

    Get-RMSFileStatus -File \Server1\Documents\Test1.docx

Raport będzie wyglądał podobnie do poniższego:

    FileName                              Status
    --------                              ------
    \Server1\Documents\Test1.docx         Protected

Usunięcie ochrony pliku, musisz mieć uprawnienia właściciela lub wyodrębniania, od kiedy plik jest chroniony. Lub poleceń cmdlet należy uruchomić jako administrator. Następnie należy użyć polecenia cmdlet Unprotect. Przykład:

    Unprotect-RMSFile C:\test.docx -InPlace

Raport będzie wyglądał podobnie do poniższego:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx

Należy pamiętać, że jeśli do szablonów usługi Rights Management zostaną wprowadzone zmiany, należy pobrać je ponownie przy użyciu polecenia `Get-RMSTemplate -force`. 

## <a name="active-directory-rights-management-services"></a>Usługi Active Directory Rights Management

Przeczytaj tę sekcję przed rozpoczęciem korzystania z poleceń środowiska PowerShell w celu włączania lub wyłączania ochrony plików, jeśli Twoja organizacja używa tylko usług Active Directory Rights Management.


### <a name="prerequisites"></a>Wymagania wstępne

Oprócz wymagań wstępnych dotyczących instalacji modułu AzureInformationProtection konto używane do ochrony lub wyłączanie plików musi mieć uprawnienia odczytu i wykonywania na dostęp do pliku ServerCertification.asmx:

1. Zaloguj się do serwera usług AD RMS.

2. Kliknij pozycję **Start**, a następnie **Komputer**.

3. W Eksploratorze plików przejdź do lokalizacji %systemdrive%\Initpub\wwwroot\_wmsc\Certification.

4. Kliknij prawym przyciskiem myszy plik **ServerCertification.asmx**, następnie kliknij polecenie **Właściwości**.

5. W oknie dialogowym **Właściwości pliku ServerCertification.asmx** kliknij kartę **Zabezpieczenia**. 

6. Kliknij przycisk **Kontynuuj** lub **Edytuj**. 

7. W oknie dialogowym **Uprawnienia dla pliku ServerCertification.asmx** kliknij przycisk **Dodaj**. 

8. Dodaj nazwę swojego konta. Jeśli inni administratorzy usług AD RMS lub konta usług będzie również używają tych poleceń cmdlet do włączania i wyłączania ochrony plików, Dodaj również do tych kont. 
    
    Aby lub wyłączanie ochrony plików nieinteraktywnego, należy dodać odpowiednie konto lub konta. Na przykład dodać konto komputera komputera systemu Windows Server, który jest skonfigurowany dla funkcji infrastruktury klasyfikacji plików i użyje skrypt programu PowerShell w celu ochrony plików.

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

Aby chronić wszystkie pliki w folderze, użyj parametru -Folder z literą dysku i ścieżką lub ścieżką UNC. Przykład:

    Protect-RMSFile -Folder \\Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

Raport będzie wyglądał podobnie do poniższego:

    InputFile                          EncryptedFile
    ---------                          -------------
    \\Server1\Documents\Test1.docx     \\Server1\Documents\Test1.docx   
    \\Server1\Documents\Test2.docx     \\Server1\Documents\Test2.docx   
    \\Server1\Documents\Test3.docx     \\Server1\Documents\Test3.docx   
    \\Server1\Documents\Test4.docx     \\Server1\Documents\Test4.docx   

Jeśli rozszerzenie nazwy pliku nie zmienia się po zastosowaniu ochrony, należy zawsze można użyć polecenia cmdlet Get-RMSFileStatus później do sprawdzenia, czy plik jest chroniony. Przykład: 

    Get-RMSFileStatus -File \\Server1\Documents\Test1.docx

Raport będzie wyglądał podobnie do poniższego:

    FileName                              Status
    --------                              ------
    \\Server1\Documents\Test1.docx        Protected

Aby wyłączyć ochronę pliku, musi mieć właściciela lub Wyodrębnij praw użytkowania, gdy był chroniony plików lub być administratorem usług AD RMS. Następnie należy użyć polecenia cmdlet Unprotect. Przykład:

    Unprotect-RMSFile C:\test.docx -InPlace

Raport będzie wyglądał podobnie do poniższego:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx

## <a name="how-to-label-files-non-interactively-for-azure-information-protection"></a>Jak nieinteraktywnie etykietować pliki na potrzeby usługi Azure Information Protection

Można uruchomić polecenia cmdlet etykietowania nieinterakcyjny za pomocą **Set-AIPAuthentication** polecenia cmdlet. Nieinterakcyjne operacja jest także wymagane dla skanera usługi Azure Information Protection.

Domyślnie polecenia cmdlet służące do etykietowania są uruchamiane we własnym kontekście użytkownika w interaktywnej sesji programu PowerShell. Aby uruchamiać polecenia w trybie nienadzorowanym, utwórz nowe konto użytkownika usługi Azure AD. Następnie w kontekście tego użytkownika uruchom polecenie cmdlet Set-AIPAuthentication, aby skonfigurować i przechowywać poświadczenia przy użyciu tokenu dostępu z usługi Azure AD. To konto użytkownika jest następnie uwierzytelniane i uruchamiane dla usługi Azure Rights Management. Konto pobiera zasady usługi Azure Information Protection i wszystkie szablony usług Rights Management używane w etykietach.

> [!NOTE]
> Jeśli używasz [zasady o określonym zakresie] skonfigurować — zasady — scope.md), należy pamiętać, że może być konieczne do dodania tego konta do zasad o określonym zakresie.

Przy pierwszym uruchomieniu tego polecenia cmdlet zostanie wyświetlony monit o zalogowanie do usługi Azure Information Protection. Określ nazwę konta użytkownika i hasła, który został utworzony dla instalacji nienadzorowanej użytkownika. Następnie na tym koncie będzie można uruchamiać polecenia cmdlet nieinteraktywnego etykietowania do momentu wygaśnięcia ważności tokenu uwierzytelniania. 

Dla konta użytkownika móc zalogować się interaktywnie to po raz pierwszy, konto musi mieć **logować się lokalnie** prawo. To prawo jest standardem dla kont użytkowników, ale zasady firmy może uniemożliwiać tej konfiguracji dla kont usług. Jeśli tak jest rzeczywiście, możesz uruchomić polecenia Set-AIPAuthentication z *tokenu* parametrów, tak aby uwierzytelnianie zakończy się bez monitu zaloguj się. Możesz uruchomić to polecenie jako zaplanowane zadanie i Przyznaj kontu w prawej dolnej części **logowanie w trybie wsadowym**. Aby uzyskać więcej informacji zobacz następujące sekcje. 

Po wygaśnięciu ważności tokenu Uruchom polecenie cmdlet ponownie, aby uzyskać nowy token.

Po uruchomieniu tego polecenia cmdlet bez parametrów konto uzyskuje token dostępu, który jest ważny przez 90 dni lub do momentu wygaśnięcia ważności hasła.  

Aby kontrolować moment wygaśnięcia ważności tokenu dostępu, uruchom to polecenie cmdlet z parametrami. Umożliwi to skonfigurowanie tokenu dostępu na jeden rok, dwa lata lub bez określonej daty wygaśnięcia. Ta konfiguracja wymaga zarejestrowania dwóch aplikacji w usłudze Azure Active Directory: **aplikacji internetowej/interfejsu API** i **aplikacji natywnej**. Parametry tego polecenia cmdlet używają wartości z tych aplikacji.

Po uruchomieniu tego polecenia cmdlet możesz uruchomić polecenia cmdlet etykietowania w kontekście utworzonego konta użytkownika.

### <a name="to-create-and-configure-the-azure-ad-applications-for-set-aipauthentication"></a>Tworzenie i konfigurowanie aplikacji usługi Azure AD na potrzeby polecenia Set-AIPAuthentication

1. W nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com/).

2. W przypadku dzierżawcy usługi Azure AD, który jest używany z usługą Azure Information Protection, przejdź do pozycji **Azure Active Directory** > **Rejestracje aplikacji**. 

3. Wybierz pozycję **Rejestrowanie nowej aplikacji**, aby utworzyć aplikację internetową/interfejsu API. Na etykiecie **Utwórz** określ następujące wartości, a następnie kliknij pozycję **Utwórz**:
    
    - Nazwa: **AIPOnBehalfOf**
    
    Jeśli chcesz, podaj inną nazwę. Nazwa musi być unikatowa dla dzierżawy.
    
    - Typ aplikacji: **Aplikacja internetowa/interfejs API**
    
    - Adres URL logowania: **http://localhost**

4. Wybierz właśnie utworzoną aplikację, na przykład **AIPOnBehalfOf**. Następnie w bloku **Ustawienia** wybierz pozycję **Właściwości**. Z bloku **Właściwości** skopiuj wartość **Identyfikator aplikacji**, a następnie zamknij ten blok. 
    
    Ta wartość jest używana dla parametru `WebAppId` podczas uruchamiania polecenia cmdlet Set-AIPAuthentication. Wklej i zapisz go do późniejszego wykorzystania.

5. Po powrocie **ustawienia** bloku wybierz **wymagane uprawnienia**. Na **wymagane uprawnienia** bloku wybierz **Udziel uprawnień**, kliknij przycisk **tak** celu potwierdzenia, a następnie zamknij ten blok.

6. Po powrocie **ustawienia** blok ponownie, wybierz opcję **klucze**. Dodaj nowy klucz, podając opis i wybierając czas trwania (1 rok, 2 lata lub bez daty wygaśnięcia). Następnie wybierz pozycję **Zapisz** i skopiuj ciąg wyświetlony w polu **Wartość**. Ważne jest, aby zapisać ten ciąg, ponieważ nie jest on wyświetlany ponownie i nie można go pobrać. Podobnie jak w przypadku każdego używanego klucza, przechowuj zapisaną wartość w bezpiecznym miejscu i ogranicz dostęp do niej.
    
    Ta wartość jest używana dla parametru `WebAppKey` podczas uruchamiania polecenia cmdlet Set-AIPAuthentication.

7. W bloku **Rejestracje aplikacji** wybierz ponownie pozycję **Rejestrowanie nowej aplikacji**, aby utworzyć aplikację natywną. Na etykiecie **Utwórz** określ następujące wartości, a następnie kliknij pozycję **Utwórz**:
    
    - Nazwa: **AIPClient**
    
    Jeśli chcesz, podaj inną nazwę. Nazwa musi być unikatowa dla dzierżawy.
    
    - Typ aplikacji: **Natywna**
    
    - Adres URL logowania: **http://localhost**

8. Wybierz właśnie utworzoną aplikację, na przykład **AIPClient**. Następnie w bloku **Ustawienia** wybierz pozycję **Właściwości**. Z bloku **Właściwości** skopiuj wartość **Identyfikator aplikacji**, a następnie zamknij ten blok.
    
    Ta wartość jest używana dla parametru `NativeAppId` podczas uruchamiania polecenia cmdlet Set-AIPAuthentication. Wklej i zapisz go do późniejszego wykorzystania.

9. W bloku **Ustawienia** wybierz pozycję **Wymagane uprawnienia**. 

10. W bloku **Wymagane uprawnienia** kliknij pozycję **Dodaj**, a następnie kliknij pozycję **Wybierz interfejs API**. W polu wyszukiwania wpisz **AIPOnBehalfOf**. Wybierz tę wartość w polu listy, a następnie kliknij pozycję **Wybierz**.

11. W bloku **Włączanie dostępu** wybierz pozycję **AIPOnBehalfOf**, kliknij pozycję **Wybierz**, a następnie kliknij pozycję **Gotowe**.

12. Po powrocie **wymagane uprawnienia** bloku wybierz **Udziel uprawnień**, kliknij przycisk **tak** celu potwierdzenia, a następnie zamknij ten blok.
    

Konfiguracja dwóch aplikacji została teraz zakończona i wartości, które należy uruchomić [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) z parametrami *WebAppId*, *WebAppKey* i *NativeAppId*. Przykład:

`Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"`

Uruchom następujące polecenie w kontekście konta, które będą etykietowanie i ochrona nieinterakcyjny dokumentów. Na przykład konto użytkownika dla skryptów programu PowerShell lub konta usługi, aby uruchomić skanera usługi Azure Information Protection.  

Po uruchomieniu tego polecenia po raz pierwszy monit do logowania, który tworzy i OS x bezpiecznie przechowa token dostępu dla swojego konta w % localappdata%\Microsoft\MSIP. Po tej początkowej logowania umożliwia etykietowanie i ochronę plików nieinteraktywnego na komputerze. Jeśli jednak używasz konta usługi, etykietowanie i ochronę plików, a to konto usługi nie można zalogować się interaktywnie, użyć instrukcji w poniższej sekcji, aby konto usługi można uwierzytelnić przy użyciu tokenu.

### <a name="specify-and-use-the-token-parameter-for-set-aipauthentication"></a>Określ i użyj parametru tokenu dla polecenia Set-AIPAuthentication

Użyj następujące dodatkowe kroki i instrukcje, aby uniknąć początkowej interakcyjnego logowania dla konta które etykiety i chroni pliki. Zazwyczaj te dodatkowe kroki są wymagane tylko wtedy, gdy to konto nie można udzielić **logować się lokalnie** kliknij prawym przyciskiem myszy, ale jest udzielany **logowanie w trybie wsadowym** prawo. Na przykład może to być w przypadku konta usługi, który działa skaner usługi Azure Information Protection.

Ogólne kroki:

1. Utwórz skrypt programu PowerShell na komputerze lokalnym.

2. Uruchom polecenia Set-AIPAuthentication do uzyskania tokenu dostępu i skopiować go do Schowka.

3. Zmodyfikuj skrypt programu PowerShell, aby uwzględnić tokenu.

4. Utwórz zadanie, które uruchamia skrypt programu PowerShell w kontekście konta usługi, która będzie etykietowanie i ochronę plików.

5. Upewnij się, że token są zapisywane dla konta usługi, a następnie usuń skrypt programu PowerShell.

#### <a name="step-1-create-a-powershell-script-on-your-local-computer"></a>Krok 1: Tworzenie skryptu programu PowerShell na komputerze lokalnym

1. Na komputerze należy utworzyć nowy skrypt programu PowerShell o nazwie Aipauthentication.ps1.

2. Skopiuj i wklej poniższe polecenie do skryptu:
    
         Set-AIPAuthentication -WebAppId <ID of the "Web app / API" application> -WebAppKey <key value generated in the "Web app / API" application> -NativeAppId <ID of the "Native" application > -Token <token value>

3. Zgodnie z instrukcjami w poprzedniej sekcji, zmieniać tego polecenia, określając wartości dla **WebAppId**, **WebAppkey**, i **NativeAppId** parametrów. W tej chwili nie ma wartości dla **tokenu** parametr, który określisz później. 
    
    Na przykład: `Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f -Token <token value>`
    
#### <a name="step-2-run-set-aipauthentication-to-get-an-access-token-and-copy-it-to-the-clipboard"></a>Krok 2: Uruchomienia polecenia Set-AIPAuthentication do uzyskania tokenu dostępu i skopiować go do Schowka

1. Otwórz sesję środowiska Windows PowerShell.

2. Przy użyciu tej samej wartości jak określonego w skrypcie, uruchom następujące polecenie:
    
        (Set-AIPAuthentication -WebAppId <ID of the "Web app / API" application>  -WebAppKey <key value generated in the "Web app / API" application> -NativeAppId <ID of the "Native" application >).token | clip
    
    Na przykład: `(Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f").token | clip`

#### <a name="step-3-modify-the-powershell-script-to-supply-the-token"></a>Krok 3. modyfikowanie skrypt programu PowerShell, aby dostarczyć token

1. W skrypcie programu PowerShell Określ wartość tokenu wklejając ciąg ze Schowka, a następnie zapisz plik.

2. Podpisz skrypt. Jeśli zrezygnujesz z podpisania skryptu (bezpieczniejsza opcja), należy skonfigurować programu Windows PowerShell na komputerze, który będzie uruchamiać polecenia etykietowania. Na przykład Uruchom sesję programu Windows PowerShell, korzystając z **Uruchom jako Administrator** opcję i wpisz: `Set-ExecutionPolicy RemoteSigned`. Jednak taka konfiguracja pozwala na uruchomienie, gdy są one przechowywane na tym komputerze (mniej bezpieczna opcja) wszystkich niepodpisanych skryptów.
    
    Aby uzyskać więcej informacji na temat podpisywania skryptów programu Windows PowerShell, zobacz artykuł [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing) w bibliotece dokumentacji programu PowerShell.

3. Skopiuj ten skrypt programu PowerShell na komputerze, na którym będą etykiety i chronić pliki i usuniesz oryginał na tym komputerze. Na przykład możesz skopiować skrypt programu PowerShell do C:\Scripts\Aipauthentication.ps1 na komputerze z systemem Windows Server.

#### <a name="step-4-create-a-task-that-runs-the-powershell-script"></a>Krok 4: Tworzenie zadania, które uruchamia skrypt programu PowerShell

1. Upewnij się, że konto usługi, która będzie etykietowanie i ochronę plików ma **logowanie w trybie wsadowym** prawo.

2. Na komputerze, na którym będzie etykietowanie i ochronę plików Otwórz Harmonogram zadań, a następnie utwórz nowe zadanie. To zadanie do uruchamiania jako konto usługi, które będą etykiety i ochronę plików, a następnie skonfiguruj następujące wartości dla konfiguracji **akcje**:
    
    - **Akcja**: `Start a program`
    - **Program/skrypt**: `Powershell.exe`
    - **Dodaj argumenty (opcjonalne)**: `-NoProfile -WindowStyle Hidden -command "&{C:\Scripts\Aipauthentication.ps1}"` 
    
    Argument w wierszu należy określić własne ścieżkę i nazwę pliku, jeśli są one różne od przykładu.

3. Ręcznie uruchom to zadanie.

#### <a name="step-4-confirm-that-the-token-is-saved-and-delete-the-powershell-script"></a>Krok 4: Upewnij się, że token został zapisany i Usuń skrypt programu PowerShell

1. Upewnij się, że token jest teraz przechowywany w folderze %localappdata%\Microsoft\MSIP profilu konta usługi. Ta wartość jest chroniony przez konto usługi.

2. Usuń skrypt programu PowerShell, który zawiera wartość tokenu (na przykład Aipauthentication.ps1).
    
    Opcjonalnie można usunąć zadania. Jeśli token wygaśnie, należy powtórzyć ten proces, w takiej sytuacji może być bardziej wygodne pozostawić zadań skonfigurowany tak, aby była gotowa do ponownego uruchomienia po skopiowaniu przez nowe środowisko programu PowerShell script nową wartość tokenu.

## <a name="next-steps"></a>Kolejne kroki
Aby uzyskać pomoc dotyczącą polecenia cmdlet w trakcie sesji programu PowerShell, wpisz ciąg `Get-Help <cmdlet name> cmdlet` i użyj parametru -online w celu zapoznania się z najbardziej aktualnymi informacjami. Przykład: 

    Get-Help Get-RMSTemplate -online

Zobacz następujące artykuły, aby uzyskać dodatkowe informacje potrzebne do obsługi klienta usługi Azure Information Protection:

- [Dostosowania](client-admin-guide-customizations.md)

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)


