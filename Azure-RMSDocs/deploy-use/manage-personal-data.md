---
title: Zarządzanie danych osobowych w usłudze Azure Information Protection
description: Informacje o danych osobowych, który jest używany przez usługi Azure Information Protection i jak można wyświetlić, eksportować i usuń go.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 99a51862-83e9-4a1e-873a-a84ae1465f07
ms.reviewer: aashishr
ms.suite: ems
ms.openlocfilehash: f0fc9b01b042c3210abf69804d552607d92c5928
ms.sourcegitcommit: aae04d78ff301921a4e29ac23bd932fb24a83dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34444374"
---
# <a name="manage-personal-data-for-azure-information-protection"></a>Zarządzanie danych osobowych w usłudze Azure Information Protection

Podczas konfigurowania i używania usługi Azure Information Protection, adresy e-mail i adresów IP są przechowywane i używane przez usługę Azure Information Protection. Te dane osobiste można znaleźć w następujących elementów:

- Zasady usługi Azure Information Protection

- Szablony ochrony dla usługi Azure Rights Management

- Administratorzy i delegowani administratorzy dla usługi Azure Rights Management 

- Dzienniki administracji dla usługi Azure Rights Management

- Dzienniki użycia dla usługi Azure Rights Management

- Dzienniki śledzenia dokumentów

- Dzienniki użycia dla klienta usługi Azure Information Protection i klienta usługi RMS 


[!INCLUDE [GDPR-related guidance](../includes/gdpr-intro-sentence.md)]


## <a name="viewing-personal-data-that-azure-information-protection-uses"></a>Wyświetlanie danych osobowych, która używa usługi Azure Information Protection

Przy użyciu portalu Azure, administrator może określić adresy e-mail dla zakresu zasady i ustawienia ochrony w konfiguracji etykiety. Aby uzyskać więcej informacji, zobacz [sposobu konfigurowania zasad usługi Azure Information Protection dla konkretnych użytkowników przy użyciu zakres zasad](../deploy-use/configure-policy-scope.md) i [jak konfigurowanie etykiety pod kątem ochrony usługi Rights Management](configure-policy-protection.md). 

Dla etykiet, które są skonfigurowane w celu zastosowania ochrony usługi Azure Rights Management, adres e-mail można znaleźć w szablonach ochrony za pomocą poleceń cmdlet programu PowerShell z [AADRM module](/powershell/module/aadrm). Ten moduł programu PowerShell umożliwia również określić użytkowników według adresu e-mail jako administratora [superużytkowników](../deploy-use/configure-super-users.md), lub administratora dla usługi Azure Rights Management. 

W przypadku używania usługi Azure Information Protection do klasyfikowania i ochrony dokumentów i wiadomości e-mail, adresów e-mail i adresów IP użytkowników może być zapisany w plikach dziennika.


### <a name="protection-templates"></a>Szablony ochrony

Uruchom [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) polecenia cmdlet, aby uzyskać listę szablonów ochrony. Identyfikator szablonu można użyć, aby uzyskać szczegółowe informacje dotyczące określonego szablonu. `RightsDefinitions` Obiekt wyświetla dane osobowe, jeśli istnieje. 

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

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Administratorzy i delegowani administratorzy dla usługi Azure Rights Management

Uruchom [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperuser) polecenia cmdlet i [Get-AadrmRoleBasedAdministrator](/powershell/module/aadrm/get-aadrmrolebasedadministrator) polecenia cmdlet, aby wyświetlić użytkowników, którzy przypisano rolę administratora lub rolę administratora globalnego usługi Azure Rights Management Usługa. Dla użytkowników, którzy zostali przypisani dowolna z tych ról są wyświetlane ich adresów e-mail.


### <a name="administration-logs-for-the-azure-rights-management-service"></a>Dzienniki administracji dla usługi Azure Rights Management

Uruchom [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) polecenia cmdlet, aby pobrać dziennik czynności administracyjnych dla usługi Azure Rights Management, który chroni dane usługi Azure Information Protection. Ten dziennik zawiera dane osobowe w formie adresy e-mail i adresów IP. Dziennik jest w postaci zwykłego tekstu, a po pobraniu jej szczegóły określonego administratora można przeszukiwać w trybie offline.

Przykład:
```
PS C:\Users> Get-AadrmAdminLog -Path '.\Desktop\admin.log' -FromTime 4/1/2018 -ToTime 4/30/2018 -Verbose
The Rights Management administration log was successfully generated and can be found at .\Desktop\admin.log.
```

### <a name="usage-logs-for-the-azure-rights-management-service"></a>Dzienniki użycia dla usługi Azure Rights Management
Uruchom [polecenia Get-AadrmUserLog](/powershell/module/aadrm/get-aadrmuserlog) polecenia cmdlet, aby pobrać dziennik akcji przez użytkownika końcowego, które korzystają z usługi Azure Rights Management. Ta usługa chroni dane usługi Azure Information Protection. Dziennik może zawierać danych osobowych w formie adresy e-mail i adresów IP. Dziennik jest w postaci zwykłego tekstu, a po pobraniu jej szczegóły określonego administratora można przeszukiwać w trybie offline.

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

