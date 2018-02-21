---
title: Instalowanie programu PowerShell dla AADRM - Efektywnych
description: "Instrukcje instalowania programu Windows PowerShell dla usługi Azure Rights Management z usługi Azure Information Protection. Nazwa tego modułu to AADRM."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 757901d4c16b36dfe14e31f5ab9910c47b0b1917
ms.sourcegitcommit: 31c79d948ec3089a4dc65639f1842c07c7aecba6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2018
---
# <a name="installing-the-aadrm-powershell-module"></a>Instalowanie modułu programu PowerShell AADRM

>*Dotyczy: Azure Information Protection, Office 365*

Skorzystaj z poniższych informacji, aby zainstalować moduł Windows PowerShell dla usługi Azure Rights Management z usługi Azure Information Protection. Nazwa tego modułu to AADRM.

Ten moduł programu PowerShell umożliwia administrowanie usługą Azure Rights Management z wiersza polecenia przy użyciu dowolnego komputera z połączeniem internetowym, który spełnia wymagania wstępne określone w kolejnej sekcji. Program Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] obsługuje wykonywanie skryptów automatyzacji oraz może być wymagany w scenariuszach konfiguracji zaawansowanej. Aby uzyskać więcej informacji na temat zadań administracyjnych i konfiguracji obsługiwanych przez moduł, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](administer-powershell.md).

## <a name="prerequisites"></a>Wymagania wstępne
Poniższa tabela zawiera wymagania wstępne dotyczące instalacji i używania module AADRM środowiska PowerShell dla usługi Azure Rights Management z usługi Azure Information Protection.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Minimalna wersja programu Windows PowerShell: 3.0|Możesz sprawdzić wersję środowiska Windows PowerShell, które są uruchomione, wpisując `$PSVersionTable` w sesji programu PowerShell. <br /><br /> Jeśli musisz zainstalować nowszą wersję programu Windows PowerShell, zobacz [uaktualniania istniejącego programu Windows PowerShell](/powershell/scripting/setup/installing-windows-powershell#upgrading-existing-windows-powershell).|
|Minimalna wersja platformy Microsoft .NET Framework: 4.5<br /><br />Uwaga: ta wersja platformy Microsoft .NET Framework jest dołączona do nowszych systemów operacyjnych, w związku z czym jej ręczna instalacja powinna być konieczna tylko wtedy, gdy kliencki system operacyjny jest starszy niż Windows 8.0 lub serwerowy system operacyjny jest starszy niż Windows Server 2012.|Jeśli nie zainstalowano minimalnej wersji platformy Microsoft .NET Framework, można pobrać platformę [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Ta minimalna wersja architektury Microsoft .NET Framework jest wymagana przez niektóre klasy używane w AADRM module.|

> [!NOTE]
> Począwszy od wersji 2.5.0.0 AADRM module Microsoft Online Services Asystenta logowania nie jest już wymagane.
> 
> Jeśli był zainstalowany moduł AADRM poprzedniej wersji, użyj **programy i funkcje** odinstalować **systemu Windows Azure AD Rights Management administracji** przed zainstalowaniem najnowszej wersji.


## <a name="how-to-install-the-aadrm-module"></a>Jak zainstalować moduł AADRM

AADRM module jest przenoszona do [galerii programu PowerShell](/powershell/gallery/readme), ale przez ograniczony czas jest również dostępny w Microsoft Download Center. 

### <a name="to-install-the-aadrm-module-from-the-powershell-gallery"></a>Aby zainstalować moduł AADRM z galerii programu PowerShell

Jeśli jesteś nowym użytkownikiem galerii programu PowerShell, zobacz [Rozpoczynanie pracy z galerii programu PowerShell](/powershell/gallery/psgallery/psgallery_gettingstarted). Postępuj zgodnie z instrukcjami wymagania w zakresie galerii, które dotyczą instalowania modułu PowerShellGet i dostawcy programu NuGet.

Aby wyświetlić szczegółowe informacje o AADRM module w galerii programu PowerShell, odwiedź stronę [strony AADRM](https://www.powershellgallery.com/packages/AADRM).

Aby zainstalować moduł AADRM, Uruchom sesję programu PowerShell i wpisz:

    Install-Module -Name AADRM


### <a name="to-install-the-aadrm-module-from-the-microsoft-download-center"></a>Aby zainstalować moduł AADRM z Microsoft Download Center

1. Przejdź do witryny Microsoft Download Center i Znajdź [usługi Azure Rights Management Administration Tool](https://go.microsoft.com/fwlink/?LinkId=257721), który zawiera [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] modułu administracyjnego dla programu Windows PowerShell.

2. Pobierz i Zapisz [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] pliku Instalatora **WindowsAzureADRightsManagementAdministration_x64**. Następnie kliknij dwukrotnie ten plik, aby rozpocząć Azure AD Rights Management administracji Kreatora instalacji.

3.  Ukończ pracę kreatora, który instaluje moduł AADRM PowerShell.

## <a name="next-steps"></a>Następne kroki
W sesji programu Windows PowerShell upewnij się, wersję zainstalowanego modułu. Ta czynność jest szczególnie ważna w przypadku przeprowadzenia uaktualnienia ze starszej wersji:

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

Przed uruchomieniem dowolnych poleceń konfigurujących usługę [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] należy nawiązać połączenie z tą usługą przy użyciu polecenia cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice). Po zakończeniu uruchamiania odpowiednich poleceń konfiguracji zaleca się rozłączyć się z usługą przy użyciu polecenia cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice). W przeciwnym razie połączenie zostanie automatycznie rozłączone po upływie określonego czasu braku aktywności. Ze względu na działanie funkcji automatycznego rozłączenia od czasu do czasu może okazać się konieczne ponowne nawiązanie połączenia w ramach sesji programu PowerShell. 

> [!NOTE]
> Jeśli nie aktywowano jeszcze usługi Azure Rights Management, można to zrobić po nawiązaniu połączenia z usługą, używając polecenia cmdlet [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]