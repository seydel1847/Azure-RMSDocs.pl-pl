---
title: "Konfiguracja interfejsu API plików | Azure RMS"
description: "Działanie interfejsu API plików można skonfigurować za pomocą ustawień rejestru."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 10/11/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 930878C2-D2B4-45F1-885F-64927CEBAC1D
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 252300e1d370a0c9b8260fb93315782dd01787c7
ms.sourcegitcommit: 965108d50739148864b2ae7dcc661ae65f1b154c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2017
---
# <a name="file-api-configuration"></a>Konfiguracja interfejsu API plików


Działanie interfejsu API plików można skonfigurować za pomocą ustawień rejestru.

Interfejs API plików zawiera dwa rodzaje ochrony; ochronę natywną i ochronę pliku PFile.

-   **Ochrona natywna** — plik jest chroniony do formatu usługi AD RMS na podstawie jego typu MIME (rozszerzenie pliku).
-   **Ochrona pliku PFile** — plik jest chroniony do formatu pliku chronionego przez usługę AD RMS (PFile).

Aby uzyskać więcej informacji na temat obsługiwanych formatów plików, zobacz **szczegóły dotyczące obsługi plików interfejsu API plików** w tym artykule.

## <a name="keykey-value-types-and-descriptions"></a>Nazwy i opisy typów kluczy i ich wartości

W poniższych sekcjach opisano klucze i wartości kluczy, które sterują szyfrowaniem.

### `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection`

**Typ**: klucz

**Opis**: zawiera ogólną konfigurację interfejsu API plików.

### `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\<EXT>`

**Typ**: klucz

**Opis**: zawiera informacje o konfiguracji dla określonych rozszerzeń plików, na przykład TXT, JPG itp.

- Znak symbolu wieloznacznego "*", jest dozwolony; Jednak ustawienie dla określonego rozszerzenia ma pierwszeństwo przed ustawieniem symboli wieloznacznych. Symbol wieloznaczny nie ma wpływu na ustawienia dla plików programu Microsoft Office — muszą być one jawnie wyłączone według typu pliku.
- Aby określić pliki, które nie mają rozszerzenia, użyj znaku „.”
- Nie określaj "." podczas określania klucza dla konkretnego rozszerzenia pliku; na przykład użyć `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\TXT` do określenia ustawień dla plików txt. (Nie używaj zapisu `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\.TXT`).

W celu określenia zachowania ochrony, należy ustawić **szyfrowania** wartość klucza. Jeśli wartość **Encryption** nie zostanie ustawiona, dla danego typu pliku zostanie zastosowane zachowanie domyślne.


### `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\<EXT>\Encryption*`

**Typ**: REG_SZ

**Opis**: zawiera jedną z trzech wartości:

- **Off**: szyfrowanie jest wyłączone.

> [!Note]
> To ustawienie nie ma żadnego wpływu na odszyfrowywanie. Każdy zaszyfrowany plik (niezależnie od tego, czy został zaszyfrowany za pomocą ochrony natywnej czy pliku Pfile) można odszyfrować, jeśli użytkownik ma prawo **WYODRĘBNIANIA**.

- **Native**: jest używane szyfrowanie natywne. W przypadku plików pakietu Office zaszyfrowany plik ma takie samo rozszerzenie jak plik oryginalny. Na przykład plik z rozszerzeniem docx zostanie zaszyfrowany do pliku z rozszerzeniem docx. W przypadku innych plików, które mogą zostać objęte ochroną natywną, dany plik zostanie zaszyfrowany w pliku z rozszerzeniem w formacie p*zzz*, gdzie *zzz* oznacza pierwotne rozszerzenie pliku. Na przykład pliki txt będą szyfrowane do pliku z rozszerzeniem ptxt. Lista rozszerzeń plików, które mogą zostać objęte ochroną natywną jest zgodna.

- **Pfile**: jest używane szyfrowanie pliku PFile. Zaszyfrowany plik będzie miał rozszerzenie pfile dołączone do pierwotnego rozszerzenia. Na przykład po zaszyfrowaniu plik txt będzie mieć rozszerzenie txt.pfile.


