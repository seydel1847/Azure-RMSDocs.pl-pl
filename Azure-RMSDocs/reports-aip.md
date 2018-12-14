---
title: Środkowe raportowania usługi Azure Information Protection
description: Jak używać centralnej funkcji raportowania do śledzenia wdrożenia etykiet usługi Azure Information Protection i identyfikowania plików, które zawierają poufne informacje
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/08/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.reviewer: lilukov
ms.suite: ems
ms.openlocfilehash: 58ea955deef9341ec80b516b89feec609389b9ad
ms.sourcegitcommit: 4caf3aa13506554928c5fda38994301ddcbdfb41
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068813"
---
# <a name="central-reporting-for-azure-information-protection"></a>Środkowe raportowania usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> Ta funkcja jest obecnie dostępna w wersji zapoznawczej i może ulec zmianie. Wszystkie dane zebrane w trakcie tego okresu zapoznawczego nie mogą być obsługiwane, gdy ta funkcja zostanie przeniesiony do ogólnej dostępności.

Użyj analizy usługi Azure Information Protection dla centralnej funkcji raportowania do śledzenia przyjęcia etykiet usługi Azure Information Protection. Ponadto:

- Monitorowanie dostępu użytkowników do etykietami dokumentów i wiadomości e-mail i zmiany ich klasyfikacji. 

- Identyfikowanie dokumentów zawierających poufne informacje, które muszą być chronione.

Obecnie dane widoczne są agregowane z klientów usługi Azure Information Protection i skanery usługi Azure Information Protection, a także z systemem Windows [Windows Defender zaawansowanej ochrony przed zagrożeniami (Windows Defender ATP)](/windows/security/threat-protection/windows-defender-atp/overview).

Na przykład można znaleźć w następujących tematach:

- Z **raport użycia**, w którym można wybrać okres:
    
    - Etykiety, które są stosowane
    
    - Jak wiele dokumentów i wiadomości e-mail są są oznaczone etykietami
    
    - Jak wiele dokumentów i wiadomości e-mail są chronione
    
    - Ilu użytkowników oraz ile urządzeń są etykietowania dokumentów i wiadomości e-mail
    
    - Które aplikacje są używane do etykietowania

- Z **dzienników aktywności**, w którym można wybrać okres:
    
    - Jakie etykietowania akcje zostały wykonane przez określonego użytkownika
    
    - Jakie etykietowania akcje zostały wykonane z określonym urządzeniem
    
    - Użytkowników, którzy mają uzyskują dostęp do określonych dokumentów etykietą
    
    - Jakie etykietowania akcje zostały wykonane dla ścieżki konkretnego pliku
    
    - Jakie etykietowania akcje zostały wykonane przez określoną aplikację, takie Eksploratora plików i kliknij prawym przyciskiem myszy lub moduł AzureInformationProtection PowerShell

- Z **odnajdywanie danych** raportu:

    - Jakie pliki znajdują się na swoje repozytoria danych zeskanowane lub komputerach z systemem Windows 10
    
    - Pliki, które są oznaczone i chronione i lokalizację plików według etykiet
    
    - Pliki, które zawierają poufne informacje dotyczące znanych kategorie, takie jak dane finansowe i dane osobowe i lokalizację plików według tych kategorii
    
