---
title: Plan wdrażania usługi Azure Information Protection
description: Skorzystaj z tych procedur, aby przygotować się do wdrożenia usługi Azure Information Protection, przeprowadzić to wdrożenie, a następnie zarządzać usługą Azure Information Protection w swojej organizacji.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/05/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 68a02ba4ec9ef0a91d2aa4fbd541c27ba2a07bcd
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42806449"
---
# <a name="azure-information-protection-deployment-roadmap"></a>Plan wdrażania usługi Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Wykonaj następujące kroki, zalecenia, aby pomóc w przygotowaniu, wdrożenia i zarządzania usługi Azure Information Protection dla swojej organizacji.

Jeśli jednak chcesz szybko wypróbować usługę Azure Information Protection we własnym zakresie zamiast wdrażać ją w środowisku produkcyjnym, zobacz [Samouczek Szybki start dotyczący usługi Azure Information Protection](./infoprotect-quick-start-tutorial.md).

> [!IMPORTANT]
> Przed wykonaniem poniższych kroków zapoznaj się z tematem [Wymagania dotyczące usługi Azure Information Protection](./requirements.md).

Wybierz plan wdrożenia, który jest odpowiedni dla Twojej organizacji i uwzględnia [subskrypcje zawierające potrzebne funkcje i możliwości](https://azure.microsoft.com/pricing/details/information-protection/):

- [Korzystanie z funkcji klasyfikacji, etykietowania i ochrony](#deployment-roadmap-for-classification-labeling-and-protection)

- [Korzystanie tylko z funkcji ochrony danych](#deployment-roadmap-for-data-protection-only)


## <a name="deployment-roadmap-for-classification-labeling-and-protection"></a>Mapa wdrożenia funkcji klasyfikacji, etykietowania i ochrony

> [!NOTE]
> Już korzystasz z funkcji ochrony z usługi Azure Information Protection? Możesz pominąć wiele z tych czynności i skoncentrować się na krokach 3 i 5.1.

### <a name="step-1-confirm-your-subscription-and-assign-user-licenses"></a>Krok 1: Potwierdzenie informacji o subskrypcji i przypisanie licencji użytkowników
Przejrzyj listę funkcji i informacje o subskrypcji z [cennik usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection) strony, aby upewnić się, że Twoja organizacja ma subskrypcję, która obejmuje funkcjonalność i funkcje, których można oczekiwać. Następnie przypisz licencję z tej subskrypcji do poszczególnych użytkowników w organizacji, którzy będą zajmować się klasyfikacją, etykietowaniem i ochroną dokumentów i wiadomości e-mail.

Uwaga: Nie przypisuj ręcznie licencji użytkownika z bezpłatnej subskrypcji usługi RMS dla użytkowników indywidualnych ani nie używaj tej licencji do administrowania usługą Azure Rights Management dla swojej organizacji. Te licencje są wyświetlane jako usługa **Rights Management Adhoc** w Centrum administracyjnym usługi Office 365 i **RIGHTSMANAGEMENT_ADHOC** po uruchomieniu polecenia cmdlet programu PowerShell usługi Azure AD [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx). Aby uzyskać więcej informacji dotyczących sposobu automatycznego przyznawania subskrypcji usługi RMS dla użytkowników indywidualnych i jej przypisywania do użytkowników, zobacz [Usługa RMS dla użytkowników indywidualnych i Azure Information Protection](./rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Krok 2: Przygotowanie dzierżawy do używania usługi Azure Information Protection
Przed rozpoczęciem korzystania z usługi Azure Information Protection należy wykonać następujące przygotowania:

- Upewnij się, że masz konta użytkowników i grupy w usłudze Office 365 lub Azure Active Directory, które będą używane przez usługę Azure Information Protection do uwierzytelniania i autoryzowania użytkowników z Twojej organizacji. W razie potrzeby utwórz to konto i grupy lub zsynchronizuj je z katalogu lokalnego. Aby uzyskać więcej informacji, zobacz artykuł [Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection](prepare.md).

### <a name="step-3-configure-and-deploy-classification-and-labeling"></a>Krok 3: Skonfigurowanie i wdrożenie funkcji klasyfikacji i etykietowania

Jeśli nie masz jeszcze strategii dotyczącej klasyfikacji, przejrzyj [domyślne zasady usługi Azure Information Protection](./configure-policy-default.md) i na ich podstawie zdecyduj, jakie etykiety klasyfikacji przypisać do danych Twojej organizacji. Możesz je dostosować tak, aby spełniały wymagania Twojej firmy. 

Zmień konfigurację domyślnych etykiet usługi Azure Information Protection, aby wprowadzić wszelkie zmiany wymagane w odniesieniu do Twoich decyzji dotyczących klasyfikacji. Skonfiguruj zasady w zakresie ręcznego etykietowania przez użytkowników i napisz dla nich wskazówki objaśniające, jakie etykiety należy stosować w poszczególnych sytuacjach. Jeśli zasady domyślne został utworzony za pomocą etykiet, które automatyczne stosowanie ochrony, Usuń ustawienia ochrony lub wyłączanie etykiety. Aby uzyskać więcej informacji o metodach konfigurowania zasad usługi Azure Information Protection, zobacz [Konfigurowanie zasad usługi Azure Information Protection](./configure-policy.md).

Następnie wdróż klienta usługi Azure Information Protection dla użytkowników i zapewnij dla niego pomoc techniczną, oferując użytkownikom szkolenia i instrukcje dotyczące tego, w jakich sytuacjach należy wybierać poszczególne etykiety. Aby uzyskać więcej informacji dotyczących instalacji i obsługi klienta, zobacz temat [Podręcznik administratora klienta usługi Azure Information Protection](./rms-client/client-admin-guide.md).

Po pewnym czasie, gdy użytkownicy nabiorą wprawy w etykietowaniu dokumentów i wiadomości e-mail, wprowadź bardziej zaawansowane konfiguracje. Mogą one obejmować następujące działania i elementy:

- Stosowanie etykiety domyślnej

- Monitowanie użytkowników o uzasadnienie w przypadku wybrania etykiety o niższym poziomie klasyfikacji

- Wprowadzenie obowiązkowego etykietowania wszystkich dokumentów i wiadomości e-mail

- Niestandardowe nagłówki, stopki lub znaki wodne

- Warunki w celu zapewniania obsługi rekomendacji i etykietowania automatycznego

Na tym etapie nie należy wybierać opcji ochrony dokumentów i wiadomości e-mail.

### <a name="step-4-prepare-for-data-protection"></a>Krok 4: Przygotowanie do ochrony danych

Gdy użytkownicy nabiorą wprawy w etykietowaniu dokumentów i wiadomości e-mail, możesz przystąpić do wprowadzania funkcji ochrony danych dla najbardziej poufnych danych. Ten etap wymaga następujących przygotowań pod:

1. Określ, czy Twoim kluczem dzierżawy powinna zarządzać firma Microsoft (opcja domyślna), czy też chcesz wygenerować klucz dzierżawy i zarządzać nim samodzielnie (opcja nazywana „przynieś własny klucz”, BYOK). Aby uzyskać więcej informacji, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](plan-implement-tenant-key.md).

2. Zainstaluj moduł programu PowerShell dla usługi AADRM na co najmniej jeden komputer, który ma dostęp do Internetu. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Instalowanie modułu AADRM programu PowerShell](./install-powershell.md).

3. Jeśli obecnie używasz usługi AD RMS: Przeprowadź migrację, aby przenieść klucze, szablony i adresy URL do chmury. Aby uzyskać więcej informacji, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

4. Upewnij się, że usługi ochrony jest aktywna, więc możesz zacząć chronić dokumenty i wiadomości e-mail. Jeśli wymagane jest wdrożenie etapowe, skonfiguruj kontrolki dołączania użytkowników, aby ograniczyć użytkowanie do określonych użytkowników. Aby uzyskać więcej informacji, zobacz [Aktywacja usługi Azure Rights Management](./activate-service.md).

Opcjonalnie rozważ skonfigurowanie następujących elementów:

-   Szablony niestandardowe ustawienia ochrony, jeśli domyślne szablony nie są wystarczające dla Twojej organizacji. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](./configure-policy-templates.md).

-   Rejestrowania użycia, tak że można monitorować, jak Twoja organizacja używa usługi ochrony. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](./log-analyze-usage.md).

