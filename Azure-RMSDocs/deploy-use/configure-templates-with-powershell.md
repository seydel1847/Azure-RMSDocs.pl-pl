---
title: "Programu PowerShell na potrzeby ochrony szablony — usługi Azure Information Protection"
description: "Wszystko, co można zrobić w portalu Azure do tworzenia szablonów i zarządzania nimi ochrony należy z poziomu wiersza polecenia przy użyciu programu PowerShell. Ponadto istnieje możliwość eksportowania i importowania szablonów, dzięki czemu można kopiować szablony między dzierżawami i dokonywać edycji zbiorczej złożonych właściwości w szablonach, takich jak wielojęzyczne nazwy i opisy."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 051144562b1c26a22953f6e83a41b4902404fd2f
ms.sourcegitcommit: 85250f5ea80c2ee22197058ff2f65a79503b0f0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/24/2018
---
# <a name="powershell-reference-for-protection-templates"></a>Dokumentacja programu PowerShell dla szablonów ochrony

>*Dotyczy: Azure Information Protection, Office 365*

Ustawienia ochrony dla usługi Azure Information Protection są zapisywane w szablonach ochrony. Wszystko, co można zrobić w portalu Azure do tworzenia i zarządzania ustawieniami ochrony można wykonać z poziomu wiersza polecenia przez przy użyciu programu PowerShell. 

Ponadto można eksportować i importować szablony ochrony przez użytkownika. Te dwie akcje umożliwiają ochronę przed kopiowaniem szablony między dzierżawami lub zbiorcze zmiany właściwości złożonych, takich jak wielojęzyczne nazwy i opisy.

Użytkownik może również używać funkcji eksportowania i importowania kopii zapasowej i przywracanie szablonów ochrony. Najlepszym rozwiązaniem regularne tworzenie kopii zapasowych szablonów. Następnie Jeśli wprowadzisz zmiany w ustawieniach ochrony, których nie ma można łatwo przywrócić poprzednią wersję.

Aby uzyskać instrukcje instalacji, zobacz [Instalowanie modułu programu PowerShell AADRM](install-powershell.md).

Polecenia cmdlet, który obsługuje tworzenie szablonów i zarządzania nimi ochrony:

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
