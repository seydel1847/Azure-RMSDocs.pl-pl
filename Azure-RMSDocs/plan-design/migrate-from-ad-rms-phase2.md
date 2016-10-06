---
title: "Migrowanie z usługi AD RMS do usługi Azure Rights Management — faza 2 | Azure Information Protection"
description: "Faza 2 migracji z usługi AD RMS do usługi Azure Information Protection obejmująca krok 5 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f9a7ceee318fee5414e02af7927256e74800a16
ms.openlocfilehash: 113636139f0ff6e47a5b5c0467dfe8616c641e04


---
# Faza 2 migracji — konfiguracja po stronie klienta

>*Dotyczy: Active Directory Rights Management, Azure Information Protection, Office 365*

Skorzystaj z poniższych informacji dotyczących fazy 2 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują krok 5 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).


## Krok 5. Ponownie skonfiguruj klientów do korzystania z usługi Azure Information Protection
W przypadku klientów systemu Windows:

1.  [Pobierz skrypty migracji](https://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Skrypty te służą do resetowania konfiguracji na komputerach z systemem Windows, co spowoduje korzystanie z usługi Azure Information Protection, a nie usługi AD RMS.

2.  Postępuj zgodnie z instrukcjami w skrypcie przekierowania (Redirect_OnPrem.cmd) w celu zmodyfikowania skryptu w taki sposób, aby wskazywał nową dzierżawę usługi Azure Information Protection.

    > [!IMPORTANT]
    > Instrukcje zawierają opis zastępowania przykładowych adresów **adrms** i **adrms.contoso.com** adresami Twoich serwerów usługi AD RMS. Gdy to robisz, należy sprawdzić, czy nie występują żadne dodatkowe spacje przed adresami lub po nich, które spowodują przerwanie skryptu migracji i są bardzo trudne do zidentyfikowania jako główna przyczyna problemu. Niektóre narzędzia do edycji automatycznie dodają spację po wklejeniu tekstu.

3. Jeśli użytkownicy posiadają pakiet Office 2016: skrypty nie zostały jeszcze zaktualizowane w celu uwzględnienia konfiguracji programu Office 2016, więc jeśli użytkownicy mają tę wersję pakietu Office, należy ręcznie zaktualizować skrypty:

    - W przypadku pliku **CleanUpRMS.cmd** — wyszukaj wiersz `reg delete HKCU\Software\Microsoft\Office\15.0\Common\DRM /f` i poniżej dodaj następujący wiersz:

            reg delete HKCU\Software\Microsoft\Office\16.0\Common\DRM /f

    - W przypadku pliku **Redirect_Onprem.cmd** — wyszukaj wiersz `reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM" /t REG_SZ /v "DefaultServer" /d "%CloudRMS%" /F` i poniżej dodaj następujące dwa wiersze:

            reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM" /t REG_SZ /v "DefaultServerUrl" /d "https://%CloudRMS%/_wmcs/licensing" /F 

            reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM" /t REG_SZ /v "DefaultServer" /d "%CloudRMS%" /F

    Opcjonalnie: skrypty nie odwołują się do programu Office 2016 w komentarzach. Jeśli chcesz zaktualizować komentarze, aby odzwierciedlić te dodatki do pakietu Office 2016, wprowadź następujące zmiany w pliku **Redirect_Onprem.cmd**:

    - Wyszukaj łańcuch `::     or MSIPC (Office 2013) with on-premises AD RMS` i zastąp go następującym łańcuchem:
    
            ::     or MSIPC (Office 2013 and 2016) with on-premises AD RMS

    - Wyszukaj łańcuch `echo Redirect SCP for Office 2013` i zastąp go następującym łańcuchem:
    
            echo Redirect SCP for Office versions based on MSIPC

    - Wyszukaj łańcuch `echo Redirect MSIPC for Office 2013` i zastąp go następującym łańcuchem:
    
            echo Redirect MSIPC for Office versions based on MSIPC

4.  Na komputerach z systemem Windows:

    - Uruchom te skrypty z podwyższonym poziomem uprawnień w kontekście użytkownika.

    W przypadku klientów urządzeń przenośnych i komputerów Mac:

    -  Usuń rekordy SRV systemu DNS, które zostały utworzone podczas wdrażania [rozszerzenia usługi AD RMS dla urządzeń przenośnych](http://technet.microsoft.com/library/dn673574.aspx).

#### Zmiany wprowadzone przez skrypty migracji
W tej sekcji omówiono zmiany wprowadzane za pośrednictwem skryptów migracji. Ten dokument może być używany tylko do celów informacyjnych lub na potrzeby rozwiązywania problemów, jeśli wolisz samodzielnie wprowadzać zmiany.

CleanUpRMS_RUN_Elevated.cmd:

-   Usuń zawartość folderów %userprofile%\AppData\Local\Microsoft\DRM i %userprofile%\AppData\Local\Microsoft\MSIPC, w tym wszystkie podfoldery i pliki o długich nazwach.

-   Usuń zawartość następujących kluczy rejestru:

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   Dodaj następujące wartości rejestru:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Utwórz następujące wartości rejestru dla każdego adresu URL dostarczanego jako parametr w każdej z następujących lokalizacji:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Każdy wpis ma wartość REG_SZ **https://stary_adres_URL_serwera_usług_RMS/_wmcs/licensing** z danymi w następującym formacie: **https://&lt;adres_URL_dzierżawy&gt;/_wmcs/licensing**.

    > [!NOTE]
    > *&lt;adres_URL_dzierżawy&gt;* ma następujący format: **{GUID}.rms.[region].aadrm.com**.
    > 
    > Na przykład: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Tę wartość można znaleźć, identyfikując wartość **RightsManagementServiceId** po uruchomieniu polecenia cmdlet [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) dla usługi Azure RMS.


## Następne kroki
Aby kontynuować migrację, przejdź do [fazy 3 — konfiguracja usług pomocniczych](migrate-from-ad-rms-phase3.md).


<!--HONumber=Sep16_HO4-->


