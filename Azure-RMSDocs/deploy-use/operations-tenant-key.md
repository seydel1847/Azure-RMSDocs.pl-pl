---
# required metadata

title: Operacje związane z kluczem dzierżawy usługi Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Operacje związane z kluczem dzierżawy usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

W zależności od topologii klucza dzierżawy (zarządzany przez firmę Microsoft lub zarządzany przez klienta) będziesz mieć różne poziomy kontroli i odpowiedzialności za klucz dzierżawy usługi Microsoft Azure Rights Management (Azure RMS) po jego wdrożeniu.

Jeśli zarządzasz swoim kluczem dzierżawy, taką sytuację najczęściej nazywa się scenariuszem z użyciem własnego klucza (BYOK, bring your own key). Aby uzyskać więcej informacji na temat tego scenariusza i dowiedzieć się, jak wybrać odpowiednią topologię klucza dzierżawy, zobacz temat [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](../plan-design/plan-implement-tenant-key.md)..

W poniższej tabeli przedstawiono operacje, które można wykonać w zależności od topologii wybranej dla klucza dzierżawy usługi Azure RMS.

|Operacja cyklu życia|Zarządzany przez firmę Microsoft (domyślny)|Zarządzany przez klienta (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Odwołanie klucza dzierżawy|Nie (automatyczny)|Nie (automatyczny)|
|Ponowne tworzenie klucza dzierżawy|Tak|Tak|
|Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy|Nie|Tak|
|Eksport klucza dzierżawy|Tak|Nie|
|Reakcja na naruszenie zabezpieczeń|Tak|Tak|

Po zidentyfikowaniu wdrożonej topologii wybierz jeden z poniższych elementów, aby uzyskać więcej informacji o tych operacjach dla swojego klucza dzierżawy usługi Azure RMS:


- [Klucz dzierżawy zarządzany przez firmę Microsoft](operations-microsoft-managed-tenant-key.md)
- [Klucz dzierżawy zarządzany przez klienta](operations-customer-managed-tenant-key.md)






<!--HONumber=Apr16_HO4-->


