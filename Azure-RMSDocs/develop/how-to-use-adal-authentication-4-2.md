---
title: "Konfigurowanie uwierzytelniania usługi RMS za pomocą Portalu Azure | Azure RMS"
description: "Zawiera opis procesu uwierzytelniania przy użyciu biblioteki ADAL"
keywords: uwierzytelnianie, RMS, ADAL
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2680b399-febb-4bd6-b844-ac3d1e69aca4
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 0bea42f0de08dc521828ccfe3cbff85e32c74aca


---

# <a name="how-to-use-azure-portal-to-configure-for-rms-authentication"></a>Instrukcje: konfigurowanie uwierzytelniania usługi RMS za pomocą Portalu Azure

Uwierzytelnianie w usłudze Azure RMS dla aplikacji z użyciem biblioteki Azure Active Directory Authentication Library (ADAL).

Użycie tej metody wymaga, aby aplikacja zarządzała własnym uwierzytelnianiem OAuth. W przypadku tego podejścia klient RMS wykonuje wywołanie zwrotne określone w aplikacji, gdy jest wymagane uwierzytelnienie.

## <a name="configure-via-azure-portal"></a>Konfigurowanie za pomocą Portalu Azure
Najpierw wykonaj czynności przedstawione w tym przewodniku konfigurowania za pomocą Portalu Azure [Konfigurowanie usługi Azure RMS na potrzeby uwierzytelniania ADAL](adal-auth.md). Skopiuj i zapisz *identyfikator klienta* oraz *identyfikator URI przekierowania* z tego procesu do użycia w przyszłości.

## <a name="code-sample"></a>Przykładowy kod
Poniżej przedstawiono fragment kodu z większego przykładu kodu klientów urządzeń przenośnych umożliwiający włączenie uwierzytelniania opartego na bibliotece Azure ADAL. Aby uzyskać więcej informacji, zobacz pełny przykład w temacie [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)

       /**
       * Instantiates a new rms authentication callback.
       *
       * @param parentActivity the parent activity
       * @throws NoSuchAlgorithmException the no such algorithm exception
       * @throws InvalidKeySpecException the invalid key spec exception
       * @throws UnsupportedEncodingException the unsupported encoding exception
       */

       public MsipcAuthenticationCallback(Activity parentActivity) throws NoSuchAlgorithmException, InvalidKeySpecException, UnsupportedEncodingException
       {
         mParentActivity = parentActivity;
         setADALKeyStore();

         /**
         * Note: Following values of are client_id and redirect_uri are for demo purpose only.
         * Your values will come from the preceeding Azure Portal process.
         */
         mClientId = "com.microsoft.rightsmanagement.sampleapp";
         mRedirectURI = mClientId + "://authorize";
       }


## <a name="related-topics"></a>Tematy pokrewne

- [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)
- [Konfigurowanie usługi Azure RMS na potrzeby uwierzytelniania ADAL](adal-auth.md)



<!--HONumber=Nov16_HO2-->


