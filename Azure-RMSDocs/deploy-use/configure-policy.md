---
title: Konfigurowanie zasad usługi Azure Information Protection
description: Aby skonfigurować klasyfikację, etykiety i ochronę, musisz skonfigurować zasady usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/22/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: e8d641fd3165346ab052daad7ec7040b0d9e543f
ms.sourcegitcommit: 94d1c7c795e305444e9fde17ad73e46f242bcfa9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2018
---
# <a name="configuring-the-azure-information-protection-policy"></a>Konfigurowanie zasad usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

>[!NOTE]
> W tym artykule odzwierciedla najnowsze aktualizacje do portalu Azure, które pozwalają tworzyć etykiety niezależnie od globalnych zasad lub zakresie zasad. Opcję, aby opublikować zasady zostaną również usunięte. Jeśli dzierżawy nie jest jeszcze zaktualizowane dla tych zmian — na przykład nadal zobacz **publikowania** opcja dla usługi Azure Information Protection i nie ma **klasyfikacje** opcji menu — należy odczekać kilka dni i następnie wróć do niniejszych instrukcji.

Aby skonfigurować klasyfikację, etykiety i ochronę, musisz skonfigurować zasady usługi Azure Information Protection. Te zasady są pobierane na komputery z zainstalowanym [klientem usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

## <a name="subscription-support"></a>Obsługa subskrypcji

Usługa Azure Information Protection obsługuje różne poziomy subskrypcji:

- Subskrypcja P2 usługi Azure Information Protection: obsługa wszystkich funkcji klasyfikacji, etykietowania i ochrony.

- Subskrypcja P1 usługi Azure Information Protection: obsługa większości funkcji klasyfikacji, etykietowania i ochrony, ale nie automatycznej klasyfikacji ani funkcji HYOK.

- Usługa Office 365 obejmująca usługę Azure Rights Management: obsługa ochrony, ale nie klasyfikacji i etykietowania.

Opcje, które wymagają subskrypcji usługi Azure Information Protection P2 są identyfikowane w portalu.

Jeśli Twoja organizacja ma różnych subskrypcji, jest obowiązek upewnij się, że użytkownicy nie używają funkcji, które konta nie jest licencjonowany do użycia. Azure Information Protection, klient nie nie licencji sprawdzanie i wymuszania. Po skonfigurowaniu opcji, które nie wszyscy użytkownicy mają licencji, użyj zakres zasady lub ustawienia rejestru, aby upewnić się, że Twoja organizacja jest zgodność z licencji:

- **Jeśli Twoja organizacja ma mieszane licencje usługi Azure Information Protection P1 i Azure Information Protection P2**: dla użytkowników, którzy mają P2 licencji, Utwórz i użyj jednej lub kilku [zakres zasad](configure-policy-scope.md) podczas konfigurowania opcji które wymagają licencji usługi Azure Information Protection P2. Upewnij się, że globalne zasady zawierają opcje, które wymagają licencji usługi Azure Information Protection P2.

- **Jeśli Twoja organizacja ma subskrypcję usługi Azure Information Protection, ale w przypadku niektórych użytkowników ma tylko licencji dla usługi Office 365 obejmującą usługę Azure Rights Management**: dla użytkowników, którzy nie mają licencji usługi Azure Information Protection Edytuj rejestr na komputerach, bez pobierania zasad usługi Azure Information Protection. Aby uzyskać instrukcje, zobacz Przewodnik administratora do następujących dostosowania: [Wymuś ochrony trybu tylko gdy organizacja ma mieszane licencje](../rms-client/client-admin-guide-customizations.md#enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses).

Aby uzyskać więcej informacji o subskrypcjach, zobacz temat [Jaka subskrypcja jest potrzebna do korzystania z usługi Azure Information Protection i jakie funkcje obejmuje ta subskrypcja?](../get-started/faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)

## <a name="signing-in-to-the-azure-portal"></a>Logowanie do portalu Azure

Aby zalogować się do portalu Azure, do konfigurowania i zarządzania usługi Azure Information Protection:

- Użyj następującego łącza: https://portal.azure.com

- Użyj konta, które ma jeden z następujących [ról administratora](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
    - **Administrator ochrona informacji**

    - **Administrator zabezpieczeń**

    - **Administrator globalny / Administrator firmy**


## <a name="to-access-the-azure-information-protection-blade-for-the-first-time"></a>Aby dostęp do bloku usługi Azure Information Protection po raz pierwszy

1. Zaloguj się do witryny Azure Portal.

2. W menu centralnym kliknij **Utwórz zasób**, a następnie, z **MARKETPLACE** listy, wybierz **bezpieczeństwo i Obsługa tożsamości**. 
    
3. Na **zabezpieczeń + Identyfikuj** bloku z **POLECANE aplikacje** listy, wybierz **usługi Azure Information Protection**. Następnie na **usługi Azure Information Protection** bloku, kliknij przycisk **Utwórz**.
    
    Ta akcja tworzy **usługi Azure Information Protection** bloku dla dzierżawy, dzięki czemu przy następnym logowaniu do portalu, możesz wybrać usługę z koncentratora **wszystkie usługi** listy. 
    
    > [!TIP] 
    > Wybierz opcję **Przypnij do pulpitu nawigacyjnego**, aby utworzyć kafelek usługi **Azure Information Protection** na pulpicie nawigacyjnym, dzięki czemu można będzie pominąć krok przeglądania w poszukiwaniu usługi przy następnym zalogowaniu w witrynie portalu.

4. Zostanie wyświetlony **szybki start** stroną wyświetlaną automatycznie połączyć się z usługą po raz pierwszy. Przejrzyj sugerowane zasoby, lub użyj opcji menu. Aby skonfigurować etykiety, które użytkownicy mogą wybrać, użyj następującej procedury.

Następny czas dostępu **usługi Azure Information Protection** bloku, powoduje automatyczne wybranie **etykiety** opcję, dzięki czemu można wyświetlić i skonfigurować etykiety dla wszystkich użytkowników. Możesz wrócić do **szybki start** strony, wybierając ją z **ogólne** menu.

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Jak skonfigurować zasady usługi Azure Information Protection

1. Upewnij się, że użytkownik jest zalogowany do portalu Azure za pomocą jednej z tych ról administracyjnych: Administrator ochrony informacji, zabezpieczeń administratora lub administratora globalnego. Zobacz [powyższej sekcji](#signing-in-to-the-azure-portal) uzyskać więcej informacji o tych ról administracyjnych.

2. Jeśli to konieczne, przejdź do **usługi Azure Information Protection** bloku: na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **Information Protection** w Pole filtru. Spośród wyników wybierz **Azure Information Protection**. 
    
    **Usługi Azure Information Protection — etykiety** automatycznie zostanie otwarty blok można wyświetlić i edytować dostępne etykiety. Etykiety mogą udostępniane wszystkim użytkownikom, wybranych użytkowników lub użytkownicy nie przez dodanie lub usunięcie ich z zasad.

3. Aby wyświetlić i edytować zasady, wybierz **zasady** z opcji menu. Aby wyświetlić i edytować zasad, które pobrania wszystkich użytkowników, wybierz **Global** zasad. Aby utworzyć zasady niestandardowe dla wybranych użytkowników, wybierz **dodać nową zasadę**.
    
    Zasady usługi Azure Information Protection zawiera następujące elementy, które można skonfigurować:
    
    - Etykiety, które są dołączone które pozwalają Administratorzy i użytkownicy klasyfikować dokumenty i wiadomości e-mail.
    
    - Tytuł i etykietka narzędzia paska usługi Information Protection, które użytkownicy zobaczą w swoich aplikacjach pakietu Office.
    
    - Opcja ustawienia etykiety domyślnej jako punktu wyjścia dla klasyfikowania dokumentów i wiadomości e-mail.
     
    - Opcja wymuszenia klasyfikacji w momencie zapisywania dokumentów i wysyłania wiadomości e-mail przez użytkowników.
    
    - Opcja monitowania użytkowników o podanie przyczyny wybrania etykiety, która ma niższą charakterystykę niż oryginalna.
    
    - Opcja automatycznego określania etykiety wiadomości e-mail na podstawie jej załączników.

    - Opcji, aby określić czy pasek Information Protection jest wyświetlany w aplikacji pakietu Office.

    - Opcja kontrolująca, czy przycisk nie przesyłaj dalej jest wyświetlany w programie Outlook.
    
    - Opcja umożliwia użytkownikowi określenie własnych uprawnień dla dokumentów.
    
    - Opcja udostępniania linku do niestandardowej pomocy dla użytkowników.

Usługa Azure Information Protection obejmuje [domyślne zasady](configure-policy-default.md), które zawierają pięć głównych etykiet. Dwa z tych etykiet zawiera sublabels zapewnienie podkategorie, w razie potrzeby. Po skonfigurowaniu etykiety dla sublabels użytkowników nie można wybrać etykietę głównego, ale należy wybrać jedną z sublabels.

Etykiety usługi Azure Information Protection może służyć z pełnego zakresu danych, które organizacji zwykle tworzy i przechowuje z najniższą klasyfikacji danych osobowych, do najwyższej klasyfikacji wysoce poufnych danych. 

Możesz użyć domyślnych etykiet bez wprowadzania zmian, dostosować etykiety lub usunąć je, a także utworzyć nowe etykiety. Aby uzyskać więcej informacji, użyj linków z następnej sekcji w celu ułatwienia znalezienia odpowiednich opcji i sposobów ich konfigurowania.

Można utworzyć dowolną liczbę etykiet. Jednak po rozpoczęciu uzyskanie zbyt duża, aby użytkownicy mogli łatwo oglądać i wybierz etykietę prawym utworzyć zakresie zasad, aby użytkownicy widzieli tylko etykiety, które są istotne dla nich. Brak górny limit dla etykiety, które stosują ochronę, który wynosi 500.

Po wprowadzeniu zmian w bloku Azure Information Protection kliknij przycisk **Zapisz**, aby zapisać te zmiany lub kliknij przycisk **Odrzuć**, aby przywrócić stan do ostatnio zapisanych ustawień. Zapisz zmiany w zasadach lub zmiany zmiany do etykiet, które są dodawane do zasady, zmiany te są automatycznie publikowane. Nie istnieje żadne oddzielne opcja publikowania.

Klient usługi Azure Information Protection sprawdza zmiany podczas uruchamiania obsługiwanej aplikacji pakietu Office i pobiera zmiany jako najnowsze zasady usługi Azure Information Protection. Dodatkowe wyzwalacze powodujące odświeżenie zasad na komputerze klienckim:

- Kliknięcie prawym przyciskiem myszy w celu sklasyfikowania i ochrony pliku lub folderu.

- Uruchamianie [poleceń cmdlet programu PowerShell](../rms-client/client-admin-guide-powershell.md) mających na celu etykietowanie oraz ochronę (Get-AIPFileStatus, Set-AIPFileClassification i Set-AIPFileLabel).

- Upływ kolejnych 24 godzin.

- Aby uzyskać [skanera ochrony informacji Azure](deploy-aip-scanner.md): podczas uruchamiania usługi, (Jeśli zasady są starsze niż godzinę), a co godzinę, podczas operacji.


>[!NOTE]
>Gdy klient pobierze zasady, przygotuj się na odczekanie paru minut, zanim staną się w pełni funkcjonalne. Rzeczywisty czas może być różny w zależności od takich czynników, jak rozmiar i złożoność konfiguracji zasad oraz łączność sieciowa. Jeśli wynikowe działanie etykiet nie odpowiada najnowszym zmianom, zaczekaj do 15 minut i spróbuj ponownie.

### <a name="configuring-your-organizations-policy"></a>Konfigurowanie zasad organizacji

Skorzystaj z poniższych informacji, aby skonfigurować zasady usługi Azure Information Protection:

- [Domyślne zasady usługi Information Protection](configure-policy-default.md)

- [Konfigurowanie ustawień zasad](configure-policy-settings.md)

- [Tworzenie nowej etykiety](configure-policy-new-label.md)

- [Jak dodać lub usunąć etykiety](configure-policy-add-remove-label.md)
 
- [Usuwanie lub zmiana kolejności etykiet](configure-policy-delete-reorder.md)

- [Zmiana lub dostosowanie istniejącej etykiety](configure-policy-change-label.md)

- [Konfigurowanie etykiety w celu zastosowania ochrony](configure-policy-protection.md)

- [Konfigurowanie etykiety w celu zastosowania oznaczeń wizualnych](configure-policy-markings.md)

- [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej](configure-policy-classification.md)

- [Konfigurowanie zasad dla konkretnych użytkowników poprzez użycie zasad o określonym zakresie](configure-policy-scope.md)

- [Konfigurowanie szablonów i zarządzanie nimi](configure-policy-templates.md)

- [Konfigurowanie etykiet w różnych językach](configure-policy-languages.md)

## <a name="next-steps"></a>Następne kroki

Aby uzyskać przykład konfigurowania zasad domyślnych i zobaczyć efekty w aplikacji pakietu Office, wypróbuj [Samouczek Szybki start dla usługi Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
