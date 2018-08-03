---
title: Przygotowanie środowiska do korzystania z usług Azure RMS i AD RMS
description: W tej sekcji znajdują się wskazówki mające zastosowanie w przypadku wdrożenia usługi Azure Rights Management wraz z usługami AD RMS.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/29/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 094088ac8f33a4a6bfaf3f0eec2401785bd0ccdc
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39473556"
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>Przygotowywanie środowiska na potrzeby usługi Azure Rights Management w przypadku używania również usług Active Directory Rights Management Services (AD RMS)

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> Wskazówki dotyczące korzystania z Active Directory Rights Management Services (AD RMS)

Jeśli usługa Azure Rights Management została aktywowana i są również przy użyciu usług AD RMS, ta kombinacja nie jest zgodna. Bez dodatkowych kroków dla niektórych komputerów może automatycznie zacząć używać usługi Azure Rights Management i również połączenia z klastrem usługi AD RMS. W tym scenariuszu nie jest obsługiwana i ma wyniki nie są wiarygodne, więc jest ważne, wykonanie dodatkowych kroków. 

**Aby sprawdzić, czy mają zostać wdrożone usługi AD RMS:**

1. Mimo że jest to opcjonalne, większości wdrożeń usług AD RMS opublikować punkt połączenia usługi (SCP) do usługi Active Directory, aby komputerów w domenie mogą odnajdywać klastra usług AD RMS. 
    
    Użyj ADSI: Edycja, aby sprawdzić, czy punkt połączenia usługi, opublikowane w usłudze Active Directory: `CN=Configuration [server name], CN=Services, CN=RightsManagementServices, CN=SCP`

