---
# required metadata

title: Wdrażanie aplikacji | Azure RMS
description: Ten temat przedstawia opcje wdrażania aplikacji z obsługą praw i przeprowadza Cię przez ten proces
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Wdrażanie aplikacji


Ten temat przedstawia opcje wdrażania aplikacji z obsługą praw i przeprowadza Cię przez ten proces.

> [!IMPORTANT]
> Zalecanym najlepszym rozwiązaniem jest przetestowanie aplikacji z obsługą zestawu SDK 2.1 Usług Rights Management w środowisku przedprodukcyjnym usługi RMS względem serwera usługi RMS. Następnie, jeśli klient ma mieć możliwość używania aplikacji z usługą Azure RMS, należy przejść do testowania w tym środowisku. Aby uzyskać więcej informacji, zobacz [Umożliwianie współpracy aplikacji usługi z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

 

## Opcje instalacji programu Active Directory Rights Management Services Client 2.1

Po utworzeniu pliku manifestu za pomocą certyfikatu produkcji aplikacja jest gotowa do wdrożenia. Jeśli był używany zestaw SDK 2.1 usługi RMS, na komputerze użytkownika końcowego będzie trzeba wdrożyć program Active Directory Rights Management Services Client 2.1.

### AD RMS Client 2.1

Klient AD RMS Client 2.1 to oprogramowanie klienckie pomagające chronić użycie informacji przepływających przez aplikacje korzystające z usługi RMS i dostęp do tych informacji — w przypadku instalacji lokalnej lub instalacji w centrum danych firmy Microsoft.

Klient AD RMS Client 2.1 nie jest składnikiem systemu operacyjnego Windows. Klient AD RMS Client 2.1 jest dostarczany w formie pliku do opcjonalnego pobrania i może być (po potwierdzeniu i zaakceptowaniu umowy licencyjnej) dystrybuowany za darmo razem z aplikacjami innych firm, aby umożliwić klientom dostęp do zawartości, do której prawa dostępu są chronione przez użycie i wdrożenie serwerów usługi RMS w danym środowisku.

> [!IMPORTANT]
> Klient AD RMS Client 2.1 jest powiązany z architekturą i musi odpowiadać architekturze docelowego systemu operacyjnego.


## Opcje instalacji klienta AD RMS Client 2.1

-   **Redystrybucja klienta AD RMS Client 2.1**

    Zalecanym podejściem jest dołączenie pakietu instalatora klienta RMS Client do aplikacji lub rozwiązania z wykorzystaniem preferowanej technologii instalacji. Klient RMS Client może być za darmo dystrybuowany i umieszczany w pakietach z innymi aplikacjami i rozwiązaniami IT.

    Istnieje możliwość interaktywnego instalowania klienta AD RMS Client 2.1 poprzez uruchomienie instalatora klienta AD RMS Client 2.1 lub jego zainstalowanie w trybie cichym. Kroki integracji:

    -   Pobierz instalator klienta RMS Client 2.1
    -   Zintegruj uruchomienie instalatora klienta AD RMS Client 2.1 z instalatorem aplikacji

    Dwa dobre przykłady integracji klienta AD RMS Client 2.1 z aplikacją to pakiet instalatora zestawu SDK 2.1 usługi RMS oraz pakiet Right Protected Folder Explorer. Spróbuj je zainstalować, aby zrozumieć zastosowane podejście.

-   **Ustaw klienta AD RMS Client 2.1 jako warunek wstępny dla instalacji aplikacji**

    W takim przypadku utworzysz warunek wstępny, który spowoduje, że instalacja aplikacji zakończy się niepowodzeniem, jeśli klienta AD RMS Client 2.1 nie będzie na komputerze użytkownika końcowego.

    W przypadku braku klienta podaj komunikat o błędzie, z którego użytkownik dowie się, skąd pobrać kopię klienta AD RMS Client 2.1.

    W przypadku obecności klienta przejdź do instalacji aplikacji.

## Włączanie Usług Azure Rights Management z aplikacją

> [!NOTE]
> W przypadku migracji do nowego modelu ADAL w celu uwierzytelniania nie trzeba instalować usługi SIA. Aby uzyskać więcej informacji, zobacz uwierzytelnianie ADAL dla aplikacji z obsługą usługi RMS.

- **Certyfikowanie aplikacji dla systemu Windows 10** — aktualizacja aplikacji umożliwiająca użycie uwierzytelniania ADAL zamiast asystenta logowania usługi online firmy Microsoft oferuje następujące możliwości:
  - Korzystanie z uwierzytelniania wieloskładnikowego
  - Instalowanie klienta usługi RMS 2.1 bez wymagania uprawnień administracyjnych na maszynie
 
  Aby użytkownik końcowy mógł korzystać z usług Azure Rights Management, należy wdrożyć *Asystenta logowania w witrynie Online Services*. Jako deweloper aplikacji nie wiesz, czy użytkownik końcowy skorzysta z usługi RMS (lokalnie), czy usług Azure Rights Management (usługa w chmurze).

> [!IMPORTANT]
> Uruchomienie aplikacji klienckiej zestawu SDK 2.1 usługi RMS z usługą Azure RMS wymaga zażądania dzierżawy usługi Azure RMS. Wyślij żądanie dzierżawy na adres <rmcstbeta@microsoft.com>.

-   Pobierz [Asystenta logowania w witrynie Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=28177) z Centrum pobierania Microsoft.
-   Upewnij się, że wdrożenie aplikacji z obsługą praw zawiera kontrolę warunków wstępnych dla tego wyboru usługi.
-   Aby uzyskać informacje o własnym testowaniu i wykorzystaniu usługi online przez użytkownika końcowego, zobacz temat TechNet [Konfiguracja usługi Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx).

Aby uzyskać więcej informacji na temat umożliwiania aplikacji korzystania z usługi RMS na potrzeby usług Azure Rights Management, zobacz temat [Umożliwianie współpracy aplikacji z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

## Tematy pokrewne

* [Sposób użycia](how-to-use-msipc.md)
* [Asystent logowania w witrynie Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Konfiguracja usługi Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [Umożliwianie współpracy aplikacji z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md)
 

 





<!--HONumber=Apr16_HO4-->


