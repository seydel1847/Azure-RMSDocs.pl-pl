---
title: "Włączanie powiadomień e-mail | Azure RMS"
description: "Powiadomienia e-mail umożliwiają powiadamianie właściciela chronionej zawartości o dostępie do jego zawartości."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5FB975EE-E4E5-4089-B8E1-CAFD5B9B34EC
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: de5e3d831e20b06e88aedf6255a34ab5aa2bb58c


---

# <a name="how-to-enable-email-notification"></a>Instrukcje: włączanie powiadomień e-mail

Powiadomienia e-mail umożliwiają powiadamianie właściciela chronionej zawartości o dostępie do jego zawartości.

Aby skonfigurować powiadomienia e-mail dla danej licencji, użyj polecenia [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx) z parametrem typu właściwości *dwPropID* jako [IPC\_LI\_APP\_SPECIFIC\_DATA](https://msdn.microsoft.com/library/hh535287.aspx) oraz polami danych aplikacji sformatowanymi jako [IPC\_NAME\_VALUE\_LIST](https://msdn.microsoft.com/library/hh535277.aspx).

    C++

    int numDataPairs = 3;

    IPC_NAME_VALUE propertyValuePairs [numDataPairs];

    // lcid field set to 0 causes the default lcid to be used

    propertyValuePairs[0] = {"MS.Conetent.Name", 0, "FinancialReport.docx"};
    propertyValuePairs[1] = {"MS.Notify.Enabled",0 , "true"};
    propertyValuePairs[2] = {"MS.Notify.Culture",0 , “en-US”};

    IPC_NAME_VALUE_LIST emailNotificationAppData = {numDataPairs, propertyValuePairs};

    result = IpcSetLicenseProperty( licenseHandle, FALSE, IPC_LI_APP_SPECIFIC_DATA, emailNotificationAppData);


Poniższa tabela zawiera pola danych aplikacji oraz pary nazw właściwości i wartości dla powiadomienia e-mail usługi RMS.


|Nazwa właściwości | Typ danych | Przykładowa wartość | Uwagi |
|--------------|-----------|---------------|-------|
|MS.Content.Name|ciąg|„FinancialReport.docx”|Jest to identyfikator związany z chronioną zawartością.<br><br> W przypadku plików chronionych wartość ta powinna być nazwą pliku bez żadnych danych ścieżki.<br><br> W przypadku innych typów zawartości, takich jak wiadomości e-mail, może to być temat wiadomości e-mail lub też wartość może być pusta.|
|MS.Notify.Enabled|ciąg|„true” &#124; „false”|W przypadku wartości „true” do właściciela licencji publikowania wysyłane jest powiadomienie e-mail przy próbie jej użycia do uzyskania licencji użytkownika końcowego.|
|MS.Notify.Culture|ciąg|„pl-PL”| **Źródło:** System.Globalization.CultureInfo.CurrentUICulture.Name <br><br>Ta wartość jest używana do określenia zlokalizowanego języka powiadomienia e-mail oraz formatowania daty/godziny i liczb używanego w wiadomości e-mail.<br><br>Należy ją ustawić na podstawie ustawień użytkownika maszyny, na której utworzono licencję publikowania, lub też preferowanej kultury właściciela licencji publikowania.|
|MS.Notify.TZID|ciąg|„Czas pacyficzny”|**Źródło:** TimeZoneInfo.Local.Id - identyfikator strefy czasowej systemu Windows.<br><br>Wartość ta to identyfikator strefy czasowej systemu Microsoft Windows, opisujący daną strefę czasową i jej charakterystykę.|
|MS.Notify.TZO|ciąg|“-480”|Jest to przesunięcie strefy czasowej właściciela licencji publikowania w minutach od czasu UTC.<br><br>W przypadku podania prawidłowej wartości TZID używane jest przesunięcie strefy czasowej przez nią określone, a wartość ta jest ignorowana.<br><br>Wartość ta jest używana najczęściej przez platformy publikowania oparte na systemach innych niż Windows, które nie mają dostępu do listy wartości identyfikatorów stref czasowych systemu Windows.<br><br>Jeśli nie podano wartości TZID, wartość ta jest używana do obliczenia przesunięcia czasu w powiadomieniach, a wartość TZSN jest używana (niezależnie od wartości strefy czasowej) do wskazania nazwy strefy czasowej. Spowoduje to zastosowanie stałej strefy czasowej, która nie jest aktualizowana w celu uwzględnienia czasu letniego, jeśli ma zastosowanie.<br><br>Na przykład:<br><br>Jeśli wartość TXID jest pusta, wartość TZ0 ustawiono na „-420”, a wartość TZSN jest ustawiona na „Czas pacyficzny letni”, wszystkie wartości zamieszczone w powiadomieniu e-mail są dostosowywane do czasu pacyficznego letniego i prezentowane w ten sposób, nawet jeśli w danym momencie nie obowiązuje już czas letni.<br><br>Z kolei w przypadku podania wartości TZID wraz z TZSN i TZDN czasy określone w powiadomieniu e-mail są zmieniane i wyświetlane zależnie od tego, czy data i godzina powinny być wyświetlane w trybie czasu letniego, czy też trybie standardowym.|
|MS.Notify.TZSN|ciąg|„Czas pacyficzny”|**Źródło:** TimeZoneInfo.Local.StandardName — nazwa standardowa strefy czasowej.<br><br>Powinna to być zlokalizowana nazwa standardowa strefy czasowej.|
|MS.Notify.TZDN|ciąg|„Czas pacyficzny letni”|**Źródło:** TimeZoneInfo.Local.DaylightName — nazwa letniej strefy czasowej.<br><br>Powinna to być zlokalizowana nazwa letniej strefy czasowej. Może być ona identyczna z nazwą standardową, jeśli dana strefa czasowa nie korzysta z czasu letniego.|

## <a name="related-topics"></a>Tematy pokrewne

- [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx)
- [IPC\_LI\_APP\_SPECIFIC\_DATA](https://msdn.microsoft.com/library/hh535287.aspx)
- [IPC\_NAME\_VALUE\_LIST](https://msdn.microsoft.com/library/hh535277.aspx).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


