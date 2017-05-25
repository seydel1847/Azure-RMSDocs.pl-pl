---
title: "Ochrona za pomocą usługi Azure RMS z użyciem infrastruktury FCI w systemie Windows Server — AIP"
description: "Instrukcje dotyczące używania klienta usługi Rights Management (RMS) z narzędziem RMS Protection Tool w celu skonfigurowania Menedżera zasobów serwera plików oraz infrastruktury klasyfikacji plików (FCI)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f3bdfee3a3dfa60c7cc81a553f3c889c30134a6a
ms.sourcegitcommit: b471c20eda011a7b75ee801c34081fb4773b64dc
ms.translationtype: HT
ms.contentlocale: pl-PL
---
# <a name="rms-protection-with-windows-server-file-classification-infrastructure-fci"></a>Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) w systemie Windows Server

>*Dotyczy: Azure Information Protection, Windows Server 2016, Windows Server 2012, Windows Server 2012 R2*

Ten artykuł zawiera instrukcje i skrypt umożliwiające użycie klienta usługi Azure Information Protection i programu PowerShell w celu skonfigurowania Menedżera zasobów serwera plików oraz infrastruktury klasyfikacji plików (FCI).

To rozwiązanie pozwala automatycznie chronić pliki w folderze na serwerze plików z systemem Windows Server lub pliki, które spełniają określone kryteria. Na przykład pliki, które zostały sklasyfikowane jako zawierające informacje poufne lub szczególnie chronione. Wdrożenie tej usługi w organizacji jest niezbędne, jako że omawiane rozwiązanie łączy się z poziomu usługi Azure Information Protection bezpośrednio z usługą Azure Rights Management w celu zapewnienia ochrony plików.

> [!NOTE]
> Mimo że usługa Azure Information Protection obejmuje [łącznik](../deploy-use/deploy-rms-connector.md), który obsługuje infrastrukturę klasyfikacji plików, to rozwiązanie obsługuje wyłącznie ochronę natywną, np. ochronę plików pakietu Office.
> 
> Aby obsługiwać wiele typy plików za pomocą infrastruktury klasyfikacji plików systemu Windows Server, należy użyć modułu **AzureInformationProtection** programu PowerShell w sposób opisany w tym artykule. Polecenia cmdlet usługi Azure Information Protection, podobnie jak klient usługi Azure Information Protection, obsługują nie tylko ochronę natywną, ale też ochronę ogólną, co oznacza, że możliwa jest ochrona plików innych niż dokumenty pakietu Office. Aby uzyskać więcej informacji, zobacz sekcję [Typy plików obsługiwane przez klienta usługi Azure Information Protection](client-admin-guide-file-types.md) w podręczniku administratora klienta usługi Azure Information Protection.

Poniższe instrukcje dotyczą systemu Windows Server 2012 R2 lub Windows Server 2012. W przypadku korzystania z innych obsługiwanych wersji systemu Windows może okazać się konieczne dostosowanie niektórych kroków z powodu różnic między używaną wersją systemu operacyjnego i wersją opisaną w tym artykule.

## <a name="prerequisites-for-azure-rights-management-protection-with-windows-server-fci"></a>Wymagania wstępne dotyczące ochrony za pomocą usług Azure Rights Management z użyciem infrastruktury FCI w systemie Windows Server
Wymagania wstępne dotyczące tych instrukcji:

-  Na każdym serwerze plików, na którym będzie uruchamiany Menedżer zasobów plików z infrastrukturą klasyfikacji plików:
    
    - Zainstalowano Menedżer zasobów serwera plików jako jedną z usług ról dla roli Usługi plików.
    
    - Zidentyfikowano lokalny folder zawierający pliki, które mają być chronione przez usługę Rights Management. Na przykład C:\FileShare.
    
    - Zainstalowano moduł AzureInformationProtection i skonfigurowano wymagania wstępne dotyczące usługi Azure Rights Management. Aby uzyskać więcej informacji, zobacz temat [Używanie środowiska PowerShell z klientem usługi Azure Information Protection](client-admin-guide-powershell.md). Do usługi Azure Rights Management należy dołączyć w szczególności następujące wartości, korzystając z nazwy głównej usługi: **BposTenantId**, **AppPrincipalId**, i **Symmetric key**. 
    
    - Aby zmienić domyślny poziom ochrony (natywnej lub ogólnej) dla określonych rozszerzeń nazw plików, należy dokonać edycji rejestru zgodnie z opisem w sekcji [Zmiana domyślnego poziomu ochrony plików](client-admin-guide-file-types.md#changing-the-default-protection-level-of-files) w podręczniku administratora.
    
    - Masz połączenie z Internetem z ustawieniami komputera skonfigurowanymi w razie potrzeby dla serwera proxy. Na przykład: `netsh winhttp import proxy source=ie`
    
- Zsynchronizowano lokalne konta użytkowników usługi Active Directory, w tym ich adresy e-mail, z usługą Azure Active Directory lub Office 365. Jest to wymagane dla wszystkich użytkowników, którzy mogą wymagać dostępu do plików po objęciu ich ochroną przez infrastrukturę FCI i usługę Azure Rights Management. W przypadku pominięcia tego kroku (na przykład w środowisku testowym) dostęp użytkowników do tych plików może zostać zablokowany. Aby uzyskać więcej informacji na temat tego wymagania, zobacz artykuł [Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection](../plan-design/prepare.md).
    
- Na serwer plików zostały pobrane szablony usługi Rights Management oraz został rozpoznany identyfikator szablonu, który będzie chronić pliki. W tym celu użyj polecenia cmdlet [Get-RMSTemplate](/powershell/azureinformationprotection/vlatest/get-rmstemplate). W tym scenariuszu nie są obsługiwane szablony przypisane do działów, więc należy użyć szablonu, który nie został skonfigurowany dla zakresu. Ewentualnie konfiguracja zakresu musi zawierać taką opcję zgodności aplikacji, dla której pole wyboru **Pokaż ten szablon wszystkim użytkownikom, gdy aplikacje nie obsługują tożsamości użytkownika** jest zaznaczone.

## <a name="instructions-to-configure-file-server-resource-manager-fci-for-azure-rights-management-protection"></a>Instrukcje dotyczące konfiguracji infrastruktury klasyfikacji plików (FCI) Menedżera zasobów serwera plików na potrzeby ochrony z użyciem usługi Azure Rights Management
Wykonaj te instrukcje, aby automatycznie chronić wszystkie pliki w folderze przy użyciu skryptu programu PowerShell w ramach zadania niestandardowego. Wykonaj te procedury w następującej kolejności:

1. Zapisz skrypt programu PowerShell.

2. Utwórz właściwość klasyfikacji dla usługi Rights Management (RMS).

3. Utwórz regułę klasyfikacji (Klasyfikuj do ochrony za pomocą usługi RMS).

4. Skonfiguruj harmonogram klasyfikacji.

5. Utwórz niestandardowe zadanie zarządzania plikami (Chroń pliki za pomocą usługi RMS).

6. Przetestuj konfigurację, ręcznie uruchamiając regułę i zadanie.

Po wykonaniu tych instrukcji wszystkie pliki w wybranym folderze zostaną sklasyfikowane z niestandardowymi właściwościami usługi RMS i będą chronione za pomocą usługi Rights Management. Na potrzeby bardziej złożonej konfiguracji selektywnej ochrony plików można utworzyć inną właściwość i regułę klasyfikacji zadania zarządzania plikami chroniącego tylko wybrane pliki, a następnie użyć jej.

Należy pamiętać, że po wprowadzeniu zmian w szablonie usługi Rights Management używanym do infrastruktury FCI należy uruchomić polecenie `Get-RMSTemplate -Force` na komputerze serwera plików w celu pobrania zaktualizowanego szablonu. Zaktualizowany szablon zostanie użyty do ochrony nowych plików. Jeśli zmiany wprowadzone w szablonie są na tyle istotne, że należy ponownie włączyć ochronę plików na serwerze plików, można to zrobić, uruchamiając interaktywnie polecenie cmdlet Protect-RMSFile cmdlet przy użyciu konta, które ma prawa do eksportu plików lub pełnej kontroli. Należy także uruchomić polecenie `Get-RMSTemplate -Force` na tym serwerze plików w przypadku publikowania nowego szablonu, którego chcesz używać dla infrastruktury FCI.

### <a name="save-the-windows-powershell-script"></a>Zapisz skrypt programu Windows PowerShell.

1.  Skopiuj zawartość [skryptu programu Windows PowerShell](fci-script.md) na potrzeby ochrony za pomocą usług Azure RMS przy użyciu Menedżera zasobów serwera plików. Wklej zawartość skryptu i nazwij plik **Ochrona-RMS-FCI.ps1** na własnym komputerze.

2.  Przejrzyj skrypt i wprowadź następujące zmiany:
    
    - Wyszukaj następujący ciąg i zastąp go własną wartością AppPrincipalId, która jest używana z poleceniem cmdlet [Set-RMSServerAuthentication](/powershell/azureinformationprotection/vlatest/set-rmsserverauthentication), aby nawiązać połączenie z usługą Azure Rights Management:

        ```
        <enter your AppPrincipalId here>
        ```
        Przykładowy skrypt może wyglądać następująco:

        `[Parameter(Mandatory = $false)]`

        `[Parameter(Mandatory = $false)]             [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",`

    -   Wyszukaj następujący ciąg i zastąp go własnym kluczem symetrycznym, który jest używany z poleceniem cmdlet [Set-RMSServerAuthentication](/powershell/azureinformationprotection/vlatest/set-rmsserverauthentication), aby nawiązać połączenie z usługą Azure Rights Management:

        ```
        <enter your key here>
        ```
        Przykładowy skrypt może wyglądać następująco:

        `[Parameter(Mandatory = $false)]`

        `[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="`

    -   Wyszukaj następujący ciąg i zastąp go własnym identyfikatorem BposTenantId (identyfikatorem dzierżawy), który jest używany z poleceniem cmdlet [Set-RMSServerAuthentication](/powershell/azureinformationprotection/vlatest/set-rmsserverauthentication), aby nawiązać połączenie z usługą Azure Rights Management:

        ```
        <enter your BposTenantId here>
        ```
        Przykładowy skrypt może wyglądać następująco:

        `[Parameter(Mandatory = $false)]`

        `[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",`

3.  Podpisz skrypt. Jeśli nie podpiszesz skryptu (bezpieczniejsza opcja), należy skonfigurować program Windows PowerShell na serwerach, na których uruchomiono skrypt. Na przykład uruchom sesję programu Windows PowerShell, korzystając z opcji **Uruchom jako Administrator** i wpisz **Set-ExecutionPolicy RemoteSigned**. Jednak taka konfiguracja pozwala na uruchomienie wszystkich niepodpisanych skryptów przechowywanych na tym serwerze (mniej bezpieczna opcja).

    Aby uzyskać więcej informacji na temat podpisywania skryptów programu Windows PowerShell, zobacz artykuł [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) w bibliotece dokumentacji programu PowerShell.

4.  Zapisz plik lokalnie na każdym serwerze plików, na którym będzie uruchamiany Menedżer zasobów plików z infrastrukturą klasyfikacji plików. Na przykład zapisz plik w katalogu **C:\RMS-Protection**. Jeśli używasz innej ścieżki lub nazwy folderu, wybierz ścieżkę i folder, których nazwy nie zawierają spacji. Zabezpiecz ten plik, używając uprawnień NTFS, aby nieautoryzowani użytkownicy nie mogli go zmodyfikować.

Teraz możesz rozpocząć konfigurowanie Menedżera zasobów serwera plików.

### <a name="create-a-classification-property-for-rights-management-rms"></a>Utwórz właściwość klasyfikacji dla usługi Rights Management (RMS).

-   W węźle Menedżer zasobów serwera plików w pozycji Zarządzanie klasyfikacją utwórz nową lokalną właściwość:

    -   **Nazwa**: Wpisz **RMS**.

    -   **Opis**: Wpisz **Ochrona za pomocą usługi Rights Management**.

    -   **Typ właściwości**: Wybierz **Tak/Nie**.

    -   **Wartość**: Wybierz **Tak**.

Teraz można utworzyć regułę klasyfikacji korzystającą z tej właściwości.

### <a name="create-a-classification-rule-classify-for-rms"></a>Utwórz regułę klasyfikacji (Klasyfikuj do ochrony za pomocą usługi RMS).

-   Utwórz nową regułę klasyfikacji:

    -   Na karcie **Ogólne**:

        -   **Nazwa**: Wpisz **Klasyfikuj do ochrony za pomocą usługi RMS**.

        -   **Włączone**: Zachowaj ustawienie domyślne, czyli zaznaczenie tego pola wyboru.

        -   **Opis**: wpisz **Klasyfikuj wszystkie pliki w folderze &lt;nazwa folderu&gt; do ochrony za pomocą usługi Rights Management**.

            Zastąp *&lt;nazwę folderu&gt;* wybraną nazwą folderu. Na przykład **Klasyfikuj wszystkie pliki w folderze C:\FileShare do ochrony za pomocą usług Rights Management**.

        -   **Zakres**: Dodaj wybrany folder. Na przykład **C:\FileShare**.

            Nie zaznaczaj pól wyboru.

    -   Na karcie **Klasyfikacja**:

    -   **Metoda klasyfikacji**: Wybierz **Klasyfikator folderów**.

    -   Nazwa **Właściwości**: Wybierz **RMS**.

    -   **Wartość** właściwości: Wybierz **Tak**.

Chociaż zasady klasyfikacji można uruchomić ręcznie, dla trwających operacji ta reguła powinna być uruchamiana zgodnie z harmonogramem, dzięki czemu nowe pliki zostaną sklasyfikowane z właściwością usługi RMS.

### <a name="configure-the-classification-schedule"></a>Skonfiguruj harmonogram klasyfikacji.

-   Na karcie **Automatyczna klasyfikacja**:

    -   **Włącz ustalony harmonogram**: Zaznacz to pole wyboru.

    -   Skonfiguruj harmonogram uruchamiania wszystkich reguł klasyfikacji, w tym naszej nowej reguły do klasyfikowania plików za pomocą właściwości usługi RMS.

    -   **Zezwalaj na ciągłą klasyfikację nowych plików**: zaznaczenie tego pola wyboru spowoduje, że nowe pliki będą klasyfikowane.

    -   Opcjonalnie: Wprowadź wszelkie potrzebne zmiany, takie jak konfigurowanie opcji raportów i powiadomień.

Po zakończeniu konfigurowania klasyfikacji można przejść do konfigurowania zadania zarządzania w celu zastosowania ochrony plików przy pomocy usługi RMS.

### <a name="create-a-custom-file-management-task-protect-files-with-rms"></a>Utwórz niestandardowe zadanie zarządzania plikami (Chroń pliki za pomocą usługi RMS).

-   W **Zadaniach zarządzania plikami** utwórz nowe zadanie zarządzania plikami:

    -   Na karcie **Ogólne**:

        -   **Nazwa zadania**: Wpisz **Chroń pliki za pomocą usługi RMS**

        -   Zachowaj zaznaczenie pola wyboru **Włącz**.

        -   **Opis**: Wpisz **Chroń pliki w folderze &lt;nazwa folderu&gt; za pomocą usługi Rights Management oraz szablon za pomocą skryptu Windows PowerShell.**

            Zastąp *&lt;nazwę folderu&gt;* wybraną nazwą folderu. Na przykład **Chroń pliki w folderze C:\FileShare za pomocą usługi Rights Management oraz szablon za pomocą skryptu Windows PowerShell.**

        -   **Zakres**: Zaznacz wybrany folder. Na przykład **C:\FileShare**.

            Nie zaznaczaj pól wyboru.

    -   Na karcie **Akcja**:

        -   **Typ**: Wybierz **Niestandardowe**

        -   **Plik wykonywalny**: Określ następujące ustawienia:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Jeśli system Windows nie znajduje się na dysku C:, należy zmodyfikować tę ścieżkę lub przejść do tego pliku.

        -   **Argument**: Określ następujące ustawienia, podając własne wartości &lt;ścieżki&gt; i &lt;identyfikatora szablonu&gt;:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail [Source File Owner Email]"
            ```
            Jeśli np. skrypt został skopiowany do katalogu C:\RMS-Protection, a identyfikator szablonu wskazanego na podstawie wymagań wstępnych to e6ee2481-26b9-45e5-b34a-f744eacd53b0, określ następujące ustawienia:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"`

            W tym poleceniu zarówno **[Ścieżka pliku źródłowego]**, jak i **[E-mail właściciela pliku źródłowego]** są zmiennymi specyficznymi dla infrastruktury FCI i należy je wpisać dokładnie w takiej formie, w jakiej występują w powyższym poleceniu. Pierwsza z nich jest używana przez infrastrukturę FCI w celu automatycznego określenia wskazanego pliku w folderze, a druga jest przeznaczona dla infrastruktury FCI w celu automatycznego pobrania adresu e-mail nazwanego właściciela wskazanego pliku. To polecenie jest powtarzane dla każdego pliku w folderze, co w użytym przykładzie oznacza wszystkie pliki w folderze C:\FileShare, które dodatkowo jako właściwość klasyfikacji pliku mają usługę RMS.

            > [!NOTE]
            > Parametr i wartość **-OwnerMail [E-mail właściciela pliku źródłowego]** zapewniają, że po włączeniu ochrony pliku właściciel oryginalnego pliku otrzymuje uprawnienia właściciela zarządzania prawami pliku. Dzięki temu pierwotny właściciel pliku ma uprawnienia do zarządzania prawami dostępu do swoich plików. Kiedy pliki są tworzone przez użytkownika domeny, adres e-mail jest automatycznie pobierany z usługi Active Directory przy użyciu nazwy konta użytkownika w pliku właściwości właściciela. Aby to zrobić, serwer plików musi być w tej samej domenie lub zaufanej domenie co użytkownik.
            > 
            > W miarę możliwości należy przypisać pierwotnych właścicieli do chronionych dokumentów, aby zapewnić im dalszą pełną kontrolę nad utworzonymi przez nich plikami. Jeśli jednak użyjesz zmiennej [E-mail właściciela pliku źródłowego] zgodnie z powyższymi instrukcjami, a plik nie ma zdefiniowanego użytkownika domeny jako właściciela (na przykład do utworzenia pliku użyto konta lokalnego, więc jako właściciela wyświetlany jest SYSTEM), to skrypt zakończy się niepowodzeniem.
            > 
            > W przypadku plików, których właścicielem nie jest użytkownik domeny, możesz skopiować i zapisać pliki jako użytkownik domeny, stając się właścicielem tylko tych plików. Lub, jeśli masz uprawnienia, możesz ręcznie zmienić właściciela.  Możesz także podać konkretny adres e-mail (np. własny lub adres grupy działu informatycznego) zamiast zmiennej [E-mail właściciela pliku źródłowego], co oznacza, że wszystkie pliki, które chronisz za pomocą tego skryptu, będą używać tego adresu e-mail do definiowania nowego właściciela.

    -   **Uruchom polecenie jako**: Wybierz **System lokalny**

    -   Na karcie **Warunek**:

        -   **Właściwość**: Wybierz **RMS**

        -   W obszarze **Operator** wybierz pozycję **Równe**.

        -   **Wartość**: Wybierz **Tak**.

    -   Na karcie **Harmonogram**:

        -   **Uruchom o**: Skonfiguruj preferowany harmonogram.

            Wykonanie skryptu może zająć dużo czasu. Chociaż to rozwiązanie chroni wszystkie pliki w folderze, skrypt jest wykonywany jednokrotnie dla każdego pliku, przy każdym uruchomieniu. Mimo że trwa to dłużej niż obsługiwana przez klienta Azure Information Protection ochrona wszystkich plików jednocześnie, to konfiguracja ochrony każdego pliku z osobna jest bardziej skuteczna. Na przykład chronione pliki mogą mieć różnych właścicieli (przy zachowaniu pierwotnego właściciela), gdy jest używana zmienna [E-mail właściciela pliku źródłowego]. Akcja ochrony każdego pliku osobno będzie wymagana, jeśli użytkownik zmieni konfigurację w celu ochrony tylko wybranych plików, a nie wszystkich plików w folderze.

        -   **Uruchamiaj stale w nowych plikach**: Zaznacz to pole wyboru.

### <a name="test-the-configuration-by-manually-running-the-rule-and-task"></a>Przetestuj konfigurację, ręcznie uruchamiając regułę i zadanie.

1.  Uruchom regułę klasyfikacji:

    1.  Kliknij pozycję **Reguły klasyfikacji** &gt; **Uruchom teraz klasyfikację przy użyciu wszystkich reguł**

    2.  Kliknij pozycję **Zaczekaj na zakończenie operacji klasyfikacji**, a następnie kliknij przycisk **OK**.

2.  Poczekaj na zamknięcie okna dialogowego **Wykonywanie klasyfikacji**, a następnie przejrzyj wyniki w raporcie, który zostanie automatycznie wyświetlony. Dla pola **Właściwości** powinna zostać wyświetlona wartość **1**. Powinna również zostać wyświetlona liczba plików w folderze. Sprawdź właściwości plików w wybranym folderze za pomocą Eksploratora plików. Na karcie **Klasyfikacja** powinna zostać wyświetlona nazwa **RMS** jako nazwa właściwości i pozycja **Tak** dla jej **wartości**.

3.  Uruchom zadanie zarządzania plikami:

    1.  Kliknij węzeł **Zadania zarządzania plikami** &gt; **Chroń pliki za pomocą usługi RMS** &gt; **Uruchom teraz zadanie zarządzania plikami**

    2.  Kliknij pozycję **Zaczekaj na zakończenie zadania**, a następnie kliknij przycisk **OK**.

4.  Poczekaj na zamknięcie okna dialogowego **Uruchamianie zadania zarządzania plikami**, a następnie przejrzyj wyniki w raporcie, który zostanie automatycznie wyświetlony. Liczba plików w wybranym folderze programu powinna być widoczna w polu **Pliki**. Upewnij się, że pliki w wybranym folderze są teraz chronione przez usługę Rights Management. Na przykład jeśli wybrany folder to C:\FileShare, wpisz następujące polecenie w sesji środowiska Windows PowerShell i upewnij się, że żaden plik nie ma statusu **Niechroniony**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Wskazówki dotyczące rozwiązywania problemów:
    > 
    > -   Jeśli raport zawiera wartość **0** zamiast liczby plików w folderze, oznacza to, że skrypt nie został uruchomiony. Po pierwsze sprawdź sam skrypt przez załadowanie go w środowisku Windows PowerShell ISE, aby zweryfikować jego zawartość, a następnie spróbuj go uruchomić, aby zobaczyć, czy zostaną wyświetlone błędy. Jeśli nie zostaną określone argumenty, skrypt podejmie próbę nawiązania połączenia z usługą Azure Rights Management i wykonania uwierzytelnienia za jej pomocą.
    > 
    >     -   Jeśli skrypt zgłasza, że nie może nawiązać połączenia z usługą Azure Rights Management (Azure RMS), sprawdź wartości wyświetlane dla konta głównego usługi określonego w skrypcie. Aby uzyskać więcej informacji o tworzeniu konta głównego usługi, zobacz [Wymaganie wstępne 3: włączanie lub wyłączanie ochrony plików bez interakcji z użytkownikiem](client-admin-guide-powershell.md#prerequisite-3-to-protect-or-unprotect-files-without-user-interaction) opisane w podręczniku administratora klienta usługi Azure Information Protection.
    >     -   Jeśli skrypt zgłasza, że może nawiązać połączenie z usługami Azure RMS, sprawdź, czy może znaleźć wskazany szablon, uruchamiając polecenie [Get-RMSTemplate](/powershell/azureinformationprotection/vlatest/get-rmstemplate) bezpośrednio w programie Windows PowerShell na serwerze. Określony szablon powinien pojawić się w zwracanych w wynikach.
    > -   Jeśli skrypt samodzielnie uruchamia się w środowisku Windows PowerShell ISE bez błędów, spróbuj uruchomić go w następujący sposób z sesji programu PowerShell, określając nazwę pliku do ochrony i bez parametru -OwnerEmail:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '<full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Jeśli skrypt zostanie uruchomiony pomyślnie w tej sesji środowiska Windows PowerShell, sprawdź wpisy dla pozycji **Główne** i **Argument** w akcji zadania zarządzania plikami.  Jeśli określono parametr **-OwnerEmail [E-mail właściciela pliku źródłowego]**, spróbuj go usunąć.
    > 
    >         Jeśli zadanie zarządzania plikami działa pomyślnie bez określenia parametru **-OwnerEmail [E-mail właściciela pliku źródłowego]**, upewnij się, że właścicielem niechronionych plików jest użytkownik domeny, a nie **SYSTEM**.  W tym celu użyj karty **Zabezpieczenia** we właściwościach pliku, a następnie kliknij pozycję **Zaawansowane**. Wartość **Właściciel** jest wyświetlana bezpośrednio po wartości **Nazwa** pliku. Sprawdź także, czy serwer plików jest w tej samej domenie lub w zaufanej domenie, aby wyszukać adres e-mail użytkownika z usług domenowych Active Directory.
    > -   Jeśli raport zawiera poprawną liczbę plików, ale pliki nie są chronione, spróbuj uruchomić ochronę ręcznie, za pomocą polecenia cmdlet [Protect-RMSFile](/powershell/azureinformationprotection/vlatest/protect-rmsfile), aby sprawdzić, czy są wyświetlane błędy.

Po potwierdzeniu, że zadania zostały pomyślnie uruchomione, można zamknąć Menedżera zasobów plików. Nowe pliki będą automatycznie klasyfikowane i obejmowane ochroną podczas przeprowadzania zaplanowanych zadań. 

## <a name="modifying-the-instructions-to-selectively-protect-files"></a>Modyfikowanie instrukcji na potrzeby selektywnej ochrony plików
Jeżeli poprzednie instrukcje działają, można je łatwo zmodyfikować na potrzeby bardziej zaawansowanej konfiguracji. Na przykład uruchom ochronę plików za pomocą tego samego skryptu, ale obejmij nią tylko pliki, które zawierają dane osobowe, wybierając szablon z bardziej restrykcyjnymi uprawnieniami.

Aby to zrobić, użyj jednej z wbudowanych właściwości klasyfikacji (na przykład **Dane osobowe**) lub utwórz własną właściwość. Następnie utwórz nową regułę, która używa tej właściwości. Na przykład możesz wybrać pozycję **Klasyfikator zawartości**, wybrać właściwość **Dane osobowe** o wartości **Wysokie** i skonfigurować ciąg lub wzorzec wyrażenia, który identyfikuje plik do skonfigurowania dla tej właściwości (np. **Data urodzenia**).

Teraz wystarczy tylko utworzyć nowe zadanie zarządzania plikami, które korzysta z tego samego skryptu, ale np. z innego szablonu, i skonfigurować warunek dla właśnie skonfigurowanej właściwości klasyfikacji. Na przykład zamiast warunku, który został wcześniej skonfigurowany (właściwość **RMS**, **Równe**, **Tak**), wybierz właściwość **Dane osobowe** z ustawieniem **Operator** o wartości **Równe** i ustawieniem **Wartość** o wartości **Wysokie**.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
