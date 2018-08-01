---
title: Konfigurowanie superużytkowników dla usługi Azure Rights Management — AIP
description: Uzyskaj informacje o funkcji superużytkowników usługi Azure Rights Management w ramach usługi Azure Information Protection i zaimplementuj tę funkcję. Zapewnia ona, że upoważnione osoby i usługi mogą zawsze odczytywać i sprawdzać dane chronione w organizacji przez usługę Azure Rights Management. Tę możliwość czasami nazywa się „rozsądkiem ponad danymi”. Jest to kluczowy element w zachowaniu kontroli nad danymi w organizacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/31/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 57cf471c614734c6183853b900750c9fef333100
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39369762"
---
# <a name="configuring-super-users-for-azure-rights-management-and-discovery-services-or-data-recovery"></a>Konfigurowanie superużytkowników usług Azure Rights Management i usług odnajdywania lub odzyskiwania danych

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Dzięki funkcji superużytkowników usługi Azure Rights Management w ramach usługi Azure Information Protection upoważnione osoby i usługi mogą zawsze odczytywać i sprawdzać dane chronione w organizacji przez usługę Azure Rights Management. W razie potrzeby mogą też usunąć lub zmienić uprzednio zastosowaną ochronę. 

Administrator ma zawsze w usłudze Rights Management [prawo użytkowania](configure-usage-rights.md) typu Pełna kontrola w odniesieniu do dokumentów i wiadomości e-mail chronionych przez dzierżawę usługi Azure Information Protection w organizacji. Tę możliwość czasami nazywa się "rozsądkiem ponad danymi" i jest to kluczowy element w zachowaniu kontroli nad danymi w organizacji. Przykładowo z tej funkcji można skorzystać w każdym z następujących scenariuszy:

- Pracownik opuszcza organizację i zachodzi potrzeba odczytania plików, które zabezpieczył.

- Administrator IT musi usunąć bieżące zasady ochrony skonfigurowane dla plików i zastosować nowe zasady ochrony.

- Serwer programu Exchange musi indeksować skrzynki pocztowe na potrzeby operacji wyszukiwania.

- Masz istniejące usługi IT związane z rozwiązaniami zapobiegania utracie danych (DLP), bramy szyfrowania zawartości (CEG) i produkty chroniące przed złośliwym oprogramowaniem, które muszą sprawdzić już zabezpieczone pliki.

- Musisz zbiorczo odszyfrować pliki w związku z audytem, kwestiami prawnymi lub innymi kwestiami dotyczącymi zgodności.

## <a name="configuration-for-the-super-user-feature"></a>Konfiguracja funkcji superużytkowników

Domyślnie funkcja superużytkowników nie jest włączona i żadni użytkownicy nie są przypisani do tej roli. Funkcja zostanie włączona automatycznie, jeśli skonfigurujesz łącznik usługi Rights Management dla programu Exchange. Nie jest ona wymagana dla standardowych usług działających na bazie usług Exchange Online i SharePoint Online albo serwera programu SharePoint.

Jeśli musisz ręcznie włączyć funkcję superużytkowników, użyj polecenia cmdlet środowiska PowerShell [Enable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/enable-aadrmsuperuserfeature), a następnie przypisz użytkowników (lub konta usługi) według potrzeb, używając poleceń cmdlet [Add-AadrmSuperUser](/powershell/aadrm/vlatest/add-aadrmsuperuser) lub [Set-AadrmSuperUserGroup](/powershell/aadrm/vlatest/set-aadrmsuperusergroup) i dodaj użytkowników (lub inne grupy) według potrzeb do tej grupy. 

Chociaż użycie grupy dla superużytkowników jest łatwiejsze w zarządzaniu, należy pamiętać, że ze względu na wydajność w usłudze Azure Rights Management [członkostwo w grupie jest buforowane](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection). Jeśli więc trzeba przypisać nowego użytkownika jako superużytkownika w celu natychmiastowego odszyfrowania zawartości, dodaj tego użytkownika za pomocą polecenia Add-AadrmSuperUser, zamiast dodawać go do istniejącej grupy skonfigurowanej przy użyciu polecenia Set-AadrmSuperUserGroup.

> [!NOTE]
> Jeśli nie zainstalowano jeszcze modułu programu Windows PowerShell dla [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1.md)], zobacz [Instalowanie modułu AADRM programu PowerShell](install-powershell.md).

Po włączeniu funkcji superużytkowników lub kiedy dodawać użytkowników jako administratorów nie ma znaczenia. Na przykład jeśli włączyć tę funkcję w czwartek, a następnie dodanie użytkownika w piątek, ten użytkownik natychmiast otworzyć zawartość, która była chroniona na samym początku tygodnia.

