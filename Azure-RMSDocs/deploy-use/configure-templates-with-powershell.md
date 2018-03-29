---
title: Programu PowerShell na potrzeby ochrony szablony — usługi Azure Information Protection
description: Wszystko, co można zrobić w portalu Azure do tworzenia szablonów i zarządzania nimi ochrony należy z poziomu wiersza polecenia przy użyciu programu PowerShell. Ponadto istnieje możliwość eksportowania i importowania szablonów, dzięki czemu można kopiować szablony między dzierżawami i dokonywać edycji zbiorczej złożonych właściwości w szablonach, takich jak wielojęzyczne nazwy i opisy.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 30dbfbe2cd9ef7d8acd89a9a76cd1108d7c03ab2
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="powershell-reference-for-protection-templates"></a>Dokumentacja programu PowerShell dla szablonów ochrony

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

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
