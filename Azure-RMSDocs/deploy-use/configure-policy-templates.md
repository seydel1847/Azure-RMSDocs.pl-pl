---
title: "Konfigurowanie szablonów w usłudze Azure Information Protection i zarządzanie nimi"
description: "Obecnie w wersji zapoznawczej można konfigurować szablony zarządzania prawami i zarządzać nimi przy użyciu zasad usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 1f41aad2d132e087e9122b2683be4b45185527de
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="configuring-and-managing-templates-in-the-azure-information-protection-policy"></a>Konfigurowanie szablonów i zarządzanie nimi przy użyciu zasad w usłudze Azure Information Protection

>*Dotyczy: Azure Information Protection*

>[!NOTE]
>Ta funkcja jest obecnie w wersji zapoznawczej i podlega częstym zmianom.
>
>Przed przetestowaniem tej funkcji w wersji zapoznawczej przy użyciu szablonów niestandardowych, które zostały utworzone w klasycznym portalu Azure, sprawdź, czy masz najnowsze kopie zapasowe szablonów. Wykonaj kopie zapasowe szablonów niestandardowych za pomocą polecenia cmdlet programu PowerShell [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) i w razie potrzeby użyj polecenia [Import-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate), aby je przywrócić.
>
>Z powodu różnic w implementacji nie zaleca się zarządzania tymi samymi szablonami z klasycznego portalu Azure i portalu Azure.


Szablony zarządzania prawami są teraz zintegrowane z zasadami usługi Azure Information Protection. 

**Subskrypcja, która obejmuje usługę Azure Information Protection na potrzeby klasyfikacji, etykietowania i ochrony (Azure Information Protection P1 lub P2):**

- Szablony zarządzania prawami dla Twojej dzierżawy są wyświetlane w nowej sekcji **Szablony** po etykietach. Szablony te można konwertować na etykiety lub można nadal nimi zarządzać jako osobnymi szablonami i połączyć je w ramach konfigurowania ochrony dla etykiety. 

**Jeśli masz subskrypcję obejmującą wyłącznie ochronę (subskrypcja usługi Office 365 obejmującą usługę Azure Rights Management):**

- Szablony zarządzania prawami dla Twojej dzierżawy są wyświetlane jako etykiety i obecnie są dostępne ustawienia konfiguracji specyficzne dla klasyfikacji i etykietowania. 


## <a name="considerations-for-templates-in-the-azure-portal"></a>Zagadnienia dotyczące szablonów w portalu Azure

Przed rozpoczęciem edycji tych szablonów lub konwersji do etykiet w portalu Azure należy pamiętać o następujących zmianach w implementacji szablonów zarządzania w klasycznym portalu Azure. Należy oczekiwać usunięcia kilku ograniczeń w wersji zapoznawczej:

- Po edycji lub konwersji szablonu i zapisaniu zasad usługi Azure Information Protection w oryginalnych [prawach użytkowania](configure-usage-rights.md) są wprowadzane następujące zmiany. W razie potrzeby można dodawać lub usuwać poszczególne prawa użytkowania za pomocą poleceń cmdlet programu PowerShell [New-AadrmRightsDefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) i [Set-AadrmTemplateProperty](/powershell/module/aadrm/new-aadrmrightsdefinition).
    
    - Usunięto opcję **Zapisz jako, eksportuj** (nazwa pospolita). W portalu Azure nie można ręcznie określić tego prawa użytkowania, ale jest ono uwzględnione w prawie użytkowania Pełna kontrola, które może zostać dodane w razie potrzeby.
    
    - Opcja **Zezwalaj na makra** (nazwa pospolita) jest automatycznie dodawana. To prawo użytkowania jest wymagane przez pasek usługi Azure Information Protection w aplikacji pakietu Office.
    
- Obecnie domyślne szablony są wyświetlane, ale nie można ich edytować ani poddawać konwersji. 

- Nie można skopiować ani usunąć szablonu. Aby usunąć szablon, użyj polecenia cmdlet programu PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate). 

- Obecnie szablony, które zostały skonfigurowane na potrzeby języków przy użyciu klasycznego portalu Azure lub programu PowerShell, nie wyświetlają nazw i opisów w tych językach, ale są one zachowane.

- Ustawienia **Opublikowane** i **Zarchiwizowane** są wyświetlane odpowiednio jako **Włączone**: **Włączone** i **Włączone**: **Wyłączone** w bloku **Etykiety**.

- Wyświetlanie szablonów dla działów (szablony, których zakres jest skonfigurowany) w ramach globalnych zasad. Obecnie edytowanie i zapisanie szablonu dla działu powoduje usunięcie konfiguracji zakresu. Odpowiednikiem szablonu o określonym zakresie w zasadach usługi Azure Information Protection jest [zasada z określonym zakresem](configure-policy-scope.md). W przypadku konwersji szablonu na etykietę możesz wybrać istniejący zakres.
    
    Ponadto obecnie nie można ustawić zgodności aplikacji dla szablonu dla działu. Jeśli to konieczne, możesz ustawić zgodność za pomocą polecenia cmdlet programu PowerShell [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty).

- Nowy szablon nie jest tworzony z kontenera **Szablony**; zamiast tego należy utworzyć etykietę z ustawieniem **Chroń** i skonfigurować prawa użytkowania i ustawienia w bloku **Ochrona**. Aby uzyskać pełne instrukcje, zobacz sekcję [Aby utworzyć nowy szablon](#to-create-a-new-template).

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

- Oryginalny szablon nie będzie już wyświetlany w obszarze **Szablony** i, aby edytować go w portalu Azure, można teraz dokonać edycji utworzonej etykiety. Szablon pozostaje dostępny dla usługi Azure Rights Management i wciąż można nim zarządzać za pomocą [poleceń programu PowerShell](administer-powershell.md).  

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

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
