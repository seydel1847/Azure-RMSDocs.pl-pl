---
title: Jak dodać jawne prawa właściciela | Azure RMS
description: W przypadku tworzenia licencji od podstaw w aplikacji należy jawnie dodać prawa właściciela.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: EF43FAC4-ABB4-459D-B173-972B5716F816
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 6322831ee15266a4709284da0f9eb113f6d3eaf0
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44147123"
---
# <a name="how-to-add-explicit-owner-rights"></a>Instrukcje: dodawanie jawnych praw właściciela

W przypadku tworzenia licencji od podstaw przy użyciu funkcji [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx) w aplikacji należy jawnie dodać prawa „właściciela”.

## <a name="prerequisites"></a>Wymagania wstępne

Gdy aplikacja tworzy dojście licencji przy użyciu funkcji [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx), musi również jawnie przyznać pełne prawa (uprawnienia) właściciela.

>[!NOTE] 
> Ustawienie użytkownika jako „właściciela” przy użyciu funkcji [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx) **IPC\_LI\_OWNER** nie powoduje przyznania pełnych uprawnień właściciela.

Ten przykładowy kod przedstawia tylko kroki związane z tworzeniem i dodawaniem określonych praw do danej licencji.

## <a name="instructions"></a>Instrukcje
 
## <a name="step-1-example-scenario"></a>Krok 1. Przykładowy scenariusz

W tym przykładzie potrzebne prawa są dodawane do licencji utworzonej przy użyciu funkcji [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx). W przykładzie pokazano tworzenie i przypisywanie praw do licencji za pomocą listy praw.

Następujące dwa uprawnienia są dodawane do tych użytkowników:

-   Uprawnienia *Odczyt* przypisane do joe@contoso.com
-   Uprawnienia *Pełne* przypisane do mary\_kay@contoso.com

        // Create User Rights structure
        IPC_USER_RIGHTS ownerRightForOwner = {0};

        // Create rights
        LPCWSTR rgwszOwnerRights[1] = {IPC_GENERIC_ALL};

        // Assign values to members of Rights structure
        ownerRightForOwner.User.dwType = IPC_USER_TYPE_IPC;
        ownerRightForOwner.User.wszID = IPC_USER_ID_OWNER;
        ownerRightForOwner.rgwszRights = rgwszOwnerRights;
        ownerRightForOwner.cRights = 1;

        // Create User Rights structure for Joe with Read permissions
        IPC_USER_RIGHTS joeReadRight = {0};
        LPCWSTR rgwszReadRights[1] = {IPC_GENERIC_READ};

        // Assign values to members of Rights structure for Joe
        joeReadRight.User.dwType = IPC_USER_TYPE_EMAIL;
        joeReadRight.User.wszID = "joe@contoso.com";
        joeReadRight.rgwszRights = rgwszReadRights;
        joeReadRight.cRights = 1;

        // Create User Rights structure for Mary Kay with Full permissions
        IPC_USER_RIGHTS mary_kayFullRight = {0};
        LPCWSTR rgwszFullRights[1] = {IPC_GENERIC_ALL};

        // Assign values to members of Rights structure for Mary Kay
        mary_kayFullRight.User.dwType = IPC_USER_TYPE_EMAIL;
        mary_kayFullRight.User.wszID = L"mary_kay@contoso.com";
        mary_kayFullRight.rgwszRights = rgwszFullRights;
        mary_kayFullRight.cRights = 1;

        // Create User Rights List and assign the above rights
        size_t uNoOfUserRights = 3;
        PIPC_USER_RIGHTS_LIST pUserRightsList = NULL;
        pUserRightsList = reinterpret_cast<PIPC_USER_RIGHTS_LIST>
        (new BYTE[ sizeof(IPC_USER_RIGHTS_LIST) + uNoOfUserRights * sizeof(IPC_USER_RIGHTS)]);

        if(pUserRightsList == NULL)
        {
          // Handle error
        }

        // Assign values to members of Rights List structure for Joe and Mary Kay
        (*pUserRightsList).cbSize = sizeof(IPC_USER_RIGHTS_LIST);
        (*pUserRightsList).cUserRights = uNoOfUserRights;
        (*pUserRightsList).rgUserRights[0] = ownerRightForOwner;
        (*pUserRightsList).rgUserRights[1] = joeReadRight;
        (*pUserRightsList).rgUserRights[2] = mary_kayFullRight;

        // Set the Rights List property on the license via its handle
        // hLicense is a license handle created with IpcCreateLicenseFromScratch
        hr = IpcSetLicenseProperty(hLicense, FALSE, IPC_LI_USER_RIGHTS_LIST, pUserRightsList);

        if(FAILED(hr))
        {
          // Handle the error
        }



## <a name="related-topics"></a>Tematy pokrewne

- [Uwagi dla deweloperów](developer-notes.md)
- [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx)
- [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx)
