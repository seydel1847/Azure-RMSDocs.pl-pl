---
title: "Tworzenie aplikacji — AIP"
description: "Wskazówki dotyczące tworzenia podstawowej aplikacji konsoli wdrażającej ochronę dokumentów z użyciem usługi AIP"
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 396A2C19-3A00-4E9A-9088-198A48B15289
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 24689c3337361fb5e59420684ec8f5e9c723e448
ms.sourcegitcommit: 262f88c4f46e29f3747271276c62913b4cefe4f7
translationtype: HT
---
# <a name="developing-your-application"></a>Tworzenie aplikacji

W tym przykładzie zostanie utworzona prosta aplikacja konsoli, która współpracuje z usługą Azure Information Protection (AIP).  Proces będzie wymagał wprowadzenia ścieżki dokumentu, który ma zostać objęty ochroną, a następnie objęcia go ochroną za pomocą zasad ad hoc lub szablonu usługi Azure. Aplikacja zastosuje następnie właściwe zasady zgodnie z wprowadzonymi danymi, tworząc dokument zawierający informacje chronione. W ćwiczeniu zostanie użyty przykładowy kod [Azure IP test application](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test), który jest dostępny w witrynie Github.

## <a name="sample-app-prerequisites"></a>Wymagania wstępne dotyczące przykładowej aplikacji
- **System operacyjny**: Windows 10, Windows 8, Windows 7, Windows Server 2008, Windows Server 2008 R2 lub Windows Server 2012
- **Język programowania**: C# (oprogramowanie .NET Framework w wersji 3.0 lub nowszej)
- **Środowisko deweloperskie**: Visual Studio 2015 (lub nowsze)

## <a name="setting-up-your-azure-configuration"></a>Ustawianie konfiguracji usługi Azure

Skonfigurowanie usługi Azure pod kątem tej aplikacji wymaga utworzenia identyfikatora dzierżawcy, klucza symetrycznego i identyfikatora podmiotu zabezpieczeń aplikacji.

### <a name="azure-ad-tenant-configuration"></a>Konfiguracja dzierżawy usługi Azure AD

