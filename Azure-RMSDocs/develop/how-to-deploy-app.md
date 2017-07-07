---
title: "Wdrażanie aplikacji — AIP"
description: "W tym artykule opisano proces wdrażania aplikacji usługi do dzierżawy innej niż ta, z którą była ona pierwotnie opracowana."
keywords: 
author: kkanakas
ms.author: kartikk
manager: mbaldwin
ms.date: 02/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 34dc6d6f-cfe4-4848-9b11-8d90c4b38ef7
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 3b7ff758abeb3f1ddc1ae82349233e437d05dacc
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="deploying-a-service-application-into-a-different-tenant"></a>Wdrażanie aplikacji usługi do innej dzierżawy

W tym artykule opisano proces wdrażania aplikacji usługi. W tym scenariuszu przedstawiono przejście od aplikacji zarejestrowanej za pomocą dzierżawy usługi AD, w której została pierwotnie opracowana, do aplikacji zarejestrowanej za pomocą produkcyjnej dzierżawy usługi AD innej firmy.

> [!Note]
> Ten scenariusz ma zastosowanie tylko wtedy, gdy w aplikacji usługi używane jest uwierzytelnianie za pomocą klucza symetrycznego.

## <a name="scenario"></a>Scenariusz
Firma *CoolApp* opracowała przy użyciu usługi Azure Information Protection (AIP) aplikację usługi, która szyfruje, etykietuje i chroni dokumenty, gdy użytkownicy eksportują je z aplikacji biznesowych, takich jak Dynamics, SAP lub Salesforce. W tym scenariuszu duże przedsiębiorstwo *ABC* kupuje nową aplikację firmy *CoolApp*, więc zespół *CoolApp* musi wdrożyć swoje rozwiązanie w środowisku firmy *ABC*. 

![Przykładowy przepływ tworzenia klucza symetrycznego w innej dzierżawie](../media/develop/service-app-provision.jpg)

## <a name="flow-1-coolapp-provides-a-ui-dialog-to-abc-to-implement-the-deployment"></a>Przepływ 1: firma *CoolApp* udostępnia firmie *ABC* okno dialogowe interfejsu użytkownika, aby zaimplementować wdrożenie

Po zakupieniu przez firmę *ABC* rozwiązania *CoolApp* administrator IT w firmie *ABC* musi utworzyć nazwę główną usługi *CoolApp* oraz zarejestrować aplikację w dzierżawie usługi Azure AD firmy *ABC*. 

Kroki te opisano w sekcji **Tworzenie nazwy głównej usługi** w artykule [Tworzenie aplikacji](developing-your-application.md).

![Przykład interfejsu użytkownika do wprowadzenia do aplikacji przez administratora IT](../media/develop/how-to-deploy-app-UI.png)

> [!Note]
> Aby utworzyć nazwę główną usługi w dzierżawie trzeba mieć uprawnienia administratora dzierżawy

Następnie administrator IT firmy *ABC* uruchamia aplikację firmy *CoolApp* jako usługę w swoim środowisku i osadza szczegóły potrzebne do działania aplikacji *CoolApp*, takie jak identyfikator aplikacji, identyfikator dzierżawy i klucz symetryczny.

Jeśli założenie jest takie, że nie będzie się udostępniać administratorowi IT firmy *ABC* okna dialogowego interfejsu użytkownika do wprowadzania informacji dotyczących nazwy głównej usługi, wtedy należy zastosować metodę **Przepływ 2**.

## <a name="flow-2-abc-it-administrator-provides-the-key-to-the-coolapp-team"></a>Przepływ 2: administrator IT firmy *ABC* udostępnia klucz zespołowi firmy *CoolApp*

Po utworzeniu nazwy głównej usługi przez administratora IT firmy *ABC*, jak przedstawiono na **Rysunku 1**, firma *ABC* przekaże informacje zespołowi firmy *CoolApp*. Następnie zespół firmy *CoolApp* osadza informacje w aplikacji *CoolApp* do użytku w dzierżawie firmy *ABC*.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]