Raporty używają [usługi Azure Log Analytics](/azure/log-analytics/log-analytics-overview) do przechowywania danych w obszarze roboczym, który Twoja organizacja jest właścicielem. Jeśli znasz język zapytań, można modyfikować zapytania bezpośrednio i utworzyć nowe raporty i pulpity nawigacyjne usługi Power BI. Poznać język zapytań może znaleźć następującego samouczka: [Rozpoczęcie korzystania z portalu usługi analiza](https://docs.loganalytics.io/docs/Learn/Getting-Started/Getting-started-with-the-Analytics-portal). 

Aby uzyskać więcej informacji przeczytaj następujące wpisy na blogu: 

- [Odnajdywanie danych, raportowanie i analiza dla wszystkich swoich danych z usługą Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854)

- [Odnajdywanie i chronić poufne dane przy użyciu usługi Azure Information Protection i usługi Windows Defender ATP](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Discover-and-protect-sensitive-data-through-Azure-Information/ba-p/297292)

### <a name="information-collected-and-sent-to-microsoft"></a>Informacje zbierane i przesyłane do firmy Microsoft

Aby wygenerować raporty, punkty końcowe Wyślij następujące rodzaje informacji do firmy Microsoft:

- Etykieta akcji. Na przykład ustawić etykietę, Zmiana etykiety, dodać lub usunąć ochronę, automatycznej i zalecanej etykiety.

- Nazwa etykiety, przed i po wykonaniu akcji etykietę.

- Identyfikator organizacji dzierżawy.

- Identyfikator użytkownika (adres e-mail lub nazwy UPN).

- Nazwa urządzenia użytkownika.

- W przypadku dokumentów: Ścieżka do pliku i nazwa pliku, dokumentów, które są oznaczone etykietami.

- Dla wiadomości e-mail: Temat wiadomości e-mail, nadawcą wiadomości e-mail i wiadomości e-mail adresaci wiadomości e-mail, które są oznaczone etykietami. 

- Typy informacji poufnych ([wstępnie zdefiniowanych](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) i niestandardowych), zostały wykryte w zawartości.

- Wersja klienta usługi Azure Information Protection.

- Wersja systemu operacyjnego klienta.

Te informacje są przechowywane w obszarze roboczym usługi Azure Log Analytics, które Twoja organizacja jest właścicielem i mogą być wyświetlane przez użytkowników, którzy mają prawa dostępu do tego obszaru roboczego. Aby uzyskać informacji na temat konfigurowania dostępu do swojego obszaru roboczego, zobacz [Zarządzanie kontami i użytkownikami](/azure/log-analytics/log-analytics-manage-access?toc=/azure/azure-monitor#manage-accounts-and-users) sekcji w dokumentacji platformy Azure.

## <a name="prerequisites-for-azure-information-protection-analytics"></a>Wymagania wstępne dotyczące analizy usługi Azure Information Protection
Aby wyświetlić raporty usługi Azure Information Protection i tworzyć własne, upewnij się, że zostały spełnione następujące wymagania.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Subskrypcję platformy Azure, która obejmuje usługi Log Analytics|Zobacz [cen usługi Azure Log Analytics](https://azure.microsoft.com/pricing/details/log-analytics) strony.<br /><br />Jeśli nie masz subskrypcji platformy Azure lub obecnie nie używasz usługi Azure Log Analytics, stronie cennika zawiera również link do bezpłatnej wersji próbnej.|
|Bieżący ogólnie dostępnej wersji klienta usługi Azure Information Protection.|Jeśli użytkownik jeszcze nie zainstalowano tę wersję klienta, możesz pobrać i zainstalować go z [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018).|
|Aby uzyskać **odnajdywania i ryzyko** raportu: <br /><br />-Aby wyświetlić dane z lokalnych magazynów danych, wdrożono co najmniej jedno wystąpienie skanera usługi Azure Information Protection (bieżąca wersja GA) <br /><br />— Aby wyświetlić dane z komputerów z systemem Windows 10, muszą one być minimalna kompilacji 1809, w przypadku korzystania z systemu Windows Defender zaawansowanej ochrony przed zagrożeniami (Windows Defender ATP) i została włączona funkcja integracji usługi Azure Information Protection z usługi Windows Defender Usługa Security Center|Aby uzyskać instrukcje instalacji skaner, zobacz [wdrażanie skanera usługi Azure Information Protection do automatycznego klasyfikowania i ochrony plików](deploy-aip-scanner.md). Jeśli wykonujesz uaktualnienie z poprzedniej wersji skanera, zobacz [uaktualnianie skanera usługi Azure Information Protection](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).<br /><br />Aby uzyskać informacje na temat konfigurowania i korzystania z funkcji integracji usługi Azure Information Protection z usługi Windows Defender Security Center, zobacz [ochrony informacji w Windows — omówienie](/windows/security/threat-protection/windows-defender-atp/information-protection-in-windows-overview).|

## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Konfigurowanie obszaru roboczego usługi Log Analytics dla raportów

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.
    
2. Znajdź **Zarządzaj** opcje menu, a następnie wybierz **analytics (wersja zapoznawcza) Konfiguruj**.

3. Na **usługi Azure Information Protection log analytics** bloku, możesz wyświetlić listę żadnych obszarów roboczych usługi Log Analytics, które są własnością Twojej dzierżawy. Wykonaj jedną z następujących czynności:
    
    - Aby utworzyć nowy obszar roboczy usługi Log Analytics: Wybierz **Utwórz nowy obszar roboczy**, a następnie na **obszar roboczy usługi Log analytics** bloku, podaj wymagane informacje.
    
    - Aby użyć istniejącego obszaru roboczego usługi Log Analytics: Wybierz obszar roboczy z listy.

Jeśli potrzebujesz, aby uzyskać pomoc przy tworzeniu obszaru roboczego usługi Log Analytics, zobacz [Utwórz obszar roboczy usługi Log Analytics w witrynie Azure portal](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace).

W przypadku skonfigurowania obszaru roboczego, możesz przystąpić do ich wyświetlania.

## <a name="how-to-view-the-reports"></a>Jak wyświetlić raporty

W bloku Azure Information Protection, Znajdź **pulpity nawigacyjne** opcje menu, a następnie wybierz jedną z następujących opcji:

- **Raport użycia (wersja zapoznawcza)**: Aby zobaczyć, jak etykiety są używane, należy użyć tego raportu. 

- **Dzienniki aktywności (wersja zapoznawcza)**: Ten raport służy do Zobacz etykietowanie działania użytkowników i na urządzeniach i ścieżki plików.
    
    Ten raport jest obecnie wprowadzane do dzierżawców, więc jeśli nie widzisz go, spróbuj ponownie za kilka dni.
    
    Ten raport zawiera **kolumn** opcja, która pozwala wyświetlić więcej informacji o aktywności niż domyślnym wyświetlaniem.

- **Odnajdywanie danych (wersja zapoznawcza)**: Ten raport zawiera informacje dotyczące plików znalezionych przez skanery lub usługi Windows Defender ATP.

## <a name="how-to-modify-the-reports"></a>Jak modyfikować raporty

Wybierz ikonę zapytania na pulpicie nawigacyjnym, aby otworzyć **wyszukiwanie w dzienniku** bloku: 

![Log Analytics ikonę, aby dostosować raporty usługi Azure Information Protection](./media/log-analytics-icon.png)


Zarejestrowanych danych usługi Azure Information Protection znajduje się w poniższej tabeli: **InformationProtectionLogs_CL**

## <a name="next-steps"></a>Następne kroki
Po przejrzeniu informacji w raportach, można zdecydować wprowadzić zmiany w zasadach usługi Azure Information Protection. Aby uzyskać instrukcje, zobacz [Konfigurowanie zasad usługi Azure Information Protection](configure-policy.md).