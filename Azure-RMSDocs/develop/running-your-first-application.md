---
# required metadata

title: Testowanie aplikacji obsługujących prawa | Azure RMS
description: Zawiera opis czynności, które należy wykonać, aby przetestować obsługującą prawa aplikację zestawu SDK 2.1 usługi RMS.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 834B7242-31D3-4275-A892-CFE95A61E29E
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Testowanie aplikacji obsługującej prawa

Ten temat zawiera opis czynności, które należy wykonać, aby przetestować obsługującą prawa aplikację zestawu SDK 2.1 Usług Rights Management.

W celu publikacji chronionej zawartości i korzystania z niej aplikacja Usług Rights Management (RMS) korzysta z różnych typów certyfikatów i licencji, z których każda obejmuje łańcuch certyfikatów prowadzący ostatecznie do urzędu certyfikacji firmy Microsoft. Firma Microsoft udostępnia następujące hierarchie:

-   Hierarchia przedprodukcyjna może służyć do tworzenia i testowania aplikacji.
-   Hierarchia produkcyjna musi być używana przez opublikowane aplikacje

Przy tworzeniu aplikacji zaleca się korzystanie z hierarchii przedprodukcyjnej. Umożliwia to pracę bez podpisywania produkcyjnej umowy licencyjnej z firmą Microsoft.