## <a name="security-best-practices-for-the-super-user-feature"></a>Najlepsze rozwiązania dotyczące funkcji superużytkowników

- Ogranicz i monitoruj administratorów, którzy zostali przypisani do funkcji administratora globalnego usługi Office 365 lub dzierżawy usługi Azure Information Protection albo zostali przypisani do roli GlobalAdministrator za pomocą polecenia cmdlet [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator). Ci użytkownicy mogą włączyć funkcję superużytkowników i przypisywać użytkowników (w tym siebie) do funkcji superużytkowników. Mogą też potencjalnie odszyfrować wszystkie pliki chronione w organizacji.

- Aby zobaczyć, którzy użytkownicy i konta usług są indywidualnie przypisane jako superużytkowników, użyj [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperuser) polecenia cmdlet. Aby zobaczyć, czy skonfigurowano grupę superużytkowników, użyj [Get-AadrmSuperUserGroup](/powershell/module/aadrm/get-aadrmsuperusergroup) polecenia cmdlet i narzędzia zarządzania użytkownika standardowego do sprawdzenia, którzy użytkownicy są członkami tej grupy. Tak jak wszystkie działania administratorów, włączanie lub wyłączanie funkcji superużytkowników oraz dodawanie i usuwanie superużytkowników jest rejestrowane i może być sprawdzone za pomocą polecenia [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog). Zobacz następną sekcję, aby uzyskać przykład. Gdy superużytkownik odszyfrowuje pliki, akcja ta jest rejestrowana i może być sprawdzona za pomocą funkcji [rejestrowania użycia](log-analyze-usage.md).

- Jeśli nie potrzebujesz funkcji superużytkowników w codziennych działaniach, włącz tę funkcję tylko wtedy, gdy jest potrzeba, a następnie wyłącz ją za pomocą polecenia cmdlet [Disable-AadrmSuperUserFeature](/powershell/module/aadrm/disable-aadrmsuperuserfeature).

### <a name="example-auditing-for-the-super-user-feature"></a>Przykład inspekcji dla superużytkowników

Poniższy fragment dziennika pokazuje przykładowe wpisy uzyskane za pomocą [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) polecenia cmdlet. 

W tym przykładzie administrator firmy Contoso Ltd potwierdza, że funkcja superużytkowników jest wyłączona, dodaje użytkownika Richard Simone jako superużytkownika, sprawdza, czy Richard jest jedynym superużytkownikiem skonfigurowanym dla usługi Azure Rights Management, a następnie włącza funkcję superużytkownika. Dzięki temu Richard może teraz odszyfrować pliki zabezpieczone przez byłego pracownika firmy.

`2015-08-01T18:58:20    admin@contoso.com   GetSuperUserFeatureState    Passed  Disabled`

`2015-08-01T18:59:44    admin@contoso.com   AddSuperUser -id rsimone@contoso.com    Passed  True`

`2015-08-01T19:00:51    admin@contoso.com   GetSuperUser    Passed  rsimone@contoso.com`

`2015-08-01T19:01:45    admin@contoso.com   SetSuperUserFeatureState -state Enabled Passed  True`

## <a name="scripting-options-for-super-users"></a>Opcje obsługi skryptów dla superużytkowników
Często osoba przypisana do roli superużytkownika usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1.md)] będzie musiała usunąć ochronę z wielu plików w wielu różnych lokalizacjach. Mimo że można to zrobić ręcznie, bardziej wydajne (a często też bardziej niezawodne) jest zastosowanie skryptów. W tym celu możesz użyć polecenia cmdlet [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile), a w razie potrzeby także polecenia cmdlet [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile). 

Jeśli korzystasz z klasyfikacji i ochrony, możesz również użyć polecenia [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) w celu zastosowania nowej etykiety, która nie spowoduje zastosowania ochrony, lub usunąć etykietę, która powodowała zastosowanie ochrony. 

Aby uzyskać więcej informacji na temat wymienionych poleceń cmdlet, zobacz sekcję [Używanie środowiska PowerShell z klientem usługi Azure Information Protection](../rms-client/client-admin-guide-powershell.md) w podręczniku administratora klienta usługi Azure Information Protection.

> [!NOTE]
> Moduł AzureInformationProtection zastępuje moduł ochrony usługi RMS programu PowerShell, który został zainstalowany razem z narzędziem RMS Protection Tool. Oba te moduły są inne niż i uzupełnia [modułu programu PowerShell dla usługi Azure Rights Management](administer-powershell.md). Moduł AzureInformationProtection obsługuje zarówno usługę Azure Information Protection, Azure Rights Management (Azure RMS) w ramach usługi Azure Information Protection, jak i usługi Active Directory Rights Management (AD RMS).


