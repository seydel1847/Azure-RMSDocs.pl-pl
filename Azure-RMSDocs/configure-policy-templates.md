---
title: Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection — AIP
description: Konfigurowanie i zarządzanie nimi szablony usługi rights management, w witrynie Azure portal.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/28/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 6147a065f6aff31dd40c339699f0dc35f1ebaa82
ms.sourcegitcommit: b10df82d9f00b3f826bce38beb7b666ce3f56e84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/28/2018
ms.locfileid: "53814241"
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Szablony ochrony, znany także jako szablony usługi Rights Management to zbiór ustawień ochrony zdefiniowane przez administratora dla usługi Azure Information Protection. Te ustawienia obejmują wybranego [prawa użytkowania](configure-usage-rights.md) dla autoryzowanych użytkowników i kontroli dostępu dla wygaśnięcia i dostęp w trybie offline. Te szablony są zintegrowane z zasadami usługi Azure Information Protection: 

**Subskrypcja, która obejmuje usługę Azure Information Protection na potrzeby klasyfikacji, etykietowania i ochrony (Azure Information Protection P1 lub P2):**

- Szablony, które nie są zintegrowane z etykiet dla Twojej dzierżawy są wyświetlane w **szablonami ochrony** sekcji znajdujący się za etykietami na **usługi Azure Information Protection — etykiety** bloku. Aby przejść do tego bloku, wybierz pozycję **klasyfikacje** > **etykiety** opcji menu. Szablony te można konwertować na etykiety lub możesz połączyć się z nich, podczas konfigurowania ochrony dla etykiety. 

**Jeśli masz subskrypcję obejmującą wyłącznie ochronę (subskrypcja usługi Office 365 obejmującą usługę Azure Rights Management):**

- Szablony dla Twojej dzierżawy są wyświetlane w **szablonami ochrony** sekcji na **usługi Azure Information Protection — etykiety** bloku. Aby przejść do tego bloku, wybierz pozycję **klasyfikacje** > **etykiety** opcji menu. Nie będą wyświetlane etykiety. Zobaczysz również ustawienia konfiguracji, które są specyficzne dla klasyfikacji i etykietowania, ale nie mają wpływu na szablonach lub nie można skonfigurować te ustawienia. 

