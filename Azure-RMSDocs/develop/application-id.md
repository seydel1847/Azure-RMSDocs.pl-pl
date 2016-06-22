---
# required metadata

title: "Porady: uzyskiwanie identyfikatora aplikacji Azure | Azure RMS"
description: Tworzenie aplikacji z obsługą usługi RMS za pomocą zestawu Microsoft Rights Management SDK 4.2 wymaga podpisania umowy z zespołem usługi RMS.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0fe9dc-bc91-4018-b28d-2db293a3eaa2
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Porady: uzyskiwanie identyfikatora aplikacji Azure

Tworzenie aplikacji z obsługą usługi RMS za pomocą zestawu Microsoft Rights Management SDK 4.2 wymaga podpisania umowy z zespołem usługi RMS.

## Przegląd

Tworzenie i wydanie aplikacji obsługującej usługi RMS za pomocą zestawu MS RMS SDK 4.2 wymaga także podpisania umowy dotyczącej korzystania z usług z zespołem usługi RMS. Umowa ta, nazywana również umową licencyjną usługi Rights Management (RMLA), zawiera wytyczne odnośnie honorowania umowy dotyczącej ochrony danych, której będziesz przestrzegać w imieniu użytkownika i/lub właściciela zawartości przez zachowanie (zgodność z zasadami biznesowymi) Twojej aplikacji. Umowa twórcy aplikacji obsługującej usługę RMS z zespołem usługi RMS będzie egzekwowana przez istnienie „identyfikatora aplikacji Azure”, który reprezentuje tę umowę i umożliwia aplikacji łączenie się z usługą uwierzytelniania Azure AD.

## Proces

Wykonaj następujące kroki, aby utworzyć identyfikator aplikacji i podpisać umowę użytkowania z zespołem usługi RMS.

-   Utwórz identyfikator aplikacji, postępując zgodnie z instrukcjami podanymi w temacie [Jak utworzyć identyfikator aplikacji na platformie Azure](https://msdn.microsoft.com/en-us/library/azure/dn132599.aspx).
-   Napisz do zespołu usługi RMS, aby zainicjować proces zawierania umowy RMLA, wysyłając swój identyfikator aplikacji na adres <askipteam@microsoft.com>.
-   Podpisz umowę RMLA i odeślij ją do zespołu usługi RMS.
-   Teraz, gdy masz już podpisaną umowę RMLA, przekaż swój identyfikator aplikacji podczas wywoływania biblioteki uwierzytelniania za pomocą parametru *clientID*.

    A oto, jak wygląda wywołanie uwierzytelniania przedstawione w temacie [Przykłady kodu dla systemu iOS/OS X](ios-os-x-code-examples.md):


    // Retrieve token using ADAL
        [context acquireTokenWithResource:authenticationParameters.resource
                                 clientId:appClientId
                              redirectUri:redirectURI
                                   userId:authenticationParameters.userId
                          completionBlock:^(ADAuthenticationResult *result)



**Uwaga**: jeśli zespół usługi RMS nie otrzyma podpisanej umowy RMLA w ciągu 60 dni, uwierzytelnianie Twojej aplikacji w systemie uwierzytelniania platformy Azure zostanie zablokowane.

 

 

 


<!--HONumber=Apr16_HO4-->


