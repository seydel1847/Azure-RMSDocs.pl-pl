---
title: Zarządzanie danymi osobowymi usługi Azure Information Protection
description: Informacje o danych osobowych, które jest używane przez usługi Azure Information Protection i jak mogą wyświetlać, eksportowanie i usuń go.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 99a51862-83e9-4a1e-873a-a84ae1465f07
ms.reviewer: aashishr
ms.suite: ems
ms.openlocfilehash: 4e44796d3bd2fdf1fd2f0c39cc759f16d87267a1
ms.sourcegitcommit: db60fe8f74ffaa4f6ffbf5defb22efc476c28312
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53319418"
---
# <a name="manage-personal-data-for-azure-information-protection"></a>Zarządzanie danymi osobowymi usługi Azure Information Protection

Podczas konfigurowania i korzystania z usługi Azure Information Protection, adresy e-mail i adresów IP są przechowywane i używane przez usługę Azure Information Protection. Tych danych osobowych można znaleźć w następujących elementów:

- Zasady usługi Azure Information Protection

- Szablony ochrony dla usługi Azure Rights Management

- Administratorzy i Administratorzy delegowani dla usługi Azure Rights Management 

- Dzienniki administracji dla usługi Azure Rights Management

- Dzienniki użycia dla usługi Azure Rights Management

- Dzienniki śledzenia dokumentów

- Dzienniki użycia klienta usługi Azure Information Protection i klienta usługi RMS 


[!INCLUDE [GDPR-related guidance](./includes/gdpr-intro-sentence.md)]


## <a name="viewing-personal-data-that-azure-information-protection-uses"></a>Wyświetlanie danych osobowych, które korzysta z usługi Azure Information Protection

W witrynie Azure portal, administrator może określić adresy e-mail dla zasad o określonym zakresie i ustawienia ochrony w ramach konfiguracji etykiety. Aby uzyskać więcej informacji, zobacz [do konfigurowania zasad usługi Azure Information Protection dla konkretnych użytkowników przy użyciu zasad o określonym zakresie](configure-policy-scope.md) i [sposobu konfigurowania etykiety dla ochrony usługi Rights Management](configure-policy-protection.md). 

Dla etykiet, które są skonfigurowane do stosowania ochrony usługi Azure Rights Management, adresu e-mail można także znaleźć w szablonach ochrony za pomocą poleceń cmdlet programu PowerShell z [AADRM module](/powershell/module/aadrm). Ten moduł programu PowerShell umożliwia również określanie użytkowników według adresu e-mail jako administratora [superużytkowników](configure-super-users.md), lub administrator usługi Azure Rights Management. 

W przypadku usługi Azure Information Protection do klasyfikowania i ochrony dokumentów i wiadomości e-mail, adresy e-mail i adresy IP użytkowników może być zapisany w plikach dziennika.


### <a name="protection-templates"></a>Szablony ochrony

Uruchom [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) polecenia cmdlet, aby uzyskać listę szablonów ochrony. Identyfikator szablonu można użyć, aby uzyskać szczegółowe informacje z określonego szablonu. `RightsDefinitions` Obiektu wyświetli dane osobowe, jeśli istnieje. 

Przykład:
```
PS C:\Users> Get-AadrmTemplate -TemplateId fcdbbc36-1f48-48ca-887f-265ee1268f51 | select *


TemplateId              : fcdbbc36-1f48-48ca-887f-265ee1268f51
Names                   : {1033 -> Confidential}
Descriptions            : {1033 -> This data includes sensitive business information. Exposing this data to
                          unauthorized users may cause damage to the business. Examples for Confidential information
                          are employee information, individual customer projects or contracts and sales account data.}
Status                  : Archived
RightsDefinitions       : {admin@aip500.onmicrosoft.com -> VIEW, VIEWRIGHTSDATA, EDIT, DOCEDIT, PRINT, EXTRACT,
                          REPLY, REPLYALL, FORWARD, EXPORT, EDITRIGHTSDATA, OBJMODEL, OWNER,
                          AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@aip500.onmicrosoft.com -> VIEW,
                          VIEWRIGHTSDATA, EDIT, DOCEDIT, PRINT, EXTRACT, REPLY, REPLYALL, FORWARD, EXPORT,
                          EDITRIGHTSDATA, OBJMODEL, OWNER, admin2@aip500.onmicrosoft.com -> VIEW, VIEWRIGHTSDATA, EDIT,
                          DOCEDIT, PRINT, EXTRACT, REPLY, REPLYALL, FORWARD, EXPORT, EDITRIGHTSDATA, OBJMODEL, OWNER}
ContentExpirationDate   : 1/1/0001 12:00:00 AM
ContentValidityDuration : 0
ContentExpirationOption : Never
LicenseValidityDuration : 7
ReadOnly                : False
LastModifiedTimeStamp   : 1/26/2018 6:17:00 PM
ScopedIdentities        : {}
EnableInLegacyApps      : False
LabelId                 :
```

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Administratorzy i Administratorzy delegowani dla usługi Azure Rights Management

