---
title: Jak umożliwiać współpracę aplikacji usługi z usługą RMS opartą na chmurze | Azure RMS
description: W tym temacie opisano kroki konfigurowania aplikacji usługi do korzystania z usługi Azure Rights Management.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: EA1457D1-282F-4CF3-A23C-46793D2C2F32
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 656715f8632fb17f0dd12f6e521dd6f5993a92b9
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39371377"
---
# <a name="how-to-enable-your-service-application-to-work-with-cloud-based-rms"></a>Instrukcje: umożliwianie współdziałania aplikacji usługi z usługą RMS opartą na chmurze

W tym temacie opisano kroki konfigurowania aplikacji usługi do korzystania z usługi Azure Rights Management. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy z usługą Azure Rights Management](https://technet.microsoft.com/library/jj585016.aspx).

**Ważne**  
Aby móc użyć aplikacji usługi zestawu Rights Management Services SDK 2.1 z usługą Azure RMS, musisz utworzyć własne dzierżawy. Aby uzyskać więcej informacji, zobacz [Wymagania dotyczące usługi Azure RMS: subskrypcje usług w chmurze, które obsługują usługę Azure RMS](../get-started/requirements-subscriptions.md)

## <a name="prerequisites"></a>Wymagania wstępne

-   Należy zainstalować i skonfigurować zestaw SDK usług RMS 2.1. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy z zestawem SDK usług RMS 2.1](getting-started-with-ad-rms-2-0.md).
-   Musisz [utworzyć tożsamość usługi przez ACS](https://msdn.microsoft.com/library/gg185924.aspx) przy użyciu opcji klucza symetrycznego lub innej metody oraz zarejestrować dane klucza z tego procesu.

## <a name="connecting-to-the-azure-rights-management-service"></a>Łączenie z usługą Azure Rights Management

-   Wywołaj metodę [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx).
-   Ustaw właściwość [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx).

        C++
        int mode = IPC_API_MODE_SERVER;
        IpcSetGlobalProperty(IPC_EI_API_MODE, &(mode));


  **Uwaga** Aby uzyskać więcej informacji, zobacz [Ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md)

     
-   Poniższe kroki to etapy konfiguracji tworzenia wystąpienia struktury [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx) z elementem *pcCredential* ([IPC\_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx)) wypełnionym informacjami na temat połączenia z usługą Azure Rights Management.
-   Użyj informacji z procedury tworzenia tożsamości usługi klucza symetrycznego (zobacz wymagania wstępne wymienione we wcześniejszej części tego tematu), aby ustawić parametry *wszServicePrincipal*, *wszBposTenantId* i *cbKey* podczas tworzenia wystąpienia struktury [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx).

**Uwaga**: Ze względu na stan naszej usługi odnajdywania, jeśli nie znajdujesz się w Ameryce Północnej, nie są akceptowane poświadczenia kluczy symetrycznych z innych regionów, w związku z czym należy bezpośrednio określić adresy URL dzierżawy. Można to zrobić przy użyciu parametru *pConnectionInfo* typu [IPC\_CONNECTION\_INFO](https://msdn.microsoft.com/library/hh535274.aspx) w funkcjach [IpcGetTemplateList](https://msdn.microsoft.com/library/hh535267.aspx) lub [IpcGetTemplateIssuerList](https://msdn.microsoft.com/library/hh535266.aspx).

## <a name="generate-a-symmetric-key-and-collect-the-needed-information"></a>Generowanie klucza symetrycznego i zbieranie potrzebnych informacji

### <a name="instructions-to-generate-a-symmetric-key"></a>Instrukcje generowania klucza symetrycznego

-   Zainstaluj [Asystenta logowania w witrynie Microsoft Online Services](http://go.microsoft.com/fwlink/p/?LinkID=286152)
-   Zainstaluj [moduł PowerShell usługi Azure AD](https://bposast.vo.msecnd.net/MSOPMW/8073.4/amd64/AdministrationConfig-en.msi).

**Uwaga**: Tylko administrator dzierżawy może korzystać z poleceń cmdlet modułu Powershell.

- Uruchom program Powershell i uruchom następujące polecenia, aby wygenerować klucz

    `Import-Module MSOnline`

    `Connect-MsolService` (wpisz swoje poświadczenia administratora)

    `New-MsolServicePrincipal` (wpisz nazwę wyświetlaną)

- Po wygenerowaniu klucza symetrycznego wyświetlane są informacje na temat klucza, w tym sam klucz i element *AppPrincipalId*.

      The following symmetric key was created as one was not supplied
      ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

      DisplayName : RMSTestApp
      ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963}
      ObjectId : 0ee53770-ec86-409e-8939-6d8239880518
      AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963


### <a name="instructions-to-find-out-tenantbposid-and-urls"></a>Instrukcje określania wartości **TenantBposId** i **Urls**

-   Zainstaluj [moduł PowerShell usługi Azure RMS](https://technet.microsoft.com/library/jj585012.aspx).
-   Uruchom program Powershell i uruchom następujące polecenia, aby uzyskać konfigurację usługi RMS dzierżawy.

    `Import-Module aadrm`

    `Connect-AadrmService` (wpisz swoje poświadczenia administratora)

    `Get-AadrmConfiguration`


- Utwórz wystąpienie struktury [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx) i ustaw kilku członków.

      // Create a key structure.
      IPC_CREDENTIAL_SYMMETRIC_KEY symKey = {0};

      // Set each member with information from service creation.
      symKey.wszBase64Key = "your service principal key";
      symKey.wszAppPrincipalId = "your app principal identifier";
      symKey.wszBposTenantId = "your tenant identifier";


Aby uzyskać więcej informacji, zobacz [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx).

-   Utwórz wystąpienie struktury [IPC\_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx) zawierające wystąpienie [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx).

**Uwaga**: Elementy członkowskie *connectionInfo* są konfigurowane przy użyciu adresów URL z poprzedniego wywołania elementu `Get-AadrmConfiguration` i oznaczane w tym miejscu przy użyciu tych nazw pól.

    // Create a credential structure.
    IPC_CREDENTIAL cred = {0};

    IPC_CONNECTION_INFO connectionInfo = {0};
    connectionInfo.wszIntranetUrl = LicensingIntranetDistributionPointUrl;
    connectionInfo.wszExtranetUrl = LicensingExtranetDistributionPointUrl;

    // Set each member.
    cred.dwType = IPC_CREDENTIAL_TYPE_SYMMETRIC_KEY;
    cred.pcCertContext = (PCCERT_CONTEXT)&symKey;

    // Create your prompt control.
    IPC_PROMPT_CTX promptCtx = {0};

    // Set each member.
    promptCtx.cbSize = sizeof(IPC_PROMPT_CTX);
    promptCtx.hwndParent = NULL;
    promptCtx.dwflags = IPC_PROMPT_FLAG_SILENT;
    promptCtx.hCancelEvent = NULL;
    promptCtx.pcCredential = &cred;

### <a name="identify-a-template-and-then-encrypt"></a>Zidentyfikuj szablon i zaszyfruj go

-   Wybierz szablon do użycia dla szyfrowania.
    Wywołaj element [IpcGetTemplateList](https://msdn.microsoft.com/library/hh535267.aspx), przekazując to samo wystąpienie elementu [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx).


    PCIPC_TIL pTemplates = NULL; IPC_TEMPLATE_ISSUER templateIssuer = (pTemplateIssuerList->aTi)[0];

    hr = IpcGetTemplateList(&(templateIssuer.connectionInfo),        IPC_GTL_FLAG_FORCE_DOWNLOAD,        0,        &promptCtx,        NULL,        &pTemplates);


-   Przy użyciu szablonu z wcześniejszej części tego tematu wywołaj element [IpcfEncrcyptFile](https://msdn.microsoft.com/library/dn133059.aspx), przekazując to samo wystąpienie elementu [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx).

Przykładowe zastosowanie wywołania elementu [IpcfEncrcyptFile](https://msdn.microsoft.com/library/dn133059.aspx):

    LPCWSTR wszContentTemplateId = pTemplates->aTi[0].wszID;
    hr = IpcfEncryptFile(wszInputFilePath,
           wszContentTemplateId,
           IPCF_EF_TEMPLATE_ID,
           IPC_EF_FLAG_KEY_NO_PERSIST,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Przykładowe zastosowanie wywołania elementu [IpcfDecryptFile](https://msdn.microsoft.com/library/dn133058.aspx):

    hr = IpcfDecryptFile(wszInputFilePath,
           IPCF_DF_FLAG_DEFAULT,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Ukończono kroki niezbędne do włączenia obsługi usługi Azure Rights Management przez aplikację.

## <a name="related-topics"></a>Tematy pokrewne

* [Rozpoczynanie pracy z usługą Azure Rights Management](https://technet.microsoft.com/library/jj585016.aspx)
* [Rozpoczynanie pracy z zestawem SDK 2.1 usługi RMS](getting-started-with-ad-rms-2-0.md)
* [Tworzenie tożsamości usługi za pośrednictwem usługi ACS](https://msdn.microsoft.com/library/gg185924.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)
* [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx)
* [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx)
* [IPC\_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx)
* [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx)
* [IpcGetTemplateIssuerList](https://msdn.microsoft.com/library/hh535266.aspx)
* [IpcGetTemplateList](https://msdn.microsoft.com/library/hh535267.aspx)
* [IpcfDecryptFile](https://msdn.microsoft.com/library/dn133058.aspx)
* [IpcfEncrcyptFile](https://msdn.microsoft.com/library/dn133059.aspx)
* [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx)
* [IpcCreateLicenseFromTemplateID](https://msdn.microsoft.com/library/hh535257.aspx)
