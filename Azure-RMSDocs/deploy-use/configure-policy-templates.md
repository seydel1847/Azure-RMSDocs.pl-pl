---
title: "Konfigurowanie szablonów w usłudze Azure Information Protection i zarządzanie nimi"
description: "Obecnie w wersji zapoznawczej można konfigurować szablony zarządzania prawami i zarządzać nimi przy użyciu zasad usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: b9c6b808de6c5967885f4937965b4e0e759668f3
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2017
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Konfigurowanie i zarządzanie nimi szablonów usługi Azure Information Protection

>*Dotyczy: Azure Information Protection*

>[!NOTE]
>Ta funkcja zastępuje Konfigurowanie szablonów niestandardowych w klasycznym portalu Azure.
>
>Mimo że można nadal tworzyć i zarządzać szablonów w klasycznym portalu Azure, nie zaleca się zarządzanie te same szablony z klasycznego portalu Azure i portalu Azure. Konfigurowanie szablonów w tych portali inną implementację uległ zmianie, więc konfigurowanie tego samego szablonu w różnych portali może spowodować zawodnych konfiguracji.


Szablony zarządzania prawami są teraz zintegrowane z zasadami usługi Azure Information Protection. 

**Subskrypcja, która obejmuje usługę Azure Information Protection na potrzeby klasyfikacji, etykietowania i ochrony (Azure Information Protection P1 lub P2):**

- Szablony zarządzania praw, które nie są zintegrowane z etykiety dla dzierżawy są wyświetlane w **szablony** sekcji po etykiet w **usługi Azure Information Protection — globalne zasady** bloku. Szablony te można przekonwertować na etykiety lub można nadal nimi zarządzać jako osobne szablonów i link do ich podczas konfigurowania ochrony dla etykiet. 

**Jeśli masz subskrypcję obejmującą wyłącznie ochronę (subskrypcja usługi Office 365 obejmującą usługę Azure Rights Management):**

- Szablony zarządzania praw dla Twojej dzierżawy są wyświetlane w **usługi Azure Information Protection — globalne zasady** bloku, w **szablony** sekcji. Nie będą wyświetlane etykiety. Zobacz też ustawienia konfiguracji, które są specyficzne dla klasyfikacji i etykietowania, ale te nie mają wpływu na szablonów lub nie można skonfigurować. 

## <a name="default-templates"></a>Szablony domyślne

Po uzyskaniu subskrypcji dla usługi Azure Information Protection lub subskrypcję usługi Office 365 obejmującą usługę Azure Rights Management, dwa szablony domyślne są tworzone automatycznie dla dzierżawy ograniczyć dostęp do autoryzowanych użytkowników w organizacji. Wspomniane dwa szablony obejmują następujące ograniczenia: 

- Uprawnienia Odczyt lub Modyfikacja odnoszące się do chronionej zawartości
    
    -Określone uprawnienia: Wyświetl zawartość, Zapisz plik, Edytuj zawartość, Wyświetl przypisane prawa, Zezwalaj na makra, Przekaż, Odpowiedz, Odpowiedz wszystkim

- Wyświetlanie chronionej zawartości w trybie tylko do odczytu
    
    - Określone uprawnienie: Wyświetl zawartość

Te szablony ułatwiają dla Ciebie i inne osoby do natychmiast rozpocząć ochronę danych poufnych w organizacji. Te szablony mogą być używane z etykietami usługi Azure Information Protection lub samodzielnie z [aplikacji i usług](../understand-explore/applications-support.md) mogą używać szablony usługi Rights Management.

Można również tworzyć własne szablony niestandardowe. Prawdopodobnie potrzebne będzie tylko kilka szablonów, ale można mieć maksymalnie 500 szablonów niestandardowych zapisanych na platformie Azure.

### <a name="default-template-names"></a>Domyślne nazwy szablonu

Jeśli ostatnio uzyskano subskrypcję usługi Azure Information Protection, nazwy szablony domyślne są następujące:

- **Poufne \ wszyscy pracownicy** uprawnienia odczytu lub modyfikowania chronionej zawartości.

- **Poufny \ wszyscy pracownicy** w celu wyświetlenia tylko do odczytu do chronionej zawartości.

Jeśli uzyskać subskrypcję usługi Azure Information Protection pewien czas temu, lub jeśli nie masz subskrypcji usługi Azure Information Protection, ale masz subskrypcję usługi Office 365 obejmującą usługę Azure Rights Management, nazwy szablony domyślne są następujące:

- **\<Nazwa organizacji > — poufne** uprawnienia odczytu lub modyfikowania chronionej zawartości.

- **\<Nazwa organizacji > — poufne tylko do wyświetlania**, w celu wyświetlenia tylko do odczytu do chronionej zawartości. 

>[!NOTE]
>Jeśli nie widzisz szablony domyślne w **usługi Azure Information Protection — globalne zasady** bloku są konwertowane na etykiety. Nadal istnieją jako szablon, ale w portalu Azure, zobaczysz je w ramach konfiguracji etykietę, która obejmuje usługę Azure RMS protection. Zawsze można potwierdzić, szablony, jakie ma dzierżawy, uruchamiając [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) z [modułu AADRM PowerShell](administer-powershell.md).
>
>Szablony, można przekonwertować ręcznie, zgodnie z objaśnieniem w dalszej części artykułu [przekonwertować szablony do etykiet](#to-convert-templates-to-labels), a następnie zmień je, jeśli chcesz. Lub one będą konwertowane automatycznie dla Ciebie Jeśli Twoje domyślne zasady usługi Azure Information Protection została niedawno utworzona i uaktywniono usługę Azure Rights Management dla swojej dzierżawy w tym czasie.

Szablony, które zostaną zarchiwizowane wyświetlane jako niedostępny w **usługi Azure Information Protection — globalne zasady** bloku. Nie można wybrać te szablony dla etykiet, ale może być przekonwertowany do etykiet.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Zagadnienia dotyczące szablonów w portalu Azure

Przed rozpoczęciem edycji tych szablonów lub przekonwertować je na etykiety, upewnij się, że masz świadomość następujących zmian i zagadnienia. Z powodu zmiany implementacji poniżej jest szczególnie ważne, jeśli wcześniej zarządzane szablonów w klasycznym portalu Azure.

- Po edycji lub konwersji szablonu i zapisaniu zasad usługi Azure Information Protection w oryginalnych [prawach użytkowania](configure-usage-rights.md) są wprowadzane następujące zmiany. W razie potrzeby można dodawać lub usuwać poszczególne prawa użytkowania za pomocą poleceń cmdlet programu PowerShell [New-AadrmRightsDefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) i [Set-AadrmTemplateProperty](/powershell/module/aadrm/new-aadrmrightsdefinition).
    
    - Usunięto opcję **Zapisz jako, eksportuj** (nazwa pospolita). W portalu Azure nie można ręcznie określić tego prawa użytkowania, ale jest ono uwzględnione w prawie użytkowania Pełna kontrola, które może zostać dodane w razie potrzeby.
    
    - Opcja **Zezwalaj na makra** (nazwa pospolita) jest automatycznie dodawana. To prawo użytkowania jest wymagane przez pasek usługi Azure Information Protection w aplikacji pakietu Office.
    

- Ustawienia **Opublikowane** i **Zarchiwizowane** są wyświetlane odpowiednio jako **Włączone**: **Włączone** i **Włączone**: **Wyłączone** w bloku **Etykiety**. Dla szablonów, które chcesz zachować, ale nie być widoczna dla użytkowników lub usług, należy ustawić je na **włączone**: **poza**.

- Nie można skopiować ani usunąć szablonu w portalu Azure. Po przekonwertowaniu szablonu z etykietą, można skonfigurować etykietę można zatrzymać za pomocą szablonu, wybierając **nieskonfigurowane** dla **ustawić uprawnień dla dokumentów i wiadomości e-mail zawierających tę etykietę** opcji. Alternatywnie można usunąć etykietę. W obu przypadkach jednak szablon nie zostanie usunięty i pozostaje w stanie zarchiwizowane.
    
    Można teraz usunąć szablon przy użyciu programu PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) polecenia cmdlet. Umożliwia także tego polecenia cmdlet programu PowerShell dla szablonów, które nie są konwertowane na etykiety. Jednak jeśli usuniesz szablon, który został użyty do ochrony zawartości tej zawartości można będzie niemożliwe. Usuń szablony tylko wtedy, gdy masz pewność, że nie zostały użyte do ochrony dokumentów lub wiadomości e-mail w środowisku produkcyjnym. Ze względów należy wziąć pod uwagę najpierw Eksportowanie szablonu jako kopii zapasowej, za pomocą [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) polecenia cmdlet. 

