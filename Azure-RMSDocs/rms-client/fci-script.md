---
title: Skrypt programu PowerShell dla usługi Azure RMS i infrastruktury klasyfikacji plików — AIP
description: Przykładowy skrypt do skopiowania i zmodyfikowania zgodnie z opisem podanym w instrukcjach dotyczących ochrony za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików w systemie Windows Server.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ae6d8d0f-4ebc-43fe-a1f6-26b690fd83d0
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9a59be70117f4ed2dd0a0c3bb14bc9fa6f0c530d
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305118"
---
# <a name="windows-powershell-script-for-azure-rms-protection-by-using-file-server-resource-manager-fci"></a>Skrypt programu Windows PowerShell na potrzeby ochrony za pomocą usług Azure RMS przy użyciu infrastruktury klasyfikacji plików Menedżera zasobów serwera plików

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), system Windows Server 2016, Windows Server 2012, Windows Server 2012 R2*

Ta strona zawiera przykładowy skrypt do skopiowania i zmodyfikowania zgodnie z opisem podanym w artykule [Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików w systemie Windows Server](configure-fci.md).

Ten skrypt wymaga co najmniej wersji **1.3.155.2** dla modułu usługi AzureInformationProtection. Uruchom następujące polecenie, aby sprawdzić wersję: `(Get-Module AzureInformationProtection -ListAvailable).Version` 

*&#42;&#42;Zastrzeżenie&#42;&#42;: Ten przykładowy skrypt nie jest obsługiwana w ramach usług ani programów pomocy technicznej standard firmy Microsoft. Ten przykładowy skrypt jest dostarczany, w jakim jest bez żadnego rodzaju gwarancji.*

```
<#
.SYNOPSIS 
     Helper script to protect all file types using the Azure Rights Management service and FCI.
.DESCRIPTION
     Protect files with the Azure Rights Management service and Windows Server FCI, using an RMS template ID and AzureInformationProtection module minimum version 1.3.155.2.   
#>
param(
            [Parameter(Mandatory = $false)]
            [ValidateScript({ If($_ -eq "") {$true} else { if (Test-Path -Path $_ -PathType Leaf) {$true} else {throw "Can't find file specified"} } })]
            [string]$File,

            [Parameter(Mandatory = $false)]
            [string]$TemplateID,

            [Parameter(Mandatory = $false)]
            [string]$OwnerMail,

            [Parameter(Mandatory = $false)]
            [string]$AppPrincipalId = "<enter your AppPrincipalId here>",

            [Parameter(Mandatory = $false)]
            [string]$SymmetricKey = "<enter your key here>",

            [Parameter(Mandatory = $false)]
            [string]$BposTenantId = "<enter your BposTenantId here>"
) 

# script information
[String] $Script:Version = 'version 3.4' 
[String] $Script:Name = "RMS-Protect-FCI.ps1"

#global working variables
[switch] $Script:isScriptProcess = $False # Controls the script process. If false, the script gracefully stops running.

#**Functions (general helper)***************************************
function Get-ScriptName(){ 

    return $MyInvocation.ScriptName.Substring($MyInvocation.ScriptName.LastIndexOf('\') + 1, $MyInvocation.ScriptName.LastIndexOf('.') - $MyInvocation.ScriptName.LastIndexOf('\') - 1)
}

#**Functions (script specific)**************************************

function Check-Module{

    param ([String]$Module = $(Throw "Module name not specified"))

    [bool]$isResult = $False

    #try to load the module
    if ((get-module -list -name $Module) -ne $nil)
        {

            $isResult = $True
        } else 
        
        {
            $isResult = $False
        } 

    return $isResult
}

function Protect-File ($ffile, $ftemplateId, $fownermail) {

    [bool] $returnValue = $false
    try {
        If ($OwnerMail -eq $null -or $OwnerMail -eq "") {
            $protectReturn = Protect-RMSFile -File $ffile -InPlace -DoNotPersistEncryptionKey All -TemplateID $ftemplateId
            $returnValue = $true
            Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId")
        } else {
            $protectReturn = Protect-RMSFile -File $ffile -InPlace -DoNotPersistEncryptionKey All -TemplateID $ftemplateId -OwnerEmail $fownermail
            $returnValue = $true
            Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId, set Owner: $fownermail")
        }
    } catch {
        Write-Host ( "ERROR" + "During protection of file: $ffile with Template: $ftemplateId")
            }
    return $returnValue
}

function Set-RMSConnection ($fappId, $fkey, $fbposId) {

    [bool] $returnValue = $false
    try {
               Set-RMSServerAuthentication -AppPrincipalId $fappId -Key $fkey -BposTenantId $fbposId
        Write-Host ("Information: " + "Connected to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId")
#       Get-RMSTemplate -Force
        $returnValue = $true
    } catch {
        Write-Host ("ERROR" + "During connection to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId")

    }
    return $returnValue
}

#**Main Script (Script)*********************************************
Write-Host ("-== " + $Script:Name + " " + $Version + " ==-")

$Script:isScriptProcess = $True

# Validate Azure RMS connection by checking the module and then connection
if ($Script:isScriptProcess) {
        if (Check-Module -Module AzureInformationProtection){
        $Script:isScriptProcess = $True
    } else {

        Write-Host ("The AzureInformationProtection module is not loaded") -foregroundcolor "yellow" -backgroundcolor "black"           
        $Script:isScriptProcess = $False
    }
}

if ($Script:isScriptProcess) {
    #Write-Host ("Try to connect to Azure RMS with AppId: $AppPrincipalId and BPOSID: $BposTenantId" )  
    if (Set-RMSConnection $AppPrincipalId $SymmetricKey $BposTenantId) {
        Write-Host ("Connected to Azure RMS")

    } else {
        Write-Host ("Couldn't connect to Azure RMS") -foregroundcolor "yellow" -backgroundcolor "black"
        $Script:isScriptProcess = $False
    }
}

#  Start working loop
if ($Script:isScriptProcess) {
    if ( !(($File -eq $null) -or ($File -eq "")) ) {
        if (!(Protect-File -ffile $File -ftemplateId $TemplateID -fownermail $OwnerMail)) {
            $Script:isScriptProcess = $False           
        }
    }
}

# Closing
if (!$Script:isScriptProcess) { Write-Host "ERROR occurred during script process" -foregroundcolor "red" -backgroundcolor "black"}
write-host ("-== " + $Script:Name + " " + $Version + "  ==-")
if (!$Script:isScriptProcess) { exit(-1) } else {exit(0)}
```

---

Powrót do tematu [Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików w systemie Windows Server](configure-fci.md).
