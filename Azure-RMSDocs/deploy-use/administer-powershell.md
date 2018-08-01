---
title: Administrowanie usługą Azure Rights Management przy użyciu programu PowerShell — AIP
description: Dowiedz się, jak użyć modułu programu PowerShell dla usługi Azure Rights Management (AADRM) w ramach usługi Azure Information Protection w celu administrowania usługą AADRM na potrzeby Twojej organizacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/13/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 06cfc6284be5547982e9ff06987e284a6ca43eeb
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39370853"
---
# <a name="administering-the-azure-rights-management-service-by-using-windows-powershell"></a>Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Czy do administrowania usługą Azure Rights Management dla usługi Azure Information Protection jest wymagane korzystanie z programu PowerShell? Nie konieczne może być w przypadku wszystkich konfiguracji może odbywać się w witrynie Azure portal lub portalu usługi Office 365. Jednak należy użyć programu PowerShell dla niektóre zaawansowane konfiguracje i można również wybrać przy użyciu programu PowerShell dla wiersza polecenia i skryptów.

Tabela przedstawiona w następnej sekcji zawiera niektóre scenariusze zaawansowanej konfiguracji, które korzystają z programu PowerShell. Jeśli konfigurację można również przeprowadzić bez użycia programu PowerShell, taka informacja także będzie umieszczona w tabeli.

