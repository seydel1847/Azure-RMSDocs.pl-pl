---
title: "Plan wdrożenia usługi Azure Information Protection | Azure Information Protection"
description: "Skorzystaj z tych procedur, aby przygotować się do wdrożenia usługi Azure Information Protection, przeprowadzić to wdrożenie, a następnie zarządzać usługą Azure Information Protection w swojej organizacji."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 884a4528da6fa79d92f39fa08860773bcc5552d3


---

# <a name="azure-information-protection-deployment-roadmap"></a>Plan wdrażania usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Skorzystaj z poniższych procedur, aby przygotować się do wdrożenia usługi Azure Information Protection, przeprowadzić to wdrożenie, a następnie zarządzać usługą Azure Information Protection w swojej organizacji.

Jeśli jednak chcesz szybko wypróbować usługę Azure Information Protection we własnym zakresie zamiast wdrażać ją w środowisku produkcyjnym, zobacz [Samouczek Szybki start dotyczący usługi Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

> [!IMPORTANT]
> Przed wykonaniem poniższych kroków zapoznaj się z tematem [Wymagania dotyczące usługi Azure Information Protection](../get-started/requirements-azure-rms.md).

Wybierz plan wdrożenia, który jest odpowiedni dla Twojej organizacji i uwzględnia [subskrypcje zawierające potrzebne funkcje i możliwości](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features):

- [Korzystanie z funkcji klasyfikacji, etykietowania i ochrony](#deployment-roadmap-for-classification-labeling-and-protection)

- [Korzystanie tylko z funkcji ochrony danych](#deployment-roadmap-for-data-protection-only)


## <a name="deployment-roadmap-for-classification-labeling-and-protection"></a>Mapa wdrożenia funkcji klasyfikacji, etykietowania i ochrony

> [!NOTE]
> Już używasz usługi Azure Rights Management do ochrony danych? Możesz pominąć wiele z tych czynności i skoncentrować się na krokach 3 i 5.1.

### <a name="step-1-confirm-your-subscription-and-assign-user-licenses"></a>Krok 1: Potwierdzenie informacji o subskrypcji i przypisanie licencji użytkowników
Przejrzyj [informacje o subskrypcji](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) i [listę funkcji](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection, aby upewnić się, że Twoja organizacja korzysta z subskrypcji obejmującej oczekiwane funkcje i możliwości. Następnie przypisz licencję z tej subskrypcji do poszczególnych użytkowników w organizacji, którzy będą zajmować się klasyfikacją, etykietowaniem i ochroną dokumentów i wiadomości e-mail.

### <a name="step-2-prepare-your-tenant-account-to-use-azure-information-protection"></a>Krok 2: Przygotowanie konta dzierżawy do używania usługi Azure Information Protection
Przed rozpoczęciem korzystania z usługi Azure Information Protection należy wykonać następujące przygotowania:

- Upewnij się, że masz konta użytkowników i grupy w usłudze Office 365 lub Azure Active Directory, które będą używane przez usługę Azure Information Protection do uwierzytelniania użytkowników z Twojej organizacji. W razie potrzeby utwórz to konto i grupy lub zsynchronizuj je z katalogu lokalnego. Aby uzyskać więcej informacji, zobacz [Przygotowanie do korzystania z usługi Azure Information Protection](prepare.md).

### <a name="step-3-configure-and-deploy-classification-and-labeling"></a>Krok 3: Skonfigurowanie i wdrożenie funkcji klasyfikacji i etykietowania

Jeśli nie masz jeszcze strategii dotyczącej klasyfikacji, przejrzyj [domyślne zasady usługi Azure Information Protection](../deploy-use/configure-policy-default.md) i na ich podstawie zdecyduj, jakie etykiety klasyfikacji przypisać do danych Twojej organizacji. Możesz je dostosować tak, aby spełniały wymagania Twojej firmy. 

Zmień konfigurację domyślnych etykiet usługi Azure Information Protection, aby wprowadzić wszelkie zmiany wymagane w odniesieniu do Twoich decyzji dotyczących klasyfikacji. Skonfiguruj zasady w zakresie ręcznego etykietowania przez użytkowników i napisz dla nich wskazówki objaśniające, jakie etykiety należy stosować w poszczególnych sytuacjach. Aby uzyskać więcej informacji o metodach konfigurowania zasad usługi Azure Information Protection, zobacz [Konfigurowanie zasad usługi Azure Information Protection](../deploy-use/configure-policy.md).

Następnie wdróż klienta usługi Azure Information Protection dla użytkowników i zapewnij dla niego pomoc techniczną, oferując użytkownikom szkolenia i instrukcje dotyczące tego, w jakich sytuacjach należy wybierać poszczególne etykiety. Aby uzyskać więcej informacji dotyczących instalowania klienta, zobacz [Instalowanie klienta usługi Azure Information Protection](../rms-client/info-protect-client.md).

Po pewnym czasie, gdy użytkownicy nabiorą wprawy w etykietowaniu dokumentów i wiadomości e-mail, wprowadź bardziej zaawansowane konfiguracje. Mogą one obejmować następujące działania i elementy:

- Stosowanie etykiety domyślnej

- Monitowanie użytkowników o uzasadnienie w przypadku wybrania etykiety o niższym poziomie klasyfikacji

- Wprowadzenie obowiązkowego etykietowania wszystkich dokumentów i wiadomości e-mail

- Niestandardowe nagłówki, stopki lub znaki wodne

- Warunki w celu zapewniania obsługi rekomendacji i etykietowania automatycznego

Na tym etapie nie należy wybierać opcji ochrony dokumentów i wiadomości e-mail.

### <a name="step-4-prepare-for-rights-management-data-protection"></a>Krok 4: Przygotowanie do ochrony danych za pomocą usługi Rights Management

Gdy użytkownicy nabiorą wprawy w etykietowaniu dokumentów i wiadomości e-mail, możesz przystąpić do wprowadzania funkcji ochrony danych dla najbardziej poufnych danych. Ten etap wymaga następujących przygotowań pod kątem usługi Azure Rights Management:

1. Określ, czy Twoim kluczem dzierżawy powinna zarządzać firma Microsoft (opcja domyślna), czy też chcesz wygenerować klucz dzierżawy i zarządzać nim samodzielnie (opcja nazywana „przynieś własny klucz”, BYOK). Pamiętaj, że obecnie nie możesz korzystać z opcji BYOK, jeśli używasz usługi Exchange Online. Aby uzyskać więcej informacji, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](plan-implement-tenant-key.md).

2. Zainstaluj moduł Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] na co najmniej jednym komputerze z dostępem do Internetu. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

3. Jeśli obecnie używasz lokalnych usług Rights Management: przeprowadź migrację, aby przenieść klucze, szablony i adresy URL do chmury. Aby uzyskać więcej informacji, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

4. Aktywuj usługę Azure Rights Management, aby można było zacząć chronić dokumenty i wiadomości e-mail. Jeśli wymagane jest wdrożenie etapowe, skonfiguruj kontrolki dołączania użytkowników, aby ograniczyć użytkowanie do określonych użytkowników. Aby uzyskać więcej informacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

Opcjonalnie rozważ skonfigurowanie następujących elementów:

-   Szablony niestandardowe, jeśli domyślne szablony zasad praw nie są wystarczające dla Twojej organizacji. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

-   Rejestrowanie użytkowania, umożliwiające monitorowanie wykorzystania usługi Rights Management przez organizację. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).

### <a name="step-5-configure-your-azure-information-protection-policy-applications-and-services-for-rights-management-data-protection"></a>Krok 5: Skonfigurowanie zasad, aplikacji i usług Azure Information Protection pod kątem funkcji ochrony danych usługi Rights Management

1. Aktualizowanie zasad usługi Azure Information Protection w celu zastosowania funkcji ochrony danych
    
    Zmodyfikuj zasady usługi Azure Information Protection w taki sposób, aby co najmniej jedna etykieta stosowała funkcje ochrony usługi Rights Management. Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiety w celu zastosowania ochrony usługi Rights Management](../deploy-use/configure-policy-protection.md).

