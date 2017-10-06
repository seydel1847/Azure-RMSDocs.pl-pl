---
title: "Typy plików obsługiwane przez usługę Azure Information Protection"
description: "Informacje techniczne na temat obsługiwanych typów plików, rozszerzenia nazw plików i poziomy ochrony dla administratorów, którzy są odpowiedzialni za klienta usługi Azure Information Protection dla systemu Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/03/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5a3d13861e3eff0cfaf4a92eb005b8192f2b447c
ms.sourcegitcommit: 4d730631ea8c16c7150b794722bb23921f1b2008
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2017
---
# <a name="file-types-supported-by-the-azure-information-protection-client"></a>Typy plików obsługiwane przez klienta usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Klient usługi Azure Information Protection może zastosować następujące środki względem dokumentów i wiadomości e-mail:

- Tylko klasyfikacja

- Klasyfikacja i ochrona

- Tylko ochrona

Skorzystaj z poniższych informacji, aby dowiedzieć się, jakie typy plików są obsługiwane, jakie są poziomy ochrony i jak zmienić jej domyślny poziom, a także, jakie pliki są automatycznie wyłączone z klasyfikacji i ochrony.

## <a name="file-types-supported-for-classification-only"></a>Typy plików, dla których jest obsługiwana tylko klasyfikacja