### <a name="step-5-configure-your-azure-information-protection-policy-applications-and-services-for-data-protection"></a>Krok 5. Konfigurowanie zasad usługi Azure Information Protection, aplikacji i usług w celu ochrony danych

1. Aktualizowanie zasad usługi Azure Information Protection w celu zastosowania funkcji ochrony danych
    
    Zmodyfikuj zasady usługi Azure Information Protection, tak, aby co najmniej jedna etykieta stosowała ochrony. Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management](./configure-policy-protection.md).
    
    Należy pamiętać, że użytkownicy mogą używać w programie Outlook etykiet stosowanych do ochrony usługi Rights Management, nawet jeśli program Exchange nie został skonfigurowany do zarządzania prawami do informacji (IRM). Jednak dopóki program Exchange jest skonfigurowany dla usługi IRM lub [szyfrowanie wiadomości usługi Office 365 dzięki nowym funkcjom](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e), Twoja organizacja nie będzie można uzyskać pełnej funkcjonalności podczas korzystania z ochrony usługi Azure Rights Management z programem Exchange. Ta dodatkowa konfiguracja jest dostępna na poniższej liście (w kroku 2 dla usługi Exchange Online i kroku 5 dla lokalnego programu Exchange). 

2. Skonfiguruj aplikacje pakietu Office i usługi
    
    Skonfiguruj aplikacje i usługi pakietu Office pod kątem funkcji zarządzania prawami do informacji (IRM) w usłudze SharePoint Online lub Exchange Online. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](./configure-applications.md).

