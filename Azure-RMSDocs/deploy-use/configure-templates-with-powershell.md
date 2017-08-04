---
title: "Środowisko PowerShell dla szablonów niestandardowych usługi Azure RMS — AIP"
description: "Szablony zarządzania prawami dostępu w wszystko, co można zrobić w portalu Azure, aby utworzyć i zarządzać nimi, można skorzystać z wiersza polecenia przy użyciu programu PowerShell. Ponadto istnieje możliwość eksportowania i importowania szablonów, dzięki czemu można kopiować szablony między dzierżawami i dokonywać edycji zbiorczej złożonych właściwości w szablonach, takich jak wielojęzyczne nazwy i opisy."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: c3b1662275b051ea75dcc104c4f09b5db53dbe3e
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2017
---
# <a name="powershell-reference-for-custom-templates"></a>Informacje dotyczące obsługi szablonów niestandardowych w programie PowerShell

>*Dotyczy: Azure Information Protection, Office 365*

Wszystko, co można zrobić w portalu Azure, aby utworzyć szablony i zarządzać nimi, należy w wierszu polecenia przy użyciu programu PowerShell. Ponadto istnieje możliwość eksportowania i importowania szablonów, dzięki czemu można kopiować szablony między dzierżawami i dokonywać edycji zbiorczej złożonych właściwości w szablonach, takich jak wielojęzyczne nazwy i opisy.

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



## <a name="see-also"></a>Zobacz też
[Konfigurowanie i zarządzanie nimi szablonów usługi Azure Information Protection](configure-policy-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]