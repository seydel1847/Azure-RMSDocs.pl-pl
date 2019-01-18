---
title: Typy plików obsługiwane przez usługę Azure Information Protection
description: Informacje techniczne na temat obsługiwanych typów plików, rozszerzenia nazw plików i poziomy ochrony dla administratorów, którzy są odpowiedzialni za klienta usługi Azure Information Protection dla systemu Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ''
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: cd0279bb45c04bc6f62c9eb20ffc006c7838b286
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393861"
---
# <a name="admin-guide-file-types-supported-by-the-azure-information-protection-client"></a>Podręcznik administratora: Typy plików obsługiwane przez klienta usługi Azure Information Protection

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, systemu Windows Server 2012, Windows Server 2008 R2*

Klient usługi Azure Information Protection może zastosować następujące środki względem dokumentów i wiadomości e-mail:

- Tylko klasyfikacja

- Klasyfikacja i ochrona

- Tylko ochrona

Klient usługi Azure Information Protection można też sprawdzić zawartość niektórych typów plików za pomocą dobrze znanych informacji poufnych typów lub wyrażeń regularnych, które definiujesz.

Użyj poniższych informacji, sprawdź, jakie typy plików, klient usługi Azure Information Protection obsługuje, zrozumieć różne poziomy ochrony i jak zmienić domyślny poziom ochrony i zidentyfikować, które pliki są automatycznie wykluczone) pominięte) z klasyfikacji i ochrony.

Dla typów wymienionych plików WebDav lokalizacje nie są obsługiwane.

## <a name="file-types-supported-for-classification-only"></a>Typy plików, dla których jest obsługiwana tylko klasyfikacja

Następujące typy plików mogą być klasyfikowane, nawet wtedy, gdy nie są chronione.

- **Adobe Portable Document Format**: .pdf

- **Microsoft Project**: .mpp, .mpt

- **Microsoft Publisher**: .pub

- **Microsoft XPS**: .xps .oxps

- **Obrazy**: .jpg, .jpe, .jpeg, .jif, .jfif, .jfi. png, .tif, .tiff

- **Autodesk Design Review 2013**: .dwfx

- **Adobe Photoshop**: .psd

- **Digital Negative**: .dng

- **Microsoft Office**: Typy plików w poniższej tabeli.

    Obsługiwane formaty plików dla tych typów plików są 97 – 2003 formaty plików i formaty Office Open XML dla następujących programów pakietu Office: Word, Excel i PowerPoint.

    |Typ pliku pakietu Office|Typ pliku pakietu Office|
    |----------------------------------|----------------------------------|
    |doc<br /><br />docm<br /><br />docx<br /><br />dot<br /><br />dotm<br /><br />dotx<br /><br />potm<br /><br />potx<br /><br />pps<br /><br />ppsm<br /><br />ppsx<br /><br />ppt<br /><br />pptm<br /><br />.pptx<br /><br />.vdw<br /><br />VSD|.vsdm<br /><br /> .vsdx<br /><br />.vss<br /><br />.vssm<br /><br />.vst<br /><br />.vstm<br /><br />.vssx<br /><br />.vstx<br /><br />xls<br /><br />xlsb<br /><br />xlt<br /><br />xlsm<br /><br />xlsx<br /><br />xltm<br /><br />.xltx|

