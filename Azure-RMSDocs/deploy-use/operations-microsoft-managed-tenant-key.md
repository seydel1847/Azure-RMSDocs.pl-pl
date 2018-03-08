---
title: "Zarządzane przez firmę Microsoft w Efektywnych operacje cyklu życia klucza dzierżawy"
description: "Informacji na temat operacji cyklu życia, które są istotne, jeśli firma Microsoft zarządza kluczem dzierżawy usługi Azure Information Protection (ustawienie domyślne)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3c48cda6-e004-4bbd-adcf-589815c56c55
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: dea6fffc32876b548e5daa33a76e7891088f1e9b
ms.sourcegitcommit: dd53f3dc2ea2456ab512e3a541d251924018444e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-managed-tenant-key-life-cycle-operations"></a>Zarządzany przez firmę Microsoft: Operacje cyklu życia klucza dzierżawy

>*Dotyczy: Azure Information Protection, Office 365*

Jeśli firma Microsoft zarządza kluczem dzierżawy usługi Azure Information Protection (ustawienie domyślne), użyj poniższych sekcji, aby uzyskać więcej informacji na temat operacji cyklu życia związanych z tą topologią.

## <a name="revoke-your-tenant-key"></a>Odwołanie klucza dzierżawy
Po anulowaniu subskrypcji usługi Azure Information Protection usługa ta wstrzymuje korzystanie z klucza dzierżawy, co nie wymaga żadnej akcji ze strony użytkownika.

## <a name="rekey-your-tenant-key"></a>Wymiana klucza dzierżawy
Wymiana klucza jest także określana jako uaktualnianie klucza. Po wykonaniu tej operacji usługi Azure Information Protection przestanie używać istniejącego klucza dzierżawy do ochrony dokumentów i wiadomości e-mail i rozpoczyna się użyć innego klucza. Zasady i szablony są natychmiast ponownie podpisane, ale tego przejścia jest stopniowego dla istniejących klientów i usług przy użyciu usługi Azure Information Protection. Dlatego przez pewien czas część nowej zawartości nadal ma być chroniona przez stary klucz dzierżawy.

Do ponownego generowania kluczy należy skonfigurować obiekt klucza dzierżawy i określ alternatywny klucz do użycia. Następnie, wcześniej używany klucz automatycznie jest oznaczony jako zarchiwizowane usługi Azure Information Protection. Ta konfiguracja zapewnia tej zawartości, która była chroniona za pomocą tego klucza pozostaną dostępne.

Przykłady gdy może być konieczne ponowne generowanie kluczy dla usługi Azure Information Protection:

- W przypadku migracji z Active Directory Rights Management Services (AD RMS) z kluczem trybu kryptograficznego 1. Po zakończeniu migracji chcesz zmienić przy użyciu klucza, który korzysta z trybu kryptograficznego 2.

- Firma została podzielona na dwie lub więcej firm. Po wymianie klucza dzierżawy nowa firma nie będzie miała dostępu do nowej zawartości publikowanej przez pracowników. Mogą oni uzyskać dostęp do starej zawartości, jeśli dysponują kopią starego klucza dzierżawy.

- Chcesz przenieść od jednego topologii zarządzania kluczami do innego.

- Uważasz, że zostanie naruszone bezpieczeństwo kopii głównej klucza dzierżawy.

Do ponownego generowania kluczy można wybrać inny klucz zarządzany przez firmę Microsoft jako klucz dzierżawy, ale nie można utworzyć nowy klucz zarządzany przez firmę Microsoft. Aby utworzyć nowy klucz, należy zmienić topologii klucza być zarządzany przez klienta (BYOK).

Masz więcej niż jeden klucz zarządzany przez firmę Microsoft, jeśli migrowane z Active Directory Rights Management Services (AD RMS) i wybierz zarządzany przez firmę Microsoft topologii klucza usługi Azure Information Protection. W tym scenariuszu istnieją co najmniej dwa klucze zarządzany przez firmę Microsoft dla dzierżawy. Klucz jeden lub więcej, jest klucza lub kluczy, które są importowane z usług AD RMS. Konieczne będzie również domyślny klucz, który został utworzony automatycznie dla dzierżawy usługi Azure Information Protection.

