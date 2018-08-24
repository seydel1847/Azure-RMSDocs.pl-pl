---
title: Program PowerShell dla szablonów ochrona — Azure Information Protection
description: Wszystko, co można zrobić w witrynie Azure portal, aby utworzyć i zarządzać szablonami ochrony, możesz zrobić z wiersza polecenia przy użyciu programu PowerShell. Ponadto istnieje możliwość eksportowania i importowania szablonów, dzięki czemu można kopiować szablony między dzierżawami i dokonywać edycji zbiorczej złożonych właściwości w szablonach, takich jak wielojęzyczne nazwy i opisy.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 200a8ab379a6e29fcbe59b60eacaf40ac47569c4
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42805663"
---
# <a name="powershell-reference-for-protection-templates"></a>Dokumentacja programu PowerShell dla szablonów ochrony

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Ustawienia ochrony dla usługi Azure Information Protection są zapisywane w szablonach ochrony. Wszystko, co można zrobić w witrynie Azure portal do tworzenia i zarządzania ustawieniami ochrony zrobić z wiersza polecenia, za pomocą programu PowerShell. 

Ponadto można eksportować i importować szablony ochrony przez użytkownika. Te dwie akcje umożliwiają ochronę przed kopiowaniem szablony między dzierżawami lub zbiorczej edycji właściwości złożonych, takich jak wielojęzyczne nazwy i opisy.

Możesz również użyć eksportowania i importowania kopii zapasowej i przywracanie szablonów ochrony. Najlepszym rozwiązaniem jest regularnie wykonywać kopie zapasowe szablonów. Następnie Jeśli wprowadzisz zmiany do ustawień ochrony, które nie był przeznaczony można łatwo przywrócić poprzednią wersję.

Aby uzyskać instrukcje dotyczące instalacji, zobacz [Instalowanie modułu AADRM programu PowerShell](install-powershell.md).

Polecenia cmdlet, które obsługują tworzenie i Zarządzanie szablonami ochrony:

- [Add-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate)

- [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate)

- [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate)

- [Get-AadrmTemplateProperty](/powershell/module/aadrm/get-aadrmtemplateproperty)

- [Import-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate)

- [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition)

- [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate)

- [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty)



## <a name="see-also"></a>Zobacz też
[Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](configure-policy-templates.md)

