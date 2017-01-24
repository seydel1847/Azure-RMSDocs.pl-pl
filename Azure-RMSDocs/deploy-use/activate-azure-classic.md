---
title: "Jak aktywować usługę Azure Rights Management w klasycznym portalu Azure | Azure Information Protection"
description: "Instrukcje dotyczące aktywacji usługi Rights Management po uzyskaniu dostępu do witryny Azure Portal. Na przykład masz subskrypcję pakietu Enterprise Mobility Suite lub subskrypcję usługi Azure Information Protection w wersji Premium."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 9b0a0227-88ce-44b8-ba3f-31eeaab27ff7
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 3565277446866514f975390d4fee233117eeccec


---

# <a name="how-to-activate-azure-rights-management-from-the-azure-classic-portal"></a>Jak aktywować usługę Azure Rights Management w klasycznym portalu Azure

>*Dotyczy: Azure Information Protection*


Te instrukcje są przeznaczone dla użytkowników, którzy mają dostęp do portalu Azure. Na przykład masz subskrypcję pakietu Enterprise Mobility Suite lub subskrypcję usługi Azure Information Protection w wersji Premium.

> [!TIP]
> Obejrzyj 2-minutowy film wideo: [Jak aktywować usługę Azure RMS](https://channel9.msdn.com/series/pit-stop-enterprise-mobility-suite/activate-azure-rms)

1.  Po zarejestrowaniu się w celu utworzenia konta Azure [zaloguj się do klasycznego portalu Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081). Użyj konta administratora globalnego, takiego jak konto użyte do uzyskania subskrypcji, która obejmuje usługę Azure Rights Management.

2.  W okienku po lewej stronie kliknij opcję **ACTIVE DIRECTORY**.

3.  Na stronie **Active Directory** kliknij pozycję **RIGHTS MANAGEMENT**.

4.  Wybierz katalog do zarządzania dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], kliknij pozycję **AKTYWUJ**, a następnie potwierdź akcję.

    > [!NOTE]
    >Jeśli wyświetlany jest błąd aktywacji, może to oznaczać, że Twój plan usługi lub wersja produktu nie obejmuje usługi Azure Rights Management dla usługi Azure Information Protection.
    >
    >Aby aktywować usługę Azure Rights Management, potrzebujesz [planu usługi Azure Information Protection Premium](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) lub [planu usługi Office 365 obejmującego usługę Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). Aby uzyskać pomoc związaną z tym problemem, wyślij wiadomość e-mail na adres [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).


**STAN USŁUGI RIGHTS MANAGEMENT** powinien być teraz ustawiony na **Aktywna**, a opcja **AKTYWUJ** zostaje zastąpiona opcją **DEZAKTYWUJ**.

## <a name="rights-management-status-values-and-descriptions-in-the-azure-classic-portal"></a>Wartości i opisy stanu usługi Rights Management w klasycznym portalu Azure
Oprócz stanu **Aktywna**, który wskazuje, że usługa Rights Management została włączona i jest gotowa do użycia, może być również wyświetlany stan **Nieaktywna**, **Niedostępna** lub **Bez autoryzacji**.

|Wartość stanu|Opis|
|----------------|---------------|
|**Aktywna**|Usługa [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] jest włączona i gotowa do użytku.|
|**Nieaktywna**|Usługa [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] jest wyłączona i musi zostać aktywowana, aby organizacja mogła chronić pliki.|
|**Niedostępna**|Usługa [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] nie działa. Spróbuj ponownie później.|
|**Bez autoryzacji**|Nie masz uprawnień umożliwiających wyświetlanie stanu usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]. Na przykład Twoje konto jest zablokowane lub nie jesteś administratorem globalnym dla wybranej dzierżawy.|

## <a name="next-steps"></a>Następne kroki
Powrót do części [Aktywacja usługi Azure Rights Management](activate-service.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


