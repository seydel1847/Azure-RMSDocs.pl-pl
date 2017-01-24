---
title: "Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych | Azure Information Protection"
description: "Uzyskaj informacje o funkcji superużytkowników usługi Azure Rights Management w ramach usługi Azure Information Protection i zaimplementuj tę funkcję. Zapewnia ona, że upoważnione osoby i usługi mogą zawsze odczytywać i sprawdzać dane chronione w organizacji przez usługę Azure Rights Management. Tę możliwość czasami nazywa się „rozsądkiem ponad danymi”. Jest to kluczowy element w zachowaniu kontroli nad danymi w organizacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: d2c7c5307ad1ea8866b40e9daa29634496f9323c


---

# <a name="configuring-super-users-for-azure-rights-management-and-discovery-services-or-data-recovery"></a>Konfigurowanie superużytkowników usług Azure Rights Management i usług odnajdywania lub odzyskiwania danych

>*Dotyczy: Azure Information Protection, Office 365*

Dzięki funkcji superużytkowników usługi Azure Rights Management w ramach usługi Azure Information Protection upoważnione osoby i usługi mogą zawsze odczytywać i sprawdzać dane chronione w organizacji przez usługę Azure Rights Management. W razie potrzeby mogą też usunąć lub zmienić uprzednio zastosowaną ochronę. Superużytkownik ma zawsze pełne prawa właściciela wobec wszystkich licencji użytkowania przyznanych przez dzierżawę usługi Azure Information Protection w organizacji. Tę możliwość czasami nazywa się „rozsądkiem ponad danymi”. Jest to kluczowy element w zachowaniu kontroli nad danymi w organizacji. Przykładowo z tej funkcji można skorzystać w każdym z następujących scenariuszy:

-   Pracownik opuszcza organizację i zachodzi potrzeba odczytania plików, które zabezpieczył.

-   Administrator IT musi usunąć bieżące zasady ochrony skonfigurowane dla plików i zastosować nowe zasady ochrony.

-   Serwer programu Exchange musi indeksować skrzynki pocztowe na potrzeby operacji wyszukiwania.

-   Masz istniejące usługi IT związane z rozwiązaniami zapobiegania utracie danych (DLP), bramy szyfrowania zawartości (CEG) i produkty chroniące przed złośliwym oprogramowaniem, które muszą sprawdzić już zabezpieczone pliki.

-   Musisz zbiorczo odszyfrować pliki w związku z audytem, kwestiami prawnymi lub innymi kwestiami dotyczącymi zgodności.

Domyślnie funkcja superużytkowników nie jest włączona i żadni użytkownicy nie są przypisani do tej roli. Funkcja zostanie włączona automatycznie, jeśli skonfigurujesz łącznik usługi Rights Management dla programu Exchange. Nie jest ona wymagana dla standardowych usług działających na bazie usług Exchange Online i SharePoint Online albo serwera programu SharePoint.

Jeśli musisz ręcznie włączyć funkcję superużytkowników, użyj polecenia cmdlet środowiska Windows PowerShell [Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx), a następnie przypisz użytkowników (lub konta usługi) wedle potrzeby, używając poleceń cmdlet [Add-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629411.aspx) lub [Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx) i dodaj użytkowników (lub inne grupy) wedle potrzeby do tej grupy. 

> [!NOTE]
> Jeśli jeszcze nie masz zainstalowanego modułu Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)], zobacz temat [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).

Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące funkcji superużytkowników:

-   Ogranicz i monitoruj administratorów, którzy zostali przypisani do funkcji administratora globalnego usługi Office 365 lub dzierżawy usługi Azure Information Protection albo zostali przypisani do roli GlobalAdministrator za pomocą polecenia cmdlet [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx). Ci użytkownicy mogą włączyć funkcję superużytkowników i przypisywać użytkowników (w tym siebie) do funkcji superużytkowników. Mogą też potencjalnie odszyfrować wszystkie pliki chronione w organizacji.

-   Aby zobaczyć, którzy użytkownicy i które konta usług są indywidualnie przypisane do funkcji superużytkowników, użyj polecenia cmdlet [Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx). Aby zobaczyć, czy skonfigurowano grupę superużytkowników, użyj polecenia cmdlet [Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/mt653942.aspx) i swoich standardowych narzędzi do zarządzania użytkownikami w celu sprawdzenia, którzy użytkownicy są członkami tej grupy. Tak jak wszystkie działania administratorów, włączanie lub wyłączanie funkcji superużytkowników oraz dodawanie i usuwanie superużytkowników jest rejestrowane i może być sprawdzone za pomocą polecenia [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx). Gdy superużytkownik odszyfrowuje pliki, akcja ta jest rejestrowana i może być sprawdzona za pomocą funkcji [rejestrowania użycia](log-analyze-usage.md).

-   Jeśli nie potrzebujesz funkcji superużytkowników w codziennych działaniach, włącz tę funkcję tylko wtedy, gdy jest potrzeba, a następnie wyłącz ją za pomocą polecenia cmdlet [Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx).

Poniższy fragment dziennika pokazuje przykładowe wpisy uzyskane za pomocą polecenia cmdlet Get-AadrmAdminLog. W tym przykładzie administrator firmy Contoso Ltd potwierdza, że funkcja superużytkowników jest wyłączona, dodaje użytkownika Richard Simone jako superużytkownika, sprawdza, czy Richard jest jedynym superużytkownikiem skonfigurowanym dla usługi Azure Rights Management, a następnie włącza funkcję superużytkownika. Dzięki temu Richard może teraz odszyfrować pliki zabezpieczone przez byłego pracownika firmy.

`2015-08-01T18:58:20    admin@contoso.com   GetSuperUserFeatureState    Passed  Disabled`

`2015-08-01T18:59:44    admin@contoso.com   AddSuperUser -id rsimone@contoso.com    Passed  True`

`2015-08-01T19:00:51    admin@contoso.com   GetSuperUser    Passed  rsimone@contoso.com`

`2015-08-01T19:01:45    admin@contoso.com   SetSuperUserFeatureState -state Enabled Passed  True`

## <a name="scripting-options-for-super-users"></a>Opcje obsługi skryptów dla superużytkowników
Często osoba przypisana do roli superużytkownika usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] będzie musiała usunąć ochronę z wielu plików w wielu różnych lokalizacjach. Mimo że można to zrobić ręcznie, bardziej wydajne (a często też bardziej niezawodne) jest zastosowanie skryptów. Aby to zrobić, [pobierz narzędzie RMS Protection Tool](http://www.microsoft.com/en-us/download/details.aspx?id=47256). Następnie wedle potrzeby użyj poleceń cmdlet [Unprotect-RMSFile](https://msdn.microsoft.com/library/azure/mt433200.aspx) i [Protect-RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx).

Aby uzyskać więcej informacji o tych poleceniach cmdlet, zobacz [RMS Protection Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx) (Polecenia cmdlet narzędzia RMS Protection).

> [!NOTE]
> Moduł PowerShell RMS Protection dołączany do narzędzia RMS Protection Tool różni się od głównego [modułu Windows PowerShell dla usługi Azure Rights Management](administer-powershell.md) i uzupełnia go. Moduł RMS Protection obsługuje zarówno usługę Azure Rights Management (Azure RMS) w ramach usługi Azure Information Protection, jak i usługi Active Directory Rights Management (AD RMS).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]




<!--HONumber=Jan17_HO4-->