> [!Note]
> To ustawienie nie ma żadnego wpływu na formaty plików pakietu Office. Na przykład jeśli wartość `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX\Encryption` jest ustawiona na &quot;Pfile”, pliki docx nadal będą szyfrowane przy użyciu ochrony natywnej, a zaszyfrowany plik nadal będzie miał rozszerzenie docx.

Ustawienie dowolnej innej wartości lub brak wartości powoduje zachowanie domyślne.

## <a name="default-behavior-for-different-file-formats"></a>Domyślne zachowanie dla różnych formatów plików

-   **Pliki pakietu Office** Włączone jest szyfrowanie natywne.
-   **Pliki txt, xml, jpg, jpeg, pdf, png, tiff, bmp, gif, giff, jpe, jfif, jif** Włączone jest szyfrowanie natywne (xxx staje się pxxx)
-   **Wszystkie inne pliki** Włączone jest szyfrowanie chronionego pliku (pfile) (xxx staje się xxx.pfile)

Jeśli próba szyfrowania zostanie podjęta na typie pliku, który jest zablokowany, wystąpi błąd [IPCERROR\_FILE\_ENCRYPT\_BLOCKED](https://msdn.microsoft.com/library/hh535248.aspx).

### <a name="file-api---file-support-details"></a>Interfejs API plików — szczegóły dotyczące obsługi plików

Można dodać natywną obsługę dowolnego typu pliku (rozszerzenie). Na przykład dla dowolnego rozszerzenia &lt;roz&gt; (innego niż rozszerzenia pakietu Office) będzie używany ciąg \*.p&lt;roz&gt;, jeśli konfiguracja administratora dla tego rozszerzenia ma wartość „NATIVE”.

**Pliki pakietu Office**

-   Rozszerzenia plików: doc, dot, xla, xls, xlt, pps, ppt, docm, docx, dotm, dotx, xlam, xlsb, xlsm, xlsx, xltm, xltx, xps, potm, potx, ppsx, ppsm, pptm, pptx, thmx, vsdx, vsdm, vssx, vssm, vstx i vstm. 
-   Typ ochrony = Native (domyślnie): plik sample.docx jest szyfrowany do sample.docx
-   Typ ochrony = Pfile: dla plików pakietu Office działa tak samo jak w trybie natywnym.
-   Off: Wyłącza funkcję szyfrowania.

**Pliki PDF**

-   Typ ochrony = Native: plik sample.pdf zostaje zaszyfrowany i nosi nazwę sample.ppdf
-   Typ ochrony = Pfile: plik sample.pdf zostaje zaszyfrowany i nosi nazwę sample.pdf.pfile.
-   Off: Wyłącza funkcję szyfrowania.

**Wszystkie inne formaty plików**

-   Typ ochrony = Pfile: plik sample.*zzz* jest szyfrowany i nosi nazwę sample.*zzz*.pfile, gdzie *zzz* to pierwotne rozszerzenie pliku.
-   Off: Wyłącza funkcję szyfrowania.

### <a name="examples"></a>Przykłady

Następujące ustawienia pozwalają włączyć szyfrowanie pliku PFile dla plików txt. Pliki pakietu Office będą chronione natywnie (domyślnie), pliki txt będą miały ochronę pliku PFile, a ochrona wszystkich innych plików będzie zablokowana (domyślnie).

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               txt
                  Encryption = Pfile
```

Następujące ustawienia pozwalają włączyć szyfrowanie pliku PFile dla wszystkich plików nienależących do pakietu Office, z wyjątkiem plików txt. Pliki pakietu Office będą chronione natywnie (domyślnie), ochrona plików txt będzie zablokowana, a wszystkie inne pliki będą miały włączoną ochronę pliku PFile.

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               *
                  Encryption = Pfile
               txt
                  Encryption = Off
```

Następujące ustawienia pozwalają wyłączyć szyfrowanie natywne plików docx. Pliki pakietu Office, z wyjątkiem plików docx, będą chronione natywnie (domyślnie), a ochrona wszystkich innych plików będzie zablokowana (domyślnie).

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               docx
                  Encryption = Off
```

## <a name="related-articles"></a>Pokrewne artykuły

- [Uwagi dla deweloperów](developer-notes.md)
- [IPCERROR\_FILE\_ENCRYPT\_BLOCKED](https://msdn.microsoft.com/library/hh535248.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]