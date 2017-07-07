---
title: "Instalowanie programu Windows PowerShell dla usługi Azure Rights Management — AIP"
description: "Instrukcje instalowania programu Windows PowerShell dla usługi Azure Rights Management z usługi Azure Information Protection. Nazwa tego modułu to AADRM."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5dae84eea9e67be75530d69b6124b97c7c29f8a3
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="installing-windows-powershell-for-azure-rights-management"></a>Instalowanie programu Windows PowerShell dla usługi Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

Skorzystaj z poniższych informacji, aby zainstalować moduł Windows PowerShell dla usługi Azure Rights Management z usługi Azure Information Protection.

Ten moduł programu PowerShell umożliwia administrowanie usługą Azure Rights Management z wiersza polecenia przy użyciu dowolnego komputera z połączeniem internetowym, który spełnia wymagania wstępne określone w kolejnej sekcji. Program Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] obsługuje wykonywanie skryptów automatyzacji oraz może być wymagany w scenariuszach konfiguracji zaawansowanej. Aby uzyskać więcej informacji na temat zadań administracyjnych i konfiguracji obsługiwanych przez moduł, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](administer-powershell.md).

## <a name="prerequisites"></a>Wymagania wstępne
Poniższa tabela zawiera wymagania wstępne dotyczące instalacji i używania programu Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Wersja systemu Windows, która obsługuje moduł administracji usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]|Sprawdź listę obsługiwanych systemów operacyjnych w sekcji **Wymagania systemowe** [strony pobierania narzędzia Azure Rights Management Administration Tool](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Minimalna wersja programu Windows PowerShell: 2.0<br /><br /> |Domyślnie większość systemów operacyjnych Windows jest instalowana z programem Windows PowerShell w wersji co najmniej 2.0. Jeśli musisz zainstalować tę minimalną obsługiwaną wersję, zobacz artykuł [Install Windows PowerShell 2.0](https://msdn.microsoft.com/library/ff637750.aspx) (Instalowanie programu Windows PowerShell 2.0).<br /><br />Porada: używaną wersję programu Windows PowerShell możesz sprawdzić, wpisując polecenie `$PSVersionTable` w sesji programu PowerShell. <br /><br /> Użytkownicy tej wersji minimalnej muszą ręcznie załadować moduł w sesji programu PowerShell, uruchamiając polecenie `Import-Module AADRM` przed użyciem jakiegokolwiek polecenia cmdlet z modułu administracyjnego usługi Rights Management. W przypadku środowiska Windows PowerShell w wersji 3 lub nowszej moduł ładuje się automatycznie i nie jest wymagane użycie dodatkowego polecenia.|
|Minimalna wersja platformy Microsoft .NET Framework: 4.5<br /><br />Uwaga: ta wersja platformy Microsoft .NET Framework jest dołączona do nowszych systemów operacyjnych, w związku z czym jej ręczna instalacja powinna być konieczna tylko wtedy, gdy kliencki system operacyjny jest starszy niż Windows 8.0 lub serwerowy system operacyjny jest starszy niż Windows Server 2012.|Jeśli nie zainstalowano minimalnej wersji platformy Microsoft .NET Framework, można pobrać platformę [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Ta minimalna wersja platformy Microsoft .NET Framework jest wymagana przez niektóre klasy używane przez moduł administracyjny usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|

> [!NOTE]
> Począwszy od wersji 2.5.0.0 modułu administracyjnego usługi Rights Management, asystent logowania w witrynie Microsoft Online Services nie jest już wymagany.
> 
> Jeśli istniała już zainstalowana wcześniejsza wersja modułu administracyjnego usługi Rights Management, użyj opcji **Programy i funkcje**, aby odinstalować narzędzie **Windows Azure AD Rights Management Administration** przed zainstalowaniem najnowszej wersji.


## <a name="how-to-install-the-rights-management-administration-module"></a>Instalacja modułu administracyjnego usługi Rights Management

1.  Przejdź do Centrum pobierania Microsoft i pobierz [narzędzie Azure Rights Management Administration Tool](https://go.microsoft.com/fwlink/?LinkId=257721), które zawiera moduł administracyjny usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] dla programu Windows PowerShell.

2.  W folderze lokalnym, do którego pobrano i w którym zapisano plik instalatora usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], kliknij dwukrotnie plik wykonywalny pobrany dla używanej platformy (WindowsAzureADRightsManagementAdministration_x64 lub WindowsAzureADRightsManagementAdministration_x86.exe), aby uruchomić Kreatora instalacji modułu administracyjnego usługi Azure AD Rights Management.

3.  Ukończ pracę kreatora.

Zostanie zainstalowany program Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

## <a name="next-steps"></a>Następne kroki
Uruchom sesję programu Windows PowerShell i sprawdź wersję zainstalowanego modułu. Ta czynność jest szczególnie ważna w przypadku przeprowadzenia uaktualnienia ze starszej wersji:

```
(Get-Module AADRM –ListAvailable).Version
```

Uwaga: jeśli wykonanie tego polecenia nie powiedzie się, uruchom najpierw polecenie **Import-Module AADRM**.

Aby zobaczyć, jakie polecenia cmdlet są dostępne, wpisz następujące polecenie:

```
Get-Command -Module AADRM
```

Użyj polecenia `Get-Help <cmdlet_name>`, aby wyświetlić sekcję pomocy dla określonego polecenia cmdlet, i użyj parametru **-online**, aby wyświetlić najnowszą pomoc w witrynie dokumentacji firmy Microsoft. Na przykład:

```
Get-Help Connect-AadrmService -online
```


Aby uzyskać dodatkowe informacje:

-   Pełna lista dostępnych poleceń cmdlet: [Moduł AADRM](/powershell/aadrm/vlatest/rightsmanagement)

-   Lista głównych scenariuszy konfiguracji obsługujących program PowerShell: [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](administer-powershell.md)

Przed uruchomieniem dowolnych poleceń konfigurujących usługę [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] należy nawiązać połączenie z tą usługą przy użyciu polecenia cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice). 

Po zakończeniu uruchamiania odpowiednich poleceń konfiguracji zaleca się rozłączyć się z usługą przy użyciu polecenia cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice). W przeciwnym razie połączenie zostanie automatycznie rozłączone po upływie określonego czasu braku aktywności. Ze względu na działanie funkcji automatycznego rozłączenia od czasu do czasu może okazać się konieczne ponowne nawiązanie połączenia w ramach sesji programu PowerShell. 

> [!NOTE]
> Jeśli nie aktywowano jeszcze usługi Azure Rights Management, można to zrobić po nawiązaniu połączenia z usługą, używając polecenia cmdlet [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]