---
title: Klient usługi Azure Information Protection — wersja Historia wersji i zasady pomocy technicznej
description: Zobacz, co wprowadzono lub zmieniono w wersji klienta usługi Azure Information Protection dla systemu Windows i zrozumieć zasady cyklu pomocy technicznej.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ff9d6a4ce66deed8add68d7b1efc889ee9448f53
ms.sourcegitcommit: 5866509c17872e274720d3014fe218ed95e86ee3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2018
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Klient usługi Azure Information Protection: wersji wersji historii i obsługa zasad

>*Dotyczy: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, systemu Windows Server 2008 R2*

Zespół pracujący nad usługą Azure Information Protection regularnie aktualizuje klienta usługi Azure Information Protection w celu wprowadzenia poprawek i dodania nowych funkcji. 

Możesz pobrać najnowszej wersji GA i bieżąca wersja preview z [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Te wersje są także objęte wykazu usługi Microsoft Update (kategoria: **usługi Azure Information Protection**), dzięki czemu można wdrożyć klienta przy użyciu usług WSUS lub programu Configuration Manager lub innych mechanizmów wdrażania oprogramowania, które używają Usługa Microsoft Update.

### <a name="servicing-information-and-timelines"></a>Obsługa informacji i osi czasu

Każdej wersji ogólnodostępnej (GA) klienta Azure Information Protection jest obsługiwana przez po kolejnych wersji GA maksymalnie sześć miesięcy. Nieobsługiwanej wersji klienta nie znajdują się na tej stronie. Poprawki i nowe funkcje są zawsze stosowane do najnowszej wersji GA i nie zostaną zastosowane do starszych wersji GA.

Wersje zapoznawcze nie powinny być wdrażane dla użytkowników końcowych w sieciach produkcyjnych. Aby wyświetlić i spróbuj nowe funkcje i poprawki, które są dostępne w następnej wersji GA w zamian użyj najnowszej wersji wstępnej. Nie są obsługiwane w wersji zapoznawczej wersje, które nie są aktualne.

### <a name="release-history"></a>Historia wersji

Skorzystaj z poniższych informacji, aby zobaczyć nowe lub zmienione w obsługiwanej wersji klienta usługi Azure Information Protection dla systemu Windows. Najnowsza wersja jest wyświetlana na początku listy. 

> [!NOTE]
> Drobne poprawki nie są wyświetlane, jeśli wystąpi problem z klientem usługi Azure Information Protection, zaleca się sprawdzenie, czy problem został rozwiązany z najnowszą wersją GA. Jeśli ten problem, sprawdź bieżącą wersję podglądu.
>  
> Aby uzyskać pomoc techniczną, zobacz [opcje pomocy technicznej i zasoby społecznościowe](../get-started/information-support.md#support-options-and-community-resources) informacji. Zachęcamy także do kontaktowania się z naszym zespołem ds. usługi Azure Information Protection w [witrynie Yammer](https://www.yammer.com/askipteam/).

## <a name="versions-later-than-110560"></a>Wersjach starszych niż 1.10.56.0

Jeśli masz wersję klienta, która jest nowsza niż 1.10.56.0 jest kompilacji w wersji zapoznawczej do celów testowania i oceny.

Bieżąca wersja preview to **1.21.203.0** i ma następujące zmiany od bieżącej wersji GA klienta.

Ta wersja zawiera MSIPC wersji 1.0.3403.1224 klienta usługi RMS.

**Nowe funkcje**:

- Skaner usługi Azure Information Protection: moduł programu PowerShell, który znajduje się klient ma nowe polecenia cmdlet do instalowania i konfigurowania skanera, dzięki czemu odnajdywania, klasyfikowania i ochrona plików w sieci lokalnych magazynów danych. Aby uzyskać instrukcje, zobacz [wdrażanie usługi Azure Information Protection skanera można automatycznie klasyfikować i chronić pliki](../deploy-use/deploy-aip-scanner.md). 

- W przypadku aplikacji pakietu Office klasyfikacji automatycznej i zalecanej stale działa w tle, zamiast uruchamiania przy zapisywaniu dokumentów. Ta zmiana zachowania można teraz stosować klasyfikacji automatycznej i zalecanej do dokumentów, które są przechowywane w usłudze SharePoint Online. [Więcej informacji](../deploy-use/configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied) 

- Można teraz ustawić różne oznaczenia wizualne dla programu Word, Excel, PowerPoint i Outlook przy użyciu zmiennej instrukcji "If.App" w ciągu tekstowym i określ typ aplikacji. [Więcej informacji](../deploy-use/configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)

- Obsługa [ustawienie zasad](../deploy-use/configure-policy-settings.md), **wyświetlane na pasku Information Protection w aplikacji pakietu Office**. Gdy to ustawienie jest wyłączone, użytkownicy wybierają etykiety z **Chroń** na Wstążce.

- Nowy klient Zaawansowane ustawienia, aby program Outlook nie ma zastosowania etykiety domyślnej, który jest skonfigurowany w ramach zasad usługi Azure Information Protection. Zamiast tego programu Outlook można stosować różne domyślne etykiety lub bez etykiety. [Więcej informacji](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) 

- W przypadku aplikacji pakietu Office podczas określania uprawnień niestandardowych, można teraz Przeglądaj i wybierz opcję użytkownicy z ikonę książki adresowej. Wybranie tej opcji powoduje parzystości środowiska użytkownika podczas określania uprawnień niestandardowych za pomocą Eksploratora plików.

- Obsługa metodę uwierzytelniania całkowicie nieinterakcyjnym, kont usług, które używają programu PowerShell i nie można udzielić **logować się lokalnie** prawo. Ta metoda uwierzytelniania wymaga użycia nowego *tokenu* parametr o [AIPAuthentication zestaw](/powershell/module/azureinformationprotection/Set-AIPAuthentication), i uruchom skrypt programu PowerShell jako zadania. [Więcej informacji](../rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)

- Nowy parametr *IntegratedAuth* dla [Set-RMSServerAuthentication](/powershell/module/azureinformationprotection/set-rmsserverauthentication). Ten parametr obsługuje tryb serwera usług AD RMS, który jest wymagany dla usług AD RMS do obsługi infrastruktury klasyfikacji plików systemu Windows Server.


**Poprawki**:

Poprawki dla stabilności i dla konkretnych scenariuszy, które obejmują:

- W przypadku wersji pakietu Office 16.0.8628.2010 i nowsze (kliknij instalacja), pasek usługi Azure Information Protection obsługuje najnowsze opcje wyświetlania monitor, które wcześniej może spowodować na pasku Wyświetlanie poza aplikacje pakietu Office.

- Po dwóch organizacji przy użyciu usługi Azure Information Protection udostępnić etykietą dokumentów i wiadomości e-mail, własne etykiety są zachowywane i nie zastępuje etykiety Twojej organizacji.

- Obsługę komórek w programie Excel, które zawierają odsyłacze, które wcześniej spowodowany uszkodzeniem tekst w komórce.

- Obsługa zmiany Motywy pakietu Office i kompozycji systemu Windows, które uprzednio spowodowały program Excel nie zawiera żadnych danych po motyw został zmieniony.

- Teraz plików mających rozszerzenie nazwy pliku .xml mogą być sprawdzane pod kątem zalecaną lub automatyczną klasyfikację.

- Podgląd komunikatów o teraz otworzyć tekstowych plików chronionych (ptxt i pxml) większe niż 20 MB. 

- Zapobiegaj wiszące Outlook stosowania przypomnienia programu Outlook.

- Ładowania początkowego pomyślnie Office 64-bitowy, dzięki czemu możesz chronić dokumenty i wiadomości e-mail.

- Można teraz skonfigurować etykietę uprawnienia zdefiniowane przez użytkownika dla programu Word, Excel, PowerPoint i Eksplorator plików i również użyć Zaawansowane ustawienia klienta dotyczącego Ukryj opcje uprawnienia niestandardowe. [Więcej informacji](client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users) 

- Wrócić do czcionki Calibri skonfigurowanie znaczniki wizualne w zasadach usługi Azure Information Protection dla nazwy czcionki, który nie jest zainstalowany na komputerze klienckim.

- Zapobiegaj Office awarii po uaktualnieniu klienta Azure Information Protection.

- W przypadku aplikacji pakietu Office zwiększenia zużycia pamięcią i wydajnością.

- Po skonfigurowaniu etykiety dla użytkownika zdefiniowane uprawnienia, i ochrony HYOK (AD RMS), nie jest już ochrony niepoprawnie korzysta z usługi Azure Rights Management.

- Bardziej spójne środowisko zarządzania sublabels już dziedziczyć oznaczenia wizualne i ustawienia ochrony ich etykiecie nadrzędnej.


## <a name="version-110560"></a>Wersja 1.10.56.0

**Wydane**: 2017-09/18

Ta wersja zawiera MSIPC wersji 1.0.3219.0619 klienta usługi RMS.

**Nowe funkcje**:

- Obsługa nowych warunków Office 365 DLP, które można skonfigurować dla etykiety. Aby uzyskać więcej informacji, zobacz [Konfigurowanie warunków dla etykiety usługi Azure Information Protection](../deploy-use/configure-policy-classification.md).

- Obsługa etykiety, które są skonfigurowane dla akcji zdefiniowane przez użytkownika. Dla programu Outlook etykieta automatycznie stosuje opcji programu Outlook nie przesyłaj dalej. Dla programu Word, Excel, PowerPoint i Eksploratora plików etykieta monituje użytkownika o określ uprawnienia niestandardowe. Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiety usługi Azure Information Protection do ochrony](../deploy-use/configure-policy-protection.md).

- Etykiety obsługuje wiele języków. Począwszy od 30 sierpnia 2017 [domyślne zasady](../deploy-use/configure-policy-default.md) obsługuje wiele języków, które tej wersji klienta wyświetlana dla użytkowników. Aby użytkownicy widzieli etykiet w ich preferowany język z domyślnych zasad przed tą datą oraz etykiety, które można skonfigurować, zobacz [Konfigurowanie etykiety w różnych językach usługi Azure Information Protection](../deploy-use/configure-policy-languages.md).

- Etykiety są wyświetlane z **Chroń** na Wstążce pakietu Office, oprócz wyświetlania na pasku Information Protection. 

- Ochrona natywna dla następujących typów plików programu Visio: .vsdm, vsdx, .vssm, .vssx, .vstm, .vstx

- Obsługa klienta zaawansowane konfiguracje, które można skonfigurować w portalu Azure. Te konfiguracje obejmują:
    
    - [Ukrycie lub pokazanie przycisku nie przesyłaj dalej w programie Outlook](../rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook)
    
    - [Uprawnienia niestandardowe opcje stały dostępne lub niedostępne dla użytkowników](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users)
    
    - [Trwale ukryć pasek usługi Azure Information Protection](../rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar)
    
    - [Włącz zalecana klasyfikacja w programie Outlook](../rms-client/client-admin-guide-customizations.md#enable-recommended-classification-in-outlook)

- Dla programu PowerShell, obsługiwać pliki etykiet nieinteraktywnie przy użyciu nowych poleceń cmdlet programu PowerShell [AIPAuthentication zestaw](/powershell/module/azureinformationprotection/set-aipauthentication) i [AIPAuthentication wyczyść](/powershell/module/azureinformationprotection/clear-aipauthentication). Aby uzyskać więcej informacji jak używać tych poleceń cmdlet, zobacz [sekcji PowerShell](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) podręczniku administratora.

- Dla polecenia cmdlet programu PowerShell [AIPFileLabel zestaw](/powershell/module/azureinformationprotection/set-aipfilelabel) i [AIPFileClassification zestaw](/powershell/module/azureinformationprotection/set-aipfileclassification), istnieją nowe parametry: **właściciela** i **PreserveFileDetails** . Parametry te umożliwiają Określ adres e-mail właściciela właściwości niestandardowej, a pozostawienie niezmienionej dokumentów, które etykiety daty.

**Poprawki**:

Poprawki dla stabilności i dla konkretnych scenariuszy, które obejmują:

- Obsługa ochrony ogólnej duże pliki, które wcześniej może spowodować uszkodzenie, jeżeli jest większy niż 1 GB. Teraz rozmiar pliku jest ograniczona tylko miejsce na dysku twardym i dostępnej pamięci. Aby uzyskać więcej informacji dotyczących ograniczenia rozmiaru plików, zobacz [rozmiary obsługiwane w przypadku ochrony plików](client-admin-guide-file-types.md#file-sizes-supported-for-protection) z podręcznika administratora.

- Przeglądarka klienta usługi Azure Information Protection otwiera chronione pliki PDF (ppdf) jako tylko do odczytu.

- Obsługa etykietowanie i ochronę plików przechowywanych na serwerze programu SharePoint.

- Znaki wodne teraz obsługuje wiele wierszy. Ponadto oznaczenia wizualne są teraz stosowane do dokumentu na [najpierw zapisać tylko](../deploy-use/configure-policy-markings.md#when-visual-markings-are-applied) zamiast zawsze zapisaniu dokumentu.

- **Uruchom diagnostykę** opcji **Pomoc i opinie** okno dialogowe jest zastępowany **Resetowanie ustawień**. Zachowanie dla tej akcji została zmieniona wylogowaniu się użytkownika i usunięcie zasad usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz [więcej informacji na temat opcji Resetowanie ustawień](..\rms-client\client-admin-guide.md#more-information-about-the-reset-settings-option) z podręcznika administratora.

- Obsługa uwierzytelniania serwera proxy.

Poprawki dla wygody użytkowników, które obejmują:

- Wyślij wiadomość e-mail sprawdzania poprawności, gdy użytkownik określi uprawnień niestandardowych. Ponadto wielu adresów e-mail teraz można określić, naciskając klawisz Enter.

- Etykieta nadrzędna nie jest wyświetlane, gdy wszystkie jego sublabels jest skonfigurowane dla ochrony i klienta nie ma pakietu Office, która obsługuje ochronę. 

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o instalowaniu i używaniu klienta: 

- Użytkownicy: [pobieranie i instalowanie klienta](install-client-app.md)

- Administratorzy: [Podręcznik administratora klienta usługi Azure Information Protection](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
