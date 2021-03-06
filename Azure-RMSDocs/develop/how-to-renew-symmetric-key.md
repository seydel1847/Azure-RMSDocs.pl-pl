---
title: Odnawianie klucza symetrycznego w usłudze Azure Information Protection
description: W tym artykule opisano proces odnawiania klucza symetrycznego w usłudze Azure Information Protection.
keywords: ''
author: bryanla
manager: mbaldwin
ms.author: bryanla
ms.date: 03/27/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: a0b8c8f0-6ed5-48bb-8155-ac4f319ec178
ms.openlocfilehash: 7d0a6bc4c99108bff009846952e2aa569340531b
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071356"
---
# <a name="how-to-renew-the-symmetric-key-in-azure-information-protection"></a>Instrukcje: Odnawianie klucza symetrycznego w usłudze Azure Information Protection

**Klucz symetryczny** jest kluczem tajnym, który służy do szyfrowania i odszyfrowywania wiadomości w szyfrowaniu kluczem symetrycznym.  

W usłudze Azure Active Directory (Azure AD) podczas tworzenia obiektu jednostki usługi w celu reprezentowania aplikacji proces generuje również 256-bitowy klucz symetryczny służący do weryfikowania aplikacji. Ten klucz symetryczny domyślnie jest ważny przez rok. 

Poniższe kroki pokazują sposób odnawiania klucza symetrycznego. 

## <a name="prerequisites"></a>Wymagania wstępne

* Moduł usługi Azure Active Directory (Azure AD) dla programu PowerShell musi być zainstalowany zgodnie ze wskazówkami podanymi w [dokumentacji programu PowerShell usługi Azure AD](https://docs.microsoft.com/powershell/msonline/).


## <a name="renewing-the-symmetric-key-after-expiry"></a>Odnawianie klucza symetrycznego po wygaśnięciu

Nie trzeba tworzyć nowej jednostki usługi, gdy klucz symetryczny skojarzony z aplikacją utracił ważność. Zamiast tego można użyć [poleceń cmdlet programu PowerShell](https://docs.microsoft.com/powershell/module/msonline) udostępnianych w witrynie Microsoft Online Services (MSol), aby wystawić nowy klucz symetryczny dla istniejącej jednostki usługi.

Aby zilustrować ten proces, załóżmy, że już utworzono nową jednostkę usługi za pomocą polecenia [`New-MsolServicePrincipal`](https://docs.microsoft.com/powershell/msonline/v1/new-msolserviceprincipalcredential).

```
New-MsolServicePrincipalCredential -ServicePrincipalName "SupportExampleApp"
```

Proces tworzenia tworzy klucz symetryczny i identyfikator **AppPrincipalId**, jak pokazano poniżej.

```
The following symmetric key was created as one was not supplied
ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

DisplayName : SupportExampleApp
ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963}
ObjectId : 0ee53770-ec86-409e-8939-6d8239880518
AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963
TrustedForDelegation : False
AccountEnabled : True
Addresses : []
KeyType : Symmetric
KeyId : acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe
StartDate : 3/22/2017 3:27:53 PM
EndDate : 3/22/2018 3:27:53 PM
Usage : Verify
```

Ten klucz symetryczny wygasa w dniu 22/3/2018 o 3:27:53. Aby użyć jednostki usługi po tym terminie, musisz odnowić klucz symetryczny. Aby to zrobić, należy użyć [ `New-MsolServicePrincipalCredential` ](https://docs.microsoft.com/powershell/msonline/v1/new-msolserviceprincipalcredential) polecenia. 

```
New-MsolServicePrincipalCredential -AppPrincipalId 7d9c1f38-600c-4b4d-8249-22427f016963
```

Spowoduje to utworzenie nowego klucza symetrycznego dla określonego identyfikatora **AppPrincipalId**.

```
The following symmetric key was created as one was not supplied ON8YYaMYNmwSfMX625Ei4eC6N1zaeCxbc219W090v28-
```
Za pomocą polecenia [`GetMsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/get-msolserviceprincipalcredential) można sprawdzić, czy nowy klucz symetryczny jest skojarzony z poprawną jednostką usługi. Zwróć uwagę, że to polecenie wyświetla wszystkie klucze, aktualnie skojarzona z jednostką usługi.

```
Get-MsolServicePrincipalCredential -AppPrincipalId 7d9c1f38-600c-4b4d-8249-22427f016963 -ReturnKeyValues $true

Type : Symmetric
Value :
KeyId : c1ac145f-e899-4c90-8a02-2cef40054fc5
StartDate : 3/24/2017 10:11:07 PM
EndDate : 3/24/2018 10:11:07 PM
Usage : Verify

Type : Symmetric
Value :
KeyId : acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe
StartDate : 3/22/2017 3:27:53 PM
EndDate : 3/22/2018 3:27:53 PM
Usage : Verify
```

Po upewnieniu się, że klucz symetryczny jest faktycznie skojarzony z właściwą jednostką usługi, należy zaktualizować parametry uwierzytelniania jednostki usługi przy użyciu nowego klucza. 

Następnie można usunąć stary klucz symetryczny za pomocą polecenia [`Remove-MsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/remove-msolserviceprincipalcredential) i sprawdzić przy użyciu polecenia `Get-MsolServicePrincipalCredential`, czy klucz został usunięty.

```
Remove-MsolServicePrincipalCredential -KeyId acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe -ObjectId 0ee53770-ec86-409e-8939-6d8239880518
```

## <a name="related-topics"></a>Tematy pokrewne

* [Instrukcje: Włączanie aplikacji usługi do pracy z usługą RMS oparte na chmurze](how-to-use-file-api-with-aadrm-cloud.md)
* [Dokumentacja modułu usługi Azure Active Directory (MSOnline) dla programu PowerShell](https://docs.microsoft.com/powershell/msonline/)