3. Konfigurowanie funkcji administratora na potrzeby odzyskiwania danych
    
    Jeśli masz istniejące usługi IT, które wymagają inspekcji plików, które ma być chroniony przez usługę Azure Information Protection — takie jak data rozwiązania zapobiegania wyciekom (DLP), bramy szyfrowania zawartości (CEG) i produkty chroniące przed złośliwym kodem — Skonfiguruj konta usług jako super Użytkownicy usługi Azure Rights Management. Aby uzyskać więcej informacji, zobacz [Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](./configure-super-users.md).

4. Zbiorcza klasyfikacja i ochrona plików — w razie potrzeby
    
    Polecenia cmdlet programu PowerShell, umożliwiające klasyfikowanie i ochronę plików, a także usuwanie ich klasyfikacji i ochrony, są instalowane automatycznie wraz z klientem usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz temat [Używanie środowiska PowerShell z klientem usługi Azure Information Protection](./rms-client/client-admin-guide-powershell.md) w podręczniku administratora.

6. Wdrażanie łącznika na serwerach lokalnych
    
    W przypadku usług lokalnych, które mają korzystać z usługi ochrony należy zainstalować i skonfigurować łącznik usługi Rights Management. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](./deploy-rms-connector.md).

### <a name="step-6-use-and-monitor-your-data-protection-solutions"></a>Krok 6. Rozpoczęcie korzystania i monitorowania rozwiązań ochrony danych
Teraz możesz przystąpić do ochrony danych i zaloguj się, jak firma korzysta z etykiet, które zostały skonfigurowane i ochrony danych. Aby uzyskać dodatkowe informacje przydatne w ramach tej fazy wdrażania, zobacz następujące tematy:

- [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](./help-users.md)

-  [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](./log-analyze-usage.md)

- [Rejestrowanie plików i użycia klienta](./rms-client/client-admin-guide-files-and-logging.md)

