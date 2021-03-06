---
title: Konfiguracja dla klientów usługi Office 365 i usług online do korzystania z usługi Azure RMS z usługi AIP
description: Informacje i instrukcje dla administratorów dotyczące konfigurowania usługi Office 365 do pracy z usługą Azure Rights Management w ramach usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 0a6ce612-1b6b-4e21-b7fd-bcf79e492c3b
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: be8378705611f10064026dd0043e6404ad693092
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393499"
---
# <a name="office365-configuration-for-clients-and-online-services-to-use-the-azure-rights-management-service"></a>Office 365: Konfiguracja dla klientów i usług online do korzystania z usługi Azure Rights Management

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Ponieważ usługi Office 365 natywnie obsługuje usługę Azure Rights Management z usługi Azure Information Protection, żadna konfiguracja komputera klienckiego jest wymagany do obsługi funkcji information rights management (IRM) dla aplikacji, takich jak Word, Excel, PowerPoint, Outlook i Outlook w sieci web. Wszyscy użytkownicy muszą wykonać, zaloguj się w swoich aplikacjach pakietu Office przy użyciu swoich poświadczeń usługi Rights Management. Następnie mogą chronić pliki i wiadomości e-mail i używać plików i wiadomości e-mail, które są chronione przez innych użytkowników.

Zalecamy jednak uzupełnienie tych aplikacji o klienta usługi Azure Information Protection, dzięki czemu użytkownicy będą mogli skorzystać z zalet dodatku pakietu Office i możliwości obsługi dodatkowych typów plików. Aby uzyskać więcej informacji, zobacz [klienta Azure Information Protection: Instalacja i konfiguracja dla klientów](configure-client.md).

