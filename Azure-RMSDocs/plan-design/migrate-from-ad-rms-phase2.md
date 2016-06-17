---
# required metadata

title: Migrowanie z usług AD RMS do usługi Azure Rights Management — faza 2 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793


# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
# Faza 2 migracji — konfiguracja po stronie klienta

*Dotyczy usług: Active Directory Rights Management Services, Azure Rights Management*

Skorzystaj z poniższych informacji dotyczących fazy 2 migrowania usług AD RMS do usługi Azure Rights Management (Azure RMS). Te procedury obejmują krok 5 z sekcji [Migrowanie z usług AD RMS do usługi Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md).


## Krok 5. Ponowne konfigurowanie klientów do korzystania z usługi Azure RMS
W przypadku klientów systemu Windows:

1.  [Pobierz skrypty migracji](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Skrypty te służą do resetowania konfiguracji na komputerach z systemem Windows, co spowoduje korzystanie z usługi Azure RMS, a nie usług AD RMS.

2.  Postępuj zgodnie z instrukcjami w skrypcie przekierowania (Redirect_OnPrem.cmd) w celu zmodyfikowania skryptu w taki sposób, by wskazywał nową dzierżawę usługi Azure RMS.

3.  Na komputerach z systemem Windows należy uruchamiać te skrypty z podwyższonym poziomem uprawnień w kontekście użytkownika.

W przypadku klientów urządzeń przenośnych i komputerów Mac:

-   Usuń rekordy SRV systemu DNS, które zostały utworzone podczas wdrażania [rozszerzenia usług AD RMS dla urządzeń przenośnych](http://technet.microsoft.com/library/dn673574.aspx)..

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

-   Usuń następujące wartości rejestru:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Utwórz następujące wartości rejestru dla każdego adresu URL dostarczanego jako parametr w każdej z następujących lokalizacji:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Każdy wpis ma wartość REG_SZ **https://OldRMSserverURL/_wmcs/licensing** z danymi w następującym formacie: **https://&lt;Adres_URL_dzierżawy&gt;/_wmcs/licensing**.

    > [!NOTE]
    > *&lt;Adres_URL_dzierżawy&gt;* ma następujący format: **{GUID}.rms.[Region].aadrm.com**..
    > 
    > Na przykład: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Tę wartość można znaleźć, identyfikując wartość **RightsManagementServiceId** po uruchomieniu polecenia cmdlet [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) dla usługi Azure RMS.


## Następne kroki
Aby kontynuować migrację, przejdź do [fazy 3 — konfiguracji usług pomocniczych](migrate-from-ad-rms-phase3.md)..

<!--HONumber=Apr16_HO4-->