2. Wdrażanie aplikacji RMS sharing
    
    Zainstaluj aplikację RMS sharing dla użytkowników, aby mogli bezpiecznie udostępniać dokumenty za pomocą poczty e-mail, stosować miejscową ochronę plików i śledzić udostępnione przez siebie dokumenty, dla których włączyli ochronę. Zapewnij użytkownikom szkolenia dotyczące tej aplikacji. Aby uzyskać więcej informacji, zobacz [Aplikacja do udostępniania usługi Rights Management dla systemu Windows](../rms-client/sharing-app-windows.md).

3. Konfigurowanie aplikacji i usług pakietu Office pod kątem funkcji IRM
    
    Skonfiguruj aplikacje i usługi pakietu Office pod kątem funkcji zarządzania prawami do informacji (IRM) w usłudze SharePoint Online lub Exchange Online. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](../deploy-use/configure-applications.md).

4. Konfigurowanie funkcji administratora na potrzeby odzyskiwania danych
    
    Jeśli masz istniejące usługi IT, które wymagają inspekcji plików chronionych przez usługę Azure Rights Management, takie jak rozwiązania zapobiegania wyciekom danych (DLP), bramy szyfrowania zawartości (CEG) i produkty chroniące przed złośliwym oprogramowaniem, skonfiguruj konta usług jako administratorów usługi Azure Rights Management. Aby uzyskać więcej informacji, zobacz [Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).