## <a name="exchangeonline-irm-configuration"></a>Exchange Online: Konfiguracja usługi IRM
Aby uzyskać informacje na temat współdziałania usługi Exchange Online IRM z usługą Azure Rights Management, zobacz [usługi Exchange Online i Exchange Server](office-apps-services-support.md#exchange-online-and-exchange-server) sekcja [Office jak aplikacje i usługi obsługują usługę Azure Rights Zarządzanie](office-apps-services-support.md).

Exchange Online mogą już mieć możliwość użycia usługi Azure Rights Management. Aby sprawdzić, uruchom następujące polecenia:

1. Jeśli używasz programu Windows PowerShell dla usługi Exchange Online na komputerze po raz pierwszy, musisz skonfigurować program Windows PowerShell do uruchamiania podpisanych skryptów. Uruchom sesję programu Windows PowerShell przy użyciu opcji **Uruchom jako administrator**, a następnie wpisz:
    
        Set-ExecutionPolicy RemoteSigned
    
    Naciśnij klawisz **Y** o potwierdzenie.

2. W sesji programu Windows PowerShell zaloguj się do usługi Exchange Online przy użyciu konta z włączoną opcją zdalnego dostępu do programu PowerShell. Domyślnie wszystkie konta tworzone w usłudze Exchange Online mają włączoną opcję zdalnego dostępu do programu PowerShell, ale można ją wyłączyć (i włączyć) przy użyciu polecenia [Set-User &lt;TożsamośćUżytkownika&gt; -RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx).
    
    Aby się zarejestrować, najpierw wpisz polecenie:
    
        $Cred = Get-Credential
   
    Następnie w **żądanie poświadczeń programu Windows PowerShell** okna dialogowego podaj nazwę użytkownika usługi Office 365 i hasła.

3. Połącz się z usługą Exchange Online, przez ustawienie zmiennej:
    
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
    
    Następnie uruchom następujące polecenie:
    
        Import-PSSession $Session

4. Uruchom [Get-IRMConfiguration](https://technet.microsoft.com/library/dd776120(v=exchg.160).aspx) polecenie, aby wyświetlić konfigurację usługi Exchange Online dla usługi ochrony:
    
        Get-IRMConfiguration
    
    W danych wyjściowych, Znajdź **AzureRMSLicensingEnabled** wartość:
    
    - Jeśli ustawiono AzureRMSLicensingEnabled **True**, Exchange Online jest już włączona dla usługi Azure Rights Management. 
    
    - Jeśli ustawiono AzureRMSLicensingEnabled **False**, uruchom polecenie poniżej, aby umożliwić usłudze Exchange Online dla usługi Azure Rights Management: `Set-IRMConfiguration -AzureRMSLicensingEnabled $true`

5. Aby przetestować ten Exchange Online skonfigurowano pomyślnie, uruchom następujące polecenie:
    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    Przykład: <strong>Test-IRMConfiguration -Sender  adams@contoso.com</strong>
    
    To polecenie umożliwia uruchomienie serii testów obejmujących sprawdzanie połączenia z usługą, pobieranie konfiguracji oraz pobieranie identyfikatorów URI, licencji i dowolnych szablonów. W sesji programu Windows PowerShell zobaczysz wyniki każdego z nich, a na koniec, jeśli testy zakończą się pomyślnie kontrole: **OGÓLNY WYNIK: PASS**

Włączenie usługi Exchange Online do korzystania z usługi Azure Rights Management, można skonfigurować funkcje, które automatycznie stosować ochronę informacji takich jak [reguły przepływu poczty](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8), [zasad (DLP) zapobiegania utracie danych ](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx), i [chroniona poczta głosowa](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (Unified Messaging).

## <a name="sharepointonline-and-onedrive-for-business-irm-configuration"></a>SharePoint Online i OneDrive dla firm: Konfiguracja usługi IRM

Aby uzyskać informacje na temat współdziałania usługi SharePoint Online IRM z usługą Azure Rights Management, zobacz [SharePoint Online i SharePoint Server](office-apps-services-support.md#sharepoint-online-and-sharepoint-server) w sekcji **Poznawanie i eksplorowanie**.

Aby skonfigurować usługi SharePoint Online i OneDrive dla firm do obsługi usługi Azure Rights Management, należy najpierw włączyć information rights management (IRM) dla usługi SharePoint Online, za pomocą Centrum administracyjnego programu SharePoint. Następnie właściciele witryn mogą używać usługi IRM do ochrony bibliotek dokumentów i list programu SharePoint, a użytkownicy — do ochrony biblioteki usługi OneDrive dla Firm, dzięki czemu dokumenty zapisywane w tej usłudze i udostępniane innym osobom są automatycznie chronione przez usługę Azure Rights Management.

> [!NOTE]
> Chronioną przez IRM biblioteki programu SharePoint i OneDrive dla firm wymaga najnowszej wersji nowego klienta synchronizacji OneDrive (OneDrive.exe) i wersję [klient usługi RMS z Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=38396). Zainstaluj tę wersję klienta RMS, nawet jeśli masz zainstalowanego klienta usługi Azure Information Protection. Aby uzyskać więcej informacji na temat tego scenariusza wdrażania, zobacz [wdrożyć nowego klienta synchronizacji OneDrive w środowisku przedsiębiorstwa](https://support.office.com/article/Deploy-the-new-OneDrive-sync-client-in-an-enterprise-environment-3f3a511c-30c6-404a-98bf-76f95c519668).

Aby włączyć usługę zarządzania prawami do informacji (IRM) dla usługi SharePoint Online, zobacz następujące instrukcje dostępne w witrynie sieci Web pakietu Office:

- [Konfigurowanie usługi Zarządzanie prawami do informacji w centrum administracyjnym programu SharePoint](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/set-up-information-rights-management-irm-insharepoint-online-HA102895193.aspx)

Ta konfiguracja jest implementowana przez administratora usługi Office 365.

### <a name="configuring-irm-for-libraries-and-lists"></a>Konfigurowanie usługi IRM na potrzeby bibliotek i list
Po włączeniu usługi IRM dla programu SharePoint właściciele witryn mogą przy jej użyciu chronić listy i biblioteki dokumentów programu SharePoint. Aby uzyskać instrukcje, zobacz następujące tematy w witrynie pakietu Office w sieci Web:

- [Stosowanie usługi Zarządzanie prawami do informacji w odniesieniu do listy lub biblioteki](https://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)

Ta konfiguracja jest implementowana przez administratora witryny programu SharePoint.

### <a name="configuring-irm-for-onedrive-for-business"></a>Konfigurowanie usługi IRM na potrzeby usługi OneDrive dla Firm
Po włączeniu usługi IRM dla usługi SharePoint Online, następnie można skonfigurować użytkowników w usłudze OneDrive dla firm, biblioteki dokumentów lub poszczególnych folderów dla ochrony usługi Rights Management. Użytkownicy mogą skonfigurować ją samodzielnie przy użyciu ich witryny sieci Web usługi OneDrive. Chociaż administratorzy nie można skonfigurować ochrony dla ich przy użyciu Centrum administracyjnego programu SharePoint, możesz to zrobić za pomocą programu Windows PowerShell.

> [!NOTE]
> Aby uzyskać więcej informacji na temat konfigurowania usługi OneDrive dla Firm, zobacz [Konfigurowanie usługi OneDrive dla Firm w usłudze Office 365](https://support.office.com/article/Set-up-OneDrive-for-Business-in-Office-365-3e21f8f0-e0a1-43be-aa3e-8c0236bf11bb) w dokumentacji pakietu Office.

#### <a name="configuration-for-users"></a>Konfiguracja dla użytkowników
Zapewnij użytkownikom zgodnie z poniższymi instrukcjami, aby może skonfigurować usługi OneDrive dla firm, aby chronić swoje pliki biznesowych.

1. Zaloguj się do usługi Office 365 przy użyciu konta służbowego lub szkolnego i przejdź do [witryny sieci Web w usłudze OneDrive](https://portal.office.com/onedrive).

2. W okienku nawigacji na dole, zaznacz **wróć do klasycznego OneDrive**.

3. Wybierz **ustawienia** ikony. W **ustawienia** okienko, jeśli **wstążki** ustawiono **poza**, wybierz to ustawienie, aby włączyć na Wstążce.

4. Aby skonfigurować wszystkie usługi OneDrive dla firm pliki mają być chronione, wybierz **biblioteki** karty na Wstążce, a następnie wybierz **ustawienia biblioteki**.

5. Na **dokumentów > Ustawienia** stronie **uprawnienia i zarządzanie** zaznacz **Zarządzanie prawami do informacji**.

6. Na **ustawienia zarządzania prawami do informacji** wybierz opcję **Ogranicz uprawnienia do tej biblioteki podczas pobierania** pole wyboru. Podaj wybraną nazwę i opis uprawnienia i opcjonalnie kliknij **Pokaż opcje** ustawienia konfiguracji opcjonalnych, a następnie kliknij przycisk **OK**.

    Aby uzyskać więcej informacji na temat opcji konfiguracji, zobacz instrukcje w artykule [Stosowanie usługi Zarządzanie prawami do informacji w odniesieniu do listy lub biblioteki](https://support.office.com/article/Apply-Information-Rights-Management-to-a-list-or-library-3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1) w dokumentacji pakietu Office.

Ponieważ ta konfiguracja korzysta z użytkowników, a nie administratora do usługi OneDrive dla firm plików ochronę usługi IRM, należy poinformować użytkowników o korzyściach z ochrony plików i jak to zrobić. Można na przykład wyjaśnić, że po udostępnieniu dokumentu z poziomu usługi OneDrive dla Firm tylko autoryzowane osoby będą mogły uzyskiwać do niego dostęp przy zachowaniu dowolnych ograniczeń skonfigurowanych przez użytkowników, nawet jeśli nazwa pliku została zmieniona, a plik został skopiowany do innej lokalizacji.

#### <a name="configuration-for-administrators"></a>Konfiguracja dla administratorów
Mimo że nie można konfigurować usługi Rights Management na potrzeby usługi OneDrive dla Firm użytkowników przy użyciu centrum administracyjnego programu SharePoint, można to zrobić w programie Windows PowerShell. Aby włączyć usługę IRM dla bibliotek, wykonaj następujące kroki:

1. Pobierz i zainstaluj [zestaw SDK składników klienta usługi SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=42038).

2. Pobierz i zainstaluj [powłokę zarządzania usługi SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588).

3. Skopiuj zawartość poniższego skryptu i nadaj plikowi nazwę Set-IRMOnOneDriveForBusiness.ps1 na swoim komputerze.

   *&#42;&#42;Zastrzeżenie&#42;&#42;*: Ten przykładowy skrypt nie jest obsługiwana w ramach usług ani programów pomocy technicznej standard firmy Microsoft. Ten przykładowy skrypt jest dostarczany W STANIE TAKIM, W JAKIM SIĘ ZNAJDUJE, bez jakichkolwiek gwarancji.

   ```
   # Requires Windows PowerShell version 3

   <#
     Description:

       Configures IRM policy settings for OneDrive for Business and can also be used for SharePoint Online libraries and lists

    Script Installation Requirements:

      SharePoint Online Client Components SDK
      https://www.microsoft.com/en-us/download/details.aspx?id=42038

      SharePoint Online Management Shell
      https://www.microsoft.com/en-us/download/details.aspx?id=35588

   ======
   #>

   # URL will be in the format https://<tenant-name>-admin.sharepoint.com
   $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

   $tenantAdmin = "admin@contoso.com"

   $webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com",
                "https://contoso-my.sharepoint.com/personal/user2_contoso_com",
                "https://contoso-my.sharepoint.com/personal/user3_contoso_com")

   <# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row).
      Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv"

   #>

   $listTitle = "Documents"

   function Load-SharePointOnlineClientComponentAssemblies
   {
       [cmdletbinding()]
       param()

       process
       {
           # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
           try
           {
               Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
               [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

               Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
               [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

               Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
               [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

               Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
               [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

               Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
               [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

               Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
               [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

               Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
               [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

               Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
               [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

               Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
               [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

               Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
               [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

               return $true
           }
           catch
           {
               if($_.Exception.Message -match "Could not load file or assembly")
               {
                   Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=42038"
               }
               else
               {
                   Write-Error -Exception $_.Exception
               }
               return $false
           }
       }
   }

   function Load-SharePointOnlineModule
   {
       [cmdletbinding()]
       param()

       process
       {
           do
           {
               # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
               $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

               if(-not $spoModule)
               {
                   try
                   {
                       Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                       return $true
                   }
                   catch
                   {
                       if($_.Exception.Message -match "Could not load file or assembly")
                       {
                           Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=35588"
                       }
                       else
                       {
                           Write-Error -Exception $_.Exception
                       }
                       return $false
                   }
               }
               else
               {
                   return $true
               }
           }
           while(-not $spoModule)
       }
   }

   function Set-IrmConfiguration
   {
       [cmdletbinding()]
       param(
           [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List,
           [parameter(Mandatory=$true)][string]$PolicyTitle,
           [parameter(Mandatory=$true)][string]$PolicyDescription,
           [parameter(Mandatory=$false)][switch]$IrmReject,
           [parameter(Mandatory=$false)][DateTime]$ProtectionExpirationDate,
           [parameter(Mandatory=$false)][switch]$DisableDocumentBrowserView,
           [parameter(Mandatory=$false)][switch]$AllowPrint,
           [parameter(Mandatory=$false)][switch]$AllowScript,
           [parameter(Mandatory=$false)][switch]$AllowWriteCopy,
           [parameter(Mandatory=$false)][int]$DocumentAccessExpireDays,
           [parameter(Mandatory=$false)][int]$LicenseCacheExpireDays,
           [parameter(Mandatory=$false)][string]$GroupName
       )

       process
       {
           Write-Verbose "Applying IRM Configuration on '$($List.Title)'"

           # reset the value to the default settings
           $list.InformationRightsManagementSettings.Reset()

           $list.IrmEnabled = $true

           # IRM Policy title and description

               $list.InformationRightsManagementSettings.PolicyTitle       = $PolicyTitle
               $list.InformationRightsManagementSettings.PolicyDescription = $PolicyDescription

           # Set additional IRM library settings

               # Do not allow users to upload documents that do not support IRM
               $list.IrmReject = $IrmReject.IsPresent

               $parsedDate = Get-Date
               if([DateTime]::TryParse($ProtectionExpirationDate, [ref]$parsedDate))
               {
                   # Stop restricting access to the library at <date>
                   $list.IrmExpire = $true
                   $list.InformationRightsManagementSettings.DocumentLibraryProtectionExpireDate = $ProtectionExpirationDate
               }

               # Prevent opening documents in the browser for this Document Library
               $list.InformationRightsManagementSettings.DisableDocumentBrowserView = $DisableDocumentBrowserView.IsPresent

           # Configure document access rights

               # Allow viewers to print
               $list.InformationRightsManagementSettings.AllowPrint = $AllowPrint.IsPresent

               # Allow viewers to run script and screen reader to function on downloaded documents
               $list.InformationRightsManagementSettings.AllowScript = $AllowScript.IsPresent

               # Allow viewers to write on a copy of the downloaded document
               $list.InformationRightsManagementSettings.AllowWriteCopy = $AllowWriteCopy.IsPresent

               if($DocumentAccessExpireDays)
               {
                   # After download, document access rights will expire after these number of days (1-365)
                   $list.InformationRightsManagementSettings.EnableDocumentAccessExpire = $true
                   $list.InformationRightsManagementSettings.DocumentAccessExpireDays   = $DocumentAccessExpireDays
               }

           # Set group protection and credentials interval

               if($LicenseCacheExpireDays)
               {
                   # Users must verify their credentials using this interval (days)
                   $list.InformationRightsManagementSettings.EnableLicenseCacheExpire = $true
                   $list.InformationRightsManagementSettings.LicenseCacheExpireDays   = $LicenseCacheExpireDays
               }

               if($GroupName)
               {
                   # Allow group protection. Default group:
                   $list.InformationRightsManagementSettings.EnableGroupProtection = $true
                   $list.InformationRightsManagementSettings.GroupName             = $GroupName
               }
       }
       end
       {
           if($list)
           {
               Write-Verbose "Committing IRM configuration settings on '$($list.Title)'"
               $list.InformationRightsManagementSettings.Update()
               $list.Update()
               $script:clientContext.Load($list)
               $script:clientContext.ExecuteQuery()
           }
       }
   }

   function Get-CredentialFromCredentialCache
   {
       [cmdletbinding()]
       param([string]$CredentialName)

       #if( Test-Path variable:\global:CredentialCache )
       if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
       {
           if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
           {
               Write-Verbose "Credential Cache Hit: $CredentialName"
               return $global:O365TenantAdminCredentialCache[$CredentialName]
           }
       }
       Write-Verbose "Credential Cache Miss: $CredentialName"
       return $null
   }

   function Add-CredentialToCredentialCache
   {
       [cmdletbinding()]
       param([System.Management.Automation.PSCredential]$Credential)

       if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
       {
           Write-Verbose "Initializing the Credential Cache"
           $global:O365TenantAdminCredentialCache = @{}
       }

       Write-Verbose "Adding Credential to the Credential Cache"
       $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
   }

   # load the required assemblies and Windows PowerShell modules

       if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

   # Add the credentials to the client context and SharePoint Online service connection

       # check for cached credentials to use
       $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

       if(-not $o365TenantAdminCredential)
       {
           # when credentials are not cached, prompt for the tenant admin credentials
           $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

           if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
           {
               Write-Error -Message "Could not validate the supplied tenant admin credentials"
               return
           }

           # add the credentials to the cache
           Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
       }

   # connect to Office365 first, required for SharePoint Online cmdlets to run

       Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential

   # enumerate each of the specified site URLs

       foreach($webUrl in $webUrls)
       {
           $grantedSiteCollectionAdmin = $false

           try
           {
               # establish the client context and set the credentials to connect to the site
               $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl)
               $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

               # initialize the site and web context
               $script:clientContext.Load($script:clientContext.Site)
               $script:clientContext.Load($script:clientContext.Web)
               $script:clientContext.ExecuteQuery()

               # load and ensure the tenant admin user account if present on the target SharePoint site
               $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName)
               $script:clientContext.Load($tenantAdminUser)
               $script:clientContext.ExecuteQuery()

               # check if the tenant admin is a site admin
               if( -not $tenantAdminUser.IsSiteAdmin )
               {
                   try
                   {
                       # grant the tenant admin temporary admin rights to the site collection
                       Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null
                       $grantedSiteCollectionAdmin = $true
                   }
                   catch
                   {
                       Write-Error $_.Exception
                       return
                   }
               }

               try
               {
                   # load the list orlibrary using CSOM

                   $list = $null
                   $list = $script:clientContext.Web.Lists.GetByTitle($listTitle)
                   $script:clientContext.Load($list)
                   $script:clientContext.ExecuteQuery()

                   # **************  ADMIN INSTRUCTIONS  **************
                   # If necessary, modify the following Set-IrmConfiguration parameters to match your required values
                   # The supplied options and values are for example only
                   # Example that shows the Set-IrmConfiguration command with all parameters: Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" -IrmReject -ProtectionExpirationDate $(Get-Date).AddDays(180) -DisableDocumentBrowserView -AllowPrint -AllowScript -AllowWriteCopy -LicenseCacheExpireDays 25 -DocumentAccessExpireDays 90

                   Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users"  
               }
               catch
               {
                   Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())"
               }
          }
          finally
          {
               if($grantedSiteCollectionAdmin)
               {
                   # remove the temporary admin rights to the site collection
                   Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null
               }
          }
       }

   Disconnect-SPOService -ErrorAction SilentlyContinue
   ```

4. Przejrzyj skrypt i wprowadź następujące zmiany:

   1. Wyszukaj ciąg `$sharepointAdminCenterUrl` i zastąp przykładową wartość adresem URL swojego centrum administracyjnego programu SharePoint.

      Ta wartość jest dostępna jako podstawowy adres URL w centrum administracyjnym programu SharePoint. Jej format jest następujący: https://<em>&lt;nazwa_dzierżawy&gt;</em>-admin.sharepoint.com

      Na przykład jeśli nazwa dzierżawy jest "contoso", następnie należy określić: **https://contoso-admin.sharepoint.com**

   2. Wyszukaj ciąg `$tenantAdmin` i zastąp przykładową wartość nazwą własnego w pełni kwalifikowanego konta administratora globalnego dla usługi Office 365.

      Ta wartość jest taka sama jak wartość używana do logowania do portalu administracyjnego usługi Office 365 jako administrator globalny i ma następujący format: nazwa_użytkownika@*&lt;nazwa_domeny_dzierżawy&gt;*.com.

      Jeśli na przykład nazwa użytkownika administratora globalnego usługi Office 365 „admin” odpowiada domenie dzierżawy „contoso.com”, należy podać wartość <strong>admin@contoso.com</strong>

   3. Wyszukaj ciąg `$webUrls` i zastąp przykładowe wartości adresami URL w sieci Web powiązanymi z usługą OneDrive dla Firm dla użytkowników, dodając lub usuwając potrzebną liczbę wpisów.

      Możesz również zapoznać się z komentarzami w skrypcie dotyczącymi sposobu zastępowania tej tablicy przez zaimportowanie pliku CSV zawierającego wszystkie adresy URL do zaimportowania.  Przygotowaliśmy inny przykładowy skrypt umożliwiający automatyczne wyszukiwanie i wyodrębnianie adresów URL na potrzeby wypełniania tego pliku CSV. Jeśli wszystko jest gotowe do wykonania tej czynności, skorzystaj z sekcji [Dodatkowy skrypt służący do wypełniania wyjściowego pliku CSV przy użyciu wszystkich adresów URL usługi OneDrive dla Firm](#additional-script-to-output-all-onedrive-for-business-urls-to-a-csv-file) od razu po wykonaniu tych kroków.

      Adres URL sieci Web dla usługi użytkownika OneDrive dla Firm użytkownika ma następujący format: https://<em>&lt;nazwa_dzierżawcy&gt;</em>-my.sharepoint.com/personal/*&lt;nazwa_użytkownika&gt;*_*&lt;nazwa dzierżawcy&gt;*_com

      Na przykład jeśli użytkownik w dzierżawie contoso ma nazwę użytkownika "rsimone", należy określić: **https://contoso-my.sharepoint.com/personal/rsimone_contoso_com**

   4. Ponieważ skrypt jest używany do konfigurowania usługi OneDrive dla Firm, nie należy zmieniać wartości **Dokumenty** zmiennej `$listTitle`.

   5. Wyszukaj ciąg `ADMIN INSTRUCTIONS`. Jeśli w tej sekcji nie zostaną wprowadzone żadne zmiany, usługa OneDrive dla Firm użytkownika zostanie skonfigurowana na potrzeby usług IRM z tytułem „Chronione pliki” i opisem zasad „Te zasady ograniczają dostęp do użytkowników autoryzowanych”.  Żadna inna opcja nie zostanie ustawiona — jest to prawdopodobnie odpowiednie w większości środowisk. Można jednak zmienić sugerowany tytuł i opis zasad, a także dodać inne opcje usługi IRM, które są odpowiednie dla danego środowiska. Zapoznaj się z opatrzonym komentarzami przykładem w skrypcie, który ułatwi Ci utworzenie własnego zestawu parametrów polecenia Set-IrmConfiguration.

5. Zapisz skrypt i podpisz go. Jeśli zrezygnujesz z podpisania skryptu (bezpieczniejsza opcja), program Windows PowerShell musi zostać skonfigurowany na komputerze, aby uruchamiać niepodpisane skrypty. Aby to zrobić, Uruchom sesję programu Windows PowerShell, korzystając z **Uruchom jako Administrator** opcję i wpisz: **Set-ExecutionPolicy Unrestricted**. Jednak taka konfiguracja pozwala na uruchomienie wszystkich niepodpisanych skryptów (mniej bezpieczna opcja).

   Aby uzyskać więcej informacji na temat podpisywania skryptów programu Windows PowerShell, zobacz artykuł [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) w bibliotece dokumentacji programu PowerShell.

6. Uruchom skrypt i po wyświetleniu monitu podaj hasło do konta administratora usługi Office 365. Jeśli zmodyfikujesz skrypt i uruchomisz go w tej samej sesji programu Windows PowerShell, nie pojawi się monit o podanie poświadczeń.

> [!TIP]
> Możesz również użyć tego skryptu do skonfigurowania usługi IRM na potrzeby biblioteki usługi SharePoint Online. W tej konfiguracji zechcesz prawdopodobnie włączyć opcję dodatkową, **Nie zezwalaj użytkownikom na przekazywanie dokumentów nieobsługujących usługi IRM**, aby upewnić się, że biblioteka zawiera tylko dokumenty chronione.    W tym celu dodaj parametr `-IrmReject` do polecenia Set-IrmConfiguration w skrypcie.
>
> Czy trzeba będzie również zmodyfikować `$webUrls` zmiennej (na przykład **https://contoso.sharepoint.com**) i `$listTitle` zmiennej (na przykład **$Reports**).

Jeśli chcesz wyłączyć usługę IRM w bibliotekach usługi OneDrive dla Firm użytkownika, zobacz sekcję [Skrypt służący do wyłączania usługi IRM dla usługi OneDrive dla Firm](#script-to-disable-irm-for-onedrive-for-business).

##### <a name="additional-script-to-output-all-onedrive-for-business-urls-to-a-csv-file"></a>Dodatkowy skrypt służący do wypełniania wyjściowego pliku CSV przy użyciu wszystkich adresów URL usługi OneDrive dla Firm
W powyższym kroku 4c możesz użyć poniższego skryptu programu Windows PowerShell, aby wyodrębnić adresy URL bibliotek usługi OneDrive dla Firm wszystkich użytkowników, które można potem sprawdzić, w razie potrzeby zmodyfikować, a następnie zaimportować do głównego skryptu.

Ten skrypt wymaga również [zestawu SDK składników klienta usługi SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=42038) i [powłoki zarządzania usługi SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588). Postępuj zgodnie z tymi samymi instrukcjami, aby go skopiować i wkleić, zapisz plik lokalnie (np. „raport-OneDriveForBusinessSiteInfo.ps1”), tak jak poprzednio zmodyfikuj wartości `$sharepointAdminCenterUrl` i `$tenantAdmin`, a następnie uruchom skrypt.

*&#42;&#42;Zastrzeżenie&#42;&#42;*: Ten przykładowy skrypt nie jest obsługiwana w ramach usług ani programów pomocy technicznej standard firmy Microsoft. Ten przykładowy skrypt jest dostarczany W STANIE TAKIM, W JAKIM SIĘ ZNAJDUJE, bez jakichkolwiek gwarancji.

```
# Requires Windows PowerShell version 3

<#
  Description:

    Queries the search service of an Office 365 tenant to retrieve all OneDrive for Business sites.  
    Details of the discovered sites are written to a .CSV file (by default,"OneDriveForBusinessSiteInfo_<date>.csv").

 Script Installation Requirements:

   SharePoint Online Client Components SDK
   https://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   https://www.microsoft.com/en-us/download/details.aspx?id=35588

======
#>

# URL will be in the format https://<tenant-name>-admin.sharepoint.com
$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.onmicrosoft.com"                           

$reportName = "OneDriveForBusinessSiteInfo_$((Get-Date).ToString("yyyy-MM-dd_hh.mm.ss")).csv"

$oneDriveForBusinessSiteUrls= @()
$resultsProcessed = 0

function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        {
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }

# establish the client context and set the credentials to connect to the site

    $clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($sharepointAdminCenterUrl)
    $clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

# run a query against the Office 365 tenant search service to retrieve all OneDrive for Business URLs

    do
    {
        # build the query object
        $query = New-Object Microsoft.SharePoint.Client.Search.Query.KeywordQuery($clientContext)
        $query.TrimDuplicates        = $false
        $query.RowLimit              = 500
        $query.QueryText             = "SPSiteUrl:'/personal/' AND contentclass:STS_Site"
        $query.StartRow              = $resultsProcessed
        $query.TotalRowsExactMinimum = 500000

        # run the query
        $searchExecutor = New-Object Microsoft.SharePoint.Client.Search.Query.SearchExecutor($clientContext)
        $queryResults = $searchExecutor.ExecuteQuery($query)
        $clientContext.ExecuteQuery()

        # enumerate the search results and store the site URLs
        $queryResults.Value[0].ResultRows | % {
            $oneDriveForBusinessSiteUrls += $_.Path
            $resultsProcessed++
        }
    }
    while($resultsProcessed -lt $queryResults.Value.TotalRows)

$oneDriveForBusinessSiteUrls | Out-File -FilePath $reportName
```

##### <a name="script-to-disable-irm-for-onedrive-for-business"></a>Skrypt służący do wyłączania usługi IRM dla usługi OneDrive dla Firm
Poniższy przykładowy skrypt umożliwia wyłączenie usługi IRM dla usługi OneDrive dla Firm użytkowników.

Ten skrypt wymaga również [zestawu SDK składników klienta usługi SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=42038) i [powłoki zarządzania usługi SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588). Skopiuj i wklej zawartość, zapisz plik lokalnie (np. „Disable-IRMOnOneDriveForBusiness.ps1”), a następnie zmodyfikuj wartości `$sharepointAdminCenterUrl` i `$tenantAdmin`. Ręcznie określ adresy URL usługi OneDrive dla Firm lub użyj skryptu z poprzedniej sekcji, aby je zaimportować, a następnie uruchom skrypt.

*&#42;&#42;Zastrzeżenie&#42;&#42;*: Ten przykładowy skrypt nie jest obsługiwana w ramach usług ani programów pomocy technicznej standard firmy Microsoft. Ten przykładowy skrypt jest dostarczany W STANIE TAKIM, W JAKIM SIĘ ZNAJDUJE, bez jakichkolwiek gwarancji.

```
# Requires Windows PowerShell version 3

<#
  Description:

    Disables IRM for OneDrive for Business and can also be used for SharePoint Online libraries and lists

 Script Installation Requirements:

   SharePoint Online Client Components SDK
   https://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   https://www.microsoft.com/en-us/download/details.aspx?id=35588

======
#>

$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.com"

$webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com",
             "https://contoso-my.sharepoint.com/personal/user2_contoso_com",
             "https://contoso-my.sharepoint.com/personal/person3_contoso_com")

<# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row).
   Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv"

#>

$listTitle = "Documents"

function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Remove-IrmConfiguration
{
    [cmdletbinding()]
    param(
        [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List
    )

    process
    {
        Write-Verbose "Disabling IRM Configuration on '$($List.Title)'"

        $List.IrmEnabled = $false
        $List.IrmExpire  = $false
        $List.IrmReject  = $false
        $List.InformationRightsManagementSettings.Reset()
    }
    end
    {
        if($List)
        {
            Write-Verbose "Committing IRM configuration settings on '$($list.Title)'"
            $list.InformationRightsManagementSettings.Update()
            $list.Update()
            $script:clientContext.Load($list)
            $script:clientContext.ExecuteQuery()
        }
    }
}

function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        {
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }

# connect to Office365 first, required for SharePoint Online cmdlets to run

    Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential

# enumerate each of the specified site URLs

    foreach($webUrl in $webUrls)
    {
        $grantedSiteCollectionAdmin = $false

        try
        {
            # establish the client context and set the credentials to connect to the site
            $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl)
            $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

            # initialize the site and web context
            $script:clientContext.Load($script:clientContext.Site)
            $script:clientContext.Load($script:clientContext.Web)
            $script:clientContext.ExecuteQuery()

            # load and ensure the tenant admin user account if present on the target SharePoint site
            $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName)
            $script:clientContext.Load($tenantAdminUser)
            $script:clientContext.ExecuteQuery()

            # check if the tenant admin is a site admin
            if( -not $tenantAdminUser.IsSiteAdmin )
            {
                try
                {
                    # grant the tenant admin temporary admin rights to the site collection
                    Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null
                    $grantedSiteCollectionAdmin = $true
                }
                catch
                {
                    Write-Error $_.Exception
                    return
                }
            }

            try
            {
                # load the list orlibrary using CSOM

                $list = $null
                $list = $script:clientContext.Web.Lists.GetByTitle($listTitle)
                $script:clientContext.Load($list)
                $script:clientContext.ExecuteQuery()

               Remove-IrmConfiguration -List $list                 
            }
            catch
            {
                Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())"
            }
       }
       finally
       {
            if($grantedSiteCollectionAdmin)
            {
                # remove the temporary admin rights to the site collection
                Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null
            }
       }
    }

Disconnect-SPOService -ErrorAction SilentlyContinue
```

