---
# required metadata

title: Konfigurowanie środowiska testowego | Azure RMS
description: Aplikację obsługującą prawa można przetestować z różnymi opcjami serwerów.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurowanie środowiska testowego

Aplikację obsługującą prawa można przetestować z różnymi opcjami serwerów.

**Ważne** Zalecanym najlepszym rozwiązaniem jest przetestowanie aplikacji zestawu Rights Management Services SDK 2.1 najpierw w przedprodukcyjnym środowisku usługi AD RMS względem serwera usługi AD RMS. Następnie, jeśli klient ma mieć możliwość używania aplikacji z usługą Azure RMS, należy przejść do testowania w tym środowisku. Aby uzyskać więcej informacji, zobacz [Umożliwianie współpracy aplikacji usługi z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

 

### Wymagania wstępne

-   [Instalacja zestawu SDK](create-your-first-rights-aware-application.md)

Instrukcje

### Krok 1. Skonfigurowanie środowiska testowego

Aby przetestować aplikację obsługującą prawa, musisz uruchomić ją na serwerze RMS skonfigurowanym jako serwer przedprodukcyjny. Przedprodukcyjny serwer usługi RMS używa przedprodukcyjnej hierarchii certyfikatów lub hierarchii certyfikatów niezależnego dostawcy oprogramowania do szyfrowania i odszyfrowywania plików.

Aby uzyskać więcej informacji na temat hierarchii certyfikatów usługi AD RMS, zobacz [Opis łańcuchów certyfikatów](understanding-certificate-chains.md).

Dostępne są dwie opcje testowania aplikacji na serwerze RMS:

-   **Uruchomienie aplikacji w środowisku niezależnego dostawcy oprogramowania AD RMS z jednym komputerem**. Jeśli używasz systemu Windows Server 2012, Windows Server 2008 R2 lub Windows Server 2008 z zainstalowaną funkcją Hyper-V, możesz wdrożyć środowisko niezależnego dostawcy oprogramowania AD RMS z jednym komputerem, tworząc maszynę wirtualną przy użyciu dysku VHD AD RMS z jednym komputerem. Środowisko niezależnego dostawcy oprogramowania AD RMS z jednym komputerem zapewnia serwer RMS skonfigurowany jako serwer przedprodukcyjny z zainstalowanym klientem Active Directory Rights Management Services Client 2.1. Ustawienia rejestru dotyczące serwera i klienta usługi RMS są już skonfigurowane. Aby przetestować aplikację, uruchom ją na maszynie wirtualnej, na której wdrożono środowisko z jednym komputerem.
-   **Uruchomienie aplikacji na serwerze RMS skonfigurowanym jako serwer przedprodukcyjny i wdrożonym w sieci**. W takim przypadku należy również zainstalować i skonfigurować klienta AD RMS Client 2.1 na komputerze, na którym aplikacja zostanie uruchomiona. Aby uzyskać więcej informacji na ten temat, zobacz [Konfigurowanie klienta](how-to-configure-the-ad-rms-client-2-0.md). Więcej informacji dotyczących wdrażania serwera usługi RMS i konfigurowania go jako serwera przedprodukcyjnego znajduje się w temacie [Instalacja i konfigurowanie serwera](how-to-install-and-configure-an-rms-server.md).

## Tematy pokrewne

* [Sposób użycia](how-to-use-msipc.md)
* [Strona pobierania materiałów dodatkowych seminarium internetowego poświęconego zestawowi AD RMS SDK](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)
* [Konfigurowanie klienta](how-to-configure-the-ad-rms-client-2-0.md)
* [Instalacja zestawu SDK](create-your-first-rights-aware-application.md)
* [Instalacja i konfigurowanie serwera](how-to-install-and-configure-an-rms-server.md)
* [Opis łańcuchów certyfikatów](understanding-certificate-chains.md)
 

 





<!--HONumber=Apr16_HO4-->