2. Jeśli punkt połączenia usługi nie jest używany, komputery Windows, łączących się z klastrem usług AD RMS muszą być skonfigurowane dla potrzeb odnajdowania usługi po stronie klienta lub przekierowywanie licencjonowania, za pomocą rejestru Windows: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation` lub `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`
    
    Aby uzyskać więcej informacji o tych konfiguracjach rejestru, zobacz [Włączanie odnajdowania usług po stronie klienta za pomocą rejestru Windows](../rms-client/client-deployment-notes.md#enabling-client-side-service-discovery-by-using-the-windows-registry) i [przekierowywanie ruchu serwera licencyjnego](../rms-client/client-deployment-notes.md#redirecting-licensing-server-traffic).   

Jeśli usługi AD RMS jest wdrażana dla Twojej organizacji, należy rozważyć, czy można migrować do usługi Azure Information Protection. Usługa Azure Information Protection ma wiele zalet za pośrednictwem usług AD RMS. Na przykład lepszą obsługę urządzeń przenośnych i integracji z usługami Office 365, a także za pomocą programu Exchange Server i SharePoint Server. Aby uzyskać więcej informacji, zobacz [Porównanie usług Azure Information Protection i AD RMS](../compare-on-premise.md).

Podczas migracji do usługi Azure Information Protection, nie utracisz dostępu do wcześniej chronionej zawartości i nie musisz wyłączyć ochronę, lub ponownie włączyć ochronę zawartości. Dokumenty i wiadomości e-mail, które były chronione przez usługi AD RMS nadal będzie można otworzyć nawet w przypadku, po anulowaniu obsługi usług AD RMS.

Czy użytkownik chce migrować do usługi Azure Information Protection zdecydujesz się zaakceptować ograniczenia przy użyciu w bieżącym wdrożeniu usług AD RMS, należy się najpierw upewnić dezaktywacji usługi Azure Rights Management. Aby uzyskać instrukcje postępuj zgodnie z instrukcjami dla scenariusza użytkownika:

- [Swoją subskrypcję, która obejmuje usługę Azure Rights Management została zakupiona w trakcie lub po lutego 2018 r.](#your-subscription-was-purchased-during-or-after-february-2018)

- [Twoja subskrypcja została zakupiona przed lub w trakcie lutego 2018 r. i masz w usłudze Exchange Online](#your-subscription-was-purchased-before-or-during-february-2018-and-you-have-exchange-online)

- [Zostanie wyświetlona opcja aktywowania ochrony podczas konfigurowania zasad usługi Azure Information Protection w witrynie Azure portal](#you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection)


## <a name="your-subscription-was-purchased-during-or-after-february-2018"></a>Twoja subskrypcja została zakupiona w trakcie lub po lutego 2018 r.

Pod koniec lutego 2018 r. nowe subskrypcje, które obejmują usługi Azure Information Protection, teraz aktywować usługę Azure Rights Management domyślnie. Jeśli ta usługa jest aktywowana automatycznie dla Ciebie, a także używasz Active Directory Rights Management Services (AD RMS), ta kombinacja jest niezgodna, dlatego należy jak najszybciej dezaktywowanie usługi Azure Rights Management. 

### <a name="step-1-deactivate-azure-rights-management"></a>Krok 1: Dezaktywowanie usługi Azure Rights Management
Użyj jednej z poniższych procedur, aby zdezaktywować usługę Azure Rights Management.

> [!TIP]
> Możesz również użyć polecenia cmdlet programu Windows PowerShell, [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm), aby zdezaktywować usługę Azure Rights Management.

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Aby zdezaktywować usługę Rights Management w centrum administracyjnym usługi Office 365

1. Przejdź na [stronę usługi Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) dla administratorów usługi Office 365.
    
    Po wyświetleniu monitu o zalogowanie użyj konta administratora globalnego usługi Office 365.

2. Na stronie **Rights Management** kliknij pozycję **Dezaktywuj**.

3.  Po wyświetleniu monitu **czy chcesz dezaktywować usługę Rights Management?** kliknij **dezaktywować**.

Teraz powinien pojawić się komunikat **Usługa Rights Management nie została aktywowana** oraz opcja jej aktywowania.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Aby zdezaktywować usługę Rights Management w witrynie Azure portal

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.
    
    Jeśli jeszcze nie dostęp do bloku usługi Azure Information Protection przed, zobacz jednorazowe [dodatkowe kroki](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time) można dodać tego bloku do portalu.

2. Wybierz **Aktywacja ochrony** z opcji menu. 

3.  Na **usługi Azure Information Protection — Aktywacja ochrony** bloku wybierz **Dezaktywuj**. Wybierz **tak** o potwierdzenie wyboru.

Wyświetla pasek informacji **dezaktywacja została zakończona pomyślnie** i **Dezaktywuj** zostanie zastąpiona przez **Aktywuj**. 

### <a name="step-2-start-planning-for-migration"></a>Krok 2. Rozpoczynanie planowania migracji

Zobacz wskazówki dotyczące migracji: [Migrowanie z usług AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)


## <a name="your-subscription-was-purchased-before-or-during-february-2018-and-you-have-exchange-online"></a>Twoja subskrypcja została zakupiona przed lub w trakcie lutego 2018 r. i masz w usłudze Exchange Online

Microsoft jest uruchamiana do aktywowania usługi Azure Rights Management w przypadku subskrypcji obejmujących usługę Azure Rights Management lub usługi Azure Information Protection i dzierżawcy korzystają z usługi Exchange Online. W przypadku tych dzierżaw automatycznej aktywacji rozpoczyna wprowadzane do 1 sierpnia 2018.

Jeśli usługa jest aktywowana automatycznie dla Ciebie i są również przy użyciu usług AD RMS, ta kombinacja nie jest zgodna tak jest, że dzierżawy jest wyłączony z aktualizacji automatycznych usługi. 

### <a name="step-1-opt-out-from-the-automatic-service-update"></a>Krok 1: Zrezygnować z aktualizacji automatycznych usługi

Należy użyć następującego [Set-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/set-irmconfiguration) polecenie programu Exchange Online PowerShell:`Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false`

[Więcej informacji](https://support.office.com/article/protection-features-in-azure-information-protection-rolling-out-to-existing-office-365-tenants-7ad6f58e-65d7-4c82-8e65-0b773666634d) 

### <a name="step-2-start-planning-for-migration"></a>Krok 2. Rozpoczynanie planowania migracji

Zobacz wskazówki dotyczące migracji: [Migrowanie z usług AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)


## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Zostanie wyświetlona opcja aktywowania ochrony, po skonfigurowaniu usługi Azure Information Protection

**Usługi Azure Information Protection — Aktywacja ochrony** bloku znajduje się opcja aktywowania usługi Azure Rights Management.  

Jeśli są również za pomocą usług AD RMS, nie należy wybierać **Aktywuj** opcji. Jeśli usługa Azure Rights Management nie została aktywowana, nadal można używać usługi Azure Information Protection dla etykiet, w przypadków których stosowane jest tylko klasyfikowanie. Tworzone są specjalne zasady domyślne, które nie obejmują funkcji ochrony danych. Te opcje konfiguracji pozostają niedostępne do momentu aktywowania usługi Azure Rights Management.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Krok 1. Konfigurowanie zasad usługi Azure Information Protection pod kątem klasyfikowania i etykietowania — bez ochrony

Z **usługi Azure Information Protection — etykiety** bloku, wyświetlić i skonfigurować etykiety, które nie obejmują opcji ochrony danych. Aby uzyskać więcej informacji o tym, jak skonfigurować ustawienia zasad i etykiet, zobacz [zasad konfigurowania usługi Azure Information Protection](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Krok 2. Rozpoczynanie planowania migracji

Zobacz wskazówki dotyczące migracji: [Migrowanie z usług AD RMS do usługi Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)

### <a name="step-3-configure-labels-for-protection"></a>Krok 3: Skonfigurować etykiety dla ochrony

Po aktywowaniu usługi Azure Rights Management w ramach procesu migracji można skonfigurować etykiety na potrzeby ochrony danych. Jednak w przypadku migrowania partii użytkowników w upewnij się, że etykiety umożliwiające objęcie ochroną są ograniczone do migrowanych użytkowników tylko.


