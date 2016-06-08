---
# required metadata

title: Uwierzytelnianie ADAL dla aplikacji z obsługą usługi RMS| Azure RMS
description: Zawiera opis procesu uwierzytelniania przy użyciu biblioteki ADAL
keywords: authentication, RMS, ADAL
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Zawartość tego zestawu SDK jest nieaktualna. Tymczasem należy korzystać z [bieżącej wersji](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) dokumentacji w witrynie MSDN. **
# Uwierzytelnianie ADAL dla aplikacji z obsługą usługi RMS

Uwierzytelnianie w usłudze Azure RMS dla aplikacji z użyciem biblioteki Azure ADAL jest obecnie dostępne w kliencie RMS w wersji 2.1.

Aktualizacja aplikacji umożliwiająca korzystanie z uwierzytelniania ADAL zamiast asystenta logowania usługi online firmy Microsoft zapewnia następujące możliwości:

- Korzystanie z uwierzytelniania wieloskładnikowego
- Instalowanie klienta usługi RMS 2.1 bez wymogu posiadania uprawnień administracyjnych na komputerze
- Certyfikowanie aplikacji dla systemu Windows 10

## Dwa podejścia do uwierzytelniania

W tym temacie przedstawiono dwie metody uwierzytelniania wraz z odpowiednimi przykładami kodu.

- **Uwierzytelnianie wewnętrzne** — uwierzytelnianie OAuth zarządzane przez zestaw RMS SDK. Tej metody należy użyć, jeśli klient RMS ma wyświetlać monit o uwierzytelnienie ADAL w przypadku, gdy wymagane jest uwierzytelnienie. Aby uzyskać szczegółowe informacje na temat konfigurowania aplikacji, zobacz część „Uwierzytelnianie wewnętrzne”.

> [!NOTE] Jeśli aplikacja używa aktualnie zestawu SDK usług AD RMS w wersji 2.1 z asystentem logowania, zalecane jest użycie metody uwierzytelniania wewnętrznego jako ścieżki migracji aplikacji.

- **Uwierzytelnianie zewnętrzne** — uwierzytelnianie OAuth zarządzane przez aplikację. Tej metody należy użyć, jeśli aplikacja ma zarządzać własnym uwierzytelnianiem OAuth. W przypadku tego podejścia klient RMS wykonuje wywołanie zwrotne określone w aplikacji, gdy jest wymagane uwierzytelnienie. Szczegółowy przykład znajduje się w części „Uwierzytelnianie zewnętrzne” na końcu tego tematu.

> [!NOTE] Uwierzytelnianie zewnętrzne nie oznacza możliwości zmiany użytkowników — w kliencie RMS zawsze używany jest domyślny użytkownik dla danej dzierżawy RMS.

### Uwierzytelnianie wewnętrzne

Potrzebne są następujące elementy:

