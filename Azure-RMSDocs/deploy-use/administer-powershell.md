---
title: "Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell | Azure Information Protection"
description: "Dowiedz się, jak użyć modułu programu PowerShell dla usługi Azure Rights Management (AADRM) w ramach usługi Azure Information Protection w celu administrowania usługą AADRM na potrzeby Twojej organizacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 16d6a8a00db28c23fd650a1b8beba00333ba6ea4
ms.openlocfilehash: f9aa0d5910ba4868878ae54c446793bfc031d3c2


---

# <a name="administering-the-azure-rights-management-service-by-using-windows-powershell"></a>Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell

>*Dotyczy: Azure Information Protection, Office 365*

Czy do administrowania usługą Azure Rights Management dla usługi Azure Information Protection jest wymagane korzystanie z programu PowerShell? Taka potrzeba może nie zachodzić, jeśli jesteś administratorem globalnym, a jedynym ustawieniem konfiguracji wymaganym dla tej usługi jest jej aktywowanie (lub dezaktywowanie) oraz skonfigurowanie szablonów usługi Rights Management.

Jednak w razie konieczności dokonania bardziej zaawansowanych ustawień konfiguracji należy użyć programu PowerShell. Może to być również niezbędne, gdy nie jesteś administratorem globalnym, ale masz uprawnienia do administrowania usługą przyznane przez administratora globalnego. Programu PowerShell można również używać w celu efektywniejszego korzystania z wiersza polecenia i skryptów.

Tabela przedstawiona w następnej sekcji zawiera niektóre scenariusze zaawansowanej konfiguracji, które korzystają z programu PowerShell. Jeśli konfigurację można również przeprowadzić bez użycia programu PowerShell, taka informacja także będzie umieszczona w tabeli.

Aby uzyskać pełną listę dostępnych poleceń cmdlet i więcej informacji o każdym z nich, zobacz [Azure Rights Management Cmdlets](http://msdn.microsoft.com/library/azure/dn629398.aspx) (Polecenia cmdlet usługi Azure Rights Management).

> [!NOTE]
> Aby zainstalować ten moduł programu PowerShell, zobacz artykuł [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).

Oprócz tego modułu programu PowerShell po stronie usługi klient usługi Azure Information Protection zainstaluje dodatkowy moduł programu PowerShell, **AzureInformationProtection**. Ten moduł klienta obsługuje klasyfikację i ochronę wielu plików, dzięki czemu na przykład można zbiorczo chronić wszystkie pliki w folderze. Aby uzyskać więcej informacji, zobacz temat [Używanie środowiska PowerShell z klientem usługi Azure Information Protection](../rms-client/client-admin-guide-powershell.md) w podręczniku administratora.

## <a name="cmdlets-grouped-by-administration-task"></a>Polecenia cmdlet pogrupowane według zadań administracyjnych

|Jeśli chcesz...|...użyj następujących poleceń cmdlet|
|-------------------|------------------------------|
|Wykonać migrację z lokalnej usługi Rights Management (AD RMS lub Windows RMS) do usługi Azure Information Protection.|[Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|Połączyć lub rozłączyć się z usługą [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Wygenerować własny klucz dzierżawy i zarządzać nim — scenariusz dostarczania własnego klucza (BYOK).|[Use-AadrmKeyVaultKey](https://msdn.microsoft.com/library/azure/mt759829.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Aktywować lub dezaktywować usługę [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.<br /><br />Te czynności te można również wykonać w portalach zarządzania. Aby uzyskać więcej informacji, zobacz artykuł [Aktywacja usługi Azure Rights Management](activate-service.md).|[Enable-Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Wyłączyć lub włączyć witrynę śledzenia dokumentów dla usługi Azure Information Protection.|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Enable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Skonfigurować kontrolki dołączania we wdrożeniu etapowym usługi Azure Rights Management.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Tworzenie szablonów usługi Rights Management i zarządzanie nimi w organizacji.<br /><br />Większość z tych czynności można również wykonać w klasycznym portalu Azure, ale program PowerShell zapewnia nad nimi bardziej precyzyjną kontrolę. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management](configure-custom-templates.md).|[Add-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Export-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Import-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[New-AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Remove-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Set-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Skonfigurować maksymalną liczbę dni, przez jaką zawartość chroniona przez organizację może być dostępna bez połączenia internetowego (okres ważności licencji użytkowania).|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|Zarządzać funkcją superużytkowników usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Add-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Remove-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629405.aspx)<br /><br />[Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx)<br /><br />[Get-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653942.aspx)<br /><br />[Clear-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653944.aspx)|
|Zarządzać użytkownikami i grupami, które mają uprawnienia do administrowania usługą [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Add-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Remove-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Pobrać dziennik zadań administracyjnych usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Rejestrować i analizować dzienniki użycia dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|[Get-AadrmUserLog](https://msdn.microsoft.com/library/azure/mt653941.aspx)|
|Wyświetlić bieżącą konfigurację usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Przeprowadzić migrację organizacji z usługi Azure Information Protection do lokalnego wdrożenia usług AD RMS.|[Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]





<!--HONumber=Feb17_HO2-->