Uruchom [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperuser) polecenia cmdlet i [Get-AadrmRoleBasedAdministrator](/powershell/module/aadrm/get-aadrmrolebasedadministrator) polecenia cmdlet, aby wyświetlić użytkowników, którzy przypisano rolę administratora lub rolę administratora globalnego usługi Azure Rights Management Usługa. Dla użytkowników, którzy zostali przypisani jednej z tych ról ich adresy e-mail są wyświetlane.


### <a name="administration-logs-for-the-azure-rights-management-service"></a>Dzienniki administracji dla usługi Azure Rights Management

Uruchom [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) polecenia cmdlet, aby pobrać dziennik akcji administracyjnych dla usługi Azure Rights Management, co zapewnia ochronę danych usługi Azure Information Protection. Ten dziennik zawiera danych osobowych w formie adresy e-mail i adresów IP. Dziennik jest w postaci zwykłego tekstu, a po jej pobraniu szczegóły określonego administratora mogą być wyszukiwane w trybie offline.

Przykład:
```
PS C:\Users> Get-AadrmAdminLog -Path '.\Desktop\admin.log' -FromTime 4/1/2018 -ToTime 4/30/2018 -Verbose
The Rights Management administration log was successfully generated and can be found at .\Desktop\admin.log.
```

### <a name="usage-logs-for-the-azure-rights-management-service"></a>Dzienniki użycia dla usługi Azure Rights Management
Uruchom [Get-AadrmUserLog](/powershell/module/aadrm/get-aadrmuserlog) polecenia cmdlet, aby pobrać dziennik akcji przez użytkownika końcowego, które korzystają z usługi Azure Rights Management. Ta usługa pozwala chronić dane usługi Azure Information Protection. Dziennik może zawierać danych osobowych w formie adresy e-mail i adresów IP. Dziennik jest w postaci zwykłego tekstu, a po jej pobraniu szczegóły określonego administratora mogą być wyszukiwane w trybie offline.

Przykład:
```
PS C:\Users> Get-AadrmUserLog -Path '.\Desktop\' -FromDate 4/1/2018 -ToDate 4/30/2018 -NumberOfThreads 10
Acquiring access to your user log…
Downloading the log for 2018-04-01.
Downloading the log for 2018-04-03.
Downloading the log for 2018-04-06.
Downloading the log for 2018-04-09.
Downloading the log for 2018-04-10.
Downloaded the log for 2018-04-01. The log is available at .\Desktop\rmslog-2018-04-01.log.
Downloaded the log for 2018-04-03. The log is available at .\Desktop\rmslog-2018-04-03.log.
Downloaded the log for 2018-04-06. The log is available at .\Desktop\rmslog-2018-04-06.log.
Downloaded the log for 2018-04-09. The log is available at .\Desktop\rmslog-2018-04-09.log.
Downloaded the log for 2018-04-10. The log is available at .\Desktop\rmslog-2018-04-10.log.
Downloading the log for 2018-04-12.
Downloading the log for 2018-04-13.
Downloading the log for 2018-04-14.
Downloading the log for 2018-04-16.
Downloading the log for 2018-04-18.
Downloaded the log for 2018-04-12. The log is available at .\Desktop\rmslog-2018-04-12.log.
Downloaded the log for 2018-04-13. The log is available at .\Desktop\rmslog-2018-04-13.log.
Downloaded the log for 2018-04-14. The log is available at .\Desktop\rmslog-2018-04-14.log.
Downloaded the log for 2018-04-16. The log is available at .\Desktop\rmslog-2018-04-16.log.
Downloaded the log for 2018-04-18. The log is available at .\Desktop\rmslog-2018-04-18.log.
Downloading the log for 2018-04-24.
Downloaded the log for 2018-04-24. The log is available at .\Desktop\rmslog-2018-04-24.log.
```   

