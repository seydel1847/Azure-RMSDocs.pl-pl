---
title: "Tworzenie aplikacji użytkownika | Azure Information Protection"
description: "Ten temat zawiera opis procesu wdrażania aplikacji i przeprowadza przez niego"
keywords: "wdrażanie, RMS, AIP"
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 00bf0748f67afe3f81de86fa643e78652cc0d7a4


---
# <a name="deploy-into-production"></a>Wdrażanie w środowisku produkcyjnym

W tym temacie użytkownik jest prowadzony przez proces wdrażania aplikacji obsługującej usługi Azure Information Protection (AIP)/Rights Management Services (RMS).

## <a name="request-an-information-protection-integration-agreement-ipia"></a>Żądanie Umowy integracyjnej usługi Information Protection (IPIA, Information Protection Integration Agreement)
Przed wydaniem aplikacji utworzonych za pomocą usługi AIP/RMS należy wystąpić o formalną umowę z firmą Microsoft i ją zawrzeć.

### <a name="begin-the-process"></a>Rozpoczęcie procesu
Uzyskaj umowę IPIA, wysyłając na adres **IPIA@microsoft.com** wiadomość e-mail z następującymi informacjami:

**Temat:** Żądanie umowy IPIA dla *nazwa firmy*

W treści wiadomości e-mail umieść następujące dane:
- Nazwa aplikacji i produktu
- Imię i nazwisko osoby żądającej
- Adres e-mail osoby żądającej

### <a name="next-steps"></a>Następne kroki
Po otrzymaniu żądania umowy IPIA wyślemy formularz (jako dokument programu Word).
Zapoznaj się z warunkami i postanowieniami umowy IPIA i wróć do formularza **IPIA@microsoft.com** w celu podania następujących informacji:
- Prawna nazwa firmy
- Stan/prowincja (USA/Kanada) lub kraj siedziby
- Adres URL firmy
- Adres e-mail osoby upoważnionej do kontaktu
- Dodatkowe adresy firmy (opcjonalnie)
- Nazwa aplikacji firmy
- Krótki opis aplikacji
- *Identyfikator dzierżawy Azure*
- *Identyfikator aplikacji* dla aplikacji
- Dane kontaktowe, adres e-mail i telefon do firmy do korespondencji w sytuacjach krytycznych

### <a name="completing-the-agreement"></a>Zawarcie umowy
Po otrzymaniu formularza wyślemy Ci link do ostatecznej postaci umowy IPIA, którą należy cyfrowo podpisać. Następnie zostanie ona podpisana przez przedstawiciela firmy Microsoft, co spowoduje zawarcie umowy.

### <a name="already-have-a-signed-ipia"></a>Masz już podpisaną umowę IPIA?
Jeśli masz już podpisaną umowę IPIA i chcesz dodać nowy *Identyfikator aplikacji* dla aplikacji, którą chcesz wydać, wyślij wiadomość e-mail na adres **IPIA@microsoft.com** i przekaż nam następujące informacje:
- Nazwa aplikacji firmy
- Krótki opis aplikacji
- Identyfikator dzierżawy Azure (nawet jeśli jest taki sam, jak poprzednio)
- Identyfikator aplikacji dla aplikacji
- Dane kontaktowe, adres e-mail i telefon do firmy do korespondencji w sytuacjach krytycznych

Po wysłaniu wiadomości e-mail odczekaj do 72 godzin na potwierdzenie przez nas odbioru.

## <a name="deploying-to-the-client-environment"></a>Wdrażanie w środowisku klienta

W celu wdrożenia aplikacji skompilowanej przy użyciu narzędzi Azure Information Protection (AIP)/Rights Management Services (RMS) musisz wdrożyć klienta RMS Client 2.1 na komputerze użytkownika końcowego.

### <a name="rms-client-21"></a>Klient RMS Client 2.1
Klient RMS Client 2.1 został zaprojektowany w celu ochrony dostępu do informacji przepływających przez aplikacje korzystające z usług AIP/RMS i ich wykorzystania — w przypadku instalacji lokalnej lub instalacji w centrum danych firmy Microsoft.

Klient RMS Client 2.1 nie jest składnikiem systemu operacyjnego Windows. Klient jest dostarczany jako opcjonalny plik do pobrania, który po potwierdzeniu i zaakceptowaniu umowy licencyjnej może być bezpłatnie dystrybuowany z aplikacją.

> [!IMPORTANT]
> Klient AD RMS Client 2.1 jest powiązany z architekturą i musi odpowiadać architekturze docelowego systemu operacyjnego.