Jeśli interesuje Cię automatyczne chronienie plików przy użyciu infrastruktury klasyfikacji plików na serwerze plików opartym na systemie Windows, zobacz temat [Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) w systemie Windows Server](./rms-client/configure-fci.md).

### <a name="step-7-administer-the-protection-service-for-your-tenant-account-as-needed"></a>Krok 7: Przystąpienie do zarządzania usługą ochrony dla danego konta dzierżawy zgodnie z potrzebami
Po rozpoczęciu korzystania z usługi ochrony programu PowerShell może być przydatna do ułatwia tworzenie skryptów i automatyzację zmian administracyjnych. Aby uzyskać więcej informacji, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](./administer-powershell.md).


## <a name="deployment-roadmap-for-data-protection-only"></a>Plan wdrożenia obejmujący tylko funkcje ochrony danych

### <a name="step-1-confirm-that-you-have-a-subscription-that-includes-the-protection-service-from-azure-information-protection"></a>Krok 1: Upewnij się, że masz subskrypcję, która obejmuje usługi ochrony z usługi Azure Information Protection
Przejrzyj listę funkcji i informacje o subskrypcji z [cennik usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection) strony, aby upewnić się, że Twoja organizacja ma subskrypcję, która obejmuje funkcjonalność i funkcje, których można oczekiwać. Następnie przypisz licencję z tej subskrypcji do poszczególnych użytkowników w organizacji, którzy będą chronić dokumenty i wiadomości e-mail.

Uwaga: Nie przypisuj ręcznie licencji użytkownika z bezpłatnej subskrypcji usługi RMS dla użytkowników indywidualnych ani nie używaj tej licencji do administrowania usługą Azure Rights Management dla swojej organizacji. Te licencje są wyświetlane jako usługa **Rights Management Adhoc** w Centrum administracyjnym usługi Office 365 i **RIGHTSMANAGEMENT_ADHOC** po uruchomieniu polecenia cmdlet programu PowerShell usługi Azure AD [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx). Aby uzyskać więcej informacji dotyczących sposobu automatycznego przyznawania subskrypcji usługi RMS dla użytkowników indywidualnych i jej przypisywania do użytkowników, zobacz [Usługa RMS dla użytkowników indywidualnych i Azure Information Protection](./rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Krok 2: Przygotowanie dzierżawy do używania usługi Azure Information Protection
Przed rozpoczęciem korzystania z usług ochrony usługi Azure Information Protection, należy wykonać następujące przygotowania:

1.  Upewnij się, że dzierżawa usługi Office 365 obejmuje konta użytkowników i grupy, które będą używane przez usługę Azure Information Protection do uwierzytelniania i autoryzowania użytkowników z organizacji. W razie potrzeby utwórz to konto i grupy lub zsynchronizuj je z katalogu lokalnego. Aby uzyskać więcej informacji, zobacz artykuł [Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection](prepare.md).

2. Określ, czy Twoim kluczem dzierżawy powinna zarządzać firma Microsoft (opcja domyślna), czy też chcesz wygenerować klucz dzierżawy i zarządzać nim samodzielnie (opcja nazywana „przynieś własny klucz”, BYOK). Aby uzyskać więcej informacji, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](plan-implement-tenant-key.md).

3. Zainstaluj moduł programu PowerShell dla usługi AADRM na co najmniej jeden komputer, który ma dostęp do Internetu. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Instalowanie modułu AADRM programu PowerShell](./install-powershell.md).

4. Jeśli obecnie używasz usługi AD RMS: Przeprowadź migrację, aby przenieść klucze, szablony i adresy URL do chmury. Aby uzyskać więcej informacji, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

5. Upewnij się, że usługi ochrony jest aktywna, więc możesz zacząć chronić dokumenty i wiadomości e-mail. Jeśli wymagane jest wdrożenie etapowe, skonfiguruj kontrolki dołączania użytkowników, aby ograniczyć użytkowanie do określonych użytkowników. Aby uzyskać więcej informacji, zobacz [Aktywacja usługi Azure Rights Management](./activate-service.md).

