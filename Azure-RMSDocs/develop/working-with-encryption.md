---
title: Jak pracować z ustawieniami szyfrowania | Azure RMS
description: Różne pakiety szyfrowania usługi Azure RMS i przykłady fragmentów kodu, w których zastosowano te pakiety.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: B1D2C227-F43D-4B18-9956-767B35145792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: f5d50aef96520e390bd83a450e2c1bb456aba323
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39375423"
---
# <a name="how-to-work-with-encryption-settings"></a>Instrukcje: korzystanie z ustawień szyfrowania

Ten temat kieruje użytkowników do pakietów szyfrowania firmy Microsoft i zawiera przykłady fragmentów kodu, w których zastosowano te pakiety.

## <a name="support-for-aes-256-the-new-default"></a>Obsługa nowego domyślnego algorytmu szyfrowania AES 256

Żaden dodatkowy kod nie jest wymagany do korzystania z szyfrowania opartego na nowym domyślnym algorytmie *AES 256* przy założeniu, że do opracowywania aplikacji jest używana aktualizacja zestawu RMS SDK 2.1 z marca 2015 lub nowsza. Zachęcamy do rozważenia możliwości zaktualizowania aplikacji przy użyciu tej wersji w celu skorzystania z dodatkowych zalet zabezpieczeń algorytmu *AES 256*.

> [!IMPORTANT]
> Obsługa plików chronionych przy użyciu algorytmu *AES 256* była dostępna już w [wersji z października 2014 roku](release-notes-rtm.md). Jeśli używasz aplikacji utworzonych za pomocą wersji zestawu SDK sprzed października 2014 r., ta aktualizacja spowoduje awarię aplikacji. Upewnij się, że klienci aplikacji, które tworzysz, używają zaktualizowanego zestawu SDK lub są gotowi do natychmiastowego przeprowadzenia aktualizacji do najnowszej wersji aplikacji.

 
## <a name="api-encryption-support"></a>Obsługa szyfrowania w interfejsie API

Począwszy od [aktualizacji z marca 2015 roku](release-notes-rtm.md), uwzględniliśmy następujące trzy flagi w naszym interfejsie API i skojarzonych pakietach szyfrowania:

-   IPC\_ENCRYPTION\_PACKAGE\_AES256\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_ECB (nazywane również przestarzałymi algorytmami)

Flag pakietów szyfrowania (zobacz [Preferowane szyfrowanie](https://msdn.microsoft.com/library/dn974065.aspx)) można używać razem z nową flagą właściwości licencji *IPC\_LI\_PREFERRED\_ENCRYPTION\_PACKAGE*.

Poniższe przykłady fragmentu kodu przedstawiają sposób użycia nowej właściwości licencji.

## <a name="deprecated-algorithms"></a>Przestarzałe algorytmy

Flaga *IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS* nie jest już widoczna w interfejsie API. Oznacza to, że kompilacje aplikacji odwołujących się do tej flagi nie będą możliwe w przyszłości, ale aplikacje, które zostały już utworzone przy użyciu tej flagi, będą nadal działać, ponieważ flaga będzie prywatnie uznawana w kodzie interfejsu API.

Nadal będzie można uzyskiwać korzyści zapewniane przez przestarzałą flagę algorytmów szyfrowania, zmieniając po prostu jedną flagę. Jako przykład mogą posłużyć poniższe fragmenty kodu.

## <a name="protect-files-with-aes-256-cbc4k"></a>Ochrona plików przy użyciu algorytmu AES 256 CBC4K

Zmiana kodu nie jest potrzebna, ponieważ *AES 256* CBC4K jest ustawieniem domyślnym.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);


## <a name="protect-files-with-aes-128-cbc4k"></a>Ochrona plików przy użyciu algorytmu AES-128 CBC4K

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_CBC4K;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);


## <a name="protect-files-with-aes-128-ecb-deprecated-algorithms"></a>Ochrona plików przy użyciu algorytmu AES-128 ECB (przestarzałe algorytmy)

W tym przykładzie przedstawiono również nową metodą obsługi *przestarzałych algorytmów*.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_ECB;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);