>[!NOTE]
>W niektórych aplikacjach i usługach, można napotkać [nie przesyłaj dalej](configure-usage-rights.md#do-not-forward-option-for-emails) i [tylko do szyfrowania](configure-usage-rights.md#encrypt-only-option-for-emails) (lub **Szyfruj**) wyświetlane jako szablon. Nie są to szablony, które można edytować lub usunięcia, ale opcje, które pochodzą domyślnie z usługą Exchange.

## <a name="default-templates"></a>Szablony domyślne

W przypadku uzyskania subskrypcji usługi Azure Information Protection lub subskrypcję usługi Office 365, która obejmuje usługę Azure Rights Management, dwa szablony domyślne są tworzone automatycznie dla dzierżawy. Te szablony ograniczanie dostępu do grona upoważnionych użytkowników w Twojej organizacji. Po utworzeniu tych szablonów, mają uprawnienia, które są wymienione w [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](configure-usage-rights.md#rights-included-in-the-default-templates) dokumentacji.

Ponadto szablony są skonfigurowane i umożliwiają dostęp w trybie offline przez siedem dni i nie mają datę wygaśnięcia.

>[!NOTE]
> Możesz zmienić te ustawienia, a nazwy i opisy w domyślnych szablonach. Ta możliwość nie było możliwe przy użyciu klasycznego portalu Azure i nadal nie jest obsługiwane dla programu PowerShell.

Te szablony domyślne ułatwiają Ty i inni od razu chronić poufne dane Twojej organizacji. Te szablony mogą być używane, za pomocą etykiety usługi Azure Information Protection lub samodzielnie za pomocą [aplikacji i usług](applications-support.md) , za pomocą szablonów usługi Rights Management.

Można również utworzyć własne szablony niestandardowe. Prawdopodobnie potrzebne będzie tylko kilka szablonów, ale można mieć maksymalnie 500 szablonów niestandardowych zapisanych na platformie Azure.


### <a name="default-template-names"></a>Domyślne nazwy szablonu

Jeśli niedawno uzyskano subskrypcję, szablony domyślne są tworzone za pomocą następujących nazw:

- **Poufne \ wszyscy pracownicy** że przyznaje odczytu i modyfikowania uprawnień dla zawartości chronionej.

- **Wysoce poufne \ wszyscy pracownicy** która przyznaje uprawnienia tylko do odczytu dla zawartości chronionej.

Jeśli uzyskano subskrypcję pewien czas temu szablony domyślne są tworzone o następujących nazwach:

- **\<Nazwa organizacji > — poufne** że przyznaje odczytu i modyfikowania uprawnień dla zawartości chronionej.

- **\<Nazwa organizacji > — poufne tylko do wyświetlania** która przyznaje uprawnienia tylko do odczytu dla zawartości chronionej. 

Można zmienić nazwy (i ponownie skonfigurować) te szablony domyślne, korzystając z witryny Azure portal.

>[!NOTE]
>Jeśli nie widzisz szablony domyślne w **usługi Azure Information Protection — etykiety** bloku są konwertowane na etykiety lub połączone z etykiety. Nadal istnieją jako szablony, ale w witrynie Azure portal, zobaczysz je w ramach konfiguracji etykiety, który zawiera ustawienia ochrony dla klucz w chmurze. Zawsze można potwierdzić szablonach, które ma dzierżawy, uruchamiając [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) z [modułu AADRM programu PowerShell](administer-powershell.md).
>
>Szablony, można przekonwertować ręcznie, zgodnie z opisem w dalszej części [Aby dokonać konwersji szablonów na etykiety](#to-convert-templates-to-labels), a następnie zmień je, jeśli chcesz. Lub są one konwertowane automatycznie dla Ciebie, jeśli domyślne zasady usługi Azure Information Protection została niedawno utworzona i usługi Azure Rights Management dla dzierżawy została aktywowana w danym momencie.

Szablony, które zostały zarchiwizowane wyświetlane jako niedostępny w **usługi Azure Information Protection — etykiety** bloku. Nie można wybrać te szablony dla etykiet, ale mogą być konwertowane do etykiet.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Zagadnienia dotyczące szablonów w portalu Azure

Przed rozpoczęciem edycji tych szablonów, lub konwersji do etykiet, upewnij się, że masz świadomość następujących zmian i zagadnienia. Z powodu zmiany implementacji poniżej jest szczególnie ważne, jeśli wcześniej zarządzane szablonów w klasycznym portalu Azure.

- Po edycji lub konwersji szablonu i zapisaniu zasad usługi Azure Information Protection w oryginalnych [prawach użytkowania](configure-usage-rights.md) są wprowadzane następujące zmiany. W razie potrzeby można dodawać lub usuwać poszczególne prawa użytkowania za pomocą witryny Azure portal. Możesz też korzystać z programu PowerShell [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) i [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) polecenia cmdlet.
    
    - Opcja **Zezwalaj na makra** (nazwa pospolita) jest automatycznie dodawana. To prawo użytkowania jest wymagane przez pasek usługi Azure Information Protection w aplikacji pakietu Office.

- **Opublikowane** i **zarchiwizowane** ustawienia są wyświetlane jako **włączone**: **Na** i **włączone**: **Wyłącz** odpowiednio na **etykiety** bloku. Dla szablonów, które chcesz zachować, ale nie być widoczne dla użytkowników lub usług, ustawienie tych szablonów **włączone**: **Wyłącz**.

- Nie można skopiować ani usunąć szablonu w witrynie Azure portal. Gdy szablon jest konwertowany na etykietę, można skonfigurować etykiety, można zatrzymać za pomocą tego szablonu, wybierając **nieskonfigurowane** dla **ustawić uprawnienia dla dokumentów i wiadomości e-mail zawierających tę etykietę** Opcja. Alternatywnie możesz usunąć etykiety. W obu scenariuszach jednak szablon nie zostanie usunięta i pozostaje w stanie zarchiwizowane.
    
    Można teraz usunąć szablon przy użyciu programu PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) polecenia cmdlet. Umożliwiają to polecenie cmdlet programu PowerShell dla szablonów, które nie są konwertowane na etykiety. Jednakże aby upewnić się, że wcześniej chronionej zawartości, można go otworzyć i używać zgodnie z oczekiwaniami, zwykle odradzamy usuwanie szablonów. Najlepszym rozwiązaniem jest usunięcie szablonów, tylko wtedy, gdy masz pewność, że nie były używane do ochrony dokumentów lub wiadomości e-mail w środowisku produkcyjnym. Jako środek ostrożności warto rozważyć najpierw wyeksportowanie szablonu do przechowywania kopii zapasowych, przy użyciu [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) polecenia cmdlet. 

- Obecnie edytowanie i zapisanie szablonu dla działu powoduje usunięcie konfiguracji zakresu. Odpowiednikiem szablonu o określonym zakresie w zasadach usługi Azure Information Protection jest [zasada z określonym zakresem](configure-policy-scope.md). W przypadku konwersji szablonu na etykietę możesz wybrać istniejący zakres.
    
    Ponadto nie można ustawić ustawienia zgodności aplikacji dla szablonu dla działu za pomocą witryny Azure portal. Jeśli to konieczne, możesz ustawić to ustawienie zgodności aplikacji przy użyciu [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) polecenia cmdlet i *EnableInLegacyApps* parametru.

- Podczas konwersji lub link szablonu na etykietę, może on nie jest już używany przez inne etykiety. Ponadto, ten szablon nie jest już wyświetlany w **szablonami ochrony** sekcji. 

- Nie tworzysz nowy szablon z **szablonami ochrony** sekcji. Zamiast tego utworzyć etykiety, która ma **Chroń** ustawienia i skonfigurować prawa użytkowania i ustawienia z **ochrony** bloku. Aby uzyskać pełne instrukcje, zobacz sekcję [Aby utworzyć nowy szablon](#to-create-a-new-template).

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Aby skonfigurować szablony w usłudze Azure Information Protection

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do **usługi Azure Information Protection — etykiety** bloku.
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **klasyfikacje** > **etykiety** opcji menu: Na **usługi Azure Information Protection — etykiety** bloku rozwiń **szablonami ochrony**, a następnie zlokalizuj szablon, który chcesz skonfigurować.
    
3. Wybierz szablon, a następnie na **etykiety** bloku można zmienić nazwę i opis szablonu w razie potrzeby, edytując **Nazwa wyświetlana etykiety** i **opis**. Następnie wybierz **ochrony** wartością **Azure (klucz w chmurze)**, aby otworzyć **ochrony** bloku.

4. W bloku **Ochrona** można zmienić uprawnienia, wygaśnięcia zawartości i ustawienia dostępu w trybie offline. Aby uzyskać więcej informacji o konfiguracji ustawień ochrony, zobacz temat [Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management](configure-policy-protection.md)
    
    Kliknij przycisk **OK**, aby zachować zmiany, a w bloku **Etykieta** kliknij przycisk **Zapisz**.
    
> [!NOTE]
> Można również edytować szablon przy użyciu **Edytuj szablon** znajdujący się na **ochrony** bloku, jeśli skonfigurowano etykietę do używania wstępnie zdefiniowany szablon. Jeśli żadna etykieta nie innych również korzysta z wybranego szablonu, ten przycisk konwertuje szablonu na etykietę i przejście do kroku 5. Aby uzyskać więcej informacji na temat zachodzących podczas konwertowania szablonów do etykiet zobacz następną sekcję.

## <a name="to-convert-templates-to-labels"></a>Aby dokonać konwersji szablonów na etykiety

Jeśli masz subskrypcję, która obejmuje klasyfikację, etykietowanie i ochronę, możesz dokonać konwersji szablonu na etykietę. Podczas konwertowania szablonu oryginalny szablon zostaje zachowany, ale w witrynie Azure portal jest teraz wyświetlany jako zawarty w nowej etykiecie.

Na przykład jeśli dokonano konwersji etykiety o nazwie **Marketing**, która przyznaje prawa użytkowania dla grupy marketingu, w portalu Azure jest ona teraz wyświetlana jako etykieta o nazwie **Marketing**, która ma takie same ustawienia ochrony. W przypadku zmiany ustawień ochrony w nowo utworzonej etykiecie zostaną one zmienione w szablonie, a korzystający z szablonu użytkownik lub usługa otrzyma nowe ustawienia ochrony przy następnym odświeżeniu szablonu. 

Nie jest wymagana konwersja wszystkich szablonów do etykiet, ale po takiej konwersji ustawienia ochrony będą w pełni zintegrowane z pełną funkcjonalnością etykiet, dzięki czemu nie trzeba utrzymywać oddzielnych ustawień.

Aby dokonać konwersji szablonu na etykietę, kliknij prawym przyciskiem myszy szablon, a następnie wybierz opcję **Konwertuj do etykiety**. Aby wybrać tę opcję, można również użyć menu kontekstowego. 

Można również konwersji szablonu na etykietę, podczas konfigurowania etykiety dla ochrony i wstępnie zdefiniowany szablon przy użyciu **Edytuj szablon** przycisku. 

Podczas konwertowania szablonu do etykiety:

- Nazwa szablonu jest konwertowana na nazwę nowej etykiety i opis szablonu jest konwertowany na etykietkę narzędzia. 

- Jeśli stan szablonu został opublikowany, to ustawienie jest mapowane na **włączone**: **Na** dla etykiety, która będzie wyświetlana jako etykieta dla użytkowników po następnym opublikowaniu zasad usługi Azure Information Protection. Jeśli stan szablonu został zarchiwizowany, to ustawienie jest mapowane na **włączone**: **Wyłącz** dla etykiety i nie są wyświetlane jako etykieta dostępna dla użytkowników.

- Ustawienia ochrony są zachowywane i można je edytować, jeśli jest to wymagane, a także dodać inne ustawienia etykiety, takie jak znaczniki wizualne i warunki.

- Oryginalny szablon nie będzie już wyświetlany w **szablonami ochrony** i nie można wybrać jako wstępnie zdefiniowany szablon, podczas konfigurowania ochrony dla etykiety. Aby edytować ten szablon w witrynie Azure portal, teraz edytować etykietę, który został utworzony podczas konwertowania szablonu. Szablon pozostaje dostępny dla usługi Azure Rights Management i wciąż można nim zarządzać za pomocą [poleceń programu PowerShell](administer-powershell.md).  

## <a name="to-create-a-new-template"></a>Aby utworzyć nowy szablon

Po utworzeniu nowej etykiety z ustawieniem ochrony **Azure (klucz w chmurze)**, dzieje się w tle, ta akcja tworzy nowy szablon niestandardowy, który następnie jest możliwy przez usługi i aplikacje, które integrują się z usługą Rights Management Szablony.

1. Z **klasyfikacje** > **etykiety** opcji menu: Na **usługi Azure Information Protection — etykiety** bloku wybierz **Dodaj nową etykietę**.

2. Na **etykiety** bloku, Zachowaj wartość domyślną **włączone**: **Na**, następnie wprowadź nazwę etykiety i opis nazwę i opis szablonu.

3. W sekcji **Ustaw uprawnienia do dokumentów i wiadomości e-mail zawierających tę etykietę** wybierz pozycję **Chroń**, a następnie **Ochrona**:
    
     ![Konfigurowanie ochrony dla etykiety usługi Azure Information Protection](./media/info-protect-protection-bar-configured.png)

4. W bloku **Ochrona** można zmienić uprawnienia, wygaśnięcia zawartości i ustawienia dostępu w trybie offline. Aby uzyskać więcej informacji o konfiguracji ustawień ochrony, zobacz temat [Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management](configure-policy-protection.md)
    
    Kliknij przycisk **OK**, aby zachować zmiany, a w bloku **Etykieta** kliknij przycisk **Zapisz**.
    
    Na **usługi Azure Information Protection — etykiety** bloku będą teraz widoczne nowe etykiety wyświetlana **ochrony** kolumny, aby wskazać, że zawiera on ustawienia ochrony. Te ustawienia ochrony są wyświetlane jako szablony do aplikacji i usług, które obsługują usługę Azure Rights Management.
    
    Mimo, że etykieta jest włączona, domyślnie szablon zostanie zarchiwizowany. Tak, aby aplikacje i usługi można użyć szablonu do ochrony dokumentów i wiadomości e-mail, należy wykonać ostatni krok, aby opublikować szablon.

5. Z **klasyfikacje** > **zasady** menu, wybierz zasady, które zawierają nowe ustawienia ochrony. Następnie wybierz pozycję **apletu Dodaj lub usuń etykiety**. Z **zasad: Dodaj lub usuń etykiety** bloku wybierz nowo utworzony etykiety, który zawiera ustawienia ochrony, wybierz pozycję **OK**, a następnie wybierz pozycję **Zapisz**.

## <a name="next-steps"></a>Następne kroki

Na komputerze klienta usługi Azure Information Protection w celu uzyskania tych ustawień zmiany może potrwać do 15 minut. Aby uzyskać informacje dotyczące sposobu pobierania i odświeżania szablonów przez komputery i usługi, zobacz temat [Odświeżanie szablonów dla użytkowników i usług](refresh-templates.md).

Wszystko, co można skonfigurować w witrynie Azure portal do tworzenia i zarządzania szablonami, można wykonać przy użyciu programu PowerShell. Ponadto program PowerShell udostępnia więcej opcji, które nie są dostępne w portalu. Aby uzyskać więcej informacji, zobacz [dokumentacja programu PowerShell dla szablonów ochrony](configure-templates-with-powershell.md). 

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