## <a name="rms-client-21-installation-options"></a>Opcje instalacji klienta RMS Client 2.1

### <a name="creating-your-deployment-package"></a>Tworzenie pakietu wdrażania

Zalecamy dołączenie pakietu instalatora klienta RMS Client do aplikacji lub rozwiązania z wykorzystaniem preferowanej technologii instalacji. Klient usługi RMS może być za darmo dystrybuowany z innymi aplikacjami i rozwiązaniami.

Istnieje możliwość interaktywnego instalowania klienta RMS Client 2.1 poprzez uruchomienie instalatora klienta RMS Client 2.1 lub jego zainstalowanie w trybie dyskretnym. Kroki integracji:

-   Pobierz instalator klienta RMS Client 2.1
-   Zintegrowanie uruchomienia instalatora klienta RMS Client 2.1 z instalatorem aplikacji

Przykładem integracji klienta RMS Client 2.1 z aplikacją użytkownika jest pakiet [Rights Protected Folder Explorer](https://technet.microsoft.com/en-us/library/rights-protected-folder-explorer(v=ws.10).aspx). Spróbuj go zainstalować, aby zrozumieć zastosowane podejście.

### <a name="make-rms-client-21-a-pre-requisite-for-your-application-install"></a>Ustawianie klienta RMS Client 2.1 jako warunek wstępny dla instalacji aplikacji

W takim przypadku utworzysz warunek wstępny, który spowoduje, że instalacja aplikacji zakończy się niepowodzeniem, jeśli klient RMS Client 2.1 nie będzie znajdował się na komputerze użytkownika końcowego.

W przypadku braku klienta podaj komunikat o błędzie, z którego użytkownik dowie się, skąd pobrać kopię klienta RMS Client 2.1

W przypadku obecności klienta przejdź do instalacji aplikacji.

## <a name="enabling-azure-information-protection--rights-management-services-with-your-application"></a>Włączanie usług Azure Information Protection/Rights Management w aplikacji

> [!NOTE]
> W przypadku migracji do nowego modelu ADAL w celu uwierzytelniania nie trzeba instalować usługi **SIA**. Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie ADAL dla aplikacji z obsługą usług RMS](adal-auth.md).
> Możliwe jest również **certyfikowanie aplikacji dla systemu Windows 10** — aktualizacja aplikacji umożliwiająca użycie uwierzytelniania ADAL zamiast asystenta logowania usługi online firmy Microsoft oferuje następujące możliwości: korzystanie z uwierzytelniania wieloskładnikowego i instalowanie klienta RMS Client 2.1 bez wymogu posiadania uprawnień administracyjnych na komputerze


Aby użytkownik końcowy mógł korzystać z usług Information Protection/Rights Management, należy wdrożyć *Asystenta logowania w witrynie Online Services (SIA, Online Services Sign-in Assistant)*. Jako deweloper aplikacji nie wiesz, czy użytkownik końcowy będzie korzystał z ochrony informacji za pośrednictwem usług RMS (lokalnie) czy Azure Information Protection.


> [!IMPORTANT]
> Jeśli aplikacja kliencka będzie uruchamiana za pomocą usług RMS na platformie Azure, konieczne będzie utworzenie własnych dzierżaw. Aby uzyskać więcej informacji, zobacz [Wymagania dotyczące usług Azure RMS: subskrypcje usług w chmurze, które obsługują usługi Azure RMS](../get-started/requirements-subscriptions.md).
> Aby uzyskać więcej informacji o współpracy z usługami Azure RMS, zobacz [Umożliwianie współpracy aplikacji usługi z usługami RMS opartymi na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

-   Pobierz [Asystenta logowania w witrynie Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=28177) z Centrum pobierania Microsoft.
-   Upewnij się, że wdrożenie aplikacji z obsługą praw zawiera kontrolę warunków wstępnych dla tego wyboru usługi.
-   Aby uzyskać informacje o własnym testowaniu i wykorzystaniu usługi online przez użytkownika końcowego, zobacz temat TechNet [Konfiguracja usługi Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx).

Aby uzyskać więcej informacji na temat umożliwiania aplikacji korzystania z usługi RMS na potrzeby usług Azure Rights Management, zobacz temat [Umożliwianie współpracy aplikacji z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="related-topics"></a>Tematy pokrewne

* [Asystent logowania w witrynie Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Konfiguracja usługi Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [Umożliwianie współpracy aplikacji z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


