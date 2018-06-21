---
title: Operacje związane z kluczem dzierżawy usługi Azure Information Protection
description: Identyfikowanie różnych poziomów kontroli i odpowiedzialności dostępnych w przypadku klucza dzierżawy usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/22/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f459504f43c8e361e36832b19011f93d1cbaccc4
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
ms.locfileid: "30205799"
---
# <a name="operations-for-your-azure-information-protection-tenant-key"></a>Operacje związane z kluczem dzierżawy usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

W zależności od topologii klucza dzierżawy usługi Azure Information Protection należy mieć różne poziomy kontroli i odpowiedzialności za klucz dzierżawy usługi Azure Information Protection. Są dwie topologie klucza **zarządzany przez firmę Microsoft** i **zarządzany przez klienta**.

Jeśli zarządzasz swoim kluczem dzierżawy w usłudze Azure Key Vault, taką sytuację najczęściej nazywa się rozwiązaniem Bring Your Own Key (BYOK). Aby uzyskać więcej informacji na temat tego scenariusza i jak wybrać topologię klucza dzierżawy, zobacz [planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md).

W poniższej tabeli przedstawiono operacje, które mogą wykonywać, w zależności od topologii wybranej dla klucza dzierżawy usługi Azure Information Protection.

|Operacja cyklu życia|Zarządzany przez firmę Microsoft (domyślny)|Zarządzany przez klienta (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Odwołanie klucza dzierżawy|Nie (automatyczny)|Tak|
|Wymiana klucza dzierżawy|Tak|Tak|
|Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy|Nie|Tak|
|Eksport klucza dzierżawy|Tak|Nie|
|Reakcja na naruszenie zabezpieczeń|Tak|Tak|

Po zidentyfikowaniu wdrożonej topologii został zaimplementowany, wybierz jedną z poniższych linków, aby uzyskać więcej informacji o tych operacjach dla klucza dzierżawy usługi Azure Information Protection:

- [Klucz dzierżawy zarządzany przez firmę Microsoft](operations-microsoft-managed-tenant-key.md)
- [Klucz dzierżawy zarządzany przez klienta](operations-customer-managed-tenant-key.md)

Jednak jeśli chcesz utworzyć klucz dzierżawy usługi Azure Information Protection, importując zaufaną domenę publikacji (TPD) z usług zarządzania prawami dostępu w usłudze Active Directory, to ta operacja importu jest częścią [migracji z usług AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
