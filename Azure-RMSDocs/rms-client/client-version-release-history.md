---
title: "Klient usługi Azure Information Protection&colon; wersji wersji historii i obsługa zasad"
description: "Zobacz, co wprowadzono lub zmieniono w wersji klienta usługi Azure Information Protection dla systemu Windows i zrozumieć zasady cyklu pomocy technicznej."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: c3c0acad413ddbbcd1caccd4f1a73c7b0884ae7c
ms.sourcegitcommit: f1d0b899e6d79ebef3829f24711f947316bca8ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2017
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Klient usługi Azure Information Protection: wersji wersji historii i obsługa zasad

>*Dotyczy: Azure Information Protection*

Zespół pracujący nad usługą Azure Information Protection regularnie aktualizuje klienta usługi Azure Information Protection w celu wprowadzenia poprawek i dodania nowych funkcji. 

Możesz pobrać najnowszej wersji GA i bieżąca wersja preview z [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Te wersje są także objęte wykazu usługi Microsoft Update (kategoria: **usługi Azure Information Protection**), dzięki czemu można wdrożyć klienta przy użyciu usług WSUS lub programu Configuration Manager lub innych mechanizmów wdrażania oprogramowania, które używają Usługa Microsoft Update.

### <a name="servicing-information-and-timelines"></a>Obsługa informacji i osi czasu

Klienta usługi Azure Information Protection wersji ogólnodostępnej (GA) są obsługiwane przez okres sześciu miesięcy od ich wydania. Poprawki i nowe funkcje są zawsze stosowane do najnowszej wersji GA i nie zostaną zastosowane do starszych wersji GA.

Wersje zapoznawcze nie powinny być wdrażane dla użytkowników końcowych w sieciach produkcyjnych. Aby wyświetlić i spróbuj nowe funkcje i poprawki, które są dostępne w następnej wersji GA w zamian użyj najnowszej wersji wstępnej. Nie są obsługiwane w wersji zapoznawczej wersje, które nie są aktualne.

### <a name="release-history"></a>Historia wersji

Skorzystaj z poniższych informacji, aby zobaczyć nowe lub zmienione w obsługiwanej wersji klienta usługi Azure Information Protection dla systemu Windows. Najnowsza wersja jest wyświetlana na początku listy. 

> [!NOTE]
> Drobne poprawki nie są wyświetlane, jeśli wystąpi problem z klientem usługi Azure Information Protection, zaleca się sprawdzenie, czy problem został rozwiązany z najnowszą wersją GA. Jeśli ten problem, sprawdź bieżącą wersję podglądu.
>  
> Aby uzyskać pomoc techniczną, zobacz [opcje pomocy technicznej i zasoby społecznościowe](../get-started/information-support.md#support-options-and-community-resources) informacji. Zachęcamy także do kontaktowania się z naszym zespołem ds. usługi Azure Information Protection w [witrynie Yammer](https://www.yammer.com/askipteam/).

## <a name="versions-later-than-110560"></a>Wersjach starszych niż 1.10.56.0

Jeśli masz wersję klienta, która jest nowsza niż 1.10.56.0 jest kompilacji w wersji zapoznawczej do celów testowania i oceny. 

Co to jest nowe lub zostały zmienione w bieżącej wersji preview od ostatniej wersji GA klienta dla **szczegóły** sekcji na [stronę pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 

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

## <a name="version-172100"></a>Wersja 1.7.210.0

**Wydana**: 2017-06-06

Ta wersja zawiera wersję MSIPC 1.0.2217.1 klienta usługi RMS.

**Nowe funkcje**:

- Nowe polecenia cmdlet programu PowerShell [Set-AIPFileClassification](/powershell/module/azureinformationprotection/Set-AIPFileClassification). Po uruchomieniu tego polecenia cmdlet jest sprawdzana zawartość pliku i do plików bez etykiet są automatycznie stosowane etykiety, zgodnie z warunkami określonymi w zasadach usługi Azure Information Protection.

**Poprawki**:

- Wszystkie polecenia cmdlet dotyczące etykietowania i klasyfikacji są teraz obsługiwane na komputerach, które nie są połączone z Internetem, ale mają prawidłowe zasady usługi Azure Information Protection.

- W celu zapewnieniu zgodności, parametr wyjściowy polecenia cmdlet [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) została zmieniona z angielskiego (brytyjskiego) (**IsLabelled**) na angielski (amerykański) (**IsLabeled**). Jeśli masz skrypty lub zautomatyzowane procesy, które poszukują tego parametru, zaktualizuj jego pisownię.

- Ogólne poprawki dotyczące stabilności, które obejmują:

    - Dla programu Outlook: poprawki dotyczące awarii, dużego użycia pamięci i problemów z wyświetlaniem menu.
    
    - Dla programu Word, Excel i PowerPoint: poprawki dotyczące wysokiego użycia procesora, problemów z wyświetlaniem przy zapisywaniu dużych plików programu Excel lub braku odpowiedzi aplikacji. 
    
    Również w przypadku tych aplikacji, w celu zwiększenia wydajności pakietu Office 2016 z usługami SharePoint Online i OneDrive dla firm, automatyczne i zalecane etykietowanie jest stosowane podczas zamykania plików, a nie podczas ich zapisywania (zapisywania automatycznego lub wywołanego przez użytkownika). Podobnie jeśli ustawienie **wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę** jest włączona, użytkownicy nie są monitowani o wybierz etykietę, aż do zamknięcia pliku. Wyjątek stanowią programy Word 2016 i Excel 2016, gdy użytkownik wybiera opcję **Zapisz jako**. Ta akcja wyzwala etykietowanie, jeśli etykietowanie zostało skonfigurowane. 

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o instalowaniu i używaniu klienta: 

- Użytkownicy: [pobieranie i instalowanie klienta](install-client-app.md)

- Administratorzy: [Podręcznik administratora klienta usługi Azure Information Protection](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