Sama klasyfikacja jest obsługiwana dla następujących typów plików. Dodatkowe typy plików obsługują klasyfikację, jeśli są również chronione (zobacz sekcję [Typy plików, dla których jest obsługiwana klasyfikacja i ochrona](#supported-file-types-for-classification-and-protection)).

- **Adobe Portable Document Format**: .pdf

- **Microsoft Visio**: .vsdx, .vsdm, .vssx, .vssm, .vsd, .vdw, .vst

- **Microsoft Project**: .mpp, .mpt

- **Microsoft Publisher**: .pub

- **Microsoft Office 97, Office 2010, Office 2003**: .xls, .xlt, .doc, .dot, .ppt, .pps, .pot
- **Microsoft XPS**: .xps .oxps

- **Obrazy**: .jpg, .jpe, .jpeg, .jif, .jfif, .jfi.png, .tif, .tiff

- **Autodesk Design Review 2013**: .dwfx

- **Adobe Photoshop**: .psd

- **Digital Negative**: .dng

## <a name="file-types-supported-for-protection"></a>Typy plików, dla których jest obsługiwana ochrona

Klient usługi Azure Information Protection obsługuje ochronę na dwóch różnych poziomach, jak opisano w poniższej tabeli.

|Typ ochrony|Natywna|Ogólne|
|----------------------|----------|-----------|
|Opis|W przypadku plików tekstowych, obrazów, plików pakietu Microsoft Office (Word, Excel, PowerPoint), plików pdf oraz innych typów plików aplikacji obsługujących usługę Rights Management ochrona natywna zapewnia silny poziom ochrony obejmujący szyfrowanie i wymuszanie praw (uprawnień).|W przypadku pozostałych aplikacji i typów plików ochrona ogólna zapewnia poziom ochrony obejmujący hermetyzację plików z wykorzystaniem typu pliku pfile oraz uwierzytelnianie umożliwiające weryfikację, czy użytkownik jest autoryzowany do otwierania pliku.|
|Protection|Ochrona plików jest wymuszana w następujący sposób:<br /><br />— Przed wyświetleniem chronionej zawartości musi nastąpić pomyślne uwierzytelnienie użytkowników odbierających plik pocztą e-mail lub mających dostęp do niego za pośrednictwem uprawnień do pliku lub uprawnień udziału.<br /><br />— Jeśli pliki są chronione, dodatkowo wymuszane są prawa użytkowania i zasady skonfigurowane przez właściciela zawartości, gdy zawartość jest wyświetlana w przeglądarce usługi Azure Information Protection (w przypadku chronionych plików tekstowych i obrazów) lub w skojarzonej aplikacji (w przypadku wszystkich pozostałych obsługiwanych typów plików).|Ochrona plików jest wymuszana w następujący sposób:<br /><br />— Przed wyświetleniem chronionej zawartości musi nastąpić pomyślne uwierzytelnienie użytkowników autoryzowanych do otwierania pliku i mających do niego dostęp. W przypadku niepowodzenia autoryzacji plik nie jest otwierany.<br /><br />— Prawa do użytkowania i zasady ustawiane przez właściciela zawartości są wyświetlane, aby informować autoryzowanych użytkowników o zamierzonych zasadach użytkowania.<br /><br />— Rejestrowana jest inspekcja autoryzowanych użytkowników otwierających pliki i uzyskujących do nich dostęp. Jednak prawa użytkowania nie są wymuszane.|
|Domyślny dla typów plików|Jest to domyślny poziom ochrony dla następujących typów plików:<br /><br />— Pliki tekstowe i pliki obrazów<br /><br />— Pliki pakietu Microsoft Office (programów Word, Excel i PowerPoint)<br /><br />— Pliki w formacie Portable Document Format (pdf)<br /><br />Więcej informacji znajduje się w sekcji [Typy plików, dla których jest obsługiwana klasyfikacja i ochrona](#supported-file-types-for-classification-and-protection).|Jest to domyślna ochrona dla wszystkich pozostałych typów plików (takich jak vsdx, rtf itd.), które nie są obsługiwane w ramach ochrony natywnej.|

Domyślny poziom ochrony stosowany przez klienta usługi Azure Information Protection można zmienić. Poziom domyślny można zmienić z natywnego na ogólny, z ogólnego na natywny, a nawet zupełnie uniemożliwić ochronę ze strony klienta usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz sekcję [Zmiana domyślnego poziomu ochrony plików](#changing-the-default-protection-level-of-files) w tym artykule.

Tę ochronę danych można zastosować automatycznie po wybraniu etykiety, która została skonfigurowana przez administratora, lub można określić własne ustawienia ochrony za pomocą [poziomów uprawnień](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels). 

### <a name="file-sizes-supported-for-protection"></a>Rozmiary plików, dla których jest obsługiwana ochrona

Istnieją określone maksymalne rozmiary plików, dla których klient usługi Azure Information Protection obsługuje funkcje ochrony.

- **Pliki pakietu Office:**
    
    |Aplikacje pakietu Office|Maksymalny rozmiar obsługiwanego pliku|
    |--------------------------------|-------------------------------------|
    |Word 2007 (obsługiwane tylko przez usługi AD RMS)<br /><br />Word 2010<br /><br />Word 2013<br /><br />Word 2016|32-bitowe: 512 MB<br /><br />64-bitowe: 512 MB
    |Excel 2007 (obsługiwane tylko przez usługi AD RMS)<br /><br />Excel 2010<br /><br />Excel 2013<br /><br />Excel 2016|32-bitowe: 2 GB<br /><br />64-bitowe: ograniczony tylko ilością dostępnego miejsca na dysku i pamięci|
    |PowerPoint 2007 (obsługiwane tylko przez usługi AD RMS)<br /><br />PowerPoint 2010<br /><br />PowerPoint 2013<br /><br />PowerPoint 2016|32-bitowe: ograniczony tylko ilością dostępnego miejsca na dysku i pamięci<br /><br />64-bitowe: ograniczony tylko ilością dostępnego miejsca na dysku i pamięci

- **Dla wszystkich innych plików**: ograniczony tylko ilością dostępnego miejsca na dysku i pamięci.

### <a name="supported-file-types-for-classification-and-protection"></a>Typy plików, dla których jest obsługiwana klasyfikacja i ochrona

W poniższej tabeli wymieniono podzbiór typów plików, które obsługują ochronę natywną przez klienta usługi Azure Information Protection oraz które także mogą być klasyfikowane. 

Te typy plików są identyfikowane oddzielnie, ponieważ jeśli są objęte ochroną natywną, oryginalne rozszerzenie nazwy pliku jest zmieniane, a pliki stają się plikami tylko do odczytu. W przypadku plików objętych ochroną ogólną oryginalne rozszerzenie nazwy pliku w każdej sytuacji zostaje zmienione na pfile.

> [!WARNING]
> Jeśli korzystasz z zapory, internetowego serwera proxy lub oprogramowania zabezpieczającego, które sprawdza pliki i podejmuje odpowiednie działania w zależności od rozszerzenia nazwy pliku, może zaistnieć konieczność zmiany konfiguracji tych zasobów w celu zapewnienia obsługi nowych rozszerzeń.

|Oryginalne rozszerzenie nazwy pliku|Chronione rozszerzenie nazwy pliku|
|--------------------------------|-------------------------------------|
|txt|ptxt|
|xml|pxml|
|jpg|pjpg|
|jpeg|pjpeg|
|pdf|ppdf|
|PNG|ppng|
|tif|ptif|
|tiff|ptiff|
|bmp|pbmp|
|gif|pgif|
|jpe|pjpe|
|jfif|pjfif|
|jt|pjt|

W poniższej tabeli wymieniono pozostałe typy plików, które obsługują ochronę natywną przez klienta usługi Azure Information Protection oraz które także mogą być klasyfikowane. Są to typy plików aplikacji pakietu Microsoft Office. 

Rozszerzenia nazw tych plików nie zmieniają się po objęciu plików ochroną przez usługę Rights Management.

|Typy plików obsługiwanych przez pakiet Office|Typy plików obsługiwanych przez pakiet Office|
|----------------------------------|----------------------------------|
|doc<br /><br />docm<br /><br />docx<br /><br />dot<br /><br />dotm<br /><br />dotx<br /><br />potm<br /><br />potx<br /><br />pps<br /><br />ppsm<br /><br />ppsx<br /><br />ppt<br /><br />pptm|pptx<br /><br />thmx<br /><br />xla<br /><br />xlam<br /><br />xls<br /><br />xlsb<br /><br />xlt<br /><br />xlsm<br /><br />xlsx<br /><br />xltm<br /><br />xltx<br /><br />xps|

### <a name="changing-the-default-protection-level-of-files"></a>Zmiana domyślnego poziomu ochrony plików
Edytując rejestr, możesz zmienić sposób ochrony plików przez klienta usługi Azure Information Protection. Możesz na przykład wymusić, aby pliki obsługujące ochronę natywną były objęte ochroną ogólną przez klienta usługi Azure Information Protection.

W jakich sytuacjach warto to zrobić:

- Jeśli chcesz mieć pewność, że każdy użytkownik będzie mógł otworzyć plik, nawet jeśli nie ma aplikacji obsługującej ochronę natywną.

- Jeśli chcesz rozwiązać problem dotyczący systemów zabezpieczeń, które podejmują działania względem plików na podstawie ich rozszerzeń nazw i które można tak skonfigurować, aby uwzględniały rozszerzenie nazwy pliku pfile, ale nie wiele rozszerzeń nazw plików w ramach ochrony natywnej.

Analogicznie można wymusić stosowanie przez klienta usługi Azure Information Protection do ochrony natywnej plików, które domyślnie byłyby chronione w sposób ogólny. Może się to przydać, jeśli masz aplikację obsługującą interfejsy API usług RMS, taką jak aplikacja branżowa utworzona przez deweloperów w Twojej firmie lub aplikacja kupiona od niezależnego dostawcy oprogramowania.

Możesz też wymusić blokowanie ochrony plików przez klienta usługi Azure Information Protection. Wówczas nie jest stosowana ani ochrona natywna, ani ogólna. Ta opcja może się przydać, jeśli na przykład masz działającą automatycznie aplikację lub usługę, która musi otworzyć określony plik, aby przetworzyć jego zawartość. Jeśli zablokujesz ochronę określonego typu plików, użytkownicy nie mogą ochronić plików tego typu za pomocą klienta usługi Azure Information Protection. Jeśli ktoś spróbuje to zrobić, zobaczy komunikat informujący o zablokowaniu przez administratora możliwości ochrony i będzie musiał zrezygnować z tego działania.

W celu skonfigurowania klienta usługi Azure Information Protection w taki sposób, aby była stosowana ogólna ochrona wszystkich plików, które domyślnie są chronione natywnie, wprowadź w rejestrze następujące zmiany. Jeśli klucz FileProtection nie istnieje, należy utworzyć go ręcznie.

1. Utwórz nowy klucz o nazwie * dla następującej ścieżki rejestru, który oznacza pliki z dowolnym rozszerzeniem nazwy:
    
    - Dla 32-bitowych wersji systemu Windows: **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection**
    
    - Dla 64-bitowych wersji systemu Windows: **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\FileProtection**

2. W nowo dodanym kluczu (np. HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\\\*) utwórz nową wartość ciągu (REG_SZ) o nazwie **Encryption** z wartością **Pfile**.

    To ustawienie powoduje stosowanie ochrony ogólnej przez klienta usługi Azure Information Protection.

Te dwa ustawienia powodują, że klient usługi Azure Information Protection stosuje ochronę ogólną do wszystkich plików mających rozszerzenie nazwy pliku. Jeśli taki był Twój cel, nie trzeba już nic konfigurować. Możesz jednak zdefiniować wyjątki dla określonych typów plików, aby nadal były objęte ochroną natywną. W tym celu dla każdego typu plików trzeba wprowadzić trzy dodatkowe zmiany do rejestru:

1. Dla ścieżki **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection** (32-bitowy system Windows) lub **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\FileProtection** (64-bitowy system Windows): dodaj nowy klucz z nazwą rozszerzenia nazwy pliku (bez kropki na początku).

    Na przykład w przypadku plików z rozszerzeniem nazwy pliku docx utwórz klucz o nazwie **DOCX**.

2. W nowo dodanym kluczu typu pliku (np. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) utwórz nową wartość DWORD o nazwie **AllowPFILEEncryption** z wartością **0**.

3. W nowo dodanym kluczu typu pliku (np. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) utwórz nową wartość ciągu o nazwie **Encryption** z wartością **Native**.

W wyniku skonfigurowania tych ustawień wszystkie pliki będą chronione ogólnie z wyjątkiem plików mających rozszerzenie nazwy pliku docx, które przez klienta usługi Azure Information Protection będą chronione natywnie.

Powtórz te trzy kroki dla innych typów plików, które chcesz zdefiniować jako wyjątki objęte ochronę natywną i nie chcesz, aby były objęte ochroną ogólną przez klienta usługi Azure Information Protection.

Podobne zmiany w rejestrze możesz wprowadzić w innych sytuacjach, zmieniając wartość ciągu **Encryption** obsługującego następujące wartości:

- **Pfile**: ogólna ochrona

- **Native**: ochrona natywna

- **Off**: blokowanie ochrony

Aby uzyskać dodatkowe informacje, zobacz artykuł [Konfiguracja interfejsu API plików](../develop/file-api-configuration.md) we wskazówkach dla deweloperów. W tej dokumentacji dla deweloperów ochrona ogólna jest określana jako „PFile”. 

## <a name="file-types-that-are-excluded-from-classification-and-protection-by-the-azure-information-protection-client"></a>Typy plików wykluczone z klasyfikacji i ochrony przez klienta usługi Azure Information Protection

Aby uniemożliwić użytkownikom zmianę plików, które są krytyczne dla działania komputera, niektóre typy plików i folderów są automatycznie wykluczone z ochrony i klasyfikacji. Jeśli użytkownicy spróbują sklasyfikować lub chronić te pliki, zobaczą komunikat informujący o tym, że pliki są wykluczone.

- **Wykluczone typy plików**: .lnk, .exe, .com, .cmd, .bat, .dll, .ini, .pst, .sca, .drm, .sys, .cpl, .inf, .drv, .dat, .tmp, .msp, .msi, .pdb, .jar

- **Wykluczone foldery** : 
    - Windows
    - Program Files (\Program Files i \Program Files (x86))
    - \ProgramData 
    - \AppData (dla wszystkich użytkowników)

### <a name="files-that-cannot-be-protected-by-default"></a>Pliki, które nie mogą być chronione przez domyślny

Każdego pliku, który jest chroniony hasłem nie mogą być chronione natywnie przez klienta usługi Azure Information Protection. W większości przypadków Zobacz pliki PDF, które są chronione hasłem, ale ta funkcja oferuje także inne aplikacje, takie jak aplikacje pakietu Office.

Ponadto klienta usługi Azure Information Protection dla systemu Windows nie można natywnie chronić (lub wyłączyć ochronę) plików PDF w jednym z następujących sytuacji:

- Plik PDF jest oparta na formularzu.

- Chroniony plik PDF, który ma rozszerzenie nazwy pliku PDF. 
    
    Klienta usługi Azure Information Protection można chronić niechronionych plików PDF i włącz ponownie ochronę chroniony plik PDF, który ma rozszerzenie nazwy pliku ppdf.

Jako obejście dla tych plików, można objęty ochroną ogólną je zgodnie z instrukcjami w [zmiana domyślnego poziomu ochrony plików](#changing-the-default-protection-level-of-files) sekcji. Jednak ta metoda zmienia poziom ochrony dla wszystkich plików mających rozszerzenie nazwy pliku PDF na poziomie komputera. Nie można zdefiniować ogólna ochrona tylko pliki, które spełnia podanych kryteriów.

Chroni pliki te są ważne, można tymczasowo skopiuj je do innego komputera w celu ich objęty ochroną, a następnie skopiuj je ponownie ponownie.


## <a name="next-steps"></a>Następne kroki
Po zidentyfikowaniu typów plików obsługiwanych przez klienta usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:

- [Dostosowania](client-admin-guide-customizations.md)

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
