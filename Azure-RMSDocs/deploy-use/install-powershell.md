---
title: Instalowanie programu PowerShell dla usługi AADRM — AIP
description: Instrukcje instalowania programu Windows PowerShell dla usługi Azure Rights Management z usługi Azure Information Protection. Nazwa tego modułu to AADRM.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 8db342dc8527563268f9c740da3d9741d258ea79
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39373444"
---
# <a name="installing-the-aadrm-powershell-module"></a>Instalowanie modułu AADRM programu PowerShell

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Skorzystaj z poniższych informacji, aby zainstalować moduł Windows PowerShell dla usługi Azure Rights Management z usługi Azure Information Protection. Nazwa tego modułu to AADRM.

Ten moduł programu PowerShell umożliwia administrowanie usługą Azure Rights Management z wiersza polecenia przy użyciu dowolnego komputera z połączeniem internetowym, który spełnia wymagania wstępne określone w kolejnej sekcji. Program Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1.md)] obsługuje wykonywanie skryptów automatyzacji oraz może być wymagany w scenariuszach konfiguracji zaawansowanej. Aby uzyskać więcej informacji na temat zadań administracyjnych i konfiguracji obsługiwanych przez moduł, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](administer-powershell.md).

## <a name="prerequisites"></a>Wymagania wstępne
Ta tabela zawiera wymagania wstępne dotyczące instalowania i używania modułu AADRM programu PowerShell dla usługi Azure Rights Management z usługi Azure Information Protection.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Minimalna wersja programu Windows PowerShell: 3.0|Możesz potwierdzić wersji programu Windows PowerShell, które są uruchomione, wpisując `$PSVersionTable` w sesji programu PowerShell. <br /><br /> Jeśli musisz zainstalować nowszą wersję programu Windows PowerShell, zobacz [Uaktualnianie istniejącego Windows PowerShell](/powershell/scripting/setup/installing-windows-powershell#upgrading-existing-windows-powershell).|
|Minimalna wersja platformy Microsoft .NET Framework: 4.5<br /><br />Uwaga: ta wersja platformy Microsoft .NET Framework jest dołączona do nowszych systemów operacyjnych, w związku z czym jej ręczna instalacja powinna być konieczna tylko wtedy, gdy kliencki system operacyjny jest starszy niż Windows 8.0 lub serwerowy system operacyjny jest starszy niż Windows Server 2012.|Jeśli nie zainstalowano minimalnej wersji platformy Microsoft .NET Framework, można pobrać platformę [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Ta minimalna wersja programu Microsoft .NET Framework jest wymagana dla niektórych klas, których używa w module AADRM.|

Począwszy od wersji 2.5.0.0 modułu AADRM Microsoft Online Services Sign-In Assistant nie jest już wymagane.

> [!NOTE]
> 
> Jeśli zainstalowano wersję modułu AADRM za pomocą usługi Azure Rights Management Administration Tool, użyj **programy i funkcje** odinstalować **Windows Azure AD Rights Management Administration** przed Możesz zainstalować najnowszą wersję modułu AADRM z galerii programu PowerShell.


## <a name="how-to-install-the-aadrm-module"></a>Jak zainstalować moduł AADRM

W module AADRM została przeniesiona do [galerii programu PowerShell](/powershell/gallery/readme) i jest dostępny z Microsoft Download Center. 

### <a name="to-install-the-aadrm-module-from-the-powershell-gallery"></a>Aby zainstalować moduł AADRM z galerii programu PowerShell

Jeśli dopiero zaczynasz pracę w galerii programu PowerShell, zobacz [Rozpoczynanie pracy z galerii programu PowerShell](/powershell/gallery/psgallery/psgallery_gettingstarted). Postępuj zgodnie z instrukcjami dotyczącymi galerii wymagania które obejmują Instalowanie modułu PowerShellGet i dostawcy NuGet.

Aby wyświetlić szczegółowe informacje o AADRM module w galerii programu PowerShell, odwiedź stronę [strony AADRM](https://www.powershellgallery.com/packages/AADRM).

Aby zainstalować moduł AADRM, Uruchom sesję programu PowerShell, za pomocą **Uruchom jako Administrator** opcję i wpisz:

    Install-Module -Name AADRM

Zostanie wyświetlone ostrzeżenie dotyczące instalowania z niezaufanych repozytorium, po naciśnięciu T, aby potwierdzić. Lub naciśnij klawisz N i skonfigurować galerii programu PowerShell jako zaufane repozytorium za pomocą polecenia `Set-PSRepository -Name PSGallery -InstallationPolicy Trusted` , a następnie uruchom ponownie polecenie, aby zainstalować moduł AADRM.  

W przypadku poprzedniej wersji modułu AADRM zainstalowany z galerii programu zaktualizuj ją do najnowszej wersji, wpisując:

    Update-Module -Name AADRM


## <a name="next-steps"></a>Kolejne kroki
W sesji programu Windows PowerShell sprawdź wersję zainstalowanego modułu. Ta czynność jest szczególnie ważna w przypadku przeprowadzenia uaktualnienia ze starszej wersji:

```
(Get-Module AADRM –ListAvailable).Version
```

Uwaga: jeśli wykonanie tego polecenia nie powiedzie się, uruchom najpierw polecenie **Import-Module AADRM**.

Aby zobaczyć, jakie polecenia cmdlet są dostępne, wpisz następujące polecenie:

```
Get-Command -Module AADRM
```

Użyj polecenia `Get-Help <cmdlet_name>`, aby wyświetlić sekcję pomocy dla określonego polecenia cmdlet, i użyj parametru **-online**, aby wyświetlić najnowszą pomoc w witrynie dokumentacji firmy Microsoft. Przykład:

```
Get-Help Connect-AadrmService -online
```

Aby uzyskać dodatkowe informacje:

-   Pełna lista dostępnych poleceń cmdlet: [Moduł AADRM](/powershell/aadrm/vlatest/rightsmanagement)

-   Lista głównych scenariuszy konfiguracji obsługujących program PowerShell: [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](administer-powershell.md)

Przed uruchomieniem dowolnych poleceń konfigurujących usługę [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1.md)] należy nawiązać połączenie z tą usługą przy użyciu polecenia cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice). Po zakończeniu uruchamiania odpowiednich poleceń konfiguracji zaleca się rozłączyć się z usługą przy użyciu polecenia cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice). W przeciwnym razie połączenie zostanie automatycznie rozłączone po upływie określonego czasu braku aktywności. Ze względu na działanie funkcji automatycznego rozłączenia od czasu do czasu może okazać się konieczne ponowne nawiązanie połączenia w ramach sesji programu PowerShell. 

> [!NOTE]
> Jeśli nie aktywowano jeszcze usługi Azure Rights Management, można to zrobić po nawiązaniu połączenia z usługą, używając polecenia cmdlet [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm).

