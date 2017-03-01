---
title: "Środowisko PowerShell dla szablonów niestandardowych usługi Azure RMS — AIP"
description: "Wszystkie czynności, które można wykonać w klasycznym portalu Azure w zakresie tworzenia szablonów zarządzania uprawnieniami i zarządzania tymi szablonami, można wykonać z poziomu wiersza polecenia, korzystając z programu PowerShell. Ponadto istnieje możliwość eksportowania i importowania szablonów, dzięki czemu można kopiować szablony między dzierżawami i dokonywać edycji zbiorczej złożonych właściwości w szablonach, takich jak wielojęzyczne nazwy i opisy."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: fac6f2180c8b108ea237cb36d29058b4907db18a
ms.lasthandoff: 02/24/2017


---



# <a name="powershell-reference-for-custom-templates"></a>Informacje dotyczące obsługi szablonów niestandardowych w programie PowerShell

>*Dotyczy: Azure Information Protection, Office 365*

Wszystkie czynności, które można wykonać w klasycznym portalu Azure w zakresie tworzenia szablonów zarządzania uprawnieniami i zarządzania tymi szablonami, można wykonać z poziomu wiersza polecenia, korzystając z programu PowerShell. Ponadto istnieje możliwość eksportowania i importowania szablonów, dzięki czemu można kopiować szablony między dzierżawami i dokonywać edycji zbiorczej złożonych właściwości w szablonach, takich jak wielojęzyczne nazwy i opisy.

Można również używać funkcji eksportowania i importowania w celu tworzenia kopii zapasowych szablonów niestandardowych i ich przywracania. Najlepszym rozwiązaniem jest regularne tworzenie kopii zapasowych szablonów niestandardowych, dzięki któremu po ewentualnym przypadkowym wprowadzeniu zmiany można łatwo przywrócić poprzednią wersję szablonów.

> [!IMPORTANT]
> Aby użyć programu Windows PowerShell do tworzenia szablonów usługi Azure Rights Management i zarządzania nimi, użytkownik musi dysponować [modułem Windows PowerShell dla usługi Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721) w wersji 2.0.0.0 lub nowszej.
> 
> Jeśli wcześniej zainstalowano ten moduł programu PowerShell, należy uruchomić następujące polecenie w oknie PowerShell, aby sprawdzić numer wersji: `(Get-Module aadrm -ListAvailable).Version`

Instrukcje instalacji znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).

Polecenia cmdlet używane do tworzenia szablonów i zarządzania nimi:

-   [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Remove-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)



## <a name="see-also"></a>Zobacz też
[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](configure-custom-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
