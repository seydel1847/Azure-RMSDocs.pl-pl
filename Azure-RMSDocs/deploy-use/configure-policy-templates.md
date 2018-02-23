---
title: "Konfigurowanie i zarządzanie nimi szablonów usługi Azure Information Protection"
description: "Konfigurowanie szablonów i zarządzania nimi rights management z portalu Azure."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 303b8d55faf3aa25389bf5810df4e65f18459bc6
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Konfigurowanie i zarządzanie nimi szablonów usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

>[!NOTE]
>Ta funkcja zastępuje Konfigurowanie szablonów niestandardowych w klasycznym portalu Azure. Klasyczny portal teraz został wycofany, trzeba używać portalu Azure. Szybkie mapowania instrukcje, zobacz [zadań, które są używane z klasycznego portalu Azure](migrate-portal.md).


Szablony zarządzania prawami są teraz zintegrowane z zasadami usługi Azure Information Protection. 

**Subskrypcja, która obejmuje usługę Azure Information Protection na potrzeby klasyfikacji, etykietowania i ochrony (Azure Information Protection P1 lub P2):**

- Szablony zarządzania praw, które nie są zintegrowane z etykiety dla dzierżawy są wyświetlane w **szablony ochrony** sekcji po etykiet w **usługi Azure Information Protection — globalne zasady**bloku. Szablony te można przekonwertować na etykiety, lub możesz połączyć się z nimi, podczas konfigurowania ochrony dla etykiet. 

**Jeśli masz subskrypcję obejmującą wyłącznie ochronę (subskrypcja usługi Office 365 obejmującą usługę Azure Rights Management):**

- Szablony zarządzania praw dla Twojej dzierżawy są wyświetlane w **usługi Azure Information Protection — globalne zasady** bloku, w **szablony ochrony** sekcji. Nie będą wyświetlane etykiety. Zobacz też ustawienia konfiguracji, które są specyficzne dla klasyfikacji i etykietowania, ale nie mają wpływu na szablonów lub nie można skonfigurować te ustawienia. 

## <a name="default-templates"></a>Szablony domyślne

