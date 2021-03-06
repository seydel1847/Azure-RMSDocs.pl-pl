---
title: Operacje związane z kluczem dzierżawy usługi Azure Information Protection
description: Identyfikowanie różnych poziomów kontroli i odpowiedzialności dostępnych w przypadku klucza dzierżawy usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 72607226c594e3b9d8b7fa203c38f9ee86ca4283
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53304812"
---
# <a name="operations-for-your-azure-information-protection-tenant-key"></a>Operacje związane z kluczem dzierżawy usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

W zależności od topologii klucza dzierżawy usługi Azure Information Protection będziesz mieć różne poziomy kontroli i odpowiedzialności dla klucza dzierżawy usługi Azure Information Protection. Są dwie topologie klucza **zarządzanych przez firmę Microsoft** i **zarządzanych przez klienta**.

Jeśli zarządzasz swoim kluczem dzierżawy w usłudze Azure Key Vault, taką sytuację najczęściej nazywa się rozwiązaniem Bring Your Own Key (BYOK). Aby uzyskać więcej informacji na temat tego scenariusza i jak wybrać odpowiednią topologię klucza dzierżawy, zobacz [planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](plan-implement-tenant-key.md).

W poniższej tabeli przedstawiono operacje, które można wykonać w zależności od topologii wybranej dla klucza dzierżawy usługi Azure Information Protection.

|Operacja cyklu życia|Zarządzany przez firmę Microsoft (domyślny)|Zarządzany przez klienta (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Odwołanie klucza dzierżawy|Nie (automatyczny)|Tak|
|Wymiana klucza dzierżawy|Tak|Tak|
|Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy|Nie|Tak|
|Eksport klucza dzierżawy|Tak|Nie|
|Reakcja na naruszenie zabezpieczeń|Tak|Tak|

Po zidentyfikowaniu wdrożonej topologii, udało Ci się wdrożyć, wybierz jedną z następujących linków, aby uzyskać więcej informacji o tych operacjach dla klucza dzierżawy usługi Azure Information Protection:

- [Klucz dzierżawy zarządzany przez firmę Microsoft](operations-microsoft-managed-tenant-key.md)
- [Klucz dzierżawy zarządzany przez klienta](operations-customer-managed-tenant-key.md)

Jednak jeśli chcesz utworzyć klucz dzierżawy usługi Azure Information Protection, importując zaufaną domenę publikacji (TPD) z usług zarządzania prawami dostępu w usłudze Active Directory, to ta operacja importu jest częścią [migracji z usług AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).  