5. Zbiorcza ochrona plików 
    
    Aby włączyć funkcje zbiorczej ochrony i wyłączania ochrony wszystkich typów plików, zainstaluj narzędzie RMS Protection Tool, które korzysta z modułu RMS Protection PowerShell. Aby uzyskać więcej informacji, zobacz [Polecenia cmdlet narzędzia RMS Protection](https://msdn.microsoft.com/library/mt433195.aspx).

6. Wdrażanie łącznika na serwerach lokalnych
    
    Jeśli masz usługi lokalne, których chcesz używać z usługą Azure Rights Management, zainstaluj i skonfiguruj łącznik usługi Rights Management. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

### <a name="step-4-use-and-monitor-your-data-protection-solutions"></a>Krok 4. Rozpoczęcie korzystania i monitorowania rozwiązań ochrony danych
Masz teraz wszystko gotowe do rozpoczęcia ochrony danych oraz rejestrowania sposobu korzystania z usługi Rights Management przez firmę. Aby uzyskać więcej informacji dotyczących tej fazy wdrożenia, zobacz [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](../deploy-use/help-users.md) oraz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).

Jeśli interesuje Cię automatyczne chronienie plików przy użyciu infrastruktury klasyfikacji plików na serwerze plików opartym na systemie Windows, zobacz temat [Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) w systemie Windows Server](../rms-client/configure-fci.md).

### <a name="step-5-administer-the-rights-management-service-for-your-tenant-account-as-needed"></a>Krok 5. Przystąpienie do zarządzania usługą Rights Management dla danego konta dzierżawy zgodnie z potrzebami
Po rozpoczęciu korzystania z usługi Azure Rights Management pomocny może okazać się program Windows PowerShell, który ułatwia tworzenie skryptów i automatyzację zmian administracyjnych. Aby uzyskać więcej informacji, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](../deploy-use/administer-powershell.md).


## <a name="deployment-roadmap-for-data-protection-only"></a>Plan wdrożenia obejmujący tylko funkcje ochrony danych

### <a name="step-1-confirm-that-you-have-a-subscription-that-includes-azure-rights-management"></a>Krok 1. Sprawdź, czy masz subskrypcję obejmującą usługę Azure Rights Management
Przejrzyj [informacje o subskrypcji](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) i [listę funkcji](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) w witrynie usługi Azure Information Protection, aby upewnić się, że Twoja organizacja korzysta z subskrypcji obejmującej oczekiwane funkcje i możliwości. Następnie przypisz licencję z tej subskrypcji do poszczególnych użytkowników w organizacji, którzy będą zajmować się ochroną dokumentów i wiadomości e-mail za pomocą usługi Azure Rights Management.

### <a name="step-2-prepare-your-tenant-account-to-use-the-azure-rights-management-service"></a>Krok 2. Przygotowanie konta dzierżawy do używania usługi Rights Management
Przed rozpoczęciem korzystania z usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] przeprowadź następujące przygotowania:

1.  Upewnij się, że dzierżawa usługi Office 365 obejmuje konta użytkowników i grupy, które będą używane przez usługę Azure Information Protection do uwierzytelniania użytkowników z organizacji. W razie potrzeby utwórz to konto i grupy lub zsynchronizuj je z katalogu lokalnego. Aby uzyskać więcej informacji, zobacz [Przygotowanie do wdrożenia usługi Azure Rights Management](prepare.md).

2. Określ, czy Twoim kluczem dzierżawy powinna zarządzać firma Microsoft (opcja domyślna), czy też chcesz wygenerować klucz dzierżawy i zarządzać nim samodzielnie (opcja nazywana „przynieś własny klucz”, BYOK). Pamiętaj, że obecnie nie możesz korzystać z opcji BYOK, jeśli używasz usługi Exchange Online. Aby uzyskać więcej informacji, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](plan-implement-tenant-key.md).