Uruchom [Get-AadrmDocumentLog](/powershell/module/aadrm/get-aadrmdocumentlog) polecenia cmdlet, aby pobrać informacje z lokacji o określonych użytkowników śledzenia dokumentów. Aby uzyskać śledzenia informacje związane z dziennikami dokumentu, należy użyć [Get-AadrmTrackingLog](/powershell/module/aadrm/get-aadrmtrackinglog?view=azureipps) polecenia cmdlet.

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

Brak nie wyszukiwania przez identyfikator obiektu. Jednak użytkownik nie jest ograniczana przez `-UserEmail` parametr i musisz podać adres e-mail nie musi być częścią dzierżawy. Jeśli podany adres e-mail jest przechowywany w dowolnym miejscu w dziennikach śledzenia dokumentów, wpis śledzenia dokumentów jest zwracany w danych wyjściowych polecenia cmdlet.

### <a name="usage-logs-for-the-azure-information-protection-client-and-rms-client"></a>Dzienniki użycia dla klienta usługi Azure Information Protection i klienta usługi RMS

Gdy etykiety i chroni są stosowane do dokumentów i wiadomości e-mail, adresów e-mail i adresów IP mogą być przechowywane w plikach dziennika na komputerze użytkownika w następujących lokalizacjach:

- Dla klienta usługi Azure Information Protection: %localappdata%\Microsoft\MSIP\Logs

- Klienta usługi RMS: %localappdata%\Microsoft\MSIPC\msip\Logs

Ponadto klienta usługi Azure Information Protection rejestruje tej zapewnionej w lokalnym dzienniku zdarzeń systemu Windows **Dzienniki aplikacji i usług** > **usługi Azure Information Protection**.

