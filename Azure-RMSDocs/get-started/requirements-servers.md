---
title: "Serwery obsługujące ochronę danych za pomocą usługi RMS — AIP"
description: "Identyfikowanie produktów serwera lokalnego, które mogą korzystać z usługi Azure Rights Management w ramach usługi Azure Information Protection przy użyciu łącznika usługi Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/22/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 87e887bb121b3d92065153a5d264767ef87d517b
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="on-premises-servers-that-support-azure-rights-management-data-protection"></a>Serwery lokalne obsługujące ochronę danych usługi Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

Następujące produkty serwera lokalnego są obsługiwane przez usługę Azure Information Protection podczas używania łącznika usługi Azure Rights Management. Ten łącznik działa jako interfejs komunikacji (przekaźnik) między serwerami lokalnymi i usługą Azure Rights Management, która służy usłudze Azure Information Protection do ochrony wiadomości e-mail i dokumentów pakietu Office. 

Aby użyć tego łącznika, należy skonfigurować synchronizację katalogów między lasami usługi Active Directory a usługą Azure Active Directory.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików**:

    -   Windows Server 2016

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Ponieważ serwery plików z systemem Windows Server 2008 R2 nie mają wbudowanej akcji zadania zarządzania plikami, która pozwala na zastosowanie ochrony przy użyciu usługi Rights Management, w tym scenariuszu nie można używać łącznika usługi Rights Management. Można jednak użyć pliku klasyfikacji infrastruktury i usługi Azure RMS w tych systemach operacyjnych w przypadku konfigurowania niestandardowego zadania zarządzania plikami, aby uruchomić plik wykonywalny lub skrypt służący do ochrony plików przy użyciu usługi Azure RMS. Przykładem jest skrypt programu Windows PowerShell, który używa [poleceń cmdlet usługi Azure Information Protection](/powershell/azureinformationprotection/vlatest/aip).
    > 
    > Można również używać tych poleceń cmdlet na serwerach z nowszymi wersjami systemu Windows Server, ponieważ umożliwiają one ochronę wszystkich typów plików. Łącznik usługi RMS chroni tylko pliki pakietu Office. Dokładne instrukcje można znaleźć w temacie [Ochrona za pomocą usługi RMS z użyciem infrastruktury klasyfikacji plików (FCI)](../rms-client/configure-fci.md).

Łącznik usługi Rights Management jest obsługiwany w systemach Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 i Windows Server 2008 R2.

Aby uzyskać więcej informacji o sposobie konfigurowania łącznika usługi Rights Management na wymienionych serwerach lokalnych, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

## <a name="next-steps"></a>Następne kroki
Aby sprawdzić pozostałe wymagania, zobacz [Wymagania dotyczące usługi Azure Rights Management](requirements-azure-rms.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]