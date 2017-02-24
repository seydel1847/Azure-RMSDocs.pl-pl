---
title: "Operacje związane z kluczem dzierżawy usługi Azure Information Protection"
description: "Identyfikowanie różnych poziomów kontroli i odpowiedzialności dostępnych w przypadku klucza dzierżawy usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 0895050d1bc0528f9ab230bdeac9e2a3ee787b31


---

# <a name="operations-for-your-azure-information-protection-tenant-key"></a>Operacje związane z kluczem dzierżawy usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

W zależności od topologii klucza dzierżawy (zarządzany przez firmę Microsoft lub zarządzany przez klienta) będziesz mieć różne poziomy kontroli i odpowiedzialności dla klucza dzierżawy usługi Azure Information Protection po jego wdrożeniu.

Jeśli zarządzasz swoim kluczem dzierżawy w usłudze Azure Key Vault, taką sytuację najczęściej nazywa się rozwiązaniem Bring Your Own Key (BYOK). Aby uzyskać więcej informacji na temat tego scenariusza i dowiedzieć się, jak wybrać odpowiednią topologię klucza dzierżawy, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](../plan-design/plan-implement-tenant-key.md).

W poniższej tabeli przedstawiono operacje, które można wykonać w zależności od topologii wybranej dla klucza dzierżawy usługi Azure Information Protection.

|Operacja cyklu życia|Zarządzany przez firmę Microsoft (domyślny)|Zarządzany przez klienta (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Odwołanie klucza dzierżawy|Nie (automatyczny)|Tak|
|Ponowne tworzenie klucza dzierżawy|Tak|Tak|
|Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy|Nie|Tak|
|Eksport klucza dzierżawy|Tak|Nie|
|Reakcja na naruszenie zabezpieczeń|Tak|Tak|

Po zidentyfikowaniu wdrożonej topologii wybierz jeden z poniższych elementów, aby uzyskać więcej informacji o tych operacjach dla swojego klucza dzierżawy usługi Azure Information Protection:


- [Klucz dzierżawy zarządzany przez firmę Microsoft](operations-microsoft-managed-tenant-key.md)
- [Klucz dzierżawy zarządzany przez klienta](operations-customer-managed-tenant-key.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Feb17_HO4-->