Aby wybrać inny klucz, aby pełnił rolę klucza aktywne dzierżawy usługi Azure Information Protection, użyj [AadrmKeyProperties zestaw](/powershell/module/aadrm/set-aadrmkeyproperties) polecenia cmdlet w AADRM module. Aby ułatwić identyfikację klucz, który ma być używany, należy użyć [Get-AadrmKeys](/powershell/module/aadrm/get-aadrmkeys) polecenia cmdlet. Można określić domyślny klucz, który został utworzony automatycznie dla dzierżawy usługi Azure Information Protection, uruchamiając następujące polecenie:

    (Get-AadrmKeys) | Sort-Object CreationTime | Select-Object -First 1

Aby zmienić topologii klucza być zarządzany przez klienta (BYOK), zobacz [BYOK wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key).

## <a name="backup-and-recover-your-tenant-key"></a>Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy
Za tworzenie kopii zapasowych klucza dzierżawy odpowiada firma Microsoft. Nie wymaga to żadnej akcji z Twojej strony.

## <a name="export-your-tenant-key"></a>Eksport klucza dzierżawy
Możesz wyeksportować konfigurację usługi Azure Information Protection i klucz dzierżawy zgodnie z instrukcjami w następujące trzy kroki:

### <a name="step-1-initiate-export"></a>Krok 1. Zainicjowanie eksportu

- [Skontaktuj się z Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support) otworzyć **sprawy pomocy technicznej usługi Azure Information Protection z żądaniem eksportu klucza usługi Azure Information Protection**. Musisz udowodnić, że jesteś administratorem dzierżawy usługi Azure Information Protection oraz wiedzieć, że potwierdzenie tego procesu trwa kilka dni. Naliczane są standardowe opłaty za pomoc techniczną. Eksportowanie klucza dzierżawy nie jest bezpłatną usługą pomocy technicznej.

### <a name="step-2-wait-for-verification"></a>Krok 2. Oczekiwanie na weryfikację

- Firma Microsoft sprawdza, czy żądanie wydania klucza dzierżawy usługi Azure Information Protection jest uzasadnione. Proces ten może potrwać do trzech tygodni.

### <a name="step-3-receive-key-instructions-from-css"></a>Krok 3. Otrzymanie instrukcji dotyczących klucza od CSS

- Pomoc techniczna firmy Microsoft (CSS, Customer Support Services) przesyła konfigurację i klucz dzierżawy usługi Azure Information Protection w formie zaszyfrowanej w pliku chronionym hasłem. Ten plik ma rozszerzenie **tpd**. W tym celu CSS przesyła najpierw Tobie (osobie, która zainicjowała eksport) narzędzie pocztą e-mail. Narzędzie należy uruchomić z wiersza polecenia w następujący sposób:

    ```
    AadrmTpd.exe -createkey
    ```
    Powoduje to wygenerowanie pary kluczy RSA oraz zapisanie części publicznej i prywatnej w formie plików w bieżącym folderze. Przykład: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** i **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Odpowiedz na wiadomość e-mail od CSS, dołączając plik o nazwie rozpoczynającej się od **PublicKey**. CSS wysyła następnie możesz plik zaufanej domeny publikacji jako pliku XML zaszyfrowanego przy użyciu Twojego klucza RSA. Skopiuj ten plik do folderu, w którym pierwotnie zostało uruchomione narzędzie AadrmTpd i uruchom narzędzie ponownie przy użyciu pliku o nazwie rozpoczynającej się od **PrivateKey** oraz pliku otrzymanego od CSS. Przykład:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    Polecenie to powinno zwracać dwa pliki: jeden z nich zawiera hasło do chronionego hasłem pliku TPD w formie zwykłego tekstu, a drugi to sam chroniony hasłem plik TPD. Pliki mają nowy identyfikator GUID, na przykład:
     
    - Password-5E4C2018-8C8C-4548-8705-E3218AA1544E.txt

    - ExportedTPD-5E4C2018-8C8C-4548-8705-E3218AA1544E.xml

    Należy wykonać kopię zapasową tych plików i zapisać je w bezpiecznym miejscu, co pozwoli na kontynuowanie odszyfrowywania zawartości chronionej przy użyciu tego klucza dzierżawy. Dodatkowo w przypadku migracji do usługi AD RMS można zaimportować ten plik TPD (plik o nazwie rozpoczynającej się od **ExportedTDP**) do serwera usługi AD RMS.