> [!IMPORTANT]
> Zalecanym najlepszym rozwiązaniem jest przetestowanie aplikacji zestawu SDK 2.1 usługi RMS w środowisku przedprodukcyjnym usługi RMS względem serwera usługi RMS. Następnie, jeśli klient ma mieć możliwość używania aplikacji z usługą Azure RMS, należy przejść do testowania w tym środowisku. Aby uzyskać więcej informacji, zobacz [Umożliwianie współpracy aplikacji usługi z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

 

### Wymagania wstępne

-   Konfigurowanie środowiska deweloperskiego zestawu SDK 2.1 usługi RMS. Aby uzyskać więcej informacji, zobacz [Konfigurowanie przedprodukcyjnego środowiska deweloperskiego](how-to-set-up-the-pre-production-development-environment.md).
-   Aby zapoznać się z przykładową aplikacją, zobacz temat [IPCHelloWorld — przykładowa aplikacja](how-to-build-your-first-application.md).

Instrukcje

### Krok 1.

Tworzenie i kompilacja aplikacji obsługującej prawa. Opcje zamieszczono w powyższej sekcji Wymaganie wstępne.

### Krok 2. Generowanie manifestu aplikacji przy użyciu przedprodukcyjnego łańcucha certyfikatów

Przed uruchomieniem aplikacji należy wygenerować jej manifest.

**Uwaga** Jeśli aplikacja korzysta z trybu API serwera (**IPC\_API\_MODE\_SERVER**), nie trzeba używać manifestu aplikacji. Można przetestować aplikację na serwerze produkcyjnym usługi AD RMS, przy czym nie jest wymagane uzyskanie licencji produkcyjnej podczas przełączania do środowiska produkcyjnego. Aby uzyskać więcej informacji na temat aplikacji w trybie serwera, zobacz [Typy aplikacji](application-types.md).

 

Ten proces jest nazywany również podpisywaniem aplikacji. Manifest można wygenerować przy użyciu produkcyjnego łańcucha certyfikatów lub przedprodukcyjnego łańcucha certyfikatów instalowanego z zestawem SDK. Podczas tworzenia zaleca się stosowanie przedprodukcyjnego łańcucha certyfikatów.

Aby uzyskać więcej informacji na temat kluczy i łańcuchów certyfikatów, zobacz [Opis łańcuchów certyfikatów](understanding-certificate-chains.md).

Aby uzyskać informacje na temat metod podpisywania aplikacji przy użyciu łańcucha certyfikatów produktu, zobacz [Przełączanie do środowiska produkcyjnego](switching-to-the-production-environment.md).

Aby wygenerować manifest aplikacji przy użyciu przedprodukcyjnego łańcucha certyfikatów, wykonaj następujące kroki na komputerze deweloperskim:

1.  Skopiuj następujące pliki z katalogów instalacyjnych do folderu, w którym znajduje się aplikacja.

    %MSIPCSdkDir%\\Tools\\Genmanifest.exe

    %MSIPCSdkDir%\\bin\\Isvtier5appsigningprivkey.dat

    %MSIPCSdkDir%\\bin\\Isvtier5appsigningpubkey.dat

    %MSIPCSdkDir%\\bin\\Isvtier5appsignsdk\_client.xml

    %MSIPCSdkDir%\\bin\\YourAppName.isv.mcf

2.  W folderze aplikacji zmień nazwę pliku konfiguracji manifestu YourAppName.isv.mcf na nazwę aplikacji z dodanym rozszerzeniem pliku mcf. Na przykład jeśli aplikacja nosi nazwę MojaAplikacja.exe, zmień nazwę pliku YourAppName.isv.mcf na MojaAplikacja.exe.mcf.

3.  Użyj edytora tekstów, aby dodać aplikację do pliku konfiguracji manifestu. W tym celu zmień tekst zastępczy &lt;YourAppName&gt;.exe na liście modułów w pliku mcf na nazwę aplikacji, na przykład MojaAplikacja.exe.

    Proces podpisywania generuje błąd w przypadku użycia pliku mcf bez zmodyfikowania go.

4.  Uruchom program Genmanifest.exe, aby wygenerować manifest aplikacji. Ten proces jest nazywany również podpisywaniem aplikacji. Operacja ta powinna zwracać plik man. Na przykład jeśli aplikacja nosi nazwę MojaAplikacja.exe, a plik konfiguracji manifestu to MojaAplikacja.exe.mcf, uruchom następujące polecenie:

    **genmanifest.exe -chain isvtier5appsignsdk\_client.xml MojaAplikacja.exe.mcf MojaAplikacja.exe.man**

### Krok 3. Uruchamianie aplikacji

Aplikację można uruchomić z dowolnego katalogu, ale manifest aplikacji (MojaAplikacja.exe.man) musi znajdować się w tym samym katalogu co plik wykonywalny (MojaAplikacja.exe).

-   **Korzystanie ze środowiska jednopunktowego usługi RMS**

    Jeśli korzystasz ze środowiska jednopunktowego usługi RMS do testowania aplikacji, skopiuj plik wykonywalny aplikacji i manifest aplikacji do dowolnego katalogu w środowisku jednopunktowym i uruchom aplikację.

    Informacje na temat jednopunktowego środowiska usługi RMS zamieszczono w artykule [Konfiguracja środowiska testowego](how-to-set-up-your-test-environment.md).

-   **Korzystanie z konfiguracji serwera przedprodukcyjnego**

    Jeśli testujesz aplikację przy użyciu serwera RMS skonfigurowanego do produkcji wstępnej, upewnij się, że skonfigurowano klienta Active Directory Rights Management Services Client 2.1 na komputerze, na którym zostanie uruchomiona aplikacja, na przykład na komputerze dewelopera. Następnie upewnij się, że plik wykonywalny aplikacji i manifest aplikacji znajdują się w tym samym katalogu na komputerze, i uruchom aplikację.

    Aby uzyskać informacje na temat konfigurowania klienta na komputerze, zobacz [Konfigurowanie klienta](how-to-configure-the-ad-rms-client-2-0.md). Aby uzyskać informacje na temat instalowania serwera usługi RMS, zobacz temat [Instalacja i konfigurowanie serwera](how-to-install-and-configure-an-rms-server.md).

## Tematy pokrewne

* [Sposób użycia](how-to-use-msipc.md)
* [Konfigurowanie klienta](how-to-configure-the-ad-rms-client-2-0.md)
* [Instalacja i konfigurowanie serwera](how-to-install-and-configure-an-rms-server.md)
* [IPCHelloWorld — przykładowa aplikacja](how-to-build-your-first-application.md)
* [Konfigurowanie przedprodukcyjnego środowiska deweloperskiego](how-to-set-up-the-pre-production-development-environment.md)
* [Przełączanie do środowiska produkcyjnego](switching-to-the-production-environment.md)
* [Konfigurowanie środowiska testowego](how-to-set-up-your-test-environment.md)
* [Opis łańcuchów certyfikatu](understanding-certificate-chains.md)
 

 





<!--HONumber=Apr16_HO4-->