3. Zainstaluj moduł Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] na co najmniej jednym komputerze z dostępem do Internetu. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

4. Jeśli obecnie używasz lokalnych usług Rights Management: przeprowadź migrację, aby przenieść klucze, szablony i adresy URL do chmury. Aby uzyskać więcej informacji, zobacz [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

5. Aktywuj usługę Rights Management, aby rozpocząć korzystanie z usługi. Jeśli wymagane jest wdrożenie etapowe, skonfiguruj kontrolki dołączania użytkowników, aby ograniczyć użytkowanie do określonych użytkowników. Aby uzyskać więcej informacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

Opcjonalnie rozważ skonfigurowanie następujących elementów:

-   Szablony niestandardowe, jeśli domyślne szablony zasad praw nie są wystarczające dla Twojej organizacji. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

-   Rejestrowanie użytkowania, umożliwiające monitorowanie wykorzystania usługi Rights Management przez organizację. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).

### <a name="step-3-configure-your-applications-and-services-for-rights-management"></a>Krok 3. Skonfiguruj aplikacje i usługi dla usługi Rights Management

1. Wdrażanie aplikacji RMS sharing
    
    Zainstaluj aplikację RMS sharing dla użytkowników, aby mogli bezpiecznie udostępniać dokumenty za pomocą poczty e-mail, stosować miejscową ochronę plików i śledzić udostępnione przez siebie dokumenty, dla których włączyli ochronę. Zapewnij użytkownikom szkolenia dotyczące tej aplikacji. Aby uzyskać więcej informacji, zobacz [Aplikacja do udostępniania usługi Rights Management dla systemu Windows](../rms-client/sharing-app-windows.md).

2. Konfigurowanie aplikacji i usług pakietu Office pod kątem funkcji IRM
    
    Skonfiguruj aplikacje i usługi pakietu Office pod kątem funkcji zarządzania prawami do informacji (IRM) w usłudze SharePoint Online lub Exchange Online. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](../deploy-use/configure-applications.md).

3. Konfigurowanie funkcji administratora na potrzeby odzyskiwania danych
    
    Jeśli masz istniejące usługi IT, które wymagają inspekcji plików chronionych przez usługę Azure Rights Management, takie jak rozwiązania zapobiegania wyciekom danych (DLP), bramy szyfrowania zawartości (CEG) i produkty chroniące przed złośliwym oprogramowaniem, skonfiguruj konta usług jako administratorów usługi Azure Rights Management. Aby uzyskać więcej informacji, zobacz [Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).

4. Zbiorcza ochrona plików 
    
    Aby włączyć funkcje zbiorczej ochrony i wyłączania ochrony wszystkich typów plików, zainstaluj narzędzie RMS Protection Tool, które korzysta z modułu RMS Protection PowerShell. Aby uzyskać więcej informacji, zobacz [Polecenia cmdlet narzędzia RMS Protection](https://msdn.microsoft.com/library/mt433195.aspx).

5. Wdrażanie łącznika na serwerach lokalnych
    
    Jeśli masz usługi lokalne, których chcesz używać z usługą Azure Rights Management, zainstaluj i skonfiguruj łącznik usługi Rights Management. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).


### <a name="step-4-use-and-monitor-your-data-protection-solutions"></a>Krok 4. Rozpoczęcie korzystania i monitorowania rozwiązań ochrony danych
Masz teraz wszystko gotowe do rozpoczęcia ochrony danych oraz rejestrowania sposobu korzystania z usługi Rights Management przez firmę. Aby uzyskać więcej informacji dotyczących tej fazy wdrożenia, zobacz [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](../deploy-use/help-users.md) oraz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).

Jeśli interesuje Cię automatyczne chronienie plików przy użyciu infrastruktury klasyfikacji plików na serwerze plików opartym na systemie Windows, zobacz temat [Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) w systemie Windows Server](../rms-client/configure-fci.md).

### <a name="step-5-administer-the-rights-management-service-for-your-tenant-account-as-needed"></a>Krok 5. Przystąpienie do zarządzania usługą Rights Management dla danego konta dzierżawy zgodnie z potrzebami
Po rozpoczęciu korzystania z usługi Azure Rights Management pomocny może okazać się program Windows PowerShell, który ułatwia tworzenie skryptów i automatyzację zmian administracyjnych. Aby uzyskać więcej informacji, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](../deploy-use/administer-powershell.md).





<!--HONumber=Nov16_HO2-->