### <a name="step-4-ongoing-protect-your-tenant-key"></a>Krok 4. Ciągły: ochrona klucza dzierżawy

Po otrzymaniu klucza dzierżawy należy przechowywać go w bezpiecznym miejscu, ponieważ uzyskanie dostępu do niego umożliwia odszyfrowanie wszystkich dokumentów chronionych przy użyciu tego klucza.

Jeśli przyczyną eksportu klucza dzierżawy jest chęć zaprzestania korzystania z usługi Azure Information Protection, najlepszym rozwiązaniem jest dezaktywacja usługi Azure Rights Management w dzierżawie usługi Azure Information Protection. Nie należy opóźniać tego działania po otrzymaniu klucza dzierżawy. Ten środek ostrożności pozwala zminimalizować konsekwencje w przypadku uzyskania dostępu do klucza dzierżawy przez osobę nieupoważnioną. Aby uzyskać instrukcje, zobacz [Likwidowanie i dezaktywowanie usługi Azure Rights Management](decommission-deactivate.md).

## <a name="respond-to-a-breach"></a>Reakcja na naruszenie zabezpieczeń
Żaden system zabezpieczeń, niezależnie od jego siły, nie jest kompletny bez procedur reakcji na naruszenie zabezpieczeń. Klucz dzierżawy może zostać naruszony lub skradziony. Nawet wtedy, gdy jest on chroniony dobrze, mogą występować luki w obecnej generacji technologii klucza i algorytmy i długości kluczy.

Firma Microsoft ma dedykowany zespół, który reaguje na przypadki naruszenia zabezpieczeń produktów i usług. Bezpośrednio po uzyskaniu wiarygodnego raportu o incydencie zespół ten bada jego zakres, przyczynę i środki naprawcze. Jeśli to zdarzenie dotyczy Twoich zasobów, firma Microsoft będzie wysyłać administratorami dzierżawy usługi Azure Information Protection za pośrednictwem poczty e-mail, za pomocą adresu e-mail podanego podczas subskrybowania.

W przypadku naruszenia zabezpieczeń najlepsze działanie, które może podjąć użytkownik lub firma Microsoft, jest zależne od zakresu naruszenia. Firma Microsoft zapewnia wsparcie w tym procesie. Poniższa tabela przedstawia typowe sytuacje i prawdopodobne reakcje, choć dokładna reakcja jest zależna od informacji uzyskanych w trakcie badania.

|Opis zdarzenia|Prawdopodobna reakcja|
|------------------------|-------------------|
|Przeciek klucza dzierżawy.|Wymień klucz dzierżawy. Zobacz sekcję [Wymiana klucza dzierżawy](#rekey-your-tenant-key) w tym artykule.|
|Nieautoryzowana osoba lub złośliwe oprogramowanie uzyskało prawa do korzystania z klucza dzierżawy, ale nie nastąpił przeciek samego klucza.|Wymiana klucza dzierżawy nie jest w tym przypadku pomocna, a problem wymaga analizy przyczyny. Jeśli za uzyskanie dostępu przez nieautoryzowaną osobę odpowiada proces lub błąd oprogramowania, sytuację należy rozwiązać.|
|Odkryto lukę w zabezpieczeniach algorytmu RSA lub długości klucza albo ataki siłowe stały się wykonalne.|Firma Microsoft musi zaktualizować usługę Azure Information Protection do obsługi nowych algorytmów i długości kluczy dłużej, które są odporne i poinstruować wszystkich klientów do ponowne tworzenie klucza swój klucz dzierżawy.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

