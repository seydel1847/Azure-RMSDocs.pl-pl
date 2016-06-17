---
# required metadata

title: Jak aktywować usługę Azure Rights Management w klasycznym portalu Azure | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/05/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 9b0a0227-88ce-44b8-ba3f-31eeaab27ff7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Jak aktywować usługę Azure Rights Management w klasycznym portalu Azure

*Dotyczy: Azure Rights Management*


Te instrukcje są przeznaczone dla użytkowników, którzy mają dostęp do portalu Azure. Przykładem mogą być użytkownicy z subskrypcją pakietu Enterprise Mobility Suite.

> [!TIP]
> Obejrzyj 2-minutowy film wideo: [Jak aktywować usługę Azure RMS](https://channel9.msdn.com/series/pit-stop-enterprise-mobility-suite/activate-azure-rms)

1.  Po zarejestrowaniu się w celu utworzenia konta Azure [zaloguj się do klasycznego portalu Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081)..

2.  W okienku po lewej stronie kliknij pozycję **ACTIVE DIRECTORY**..

3.  Na stronie **Active Directory** kliknij pozycję **RIGHTS MANAGEMENT**..

4.  Wybierz katalog do zarządzania dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], kliknij pozycję **AKTYWUJ**, a następnie potwierdź akcję.

---

   UWAGA: Jeśli zostanie wyświetlony błąd aktywacji, może to oznaczać, że Twój plan usługi lub wersja produktu nie zawiera usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

   Aby potwierdzić obsługę usługi RMS, skorzystaj z informacji w artykule [Subskrypcje usług w chmurze, które obsługują usługę Azure RMS](../get-started/requirements-subscriptions.md). Aby uzyskać pomoc związaną z tym problemem, wyślij wiadomość e-mail na adres [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS)..

---


**STAN USŁUGI RIGHTS MANAGEMENT** powinien mieć teraz wartość **Aktywna**, a opcja **AKTYWUJ** powinna zostać zastąpiona opcją **DEZAKTYWUJ**..

## Wartości i opisy stanu usługi Rights Management w klasycznym portalu Azure
Oprócz stanu **Aktywna**, który wskazuje, że usługa Rights Management jest włączona i gotowa do użycia, może być również wyświetlany stan **Nieaktywna**, **Niedostępna** lub **Bez autoryzacji**..

|Wartość stanu|Opis|
|----------------|---------------|
|**Aktywny**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] Jest włączona i gotowa do użytku.|
|**Nieaktywna**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] Jest wyłączona i musi zostać aktywowana, aby organizacja mogła chronić pliki.|
|**Niedostępny**|Usługa [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] nie działa. Spróbuj ponownie później.|
|**Nieupoważniony**|Nie masz uprawnień umożliwiających wyświetlanie stanu usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]. Na przykład Twoje konto jest zablokowane lub nie jesteś administratorem globalnym dla wybranej dzierżawy.|

## Następne kroki
Powrót do [Aktywacja usługi Azure Rights Management](activate-service.md)..

<!--HONumber=May16_HO1-->

