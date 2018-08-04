---
title: Odświeżanie szablonów usługi Azure RMS — AIP
description: W przypadku korzystania z usługi Azure Rights Management szablony są automatycznie pobierane na komputery klienckie, dzięki czemu użytkownicy mogą wybrać je z poziomu ich aplikacji. W przypadku wprowadzenia zmian do szablonów może być jednak konieczne wykonanie dodatkowych czynności.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8c2064f0-dd71-4ca5-9040-1740ab8876fb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4907851f6b538ab0f6c85bc9f5a21d14314af8d3
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491410"
---
# <a name="refreshing-templates-for-users-and-services"></a>Odświeżanie szablonów dla użytkowników i usług

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

W przypadku korzystania z usługi Azure Rights Management w ramach usługi Azure Information Protection szablony są automatycznie pobierane na komputery klienckie, dzięki czemu użytkownicy mogą wybrać je z poziomu ich aplikacji. W przypadku wprowadzenia zmian do szablonów może być jednak konieczne wykonanie dodatkowych czynności:

|Aplikacja lub usługa|Odświeżanie szablonów po wprowadzeniu zmian|
|--------------------------|---------------------------------------------|
|Exchange Online<br /><br />Ma zastosowanie do reguł transportu i aplikacji Outlook Web App |Odświeżane automatycznie w ciągu godziny — nie wymaga dodatkowych kroków.<br /><br />Dotyczy to sytuacji, jeśli używasz [szyfrowanie wiadomości usługi Office 365 dzięki nowym funkcjom](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Jeśli wcześniej skonfigurowano usługi Exchange Online do korzystania z usługi Azure Rights Management, importując zaufaną domenę publikacji (TPD), użyj tego samego zestawu instrukcji włączyć nowych funkcji w programie Exchange Online.|
|Klient usługi Azure Information Protection|Automatyczne odświeżanie przy każdym odświeżeniu zasad usługi Azure Information Protection na komputerze klienckim:<br /><br /> – Po otwarciu aplikacji pakietu Office obsługującej pasek usługi Azure Information Protection. <br /><br /> – Po kliknięciu prawym przyciskiem myszy w celu sklasyfikowania i ochrony pliku lub folderu. <br /><br /> – Po uruchomieniu poleceń cmdlet programu PowerShell mających na celu przypisanie etykiet oraz ochronę (Get-AIPFileStatus and Set-AIPFileLabel).<br /><br /> — W przypadku usługa zostanie uruchomiona skaner ochrony informacji Azure i lokalne zasady jest starsza niż jedna godzina. Ponadto usługa skaner sprawdza obecność zmian co godzinę i używa tych zmian na następny cykl skanowania.<br /><br /> – Każdorazowo po upływie 24 godzin.<br /><br /> Ponadto, jako że klient usługi Azure Information Protection jest ściśle zintegrowany z pakietem Office, wszelkie odświeżone szablony pakietu Office 2016 lub Office 2013 zostaną odświeżone również dla klienta usługi Azure Information Protection.|
|Pakiety Office 2016 i Office 2013<br /><br />Aplikacja RMS sharing dla systemu operacyjnego Windows|Automatycznie odświeżane — według harmonogramu:<br /><br />– W przypadku nowszych wersji pakietu Office: odświeżanie odbywa się domyślnie co 7 dni.<br /><br />– W przypadku aplikacji RMS sharing dla systemu Windows: od wersji 1.0.1784.0 domyślne ustawienie uwzględnia codzienne odświeżanie. W przypadku wcześniejszych wersji odświeżanie odbywa się domyślnie co 7 dni.<br /><br />Aby wymusić odświeżenie w terminie wcześniejszym niż ujęty w harmonogramie, zobacz następującą sekcję: [Pakiety Office 2016 i Office 2013 oraz aplikacja RMS sharing dla systemu Windows: Wymuszenie odświeżenia zmienionego szablonu niestandardowego](#office-2016--office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template).|
|Pakiet Office 2010|Automatyczne odświeżanie, gdy użytkownik wyloguje się z systemu Windows, zaloguje się ponownie i odczeka maksymalnie 1 godzinę.|
|Lokalna instalacja programu Exchange z łącznikiem usługi Rights Management<br /><br />Ma zastosowanie do reguł transportu i aplikacji Outlook Web App|Automatyczne odświeżanie — nie wymaga dodatkowych kroków. Jednak aplikacja Outlook Web App buforuje interfejs użytkownika na dzień.|
|Office 2016 dla komputerów Mac|Automatyczne odświeżanie — nie wymaga dodatkowych kroków.|
|Aplikacja RMS sharing dla komputerów Mac|Automatyczne odświeżanie — nie wymaga dodatkowych kroków.|

Gdy aplikacje klienckie wymagają pobrania szablonów (pierwszy raz lub odświeżonych po zmianach), należy przygotować się na odczekanie do 15 minut, zanim pobranie zostanie ukończone, a nowe lub zaktualizowane szablony staną się w pełni funkcjonalne. Rzeczywisty czas może być różny zależnie od takich czynników, jak rozmiar i złożoność konfiguracji szablonu oraz łączność sieciowa. 

## <a name="office-2016--office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template"></a>Pakiety Office 2016 i Office 2013 oraz aplikacja RMS sharing dla systemu Windows: Wymuszenie odświeżenia zmienionego szablonu niestandardowego
Edytując rejestr na komputerach z pakietem Office 2016 lub Office 2013 albo z aplikacją do udostępniania usługi Rights Management (RMS) dla systemu operacyjnego Windows, można zmienić automatyczny harmonogram w taki sposób, aby zmienione szablony były odświeżane częściej niż częstotliwość domyślna. Można też wymusić natychmiastowe odświeżanie przez usunięcie istniejących danych z wartości rejestru.

> [!WARNING]
> Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, w wyniku których może być konieczna ponowna instalacja systemu operacyjnego. Firma Microsoft nie może zagwarantować użytkownikowi, że uda się rozwiązać problemy wynikające z niewłaściwego używania Edytora rejestru. Używasz Edytora rejestru na własne ryzyko.

### <a name="to-change-the-automatic-schedule"></a>Zmiana automatycznego harmonogramu

1.  Za pomocą edytora rejestru należy utworzyć i ustawić jedną z następujących wartości rejestru:

    - Aby ustawić częstotliwość aktualizacji w dniach (co najmniej 1 dzień): Utwórz nową wartość rejestru o nazwie **TemplateUpdateFrequency** i zdefiniuj dla danych wartość całkowitą, która będzie określać wyrażaną w dniach częstotliwość pobierania wszelkich zmian do pobranego szablonu. Skorzystaj z poniższych informacji, aby zlokalizować ścieżkę rejestru w celu utworzenia wspomnianej nowej wartości rejestru.

        **Ścieżka rejestru:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Typ:** REG_DWORD

        **Wartość:** TemplateUpdateFrequency

    - Aby ustawić częstotliwość aktualizacji w sekundach (co najmniej 1 sekunda): Utwórz nową wartość rejestru o nazwie **TemplateUpdateFrequencyInSeconds** i zdefiniuj dla danych wartość całkowitą, która będzie określać wyrażaną w sekundach częstotliwość pobierania wszelkich zmian do pobranego szablonu. Skorzystaj z poniższych informacji, aby zlokalizować ścieżkę rejestru w celu utworzenia wspomnianej nowej wartości rejestru.

        **Ścieżka rejestru:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Typ:** REG_DWORD

        **Wartość:** TemplateUpdateFrequencyInSeconds

    Upewnij się, że utworzona i ustawiona została jedna z tych wartości rejestru, a nie obie. Jeśli dostępne są obie wartości, wartość **TemplateUpdateFrequency** jest ignorowana.

2.  Aby wymusić natychmiastowe odświeżenie szablonów, przejdź do następnej procedury. Jeśli nie jest konieczne natychmiastowe odświeżenie, należy ponownie uruchomić aplikacje pakietu Office i wystąpienia Eksploratora plików.

### <a name="to-force-an-immediate-refresh"></a>Wymuszenie natychmiastowego odświeżenia

1.  Korzystając z edytora rejestru, usuń dane dla wartości **LastUpdatedTime**. Przykładowa wartość to **2015-04-20T15:52** — w tym przypadku należy usunąć ciąg 2015-04-20T15:52, aby nie były wyświetlane żadne dane. Skorzystaj z poniższych informacji, aby zlokalizować ścieżkę rejestru w celu usunięcia danych dla tej wartości rejestru.

    **Ścieżka rejestru:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\\<*MicrosoftRMS_FQDN*> \Template\\ < *user_alias*>

    **Typ:** REG_SZ

    **Wartość:** LastUpdatedTime

    > [!TIP]
    > W ścieżce rejestru ciąg <*MicrosoftRMS_FQDN*> odnosi się do nazwy FQDN usługi RMS firmy Microsoft. Aby sprawdzić tę wartość:

    > Uruchom polecenie cmdlet [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) dla usługi Azure RMS. Jeśli użytkownik jeszcze nie zainstalowano modułu Windows PowerShell dla usługi Azure RMS, zobacz [Instalowanie modułu AADRM programu PowerShell](install-powershell.md).
    >
    > Opierając się na danych wyjściowych, zidentyfikuj wartość **LicensingIntranetDistributionPointUrl**.
    >
    > Na przykład: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 
    > Wykasuj z wartości ciąg **https://** oraz **/_wmcs/licensing**. Pozostała wartość stanowi nazwę FQDN usługi Microsoft RMS. W naszym przykładzie nazwa FQDN usługi Microsoft RMS ma następującą wartość:
    >
    >**5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Usuń następujący folder i wszystkie zawarte w nim pliki: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Ponownie uruchom aplikacje pakietu Office i wystąpienia Eksploratora plików.


## <a name="see-also"></a>Zobacz też
[Konfigurowanie szablonów i zarządzanie nimi w zasadach usługi Azure Information Protection](configure-policy-templates.md)

