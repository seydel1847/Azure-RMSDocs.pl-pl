---
# required metadata

title: Konfiguracja interfejsu API plików | Azure RMS
description: Działanie interfejsu API plików można skonfigurować za pomocą ustawień rejestru.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 930878C2-D2B4-45F1-885F-64927CEBAC1D
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfiguracja interfejsu API plików


Działanie interfejsu API plików można skonfigurować za pomocą ustawień rejestru.

Interfejs API plików zawiera dwa rodzaje ochrony; ochronę natywną i ochronę pliku PFile.

-   **Ochrona natywna** — plik jest chroniony do formatu usługi AD RMS na podstawie jego typu MIME (rozszerzenie pliku).
-   **Ochrona pliku PFile** — plik jest chroniony do formatu pliku chronionego przez usługę AD RMS (PFile).

Aby uzyskać więcej informacji o obsługiwanych formatach plików, zobacz sekcję **Interfejs API plików — szczegóły dotyczące obsługi plików** w tym temacie.

## Nazwy i opisy typów kluczy i ich wartości

W poniższych sekcjach opisano klucze i wartości kluczy, które sterują szyfrowaniem.


### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection

*Typ*: Klucz

*Opis*: Zawiera ogólną konfigurację interfejsu API plików.

### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\&lt;EXT&gt;

*Typ: Klucz

*Opis: Zawiera informacje o konfiguracji dla określonych rozszerzeń plików, na przykład TXT, JPG i tak dalej.

- Znak symbolu wieloznacznego „*”, jest dozwolony; jednak ustawienie dla określonego rozszerzenia ma pierwszeństwo przed ustawieniem zdefiniowanym przy użyciu symboli wieloznacznych. Symbol wieloznaczny nie ma wpływu na ustawienia dla plików programu Microsoft Office — muszą być one jawnie wyłączone według typu pliku.
- Aby określić pliki, które nie mają rozszerzenia, użyj znaku „.”
- Nie podawaj znaku „.” podczas określania klucza dla konkretnego rozszerzenia pliku Na przykład użyj `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\TXT` w celu określenia ustawień dla plików txt. (Nie używaj zapisu `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\.TXT`).

Ustaw wartość *Encryption* w kluczu w celu określenia zachowania ochrony. Jeśli wartość *Encryption* nie jest ustawiona, dla danego typu pliku realizowane jest zachowanie domyślne.


### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\&lt;EXT&gt;\Encryption*

*Typ: REG_SZ*

*Opis: Zawiera jedną z trzech wartości:

- *Off*: Szyfrowanie jest wyłączone.

> [AZURE.NOTE] To ustawienie nie ma żadnego wpływu na odszyfrowywanie. Dowolny zaszyfrowany plik, niezależnie od tego, czy został zaszyfrowany za pomocą ochrony natywnej, czy też pliku Pfile, można odszyfrować, jeśli tylko użytkownik ma prawo WYODRĘBNIANIA.

- *Native*: Używane jest szyfrowanie natywne. W przypadku plików pakietu Office zaszyfrowany plik ma takie samo rozszerzenie jak plik oryginalny. Na przykład plik z rozszerzeniem docx zostanie zaszyfrowany do pliku z rozszerzeniem docx. W przypadku innych plików, które mogą zostać objęte ochroną natywną, dany plik zostanie zaszyfrowany w pliku z rozszerzeniem w formacie p**zzz**, gdzie **zzz** oznacza pierwotne rozszerzenie pliku. Na przykład pliki txt będą szyfrowane do plików z rozszerzeniem ptxt. Poniżej znajduje się lista rozszerzeń nazw plików, które mogą zostać objęte ochroną natywną.

- *Pfile*: Używane jest szyfrowanie pliku PFile. Zaszyfrowany plik będzie miał rozszerzenie pfile dołączone do pierwotnego rozszerzenia. Na przykład po zaszyfrowaniu plik txt będzie mieć rozszerzenie txt.pfile.


> [AZURE.NOTE] To ustawienie nie ma żadnego wpływu na formaty plików pakietu Office. Na przykład jeśli wartość `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX\Encryption` jest ustawiona na „Pfile”, pliki docx nadal będą szyfrowane przy użyciu ochrony natywnej, a zaszyfrowany plik nadal będzie miał rozszerzenie docx.

Ustawienie dowolnej innej wartości lub brak wartości powoduje zachowanie domyślne.

## Domyślne zachowanie dla różnych formatów pliku**

-   **Pliki pakietu Office** Włączone jest szyfrowanie natywne.
-   **Pliki txt, xml, jpg, jpeg, pdf, png, tiff, bmp, gif, giff, jpe, jfif, jif** Włączone jest szyfrowanie natywne (xxx staje się pxxx)
-   **Wszystkie inne pliki** Włączone jest szyfrowanie chronionego pliku (pfile) (xxx staje się xxx.pfile)

Jeśli próba szyfrowania zostanie podjęta na typie pliku, który jest zablokowany, wystąpi błąd [**IPCERROR\_FILE\_ENCRYPT\_BLOCKED**](/rights-management/sdk/2.1/api/win/error%20codes).

### Interfejs API plików — szczegóły dotyczące obsługi plików

Natywny mechanizm obsługi można dodać dla dowolnego typu pliku (rozszerzenia). Na przykład w przypadku dowolnego rozszerzenia &lt;ext&gt; (nienależącego do pakietu office) zostanie użyte rozszerzenie \*.p&lt;ext&gt;, jeśli konfiguracja administratora dla tego rozszerzenia jest natywna („NATIVE”).

**Pliki pakietu Office**

-   Rozszerzenia plików: doc, dot, xla, xls, xlt, pps, ppt, docm, docx, dotm, dotx, xlam, xlsb, xlsm, xlsx, xltm, xltx, xps, potm, potx, ppsx, ppsm, pptm, pptx, thmx.
-   Typ ochrony = Native (domyślnie): plik sample.docx jest szyfrowany do sample.docx
-   Typ ochrony = Pfile: Dla plików pakietu Office działa tak samo jak w trybie natywnym.
-   Off: Wyłącza funkcję szyfrowania.

**Pliki PDF**

-   Typ ochrony = Native: plik sample.pdf zostaje zaszyfrowany i nosi nazwę sample.ppdf
-   Typ ochrony = Pfile: plik sample.pdf zostaje zaszyfrowany i nosi nazwę sample.pdf.pfile.
-   Off: Wyłącza funkcję szyfrowania.

**Wszystkie inne formaty plików**

-   Typ ochrony = Pfile: plik sample.*zzz* zostaje zaszyfrowany i nosi nazwę sample.*zzz*pfile; gdzie zzz jest pierwotnym rozszerzeniem pliku.
-   Off: Wyłącza funkcję szyfrowania.

### Przykłady

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

## Tematy pokrewne

* [Uwagi dla deweloperów](developer-notes.md)
* [**IPCERROR\_FILE\_ENCRYPT\_BLOCKED**](/rights-management/sdk/2.1/api/win/error%20codes)
 

 





<!--HONumber=Apr16_HO4-->