Po uruchomieniu klienta Azure Information Protection skanera danych osobowych są zapisywane w %localappdata%\Microsoft\MSIP\Scanner\Reports komputer z systemem Windows Server z uruchomioną skanera.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="securing-and-controlling-access-to-personal-information"></a>Zabezpieczanie i kontrolowanie dostępu do danych osobowych
Dane osobowe, które możesz wyświetlać i określać w portalu Azure jest dostępny tylko dla użytkowników, którzy zostali przypisani jedną z następujących [ról administratora w usłudze Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
- **Administrator ochrona informacji**

- **Administrator zabezpieczeń**

- **Administrator globalny / Administrator firmy**

Dane osobowe, które możesz wyświetlać i określać przy użyciu modułu AADRM jest dostępny tylko dla użytkowników, którzy zostali przypisani **administratora ochrony informacji** roli lub **administratora globalnego / Administrator firmy** ról z usługi Azure Active Directory lub rolę administratora globalnego usługi Azure Rights Management.  

## <a name="updating-personal-data"></a>Aktualizowanie danych osobowych

Można aktualizować adresy e-mail dla zakresu zasady i ustawienia ochrony w zasadach usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz [sposobu konfigurowania zasad usługi Azure Information Protection dla konkretnych użytkowników przy użyciu zakres zasad](../deploy-use/configure-policy-scope.md) i [jak konfigurowanie etykiety pod kątem ochrony usługi Rights Management](configure-policy-protection.md). 

Ustawienia ochrony można zaktualizować te same informacje przy użyciu poleceń cmdlet programu PowerShell z [AADRM module](/powershell/module/aadrm).

Nie można zaktualizować adresy e-mail dla administratorów i administratorów delegowanych. Zamiast tego usuń określone konto użytkownika, a następnie dodaj konto użytkownika z adresem e-mail zaktualizowane. 

### <a name="protection-templates"></a>Szablony ochrony

Uruchom [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) polecenia cmdlet, aby zaktualizować szablon ochrony. Ponieważ dane osobowe w ramach `RightsDefinitions` właściwość, należy również używać [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) polecenia cmdlet, aby utworzyć obiekt RightsDefinitions zaktualizowane informacje, a następnie użyj RightsDefinitions obiekt z `Set-AadrmTemplateProperty` polecenia cmdlet.

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Administratorzy i delegowani administratorzy dla usługi Azure Rights Management

Kiedy należy zaktualizować adres e-mail użytkownika nadrzędnego:

1. Użyj [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser) Aby usunąć stary adres e-mail i użytkownika.

2. Użyj [Add-AadrmSuperUser](/powershell/module/aadrm/Add-AadrmSuperUser) , aby dodać użytkowników i nowy adres e-mail.

Jeśli konieczne jest zaktualizowanie adresu e-mail dla administratora delegowanego:

1. Użyj [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator) Aby usunąć stary adres e-mail i użytkownika.

2. Użyj [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Add-AadrmRoleBasedAdministrator) , aby dodać użytkowników i nowy adres e-mail.

## <a name="deleting-personal-data"></a>Usuwanie danych osobowych
Możesz usunąć adresy e-mail dla zakresu zasady i ustawienia ochrony w zasadach usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz [sposobu konfigurowania zasad usługi Azure Information Protection dla konkretnych użytkowników przy użyciu zakres zasad](../deploy-use/configure-policy-scope.md) i [jak konfigurowanie etykiety pod kątem ochrony usługi Rights Management](configure-policy-protection.md). 

Ustawienia ochrony można usunąć tych samych informacji za pomocą poleceń cmdlet programu PowerShell z [AADRM module](/powershell/module/aadrm).

Aby usunąć adresy e-mail dla administratorów i administratorów delegowanych, należy usunąć tych użytkowników przy użyciu [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser) polecenia cmdlet i [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator). 

Do usunięcia danych osobowych w dziennikach śledzenia dokumentów, dzienniki administracji lub dzienników użycia usługi Azure Rights Management, użyj poniższej sekcji, aby wywołać żądanie z Microsoft Support.

Aby usunąć danych osobowych w plikach dziennika klienta i dzienniki skanera, które są przechowywane na komputerach, użyj standardowych narzędzi systemu Windows do usuwania plików lub danych osobowych w plikach. 

### <a name="to-delete-personal-data-with-microsoft-support"></a>Aby usunąć dane osobowe z Support firmy Microsoft

Poniższe trzy kroki umożliwia żądanie, że Microsoft powoduje usunięcie danych osobowych w dokumencie śledzenia dzienniki, dzienniki administracji lub dzienników użycia usługi Azure Rights Management. 

**Krok 1: Żądanie usunięcia inicjowania**
[kontakt z działem pomocy technicznej firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support) na otwieranie sprawy pomocy technicznej usługi Azure Information Protection wniosku o usunięcie danych z dzierżawą. Musisz udowodnić, są przeznaczone dla administratorów dzierżawy usługi Azure Information Protection i zrozumieć, że ten proces może potrwać kilka dni, aby potwierdzić. Podczas przesyłania żądania, konieczne będzie podanie dodatkowych informacji, w zależności od danych, który musi zostać usunięty.

- Aby usunąć dziennika administracyjnej, należy podać **Data zakończenia**. Wszystkie dzienniki administratora aż do tej daty zakończenia zostaną usunięte.
- Aby usunąć dzienniki użycia, należy podać **Data zakończenia**. Użycie wszystkich dzienników do daty zakończenia zostaną usunięte.
- Aby usunąć dzienniki śledzenia dokumentów, należy podać **konto użytkownika**. Wszystkie dokumentu śledzenia informacji dotyczących konto użytkownika zostanie usunięte.

Usunięcie tych danych jest trwałe. Nie istnieje sposób odzyskiwania danych po przetworzeniu żądanie usunięcia. Zaleca się, że administratorzy wyeksportować wymagane dane przed przesłaniem żądanie usunięcia.

**Krok 2: Oczekiwanie na weryfikację** firma Microsoft zweryfikuje, że Twoje żądanie, aby usunąć jednego lub większej liczby dzienników jest uzasadnione. Ten proces może potrwać maksymalnie pięć dni roboczych.

**Krok 3: Pobierz potwierdzenie usunięcia** usług obsługi klienta firmy Microsoft (CSS) będzie wysyłać wiadomość e-mail z potwierdzeniem, że dane zostały usunięte. 

## <a name="exporting-personal-data"></a>Eksportowanie danych osobowych
Korzystając z polecenia cmdlet programu AADRM PowerShell, dane osobowe jest udostępniana do wyszukiwania i eksportowanie jako obiekt programu PowerShell. Obiekt programu PowerShell może być przekonwertowany do formatu JSON i zapisane przy użyciu `ConvertTo-Json` polecenia cmdlet.

## <a name="restricting-the-use-of-personal-data-for-profiling-or-marketing-without-consent"></a>Ograniczanie użycia danych osobowych dla profilowania lub marketingu bez zgody
Usługa Azure Information Protection następuje firmy Microsoft [zasadami zachowania poufności informacji](https://privacy.microsoft.com/privacystatement) dla profilowania lub marketingu oparte na danych osobowych.

## <a name="auditing-and-reporting"></a>Inspekcja i raportowanie
Tylko użytkownicy, którzy zostali przypisani [uprawnienia administratora](#securing-and-controlling-access-to-personal-information) można użyć modułu AADRM wyszukiwania i eksportowania danych osobowych. Te operacje są rejestrowane w dzienniku administracji, które można pobrać.

Akcje usuwania żądania obsługi działa jako funkcję inspekcji i raportowania śladu akcje wykonywane przez firmę Microsoft. Po usunięciu usunięte dane nie będą dostępne dla funkcji wyszukiwania i eksportu, a administrator można to sprawdzić za pomocą polecenia cmdlet Get w AADRM module.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