Dodatkowe typy plików obsługują klasyfikację, gdy są one również chronione. Dla tych typów plików, zobacz [obsługiwane typy plików do klasyfikacji i ochrony](#supported-file-types-for-classification-and-protection) sekcji.

Na przykład w bieżącym [domyślne zasady](../configure-policy-default.md), **ogólne** etykieta dotyczy klasyfikacji i ochrony nie ma zastosowania. Można zastosować **ogólne** etykiety w pliku o nazwie sales.pdf, ale nie może zastosować tej etykiety w pliku o nazwie sales.txt. 

Również w bieżące zasady domyślne **poufne \ wszyscy pracownicy** dotyczy klasyfikacji i ochrony. W pliku o nazwie sales.pdf i plik o nazwie sales.txt może zastosować tej etykiety. Po prostu ochronę można zastosować do tych plików bez klasyfikacji.

## <a name="file-types-supported-for-protection"></a>Typy plików, dla których jest obsługiwana ochrona

Klient usługi Azure Information Protection obsługuje ochronę na dwóch różnych poziomach, jak opisano w poniższej tabeli.

|Typ ochrony|Natywna|Ogólne|
|----------------------|----------|-----------|
|Opis|W przypadku plików tekstowych, obrazów, plików pakietu Microsoft Office (Word, Excel, PowerPoint), plików pdf oraz innych typów plików aplikacji obsługujących usługę Rights Management ochrona natywna zapewnia silny poziom ochrony obejmujący szyfrowanie i wymuszanie praw (uprawnień).|W przypadku pozostałych aplikacji i typów plików ochrona ogólna zapewnia poziom ochrony obejmujący hermetyzację plików z wykorzystaniem typu pliku pfile oraz uwierzytelnianie umożliwiające weryfikację, czy użytkownik jest autoryzowany do otwierania pliku.|
|Protection|Ochrona plików jest wymuszana w następujący sposób:<br /><br />— Przed wyświetleniem chronionej zawartości musi nastąpić pomyślne uwierzytelnienie użytkowników odbierających plik pocztą e-mail lub mających dostęp do niego za pośrednictwem uprawnień do pliku lub uprawnień udziału.<br /><br />— Ponadto prawa do użytkowania i zasady, które zostały określone przez właściciela zawartości, gdy pliki były chronione są wymuszane, gdy zawartość jest wyświetlana w podglądzie usługi Azure Information Protection (dla chronionych plików tekstowych i obrazów) lub (skojarzonej aplikacji wszystkie inne obsługiwane typy plików).|Ochrona plików jest wymuszana w następujący sposób:<br /><br />— Przed wyświetleniem chronionej zawartości musi nastąpić pomyślne uwierzytelnienie osób uprawnionych do otwierania pliku i mających dostęp do niego. W przypadku niepowodzenia autoryzacji plik nie jest otwierany.<br /><br />— Prawa do użytkowania i zasady ustawiane przez właściciela zawartości są wyświetlane, aby informować autoryzowanych użytkowników o zamierzonych zasadach użytkowania.<br /><br />— Rejestrowana jest inspekcja autoryzowanych użytkowników otwierających pliki i uzyskujących do nich dostęp. Jednak prawa użytkowania nie są wymuszane.|
|Domyślny dla typów plików|Jest to domyślny poziom ochrony dla następujących typów plików:<br /><br />— Pliki tekstowe i pliki obrazów<br /><br />— Pliki pakietu Microsoft Office (programów Word, Excel i PowerPoint)<br /><br />— Pliki w formacie Portable Document Format (pdf)<br /><br />Więcej informacji znajduje się w sekcji [Typy plików, dla których jest obsługiwana klasyfikacja i ochrona](#supported-file-types-for-classification-and-protection).|Jest to domyślna ochrona dla wszystkich pozostałych typów plików (takich jak vsdx, rtf itd.), które nie są obsługiwane w ramach ochrony natywnej.|

Domyślny poziom ochrony stosowany przez klienta usługi Azure Information Protection można zmienić. Poziom domyślny można zmienić z natywnego na ogólny, z ogólnego na natywny, a nawet zupełnie uniemożliwić ochronę ze strony klienta usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz sekcję [Zmiana domyślnego poziomu ochrony plików](#changing-the-default-protection-level-of-files) w tym artykule.

Tę ochronę danych można zastosować automatycznie po wybraniu etykiety, która została skonfigurowana przez administratora, lub można określić własne ustawienia ochrony za pomocą [poziomów uprawnień](../configure-usage-rights.md#rights-included-in-permissions-levels). 

### <a name="file-sizes-supported-for-protection"></a>Rozmiary plików, dla których jest obsługiwana ochrona

Istnieją określone maksymalne rozmiary plików, dla których klient usługi Azure Information Protection obsługuje funkcje ochrony.

- **Pliki pakietu Office:**


  |                                                     Aplikacje pakietu Office                                                      |                                                Maksymalny rozmiar obsługiwanego pliku                                                 |
  |-----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
  |             Word 2007 (obsługiwane tylko przez usługi AD RMS)<br /><br />Word 2010<br /><br />Word 2013<br /><br />Word 2016             |                                          32-bitowe: 512 MB<br /><br />64-bitowe: 512 MB                                          |
  |           Excel 2007 (obsługiwane tylko przez usługi AD RMS)<br /><br />Excel 2010<br /><br />Excel 2013<br /><br />Excel 2016           |                      32-bitowe: 2 GB<br /><br />64-bitowe: Ograniczony tylko ilością dostępnego miejsca na dysku i pamięci                       |
  | PowerPoint 2007 (obsługiwane tylko przez usługi AD RMS)<br /><br />PowerPoint 2010<br /><br />PowerPoint 2013<br /><br />PowerPoint 2016 | 32-bitowe: Ograniczony tylko ilością dostępnego miejsca na dysku i pamięci<br /><br />64-bitowe: Ograniczony tylko ilością dostępnego miejsca na dysku i pamięci |


- **Wszystkie inne pliki**: 

  - Aby chronić inne typy plików i otwieranie tych typów plików w przeglądarce usługi Azure Information Protection: Maksymalny rozmiar pliku jest ograniczony tylko ilością dostępnego miejsca na dysku i pamięci.

  - Do wyłączania ochrony plików za pomocą [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) polecenia cmdlet: Maksymalny obsługiwany rozmiar pliku pst plików to 5 GB. Inne typy plików są ograniczony tylko ilością dostępnego miejsca na dysku i pamięci

    Porada: Jeśli potrzebujesz wyszukiwania lub odzyskiwanie chronionych elementach pst dużych plików, zobacz [wskazówki dotyczące używania Unprotect-RMSFile dla zbierania elektronicznych materiałów dowodowych](../configure-super-users.md#guidance-for-using-unprotect-rmsfile-for-ediscovery).

### <a name="supported-file-types-for-classification-and-protection"></a>Typy plików, dla których jest obsługiwana klasyfikacja i ochrona

W poniższej tabeli wymieniono podzbiór typów plików, które obsługują ochronę natywną przez klienta usługi Azure Information Protection oraz które także mogą być klasyfikowane. 

Te typy plików są identyfikowane oddzielnie, ponieważ jeśli są objęte ochroną natywną, oryginalne rozszerzenie nazwy pliku jest zmieniane, a pliki stają się plikami tylko do odczytu. W przypadku plików objętych ochroną ogólną oryginalne rozszerzenie nazwy pliku w każdej sytuacji zostaje zmienione na pfile.

> [!WARNING]
> Jeśli masz zapory, internetowego serwera proxy lub oprogramowania zabezpieczającego, które sprawdza pliki i podjąć działania w zależności od rozszerzenia nazwy pliku, może być konieczne ponownie skonfigurować te urządzenia sieciowe i oprogramowanie do obsługi tych nowych rozszerzeń nazw plików.

|Oryginalne rozszerzenie nazwy pliku|Chronione rozszerzenie nazwy pliku|
|--------------------------------|-------------------------------------|
|txt|ptxt|
|xml|pxml|
|jpg|pjpg|
|jpeg|pjpeg|
|.pdf|ppdf [[1]](#footnote-1)|
|.png|ppng|
|tif|ptif|
|tiff|ptiff|
|bmp|pbmp|
|gif|pgif|
|jpe|pjpe|
|jfif|pjfif|
|jt|pjt|

###### <a name="footnote-1"></a>Przypis 1
Za pomocą najnowszej wersji klienta usługi Azure Information Protection [domyślnie](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption), rozszerzenie nazwy pliku chronionego dokumentu PDF pozostaje jako PDF.

W poniższej tabeli wymieniono pozostałe typy plików, które obsługują ochronę natywną przez klienta usługi Azure Information Protection oraz które także mogą być klasyfikowane. Są to typy plików aplikacji pakietu Microsoft Office. Obsługiwane formaty plików dla tych typów plików są 97 – 2003 formaty plików i formaty Office Open XML dla następujących programów pakietu Office: Word, Excel i PowerPoint.

Rozszerzenia nazw tych plików nie zmieniają się po objęciu plików ochroną przez usługę Rights Management.

|Typy plików obsługiwanych przez pakiet Office|Typy plików obsługiwanych przez pakiet Office|
|----------------------------------|----------------------------------|
|doc<br /><br />docm<br /><br />docx<br /><br />dot<br /><br />dotm<br /><br />dotx<br /><br />potm<br /><br />potx<br /><br />pps<br /><br />ppsm<br /><br />ppsx<br /><br />ppt<br /><br />pptm<br /><br />.pptx<br /><br />.vsdm|.vsdx<br /><br />.vssm<br /><br />.vssx<br /><br />.vstm<br /><br />.vstx<br /><br />xla<br /><br />xlam<br /><br />xls<br /><br />xlsb<br /><br />xlt<br /><br />xlsm<br /><br />xlsx<br /><br />xltm<br /><br />xltx<br /><br />xps|

### <a name="changing-the-default-protection-level-of-files"></a>Zmiana domyślnego poziomu ochrony plików
Edytując rejestr, możesz zmienić sposób ochrony plików przez klienta usługi Azure Information Protection. Możesz na przykład wymusić, aby pliki obsługujące ochronę natywną były objęte ochroną ogólną przez klienta usługi Azure Information Protection.

W jakich sytuacjach warto to zrobić:

- Jeśli chcesz mieć pewność, że każdy użytkownik będzie mógł otworzyć plik, nawet jeśli nie ma aplikacji obsługującej ochronę natywną.

- Jeśli chcesz rozwiązać problem dotyczący systemów zabezpieczeń, które podejmują działania względem plików na podstawie ich rozszerzeń nazw i które można tak skonfigurować, aby uwzględniały rozszerzenie nazwy pliku pfile, ale nie wiele rozszerzeń nazw plików w ramach ochrony natywnej.

Analogicznie można wymusić stosowanie przez klienta usługi Azure Information Protection do ochrony natywnej plików, które domyślnie byłyby chronione w sposób ogólny. Ta akcja może być odpowiednie, jeśli masz aplikację obsługującą interfejsy API usługi RMS. Na przykład line-of-business napisane przez wewnętrzni programiści lub aplikacja zakupione od niezależnego dostawcę oprogramowania (ISV).

Możesz też wymusić blokowanie ochrony plików przez klienta usługi Azure Information Protection. Wówczas nie jest stosowana ani ochrona natywna, ani ogólna. Na przykład ta akcja może być wymagane, jeśli masz działającą automatycznie aplikację lub usługę, która musi być w stanie otworzyć określony plik, aby przetworzyć jego zawartość. Jeśli zablokujesz ochronę określonego typu plików, użytkownicy nie mogą ochronić plików tego typu za pomocą klienta usługi Azure Information Protection. Jeśli ktoś spróbuje to zrobić, zobaczy komunikat informujący o zablokowaniu przez administratora możliwości ochrony i będzie musiał zrezygnować z tego działania.

W celu skonfigurowania klienta usługi Azure Information Protection w taki sposób, aby była stosowana ogólna ochrona wszystkich plików, które domyślnie są chronione natywnie, wprowadź w rejestrze następujące zmiany. Jeśli klucz FileProtection nie istnieje, należy utworzyć go ręcznie.

1. Utwórz nowy klucz o nazwie * dla następującej ścieżki rejestru, który oznacza pliki z dowolnym rozszerzeniem nazwy:

    - Dla 32-bitowej wersji systemu Windows: **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection**

    - Dla 64-bitowej wersji systemu Windows: **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\FileProtection**

2. W nowo dodanym kluczu (np. HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\\\*) utwórz nową wartość ciągu (REG_SZ) o nazwie **Encryption** z wartością **Pfile**.

    To ustawienie powoduje stosowanie ochrony ogólnej przez klienta usługi Azure Information Protection.

Te dwa ustawienia powodują, że klient usługi Azure Information Protection stosuje ochronę ogólną do wszystkich plików mających rozszerzenie nazwy pliku. Jeśli taki był Twój cel, nie trzeba już nic konfigurować. Możesz jednak zdefiniować wyjątki dla określonych typów plików, aby nadal były objęte ochroną natywną. W tym celu dla każdego typu plików trzeba wprowadzić trzy dodatkowe zmiany do rejestru:

1. Aby uzyskać **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection** (32-bitowa Windows) lub **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\FileProtection** (Windows 64-bitowy): Dodaj nowy klucz o nazwie rozszerzenie nazwy pliku (bez kropki).

    Na przykład w przypadku plików z rozszerzeniem nazwy pliku docx utwórz klucz o nazwie **DOCX**.

2. W nowo dodanym kluczu typu pliku (np. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) utwórz nową wartość DWORD o nazwie **AllowPFILEEncryption** z wartością **0**.

3. W nowo dodanym kluczu typu pliku (np. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) utwórz nową wartość ciągu o nazwie **Encryption** z wartością **Native**.

W wyniku skonfigurowania tych ustawień wszystkie pliki będą chronione ogólnie z wyjątkiem plików mających rozszerzenie nazwy pliku docx. Pliki te są natywnie chronione przez klienta usługi Azure Information Protection.

Powtórz te trzy kroki dla innych typów plików, które chcesz zdefiniować jako wyjątki objęte ochronę natywną i nie chcesz, aby były objęte ochroną ogólną przez klienta usługi Azure Information Protection.

Podobne zmiany w rejestrze możesz wprowadzić w innych sytuacjach, zmieniając wartość ciągu **Encryption** obsługującego następujące wartości:

- **Pfile**: Ochrona ogólna

- **Natywne**: Ochrona natywna

- **Wyłącz**: Ochrona zablokowana

Aby uzyskać więcej informacji, zobacz [Konfiguracja interfejsu API plików](../develop/file-api-configuration.md) we wskazówkach dla deweloperów. W tej dokumentacji dla deweloperów ochrona ogólna jest określana jako „PFile”. 

## <a name="file-types-that-are-excluded-from-classification-and-protection"></a>Typy plików, które są wykluczone z klasyfikacji i ochrony

Aby uniemożliwić użytkownikom zmianę plików, które są krytyczne dla działania komputera, niektóre typy plików i folderów są automatycznie wykluczone z ochrony i klasyfikacji. Jeśli użytkownicy spróbują sklasyfikować lub chronić te pliki przy użyciu klienta usługi Azure Information Protection, zobaczy komunikat, że są one wyłączone.

- **Wykluczone typy plików**: lnk, .exe, .com, .cmd, .bat, .dll, .ini, .pst, .sca, .drm, .sys, .cpl, .inf, .drv, .dat, .tmp, msg, .msp, .msi, .pdb, JAR


- **Wykluczone foldery** : 
    - Windows
    - Program Files (\Program Files i \Program Files (x86))
    - \ProgramData 
    - \AppData (dla wszystkich użytkowników)

### <a name="file-types-that-are-excluded-from-classification-and-protection-by-the-azure-information-protection-scanner"></a>Typy plików, które są wykluczone z klasyfikacji i ochrony przez skaner usługi Azure Information Protection

Domyślnie skaner także wyklucza te same typy plików jako klienta usługi Azure Information Protection z następującymi wyjątkami:

Dla wersji ogólnie dostępnej:

- RTF, RAR i ZIP również są wyłączone.

W bieżącej wersji (wersja zapoznawcza): 

    - .rtf i RAR, również są wyłączone.

Możesz zmienić typy plików dołączone lub wykluczone w celu przeprowadzenia inspekcji pliku przez skaner:

Dla wersji ogólnie dostępnej Użyj następujących poleceń cmdlet programu PowerShell:

- [Set-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes)

- [Add-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileTypes)

- [Remove-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileTypes)

W bieżącej wersji (wersja zapoznawcza):

- Konfigurowanie **typów w celu skanowania plików** w profilu skanera przez [przy użyciu witryny Azure portal](../deploy-aip-scanner-preview.md#configure-the-scanner-in-the-azure-portal).

> [!NOTE]
> Jeśli dodasz .rtf — pliki do skanowania, należy uważnie monitorować skanera. Niektóre pliki .rtf nie można pomyślnie przeprowadzić inspekcji przez skaner tych plików nie wykona inspekcji i należy ponownie uruchomić usługę. 

Domyślnie skaner chroni tylko typów plików pakietu Office i plików PDF, wtedy, gdy są chronione przy użyciu standardu ISO do szyfrowania plików PDF. Aby zmienić to zachowanie skanera, edytowania rejestru, a następnie określ dodatkowe typy plików, które mają być chronione. Aby uzyskać instrukcje, zobacz [edycji rejestru skanera](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner) z instrukcjami wdrażania skanera.

### <a name="files-that-cannot-be-protected-by-default"></a>Pliki, które nie mogą być chronione domyślnie

Każdy plik jest chroniony hasłem nie można natywnie chronić przez klienta usługi Azure Information Protection, chyba że plik jest obecnie otwarty w aplikacji, która odnosi się do ochrony. Zostanie wyświetlony w większości przypadków pliki PDF chronionych hasłem, ale ta funkcja oferują również innych aplikacji, takich jak aplikacje pakietu Office.

Jeśli zmienisz [domyślne zachowanie](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption) klienta usługi Azure Information Protection, aby chroni pliki PDF z rozszerzeniem nazwy pliku ppdf klient nie może natywnie Włączanie lub wyłączanie ochrony plików PDF w jednej z następujących okoliczności:

- Pliku PDF, która jest oparta na formularzu.

- Chroniony plik PDF, który ma rozszerzenie nazwy pliku PDF.

    Klient usługi Azure Information Protection można chronić niechronionych plików PDF i może wyłączyć ochronę i włącz ponownie ochronę chroniony plik PDF, gdy ma ona rozszerzenie nazwy pliku ppdf.

### <a name="limitations-for-container-files-such-as-zip-files"></a>Ograniczenia dotyczące plików kontenera, takich jak pliki zip

Kontener plików są pliki, które zawierają inne pliki z typowym przykładem są pliki z rozszerzeniem .zip, które zawierają pliki skompresowane. Inne przykłady, RAR, .7z, msg plików i dokumentów PDF, które zawierają załączniki.

Można klasyfikować i chronić te pliki kontenerów, ale klasyfikacji i ochrony nie ma zastosowania do każdego pliku w kontenerze.

Jeśli masz plik kontenera, który zawiera sklasyfikowanych i chronionych plików, należy wyodrębnić pliki, aby zmienić ustawienia klasyfikacji i ochrony. Jednak można usunąć ochrony dla wszystkich plików w plikach obsługiwane kontenerów przy użyciu [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) polecenia cmdlet.

Przeglądarka usługi Azure Information Protection nie może otworzyć załączniki chronionego dokumentu PDF.

## <a name="file-types-supported-for-inspection"></a>Typy plików obsługiwane w celu przeprowadzenia inspekcji

Bez przeprowadzania dodatkowej konfiguracji klienta usługi Azure Information Protection używa Windows IFilter, aby sprawdzić zawartość dokumentów. Windows IFilter jest używany przez Windows Search do indeksowania. W rezultacie można sprawdził następujące typy plików korzystając z [skanera usługi Azure Information Protection](../deploy-aip-scanner.md), lub [AIPFileClassiciation zestaw](/powershell/module/azureinformationprotection/set-aipfileclassification) polecenia programu PowerShell.

|Typ aplikacji|Typ pliku|
|--------------------------------|-------------------------------------|
|Word|.docx; .docm; .dotm; .dotx|
|Excel|.xls; .xlt; .xlsx; .xltx; .xltm; .xlsm; .xlsb|
|PowerPoint|.ppt; .pps; .pot; .pptx; .ppsx; .pptm; .ppsm; .potx; .potm|
|PDF |.pdf|
|Tekst|.txt; .xml; .csv|

Bez dodatkowej konfiguracji można także kontrolowane innych typów plików. Można na przykład [zarejestrować rozszerzenie nazwy pliku niestandardowego, aby użyć istniejącej procedury obsługi filtra Windows szukać plików tekstowych](https://docs.microsoft.com/windows/desktop/search/-search-ifilter-registering-filters), można zainstalować dodatkowe filtry od dostawców oprogramowania.

Aby sprawdzić, jakie filtry są zainstalowane, zobacz [znajdowanie procedury obsługi filtra dla danego rozszerzenia pliku](https://docs.microsoft.com/windows/desktop/search/-search-ifilter-registering-filters#finding-a-filter-handler-for-a-given-file-extension) sekcji w Podręczniku dewelopera Windows Search.

Poniższe sekcje mają instrukcje dotyczące konfiguracji, aby sprawdzić pliki zip i plików TIFF.

### <a name="to-inspect-zip-files"></a>Aby sprawdzić pliki zip

Skaner usługi Azure Information Protection i [AIPFileClassiciation zestaw](/powershell/module/azureinformationprotection/set-aipfileclassification) polecenia programu PowerShell można sprawdzić pliki zip, po wykonaniu tych instrukcji:

1. Komputera z programem skaner lub sesji programu PowerShell, należy zainstalować [pakietu Office 2010 filtru pakietu z dodatkiem SP2](https://support.microsoft.com/en-us/help/2687447/description-of-office-2010-filter-pack-sp2).

2. Skanera: Chyba że używasz bieżącą wersję zapoznawczą skaner obejmują plików .zip, aby sprawdził, zgodnie z opisem w [skanera usługi Azure Information Protection](#file-types-that-are-excluded-from-classification-and-protection-by-the-azure-information-protection-scanner) sekcji.

3. Skanera: Po znalezieniu poufne informacje, jeśli plik zip powinien można klasyfikować i chronić za pomocą etykiety, Dodaj wpis rejestru dla rozszerzenie nazwy pliku ochrona ogólna (pfile), zgodnie z opisem w [edycji rejestru skanera](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner) z instrukcjami wdrażania skanera.

Przykładowy scenariusz po wykonaniu tych kroków: 

Plik o nazwie **accounts.zip** zawiera arkusze kalkulacyjne programu Excel z numerów kart kredytowych. Zasady usługi Azure Information Protection ma etykietę o nazwie **poufne \ Finanse**, który jest skonfigurowany do odnajdywania numery kart kredytowych i automatycznie stosować etykiety z ochroną, która ogranicza dostęp do grupy Finanse. 

Po sprawdzeniu pliku, skaner klasyfikuje ten plik jako **poufne \ Finanse**, stosuje ochronę ogólną do pliku, tak aby tylko członkowie grupy Finanse możliwe jego rozpakowanie i zmienia nazwę pliku  **accounts.zip.pfile**.

### <a name="to-inspect-tiff-files-by-using-ocr"></a>Aby sprawdzić .tiff plików za pomocą oprogramowania OCR

Skaner usługi Azure Information Protection i [AIPFileClassiciation zestaw](/powershell/module/azureinformationprotection/set-aipfileclassification) polecenia programu PowerShell umożliwia sprawdzanie obrazów TIFF z rozszerzeniem nazwy pliku TIFF, po zainstalowaniu Windows TIFF optyczne rozpoznawanie znaków (OCR) IFilter funkcji, a następnie skonfiguruj [Windows TIFF IFilter ustawienia](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-7/dd744701%28v%3dws.10%29) na komputerze z systemem skaner lub sesji programu PowerShell.

Skanera: Po znalezieniu poufne informacje, jeśli plik TIFF powinien można klasyfikować i chronić za pomocą etykiety, Dodaj wpis rejestru dla rozszerzenie nazwy pliku są chronione natywnie, zgodnie z opisem w [edycji rejestru skanera](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner) z instrukcjami wdrażania skanera.

## <a name="next-steps"></a>Następne kroki
Po zidentyfikowaniu typów plików obsługiwanych przez klienta usługi Azure Information Protection zapoznaj się następujące zasoby, aby uzyskać dodatkowe informacje, przydatnymi przy obsłudze tego klienta:

- [Dostosowania](client-admin-guide-customizations.md)

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)

