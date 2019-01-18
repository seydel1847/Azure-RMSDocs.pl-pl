---
title: Rejestrowanie i analizowanie użycia usługi Azure RMS — AIP
description: Informacje i instrukcje dotyczące sposobu korzystania z rejestrowania użycia za pomocą usługi Azure Rights Management (Azure RMS).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/15/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: bf42c0309af481847e80b12cb161422b7cd18378
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54394334"
---
# <a name="logging-and-analyzing-usage-of-the-azure-rights-management-service"></a>Rejestrowanie i analizowanie użycia usługi Azure Rights Management

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Dzięki tym informacjom, które pomagają zrozumieć, jak można użyć dzienniki użycia dla usługi Azure Rights Management z usługi Azure Information Protection. Ta usługa zapewnia ochronę danych dla Twojej organizacji, dokumentów i wiadomości e-mail, może rejestrować wszystkie żądania do niego. Te żądania obejmują, gdy użytkownicy chronić dokumenty i wiadomości e-mail i również używanie tej zawartości, akcje wykonywane przez administratorów dla tej usługi i akcje wykonywane przez operatorów firmy Microsoft w celu obsługi wdrożenia usługi Azure Information Protection. 

Te dzienniki usługi Azure Rights Management można następnie użyć na potrzeby następujących scenariuszy biznesowych:

-   **Analiza danych biznesowych**

    Dzienniki generowane przez usługę Azure Rights Management można zaimportować do wybranego przez użytkownika repozytorium (na przykład bazy danych, systemu przetwarzania analitycznego online (OLAP) lub systemu MapReduce) w celu analizowania danych i tworzenia raportów. Na przykład można zidentyfikować osoby, które uzyskują dostęp do chronionych danych. Można określić, do jakich chronionych danych, z jakich urządzeń i z jakich lokalizacji użytkownicy uzyskują dostęp. Można ustalić, czy użytkownicy są w stanie pomyślnie odczytywać zawartość chronioną. Można również zidentyfikować osoby, które odczytały ważny dokument objęty ochroną.

-   **Monitorowanie nadużyć**

    Dane rejestrowania usługi Rights Management usługi Azure jest dostępne w niemal w czasie rzeczywistym, tak aby pozwala na stałe monitorowanie użycia firmie usługi Rights Management. 99,9% dzienników jest dostępnych w ciągu 15 minut od akcji zainicjowanej przy użyciu usługi.

    Na przykład można otrzymywać alerty w przypadku nagłego wzrostu liczby osób odczytujących chronione dane poza standardowymi godzinami pracy, co mogłoby wskazywać, że złośliwy użytkownik gromadzi informacje, aby je sprzedać konkurencji. Można też wykryć sytuację, w której ten sam użytkownik w krótkim czasie uzyskuje dostęp do danych z dwóch różnych adresów IP, co mogłoby oznaczać naruszenie zabezpieczeń konta użytkownika.

-   **Wykonywanie analizy śledczej**

    W przypadku wycieku informacji prawdopodobnie pojawi się pytanie, kto ostatnio uzyskiwał dostęp do określonych dokumentów i z jakich informacji korzystała ostatnio podejrzana osoba. Tego rodzaju pytania pozwala odpowiedzieć na korzystanie z funkcji rejestrowania, ponieważ osoby korzystające z zawartości chronionej muszą zawsze uzyskać licencję usługi Rights Management, aby otworzyć dokumenty i obrazy, które są chronione przez usługę Azure Rights Management, nawet jeśli te pliki są przesyłane za pośrednictwem poczty e-mail lub kopiowane na dyski USB lub inne urządzenia pamięci masowej. Oznacza to, że służy te dzienniki jako ostateczne źródło informacji dla analizy śledczej w przypadku, gdy dane są chronione przy użyciu usługi Azure Rights Management.

Oprócz tego rejestrowania użycia, także mają następujące opcje rejestracji:

|Opcja rejestrowania|Opis|
|----------------|---------------|
|Dziennik administratora|Rejestruje zadania administracyjne dla usługi Azure Rights Management. Na przykład, jeśli usługa jest dezaktywowany, gdy jest włączona funkcja administratora i, gdy użytkownicy są uprawnienia administratora delegowanego do usługi. <br /><br />Aby uzyskać więcej informacji, zobacz polecenia cmdlet programu PowerShell [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog).|
|Śledzenie dokumentów|Umożliwia użytkownikom śledzenie i odwoływanie dokumentów, które mają one śledzone za pomocą klienta usługi Azure Information Protection lub aplikację RMS sharing. Administratorzy globalni mogą również śledzić te dokumenty w imieniu użytkowników. <br /><br />Aby uzyskać więcej informacji, zobacz [Konfigurowanie i używanie śledzenia dokumentów usługi Azure Information Protection](./rms-client/client-admin-guide-document-tracking.md).|
|Dzienniki zdarzeń klienta|Działania dla klienta usługi Azure Information Protection, rejestrowane w lokalnym Windows **aplikacji i usług** dziennika zdarzeń **usługi Azure Information Protection**. <br /><br />Aby uzyskać więcej informacji, zobacz [rejestrowanie użycia klienta usługi Azure Information Protection](./rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client).|
|Pliki dziennika klienta|Rozwiązywanie problemów z dzienników dla klienta usługi Azure Information Protection znajduje się w **%localappdata%\Microsoft\MSIP**. <br /><br />Pliki te zostały zaprojektowane dla programu Microsoft Support.|

Ponadto informacje z dzienników użycia klienta usługi Azure Information Protection i skanera usługi Azure Information Protection jest zbierane i zagregowane, aby tworzyć raporty w witrynie Azure portal. Aby uzyskać więcej informacji, zobacz [raportowania usługi Azure Information Protection](reports-aip.md).

Aby uzyskać więcej informacji na temat rejestrowania użycia usługi Azure Rights Management, należy użyć poniższych sekcjach. 

## <a name="how-to-enable-azure-rightsmanagement-usage-logging"></a>Jak włączyć rejestrowanie użycia usługi Azure Rights Management
Od lutego 2016 r. rejestrowanie użycia usługi Azure Rights Management jest domyślnie włączona, dla wszystkich klientów. Dotyczy to klientów, którzy aktywowali usługę Azure Rights Management przed lutym 2016 r., oraz klientów, którzy aktywowali usługę po lutym 2016 r. 

> [!NOTE]
> Przechowywanie dziennika lub korzystanie z funkcji rejestrowania nie wiąże się z żadnymi dodatkowymi kosztami.
> 
> Do korzystania z funkcji rejestrowania użycia usługi Azure Rights Management przed lutym 2016 r. potrzebna była subskrypcja platformy Azure oraz wystarczająca ilość miejsca w magazynie Azure, co nie jest już wymagane.