Po uzyskaniu subskrypcji dla usługi Azure Information Protection lub subskrypcję usługi Office 365 obejmującą usługę Azure Rights Management, dwa szablony domyślne są tworzone automatycznie dla dzierżawy. Te szablony ograniczyć dostęp do autoryzowanych użytkowników w organizacji. Te szablony są tworzone, mają uprawnienia, które są wymienione w [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](configure-usage-rights.md#rights-included-in-the-default-templates) dokumentacji.

Ponadto szablony są skonfigurowane i umożliwiają dostęp w trybie offline przez 7 dni i nie mają datę wygaśnięcia.

>[!NOTE]
> Można zmienić te ustawienia oraz nazwy i opisy domyślnych szablonów. Ta możliwość nie było możliwe z klasycznego portalu Azure i nadal nie jest obsługiwane dla środowiska PowerShell.

Te szablony domyślne ułatwiają dla Ciebie i inne osoby do natychmiast rozpocząć ochronę danych poufnych w organizacji. Te szablony mogą być używane z etykietami usługi Azure Information Protection lub samodzielnie z [aplikacji i usług](../understand-explore/applications-support.md) mogą używać szablony usługi Rights Management.

Można również tworzyć własne szablony niestandardowe. Prawdopodobnie potrzebne będzie tylko kilka szablonów, ale można mieć maksymalnie 500 szablonów niestandardowych zapisanych na platformie Azure.

### <a name="default-template-names"></a>Domyślne nazwy szablonu

Jeśli użytkownik uzyskał ostatnio subskrypcji, szablony domyślne są tworzone z następujących nazw:

- **Poufne \ wszyscy pracownicy** że przyznaje odczytywać i modyfikować uprawnienia do chronionej zawartości.

- **Poufny \ wszyscy pracownicy** który nadaje uprawnienia tylko do odczytu do chronionej zawartości.

Jeśli użytkownik uzyskał subskrypcji pewien czas temu, szablony domyślne są tworzone z następujących nazw:

- **\<Nazwa organizacji > — poufne** że przyznaje odczytywać i modyfikować uprawnienia do chronionej zawartości.

- **\<Nazwa organizacji > — poufne tylko do wyświetlania** który nadaje uprawnienia tylko do odczytu do chronionej zawartości. 

Możesz zmienić nazwę (i ponownie skonfiguruj) te szablony domyślne, korzystając z portalu Azure.

>[!NOTE]
>Jeśli nie widzisz szablony domyślne w **usługi Azure Information Protection — globalne zasady** bloku są konwertowane na etykiety lub połączony z etykietą. Nadal istnieją jako szablon, ale w portalu Azure, zobaczysz je w ramach konfiguracji etykietę, która obejmuje usługę Azure RMS protection. Zawsze można potwierdzić, szablony, jakie ma dzierżawy, uruchamiając [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) z [modułu AADRM PowerShell](administer-powershell.md).
>
>Szablony, można przekonwertować ręcznie, zgodnie z objaśnieniem w dalszej części artykułu [przekonwertować szablony do etykiet](#to-convert-templates-to-labels), a następnie zmień je, jeśli chcesz. Lub są konwertowane automatycznie dla Ciebie Jeśli Twoje domyślne zasady usługi Azure Information Protection została niedawno utworzona i uaktywniono usługę Azure Rights Management dla swojej dzierżawy w tym czasie.

Szablony, które zostaną zarchiwizowane wyświetlane jako niedostępny w **usługi Azure Information Protection — globalne zasady** bloku. Nie można wybrać te szablony dla etykiet, ale może być przekonwertowany do etykiet.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Zagadnienia dotyczące szablonów w portalu Azure

Przed rozpoczęciem edycji tych szablonów lub przekonwertować je na etykiety, upewnij się, że masz świadomość następujących zmian i zagadnienia. Z powodu zmiany implementacji poniżej jest szczególnie ważne, jeśli wcześniej zarządzane szablonów w klasycznym portalu Azure.

- Po edycji lub konwersji szablonu i zapisaniu zasad usługi Azure Information Protection w oryginalnych [prawach użytkowania](configure-usage-rights.md) są wprowadzane następujące zmiany. W razie potrzeby możesz można dodawać i usuwać prawa użytkowania poszczególnych przy użyciu portalu Azure. Lub użyj programu PowerShell z [New-AadrmRightsDefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) i [Set-AadrmTemplateProperty](/powershell/module/aadrm/new-aadrmrightsdefinition) polecenia cmdlet.
    
    - Opcja **Zezwalaj na makra** (nazwa pospolita) jest automatycznie dodawana. To prawo użytkowania jest wymagane przez pasek usługi Azure Information Protection w aplikacji pakietu Office.

- Ustawienia **Opublikowane** i **Zarchiwizowane** są wyświetlane odpowiednio jako **Włączone**: **Włączone** i **Włączone**: **Wyłączone** w bloku **Etykiety**. Dla szablonów, które chcesz zachować, ale nie być widoczna dla użytkowników lub usług, należy ustawić te szablony na **włączone**: **poza**.

- Nie można skopiować ani usunąć szablonu w portalu Azure. Po przekonwertowaniu szablonu z etykietą, można skonfigurować etykietę można zatrzymać za pomocą szablonu, wybierając **nieskonfigurowane** dla **ustawić uprawnień dla dokumentów i wiadomości e-mail zawierających tę etykietę** opcji. Alternatywnie można usunąć etykietę. W obu przypadkach jednak szablon nie zostanie usunięty i pozostaje w stanie zarchiwizowane.
    
    Można teraz usunąć szablon przy użyciu programu PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) polecenia cmdlet. Umożliwia także tego polecenia cmdlet programu PowerShell dla szablonów, które nie są konwertowane na etykiety. Jednak jeśli usuniesz szablon, który został użyty do ochrony zawartości tej zawartości można będzie niemożliwe. Usuń szablony tylko wtedy, gdy masz pewność, że nie zostały użyte do ochrony dokumentów lub wiadomości e-mail w środowisku produkcyjnym. Ze względów warto rozważyć najpierw wyeksportowanie szablonu jako kopii zapasowej za pomocą [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) polecenia cmdlet. 

- Wyświetl szablony dla działów (szablony, które są skonfigurowane dla zakresu) w ramach globalnych zasad. Obecnie edytowanie i zapisanie szablonu dla działu powoduje usunięcie konfiguracji zakresu. Odpowiednikiem szablonu o określonym zakresie w zasadach usługi Azure Information Protection jest [zasada z określonym zakresem](configure-policy-scope.md). W przypadku konwersji szablonu na etykietę możesz wybrać istniejący zakres.
    
    Ponadto obecnie nie można ustawić zgodności aplikacji dla szablonu dla działu. Jeśli to konieczne, możesz ustawić ustawienia zgodności aplikacji przy użyciu [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) polecenia cmdlet i *EnableInLegacyApps* parametru.

- Podczas konwersji lub łączenia szablonu z etykietą, może on już używany przez innych etykiet. Ponadto ten szablon nie jest już wyświetlany w **szablony ochrony** sekcji. 

- Nie można utworzyć nowy szablon z **szablony ochrony** sekcji. Zamiast tego utworzyć etykietę **Chroń** ustawienia i skonfigurować prawa użytkowania i ustawienia z **ochrony** bloku. Aby uzyskać pełne instrukcje, zobacz sekcję [Aby utworzyć nowy szablon](#to-create-a-new-template).

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Aby skonfigurować szablony w usłudze Azure Information Protection

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Jeśli szablon, który chcesz skonfigurować dla wszystkich użytkowników, pozostają **usługi Azure Information Protection — globalne zasady** bloku.
    
    Jeśli szablon, który chcesz skonfigurować jest [zakres zasad](configure-policy-scope.md) tak, aby dotyczył tylko wybrani użytkownicy z **zasady** zaznaczenia menu, wybierz opcję **zakres zasad**. Następnie wybierz zakresie zasad z **zasady usługi Azure Information Protection - zakres** bloku.

3. Z **usługi Azure Information Protection — globalne zasady** bloku lub **zasad:\<name >** bloku, Znajdź szablon, który chcesz skonfigurować:
    
    - Jeśli masz subskrypcję obejmującą klasyfikacji, etykietowania i ochrony: rozwiń węzeł **szablony ochrony** po etykiety.
    
    - Jeśli posiadasz subskrypcję obejmującą wyłącznie ochronę: wyświetl szablony jako etykiety.

4. Wybierz szablon, a następnie na **etykiety** bloku, można zmienić nazwę i opis szablonu w razie potrzeby, edytując **Nazwa wyświetlana etykieta** i **opis**. Następnie wybierz opcję **ochrony** , który ma wartość **Azure (klucz w chmurze)**, aby otworzyć **ochrony** bloku.

5. W bloku **Ochrona** można zmienić uprawnienia, wygaśnięcia zawartości i ustawienia dostępu w trybie offline. Aby uzyskać więcej informacji o konfiguracji ustawień ochrony, zobacz temat [Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management](configure-policy-protection.md)
    
    Kliknij przycisk **OK**, aby zachować zmiany, a w bloku **Etykieta** kliknij przycisk **Zapisz**.

6. Aby udostępnić użytkownikom zmiany do użytkownika aplikacji i usług, w początkowym **usługi Azure Information Protection** bloku, kliknij przycisk **publikowania**.

> [!NOTE]
> Można również edytować szablonu, za pomocą **Edytuj szablon** znajdującego się na **ochrony** bloku, jeśli skonfigurowano etykietę do używania wstępnie zdefiniowanego szablonu. Jeśli nie inne etykieta używa również wybranego szablonu, ten przycisk konwertuje szablon do etykiety i przejście do kroku 5. Aby uzyskać więcej informacji na temat co się stanie, jeśli szablony są konwertowane na etykiety zobacz następną sekcję.

## <a name="to-convert-templates-to-labels"></a>Aby dokonać konwersji szablonów na etykiety

Jeśli masz subskrypcję, która obejmuje klasyfikację, etykietowanie i ochronę, możesz dokonać konwersji szablonu na etykietę. Podczas konwertowania szablonu, są przechowywane w oryginalnym szablonie, ale w portalu Azure, teraz wyświetla zawartych w nowej etykiety.

Na przykład jeśli dokonano konwersji etykiety o nazwie **Marketing**, która przyznaje prawa użytkowania dla grupy marketingu, w portalu Azure jest ona teraz wyświetlana jako etykieta o nazwie **Marketing**, która ma takie same ustawienia ochrony. W przypadku zmiany ustawień ochrony w nowo utworzonej etykiecie zostaną one zmienione w szablonie, a korzystający z szablonu użytkownik lub usługa otrzyma nowe ustawienia ochrony przy następnym odświeżeniu szablonu. 

Nie jest wymagana konwersja wszystkich szablonów do etykiet, ale po takiej konwersji ustawienia ochrony będą w pełni zintegrowane z pełną funkcjonalnością etykiet, dzięki czemu nie trzeba utrzymywać oddzielnych ustawień.

Aby dokonać konwersji szablonu na etykietę, kliknij prawym przyciskiem myszy szablon, a następnie wybierz opcję **Konwertuj do etykiety**. Aby wybrać tę opcję, można również użyć menu kontekstowego. 

Można także przekonwertować szablon na etykiecie po skonfigurowaniu etykiety dla ochrony i wstępnie zdefiniowanego szablonu, za pomocą **Edytuj szablon** przycisku. 

Podczas konwertowania szablonu do etykiety:

- Nazwa szablonu jest konwertowana na nazwę nowej etykiety i opis szablonu jest konwertowany na etykietkę narzędzia. 

- Jeśli stan szablonu został opublikowany, to ustawienie jest mapowane na **Włączone**: **Włączone** dla etykiety, która będzie wyświetlana jako etykieta dla użytkowników po następnym opublikowaniu zasad usługi Azure Information Protection. Jeśli stan szablon został zarchiwizowany, to ustawienie mapuje **włączone**: **poza** etykiety i będzie wyświetlany jako etykieta dostępne dla użytkowników.

- Ustawienia ochrony są zachowywane i można je edytować, jeśli jest to wymagane, a także dodać inne ustawienia etykiety, takie jak znaczniki wizualne i warunki.

- Oryginalnego szablonu nie będzie już wyświetlany w **szablony ochrony** i nie można wybrać jako szablon wstępnie zdefiniowany podczas konfigurowania ochrony dla etykiety. Do edycji tego szablonu w portalu Azure, możesz edytować etykiety, dla której został utworzony po przekonwertowaniu szablonu. Szablon pozostaje dostępny dla usługi Azure Rights Management i wciąż można nim zarządzać za pomocą [poleceń programu PowerShell](administer-powershell.md).  

## <a name="to-create-a-new-template"></a>Aby utworzyć nowy szablon

Podczas tworzenia nowej etykiety z ustawieniem ochrony **usługi Azure RMS** lub **Azure (klucz w chmurze)**, w obszarze obejmuje, ta akcja tworzy nowy szablon niestandardowy, które następnie są dostępne dla usług i aplikacje, które zintegrować z szablony usługi Rights Management.

1. Jeśli nowy szablon jest przeznaczony dla wszystkich użytkowników, pozostają **usługi Azure Information Protection — globalne zasady** bloku.
    
     Jeśli nowy szablon będzie szablon dla działu, tak że dotyczy ona tylko wybranych użytkowników z **zasady** zaznaczenia menu, wybierz opcję **zakres zasad**. Następnie utwórz lub wybierz Twoje [zakres zasad](configure-policy-scope.md) z **zasady usługi Azure Information Protection - zakres** bloku.

2. Z **usługi Azure Information Protection — globalne zasady** bloku lub **zasad:\<name >** bloku, kliknij przycisk **dodać nową etykietę**.

3. W bloku **Etykieta** zachowaj ustawienie domyślne **Włączone**: **Włączone**, aby opublikować nowy szablon, lub zmień to ustawienie na **Wyłączone**, aby utworzyć szablon jako zarchiwizowany. Następnie wprowadź nazwę etykiety i opis dla nazwy i opisu szablonu.

4. W sekcji **Ustaw uprawnienia do dokumentów i wiadomości e-mail zawierających tę etykietę** wybierz pozycję **Chroń**, a następnie **Ochrona**:
    
     ![Konfigurowanie ochrony dla etykiety usługi Azure Information Protection](../media/info-protect-protection-bar-configured.png)

5. W bloku **Ochrona** można zmienić uprawnienia, wygaśnięcia zawartości i ustawienia dostępu w trybie offline. Aby uzyskać więcej informacji o konfiguracji ustawień ochrony, zobacz temat [Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management](configure-policy-protection.md)
    
    Kliknij przycisk **OK**, aby zachować zmiany, a w bloku **Etykieta** kliknij przycisk **Zapisz**.

6. Aby udostępnić te szablony użytkownika aplikacji i usług, w początkowym **usługi Azure Information Protection** bloku, kliknij przycisk **publikowania**.


## <a name="next-steps"></a>Następne kroki

Tak jak w przypadku wszystkich zmian zasad usługi Azure Information Protection, zakończenie pobierania tych szablonów na komputer klienta usługi Azure Information Protection może potrwać do 15 minut. Aby uzyskać informacje dotyczące sposobu pobierania i odświeżania szablonów przez komputery i usługi, zobacz temat [Odświeżanie szablonów dla użytkowników i usług](refresh-templates.md).

Wszystkie elementy, które można skonfigurować w portalu Azure do tworzenia i zarządzania szablonami, można wykonać za pomocą programu PowerShell. Ponadto program PowerShell oferuje więcej opcji, które nie są dostępne w portalu. Aby uzyskać więcej informacji, zobacz [ochrony szablonów w programie PowerShell](configure-templates-with-powershell.md). 

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