### <a name="document-tracking-logs"></a>Dzienniki śledzenia dokumentów

Uruchom [Get AadrmDocumentLog](/powershell/module/aadrm/get-aadrmdocumentlog) polecenie cmdlet do pobierania informacji z witryny o określonym użytkowniku śledzenia dokumentów. Aby uzyskać śledzenie informacje związane z dziennikami dokumentu, należy użyć [Get AadrmTrackingLog](/powershell/module/aadrm/get-aadrmtrackinglog?view=azureipps) polecenia cmdlet.

Przykład:
```
PS C:\Users> Get-AadrmDocumentLog -UserEmail "admin@aip500.onmicrosoft.com"


ContentId             : 6326fcb2-c465-4c24-a7f6-1cace7a9cb6f
Issuer                : admin@aip500.onmicrosoft.com
Owner                 : admin@aip500.onmicrosoft.com
ContentName           :
CreatedTime           : 3/6/2018 10:24:00 PM
Recipients            : {
                        PrimaryEmail: johndoe@contoso.com
                        DisplayName: JOHNDOE@CONTOSO.COM
                        UserType: External,
                        PrimaryEmail: alice@contoso0110.onmicrosoft.com
                        DisplayName: ALICE@CONTOSO0110.ONMICROSOFT.COM
                        UserType: External
                        }
TemplateId            :
PolicyExpires         :
EULDuration           :
SendRegistrationEmail : True
NotificationInfo      : Enabled: False
                        DeniedOnly: False
                        Culture:
                        TimeZoneId:
                        TimeZoneOffset: 0
                        TimeZoneDaylightName:
                        TimeZoneStandardName:

RevocationInfo        : Revoked: False
                        RevokedTime:
                        RevokedBy:


PS C:\Users> Get-AadrmTrackingLog -UserEmail "admin@aip500.onmicrosoft.com"

ContentId            : 6326fcb2-c465-4c24-a7f6-1cace7a9cb6f
Issuer               : admin@aip500.onmicrosoft.com
RequestTime          : 3/6/2018 10:45:57 PM
RequesterType        : External
RequesterEmail       : johndoe@contoso.com
RequesterDisplayName : johndoe@contoso.com
RequesterLocation    : IP: 167.220.1.54
                       Country: US
                       City: redmond
                       Position: 47.6812453974602,-122.120736471666

Rights               : {VIEW,OBJMODEL}
Successful           : False
IsHiddenInfo         : False
```

Brak bez wyszukiwania przez identyfikator obiektu. Jednak nie jest ograniczona przez `-UserEmail` parametru i adres e-mail, należy podać nie musi być częścią Twojej dzierżawy. Jeśli określony adres e-mail jest przechowywany w dowolnym miejscu w dziennikach śledzenia dokumentów, wpis śledzenia dokumentów jest zwracany w danych wyjściowych polecenia cmdlet.

### <a name="usage-logs-for-the-azure-information-protection-client-and-rms-client"></a>Dzienniki użycia klienta usługi Azure Information Protection i klienta usługi RMS

Stosowania etykiet i ochrony dokumentów i wiadomości e-mail, adresy e-mail i adresów IP mogą być przechowywane w plikach dziennika na komputerze użytkownika w następujących lokalizacjach:

- Dla klienta usługi Azure Information Protection: %localappdata%\Microsoft\MSIP\Logs

- Klienta usługi RMS: %localappdata%\Microsoft\MSIPC\msip\Logs

