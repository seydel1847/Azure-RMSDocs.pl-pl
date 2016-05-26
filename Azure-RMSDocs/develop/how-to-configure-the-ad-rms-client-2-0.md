---
# required metadata

title: Konfigurowanie klienta | Azure RMS
description: Instrukcje dotyczące konfigurowania klienta Active Directory Rights Management Services Client 2.1.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 74C342BF-0F79-486D-AED7-C53230DE5FA7
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurowanie klienta

Ten temat zawiera instrukcje dotyczące konfigurowania klienta Active Directory Rights Management Services Client 2.1.

**Ważne** W przypadku testowania aplikacji przez uruchomienie jej w jednopunktowym środowisku RMS niezależnego dostawcy oprogramowania nie trzeba konfigurować klienta AD RMS Client 2.1. Aby uzyskać więcej informacji, zobacz [Testowanie aplikacji obsługujących prawa](running-your-first-application.md).

 

### Wymagania wstępne

-   Klient AD RMS Client 2.1 musi być zainstalowany na komputerze, na którym będzie testowana aplikacja.

    -   W przypadku testowania aplikacji na komputerze deweloperskim zestaw SDK 2.1 Usług Rights Management powinien być już na nim zainstalowany. Klient AD RMS Client 2.1 powinien zostać wtedy zainstalowany w trybie cichym.

        Informacje na temat metody instalowania zestawu SDK 2.1 usługi RMS znajdują się w temacie [Instalacja zestawu SDK](create-your-first-rights-aware-application.md).

    -   W przypadku testowania aplikacji na komputerze innym niż komputer deweloperski można zainstalować na nim klienta AD RMS Client 2.1 przy użyciu [strony pobierania klienta AD RMS Client 2.1](http://www.microsoft.com/en-us/download/details.aspx?id=38396).
        **Uwaga** Jeśli aplikacja korzysta z trybu API serwera (**IPC\_API\_MODE\_SERVER**), nie trzeba używać manifestu aplikacji. Można przetestować aplikację na serwerze produkcyjnym usługi RMS, przy czym nie jest wymagane uzyskanie licencji produkcyjnej podczas przełączania do środowiska produkcyjnego. Aby uzyskać więcej informacji na temat aplikacji w trybie serwera, zobacz [Typy aplikacji](application-types.md).

         

-   Konieczne jest zainstalowanie serwera usługi RMS i skonfigurowanie go do pracy w środowisku przedprodukcyjnym. Aby uzyskać więcej informacji, zobacz [Instalacja i konfigurowanie serwera](how-to-install-and-configure-an-rms-server.md).

Instrukcje

### Krok 1. Jak skonfigurować klienta RMS Client 2.1 dla hierarchii przedprodukcyjnej certyfikatów

Poniższe kroki zawierają opis instalacji środowiska uruchomieniowego dewelopera, konfigurowania klienta do korzystania z hierarchii certyfikatów niezależnego dostawcy oprogramowania (przedprodukcyjnej) oraz konfigurowania odnajdywania usług na kliencie.

1.  Skopiuj środowisko uruchomieniowe dewelopera Ipcsecproc\_isv.dll z folderu %MSIPCSDKDIR%\\bin\\x86 (32-bitowe wersje systemu Windows) lub %MSIPCSDKDIR\\bin\\x64 (64-bitowe wersje systemu Windows) do folderu C:\\Program Files\\Active Directory Rights Management Services Client 2.1.

    **Ważne** W przypadku uruchamiania 32-bitowej aplikacji w 64-bitowej wersji systemu Windows należy skopiować bibliotekę Ipcsecproc\_isv.dll z folderu %MSIPCSDKDIR%\\bin\\x86 do folderu C:\\Program Files(x86)\\Active Directory Rights Management Services Client 2.1.

     

2.  Skonfiguruj klienta AD RMS Client 2.1 do korzystania z hierarchii certyfikatów niezależnego dostawcy oprogramowania (przedprodukcyjnej), ustawiając wartość klucza rejestru **Hierarchy** na 1.

    ```
    HKEY_LOCAL_MACHINE
       SOFTWARE
          Microsoft
             MSIPC
                Hierarchy DWORD = 00000001
                Data type
                DWORD
    ```

    **Uwaga** Brak wartości **Hierarchy** w rejestrze jest funkcjonalnie równy ustawieniu tej wartości na 0 (zero), co oznacza pracę zestawu SDK 2.1 usługi RMS w trybie produkcyjnym. Aby uzyskać więcej informacji na temat kluczy i łańcuchów certyfikatów, zobacz [Opis łańcuchów certyfikatów](understanding-certificate-chains.md).

    **Ważne**  
    Jeśli uruchamiasz 32-bitową aplikację w 64-bitowej wersji systemu Windows, musisz ustawić wartość **Hierarchy** w następującej lokalizacji klucza:

    ```
    HKEY_LOCAL_MACHINE
        SOFTWARE
           Wow6432Node
              Microsoft
                MSIPC
    ```
     

3.  Skonfiguruj odnajdywanie po stronie serwera lub klienta, aby umożliwić klientowi AD RMS Client 2.1 odnajdywanie i nawiązywanie komunikacji z przedprodukcyjnym serwerem usługi RMS.

    -   W przypadku odnajdywania po stronie serwera administrator rejestruje punkt połączenia usługi (SCP) dla przedprodukcyjnego klastra głównego usługi RMS w usłudze Active Directory, a klient wysyła do usługi Active Directory zapytanie w celu odnalezienia punktu SCP i nawiązania połączenia z serwerem.
    -   W przypadku odnajdywania po stronie klienta ustawienia odnajdywania usługi RMS konfiguruje się w rejestrze na komputerze, na którym uruchomiono klienta AD RMS Client 2.1. Ustawienia te wskazują klienta AD RMS Client 2.1, którego powinien użyć serwer usługi RMS. Jeśli ustawienia są obecne, nie jest przeprowadzane odnajdywanie po stronie serwera.

    W celu skonfigurowania odnajdywania po stronie klienta można ustawić następujące klucze rejestru, aby wskazywały przedprodukcyjny serwer usługi RMS. Informacje na temat konfigurowania odnajdywania po stronie serwera znajdują się w temacie [Uwagi dotyczące wdrażania klienta RMS Client 2.0](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx).

|Klucz|Wartość|
|---|-----|
|`HKEY_LOCAL_MACHINE\`<br>`SOFTWARE\`<br>`Microsoft\`<br>`MSIPC\`<br>`ServiceLocation\`<br>`EnterpriseCertification`|(Domyślnie):<br><br> [**http**&#124;**https**]**://** *RMSClusterName* **/_wmcs/Certification**|
|`HKEY_LOCAL_MACHINE\`<br>`SOFTWARE\`<br>`Microsoft\`<br>`MSIPC\`<br>`ServiceLocation\`<br>`EnterprisePublishing`|(Domyślnie):<br><br> [**http**&#124;**https**]**://** *RMSClusterName* **/_wmcs/Licensing**|


**Uwaga** Domyślnie kluczy tych nie ma w rejestrze i należy je utworzyć.
     
**Ważne**  
    Jeśli uruchamiasz 32-bitową aplikację w 64-bitowej wersji systemu Windows, musisz ustawić te klucze w następującej lokalizacji klucza:


    HKEY_LOCAL_MACHINE
        SOFTWARE
           Wow6432Node
              Microsoft
                MSIPC
    

### Uwagi

Wskazówki zawarte w tym temacie nie są kompletne. Szczegółowe informacje na temat konfigurowania klienta AD RMS Client 2.1 znajdują się w temacie [Uwagi dotyczące wdrażania klienta RMS Client 2.0](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx).

## Tematy pokrewne


* [Sposób użycia](how-to-use-msipc.md)
* [Uwagi dotyczące wdrażania klienta RMS Client 2.0](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx)
* [Instalacja zestawu SDK](create-your-first-rights-aware-application.md)
* [Instalacja i konfigurowanie serwera](how-to-install-and-configure-an-rms-server.md)
* [Testowanie aplikacji obsługujących prawa](running-your-first-application.md)
* [Opis łańcuchów certyfikatu](understanding-certificate-chains.md)
 

 


<!--HONumber=Apr16_HO4-->