## <a name="how-to-access-and-use-your-azure-rights-management-usage-logs"></a>Uzyskiwanie dostępu i korzystanie z dzienników użycia usługi Azure Rights Management
Usługa Azure Rights Management zapisuje dzienniki na koncie magazynu Azure w postaci serii obiektów blob. Każdy obiekt blob zawiera jeden lub większą liczbę rekordów w rozszerzonym formacie W3C dziennika. Nazwy obiektów blob są liczbami odpowiadającymi kolejności ich utworzenia. Sekcja [Interpretowanie dzienników użycia usługi Azure Rights Management](#how-to-interpret-your-azure-rights-management-usage-logs) w dalszej części tego dokumentu zawiera więcej informacji na temat zawartości dzienników i ich tworzenia.

Może upłynąć trochę czasu zanim dzienniki będą widoczne na koncie magazynu po akcji usługi Azure Rights Management. Większość dzienników pojawia się w ciągu 15 minut. Zalecamy pobranie dzienników do lokalnego magazynu, na przykład folderu lokalnego, bazy danych lub repozytorium MapReduce.

Aby pobrać dzienniki użycia, należy skorzystać z modułu administracyjnego usługi Azure Rights Management dla programu Windows PowerShell. Aby uzyskać instrukcje dotyczące instalacji, zobacz [Instalowanie modułu AADRM programu PowerShell](install-powershell.md). Jeśli ten moduł programu Windows PowerShell został już wcześniej pobrany, wykonaj następujące polecenie, aby sprawdzić, czy numer wersji nie jest niższy niż **2.4.0.0**: `(Get-Module aadrm -ListAvailable).Version` 

### <a name="to-download-your-usage-logs-by-using-powershell"></a>Pobieranie dzienników użycia za pomocą programu PowerShell

1.  Uruchom program Windows PowerShell z opcją **Uruchom jako administrator** i wykonaj polecenie cmdlet [Connect AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice), aby nawiązać połączenie z usługą Azure Rights Management:

    ```
    Connect-AadrmService
    ```
    
2.  Wykonaj następujące polecenie, aby pobrać dzienniki dotyczące określonej daty: 

    ```
    Get-AadrmUserLog -Path <location> -fordate <date>
    ```

    Na przykład po utworzeniu folderu o nazwie Dzienniki na dysku E:
    
    * Aby pobrać dzienniki dotyczące określonej daty (na przykład 1.02.2016), uruchom następujące polecenie: `Get-AadrmUserLog -Path E:\Logs -fordate 2/1/2016`
    
    * Aby pobrać dzienniki dotyczące zakresu dat (np. od 1.02.2016 do 14.02.2016), uruchom następujące polecenie: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016` 

Po określeniu tylko dnia, jak w naszych przykładach, przyjmuje się godzinę 00:00:00 w formacie czasu lokalnego, która jest następnie konwertowana na czas UTC. Po określeniu godziny przy użyciu parametrów -fromdate lub -todate (na przykład -fromdate „2/1/2016 15:00:00”), podane data i godzina są konwertowane na czas UTC. Polecenie Get-AadrmUserLog pobiera następnie dzienniki dla tego przedziału czasu UTC.

Nie można określić okresu krótszego niż cały dzień do pobrania.

Domyślnie to polecenie cmdlet używa trzech wątków do pobierania dzienników. Jeśli przepustowość sieci jest wystarczająca i chcesz skrócić czas wymagany do pobrania dzienników, użyj parametru -NumberOfThreads, który może przybierać wartość z zakresu od 1 do 32. Na przykład uruchomienie następującego polecenia cmdlet spowoduje utworzenie 10 wątków do pobierania dzienników: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016 -numberofthreads 10`


> [!TIP]
> Wszystkie pobrane pliki dziennika można zagregować do formatu CSV przy użyciu narzędzia [Log Parser firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=24659), które umożliwia konwersję pomiędzy różnymi znanymi formatami dziennika. Można również skorzystać z narzędzia do konwersji danych do formatu SYSLOG lub importować dzienniki do bazy danych. Po zainstalowaniu narzędzia uruchom polecenie `LogParser.exe /?` w celu uzyskania pomocy i informacji na temat sposobu jego używania. 
>
> Można na przykład wykonać następujące polecenie, aby zaimportować wszystkie informacje do formatu pliku LOG: `logparser –i:w3c –o:csv "SELECT * INTO AllLogs.csv FROM *.log"`

#### <a name="if-you-manually-enabled-azure-rights-management-usage-logging-before-the-logging-change-february-22-2016"></a>Jeśli rejestrowanie użycia usługi Azure Rights Management zostało włączone ręcznie przed zmianą funkcji rejestrowania w dniu 22 lutego 2016 r.


Jeśli rejestrowanie użycia było wykorzystywane przed zmianą rejestrowania, dzienniki użycia będą znajdowały się na Twoim skonfigurowanym koncie magazynu Azure. Firma Microsoft nie skopiuje tych dzienników z Twojego konta magazynu do nowego zarządzanego konta magazynu usługi Azure Rights Management w ramach zmiany funkcji rejestrowania. Za zarządzanie cyklem życia wcześniej wygenerowanych dzienników odpowiedzialni są użytkownicy. Można wykonać polecenie cmdlet [Get-AadrmUsageLog](/powershell/aadrm/vlatest/get-aadrmusagelog) polecenia cmdlet, aby pobrać stare dzienniki. Przykład:

- Aby pobrać wszystkie dzienniki dostępne w folderze E:\logs: `Get-AadrmUsageLog -Path "E:\Logs"`
    
- Aby pobrać określony zakres obiektów blob: `Get-AadrmUsageLog –Path "E:\Logs" –FromCounter 1024 –ToCounter 2047`

Należy zauważyć, że nie trzeba pobierać dzienników przy użyciu polecenia cmdlet Get-AadrmUsageLog, jeśli została wykonana jedna z następujących czynności:

-  Usługa Azure Rights Management została aktywowana w dniu 22 lutego 2016 r. lub wcześniej, ale nie została włączona funkcja rejestrowania użycia.

- Usługa Azure Rights Management została aktywowana po 22 lutego 2016 r.

## <a name="how-to-interpret-your-azure-rights-management-usage-logs"></a>Interpretowanie dzienników użycia usługi Azure Rights Management
Poniższe informacji mogą ułatwić interpretowanie dzienników użycia usługi Azure Rights Management.

### <a name="the-log-sequence"></a>Sekwencja dzienników
Usługa Azure Rights Management zapisuje dzienniki w postaci serii obiektów blob. 

Każdy wpis w dzienniku ma sygnaturę czasową UTC. Ponieważ usługa Azure Rights Management działa na wielu serwerach w wielu centrach danych, czasami dzienniki mogą wydawać się ułożone nie po kolei, nawet jeśli są posortowane według sygnatur czasowych. Jednak różnica jest mała i zazwyczaj mieści się zakresie jednej minuty. W większości przypadków nie jest to kwestia, która mogłaby stanowić problem podczas analizy dziennika.

### <a name="the-blob-format"></a>Format obiektów blob
Każdy obiekt blob jest w rozszerzonym formacie W3C dziennika. Rozpoczyna się od następujących dwóch wierszy:

**#Software: RMS**

**#Version: 1.1**

Pierwszy wiersz określa, że są to dzienniki usługi Azure Rights Management. Drugi wiersz wskazuje, że pozostała część obiektu blob odpowiada specyfikacji wersji 1.1. Zaleca się, aby wszystkie aplikacje, które analizują te dzienniki, sprawdziły te dwa wiersze przed kontynuowaniem analizowania pozostałej części obiektu blob.

Trzeci wiersz wylicza listę nazw pól rozdzielonych znakami tabulatora:

**#Fields: Data Godzina identyfikator wiersza typ żądania identyfikator użytkownika wynik identyfikator korelacji identyfikator zawartości adres e-mail właściciela wystawcy identyfikator szablonu — nazwa pliku Data publikacji      c-info c-ip admin-action acting-as-user**

Każdy z kolejnych wierszy jest rekordem dziennika. Wartości pól są zapisane w takiej samej kolejności, jak poprzedni wiersz, i są rozdzielone znakami tabulatora. Podczas interpretowania pól skorzystaj z poniższej tabeli.


|   Nazwa pola   | Typ danych W3C |                                                                                                                                                                          Opis                                                                                                                                                                          |                                                            Przykładowa wartość                                                            |
|----------------|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
|      date      |     Data      |                                                                                                                     Data obsługi żądania w formacie UTC.<br /><br />Źródłem jest zegar lokalny na serwerze, który obsłużył żądanie.                                                                                                                     |                                                             2013-06-25                                                              |
|      time      |     Godzina      |                                                                                                            Czas obsługi żądania w 24-godzinnym formacie UTC.<br /><br />Źródłem jest zegar lokalny na serwerze, który obsłużył żądanie.                                                                                                            |                                                              21:59:28                                                               |
|     row-id     |     Tekst      |                                                                           Unikatowy identyfikator GUID dla tego rekordu dziennika. Jeśli ta wartość nie została podana, użyj wartości correlation-id do zidentyfikowania wpisu.<br /><br />Ta wartość jest przydatna przy agregowaniu dzienników lub kopiowaniu dzienników do innego formatu.                                                                           |                                                1c3fe7a9-d9e0-4654-97b7-14fafa72ea63                                                 |
|  request-type  |     Name (Nazwa)      |                                                                                                                                                            Nazwa żądanego interfejsu API usługi RMS.                                                                                                                                                            |                                                           AcquireLicense                                                            |
|    user-id     |    String     |                                                               Użytkownik, który wysłał żądanie.<br /><br />Wartość jest ujęta w cudzysłów pojedynczy. Wywołania z klucza dzierżawy, który jest zarządzany przez użytkownika (BYOK), mają wartość **"**, która ma zastosowanie również w przypadku anonimowych typów żądań.                                                                |                                                          ‘joe@contoso.com’                                                          |
|     result     |    String     |                                                                                                                  ‘Success’, jeśli żądanie zostało obsłużone pomyślnie.<br /><br />Typ błędu w cudzysłowie pojedynczym, jeśli żądanie zakończyło się niepowodzeniem.                                                                                                                   |                                                              'Success'                                                              |
| correlation-id |     Tekst      |                                                                                                 Identyfikator GUID, który jest wspólny dla dziennika klienta usługi RMS i dziennika serwera dotyczącego danego żądania.<br /><br />Ta wartość może być przydatna do rozwiązywania problemów klienta.                                                                                                 |                                                cab52088-8925-4371-be34-4b71a3112356                                                 |
|   content-id   |     Tekst      |                                                                      Identyfikator GUID ujęty w nawiasy klamrowe, który identyfikuje chronioną zawartość (na przykład dokument).<br /><br />To pole ma wartość tylko w przypadku typu żądania AcquireLicense w polu request-type. Dla wszystkich innych typów żądań to pole jest puste.                                                                       |                                               {bb4af47b-cfed-4719-831d-71b98191a4f2}                                                |
|  owner-email   |    String     |                                                                                                                       Adres e-mail właściciela dokumentu.<br /><br /> To pole jest puste, jeśli typem żądania jest RevokeAccess.                                                                                                                        |                                                          alice@contoso.com                                                          |
|     issuer     |    String     |                                                                                                                          Adres e-mail wystawcy dokumentu. <br /><br /> To pole jest puste, jeśli typem żądania jest RevokeAccess.                                                                                                                          |                       alice@contoso.com (lub) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'                       |
|  template-id   |    String     |                                                                                                                    Identyfikator szablonu użytego do ochrony dokumentu. <br /><br /> To pole jest puste, jeśli typem żądania jest RevokeAccess.                                                                                                                     |                                               {6d9371a6-4e2d-4e97-9a38-202233fed26e}                                                |
|   file-name    |    String     | Nazwa pliku chronionego dokumentu śledzonego za pomocą klienta usługi Azure Information Protection dla systemu Windows lub aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management dla systemu Windows. <br /><br />Obecnie dla niektórych plików (takich jak dokumenty pakietu Office) są wyświetlane identyfikatory GUID, a nie rzeczywiste nazwy plików.<br /><br /> To pole jest puste, jeśli typem żądania jest RevokeAccess. |                                                       TopSecretDocument.docx                                                        |
| date-published |     Date      |                                                                                                                          Data, w której włączono ochronę dokumentu.<br /><br /> To pole jest puste, jeśli typem żądania jest RevokeAccess.                                                                                                                           |                                                         2015-10-15T21:37:00                                                         |
|     c-info     |    String     |                                                                                   Informacje o platformie klienta, z której wysłano żądanie.<br /><br />Określony ciąg znaków różni się w zależności od aplikacji (na przykład systemu operacyjnego lub przeglądarki).                                                                                   | 'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64' |
|      c-ip      |    Adres    |                                                                                                                                                       Adres IP klienta, który wysłał żądanie.                                                                                                                                                        |                                                            64.51.202.144                                                            |
|  admin-action  |     Wartość logiczna      |                                                                                                                                    Czy administrator ma dostęp do witryny śledzenia dokumentów w trybie administratora.                                                                                                                                    |                                                                Prawda                                                                 |
| acting-as-user |    String     |                                                                                                                               Adres e-mail użytkownika, dla którego administrator uzyskuje dostęp do witryny śledzenia dokumentów.                                                                                                                                |                                                          'joe@contoso.com'                                                          |

#### <a name="exceptions-for-the-user-id-field"></a>Wyjątki w polu user-id
Chociaż pole user-id zwykle wskazuje użytkownika, który wysłał żądanie, istnieją dwa wyjątki, kiedy wartość w polu nie odwzorowuje rzeczywistego użytkownika:

-   Wartość **'microsoftrmsonline@&lt;ID_dzierżawy&gt;.rms.&lt;region&gt;.aadrm.com'**.

    Oznacza to, że wysłano żądanie usługi Office 365, takich jak Exchange Online lub SharePoint Online. W podanym ciągu znaków *&lt;ID_dzierżawy&gt;* oznacza identyfikator GUID dzierżawy, a *&lt;region&gt;* oznacza region rejestracji dzierżawy. Na przykład ciąg **na** reprezentuje Amerykę Północną, **eu** określa Europę, a **ap** — Azję.

-   Jeśli używasz łącznika usługi RMS.

    Żądania z tego łącznika są rejestrowane przy użyciu nazwy głównej usługi **Aadrm_S-1-7-0**, która jest generowana automatycznie po zainstalowaniu łącznika usług RMS.

#### <a name="typical-request-types"></a>Popularne typy żądań
Istnieje wiele typów żądań usługi Azure Rights Management. W poniższej tabeli przedstawiono niektóre spośród najbardziej popularnych typów żądań.

|Typ żądania|Opis|
|----------------|---------------|
|AcquireLicense|Klient z komputera z systemem Windows żąda licencji dla zawartości chronionej przez usługę RMS.|
|AcquirePreLicense|Klient w imieniu użytkownika żąda licencji dla zawartości chronionej przez usługę RMS.|
|AcquireTemplates|Wykonano wywołanie pobrania szablonów na podstawie identyfikatorów szablonów.|
|AcquireTemplateInformation|Wykonano wywołanie pobrania identyfikatorów szablonu z usługi.|
|AddTemplate|Aby dodać szablon Wykonano wywołanie z witryny Azure portal.|
|AllDocsCsv|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące pobrania pliku CSV ze strony **Wszystkie dokumenty**.|
|BECreateEndUserLicenseV1|Wykonano wywołanie z urządzenia przenośnego dotyczące utworzenia licencji użytkowania.|
|BEGetAllTemplatesV1|Wykonano wywołanie z urządzenia przenośnego (zaplecze) dotyczące pobrania wszystkich szablonów.|
|Certify|Klient certyfikuje użytkownika na potrzeby użycia i tworzenie chronionej zawartości.|
|DeleteTemplateById|Wykonano wywołanie z witryny Azure portal, można usunąć identyfikatora szablonu przez szablonu.|
|DocumentEventsCsv|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące pobrania pliku CSV dla pojedynczego dokumentu.|
|ExportTemplateById|Wykonano wywołanie z witryny Azure portal do eksportowania szablonu na podstawie identyfikatora szablonu.|
|FECreateEndUserLicenseV1|Działanie podobne do typu żądania AcquireLicense, ale dotyczy urządzeń przenośnych.|
|FECreatePublishingLicenseV1|Działanie takie samo, jak połączonych typów żądań Certify i GetClientLicensorCert, ale dotyczy klientów mobilnych.|
|FEGetAllTemplates|Wykonano wywołanie z urządzenia przenośnego (fronton) dotyczące pobrania szablonów.|
|FindServiceLocationsForUser|Wykonano wywołanie kwerendy zwracającej adresy URL, które są używane do wywoływania żądań Certify lub AcquireLicense.|
|GetAllDocs|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące załadowania strony **wszystkie dokumenty** dla użytkownika lub wyszukania wszystkich dokumentów dla dzierżawy. Użyj tej wartości z polami admin-action i acting-as-admin:<br /><br />— pole admin-action jest puste: Widoki użytkowników **wszystkie dokumenty** strony dla swoich własnych dokumentów.<br /><br />— pole admin-action ma wartość true, pole acting-as-user jest puste: Administrator Wyświetla wszystkie dokumenty dla swojej dzierżawy.<br /><br />— pole admin-action to wartość true, pole acting-as-user nie jest pusty: Administrator Wyświetla **wszystkie dokumenty** strony dla użytkownika.|
|GetAllTemplates|Wykonano wywołanie z witryny Azure portal w celu pobrania wszystkich szablonów.|
|GetClientLicensorCert|Klient żąda certyfikatu publikowania (który jest później używany do ochrony zawartości) z komputera z systemem Windows.|
|GetConfiguration|Wykonano wywołanie polecenia cmdlet programu Azure PowerShell w celu pobrania konfiguracji dzierżawy usługi Azure RMS.|
|GetConnectorAuthorizations|Wykonano wywołanie z łączników usługi RMS dotyczące pobrania ich konfiguracji z chmury.|
|GetRecipients|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące przejścia do widoku listy dla pojedynczego dokumentu.|
|GetSingle|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące przejścia do strony **pojedynczego dokumentu**.|
|GetTenantFunctionalState|Azure portal sprawdza, czy usługa Azure Rights Management została aktywowana.|
|GetTemplateById|Wykonano wywołanie z witryny Azure portal do pobrania szablonu przez określenie identyfikatora szablonu.|
|KeyVaultDecryptRequest|Klient próbuje odszyfrować zawartość chronioną przez usługę RMS. Dotyczy tylko klucza dzierżawy zarządzanego przez klienta (BYOK) w usłudze Azure Key Vault.|
|KeyVaultGetKeyInfoRequest|Wykonywane jest wywołanie, aby sprawdzić, czy klucz podany do wykorzystania w usłudze Azure Key Vault dla klucza dzierżawy usługi Azure Information Protection jest dostępny i czy nie jest już używany.|
|KeyVaultSignDigest|Wykonywane jest wywołanie, gdy klucz zarządzany przez klienta (BYOK) w usłudze Azure Key Vault jest używany w celu złożenia podpisu. Jest to zazwyczaj jedno wywołanie dla typów żądań AcquireLicence (lub FECreateEndUserLicenseV1), Certify i GetClientLicensorCert (lub FECreatePublishingLicenseV1).|
|KMSPDecrypt|Klient próbuje odszyfrować zawartość chronioną przez usługę RMS. Dotyczy tylko starszego klucza dzierżawy zarządzanego przez klienta (BYOK).|
|KMSPSignDigest|Wykonywane jest wywołanie, gdy starszy klucz zarządzany przez klienta (BYOK) jest używany w celu złożenia podpisu. Jest to zazwyczaj jedno wywołanie dla typów żądań AcquireLicence (lub FECreateEndUserLicenseV1), Certify i GetClientLicensorCert (lub FECreatePublishingLicenseV1).|
|LoadEventsForMap|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące przejścia do widoku mapy dla pojedynczego dokumentu.|
|LoadEventsForSummary|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące przejścia do widoku osi czasu dla pojedynczego dokumentu.|
|LoadEventsForTimeline|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące przejścia do widoku mapy dla pojedynczego dokumentu.|
|ImportTemplate|Aby zaimportować szablon Wykonano wywołanie z witryny Azure portal.|
|RevokeAccess|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące odwołania dokumentu.|
|SearchUsers |Wykonano wywołanie z witryny śledzenia dokumentów dotyczące wyszukania wszystkich użytkowników w dzierżawie.|
|ServerCertify|Wykonano wywołanie z klienta z obsługą usługi RMS (na przykład programu SharePoint) dotyczące certyfikacji serwera.|
|SetUsageLogFeatureState|Wykonano wywołanie dotyczące włączenia rejestrowania użycia.|
|SetUsageLogStorageAccount|Wykonano wywołanie dotyczące określenia lokalizacji dzienników usługi Azure Rights Management.|
|UpdateNotificationSettings|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące zmiany ustawień powiadomień dla pojedynczego dokumentu.|
|UpdateTemplate|Wykonano wywołanie z witryny Azure portal można zaktualizować istniejącego szablonu.|


## <a name="windows-powershell-reference"></a>Uwagi dotyczące programu Windows PowerShell
Od lutego 2016 r. jedynym poleceniem cmdlet programu Windows PowerShell potrzebnym do rejestrowania użycia usługi Azure Rights Management jest [Get-AadrmUserLog](/powershell/module/aadrm/get-aadrmuserlog). 

Przed wprowadzeniem tej zmiany do obsługi dzienników użycia usługi Azure Rights Management potrzebne były następujące polecenia cmdlet, które obecnie są przestarzałe:  

-   [Disable-AadrmUsageLogFeature](/powershell/module/aadrm/disable-aadrmusagelogfeature)

-   [Enable-AadrmUsageLogFeature](/powershell/module/aadrm/enable-aadrmusagelogfeature)

-   [Get-AadrmUsageLog](/powershell/module/aadrm/get-aadrmusagelog)

-   [Get-AadrmUsageLogFeature](/powershell/module/aadrm/get-aadrmusagelogfeature)

-   [Get-AadrmUsageLogLastCounterValue](/powershell/module/aadrm/get-aadrmusageloglastcountervalue)

-   [Get-AadrmUsageLogStorageAccount](/powershell/module/aadrm/get-aadrmusagelogstorageaccount)

-   [Set-AadrmUsageLogStorageAccount](/powershell/module/aadrm/set-aadrmusagelogstorageaccount)

Jeśli masz w magazynie Azure dzienniki sprzed zmiany funkcji rejestrowania usługi Azure Rights Management, możesz je pobrać w taki sam sposób jak wcześniej, korzystając z tych starszych poleceń cmdlet: Get-AadrmUsageLog i Get-AadrmUsageLogLastCounterValue. Jednak wszystkie nowe dzienniki użycia będą zapisywane w nowym magazynie usługi Azure RMS i muszą zostać pobrane za pomocą polecenia Get-AadrmUserLog.

Aby uzyskać więcej informacji na temat korzystania z programu Windows PowerShell z usługą Azure Rights Management, zobacz temat [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](administer-powershell.md).



