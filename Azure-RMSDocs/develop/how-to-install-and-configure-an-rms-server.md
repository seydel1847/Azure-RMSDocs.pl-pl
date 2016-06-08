---
# required metadata

title: Instalacja i konfigurowanie serwera | Azure RMS
description: Zainstaluj i skonfiguruj serwer usługi RMS na potrzeby testowania aplikacji obsługujących prawa.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 32C7F387-CF7E-4CE0-AFC9-4C63FE1E134A
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Zawartość tego zestawu SDK jest nieaktualna. Tymczasem należy korzystać z [bieżącej wersji](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) dokumentacji w witrynie MSDN. **
# Instalacja i konfigurowanie serwera

Ten temat zawiera opis kroków instalacji i konfigurowania serwera usługi RMS na potrzeby testowania aplikacji obsługujących prawa.

**Ważne**  W przypadku testowania aplikacji przez uruchomienie jej w jednopunktowym środowisku RMS niezależnego dostawcy oprogramowania nie jest konieczna instalacja serwera usługi RMS, ponieważ został on już zainstalowany i skonfigurowany w środowisku jednopunktowym.
Dodatkowe informacje na temat jednopunktowego środowiska usługi AD RMS niezależnego dostawcy oprogramowania zamieszczono w artykule [Konfiguracja środowiska testowego](how-to-set-up-your-test-environment.md).

 

## Instrukcje

### Krok 1. Konfiguracja serwera usługi RMS

Poniższe kroki ułatwiają konfigurację serwera usługi RMS i obejmują następujące elementy:

-   Konfiguracja rejestru
-   Instalacja serwera
-   Rejestracja serwera

1.  **Konfiguracja rejestru**

    Aby określić stosowanie hierarchii przedprodukcyjnej certyfikatów, należy określić następujące wartości rejestru.

    **Uwaga**  Jeśli używasz systemu Windows Server 2008 R2 lub Windows Server 2008, ustaw wartości rejestru przed zainstalowaniem usługi AD RMS.

    Jeśli używasz usługi AD RMS w systemie Windows Server 2008 R2, musisz ustawić następującą wartość **REG\_DWORD**. Zmień tę wartość na 0 (zero), aby przełączyć się do hierarchii produkcyjnej.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**Hierarchy** = 0x00000001

    Jeśli używasz usługi AD RMS w systemie Windows Server 2008 R2 lub w usłudze Active Directory wdrożono już inną usługę AD RMS jako usługę przedprodukcyjną, dodaj do rejestru następującą wartość pustego ciągu.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**GICURL** = ""

    Jeśli używasz usługi AD RMS w systemie Windows Server 2008, musisz ustawić następującą wartość **REG\_DWORD**. Zmień tę wartość na 0 (zero), aby przełączyć się do hierarchii produkcyjnej.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**2.0**\\**Hierarchy** = 0x00000001

    Jeśli używasz usługi AD RMS w systemie Windows Server 2008 i w usłudze Active Directory wdrożono już inną usługę AD RMS jako usługę przedprodukcyjną, dodaj do rejestru następującą wartość pustego ciągu.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**2.0**\\**GICURL** = ""

2.  **Instalacja serwera**

    Usługi Active Directory Rights Management (AD RMS) obejmują osobne składniki klienta i serwera. Składnik serwera jest wdrażany jako zestaw usług sieci Web, których można użyć do administrowania infrastrukturą usługi RMS, wydawania licencji dla konsumentów i wydawców treści oraz wydawania certyfikatów dla komputerów i użytkowników.

    Począwszy od systemu Windows Server 2008 składniki klienta i serwera są zawarte w systemie operacyjnym. Składniki serwera dla starszych systemów operacyjnych można pobrać z następującej lokalizacji.

    -   [Serwer usługi RMS 1.0 SP2](http://go.microsoft.com/fwlink/p/?linkid=73722)

    Aby skonfigurować składnik serwera w systemie Windows Server 2008, należy zainstalować rolę usługi AD RMS. Wcześniej jednak należy skonfigurować rejestr, aby określić korzystanie z hierarchii przedprodukcyjnej certyfikatów, nie hierarchii produkcyjnej. Z kolei w przypadku tworzenia aplikacji dla wcześniejszego serwerowego systemu operacyjnego należy skonfigurować rejestr po zainstalowaniu serwera usługi RMS 1.0 SP2, ale przed aprowizacją usługi RMS.

    Aby uzyskać więcej informacji, zobacz poprzedni krok, krok 1, „Konfiguracja rejestru”.

3.  **Rejestracja serwera**

    Należy zarejestrować serwer Usług Rights Management (RMS) w celu zidentyfikowania go w hierarchii przedprodukcyjnej lub hierarchii produkcyjnej. Proces rejestracji pozostawia certyfikat licencjodawcy serwera na komputerze serwera. Ten certyfikat zapewnia powiązanie z elementem głównym zaufania firmy Microsoft. Sposób rejestracji serwera jest zależny od używanej wersji usługi RMS.

    -   **Rejestracja samodzielna**

        Począwszy od systemu Windows Server 2008, można zarejestrować serwer usługi RMS w odpowiedniej hierarchii bez wysyłania informacji do firmy Microsoft. Przy instalacji roli usługi RMS instalowany jest także certyfikat rejestracji samodzielnej i klucz prywatny. Są one używane do automatycznego tworzenia certyfikatu licencjodawcy serwera. Żadne informacje nie są wymieniane z firmą Microsoft.

    -   **Rejestracja online**W przypadku korzystania z usługi AD RMS 1.0 SP2 można zarejestrować serwer online. Rejestracja odbywa się w tle podczas procesu aprowizacji, ale wymagane jest połączenie internetowe oraz konieczne jest określenie odpowiedniej wartości rejestru w celu zidentyfikowania hierarchii, w której rejestrowany jest serwer. Aby zarejestrować się w hierarchii przedprodukcyjnej, dodaj następującą wartość **REG\_SZ** i aprowizuj serwer. Aby zarejestrować się w hierarchii produkcyjnej, usuń tę wartość i aprowizuj serwer.

        Aby uzyskać więcej informacji, zobacz poprzedni krok, krok 1, „Konfiguracja rejestru”.

        **HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**1.0**\\**UddiProvider** = 0e3d9bb8-b765-4a68-a329-51548685fed3

## Tematy pokrewne

* [Sposób użycia](how-to-use-msipc.md)
 

 





<!--HONumber=Jun16_HO1-->


