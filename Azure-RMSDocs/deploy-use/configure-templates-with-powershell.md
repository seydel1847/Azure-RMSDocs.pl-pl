---
title: "Środowisko PowerShell dla szablonów niestandardowych usługi Azure RMS — AIP"
description: "Wszystkie czynności, które można wykonać w klasycznym portalu Azure w zakresie tworzenia szablonów zarządzania uprawnieniami i zarządzania tymi szablonami, można wykonać z poziomu wiersza polecenia, korzystając z programu PowerShell. Ponadto istnieje możliwość eksportowania i importowania szablonów, dzięki czemu można kopiować szablony między dzierżawami i dokonywać edycji zbiorczej złożonych właściwości w szablonach, takich jak wielojęzyczne nazwy i opisy."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 8da24d00f6b6cb62bc745404e68e691b5afc2cb8
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Informacje dotyczące obsługi szablonów niestandardowych w programie PowerShell
<a id="powershell-reference-for-custom-templates" class="xliff"></a>

>*Dotyczy: Azure Information Protection, Office 365*

Wszystkie czynności, które można wykonać w klasycznym portalu Azure w zakresie tworzenia szablonów zarządzania uprawnieniami i zarządzania tymi szablonami, można wykonać z poziomu wiersza polecenia, korzystając z programu PowerShell. Ponadto istnieje możliwość eksportowania i importowania szablonów, dzięki czemu można kopiować szablony między dzierżawami i dokonywać edycji zbiorczej złożonych właściwości w szablonach, takich jak wielojęzyczne nazwy i opisy.

Można również używać funkcji eksportowania i importowania w celu tworzenia kopii zapasowych szablonów niestandardowych i ich przywracania. Najlepszym rozwiązaniem jest regularne tworzenie kopii zapasowych szablonów niestandardowych, dzięki któremu po ewentualnym przypadkowym wprowadzeniu zmiany można łatwo przywrócić poprzednią wersję szablonów.

> [!IMPORTANT]
> Aby użyć programu PowerShell do tworzenia szablonów usługi Azure Rights Management i zarządzania nimi, użytkownik musi dysponować [modułem Windows PowerShell dla usługi Azure RMS](https://go.microsoft.com/fwlink/?LinkId=257721) w wersji 2.0.0.0 lub nowszej.
> 
> Jeśli wcześniej zainstalowano ten moduł programu PowerShell, należy uruchomić następujące polecenie w oknie PowerShell, aby sprawdzić numer wersji: `(Get-Module aadrm -ListAvailable).Version`

Instrukcje instalacji znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).

Polecenia cmdlet używane do tworzenia szablonów i zarządzania nimi:

- [Add-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate)

- [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate)

- [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate)

- [Get-AadrmTemplateProperty](/powershell/module/aadrm/get-aadrmtemplateproperty)

- [Import-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate)

- [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition)

- [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate)

- [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty)



## Zobacz też
<a id="see-also" class="xliff"></a>
[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](configure-custom-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]