Ponadto klient usługi Azure Information Protection rejestruje tych danych osobowych w lokalnym dzienniku zdarzeń Windows **Dzienniki aplikacji i usług** > **usługi Azure Information Protection**.

Po uruchomieniu przez klienta usługi Azure Information Protection skaner dane osobowe są zapisywane %localappdata%\Microsoft\MSIP\Scanner\Reports na komputerze systemu Windows Server, który działa skaner.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-hybrid-note.md)]

## <a name="securing-and-controlling-access-to-personal-information"></a>Zabezpieczanie i kontrolowanie dostępu do danych osobowych
Dane osobowe, wyświetlać i określić w witrynie Azure portal jest dostępna tylko dla użytkowników, którzy zostali przypisani jedną z następujących [ról administratora w usłudze Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
- **Administrator usługi Information Protection**

- **Administrator zabezpieczeń**

- **Administrator globalny / Administrator firmy**

Dane osobowe, wyświetlać i określić przy użyciu modułu AADRM jest dostępny tylko dla użytkowników, którzy zostali przypisani **Administrator usługi Information Protection** roli lub **administratora globalnego / firmowego administratora** ról z usługi Azure Active Directory lub rolę administratora globalnego usługi Azure Rights Management.  

## <a name="updating-personal-data"></a>Aktualizowanie danych osobowych

Możesz zaktualizować adresy e-mail dla zasad o określonym zakresie i ustawienia ochrony w zasadach usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz [do konfigurowania zasad usługi Azure Information Protection dla konkretnych użytkowników przy użyciu zasad o określonym zakresie](configure-policy-scope.md) i [sposobu konfigurowania etykiety dla ochrony usługi Rights Management](configure-policy-protection.md). 

Dla ustawienia ochrony, można zaktualizować te same informacje przy użyciu poleceń cmdlet programu PowerShell z [AADRM module](/powershell/module/aadrm).

Nie można zaktualizować adresy e-mail dla administratorów i Administratorzy delegowani. Zamiast tego usuń określonego konta użytkownika, a następnie dodaj konto użytkownika za pomocą zaktualizowany adres e-mail. 

### <a name="protection-templates"></a>Szablony ochrony

Uruchom [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) polecenia cmdlet, aby zaktualizować szablon ochrony. Ponieważ dane osobowe w ramach `RightsDefinitions` właściwość, należy również używać [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) polecenia cmdlet, aby utworzyć obiekt RightsDefinitions przy użyciu zaktualizowanych informacji i użyć RightsDefinitions obiekt z `Set-AadrmTemplateProperty` polecenia cmdlet.

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Administratorzy i Administratorzy delegowani dla usługi Azure Rights Management

Kiedy należy aktualizować adres e-mail administratora:

1. Użyj [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser) do usuwania użytkownika i stary adres e-mail.

2. Użyj [Add-AadrmSuperUser](/powershell/module/aadrm/Add-AadrmSuperUser) do dodawania użytkowników i nowy adres e-mail.

Kiedy należy aktualizować adres e-mail dla administratora delegowanego:

1. Użyj [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator) do usuwania użytkownika i stary adres e-mail.

2. Użyj [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Add-AadrmRoleBasedAdministrator) do dodawania użytkowników i nowy adres e-mail.

## <a name="deleting-personal-data"></a>Usuwanie danych osobowych
Adresy e-mail dla zasad o określonym zakresie i ustawienia ochrony w zasadach usługi Azure Information Protection, można usunąć. Aby uzyskać więcej informacji, zobacz [do konfigurowania zasad usługi Azure Information Protection dla konkretnych użytkowników przy użyciu zasad o określonym zakresie](configure-policy-scope.md) i [sposobu konfigurowania etykiety dla ochrony usługi Rights Management](configure-policy-protection.md). 

Dla ustawienia ochrony, możesz usunąć te same informacje przy użyciu poleceń cmdlet programu PowerShell z [AADRM module](/powershell/module/aadrm).

Aby usunąć adresy e-mail dla administratorów i Administratorzy delegowani, należy usunąć tych użytkowników za pomocą [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser) polecenia cmdlet i [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator). 

Aby usunąć dane osobowe w dziennikach śledzenia dokumentów, dzienniki administracji lub dzienników użycia usługi Azure Rights Management, następująca sekcja służy Aby zgłosić żądanie z Microsoft Support.

Aby usunąć danych osobowych w plikach dziennika klienta i dzienników skanera, które są przechowywane na komputerach, należy użyć żadnych standardowych narzędzi Windows można usunąć pliki lub dane osobowe w ramach plików. 

### <a name="to-delete-personal-data-with-microsoft-support"></a>Aby usunąć dane osobowe z Microsoft Support

Użyj następujących trzech kroków do żądania, że Microsoft powoduje usunięcie danych osobowych w dokumencie śledzenia dzienników, dzienniki administracji lub dzienników użycia usługi Azure Rights Management. 

**Krok 1: Żądanie usunięcia inicjowania**
[się z pomocą techniczną firmy Microsoft](information-support.md#to-contact-microsoft-support) otworzyć zgłoszenie do pomocy technicznej usługi Azure Information Protection z żądaniem usunięcie danych z Twojej dzierżawy. Musisz udowodnić, że jesteś administratorem dzierżawy usługi Azure Information Protection i zrozumieć, że ten proces trwa kilka dni, aby potwierdzić. Podczas przesyłania żądania, konieczne będzie podanie dodatkowych informacji, w zależności od danych, który musi zostać usunięty.

- Aby usunąć z dziennikiem administracji, należy podać **Data zakończenia**. Wszystkie dzienniki administratora do momentu usunięcia tej daty zakończenia.
- Aby usunąć dzienniki użycia, należy podać **Data zakończenia**. Dzienniki użycia wszystkich aż do daty zakończenia zostaną usunięte.
- Aby usunąć dzienniki śledzenia dokumentów, zapewnienia **konto użytkownika**. Wszystkich dokumentów śledzenie informacji dotyczących konto użytkownika zostaną usunięte.

Usunięcie tych danych jest trwałe. Istnieje sposób odzyskiwania danych po przetworzeniu żądania usunięcia. Zaleca się, że administratorzy wyeksportować wymagane dane przed przesłaniem żądania usunięcia.

**Krok 2: Oczekiwanie na weryfikację** firma Microsoft zweryfikuje, że żądanie można usunąć jednego lub więcej dzienników jest uzasadnione. Ten proces może potrwać do pięciu dni roboczych.

**Krok 3: Uzyskaj potwierdzenie usunięcia** usług pomocy technicznej firmy Microsoft (CSS) będzie wysyłać wiadomość e-mail z potwierdzeniem, że dane zostały usunięte. 

## <a name="exporting-personal-data"></a>Eksportowanie danych osobowych
Korzystając z polecenia cmdlet programu PowerShell usługi AADRM, dane osobowe staje się dostępny do wyszukiwania i eksportowanie jako obiekt programu PowerShell. Obiekt programu PowerShell może być przekonwertowany do formatu JSON i zapisywane przy użyciu `ConvertTo-Json` polecenia cmdlet.

## <a name="restricting-the-use-of-personal-data-for-profiling-or-marketing-without-consent"></a>Ograniczenie użytkowania danych osobowych dla profilowania i marketingowych bez ich zgody
Usługa Azure Information Protection jest zgodna firmy Microsoft [postanowienia dotyczące prywatności](https://privacy.microsoft.com/privacystatement) marketingowych lub profilowania opartego na danych osobowych.

## <a name="auditing-and-reporting"></a>Inspekcja i raportowanie
Tylko użytkownicy, którzy zostali przypisani [uprawnienia administratora](#securing-and-controlling-access-to-personal-information) służy do wyszukiwania i eksportowanie danych osobowych w module AADRM. Te operacje są rejestrowane w dzienniku administracyjną, którą można pobrać.

Akcje usuwania żądania pomocy technicznej, działa jako funkcję inspekcji i raportowanie dziennik akcji wykonywanych przez firmę Microsoft. Po usunięciu usuniętych danych nie będzie dostępna w przypadku wyszukiwania i eksportu, a administrator można to sprawdzić za pomocą polecenia cmdlet Get w module AADRM.

