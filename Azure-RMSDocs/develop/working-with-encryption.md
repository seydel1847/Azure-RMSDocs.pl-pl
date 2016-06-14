---
# required metadata

title: Praca z szyfrowaniem | Azure RMS
description: kieruje użytkowników do pakietów szyfrowania firmy Microsoft
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: B1D2C227-F43D-4B18-9956-767B35145792
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Praca z szyfrowaniem

Ten temat kieruje użytkowników do pakietów szyfrowania firmy Microsoft i zawiera przykłady fragmentów kodu, w których zastosowano te pakiety.

## Obsługa nowego domyślnego algorytmu szyfrowania AES 256

Żaden dodatkowy kod nie jest wymagany do korzystania z szyfrowania opartego na nowym domyślnym algorytmie *AES 256*, zakładając że do programowania używana jest aktualizacja zestawu RMS SDK 2.1 z marca 2015 lub nowsza. Firma Microsoft zachęca do rozważenia możliwości zaktualizowania aplikacji przy użyciu tej wersji w celu wykorzystania dodatkowych zalet zabezpieczeń algorytmu *AES 256*.

> [!IMPORTANT]
> Obsługa plików chronionych przy użyciu algorytmu *AES 256* była dostępna już w [wersji z października 2014 roku](release-notes-rtm.md). Jeśli używasz aplikacji utworzonych za pomocą wersji zestawu SDK sprzed października 2014 roku, ta aktualizacja spowoduje awarię aplikacji. Upewnij się, że klienci aplikacji, które tworzysz, używają zaktualizowanego zestawu SDK lub są gotowi do natychmiastowego przeprowadzenia aktualizacji do najnowszej wersji aplikacji.

 
## Obsługa szyfrowania w interfejsie API

Począwszy od [aktualizacji z marca 2015 roku](release-notes-rtm.md), firma Microsoft uwzględniła następujące trzy flagi w jej interfejsie API i skojarzonych pakietach szyfrowania:

-   IPC\_ENCRYPTION\_PACKAGE\_AES256\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_ECB (zwane również przestarzałymi algorytmami)

Flag pakietów szyfrowania (zobacz [**Preferowane szyfrowanie**](/rights-management/sdk/2.1/api/win/constants#msipc_preferred_encryption)) można używać w połączeniu z nową flagą właściwości licencji **IPC\_LI\_PREFERRED\_ENCRYPTION\_PACKAGE**.

Poniższe przykłady fragmentu kodu przedstawiają sposób użycia nowej właściwości licencji.

## Przestarzałe algorytmy

Flaga **IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS** nie jest już dostępna w interfejsie API firmy Microsoft. Oznacza to, że kompilacje aplikacji odwołujących się do tej flagi nie będą możliwe w przyszłości, ale aplikacje, które zostały już utworzone przy użyciu tej flagi, będą nadal działać, ponieważ flaga będzie prywatnie uznawana w kodzie interfejsu API.

Nadal będzie można uzyskiwać korzyści zapewniane przez przestarzałą flagę algorytmów szyfrowania, zmieniając po prostu jedną flagę. Jako przykład mogą posłużyć poniższe fragmenty kodu.

## Ochrona plików przy użyciu algorytmu AES 256 CBC4K

Zmiana kodu nie jest potrzebna, ponieważ *AES 256* CBC4K jest ustawieniem domyślnym.

    
    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID, 
                                    0, 
                                    NULL, 
                                    &amp;pLicenseHandle);
    

## Ochrona plików przy użyciu algorytmu AES-128 CBC4K

    
    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID, 
                                    0, 
                                    NULL, 
                                    &amp;pLicenseHandle);
    
    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_CBC4K; 
    
    hr = IpcSetLicenseProperty(pLicenseHandle, 
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);
    

## Ochrona plików przy użyciu algorytmu AES-128 ECB (przestarzałe algorytmy)

W tym przykładzie przedstawiono również nową metodą obsługi *przestarzałych algorytmów*.

    
    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID, 
                                    0, 
                                    NULL, 
                                    &amp;pLicenseHandle);
    
    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_ECB;
    
    hr = IpcSetLicenseProperty(pLicenseHandle, 
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE, 
                           &amp;dwEncryptionMode);
    
 

 





<!--HONumber=May16_HO2-->


