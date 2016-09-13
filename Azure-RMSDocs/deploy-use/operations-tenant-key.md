---
title: "Operacje związane z kluczem dzierżawy usługi Azure Rights Management | Azure RMS"
description: "Informacje znajdujące się poniżej pozwalają zidentyfikować różne poziomy kontroli i odpowiedzialności dostępne w przypadku klucza dzierżawy usługi Azure Rights Management (Azure RMS)."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ad32910b482ca9d92b4ac8f3f123eda195db29cd
ms.openlocfilehash: d496a99c4b05e0cf0ba5929f44cdbd1906d31341


---

# Operacje związane z kluczem dzierżawy usługi Azure Rights Management

>*Dotyczy usług: Azure Rights Management, Office 365*

W zależności od topologii klucza dzierżawy (zarządzany przez firmę Microsoft lub zarządzany przez klienta) będziesz mieć różne poziomy kontroli i odpowiedzialności za klucz dzierżawy usługi Microsoft Azure Rights Management (Azure RMS) po jego wdrożeniu.

Jeśli zarządzasz swoim kluczem dzierżawy w usłudze Azure Key Vault, taką sytuację najczęściej nazywa się rozwiązaniem Bring Your Own Key (BYOK). Aby uzyskać więcej informacji na temat tego scenariusza i dowiedzieć się, jak wybrać odpowiednią topologię klucza dzierżawy, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](../plan-design/plan-implement-tenant-key.md).

W poniższej tabeli przedstawiono operacje, które można wykonać w zależności od topologii wybranej dla klucza dzierżawy usługi Azure RMS.

|Operacja cyklu życia|Zarządzany przez firmę Microsoft (domyślny)|Zarządzany przez klienta (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Odwołanie klucza dzierżawy|Nie (automatyczny)|Tak|
|Ponowne tworzenie klucza dzierżawy|Tak|Tak|
|Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy|Nie|Tak|
|Eksport klucza dzierżawy|Tak|Nie|
|Reakcja na naruszenie zabezpieczeń|Tak|Tak|

Po zidentyfikowaniu wdrożonej topologii wybierz jeden z poniższych elementów, aby uzyskać więcej informacji o tych operacjach dla swojego klucza dzierżawy usługi Azure RMS:


- [Klucz dzierżawy zarządzany przez firmę Microsoft](operations-microsoft-managed-tenant-key.md)
- [Klucz dzierżawy zarządzany przez klienta](operations-customer-managed-tenant-key.md)







<!--HONumber=Aug16_HO4-->