Aby uzyskać pełną listę dostępnych poleceń cmdlet dla tego modułu i więcej informacji o każdym z nich, zobacz temat [Usługa AADRM](/powershell/module/aadrm/?view=azureipps#aadrm).

> [!NOTE]
> Aby zainstalować ten moduł programu PowerShell, zobacz [Instalowanie modułu AADRM programu PowerShell](install-powershell.md).

Oprócz tego modułu programu PowerShell po stronie usługi klient usługi Azure Information Protection zainstaluje dodatkowy moduł programu PowerShell, **AzureInformationProtection**. Ten moduł klienta obsługuje klasyfikację i ochronę wielu plików, dzięki czemu na przykład można zbiorczo chronić wszystkie pliki w folderze. Aby uzyskać więcej informacji, zobacz temat [Używanie środowiska PowerShell z klientem usługi Azure Information Protection](../rms-client/client-admin-guide-powershell.md) w podręczniku administratora.

## <a name="cmdlets-grouped-by-administration-task"></a>Polecenia cmdlet pogrupowane według zadań administracyjnych

|Jeśli chcesz...|...użyj następujących poleceń cmdlet|
|-------------------|------------------------------|
|Wykonać migrację z lokalnej usługi Rights Management (AD RMS lub Windows RMS) do usługi Azure Information Protection.|[Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd)<br /><br />[Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)|
|Połączyć lub rozłączyć się z usługą [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2.md)] dla Twojej organizacji.|[Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice)<br /><br />[Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice)|
|Wygenerować własny klucz dzierżawy i zarządzać nim — scenariusz dostarczania własnego klucza (BYOK).|[Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)<br /><br />[Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey)<br /><br />[Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys)|
|Aktywować lub dezaktywować usługę [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2.md)] dla Twojej organizacji.<br /><br />Te czynności te można również wykonać w portalach zarządzania. Aby uzyskać więcej informacji, zobacz artykuł [Aktywacja usługi Azure Rights Management](activate-service.md).|[Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm)<br /><br />[Disable-Aadrm](/powershell/aadrm/vlatest/disable-aadrm)|
|Zarządzaj witrynę śledzenia dokumentów dla usługi Azure Information Protection.|[Disable-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/disable-aadrmdocumenttrackingfeature)<br /><br />[Enable-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/enable-aadrmdocumenttrackingfeature)<br /><br />[Get-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/get-aadrmdocumenttrackingfeature)<br /><br />[Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/set-aadrmdonottrackusergroup)<br /><br />[Clear-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Clear-AadrmDoNotTrackUserGroup)<br /><br />[Get-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/get-AadrmDoNotTrackUserGroup)<br /><br />[Get-AadrmTrackingLog](/powershell/module/aadrm/Get-AadrmTrackingLog)<br /><br />[Get-AadrmDocumentLog](/powershell/module/aadrm/Get-AadrmDocumentLog)|
|Skonfigurować kontrolki dołączania we wdrożeniu etapowym usługi Azure Rights Management.|[Get-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/get-aadrmonboardingcontrolpolicy)<br /><br />[Set-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/set-aadrmonboardingcontrolpolicy)|
|Tworzenie szablonów usługi Rights Management i zarządzanie nimi w organizacji.<br /><br />Większość z tych czynności w witrynie Azure portal, mogą robić, mimo że program PowerShell oferuje więcej szczegółową kontrolę. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md).|[Add-AadrmTemplate](/powershell/aadrm/vlatest/add-aadrmtemplate)<br /><br />[Export-AadrmTemplate](/powershell/aadrm/vlatest/export-aadrmtemplate)<br /><br />[Get-AadrmTemplate](/powershell/aadrm/vlatest/get-aadrmtemplate)<br /><br />[Get-AadrmTemplateProperty](/powershell/aadrm/vlatest/get-aadrmtemplateproperty)<br /><br />[Import-AadrmTemplate](/powershell/aadrm/vlatest/import-aadrmtemplate)<br /><br />[New-AadrmRightsDefinition](/powershell/aadrm/vlatest/new-aadrmrightsdefinition)<br /><br />[Remove-AadrmTemplate](/powershell/aadrm/vlatest/remove-aadrmtemplate)<br /><br />[Set-AadrmTemplateProperty](/powershell/aadrm/vlatest/set-aadrmtemplateproperty)|
|Skonfigurować maksymalną liczbę dni, przez jaką zawartość chroniona przez organizację może być dostępna bez połączenia internetowego (okres ważności licencji użytkowania).|[Get-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/get-aadrmmaxuselicensevaliditytime)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime)|
|Zarządzać funkcją superużytkowników usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2.md)] dla Twojej organizacji.|[Enable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/enable-aadrmsuperuserfeature)<br /><br />[Disable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/disable-aadrmsuperuserfeature)<br /><br />[Add-AadrmSuperUser](/powershell/aadrm/vlatest/add-aadrmsuperuser)<br /><br />[Get-AadrmSuperUser](/powershell/aadrm/vlatest/get-aadrmsuperuser)<br /><br />[Remove-AadrmSuperUser](/powershell/aadrm/vlatest/remove-aadrmsuperuser)<br /><br />[Set-AadrmSuperUserGroup](/powershell/aadrm/vlatest/set-aadrmsuperusergroup)<br /><br />[Get-AadrmSuperUserGroup](/powershell/aadrm/vlatest/get-aadrmsuperusergroup)<br /><br />[Clear-AadrmSuperUserGroup](/powershell/aadrm/vlatest/clear-aadrmsuperusergroup)|
|Zarządzać użytkownikami i grupami, które mają uprawnienia do administrowania usługą [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2.md)] dla Twojej organizacji.|[Add-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/add-aadrmrolebasedadministrator)<br /><br />[Get-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/get-aadrmrolebasedadministrator)<br /><br />[Remove-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/remove-aadrmrolebasedadministrator)|
|Pobrać dziennik zadań administracyjnych usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2.md)] dla Twojej organizacji.|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Rejestrować i analizować dzienniki użycia dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2.md)].|[Get-AadrmUserLog](/powershell/aadrm/vlatest/get-aadrmuserlog)|
|Wyświetlić bieżącą konfigurację usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2.md)] dla Twojej organizacji.|[Get-AadrmConfiguration](/powershell/aadrm/vlatest/get-aadrmconfiguration)|
|Przeprowadzić migrację organizacji z usługi Azure Information Protection do lokalnego wdrożenia usług AD RMS.|[Set-AadrmMigrationUrl](/powershell/aadrm/vlatest/set-aadrmmigrationurl)<br /><br />[Get-AadrmMigrationUrl](/powershell/aadrm/vlatest/get-aadrmmigrationurl)|

