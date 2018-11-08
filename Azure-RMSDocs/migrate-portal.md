---
title: Migracja z klasycznego portalu Azure — AIP
description: Zadań administracyjnych w skrócie w witrynie Azure portal, które były wykonywane w klasycznym portalu Azure
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/07/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 57a1073c-02e0-441b-bf49-c6b72fdba24f
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 0f94a36f7653ef4aff590bb6815c75210768f7c5
ms.sourcegitcommit: 227f54a8e90aa57d778ab60c646179c10e5edb44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "51272367"
---
# <a name="tasks-that-you-used-to-do-with-the-azure-classic-portal"></a>Zadania, które były wykonywane przy użyciu klasycznego portalu Azure

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Używany do klasycznego portalu Azure do zarządzania usługą Azure Rights Management i muszą się o pomoc przejście do witryny Azure portal?

Wycofane w klasycznym portalu Azure **08 stycznia 2018 r**. Po tej dacie nie będziesz mógł zarządzać w klasycznym portalu usługi Azure Rights Management i szablonów niestandardowych. Jeśli spróbujesz uzyskać dostęp do portalu klasycznego, zostanie wyświetlony link umożliwiający przejście do nowej witryny Azure portal.

Aby uzyskać więcej informacji na temat klasycznego portalu wycofywania, zobacz wpis w blogu: [Pochód w przyszłości środowiska pracy administratora usługi Azure AD: wycofywanie w klasycznym portalu Azure](https://cloudblogs.microsoft.com/enterprisemobility/2017/09/18/marching-into-the-future-of-the-azure-ad-admin-experience-retiring-the-azure-classic-portal/). Tymczasowe rozszerzenia oryginalnej dacie wycofania, zobacz [aktualizacji na wycofanie środowisku klasycznym portalu usługi Azure AD i migrację zasad dostępu warunkowego](https://cloudblogs.microsoft.com/enterprisemobility/2017/11/29/update-on-retirement-of-azure-ad-classic-portal-experience-and-migration-of-conditional-access-policies/).

## <a name="how-to-do-your-familiar-admin-tasks"></a>Jak wykonywać zadania związane z dobrze znanych administratora

Skorzystaj z poniższych informacji, aby ułatwić szybkie przejście do bieżącego portalu.

|Klasyczny portal Azure|Jak wykonać to zadanie w witrynie Azure portal
|-----------|--------------------|
|Dostęp do ustawień konfiguracji po raz pierwszy|1. [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal).<br /><br />2. Postępuj zgodnie z instrukcjami dotyczącymi [dostęp do bloku usługi Azure Information Protection po raz pierwszy do](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time).
|Utwórz nowy szablon|Utwórz etykietę powodującą zastosowanie ochrony, a następnie użyj **Ustaw uprawnienia** zdefiniować uprawnienia, wygaśnięcia i dostęp w trybie offline. <br /><br />Dzieje się w tle ta konfiguracja tworzy nowy szablon niestandardowy, który następnie jest możliwy przez usługi i aplikacje, które integrują się z szablonami usługi Rights Management.<br /><br />Aby uzyskać więcej informacji, zobacz [do utworzenia nowego szablonu](configure-policy-templates.md#to-create-a-new-template).
|Edytowanie właściwości szablonu: <br /><br />-Nazwę i opis szablonu<br /><br />— Prawa do użytkowania, wygaśnięcia zawartości i ustawień dostępu w trybie offline|Jeśli użytkownik jeszcze tego nie zrobiono, [konwersji szablonu na etykietę](configure-policy-templates.md#to-convert-templates-to-labels), a następnie wykonaj następujące czynności<br /><br />1. Zmień nazwę etykiety i opis<br /><br />2. Zmień ustawienia ochrony na etykiecie, aby zaktualizować uprawnienia, wygaśnięcia i ustawienia dostępu w trybie offline.<br /><br />Aby uzyskać więcej informacji, zobacz [na konfigurowanie etykiety w celu ustawienia ochrony](configure-policy-protection.md#to-configure-a-label-for-protection-settings).
|Przeprowadzona Archiwizacja szablonu|Ustaw stan etykiet **wyłączone**.
|Tworzenie szablonu o określonym zakresie|Utwórz zasady o określonym zakresie i utworzyć etykietę w tym zakresie, która dotyczy ochrony. <br /><br />Aby uzyskać więcej informacji, zobacz [do konfigurowania zasad usługi Azure Information Protection dla konkretnych użytkowników przy użyciu zasad o określonym zakresie](configure-policy-scope.md).
|Kopiowanie szablonu|Nie można skopiować szablon w witrynie Azure portal. Jeśli chcesz, aby dwóch etykiet, które mają takie same ustawienia ochrony, należy ustawić uprawnienia dla każdej etykiety. <br /><br />Aby uzyskać więcej informacji, zobacz [na konfigurowanie etykiety w celu ustawienia ochrony](configure-policy-protection.md#to-configure-a-label-for-protection-settings).
|Usuń szablon|Usuwanie szablonów może spowodować niedostępnych danych, dzięki czemu witryny Azure portal nie obsługuje tej akcji. Można jednak usunąć etykietę i następnie za pomocą programu PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) polecenie cmdlet do usuwania szablonu. <br /><br />Aby uzyskać więcej informacji, zobacz [jak usunąć lub zmiana kolejności etykiet dla usługi Azure Information Protection](configure-policy-delete-reorder.md).
|Obsługa wielu języków|Z **Zarządzaj** wybór menu, wybierz opcję **języków** do wyeksportowania pól możliwych do dostosowania, które zawierają nazwę i opis szablonu. Tłumaczenia ciągów, a następnie zaimportować te ciągi do portalu. <br /><br />Aby uzyskać więcej informacji, zobacz [sposobu konfigurowania etykiet i szablony w różnych językach dla usługi Azure Information Protection](configure-policy-languages.md).
|Raporty sieci web zarządzania prawami dostępu w|[Scentralizowane raportowanie usługi Azure Information Protection](reports-aip.md) jest teraz dostępna w wersji zapoznawczej.<br /><br />Możesz również użyć programu PowerShell [Get-AadrmUsageLog](/powershell/module/aadrm/Get-AadrmUsageLog) polecenia cmdlet, aby pobrać dzienniki użycia dla usługi Azure Rights Management. Te dane można następnie użyć do tworzenia niestandardowych raportów. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](log-analyze-usage.md).
|Aktywowanie i dezaktywowanie usługi Rights Management|Z **Zarządzaj** opcje menu, wybierz opcję **Aktywacja ochrony**.<br /><br />Aby uzyskać więcej informacji, zobacz [jak aktywować usługę Azure Rights Management w witrynie Azure portal](activate-azure.md).

Przed rozpoczęciem edycji szablonów, lub konwersji do etykiet w witrynie Azure portal, zobacz [zagadnienia dotyczące szablonów w witrynie Azure portal](configure-policy-templates.md#considerations-for-templates-in-the-azure-portal).


## <a name="what-else-has-changed"></a>Co jeszcze został zmieniony

Nowe funkcje w witrynie Azure portal:

- Możesz edytować [szablony domyślne](configure-policy-templates.md#default-templates) są tworzone automatycznie dla Twojej organizacji.

- Szablony można konwertować do etykiet, tak, aby zarządzać pojedynczy obiekt, zamiast zarządzać szablonem i etykiety niezależnie. Aby uzyskać instrukcje, zobacz [Aby dokonać konwersji szablonów na etykiety](configure-policy-templates.md#to-convert-templates-to-labels).

- Obsługa innych ról administratora: konieczne było Zaloguj się do klasycznego portalu Azure jako Administrator globalny do konfigurowania usługi Azure Rights Management, można logowaniu do witryny Azure portal do konfigurowania usługi Azure Information Protection przy użyciu konta, które ma jakiekolwiek z następujące role administracyjne: **administratora globalnego**, **Administrator zabezpieczeń**, lub **Administrator usługi Information Protection**. Aby uzyskać więcej informacji na temat każdego z tych ról, zobacz [dostępnych ról](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) sekcji w dokumentacji usługi Azure Active Directory.

Polecenia cmdlet programu PowerShell do tworzenia szablonów i zarządzania nimi i aby aktywować lub dezaktywować usługę, w dalszym ciągu obsługiwany bez zmian.

## <a name="see-also"></a>Zobacz także
Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów i zarządzanie nimi w zasadach usługi Azure Information Protection](configure-policy-templates.md).