Aby skonfigurować środowisko usługi Azure AD pod kątem usługi Azure Information Protection, postępuj zgodnie ze wskazówkami zawartymi w części [Activating Azure Rights Management](https://docs.microsoft.com/en-us/information-protection/deploy-use/activate-service) (Aktywowanie usługi Azure Rights Management).

W celu przejścia do kolejnych kroków po aktywowaniu usługi wymagane są składniki środowiska PowerShell. Aby uzyskać do nich dostęp, wykonaj instrukcje zawarte w części [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](https://docs.microsoft.com/en-us/information-protection/deploy-use/administer-powershell).

### <a name="getting-your-tenant-id"></a>Uzyskiwanie identyfikatora dzierżawy

- Uruchom program PowerShell jako administrator.
- Zaimportuj moduł RMS:`Import-Module AADRM`
- Połącz się z usługą za pomocą przypisanych poświadczeń użytkownika:`Connect-AadrmService –Verbose`
- Upewnij się, że usługa RMS jest włączona:`Enable-AADRM`
- Uzyskaj identyfikator dzierżawy, uruchamiając polecenie:`Get-AadrmConfiguration`

>Zapisz wartość BPOSId (identyfikator dzierżawy). Będzie ona potrzebna w toku realizacji kolejnych kroków.

*Przykładowe dane wyjściowe*
![dane wyjściowe polecenia cmdlet](../media/develop/output-of-Get-AadrmConfiguration.png)

- Zakończ połączenie z usługą:`Disconnect-AadrmService`

### <a name="create-a-service-principal"></a>Tworzenie nazwy głównej usługi
Wykonaj następujące kroki, aby utworzyć nazwę główną usługi:
> Nazwa główna usługi to poświadczenia skonfigurowane globalnie do ustanawiania kontroli dostępu w celu zezwalania usłudze na uwierzytelnianie się za pomocą usługi Microsoft Azure AD oraz na zapewnianie ochrony informacji z użyciem usługi Microsoft Azure AD Rights Management

- Uruchom program PowerShell jako administrator
- Zaimportuj moduł usługi Microsoft Azure AD, korzystając z polecenia:`Import-Module MSOnline`
- Połącz się z usługą online za pomocą przypisanych poświadczeń użytkownika: `Connect-MsolService`
- Utwórz nową nazwę główną usługi za pomocą polecenia:`New-MsolServicePrincipal`
- Podaj nazwę główną usługi
> Zapisz klucz symetryczny i identyfikator podmiotu zabezpieczeń aplikacji, aby móc ich użyć w przyszłości.

*Przykładowe dane wyjściowe*
![dane wyjściowe polecenia cmdlet](../media/develop/output-of-NewMsolServicePrincipal.png)

- Dodaj identyfikator podmiotu zabezpieczeń aplikacji, klucz symetryczny i identyfikator dzierżawy do pliku App.config aplikacji.

*Przykładowy plik App.config*
![dane wyjściowe polecenia cmdlet](../media/develop/example-App.config-file.png)

- Wartości *ClientID* i *RedirectUri* będą dostępne od momentu rejestracji aplikacji w usłudze Azure. Aby uzyskać więcej informacji na temat rejestrowania aplikacji w usłudze Azure oraz uzyskiwania wartości parametrów *ClientID* i *RedirectUri*, zobacz artykuł [Konfigurowanie usługi Azure RMS na potrzeby uwierzytelniania ADAL](adal-auth.md).


## <a name="design-summary"></a>Podsumowanie projektu
Poniższy diagram przedstawia architekturę i przepływ procesu tworzonej aplikacji. Niezbędne kroki opisano poniżej.
![podsumowanie projektu](../media/develop/design-summary.png)

1. Dane wejściowe użytkownika:
  - Ścieżka pliku, który ma zostać objęty ochroną
  - Wybór szablonu lub utworzenie zasady ad hoc
2. Aplikacja żąda uwierzytelnienia w usłudze AIP.
3. Usługa AIP potwierdza uwierzytelnienie.
4. Aplikacja żąda szablonów z usługi AIP.
5. Usługa AIP zwraca wstępnie zdefiniowane szablony.
6. Aplikacja lokalizuje określony plik znajdujący się w podanej lokalizacji.
7. Aplikacja stosuje do pliku zasady ochrony usługi AIP.

## <a name="how-the-code-works"></a>Działanie kodu

W przykładzie (Azure IP Test) rozwiązanie rozpoczyna się od pliku Iprotect.cs. Jest to aplikacja konsoli C#, która, podobnie jak każda inna aplikacja z obsługą usługi AIP, rozpoczyna działanie od załadowania pliku *MSIPC.dll*, jak zostało to pokazane w metodzie `main()`.

    //Loads MSIPC.dll
    SafeNativeMethods.IpcInitialize();
    SafeNativeMethods.IpcSetAPIMode(APIMode.Server);

Załadowanie parametrów wymaganych do nawiązania połączenia z usługą Azure

    //Loads credentials for the service principal from App.Config
    SymmetricKeyCredential symmetricKeyCred = new SymmetricKeyCredential();
    symmetricKeyCred.AppPrincipalId = ConfigurationManager.AppSettings["AppPrincipalId"];
    symmetricKeyCred.Base64Key = ConfigurationManager.AppSettings["Base64Key"];
    symmetricKeyCred.BposTenantId = ConfigurationManager.AppSettings["BposTenantId"];

Po podaniu ścieżki pliku w aplikacji konsoli aplikacja sprawdza, czy dokument jest już zaszyfrowany. Metoda należy do klasy **SafeFileApiNativeMethods**.

    var checkEncryptionStatus = SafeFileApiNativeMethods.IpcfIsFileEncrypted(filePath);

Jeśli dokument nie jest zaszyfrowany, następuje przejście do procedury szyfrowania dokumentu z zastosowaniem wyboru dokonanego po wyświetleniu monitu.

    if (!checkEncryptionStatus.ToString().ToLower().Contains(alreadyEncrypted))
    {
      if (method == EncryptionMethod1)
      {
        //Encrypt a file via AIP template
        ProtectWithTemplate(symmetricKeyCred, filePath);

      }
      else if (method == EncryptionMethod2)
      {
        //Encrypt a file using ad-hoc policy
        ProtectWithAdHocPolicy(symmetricKeyCred, filePath);
      }

Opcja ochrony z użyciem szablonu pobiera następnie listę szablonów z serwera i umożliwia użytkownikowi wybranie opcji.
>Jeśli nie wybrano opcji modyfikacji szablonów, nastąpi pobranie domyślnych szablonów z usługi AIP

     public static void ProtectWithTemplate(SymmetricKeyCredential symmetricKeyCredential, string filePath)
     {
       // Gets the available templates for this tenant             
       Collection<TemplateInfo> templates = SafeNativeMethods.IpcGetTemplateList(null, false, true,
           false, true, null, null, symmetricKeyCredential);

       //Requests tenant template to use for encryption
       Console.WriteLine("Please select the template you would like to use to encrypt the file.");

       //Outputs templates available for selection
       int counter = 0;
       for (int i = 0; i < templates.Count; i++)
       {
         counter++;
         Console.WriteLine(counter + ". " + templates.ElementAt(i).Name + "\n" +
             templates.ElementAt(i).Description);
       }

       //Parses template selection
       string input = Console.ReadLine();
       int templateSelection;
       bool parseResult = Int32.TryParse(input, out templateSelection);

       //Returns error if no template selection is entered
       if (parseResult)
       {
         //Ensures template value entered is valid
         if (0 < templateSelection && templateSelection <= counter)
         {
           templateSelection -= templateSelection;

           // Encrypts the file using the selected template             
           TemplateInfo selectedTemplateInfo = templates.ElementAt(templateSelection);

           string encryptedFilePath = SafeFileApiNativeMethods.IpcfEncryptFile(filePath,
               selectedTemplateInfo.TemplateId,
               SafeFileApiNativeMethods.EncryptFlags.IPCF_EF_FLAG_KEY_NO_PERSIST, true, false, true, null,
               symmetricKeyCredential);
          }
        }
      }

W przypadku wybrania opcji zasad ad hoc użytkownik aplikacji musi podać adresy e-mail osób, którym zostaną nadane prawa. W tej sekcji następuje utworzenie licencji przy użyciu metody **IpcCreateLicenseFromScratch()** i zastosowanie nowych zasad do szablonu.

    if (issuerDisplayName.Trim() != "")
    {
      // Gets the available issuers of rights policy templates.              
      // The available issuers is a list of RMS servers that this user has already contacted.
      try
      {
        Collection<TemplateIssuer> templateIssuers = SafeNativeMethods.IpcGetTemplateIssuerList(
                                                        null,
                                                        true,
                                                        false,
                                                        false, true, null, symmetricKeyCredential);

        // Creates the policy and associates the chosen user rights with it             
        SafeInformationProtectionLicenseHandle handle = SafeNativeMethods.IpcCreateLicenseFromScratch(
                                                            templateIssuers.ElementAt(0));
        SafeNativeMethods.IpcSetLicenseOwner(handle, owner);
        SafeNativeMethods.IpcSetLicenseUserRightsList(handle, userRights);
        SafeNativeMethods.IpcSetLicenseDescriptor(handle, new TemplateInfo(null, CultureInfo.CurrentCulture,
                                                                policyName,
                                                                policyDescription,
                                                                issuerDisplayName,
                                                                false));

        //Encrypts the file using the ad hoc policy             
        string encryptedFilePath = SafeFileApiNativeMethods.IpcfEncryptFile(
                                       filePath,
                                       handle,
                                       SafeFileApiNativeMethods.EncryptFlags.IPCF_EF_FLAG_KEY_NO_PERSIST,
                                       true,
                                       false,
                                       true,
                                       null,
                                       symmetricKeyCredential);
       }
    }

## <a name="user-interaction-example"></a>Przykład interakcji użytkownika

Po otrzymaniu i uruchomieniu aplikacji jej dane wyjściowe powinny wyglądać następująco:

1. Zostanie wyświetlony monit o wybranie metody szyfrowania.
![dane wyjściowe aplikacji — krok 1](../media/develop/app-output-1.png)

2. Zostanie wyświetlony monit o podanie ścieżki do pliku, który ma być chroniony.
![dane wyjściowe aplikacji — krok 2](../media/develop/app-output-2.png)

3. Zostanie wyświetlony monit o wprowadzenie adresu e-mail właściciela licencji (wskazany właściciel musi mieć uprawnienia administratora globalnego w odniesieniu do dzierżawy usługi Azure AD).
![dane wyjściowe aplikacji — krok 3](../media/develop/app-output-3.png)

4. Następuje wprowadzenie adresów e-mail użytkowników, którzy będą mieć uprawnienia dostępu do pliku (adresy e-mail należy rozdzielić spacjami).
![dane wyjściowe aplikacji — krok 4](../media/develop/app-output-4.png)

5. Należy wybrać z listy uprawnienia do nadania autoryzowanym użytkownikom.
![dane wyjściowe aplikacji — krok 5](../media/develop/app-output-5.png)

6. Po wykonaniu poprzednich kroków następuje wprowadzenie niektórych metadanych zasad: nazwy zasady, jej opisu, nazwy wyświetlanej wystawcy (dzierżawy usługi Azure AD) ![dane wyjściowe aplikacji — krok 6](../media/develop/app-output-6.png)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]