- Wyświetlanie szablonów dla działów (szablony, których zakres jest skonfigurowany) w ramach globalnych zasad. Obecnie edytowanie i zapisanie szablonu dla działu powoduje usunięcie konfiguracji zakresu. Odpowiednikiem szablonu o określonym zakresie w zasadach usługi Azure Information Protection jest [zasada z określonym zakresem](configure-policy-scope.md). W przypadku konwersji szablonu na etykietę możesz wybrać istniejący zakres.
    
    Ponadto obecnie nie można ustawić zgodności aplikacji dla szablonu dla działu. Jeśli to konieczne, możesz ustawić zgodność za pomocą polecenia cmdlet programu PowerShell [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty).

- Obecnie szablony, które skonfigurowano dla wielu języków przy użyciu klasycznego portalu Azure lub programu PowerShell nie wyświetlaj tych języków dla nazwy i opisy, ale są zachowywane.

- Podczas konwersji lub łączenia szablonu z etykietą, może on już używany przez innych etykiet.

- Nie można utworzyć nowy szablon z **szablony** kontenera. Zamiast tego utworzyć etykietę **Chroń** ustawienia i skonfigurować prawa użytkowania i ustawienia z **ochrony** bloku. Aby uzyskać pełne instrukcje, zobacz sekcję [Aby utworzyć nowy szablon](#to-create-a-new-template).

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Aby skonfigurować szablony w usłudze Azure Information Protection

1. W nowym oknie przeglądarki zaloguj się w witrynie [Azure Portal](https://portal.azure.com) jako administrator zabezpieczeń lub administrator globalny.

2. Przejdź do bloku **Azure Information Protection**: na przykład w menu centralnym kliknij pozycję **Więcej usług** i w polu filtru zacznij wpisywać ciąg **Information Protection**. Spośród wyników wybierz **Azure Information Protection**. 

2. Jeśli szablon, który chcesz skonfigurować, będzie miał zastosowanie do wszystkich użytkowników, z bloku **Azure Information Protection** wybierz opcję **Globalne**. Jeśli jednak szablon, który chcesz skonfigurować, należy do [zasad o określonym zakresie](configure-policy-scope.md) i z tego powodu ma zastosowanie tylko do wybranych użytkowników, wybierz te zasady o określonym zakresie.

3. W bloku zasad znajdź szablon, który chcesz skonfigurować:
    
    - Jeśli masz subskrypcję, która obejmuje klasyfikację, etykietowanie i ochronę: rozwiń element **Szablony** znajdujący się za etykietami.
    
    - Jeśli posiadasz subskrypcję obejmującą wyłącznie ochronę: wyświetl szablony jako etykiety.

4. Wybierz szablon, a następnie w bloku **Etykieta** możesz w razie potrzeby zmienić nazwę i opis szablonu, edytując pola **Nazwa etykiety** i **Opis**. Następnie wybierz opcję **Ochrona**, która ma wartość **Usługa Azure RMS**, aby otworzyć blok **Ochrona**.

5. W bloku **Ochrona** można zmienić uprawnienia, wygaśnięcia zawartości i ustawienia dostępu w trybie offline. Aby uzyskać więcej informacji o konfiguracji ustawień ochrony, zobacz temat [Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management](configure-policy-protection.md)
    
    Kliknij przycisk **OK**, aby zachować zmiany, a w bloku **Etykieta** kliknij przycisk **Zapisz**.

6. Aby udostępnić zmiany aplikacjom użytkownika i usługom, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## <a name="to-convert-templates-to-labels"></a>Aby dokonać konwersji szablonów na etykiety

Jeśli masz subskrypcję, która obejmuje klasyfikację, etykietowanie i ochronę, możesz dokonać konwersji szablonu na etykietę. Po wykonaniu tej czynności oryginalny szablon zostaje zachowany, ale w portalu Azure jest teraz wyświetlany jako zawarty w nowej etykiecie.

Na przykład jeśli dokonano konwersji etykiety o nazwie **Marketing**, która przyznaje prawa użytkowania dla grupy marketingu, w portalu Azure jest ona teraz wyświetlana jako etykieta o nazwie **Marketing**, która ma takie same ustawienia ochrony. W przypadku zmiany ustawień ochrony w nowo utworzonej etykiecie zostaną one zmienione w szablonie, a korzystający z szablonu użytkownik lub usługa otrzyma nowe ustawienia ochrony przy następnym odświeżeniu szablonu. 

Nie jest wymagana konwersja wszystkich szablonów do etykiet, ale po takiej konwersji ustawienia ochrony będą w pełni zintegrowane z pełną funkcjonalnością etykiet, dzięki czemu nie trzeba utrzymywać oddzielnych ustawień.

Aby dokonać konwersji szablonu na etykietę, kliknij prawym przyciskiem myszy szablon, a następnie wybierz opcję **Konwertuj do etykiety**. Aby wybrać tę opcję, można również użyć menu kontekstowego.

Podczas konwertowania szablonu do etykiety:

- Nazwa szablonu jest konwertowana na nazwę nowej etykiety i opis szablonu jest konwertowany na etykietkę narzędzia. 

- Jeśli stan szablonu został opublikowany, to ustawienie jest mapowane na **Włączone**: **Włączone** dla etykiety, która będzie wyświetlana jako etykieta dla użytkowników po następnym opublikowaniu zasad usługi Azure Information Protection. Jeśli stan szablonu został zarchiwizowany, to ustawienie jest mapowane na **Włączone**: **Wyłączone** dla etykiety i nie będzie ona wyświetlana jako etykieta dostępna dla użytkowników.

- Ustawienia ochrony są zachowywane i można je edytować, jeśli jest to wymagane, a także dodać inne ustawienia etykiety, takie jak znaczniki wizualne i warunki.

- Oryginalnego szablonu nie będzie już wyświetlany w obszarze **szablony** i nie można wybrać jako szablon wstępnie zdefiniowany podczas konfigurowania ochrony dla etykiety. Do edycji tego szablonu w portalu Azure, możesz edytować etykiety, dla której został utworzony po przekonwertowaniu szablonu. Szablon pozostaje dostępny dla usługi Azure Rights Management i wciąż można nim zarządzać za pomocą [poleceń programu PowerShell](administer-powershell.md).  

## <a name="to-create-a-new-template"></a>Aby utworzyć nowy szablon

Utworzenie nowej etykiety z ustawieniem ochrony **Usługa Azure RMS** powoduje utworzenie w sposób niewidoczny dla użytkownika nowego niestandardowego szablonu udostępnianego usługom oraz aplikacjom integrującym się z szablonami usługi Rights Management.

1. Jeśli nowy szablon, który chcesz utworzyć, będzie miał zastosowanie do wszystkich użytkowników, w bloku **Zasady: Globalne** kliknij opcję **Dodaj nową etykietę**.
    
     Jeśli nowy szablon, który chcesz utworzyć, będzie szablonem działu i z tego powodu będzie miał zastosowanie tylko do wybranych użytkowników, najpierw utwórz lub wybierz zasady o określonym zakresie z początkowego bloku **Azure Information Protection**.

2. W bloku **Etykieta** zachowaj ustawienie domyślne **Włączone**: **Włączone**, aby opublikować nowy szablon, lub zmień to ustawienie na **Wyłączone**, aby utworzyć szablon jako zarchiwizowany. Następnie wprowadź nazwę etykiety i opis dla nazwy i opisu szablonu.

3. W sekcji **Ustaw uprawnienia do dokumentów i wiadomości e-mail zawierających tę etykietę** wybierz pozycję **Chroń**, a następnie **Ochrona**:
    
     ![Konfigurowanie ochrony dla etykiety usługi Azure Information Protection](../media/info-protect-protection-bar.png)

4. W bloku **Ochrona** można zmienić uprawnienia, wygaśnięcia zawartości i ustawienia dostępu w trybie offline. Aby uzyskać więcej informacji o konfiguracji ustawień ochrony, zobacz temat [Konfigurowanie etykiety w celu zastosowania ochrony przy użyciu usługi Rights Management](configure-policy-protection.md)
    
    Kliknij przycisk **OK**, aby zachować zmiany, a w bloku **Etykieta** kliknij przycisk **Zapisz**.

5. Aby udostępnić szablony aplikacjom użytkownika i usługom, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.


## <a name="next-steps"></a>Następne kroki

Tak jak w przypadku wszystkich zmian zasad usługi Azure Information Protection, zakończenie pobierania tych szablonów na komputer klienta usługi Azure Information Protection może potrwać do 15 minut. Aby uzyskać informacje dotyczące sposobu pobierania i odświeżania szablonów przez komputery i usługi, zobacz temat [Odświeżanie szablonów dla użytkowników i usług](refresh-templates.md).

Wszystkie elementy, które można skonfigurować w portalu Azure do tworzenia i zarządzania szablonami, można wykonać za pomocą programu PowerShell. Ponadto program PowerShell oferuje więcej opcji, które nie są dostępne w portalu. Aby uzyskać więcej informacji, zobacz [ochrony szablonów w programie PowerShell](configure-templates-with-powershell.md). 

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
