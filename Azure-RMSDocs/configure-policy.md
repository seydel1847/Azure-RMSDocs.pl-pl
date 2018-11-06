---
title: Konfigurowanie zasad usługi Azure Information Protection
description: Aby skonfigurować klasyfikację, etykiety i ochronę, musisz skonfigurować zasady usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 98c3d09a72a74ce8f2abc679df1e155b3a9ee5d8
ms.sourcegitcommit: 80de8762953bdea2553c48b02259cd107d0c71dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51026591"
---
# <a name="configuring-the-azure-information-protection-policy"></a>Konfigurowanie zasad usługi Azure Information Protection

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Aby skonfigurować klasyfikację, etykiety i ochronę, musisz skonfigurować zasady usługi Azure Information Protection. Te zasady są pobierane na komputery z zainstalowanym [klientem usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Zasady zawierają ustawienia i etykiety:

- Etykiety dotyczą wartości klasyfikacji dokumentów i wiadomości e-mail i opcjonalnie można chronić tej zawartości. Klient usługi Azure Information Protection jest wyświetlany tych etykiet dla użytkowników w aplikacjach pakietu Office i użytkownicy kliknij prawym przyciskiem myszy w Eksploratorze plików. Etykiety te mogą być stosowane również za pomocą programu PowerShell i skanera usługi Azure Information Protection.

- Ustawienia, zmienić domyślne zachowanie klienta usługi Azure Information Protection. Na przykład można wybrać etykiety domyślnej, czy wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę i czy ma być wyświetlana na pasku usługi Azure Information Protection w aplikacjach pakietu Office.

## <a name="subscription-support"></a>Obsługa subskrypcji

Usługa Azure Information Protection obsługuje różne poziomy subskrypcji:

- Subskrypcja P2 usługi Azure Information Protection: obsługa wszystkich funkcji klasyfikacji, etykietowania i ochrony.

- Subskrypcja P1 usługi Azure Information Protection: obsługa większości funkcji klasyfikacji, etykietowania i ochrony, ale nie automatycznej klasyfikacji ani funkcji HYOK.

- Usługa Office 365 obejmująca usługę Azure Rights Management: obsługa ochrony, ale nie klasyfikacji i etykietowania.

Opcje, które wymagają subskrypcji usługi Azure Information Protection P2 są identyfikowane w portalu.

Jeśli Twoja organizacja ma różne subskrypcje, jest odpowiedzialny za upewnij się, że użytkowników należy używać funkcji, które ich konto nie jest licencjonowany do użycia. Nie usługi Azure Information Protection, w których klient ma licencję, sprawdzenie i wymuszania. Podczas konfigurowania opcji, których nie wszyscy użytkownicy mają licencję usługi, użyj o określonym zakresie, zasady lub ustawienia rejestru, aby upewnić się, że Twoja organizacja pozostaje zgodny z licencji:

- **Jeśli Twoja organizacja ma różne licencje usługi Azure Information Protection P1 i Azure Information Protection P2**: dla użytkowników, którzy mają P2 licencji, tworzenia i używania jednej lub kilku [zasad o określonym zakresie](configure-policy-scope.md) podczas konfigurowania opcji które wymagają licencji usługi Azure Information Protection P2. Upewnij się, że zasady globalne nie zawiera opcje, które wymagają licencji usługi Azure Information Protection P2.

- **Jeśli Twoja organizacja ma subskrypcję usługi Azure Information Protection, ale niektórzy użytkownicy mają tylko licencję usługi Office 365, która obejmuje usługę Azure Rights Management**: dla użytkowników, którzy nie mają licencji usługi Azure Information Protection, należy edytować rejestr na swoich komputerach, dzięki czemu nie będą oni mogli pobrać zasad usługi Azure Information Protection. Instrukcje można znaleźć w podręczniku administratora do następujących dostosowania: [wymusić tryb z samą ochroną, gdy Twoja organizacja ma mieszane licencje](./rms-client/client-admin-guide-customizations.md#enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses).

Aby uzyskać więcej informacji o subskrypcjach, zobacz temat [Jaka subskrypcja jest potrzebna do korzystania z usługi Azure Information Protection i jakie funkcje obejmuje ta subskrypcja?](faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)

## <a name="signing-in-to-the-azure-portal"></a>Logowanie do witryny Azure portal

Aby zalogować się do witryny Azure portal, aby skonfigurować i zarządzać usługą Azure Information Protection:

- Użyj następującego linku: https://portal.azure.com

- Użyj konta, które ma jedną z następujących [ról administratora](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
    - **Administrator usługi Information Protection**

    - **Administrator zabezpieczeń**

    - **Administrator globalny / Administrator firmy**


## <a name="to-access-the-azure-information-protection-blade-for-the-first-time"></a>Aby uzyskać dostęp do bloku usługi Azure Information Protection po raz pierwszy

1. Zaloguj się do witryny Azure Portal.

2. W menu Centrum wybierz **Utwórz zasób**, a następnie w polu wyszukiwania w portalu Marketplace wpisz **usługi Azure Information Protection**. 
    
3. Wybierz z listy wyników **usługi Azure Information Protection**. Na **usługi Azure Information Protection** bloku kliknij **Utwórz**.
    
    > [!TIP] 
    > Opcjonalnie można zaznaczyć **Przypnij do pulpitu nawigacyjnego** utworzyć **usługi Azure Information Protection** kafelka na pulpicie nawigacyjnym, dzięki czemu można pominąć, przechodząc do usługi przy następnym logowaniu do portalu.
    
    Kliknij przycisk **Utwórz** ponownie.

4. Zostanie wyświetlony **— szybki start** strona, która zostanie automatycznie otwarta po raz pierwszy łączysz się z usługą. Przeglądaj sugerowane zasoby, lub użyj opcji menu. Aby skonfigurować etykiety, które użytkownicy mogą wybrać, użyj następującej procedury.

Następny czas dostęp **usługi Azure Information Protection** bloku powoduje automatyczne wybranie **etykiety** opcję Tak, aby można wyświetlić i skonfigurować etykiety dla wszystkich użytkowników. Możesz wrócić do **— szybki start** strony, wybierając je z **ogólne** menu.

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Jak skonfigurować zasady usługi Azure Information Protection

1. Upewnij się, że użytkownik jest zalogowany do witryny Azure portal przy użyciu jednej z tych ról administracyjnych: Administrator usługi Information Protection, administratora zabezpieczeń lub administratora globalnego. Zobacz [poprzedniej sekcji](#signing-in-to-the-azure-portal) Aby uzyskać więcej informacji na temat tych ról administracyjnych.

2. Jeśli to konieczne, przejdź do **usługi Azure Information Protection** bloku: na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **Information Protection** w Pole filtru. Spośród wyników wybierz **Azure Information Protection**. 
    
    **Usługi Azure Information Protection — etykiety** automatycznie zostanie otwarty blok umożliwia wyświetlanie i edytowanie dostępne etykiety. Etykiety można udostępniane wszystkim użytkownikom, wybranych użytkowników lub żaden użytkownik, dodając lub usuwając je z zasad.

3. Aby wyświetlić i edytować zasady, wybierz **zasady** z opcji menu. Aby wyświetlić i edytować zasady, które uzyskają wszyscy użytkownicy, wybierz **Global** zasad. Aby utworzyć niestandardowe zasady dla wybranych użytkowników, wybierz **Dodawanie nowych zasad**.
    

### <a name="making-changes-to-the-policy"></a>Wprowadzanie zmian do zasad

Można utworzyć dowolną liczbę etykiet. Jednak po uruchomieniu uzyskać zbyt duża, aby użytkownicy mogli łatwo oglądać i wybierz etykietę prawym, utworzyć zasady o określonym zakresie, tak, aby użytkownicy widzieli etykiety, które są z nimi związane. Brak górną granicę dla etykiety umożliwiające objęcie ochroną, który wynosi 500.

Po wprowadzeniu zmian w bloku Azure Information Protection kliknij przycisk **Zapisz**, aby zapisać te zmiany lub kliknij przycisk **Odrzuć**, aby przywrócić stan do ostatnio zapisanych ustawień. Zapisz zmiany w zasadach lub zmiany zmiany etykiet, które są dodawane do zasady, zmiany te są automatycznie publikowane. Nie ma żadnych oddzielne opcja publikowania.

Klient usługi Azure Information Protection sprawdza zmiany podczas uruchamiania obsługiwanej aplikacji pakietu Office i pobiera zmiany jako najnowsze zasady usługi Azure Information Protection. Dodatkowe wyzwalacze powodujące odświeżenie zasad na komputerze klienckim:

- Kliknięcie prawym przyciskiem myszy w celu sklasyfikowania i ochrony pliku lub folderu.

- Uruchamianie [poleceń cmdlet programu PowerShell](./rms-client/client-admin-guide-powershell.md) mających na celu etykietowanie oraz ochronę (Get-AIPFileStatus, Set-AIPFileClassification i Set-AIPFileLabel).

- Upływ kolejnych 24 godzin.

- Aby uzyskać [skaner ochrony informacji Azure](deploy-aip-scanner.md): podczas uruchamiania usługi (Jeśli zasady są starsze niż jedna godzina), a co godzinę, podczas operacji.


>[!NOTE]
>Gdy klient pobierze zasady, przygotuj się na odczekanie paru minut, zanim staną się w pełni funkcjonalne. Rzeczywisty czas może być różny w zależności od takich czynników, jak rozmiar i złożoność konfiguracji zasad oraz łączność sieciowa. Jeśli wynikowe działanie etykiet nie odpowiada najnowszym zmianom, zaczekaj do 15 minut i spróbuj ponownie.

### <a name="configuring-your-organizations-policy"></a>Konfigurowanie zasad organizacji

Skorzystaj z poniższych informacji, aby skonfigurować zasady usługi Azure Information Protection:

- [Domyślne zasady usługi Information Protection](configure-policy-default.md)

- [Konfigurowanie ustawień zasad](configure-policy-settings.md)

- [Tworzenie nowej etykiety](configure-policy-new-label.md)

- [Jak dodać lub usunąć etykietę](configure-policy-add-remove-label.md)
 
- [Usuwanie lub zmiana kolejności etykiet](configure-policy-delete-reorder.md)

- [Zmiana lub dostosowanie istniejącej etykiety](configure-policy-change-label.md)

- [Konfigurowanie etykiety w celu zastosowania ochrony](configure-policy-protection.md)

- [Konfigurowanie etykiety w celu zastosowania oznaczeń wizualnych](configure-policy-markings.md)

- [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej](configure-policy-classification.md)

- [Konfigurowanie zasad dla konkretnych użytkowników poprzez użycie zasad o określonym zakresie](configure-policy-scope.md)

- [Konfigurowanie szablonów i zarządzanie nimi](configure-policy-templates.md)

- [Konfigurowanie etykiet w różnych językach](configure-policy-languages.md)

- [Jak przeprowadzić migrację etykiety usługi Azure Information Protection do Centrum zgodności i zabezpieczeń usługi Office 365](configure-policy-migrate-labels.md)

## <a name="next-steps"></a>Kolejne kroki

Aby uzyskać przykłady sposobów dostosowania zasad usługi Azure Information Protection i zobaczyć efekty dla użytkowników, wypróbuj następujące samouczki:

- [Edytowanie zasad usługi Azure Information Protection i utworzyć nową etykietę i tworzenie nowej etykiety](infoprotect-quick-start-tutorial.md)

- [Konfigurowanie ustawień zasad usługi Azure Information Protection, które współpracują ze sobą](infoprotect-settings-tutorial.md)

Aby dowiedzieć się, jaka jest wydajność swoich zasad, zobacz [raportowania usługi Azure Information Protection](reports-aip.md).

