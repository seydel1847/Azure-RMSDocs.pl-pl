---
title: Jak zainstalować i skonfigurować serwer usługi RMS oraz używać go do testowania | Azure RMS
description: Zainstaluj i skonfiguruj serwer usługi RMS na potrzeby testowania aplikacji obsługujących prawa.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 32C7F387-CF7E-4CE0-AFC9-4C63FE1E134A
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 515f3b70e83ddff793f79b4becd8084d306a4aa0
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393830"
---
# <a name="how-to-install-configure-and-test-with-an-rms-server"></a>Instrukcje: instalowanie i konfigurowanie serwera usługi RMS oraz używanie go do testowania

Ten temat zawiera opis procedur związanych z nawiązywaniem połączenia z serwerem usługi RMS lub usługą Azure RMS na potrzeby testowania aplikacji obsługującej prawa.
 
## <a name="instructions"></a>Instrukcje

### <a name="step-1-setup-your-rms-server"></a>Krok 1: Konfiguracja serwera usługi RMS

Poniższe kroki ułatwiają konfigurację serwera usługi RMS i obejmują następujące elementy:

-   Instalacja serwera
-   Rejestracja serwera

1. **Instalacja serwera**

   Usługi Active Directory Rights Management (AD RMS) obejmują osobne składniki klienta i serwera. Składnik serwera jest wdrażany jako zestaw usług sieci Web, których można użyć do administrowania infrastrukturą usługi RMS, wydawania licencji dla konsumentów i wydawców treści oraz wydawania certyfikatów dla komputerów i użytkowników.

   Począwszy od systemu Windows Server 2008 składniki klienta i serwera są zawarte w systemie operacyjnym. Składniki serwera dla starszych systemów operacyjnych można pobrać z następującej lokalizacji.

   -   [Serwer usługi RMS 1.0 SP2](https://go.microsoft.com/fwlink/p/?linkid=73722)

   Aby skonfigurować składnik serwera w systemie Windows Server 2008, należy zainstalować rolę usługi AD RMS. W przypadku tworzenia aplikacji dla wcześniejszego serwerowego systemu operacyjnego należy skonfigurować rejestr po zainstalowaniu serwera usługi RMS 1.0 SP2, ale przed aprowizacją usługi RMS.

2. **Rejestracja serwera**

   Należy zarejestrować serwer Usług Rights Management (RMS) w celu zidentyfikowania go w hierarchii przedprodukcyjnej lub hierarchii produkcyjnej. Proces rejestracji pozostawia certyfikat licencjodawcy serwera na komputerze serwera. Ten certyfikat zapewnia powiązanie z elementem głównym zaufania firmy Microsoft. Sposób rejestracji serwera jest zależny od używanej wersji usługi RMS.

   -   **Rejestracja samodzielna**

       Począwszy od systemu Windows Server 2008, można zarejestrować serwer usługi RMS w odpowiedniej hierarchii bez wysyłania informacji do firmy Microsoft. Przy instalacji roli usługi RMS instalowany jest także certyfikat rejestracji samodzielnej i klucz prywatny. Są one używane do automatycznego tworzenia certyfikatu licencjodawcy serwera. Żadne informacje nie są wymieniane z firmą Microsoft.

   -   **Rejestracja online**

       W przypadku korzystania z usługi AD RMS 1.0 SP2 można zarejestrować serwer online. Rejestracja odbywa się w tle podczas procesu aprowizacji, ale wymagane jest połączenie internetowe.

       **HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**1.0**\\**UddiProvider** = 0e3d9bb8-b765-4a68-a329-51548685fed3

3. **Testowanie za pomocą serwera usługi RMS**

    Aby przeprowadzić testy za pomocą serwera usługi RMS, skonfiguruj odnajdywanie po stronie serwera lub klienta w celu umożliwienia klientowi Rights Management Service Client 2.1 odnajdywania serwera usługi RMS i nawiązywania z nią komunikacji.

    > [!Note]
    > Testowanie za pomocą usługi Azure RMS nie wymaga konfiguracji odnajdywania.

   - W przypadku odnajdywania po stronie serwera administrator rejestruje punkt połączenia usługi (SCP) dla klastra głównego usługi RMS w usłudze Active Directory, a klient wysyła do usługi Active Directory zapytanie w celu odnalezienia punktu SCP i nawiązania połączenia z serwerem.
   - W przypadku odnajdywania po stronie klienta ustawienia odnajdywania usługi RMS są konfigurowane w rejestrze na komputerze, na którym uruchomiono klienta RMS Client 2.1. Ustawienia te wskazują klienta RMS Client 2.1, którego powinien użyć serwer usługi RMS. Jeśli ustawienia są obecne, nie jest przeprowadzane odnajdywanie po stronie serwera.

   W celu skonfigurowania odnajdywania po stronie klienta można ustawić poniższe klucze rejestru, aby wskazywały serwer usługi RMS. Aby uzyskać informacje na temat konfigurowania odnajdywania po stronie serwera, zobacz [Uwagi dotyczące wdrażania klienta RMS Client 2.0](https://technet.microsoft.com/library/jj159267(WS.10).aspx).

4. **EnterpriseCertification**

        HKEY_LOCAL_MACHINE
          SOFTWARE
            Microsoft
              MSIPC
                ServiceLocation
                  EnterpriseCertification

   **Wartość**: (Opcja domyślna): [**http | https**]: //RMSClusterName/**_wmcs/Certification**

5. **EnterprisePublishing**

        HKEY_LOCAL_MACHINE
          SOFTWARE
            Microsoft
              MSIPC
                ServiceLocation
                  EnterprisePublishing
                  
   **Wartość**: (Opcja domyślna): [**http | https**]: //RMSClusterName/**_wmcs/Licensing**

> [!NOTE]
> Domyślnie tych kluczy nie ma w rejestrze i należy je utworzyć.
> 
> [!IMPORTANT]
> Jeśli uruchamiasz 32-bitową aplikację w 64-bitowej wersji systemu Windows, musisz ustawić te klucze w następującej lokalizacji klucza:<p>
>   ```    
>   HKEY_LOCAL_MACHINE
>     SOFTWARE
>       Wow6432Node
>         Microsoft
>           MSIPC
>             ```