- [Subskrypcja usługi Microsoft Azure](https://azure.microsoft.com/en-us/) (wystarczy bezpłatna wersja próbna):
- Subskrypcja usługi Microsoft Azure Rights Management (wystarczy bezpłatne konto w [usłudze RMS dla użytkowników indywidualnych](https://technet.microsoft.com/en-us/library/dn592127.aspx)).

> [!NOTE] Zapytaj administratora IT, czy jest dostępna subskrypcja usługi Microsoft Azure Rights Management, i poproś go o wykonanie poniższych czynności. Jeśli organizacja nie ma subskrypcji, administrator IT powinien ją utworzyć. Ponadto administrator IT powinien uzyskać subskrypcję dla konta służbowego lub szkolnego, a nie konta Microsoft (np. usługi Hotmail).

Po zarejestrowaniu się w usłudze Microsoft Azure:

- Zaloguj się w [portalu zarządzania Azure](https://manage.windowsazure.com) organizacji przy użyciu konta z uprawnieniami administracyjnymi.

![Logowanie w usłudze Azure](../media/AzurePortalLogin.png)

- Przejdź do aplikacji **Active Directory** po lewej stronie portalu.

![Wybierz opcję Active Directory](../media/AzureADPick.png)

- Jeśli nie utworzono jeszcze katalogu, kliknij przycisk **Nowy** w lewym dolnym rogu portalu.

![Wybierz opcję NOWY](../media/AzureNewBtn.png)

- Wybierz kartę **Rights Management** i upewnij się, że **stan usługi Rights Management** ma wartość **Aktywny**, **Nieznany** lub **Bez autoryzacji**. Jeśli bieżący stan to **Nieaktywny**, kliknij przycisk **Aktywuj** znajdujący się na środku w dolnej części portalu i potwierdzić wybór.

![Wybierz opcję AKTYWUJ](../media/RMTab.png)

- Następnie utwórz nową *aplikację natywną* w katalogu, wybierając katalog i opcję Aplikacje.

![Wybierz opcję APLIKACJE](../media/CreateNativeApp.png)

- Następnie kliknij przycisk **DODAJ** znajdujący się na środku w dolnej części portalu.

![Wybierz opcję DODAJ](../media/AddAppBtn.png)

- Po wyświetleniu monitu wybierz opcję **Dodaj aplikację opracowywaną przez moją organizację**.

![Wybierz opcję Dodaj aplikację opracowywaną przez moją organizację.](../media/AddAnAppPick.png)

- Określ nazwę aplikacji, zaznaczając **NATYWNĄ APLIKACJĘ KLIENCKĄ** i klikając przycisk **Dalej**.

![Określ nazwę aplikacji](../media/TellUsInput.png)

- Dodaj identyfikator URI przekierowania i wybierz opcję Dalej. Identyfikator URI przekierowania musi być prawidłowym identyfikatorem URI unikatowym dla danego katalogu. Można na przykład użyć ciągu `com.mycompany.myapplication://authorize`.

![Dodaj identyfikator URI przekierowania](../media/RedirectURI.png)

- Wybierz aplikację z katalogu i wybierz polecenie **KONFIGURUJ**.

![Wybierz opcję KONFIGURUJ](../media/ConfigYourApp.png)

>[!NOTE] Skopiuj **IDENTYFIKATOR KLIENTA** i **IDENTYFIKATOR URI PRZEKIEROWANIA** i zapisz je do użycia w przyszłości podczas konfigurowania klienta usługi RMS.

- Przejdź do dolnej części obszaru ustawień aplikacji i kliknij przycisk **Dodaj aplikację** w obszarze **uprawnień dotyczących innych aplikacji**.

![Wybierz opcję Dodaj aplikację](../media/PermissionsToOtherBtn.png)

- Następnie dodaj ten identyfikator GUID `00000012-0000-0000-c000-000000000000` w polu edycji **ROZPOCZYNA SIĘ OD**, a następnie kliknij przycisk znaku wyboru.

![Dodaj identyfikator GUID](../media/AddGUID.png)

- Kliknij przycisk plus (+) obok opcji **Microsoft Rights Management**.

![Kliknij przycisk +](../media/ChoosePlusBtn.png)

- Następnie kliknij znacznik wyboru znajdujący się w lewym dolnym rogu okna dialogowego.

![Kliknij znacznik wyboru](../media/ChooseCheck.png)

- Możesz teraz dodać do aplikacji zależność dotyczącą usługi Azure RMS. Aby dodać zależność, wybierz nową pozycję **Microsoft Rights Management Services** w obszarze **uprawnień dotyczących innych aplikacji** i zaznacz pole wyboru **Tworzenie i uzyskiwanie dostępu do chronionej zawartości dla użytkowników** w polu listy rozwijanej **Delegowane uprawnienia**.

![Uprawnienia do konfiguracji](../media/AddDependency.png)

- Zapisz aplikację, aby zachować zmiany, wybierając ikonę **ZAPISZ** znajdującą się na środku w dolnej części portalu.

![Wybierz opcję ZAPISZ](../media/SaveApplication.png)

- Teraz możesz przystąpić do konfigurowania aplikacji do korzystania z wewnętrznego uwierzytelniania ADAL zapewnianego w ramach zestawu RMS SDK 2.1. Aby skonfigurować klienta usługi RMS, dodaj wywołanie do właściwości [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/IpcSetGlobalProperty) bezpośrednio po wywołaniu [IpcInitialize](/rights-management/sdk/2.1/api/win/IpcInitialize). Jako przykład może posłużyć poniższy fragment kodu.


    IpcInitialize();

    IPC_AAD_APPLICATION_ID applicationId = { 0 };   applicationId.cbSize = sizeof(IPC_AAD_APPLICATION_ID);   applicationId.wszClientId = L"GUID-provided-by-AAD-for-your-app-(no-brackets)";   applicationId.wszRedirectUri = L"RedirectionUriWeProvidedAADForOurApp://authorize";

    HRESULT hr = IpcSetGlobalProperty(IPC_EI_APPLICATION_ID, &amp;applicationId);

    if (FAILED(hr)) {    //Handle the error   }

### Uwierzytelnianie zewnętrzne

- Poniższy kod stanowi przykład zarządzania własnymi tokenami uwierzytelniania.


    extern HRESULT GetADALToken(LPVOID pContext, const IPC_NAME_VALUE_LIST&amp; Parameters, __out wstring wstrToken) throw();

    HRESULT GetLicenseKey(PCIPC_BUFFER pvLicense, __in LPVOID pContextForAdal, __out IPC_KEY_HANDLE &amp;hKey) { IPC_OAUTH2_CALLBACK pfGetADALToken =         [](LPVOID pvContext, PIPC_NAME_VALUE_LIST pParameters, IPC_AUTH_TOKEN_HANDLE* phAuthToken) -&gt; HRESULT { wstring wstrToken; HRESULT hr = GetADALToken(pvContext, *pParameters, wstrToken); return SUCCEEDED(hr) ? IpcCreateOAuth2Token(wstrToken.c_str(), OUT phAuthToken) : hr; };

      IPC_OAUTH2_CALLBACK_INFO callbackCredentialContext =
      {
          sizeof(IPC_OAUTH2_CALLBACK_INFO),
          pfGetADALToken,
          pContextForAdal
      };

      IPC_CREDENTIAL credentialContext =
      {
          IPC_CREDENTIAL_TYPE_OAUTH2,
          NULL
      };
      credentialContext.pcOAuth2 = &amp;callbackCredentialContext;

      IPC_PROMPT_CTX promptContext =
      {
        sizeof(IPC_PROMPT_CTX),
        NULL,
        IPC_PROMPT_FLAG_SILENT | IPC_PROMPT_FLAG_HAS_USER_CONSENT,
        NULL,
        &amp;credentialContext
      };

      hKey = 0L;
      return IpcGetKey(pvLicense, 0, &amp;promptContext, NULL, &amp;hKey);
  }

### Tematy pokrewne
- [Typy danych](/rights-management/sdk/2.1/api/win/Data%20types)
- [Właściwości środowiska](/rights-management/sdk/2.1/api/win/Environment%20properties)
- [IpcCreateOAuth2Token](/rights-management/sdk/2.1/api/win/IpcCreateOAuth2Token)
- [IpcGetKey](/rights-management/sdk/2.1/api/win/IpcGetKey)
- [IpcInitialize](/rights-management/sdk/2.1/api/win/IpcInitialize)
- [IPC_CREDENTIAL](/rights-management/sdk/2.1/api/win/IPC\_CREDENTIAL)
- [IPC_NAME_VALUE_LIST](/rights-management/sdk/2.1/api/win/IPC\_NAME\_VALUE\_LIST)
- [IPC_OAUTH2_CALLBACK_INFO](/rights-management/sdk/2.1/api/win/IPC\_OAUTH2\_CALLBACK\_INFO)
- [IPC_PROMPT_CTX](/rights-management/sdk/2.1/api/win/IPC\_PROMPT\_CTX)
- [IPC_AAD_APPLICATION_ID](/rights-management/sdk/2.1/api/win/IPC\_AAD\_APPLICATION\_ID)


<!--HONumber=Jun16_HO1-->