Opcjonalnie rozważ skonfigurowanie następujących elementów:

-   Szablony niestandardowe ustawienia ochrony, jeśli domyślne szablony nie są wystarczające dla Twojej organizacji. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](./configure-policy-templates.md).

- Rejestrowania użycia, tak że można monitorować, jak Twoja organizacja używa usługi ochrony. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](./log-analyze-usage.md).

### <a name="step-3-install-the-client-and-configure-applications-and-services-for-rights-management"></a>Krok 3. Zainstaluj klienta i skonfiguruj aplikacje i usługi dla usług Rights Management

1. Wdrażanie klienta usługi Azure Information Protection
    
    Instalacja usługi Azure Information Protection daje użytkownikom liczne korzyści, takie jak obsługa pakietu Office 2010, ochrona plików innych niż dokumenty pakietu Office i wiadomości e-mail oraz możliwość śledzenia dokumentów chronionych. Zapewnij użytkownikom szkolenia z zakresu korzystania z tego klienta. Więcej informacji zawiera temat [Klient usługi Azure Information Protection dla systemu Windows](./rms-client/aip-client.md).

2. Skonfiguruj aplikacje pakietu Office i usługi
    
    Skonfiguruj aplikacje i usługi pakietu Office pod kątem funkcji zarządzania prawami do informacji (IRM) w usłudze SharePoint Online lub Exchange Online. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](./configure-applications.md).

3. Konfigurowanie funkcji administratora na potrzeby odzyskiwania danych
    
    Jeśli masz istniejące usługi IT, które wymagają inspekcji plików, które ma być chroniony przez usługę Azure Information Protection — takie jak data rozwiązania zapobiegania wyciekom (DLP), bramy szyfrowania zawartości (CEG) i produkty chroniące przed złośliwym kodem — Skonfiguruj konta usług jako super Użytkownicy usługi Azure Rights Management. Aby uzyskać więcej informacji, zobacz [Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](./configure-super-users.md).

4. Zbiorcza ochrona plików — w razie potrzeby 
    
    Polecenia cmdlet programu PowerShell umożliwiają zbiorczą ochronę lub zbiorcze wyłączenie ochrony plików wielu typów i są automatycznie instalowane z klientem usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz temat [Używanie środowiska PowerShell z klientem usługi Azure Information Protection](./rms-client/client-admin-guide-powershell.md) w podręczniku administratora.

5. Wdrażanie łącznika na serwerach lokalnych
    
    W przypadku usług lokalnych, które mają korzystać z usługi ochrony należy zainstalować i skonfigurować łącznik usługi Rights Management. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](./deploy-rms-connector.md).


### <a name="step-4-use-and-monitor-your-data-protection-solutions"></a>Krok 4. Rozpoczęcie korzystania i monitorowania rozwiązań ochrony danych
Teraz możesz przystąpić do ochrony danych i zaloguj się, jak firma korzysta z usługi ochrony. Aby uzyskać więcej informacji dotyczących tej fazy wdrożenia, zobacz [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](./help-users.md) oraz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](./log-analyze-usage.md).

Jeśli interesuje Cię automatyczne chronienie plików przy użyciu infrastruktury klasyfikacji plików na serwerze plików opartym na systemie Windows, zobacz temat [Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) w systemie Windows Server](./rms-client/configure-fci.md).

### <a name="step-5-administer-the-protection-service-for-your-tenant-account-as-needed"></a>Krok 5: Przystąpienie do zarządzania usługą ochrony dla danego konta dzierżawy zgodnie z potrzebami
Po rozpoczęciu korzystania z usługi ochrony programu PowerShell może być przydatna do ułatwia tworzenie skryptów i automatyzację zmian administracyjnych. Aby uzyskać więcej informacji, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](./administer-powershell.md).
