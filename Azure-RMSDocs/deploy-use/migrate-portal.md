---
title: Migracja z klasycznego portalu Azure - Efektywnych
description: "Zadania administracyjne w skrócie w portalu Azure, używany w klasycznym portalu Azure"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/01/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 57a1073c-02e0-441b-bf49-c6b72fdba24f
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 194c746298024ef294c8a6a6fa0361d21cbd869e
ms.sourcegitcommit: 9b229852c59441f9387bab1d5f28a3c5d9017696
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2017
---
# <a name="tasks-that-you-used-to-do-with-the-azure-classic-portal"></a>Zadania, które są używane z klasycznego portalu Azure

>*Dotyczy: Azure Information Protection, Office 365*

Używany do klasycznego portalu Azure do zarządzania usługą Azure Rights Management i potrzebują niektóre pomocy przechodzenia do portalu Azure? 

> [!NOTE]
> Klasycznym portalu Azure zostaną wycofane **08 stycznia 2018**. Po tej dacie przy próbie za pomocą tego portalu, nastąpi automatyczne przekierowanie do portalu Azure. 
> 
> Aby uzyskać więcej informacji, zobacz anons blog [Pochód w przyszłości środowisko pracy administratora usługi Azure AD: wycofywanie klasycznego portalu Azure](https://blogs.technet.microsoft.com/enterprisemobility/2017/09/18/marching-into-the-future-of-the-azure-ad-admin-experience-retiring-the-azure-classic-portal/). Tymczasowe rozszerzenia oryginalnej dacie wycofania, zobacz [aktualizacji na wycofanie obsługi portalu klasycznego Azure AD i migracja zasad dostępu warunkowego](https://cloudblogs.microsoft.com/enterprisemobility/2017/11/29/update-on-retirement-of-azure-ad-classic-portal-experience-and-migration-of-conditional-access-policies/).

## <a name="how-to-do-your-familiar-admin-tasks"></a>Sposób wykonywania zadań administracyjnych znanych

W celu szybkiego przechodzenia do portalu nowsza, skorzystaj z poniższych informacji:

|Klasyczny portal Azure|Sposób wykonania tego zadania w portalu Azure
|-----------|--------------------|
|Dostęp do ustawień konfiguracji po raz pierwszy|1. Zaloguj się do portalu Azure jako administrator globalny lub Administrator zabezpieczeń dla dzierżawy.<br /><br />2. W menu centralnym kliknij przycisk **Nowy**, a następnie z listy **MARKETPLACE** wybierz opcję **Zabezpieczenia i tożsamość**.<br /><br />3. Na **zabezpieczeń + Identyfikuj** bloku z **POLECANE aplikacje** listy, wybierz **usługi Azure Information Protection**. Następnie na **usługi Azure Information Protection** bloku, kliknij przycisk **Utwórz**.<br /><br />Ta akcja tworzy **usługi Azure Information Protection** bloku, dzięki czemu przy następnym zalogowaniu do portalu można wybrać usługę z Centrum **więcej usług** listy.
|Utwórz nowy szablon|Utworzyć etykietę, która ma zastosowanie ochrony, a następnie użyj **ustawić uprawnienia** do definiowania uprawnień, wygaśnięcia i dostęp w trybie offline. <br /><br />W obszarze obejmuje ta konfiguracja tworzy nowy szablon niestandardowy, które mają dostęp przez usługi i aplikacje, które integrują się z szablonami usługi Rights Management.<br /><br />Aby uzyskać więcej informacji, zobacz [do utworzenia nowego szablonu](configure-policy-templates.md#to-create-a-new-template).
|Edytowanie właściwości szablonu: <br /><br />-Nazwa i opis szablonu<br /><br />— Prawa do użytkowania, wygaśnięcia zawartości i ustawień dostępu w trybie offline|Jeśli jeszcze tego nie zrobiono, [przekonwertować szablon na etykiecie](configure-policy-templates.md#to-convert-templates-to-labels), a następnie wykonaj następujące czynności<br /><br />1. Zmień nazwę etykiety i opis<br /><br />2. Zmień ustawienia ochrony na etykiecie aktualizacji uprawnień, wygaśnięcia i ustawień dostępu w trybie offline.<br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiety dla ochrony usługi Rights Management](configure-policy-protection.md#to-configure-a-label-for-rights-management-protection).
|Archiwizowanie szablonu|Ustaw stan etykiety na **wyłączone**.
|Tworzenie szablonu zakresami|Utwórz zasadę zakresami i utworzyć etykietę w tym zakresie, która ma zastosowanie ochrony. <br /><br />Aby uzyskać więcej informacji, zobacz [sposobu konfigurowania zasad usługi Azure Information Protection dla konkretnych użytkowników przy użyciu zakres zasad](configure-policy-scope.md).
|Kopiowanie szablonu|Nie można skopiować szablon w portalu Azure. Jeśli chcesz, aby dwie etykiety mają takie same ustawienia ochrony, należy ustawić uprawnienia na każdej etykiety. <br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiety dla ochrony usługi Rights Management](configure-policy-protection.md#to-configure-a-label-for-rights-management-protection).
|Usuwanie szablonu|Usuwanie szablonów może spowodować niedostępny danych, więc portalu Azure nie obsługuje tej akcji. Jednak można usunąć etykietę, a następnie użyj programu PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) polecenia cmdlet, aby usunąć szablon. <br /><br />Aby uzyskać więcej informacji, zobacz [usuwanie lub zmiana kolejności etykiet dla usługi Azure Information Protection](configure-policy-delete-reorder.md).
|Obsługa wielu języków|Z **ZARZĄDZAJ** zaznaczenia menu, wybierz opcję **języków (wersja zapoznawcza)** można wyeksportować pól możliwych do dostosowania, które zawierają nazwę i opis szablonu. Tłumaczenie ciągi, a następnie importować te ciągi do portalu. <br /><br />Aby uzyskać więcej informacji, zobacz [sposób konfigurowania usługi Azure Information Protection etykiety i szablony dla różnych języków](configure-policy-languages.md).
|Raporty sieci web zarządzania prawami dostępu w|Użyj programu PowerShell [Get-AadrmUsageLog](/powershell/module/aadrm/Get-AadrmUsageLog) polecenia cmdlet, aby pobrać dzienniki użycia dla usługi Azure Rights Management. Te dane można następnie używać do tworzenia niestandardowych raportów. <br /><br />Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](log-analyze-usage.md).<br /><br />Porada: Pojawiać zawiadomienia o [pakietu Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) dla nowych, scentralizowane rozwiązanie raportowania usługi Azure Information Protection. 
|Aktywowanie i dezaktywowanie usługi Rights Management|Z **ZARZĄDZAJ** opcji menu, wybierz opcję **ustawienia RMS** lub **aktywacji ochrony**. Ta opcja jest w trakcie zmieniana.<br /><br />Aby uzyskać więcej informacji, zobacz [jak aktywować usługę Azure Rights Management w portalu Azure](activate-azure.md).

Przed rozpoczęciem edycji szablonów lub przekonwertować je do etykiet w portalu Azure, zobacz [zagadnienia dotyczące szablonów w portalu Azure](configure-policy-templates.md#considerations-for-templates-in-the-azure-portal).


## <a name="what-else-has-changed"></a>Inne zmiany

Nowe funkcje w portalu Azure:

- Można edytować [szablony domyślne](configure-policy-templates.md#default-templates) są tworzone automatycznie dla Twojej organizacji.

- Szablony do etykiet, można przekonwertować tak, aby zarządzać pojedynczy obiekt zamiast zarządzać szablonu i etykiety niezależnie. Aby uzyskać instrukcje, zobacz [przekonwertować szablony do etykiet](configure-policy-templates.md#to-convert-templates-to-labels).

Obsługa roli administratora zabezpieczeń: konieczne było Zaloguj się do klasycznego portalu Azure jako administrator globalny do konfigurowania usługi Azure Rights Management, można logowania się do portalu Azure można skonfigurować za pomocą konta administratora globalnego usługi Azure Information Protection lub rolą administratora zabezpieczeń. 

Poleceń cmdlet programu PowerShell do tworzenia szablonów i zarządzania nimi i aktywować lub dezaktywować pozostaną usługi obsługiwane bez zmian.


## <a name="see-also"></a>Zobacz także
Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie szablonów i zarządzania nimi w ramach zasad usługi Azure Information Protection](../deploy-use/configure-policy-templates.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]